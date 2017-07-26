---
title: "E-mail hozzáférés kezelése |} Microsoft Docs"
description: "Útmutató az Exchange e-mail hozzáférésének kezelése a System Center Configuration Manager feltételes hozzáférés segítségével."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa648e73-5fb8-4818-ab57-7466ffaf888e
caps.latest.revision: 24
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: a5c2a8912cd2ef95a778b81d0b7f1f98315b8413
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-email-access-in-system-center-configuration-manager"></a>E-mail-hozzáférés kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a System Center Configuration Manager feltételes hozzáférését használva kezelheti az Ön által megadott feltételekre alapozva Exchange e-mailek elérését.  

A következők hozzáférését kezelheti:  

-   Helyszíni Microsoft Exchange  

-   Microsoft Exchange Online  

-   Dedikált Exchange Online

Az Exchange Online-hoz és a helyszíni Exchange-hez a hozzáférést a következő platformokon szabályozhatja a beépített e-mail ügyfélprogramból:  

-   Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0 és újabb verziók  

-   iOS 7.1-es és újabb verziók  

-   Windows Phone 8.1 és újabb verziók  

-   Levelezőalkalmazás a Windows 8.1-es és újabb verzióiban

Az Office asztali alkalmazásai hozzáférhetnek az Exchange online-hoz futtató számítógépeken:  

-   Asztali Office 2013 vagy újabb verzió engedélyezett [modern hitelesítéssel](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) .  

-   Windows 7.0 vagy Windows 8.1  

> [!NOTE]  
>  Számítógépeknek kell a tartományhoz csatlakoztatott vagy meg kell felelniük az Intune-ban beállított szabályzatoknak.  


## <a name="device-requirements"></a>Eszközkövetelmények
 Ha feltételes hozzáférést konfigurál, mielőtt a felhasználók az e-mail fiókjukhoz csatlakozhatnának, a használt eszköznek:  

-   Intune-ban regisztrált vagy egy tartományhoz csatlakozó számítógép.  

-   Az eszközt regisztrálni kell az Azure Active Directoryban (Ez automatikusan történik, ha az eszköz regisztrálva van az Intune (csak az Exchange Online esetén). Emellett az ügyfél Exchange ActiveSync-azonosítóját regisztrálni kell az Azure Active Directoryban (nem érvényes a helyszíni Exchange-hez csatlakozó Windows és Windows Phone rendszerű eszközökre).  

     Tartományhoz csatlakozó számítógépek esetén be kell állítani az Azure Active Directoryban való automatikus regisztrációt.  A [Szolgáltatásokhoz való hozzáférés kezelése a System Center Configuration Managerben](../../protect/deploy-use/manage-access-to-services.md) című témakör **számítógépek feltételes hozzáférésével foglalkozó szakaszában** megtalálható a számítógépek feltételes hozzáférésének engedélyezésére vonatkozó összes követelmény.  

-   Meg kell felelnie a Configuration Manager megfelelőségi szabályzatoknak eszközre telepített  

 Ha a feltételes hozzáférés egy feltétele nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:  

-   Ha az eszköz nincs regisztrálva az Intune-ban, vagy nincs regisztrálva az Azure Active Directoryban, megjelenik egy üzenet van utasításokat tartalmaz, telepítse a vállalati portál alkalmazást, regisztrálni az eszközt, és (Android és IOS rendszerű eszközök esetében), illetve aktiválja az e-mail fiókot, amely az eszköz Exchange ActiveSync-Azonosítóját az Azure Active Directoryban lévő eszközrekordhoz társítja.  

-   Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely irányítja a felhasználót, hogy az Intune webes portált, hol található információt a problémáról és annak megoldásáról.  

**Mobileszközök esetén:**

Az Exchange Online-on letilthatja az **Outlook Web Access-hez (OWA)** az **iOS-** és **Android-** eszközök böngészőin keresztül történő hozzáférést.  A hozzáférés csak a szabályzatnak megfelelő eszközök támogatott böngészőiről engedélyezett:

* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS és Android)

A nem támogatott böngészők le lesznek tiltva. Az OWA-alkalmazások nem támogatottak az iOS és Android rendszerű eszközök számára.  Ezeket az ADFS jogcímszabályai között le kell tiltani:
* Állítsa be az ADFS-jogcímszabályokat a nem modern hitelesítési protokollok blokkolására. Lépésenkénti útmutatás: 3. forgatókönyv – [Az O365-höz való hozzáférés teljes letiltása a böngészőalapú alkalmazások kivételével](https://technet.microsoft.com/library/dn592182.aspx).

 **Számítógépek esetén:**  

-   Ha a feltételes hozzáférési szabályzat **tartományhoz való csatlakozást** vagy **megfelelőséget**követel meg az engedélyezéshez, megjelenik egy utasításokat tartalmazó üzenet, amely leírja, hogyan regisztrálja az eszközt. Ha a számítógép egyik követelménynek sem nem felel meg, a rendszer regisztrálja az eszközt az Intune-nal kér a felhasználótól.  

-   Ha a feltételes hozzáférési szabályzat követelménye úgy van beállítva, hogy csak a tartományhoz csatlakozó windowsos eszközöket engedélyezze, az eszköz le lesz tiltva, és megjelenik egy üzenet, amely jelzi, hogy kapcsolatba kell lépni a rendszergazdával.  

 A következő platformokon blokkolhatja az Exchange e-mail fiókok elérését az eszközök beépített Exchange ActiveSync levelezési ügyfeléről:  

-   Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0 és újabb verziók  

-   iOS 7.1-es és újabb verziók  

-   Windows Phone 8.1 és újabb verziók  

-   A **Posta** alkalmazás a Windows 8.1-ben és az újabb verziókban  

 Az iOS és Android rendszerhez készült Outlook alkalmazás és az Outlook 2013 és újabb asztali alkalmazás csak az Exchange Online-hoz támogatott.  

 A **a helyszíni Exchange connector** Configuration Manager és az Exchange között a feltételes hozzáférés működéséhez szükség.  

 A helyszíni Exchange-hez a Configuration Manager konzolról egy feltételes hozzáférési házirend konfigurálása Ha a feltételes hozzáférési házirend konfigurálása az Exchange online-hoz, a megkezdéséhez a Configuration Manager konzol, amely elindítja az Intune-konzolon, ahol befejezhetői a folyamatot.  

## <a name="configure-conditional-access"></a>Feltételes hozzáférés konfigurálása
### <a name="step-1-evaluate-the-effect-of-the-conditional-access-policy"></a>1. lépés: A feltételes hozzáférési szabályzat hatásának értékelése  
 Miután konfigurálta a **a helyszíni Exchange connector**, használhatja a Configuration Manager**eszközök listája feltételes hozzáférési állapot szerint** jelentést használva azonosíthatja azokat az eszközöket, amelyek Exchange-hozzáférése a feltételes hozzáférési házirend konfigurálását követően le lesz tiltva. A jelentéshez az alábbiak szükségesek:  

-   Intune-előfizetés  

-   A szolgáltatáskapcsolati pont konfigurálása és telepítése  

 A jelentés paramétereiben válassza ki a kiértékelni kívánt Intune csoportot és szükség esetén azon eszközplatformokat, amelyekre a házirendet alkalmazza.  

 További információk a jelentések futtatásáról: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).  

 A jelentés futtatása után vizsgálja meg a következő négy oszlopot annak meghatározásához, hogy a felhasználók le lesznek-e tiltva:  

-   **Kezelési csatorna** -azt jelzi, hogy az eszköz Intune-ban, az Exchange ActiveSync vagy mindkettő kezeli.  

-   **Aad-ben regisztrált** -azt jelzi, hogy az eszköz regisztrálva van-e az Azure Active Directoryban (vagyis munkahelyi csatlakoztatással).  

-   **Megfelelő** -azt jelzi, hogy az eszköz megfelel-e a telepített megfelelőségi szabályzatoknak.  

-   **EAS engedélyezve** – iOS és Android-eszközök kell lennie az Exchange ActiveSync-Azonosítójának társított Azure Active Directoryban található eszközregisztrációs rekorddal. Ez akkor történik meg, amikor a felhasználó a **Levelezés aktiválása** hivatkozásra kattint a karanténba helyezett e-mailben.  

    > [!NOTE]  
    >  Windows Phone-telefonok esetén ebben az oszlopban mindig szerepel érték.  

 A célcsoporthoz vagy -gyűjteményhez tartozó eszközök Exchange-hozzáférése le lesz tiltva, ha az oszlop értékei nem egyeznek a következő táblázatban lévő értékekkel:  

|Kezelési csatorna|Az AAD-ben regisztrált|megfelelőséget|EAS engedélyezve|Eredményművelet|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**A Microsoft Intune és az Exchange ActiveSync kezeli**|Igen|Igen|**Igen** vagy **Nem** van megjelenítve|Az e-mail hozzáférés engedélyezett|  
|Bármely más érték|Nem|Nem|Nem jelenik meg érték|Az e-mail hozzáférés le van tiltva|  

 Exportálhatja a jelentés tartalmát, és az **E-mail cím** oszlop segítségével értesítheti a felhasználókat arról, hogy le lesznek tiltva.  

### <a name="step-2-configure-user-groups-or-collections-for-the-conditional-access-policy"></a>2. lépés: Felhasználói csoportok vagy gyűjtemények, a feltételes hozzáférési házirend konfigurálása  
 A feltételes hozzáférési szabályzatokkal a szabályzat típusától függően különböző felhasználói csoportokat vagy gyűjteményeket célozhat meg. Ezek a csoportok tartalmazzák a célzott vagy a házirend alól mentesülő felhasználókat. Amikor egy felhasználóra házirend vonatkozik, az általa használt összes eszköznek megfelelőnek kell lennie az e-mailek eléréséhez.  

-   **Az Exchange Online házirendhez** – az Azure Active Directory biztonsági felhasználói csoportok. Ezeket a csoportokat az **Office 365 Felügyeleti központban**vagy az **Intune-fiókportálon**konfigurálhatja.  

-   **A helyszíni Exchange-szabályzat** – a Configuration Manager felhasználói gyűjteményt. Ezek az **Eszközök és megfelelőség** munkaterületen konfigurálhatók.  

 Minden házirendben két csoporttípust adhat meg:  

-   **Megcélzott csoportok** -felhasználói csoportok vagy gyűjtemények, amelyeken a házirend érvényben van  

-   **Kivétel alá eső csoportok** -felhasználói csoportok vagy gyűjtemények, amelyek mentesülnek a házirend alól (választható)  

 Ha egy felhasználó mindkettőben szerepel, mentesül a szabályzat alól.  

 Csak a feltételes hozzáférési szabályzat által célzott csoportokat vagy gyűjteményeket értékeli ki a rendszer az Exchange-hozzáférés szempontjából.  

### <a name="step-3-configure-and-deploy-a-compliance-policy"></a>3. lépés: A megfelelőségi szabályzat konfigurálása és telepítése  
 Győződjön meg arról, hogy minden olyan eszközön létrehozott és telepített megfelelőségi házirendet, amelyet az Exchange feltételes hozzáférési házirenddel fog megcélozni.  

 A megfelelőségi szabályzat konfigurálásának ismertetését lásd: [Eszközök megfelelőségi házirendjének kezelése a System Center Configuration Managerrel](device-compliance-policies.md).  

> [!IMPORTANT]  
>  Ha nem telepített megfelelőségi házirendet, és engedélyez egy Exchange feltételes hozzáférési házirendet, az összes megcélzott eszköz hozzáférése engedélyezett lesz.  

 Ha készen áll, folytassa a **4. lépéssel**.  

### <a name="step-4-configure-the-conditional-access-policy"></a>4. lépés: A feltételes hozzáférési szabályzat konfigurálása  

#### <a name="for-exchange-online-and-tenants-in-the-new-exchange-online-dedicated-environment"></a>Exchange Online (és az új dedikált Exchange Online-környezetbeli bérlők) esetén

>[!NOTE]
>Az Azure AD felügyeleti konzol feltételes hozzáférési házirendet is létrehozhat. Az Azure AD felügyeleti konzol lehetővé teszi a feltételes hozzáférési házirendekkel (néven az eszközalapú feltételes hozzáférési szabályzatot az Azure AD) más feltételes hozzáférési szabályzatok, például többtényezős hitelesítés mellett az Intune eszköz létrehozásához. Is beállíthat feltételes hozzáférési házirendek külső vállalati alkalmazásokhoz, például a Salesforce, és be, hogy az Azure AD támogatja. További részletekért lásd: [Azure Active Directory eszközalapú feltételes hozzáférési házirend hozzáférés-vezérlés beállítása az Azure Active Directoryhoz csatlakoztatott alkalmazások](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/).

 Az Exchange Online feltételes hozzáférési házirendjei a következő folyamatot használják annak kiértékeléséhez, hogy engedélyezzék vagy letiltsák-e az eszközöket.  

 ![ConditionalAccess8&#45;1](media/ConditionalAccess8-1.png)  

 Az e-mailek eléréséhez az eszköznek:  

-   Az Intune-ban  

-   Számítógépek kell tartományhoz csatlakoztatva, vagy alkalmas a megfelelőnek minősülő regisztrált az Intune-ban beállított szabályzatoknak.  

-   Az eszközt regisztrálni kell az Azure Active Directoryban (Ez automatikusan megtörténik az eszköz Intune-nal való regisztrálásakor.  

     Tartományhoz csatlakozó számítógépek esetén be kell állítani [az eszköz automatikus regisztrációját](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) az Azure Active Directoryban.  

-   Aktiválta az e-mail fiókot, amely az eszköz Exchange ActiveSync-Azonosítóját az (iOS és Android-eszközökre vonatkozik) Azure Active Directoryban lévő eszközrekordhoz társítja.  

-   Meg kell felelnie az összes telepített megfelelőségi szabályzatnak.  

 Az eszköz állapotát a rendszer az Azure Active Directoryban tárolja, amely engedélyezi vagy letiltja az e-mailek elérését az értékelt feltételek alapján.  

 Ha egy feltétel nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:  

-   Ha az eszköz nincs regisztrálva, vagy nincs az Azure Active Directoryban regisztrálva, megjelenik egy utasításokat tartalmazó üzenet, amely leírja, hogyan telepítse a Vállalati portál alkalmazást és regisztrálja az eszközt  

-   Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely a felhasználót az Intune vállalati portál webhelyére vagy a vállalati portál alkalmazásba irányítja, hol található információ a problémáról és annak megoldásáról.  

-   Számítógépek esetén:  

    -   Ha a házirend úgy van beállítva, hogy megkövetelje a tartományhoz való csatlakozást, és a számítógép nem csatlakozik tartományhoz, megjelenik egy üzenet, amely jelzi, hogy kapcsolatba kell lépni a rendszergazdával.  

    -   Ha a szabályzat úgy van beállítva, hogy tartományhoz való csatlakozást vagy megfelelőséget követeljen meg, és a számítógép egyik követelménynek sem felel meg, egy utasításokat tartalmazó üzenet jelenik meg, amely leírja, hogyan telepítse a Vállalati portál alkalmazást és hogyan regisztrálja az eszközt.  

 Megjelenik az üzenet az eszközön az Exchange Online-felhasználók és az új dedikált Exchange Online-környezetbeli bérlők számára, és a helyszíni Exchange és az örökölt dedikált Exchange Online eszközök felhasználói e-mailben kapják meg.  

> [!NOTE]  
>  A Configuration Manager feltételes hozzáférési szabályai felülírják, engedélyezési, blokkolási és karanténba helyezik az Exchange Online felügyeleti konzolon meghatározott szabályokat.  

> [!NOTE]  
>  A feltételes hozzáférési szabályzatot az Intune-konzolon kell konfigurálni. Ehhez először a Configuration Manageren keresztül kell elérnie az Intune-konzolt. Ha a rendszer kéri, jelentkezzen be a Configuration Manager és az Intune közötti szolgáltatáskapcsolati pont telepítése során használt hitelesítő adatokkal.  

##### <a name="to-enable-the-exchange-online-policy"></a>Az Exchange Online-házirend engedélyezése  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Bontsa ki a **Megfelelőségi beállítások**, majd a **Feltételes hozzáférés**csomópontot, és kattintson az **Exchange Online**elemre.  

3.  A **Kezdőlap** **Hivatkozások** csoportjában kattintson a **Feltételes hozzáférési szabályzat konfigurálása az Intune-konzolon**hivatkozásra. Szükség lehet a felhasználó a felhasználónév és a Configuration Manager valamelyik globális rendszergazdáját összekapcsolta az Intune-ba való csatlakozáshoz használt fiók jelszavát.  

     Megnyitja az Intune felügyeleti konzolon.  

4.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com)kattintson a **Házirend** > **Feltételes hozzáférés** > **Exchange Online-szabályzat**lehetőségre.  

     ![HybridOnlineSetupIntune](media/HybridOnlineSetupIntune.png)  

5.  Az **Exchange Online-szabályzat** lapon válassza a **Feltételes hozzáférési házirend engedélyezése Exchange Online-hoz**lehetőséget. Ha bejelöli ezt a beállítást, az eszköznek kompatibilisnek kell lennie. Ha a beállítás nincs bejelölve, a feltételes hozzáférés nem lesz alkalmazva.  

    > [!NOTE]  
    >  Ha nem telepített megfelelőségi házirendet, és engedélyezi az Exchange Online-házirendet, a rendszer az összes megcélzott eszközt megfelelőként jelenti.  
    >   
    >  A megfelelőségi állapottól függetlenül a szabályzat által megcélzott összes felhasználónak kell léptetnie az eszközét az Intune-nal.  

6.  Az **Alkalmazás hozzáférése**lehetőségnél az Outlook és az egyéb alkalmazások esetén dönthet úgy, hogy kizárólag a megfelelő eszközökre korlátozza a hozzáférést.  A Windows-eszközöknek vagy tartományhoz kell csatlakozniuk, vagy regisztrálva kell lenniük az Intune-ban.  

    > [!TIP]  
    >  A **modern hitelesítéssel** Active Directory Authentication Library- (ADAL-) alapú bejelentkezés biztosítható az Office-ügyfelekhez.  
    >   
    >  -   Az ADAL-alapú hitelesítéssel az Office-ügyfelek végezhetnek böngészőalapú hitelesítést (más néven passzív hitelesítést).  A hitelesítéshez a felhasználó egy bejelentkezési weblapra van átirányítva.  
    > -   Az új bejelentkezési móddal olyan új forgatókönyvek használhatók, mint például a feltételes hozzáférés **eszközmegfelelőség** alapján, és az alapján, hogy **többtényezős hitelesítést** hajtottak-e végre.  
    >   
    >  Ebben a [cikkben](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) olvashatók további információk a modern hitelesítés működéséről.  

     Ha az Exchange Online-t a Configuration Managerrel és az Intune-nal együtt használja, nemcsak mobileszközök, hanem asztali számítógépek feltételes hozzáférését is kezelheti. A számítógépeknek egy tartományhoz kell csatlakoznia, vagy regisztrálva kell lennie az Intune-ban. A következő követelményeket állíthatja be:  

    -   **Az eszközöknek tartományhoz kell csatlakozniuk vagy meg kell felelniük a házirendnek.** A számítógépeknek tartományhoz kell csatlakozniuk, vagy meg kell felelniük a szabályzatoknak. A számítógép nem felel meg egyik követelménynek sem, ha a felhasználótól regisztrálja az eszközt az Intune-ban.  

    -   **Az eszközöknek tartományhoz kell csatlakozniuk.** A számítógépeknek tartományhoz kell csatlakozniuk az Exchange Online-hoz való hozzáféréshez. Ha a számítógép nem csatlakozik tartományhoz, a rendszer blokkolja a levelezéshez való hozzáférést, és kéri a felhasználót, hogy lépjen kapcsolatba a rendszergazdával.  

    -   **Az eszközöknek meg kell felelniük a házirendnek.** Számítógépeknek regisztrálva kell lenniük az Intune-ban és a megfelelő. Ha a számítógép nincs regisztrálva, megjelenik egy, a regisztráció lépéseit bemutató üzenet.  

7.  A **az Outlook web access (OWA)**, ha szeretné, csak a támogatott böngészőkkel keresztül Exchange online-hoz való hozzáférés engedélyezése: Safari (iOS), és Chrome (Android). A más böngészőkkel történő hozzáférés le lesz tiltva. Az Outlookhoz megadott alkalmazás-hozzáférési platformkorlátozások itt is érvényesek.

    Az **Android** eszközök felhasználóinak engedélyezni kell a böngészőalapú hozzáférést.  A végfelhasználónak ehhez engedélyezni kell a regisztrált eszköz a "Böngészőalapú hozzáférés engedélyezése" beállítást az alábbiak szerint:
     1. Nyissa meg a **Vállalati portál alkalmazást**.
     2. Lépjen a **beállítások** lapot a három pontra (...) vagy a hardver menü gombjára kattintva.
      3.    Kattintson a **Böngészőalapú hozzáférés engedélyezése** gombra.
      4.    A Chrome böngészőben jelentkezzen ki az Office 365-ből, majd indítsa újra a Chrome-ot.

     **iOS és Android** platformokon a szolgáltatás eléréséhez használt eszköz azonosításához az Azure Active Directory egy TLS-tanúsítványt (Transport Layer Security) rendel az eszközhöz.  Az eszköz az alábbi képernyőfelvételnek megfelelően megjeleníti a tanúsítványt, és a végfelhasználótól annak kiválasztását kéri. A végfelhasználónak a böngésző további használatához ki kell választania ezt a tanúsítványt.

     **iOS--**

     ![képernyőfelvétel a tanúsítvány kiválasztásának kéréséről egy ipad készüléken](media/mdm-browser-ca-ios-cert-prompt_v2.png)

    **Android--**

    ![képernyőfelvétel a tanúsítvány kiválasztásának kéréséről egy Android készüléken](media/mdm-browser-ca-android-cert-prompt.png)

7.  Az**Exchange ActiveSync-levelezőalkalmazások**esetében blokkolhatja a levelezőalkalmazások hozzáférését az Exchange Online-hoz, ha az eszköz nem megfelelő, illetve megadhatja, hogy engedélyezi vagy letiltja a levelezéshez való hozzáférést, ha az Intune nem tudja kezelni az eszközt.  

8.  A **Megcélzott csoportok**területen válassza ki azon felhasználók Active Directory biztonsági csoportjait, akikre érvényes a házirend.  

    > [!NOTE]  
    >  A Megcélzott csoportokban lévő felhasználók esetében az Intune-házirendek leváltják az Exchange-szabályokat és -házirendeket.  
    >   
    >  Az Exchange csak a következő esetekben érvényesíti az engedélyezési, blokkolási és karanténba helyezési Exchange-szabályokat és az Exchange-házirendeket:  
    >   
    >  -   A felhasználó nem rendelkezik Intune-licenccel.  
    > -   A felhasználó rendelkezik Intune-licenccel, de egy, a feltételes hozzáférési házirendben megcélzott biztonsági csoportnak sem tagja.  

9. A **Kivétel alá eső csoportok**területen válassza ki azon felhasználók Active Directory biztonsági csoportjait, akikre nem érvényes a házirend. Ha egy felhasználó a megcélzott és a mentesített csoportban is szerepel, mentes a szabályzat alól, és hozzáfér a levelezéséhez.  

10. Amikor végzett, kattintson a **Mentés**gombra.  

-   Nem kell telepítenie a feltételes hozzáférési szabályzatot, az azonnal érvénybe lép.  

-   Miután egy felhasználó e-mail fiókot hoz létre, azonnal letiltja az eszközt.  

-   Ha egy letiltott felhasználó regisztrálja az eszközt az Intune-ban (vagy javítja a nem megfelelőséget), e-mailek elérését rendszer percen belül feloldja 2.  

-   Ha a felhasználó megszünteti az eszköz regisztrációját, körülbelül 6 óra múlva letiltja a rendszer a levelezést.  

### <a name="for-exchange-on-premises-and-tenants-in-the-legacy-exchange-online-dedicated-environment"></a>A helyszíni Exchange (és az örökölt dedikált Exchange Online-környezetbeli bérlők) esetén  
 A helyszíni Exchange és az örökölt dedikált Exchange Online-környezetbeli bérlők feltételes hozzáférési házirendjei a következő folyamatot használják annak kiértékeléséhez, hogy engedélyezzék vagy letiltsák az eszközöket.  

 ![ConditionalAccess8&#45;2](media/ConditionalAccess8-2.png)  

##### <a name="to-enable-the-exchange-on-premises-policy"></a>A helyszíni Exchange-házirend engedélyezése  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Bontsa ki a **Megfelelőségi beállítások**, majd a **Feltételes hozzáférés**csomópontot, és kattintson a **Helyi Exchange**elemre.  

3.  A **Kezdőlap** lap **Helyi Exchange** csoportjában kattintson a **Feltételes hozzáférési házirend konfigurálása**elemre.  

4.  A**Configuration Manager 1602-es verziójától kezdve**a **Feltételes hozzáférési házirend konfigurálása varázsló**  **Általános**lapján megadhatja, hogy szeretné-e felülbírálni az Exchange Active Sync alapértelmezett szabályát. Kattintson erre a beállításra, ha azt szeretné, hogy a regisztrált és megfelelő eszközök mindig hozzáférjenek az e-mailekhez akkor is, ha az alapértelmezett szabály karanténba helyezésre vagy a hozzáférés letiltására van beállítva.  

    > [!NOTE]  
    >  Az alapértelmezett felülbírálás esetében probléma jelentkezik az Android-eszközökön. Ha az Exchange-kiszolgáló alapértelmezett hozzáférési szabály a **Tiltás** értékre van beállítva, és az Exchange feltételes hozzáférési szabályzata engedélyezve van az alapértelmezett szabályt felülbíráló kapcsolóval, akkor előfordulhat, hogy a megcélzott felhasználók Android-eszközeinek tiltása nem lesz feloldva az Intune-ba való regisztrálás és a megfelelőség teljesítése után.  A probléma megoldásához az Exchange alapértelmezett hozzáférési szabályát állítsa **Karantén**értékűre. Az eszköz alapértelmezés szerint nem férhet hozzá az Exchange-hez, és a rendszergazda lekérheti az Exchange-kiszolgálóról a karanténba helyezett eszközök listáját tartalmazó jelentést.  

     Ha nem adott meg értesítési e-mail fiókot az Exchange-összekötő beállításakor, figyelmeztetés jelenik meg ezen a lapon, és a **Tovább** gomb le lesz tiltva.  A folytatás előtt konfigurálja az értesítési e-mail beállításait az Exchange-összekötőben, majd a művelet befejezéséhez térjen vissza a **Feltételes hozzáférési házirend konfigurálása varázsló** lapjára.  

     ![HybridCondAccessWiz1](media/HybridCondAccessWiz1.PNG)  

     Kattintson a **Tovább**gombra.  

5.  A **Célgyűjtemények** lapon vegyen fel legalább egy felhasználói gyűjteményt. Exchange eléréséhez a gyűjteményekbe tartozó felhasználóknak regisztrálniuk kell az eszközeiket az Intune-nal, és is meg kell felelniük minden megfelelőségi szabályzatnak, amelyet központilag telepített.  

     ![HybridCondAccessWiz2](media/HybridCondAccessWiz2.PNG)  

     Kattintson a **Tovább**gombra.  

6.  A **Kivételezett gyűjtemények** lapon bármilyen felhasználói gyűjteményt felvehet, amelyet mentesíteni kíván a házirend alól. Ebben a csoportokban lévő felhasználóknak nem kell regisztrálniuk az eszközeiket az Intune-ban, és nem kell Exchange eléréséhez meg kell felelniük a telepített megfelelőségi szabályzatoknak.  

     ![HybridCondAccessWiz3](media/HybridCondAccessWiz3.png)  

     Ha egy felhasználó a megcélzott és a mentesített listában is szerepel, mentesül a feltételes hozzáférési házirend alól.  

     Kattintson a **Tovább** gombra.  

7.  Az a **felhasználói értesítés szerkesztése** lapján konfigurálhatja az e-maileket, Intune által a felhasználók (az Exchange által küldött e-mail) mellett az eszköz letiltásának feloldására vonatkozó utasításokkal.  

     Szerkesztheti az alapértelmezett üzenetet, és HTML-címkékkel formázhatja a szöveg megjelenését. Az alkalmazottakat előzetesen is értesítheti e-mailben a jövőbeli változásokról, és útmutatást adhat nekik az eszközük regisztrációjával kapcsolatban.  

     ![HybridCondAccessWiz4](media/HybridCondAccessWiz4.PNG)  

    > [!NOTE]  
    >  Mivel a javítással kapcsolatos utasításokat tartalmazó Intune értesítő e-mail a felhasználó Exchange-postaládájába kerül, abban az esetben, ha a felhasználó eszköze le van tiltva az e-mail üzenet megérkezése előtt, egy tiltott eszközzel vagy más módon használhatnak Exchange-hozzáférést, és tekintheti meg az üzenetet.  

    > [!NOTE]  
    >  Konfigurálnia kell az értesítő e-mail elküldéséhez használt fiókot, hogy az Exchange elküldhesse az értesítő e-mailt. Ezt az Exchange Server Connector konfigurálásakor végezheti el.  
    >   
    >  További részletekért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

     Kattintson a **Tovább**gombra.  

8.  Az  **Összefoglalás** lapon ellenőrizze a beállításokat, majd hajtsa végre a varázsló lépéseit.  

-   Nem kell telepítenie a feltételes hozzáférési házirendet, azonnal érvénybe lép.  

-   Miután a felhasználó beállítja az Exchange ActiveSync-profilt, az eszköz (ha az Intune által nem felügyelt) letiltása 1 – 3 órát vehet igénybe.  

-   Ha egy letiltott felhasználó ezután regisztrálja az eszközt az Intune-ban (vagy javítja a nem megfelelőséget), e-mailek elérését lesz feloldva 2 percen belül.  

-   Ha a felhasználó megszünteti-regisztrálja az Intune-ban az eszköz letiltása 1 – 3 órát vehet igénybe.  

### <a name="see-also"></a>További információ  
 [A System Center Configuration Manager-szolgáltatásokhoz való hozzáférés kezelése](../../protect/deploy-use/manage-access-to-services.md)

