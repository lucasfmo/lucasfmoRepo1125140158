---
title: "Támogatott konfigurációk a LTSB |} Microsoft Docs"
description: "Ismerje meg, milyen operációs rendszerek és a függő termékek működik együtt a hosszú távú karbantartási ág a System Center Configuration Manager."
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ec33d5febcbf7b57e220f7fe27db9671080fecff
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>A hosszú távú karbantartási ág a System Center Configuration Manager támogatott konfigurációk

*Vonatkozik: A System Center Configuration Manager (hosszú távú karbantartási ág)*

Olvassa el ebben a témakörben milyen operációs rendszerek és a termék függőségek által a hosszú távú karbantartási ág (LTSB) a Configuration Manager támogatott.
Ha nincs másként ez vagy a LTSB meg adott témákat, ugyanazokat a konfigurációkat és az aktuális ág verzió 1606 vonatkozó korlátozások vonatkoznak a LTSB.  Akkor történik ütközés, használja a kiadásra vonatkozó információkat. A LTSB általában korlátozottabb, mint az aktuális ág.

## <a name="general-statement-of-support"></a>Általános utasítás támogatás
A következő termékeket és technológiákat a Configuration Manager fiókirodai támogatja. Azonban a tartalom felvételükről nem terjed ki a bármely termék vagy a verzió túl a termék egyes támogatási életciklusa támogatása. Terméktámogatási ciklusukon túllépett termékek esetében nem támogatottak a Configuration Managerrel történő használathoz. További tudnivalókért keresse fel a [Microsoft terméktámogatási ciklus](http://go.microsoft.com/fwlink/p/?LinkId=208270) webhelyet, és olvassa el a [a Microsoft támogatási életciklusra vonatkozó házirend gyakori Kérdéseinek](http://go.microsoft.com/fwlink/p/?LinkId=31976).

Emellett termékek és termékverziók, amelyek nem szerepelnek a következő témakörök akkor támogatott, ha a bejelentette a [Enterprise Mobility + Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/).

**Jövőbeli támogatási vonatkozó korlátozások:** A LTSB korlátozott mértékben támogatja a jövőbeli kiszolgáló és az ügyféloldali operációs rendszerek és a termék függőségek. A platformok listája a LTSB rögzített a kiadás során:

**Windows:**
- Csak Windows minőségének és biztonságának frissítések támogatottak.
- Nem támogatja az aktuális ágak (CB), üzleti (CBB), vagy a LTSB Windows 10 aktuális ágak.
-    A Windows Server új fő verziói nem támogatottak.

**SQL Server:**
- SQL Server csak a minőségi és biztonsági frissítések vagy szervizcsomagok, mint a kisebb frissítések esetén támogatott.
- SQL Server új fő verziói nem támogatottak.  

## <a name="site-systems-and-servers"></a>Helyrendszerek és -kiszolgálók
A LTSB használatát a következő Windows-számítógép operációs rendszereket támogatja a helyrendszerek között.  Minden operációs rendszer rendelkezik a azonos követelményei és korlátozásai a ugyanazon belépési [támogatott operációs rendszerek helyrendszer-kiszolgálók](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  Például a Server Core telepítési lehetőség Windows 2012 R2 kell lennie egy x64 verzió, csak akkor támogatott a terjesztési pont futtatásához, és nem támogatja a PXE vagy csoportos küldést.

**Támogatott operációs rendszerek esetén:**
- Windows Server 2016
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 SP1 (x 64): Standard, Enterprise, Datacenter
- Windows Server 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter *(lásd: 1. megjegyzés)*
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- A Server Core telepítési lehetőség Windows Server 2012
- A Server Core telepítési lehetőség Windows Server 2012 R2    

*Megjegyzés: 1*: Ez az operációs rendszer nem támogatott a helykiszolgálókon vagy helyrendszer-szerepkörök a terjesztési pont és a lekéréses terjesztési pontok kivételével. Továbbra is használható az operációs rendszer terjesztési pontként, amíg ez a támogatás elavulásának bejelentéséig, illetve az operációs rendszer kiterjesztett támogatási időszakának lejártáig. További információkért lásd: [a System Center Configuration Manager CB telepítési és LTSB nem sikerül, a Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="client-management"></a>Ügyfélfelügyelet
Az alábbi szakaszok ismertetik az ügyféloperációs-rendszereket, amelyek a LTSB a kezelhető. A LTSB nem támogatja az új operációs rendszerek támogatott ügyfélként hozzáadását.

### <a name="windows-computers"></a>Windows rendszerű számítógépek
A LTSB segítségével kezelheti a következő Windows számítógép operációs rendszerek és a Configuration Manager ügyfélszoftver, a Configuration Managerben is megtalálható. További információkért lásd: [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

**Támogatott operációs rendszerek esetén:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter (1. megjegyzés)
- Windows Server 2012 (x 64): Standard, Datacenter (1. megjegyzés)
- A Windows Storage Server 2012 R2 (x 64)
- A Windows Storage Server 2012 (x 64)
- Windows Server 2008 R2 SP1 (x 64): Standard, Enterprise, Datacenter (1. megjegyzés)
- A Windows Storage Server 2008 R2 (x 86, x 64): Workgroup, Standard, Enterprise
- Windows Server 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter (1. megjegyzés)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- A Server Core telepítési lehetőség Windows Server 2012 R2 (x64) (2. megjegyzés)
- A Server Core telepítési lehetőség Windows Server 2012 (x64) (2. megjegyzés)
- A Server Core telepítési lehetőség Windows Server 2008 R2 SP1 (x64)
- A Server Core telepítési lehetőség Windows Server 2008 SP2 (x86, x64)

**(1. megjegyzés)**  Datacenter kiadásait támogatja, de nincsen tanúsítva a Configuration Manager.  
**(2. megjegyzést)**  Ügyfélleküldéses telepítés támogatásához az operációs rendszert futtató számítógépen kell futtatnia a Fájlkiszolgáló szerepkör-szolgáltatást a fájl- és tárolási szolgáltatások kiszolgálói szerepkör. További információ a Windows-szolgáltatások telepítése Server Core számítógépre: [kiszolgálói szerepkörök és szolgáltatások telepítése Server Core kiszolgálón](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx) a Windows Server 2012 TechNet könyvtárában.

### <a name="windows-embedded"></a>Windows Embedded
A LTSB használatával a kliens szoftver telepítése az eszközön a következő Windows Embedded-eszközök kezeléséhez.  További információkért lásd: [tervezése a System Center Configuration Manager Windows Embedded-eszközökre történő központi ügyféltelepítésre](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

**Követelmények és korlátozások:**  

-   Minden ügyfélfunkciót a támogatott Windows Embedded rendszerek, amelyeken nincs engedélyezett írási szűrőkkel támogatottak.  

-   Az alábbi használó ügyfelek az energiaoptimalizálás kivételével minden funkció támogatja:  

    -   Speciális írási szűrők (EWF)    

    -   RAM fájlalapú írási szűrőt (FBWF)    

    -   Egyesített írási szűrők (UWF)  

-   Az Alkalmazáskatalógus nem támogatott Windows Embedded-eszközök.  

-   Windows XP-alapú Windows Embedded-eszközökön az észlelt kártevők megfigyeléséhez, telepítenie kell a Microsoft Windows WMI parancsprogramcsomagot a beágyazott eszköz. Ez a csomag telepítése a Windows Embedded Target Designer használatával. A *WBEMDISP. DLL* és *WBEMDISP. TLB* fájlok létezése és regisztrálni kell a beágyazott eszköz győződjön meg arról, hogy az észlelt kártevők jelentéséhez %windir%\System32\WBEM mappájába.  

**Támogatott operációs rendszerek esetén:**  
-   Windows 10 Enterprise 2016 LTSB (x86, x64)  
-   Windows 10 Enterprise 2015 LTSB (x86, x64)  
-   Windows Embedded 8.1 Industry (x86, x64)    
-   Windows vékony PC (x86, x64)    
-   Windows Embedded POSReady 7 (x86, x64)    
-   Windows Embedded Standard 7 SP1 (x 86, x 64)    
-   Windows Embedded POSReady 2009 (x86)   
-   Windows Embedded Standard 2009 (x86)  

### <a name="windows-ce"></a>Windows CE  
 Windows CE rendszerű eszközöket szeretne felügyelni a Configuration Manager mobileszközön lévő korábbi ügyfél a Configuration Managerben is megtalálható.  

**Követelmények és korlátozások:**  

-   A mobileszközön lévő ügyfél 0,78 MB tárolóhely az ügyfél telepítéséhez szükséges. A mobileszköz legfeljebb 256 KB tárolóhelyre jelentkezhet be lehet szükség.    

-   A mobileszközök platform és ügyféltípus szerint változnak a szolgáltatások típusát. Milyen típusú, amely a mobileszközön lévő korábbi ügyfél támogatja a Configuration Manager felügyeleti funkciók kapcsolatos információkért lásd: [eszköz megoldás választása a System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

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

### <a name="mac-computers"></a>Mac számítógépek  
 A LTSB segítségével Mac OS X rendszerű számítógépek kezelése a Configuration Manager-ügyfél for Mac csomagokkal.

A Mac ügyfél-telepítési csomag nem rendelkezik a Configuration Manager adathordozóján. Letöltheti a "ügyfelek egyéb operációs rendszerekhez készült" letölthető részeként a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

Mac operációs rendszerek támogatása csak azok a jelen szakaszban felsorolt. Támogatás nem tartalmazza az egyéb operációs rendszerekhez, előfordulhat, hogy támogatni a Mac ügyfél-telepítési csomagokat egy következő frissítés az aktuális ág.

További információkért lásd: [ügyfélszoftverek központi telepítése Mac-számítógépekre a System Center Configuration Managerben](/sccm/core/clients/deploy/deploy-clients-to-macs).

**Támogatott verziók:**  
-   Mac OS X 10.9 (Mavericks)  
-   Mac OS X 10.10 (Yosemite)  
-   Mac OS X 10.11 (El Capitan)  

## <a name="linux-and-unix-servers"></a>Linux és UNIX rendszerű kiszolgálók
A LTSB segítségével a Configuration Manager-ügyfél Linux és UNIX rendszerű kiszolgálók felügyelt Linux és UNIX rendszerekhez készült.

A Linux és UNIX rendszerű ügyfél-telepítési csomagokat nem rendelkeznek a Configuration Manager adathordozóján. Letöltheti azokat a "ügyfelek egyéb operációs rendszerekhez készült" letölthető részeként a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Ügyféltelepítési csomag mellett a letölthető ügyfél tartalmazza a telepítési parancsfájl, amely minden számítógépen az ügyfél telepítését felügyeli.

Linux és UNIX operációs rendszerek támogatása csak azok a jelen szakaszban felsorolt. Támogatás nem tartalmazza az egyéb operációs rendszerekhez, előfordulhat, hogy támogatni a jövőbeni frissítése Linux és UNIX rendszerű ügyfél csomagokat az aktuális ág.

**Követelmények és korlátozások:**  

-   Operációs rendszer fájlfüggőségeiről az ügyfél Linux és UNIX rendszerű ellenőrzéséhez tekintse meg [ügyféltelepítés előfeltételei a Linux és UNIX rendszerű kiszolgálók](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu).  
-   A Linux vagy UNIX rendszert futtató számítógépeken támogatott felügyeleti képességek áttekintéséhez lásd: [üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Manager ügyfelek](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).  
-   Linux és UNIX támogatott verzióit az itt említett verzió magában foglalja a minden későbbi alverziót. Például 6-os verziójú CentOS támogatási jelzett ez is egyetlen követő alverziója a CentOS 6, például a CentOS 6.3. Hasonlóképpen ha támogatása az operációs rendszer által használt szervizcsomagok, például a SUSE Linux Enterprise Server 11 SP1 támogatási operációs rendszer verziójának későbbi szervizcsomagokat tartalmaz.
-   További információ az ügyfél-telepítési csomagokról és az univerzális ügynökről: [üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Manager ügyfelek](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).


**Támogatott verziók:**   
A következő verziók támogatottak a jelzett .tar fájl használatával.  
### <a name="aix"></a>AIX  

|Verzió|Fájl|  
|-|-|  
|5.3-as (Power) verzió|CCM-Aix53ppc. &lt;build\>.tar|  
|Verzió 6.1 (Power)|CCM-Aix61ppc. &lt;build\>.tar|  
|Verzió 7.1 (Power)|CCM-Aix71ppc. &lt;build\>.tar|  

### <a name="centos"></a>CentOS  

|Verzió|Fájl|  
|-|-|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="debian"></a>Debian  

|Verzió|Fájl|    
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

|Verzió|Fájl|  
|-|-|  
|11iv2 IA64 verzió|CCM-HpuxB.11.23i64. &lt;build\>.tar|  
|11iv2 PA-RISC verzió|CCM-HpuxB.11.23PA. &lt;build\>.tar|  
|11iv3 IA64 verzió|CCM-HpuxB.11.31i64. &lt;build\>.tar|  
|11iv3 PA-RISC verzió|CCM-HpuxB.11.31PA. &lt;build\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|Verzió|Fájl|    
|-|-|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Verzió|Fájl|  
|-|-|  
|4. verziójú x86|CCM-RHEL4x86. &lt;build\>.tar|  
|4. verziójú x64|CCM-RHEL4x64. &lt;build\>.tar|  
|5-ös verzió x86|CCM-Universalx86. &lt;build\>.tar|  
|5-ös verzió x64|CCM-Universalx64. &lt;build\>.tar|  
|6-os verziójának x86|CCM-Universalx86. &lt;build\>.tar|  
|6-os verziójának x64|CCM-Universalx64. &lt;build\>.tar|  
|7-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="solaris"></a>Solaris  

|Verzió|Fájl|   
|-|-|  
|9-es verzió SPARC|CCM-Sol9sparc. &lt;build\>.tar|  
|10-es verzió x86|CCM-Sol10x86. &lt;build\>.tar|  
|10-es verzió SPARC|CCM-Sol10sparc. &lt;build\>.tar|  
|11-es verzió x86|CCM-Sol11x86. &lt;build\>.tar|  
|11-es verzió SPARC|CCM-Sol11sparc. &lt;build\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|Verzió|Fájl|  
|-|-|  
|9-es verzió x86|CCM-SLES9x86. &lt;build\>.tar|  
|10-es verzió SP1 x86|CCM-Universalx86. &lt;build\>.tar|  
|10-es verzió SP1 x64|CCM-Universalx64. &lt;build\>.tar|  
|11-es verzió SP1 x86|CCM-Universalx86. &lt;build\>.tar|  
|11-es verzió SP1 x64|CCM-Universalx64. &lt;build\>.tar|  
|12-es verzió x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|Verzió|Fájl|    
|-|-|  
|Verzió 10.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 10.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  
|Verzió 12.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 12.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  
|Verzió 14.04 LTS x86|CCM-Universalx86. &lt;build\>.tar|  
|Verzió 14.04 LTS x64|CCM-Universalx64. &lt;build\>.tar|  

### <a name="exchange-server-connector"></a>Exchange Server-összekötő
 A LTSB korlátozott funkciókkal az eszközről, amelyen az ügyfélszoftver telepítése nélküli csatlakozás az Exchange Server-példányt. További információkért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync).

 **Követelmények és korlátozások:**  

-   A Configuration Manager mobileszközök korlátozott felügyeletét nyújtja. Korlátozott felügyelet az Exchange Server-összekötőt használhatja az Exchange Server vagy Exchange online-hoz csatlakozó Exchange Active Sync (EAS) kompatibilis eszközök esetén érhető el.  

-   A Configuration Manager által támogatott az Exchange Server-összekötő által felügyelt mobileszközök kezelési funkciók kapcsolatos további információkért lásd: [eszköz megoldás választása a System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Az Exchange Server támogatott verziói:**  
-   Exchange Server 2010 SP1  
-   Az Exchange Server 2010 SP2  
-   Exchange Server 2013  

> [!NOTE]
> A LTSB nem támogatja az online szolgáltatásként működik, mint például az Exchange Online (Office 365) keresztül csatlakozó eszközök kezeléséhez.


## <a name="configuration-manager-console"></a>Configuration Manager-konzol
A LTSB a Configuration Manager konzol futtatása a következő operációs rendszereket támogatja. Minden olyan számítógépen, amelyre a konzol 4.5.2, kivéve a Windows 10, amely szükséges a .NET-keretrendszer 4.6 legalább a .NET-keretrendszer verzióját kell rendelkeznie.

**Támogatott operációs rendszerek esetén:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 SP1 (x 64): Standard, Enterprise, Datacenter
- Windows Server 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 SP1 (x 86, x 64): Professional, Enterprise, Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>A Helyadatbázis és a jelentéskészítési pont támogatott SQL Server-verziók
A LTSB a Helyadatbázis és a jelentéskészítési pont üzemeltetésére szolgáló SQL Servert a következő verzióit támogatja. Az egyes támogatott verziója, a azonos konfigurációs követelmények és korlátozások megjelenő [SQL Server-verziók támogatása](/sccm/core/plan-design/configs/support-for-sql-server-versions) aktuális ágának a LTSB vonatkozik.  Ez magában foglalja az SQL Server-fürt, vagy egy SQL Server AlwaysOn rendelkezésre állási csoport használata.  

**Támogatott verziók:**

- SQL Server 2016: Standard, Enterprise
- Az SQL Server 2014 SP2: Standard, Enterprise
- SQL Server 2014 SP1: Standard, Enterprise
- SQL Server 2012 SP3: Standard, Enterprise
- SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter
- Az SQL Server 2016 Express
- Az SQL Server 2014 expressz SP2
- SQL Server 2014 Express SP1
- SQL Server 2012 Express SP3

## <a name="support-for-active-directory-domains"></a>Az Active Directory-tartományok támogatása
Az összes LTSB-helyrendszer egy támogatott Windows Active Directory-tartomány tagjának kell lennie. Az Active Directory-tartomány támogatása a azonos követelményeket és korlátozásokat az látható, amely rendelkezik [Active Directory-tartományok támogatása](/sccm/core/plan-design/configs/support-for-active-directory-domains), de a következő tartományi funkcionális szintű korlátozódik:

**Támogatott szintek:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>További támogatási témakörök, amelyek érvényesek a hosszú távú karbantartási ág
A következő aktuális ág témakörökben található információk a LTSB vonatkoznak:
- [Méret és skálázási számok](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [Hely és hely rendszer Előfeltételek](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [Magas rendelkezésre állású lehetőség](/sccm/protect/understand/high-availability-options)
- [Ajánlott hardver](/sccm/core/plan-design/configs/recommended-hardware)
- [Windows-szolgáltatások és -hálózatok támogatása](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [Virtualizálási környezetek támogatása](/sccm/core/plan-design/configs/support-for-virtualization-environments)

