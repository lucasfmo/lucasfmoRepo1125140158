---
title: "Alkalmazások központi telepítésének szimulálása |} Microsoft Docs"
description: "Értékelje ki, az észlelési módszert, követelményeket és a központi telepítési típus függőségeinek az alkalmazás telepítése nélkül."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0ad42d07d260581099046f11255ee312046b2595
ms.openlocfilehash: b06539ded21eac71dda7da89dae96fda7a801260
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>Alkalmazások központi telepítésének a System Center Configuration Managerrel szimulálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Szimulált központi telepítés segítségével tesztelje az alkalmazás központi telepítése az alkalmazás telepítése vagy eltávolítása nélkül. A szimulált központi telepítés kiértékeli az észlelési módszert, követelményeket és a központi telepítési típus függőségeit. Azt jelzi, hogy az eredményeket a **központi telepítések** munkaterület a **figyelés** munkaterületen. Ez a témakör az eljárás segítségével a System Center Configuration Manager (a Configuration Manager) alkalmazás központi telepítésének szimulálása.  

> [!NOTE]  
> Mobileszközök gyűjteményeire vonatkozóan nem használható szimulált központi telepítés.  
>   
> **Eltávolítás** céllal nem lehet alkalmazás központi telepítését végrehajtani, ha ugyanazzal az alkalmazással éppen aktív egy szimulált központi telepítés.  

## <a name="configure-a-simulated-application-deployment"></a>Egy alkalmazás szimulált központi telepítés konfigurálása

1.  A Configuration Manager konzolon válassza ki a következők egyikét:  
    -   Felhasználók gyűjteménye.  
    -   Eszközök gyűjteménye.  
    -   Configuration Manager-alkalmazás.  

2.  Az a **Home** lap a **telepítési** csoportjában válassza **központi telepítés szimulálása**.  

3.  Alkalmazás központi telepítés szimulálása varázslóban adja meg a szimulált központi telepítés a következő adatokat:  

    -   **Alkalmazás**. Válasszon **Tallózás**, majd válassza ki az alkalmazást, a szimulált központi telepítés létrehozásához.  

    -   **Gyűjtemény**. Válasszon **Tallózás**, és válassza ki a gyűjteményt, a szimulált központi telepítéshez használni kívánt.  

    -   **A művelet**. A legördülő listából válassza ki, hogy a telepítés vagy az Eltávolítás a kijelölt alkalmazás szimulálásához.  

    -   **Automatikus központi telepítés felhasználói bejelentkezéssel vagy anélkül**. Ha ez a beállítás be van jelölve, az ügyfelek a szimulált központi telepítés értékelése, attól függetlenül, hogy a bejelentkezett.  

4.  Kattintson a **következő**, ellenőrizze az adatokat a **összegzés** lapon, majd fejezze be a varázslót az alkalmazás szimulált központi telepítés létrehozásához.  

5.  Szimulált alkalmazások jelennek meg a **központi telepítések** csomópontjának a **figyelés** munkaterület céllal **szimulálás**. További információ az alkalmazások központi telepítésének figyeléséről: [figyelése a System Center Configuration Manager konzolról alkalmazások](../../apps/deploy-use/monitor-applications-from-the-console.md).  

