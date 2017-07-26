---
title: "Adja meg a határok |} Microsoft Docs"
description: "Megtudhatja, hogyan határozza meg a hálózati helyek az intraneten, amely tartalmazhat a kezelni kívánt eszközöket."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 4a9dc4d9-e114-42ec-ae2b-73bee14ab04f
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bed70809008fde5e2b0215f4dce049402edf83ba
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="define-network-locations-as-boundaries-for-system-center-configuration-manager"></a>Hálózati helyeket határként határozza meg a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager határok, amely a kezelni kívánt eszközöket tartalmazó helyek a hálózaton. A határ egy eszköz a Active Directory-helyet, vagy az eszközre telepített Configuratoin Manager-ügyfél által azonosított hálózati IP-címe megegyezik.
 - Egyéni határokat manuálisan hozhat létre. Ugyanakkor a Configuration Manager nem támogatja a hálózat közvetlen megadását határként felsőbb szintű hálózatot észlel. Ehelyett az IP-címtartomány határtípust használhatja.
 - Konfigurálhatja a [Active Directory-Erdőfelderítés](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutForest) módszert automatikus felderítése, és határokat hozzon létre minden egyes IP-alhálózat és az Active Directory-helyhez. Ha az Active Directory-Erdőfelderítés olyan felsőbb szintű hálózatot észlel, amely az Active Directory-helyhez van rendelve, a Configuration Manager egy IP-címtartományhatárt konvertálja a felsőbb szintű hálózatot észlel.  

Nem ritka, hogy az IP-címmel, a Configuration Manager-rendszergazda által nem ismert, az eszköz. Ha a hálózati eszköz helye kétségei vannak, győződjön meg arról, mire az eszköz jelentés készít az helyeként használatával a **IPCONFIG** parancsot az eszközön.  

Határok létrehozásakor azok automatikusan a határ típusán és hatókörén alapuló nevet kapnak. Ez a név nem módosítható. Ehelyett azonosíthatja a határt, a Configuration Manager konzol segítségével egy leírást is megadhat.  

Minden határ érhető el a hierarchiában minden hely is használja. A határ létrehozása után módosíthatja a tulajdonságait, tegye a következőket:  
-   A határ felvétele egy vagy több határcsoportba.  
-   A határ típusának vagy hatókörének megváltoztatása.  
-   A határok **Helyrendszerek** lapján megtekintheti, hogy mely helyrendszer-kiszolgálók (terjesztési pontok, állapot-áttelepítési pontok és felügyeleti pontok) vannak az adott határhoz társítva.  

## <a name="to-create-a-boundary"></a>Határ létrehozása  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Hierarchiakonfiguráció** > **határok**  

2.  A **Kezdőlap**  **Létrehozás** csoportjában kattintson a **Létrehozás Boundary.**elemre.  

3.  A Határ létrehozása párbeszédpanel **Általános** lapján a **Leírás** mezőben megadott egyszerű név vagy hivatkozás segítségével azonosíthatja a határt.  

4.  Adja meg a határ **Típus** beállítását:  

    -   Ha az **IP-alhálózat**értéket adja meg, ehhez a határhoz meg kell adnia az **Alhálózati azonosító** értékét.  
        > [!TIP]  
        >  A **Hálózat** és az **Alhálózati maszk** mező kitöltésével automatikusan megadható az **Alhálózati azonosító** értéke. A határ mentésekor csak az Alhálózati azonosító értékét menti a folyamat.  

    -   Ha az **Active Directory-hely**beállítást választja, a helykiszolgáló helyi erdőjében meg kell adnia vagy a **Tallózás** funkcióval meg kell keresnie egy Active Directory-helyet.  

        > [!IMPORTANT]  
        >  Amikor a határhoz Active Directory-helyet ad meg, a határhoz tartozik minden olyan IP-alhálózat, amely tagja az adott Active Directory-helynek. Ha az Active Directory-hely konfigurációja megváltozik az Active Directoryban, a határban szereplő hálózati helyek is megváltoznak.  

    -   Ha az **IPv6-előtag**beállítást választja, az IPv6-előtagok formátumában kell kitöltenie az **Előtag** mezőt.  

    -   Ha az **IP-címtartomány**beállítást választja, meg kell adnia egy **Kezdő IP-cím** és egy **Záró IP-cím** értéket, amelyben egy IP-alhálózat egy része vagy több IP-alhálózat szerepel.    

5.  Az új határ mentéséhez kattintson az **OK** gombra.  

## <a name="to-configure-a-boundary"></a>Határ konfigurálása  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Hierarchiakonfiguráció** > **határok**  

2.  Válassza ki a módosítandó határt.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  A határhoz tartozó **Tulajdonságok** párbeszédpanelen az **Általános** lap választásával tudja szerkeszteni a határra vonatkozó **Leírás** vagy **Típus** beállítást. A határok hatókörét a határra vonatkozó hálózati helyek szerkesztésével is meg lehet változtatni. Például Active Directory-hely határánál meg lehet adni egy új Active Directory-hely nevét.  

5.  A **Helyrendszerek** lap választásával tudja megtekinteni az ehhez a határhoz társított helyrendszereket. Ezt a konfigurációt a határ tulajdonságaiból nem lehet megváltoztatni.  

    > [!TIP]  
    >  Ahhoz, hogy egy helyrendszer-kiszolgáló helyrendszerként legyen felsorolva egy határhoz, a helyrendszer-kiszolgálót helyrendszer-kiszolgálóként kell társítani legalább egy, az adott határt tartalmazó határcsoporthoz. Ennek a konfigurációja a határcsoport **Referenciák** lapján történik.  

6.  A határra vonatkozó határcsoporttagság módosításához válassza a **Határcsoportok** lapot:  

    -   A határ egy vagy több határcsoportba való felvételéhez kattintson a **Hozzáadás**gombra, jelölje be egy vagy több határcsoport jelölőnégyzetét, majd kattintson az **OK**gombra.  

    -   Ha ezt a határt szeretné eltávolítani egy határcsoportból, jelölje ki a határcsoportot, majd kattintson az **Eltávolítás**gombra.  

7.  A határ tulajdonságainak bezárásához és a konfiguráció mentéséhez kattintson az **OK** gombra.  

