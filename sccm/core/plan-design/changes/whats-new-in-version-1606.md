---
title: "Újdonság a System Center Configuration Manager frissítése 1606 |} Microsoft Docs"
description: "Ezzel adatokat kapjon módosítások és a System Center Configuration Manager 1606 verziójában bevezetett új képességekkel rendelkezik."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34809ddf7819eab5deb3995cd8138c7b38cd2f9a
ms.openlocfilehash: 9fdff6049d6e5cde1032864e5d7aa8df71e53686
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>Mi &#39; verzió 1606 a System Center Configuration Manager újdonságai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1606 frissítése a System Center Configuration Manager 1511-es vagy az 1602-es verzióját futtató már telepített helyeken a konzolon belüli frissítésként érhető el. 1511-es verziója az alapszintű verzió új Configuration Manager-helyek telepítéséhez használt.
> [!TIP]  
>  További információ:  
>   
>  -   [Új helyek telepítése](/sccm/core/servers/deploy/install) (például 1511-es alapszintű verziójának használatával)  
>  -   [Helyfrissítések telepítése](/sccm/core/servers/manage/updates) (például az 1602-es vagy 1606 frissítés)  

 A következő szakaszok részletesen bemutatják a módosításokat, és a Configuration Manager 1606 verziójában bevezetett új képességekkel rendelkezik.  



## <a name="updatesandservicing"></a>Frissítések és karbantartás

### <a name="changes-for-the-updates-and-servicing-node"></a>A módosítások a frissítések és karbantartás csomópontjánál
Módosítások a frissítések és karbantartás csomópontjánál, a Configuration Manager konzolon a következők:
> [!NOTE]
> Ezek a változások nem érhetők el addig 1606 verziójának telepítése után.

- **Csomópont módosítása:**

    Az a **figyelés** munkaterületen, a **hely karbantartásának állapota** csomópont át lett nevezve a **frissítések és karbantartás állapot**.
- **További telepítési állapotának részletei:**

    Amikor egy hely a frissítés telepítési állapotát, a konzol ettől kezdve különálló részleteit a következő műveleteket:
    - **Töltse le** (Ez vonatkozik csak a legfelső szintű helyet, ahol a szolgáltatás kapcsolódási pont helyrendszerszerepkör telepítve van.)
    - **Replikáció**
    - **Előfeltételek ellenőrzése**
    - **Telepítés**

  Pedig most már minden lépés, beleértve a mely naplófájlban tekintheti meg további információt a további tájékoztatáshoz.  
-   **Új beállítás az újbóli előfeltétel-ellenőrzési hibák:**

    Mind a **felügyeleti** és **figyelés** munkaterületek, a **frissítés és karbantartás** csomópont tartalmazza egy új gombot a menüszalagon nevű **előfeltételekre vonatkozó figyelmeztetések mellőzését**.

    Előfeltételekre vonatkozó figyelmeztetések mellőzését a beállítás használata nélkül frissítések telepítésekor (a frissítések varázslóban), és a frissítés telepítése leáll figyelmeztetés miatt, majd kiválaszthatja **előfeltételekre vonatkozó figyelmeztetések mellőzését** a szalagról. Ezzel elindítja az automatikus folytatása a frissítés telepítését.  



- **A frissítések tisztító megtekintése:**

    Az a **frissítés és karbantartás** csomópontot, ekkor megjelenik a legutóbb telepített frissítés, és más új frissítések érhetők el, hogy telepítse. Korábban telepített frissítések megtekintéséhez kattintson az új **előzmények** gomb, amely megjelenik a menüszalagon.  

-   **Átnevezett lehetőséget éles üzem előtti használathoz:**

    Az a **frissítés és karbantartás** csomópont, a **ügyfél beállításai** gomb neve **üzem előtti ügyfél előléptetése**.


###  <a name="pre-release-features"></a>Előzetes funkciók
1606 kezdve kell adnia a hozzájárulási használata a System Center Configuration Manager előzetes kiadású szolgáltatások előtt válassza ki, és azok használatának engedélyezése. További információk a következő helyen találhatók: [A frissítésekben biztosított előzetes funkciók használata](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="new-distribution-point-update-behavior"></a>Új terjesztési pont frissítésének
Frissítés 1606 vezet be, amelyek javítják a terjesztési pontok rendelkezésre állását a jövőbeli frissítések telepítésekor módosításokat.

1606 frissítés után a van telepítve, a következő frissítés egy adott helyen, amelyhez az automatikus újratelepítése standard és a lekéréses terjesztési pont helyrendszer-szerepkörök, összes terjesztési pont már nem kapcsolat nélküli módba egyszerre frissíteni. Ehelyett a helykiszolgáló beállításai a hely terjessze a tartalmakat a terjesztési pontok egy részhalmazát frissítésének terjesztése az adott időpontban. Az eredménye, hogy csak néhány terjesztési pontról kapcsolat nélkül a frissítés telepítéséhez. Ez lehetővé teszi, hogy a terjesztési pontok, amelyek még nem kezdett frissítéséhez, vagy, hogy befejeződött a frissítés, online állapotú, és adja meg a tartalom az ügyfelek tudni maradjon.



## <a name="accessibility"></a>Kisegítő lehetőségek
Keresse meg a másik munkaterület-csomópont között, most egy csomópont neve első betűjének adhat meg. Minden egyes billentyű megnyomása a kurzor áthelyezése a következő csomópont, amely adott betűvel kezdődik. A felhasználók számára, akik rendelkeznek a képernyőolvasók az olvasó olvassa be az adott csomópont nevét. Kisegítő lehetőségekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager kisegítő lehetőségei](../../../core/understand/accessibility-features.md).

## <a name="administration"></a>Felügyeleti
A Configuration Manager konzol felügyeleti módosításainak a következők:
### <a name="oms-connector"></a>OMS-összekötő

Csatlakoztathatja a Configuration Manager gyűjtemények a System Center Configuration Manager számára, a [a Microsoft Operations Management Suite (OMS)](https://azure.microsoft.com/en-us/documentation/articles/operations-management-suite-overview/). Így az adatok, például a Configuration Manager telepítési gyűjteményt OMS látható. További tudnivalók megkeresésének című [a Microsoft Operations Management Suite Itt a Configuration Manager alkalmazásból adatok szinkronizálása](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md).

Az OMS-összekötő egy előzetes verziójú funkció. Az engedélyezéshez, lásd: [használata a frissítések előzetes kiadású szolgáltatások](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="support-for-cache-size-in-client-settings"></a>Gyorsítótár mérete az ügyfélbeállításokban támogatása

A gyorsítótár mappájának mérete most már konfigurálhatja az ügyfélszámítógépeken **ügyfélbeállítások** a Configuration Manager konzolon. Csak beállíthat korábban, az ügyfél gyorsítótára telepítésekor vagy újratelepítésekor az ügyfélszoftvert. Adja meg a gyorsítótár méretét ügyfélbeállításként (alapértelmezett vagy egyéni), és akkor kell ezeket a beállításokat alkalmazni az ügyfélen, a következő házirend-frissítés anélkül, hogy egy ügyfél telepítse újra. További információ: [A Configuration Manager-ügyfelekhez tartozó ügyfélgyorsítótár konfigurálása](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache).

## <a name="on-premises-mobile-device-management"></a>A helyszíni mobileszköz-kezelés

### <a name="support-for-multiple-device-management-points"></a>Több eszköz felügyeleti pont támogatása

A helyszíni mobileszköz-kezelés (MDM) mostantól támogatja a egy új funkció a Windows 10 évforduló frissítés, amely automatikusan konfigurálja a regisztrált eszköz szeretné, hogy egynél több eszközfelügyeleti pont használható. Ez a funkció lehetővé teszi az eszköz térhet vissza másik eszközfelügyeleti pont, amikor általában felhasznál egy nem érhető el. Ez a lehetőség csak akkor működik a számítógépek és eszközök a Windows 10 évforduló frissítés.


## <a name="application-management"></a>Alkalmazáskezelés

### <a name="manage-apps-from-the-windows-store-for-business"></a>A Vállalati Windows Áruházban vásárolt alkalmazások felügyelete

A [vállalati Windows áruház](https://www.microsoft.com/business-store) hol található, és Windows alkalmazásokat vásárolhat a szervezete számára egyenként vagy mennyiségi. Ha összekapcsolja az áruházat a Configuration Manager, szinkronizálhatja a vásárolt és a Configuration Managerben, ezeket a Configuration Manager konzolon megtekintheti, és azok meg, mint bármilyen más alkalmazást az alkalmazások listáját.

További információkért lásd: [alkalmazások kezelése a System Center Configuration Managerrel a vállalati Windows áruházból](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md).

### <a name="manage-ios-volume-purchased-apps"></a>Mennyiségi programban vásárolt iOS-alkalmazások felügyelete

Mennyiségi programban vásárolt iOS-alkalmazásokat kezeléséhez és való telepítésének a Configuration Managerrel, a munkafolyamat javult.

További információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások a System Center Configuration Managerrel kezelése](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).

### <a name="software-center-user-interface"></a>A Szoftverközpont felhasználói felülete

A Szoftverközpont felhasználói felület úgy alakították megkönnyíti a felderítéshez.
*  A **telepítési állapotát** és **telepített szoftverek** lapok egyesítettük egyetlen **telepítési állapotát** fülre.
*  **Frissítések**, **operációs rendszerek**, és **alkalmazások** rendelkezik három különálló lap lett osztva.
* Több frissítés most választható telepítéshez egyszerre, vagy minden frissítés egyszerre is telepíthető kattintva **telepítse az összes**.

### <a name="content-status-links"></a>A tartalom állapotának hivatkozások
Egy alkalmazás vagy csomag tulajdonságainál most kapcsolat van, amely az adott objektum állapotát a.

## <a name="software-updates"></a>Szoftverfrissítések

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Ügyfél-eszközbeállítást az Office 365-ügyfélügynök kezelése
Most már használhatja a Configuration Manager-ügyfél kezelése az Office 365-ügyfélügynök beállítása. Után beállítaniuk ezt, és Office 365-frissítéseket, a Configuration Manager-ügyfél ügynöke működik az Office 365 ügyfél ügynökének letöltése és telepítése az Office 365 frissítéseit a terjesztési pontról.

További információkért lásd: [Office 365 ProPlus kezelése frissíti a Configuration Manager](../../../sum/deploy-use/manage-office-365-proplus-updates.md).

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>Manuálisan váltson az ügyfelek egy új szoftverfrissítési pontra
Mostantól engedélyezhető olyan beállítás, amely lehetővé teszi, hogy a Configuration Manager ügyfelek kapcsoló egy új szoftverfrissítési pont frissítse, ha az aktív szoftverfrissítési ponttal probléma. Engedélyezése esetén a következő keresés során az ügyfelek másik szoftverfrissítési pontot fognak keresni.

További információkért lásd: [tervezése a Configuration Manager szoftverfrissítéseinek](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs).

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>Újraindítási lehetőségek Windows 10-ügyfelek számára szoftverfrissítés telepítése után
Amikor egy szoftverfrissítés újraindítást igénylő Configuration Manager használatával történik, és telepítve van a számítógépen, a függőben lévő újraindítás van ütemezve. Újraindítást kérő párbeszédpanelt is megjelenik. A Configuration Manager verziója 1606, a beállítások verziótól **frissül és újraindul** és **frissítés és a leállítási** érhetők el, ha a Configuration Manager szoftverfrissítés egy függőben lévő újraindítás. A Windows 10 számítógépek a Windows energiagazdálkodási lehetőségek elérhetők. Ezen beállítások valamelyikét használja, az újraindítást kérő párbeszédpanelt nem jelenik meg a számítógép újraindítása után.

További információkért lásd: [tervezése a System Center Configuration Manager szoftverfrissítések](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions).

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>Szoftverfrissítés-megfelelőségi ellenőrzést követően azonnal futtatni, által telepített szoftverfrissítések és újraindítása
Most a megfelelőségi vizsgálat futtatása követően azonnal által telepített szoftverfrissítések és újraindul. A meg ezt a telepítést, a **felhasználói élmény** a szoftver központi telepítése frissítések varázsló, válassza a lap **Ha a központi telepítésben található bármelyik frissítés a rendszer újraindítása, futtassa a frissítések telepítésének értékelési ciklusát újraindítás után szükséges**. Ez lehetővé teszi, hogy az ügyfél ellenőrizze a olyan további szoftverfrissítéseket, amelyek az ügyfél újraindítása után válnak alkalmazhatóvá, majd telepítse őket (és a követelményeknek megfelelővé válnak) azonos a karbantartási időszak alatt. További információkért lásd: [szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates) vagy [szoftverfrissítések manuális központi telepítése](/sccm/sum/deploy-use/manually-deploy-software-updates).

## <a name="operating-system-deployment"></a>Operációs rendszer központi telepítése

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>A feladatütemezési lépés fejlesztései: Szoftverfrissítések telepítése
Egy új beállítás **értékelik a szoftverfrissítéseket a gyorsítótárazott vizsgálati eredmények**, lehetővé teszi a szoftverfrissítések, a gyorsítótárazott vizsgálati eredmények helyett teljes ellenőrzés elvégzéséhez beállítását. További információkért lásd: [feladatütemezési lépések a System Center Configuration Managerben](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates).

Emellett új feladatütemezési változót, **SMSTSSoftwareUpdateScanTimeout**, érhető el. Ezzel a változóval adhatja meg a szoftverfrissítési keresés időtúllépés történjen a szoftverfrissítések telepítése feladatütemezési lépés során. Az alapértelmezett érték 30 perc. További információkért lásd: [feladatütemezési beépített változókat a System Center Configuration Managerben](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>Elavult OSDPreserveDriveLetter feladatütemezési változó
A OSDPreserveDriveLetter feladatütemezési változó elavult. A Configuration Manager verziója 1606 kezdődően a Windows telepítő határozza meg (általában a C:) használata során az operációs rendszer központi telepítése alapértelmezés szerint a legjobb meghajtóbetűjelet.

További információkért lásd: [feladatütemezési beépített változókat a System Center Configuration Managerben](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>A RamDisk TFTP-ablakméretet beállítani a PXE-képes terjesztési pontok testreszabása
Most már testreszabhatja a RamDisk ablakméretét, a PXE-képes terjesztési pontokon. Ha testreszabta a hálózatot, akkor a rendszerindító lemezkép letöltése időtúllépési hiba, sikertelen, mert az ablak mérete túl nagy. A RamDisk Trivial File Transfer Protocol (TFTP) ablakban testreszabásával lehetővé teszi a TFTP-forgalom optimalizálása, amikor PXE használ a konkrét hálózati követelmények teljesítéséhez.

További információkért lásd: [helyrendszerszerepkörök előkészítése operációs rendszerek központi telepítése a System Center Configuration Managerrel](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="compliance-settings"></a>Megfelelőségi beállítások

### <a name="smart-lock-setting-for-android-devices"></a>Intelligens zárolás beállítás Android-eszközökhöz
Egy új beállítás **engedélyezése a Smart Lock és más megbízhatósági ügynökök**, az Android és Samsung KNOX Standard konfigurációs elem hozzá lett adva.

Ez a beállítás lehetővé teszi, hogy a kompatibilis Android-eszközökön intelligens zárolás funkciót szabályozhatja. Ez a mint a "megbízhatósági ügynökök" néven is ismert telefonos funkció lehetővé teszi letiltását vagy megkerülését az eszköz zárolási képernyője jelszavának, ha az eszköz megbízható helyen van. Megbízható helyen lehet például, ha az egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy ha egy bizonyos NFC-címkéhez van közel. Ezzel a beállítással használhatja, hogy a felhasználók az intelligens zárolás konfigurálását.

További információkért lásd: [Android és Samsung KNOX Standard eszközökhöz konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).

## <a name="device-configuration-and-protection"></a>Eszközök konfigurálása és védelem

### <a name="product-name-changes"></a>A termék nevének módosítása

* A Microsoft Passport for Work mostantól néven **vállalati Windows Hello**.
* Nagyvállalati adatvédelem mostantól néven **Windows információvédelem**.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>A Windows Hello (a Passport for Work) vállalati telepítése

Most már telepítheti a Windows Hello-tartományhoz csatlakoztatott Windows 10-eszközökre a Configuration Manager-ügyfél által felügyelt vállalati házirendek.

A Configuration Manager konzolon a változásoknak frissítve lett.

### <a name="ios-activation-lock"></a>iOS aktiválási zára
A Configuration Manager segítségével iOS aktiválási zára, egy szolgáltatás find My iPhone alkalmazást az iOS 7.1 és újabb rendszerű eszközök kezelése. Ha a funkció be van kapcsolva, meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni az alábbiak bármelyikét:
* A Find My iPhone alkalmazás kikapcsolása.
* Az eszköz alaphelyzetbe állítása.
* Az eszköz újraaktiválása.

A Configuration Manager kétféle módon segíthet az aktiválási zár kezelésében:

- Az aktiválási zár engedélyezése felügyelt eszközökön.
- Az aktiválási zár megkerülése felügyelt eszközökön.

További információkért lásd: [kezelhető az iOS aktiválási zára a System Center Configuration Managerrel](../../../mdm/deploy-use/manage-ios-activation-lock.md).


### <a name="windows-defender-advanced-threat-protection"></a>A Windows Defender komplex veszélyforrások elleni védelem

Az Endpoint Protection kezelni és megfigyelni a Windows Defender Advanced Threat Protection (ATP) segítségével. A Windows Defender ATP egy új szolgáltatás, amely segítségére lesz a vállalatok számára, hogy észlelni, vizsgálja meg és a hálózat a speciális támadások válaszolni. A Configuration Manager-házirendek alapképességeivel és figyelheti a felügyelt számítógépeken futó Windows 10 1607. verzió (build 14328) vagy újabb.

További információkért lásd: [Windows Defender Advanced Threat Protection](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md).

### <a name="device-categories"></a>Eszközkategóriák
Tegyen eszközök eszközgyűjtemények automatikusan használatakor a Configuration Manager a Microsoft Intune-nal használható eszközkategóriákat hozhat létre. Felhasználók majd válasszon egy eszközkategóriát, amikor regisztrálják az eszköz Intune-beli van szükség. Emellett módosíthatja a kategóriája az eszköz a Configuration Manager konzoljáról.

További információkért lásd: [hogyan automatikusan eszközök kategorizálása a System Center Configuration Managerrel gyűjteményekbe](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md).

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Előzetes deklarálása IMEI- vagy iOS-sorozatszámokat rendelkező eszközök

Vállalat által birtokolt eszközök azonosíthatja az állomás nemzetközi mobilkészülék-azonosító (IMEI) számokat vagy iOS-sorozatszámokat importálásával. Feltöltheti az eszközök IMEI-számának tartalmazó vesszővel tagolt (.csv) fájlt, vagy meg manuálisan is beírhatja az eszközadatokat. Importált adatok elemnél állítja be a "Céges" eszközként eszközöket tulajdonjogát. Intune-licencet minden felhasználó, aki hozzáfér a szolgáltatás továbbra is szükség.

További részletekért lásd: [előzetes deklarálása IMEI- vagy iOS-sorozatszámokat eszközök](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

### <a name="on-premises-health-attestation-service-communication"></a>A helyszíni Állapotigazolási szolgáltatás kommunikációja

Most már engedélyezheti a Windows 10 rendszerű számítógépek figyelésének csak a helyszíni infrastruktúra segítségével Eszközállapot-igazolási szolgáltatásokról, hogy a számítógépek Internet nélkül hozzáférhessenek jelentés eszköz egészségügyi igazolás (DHA) is.

További információkért lásd: [állapotigazolás a System Center Configuration Manager](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers).  

## <a name="remote-control"></a>Távvezérlés
Lehetővé teszi a felhasználók a lehetőséget, fogadja el, vagy elutasítja a fájlátvitelek előtt tartalmat visz át a megosztott vágólap a távvezérlési munkamenetet. Felhasználók csak engedélyt kell biztosítania munkamenetenként egyszer, és az használatával nem képesek az engedélyt magukat a fájlátvitel folytatásához. Ez az új beállítás található a **felügyeleti** munkaterületen. Lépjen **ügyfélbeállítások**, majd a **alapértelmezett beállítások**, nyissa meg a **Táveszközök** panel.

