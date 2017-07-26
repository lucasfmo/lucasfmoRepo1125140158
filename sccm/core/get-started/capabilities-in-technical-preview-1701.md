---
title: "A Technical Preview-ban 1701 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1701 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b330c97a0853d1673f1cf7e0691891b72407fa51
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>A rendszer 1701 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*



Ez a cikk ismerteti az új szolgáltatásokat a Technical Preview a System Center Configuration Manager, a verzió 1701 elérhető. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>Határ csoportok fejleszthetjük tovább a szoftverfrissítési pontok frissítése
Ebben az előzetes verzióban kezdve most segítségével határcsoportok ügyfelek társítani a szoftverfrissítési pontok. Ez folyamatos munkahelyi bontsa ki a változásokat a további helyrendszer-szerepkörök kezelése a határcsoportok része.  Határcsoportok változások először Technical Preview 1609 és az aktuális ág 1610 verzióban bevezetett.  

Ebben az előzetes használja az új határ csoport viselkedése kezeléséhez mely szoftverfrissítési pontok az ügyfél használhatja, hasonló módon történő kezelésére mely terjesztési pont az ügyfél használhatja:  

- Rendelje hozzá a egy határcsoportokat konfigurál, vagy további kiszolgálók, amelyek a szoftverfrissítési pont frissítését.
- Az ügyfelek, amely egy új szoftverfrissítési pontot keresnek próbálják használni az aktuális határcsoporthoz társított.
- Ha az ügyfél nem tudja elérni az aktuális szoftverfrissítési pontot és nem található az aktuális határcsoport közül, az ügyfél tartalék viselkedés segítségével bontsa ki a szoftverfrissítési pontokról használni tudja a rendelkezésre álló készlet.    

A határcsoportok további információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/boundary-groups) az aktuális ág számára a tartalom.

Azonban ebben az előzetes a szoftverfrissítési pontokhoz határcsoportokat csak részben valósíthatók meg. Szoftverfrissítési pontok hozzáadása, és konfigurálja a szomszédos határcsoportokat, amely tartalmazza a szoftverfrissítési pontot, azonban a szoftverfrissítési pontok tartalék ideje még nem támogatott, és megvárja, hogy az ügyfelek két óra tartalék elindítása előtt.

A következő szoftverfrissítési pontok a jelen technikai előzetes kiadással működését mutatja be:  

-    **Új ügyfelek határcsoportok segítségével válassza ki a szoftverfrissítési pontok,** egy ügyfél telepítése után, akkor telepítse verzió 1701 választja ki a szoftverfrissítési pont azoktól, amelyeket az ügyfél határcsoporthoz társított.

  Ez a felváltja a korábbi viselkedését, ahol az ügyfelek a szoftverfrissítési pont véletlenszerűen egy listából választhatja ki, amely az ügyfelek erdő megosztani.   

-    **Korábban telepített ügyfelek továbbra is az aktuális szoftverfrissítési pont tartalék csak egy új kereséséhez.**
Ügyfelek, amelyeket korábban telepítettek és, hogy már rendelkezik egy szoftverfrissítési pont továbbra is a szoftverfrissítési pont használatára csak tartalék. Ez magában foglalja a szoftverfrissítési pontok, amelyek nem az ügyfél aktuális határcsoporthoz társított. Nem azonnal megpróbálják is megkeresheti, az aktuális határcsoport a szoftverfrissítési pontot.

  Egy ügyfél, amely már rendelkezik egy szoftverfrissítési pont elkezdi használni az új határ csoport viselkedése, csak az ügyfél nem tudja elérni az aktuális szoftverfrissítési pontot, és elindítja a tartalék után.
Ez a késés új viselkedésének váltás szándékosan így. Ennek az az oka megváltoztak a szoftverfrissítési pont is nagy igénybe vett sávszélesség eredményezi, mivel az ügyfél szinkronizálja az adatokat az új szoftverfrissítési ponttal. Az átmeneti késleltetés elkerülése érdekében a hálózati mágneses erősítő kell minden Váltás az ügyfelek új szoftverfrissítési pontok frissítése a egyszerre segítségével.

-    **Tartalék idő konfigurációi:** Ügyfelek keresése egy új szoftverfrissítési pontot tartalék elindításakor konfigurációi a technical Preview nem támogatottak. Ez magában foglalja a konfigurációi **tartalék alkalommal (perc)** és **soha tartalék**, hogy a különböző határcsoport csoportok közötti kapcsolatok előfordulhat, hogy konfigurálja.

  Ehelyett az ügyfelek továbbra is az aktuális viselkedését, ha egy ügyfél próbál csatlakozni, hogy az aktuális szoftverfrissítési pont található egy új szoftverfrissítési pontot használhat tartalék megkezdése előtt két órán keresztül.

  Ha egy ügyfél tartalék használja, elérhető szoftverfrissítési pontok-készlet létrehozása a határcsoportok konfigurációiról tartalékként fogja használni. Ez a készlet összes szoftverfrissítési pontján az ügyfelektől érkező tartalmaz *aktuális határcsoport*, *határcsoportok szomszéd*, és az ügyfelek *alapértelmezett helyhatárcsoportba*.

- **A alapértelmezett webhely határcsoport konfigurálásával:**  
 Vegyen fel egy szoftverfrissítési pont és a *alapértelmezett –--Helyhatárcsoportba&lt;sitecode >*. Ez biztosítja, hogy az ügyfelek, amelyek nem egy másik határcsoport tagjai tartalék olyan szoftvert is frissíti pontot.


Szoftverfrissítési pont határcsoportok kezeléséhez használja a [eljárások az aktuális ág dokumentációjában](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups), de ne feledje, hogy tartalék alkalommal konfigurálhat nem még használja szoftverfrissítési pontokat.


## <a name="hardware-inventory-collects-uefi-information"></a>Hardverleltár UEFI adatokat gyűjt.
Egy új hardverleltárosztály (**SMS_Firmware**) és a tulajdonság (**UEFI**) elérhető segítségével meghatározhatja, hogy a számítógép UEFI üzemmódban indul. Ha a számítógép UEFI módban indul el a **UEFI** tulajdonsága **igaz**. Ez a Hardverleltár alapértelmezés szerint engedélyezve van. Hardverleltár kapcsolatos további információkért lásd: [konfigurálása a Hardverleltár](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="improvements-to-operating-system-deployment"></a>Operációs rendszer központi telepítésének fejlesztései
A következő fejlesztéseket operációs rendszerek központi telepítése sok volt a felhasználó hang visszajelzést eredményét hajtottunk.
- [**Az alkalmazás telepítése feladatütemezési lépés további alkalmazások támogatása**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): Azt a 99 telepíthető alkalmazások maximális száma növekedett a **alkalmazások telepítése** feladatütemezési lépést. Az előző maximális szám 9-es alkalmazások volt.
- [**Válassza ki az alkalmazás telepítése feladatütemezési lépés több alkalmazás**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): Amikor az alkalmazás telepítése feladatütemezés alkalmazások lépést a feladatütemezés-szerkesztő, most kiválaszthatja származó alkalmazásokat a **válassza ki a telepítendő alkalmazást** ablaktáblán.
- [**Önálló adathordozót lejár**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): Amikor önálló adathordozót hoz létre, új beállítások állnak rendelkezésre a választható érvényességének kezdő és záró dátumának beállítása az adathordozón. Ezek a beállítások alapesetben le vannak tiltva. A dátum a számítógép rendszerideje összehasonlítja a különálló adathordozó futtatása előtt. Amikor a rendszer pontos ideje a kezdési időpontnál korábbi vagy későbbi, mint a lejárati idő, a különálló adathordozó nem indult el. Ezek a beállítások is elérhetők a New-CMStandaloneMedia PowerShell-parancsmag használatával.
- [**Támogatja a különálló adathordozót a további tartalmat**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): További tartalmat mostantól támogatják a különálló adathordozót. Kiválaszthatja a további csomagokat, illesztőprogram-csomagokat és alkalmazásokat és az egyéb, a feladatütemezésben hivatkozott tartalom az adathordozón átmenetileg tárolva. Csak a feladatütemezésben hivatkozott tartalom korábban, az önálló adathordozó lett előkészített.
- [**Illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezési lépés konfigurálható időkorlátjának**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): Új feladatütemezési változók is elérhető az időtúllépés értéke konfigurálása az illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezési lépés a HTTP-katalógus kérések meghozásakor. A következő változók és az alapértelmezett értékek (másodpercben) érhetők el:
   - SMSTSDriverRequestResolveTimeOut alapértelmezett: 60
   - SMSTSDriverRequestConnectTimeOut alapértelmezett: 60
   - SMSTSDriverRequestSendTimeOut alapértelmezett: 60
   - SMSTSDriverRequestReceiveTimeOut alapértelmezett: 480
- [**Csomagazonosító megjelenik a feladatütemezési lépések**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): Feladatütemezés bármely lépése egy csomag, illesztőprogram-csomagot, operációs rendszer lemezképét, rendszerindító lemezkép vagy operációs rendszer verziófrissítő csomagjára hivatkozó mostantól megjeleníti a hivatkozott objektum Csomagazonosítóját. Ha egy feladatütemezési lépés hivatkozik egy alkalmazást jeleníti meg az objektum azonosítójával.
- **Windows 10 ADK követik nyomon buildszámát**: A Windows 10 ADK mostantól több támogatott élmény biztosításához, ha a Windows 10-es rendszerindító lemezképek testreszabása buildszámát követi nyomon. Például ha a webhely használ a Windows ADK for Windows 10, verziója 1607, csak rendszerindító lemezképek 10.0.14393 verziójával testre szabható a konzolon. WinPE-verziókat testreszabásával kapcsolatos részletekért lásd: [rendszerindító lemezképek testreszabása](/sccm/osd/get-started/customize-boot-images).
- **Alapértelmezett rendszerindító lemezkép forrásának elérési útvonalára már nem módosítható**: Alapértelmezett rendszerindító lemezképek a Configuration Manager által felügyelt, és az alapértelmezett rendszerindító lemezkép forrásának elérési útvonalára már nem módosítható a Configuration Manager konzolon, vagy a Configuration Manager SDK használatával. Továbbra is adja meg egy egyéni forrás elérési útját az egyéni rendszerindító lemezképeket.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>Szoftverfrissítések gazdagépet a felhő alapú terjesztési pontokon
Az előzetes verzióval kezdve használhatja a felhőalapú terjesztési pont a szoftverfrissítési csomag tárolásához. Azonban mivel a szoftverfrissítések letöltése a Microsoft Update-ről ügyfeleket beállíthatja úgy, fontolja meg a további költségek, a szoftverek telepítését frissíti a csomagot a felhőalapú terjesztési ponthoz is fel Önnek.

Felhőalapú terjesztési pontok használatával kapcsolatos információkért lásd: [felhő alapú terjesztési pont használata](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) a tartalom az aktuális ág a Configuration Manager.

## <a name="validate-device-health-attestation-data-via-management-points"></a>Eszközállapot-igazolási adatok felügyeleti pontokon keresztül ellenőrzése

Ezen előzetes verziójával kezdve beállíthatja a felügyeleti pontok állapotigazolási jelentés a felhőbeli vagy helyszíni állapotigazolási szolgáltatás adatainak érvényesítéséhez. Egy új **speciális beállítások** lapra a **felügyeleti pont összetevő tulajdonságai** párbeszédpanel lehetővé teszi, hogy **Hozzáadás**, **szerkesztése**, vagy **eltávolítása** a **a helyszíni eszközök állapotának állapotigazolási szolgáltatás URL-címe**. Azt is megadhatja, **egyéni eszközbeállítások** az ügyfél ügynök **helyszíni Állapotigazolási szolgáltatás**.  Beállítás **Igen** esetében ez a beállítás lehetővé teszi a helyszíni jelentéskészítő felügyeleti pontot a felhő alapú szolgáltatás helyett.

### <a name="try-it-out"></a>Próbálja ki

- **Helyszíni készülékállapot-igazolás egy felügyeleti pont engedélyezése**<br>  A Configuration Manager konzolon nyissa meg a felügyeleti pont, és nyissa meg a **felügyeleti pont összetevő tulajdonságai** , majd a **speciális beállítások** fülre. Kattintson a **Hozzáadás** és adja meg a helyszíni URL-CÍMÉT (például https://10.10.10.10) **helyszíni eszköz állapotfigyelő állapotigazolási szolgáltatás URL-címek**.
- **A helyi felügyeleti pont az Eszközállapot-igazolás a ügyfélügynökének reporting engedélyezése**<br>Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** , és kattintson duplán, vagy hozzon létre egy új **egyéni eszközbeállítások**. Válassza ki **Számítógépügynök** és **helyszíni Állapotigazolási szolgáltatás** való **Igen**. Ha **kommunikáció engedélyezése az Eszközállapot-igazolási szolgáltatás** értéke **Igen** és **helyszíni Állapotigazolási** értéke **nem**, a felügyeleti pontot fogja használni a felhő alapú Eszközállapot-igazolási szolgáltatás.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>A Microsoft Azure Government felhő az OMS-összekötő használatára
A jelen technikai előzetes kiadással használhatja a Microsoft Operations Management Suite (OMS) összekötőt, amely a Microsoft Azure Government felhő OMS-munkaterület való kapcsolódáshoz.  

Ehhez az szükséges, módosítsa a konfigurációs fájlt úgy, hogy a kormányzati felhő mutasson, és telepítse az OMS-összekötő.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Állítsa be az OMS-összekötő a Microsoft Azure Government felhőbe
1.  Minden számítógépen, amely a Configuration Manager konzol telepítve van a következő konfigurációs fájlt a kormányzati felhőbe szerkesztése:  ***&lt;CM telepítési útvonala > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Szerkesztése:**

    A beállítás neve értékének módosításához *FairFaxArmResourceID* "https://management.usgovcloudapi.net/" egyenlőnek kell lennie

   - **Eredeti:** 
      &lt;Beállításnév = "FairFaxArmResourceId" serializeAs = "Karakterlánc" >   
      &lt;érték > &lt; /value >   
      &lt;/ Beállítás >

   - **Módosítani:**     
      &lt;beállítás neve "FairFaxArmResourceId" serializeAs = "Karakterlánc" = > &lt;érték > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ Beállítás >

  A beállítás neve értékének módosításához *FairFaxAuthorityResource* "https://login.microsoftonline.com/" egyenlőnek kell lennie

  - **Eredeti:** &lt;Beállításnév = "FairFaxAuthorityResource" serializeAs = "Karakterlánc" >   
    &lt;érték > &lt; /value >

    - **Módosítani:** &lt;Beállításnév = "FairFaxAuthorityResource" serializeAs = "Karakterlánc" >   
    &lt;érték > https://login.microsoftonline.com/ &lt; /value >

2.    A fájl két módosításainak mentése, után indítsa újra a ugyanazon a számítógépen a Configuration Manager konzolon, és ez a konzol segítségével az OMS-összekötő telepítése. Az összekötő telepítéséhez, olvassa el a [szinkronizálni az adatokat a Configuration Manager a Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), és válassza ki a **Operations Management Suite-munkaterület** , amely megtalálható a Microsoft Azure Government felhő.

3.    Az OMS-összekötő telepítése után a kormányzati felhőben nincs elérhető kapcsolat, amely kapcsolódik a helyhez egyetlen konzol használata esetén.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android és iOS verziója már nem nem targetable a létrehozási varázslók a hibrid MDM

Hibrid mobileszköz-kezelés (MDM) a technical preview verziótól kezdve már nem kell átadnia Android és iOS adott verzió új házirendek és profilok az Intune által felügyelt eszközök létrehozásakor. Ehelyett választhat a következő eszköztípusok esetében:

- Android
- Samsung KNOX szabvány 4.0 és újabb verziók
- iPhone
- iPad

Ez a módosítás érinti a varázsló a következő elemek létrehozásához:

- Konfigurációelemek
- Megfelelőségi szabályzatok
- Tanúsítványprofilok
- E-mail profilok
- A VPN-profilok
- Wi-Fi profilok

Ez a változás a hibrid telepítések is támogatást nyújt a gyorsabban új Android és iOS verziója egy új Configuration Manager-kiadás vagy a bővítmény anélkül. Az Intune önálló verziójának új verzió támogatott, ha felhasználók tudják verzió frissítése a mobileszközeiket.

A Configuration Manager korábbi verzióiról történő frissítése során előforduló problémák megelőzéséhez, mobil operációsrendszer-verziók továbbra is elérhetők ezek az elemek tulajdonságok lapját. Ha továbbra is szeretné egy adott verziójához, az új elem létrehozása, és adja meg a megcélzott verziója az újonnan létrehozott elemet a Tulajdonságok lapján.

