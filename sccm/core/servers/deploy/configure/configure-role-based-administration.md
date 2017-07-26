---
title: "Szerepköralapú Adminisztráció konfigurálása |} Microsoft Docs"
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 57413dd3-b2f8-4a5f-b27f-8464d357caff
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1defe96163f1bb70f586619ad89098c6f0e6c665
ms.openlocfilehash: 3eea3a6e5f23808570ded4be3bd7412954518b96
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="configure-role-based-administration-for-system-center-configuration-manager"></a>Szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása   

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben, a szerepkör alapú felügyelet biztonsági szerepköröket, biztonsági hatókörök és hozzárendelt gyűjtemények együttes használatával definiálja az egyes rendszergazda felhasználó felügyeleti hatókörét egyesíti. Egy felügyeleti hatóköre kiterjed azokra a objektumokat, amelyeket a rendszergazda felhasználók megtekinthetnek a Configuration Manager konzolon, és ezekkel az objektumokkal kapcsolatos azon feladatokat, amelyek a rendszergazda felhasználó engedéllyel rendelkezik. A szerepkör alapú felügyeleti beállítások az adott hierarchia minden helyére érvényesek.  

 Ha még nem ismeri a szerepköralapú adminisztrációval kapcsolatos fogalmakat, tanulmányozza [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 A következő eljárások segítségével hozhat létre, és a szerepköralapú Adminisztráció konfigurálása, és a kapcsolódó biztonsági beállítások megadásához:  

-   [Egyéni biztonsági szerepkörök létrehozása](#BKMK_CreateSecRole)  

-   [Biztonsági szerepkörök konfigurálása](#BKMK_ConfigSecRole)  

-   [Biztonsági hatókörök konfigurálása objektumhoz](#BKMK_ConfigSecScope)  

-   [Gyűjtemények konfigurálása a biztonság kezeléséhez](#BKMK_ConfigColl)  

-   [Új rendszergazda felhasználó létrehozása](#BKMK_Create_AdminUser)  

-   [Rendszergazda felhasználó felügyeleti hatókörének módosítása](#BKMK_ModAdminUser)  

##  <a name="BKMK_CreateSecRole"></a> Egyéni biztonsági szerepkörök létrehozása  
 A Configuration Manager számos beépített biztonsági szerepkört kínál. Ha további biztonsági szerepkörre van szüksége, létrehozhat egyéni biztonsági szerepkört meglévő biztonsági szerepkör másolatából annak módosításával. Létrehozhat egy egyéni biztonsági szerepkört, a rendszergazda felhasználók a további biztonsági engedélyek, amely nem része a aktuálisan hozzárendelt biztonsági szerepkör van szükségük. Egyéni biztonsági szerepkör használatával csak a számukra szükséges engedélyeket adhatja meg, és elkerülheti olyan biztonsági szerepkör hozzárendelését, amely a kívántnál több engedélyt biztosít.  

 A következő eljárás segítségével új biztonsági szerepkört hozhat létre meglévő biztonsági szerepkör sablonként való használatával.  

#### <a name="to-create-custom-security-roles"></a>Egyéni biztonsági szerepkörök létrehozásának lépései  

1.  Nyissa meg a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **biztonsági szerepkörök**.  

     A következő eljárások valamelyikével hozza létre az új biztonsági szerepkört:  

    -   Új biztonsági szerepkör létrehozásához hajtsa végre a következő műveleteket:  

        1.  Jelöljön ki egy meglévő biztonsági szerepkört, amelyet az új biztonsági szerepkör forrásaként fog használni.  

        2.  Az a **Home** lap a **biztonsági szerepkör** csoportjában válassza **másolási**. Ez létrehozza a forrásként használt biztonsági szerepkör másolatát.  

        3.  A Biztonsági szerepkör másolása varázslóban a **Név** mezőben adjon nevet az új egyéni biztonsági szerepkörnek.  

        4.  A **Biztonsági műveletek hozzárendelései**szakaszban bontsa ki a **Biztonsági műveletek** egyes csomópontjait a rendelkezésre álló műveletek megjelenítéséhez.  

        5.  Az adott biztonsági művelet beállításának módosítása, kattintson a lefelé mutató nyílra a **érték** oszlop, és válasszon **Igen** vagy **nem**.  

            > [!CAUTION]  
            >  Amikor konfigurál egy egyéni biztonsági szerepkört, győződjön meg arról, hogy meg nem adja meg az új biztonsági szerepkörhöz társított rendszergazda felhasználók által nem szükséges engedélyeket. Például a **módosítás** értékét a **biztonsági szerepkörök** biztonsági műveleténél engedélyt rendszergazda felhasználóknak tetszőleges elérhető biztonsági szerepkör – szerkesztésére még akkor is, ha azok nem tartozik az adott biztonsági szerepkör.  

        6.  Az engedélyek beállítása után válassza ki a **OK** az új biztonsági szerepkör mentéséhez.  

    -   Egy másik Configuration Manager-hierarchiából exportált biztonsági szerepkör importálásához hajtsa végre a következő műveleteket:  

        1.  Az a **Home** lap a **létrehozása** csoportjában válassza **biztonsági szerepkör importálása**.  

        2.  Adja meg az .xml fájlt, amely tartalmazza az importálni kívánt biztonsági szerepkör konfigurációja. Válasszon **nyitott** hajtsa végre az eljárást, és a biztonsági szerepkör mentéséhez.  

            > [!NOTE]  
            >  Biztonsági szerepkör importálása után szerkesztheti a biztonsági szerepkör tulajdonságait, és így módosíthatja az objektumokra vonatkozó hozzárendelt engedélyeket.  

##  <a name="BKMK_ConfigSecRole"></a> Biztonsági szerepkörök konfigurálása  
 A biztonsági szerepkörhöz definiált biztonsági engedélyek csoportjainak elnevezése biztonsági műveletek hozzárendelései. A biztonsági műveletek hozzárendelései az egyes objektumtípusoknál rendelkezésre álló objektumok és műveletek kombinációját jelentik. Módosíthatja, hogy mely biztonsági műveletek legyenek elérhetők tetszőleges egyéni biztonsági szerepkörnél, de nem módosíthatja a beépített biztonsági szerepkörök, amelyek a Configuration Manager kínál.  

 A következő eljárás végrehajtásával biztonsági szerepkör biztonsági műveleteit módosíthatja:  

#### <a name="to-modify-security-roles"></a>Biztonsági szerepkörök módosítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **biztonsági szerepkörök**.  

3.  Jelölje ki a módosítani kívánt egyéni biztonsági szerepkört.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **engedélyek** fülre.  

6.  A **Biztonsági műveletek hozzárendelései**szakaszban bontsa ki a **Biztonsági műveletek** egyes csomópontjait a rendelkezésre álló műveletek megjelenítéséhez.  

7.  Az adott biztonsági művelet beállításának módosítása, kattintson a lefelé mutató nyílra a **érték** oszlop, és válasszon **Igen** vagy **nem**.  

    > [!CAUTION]  
    >  Amikor konfigurál egy egyéni biztonsági szerepkört, győződjön meg arról, hogy meg nem adja meg az új biztonsági szerepkörhöz társított rendszergazda felhasználók által nem szükséges engedélyeket. Például a **módosítás** értékét a **biztonsági szerepkörök** biztonsági műveleténél engedélyt rendszergazda felhasználóknak tetszőleges elérhető biztonsági szerepkör – szerkesztésére még akkor is, ha azok nem tartozik az adott biztonsági szerepkör.  

8.  Amikor befejezte a biztonsági műveletek hozzárendeléseinek beállítása, **OK** az új biztonsági szerepkör mentéséhez.  

##  <a name="BKMK_ConfigSecScope"></a> Biztonsági hatókörök konfigurálása objektumhoz  
 Az objektum biztonsági hatókörének társítását a biztonsági hatókörről objektum – nincs származó kezelése. A biztonsági hatókörök közvetlen konfigurálásánál kizárólag a név és a leírás módosítása megengedett. Biztonsági hatókör nevének és leírásának módosításához a tulajdonságok megtekintésekor **Módosítás** engedély szükséges a **Biztonsági hatókörök** biztonságos objektumnál.  

 Új objektum létrehozásakor a Configuration Managerben a társítva lesz minden biztonsági hatókör, amely az az objektum létrehozásához használt fiók biztonsági szerepköreihez van társítva – Ha ezen biztonsági szerepkörök tartalmazzák-e a **létrehozása** engedéllyel vagy **biztonsági hatókör megadása** engedéllyel. Csak akkor válthat az objektum létrehozása után társított biztonsági hatóköröket.  

 Tegyük fel akkor hozzá vannak rendelve egy biztonsági szerepkör, amely engedélyt ad új határcsoport létrehozása. Amikor létrehoz egy határcsoportot, nincs lehetőség az adott biztonsági hatókörökkel rendelhető rendelkezik. Ehelyett a biztonsági hatóköröket, biztonsági szerepkörök adott biztonsági van társítva a rendszer automatikusan az új határcsoport. Miután az új határcsoport mentéséhez, módosíthatja az új határcsoport társított biztonsági hatóköröket.  

 A következő eljárással az objektumhoz rendelt biztonsági hatókörök konfigurálása.  

#### <a name="to-configure-security-scopes-for-an-object"></a>Biztonsági hatókörök konfigurálása objektumhoz  

1.  A Configuration Manager konzolon válassza ki olyan objektumot, amely támogatja a biztonsági hatókörhöz van hozzárendelve.  

2.  Az a **Home** lap a **besorolás** csoportjában válassza **biztonsági hatókör beállítása**.  

3.  A **Biztonsági hatókör beállítása** párbeszédpanelen jelölje be vagy törölje a biztonsági hatóköröket annak megfelelően, hogy melyeket kívánja az objektumhoz társítani. Minden olyan objektumhoz, amely támogatja a biztonsági hatóköröket, legalább egy biztonsági hatókört hozzá kell rendelni.  

4.  Válasszon **OK** a hozzárendelt biztonsági hatókörök mentéséhez.  

    > [!NOTE]  
    >  Amikor új objektumot hoz létre, azt több biztonsági hatókörhöz is hozzárendelheti. Az objektumhoz társított biztonsági hatókörök számának módosításához módosítsa ezt a hozzárendelést az objektum létrehozása után.  

##  <a name="BKMK_ConfigColl"></a> Gyűjtemények konfigurálása a biztonság kezeléséhez  
 Szerepkör alapú felügyeletnél a gyűjtemények konfigurálására nincs eljárás. Gyűjtemények nem rendelkezik a szerepköralapú adminisztrációs beállítások. Ehelyett hozzárendelt gyűjtemények azon rendszergazda felhasználó a rendszergazda felhasználó konfigurálásakor. A gyűjtemény azon biztonsági műveletei a felhasználó által hozzárendelt biztonsági szerepkörök engedélyezett határozza meg, hogy az engedélyeket, amely rendszergazdai jogosultságokkal rendelkezik a gyűjtemények és a gyűjtemény erőforrásainál (gyűjtemény tagjai).  

 Amikor a rendszergazda felhasználó engedélyekkel rendelkezik egy gyűjteményhez, egyúttal engedélyekkel rendelkezik az adott gyűjteményre korlátozott gyűjteményekhez is. Tegyük fel a szervezet összes asztali számítógép nevű gyűjteményt használja, és minden Észak-Amerika asztali számítógépek, amelyek az összes asztali számítógép gyűjteményre korlátozódik nevű gyűjtemény van. Ha egy rendszergazda felhasználó engedélyekkel rendelkezik az Összes asztali számítógép gyűjteményhez, ugyanezek az engedélyek rendelkezésére állnak az Összes közép-európai asztali számítógép gyűjteménynél is.

 Emellett a rendszergazda felhasználó nem használhatja a **törlése** vagy **módosítás** engedélyt a közvetlenül hozzá rendelt hozzájuk gyűjteményen. Azonban, hogy használhassák ezeket az engedélyeket az adott gyűjteményre korlátozott gyűjteményekhez. Az előző példában a rendszergazda felhasználó törölheti vagy módosíthatja az összes Észak-Amerika asztali számítógép gyűjteményen, de nem lehet törölni vagy módosítani az összes asztali számítógép gyűjteményen.  

##  <a name="BKMK_Create_AdminUser"></a> Új rendszergazda felhasználó létrehozása  
 Kezelheti a Configuration Manager szolgáltatásra vagy egy biztonsági csoport tagjainak hozzáférést engedélyez, egy rendszergazda felhasználó létrehozása a Configuration Managerben, és adja meg a felhasználó vagy felhasználói csoport Windows fiókját. Minden egyes rendszergazda felhasználó a Configuration Manager legalább egy biztonsági szerepkört és egy biztonsági hatókört kell rendelni. Emellett gyűjteményeket is hozzárendelhet a rendszergazda felhasználói felügyeleti hatókörének korlátozása céljából.  

 Új rendszergazda felhasználó létrehozására az alábbiakban ismertetett eljárások használhatók.  

#### <a name="to-create-a-new-administrative-user"></a>Új rendszergazda felhasználó létrehozása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **rendszergazda felhasználók**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **felhasználó vagy csoport hozzáadása**.  

4.  Válasszon **Tallózás**, majd válassza ki a felhasználói fiókot vagy csoportot az új rendszergazda felhasználóhoz használni.  

    > [!NOTE]  
    >  Konzolalapú felügyelet esetén csak tartományi felhasználók vagy biztonsági csoportok adhatók meg rendszergazda felhasználóként.  

5.  A **hozzárendelt biztonsági szerepkörök**, válassza a **Hozzáadás** az elérhető biztonsági szerepkörök listájának megnyitásához, jelölje be a egy vagy több biztonsági szerepkört, és válassza **OK**.  

6.  A biztonságos objektumok viselkedésének az új felhasználó meghatározásához a következő két lehetőség közül választhat:  

    -   **Objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**: Ez a beállítás a rendszergazda felhasználót hozzárendeli a **összes** biztonsági hatókörrel és a gyökérszintű, beépített gyűjteményekkel **minden rendszer** és **minden felhasználó és felhasználói csoport**. A felhasználóhoz rendelt biztonsági szerepkörök definiálják az objektumokhoz való hozzáférést. A rendszergazda felhasználó által létrehozott új objektumok az **Alapértelmezés** biztonsági hatókörhöz vannak társítva.  

    -   **Csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok**: Alapértelmezés szerint ez a beállítás a rendszergazda felhasználót hozzárendeli a **alapértelmezett** biztonsági hatókört, és a **minden rendszer** és **minden felhasználó és felhasználói csoport** gyűjtemények. A tényleges biztonsági hatókörök és gyűjtemények azonban az új rendszergazda felhasználó létrehozásához használt fiókkal társítottakra korlátozódnak. Ez a beállítás lehetővé teszi biztonsági hatókörök és gyűjtemények hozzáadását és eltávolítását a rendszergazda felhasználó felügyeleti hatókörének testreszabásához.  

    > [!IMPORTANT]  
    >  Az előző beállítások minden egyes hozzárendelt biztonsági hatókört és gyűjteményt a rendszergazda felhasználóhoz rendelt biztonsági szerepkörökhöz társítása. Egy harmadik beállítás segítségével **alapján a rendszergazda felhasználó biztonsági szerepkörök adott biztonsági hatókörökkel objektumok**, egyéni biztonsági szerepkörök adott biztonsági hatókörökkel és gyűjteményekkel társítja. Ezt lehetőséget az új rendszergazda felhasználó létrehozását követően érheti el, amikor módosítja a rendszergazda felhasználót.  

7.  Attól függően, hogy mit választott a 6. lépésben, hajtsa végre a következő műveleteket:  

    -   Ha a kiválasztott **objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**, válassza a **OK** művelet végrehajtásához.  

    -   Ha a kiválasztott **csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok**, dönthet úgy **Hozzáadás** kiválasztásához további gyűjteményeket és biztonsági hatóköröket. Vagy jelöljön ki egy vagy több objektumot a listából, és válassza a **eltávolítása** kattintva távolítsa el őket. Válasszon **OK** művelet végrehajtásához.  

##  <a name="BKMK_ModAdminUser"></a> Rendszergazda felhasználó felügyeleti hatókörének módosítása  
 A rendszergazda felhasználók felügyeleti hatókörét a felhasználóhoz rendelt biztonsági szerepkörök, biztonsági hatókörök és gyűjtemények hozzáadásával vagy eltávolításával módosíthatja. Minden egyes rendszergazda felhasználóhoz legalább egy biztonsági szerepkört és egy biztonsági hatókört kell rendelni. Előfordulhat, hogy egy vagy több gyűjteményt kell a felhasználó felügyeleti hatókörével társítania. A legtöbb biztonsági szerepkör együttműködik a gyűjteményekkel, és gyűjtemény hozzárendelése nélkül helyesen függvény nem.  

 Amikor módosít egy rendszergazda felhasználót, megváltoztathatja a biztonságos objektumok és a hozzárendelt biztonsági szerepkörök társításának működését. Az alábbi három működési mód közül választhat:  

-   **Objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**: Ez a beállítás a rendszergazda felhasználót hozzárendeli a **összes** hatókörrel és a gyökérszintű beépített gyűjteményekkel szinten **minden rendszer** és **minden felhasználó és felhasználói csoport**. A felhasználóhoz rendelt biztonsági szerepkörök definiálják az objektumokhoz való hozzáférést.  

-   **Csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok**: Ezt a beállítást társítja a rendszergazda felhasználót ugyanazon biztonsági hatókörök és gyűjtemények, amelyek a rendszergazda felhasználó konfigurálására használt fiókhoz társítva. Ez a beállítás lehetővé teszi biztonsági szerepkörök és gyűjtemények hozzáadását és eltávolítását a rendszergazda felhasználó felügyeleti hatókörének testreszabása céljából.  

-   **A biztonsági szerepköröket, a rendszergazda felhasználó csak biztonságos objektumok**: Ez a beállítás lehetővé teszi, hogy egyes biztonsági szerepkörök és adott biztonsági hatókörökkel és a felhasználói gyűjtemények közötti meghatározott társításokat hozhat létre.  

    > [!NOTE]  
    >  Ez a beállítás csak akkor érhető el, ha módosítja egy rendszergazda felhasználó tulajdonságait.  

A biztonságos objektumok viselkedésének aktuális konfigurációja megváltoztatja a további biztonsági szerepkörök hozzárendelésének folyamatát. A rendszergazda felhasználók felügyeletéhez a biztonságos objektumok különböző beállításai alapján az alábbi eljárások nyújtanak segítséget.  

A következő eljárással megtekintheti és kezelheti a rendszergazda felhasználó biztonságos objektumaira vonatkozó konfigurációs.  

#### <a name="to-view-and-manage-the-securable-object-behavior-for-an-administrative-user"></a>Egy rendszergazda felhasználó biztonságos objektumai viselkedésének megtekintéséhez és kezeléséhez:  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **rendszergazda felhasználók**.  

3.  Válassza ki a módosítani kívánt rendszergazda felhasználót.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **biztonsági hatókörök** fülre kattintva megtekintheti a biztonságos objektumok viselkedésének a jelen rendszergazda felhasználóra vonatkozó aktuális konfigurációját.  

6.  A biztonságos objektumok viselkedésének módosításához válasszon egy új, a biztonságos objektumok viselkedésére vonatkozó beállítást. Ez a konfiguráció módosítása után tekintse meg a további iránymutatásért biztonsági hatókörök és gyűjtemények konfigurálása a megfelelő eljárás, és a biztonsági szerepkörök az aktuális rendszergazda felhasználóhoz.  

7.  Válasszon **OK** a művelet elvégzéséhez.  

A biztonságos objektumok viselkedésének beállítása rendelkező rendszergazda felhasználók módosításához, a következő eljárással **objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**.  

#### <a name="for-option-all-securable-objects-that-are-relevant-to-their-associated-security-roles"></a>Esetén: Objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **rendszergazda felhasználók**.  

3.  Válassza ki a módosítani kívánt rendszergazda felhasználót.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **biztonsági hatókörök** lapon győződjön meg arról, hogy a rendszergazda felhasználó beállítása **objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**.  

6.  A hozzárendelt biztonsági szerepkörök módosításához válassza ki a **biztonsági szerepkörök** fülre.  

    -   További biztonsági szerepkörök az aktuális rendszergazda felhasználóhoz rendeléséhez kattintson **Hozzáadás**, jelölje be minden hozzárendelni, és válassza a kívánt biztonsági szerepkör a **OK**.  

    -   Biztonsági szerepkörök eltávolításához jelöljön ki egy vagy több biztonsági szerepkört a listából, és válassza a **eltávolítása**.  

7.  A biztonságos objektumok viselkedésének módosításához válassza ki a **biztonsági hatókörök** lapra, és válasszon egy új a biztonságos objektumok viselkedésének beállítása. Ez a konfiguráció módosítása után tekintse meg a további iránymutatásért biztonsági hatókörök és gyűjtemények konfigurálása a megfelelő eljárás, és a biztonsági szerepkörök az aktuális rendszergazda felhasználóhoz.  

    > [!NOTE]  
    >  Ha a biztonságos objektumok viselkedésének beállítása **objektumok minden olyan példánya, amely kapcsolódik a biztonsági szerepkörökhöz**, nem adja hozzá, vagy távolítsa el a megadott biztonsági hatóköröket és gyűjteményeket.  

8.  Válasszon **OK** művelet végrehajtásához.  

Azon rendszergazda felhasználók módosításához, amelyeknél a biztonságos objektumok viselkedésének beállítása **Csak a megadott biztonsági hatókörökhöz és gyűjteményekhez rendelt objektumpéldányok**, használja a következő eljárást:  

#### <a name="for-option-only-securable-objects-in-specified-security-scopes-or-collections"></a>Esetén: Csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **rendszergazda felhasználók**.  

3.  Válassza ki a módosítani kívánt rendszergazda felhasználót.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **biztonsági hatókörök** lapon győződjön meg arról, hogy a felhasználó beállítása **csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok**.  

6.  A hozzárendelt biztonsági szerepkörök módosításához válassza ki a **biztonsági szerepkörök** fülre.  

    -   További biztonsági szerepkörök hozzárendelése a felhasználóhoz, kattintson a **Hozzáadás**, jelölje be minden hozzárendelni, és válassza a kívánt biztonsági szerepkör a **OK**.  

    -   Biztonsági szerepkörök eltávolításához jelöljön ki egy vagy több biztonsági szerepkört a listából, és válassza a **eltávolítása**.  

7.  A biztonsági hatókörök és gyűjtemények társított biztonsági szerepkörök módosításához válassza ki a **biztonsági hatókörök** fülre.  

    -   Minden, az aktuális rendszergazda felhasználóhoz rendelt biztonsági szerepkörök új biztonsági hatóköröket vagy gyűjteményeket társítani, válassza a **Hozzáadás** válassza ki a négy beállítás valamelyikét. Ha **biztonsági hatókör** vagy **gyűjtemény**, jelölje be a kijelölést, majd válassza ki egy vagy több objektum **OK**.  

    -   Egy biztonsági hatókör vagy gyűjtemény eltávolításához válassza ki az objektumot, és válassza a **eltávolítása**.  

8.  Válasszon **OK** művelet végrehajtásához.  

Azon rendszergazda felhasználók módosításához, amelyeknél a biztonságos objektumok viselkedésének beállítása **Biztonsági szerepkörök adott biztonsági hatókörökkel és gyűjteményekkel történő társítása**, használja a következő eljárást:  

#### <a name="for-option-only-securable-objects-as-determined-by-the-security-roles-of-the-administrative-user"></a>Esetén: A biztonsági szerepköröket, a rendszergazda felhasználó csak a biztonságos objektumok  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **rendszergazda felhasználók**.  

3.  Válassza ki a módosítani kívánt rendszergazda felhasználót.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **biztonsági hatókörök** lapon győződjön meg arról, hogy a rendszergazda felhasználó beállítása **csak a megadott biztonsági hatókörökhöz és gyűjteményekhez objektumpéldányok**.  

6.  A hozzárendelt biztonsági szerepkörök módosításához válassza ki a **biztonsági szerepkörök** fülre.  

    -   További biztonsági szerepkörök az aktuális rendszergazda felhasználóhoz rendeléséhez kattintson **Hozzáadás**. Az a **biztonsági szerepkör hozzáadása** párbeszédpanelen jelöljön ki egy vagy több biztonsági szerepkört, válassza a **Hozzáadás**, és válassza ki a kijelölt biztonsági szerepkörökhöz társítandó objektumtípust. Ha **biztonsági hatókör** vagy **gyűjtemény**, jelölje be a kijelölést, majd válassza ki egy vagy több objektum **OK**.  

        > [!NOTE]  
        >  Legalább egy biztonsági hatókört konfigurálnia kell, mielőtt a kijelölt biztonsági szerepköröket hozzárendelné a rendszergazda felhasználóhoz. Több biztonsági szerepkör kijelölése esetén minden egyes konfigurált biztonsági hatókör és gyűjtemény társítva lesz az összes kijelölt biztonsági szerepkörhöz.  

    -   Biztonsági szerepkörök eltávolításához jelöljön ki egy vagy több biztonsági szerepkört a listából, és válassza a **eltávolítása**.  

7.  A biztonsági hatókörök és gyűjtemények, amelyek egy adott biztonsági szerepkörhöz társított módosításához válassza ki a **biztonsági hatókörök** lapon válassza ki a biztonsági szerepkört, és válassza a **szerkesztése**.  

    -   Új objektumokat a biztonsági szerepkörrel társítani, válassza a **Hozzáadás**, és válassza ki a kijelölt biztonsági szerepkörökhöz társítandó objektumtípust. Ha **biztonsági hatókör** vagy **gyűjtemény**, jelölje be a kijelölést, majd válassza ki egy vagy több objektum **OK**.  

        > [!NOTE]  
        >  Legalább egy biztonsági hatókört kell konfigurálnia.  

    -   Biztonsági hatókör vagy a biztonsági szerepkörhöz társított gyűjtemény eltávolításához jelölje ki az objektumot, és válassza **eltávolítása**.  

    -   Ha befejezte a társított objektumok módosítását, válassza ki a **OK**.  

8.  Válasszon **OK** művelet végrehajtásához.  

    > [!CAUTION]  
    >  Amennyiben egy biztonsági szerepkör gyűjteménytelepítési engedélyt biztosít a rendszergazda felhasználóknak, azok bármely olyan biztonsági hatókörből terjeszthetnek objektumokat, amelyeknél az objektumok **olvasására** vonatkozó engedélyekkel rendelkeznek, még abban az esetben is, ha az adott biztonsági hatókör egy másik biztonsági szerepkörhöz van társítva.  

