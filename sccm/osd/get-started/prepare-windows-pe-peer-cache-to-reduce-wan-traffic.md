---
title: "WAN-hálózati forgalom csökkentése érdekében a Windows PE társ-gyorsítótárazás előkészítése |} Microsoft Docs"
description: "A Windows PE társ-gyorsítótárazás beszerezni a tartalmat egy helyi társtól, és ha nincs helyi terjesztési pont a WAN-hálózati forgalom minimalizálása érdekében a Windows PE környezetben is működik."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c64f276-b88c-4b1e-8073-331876a03038
caps.latest.revision: 11
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 814c6133a30b1116d05aaeafddb0dfb7fe2a390e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-windows-pe-peer-cache-to-reduce-wan-traffic-in-system-center-configuration-manager"></a>A Windows PE társ-gyorsítótárazás előkészítése a WAN-hálózati forgalom csökkentése érdekében a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager új operációs rendszer telepítésekor a feladatütemezést futtató számítógépek használható Windows PE társ-gyorsítótárazás a tartalmak való beszerzésére egy terjesztési pontról történő letöltésük helyett egy helyi társtól (társ-gyorsítótárazási forrástól). Így minimálisra csökkenthető a nagykiterjedésű hálózat (WAN) forgalma a helyi terjesztési pont nélküli fiókirodai forgatókönyvek esetén.  

 A Windows PE társ-gyorsítótárazás hasonlít [Windows BranchCache](http://technet.microsoft.com/library/mt617255\(TechNet.10\).aspx#bkmk_branchcache), azonban a Windows előtelepítési környezetben (Windows PE) működik. Ha a feladatütemezést az operációs rendszer környezetéből, például az ügyfélen lévő Szoftverközpontból indítja el, a Windows PE társ-gyorsítótárazás nem használható. A Windows PE társ-gyorsítótárazást használó ügyfeleket az alábbi kifejezésekkel írjuk le:  

-   A **társ-gyorsítótárazási ügyfél** a Windows PE társ-gyorsítótárazás használatára konfigurált számítógép.  

-   A **társ-gyorsítótárazási forrás** a társ-gyorsítótárazásra konfigurált azon ügyfél, amely más társ-gyorsítótárazási ügyfelek számára teszi elérhetővé az általuk kért tartalmakat.  

A következő részekben társ-gyorsítótárazás kezelését.

##  <a name="BKMK_PeerCacheObjects"></a> A társ-gyorsítótárazási forrásokon tárolt objektumok  
 A Windows PE társ-gyorsítótárazás használatára konfigurált feladatütemezések a következő tartalomobjektumokat szerezhetik be a Windows PE környezetben való futtatásuk során:  

-   Operációsrendszer-lemezkép  

-   Illesztőprogram-csomag  

-   Csomagok és programok (ha az ügyfél továbbra is futtatja a feladatütemezést a teljes operációs rendszeren, kapja ezt a tartalmat egy társ-gyorsítótárazási forrástól Ha a feladatütemezést eredetileg konfigurálták a társ-gyorsítótárazás futtatásakor a Windows PE környezetben.)  

-   További rendszerindító lemezképek  

 Az alábbi tartalomobjektumok továbbítása sohasem társ-gyorsítótárazással történik. Ehelyett azok átvitele egy terjesztési pontról vagy a Windows BranchCache használatával történik, ha a Windows BranchCache konfigurálva lett a környezetben:  

-   Alkalmazások  

-   Szoftverfrissítések  

##  <a name="BKMK_PeerCacheWork"></a> A Windows PE társ-gyorsítótárazás működése  
 Példaként vegyünk egy forgatókönyvet, melyben egy fiókiroda nem rendelkezik terjesztési ponttal, számos olyan ügyféllel azonban igen, amelyek számára engedélyezett a Windows PE társ-gyorsítótárazás használata. A társ-gyorsítótárazás használatára konfigurált feladatütemezést több olyan ügyfélre is telepíti, melyek úgy vannak konfigurálva, hogy a társ-gyorsítótárazási forrás részei legyenek. A feladatütemezést elsőként futtató ügyfél kérést küld a tartalommal rendelkező társnak. Amikor nem találja, a tartalmat egy terjesztési pontról szerzi be a WAN-on keresztül. Az ügyfél telepíti az új lemezképet, majd tárolja a tartalmat a Configuration Manager-ügyfél gyorsítótárában, így más ügyfelek számára társ-gyorsítótárazási forrástól működhetnek. Amikor a következő ügyfél futtatja a feladatütemezést, társ-gyorsítótárazási forrásra vonatkozó kérést küld az alhálózaton, amelyre az első ügyfél válaszol, és elérhetővé teszi a gyorsítótárazott tartalmat.  

##  <a name="BKMK_PeerCacheDetermine"></a> Annak meghatározása, hogy mely ügyfelek fognak részt venni a Windows PE társ-gyorsítótárazásban  
 Több dolgot is figyelembe kell vennie annak meghatározásához, hogy mely számítógépeket jelölje ki Windows PE társ-gyorsítótárazási forrásként:  

-   A Windows PE társ-gyorsítótárazási forrásnak olyan asztali számítógépnek kell lennie, amely mindig van kapcsolva és elérhető a társ-gyorsítótárazási ügyfelek számára.  

-   A Windows PE társ-gyorsítótárazás ügyfélgyorsítótárának mérete elegendő a lemezképek tárolásához.  

##  <a name="BKMK_PeerCacheRequirements"></a> A Windows PE társ-gyorsítótárazási források használatának ügyfelekre vonatkozó követelményei  
 Az ügyfeleknek a következő követelményeknek kell megfelelniük egy Windows PE társ-gyorsítótárazási forrás használatához:  

-   A Configuration Manager-ügyfél a következő portokat a hálózaton keresztüli képesnek kell lennie:  

    -   Port a kezdeti hálózati szórás számára, társ-gyorsítótárazási forrás kereséséhez. Alapértelmezés szerint ez a 8004-es port.  

    -   Port tartalom letöltésére társ-gyorsítótárazási forrástól (HTTP és HTTPS). Alapértelmezés szerint ez a 8003-as port.  

        > [!TIP]  
        >  Az ügyfelek a HTTPS protokollt használják a tartalom letöltésére, ha az elérhető. Ugyanakkor a rendszer a HTTP és a HTTPS protokollhoz is ugyanazt a portszámot használja.  

-   Az ügyfeleken [konfigurálnia kell a Configuration Manager-ügyfelek ügyfélgyorsítótárát](../../core/clients/manage/manage-clients.md#BKMK_ClientCache) annak biztosításához, hogy az ügyfelek elegendő hellyel rendelkezzenek a központilag telepített lemezképek megőrzésére és tárolására. A Windows PE társ-gyorsítótárazás nincs hatással az ügyfélgyorsítótár konfigurációjára vagy viselkedésére.  

-   A feladatütemezés központi telepítésére vonatkozó központi telepítési beállítások konfigurált értékének a következőnek kell lennie: Tartalom helyi letöltése, ha a feladatütemezés igényli.  

##  <a name="BKMK_PeerCacheConfigure"></a> A Windows PE társ-gyorsítótárazás konfigurálása  
 Az alábbi módszerekkel hozhat létre társ-gyorsítótárazási tartalommal rendelkező ügyfelet, hogy az társ-gyorsítótárazási forrásként szolgálhasson:  

-   Ha egy társ-gyorsítótárazási ügyfél nem talál a tartalommal rendelkező társ-gyorsítótárazási forrást, egy terjesztési pontról fogja letölteni a tartalmat.  Ha az ügyfél a társ-gyorsítótárazást engedélyező ügyfélbeállításokkal rendelkezik, és a feladatütemezés a gyorsítótárazott tartalom megőrzésére van konfigurálva, az ügyfél társ-gyorsítótárazási forrássá válik.  

-   A társ-gyorsítótárazási ügyfél lehet beszerezni a tartalmat egy másik társ-gyorsítótárazási ügyfél (társ-gyorsítótárazási forrástól).  Mivel az ügyfél konfigurálva lett a társ-gyorsítótárazásra, ha olyan feladatütemezést futtat, amely a gyorsítótárazott tartalom megőrzésére lett konfigurálva, az ügyfél társ-gyorsítótárazási forrássá válik.  

-   Az ügyfél által futtatott feladatütemezés tartalmazza a [Csomagtartalom letöltése](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) választható lépést, amely a Windows PE társ-gyorsítótárazás feladatütemezésében található kapcsolódó tartalom előkészítésére szolgál. Ha ezt a módszert használja:  

    -   Az ügyfélnek nem kell telepítenie a központilag telepítendő lemezképet.  

    -   A **Csomag tartalmának letöltése** lépésen kívül a feladatütemezésnek a **Configuration Manager-ügyfél gyorsítótára** beállítást is használnia kell. Ezzel a beállítással tárolhatja a tartalmakat az ügyfélgyorsítótárban, így az ügyfél társ-gyorsítótárazási forrásként működhet más társ-gyorsítótárazási ügyfelek számára.  

 Az alábbi eljárások segítségével konfigurálhatja a Windows PE társ-gyorsítótárazást az ügyfeleken, illetve konfigurálhatja a társ-gyorsítótárazást támogató feladatütemezéseket.  

### <a name="to-configure-the-windows-pe-peer-cache-source-computers"></a>A Windows PE társ-gyorsítótárazási forrásszámítógépek konfigurálása  

1.  A Configuration Manager-konzolon lépjen a **felügyeleti** > **ügyfélbeállítások**, és hozzon létre egy új **egyéni ügyféleszköz-beállítások** vagy egy meglévő beállítási objektumot szerkesztése. A konfigurálást az **Alapértelmezett ügyfélbeállítások** objektum esetén is elvégezheti.  

    > [!TIP]  
    >  Egy egyéni beállítási objektum segítségével felügyelheti, hogy mely ügyfelek kapják meg ezt a konfigurációt. Lehetséges például, hogy nem szeretné ezt olyan felhasználók hordozható számítógépén konfigurálni, akik gyakran úton vannak. Egy rendkívül mobil rendszer rossz forrásnak bizonyulhat, amikor más társ-gyorsítótárazási ügyfeleknek kell tartalmat biztosítania.  
    >   
    >  Továbbá ne feledje, hogy ha ezt a beállítást az **Alapértelmezett ügyfélbeállítások**részeként konfigurálja, a konfiguráció a környezet összes ügyfelére érvényes.  

2.  A **Windows PE társ-gyorsítótárazás**területen állítsa a **Tartalom megosztásának engedélyezése a teljes operációs rendszeren futó Configuration Manager-ügyfél számára** beállítást **Igen**értékűre.  

    -   Alapértelmezés szerint csak a HTTP engedélyezett. Ha szeretné engedélyezni, hogy az ügyfelek a HTTPS használatával töltsenek le tartalmakat, állítsa a **HTTPS engedélyezése az ügyfelek társközi kommunikációjához** beállítást **Igen**értékűre.  

    -   Alapértelmezés szerint a szóráshoz beállított port a 8004-es, a tartalom letöltéséhez beállított port pedig a 8003-as. Mindkettőt módosíthatja.  

3.  Mentse az ügyfélbeállításokat, és telepítse azokat a társ-gyorsítótárazási forrásként használni kívánt ügyfelekre.  

 Miután ezzel a beállítási objektummal konfigurált egy eszközt, az eszköz társ-gyorsítótárazási forrásként való működésre van konfigurálva. Ezeket a beállításokat központilag telepíteni kell a lehetséges társ-gyorsítótárazási ügyfelekre a szükséges portok és protokollok konfigurálásához.  

###  <a name="BKMK_PeerCacheConfigureTS"></a> Feladatütemezés konfigurálása a Windows PE társ-gyorsítótárazás számára  
 A feladatütemezés konfigurálásakor az alábbi feladatütemezési változókat gyűjteményváltozóként használja abban a gyűjteményben, amelyben a feladatütemezést központilag telepíti:  

-   **SMSTSPeerDownload**  

     Érték:  IGAZ  

     Engedélyezi az ügyfél számára a Windows PE társ-gyorsítótárazás használatát.  

-   **SMSTSPeerRequestPort**  

     Érték: < Port száma\>  

     Ha nem az alapértelmezett porton konfigurálva az ügyfél beállításai (8004) használja, konfigurálnia kell ezt a változót a kezdeti szóráshoz használni kívánt hálózati port egyéni értékével.  

-   **SMSTSPreserveContent**  

     Érték: IGAZ  

     A tartalom a feladatütemezés központi telepítése után a Configuration Manager-ügyfél gyorsítótára megőrzendő tartalomként jelöli meg. Ez eltér attól smstspersiscontent használatától, amely csak a feladatütemezés idejére őrzi meg a tartalmat, és a feladatütemezés gyorsítótárát, nem a Configuration Manager-ügyfél gyorsítótára használja.  

 További információkért lásd: [beépített feladatütemezési változókat](../understand/task-sequence-built-in-variables.md).  

###  <a name="BKMK_PeerCacheValidate"></a> A Windows PE társ-gyorsítótárazás sikeres használatának ellenőrzése  
 Egy feladatütemezésnek a Windows PE társ-gyorsítótárazással történő központi telepítése után úgy ellenőrizheti, hogy a folyamat sikeresen használta-e a társ-gyorsítótárazást, hogy megtekinti az **smsts.log** fájlt a feladatütemezést futtató ügyfélen.  

 A naplóban keresse meg az alábbihoz hasonló bejegyzést ahol <*Forráskiszolgálóneve*> azonosítja azt a számítógépet, ahonnan az ügyfél beszerezte a tartalmat. Ennek a számítógépnek egy társ-gyorsítótárazási forrásnak, nem pedig terjesztésipont-kiszolgálónak kell lennie. Az egyéb részletek a helyi környezettől és konfigurációktól függően eltérőek lesznek.  

-   *<! [Napló [le a fájlt: http:// < Forráskiszolgálóneve\>: 8003/SCCM_BranchCache$/SS10000C/sccm?/install.wim c:\\_SMSTaskSequence\Packages\SS10000C\install.wim] napló]! >< idő = "14:24:33.329 + 420" dátum = "06-26-2015" component = "ApplyOperatingSystem" context = "" típus = "1" thread = "1256" file="downloadcontent.cpp:1626" >*  

