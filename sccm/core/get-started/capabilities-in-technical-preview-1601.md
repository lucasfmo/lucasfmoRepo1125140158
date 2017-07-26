---
title: "A Technical Preview 1601 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1601-es verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ef0db5b11ae2be5edcb4db87400c5c273c89972e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>A Technical Preview 1601-es rendszer képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1601-es verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan technical Preview funkciókkal kapcsolatos visszajelzés küldése közötti frissíteni.  

 **A Technical Preview kiadással kapcsolatos ismert problémák:**  

-   Amikor Ön felügyeli **ügyfélfrissítési lehetőségek** egy éles üzem előtti ügyfél előléptetése, a jelölőnégyzet szövegében a nullás (0) az ügyfél tényleges buildszáma helyett ügyfélverzió jelenik meg. A megfelelő üzem előtti ügyfélverzió jelenik meg a beállítás fölötti felületen, és az ügyfél verzióját, amely a tartományvezérlővé való előléptetése üzemi ezt a lehetőséget választva.  

-   Technical Preview 1601 való frissítése, és válassza a Configuration Manager-ügyfél tesztelése az éles üzem előtti gyűjteményben, amikor a rendszer nem frissíti az ügyfél-csomagot a gyűjteményhez. A probléma csak a Technical Preview 1601 van.  

     Probléma tegye az alábbiak egyikét:  

    -   Futtassa a következő SQL-parancsfájlt az elsődleges hely adatbázisát:  

        ```  
        DECLARE @PilotingPkgID NVARCHAR(8)  

        SELECT @PilotingPkgID = PilotingPackageID FROM ClientDeploymentSettings  

        MERGE INTO PkgServers_G AS T  
        USING (  
            SELECT @PilotingPkgID AS PkgID, NALPath, SiteCode, SiteName, SourceSite, RefreshTrigger, UpdateMask, [Action]  
            FROM PkgServers_G WHERE PkgID IN (SELECT UpgradePackageID FROM ClientDeploymentSettings)  
            ) AS S  
        ON T.PkgID = S.PkgID and T.NALPath = S.NALPath  

        WHEN NOT MATCHED THEN  
            INSERT (PkgID, NALPATH, SiteCode, SiteName, SourceSite, LastRefresh, RefreshTrigger, UpdateMask, [Action])  
            VALUES (S.PkgID, S.NALPath, S.SiteCode, S.SiteName, S.SourceSite, GetUTCDate(), S.RefreshTrigger, S.UpdateMask, S.[Action])  
        ;  

        ```  

    -   Adja hozzá egy új terjesztési pont helyrendszerszerepkört a kísérleti helyen. Az új terjesztési pont frissíti az új ügyfélcsomagot az üzem előtti gyűjtemény.  

**Új funkciókat próbálhatja ki ebben a következők:**  

##  <a name="bkmk_hybrid1"></a>A Microsoft Intune integrációjának fejlesztései  
A Technical Preview 1601 jelentek meg a következő funkciók támogatása:  

### <a name="improvements-to-conditional-access"></a>Feltételes hozzáférés fejlesztései  

-   **Feltételes hozzáférés támogatása a System Center Configuration Manager által felügyelt számítógépeken**  

     Beállíthatja a feltételes hozzáférési szabályzatokat a számítógépekhez, System Center Configuration Manager által felügyelt, ezért, hogy a számítógépeknek meg kell felelniük a megfelelőségi szabályzat Exchange Online és SharePoint Online szolgáltatások eléréséhez.  Ez az új funkció, a számítógépeket az Azure AD a megfelelőségi szabályzaton keresztül, és figyelésére és jelentésére az Azure AD-regisztrációval is rögzítheti.  

    > [!NOTE]  
    >  Feltételes hozzáférés még nem támogatott Windows 10 rendszeren.  

    Ez a szolgáltatás használatának előfeltételei a következők:  

    -   Az Azure Active Directory Premium előfizetés és AD FS-szinkronizálás.  

    -   Microsoft Intune-előfizetés. A Microsoft Intune-előfizetést a Configuration Manager konzolon lehet beállítani.  

    -   [Az Azure AD automatikus regisztrációjának előfeltételei](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    A funkció használatához az alább leírt szabályok alkalmazásával a Configuration Manager megfelelőségi szabályzat létrehozása, és állítsa be a feltételes hozzáférési szabályzatot az Intune-konzolon.  Emellett győződjön meg arról, hogy csak a megfelelő számítógépek kapjanak hozzáférést, akkor értékre kell állítani a Windows-Számítógépekkel szembeni követelményt **eszközök kompatibilisnek kell lennie** lehetőséget. Az alábbiakban, amelyek a System Center Configuration manager által felügyelt számítógépekre vonatkozó megfelelőségi szabályok.  

    -   **Az Azure Active Directoryban való regisztráció megkövetelése:** Ez a szabály ellenőrzi, hogy a felhasználó eszköze-e a munkahelyén az Azure AD-tartományhoz, és ha nem, az Azure AD automatikusan regisztrálja az eszközt. Az automatikus regisztráció csak a Windows 8.1-es rendszerben támogatott. Windows 7 rendszerű számítógépeken telepítsen egy MSI-csomagot az automatikus regisztráció végrehajtásához. További információkért lásd: [Itt](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    -   **Az összes szükséges frissítés telepítve egy bizonyos számú napnál régebbi határidő:** Ez a szabály ellenőrzi, hogy a felhasználó eszközén megtalálható-e az összes szükséges a frissítések (a megadott a **kötelező automatikus frissítések** szabály) belül megadott határidőn és türelmi időszakon is, és automatikusan telepít minden függőben lévő kötelező frissítést.  

    -   **BitLocker meghajtótitkosítás megkövetelése:** Ellenőrzi, hogy ha azt elsődleges meghajtója (pl. C:\\) az eszközön a BitLocker titkosítva van. Ha az elsődleges eszközön nincs engedélyezve a Bitlocker, a levelezéshez és a SharePoint szolgáltatásokhoz való hozzáférés le van tiltva.  

    -   **Kártevőirtó megkövetelése:** Azt ellenőrzi, hogy ha a kártevőirtó szoftver (System Center Endpoint Protection vagy csak a Windows Defender) engedélyezve van és fut.  
         Ha nincs engedélyezve a levelezéshez és a SharePoint szolgáltatásokhoz való hozzáférés le van tiltva.  

    Meg nem felelés miatt letiltott felhasználók az SCCM Szoftverközpontban tekinthetik megfelelőségi információkat, és indít el új megfelelőségi problémák szabályzatértékelést.  

-   **Feltételes hozzáférés az Állapotigazolási szolgáltatással** most korlátozzuk e-mailek és az eszközök állapotának alapján, az Állapotigazolási szolgáltatás által jelentett 0365 szolgáltatások.  Ezenkívül az Intune által kezelt eszközök szerepelnek az eszköz állapotjelentéseiben.  

    Új megfelelőségi szabály fel lett véve a configuration manager-konzolt, amely lehetővé teszi, hogy adja meg, ha engedélyezni kell az eszközöket, vagy az Eszközállapot alapján.  Ez a szabály létrehozásához nyissa meg a **megfelelőségi szabályzat létrehozása varázsló**, és vegye fel az új szabályt.  Válassza ki a **Állapotigazolási szolgáltatás által állapotként jelentett** feltétel, és állítsa be az értéket **igaz**.  Ezzel biztosíthatja, hogy csak eszközöket kifogástalan állapotúként kell jelenteni hozzáférhetnek a vállalati erőforrásokhoz. Eszközállapot-igazolási szolgáltatás és az eszközök állapotát az Intune-ban jelentésekről kapcsolatos részletekért lásd: [az Eszközállapot-igazolás](#bkmk_devicehealth).  

-   **Új megfelelőségiszabályzat-beállítások:** Az új megfelelőségiszabályzat-beállítások biztonsági és a vállalati e-mailekhez és SharePoint szolgáltatások elérésére használt eszközök védelmének javítása érdekében:  

    -   **Automatikus frissítések megkövetelése:** Szüksége van Windows 8.1 vagy újabb eszközökön a frissítések automatikus telepítésének engedélyezését, és adja meg a telepített frissítések besorolását.  Választhat, hogy: csak a fontosként megjelölt frissítéseket telepíti, vagy az összes ajánlott frissítést telepíti.  

         Egy automatikus frissítési szabály létrehozásához nyissa meg a **megfelelőségi szabályzat létrehozása varázsló**, és vegye fel az új szabályt.  Válassza ki **szükséges frissítések legalacsonyabb besorolása** a feltételt, és adja meg a rendelkezésre álló értékeket: **Nincs**, **ajánlott**, és **fontos**.  

        -   **Nincs:** Frissítései nem lesznek automatikusan telepítve.  

        -   **Ajánlott:** Az összes ajánlott frissítést telepíti  

        -   **Fontos:** Csak a fontos besorolású frissítéseket telepíti.  

    -   **A mobileszközök zárolásának feloldásához jelszó szükséges:** Ha ez a beállítás értéke **Igen**, a végfelhasználók kell adnia egy jelszót, mielőtt az eszköz eléréséhez.  

         A mobileszközök zárolásának feloldásához jelszószabály létrehozásához nyissa meg a **megfelelőségi szabályzat létrehozása varázsló**, és vegye fel az új szabályt. Válassza ki **tétlen eszközök zárolásának feloldásához jelszó szükséges** feltételt, és állítsa be az értéket **igaz**.  

    -   **Ennyi perc inaktivitás után kell jelszót beírni:**  Azt a tétlenségi időt határozza meg, amely eltelte után a felhasználónak újra be kell írnia a jelszavát.  

         Ez a szabály létrehozásához nyissa meg a **megfelelőségi szabályzat létrehozása varázsló**, és vegye fel az új szabályt. **Válassza ki a ennyi perc inaktivitás után kell jelszót beírni** a feltételt, és adja meg a rendelkezésre álló lehetőségek közül: 1 perc, 5 perc, 15 perc, 30 perc I óra.  

-   **Alapértelmezett szabály felülbírálása – mindig az Intune-ban regisztrált és megfelelőnek minősített eszközök helyszíni Exchange-hozzáférés engedélyezése:**  

     Ha ezt a beállítást, és a megfelelőségi szabályzatoknak az Intune-ban regisztrált eszközök hozzáférése engedélyezve legyen a helyszíni Exchange-hez. Ez a szabály felülírja az alapértelmezett szabályt, ami azt jelenti, hogy akkor is, ha beállította az alapértelmezett szabályt karanténba helyezésre vagy a hozzáférés letiltása a regisztrált és megfelelőnek minősített eszközök továbbra is hozzáférhetnek a helyszíni Exchange-hez lesznek.  
     Használja ezt a beállítást, ha azt szeretné, hogy a regisztrált és megfelelőnek minősített eszközök mindig hozzáférjenek a levelezéshez a helyszíni Exchange-en keresztül.  

     Ez a következő platformokon támogatott:  Windows Phone 8 és újabb verziók, iOS 6 és újabb verziók. Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0 és újabb verziók.  

     Használja ezt a beállítást, keresse fel a **általános** oldalán a **feltételes hozzáférési házirend konfigurálása varázsló** helyszíni Exchange esetén.  

##  <a name="bkmk_clientStatus"></a>Ügyfél online állapota  
Technical preview 1601-kezdve azonosíthatja egy pillantással hogy az ügyfél online vagy offline módban van, a Configuration Manager konzolon. Frissített ikonjai és oszlopai a konzolon az eszközlisták ügyfelek állapotának felmérheti a környezetben a problémás területek és a figyelmet igénylő más problémák azonosításához.  

Az ügyfél akkor online, ha jelenleg csatlakoztatva van a Configuration Manager felügyeleti pont helyrendszerszerepkörét futtatja. Mindaddig, amíg a felügyeleti pont pingszerű üzeneteket fogad az ügyféltől, addig online állapotú. Ha a felügyelet nem kap üzenetet körülbelül 5 percig, az ügyfél offline állapotúvá.  

### <a name="icons-for-client-status"></a>Az ügyfélállapot ikonok  

|||  
|-|-|  
|![online állapot ikon ügyfeleknek](media/online-status-icon.png)|Ügyfél online állapotban.|  
|![offline állapot ikon ügyfeleknek](media/offline-status-icon.png)|Ügyfél offline állapotban.|  
|![ismeretlen állapot ikon ügyfeleknek](media/unknown-status-icon.png)|Ügyfél állapota ismeretlen.|  

### <a name="prerequisites"></a>Előfeltételek  
 Ügyfél online állapota rendelkezik nincsenek előfeltételek. Megkezdheti, amint telepítve van a Configuration Manager technical preview 1601 használja azt.  

### <a name="limitations"></a>Korlátozások  
 Ügyfél online állapota lehetőség csak a Windows rendszerű számítógépekre a Configuration Manager-ügyfél telepítve van. Ügyfél online állapota nem támogatja a Mac számítógépek, Linux vagy UNIX rendszerű számítógépen vagy a kezelt eszközök\-helyszíni mobileszköz-kezelés.  

### <a name="to-view-client-online-status"></a>Online ügyfélállapot megtekintése  

1.  Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség > Áttekintés > eszközök**.  

2.  Kattintson a jobb gombbal az oszlop fejlécére, és kattintson az eszköz nézethez hozzáadandó az ügyfél online állapota mezők egyike. A mező kitöltése  

    -   **Online eszközállapot** – Azt jelzi, hogy az ügyfél jelenleg online vagy offline állapotú.  

    -   **Legutóbbi Online ideje** azt jelzi, hogy az ügyfél online állapota mikor változott offline állapotról online.  

    -   **Legutóbbi offline állapot ideje** azt jelzi, az állapota mikor változott online állapotról offline állapotba.  

 Az ügyfélállapot legutóbbi módosításainak megjelenítéséhez frissítse a konzolt.  

##  <a name="bkmk_appmgmt1601"></a>Alkalmazáskezelés fejlesztései  
 A Technical Preview 1601 jelentek meg a következő funkciók támogatása:  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>Nagy mennyiségben vásárolt alkalmazások felügyelete iOS-eszközökön  
 Egyes alkalmazás-áruházak, több licencet vásárolt a vállalatban futtatni kívánt alkalmazás képes. Ezzel a megoldással csökkenthetők az alkalmazások különböző megvásárolt példányainak nyilvántartásával járó adminisztratív terhek.  

 A Configuration Manager most segít importálja a licencadatokat az app store-ból, és nyomon követni, hogy hány licencet használt fel ilyen programban megvásárolt alkalmazások kezelésében.  

 További információkért lásd: [a Configuration Manager mennyiségi vásárlási program keretében vásárolt alkalmazások kezelése](https://technet.microsoft.com/library/mt627954.aspx).  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS - alkalmazások konfigurálása<br />Hibrid  
 Egyes iOS-alkalmazások támogatják a beállítások előkonfigurációját például egy kiszolgálón vagy adatbázisban, amelyhez az alkalmazás csatlakozni fog. A Configuration Manager mostantól támogatja a központi telepítés alkalmazások konfigurációs szabályzatainak az eszközre, amelyek lehetővé teszik a felhasználónak az alkalmazás azonnali használatát, anélkül, hogy ismernie kellene ezt az információt. A fejlesztőknek engedélyezniük kell ezt a funkciót az alkalmazásaikban.  

 Korlátozott számú nyilvánosan elérhető alkalmazás jelenleg támogatják a beállítások; akkor lehet, hogy is rendelkezik olyan házon belül fejlesztett üzletági alkalmazások, amelyek támogatják ezeket.  

#### <a name="prerequisites-for-this-scenario"></a>A forgatókönyv előfeltételei  

-   Hozzá kellett adnia egy Microsoft Intune-előfizetést a Configuration Manager.  

-   Hozzá kellett adnia egy érvényes Apple APNs-tanúsítványt az Intune-előfizetéshez.  

-   Telepítve kell lennie az iOS-alkalmazás, amely támogatja az alkalmazás konfigurációját.  

#### <a name="try-it-out"></a>Próbálja ki!  
 Ha a fenti előfeltételek teljesülnek, létre kell hoznia egy Configuration Manager-alkalmazás, amely iOS központi telepítési típust használ. A használt alkalmazásnak támogatnia kell az alkalmazás konfigurációja. Tekintse meg az alkalmazás gyártójának dokumentációjából megtudhatja, milyen egyedi elemeket (név/érték párok), konfigurálhatja.  

 Ezt követően társítani az alkalmazás konfigurációs szabályzatát az iOS központi telepítési típus alkalmazás központi telepítése során. Is telepítheti a házirendet a **alkalmazáskonfigurációs szabályzatok** csomópontot céloz meg egy létező alkalmazást és gyűjteményt.  

 Próbálja a következő feladatok végezhetők, majd ez a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel:  

-   Ha egy iOS-alkalmazást, amely támogatja az alkalmazáskonfiguráció, tekintse meg a gyártó dokumentációjában, ha szeretné tudni, a név-érték párok, meg kell adnia az alkalmazás konfigurálásához.  

-   Indítsa el a **alkalmazáskonfigurációs szabályzat létrehozása** varázsló. Az a **iOS-házirend** a varázsló, próbálja meg felvenni a vagy az alkalmazás gyártójának dokumentációjában talált név-érték párok importálhatja a szükséges értékeket tartalmazó XML-fájl.  

-   Az a **szoftver központi telepítése** varázsló a **Alkalmazáskonfigurálási szabályzat** lapon, az alkalmazás kompatibilis központi telepítési típust létrehozott alkalmazás-konfigurációs szabályzatot társítani.  

##  <a name="bkmk_compliance1601"></a>Megfelelőségi beállítások továbbfejlesztése  
 A Technical Preview 1601 jelentek meg a következő funkciók támogatása:  

### <a name="microsoft-edge-browser-settings"></a>A Microsoft Edge böngésző beállításai  
 A Microsoft Edge böngésző új beállítások érhetőek el a **Windows 8.1 és Windows 10** konfigurációs elemet (a beállítások csak Windows 10-eszközökre érvényesek).  

 Az új beállítások megtekintéséhez válassza ki **Microsoft Edge** elemet a konfigurációs elem **eszközbeállítások** oldalán a **Konfigurációelem létrehozása** varázsló.  

 További információkért lásd: [Windows 8.1 és Windows 10-eszközök konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Megfelelőségi beállítások a Windows 10 Team rendszerű eszközökhöz  
 Ezek új megfelelőségi beállítások segítségével konfigurálhatja a például a Surface Hub eszközöket a Windows 10 team rendszerű eszközök.  

 Az új beállítások megtekintéséhez válassza ki **a Windows 10 Team** elemet a konfigurációs elem **eszközbeállítások** oldalán a **Konfigurációelem létrehozása** varázsló.  

 További információkért lásd: [Windows 8.1 és Windows 10-eszközök konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android – teljes képernyős mód a Samsung KNOX szabvány<br />Hibrid  
 Teljes képernyős mód lehetővé teszi zárolhatja az eszközöket, hogy csak bizonyos szolgáltatások működjenek rajtuk. Megadhatja például, hogy az eszköz csak egy meghatározott felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok használatát az eszközön. Ezek a beállítások egy eszköz demonstrációs modelljéhez, illetve egy olyan eszközhöz használhatók, amely csak egyetlen funkció végrehajtására van kijelölve (például egy pénztári eszköz). Ezek a beállítások nem érhetők el a Samsung KNOX Standard eszközökön használható a **Windows 8.1 és Windows 10** konfigurációs elemet (a beállítások csak Windows 10-eszközökre érvényesek).  

 Az új beállítások megtekintéséhez válassza ki **teljes képernyős mód – Samsung NOx** elemet a konfigurációs elem **eszközbeállítások** oldalán a **Konfigurációelem létrehozása** varázsló.  

 További információkért lásd: [Windows 8.1 és Windows 10-eszközök konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

