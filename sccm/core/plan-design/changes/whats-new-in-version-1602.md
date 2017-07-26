---
title: "A System Center Configuration Manager 1602-es verzió új |} Microsoft Docs"
description: "Ezzel a módosítások és a System Center Configuration Manager 1602-es verziójában bevezetett új képességekkel kapcsolatos adatokat."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 9a548f43625a907173e7b967d26356bd80f1c5d9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>Mi & #39 újdonságai a System Center Configuration Manager 1602-es verzióra

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Az 1602-es frissítése a System Center Configuration Manager 1511-es verzióját futtató már telepített helyeken a konzolon belüli frissítésként csak érhető el. 1511-es verziója a kezdeti, alapszintű verzió, új Configuration Manager-helyek telepítéséhez.  


> [!TIP]  
>  További információ:  
>   
>   -   [Új helyek telepítése](/sccm/core/servers/deploy/install) (például 1511-es alapszintű verziójának használatával)  
>   -   [Helyfrissítések telepítése](/sccm/core/servers/manage/updates) (például az 1602-es frissítés)  

 A következő szakaszok részletesen bemutatják a módosításokat, és a Configuration Manager 1602-es verziójában bevezetett új képességekkel.  

## <a name="site-infrastructure"></a>Helyinfrastruktúra  

###  <a name="bkmk_UpgradeOS"></a>Az operációs rendszer Windows Server 2008 R2 rendszerű Helykiszolgálók helyben végzett verzióváltása  
 1602-es vagy újabb verziót futtató Configuration Manager-helyek támogatják a helybeni frissítést, a helykiszolgáló operációs rendszerének a Windows Server 2008 R2 Windows Server 2012 R2 rendszerre.  

> [!WARNING]  
>  Mielőtt Windows Server 2012 R2 rendszerre frissít, el kell távolítania a WSUS 3.2-es verzióját a kiszolgálóról.  
>   
>  Ez a lépés kritikus kapcsolatos információkért lásd: az "Új és módosított funkciók" című szakaszában [Windows Server Update Services áttekintése](https://technet.microsoft.com/library/hh852345.aspx), a Windows Server dokumentációjában.  

 A kiszolgálók frissítéséhez használja a Windows Server 2012 R2 frissítési eljárásait. Nem kell futtatni a Configuration Manager helyrendszer-kiszolgálójának visszaállítását a frissítés után. A frissítési eljárásokat lásd: [A Windows Server 2012 R2 frissítési lehetőségei](https://technet.microsoft.com/library/dn303416.aspx) témakör a Windows Server dokumentációjában.  

###  <a name="bkmk_AOAG"></a>SQL Server AlwaysOn rendelkezésre állási csoportok  
 SQL Server AlwaysOn rendelkezésre állási csoportok használatával a Helyadatbázis elsődleges helyeken és a központi adminisztrációs hely magas rendelkezésre állású és vész-helyreállítási megoldásként futtatni.  

 További információkért lásd: [SQL Server AlwaysOn magas rendelkezésre állású Helyadatbázis a System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

## <a name="operating-system-deployment"></a>Operációs rendszer központi telepítése  

### <a name="windows-10-servicing"></a>Windows 10 karbantartása  
 A Windows 10 karbantartásának következő fejlesztései a Configuration Manager 1602-es verzió lettek hozzáadva:  

-   Új szűrési lehetőségek kerültek be a karbantartási tervekbe, amelyek lehetővé teszik a kiszűrése **nyelvi**, **szükséges**, és **cím**. Csak a megadott feltételeknek megfelelő frissítések lesznek hozzáadva a társított központi telepítéshez.  

-   Ha bejelöli a **frissítések** szoftverfrissítési besorolás szinkronizálási frissíti, a figyelmeztetés akkor jelenik meg. Ez a figyelmeztetés értesíti Önt arról, hogy [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) Windows Server Update Services (WSUS) 4.0 szükség, mielőtt a szoftverfrissítések sikeres szinkronizálásához, valamint az a Windows 10 karbantartásának megfelelő működéséhez. A figyelmeztető üzenet megnyithatja a gyorsjavításhoz tartozó tudásbáziscikket.  

-   Windows 10 frissítései most már csak a megjelenített a **Windows 10 karbantartása** \ **minden Windows 10-frissítés** csomópont a Configuration Manager konzol. Ezek a frissítések már nem jelennek az **szoftverfrissítések** \ **minden szoftverfrissítés** a konzol csomópontjában.  

-   A karbantartási terv tekinthető magas kockázatú telepítés, és a **gyűjtemény választása** ablak csak azokat az egyéni gyűjteményeket, amelyek megfelelnek a központi telepítés ellenőrzési beállításai a hely tulajdonságai konfigurált jeleníti meg. További információkért lásd: [A System Center Configuration Manager magas kockázatú központi telepítések felügyeletéhez szükséges beállításai](../../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   Felhasználók, akik a Windows 10 frissítési csomagjait elindítása kap egy üzenetet, hogy azok frissíti az operációs rendszert.  

## <a name="application-management"></a>Alkalmazáskezelés  

### <a name="ios-app-configuration-policies"></a>iOS-alkalmazás-konfigurációs szabályzatok  
 A Configuration Manager alkalmazás-konfigurációs házirendek segítségével megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor a felhasználó egy iOS-alkalmazást futtat. Például egy alkalmazás kérheti a felhasználót, hogy adjon meg egy egyéni portszám, nyelvi, biztonsági beállítások vagy márkajelzési beállítások (például a vállalat logója). Ha helytelenül adja meg ezeket a beállításokat, ezzel növelheti az ügyfélszolgálatra nehezedő terheket, és lelassíthatja az új alkalmazások bevezetését.  

 Alkalmazás-konfigurációs házirendek segítséget nyújthatnak e problémák megoldásában azáltal, hogy telepítheti ezeket a beállításokat a felhasználók számára a házirendben még az alkalmazás futtatása előtt. A beállítások megadása ezek után automatikusan, és a felhasználónak nem kell tennie. További információkért lásd: [iOS-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek a System Center Configuration Managerben](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).  

### <a name="manage-volume-purchased-ios-apps"></a>Nagy mennyiségben vásárolt iOS-alkalmazások felügyelete  
 A Configuration Manager segítségével mennyiségi programban megvásárolt az Apple Volume Purchase Program (VPP) származó alkalmazások telepítését és kezelését. A Configuration Manager importálja a licencadatokat az app store-ból, és nyomon követi, hogy hány licencet használt fel.  

 További információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások a System Center Configuration Managerrel kezelése](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).  

### <a name="automatic-creation-of-office-mobile-apps"></a>Office-mobilalkalmazások automatikus létrehozása  
 Ha az 1511-es frissítés a 1602-es verzióra, a Configuration Manager automatikusan létrehozza a következő Microsoft Office-mobilalkalmazások Android és iOS:  

-   A Microsoft Word  

-   A Microsoft Excel  

-   Microsoft PowerPoint  

-   Microsoft onedrive vállalati verzió  

-   Microsoft OneNote (csak iOS)  

-   A Microsoft Outlook  

Ezeknek az alkalmazásoknak a megtalálja a **alkalmazások** csomópont a Configuration Manager konzol.  

 Alkalmazások központi telepítésével kapcsolatos további információkért lásd: [központi telepítése a System Center Configuration Managerrel alkalmazások](../../../apps/deploy-use/deploy-applications.md).  

## <a name="software-updates"></a>Szoftverfrissítések  

### <a name="manage-office-365-client-updates"></a>Office 365-ügyfélfrissítések kezelése  
 A System Center Configuration Manager képes kezelni az Office 365 asztali ügyfél frissítéseit a szoftverfrissítés-felügyeleti munkafolyamat használatával rendelkezik. További információkért lásd: [Office 365 ProPlus kezelése frissíti a System Center Configuration Managerrel](/sccm/sum/deploy-use/manage-office-365-proplus-updates).  

## <a name="compliance-settings"></a>Megfelelőségi beállítások  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Megfelelőségi beállítások Windows 10 Team rendszerű eszközökhöz  
 Új beállítások érhetőek el a **Windows 8.1 és Windows 10** konfigurációs elemet. Ezek a beállítások segítenek, például a Surface Hub eszközhöz Windows 10 Team rendszerű eszközök.  

 További információkért lásd: [Windows 8.1 és Windows 10-eszközök konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Teljes képernyős mód beállításai Android Samsung KNOX Standard eszközökhöz  
 Teljes képernyős mód lehetővé teszi az eszközök zárolását, hogy csak bizonyos szolgáltatások működjenek. Például az eszköz csak egy felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok az eszközön. Ezek a beállítások használhatók egy, vagy egy eszköz, például egy pénztári eszköz csak egyetlen funkció végrehajtására van kijelölve demonstrációs modelljéhez. A Configuration Manager mostantól megadhatja a teljes képernyős mód beállításai Samsung KNOX Standard eszközökön használható.  

 További információkért lásd: [Android és Samsung KNOX Standard eszközökhöz konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).  

## <a name="conditional-access"></a>Feltételes hozzáférés  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>Feltételes hozzáférés a System Center Configuration Manager által felügyelt számítógépekhez  
 Ebben a kiadásban vissza a számítógép feltételes hozzáférés beállítása a számítógép kellett az Intune-beli vagy kellett egy tartományhoz csatlakozó Számítógépnek kell. Az 1602-es frissítéstől kezdődően, feltételes hozzáférés a System Center Configuration manager által felügyelt számítógépek esetében támogatott. A System Center Configuration Manager által felügyelt számítógépeken, az access korlátozhatja Exchange Online és SharePoint online-hoz csak olyan eszközökre, amelyek megfelelnek az Ön által beállított megfelelőségi házirendnek.  

 További információkért lásd: [System Center Configuration Manager által felügyelt számítógépek esetében az Office 365-szolgáltatásokhoz való hozzáférés kezelése](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

### <a name="restricting-access-based-on-the-health-of-devices"></a>Az eszközök állapotát alapuló hozzáférés korlátozása  
 Most korlátozzuk az e-mailek és 0ffice 365 alapján az eszközök az Állapotigazolási szolgáltatás által jelentett módon. Ezenkívül az Intune által kezelt eszközök szerepelnek az eszköz állapotjelentéseiben.  

 A Configuration Manager konzol egy új megfelelőségi szabály, amely lehetővé teszi, hogy adja meg, ha engedélyezni kell az eszközöket, vagy az Eszközállapot alapján funkciókat. Eszközállapot-igazolási szolgáltatás és az eszközök állapotát az Intune-jelentésekről kapcsolatos részletekért lásd: [állapotigazolás a System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="new-compliance-policy-rules"></a>Új megfelelőségi szabályzatnak  
 Új megfelelőségi szabályzat előírásainak, például az automatikus frissítések és az eszközök zárolásának feloldásához jelszó megkövetelése a hatékonyabb biztonsági igényeinek támogatására bővült.

 További részletekért lásd: [eszközmegfelelőségi szabályzatok a System Center Configuration Managerben](../../../protect/deploy-use/device-compliance-policies.md).  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>Győződjön meg arról, hogy a regisztrált és megfelelő eszközök mindig hozzáférjenek a helyszíni Exchange-hez  
 A következő beállítást az Intune-ban, és a megfelelőségi szabályzatoknak, regisztrált eszközök hozzáférése engedélyezve legyen a helyszíni Exchange-hez: **Alapértelmezett szabály felülbírálása – mindig az Intune-ban regisztrált és megfelelőnek minősített eszközök helyszíni Exchange-hozzáférés engedélyezése:**. Ez a szabály a **Általános lap** , a **feltételes hozzáférési házirend konfigurálása varázsló** helyszíni Exchange esetén.

 Ez a szabály felülírja az alapértelmezett szabályt, ami azt jelenti, hogy akkor is, ha beállította az alapértelmezett szabály blokkolja a hozzáférést, regisztrált és megfelelőnek minősített eszközök továbbra is hozzáférhetnek a helyszíni Exchange-hez lesznek. Használja ezt a beállítást, ha azt szeretné, hogy a regisztrált és megfelelőnek minősített eszközök mindig hozzáférjenek a levelezéshez a helyszíni Exchange-en keresztül.   

 A részletes útmutatót lásd: [e-mail-hozzáférés kezelése a System Center Configuration Managerben](../../../protect/deploy-use/manage-email-access.md).  

## <a name="client-management"></a>Ügyfélfelügyelet  

### <a name="client-online-status"></a>Online ügyfélállapot  
 Ügyfelek új állapotának figyeléséhez, ha a számítógép online állapotban, vagy nem érhető el. A számítógép akkor számít online állapotúnak, ha a hozzárendelt felügyeleti pont van csatlakoztatva. Azt jelzi, hogy a számítógép online, az az ügyfél pingszerű üzeneteket küld a felügyeleti pont. A felügyeleti pont 5 perc után nem kap üzenetet, ha az ügyfél offline állapotúnak tekinti.  

 További információkért lásd: [ügyfélgépek figyelése a System Center Configuration Managerben](../../../core/clients/manage/monitor-clients.md).  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Frissítse a számítógép számítógép- és felhasználói házirendet a Szoftverközpontból  
 Egy új beállítás **házirend szinkronizálása**, hozzá lett adva a **beállítások** > **számítógép-karbantartás** Szoftverközpont a számítógép frissíti a Configuration Manager-számítógép- és felhasználói házirendjét okozó oldalán.  

### <a name="software-center-branding-changes"></a>A Szoftverközpont márkajelzési változásai  
 Módosíthatja a színt, szervezetnevet és a Szoftverközpontban megjelenő ikon. Ezek a beállítások a következő szabályok szerint alkalmazza a rendszer:  

- Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre nincs telepítve, akkor a Szoftverközpont a szervezet nevét jeleníti meg a **Számítógépügynök** ügyfélbeállítás hívott **a Szoftverközpontban megjelenített név**.  

- Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre telepítve van, akkor a Szoftverközpont jeleníti meg a szervezet nevét és az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre tulajdonságaiban megadott szín.  

- Ha a Microsoft Intune-előfizetés konfigurálva, és a Configuration Manager környezethez csatlakozik, majd a Szoftverközpont jeleníti meg a szervezet neve, a színt és a vállalati embléma, az Intune-előfizetés tulajdonságai megadott.  

### <a name="health-attestation"></a>Az Eszközállapot-igazolás  
 Rendszergazdák megtekinthetik a Windows 10 Eszközállapot-igazolási állapotát a Configuration Manager konzolon. Ez érhető el a Configuration Manager, valamint a Configuration Manager a Microsoft Intune-nal. Az eszközállapot-igazolással a rendszergazdák bekapcsolhatják az ügyfélszámítógépeken következő megbízható BIOS-, TPM- és rendszerindítószoftver-konfigurációkat:  

-   Korai indítás kártevőirtó  

-   A BitLocker  

-   A biztonságos rendszerindítás  

-   A Kódintegritás  

További információkért lásd: [állapotigazolás a System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Az Endpoint Protection kártevőirtó-beállításainak fejlesztései  
 az 1602-es ad hozzá, a Windows Defender a következő új beállítások az Endpoint Protection kártevőirtó-házirendet:  

-   A valós idejű védelem: Letöltéskor telepítés előtti vélhetően nemkívánatos alkalmazások blokkolása.  

-   Vizsgálati beállítások: Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat közben.  

-   Az automatikus mintafájlküldési beállítások:  

     A kártevőirtó motor kérheti fájlminták elküldését a Microsoftnak további elemzés céljából. Az ilyen minták küldése előtt a rendszer alapértelmezés szerint mindig megkérdezi a felhasználót. A rendszergazdák mostantól a következő beállítások kezelésével konfigurálhatják ezt a viselkedést:  

    -   Speciális: Engedélyezze a mintafájlok automatikus küldésének hogy segítse annak meghatározásában, hogy-e rosszindulatú bizonyos észlelt elemekre.  

    -   Speciális: Módosítsa az automatikus mintafájlküldési beállítások engedélyezése.  

    Emellett szakaszában a "A kizárások beállításai" az endpoint protection kártevőirtó-házirendet, a meglévő **fájlok és mappák kizárása** beállítás mostantól lehetővé teszi az eszközök kizárását.  

További információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](../../../protect/deploy-use/endpoint-antimalware-policies.md).  

## <a name="mobile-device-management"></a>Mobil eszközök felügyelete  

### <a name="ios-activation-lock"></a>iOS aktiválási zára  
 A Configuration Manager segítségével iOS aktiválási zára, egy szolgáltatás find My iPhone alkalmazást az iOS 7.1 és újabb rendszerű eszközök kezelése. Ha a Find My iPhone alkalmazást használják egy eszközön, az aktiválási zár automatikusan engedélyezve lesz. Az engedélyezése után meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni a következők bármelyikét:  

-   A Find My iPhone alkalmazás kikapcsolása.  

-   Az eszköz alaphelyzetbe állítása.  

-   Az eszköz újraaktiválása.  

A Configuration Manager kérhetnek a felügyelt és a felügyeletlen, iOS 7.1 és újabb rendszerű eszközök aktiválási Zárának állapotát. A felügyelt eszközök esetén a Configuration Manager lekérdezni az Aktiválásizár-áthidaló kódot, és közvetlenül kiadni azt az eszközt.  

 További információkért lásd: [az iOS-eszközök aktiválási zár megkerülésével a System Center Configuration Managerben védelme](/sccm/mdm/deploy-use/manage-ios-activation-lock).  

### <a name="monitor-terms-and-conditions-deployments"></a>Használati feltételek központi telepítésének figyelése  
 Használati feltételek központi telepítését a Configuration Manager konzolon figyelheti meg.  

 Válassza ki a használati feltételek központi telepítését a központi telepítések listájából. Az összegzési területen a következő statisztika megjelenítése:  

-   **Megfelelő**: Felhasználók elfogadták a használati feltételek legújabb verzióját.  

-   **Hiba:**  

-   **Nem megfelelő**: Felhasználók fogadták el a a feltételeket és kikötéseket, de nem a legújabb verziót.  

-   **Ismeretlen**: Felhasználók nem fogadták el a használati feltételeket, beleértve a regisztrált eszköz nélküli.  

