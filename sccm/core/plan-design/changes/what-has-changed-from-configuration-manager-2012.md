---
title: "A Configuration Manager 2012-ről változik |} Microsoft Docs "
description: "A módosítások és a System Center Configuration Manager és a System Center 2012 Configuration Manager új képességei azonosítása."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
caps.latest.revision: 51
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 0a3eb93a99533a1569d8f72ca01d6dfcdc75da20
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="what39s-changed-in-system-center-configuration-manager-from-system-center-2012-configuration-manager"></a>Mi &#39; s megváltozott a System Center Configuration Manager a System Center 2012 Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A System Center Configuration Manager aktuális ágának a System Center 2012 Configuration Manager olyan fontos módosításait. Ez a témakör ismerteti a jelentős változtatások és az eredeti 1511-es verzió a System Center Configuration Manager új képességei. A System Center Configuration Manager soron következő frissítések bevezetett változások kapcsolatos további tudnivalókért lásd: [What's new in System Center Configuration Manager növekményes verzióját](/sccm/core/plan-design/changes/whats-new-incremental-versions).



 A 2015. decemberi kiadása a System Center Configuration Manager (1511-es verzió) történt a jelenlegi Configuration Manager terméket a Microsoft eredeti kiadását. Ez általában nevezzük System Center Configuration Manager aktuális ágának. *Aktuális ág* azt jelzi, hogy ez a verziója, amely támogatja a termék növekményes frissítéseit. A kiadási és a korábbi kiadásokban a Configuration Manager megkülönböztetésére úgy is tartalmazza.  

 A System Center Configuration Manager:  

-   A termék nevét, például a Configuration Manager 2007 vagy System Center 2012 Configuration Manager korábbi verzióival ellentétben a nem használ évet vagy termékazonosítót azonosítója.

-   Támogatja a növekményes, a terméken belüli frissítéseket, más néven frissítési verziókat. Az eredeti kiadásának verziója 1511-es volt. Későbbi verziói konzolon belüli frissítések hasonlóan 1610 többször egy év kiadásakor.
-   Egy alapkonfiguráció verziójával van telepítve. Az eredeti alapkonfiguráció 1511-es állapotában alapkonfiguráció új verzióit is kiadott időnként, például 1702. Alapverziók egy új System Center Configuration Manager-hely és a hierarchia telepítéséhez vagy frissítéséhez a Configuration Manager 2012 támogatott verziójából származó használható.




##  <a name="bkmk_updates"></a> A Configuration Manager konzolon belüli frissítései  
 A System Center Configuration Manager egy nevű konzolon belüli szolgáltatási metódust használ **frissítés és karbantartás** megkeresheti és telepítheti az ajánlott frissítéseket is, amely megkönnyíti.  

 Egyes verziói csak meglévő helyek frissítésére használhatók (a a Configuration Manager konzolon), és nem használható új Configuration Manager-helyek telepítéséhez.   
Például a 1610 update csak egy érhető el a Configuration Manager konzolon. Segítségével, amely már egy olyan futtat a System Center Configuration Manager hely frissítése.

Egy frissítési verzió új verziójú alapkonfigurációként (ilyen például a frissítés 1702) néven rendszeres időközönként is kiadott. Az ilyen típusú frissítés telepítése egy új hierarchia, anélkül, hogy egy régebbi Alapverzió (például 1511-es) kezdődnie, és frissítse a legújabb verzióra a módon használható.


Frissítések használatával kapcsolatos további információkért lásd: [frissítések a System Center Configuration Manager](../../../core/servers/manage/updates.md).  
Baslines kapcsolatos további információkért lásd: [alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions).

##  <a name="bkmk_servicepoint"></a>Új helyrendszer-szerepkör: szolgáltatáskapcsolódási pont  
 A **Microsoft Intune-összekötő** helyébe egy új helyrendszerszerepkör, amely további funkciókat tesz lehetővé a **szolgáltatáskapcsolódási pont**. A szolgáltatáskapcsolódási pont:  

-   A Microsoft Intune-összekötő helyettesíti integrálja az Intune szolgáltatást a System Center Configuration Manager helyszíni mobileszköz-kezelés.  

-   Használható ügyfélként ponthoz-az-kezelt eszközökre.  

-   A telepítéssel kapcsolatos használati adatok feltölt a Microsoft felhőalapú szolgáltatásából.  

-   Lehetővé teszi a központi telepítés a Configuration Manager-konzolon elérhető frissítések.  

E helyrendszerszerepkör online és offline módban. További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

##  <a name="bkmk_usage"></a> Használati adatok gyűjtése  
 A System Center Configuration Manager a webhelyek és az infrastruktúra használati adatokat gyűjt. Az összeállított adatokat – elküldte a szolgáltatáskapcsolódási pont a Microsoft felhőalapú szolgáltatásából. Szükség van ahhoz, hogy az üzembe helyezéshez a Configuration Manager használt verziójára vonatkozó frissítések letöltése a Configuration Manager. A szolgáltatáskapcsolódási pont beállításakor megadhatja, hogy mindkét összegyűjtött adatok szintjét, és hogy nyújtják automatikusan (online mód) vagy manuálisan (kapcsolat nélküli módban).  

 További információkért lásd: [használati adatszintek és beállítások](../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

##  <a name="bkmk_AMT"></a> Az Intel AMT technológia (Active Management Technology) támogatása  
 A System Center Configuration Managerrel, a natív támogatást az AMT-alapú számítógépeknek a Configuration Manager konzolon belül el lett távolítva. AMT-alapú számítógépek továbbra is teljes körűen felügyelt, használatakor a [Intel SCS-bővítmény a Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). A bővítmény elérhetővé teszi a legújabb funkciókat az AMT felügyelete során a Configuration Manager áthidalja ezeket a módosításokat bevezetéséig érvényben.  

Integrált AMT eltávolítása a System Center Configuration Manager sávon kívüli felügyeleti tartalmazza. A sávon kívüli felügyeleti pont helyrendszerszerepkör már nem használható, és nem érhető el.  

Vegye figyelembe, hogy ez a változás nincs hatással a System Center 2012 Configuration Manager sávon kívüli felügyeleti.

##  <a name="bkmk_out"></a> Elavult funkciók  
 Bizonyos funkciók – például a natív [támogatása az Intel Active Management Technology (AMT)](#bkmk_AMT) rendszerű számítógépek, a Configuration Manager konzolt el lesznek távolítva. Egyéb funkciók – például a hálózati hozzáférés-védelem teljes egészében eltávolítottunk. Emellett egyes régebbi Microsoft-termékek, például a Windows Vista, Windows Server 2008 és az SQL Server 2008, már nem támogatottak.  

 Elavult szolgáltatások listáját lásd: [eltávolítva és elavult funkciók a System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 További információk a támogatott termékekről, operációs rendszerekről és konfigurációkról: [a System Center Configuration Manager által támogatott konfigurációk](../../../core/plan-design/configs/supported-configurations.md).  

## <a name="client-deployment"></a>Ügyfelek központi telepítése  
 A System Center Configuration Manager vezet be egy új funkció a Configuration Manager-ügyfél új verzióinak tesztelésére a hely többi részének az új szoftverek frissítése előtt. Beállíthat egy üzem előtti gyűjteménnyel, amelyben egy új ügyfél próbaüzemben való tesztelését. Ha elégedett az új ügyfélszoftver üzem előtti környezetben, előléptetheti az ügyfelet, hogy automatikusan frissítse az a hely többi részének az új verzióval.  

 Az ügyfelek további információkért lásd: [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

## <a name="operating-system-deployment"></a>Operációs rendszer központi telepítése  

Vegye figyelembe az operációs rendszer központi telepítéséhez a következő módosításokat:

-   A feladatütemezés létrehozása varázsló, a **frissíteni az operációs rendszer verziófrissítő csomagjának**, egy új feladatütemezés-típus érhető el. A lépések a számítógépek rendszerről Windows 7, Windows 8 vagy Windows 8.1 és Windows 10 hoz létre. További információk: [A Windows frissítése a legújabb verzióra a System Center Configuration Managerrel](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   A Windows PE társ-gyorsítótárazás már elérhető az operációs rendszerek központi telepítésekor. Az operációs rendszerek központi telepítéséhez feladatütemezést futtató számítógépek használható Windows PE társ-gyorsítótárazás egy helyi társtól (társ-gyorsítótárazási forrástól), hogy tartalmat egy terjesztési pontról történő letöltésük helyett. Így minimálisra csökkenthető a nagykiterjedésű hálózat (WAN) forgalma a helyi terjesztési pont nélküli fiókirodai forgatókönyvek esetén. További tájékoztatást [A Windows PE társ-gyorsítótárazás előkészítése a WAN-hálózati forgalom csökkentése érdekében a System Center Configuration Managerben](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic) című témakörben talál.  

-   Most már megtekintheti a állapotát a Windows szolgáltatásként a környezetben. Is létrehozhat karbantartási terveket telepítési körök kialakításához, és győződjön meg arról, hogy a Windows 10 aktuális ág a számítógépek mindig naprakészek maradjanak új buildek kiadásakor. Emellett riasztásokat is megtekinthetik, amikor a Windows 10-ügyfelek az aktuális ág (CB) vagy az aktuális ág buildjénél a támogatásuk támogatási üzleti (CBB) végéhez közelednek. További információk: [A Windows mint szolgáltatás kezelése System Center Configuration Managerrel](../../../osd/deploy-use/manage-windows-as-a-service.md).  

## <a name="application-management"></a>Alkalmazáskezelés  

Vegye figyelembe az Alkalmazáskezelés a következő módosításokat:

-   A System Center Configuration Manager lehetővé teszi az univerzális Windows Platform (UWP-) alkalmazásokat a Windows 10 és újabb rendszert futtató eszközökre. Lásd: [Windows-alkalmazások létrehozása a System Center Configuration Managerrel](../../../apps/get-started/creating-windows-applications.md).  

-   A Szoftverközpont új, modern megjelenéssel rendelkezik. Az alkalmazások lapon megjelenő korábban csak az alkalmazáskatalógusban (a felhasználók számára elérhető alkalmazások) most alkalmazások megjelenjenek a Szoftverközpontban. Lehetővé teszi több felderíthető történő központi telepítését, és a felhasználók számára az Alkalmazáskatalógus hivatkoznak szükségtelenné teszi. Emellett Silverlight-kompatibilis böngésző használata sem szükséges a továbbiakban. Lásd: [A System Center Configuration Managerrel végzett alkalmazáskezelés tervezése és konfigurálása](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   Az új Windows Installer mobileszköz-felügyelettel alkalmazástípus lehetővé teszi a Windows Installer-alapú alkalmazások létrehozását és telepítését Windows 10-et futtató, regisztrált számítógépeken. Lásd: [Windows-alkalmazások létrehozása a System Center Configuration Managerrel](../../../apps/get-started/creating-windows-applications.md).  

-   Amikor egy alkalmazás olyan belső fejlesztésű iOS-alkalmazást hoz létre, csak adja meg az alkalmazáshoz tartozó telepítő (.ipa) fájlt kell. Már nem kell megadnia egy megfelelő tulajdonságlista (.plist) fájlt. Lásd: [iOS-alkalmazások létrehozása a System Center Configuration Managerrel](../../../apps/get-started/creating-ios-applications.md).  

-   A Configuration Manager 2012-ben való adjon meg egy hivatkozást egy alkalmazást a Windows áruházban sikerült közvetlenül, vagy keresse meg a távoli számítógép, amely az alkalmazás telepítve volt. A System Center Configuration Managerben, esetében továbbra is megadhatja a hivatkozást közvetlenül, de most helyett egy referencia-számítógépet tallózással, megkeresheti az áruházban az alkalmazás közvetlenül a Configuration Manager konzoljáról.  

## <a name="software-updates"></a>Szoftverfrissítések  

Vegye figyelembe a szoftverfrissítéseket a következő módosításokat:

-   A System Center Configuration Manager már képes észlelni az szoftver frissítés módszereket számítógépek közötti különbség. Pontosabban akkor képesek megkülönböztetni a Windows 10 rendszerű számítógépeket, amely a Windows Update for Business (WUfB) a szoftverfrissítések felügyeletéhez, és a szoftverfrissítések felügyeletéhez a Windows Server Update Services (WSUS) csatlakozó számítógép. A **UseWUServer** attribútum egy új, és megadja, hogy a számítógép a WUfB kezelhető. Ezt a beállítást egy gyűjteményben használva eltávolíthatja ezeket a számítógépeket a szoftverfrissítés kezeléséből. További információkért lásd: [Integráció a Windows Update for Business szolgáltatással a Windows 10 rendszerben](../../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md).  

-   Mostantól ütemezése és a WSUS-karbantartási feladat futtatása a Configuration Manager konzolról. A **szoftverfrissítési pont összetevő** tulajdonságait, ha a WSUS-karbantartási feladat futtatását választja futtatni fogja a következő szoftverfrissítések szinkronizálását. A lejárt szoftverfrissítések frissítések vannak beállítva, hogy állapotot elutasította a WSUS-kiszolgáló és a Windows Update Agent a számítógépeken a továbbiakban nem keresi a szoftverfrissítések. További információk: [A WSUS-karbantartási feladat ütemezése és futtatása](../../../sum/deploy-use/software-updates-maintenance.md).  

## <a name="compliance-settings"></a>Megfelelőségi beállítások  

Vegye figyelembe a következő módosításokat a megfelelőségi beállítások:

-   System Center Configuration Manager javítja a munkafolyamat konfigurációelemek létrehozásához. Mostantól létrehozhat egy konfigurációelemet, majd kiválaszthatja a támogatott platformokat, és ekkor csak a platformra vonatkozó beállítások lesznek elérhetők. Lásd: [Bevezetés a System Center Configuration Manager megfelelőségi beállításainak használatába](../../../compliance/get-started/get-started-with-compliance-settings.md).  

-   A **Konfigurációelem létrehozása** varázsló egyszerűbbé a létrehozandó konfigurációelem-típus kiválasztásához. Emellett új és frissített konfigurációelemek állnak rendelkezésre a következőkhöz:  

    -   A Configuration Manager ügyfélalkalmazással felügyelt Windows 10-eszközökre.  

    -   A Configuration Manager ügyfélalkalmazással felügyelt Mac OS X-eszközökön.  

    -   Windows asztali és kiszolgáló számítógépekhez a Configuration Manager-ügyféllel felügyelt.  

    -   A Configuration Manager ügyfélalkalmazás nélkül felügyelt Windows 8.1 és Windows 10 eszközökre.  

    -   A Configuration Manager ügyfélalkalmazás nélkül felügyelt Windows Phone-eszközök.  

    -   a Configuration Manager-ügyfél nélkül felügyelt iOS és Mac OS X-eszközökön.  

    -   Android és Samsung KNOX Standard eszközökhöz a Configuration Manager ügyfélalkalmazás nélkül felügyelt.  

 Lásd: [Konfigurációelemek létrehozása a System Center Configuration Managerben](../../../compliance/deploy-use/create-configuration-items.md).  

-   Mac OS X rendszerű számítógépek, vagy a Microsoft Intune-nal regisztrált, vagy kezeli a Configuration Manager-ügyfél beállítások kezelésének támogatása. Lásd: [Konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt iOS és Mac OS X rendszerű eszközökhöz](../../../compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md).  

## <a name="protect-data-and-site-infrastructure"></a>Az adatok és a helyinfrastruktúra védelme  
A System Center Configuration Manager lehetővé teszi az integrációt a Windows Hello for Business (korábbi nevén Microsoft Passport for Work). Vállalati Windows Hello egy alternatív bejelentkezési módszer, amely az Active Directory vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett a Windows 10-es eszközökön. Lásd: [Windows Hello for Business settings in System Center Configuration Manager](../../../protect/deploy-use/windows-hello-for-business-settings.md) (A Vállalati Windows Hello beállításai a System Center Configuration Managerben).

## <a name="mobile-device-management-with-microsoft-intune"></a>Mobileszközök kezelése a Microsoft Intune-nal  
 A System Center Configuration Manager a mobileszköz-felügyeleti felületet fejlesztéseket vezet be többek között:  

-   A felhasználónként regisztrálható eszközök száma a megadott korlát helyezi.  

-   Adja meg a feltételeket és kikötéseket felhasználók a vállalati portál el kell fogadnia ahhoz, azok regisztrálása vagy használata előtt az alkalmazást.  

-   Hozzáadása egy eszközregisztráció-kezelő szerepkör nagyszámú eszköz kezeléséhez.  

A Configuration Manager és az Intune mobileszköz-kezelési képességekre vonatkozó további információkért lásd: [hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

## <a name="on-premises-mobile-device-management"></a>Helyszíni mobileszköz-felügyelet  
 Kezelheti mobileszközök most a helyi Configuration Manager-infrastruktúra használatával. Minden Eszközkezelési és felügyeleti adat kezelése a helyszínen, és nem a Microsoft Intune vagy más felhőalapú szolgáltatás részeként. Az ilyen típusú Eszközkezelés nem igényel ügyfélszoftvert. A Configuration Manager kezeli az eszközöket az eszköz operációs rendszerének beépített képességekkel.  

 További tudnivalókért lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).

