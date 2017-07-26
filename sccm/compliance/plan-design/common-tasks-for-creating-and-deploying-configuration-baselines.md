---
title: "Referenciakonfigurációk - Configuration Manager kapcsolódó általános feladatok |} Microsoft Docs"
description: "További tudnivalók a létrehozása és a System Center Configuration Manager alapkonfigurációk központi telepítése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 991eff171dce95590a7f050e0d3b07f98c0224b3
ms.openlocfilehash: 5682cacb43af5bf9248446f1c35b08f137bdae9d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>Gyakori feladatok létrehozása és telepítése a konfigurációs alaptervek a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör általános eseteken segítségével megtudhatja, hogyan hozhat létre és telepíthet a System Center Configuration Manager konfigurációs alapterv.  

 Ha már ismeri a megfelelőségi beállításokat, az összes használt funkcióra vonatkozó részletes dokumentációt megtalálható a [referenciakonfigurációk létrehozása](../../compliance/deploy-use/create-configuration-baselines.md) és [alapkonfigurációk központi telepítése](../../compliance/deploy-use/deploy-configuration-baselines.md) témaköröket.  

 Megkezdése előtt olvassa el a [Ismerkedés a System Center Configuration Manager megfelelőségi beállítások](../../compliance/get-started/get-started-with-compliance-settings.md) néhány alapvető tudnivalók a megfelelőségi beállítások, valamint is [tervezése és megfelelőségi beállítások konfigurálása](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) megvalósításához szükséges előfeltételeket.  

## <a name="create-a-configuration-baseline"></a>Referenciakonfiguráció létrehozása  
 Ebben a példában létrehozott csak Windows 10 rendszerű számítógépekhez a Configuration Manager-ügyfelet futtató egy konfigurációelemet.  

 A konfigurációelem legalább 6 karakterből álló jelszót követel meg a Windows 10 rendszerű számítógépeken. A konfigurációelem neve **Windows 10-jelszó kényszerítése**.  

A következő eljárásban megismerheti, hogy miként veheti fel ezt a konfigurációelemet egy referenciakonfigurációba, hogy előkészítse a telepítéshez.  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Referenciakonfigurációk**.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Referenciakonfiguráció létrehozása**elemre.  

4.  A **Referenciakonfiguráció létrehozása** párbeszédpanelen adja meg az alábbiakat:  

    -   **Név** – Adja meg a **Windows 10-jelszavak** nevet (vagy egy tetszés szerinti másik nevet).  

5.  Kattintson a **Hozzáadás** > **Konfigurációelemek**.  

6.  A **Konfigurációelemek hozzáadása** párbeszédpanelen válassza a korábban létrehozott **Windows 10-jelszó kényszerítése** konfigurációelemet, majd kattintson a **Hozzáadás**gombra.  

7.  Az OK gombra kattintva zárja be a **Konfigurációelemek hozzáadása** párbeszédpanelt, és lépjen vissza a **Referenciakonfiguráció létrehozása** párbeszédpanelre, amelynek az alábbi képernyőképhez hasonlóan kell megjelennie:  

     ![Hozzon létre Referenciakonfigurációt párbeszédpanel](/sccm/compliance/plan-design/media/Create-Configuration-Baseline.png)  

8.  Az **OK** gombra kattintva zárja be a **Referenciakonfiguráció létrehozása** párbeszédpanelt.  

 Most már megtekintheti az imént létrehozott referenciakonfigurációt a **Referenciakonfigurációk** csomópont a Configuration Manager konzol.  

## <a name="deploy-the-configuration-baseline"></a>Telepítse a referenciakonfigurációt  
 Ebben a példában az előző eljárásban létrehozott referenciakonfigurációt telepíti egy számítógép-gyűjteményre.  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Referenciakonfigurációk**.  

3.  A referenciakonfigurációk listájában jelölje ki a **Windows 10-jelszavak**elemet.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**gombra.  

5.  A **Referenciakonfigurációk központi telepítése** párbeszédpanelen adja meg az alábbiakat:  

    -   **Kiválasztott referenciakonfigurációk** – Győződjön meg arról, hogy a rendszer automatikusan felvette a **Windows 10-jelszavak** referenciakonfigurációt erre a listára.  

    -   **Nem megfelelő szabályok szervizelése** – ellenőrizze, hogy ezt a jelölőnégyzetet annak biztosítására, hogy ha a helyes beállítások nincsenek jelen a megcélzott eszközökön, majd azok lesz kijavítva a Configuration Manager által.  

    -   **Gyűjtemény** – Kattintson a **Tallózás** gombra egy számítógép-gyűjtemény kiválasztásához, amelyen a referenciakonfigurációt ki kell értékelni, és megfelelőség szempontjából szervizelni kell. Ebben a példában a referenciakonfiguráció a beépített **Minden asztali és kiszolgáló ügyfél** gyűjteményre lett telepítve.  

        > [!TIP]  
        >  Ne aggódjon, ha a kiválasztott gyűjtemény nem Windows 10 rendszerű számítógépeket vagy eszközöket tartalmaz. Amennyiben támogatott platformokat konfigurált a létrehozott konfigurációelemben, csak Windows 10 rendszerű számítógépek megfelelősége lesz kiértékelve.  

    -   Szükség esetén konfigurálja az ütemezést, amellyel a referenciakonfiguráció ki lesz értékelve. Ellenkező esetben hagyja meg az alapértelmezett **7 nap**értéket.  

6.  A párbeszédpanel ekkor az alábbihoz hasonló módon fog kinézni:  

     ![Konfigurációs alapterv párbeszédpanel telepítése](/sccm/compliance/plan-design/media/Deploy-configuration-baselines.png)  

7.  Az **OK** gombra kattintva zárja be a **Referenciakonfigurációk központi telepítése** párbeszédpanelt, és hozza létre a telepítést.  

 Ha gyorsan át szeretné tekinteni a jelen telepítés megfelelőségi statisztikáját, a **Figyelés** munkaterületen kattintson a **Központi telepítések**elemre. A képernyő alján látható a **Megfelelőségi statisztika** diagram.  

 Részletesebb információ a referenciakonfigurációk figyeléséről, lásd: [megfelelőségi beállítások figyelése](../../compliance/deploy-use/monitor-compliance-settings.md)  

