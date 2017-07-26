---
title: "A Skype vállalati Online-hozzáférés kezelése |} Microsoft Docs"
description: "Megtudhatja, hogyan kezelésére a Skype vállalati online feltételes hozzáférési szabályzat segítségével."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
caps.latest.revision: 6
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: cacb22a85e74a7d9cae75ad907d0206487cd4dc7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-skype-for-business-online-access"></a>A Skype Vállalati online verzió elérésének kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A  **Skype Vállalati online verzió** feltételes hozzáférési szabályzatának használatával kezelheti a Skype Vállalati online verzióhoz az Ön által megadott feltételek alapján való hozzáférést.  


 Amikor egy megcélzott felhasználó megpróbálja használni a Skype Vállalati online verziót az eszközén, a rendszer a következő szempontokat értékeli ki:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Előfeltételek  

-   A modern hitelesítés engedélyezése a Skype Vállalati online verzióhoz Az alábbi [kapcsolódási űrlap](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) kitöltésével léphet be a modern hitelesítési programba.  

-   Az összes végfelhasználójának a Skype vállalati online kell kell használatával. Ha a telepítésben Skype vállalati Online verziót és a Skype vállalati helyszíni, feltételes hozzáférési házirend nem lehet alkalmazva legyenek a végfelhasználók számára.  

-   A Skype Vállalati online verzióhoz hozzáférést igénylő eszközre vonatkozó feltételek:  

    -   Android- vagy iOS-eszköznek kell lennie.  

    -   Az Intune-nal regisztrálva kell lennie.  

    -   Meg kell felelnie az Intune összes telepített megfelelőségi szabályzatának.  

 Az eszköz állapotát a rendszer az Azure Active Directoryban tárolja. Utóbbi a megadott feltételek alapján engedélyezi vagy letiltja a hozzáférést.  
Ha egy feltétel nem teljesül, a felhasználó számára az alábbi üzenetek egyike jelenik meg a bejelentkezéskor:  

-   Ha az eszköz nincs regisztrálva az Intune-ban vagy az Azure Active Directoryban, megjelenik egy üzenet, amely leírja, hogyan kell telepíteni a Vállalati portál alkalmazást és regisztrálni az eszközt.  

-   Ha az eszköz nem megfelelő, egy üzenet jelenik meg, amely a felhasználót az Intune Vállalati portál webhelyére vagy a Vállalati portál alkalmazásba irányítja, ahol további információt talál a problémáról és megoldásáról.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>A Skype Vállalati online verzió feltételes hozzáférésének beállítása  

### <a name="step-1-configure-active-directory-security-groups"></a>1. lépés: Az Active Directory biztonsági csoportok beállítása  
 Kezdés előtt állítsa be az Azure Active Directory-alapú biztonsági csoportokat a feltételes hozzáférési házirendhez. Ezeket a csoportokat az Office 365 Felügyeleti központban konfigurálhatja. Ezek a csoportok tartalmazzák a célzott vagy a házirend alól mentesülő felhasználókat. Amikor egy felhasználóra házirend vonatkozik, az erőforrások eléréséhez az általa használt összes eszköznek meg kell felelnie a házirendnek.  

 A Skype Vállalati online verzió házirendjéhez két csoporttípust adhat meg:  

-   Megcélzott csoportok â "", amelyhez a házirend hatálya alá eső felhasználók csoportjait tartalmazza  

-   Kivétel alá eső csoportok â "" (választható) a szabályzat alól mentesülő felhasználói csoportokat tartalmazza  
    Ha egy felhasználó mindkét csoportban szerepel, mentesül a házirend alól.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2. lépés: A megfelelőségi szabályzat konfigurálása és telepítése  
 Minden olyan eszközön létre kell hoznia és regisztrálnia kell a megfelelőségi szabályzatot, amelyet a Skype Vállalati online verzió házirendjével fog megcélozni.  

 A megfelelőségi szabályzat konfigurálásának ismertetését lásd: [Eszközök megfelelőségi házirendjének kezelése a System Center Configuration Managerrel](../../protect/deploy-use/device-compliance-policies.md).  

> [!NOTE]  
>  Ha nem telepített megfelelőségi szabályzatot, és engedélyezi a Skype Vállalati online verzió szabályzatát, az összes olyan megcélzott eszköz hozzáférése engedélyezve lesz, amely regisztrálva van az Intune-ban.  

 Ha készen áll, folytassa a 3. lépéssel.  

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>3. lépés: A Skype vállalati Online-házirend konfigurálása  
 Ezután állítsa be úgy a szabályzatot, hogy csak a felügyelt és a feltételeknek megfelelő eszközök érhessék el a Skype Vállalati online verziót. A házirend ezek után az Azure Active Directoryban tárolódik.  

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com)kattintson a **Házirend** > **Feltételes hozzáférés** > **Skype for Business Online Házirend**.  

     ![ConditionalAccess&#95;SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  Válassza a **Feltételes hozzáférési házirend engedélyezése** lehetőséget.  

3.  Az **Alkalmazás hozzáférése**szakaszban kiválaszthatja, hogy mire szeretné alkalmazni a feltételes hozzáférési szabályzatot:  

    -   iOS  

    -   Android  

4.  A **Megcélzott csoportok**területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre érvényes a házirend. Kiválaszthatja, hogy a szabályzat minden felhasználóra, vagy csak felhasználók bizonyos csoportjaira vonatkozzon.  

5.  A **Kivétel alá eső csoportok**területen kattintson a **Módosítás** lehetőségre azon Active Directory-alapú biztonsági csoportok kiválasztásához, amelyekre nem érvényes a szabályzat.  

6.  Amikor elkészült, kattintson a **Mentés**gombra.  

 Ezzel beállította a Skype Vállalati online verzió feltételes elérését. Nem kell telepítenie a feltételes hozzáférési házirendet, azonnal érvénybe lép.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>A megfelelőség és a feltételes hozzáférési házirendek megfigyelése  
 A Csoportok munkaterületen megtekintheti az eszközök feltételes hozzáférési állapotát.  

 Válassza ki bármelyik mobileszköz-csoportot, majd az **Eszközök** lapon válasszon az alábbi **Szűrők**közül:  

-   **Az aad-ben nem regisztrált eszközök** â "" ezeknek az eszközöknek nincs hozzáférésük a Skype vállalati online.  

-   **Nem megfelelő eszközök** â "" ezeknek az eszközöknek nincs hozzáférésük a Skype vállalati online.  

-   **AAD-ben regisztrált és megfelelő eszközök** â "" Ezek az eszközök hozzáférhetnek a Skype vállalati online.  

### <a name="see-also"></a>További információ  

 [A System Center Configuration Manager megfelelőségi házirendjeinek kezelése](../../protect/deploy-use/device-compliance-policies.md)

