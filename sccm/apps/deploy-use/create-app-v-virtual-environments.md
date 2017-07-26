---
title: "App-V virtuális környezetek létrehozása |} Microsoft Docs"
description: "Virtuális környezetek létrehozása a Microsoft Application Virtualization, így az alkalmazások egymás között megoszthatják az adatokat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa9e87830a3a51b01fae29b564c9267ec930a60d
ms.openlocfilehash: 377ed9732fb16b062f53e78504aea394acdb7462
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-app-v-virtual-environments-in-system-center-configuration-manager"></a>App-V virtuális környezetek létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Microsoft Application Virtualization (App-V) a virtuális alkalmazások telepítése virtuális környezetben a System Center Configuration Manager (a Configuration Manager), megoszthatja a ugyanazt a fájlrendszert és beállításjegyzéket ügyfél Windows-számítógépeken. Szokásos virtuális alkalmazásoktól eltérően ezek az alkalmazások adatokat megoszthatja egymással. Virtuális környezetek létrehozása, illetve módosítása az ügyfélszámítógépek az alkalmazás telepítésekor, illetve amikor az ügyfélgépek először értékelik ki a telepített alkalmazásokat. Ezen alkalmazásokat sorba rendezheti úgy, hogy amikor több alkalmazás próbálja a fájlrendszert vagy a beállításazonosítót módosítani, a sorrendben előbb lévőnek legyen elsőbbsége.  

> [!IMPORTANT]  
>  Ne használja az App-V virtuális környezetek védelmet biztosítanak például a kártevők elleni.  

 A következő eljárással App-V virtuális környezet létrehozása a Configuration Manager alkalmazásban.  

## <a name="create-an-app-v-virtual-environment"></a>App-V virtuális környezet létrehozása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **App-V virtuális környezetek**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **virtuális környezet létrehozása**.  

4.  Az a **virtuális környezet létrehozása** párbeszédpanelen adja meg a következő adatokat:  

    -   **Név**.  Adjon meg egy egyedi nevet a virtuális környezetet (legfeljebb 128 karakter).  

    -   **Leírás**. (Választható) Adja meg a virtuális környezet leírását.  

5.  Adhatja hozzá egy új központi telepítési típust rendeljen a virtuális környezethez, **Hozzáadás**. Legalább egy központi telepítési típus hozzárendelése szükséges.  

6.  Az a **alkalmazások hozzáadása** párbeszédpanelen adja meg a **csoportnév** (legfeljebb 128 karakter). Ezt a nevet fogja használni a virtuális környezetbe felvenni kívánt alkalmazások csoportjára hivatkozik.  

7.  Válasszon **Hozzáadás**, válassza ki az App-V 5 alkalmazásokat és központi telepítési típusokat, adja hozzá a csoporthoz, és válassza a kívánt **OK**.  

8.  Az a **alkalmazások hozzáadása** párbeszédpanelen kiválaszthatja **növekvő sorrend** vagy **csökkenő sorrend** beállítani az alkalmazást, amely élvez elsőbbséget, amikor több alkalmazás próbálja módosítani a rendszer vagy a beállításjegyzék-beállítások az azonos virtuális környezetben.  

9. Visszatérhet a **virtuális környezet létrehozása** párbeszédpanelen válassza ki **OK**.  

10. Amikor befejezte a csoportok hozzáadását, válassza ki a **OK** a virtuális környezet létrehozása. Az új virtuális környezet jelenik meg a **App-V virtuális környezetek** csomópont a Configuration Manager konzol. A virtuális környezetei állapotát az App-V virtuális környezet állapota jelentés használatával figyelheti.  

    > [!NOTE]  
    >  A virtuális környezet hozzáadása vagy módosítása ügyfél-számítógépeken, ha az alkalmazás telepítve van, vagy amikor az ügyfélgép először kiértékeli a telepített alkalmazások.  

