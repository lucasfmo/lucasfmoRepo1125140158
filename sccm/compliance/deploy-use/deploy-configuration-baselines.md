---
title: "Alapkonfigurációk központi telepítése |} Microsoft Docs"
description: "Alapkonfiguráció központi telepítéseinek meghatározásához és szeretne felvenni vagy eltávolítani alapkonfigurációk központi telepítésektől alapkonfigurációk központi telepítése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 9c9e6b7780c7c10c20a60dbbbf506e916031eb88
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>A System Center Configuration Managerben referenciakonfigurációk központi telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben referenciakonfigurációk kell telepíteni kell a felhasználók vagy eszközök egy vagy több gyűjteményt ezekhez a gyűjteményekhez ügyféleszközök értékelhessék a referenciakonfigurációt a megfelelésüket.  

Az **Alapkonfigurációk központi telepítése** párbeszédpanelen adhatja meg az alapkonfigurációk központi telepítéseit, mely során alapkonfigurációkat adhat hozzá a központi telepítésekhez vagy távolíthat el azokból, és megadhatja az értékelés ütemezését.  

## <a name="deploy-a-configuration-baseline"></a>Referenciakonfiguráció telepítése  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Referenciakonfigurációk**.  

3.  Az **Alapkonfigurációk** listában válassza ki a telepíteni kívánt alapkonfigurációt, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Telepítés**elemre.  

4.  Az **Alapkonfigurációk központi telepítése** párbeszédpanelen jelölje ki a telepíteni kívánt alapkonfigurációkat az **Elérhető alapkonfigurációk** listából. A **Hozzáadás** gombra kattintva adja hozzá ezeket a **Kiválasztott alapkonfigurációk** listához.  

    > [!IMPORTANT]  
    >  Ha egy telepített alapkonfigurációhoz hozzáadott konfigurációelemet módosít, a módosított konfigurációelem megfelelőségének értékelése a következő ütemezett értékelési időpontig nem történik meg.  

5.  Adja meg az alábbi további adatokat:  

    -   **Nem megfelelő szabályok szervizelése** – automatikusan javítja a megfelelőséget összes szabály, amely nem kompatibilis a Windows Management Instrumentation (WMI), a beállításjegyzék, parancsfájlok és a Configuration Manager által beléptetett mobileszközökre vonatkozó összes beállítást.  

    -   **Szervizelés engedélyezése a karbantartási időszakon kívül** : Ha lett konfigurálva karbantartási időszak ahhoz a gyűjteményhez, amelyikben az alapkonfigurációt telepíti, ezt a beállítást engedélyezve lehetővé teheti a megfelelőségi beállítások értékének a karbantartási időszakon kívüli javítását. Karbantartási időszakok kapcsolatos további információkért lásd: [karbantartási időszakok használata](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Riasztás létrehozása** – egy riasztást, ha az alapkonfiguráció megfelelősége kisebb, mint a megadott százalék a megadott dátummal és idővel konfigurálja. Azt is megadhatja, hogy kíván-e riasztást küldeni a System Center Operations Manager alkalmazásnak.  

7.  **Gyűjtemény** : A **Tallózás** gombra kattintva kiválaszthatja a gyűjteményt, amelyben telepíteni kívánja az alapkonfigurációt.  

8.  **Adja meg a megfelelőség értékelésének ütemezését az alapkonfigurációhoz** Megadja azt az ütemezést, mely szerint a telepített alapkonfiguráció kiértékelése történik az ügyfélszámítógépeken. Az ütemezés egyszerű, illetve egyéni is lehet.  

    > [!NOTE]  
    >  Egy alapkonfiguráció egy számítógépen való telepítésekor annak megfelelőségét az ütemezett kezdési időponttól számított két órán belül értékeli a rendszer. Egy felhasználó számára való telepítéskor annak megfelelőségét akkor értékeli a rendszer, amikor a felhasználó bejelentkezik.  

9. Az **OK** gombra kattintva zárja be az **Alapkonfigurációk központi telepítése** párbeszédpanelt a központi telepítés létrehozásához. A telepítés figyeléséről további információt lásd: [megfelelőségi beállítások figyelése](/sccm/compliance/deploy-use/monitor-compliance-settings).  

