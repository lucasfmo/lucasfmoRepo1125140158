---
title: "Támogatott ügyfelek és eszközök |} Microsoft Docs"
description: "Ismerje meg, mely operációs rendszerek System Center Configuration Manager támogatja az ügyfelek és eszközök."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: 5
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: cd7b8bf35aeb26c8b7b37f6faa51c9a09138fdb9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>Az ügyfelek és eszközök a System Center Configuration Manager támogatott operációs rendszerek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A System Center Configuration Manager támogatja a Windows, Mac, Linux és UNIX rendszerű számítógépek a különböző ügyfélszoftver telepítését.  

 **Követelmények és korlátozások az összes ügyfél:**  

-   Az indítási típus módosítása vagy **jelentkezzen be** beállításait a Configuration Manager szolgáltatás nem támogatott, és előfordulhat, hogy a kulcs szolgáltatások nem fognak megfelelően futni.    

-   Telepítése vagy a Configuration Manager-ügyfél Linux vagy UNIX- vagy Mac ügyfelet a számítógépeken futó olyan fiókkal eltérő gyökér nem támogatott. Így előfordulhat, hogy fontos szolgáltatások nem fognak megfelelően futni.  

##  <a name="windows-computers"></a>Windows rendszerű számítógépek  
 A Configuration Manager-ügyfél a Configuration Manager kezelje a következő Windows operációs rendszerek részét képező is használhatja. További információkért lásd: [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

**Támogatott operációs rendszerek esetén:**  


-  **Windows Server 2016**: Standard, Datacenter <sup>1</sup>
  - Az operációs rendszer támogatott verziótól kezdve a Configuration Manager verziója 1606, a gyorsjavítás összesítő KB3186654 (vagy 1606, az Alapverzió október 2016 kiadott).  

-   **Windows Server 2012 R2** (x64): Standard, Datacenter <sup>1</sup>    

-   **A Windows Storage Server 2012 R2** (x64)    

-   **A Windows Server 2012** (x64): Standard, Datacenter <sup>1</sup>    

-   **A Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 SP1** (x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **A Windows Storage Server 2008 R2** (x86, x64): Workgroup, Standard, Enterprise    

-   **Windows Server 2008 SP2** (x86, x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows 10**: Pro, Enterprise  
   Lásd: [a Windows 10-verziók támogatási](/sccm/core/plan-design/configs/support-for-windows-10) a különböző vonatkozó további információért kiadás a Windows 10-es verziói, a Configuration Manager különböző verziói által támogatott.

-   **Windows 8.1** (x86, x64): Professional, Enterprise    

-   **Windows 8** (x86, x64): Professional, Enterprise    

-   **Windows 7 SP1** (x86, x64): Professional, Enterprise és Ultimate    

-   **A Server Core telepítési lehetőség Windows Server 2016** (x64) <sup>2</sup>
  - Az operációs rendszer verziójától 1606 a gyorsjavítás összesítő KB3186654 (vagy 1606, az Alapverzió 2016. októberi kiadott) támogatott. 


-   **A Server Core telepítési lehetőség Windows Server 2012 R2** (x64) <sup>2</sup>    

-   **A Server Core telepítési lehetőség Windows Server 2012** (x64) <sup>2</sup>    

-   **A Server Core telepítési lehetőség Windows Server 2008 R2**  
    **(szervizcsomag nélkül vagy SP1 szervizcsomaggal)**  (x64)    

-   **A Server Core telepítési lehetőség Windows Server 2008 SP2** (x86, x64)  

 <sup>1</sup> Datacenter kiadásait támogatja, de nincsen tanúsítva a Configuration Manager. Gyorsjavítási támogatás van nem érhető el a Windows Server Datacenter Edition kapcsolatos problémákat.  

 <sup>2</sup> ügyfélleküldéses telepítés támogatásához az operációs rendszert futtató számítógépen kell futtatnia a Fájlkiszolgáló szerepkör-szolgáltatást a fájl- és tárolási szolgáltatások kiszolgálói szerepkör. További információ a Windows-szolgáltatások telepítése Server Core számítógépre: [kiszolgálói szerepkörök és szolgáltatások telepítése Server Core kiszolgálón](http://go.microsoft.com/fwlink/p/?LinkId=299359) a Windows Server 2012 TechNet könyvtárban.  


##  <a name="windows-embedded-computers"></a>Windows Embedded-számítógépekre  
 A Windows Embedded-eszközök kezeléséhez az eszköz a Configuration Manager ügyfélszoftver telepítését.  További információkért lásd: [tervezése a System Center Configuration Manager Windows Embedded-eszközökre történő központi ügyféltelepítésre](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

**Követelmények és korlátozások:**  

-   Minden ügyfélfunkciót Windows Embedded rendszerek, amelyeken nincs engedélyezett írási szűrőkkel támogatottak.  

-   Az alábbi használó ügyfelek az energiaoptimalizálás kivételével minden funkció támogatja:  

    -   Speciális írási szűrők (EWF)    

    -   RAM fájlalapú írási szűrőt (FBWF)    

    -   Egyesített írási szűrők (UWF)  

-   Az Alkalmazáskatalógus nem támogatott Windows Embedded-eszközök.  

-   Windows Embedded-eszközök a Windows XP alapuló az észlelt kártevők megfigyeléséhez, telepítenie kell a Microsoft Windows WMI parancsprogramcsomagot az eszközön. Ez a csomag telepítése a Windows Embedded Target Designer használatával.
A fájlok **WBEMDISP. DLL** és **WBEMDISP. TLB** léteznie kell, és a mappa regisztrációja **%windir%\System32\WBEM** a beágyazott eszköz győződjön meg arról, hogy az észlelt kártevők jelentéséhez.  

**Támogatott operációs rendszerek esetén:**  

-   **Windows 10 Enterprise** (x86, x64)  

-   **Windows 10 IoT vállalati** (x86, x64)  

-   **Windows Embedded 8.1 Industry** (x86, x64)    

-   **Windows 8 iparági beágyazott** (x86, x64)    

-   **Windows 8 Standard beágyazott** (x86, x64)    

-   **Windows 8 Pro beágyazott** (x86, x64)    

-   **A Windows dinamikus PC** (x86, x64)    

-   **Windows Embedded POSReady 7** (x86, x64)    

-   **Windows Embedded Standard 7 SP1** (x86, x64)    

-   **WEPOS 1.1 SP3 szervizcsomaggal** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Windows Fundamentals for Legacy PCs (WinFLP)** (x86)    

-   **Windows XP SP3 beágyazott** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce-computers"></a>Windows CE rendszerű számítógépek
 Windows CE rendszerű eszközöket szeretne felügyelni a Configuration Manager mobileszközön lévő korábbi ügyfél a Configuration Managerben is megtalálható.  

**Követelmények és korlátozások**  

-   A mobileszközügyfél telepítéséhez 0,78 MB tárolóhely szükséges. Bejelentkezési legfeljebb 256 KB tárolóhelyre lehet szükség.    

-   A mobileszközök platform és ügyféltípus szerint változnak a szolgáltatások típusát. Mely felügyeleti funkciók támogatott információkért lásd: [eszköz megoldás választása a System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md).  

**Támogatott operációs rendszerek esetén:**  

-   Windows CE 7.0 (ARM és x86 processzorok)  

**Támogatott nyelvek:**  

-   Kínai (egyszerűsített és hagyományos)    

-   Angol (US)    

-   Francia (Franciaország)    

-   Német    

-   Olasz    

-   Japán  

-   koreai  

-   Portugál (brazíliai)  

-   Orosz  

-   Spanyol (Spanyolország)  

## <a name="mac-computers"></a>Mac számítógépek  
 Mac OS X rendszerű számítógépek kezelése a Configuration Manager-ügyfél for Mac csomagokkal.  

 A Mac ügyfél-telepítési csomag nem rendelkezik a Configuration Manager adathordozóján. Töltse le a **ügyfelek egyéb operációs rendszerekhez** a a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

 További információkért lásd: [ügyfélszoftverek központi telepítése Mac-számítógépekre a System Center Configuration Managerben](../../../core/clients/deploy/deploy-clients-to-macs.md).  

**Támogatott verziók:**  

-   **Mac OS X 10.6** (Hópárduc)

-   **Mac OS X 10.7** (Lion)

-   **Mac OS X 10.8** (Mountain Lion)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.10 rendszert** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)

##  <a name="linux-and-unix-servers"></a>Linux és UNIX rendszerű kiszolgálók  
 A Configuration Manager-ügyfél Linux és UNIX rendszerű kiszolgálók kezelhető a Linux és UNIX rendszerű.  

 Csomag a Linux és UNIX rendszerű ügyfél telepítése nem a Configuration Manager adathordozóján található meg. Töltse le a **ügyfelek egyéb operációs rendszerekhez** a a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Ügyféltelepítési csomag mellett a letölthető ügyfél magában foglalja a parancsfájl, amely minden számítógépen az ügyfél telepítését felügyeli.  

**Követelmények és korlátozások:**  

-   Operációs rendszer fájlfüggőségeiről az ügyfél Linux és UNIX rendszerű ellenőrzéséhez tekintse meg [ügyféltelepítés előfeltételei a Linux és UNIX rendszerű kiszolgálók](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU).  

-   A Linux vagy UNIX támogatott felügyeleti képességek áttekintéséhez lásd: [üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Manager ügyfelek](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

-   Linux és UNIX támogatott verzióit az itt említett verzió magában foglalja a minden későbbi alverziót. Például a CentOS 6-os verziójú CentOS 6.3 tartalmazza. Ehhez hasonlóan támogatása az operációs rendszer, hogy a szervizcsomagok által használt (például a SUSE Linux Enterprise Server 11 SP1) operációs rendszer verziójának későbbi szervizcsomagokat tartalmaz.  

-   További információ az ügyfél-telepítési csomagokról és az univerzális ügynökről: [üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Manager ügyfelek](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

**Támogatott verziók:** A következő verziók támogatottak a jelzett .tar fájl használatával.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|Verzió (Power) 5.3|CCM-Aix53ppc. &lt;build\>.tar|  
|Verzió 6.1 (Power)|CCM-Aix61ppc. &lt;build\>.tar|  
|Verzió 7.1 (Power)|CCM-Aix71ppc. &lt;build\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|Verzió 6 x 86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|8-as verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|8-as verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|11iv2 IA64 verzió|CCM-HpuxB.11.23i64. &lt;build\>.tar|  
|11iv2 PA-RISC verzió|CCM-HpuxB.11.23PA. &lt;build\>.tar|  
|11iv3 IA64 verzió|CCM-HpuxB.11.31i64. &lt;build\>.tar|  
|11iv3 PA-RISC verzió|CCM-HpuxB.11.31PA. &lt;build\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|4. verziójú x86|CCM-RHEL4x86. &lt;build\>.tar|  
|4. verziójú x64|CCM-RHEL4x64. &lt;build\>.tar|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|9-es verzió SPARC|CCM-Sol9sparc. &lt;build\>.tar|  
|10-es verzió x86|CCM-Sol10x86. &lt;build\>.tar|  
|10-es verzió SPARC|CCM-Sol10sparc. &lt;build\>.tar|  
|11-es verzió x86|CCM-Sol11x86. &lt;build\>.tar|  
|11-es verzió SPARC|CCM-Sol11sparc. &lt;build\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|9-es verzió x86|CCM-SLES9x86. &lt;build\>.tar|  
|10-es verzió SP1 x86|CCM-Universalx86. &lt;build\>.tar|  
|10-es verzió SP1 x64|CCM-Universalx64. &lt;build\>.tar|  
|11-es verzió SP1 x86|CCM-Universalx86. &lt;build\>.tar|  
|11-es verzió SP1 x64|CCM-Universalx64. &lt;build\>.tar|  
|12-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|Verzió 10.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 10.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  
|Verzió 12.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 12.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  
|Verzió 14.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 14.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  

##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>A Microsoft Intune által beléptetett mobileszközök  
 A számítógépek és eszközök, amelyek segítségével kezelheti a Microsoft Intune a Configuration Manager integrációjához részletekért lásd: a Microsoft Intune dokumentációs könyvtárában a következő két témakörök:  

-   [A Microsoft Intune mobileszköz-kezelési képességei](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [A Microsoft Intune Windows-számítógépek felügyeletére szolgáló képességei](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a>A helyszíni mobileszköz-kezelés  
 A Configuration Manager ügyfélszoftver telepítése nélküli helyszíni eszközök felügyelete a beépített funkciókkal rendelkezik.  További információkért lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Követelmények és korlátozások:**  

-   Konfigurálnia kell a **szolgáltatáskapcsolódási pont** a hierarchia legfelső szintű helyén.  

**Támogatott operációs rendszerek esetén:**  

- **Windows 10 Pro** (x86, x64)  

- **Windows 10 Pro Enterprise** (x86, x64)  

- **Windows 10 IoT vállalati** (x86, x64)

- **A Windows 10 Mobile**  

- **Windows 10 mobil vállalati**  

- **Windows 10 IoT Mobile Enterprise**

- **Windows 10 Team felület központ**

##  <a name="bkmk_ExSrvConOS"></a>Exchange Server-összekötő  
A Configuration Manager korlátozott funkciókkal eszközöket, amelyek az Exchange-kiszolgálóhoz kapcsolódnak a Configuration Manager-ügyfél telepítése nélkül. További információkért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

 **Követelmények és korlátozások:**  

-   A Configuration Manager mobileszközök korlátozott felügyeletét nyújtja, eszközök használatakor az Exchange Server-összekötő az Exchange Server vagy Exchange Online futtató kiszolgálóhoz csatlakozó Exchange Active Sync.  

-   További információ arról, hogy mely felügyeleti funkciót biztosít a Configuration Manager támogatja azokról az eszközökről, az Exchange Server-összekötővel kezeli, határozza meg arról, hogy mobileszközök kezelése a Configuration Manager:.  

**Az Exchange Server támogatott verziói:**  

-   **Exchange Server 2010 SP1**  

-   **Az Exchange Server 2010 SP2**  

-   **Exchange Server 2013**  

-   **Az Exchange Online (Office 365)**: Ez magában foglalja a Business Productivity Online Standard Suite csomagot  

