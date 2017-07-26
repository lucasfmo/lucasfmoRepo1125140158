---
title: "Windows-ügyfél telepítésének előfeltételei |} Microsoft Docs"
description: "Ismerje meg, hogy a Windows rendszerű számítógépekre a System Center Configuration Manager ügyfelek telepítésének előfeltételeit."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1a2a9b48-a95b-4643-b00c-b3079584ae2e
caps.latest.revision: 16
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 6636ce4d929326fad0210407d7634ea585eb0a2d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-deploying-clients-to-windows-computers-in-system-center-configuration-manager"></a>Az ügyfélszoftverek Windows rendszerű számítógépekre történő központi telepítésével kapcsolatos előfeltételek a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A környezetben a Configuration Manager-ügyfelek központi telepítéséhez rendelkezik, az alább ismertetett külső függőségeket és a termékben lévő függőségei is. Ezenkívül mindegyik ügyfél-telepítési módszernek saját függőségei vannak, amelyeknek teljesülniük kell az ügyfelek sikeres telepítéséhez.  

  Győződjön meg arról, hogy tekintse át [a System Center Configuration Manager által támogatott konfigurációk](../../../core/plan-design/configs/supported-configurations.md) annak ellenőrzéséhez, hogy az eszközök megfelelnek a minimális hardver- és operációs rendszer követelményei a Configuration Manager-ügyfél.  

 Az Előfeltételek a Configuration Manager-ügyfél Linux és UNIX rendszerű információ: [Linux és UNIX rendszerű számítógépekre a System Center Configuration Manager ügyfél központi telepítésének tervezése](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

> [!NOTE]  
>  A cikkben említett szoftververziószámok a minimálisan szükséges verziót jelentik.  

##  <a name="BKMK_prereqs_computers"></a>Számítógép ügyfelek előfeltételei  
 A következő információ használatával határozhatja meg az alkalmazás telepítésekor a Configuration Manager-ügyfelet a számítógépeken szükséges előfeltételeket.  

### <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  

|||  
|-|-|  
|Windows Installer 3.1.4000.2435-ös verzió|A Windows Installer-frissítésfájlok (.msp) támogatásához szükséges, lehetővé teszi a csomagok és a szoftverfrissítések használatát.|  
|[KB2552033](http://go.microsoft.com/fwlink/p/?LinkId=240048)|Ezt a gyorsjavítást akkor kell telepíteni a Windows Server 2008 R2 rendszerű helykiszolgálókon, ha engedélyezve van az ügyfelek leküldéses telepítése.|  
|Microsoft Background Intelligent Transfer Service (BITS) 2.5-ös verzió|Szükséges szabályozottan halmozott adatátviteleket az ügyfélszámítógép és a Configuration Manager helyrendszerei közötti engedélyezéséhez. A rendszer nem tölti le automatikusan a BITS szolgáltatást az ügyféltelepítés során. Amikor telepíti a BITS szolgáltatást a számítógépekre, a telepítés befejezéséhez rendszerint újraindítás szükséges.<br /><br /> Operációs rendszerek többsége tartalmazza a BITS szolgáltatást, de ha így tesznek, nem (Ha például a Windows Server 2003 R2 SP2), telepítenie kell a BITS a Configuration Manager-ügyfél telepítése előtt.|  
|Microsoft Feladatütemező|Engedélyezze ezt a szolgáltatást az ügyfélen az ügyféltelepítés befejezéséhez.|  

### <a name="dependencies-external-to-configuration-manager-and-automatically-downloaded-during-installation"></a>A Configuration Manager alkalmazáson kívüli, a telepítés során automatikusan letöltött függőségek  
 A Configuration Manager-ügyfél néhány lehetséges külső függőségekkel rendelkezik. Ezek a függőségek az operációs rendszertől és az ügyfélszámítógépre telepített szoftvertől függenek.  

 Ha ezekre a függőségekre szükség van az ügyfél telepítésének végrehajtásához, a rendszer automatikusan telepíti azokat az ügyfélszoftverrel együtt.  

|||  
|-|-|  
|Windows Update Agent 7.0.6000.363-as verzió|A Windows számára szükséges a frissítések észlelésének és telepítésének támogatásához.|  
|Microsoft Core XML Services (MSXML) 6.20.5002-es vagy újabb verzió|Az XML-dokumentumok feldolgozásának támogatásához szükséges a Windows rendszerben.|  
|Microsoft Remote Differential Compression (RDC)|A hálózaton keresztüli adatátvitel optimalizálásához szükséges.|  
|Microsoft Visual C++ 2013 Redistributable 12.0.21005.1-es verzió|Az ügyfélműveletek támogatásához szükséges. E frissítés ügyfélszámítógépeken történő telepítésekor előfordulhat, hogy a telepítés befejezéséhez újra kell indítani a számítógépet.|  
|Microsoft Visual C++ 2005 Redistributable 8.0.50727.42-es verzió|1606 és korábbi verziójú, a Microsoft SQL Server Compact műveleteinek támogatásához szükséges.|  
|Windows Imaging API 6.0.6001.18000|Configuration Manager kezelje a Windows-képfájlokat (.wim) engedélyezése szükséges.|  
|Microsoft Policy Platform 1.2.3514.0|Lehetővé teszi, hogy az ügyfelek kiértékeljék a megfelelési beállításokat.|  
|A Microsoft Silverlight 5.1.41212.0 (verziótól kezdve a Configuration Manager 1602-es verzió)|A felhasználói élmény támogatásához szükséges az alkalmazáskatalógus webhelyén.|  
|Microsoft .NET-keretrendszer 4.5.2-es verzió.|Az ügyfélműveletek támogatásához szükséges. Automatikusan települ az ügyfélszámítógépen, ha nincs telepítve a Microsoft .NET-keretrendszer 4.5-ös vagy újabb verziója. További információk: [További tudnivalók a Microsoft .NET-keretrendszer 4.5.2-es verziójáról](#dotNet).|  
|Microsoft SQL Server Compact 3.5 SP2 összetevők|Az ügyfélműveletekkel kapcsolatos információ tárolásához szükséges.|  
|Microsoft Windows képkezelő összetevők|A Windows Server 2003 rendszereken használt Microsoft .NET-keretrendszer 4.0-s verzió vagy a 64 bites számítógépeken használt Windows XP SP2 számára szükséges.|
|A Microsoft Intune szoftver ügyféllel|Az Intune számítógépes szoftverek ügyfél és a Configuration Manager-ügyfél ugyanazon a számítógépen nem futtatható. Gondoskodjon arról, hogy az Intune-ügyfelet a Configuration Manager-ügyfél telepítése előtt el kell távolítani.|

####  <a name="dotNet"></a>További tudnivalók a Microsoft .NET-keretrendszer 4.5.2-es verzió.  

> [!NOTE]  
>  2016. január 12-én kezdve a .NET 4.0-s, 4.5-ös és 4.5.1-es verzió támogatása véget ér. További információ: [A Microsoft .NET keretrendszer támogatási életciklusra vonatkozó szabályzata – GYIK](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) a support.microsoft.com címen.  

 A Microsoft .NET-keretrendszer 4.5.2-es verziója telepítésének befejezéséhez szükség lehet a rendszer újraindítására. Ekkor a felhasználó számára az **Újraindítás szükséges** értesítés jelenik meg a tálcán.  Az ügyfélszámítógépek újraindítását igénylő gyakori helyzetek:  

-   .NET-alkalmazások vagy -szolgáltatások futnak a számítógépen.  

-   A .NET telepítéséhez szükséges egy vagy több szoftverfrissítés hiánya.  

-   A számítógép újraindítása a .NET-keretrendszer korábbi szoftverfrissítéseinek telepítését követően függőben maradt.  

 Előfordulhat, hogy a .NET-keretrendszer 4.5.2-es verziójának telepítése után annak további frissítései is települnek, ami a számítógép további újraindításait teheti szükségessé.  

### <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  
 További információ a következő helyrendszerszerepkörökről: [A System Center Configuration Manager-ügyfelek helyrendszerszerepköreinek meghatározása](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|||  
|-|-|  
|Felügyeleti pont|Bár a Configuration Manager-ügyfél telepítése nem igényel felügyeleti pontokat, rendelkeznie kell a felügyeleti pontok információt továbbítanak az ügyfélszámítógépek és a Configuration Manager-kiszolgálók között. Felügyeleti pontok nélkül nem tudja felügyelni az ügyfélszámítógépeket.|  
|Terjesztési pont|A terjesztési pont használata nem kötelező, de ajánlott helyrendszerszerepkörnek tekintendő az ügyfelek telepítésekor. Mindegyik terjesztési ponton megtalálhatók az ügyfél forrásfájljai, ami lehetővé teszi, hogy a számítógépek a legközelebbi terjesztési pontot használják az ügyfél forrásfájljainak letöltéséhez az ügyfél telepítése során. Ha a helynek nincs terjesztési pontja, a számítógépek a felügyeleti pontjukról töltik le az ügyfél forrásfájljait.|  
|Tartalék állapotkezelő pont|A tartalék állapotkezelő pont használata nem kötelező, de ajánlott helyrendszerszerepkörnek tekintendő az ügyfelek telepítésekor. A tartalék állapotkezelő pont nyomon követi az ügyfél telepítését, és lehetővé teszi, hogy a Configuration Manager-hely, hogy állapotüzenetet küldjenek, amikor nem tudnak kommunikálni egy felügyeleti pont számítógépén.|  
|Jelentéskészítési szolgáltatási pont|A jelentéskészítési szolgáltatási pont használata nem kötelező, de ajánlott helyrendszerszerepkörnek tekintendő, amellyel megjeleníthetők az ügyfél telepítésével és felügyeletével kapcsolatos jelentések. További információ: [Jelentéskészítés a System Center Configuration Managerben](../../../core/servers/manage/reporting.md).|  

### <a name="installation-method-dependencies"></a>A telepítési módszer függőségei  
 Az ügyféltelepítés különböző módszereire a következő előfeltételek vonatkoznak.  

-   Ügyfél leküldéses telepítése  

    -   Az ügyfélleküldéses telepítés fiókjainak használatával lehet csatlakozni a számítógépekhez az ügyfél telepítéséhez. Ezek a fiókok az **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanel **Fiókok** lapján adhatók meg. A fióknak tagnak kell lennie a helyi rendszergazdák csoportjában a célszámítógépen.  

         Ha nem adja meg az ügyfélleküldéses telepítés fiókját, a rendszer a helykiszolgáló számítógép fiókját fogja használni.  

    -   A számítógép, amelyre telepíti az ügyfelet fel kell deríteni legalább egy Configuration Manager felderítési eljárás alapján.  

    -   A számítógépnek tartalmaznia kell ADMIN$ megosztást.  

    -   **Engedélyezi az ügyfélleküldéses telepítést hozzárendelt erőforrásokon** ki kell jelölni a **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanel, ha azt szeretné, hogy a Configuration Manager-ügyfél automatikusan leküldéses felderített erőforrásokhoz.  

    -   Az ügyfélszámítógépnek csatlakoznia kell egy terjesztési ponthoz vagy egy felügyeleti ponthoz a szükséges fájlok letöltéséhez.  

     A Configuration Manager-ügyfél telepítése ügyfélleküldés használatával a következő biztonsági engedélyekkel kell rendelkeznie:  

    -   A leküldéses ügyféltelepítés fióknak konfigurálása: **Módosítsa** és Olvasás engedély a **hely** objektum.  

    -   Leküldéses ügyféltelepítés használatához az ügyfél gyűjtemények, eszközökön és lekérdezéseken történő telepítéséhez: **Erőforrás módosítása** és **olvasási** engedély a gyűjtemény objektumra.  

     Az **Infrastruktúra-rendszergazda** biztonsági szerepkör tartalmazza az ügyfélleküldéses telepítés felügyeletéhez szükséges engedélyeket.  

-   Szoftverfrissítési ponton alapuló telepítés  

    -   Ha nincs kibővítve az Active Directory-séma, vagy ha másik erdőből telepít ügyfeleket, a CCMSetup.exe telepítési tulajdonságait csoportházirend használatával kell megadni a számítógép beállításjegyzékében. További információért lásd: [Az ügyféltelepítés tulajdonságainak megadása (csoportházirenden és szoftverfrissítésen alapuló ügyféltelepítés)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   A Configuration Manager-ügyfelet közzé kell tenni a szoftverfrissítési ponton.  

    -   Az ügyfélszámítógépnek csatlakoznia kell egy terjesztési ponthoz vagy egy felügyeleti ponthoz a szükséges fájlok letöltéséhez.  

     A Configuration Manager szoftverfrissítéseinek felügyeletéhez szükséges biztonsági engedélyek, lásd: [a System Center Configuration Manager szoftverfrissítéseinek előfeltételei](../../../sum/plan-design/prerequisites-for-software-updates.md).  

-   Csoportházirend-alapú telepítés  

    -   Ha nincs kibővítve az Active Directory-séma, vagy ha másik erdőből telepít ügyfeleket, a CCMSetup.exe telepítési tulajdonságait csoportházirend használatával kell megadni a számítógép beállításjegyzékében. További információért lásd: [Az ügyféltelepítés tulajdonságainak megadása (csoportházirenden és szoftverfrissítésen alapuló ügyféltelepítés)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   Az ügyfélszámítógépnek csatlakoznia kell egy felügyeleti ponthoz a szükséges fájlok letöltéséhez.  

-   Bejelentkezési parancsprogramfájlon alapuló telepítés  

     Az ügyfélszámítógépnek csatlakoznia kell egy terjesztési ponthoz vagy egy felügyeleti ponthoz a szükséges fájlok letöltéséhez, kivéve ha a parancssorban megadja a CCMSetup.exe parancsot és a **ccmsetup /source** parancssori tulajdonságot.  

-   Manuális telepítés  

     Az ügyfélszámítógépnek csatlakoznia kell egy terjesztési ponthoz vagy egy felügyeleti ponthoz a szükséges fájlok letöltéséhez, kivéve ha a parancssorban megadja a CCMSetup.exe parancsot és a **ccmsetup /source** parancssori tulajdonságot.  

-   Telepítés munkacsoporthoz tartozó számítógépen  

     A Configuration Manager helykiszolgáló tartományában lévő erőforrások eléréséhez a helyhez a hálózatelérési fiókot kell konfigurálni.  

     A hálózatelérési fiók konfigurálásával kapcsolatos további információkért lásd: a [a System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Szoftverterjesztés-alapú telepítés (csak frissítések esetén)  

    -   Ha nincs kibővítve az Active Directory-séma, vagy ha másik erdőből telepít ügyfeleket, a CCMSetup.exe telepítési tulajdonságait csoportházirend használatával kell megadni a számítógép beállításjegyzékében. További információért lásd: [Az ügyféltelepítés tulajdonságainak megadása (csoportházirenden és szoftverfrissítésen alapuló ügyféltelepítés)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   Az ügyfélszámítógépnek csatlakoznia kell egy terjesztési ponthoz vagy egy felügyeleti ponthoz a szükséges fájlok letöltéséhez.  

     A Configuration Manager-ügyfél alkalmazásfelügyelet használatával frissítéséhez szükséges biztonsági engedélyekről, lásd: [biztonság és adatvédelem az Alkalmazáskezelés](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   Automatikus ügyfélfrissítések  

     Az automatikus ügyfélfrissítések konfigurálásához a **Teljes körű rendszergazda** biztonsági szerepkör tagjának kell lennie.  

### <a name="firewall-requirements"></a>A tűzfalra vonatkozó követelmények  
 Ha tűzfal található a helyrendszer-kiszolgálók és azon számítógépek között, amelyekre telepíteni kívánja a Configuration Manager-ügyfelet, olvassa el a következő témakört: [Windows tűzfal és portbeállítások az ügyfelekhez a System Center Configuration Managerben](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

##  <a name="BKMK_prereqs_mobiledevices"></a>Mobileszközre telepített ügyfelekre vonatkozó Előfeltételek  
 A következő információ használatával határozhatja meg az előfeltételeket, amikor a Configuration Manager-ügyfél telepítése a mobileszközökre, és a Configuration Manager használatával lépteti be azokat.  

### <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  

-   A mobileszközökhöz szükséges tanúsítványok telepítéséhez és felügyeletéhez a Microsoft vállalati hitelesítésszolgáltatója és tanúsítványsablonok használandók.  

     A kiállító hitelesítésszolgáltatónak automatikusan jóvá kell hagynia a mobileszközök felhasználóinak tanúsítványra vonatkozó kérelmeit a beléptetési folyamat során.  

     További információk a tanúsítványkövetelményekről: [Tanúsítványprofilok biztonsága és adatvédelme a System Center Configuration Managerben](../../../protect/plan-design/security-and-privacy-for-certificate-profiles.md).  

-   Biztonsági csoport, amely azokat a felhasználókat tartalmazza, akik beléptethetik a mobileszközeiket.  

     Ezt a biztonsági csoportot kell használni a mobileszközök beléptetése során használt tanúsítványsablon konfigurálásához.  

-   Opcionális de javasolt: egy **ConfigMgrEnroll** nevű DNS-alias (CNAME rekord), amelyben be van állítva annak a helykiszolgálónak a neve, amelyen telepíteni fogja a beléptetési proxypontot.  

     Ez a DNS-alias szükség, a beléptetési szolgáltatás automatikus felderítésének támogatásához: Ha nem konfigurálja a DNS-rekordot, felhasználóknak kézzel kell megadniuk a beléptetési proxypont helyrendszer rendszer kiszolgáló nevét a beléptetési folyamat részeként.  

-   A helyrendszerszerepkörök függőségei azon számítógépekhez, amelyek futtatni fogják a beléptetési pontot, valamint a beléptetési proxypont helyrendszerszerepkörei.  

     További információk: [Helyrendszer-kiszolgálók által támogatott operációs rendszerek](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md).  

### <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  
 További információ a következő helyrendszerszerepkörökről: [A System Center Configuration Manager-ügyfelek helyrendszerszerepköreinek meghatározása](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

-   Felügyeleti pont, amely be van állítva a HTTPS-ügyfélkapcsolatokhoz és amelyen engedélyezve vannak a mobileszközök  

     A felügyeleti pont megadása mindig kötelező a mobileszközökön a Configuration Manager-ügyfél telepítéséhez. A HTTPS konfigurációs beállításainak megadása és a mobileszközök engedélyezése mellett a felügyeleti ponton meg kell adni egy internetes teljes tartománynevet (FQDN), és be kell állítani az internetről érkező ügyfélkapcsolatot elfogadását.  

-   Beléptetési pont és beléptetési proxypont  

     A beléptetési proxypont felügyeli a mobileszközök beléptetési kérelmeit, a beléptetési pont pedig végrehajtja a beléptetési folyamatot. A beléptetési pontnak a helykiszolgálóval azonos Active Directory-erdőben kell lennie, a beléptetési proxypont esetében azonban ez nem feltétel.  

-   A mobileszközök beléptetéséhez szükséges ügyfélbeállítások  

     Az ügyfélbeállításokat úgy kell megadnia, hogy lehetővé tegyék a felhasználóknak a mobileszközök beléptetését. Emellett konfigurálnia kell legalább egy beléptetési profilt.  

-   Jelentéskészítési szolgáltatási pont  

     A jelentéskészítési szolgáltatási pont használata nem kötelező, de ajánlott helyrendszerszerepkörnek tekintendő, amellyel megjeleníthetők a mobileszközök beléptetésével és az ügyfél felügyeletével kapcsolatos jelentések.  

     További információ: [Jelentéskészítés a System Center Configuration Managerben](../../../core/servers/manage/reporting.md).  

-   A mobileszközök beléptetésének konfigurálásához a következő biztonsági engedélyekkel kell rendelkeznie:  

    -   Hozzáadása, módosítása és törlése a beléptetési helyrendszerszerepkörök: **Módosítsa** engedély a **hely** objektum.  

    -   A beléptetéshez szükséges ügyfélbeállítások konfigurálása: Alapértelmezett ügyfélbeállítások esetében **módosítás** engedély a **hely** objektum és a szükséges egyéni ügyfélbeállításokkal **ügyfélügynök** engedélyek.  

     A **Teljes körű rendszergazda** biztonsági szerepkör tartalmazza a beléptetési helyrendszerszerepkörök konfigurálásához szükséges engedélyeket.  

     A beléptetett mobileszközök felügyeletéhez a következő biztonsági engedélyekkel kell rendelkeznie:  

    -   A mobileszköz kivonása vagy törlése: **Erőforrás törlése** a a **gyűjtemény** objektum.  

    -   A parancs kivonása, vagy szakítsa meg a törlés: **Erőforrás törlése** a a **gyűjtemény** objektum.  

    -   A mobil eszközök letiltása és engedélyezése: **Erőforrás módosítása** a a **gyűjtemény** objektum.  

    -   Távoli zárolás, vagy egy mobileszköz PIN-kód visszaállítása: **Módosítsa** -erőforrást az **gyűjtemény** objektum.  

     A **Műveleti rendszergazda** biztonsági szerepkör tartalmazza a mobileszközök felügyeletéhez szükséges engedélyeket.  

     További információ a biztonsági engedélyek beállításáról: [A System Center Configuration Manager szerepköralapú adminisztrációjának alapjai](../../../core/understand/fundamentals-of-role-based-administration.md) és [A System Center Configuration Manager szerepköralapú adminisztrációjának konfigurálása](../../../core/servers/deploy/configure/configure-role-based-administration.md).  

### <a name="firewall-requirements"></a>A tűzfalra vonatkozó követelmények  
 A beavatkozó hálózati eszközöknek, például az útválasztóknak, tűzfalaknak és a Windows tűzfalnak (ha van) engedélyeznie kell a mobileszköz beléptetéséhez kapcsolódó forgalmat.  

-   Mobileszközök és a beléptetési proxypont: között HTTPS (alapértelmezésben TCP 443)  

-   A beléptetési proxypont és a beléptetési pont: HTTPS (alapértelmezésben TCP 443)  

 A proxy webkiszolgálókon be kell állítani az SSL-bújtatást; mobileszközök esetében az SSL-áthidalás nem támogatott.  

