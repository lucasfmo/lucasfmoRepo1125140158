---
title: "Referenciakonfigurációk létrehozása |} Microsoft Docs"
description: "Referenciakonfigurációk létrehozása a System Center Configuration Managerben, amely központilag telepíthető egy gyűjteményhez."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 649942d3d468ec35c7246e08f741cdebd22fb3ac
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>Referenciakonfigurációk létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A referenciakonfigurációk a System Center Configuration Managerben előre definiált konfigurációelemeket és szükség esetén más referenciakonfigurációkat tartalmaznak. A referenciakonfiguráció létrehozását követően telepítheti azt egy gyűjteményre, hogy az abban lévő eszközök letöltsék a referenciakonfigurációt, és értékeljék vele a megfelelőségüket.  

 A referenciakonfigurációk a Configuration Manager konfigurációelemek adott változatait is tartalmazhat, vagy beállítható úgy, hogy mindig a konfigurációelem legújabb verzióját használja. Konfigurációelem-változatokról kapcsolatos további információkért lásd: [konfigurációs adatok kezelési feladatai](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

 A referenciakonfigurációk létrehozásához használható két módszer áll rendelkezésre:  

-   Konfigurációs adatok importálása egy fájlból. A **Konfigurációs adatok importálása varázsló**indításához az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** vagy **Referenciakonfigurációk** csomópontjában kattintson a **Konfigurációs adatok importálása**elemre.  

-   A **Referenciakonfiguráció létrehozása** párbeszédpanel használata új referenciakonfiguráció létrehozásához.  

 A **Referenciakonfiguráció létrehozása** párbeszédpanelt használva az alábbi eljárással hozhat létre referenciakonfigurációkat.  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Referenciakonfigurációk**.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Referenciakonfiguráció létrehozása**elemre.  

4.  A **Referenciakonfiguráció létrehozása** párbeszédpanelen adja meg a referenciakonfiguráció egyedi nevét és leírását. A név legfeljebb 255 karakterből, a leírás pedig 512 karakterből állhat.  

5.  A **Konfigurációs adatok** listában látható a referenciakonfigurációban szereplő összes konfigurációelem vagy referenciakonfiguráció. A **Hozzáadás** gombra kattintva új konfigurációelemet vagy referenciakonfigurációt vehet fel a listára. Az alábbiak közül választhat:  

    -   **Eszközök és megfelelőség**  

    -   **Szoftverfrissítések**  

    -   **Konfigurációelemek**  
      > [!IMPORTANT]
      > Ne haladja meg minden egyes konfigurációs alapterv legfeljebb 1000 szoftverfrissítés tartozhat.
6.  A **Cél módosítása** listát használva adhatja meg a **Konfigurációs adatok** listában kijelölt konfigurációelem viselkedését. Az alábbiak közül választhat:  

    -   **Kötelező:** Ha a konfigurációelem nem észlelhető az ügyféleszközön, a referenciakonfigurációt nem megfelelőként értékeli ki a rendszer. Ha észlelhető, a rendszer kiértékeli megfelelőség szempontjából.  

    -   **Választható:** A konfigurációelem megfelelőségét csak akkor értékeli ki a rendszer, ha az ügyfélszámítógépeken megtalálható az alkalmazás, amelyre hivatkozik. Ha az alkalmazás nem található, a rendszer nem jelöli meg a referenciakonfigurációt nem megfelelőként (csak alkalmazás-konfigurációelemekhez érvényes).  

    -   **Tiltott:** A referenciakonfigurációt nem megfelelőként értékeli ki a rendszer, ha a konfigurációelem észlelhető az ügyfélszámítógépeken (csak alkalmazás-konfigurációelemekhez érvényes).  

    > [!NOTE]
    >  A **Cél módosítása** lista csak akkor érhető el, ha a **Konfigurációelem létrehozása varázsló** **Általános** lapján bejelölte az **Ez a konfigurációelem alkalmazások beállításait tartalmazza**jelölőnégyzetet.  

7.  A **Változat módosítása** listát használva jelölje ki az ügyféleszközökön a megfelelőség szempontjából kiértékelendő konfigurációelem adott vagy legújabb változatát, illetve ha mindig a legújabb változatot szeretné használni, válassza a **Mindig a legutóbbit használja** beállítást. Konfigurációelem-változatokról kapcsolatos további információkért lásd: [konfigurációs adatok kezelési feladatai](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

8.  Távolítani egy konfigurációelemet a referenciakonfigurációból, jelölje ki a konfigurációs elem, és kattintson a **eltávolítása**.  

9. Kattintson az **OK** gombra a **Referenciakonfiguráció létrehozása** párbeszédpanel bezárásához és a referenciakonfiguráció létrehozásához.  

