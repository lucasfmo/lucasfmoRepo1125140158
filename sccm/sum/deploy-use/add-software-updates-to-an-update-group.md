---
title: "Frissítések felvétele frissítési csoportba - Configuration Manager |} Microsoft Docs"
description: "Manuális vagy automatikus szoftverfrissítések felvétele frissítési csoportba az adott környezetben."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: a0767664-fd60-46a8-9da5-86cc431ce53c
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4e44e2b8f6baf020c3b7742bafd607082ffacaa4
ms.openlocfilehash: 02e30ba48f3564fa8a31f21793c145054e02e002
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="add-software-updates-to-an-update-group"></a>Szoftverfrissítések felvétele frissítési csoportba  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A szoftverfrissítési csoportok hatékony módszert kínálnak a környezet szoftverfrissítésének megszervezésére. A szoftverfrissítéseket manuálisan vagy egy automatikus központi telepítési szabály segítségével veheti fel a megfelelő frissítési csoportba. A szoftverfrissítési csoportokat szintén telepítheti manuálisan vagy egy automatikus központi telepítési szabály segítségével. Szoftverfrissítési csoport telepítése után új szoftverfrissítéseket adhat hozzá a csoporthoz, és a Configuration Manager automatikusan telepíteni fogja őket. Az alábbi eljárás szerint adhat hozzá szoftverfrissítéseket egy új vagy meglévő szoftverfrissítési csoporthoz.  

#### <a name="to-add-software-updates-to-a-new-software-update-group"></a>Szoftverfrissítések hozzáadása egy új szoftverfrissítési csoporthoz  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson a **Minden szoftverfrissítés**lehetőségre.  

3.  Válassza ki azokat a szoftverfrissítéseket, amelyeket fel szeretne venni az új szoftverfrissítési csoportba.  

4.  A **Kezdőlap** **Frissítés** csoportjában kattintson a **Szoftverfrissítési csoport létrehozása**lehetőségre.  

5.  Adja meg a szoftverfrissítési csoport nevét és leírását (ez utóbbi nem kötelező). A név és a leírás lehetőleg utaljon arra, hogy milyen típusú szoftverfrissítéseket tartalmaz a csoport. A folytatáshoz kattintson a **Létrehozás**gombra.  

6.  Kattintson a **Szoftverfrissítési csoportok** lehetőségre, hogy megjelenjen az új szoftverfrissítési csoport.  

7.  Válassza ki a szoftverfrissítési csoportot, és a **Kezdőlap** **Frissítés** csoportjában kattintson a **Tagok megjelenítése** lehetőségre, amely megjeleníti a csoportban levő szoftverfrissítések listáját.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>Szoftverfrissítések felvétele meglévő szoftverfrissítési csoportba  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson a **Minden szoftverfrissítés**lehetőségre.  

3.  Válassza ki azokat a szoftverfrissítéseket, amelyeket fel szeretne venni az új szoftverfrissítési csoportba.  

    > [!NOTE]  
    >  Az a **minden szoftverfrissítés** csomópont, alapértelmezés szerint a Configuration Manager szoftverfrissítéseket jeleníti meg csak egy **kritikus** és **biztonsági** besorolású, az elmúlt 30 napban kiadott.  

4.  A **Kezdőlap** lapon lévő **Frissítés** csoportban kattintson a **Tagság szerkesztése**elemre.  

5.  Válassza ki azt a frissítési csoportot, amelybe fel szeretné venni a szoftverfrissítéseket.  

6.  Kattintson a **Szoftverfrissítési csoportok** csomópontra a szoftverfrissítési csoport megjelenítéséhez.  

7.  Válassza ki a szoftverfrissítési csoportot, és a **Kezdőlap** **Frissítés** csoportjában kattintson a **Tagok megjelenítése** lehetőségre, amely megjeleníti a csoportban levő szoftverfrissítések listáját.  

