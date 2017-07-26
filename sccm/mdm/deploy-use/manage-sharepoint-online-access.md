---
title: "SharePoint Online-hozzáférés kezelése |} Microsoft Docs"
description: "Útmutató: a onedrive vállalati verzió elérésének kezelése a System Center Configuration Manager SharePoint Online feltételes hozzáférési szabályzat segítségével."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
caps.latest.revision: 11
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: c564c1fc25c5156a2d9ddfa1b4123024c658bf61
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>SharePoint Online-hozzáférés kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Manager használata **SharePoint Online** fájljainak online, SharePoint-on található onedrive vállalati verzió hozzáférésének kezelése feltételes hozzáférési szabályzatot a megadott feltételek alapján.
A SharePoint Online-hoz a felsorolt platformok következő alkalmazásaiból szabályozhatja a hozzáférést:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android és iOS)  

-   Microsoft Word (Android és iOS)  

-   Microsoft Excel (Android és iOS)  

-   Microsoft PowerPoint (Android és iOS)  

-   Microsoft OneNote (Android és iOS)

Az Office asztali alkalmazásai hozzáférhetnek a SharePoint online-hoz futtató számítógépeken:  

-   Asztali Office 2013 vagy újabb verzió engedélyezett [modern hitelesítéssel](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) .  

-   Windows 7.0 vagy Windows 8.1  

> [!NOTE]  
>  Számítógépeknek kell a tartományhoz csatlakoztatott vagy meg kell felelniük az Intune-ban beállított szabályzatoknak.  



 Amikor egy célzott felhasználó támogatott alkalmazással (mint például a OneDrive) próbál csatlakozni egy fájlhoz az eszközéről, a következő kiértékelést hajtja végre a rendszer:  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 Ha csatlakozni szeretne a kívánt fájlokhoz, a OneDrive alkalmazást futtató eszköznek az alábbi feltételeknek kell megfelelnie:  

-   Kell léptetni a Microsoft Intune-nal vagy egy tartományhoz csatlakozó számítógép.  

-   Az eszközt regisztrálni kell az Azure Active Directoryban (Ez automatikusan megtörténik az eszköz Intune-nal való regisztrálásakor.  

     Tartományhoz csatlakozó számítógépek esetén be kell állítani az Azure Active Directoryban végzett [automatikus regisztrációt](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/).  

-   Meg kell felelnie az összes telepített Configuration Manager megfelelőségi szabályzatának  

 Az eszköz állapotát a rendszer az Azure Active Directoryban tárolja, amely a megadott feltételek alapján engedélyezi vagy letiltja a fájlok elérését.  

 Ha egy feltétel nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:  

-   Ha az eszköz nincs regisztrálva az Intune-ban vagy az Azure Active Directoryban, megjelenik egy üzenet, amely leírja, hogyan kell telepíteni a Vállalati portál alkalmazást és regisztrálni az eszközt.  

-   Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely irányítja a felhasználót, hogy az Intune webes portált, hol található információ a problémáról és annak megoldásáról.  

- Mobileszközök esetén:

  Letilthatja a SharePoint Online-hoz való **iOS** és **Android** böngészőkkel történő hozzáférést.  A hozzáférés csak a szabályzatnak megfelelő eszközök támogatott böngészőiről engedélyezett:
* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS és Android)

  A nem támogatott böngészők le lesznek tiltva.
-   Számítógépek esetén:  


    -   Ha a házirend úgy van beállítva, hogy megkövetelje a tartományhoz való csatlakozást, és a számítógép nem csatlakozik tartományhoz, megjelenik egy üzenet, amely jelzi, hogy kapcsolatba kell lépni a rendszergazdával.  

    -   Ha a szabályzat úgy van beállítva, hogy tartományhoz való csatlakozást vagy megfelelőséget követeljen meg, és a számítógép egyik követelménynek sem felel meg, egy utasításokat tartalmazó üzenet jelenik meg, amely leírja, hogyan telepítse a Vállalati portál alkalmazást és hogyan regisztrálja az eszközt.  

 A SharePoint Online-hozzáférés a következő alkalmazásokból tiltható le:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android és iOS)  

-   Microsoft Word (Android és iOS)  

-   Microsoft Excel (Android és iOS)  

-   Microsoft PowerPoint (Android és iOS)  

-   Microsoft OneNote (Android és iOS)  

## <a name="configure-conditional-access-for-sharepoint-online"></a>SharePoint Online feltételes hozzáférésének beállítása  

### <a name="step-1-configure-active-directory-security-groups"></a>1. lépés: Az Active Directory biztonsági csoportok beállítása  
 Kezdés előtt állítsa be az Azure Active Directory-alapú biztonsági csoportokat a feltételes hozzáférési házirendhez. Ezeket a csoportokat az **Office 365 Felügyeleti központban** vagy az **Intune-fiókportálon** konfigurálhatja. Ezek a csoportok tartalmazzák a célzott vagy a házirend alól mentesülő felhasználókat. Amikor egy felhasználóra házirend vonatkozik, az erőforrások eléréséhez az általa használt összes eszköznek meg kell felelnie a házirendnek.  

 Egy SharePoint Online-házirendben két csoporttípust adhat meg:  

-   **Megcélzott csoportok** â "", amelyhez a házirend hatálya alá eső felhasználók csoportjait tartalmazza  

-   **Kivétel alá eső csoportok** â "" (választható) a szabályzat alól mentesülő felhasználói csoportokat tartalmazza  

 Ha egy felhasználó mindkét csoportban szerepel, mentesül a házirend alól.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2. lépés: A megfelelőségi szabályzat konfigurálása és telepítése  
 Győződjön meg arról, hogy minden olyan eszközön létrehozza és regisztrálja a megfelelőségi házirendet, amelyet a SharePoint Online-házirenddel fog megcélozni.  

> [!NOTE]  
>  Az Intune-csoportok, vagy a Configuration Manager-gyűjtemények megfelelőségi szabályzatainak bevezetése, a feltételes hozzáférési házirendek az Azure Active Directory biztonsági csoportokat célozzák.  

 A megfelelőségi szabályzat konfigurálásának ismertetését lásd: [Eszközök megfelelőségi házirendjének kezelése a System Center Configuration Managerrel](../../protect/deploy-use/device-compliance-policies.md).  

> [!IMPORTANT]  
>  Ha nem telepített megfelelőségi házirendet, és engedélyez egy SharePoint Online-házirendet, az összes megcélzott eszköz hozzáférése engedélyezett lesz.  

 Ha készen áll, folytassa a **3. lépéssel**.  

###  <a name="BKMK_OneDrive"></a>3. lépés: A SharePoint Online-szabályzat beállítása  


 Ezután állítsa be úgy a házirendet, hogy csak a felügyelt és a feltételeknek megfelelő eszközök érhessék el a SharePoint Online-t. A házirend ezek után az Azure Active Directoryban tárolódik.

 >[!NOTE]
 >Az Azure AD felügyeleti konzol feltételes hozzáférési házirendet is létrehozhat. Az Azure AD felügyeleti konzol lehetővé teszi a feltételes hozzáférési házirendekkel (néven az eszközalapú feltételes hozzáférési szabályzatot az Azure AD) más feltételes hozzáférési szabályzatok, például többtényezős hitelesítés mellett az Intune eszköz létrehozásához. Is beállíthat feltételes hozzáférési házirendek külső vállalati alkalmazásokhoz, például a Salesforce, és be, hogy az Azure AD támogatja. További részletekért lásd: [Azure Active Directory eszközalapú feltételes hozzáférési házirend hozzáférés-vezérlés beállítása az Azure Active Directoryhoz csatlakoztatott alkalmazások](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/).  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Válassza a **Feltételes hozzáférési házirend engedélyezése SharePoint Online-hoz** lehetőséget.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  Az **Alkalmazás-hozzáférés** területen minden egyes platformhoz beállíthatja, hogy csak a házirendnek megfelelő eszközök férhessenek hozzá az Outlookhoz és a modern hitelesítést használó alkalmazásokhoz.  

    > [!TIP]  
    >  A **modern hitelesítéssel** Active Directory Authentication Library- (ADAL-) alapú bejelentkezés biztosítható az Office-ügyfelekhez.  
    >   
    >  -   Az ADAL-alapú hitelesítéssel az Office-ügyfelek végezhetnek böngészőalapú hitelesítést (más néven passzív hitelesítést).  A hitelesítéshez a felhasználó egy bejelentkezési weblapra van átirányítva.  
    > -   Az új bejelentkezési móddal olyan új forgatókönyvek használhatók, mint például a feltételes hozzáférés **eszközmegfelelőség** alapján, és az alapján, hogy **többtényezős hitelesítést** hajtottak-e végre.  
    >   
    >  Ebben a [cikkben](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) olvashatók további információk a modern hitelesítés működéséről.  

     A windows rendszerű számítógépek a Számítógépnek tartományhoz kell csatlakoznia, vagy regisztrálva az Intune-nal és a megfelelő. A következő követelményeket állíthatja be:  

    -   **Az eszközöknek tartományhoz kell csatlakozniuk vagy meg kell felelniük a házirendnek.** Ez azt jelenti, hogy a számítógépeknek tartományhoz kell csatlakoznia vagy megfelelőnek az Intune-ban beállított szabályzatoknak. Ha a számítógép egyik követelménynek sem nem felel meg, a felhasználótól regisztrálja az eszközt az Intune-ban.  

    -   **Az eszközöknek tartományhoz kell csatlakozniuk.** Ez azt jelenti, hogy a számítógépeknek egy tartományhoz kell csatlakozniuk az Exchange Online-hoz való hozzáféréshez. Ha a számítógép nem csatlakozik tartományhoz, a rendszer blokkolja a levelezéshez való hozzáférést és kéri a felhasználót, hogy lépjen kapcsolatba a rendszergazdával.  

    -   **Az eszközöknek meg kell felelniük a házirendnek.** Ez azt jelenti, hogy a számítógépeknek regisztrálva kell lenniük az Intune-ban és a megfelelő. Ha a számítógép nincs regisztrálva, megjelenik egy utasításokat tartalmazó üzenet, amely leírja, hogyan regisztrálja az eszközt.  

4.  A **böngészőalapú hozzáférés** SharePoint Online és onedrive vállalati verzió, ha szeretné, csak a támogatott böngészőkkel keresztül az Exchange online-hoz való hozzáférés engedélyezése: Safari (iOS), és Chrome (Android). A más böngészőkkel történő hozzáférés le lesz tiltva.  A OneDrive megadott alkalmazás-hozzáférési platformkorlátozásai itt is érvényesek.

    Az **Android** eszközök felhasználóinak engedélyezni kell a böngészőalapú hozzáférést.  A végfelhasználónak ehhez engedélyezni kell a â "œEnable a regisztrált eszközön böngésző Accessâ" beállítást az alábbiak szerint:
    1.  Nyissa meg a **Vállalati portál alkalmazást**.
    2.  Lépjen a **beállítások** lapot a három pontra (â "¦) vagy a hardver menü gombjára kattintva.
    3.  Kattintson a **Böngészőalapú hozzáférés engedélyezése** gombra.
    4.  A Chrome böngészőben jelentkezzen ki az Office 365-ből, majd indítsa újra a Chrome-ot.

    **iOS és Android** platformokon a szolgáltatás eléréséhez használt eszköz azonosításához az Azure Active Directory egy TLS-tanúsítványt (Transport Layer Security) rendel az eszközhöz.  Az eszköz az alábbi képernyőfelvételnek megfelelően megjeleníti a tanúsítványt, és a végfelhasználótól annak kiválasztását kéri. A végfelhasználónak a böngésző további használatához ki kell választania ezt a tanúsítványt.

     **iOS--**

     ![képernyőfelvétel a tanúsítvány kiválasztásának kéréséről egy ipad készüléken](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android--**

      ![képernyőfelvétel a tanúsítvány kiválasztásának kéréséről egy Android készüléken](media/mdm-browser-ca-android-cert-prompt.png)

4.  A **Kezdőlap** **Hivatkozások** csoportjában kattintson a **Feltételes hozzáférési szabályzat konfigurálása az Intune-konzolon**hivatkozásra. Előfordulhat, hogy meg kell adnia annak a fióknak a felhasználónevét és jelszavát, amely a Configuration Manager és az Intune közötti kapcsolat létrehozására használatos.  

     Ekkor megnyílik az Intune felügyeleti konzolja.  

5.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) kattintson a **Házirend** > **Feltételes hozzáférés** > **SharePoint Online-szabályzat** elemre.  

6.  Válassza **A SharePoint Online elérésének magakadályozása az alkalmazásoknak, ha az eszköz nem felel meg a szabályzatoknak** lehetőséget.  

7.  A **Megcélzott csoportok** területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre érvényes a házirend.  

8.  A **Kivétel alá eső csoportok** területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre nem érvényes a szabályzat.  

9. Amikor elkészült, kattintson a **Mentés** gombra.  

 Nem kell telepítenie a feltételes hozzáférési házirendet, azonnal érvénybe lép.  

 Lásd: [SharePoint Online-hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705844.aspx) a házirend az Intune-konzolon való figyeléséről kapcsolatos információkat.  

### <a name="see-also"></a>További információ  

 [A System Center Configuration Manager-szolgáltatásokhoz való hozzáférés kezelése](../../protect/deploy-use/manage-access-to-services.md)

