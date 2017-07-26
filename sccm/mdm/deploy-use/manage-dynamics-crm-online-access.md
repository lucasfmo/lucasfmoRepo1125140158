---
title: "Dynamics CRM Online-hozzáférés kezelése |} Microsoft Docs"
description: "Útmutató a Microsoft Dynamics CRM Online-hozzáférés szabályozása az iOS és Android-eszközök Microsoft Intune feltételes hozzáférésű."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
caps.latest.revision: 5
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: bd00f12ae3bc14a34d24c22c3d5277d275d51e85
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>A System Center Configuration Managerben a Dynamics CRM Online-hozzáférés kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Szabályozhatja a hozzáférést a Microsoft Dynamics CRM Online-hoz az iOS és Android-eszközök Microsoft Intune feltételes hozzáférésével.  Intune feltételes hozzáférése két összetevőből áll:
* [Eszközmegfelelőségi szabályzat](../../protect/deploy-use/device-compliance-policies.md) , hogy az eszköznek meg kell felelnie a ahhoz, hogy a rendszer megfelelőnek.
* [Feltételes hozzáférési házirend](../../protect/deploy-use/manage-access-to-services.md) , amelyben meg kell határoznia a feltételeket, amelyeknek az eszköznek teljesítenie kell a szolgáltatás eléréséhez.

Jobban megismerni a feltételes hozzáférés működését, olvassa el a [szolgáltatásokhoz való hozzáférés kezelése](../../protect/deploy-use/manage-access-to-services.md) cikk.


Amikor egy célzott felhasználó megpróbálja használhatják a Dynamics CRM alkalmazást az eszközükön, a következő ellenőrzés megy végbe:

![A segítségével meghatározhatja, hogy egy eszköz a szolgáltatáshoz való hozzáférés engedélyezett, vagy le van tiltva döntési pontokat megjelenítő diagram](media/mdm-ca-dynamics-crm-flow-diagram.png)

A Dynamics CRM Online-hoz való hozzáférést igénylő eszközre kell:
* Kell egy **Android** vagy **iOS** eszköz.
* Kell **regisztrált** Microsoft Intune-nal.
* Kell **megfelelő** az összes telepített Microsoft Intune megfelelőségi szabályzatának.

Az eszköz állapotát a rendszer az Azure Active Directoryban tárolja. Utóbbi a megadott feltételek alapján engedélyezi vagy letiltja a hozzáférést.

Ha egy feltétel nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:
* Ha az eszköz nincs regisztrálva az Intune-hoz, vagy nincs regisztrálva az Azure Active Directoryban, egy üzenet jelenik meg leírja, hogyan kell telepíteni a vállalati portál alkalmazást és regisztrálni az eszközt.
* Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely a felhasználót a Microsoft Intune vállalati portál webhelyére vagy a vállalati portál alkalmazásba irányítja, hol található a problémával kapcsolatos információkat, és annak megoldásáról.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Dynamics CRM Online feltételes hozzáférésének beállítása  
### <a name="step-1-configure-active-directory-security-groups"></a>1. lépés: Az Active Directory biztonsági csoportok beállítása

Kezdés előtt állítsa be az Azure Active Directory-alapú biztonsági csoportokat a feltételes hozzáférési házirendhez. Ezeket a csoportokat az konfigurálhatja a **Office 365 felügyeleti központban**. Ezek a csoportok használandó cél, vagy a felhasználó képez kivételt a szabályzat alól. Amikor egy felhasználóra házirend vonatkozik, az erőforrások eléréséhez az általa használt összes eszköznek meg kell felelnie a házirendnek.

A Dynamics CRM házirendjének használandó két csoporttípust adhat meg:
* **Megcélzott csoportok** –, amelyhez a házirend hatálya alá eső felhasználók csoportjait tartalmazza.
* **Kivétel alá eső csoportok** – a szabályzat alól mentesülő felhasználói csoportokat tartalmazza.

Ha egy felhasználó mindkét csoportban szerepel, mentesül a házirend alól.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2. lépés: A megfelelőségi szabályzat konfigurálása és telepítése
[Létrehozhat és telepíthet](../../protect/deploy-use/device-compliance-policies.md) a házirend által érintett összes eszköz megfelelőségi szabályzatot. Ez minden olyan eszközre, amelyet a megcélzott csoportok csoporthoz tartozó felhasználók használnak értendő.

> [!NOTE]
> A Microsoft Intune-csoportok megfelelőségi szabályzatainak bevezetése, feltételes hozzáférési házirendek az Azure Active Directory biztonsági csoportokat célozzák.

> [!IMPORTANT]
> Ha nem telepített megfelelőségi házirendet, a rendszer kell megfelelőnek tekinti az eszközöket.

Ha készen áll, folytassa a 3. lépéssel.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>3. lépés: A Dynamics CRM házirendjének konfigurálása
Ezután konfigurálja a házirendet, hogy csak a felügyelt és megfelelő eszközök érhessék el a Dynamics CRM-hez. A házirend ezek után az Azure Active Directoryban tárolódik.

1.  A Microsoft Intune felügyeleti konzolon válassza a **házirend > feltételes hozzáférés > Dynamics CRM Online-szabályzat**.

     ![Képernyőfelvétel a Dynamics CRM Online feltétes hozzáférési szabályzatának oldaláról](media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Válassza ki **feltételes hozzáférésének engedélyezésére** házirend.
3.  Az **Alkalmazás hozzáférése**szakaszban kiválaszthatja, hogy mire szeretné alkalmazni a feltételes hozzáférési szabályzatot:
  * **iOS**
  * **Android--**
4.  A **megcélzott csoportok**, válassza a **módosítás** jelölje be az Azure Active Directory biztonsági csoportok kiválasztásához, amelyekre a szabályzat érvényes. Kiválaszthatja, hogy a szabályzat minden felhasználóra, vagy csak felhasználók bizonyos csoportjaira vonatkozzon.
5.  A **kivétel alá eső csoportok**, szükség esetén válasszon **módosítás** jelölje be az Azure Active Directory biztonsági csoportokat, amelyekre nem érvényes a szabályzat.
6.  Amikor elkészült, válassza ki a **mentése**.

Most már konfigurálta a feltételes hozzáférés a Dynamics CRM. Nem kell telepítenie a feltételes hozzáférési házirendet, azonnal érvénybe lép.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>A megfelelőség és a feltételes hozzáférési házirendek megfigyelése

Az a **csoportok** munkaterületen megtekintheti eszközei feltételes hozzáférési állapotát.

Válassza ki bármelyik mobileszköz-csoportot, majd az **Eszközök** lapon válasszon az alábbi **Szűrők**közül:
* **Az aad-ben nem regisztrált eszközök** – ezeknek az eszközöknek nincs hozzáférése a Dynamics CRM-hez.
* **Nem megfelelő eszközök** – ezeknek az eszközöknek nincs hozzáférése a Dynamics CRM-hez.
* **AAD-ben regisztrált és megfelelő eszközök** – ezek az eszközök hozzáférhetnek a Dynamics CRM-hez.

###  <a name="see-also"></a>További információ
[A levelezéshez való hozzáférés kezelése](../../protect/deploy-use/manage-email-access.md)

[A SharePoint Online-hozzáférés kezelése](../../protect/deploy-use/manage-sharepoint-online-access.md)

[Hozzáférés a Skype vállalati online kezelése](../../protect/deploy-use/manage-skype-for-business-online-access.md)

