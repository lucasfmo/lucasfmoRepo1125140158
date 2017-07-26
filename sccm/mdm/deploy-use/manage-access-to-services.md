---
title: "Feltételes hozzáférés |} Microsoft Docs"
description: "Ismerje meg, hogyan használható a feltételes hozzáférés a System Center Configuration Managerben biztosíthatja a levelezés és más szolgáltatások védelmét."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
caps.latest.revision: 26
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: d6933a331bb229f7e378e8f0bfa511f6b0553ae9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>Szolgáltatásokhoz való hozzáférés kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>Feltételes hozzáférés a System Center Configuration Managerben
Használjon **feltételes hozzáférés** biztosíthatja a levelezés és más szolgáltatások attól függően, hogy az Ön által megadott feltételek alapján a Microsoft Intune-nal regisztrált eszközök segítségével.  

 További információ **feltételes hozzáféréssel a felügyelt számítógépeken a System Center Configuration Managerrel** és megfelelőségi kiértékelése [System Center Configuration Manager által felügyelt számítógépek esetében az Office 365-szolgáltatásokhoz való hozzáférés kezelése](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  


 Egy tipikus feltételes hozzáférési folyamat a következőhöz hasonlóan néz ki:  

 ![ConditionalAccess4](media/ConditionalAccess4.png)  

 Feltételes hozzáféréssel a következő szolgáltatásokhoz való hozzáférést kezelheti:  

-   Helyszíni Microsoft Exchange  

-   Microsoft Exchange Online  

-   Dedikált Exchange Online  

-   SharePoint Online  

-   Skype Vállalati online verzió

-   Dynamics CRM Online

 Feltételes hozzáférés bevezetéséhez, a Configuration Manager két házirendtípust kell konfigurálnia:  

-   A**megfelelőségi szabályzatok** felhasználógyűjteményekre alkalmazható nem kötelező szabályzatok, amelyekkel például az alábbi beállítások értékelhetők ki:  

    -   PIN-kód  

    -   Titkosítás  

    -   Az, hogy az eszközt feltörték-e  

    -   Hogy az eszközön a levelezés kezelése egy Configuration Manager vagy az Intune-házirend  

     **Ha nincs kompatibilitási házirend központi telepítése egy eszköznél történik, akkor az esetleges alkalmazható feltételes hozzáférési házirendek kompatibilisként fogják kezelni az eszközt**.  

-   **Feltételes hozzáférési házirendek** egy adott szolgáltatáshoz állíthatók be, és adja meg a szabályokat, például az Azure Active Directory biztonsági felhasználói csoportok vagy a Configuration Manager felhasználói gyűjtemények vonatkozzon, illetve mentesüljenek.  

     A Configuration Manager konzolján a helyszíni Exchange feltételes hozzáférési házirend konfigurálása Azonban az Exchange Online vagy SharePoint Online házirendjének konfigurálásakor megnyílik az Intune felügyeleti konzolon, ahol konfigurálhatja a házirendet.  

     Egyéb Intune-ban vagy a Configuration Manager eltérően nem kell feltételes hozzáférési szabályzatokat. Ehelyett ezeket csak egyszer kell konfigurálnia, és ezzel az összes megcélzott felhasználóra alkalmazza őket.  

 Ha az eszközök nem felelnek meg az Ön által konfigurált feltételeknek, a rendszer végigvezeti a felhasználót az eszköz beléptetésének és az eszköz kompatibilitását megakadályozó probléma megoldásának a folyamatán.  

**Mielőtt** feltételes hozzáférés használatának megkezdése, győződjön meg arról, hogy rendelkezik-e a megfelelő **követelmények** helyen:  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Exchange Online (a megosztott több-bérlős környezet használatával) vonatkozó követelmények
Az Exchange Online-hoz való feltételes hozzáférés a következőket futtató eszközöket támogatja:
-   Windows 8.1 és újabb verzióiban (Regisztrálás az Intune-nal)
-   Windows 7.0 vagy Windows 8.1 (Ha tartományhoz csatlakozik)
-   Windows Phone 8.1 és újabb verziók
-   iOS 7.1-es és újabb verziók
-   Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0 és újabb verziók

 **Emellett**:
-   Az eszközöknek meg kell munkahelyhez csatlakoztatott, amely regisztrálja az eszközt az Azure Active Directory Eszközregisztrációs szolgáltatással (AAD DRS).<br />     
- A tartományhoz csatlakozó számítógépeket automatikusan regisztrálni kell az Azure Active Directoryban csoportos házirenden vagy MSI-n keresztül.

  A jelen témakör **Feltételes hozzáférés a PC-ken** című szakasza a számítógép feltételes hozzáférésének engedélyezéséhez szükséges követelményeket ismerteti.<br />     
  Az AAD DRS szolgáltatás automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azok az ügyfelek, akik már telepítették az ADFS eszközregisztrációs szolgáltatását, nem fogják látni a regisztrált eszközöket a helyszíni Active Directoryban.
-   Olyan Office 365-előfizetéssel, amely tartalmazza az Exchange Online (például E3) kell használnia, és a felhasználóknak licenccel kell rendelkezniük az Exchange online-hoz.
-   A választható **Exchange Server-összekötő** nem kötelező, és a Configuration Manager kapcsolódik a Microsoft Exchange online-hoz, és a segítségével figyelheti az eszközadatokat a Configuration Manager konzolon keresztül (lásd: [mobileszközök kezelése a System Center Configuration Manager és az Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
Feltételes házirendek vagy feltételes hozzáférési házirendek használatához nincs szükség az összekötő használatára, szükség van rá azonban az olyan jelentések futtatásához, amelyek segítenek a feltételes hozzáférés hatásának vizsgálatában.

## <a name="requirements-for-exchange-online-dedicated"></a>Dedikált Exchange Online követelményei
A dedikált Exchange Online-hoz való feltételes hozzáférés a következőket futtató eszközöket támogatja:
-   Windows 8 és újabb verzióiban (Regisztrálás az Intune-nal)
-   Windows 7.0 vagy Windows 8.1 (Ha tartományhoz csatlakozik)

  A tartományhoz csatlakozó számítógépekhez csak az új dedikált Exchange Online-környezet bérlői kapnak feltételes hozzáférést.
-   Windows Phone 8 és újabb verziók
-   Bármely iOS-eszközök Exchange ActiveSync (EAS) típusú e-mail ügyfélprogramot használ
-   Android 4 és újabb verziók.
-   A bérlők számára a **örökölt dedikált Exchange Online-környezetbeli**:    

  Kell használnia a **Exchange Server-összekötő** amely Configuration Manager kapcsolódik a helyszíni Microsoft Exchange. Ez lehetővé teszi a mobileszközök kezelését, és engedélyezi a feltételes hozzáférést (lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
-   A bérlők számára a **új dedikált Exchange Online-környezetbeli**:     
  A választható **Exchange Server-összekötő** Configuration Manager kapcsolódik a Microsoft Exchange online-hoz, és segít az eszközinformációk kezelésében (lásd: [mobileszközök kezelése a System Center Configuration Manager és az Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)). Feltételes házirendek vagy feltételes hozzáférési házirendek használatához nincs szükség az összekötő használatára, szükség van rá azonban az olyan jelentések futtatásához, amelyek segítenek a feltételes hozzáférés hatásának vizsgálatában.  

## <a name="requirements-for-exchange-on-premises"></a>Helyszíni Exchange-követelményei
A helyszíni Exchange-hez való feltételes hozzáférés az alábbi platformokat támogatja:
-   Windows 8 és újabb verzióiban (Regisztrálás az Intune-nal)
-   Windows Phone 8 és újabb verziók
-   Natív e-mail alkalmazás IOS rendszerű eszközökön
-   Natív e-mail alkalmazás Android 4-es vagy újabb
-   A Microsoft Outlook alkalmazás nincs támogatott (Android és iOS).

**Emellett**:

-  Az Exchange-verzió Exchange 2010-es vagy újabb kell lennie. Az Exchange-kiszolgáló ügyfél-hozzáférési kiszolgálótömbje (CAS) nem támogatott.

> [!TIP]
> Ha az Exchange-környezet CAS-kiszolgálói konfigurációban található, majd konfigurálnia kell a helyszíni Exchange connector az egyik CAS-kiszolgálóra mutasson.
- Kell használnia a **Exchange Server-összekötő** amely Configuration Manager kapcsolódik a helyszíni Microsoft Exchange. Ez lehetővé teszi a mobileszközök kezelését, és engedélyezi a feltételes hozzáférést (lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
  - Gondoskodjon arról, hogy a **helyszíni Exchange összekötőjének**a legújabb verzióját használja. A helyszíni Exchange-összekötőt a Configuration Manager konzollal kell konfigurálni. Részletes bemutatóért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
  - Az összekötőt csak a System Center Configuration Manager elsődleges helyén kell konfigurálni.</li><li>Ez az összekötő támogatja a Exchange CAS-környezetet. <br />        Az összekötőt a konfigurálásakor úgy kell beállítani, hogy az egyik Exchange CAS-kiszolgálóval kommunikáljon.

- Az Exchange ActiveSync tanúsítványalapú hitelesítéssel vagy felhasználó által megadott hitelesítő adatokkal konfigurálható.


## <a name="requirements-for-skype-for-business-online"></a>Követelmények a Skype vállalati Online
A SharePoint Online-hoz való feltételes hozzáférés a következőket futtató eszközöket támogatja:
 -   iOS 7.1-es és újabb verziók
 -   Android 4.0 és újabb verziók
 -   Samsung KNOX szabvány 4.0-s vagy újabb

**Emellett** engedélyeznie kell a modern hitelesítést a Skype vállalati online. Az alábbi [kapcsolódási űrlap](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) kitöltésével léphet be a modern hitelesítési programba.

Az összes végfelhasználójának a Skype Vállalati online verziót kell használnia. Ha olyan központi telepítéssel rendelkezik, amely a Skype Vállalati online verziót és a Skype Vállalati helyszíni verziót is tartalmazza, akkor a rendszer nem alkalmazza a feltételes hozzáférési szabályzatot azokra a végfelhasználókra, akik a helyszíni központi telepítéshez tartoznak.

## <a name="requirements-for-sharepoint-online"></a>SharePoint Online követelményei
A SharePoint Online-hoz való feltételes hozzáférés a következőket futtató eszközöket támogatja:
 -   Windows 8.1 és újabb verzióiban (Regisztrálás az Intune-nal)
 -   Windows 7.0 vagy Windows 8.1 (Ha tartományhoz csatlakozik)
 -   Windows Phone 8.1 és újabb verziók
 -   iOS 7.1-es és újabb verziók
 -   Android 4.0-s és újabb verziók, Samsung KNOX szabvány 4.0 és újabb verziók

 **Emellett**:
 -   Az eszközöknek meg kell munkahelyhez csatlakoztatott, amely regisztrálja az eszközt az Azure Active Directory Eszközregisztrációs szolgáltatással (AAD DRS).

 A tartományhoz csatlakozó számítógépeket automatikusan regisztrálni kell az Azure Active Directoryban csoportos házirenden vagy MSI-n keresztül. A jelen témakör **Feltételes hozzáférés a PC-ken** című szakasza a számítógép feltételes hozzáférésének engedélyezéséhez szükséges követelményeket ismerteti.

 Az AAD DRS szolgáltatás automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azok az ügyfelek, akik már telepítették az ADFS eszközregisztrációs szolgáltatását, nem fogják látni a regisztrált eszközöket a helyszíni Active Directoryban.
 -   Egy SharePoint Online-előfizetésre szükség, és a felhasználóknak licenccel kell rendelkezniük a SharePoint online-hoz.

 ### <a name="conditional-access-for-pcs"></a>Feltételes hozzáférés a PC-ken

 Az Office asztali alkalmazásokat futtató számítógépekhez beállíthatja az **Exchange Online** és a **SharePoint Online** feltételes hozzáférését, ha a számítógépek megfelelnek az alábbi követelményeknek:
 -   A Számítógépnek Windows 7.0 vagy Windows 8.1 futnia kell.
 -   A számítógép tartományhoz csatlakoznia vagy megfelelőnek kell.

 Meg kell felelnie, hogy a számítógép regisztrálva kell lennie az Intune-ban, és megfelelnek a házirendek.

 Tartományhoz csatlakozó számítógépek esetén be kell állítani [az eszköz automatikus regisztrációját](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) az Azure Active Directoryban.
 -   [Az Office 365 modern hitelesítésének engedélyezettnek kell lennie](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/), és a számítógépen telepíteni kell az Office legújabb frissítéseit.<br />     A modern hitelesítéssel Active Directory Authentication Library-alapú (ADAL-alapú) bejelentkezés biztosítható az Office 2013 Windows-ügyfelein, és jobb biztonságot kínál, többek között a **többtényezős hitelesítéssel**és a **tanúsítványalapú hitelesítéssel**.
 -   Állítsa be az ADFS-jogcímszabályokat a nem modern hitelesítési protokollok blokkolására.  

## <a name="next-steps"></a>További lépések  
 A következő témakörökből megtudhatja, hogy miként konfigurálhat kompatibilitási házirendeket és feltételes hozzáférési házirendeket az adott helyzetben:  

-   [A System Center Configuration Manager megfelelőségi házirendjeinek kezelése](../../protect/deploy-use/device-compliance-policies.md)  

-   [A System Center Configuration Manager e-mail hozzáférés kezelése](../../protect/deploy-use/manage-email-access.md)  

-   [Kezelheti a SharePoint Online-hozzáférés a System Center Configuration Managerben](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [A Skype vállalati Online-hozzáférés kezelése](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>További információ  

 [Ismerkedés a megfelelőségi beállítások a System Center Configuration Managerben](../../compliance/get-started/get-started-with-compliance-settings.md)

