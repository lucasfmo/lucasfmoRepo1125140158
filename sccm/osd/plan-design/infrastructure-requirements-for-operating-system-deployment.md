---
title: "Operációs rendszer központi telepítésének infrastrukturális követelményei |} Microsoft Docs"
description: "Ellenőrizze, hogy tudja külső függőségei és a termék függőségek az operációs rendszer központi telepítéséhez a System Center 2012 Configuration Manager használata előtt."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: 24
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: a002bf5e03c3fd71a6346c8303be757b83092199
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="infrastructure-requirements-for-operating-system-deployment-in-system-center-configuration-manager"></a>Az operációs rendszer központi telepítésének infrastrukturális követelményei a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Operációs rendszer központi telepítése a System Center 2012 Configuration Manager külső és a terméken belüli függőségekkel rendelkezik. A következő szakaszok segítségével felkészülhet az operációs rendszer központi telepítésére.  

##  <a name="BKMK_ExternalDependencies"></a> A Configuration Manager alkalmazáson kívüli függőségek  
 A következő külső eszközökről, telepítőkészletekről és operációs rendszerek, a Configuration Manager operációs rendszerek központi telepítéséhez szükséges információkat biztosít.  

### <a name="windows-adk-for-windows-10"></a>Windows ADK for Windows 10  
 A Windows ADK a Windows operációs rendszerek konfigurálását és központi telepítését megkönnyítő eszköz- és dokumentumkészlet. A Configuration Manager a Windows ADK segítségével automatizálja a Windows telepítését, rögzíti a Windows lemezképeit, telepíti át a felhasználói profilokat és adatokat és így tovább.  

 A Windows ADK alábbi funkcióit kell telepíteni a hierarchia legfelső szintjén lévő helykiszolgálóra, a hierarchiában elsődleges helyeken lévő helykiszolgálókra, valamint az SMS Provider helyrendszer-kiszolgálóra:  

-   User State Migration Tool (USMT) <sup>1</sup>  

-   Windows központi telepítési eszközök  

-   Windows előtelepítési környezet (Windows PE)  

 <sup>1</sup> Az USMT megléte nem szükséges a SMS Provider helyrendszer-kiszolgálón.  

> [!NOTE]  
>  Manuálisan telepítenie kell a Windows ADK minden futtató számítógépre egy központi adminisztrációs hely vagy elsődleges helykiszolgálón a Configuration Manager-hely telepítése előtt.  

 További információkért lásd:  

-   [Windows ADK for Windows 10 scenarios for IT Pros (Windows ADK for Windows 10 forgatókönyvek informatikai szakemberek számára) (Windows ADK for Windows 10 forgatókönyvek informatikai szakemberek számára)](https://technet.microsoft.com/library/mt280162\(v=vs.85\).aspx)  

-   [A Windows ADK for Windows 10 program letöltése](https://msdn.microsoft.com/windows/hardware/dn913721.aspx#adkwin10)  

-   [Windows 10 támogatása](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>User State Migration Tool (USMT)  
 A Configuration Manager rögzítse és visszaállítsa a felhasználói állapotot az operációs rendszer központi telepítésének részeként USMT 10 forrásfájlokat tartalmazó USMT-csomagot használ. A Configuration Manager telepítő a legfelső szinten automatikusan létrehozza az USMT-csomagot. Az USMT 10 a Windows 7, Windows 8, Windows 8.1 és Windows 10 rendszerek felhasználói állapotát tudja rögzíteni. Az USMT 10-es verziójának terjesztése a Windows 10 rendszerhez készült Windows Assessment and Deployment Kit (Windows ADK) eszközben történik.  

 További információkért lásd:  

-   [Gyakori áttelepítési helyzetek az USMT 10 használatakor](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)  

-   [Felhasználói állapot kezelése](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 A Windows PE a számítógép indítására szolgáló rendszerindító lemezképekhez használt környezet. Egy olyan, korlátozott számú szolgáltatást tartalmazó Windows operációs rendszer, amely a Windows operációs rendszer előtelepítése és központi telepítése során használható. A következő biztosít a Configuration Manager verziója és a Windows ADK támogatott verzióit, a Windows PE azon verzióját a rendszerindító lemezkép alapul a Configuration Manager konzoljáról testre szabható és a Windows PE azon verzióit, amelyen a rendszerindító lemezkép alapul, hogy a DISM segítségével testreszabható, és adja a lemezképet a megadott Configuration Manager verziója.  

#### <a name="configuration-manager-version-1511"></a>A Configuration Manager 1511-es verziója  
 A következő szakasz a Windows ADK támogatott verzióit, a Windows PE azon verzióját a rendszerindító lemezkép alapul a Configuration Manager konzoljáról testre szabható és a Windows PE azon verzióit, amelyeken a rendszerindító lemezkép alapul, hogy a DISM segítségével testreszabható, és ezután hozzáadhatja a lemezképet a Configuration Manager tartalmaz.  

-   **Windows ADK-verzió**  

     Windows ADK for Windows 10  

-   **A Configuration Manager konzoljáról testre szabható rendszerindító lemezképekhez használható Windows PE-verziók**  

     Windows PE 10  

-   **A Configuration Manager konzoljáról nem testre szabható rendszerindító lemezképekhez támogatott Windows PE-verziók**  

     Windows PE 3.1<sup>1</sup> és Windows PE 5  

     <sup>1</sup> csak hozzáadhat egy rendszerindító lemezképet a Configuration Manager során, a Windows PE 3.1 rendszeren alapul. Telepítse a Windows AIK Supplement for Windows 7 SP1 szoftvert a Windows AIK for Windows 7 (Windows PE 3) frissítéséhez a Windows AIK Supplement for Windows 7 SP1 (Windows PE 3.1) verzióra. A Windows AIK Supplement for Windows 7 SP1 a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=5188)tölthető le.  

     Például ha a Configuration Manager, testre szabhatja a Windows ADK for Windows 10 (Windows PE 10-alapú) rendszerindító lemezképeket a Configuration Manager konzoljáról. Noha a Windows PE 5 alapú rendszerindító lemezképek támogatottak, egy másik számítógépen kell testre szabnia azokat, és a Windows ADK for Windows 8-cal telepített DISM-verziót kell használnia. Ezt követően a rendszerindító lemezképet is hozzáadhat a Configuration Manager-konzolra. További információ a lépésekről, amelyekkel testre szabhatja a rendszerindító lemezképeket (választható összetevők és illesztőprogramok hozzáadása), engedélyezheti a parancstámogatást a rendszerindító lemezképhez, hozzáadhatja a rendszerindító lemezképet a Configuration Manager konzolt, és a terjesztési pontokat frissíteni a rendszerindító lemezképet, lásd: [rendszerindító lemezképek testreszabása](../get-started/customize-boot-images.md). További információ a rendszerindító lemezképekről: [A rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
Az alábbi WSUS 4.0 gyorsjavításokat kell telepítenie:
  - [Hotfix 3095113](https://support.microsoft.com/kb/3095113) kiegészített WSUS 4.0-re van szükség a Windows 10 karbantartásához, amely a szoftverfrissítések infrastruktúrájának használatával szerzi be a Windows 10 szolgáltatásainak frissítéseit. Ha WSUS 3.2 szolgáltatással rendelkezik, feladatütemezés használatával frissítsen Windows 10-re. További információkért lásd: [kezelése a Windows mint szolgáltatás](../deploy-use/manage-windows-as-a-service.md).  
  - [A gyorsjavítás 3159706](https://support.microsoft.com/kb/3159706) Windows 10-karbantartási számítógépek frissítéséhez a Windows 10 évforduló frissítés, valamint a későbbi verziók használata szükséges. Manuális lépések ismertetését a támogatási továbbítania kell a gyorsjavítás. További információkért lásd: [kezelése a Windows mint szolgáltatás](../deploy-use/manage-windows-as-a-service.md).


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>Az Internet Information Services (IIS) a helykiszolgálókon  
 Az IIS a terjesztési pont, az állapotáttelepítési pont és a felügyeleti pont szempontjából szükséges. Ez a követelmény kapcsolatos további információkért lásd: [hely és hely rendszerkövetelmények](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-deployment-services-wds"></a>Központi Windows-telepítési szolgáltatások (WDS)  
 A WDS-re PXE-központitelepítések esetén (a központi telepítések csoportos küldéssel való optimalizálásakor) és a lemezképek offline szervizelésekor van szükség. Ha a szolgáltató távoli kiszolgálón van telepítve, a WDS-t a helykiszolgálón és a távoli szolgáltató kiszolgálóján egyaránt telepíteni kell. További információt a témakör [Központi Windows-telepítési szolgáltatások](#BKMK_WDS) című szakaszában talál.  

### <a name="dynamic-host-configuration-protocol-dhcp"></a>Dynamic Host Configuration Protocol (DHCP)  
 A DHCP-re PXE-központitelepítésekhez van szükség. PXE használatával történő központi operációsrendszer-telepítésekhez aktív állomással rendelkező, működő DHCP-kiszolgálóra van szükség. További információ a PXE típusú központi telepítéseknél, lásd: [PXE használatával a Windows központi telepítése a hálózaton keresztül](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

### <a name="supported-operating-systems-and-hard-disk-configurations"></a>Támogatott operációs rendszerek és merevlemez-konfigurációk  
 További információ az operációsrendszer-verziókról és merevlemez-konfigurációk a Configuration Manager által támogatott operációs rendszerek központi telepítéséhez: [támogatott operációs rendszerek](#BKMK_SupportedOS) és [támogatott lemezkonfigurációk](#BKMK_SupportedDiskConfig).  

### <a name="windows-device-drivers"></a>Windows eszközillesztők  
 A Windows eszközillesztők az operációs rendszer célszámítógépre telepítésekor, illetve akkor használhatók, amikor a Windows PE futtatása rendszerindító lemezképpel történik. Illesztőprogramokkal kapcsolatos további információkért lásd: [kezelheti az illesztőprogramokat](../get-started/manage-drivers.md).  

##  <a name="BKMK_InternalDependencies"></a> A Configuration Manager függőségei  
 A következő információkat biztosít a Configuration Manager operációs rendszer központi telepítésének előfeltételei.  

### <a name="operating-system-image"></a>Operációsrendszer-lemezkép  
 A Configuration Managerben az operációsrendszer-lemezképek tárolása WIM formátumú fájlokban történik, amelyek azoknak a referenciafájloknak és -mappáknak a tömörített gyűjteményét tartalmazzák, amelyekre szükség van az operációs rendszer sikeres telepítéséhez és konfigurációjához a számítógépen. További információkért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

### <a name="driver-catalog"></a>Illesztőprogram-katalógus  
 Eszközillesztő központi telepítéséhez meg kell az eszközillesztő importálása, engedélyezheti és tegye elérhetővé, amely a Configuration Manager-ügyfél által hozzáférhető terjesztési ponton. Az illesztőprogram-katalógus kapcsolatos további információkért lásd: [kezelheti az illesztőprogramokat](../get-started/manage-drivers.md).  

### <a name="management-point"></a>Felügyeleti pont  
 Felügyeleti pontok információt továbbítanak az ügyfélszámítógépek és a Configuration Manager-hely között. A felügyeleti pontokat az ügyfél a központi operációsrendszer-telepítés befejezéséhez szükséges feladatütemezések futtatására használja.  

 További információ a feladatütemezések: [tervezési megfontolások a feladatok automatizálásához](planning-considerations-for-automating-tasks.md).  

### <a name="distribution-point"></a>Terjesztési pont  
 A terjesztési pontok a legtöbb központi telepítés során egy operációs rendszer központi telepítéséhez felhasznált adatok (például az operációsrendszer-lemezkép vagy eszközillesztő csomagok) tárolására használatosak. A feladatütemezések jellemzően a terjesztési pontokról olvasnak be adatokat az operációs rendszerek központi telepítéséhez.  

 Terjesztési pontok telepítéséről és a tartalomkezelésről kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="pxe-enabled-distribution-point"></a>PXE-t támogató terjesztési pont  
 PXE által kezdeményezett központi telepítések megvalósításához konfigurálnia kell a terjesztési pontokat, hogy fogadni tudják az ügyfélszoftverekből érkező PXE-kéréseket. A terjesztési pont konfigurálásával kapcsolatos további információkért lásd: [a terjesztési pont](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe).  

### <a name="multicast-enabled-distribution-point"></a>Csoportos küldésre képes terjesztési pont  
 Az operációs rendszerek csoportos küldéssel történő központi telepítésének optimalizálásához olyan terjesztési pontokat kell biztosítani, amelyek támogatják azt. A terjesztési pont konfigurálásával kapcsolatos további információkért lásd: [a terjesztési pont](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).   

### <a name="state-migration-point"></a>állapotáttelepítési pont  
 Amikor párhuzamos és frissítési célú központi telepítésekhez rögzít vagy állít vissza felhasználói állapotadatokat, egy másik számítógépen történő tárolásukhoz be kell állítania egy állapotáttelepítési pontot.  

 További információ az állapotáttelepítési pont beállításáról: [Állapotáttelepítési pont](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

 Felhasználói állapot rögzítéséhez és visszaállításához kapcsolatos információkért lásd: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

### <a name="service-connection-point"></a>Szolgáltatáskapcsolódási pont  
 Ha  Windows szoftverszolgáltatással végzi a Windows 10 legújabb verziójának telepítését, az eszközén telepítve kell lennie a szolgáltatáskapcsolódási pontnak. További információkért lásd: [kezelése a Windows mint szolgáltatás](../deploy-use/manage-windows-as-a-service.md).  

### <a name="reporting-services-point"></a>Jelentéskészítési szolgáltatási pont  
 Configuration Manager-jelentések használata az operációs rendszer központi telepítése, akkor telepítenie és konfigurálnia kell egy jelentéskészítési szolgáltatási pontot. További információkért lásd: [jelentéskészítési](../../core/servers/manage/reporting.md).  

### <a name="security-permissions-for-operating-system-deployments"></a>Központi operációsrendszer-telepítésekre vonatkozó biztonsági engedélyek  
 Az **operációs rendszer központi telepítője** biztonsági szerepkör a rendszer része, és nem módosítható. A szerepkör azonban átmásolható és így módosítható, majd a módosítások mentésével új, egyéni biztonsági szerepkör jön létre. A központi operációsrendszer-telepítésekre többek között az alábbi engedélyek vonatkoznak közvetlenül:  

-   **Rendszerindító Lemezképcsomag**: Létrehozása, törlése, módosítása, módosítsa a mappa, objektum áthelyezése, Olvasás, biztonsági hatókör megadása  

-   **Eszközillesztők**: Létrehozása, törlése, módosítása, mappa módosítása, jelentés módosítása, objektum áthelyezése, Olvasás, jelentés futtatása  

-   **Illesztőprogram-csomag**: Létrehozása, törlése, módosítása, módosítsa a mappa, objektum áthelyezése, Olvasás, biztonsági hatókör megadása  

-   **Operációs rendszer lemezképének**: Létrehozása, törlése, módosítása, módosítsa a mappa, objektum áthelyezése, Olvasás, biztonsági hatókör megadása  

-   **Operációsrendszer telepítési csomagja**: Létrehozása, törlése, módosítása, módosítsa a mappa, objektum áthelyezése, Olvasás, biztonsági hatókör megadása  

-   **Feladatütemezési csomag**: Hozzon létre, a feladat létrehozása feladatütemezési adathordozó, törlése, módosítása, mappa módosítása, jelentés módosítása, objektum áthelyezése, Olvasás, jelentés futtatása, biztonsági hatókör megadása  

 Az egyéni biztonsági szerepkörökkel kapcsolatban további információt a következő témakörben talál: [Egyéni biztonsági szerepkörök létrehozása](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole).  

### <a name="security-scopes-for-operating-system-deployments"></a>Központi operációsrendszer-telepítésekre vonatkozó biztonsági hatókörök  
 Biztonsági szerepkörök alkalmazásával biztosítható a rendszergazdai szintű felhasználók hozzáférése a központi operációsrendszer-telepítések során használt biztonságos objektumokhoz, például az operációs rendszerek lemezképeihez, a rendszerindító lemezképekhez, eszközillesztő-csomagokhoz, valamint feladatütemezési csomagokhoz. További információ: [Biztonsági hatókörök](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope).  

##  <a name="BKMK_WDS"></a> Windows központi telepítési szolgáltatások  
 A Windows központi telepítési szolgáltatások (WDS) szolgáltatást ugyanarra a kiszolgálóra kell telepíteni, mint amelyiken a PXE vagy a csoportos küldés támogatására beállított terjesztési pontok vannak. A WDS szolgáltatás a kiszolgálón lévő operációs rendszer része. PXE-központitelepítések esetén a PXE-rendszerindítást a WDS szolgáltatás hajtja végre. A terjesztési pont telepítése és a PXE engedélyezve van, a Configuration Manager telepít egy szolgáltatót, hogy a WDS szolgáltatás PXE-rendszerindítási funkcióit használó WDS-be.  

> [!NOTE]  
>  Ha a kiszolgálót újra kell indítani, a WDS telepítése meghiúsulhat.  

 Egyéb, megfontolásra érdemes WDS-konfigurációk például az alábbiak:  

-   A WDS telepítéséhez a kiszolgálón a rendszergazdának a Helyi rendszergazdák csoport tagjának kell lennie.  

-   A WDS-kiszolgálónak vagy egy Active Directory-tartomány tagjának, vagy egy Active Directory-tartomány tartományvezérlőjének kell lennie. Az összes Windows-tartomány- és erdőkonfiguráció támogatja a WDS szolgáltatást.  

-   Ha a szolgáltató távoli kiszolgálón van telepítve, a WDS-t a helykiszolgálón és a távoli szolgáltató kiszolgálóján egyaránt telepíteni kell.  

###  <a name="BKMK_WDSandDHCP"></a> Figyelembe veendő szempontok, ha egyazon kiszolgálón WDS-t és DHCP-t is telepített  
 Vegye figyelembe a következő konfigurálási problémákat, ha úgy tervezi, hogy olyan kiszolgálón legyen, amelyiken fut a DHCP.  

-   Rendelkeznie kell egy aktív hatókörű DHCP kiszolgálóval. A DHCP kiszolgálóra a Központi Windows-telepítési szolgáltatásoknak a PXE használata miatt van szükségük.  

-   A DHCP kiszolgálónak és a Központi Windows-telepítési szolgáltatásoknak is szüksége van a 67-es számú portra. Ha a Központi Windows-telepítési szolgáltatások és a DHCP közös üzemeltetésű, a DHCP vagy a PXE használatához konfigurált terjesztési pont áthelyezhető külön kiszolgálóra. Az is lehet, hogy a következő eljárással úgy konfigurálja a Központi Windows-telepítési szolgáltatások kiszolgálóját, hogy az más porton figyeljen.  

    #### <a name="to-configure-the-windows-deployment-services-server-to-listen-on-a-different-port"></a>A Központi Windows-telepítési szolgáltatások kiszolgálójának konfigurálása, hogy más porton figyeljen  

    1.  Módosítsa a következő beállításkulcsot:  

         **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE**  

    2.  A beállításjegyzék-értékben beállítani: **UseDHCPPorts = 0**  

    3.  Az új konfigurálás érvénybe lépéséhez futtassa a kiszolgálón a következő parancsot:  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   A Központi Windows-telepítési szolgáltatások futtatáshoz DNS kiszolgáló szükséges.  

-   A Központi Windows-telepítési szolgáltatások kiszolgálóján a következő UDP portoknak kell nyitva lenni.  

    -   67-es port (DHCP)  

    -   69-es port (TFTP)  

    -   4011-es port (PXE)  

    > [!NOTE]  
    >  Ezen kívül, ha a kiszolgálón DHCP hitelesítésre van szükség, a DHCP 68-as ügyfélportját is meg kell nyitni a kiszolgálón.  

##  <a name="BKMK_SupportedOS"></a> Támogatott operációs rendszerek  
 Összes Windows operációs rendszer tulajdonosaként támogatott ügyféloldali operációs rendszerként [ügyfelek és eszközök támogatott operációs rendszerekről](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) támogatottak az operációs rendszer központi telepítése.  

##  <a name="BKMK_SupportedDiskConfig"></a> Támogatott lemezkonfigurációk  
 A merevlemez-konfigurációkat támogat a referencia- és célszámítógépek számítógépek által támogatott operációs rendszer telepítése a Configuration Manager a következő táblázatban láthatók.  

|Referencia-számítógép merevlemez-konfigurációja|Célszámítógép merevlemez-konfigurációja|  
|------------------------------------------------|--------------------------------------------------|  
|Egyszerű lemez|Egyszerű lemez|  
|Egyszerű kötet dinamikus lemezen|Egyszerű kötet dinamikus lemezen|  

 A Configuration Manager támogatja, csak az egyszerű kötetekkel konfigurált számítógépekről egy operációsrendszer-lemezképek rögzítését. A következő merevlemez-konfigurációk nem támogatottak:  

-   Átnyúló kötetek  

-   Csíkozott kötetek (RAID 0)  

-   Tükrözött kötetek (RAID 1)  

-   Paritásos kötetek (RAID 5)  

 Az alábbi táblázat mutatja be egy további merevlemez-konfigurációját a referencia- és célszámítógépeket, amelyet nem támogatott, ha a Configuration Manager operációs rendszerek központi telepítéséhez.  

|Referencia-számítógép merevlemez-konfigurációja|Célszámítógép merevlemez-konfigurációja|  
|------------------------------------------------|--------------------------------------------------|  
|Egyszerű lemez|Dinamikus lemez|  

## <a name="next-steps"></a>További lépések
[Operációs rendszer központi telepítésének előkészítése](../get-started/prepare-for-operating-system-deployment.md)

