---
title: "Egy nem galéria-alkalmazást konfigurált összevont bejelentkezés problémák egyszeri bejelentkezés |} Microsoft Docs"
description: "Útmutató a konkrét problémák lehetséges, hogy szembesülhetnek, az alkalmazás beállítása az SAML-alapú összevont egyszeri bejelentkezés az Azure ad-vel történő bejelentkezéskor"
services: active-directory
documentationcenter: 
author: ajamess
manager: mtillman
ms.assetid: 
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/11/2017
ms.author: asteen
ms.openlocfilehash: 681e40f3056e540c15542f22c3b30a18564dd2ed
ms.sourcegitcommit: e266df9f97d04acfc4a843770fadfd8edf4fa2b7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/11/2017
---
# <a name="problems-signing-in-to-a-non-gallery-application-configured-for-federated-single-sign-on"></a>Bejelentkezés egy összevont egyszeri bejelentkezés beállítása nem galéria alkalmazás problémák

A hiba elhárításához ellenőrizze az alkalmazás konfigurációját az Azure AD a következőképpen kell:

-   Az Azure AD-gyűjtemény alkalmazás a konfigurációs lépéseket követte.

-   A azonosító és az aad-ben megadott válasz URL-cím egyezik meg azokat az alkalmazás a várt értékek

-   Az alkalmazáshoz hozzárendelt felhasználók

## <a name="application-not-found-in-directory"></a>Az alkalmazás nem található a könyvtárban

*Hiba AADSTS70001: "Https://contoso.com" azonosítójú alkalmazás nem található a könyvtárban*.

**Lehetséges ok**

A kibocsátó attribútum küldése az alkalmazásból az Azure AD-t a SAML-kérelmet nem felel meg az alkalmazás az Azure AD konfigurált azonosító értéket.

**Megoldás**

Győződjön meg arról, hogy a kibocsátó attribútumot a SAML-kérelmet azt van megfelelő az azonosító az Azure ad-ben konfigurált értéket:

1.  Nyissa meg a [ **Azure Portal** ](https://portal.azure.com/) , és jelentkezzen be egy **globális rendszergazda** vagy **Co-rendszergazda segítségét.**

2.  Nyissa meg a **Azure Active Directory-bővítmény** kattintva **további szolgáltatások** a fő bal oldali navigációs menü alján.

3.  Írja be a **"Azure Active Directory**" a szűrő keresési mezőbe, és válasszon a **Azure Active Directory** elemet.

4.  Kattintson a **vállalati alkalmazások** az Azure Active Directory bal oldali navigációs menüjében.

5.  Kattintson a **összes alkalmazás** az alkalmazások listájának megtekintéséhez.

   * Ha azt szeretné, hogy itt megjelennek az alkalmazás nem látja, használja a **szűrő** vezérlő tetején a **összes alkalmazások listáját** és állítsa be a **megjelenítése** lehetőséggel **összes alkalmazást.**

6.  Válassza ki az egyszeri bejelentkezés konfigurálni kívánt alkalmazást.

7.  Ha az alkalmazás betölt, kattintson a **egyszeri bejelentkezés** az alkalmazás bal oldali navigációs menüjében.

8.  <span id="_Hlk477190042" class="anchor"></span>Ugrás a **tartomány és az URL-címek** szakasz. Győződjön meg arról, hogy az azonosító szövegmező értékét a értéket az azonosító a jelennek meg a hiba a megfelelő-e.

Miután frissítette az azonosító értéket az Azure ad-ben, és azt az értéket küld van megfelelő az alkalmazásnak a SAML-kérelmet, jelentkezhet be az alkalmazásba kell lennie.

## <a name="the-reply-address-does-not-match-the-reply-addresses-configured-for-the-application"></a>A válaszcím nem egyezik meg az alkalmazáshoz beállított válasz-címeket. 

*AADSTS50011. hiba: A válasz "https://contoso.com" nem egyezik a válasz címek konfigurálva az alkalmazáshoz* 

**Lehetséges ok** 

A SAML-kérelmet AssertionConsumerServiceURL értéke nem egyezik, a válasz URL-címével vagy a minta az Azure ad-ben konfigurált. A SAML-kérelmet AssertionConsumerServiceURL érték az URL-címet, a hibaüzenet látható. 

**Megoldás** 

Győződjön meg arról, hogy a SAML-kérelmet, akkor a válasz URL-cím van megfelelő AssertionConsumerServiceURL értékét az Azure ad-ben beállított értéket. 
 
1.  Nyissa meg a [ **Azure Portal** ](https://portal.azure.com/) , és jelentkezzen be egy **globális rendszergazda** vagy **Co-rendszergazda segítségét.** 

2.  Nyissa meg a **Azure Active Directory-bővítmény** kattintva **további szolgáltatások** a fő bal oldali navigációs menü alján. 

3.  Írja be a **"Azure Active Directory**" a szűrő keresési mezőbe, és válasszon a **Azure Active Directory** elemet. 

4.  Kattintson a **vállalati alkalmazások** az Azure Active Directory bal oldali navigációs menüjében. 

5.  Kattintson a **összes alkalmazás** az alkalmazások listájának megtekintéséhez. 

  * Ha azt szeretné, hogy itt megjelennek az alkalmazás nem látja, használja a **szűrő** vezérlő tetején a **összes alkalmazások listáját** és állítsa be a **megjelenítése** lehetőséggel **összes alkalmazást.**
  
6.  Válassza ki az egyszeri bejelentkezés konfigurálni kívánt alkalmazást

7.  Ha az alkalmazás betölt, kattintson a **egyszeri bejelentkezés** az alkalmazás bal oldali navigációs menüjében.

8.  Ugrás a **tartomány és az URL-címek** szakasz. Győződjön meg arról, vagy frissítse az értéket, hogy az egyezzen a SAML-kérelmet a AssertionConsumerServiceURL értékkel válasz URL-CÍMEN szövegmezőjének.

  * Ha a válasz URL-cím beviteli mező nem látható, válassza ki a **megjelenítése speciális URL-beállításainak** jelölőnégyzetet. 

Miután frissítette az válasz URL-cím az Azure ad-ben, és azt az értéket küld van megfelelő az alkalmazásnak a SAML-kérelmet, jelentkezhet be az alkalmazásba kell lennie.

## <a name="user-not-assigned-a-role"></a>Nem hozzárendelt felhasználó

*AADSTS50105. hiba: A bejelentkezett felhasználó nevében "brian@contoso.com" az alkalmazás egy szerepkörnek nincs hozzárendelve*

**Lehetséges ok**

A felhasználó nem rendelkezik az Azure AD-alkalmazás hozzáférését.

**Megoldás**

Hozzárendelése egy vagy több felhasználó alkalmazás közvetlenül, kövesse az alábbi lépéseket:

1.  Nyissa meg a [ **Azure Portal** ](https://portal.azure.com/) , és jelentkezzen be egy **globális rendszergazdája.**

2.  Nyissa meg a **Azure Active Directory-bővítmény** kattintva **további szolgáltatások** a fő bal oldali navigációs menü alján.

3.  Írja be a **"Azure Active Directory**" a szűrő keresési mezőbe, és válasszon a **Azure Active Directory** elemet.

4.  Kattintson a **vállalati alkalmazások** az Azure Active Directory bal oldali navigációs menüjében.

5.  Kattintson a **összes alkalmazás** az alkalmazások listájának megtekintéséhez.

  * Ha azt szeretné, hogy itt megjelennek az alkalmazás nem látja, használja a **szűrő** vezérlő tetején a **összes alkalmazások listáját** és állítsa be a **megjelenítése** lehetőséggel **összes alkalmazást.**

6.  Válassza ki szeretné osztani a felhasználót, hogy a listában az alkalmazást.

7.  Ha az alkalmazás betölt, kattintson **felhasználók és csoportok** az alkalmazás bal oldali navigációs menüjében.

8.  Kattintson a **Hozzáadás** gombra kattint, a a **felhasználók és csoportok** nyissa meg a listában a **hozzáadása hozzárendelés** panelen.

9.  Kattintson a **felhasználók és csoportok** a választó a **hozzáadása hozzárendelés** panelen.

10. Írja be a **teljes név** vagy **e-mail cím** érdekli hozzárendelése a felhasználó a **Keresés név vagy e-mail cím alapján** keresőmezőbe.

11. Vigye a **felhasználói** a listában, hogy láthatóvá váljon a **jelölőnégyzet**. A felhasználói profil fénykép vagy adja hozzá a felhasználót emblémát jelölőnégyzetét, kattintson a **kijelölt** listája.

12. **Választható lehetőség:** Ha azt szeretné, hogy **egynél több felhasználó hozzáadása**, egy másik típus **teljes név** vagy **e-mail cím** be a **Keresés név vagy e-mail cím alapján** mező, és a jelölőnégyzet bejelölésével adja hozzá a felhasználót, hogy a **kijelölt** listája.

13. Ha elkészült, válassza a felhasználók, kattintson a **válasszon** gombra kattintva vegye fel a listára a felhasználók és csoportok hozzá kell rendelni az alkalmazáshoz.

14. **Választható lehetőség:** kattintson a **Szerepkörválasztás** a választó a **hozzáadása hozzárendelés** hozzárendelése a kiválasztott felhasználói szerepkör kiválasztása panel.

15. Kattintson a **hozzárendelése** gombra kattintva a kijelölt felhasználók az alkalmazást.

Rövid időn belül a kijelölt felhasználók tudják elindítani ezeket az alkalmazásokat a megoldás leírása szakaszban ismertetett módszerekkel.

## <a name="not-a-valid-saml-request"></a>Nem egy érvényes SAML-kérés

*AADSTS75005. hiba: A kérelme, mert nem egy Saml2 protokoll érvényes üzenetet.*

**Lehetséges ok**

Az Azure AD nem támogatja az egyszeri bejelentkezést az alkalmazás által küldött SAML-kérelem. Néhány gyakori kérdések a következők:

-   A SAML-kérelmet a kötelező mezők hiányoznak

-   SAML kódolt kérelmek módja

**Megoldás**

1.  Rögzítse a SAML-kérelmet. az útmutató bevezeti Önt [hibakeresés SAML-alapú egyszeri bejelentkezés alkalmazásokhoz az Azure AD-ben](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-debugging) megtudhatja, hogyan rögzítheti a SAML-kérelmet.

2.  Lépjen kapcsolatba az alkalmazás gyártójának és megosztás:

    -   SAML-kérelmet

    -   [Azure AD-egyszeri bejelentkezés SAML protokoll követelmények](https://docs.microsoft.com/azure/active-directory/develop/active-directory-single-sign-on-protocol-reference)

Ellenőrizni kell az egyszeri bejelentkezés az Azure AD SAML-alapú megvalósítás támogatják.

## <a name="no-resource-in-requiredresourceaccess-list"></a>Nincs erőforrás requiredResourceAccess listában

*Hiba AADSTS65005: Az ügyfélalkalmazás kért erőforrás elérésére "00000002-0000-0000-c000-000000000000'. A kérelem sikertelen volt, mert az ügyfél nem megadva ehhez az erőforráshoz requiredResourceAccess listáján található*.

**Lehetséges ok**

Az application objektum sérült.

**Megoldás**

A probléma megoldásához távolítsa el az alkalmazást a könyvtárból. Adja hozzá, és konfigurálja újra az alkalmazást, kövesse az alábbi lépéseket:

1.  Nyissa meg a [ **Azure Portal** ](https://portal.azure.com/) , és jelentkezzen be egy **globális rendszergazda** vagy **Co-rendszergazda segítségét.**

2.  Nyissa meg a **Azure Active Directory-bővítmény** kattintva **további szolgáltatások** a fő bal oldali navigációs menü alján.

3.  Írja be a **"Azure Active Directory**" a szűrő keresési mezőbe, és válasszon a **Azure Active Directory** elemet.

4.  Kattintson a **vállalati alkalmazások** az Azure Active Directory bal oldali navigációs menüjében.

5.  Kattintson a **összes alkalmazás** az alkalmazások listájának megtekintéséhez.

  * Ha azt szeretné, hogy itt megjelennek az alkalmazás nem látja, használja a **szűrő** vezérlő tetején a **összes alkalmazások listáját** és állítsa be a **megjelenítése** lehetőséggel **összes alkalmazást.**

6.  Válassza ki az egyszeri bejelentkezés konfigurálni kívánt alkalmazást.

7.  Kattintson a **törlése** , a bal felső az alkalmazás **áttekintése** panelen.

8.  Frissítse az Azure AD, és vegye fel az alkalmazást az Azure AD-galériából. Ezt követően konfigurálja újból az alkalmazást.

Az alkalmazás újbóli beállításához után jelentkezhet be az alkalmazásba kell lennie.

## <a name="certificate-or-key-not-configured"></a>Tanúsítvány és kulcs nincs konfigurálva

Hiba AADSTS50003: Nincs aláírási kulcs konfigurálva.

**Lehetséges ok**

Az application objektum sérült, és az Azure AD nem ismeri fel az alkalmazáshoz beállított tanúsítvány.

**Megoldás**

Törölje, majd hozzon létre egy új tanúsítványt, kövesse az alábbi lépéseket:

1.  Nyissa meg a [ **Azure Portal** ](https://portal.azure.com/) , és jelentkezzen be egy **globális rendszergazda** vagy **Co-rendszergazda segítségét.**

2.  Nyissa meg a **Azure Active Directory-bővítmény** kattintva **további szolgáltatások** a fő bal oldali navigációs menü alján.

3.  Írja be a **"Azure Active Directory**" a szűrő keresési mezőbe, és válasszon a **Azure Active Directory** elemet.

4.  Kattintson a **vállalati alkalmazások** az Azure Active Directory bal oldali navigációs menüjében.

5.  Kattintson a **összes alkalmazás** az alkalmazások listájának megtekintéséhez.

  * Ha azt szeretné, hogy itt megjelennek az alkalmazás nem látja, használja a **szűrő** vezérlő tetején a **összes alkalmazások listáját** és állítsa be a **megjelenítése** lehetőséggel **összes alkalmazást.**

6.  Válassza ki az egyszeri bejelentkezés konfigurálni kívánt alkalmazást.

7.  Ha az alkalmazás betölt, kattintson a **egyszeri bejelentkezés** az alkalmazás bal oldali navigációs menüjében.

8.  Kattintson a **hozzon létre új tanúsítvány** alatt a **aláíró tanúsítvány SAML** szakasz.

9.  Válassza ki a lejárati dátum. Kattintson a **mentéséhez.**

10. Ellenőrizze **új tanúsítvány aktiválásához** az aktív tanúsítvány felülbírálására. Kattintson a **mentése** a panel tetején, és fogadja el a helyettesítő tanúsítvány aktiválásához.

11. Az a **SAML-aláíró tanúsítványa** területén kattintson **eltávolítása** eltávolítása a **nem használt** tanúsítvány.

## <a name="problem-when-customizing-the-saml-claims-sent-to-an-application"></a>Probléma a alkalmazás küldött SAML-jogcímek testreszabása

Megtudhatja, hogyan szabhatja testre a SAML attribútum típusú jogcímek az alkalmazás számára, lásd: [hozzárendelése az Azure Active Directory-jogcímek](https://docs.microsoft.com/azure/active-directory/active-directory-claims-mapping) további információt.

## <a name="next-steps"></a>Következő lépések
[Azure AD-egyszeri bejelentkezés SAML protokoll követelmények](https://docs.microsoft.com/azure/active-directory/develop/active-directory-single-sign-on-protocol-reference)
