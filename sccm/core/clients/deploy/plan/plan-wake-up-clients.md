---
title: "Ügyfelek felébresztése |} Microsoft Docs"
description: "Tervezze meg a System Center Configuration Manager ügyfelek felébresztése."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52ee82b2-0b91-4829-89df-80a6abc0e63a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 20f595a5b0634a627dff9ba6feeb848754615f2c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="plan-how-to-wake-up-clients-in-system-center-configuration-manager"></a>Tervezze meg a System Center Configuration Manager ügyfelek felébresztése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A Configuration Manager által támogatott két helyi hálózat (LAN) technológiákat telepíti a kötelező szoftverek, például szoftverfrissítések és alkalmazások alvó üzemmódban lévő számítógépek felébresztésére ébresztés: hagyományos ébresztési csomagok és az AMT bekapcsolási parancsokat.  

A hagyományos ébresztési csomagokat alkalmazó módszer kiegészíthető az ébresztési proxy ügyfélbeállításaival. Ébresztési proxy a társ-társ protokollt és választott számítógépeket használ, ellenőrizze, hogy az alhálózat más számítógépei ébren-e, és a felébresztésükre. Ha a webhely hálózati ébresztés van konfigurálva, és ügyfél az ébresztési proxy van konfigurálva, az eljárás a következő:  

1.  A Configuration Manager-ügyféllel rendelkező számítógépeken, és hogy nincsenek alvó állapotban az alhálózaton felvételkor hogy az alhálózat más számítógépei ébren-e. Ezek ehhez küldenek egymásnak TCP/IP ping parancsot minden 5 másodperc.  

2.  Ha nincs más számítógépekről érkező válasz, akkor rendszer feltételezi, hogy tekinti alvó állapotúnak. Az ébren lévő számítógépek válnak *kezelő-számítógép* az alhálózat.  

     Mivel előfordulhat, hogy a számítógép nem válaszol azért eltérő is alvó állapotban van (például ki van kapcsolva, eltávolították a hálózatról vagy a proxy ébresztési ügyfélbeállítás nincs alkalmazva), a számítógépek küldött ébresztési csomagot naponta 2 órakor helyi idő. A nem válaszoló számítógépeket a rendszer ettől kezdve nem tekinti alvó állapotúnak, és többé nem ébreszti ébresztési proxy használatával.  

     Ébresztési proxy támogatásához legalább három számítógépnek ébren kell lennie az egyes alhálózatokon. Ennek érdekében három számítógép nem determinisztikus kiválasztott *őrszámítógép* az alhálózat. Ez azt jelenti, hogy azok mindenképpen ébrenléti állapotban, annak ellenére, hogy az alvó vagy hibernált állapotba adott ideig tartó tétlenség után rajtuk beállított energiagazdálkodási házirend maradnak. Őrszámítógép tiszteletben leállítási vagy újraindítási parancsokat, például karbantartási feladatok miatt. Ez akkor fordul elő, ha a többi őrszámítógép felébreszt egy másik számítógépet az alhálózaton, úgy, hogy az alhálózat továbbra is három őrszámítógéppel.  

3.  Kezelő-számítógépek arra utasítják a hálózati kapcsoló az alvó számítógépek hálózati forgalom átirányítása magukat.  

     Az átirányítás a kezelő-számítógép olyan Ethernet-keretet, amely az alvó számítógép MAC-címét használja forráscímként teszi közzé az érhető el. Ez lehetővé teszi a hálózati kapcsoló fognak működni, mintha az alvó számítógép ugyanazt a portot, amely a kezelő-számítógép a át lett helyezve. A kezelő-számítógép az alvó számítógépek számára ne avuljanak az ARP-gyorsítótár csomagokat is küld ARP. A kezelő-számítógép nevében az alvó számítógép és a választ az alvó számítógép MAC-címét ARP-kérésekre is válaszol.  

    > [!WARNING]  
    >  A folyamat során a az alvó számítógép IP – MAC leképezése változatlan marad. Ébresztési proxy tájékoztatja a hálózati kapcsoló, hogy egy másik hálózati adaptert használja a portot egy másik hálózati adapter által regisztrált működik. Ez a viselkedés azonban egy MAC flap nevezik, és a normál hálózati működés szokatlan. Egyes Hálózatfigyelő eszközök figyelik az ilyen viselkedést, és feltételezheti, hogy valami probléma. Ezért az ilyen figyelőeszközök hozhat létre a vagy lezárhatják a portokat az ébresztési proxy használatakor.  
    >   
    >  Ne használjon ébresztési proxyt, ha a Hálózatfigyelő eszközök és szolgáltatások nem teszik lehetővé az MAC zárólapok.  

4.  Ha egy kezelő-számítógép alvó számítógép új TCP kapcsolódási kérelem látja, és a kérés egy portot, amely az alvó számítógép figyelt az alvó állapotba lépése előtt történik, a kezelő-számítógép ébresztési csomagot küld az alvó számítógép, és majd leállítja a irányít át forgalmat az ezen a számítógépen.  

5.  Az alvó számítógép megkapja az ébresztési csomagot, és felébred. A küldő számítógép automatikusan újrapróbálkozik a kapcsolódással, és ezúttal a számítógép felébresztése és válaszolhat.  

 Ébresztési proxy van, a következő előfeltételek és korlátozások:  

> [!IMPORTANT]  
>  Ha egy külön csapat foglalkozik a hálózati infrastruktúra és a hálózati szolgáltatások, értesíti, és ez a csoport tartalmazza az értékelési és tesztelési időszak alatt. Például az 802.1 X hálózati hozzáférés-vezérlést használó hálózaton az ébresztési proxy nem működik, és megszakíthatja a hálózati szolgáltatás. Ébresztési proxy Emellett egyes Hálózatfigyelő eszközökön riasztásokat, ha az eszközök észlelik a többi számítógép felébresztésére irányuló forgalmat azt okozzák.  

-   A támogatott ügyfelek: Windows 7, Windows 8, Windows Server 2008 R2, Windows Server 2012-ben.  

-   A virtuális gépen futó vendég operációs rendszerek nem támogatottak.  

-   Ügyfelek engedélyezni kell az ébresztési proxy ügyfélbeállításokkal. Habár az ébresztési proxy működése nem függ a hardverleltártól, nem jelentik az ébresztési proxy szolgáltatás telepítése kivéve, ha azok engedélyezve vannak a Hardverleltár és elküldött legalább egy hardverleltárt.  

-   Hálózati adapterek (és valószínűleg a BIOS-ban) engedélyezni és konfigurálni kell az ébresztési csomagokhoz. Ha a hálózati adapter nincs konfigurálva az ébresztési csomagokhoz, vagy ez a beállítás le van tiltva, a Configuration Manager automatikusan konfigurálja és engedélyezi azt egy számítógépen, ha az ébresztési proxy engedélyezésére vonatkozó ügyfélbeállítást kap.  

-   Ha egy számítógép több hálózati adapterrel rendelkezik, nem konfigurálhat melyik adaptert használja az ébresztési proxy; a rendszer nem determinisztikus. Azonban a kiválasztott adapter bekerül a SleepAgent_ < tartomány\> @SYSTEM_0.log fájlt.  

-   A hálózatnak engedélyeznie kell az ICMP echo kéréseket (legalább az alhálózaton belül). 5 másodperces időköze küldése az ICMP ping parancsok nem konfigurálható.  

-   Kommunikáció titkosítás és hitelesítés nélkül, és az IPsec használata nincs támogatva.  

-   A következő hálózati konfigurációk nem támogatottak:  

    -   802.1 X porthitelesítéssel  

    -   Vezeték nélküli hálózatok  

    -   Hálózati kapcsolók MAC-címeket adott portokhoz  

    -   Csak IPv6-hálózatok  

    -   DHCP-bérleti időtartamok kisebb, mint 24 órában  

Ha szeretné felébreszteni a számítógépeket az ütemezett szoftvertelepítéshez, konfigurálnia kell a minden elsődleges hely az ébresztési csomagok használata.  

 Az ébresztési proxy használatára energiagazdálkodás ébresztési proxyra vonatkozó ügyfélbeállításait az elsődleges hely konfigurálása mellett kell telepítenie.  

Döntse el, is alhálózat által vezérelt szórási csomagokat vagy egyedi küldésű csomagokat használ-e, és milyen UDP-portszámot fogja használni. Alapértelmezés szerint hagyományos ébresztési csomagok 9-es UDP-port használatával elküldött, de a nagyobb biztonság érdekében választhat a helyhez más portot Ha beavatkozó útválasztók és tűzfalak támogatják az alternatív port.  

### <a name="choose-between-unicast-and-subnet-directed-broadcast-for-wake-on-lan"></a>Válasszon az egyedi küldéses és helyi hálózati ébresztés alhálózat által vezérelt szórás  
 Ha úgy döntött, hogy felébreszteni a számítógépeket hagyományos ébresztési csomagok küldésével, el kell döntenie, hogy egyedi küldésű csomagokat vagy alhálózat által vezérelt szórási csomagokat. Ha az ébresztési proxyt használ, egyedi küldésű csomagokat kell használnia. Ellenkező esetben használja az alábbi táblázat segítségével eldöntheti, milyen átviteli mód kiválasztása.  

|Átviteli módja|Előnye|Hátránya|  
|-------------------------|---------------|------------------|  
|Egyedi küldéses|Biztonságosabb megoldás alhálózat által vezérelt szórást, mert a csomag küldése közvetlenül arra a számítógépre, ahelyett, hogy az alhálózat összes számítógépre.<br /><br /> Nem újrakonfigurálását igényelheti az útválasztók (lehetséges, hogy az ARP-gyorsítótár konfigurálása).<br /><br /> Kisebb hálózati sávszélességet, mint az alhálózat által vezérelt szórásos küldést igényel.<br /><br /> Támogatott IPv4 és IPv6-környezetben.|Az ébresztési csomagok nem találják meg célhelyként megadott számítógépeken, amelyeknek alhálózati címe a legutóbbi Hardverleltár-ütemezés után módosított.<br /><br /> Kapcsolók esetleg UDP-csomagok továbbítására kell konfigurálni.<br /><br /> Egyes hálózati adapterek nem válaszol az ébresztési csomagok minden alvási állapota mikor használják az egyedi küldéses átviteli módszert.|  
|Alhálózat által vezérelt szórás|Számítógépek, amelyek gyakran módosítják IP-címüket ugyanazon az alhálózaton van küldésnél nagyobb sikerességi arányát.<br /><br /> Nincs kapcsoló újrakonfigurálására szükség.<br /><br /> Magas kompatibilitási arány a számítógép-adapterekkel minden alvási állapot, mert az alhálózat által vezérelt szórás volt az ébresztési csomagok eredeti átviteli módszere.|Kevésbé biztonságos megoldás, mint az egyedi küldéses használatával, mert az esetleges támadók folyamatos ICMP echo-kéréseket küldhetnek egy hamisított forráscímről a vezérelt szórási címre. Ennek hatására az összes gazdagép erre a forráscímre válaszol. Ha útválasztókat úgy vannak konfigurálva, hogy alhálózat által vezérelt szórást, a további konfigurációs biztonsági okokból ajánlott:<br /><br /> -Konfigurálja az útválasztókat, hogy csak IP-vezérelt szórást a Configuration Manager helykiszolgálón, megadott UDP-portszám használatával.<br />-Configuration Manager a megadott nem alapértelmezett portszám használatára konfigurálja.<br /><br /> Az alhálózat által vezérelt szórás engedélyezése az összes beavatkozó útválasztó újrakonfigurálását igényelheti.<br /><br /> Egyedi küldéses átvitel-nál nagyobb hálózati sávszélességet igényel.<br /><br /> Csak a támogatja az IPv4-alapú; Az IPv6 nem támogatott.|  

> [!WARNING]  
>  Nincsenek alhálózat által vezérelt szórás kapcsolódó biztonsági kockázatokról: A támadó küldhet folyamatos Internet Control Message Protocol (ICMP) echo-kéréseket egy hamisított forráscímről a vezérelt szórási címre, aminek következtében az összes gazdagép erre a forráscímre válaszol. Az ilyen típusú szolgáltatásmegtagadási támadások gyakran nevezik smurf-támadásnak, és általában nem engedélyezik az alhálózat által vezérelt szórás elhárítására.

