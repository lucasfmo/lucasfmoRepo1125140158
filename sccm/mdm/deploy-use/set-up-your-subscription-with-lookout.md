---
title: "A Lookout előfizetés beállítása |} System Center Configuration Managerben"
description: "A témakörök a Lookout veszélyforrások elleni eszközvédelem konfigurálásával kapcsolatos részletes adatokat biztosít."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: b777140c753e709f4048a30e63d8ae730d3e8723
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Az előfizetés Lookout veszélyforrások elleni eszközvédelem beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az előfizetés a Lookout eszköz threat protection Service, a Lookout támogatási kész állapotba hozásához (enterprisesupport@lookout.com) a következő információkat az Azure Active Directory (Azure AD) előfizetés szükséges. A Lookout mobilitási végpont biztonsági bérlő a Lookout integrálja az Intune-nal az Azure AD-előfizetés társítva lesz. 

* **Az Azure AD-bérlő azonosítója**
* **Azure AD-csoport Objektumazonosító** a **teljes** Lookout konzol eléréséhez
* **Azure AD-csoport Objektumazonosító** a **korlátozott** Lookout konzol eléréséhez (nem kötelező)

> [!IMPORTANT]
> Meglévő Lookout Mobile végpont biztonsági bérlővel, amely még nincs hozzárendelve az Azure AD-bérlő nem használható az Azure AD integrálása és az Intune-ban. Kérje meg a Lookout támogatási hozzon létre egy új Lookout Mobile végpont biztonsági bérlőt. Az új tenanthoz érheti használja az Azure AD felhasználók.

Az alábbi szakasz segítségével gyűjtse össze az adatokat, hozzá kell rendelnie a Lookout támogatási csapathoz.  

## <a name="get-your-azure-ad-information"></a>Az Azure AD-információk
### <a name="azure-ad-tenant-id"></a>Az Azure AD bérlő azonosítója
Jelentkezzen be a [Azure AD felügyeleti portál](https://manage.windowsazure.com) , és jelölje ki az előfizetését. 

![a bemutató a bérlő nevét az Azure AD oldalát bemutató képernyőkép](media/aad_tenant_name.png) Ha úgy dönt, hogy az előfizetés nevét, az eredményül kapott URL-címet tartalmaz-e az előfizetés-azonosító.  Ha probléma merül fel keresése az előfizetés-Azonosítóval rendelkezik, ez látható [Microsoft-támogatási cikk](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) kapcsolatos tippek keresése az előfizetés-azonosító.   
### <a name="azure-ad-group-id"></a>Azure AD-csoport azonosítója
A Lookout konzol access 2 szintet támogat:  
* **Teljes hozzáférés:** Az Azure AD-rendszergazda létrehozhat olyan csoportot felhasználó számára lesz teljes hozzáféréssel rendelkeznek, és opcionálisan hozzon létre egy csoportot, korlátozott hozzáféréssel rendelkező felhasználók számára.  Csak ebben a csoportokban lévő felhasználók fognak tudni bejelentkezni a **Lookout konzol**.
* **Korlátozott hozzáférés:** A csoportban található felhasználók nem érhető el több konfigurációs lesz, és regisztrációs kapcsolatos modulok a Lookout konzol, és csak olvasási hozzáféréssel rendelkeznek a **biztonsági házirend** a Lookout konzol modul.  

Az engedélyek a további tudnivalókért olvassa el [Ez a cikk](https://personal.support.lookout.com/hc/en-us/articles/114094105653) a Lookout webhelyen.

A **csoport objektum azonosítója** megtalálható a **tulajdonságok** lap a csoport a **az Azure AD felügyeleti konzol**.

![a kijelölt csoportazonosító mező a tulajdonságlapot képernyőképe](media/aad_group_object_id.png)

Miután összegyűjtötte az adatokat, forduljon a Lookout támogatási szolgálathoz (e-mail: enterprisesupport@lookout.com).

A lookout támogatás fog dolgozni a elsődleges forduljon a bevezetni az előfizetés és a Lookout vállalati fiók létrehozásához, az összegyűjtött információk alapján.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>A Lookout veszélyforrások elleni eszközvédelem az előfizetés konfigurálása
### <a name="step-1-set-up-your-device-threat-protection"></a>1. lépés: A veszélyforrások elleni eszközvédelem beállítása
Miután a Lookout támogatása a Lookout vállalati fiókot hoz létre, bejelentkezhet a Lookout konzolhoz.   Használja ki az e-mailt nem jut hozzá a vállalat elsődleges kapcsolattartójának a bejelentkezési URL-cím: https://aad.lookout.com/les?action=consent mutató hivatkozás

Az Azure AD globális rendszergazda szerepkörrel rendelkező egy felhasználói fiókot kell használnia, ha először jelentkezik be a Lookout konzol, az a Lookout szükséges ezeket az adatokat az Azure AD-bérlő regisztrálni.   A következő bejelentkezési nincs szükség a felhasználó ezt az Azure AD jogosultsági szintet.  Az első bejelentkezés a hozzájárulási lap jelenik meg. Válasszon **elfogadás** a regisztráció befejezéséhez.

![a Lookout konzol első idő bejelentkezési oldalának képernyőképe](media/lookout-initial-login.png)

Miután elfogadta és átadni kívánt hozzájárult e, hogy a Lookout konzol van átirányítva. Későbbi bejelentkezések során a kezdeti regisztráció után az URL-cím segítségével: https://aad.lookout.com

Tekintse meg a [hibaelhárítási cikk]() bejelentkezési problémák történő futtatásakor.

A következő lépéseket kell tennie a Lookout belül befejezéséhez feladatok szerkezeti a [Lookout konzol](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>2. lépés: Az Intune-összekötő konfigurálása

1.  A Lookout konzolon az a **rendszer** modul, válassza ki a **összekötők** lapot, és jelölje be **Intune**.

  ![képernyőfelvétel a Lookout konzolon nyissa meg a csatlakozók lap, és az Intune-ban a beállítás a kijelölt](media/lookout-setup-intune-connector.png)

2.  A kapcsolódási beállítások beállítás konfigurálja a szívverés gyakoriságát percben.  Készen áll az Intune-összekötőt.  

  ![a kapcsolati beállítások lapon a szívverés gyakoriság konfigurált ábrázoló képernyőfelvétel](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>3. lépés: Beléptetési csoportok konfigurálása
Az a **beléptetési felügyeleti** lehetőségre, adja meg a felhasználók, akiknek az eszközei regisztrálva kell lennie az Lookout. Az ajánlott eljárás a felhasználók tesztelése, és ismerkedjen meg az integráció működése kis csoportot használ első lépésként.  Ha elégedett a vizsgálati eredmények, a regisztráció terjeszthetők ki további felhasználói csoportokat.

Első lépések regisztrációkat csoportokkal, először meg kell határoznia egy Azure AD biztonsági csoportot, amely a felhasználók regisztrálhatják a Lookout veszélyforrások elleni eszközvédelem egy jó első csoportja lenne. Miután az Azure-ban létrehozott csoportra, Active Directory, a Lookout konzolon lépjen a **beléptetési felügyeleti** lehetőséget, majd adja hozzá az Azure AD biztonsági csoport **megjelenített nevek** regisztrálásra.

Ha egy felhasználó egy beléptetési csoport tagja, az eszközeiket, azonosítható és az Azure ad-ben támogatott: a regisztrált és abban az esetben jogosult a Lookout veszélyforrások elleni eszközvédelem aktiválással.  Keressen olyan támogatott eszközükön munkahelyi alkalmazás első megnyitásakor az eszköz a Lookout aktiválható.

![az Intune-összekötő beléptetési oldalát bemutató képernyőkép](media/lookout-enrollment.png)

Az ajánlott eljárás alkalommal ellenőrzi az új eszközök biztonsági be, hogy az alapértelmezett (5 percig) használja.

>[!IMPORTANT]
> A megjelenített nevének értéke kis-és nagybetűket.  Használja a **megjelenített név** látható a a a **tulajdonságok** lap a biztonsági csoport az Azure portálon. Megjegyzés: a képen látható, amely alatt a **tulajdonságok** teve helyzet lap a biztonsági csoport, a megjelenített név.  A cím azonban minden kisbetű jelenik meg, és nem használatával adja meg a Lookout konzolba.
>![képernyőfelvétel az Azure-portál, Azure Active Directory szolgáltatást, Tulajdonságok lap](media/aad-group-display-name.png)

A jelenlegi kiadásban rendelkezik a következő korlátozások vonatkoznak:  
* Nincs a csoport megjelenített nevek nem lehet érvényesíteni.  Ügyeljen arra, hogy az érték legyen használva a **MEGJELENÍTETT név** mezőben jelenik meg az Azure AD-biztonsági csoport az Azure portálon.
* Csoportok létrehozása jelenleg nem támogatott.  Azure AD biztonsági csoportokat a megadott felhasználók és a nem beágyazott csoportok csak tartalmazhatnak.


### <a name="step-4-configure-state-sync"></a>4. lépés: Állítsa be a sync állapota
Az a **állapot szinkronizálási** lehetőségre, adja meg az adatok, amelyeket az Intune-hoz.  Jelenleg engedélyeznie kell a Eszközállapot és a fenyegetések állapot ahhoz, hogy a Lookout Intune-integráció helyes működéséhez.  Ezek alapértelmezés szerint engedélyezve vannak.
### <a name="step-5-configure-error-report-email-recipient-information"></a>5. lépés: A jelentés e-mailek címzettjeinek hibainformációk konfigurálása
Az a **hiba felügyeleti** lehetőségre, adja meg az e-mail cím, amely a hibajelentések kell kapniuk.

![az Intune-összekötő hiba felügyeleti oldalát bemutató képernyőkép](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>6. lépés. Regisztrációs beállítások konfigurálása
Az a **rendszer** modul, a **összekötők** adja meg azokat a hány nap elteltével eszköz csatlakozóként tekinthető.  Kapcsolat nélküli eszközök nem megfelelőnek minősülnek, és le lesz tiltva a feltételes hozzáférési házirendek szerint SCCM vállalati alkalmazásokhoz való hozzáférés. 1 és 90 nap közötti értékeket adhat meg.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>7. lépés: E-mail értesítések beállítása
Ha szeretne kapni az e-mailes riasztásokhoz fenyegetések, jelentkezzen be a [Lookout konzol](https://aad.lookout.com) a felhasználói fiókkal, amely értesítést kell kapnia. Az a **beállítások** lapján a **rendszer** modul, válassza ki a kívánt értesítések, és állítsa be őket **ON**. A módosítások mentéséhez.

![Képernyőkép a beállítások lap jelenik meg a felhasználói fiókot a](media/lookout-email-notifications.png) már nem szeretné, ha e-mail értesítést szeretne kapni, ha az értesítések beállítása **OFF** és mentse a módosításokat.
### <a name="step-8-configure-threat-classification"></a>8. lépés: Fenyegetési besorolás konfigurálása
A lookout veszélyforrások elleni eszközvédelem osztályozza a különböző típusú mobil fenyegetéseket. A [Lookout fenyegetés besorolások](http://personal.support.lookout.com/hc/en-us/articles/114094130693) alapértelmezett kockázati szintek társítva van. Ezek segítségével módosítható bármikor suite a vállalati követelményeknek megfelelően.

![a fenyegetés és besorolások-szabályzat oldalát bemutató képernyőkép](media/lookout-threat-classification.png)

>[!IMPORTANT]
> A kockázati szintek van megadva itt: veszélyforrások elleni eszközvédelem fontos eleme, mert az Intune-nal eszköznek meg kell felelnie a kockázati szinteket futásidőben alapján számítja ki. Ez azt jelenti, az Intune-rendszergazda beállítja egy szabályt egy eszköz nem megfelelő azonosítására, ha az eszköz legalább egy aktív fenyegetés házirendben szint: magas, közepes vagy alacsony. A fenyegetés adatbesorolási házirenddel a Lookout veszélyforrások elleni eszközvédelem az eszköz megfelelőségi számítási közvetlenül meghajtók az Intune-ban.

## <a name="watching-enrollment"></a>Regisztráció figyelése
A telepítés befejezése után, a Lookout veszélyforrások elleni eszközvédelem elindul, és kérdezze le az eszközökhöz, megfelelnek a megadott regisztrációs csoportok az Azure AD.  Az eszközök modul regisztrált eszközök további információt talál.  Az eszközök kezdeti állapot látható lévőként.  Keressen olyan munkahelyi alkalmazás telepítése után az eszköz állapotmódosítások megnyitva, és az eszközön aktiválni.  A Lookout beszerzésére leküldeni az eszközre munkahelyi alkalmazás részletekért lásd: a [konfigurálása és telepítése a Lookout munkahelyi alkalmazásokat](configure-and-deploy-lookout-for-work-apps.md) témakör.
## <a name="next-steps"></a>További lépések
[Intune-ban a Lookout MTP-kapcsolat engedélyezése](enable-lookout-connection-in-intune.md)

