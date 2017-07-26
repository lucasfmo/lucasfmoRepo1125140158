---
title: "Használati feltételek a System Center Configuration Managerben |} Microsoft Docs"
description: "Felhasználói csoportok a System Center Configuration Managerben az feltételeket és kikötéseket."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d3f9e6b-4d71-4fc4-9b91-47f1bfbd8c70
caps.latest.revision: 9
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: 20be68496099a67ad2d475067f073da2cef16c86
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="add-terms-and-conditions-with-system-center-configuration-manager"></a>Adja hozzá a használati feltételek a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager feltételek és kikötések telepítene felhasználói csoportok számára azt ismertetik, hogyan befolyásolják az eszköz regisztrációjától, hozzáférhet a munkahelyi erőforrásokhoz és a vállalati portál használatával a eszközök és felhasználók. A felhasználóknak el kell fogadniuk a használati feltételeket ahhoz, hogy regisztrálhassanak a vállalati portálon, és így hozzáférhessenek a munkájukhoz.  

 ## <a name="working-with-terms-and-conditions-policies-in-system-center-configuration-manager"></a>Használati feltételekre vonatkozó házirendek használata a System Center Configuration Managerben  
 Használati feltételek több készletét hozhatja létre és telepítheti. Emellett ugyanazon használati feltételek különböző nyelvű verzióit is elkészítheti, majd telepítheti azokat a megfelelő csoportokban.  

## <a name="to-create-a-terms-and-conditions"></a>Használati feltételek létrehozása  

1.  A Configuration Manager konzolon lépjen a következő elemre: **Eszközök és megfelelőség** > **Áttekintés** > **Megfelelőségi beállítások** > **Használati feltételek**.  

2.  Kattintson a **Használati feltételek létrehozása** lehetőségre új használati feltételek létrehozásához.  

3.  Az **Általános** lapon adja meg az alábbi adatokat:  

    -   **Nevét** -a Configuration Manager-konzolon megjelenő egyedi név  

    -   **Leírás** - feltételek azonosítását segítő részletek és a Configuration Manager konzolon feltételek  

     Ezután kattintson a **Tovább**gombra.  

4.  A **Feltételek** lapon adja meg az alábbi adatokat:  

    -   **Cím** : a vállalati portálon a felhasználók számára megjelenő cím  

    -   **Feltételek szövege** : a vállalati portálon a felhasználók számára megjelenő használati feltételek  

    -   **Annak magyarázata, hogy mit jelent a feltételek elfogadása a felhasználó részéről** – a felhasználók számára megjelenő, az elfogadásra vonatkozó címke. **Példa**: "Elfogadom a feltételeket és kikötéseket."  

     Ezután kattintson a **Tovább**gombra.  

5.  Fejezze be a varázslót az új használati feltételek létrehozásához. Az új használati feltételek megjelennek a Használati feltételek csomópontban az Eszközök és megfelelőség munkaterületen.  

## <a name="to-deploy-a-terms-and-conditions"></a>Használati feltételek központi telepítése  

1.  A Configuration Manager konzolon lépjen a következő elemre: **Eszközök és megfelelőség** > **Áttekintés** > **Megfelelőségi beállítások** > **Használati feltételek**.  

2.  Válassza ki a telepíteni kívánt elemet a **Használati feltételek** listából, majd kattintson a **Telepítés**elemre.  

3.  **Tallózással** keresse meg a **Gyűjteményt** , amelyben telepíteni szeretné a használati feltételeket, majd kattintson az **OK**gombra.  

     Amikor a megcélzott eszközök hozzáférnek a Vállalati portál alkalmazáshoz, az megjeleníti a telepített használati feltételeket. Ahhoz, hogy hozzáférhessenek a vállalati erőforrásokhoz, a felhasználóknak el kell fogadniuk ezeket a feltételeket.  

    > [!NOTE]  
    >  Ha több olyan felhasználógyűjteményben is telepíti az adott használati feltételeket, melynek egy felhasználó tagja, az adott felhasználó számára azonos használati feltételek több példánya lesz látható a vállalati portál megnyitásakor. Mivel a felhasználók csak az összes feltétel elfogadását vagy elutasítását hajthatják végre, nem áll fenn az elfogadás olyan nem egyértelmű állapotának veszélye, melyben a felhasználó elfogadta és el is utasította a feltételeket. A használati feltételek elfogadására vonatkozó jelentés a használati feltételek minden készletéhez egyetlen sort fog tartalmazni az egyes felhasználók esetében, így a jelentés nem tartalmaz hibákat.  

## <a name="to-monitor-terms-and-conditions"></a>A használati feltételek figyelése  

1.  Használati feltételek központi telepítését a Configuration Manager konzolon figyelheti meg. A Configuration Manager konzolon nyissa meg: **Figyelés** > **Áttekintés** > **Központi telepítések**.  

2.  Válassza ki a használati feltételek központi telepítését a központi telepítések listájából.  

     Az összegzési területen a következő statisztikai adatok jelennek meg:  

    -   **Megfelelő** – A felhasználók elfogadták a használati feltételek legújabb verzióját.  

    -   **Hiba**  

    -   **Nem megfelelő** – A felhasználók elfogadták a használati feltételeket, de nem a legújabb verziót.  

    -   **Ismeretlen** – A felhasználók nem fogadták el a használati feltételeket, beleértve a regisztrált eszköz nélküli felhasználókat is.  

3.  Jelölje ki a használati feltételek központi telepítését, majd válassza az **Összefoglalás futtatása** lehetőséget az egyes felhasználók központi telepítési állapotának megtekintéséhez.  

     A Központi telepítés állapota képernyőn válassza ki a megfelelő állapot lapját az adott állapottal rendelkező felhasználók megtekintéséhez. Az **Összefoglalás futtatása** elemre kattintva frissítheti az adatokat a hierarchiában. Kattintson a **Frissítés** elemre a konzol adatainak frissítéséhez.  

## <a name="to-view--a-terms-and-conditions-report"></a>A használati feltételek jelentésének megtekintése  

1.  A Configuration Manager konzolon lépjen a következő elemre: **Figyelés** > **Áttekintés** > **Jelentéskészítés** > **Jelentés**.  

2.  Válassza a **Használati feltételek elfogadása** lehetőséget, majd kattintson a **Futtatás**elemre. Ekkor megnyílik a használati feltételek elfogadására vonatkozó jelentés. A jelentésben megjelenik az összes olyan felhasználó, akinek telepítette a használati feltételeket. A jelentés mezői a következő adatokat tartalmazzák:  

    -   A használati feltételek neve  

    -   Felhasználónév  

    -   Elfogadott verzió  

    -   Elfogadás dátuma  

    -   Legújabb elfogadva  

## <a name="updates-and-version-control-for-terms-and-conditions"></a>A használati feltételek frissítése és a verziókövetése  
 Meglévő használati feltételek szerkesztésekor beállíthatja, hogy mi történjen a használati feltételek telepítésekor. Az alábbi eljárással frissítheti a meglévő használati feltételeket.  

### <a name="how-to-work-with-multiple-versions-of-terms-and-conditions"></a>A használati feltételek több változatának használata  

1.  A Configuration Manager konzolon lépjen a következő elemre: **Eszközök és megfelelőség** > **Áttekintés** > **Megfelelőségi beállítások** > **Használati feltételek**.  

2.  Jelölje ki a használati feltételek szerkeszteni kívánt példányát, majd kattintson rá a duplán a megnyitásához.  

3.  A szükséges módosítások végrehajtásához szerkesztheti az **Általános** és a **Feltételek** lap tartalmát is.  

4.  A **Feltételek** lapon megadhatja, hogy az új verzió minden felhasználótól megkövetelje-e a használati feltételek elfogadását, vagy az új verzió csak az új felhasználók számára jelenjen meg.  

     Javasoljuk, hogy amikor jelentős módosításokat hajt végre a használati feltételeken, mindig növelje meg a verziószámot és követelje meg azok elfogadását. Akkor tartsa meg az aktuális verziószámot, ha például gépelési hibákat javít vagy a formázást módosítja.

> [!div class="button"]
[< Előző lépés](configure-intune-subscription.md)[következő lépés >  ](create-service-connection-point.md)

