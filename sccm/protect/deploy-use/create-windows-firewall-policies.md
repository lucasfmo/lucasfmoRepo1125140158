---
title: "A Windows tűzfal házirendek Endpoint Protection |} Microsoft Docs"
description: "Megtudhatja, hogyan létrehozása és központi telepítése tűzfal házirendek Endpoint Protection a System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ecdfad1-6305-45a8-ae75-3f33b967cb8f
caps.latest.revision: 5
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: acd75a8b22d050970b8c1176f725ddb4445633aa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-and-deploy-windows-firewall-policies-for-endpoint-protection-in-system-center-configuration-manager"></a>Szabályzatok létrehozása és telepítése a Windows tűzfal az Endpoint Protection a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az Endpoint Protection a System Center 2012 Configuration Manager tűzfal házirendjei lehetővé teszik a Windows tűzfal alapszintű konfigurációs és karbantartási feladatok végrehajtása az ügyfélszámítógépeken a hierarchiában. A Windows tűzfal házirendjei segítségével a következő feladatokat hajthatja végre:  

-   Szabályozhatja a Windows tűzfal ki- és bekapcsolását.  

-   Szabályozhatja az ügyfélszámítógépek bejövő kapcsolatainak engedélyezését.  

-   Szabályozhatja, hogy kapjanak-e a felhasználók értesítést, amikor a Windows tűzfal egy új programot blokkol.  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **Endpoint Protection**, és kattintson a **Windows tűzfal házirendek**.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Windows tűzfal házirend létrehozása**elemre.  

4.  A **Windows tűzfal házirend létrehozása varázsló** elem **Általános**lapján adja meg a tűzfal-házirend nevét (az erre vonatkozó leírást is itt adhatja meg), majd válassza a **Tovább**gombot.  

5.  A varázsló **Profilbeállítások** lapján az egyes hálózati profilok következő beállításait konfigurálhatja:  

    > [!IMPORTANT]  
    >  Ha Windows Server 2008 és Windows Vista Service Pack 1 rendszerű számítógépekre szeretné alkalmazni a Windows tűzfal beállításait, először telepítenie kell [a KB971800. számú gyorsjavítást](http://go.microsoft.com/fwlink/p/?LinkId=231239) ezeken a számítógépeken.  

    > [!NOTE]  
    >  A hálózati profilokkal kapcsolatos további információkat a Windows-dokumentációban találhatja.  

    -   **A Windows tűzfal engedélyezése**  

        > [!NOTE]  
        >  Ha a **Windows tűzfal engedélyezése** lehetőség nincs bekapcsolva, a varázsló további beállításai sem érhetők el ezen a lapon.  

    -   **Az összes bejövő kapcsolat tiltása, az engedélyezett programok listáján lévőket is beleértve**  

    -   **A felhasználó értesítése, ha a Windows tűzfal új programot blokkol**  

6.  A varázsló **Összegzés** lapján ellenőrizze a végrehajtandó műveleteket, majd fejezze be a varázslót.  

7.  Ellenőrizze, hogy az új Windows tűzfal házirend megjelenik-e a **Windows tűzfal házirendek** listában.  

##  <a name="BKMK_Assign"></a> A Windows tűzfal házirend központi telepítése  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **Endpoint Protection**, és kattintson a **Windows tűzfal házirendek**.  

3.  A **Windows tűzfal házirendek** listában válassza a telepíteni kívánt Windows tűzfal házirendet.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.  

5.  A **Windows tűzfal házirend telepítése** párbeszédpanelen adja meg a Windows tűzfal házirendhez hozzárendelni kívánt gyűjteményt, majd adja meg a hozzárendelési ütemezést. A Windows tűzfal házirend az itt megadott ütemezés és az ügyfelek Windows tűzfal beállításai alapján végzi el a megfelelőségi értékelést. Az újrakonfigurálás a Windows tűzfal házirend szabályaihoz alkalmazkodik.  

6.  Az **OK** gombra kattintva bezáródik a **Windows tűzfal házirend telepítése** párbeszédpanel, és megkezdődik a Windows tűzfal házirend telepítése.  

    > [!IMPORTANT]  
    >  Ha egy gyűjteményre telepít Windows tűzfal házirendet, a rendszer 2 órán keresztül véletlenszerű sorrendben alkalmazza a házirendet a számítógépeken, hogy elkerülje a hálózat elárasztását.

