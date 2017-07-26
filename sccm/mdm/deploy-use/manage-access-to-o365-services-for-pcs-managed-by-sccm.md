---
title: "Kezelt PC-k Office 365-szolgáltatásokhoz való hozzáférés kezelése |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager által felügyelt számítógépek feltételes hozzáférésének beállítása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
caps.latest.revision: 15
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: e9028a54e538b4ec987dbaeb5ba1ee22ad091728
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>Az Office 365-szolgáltatásokhoz való hozzáférés kezelése a System Center Configuration Manager által felügyelt számítógépek esetében

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*



 A Configuration Manager 1602-es verziójától kezdve a System Center Configuration Manager által felügyelt számítógépek feltételes hozzáférés állíthatja be.  

> [!IMPORTANT]  
>  Ez az 1602-es frissítést, a frissítés 1606 és a frissítés 1610 előzetes verziójú szolgáltatás. Az előzetes funkciók azért kerülnek be a termékbe, hogy üzemi környezetben is tesztelhessék őket, ugyanakkor nem tekintendők úgy, hogy készen állnak az üzemi működésre. További információk a következő helyen találhatók: [A frissítésekben biztosított előzetes funkciók használata](../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).
> - Az 1602-es frissítés telepítése után a szolgáltatás típusa kiadott, még akkor is, ha az kiadás előtti jeleníti meg.
> - Ezután frissíti az 1602-es 1606, ha a szolgáltatás típusa láthatók, akár a keresztül kiadott kiadás előtti továbbra is.
> - Ha erre a 1606 1511-es verziójú frissíti, a szolgáltatás típusa kiadás előtti jeleníti meg.

 Ha további tájékoztatásra van szüksége arról, hogyan konfigurálható feltételes hozzáférés az Intune által beléptetett és kezelt eszközökhöz, vagy a tartományhoz kapcsolódó, és megfelelőség szempontjából még nem értékelt számítógépekhez, olvassa el a következő szakaszt: [Szolgáltatásokhoz való hozzáférés kezelése a System Center Configuration Managerben](../../protect/deploy-use/manage-access-to-services.md).  


## <a name="supported-services"></a>Támogatott szolgáltatások  

-   Exchange Online  

-   SharePoint Online  

## <a name="supported-pcs"></a>Támogatott számítógépek  

-   Windows 7  

-   Windows 8.1  

-   Windows 10 

## <a name="configure-conditional-access"></a>Feltételes hozzáférés konfigurálása  
 A feltételes hozzáférés beállításához először megfelelőségi szabályzatot kell létrehozni, majd konfigurálni kell a feltételes hozzáférési szabályzatot. A számítógépekre vonatkozó feltételes hozzáférési szabályzatok konfigurálásakor megkövetelheti, hogy a számítógépek megfeleljenek a megfelelőségi szabályzatnak ahhoz, hogy elérhessék az Exchange Online és a SharePoint Online szolgáltatást.  

### <a name="prerequisites"></a>Előfeltételek  

-   ADFS-szinkronizálás és O365-előfizetés. Az O365-előfizetés az Exchange Online és a SharePoint Online beállításához szükséges.  

-   Microsoft Intune-előfizetés. A Microsoft Intune-előfizetést a Configuration Manager konzolon lehet beállítani. Ehhez továbbra is hibrid telepítést kell használnia.  

 A számítógépeknek meg kell felelniük az alábbi követelményeknek:  

-   Az eszközöknek az Azure Directoryban történő regisztrálására vonatkozó[előfeltételek](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)   

     A megfelelőségi szabályzat útján regisztrálhatja a számítógépeket az Azure AD szolgáltatásban.  

    -   A Windows 8.1 és Windows 10 rendszerű számítógépeken az Active Directory csoportházirend segítségével konfigurálhatja az eszközöket az Azure AD szolgáltatásban történő automatikus regisztrálásra.  

    -   o   A Windows 7 rendszerű számítógépekre az eszközregisztrációs szoftvercsomagot kell telepítenie a System Center Configuration Manager segítségével. A [joined eszközök automatikus regisztrálásának](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) témakör további részleteket tartalmaz.  

-   Az Office 2013-at vagy az Office 2016-ot úgy kell használni , hogy a modern hitelesítés [engedélyezve](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)legyen.  

 Az alábbiakban ismertetett lépések Exchange Online-ra és a SharePoint Online-ra is vonatkoznak.  

### <a name="step-1-configure-compliance-policy"></a>1. lépés Megfelelőségi szabályzat konfigurálása  
 A Configuration Manager konzolon hozzon létre egy megfelelőségi szabályzatot, amely a következő szabályokat tartalmazza:  

-   Az Azure Active Directoryban való regisztráció megkövetelése: Ez a szabály ellenőrzi, hogy a felhasználói eszközök munkahelyi az Azure AD-tartományhoz, és ha nem, az Azure AD automatikusan regisztrálja az eszközt. Az automatikus regisztráció csak a Windows 8.1-es rendszerben támogatott. Windows 7 rendszerű számítógépeken telepítsen egy MSI-csomagot az automatikus regisztráció végrehajtásához. További részletek az [Automatic device registration with Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)(Automatikus eszközregisztráció az Azure Active Directoryban) című cikkben olvashatók.  

-   **Az összes szükséges frissítés telepítve egy bizonyos számú napnál régebbi határidő:** Ez a szabály ellenőrzi, hogy a felhasználó eszközén megtalálható (a kötelező automatikus frissítések szabályban megadott) minden szükséges frissítés határidőn és türelmi időszak, Ön által megadott belül, és automatikusan telepít minden függőben lévő kötelező frissítést.  

-   **BitLocker meghajtótitkosítás megkövetelése:** Ellenőrzi, hogy ha azt elsődleges meghajtója (pl. C:\\) az eszközön a BitLocker titkosítva van. Ha az elsődleges eszközön nincs engedélyezve a Bitlocker, a levelezéshez és a SharePoint szolgáltatásokhoz való hozzáférés le van tiltva.  

-   **Kártevőirtó megkövetelése:** Azt ellenőrzi, hogy ha a kártevőirtó szoftver (System Center Endpoint Protection vagy csak a Windows Defender) engedélyezve van és fut. Ha nincs engedélyezve a levelezéshez és a SharePoint szolgáltatásokhoz való hozzáférés le van tiltva.  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>2. lépés A feltételes hozzáférés hatásának kiértékelése  
 Futtassa a Megfelelőségi jelentés feltételes hozzáférésről nevű jelentést. Figyelés a jelentések szakaszban található > megfelelőség és beállítások kezelése. Látható rajta az összes eszköz megfelelőségi állapota.  A jelentésen nem megfelelőként feltüntetett eszközöket megakadályozza a rendszer az Exchange Online és a SharePoint Online elérésében.  

 ![CA&#95;compliance&#95;report](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Az Active Directory-alapú biztonsági csoportok beállítása  
 A feltételes hozzáférési szabályzatokkal a szabályzat típusától függően különböző felhasználói csoportokat célozhat meg. Ezek a csoportok tartalmazzák a célzott vagy a házirend alól mentesülő felhasználókat. Ha vonatkozik szabályzat egy felhasználóra, az általa használt összes eszköznek megfelelőnek kell lennie ahhoz, hogy elérhesse a szolgáltatást.  

 Active Directory-alapú biztonsági csoportok. Az ilyen felhasználócsoportokat szinkronizálni kell az Azure Active Directoryval. Ezeket a csoportokat az Office 365 Felügyeleti központban vagy az Intune-fiókportálon konfigurálhatja.  

 Minden házirendben két csoporttípust adhat meg. :  

-   **Megcélzott csoportok** -felhasználói csoportok, amelyekre a szabályzat érvényes. Ugyanabban a csoportban megfelelőségi és feltételes hozzáférési házirend egyaránt használhatók.  

-   **Kivétel alá eső csoportok** -felhasználói csoportokat, amelyek mentesülnek a szabályzat alól (nem kötelező)  
    Ha egy felhasználó mindkettőben szerepel, mentesül a szabályzat alól.  

     Csak a feltételes hozzáférési szabályzat által célzott csoportokat értékeli ki a rendszer.  

### <a name="step-3--create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>3. lépés  Feltételes hozzáférési szabályzat konfigurálása az Exchange Online-hoz és a SharePoint Online-hoz  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Ha az Exchange Online-hoz szeretne létrehozni szabályzatot, válassza a **Feltételes hozzáférési házirend engedélyezése Exchange Online-hoz**lehetőséget.  

     Ha a SharePoint Online-hoz szeretne létrehozni szabályzatot, válassza a **Feltételes hozzáférési házirend engedélyezése a SharePoint Online-hoz**lehetőséget.  

3.  A **Kezdőlap** **Hivatkozások** csoportjában kattintson a **Feltételes hozzáférési szabályzat konfigurálása az Intune-konzolon**hivatkozásra. Előfordulhat, hogy meg kell adnia annak a fióknak a felhasználónevét és jelszavát, amely a Configuration Manager és az Intune közötti kapcsolat létrehozására használatos.  

     Ekkor megnyílik az Intune felügyeleti konzolja.  

4.  Az Exchange online-hoz, a Microsoft Intune felügyeleti konzolon kattintson **házirend > feltételes hozzáférés > Exchange Online-szabályzat**.  

     A SharePoint online-hoz, a Microsoft Intune felügyeleti konzolon kattintson **házirend > feltételes hozzáférés > SharePoint Online-szabályzat**.  

5.  A Windows-számítógépekre vonatkozó követelményként válassza**Az eszközöknek meg kell felelniük a házirendnek**beállítást.  

6.  A **Megcélzott csoportok**területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre érvényes a házirend.  

    > [!NOTE]  
    >  Biztonsági azonos felhasználói csoportba előírásainak házirend és a feltételes hozzáférési szabályzathoz célcsoport telepítéséhez használható.  

     A **Kivétel alá eső csoportok**területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre nem érvényes a szabályzat.  

7.  Kattintson a **Mentés** gombra a szabályzat létrehozásához és mentéséhez.  

 Megfelelőségi információkat a System Center Configuration Manager Szoftverközpontban tekinthetik meg nem felelés miatt letiltott felhasználók, és indít el új megfelelőségi problémák szabályzatértékelést.  

<!---
##  <a name="bkmk_KnownIssues"></a> Known issues  
 You may see the following issues when using this feature:  

-   In this 1602 update,  the 5 day compliance is not enforced. Even if compliance check on the end-user's device has happened more than 5 days ago, users still can access Office 365 and SharePoint online.  

-   When a device is not compliant with the compliance policy, the reason is not automatically displayed. The end- user must go to the new Software Center to find the reason for non-compliance. The reason is displayed in the Device compliance section of the Software Center.  

-   Windows 10 users may see multiple access failures when trying to reach O365 and/or SharePoint online resources. Note that conditional access is not fully supported for Windows 10.  
--->
### <a name="see-also"></a>További információ  
 [Adatok és a helyinfrastruktúra a System Center Configuration Managerrel védelme](../../protect/understand/protect-data-and-site-infrastructure.md)

