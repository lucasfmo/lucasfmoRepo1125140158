---
title: "Felhasználói adatokat és profilokat tartalmazó konfigurációelemek létrehozása |} Microsoft Docs"
description: "Mappa átirányítása, offline fájlokhoz és barangoló profilok kezeléséhez használja a System Center Configuration Managerben az adatokat és profilokat tartalmazó konfigurációs elemek."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fcbcc81-cd6f-496e-b075-ef1afa2b8ccc
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 85b984d739dc9f9d2046186b381eff54ba687c66
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="create-user-data-and-profiles-configuration-items-in-system-center-configuration-manager"></a>Felhasználói adatokat és profilokat tartalmazó konfigurációelemek létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Felhasználói adatokat és profilokat tartalmazó konfigurációelemek a System Center Configuration Managerben olyan beállításokat tartalmaznak, kezelhető a mappaátirányítás, offline fájlokhoz és barangoló profilok a Windows 8 rendszerű számítógépeken, és később a hierarchiában lévő felhasználók számára. Lehetőség van például a következőkre:  

-   A felhasználó Dokumentumok mappájának átirányítására egy hálózati megosztásra.  

-   Annak biztosítására, hogy a hálózaton található megadott fájlok akkor is elérhetők a felhasználó számítógépén, ha a hálózati kapcsolat nem érhető el.  

-   Annak konfigurálására, hogy a felhasználó be- vagy kijelentkezésekor mely fájlok legyenek szinkronizálva egy hálózati megosztással a felhasználó központi profiljában.  

 Más konfigurációelemektől eltérően a Configuration Manager alkalmazásban nem adja hozzá a felhasználói adatokat és profilokat konfigurációs elemet a referenciakonfigurációhoz, majd telepíteni. Ehelyett a konfigurációelemeket közvetlenül kell telepíteni a **Felhasználói adatok és profilok konfigurációs elemének központi telepítése** párbeszédpanelen.  

> [!IMPORTANT]  
>  Felhasználói adatokat és profilokat tartalmazó konfigurációelemeket csak felhasználói gyűjteményekben lehet telepíteni.  

## <a name="enable-user-data-and-profiles-for-compliance-settings"></a>Felhasználói adatok és profilok megfelelőségi beállításainak engedélyezése  
 A következő eljárással konfigurálhatja  a felhasználói adatok és profilok megfelelőségi beállítására vonatkozó alapértelmezett ügyfélbeállítást a hierarchiában található összes számítógéphez. Ha ezt a beállítást csak néhány számítógépen szeretné alkalmazni, hozzon létre egyéni ügyfél-eszközbeállítást, és rendelje hozzá az azokat a számítógépeket tartalmazó gyűjteményhez, amelyeken a felhasználói adatok és profilok megfelelőségi beállításait használni szeretné. Egyéni Eszközbeállítás létrehozásáról további információk: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett beállítások**.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

5.  Az **Alapértelmezett beállítások** párbeszédpanelen kattintson a **Megfelelőségi beállítások**elemre.  

6.  A **Felhasználói adatok és profilok engedélyezése** legördülő listából válassza az **Igen**lehetőséget.  

7.  Kattintson az **OK** gombra az **Alapértelmezett beállítások** párbeszédpanel bezárásához.  

## <a name="create-a-user-data-and-profiles-configuration-item"></a>A felhasználói adatokat és profilokat tartalmazó konfigurációs elem létrehozása  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **felhasználói adatok és profilok**.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Felhasználói adatok és profilok konfigurációelemeinek létrehozása**elemre.  

4.  A **Felhasználói adatok és profilok konfigurációs elem létrehozása varázsló** **Általános**lapján adja meg a következő információkat:  

    -   **név:** Adjon meg egy egyedi nevet a konfigurációs elem számára. Legfeljebb 256 karakter használható.  

    -   **Leírás:** Adjon meg egy leírást, amely áttekintést ad a konfigurációs elem és olyan releváns információkat, amely segít az azonosításában a Configuration Manager konzolon. Legfeljebb 256 karakter használható.  

    -   **Mappaátirányítás:** Ezt a jelölőnégyzetet, ha a konfigurációs elem mappaátirányítási beállításokat konfigurálni szeretné.  

    -   **Kapcsolat nélküli fájlok:** Ezt a négyzetet, ha a konfigurációs elem offline fájlok beállításait konfigurálni szeretné.  

    -   **A központi felhasználói profilokat:** Ezt a négyzetet, ha a konfigurációs elem központi felhasználói profilok beállításait konfigurálni szeretné.  

5.  A **Felhasználói adatok és profilok konfigurációs elem létrehozása varázsló** **Mappaátirányítás**lapján adja meg, hogyan kell majd a konfigurációelemet fogadó felhasználók ügyfélszámítógépeinek kezelnie a mappaátirányítást. Konfigurálhat beállításokat minden olyan eszközhöz, amelyre a felhasználó bejelentkezik, vagy csak a felhasználó elsődleges eszközeihez. A mappaátirányításról további információt a Windows Server dokumentációjában talál.  

    > [!NOTE]  
    >  Ez a lap csak akkor jelenik meg, ha bejelölte **mappaátirányítás** a a **általános** a varázsló.  

6.  A **Felhasználói adatok és profilok konfigurációs elem létrehozása varázsló** **Kapcsolat nélküli fájlok**lapján engedélyezheti vagy letilthatja a kapcsolat nélküli fájlok használatát a konfigurációelemet fogadó felhasználók számára, és konfigurálhatja a kapcsolat nélküli fájlok viselkedésére vonatkozó beállításokat. Olyan kapcsolat nélküli fájlokat is megadhat, amelyek minden számítógépen elérhetők lesznek, amelyen a felhasználó bejelentkezik. A kapcsolat nélküli fájlokról további információt a Windows Server dokumentációjában talál.  

    > [!NOTE]  
    >  Ez a lap csak akkor jelenik meg, ha bejelölte a lista **kapcsolat nélküli fájlok** a a **általános** a varázsló.  

7.  A **Felhasználói adatok és profilok konfigurációs elem létrehozása varázsló** **Barangoló profilok**lapján konfigurálhatja, hogy a barangoló profilok elérhetők legyenek-e a számítógépeken, amelyeken a felhasználó bejelentkezik, illetve további adatokat adhat meg a profilok viselkedésével kapcsolatban. A barangoló profilokról további információt a Windows Server dokumentációjában talál.  

    > [!NOTE]  
    >  Ez a lap csak akkor jelenik meg, ha bejelölte a lista **központi felhasználói profilok** a a **általános** a varázsló.  

8.  Fejezze be a varázslót.  

 Az új felhasználói adatokat és profilokat tartalmazó konfigurációelem megjelenik a **Felhasználói adatok és profilok** csomópontban az **Eszközök és megfelelőség** munkaterületen.  

## <a name="deploy-a-user-data-and-profiles-configuration-item"></a>A felhasználói adatokat és profilokat tartalmazó konfigurációs elem központi telepítése  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **felhasználói adatok és profilok**.  

3.  Válassza ki a telepíteni kívánt felhasználói adatokat és profilokat tartalmazó konfigurációelemet, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Telepítés**elemre.  

4.  A **Felhasználói adatok és profilok konfigurációs elemének központi telepítése** párbeszédpanelen adja meg a következő információkat:  

    -   **Gyűjtemény** : A **Tallózás** gombra kattintva kiválaszthatja a gyűjteményt, amelyben telepíteni kívánja a konfigurációelemet.  

        > [!IMPORTANT]  
        >  Felhasználói adatokat és profilokat tartalmazó konfigurációelemeket csak felhasználói gyűjteményekben lehet telepíteni.  

    -   **Nem megfelelő szabályok szervizelése (ha támogatott)** : Ha engedélyezi ezt a beállítást, a rendszer automatikusan szervizeli a nem megfelelőként értékelt szabályokat.  

    -   **Szervizelés engedélyezése a karbantartási időszakon kívül** : Ha lett konfigurálva karbantartási időszak ahhoz a gyűjteményhez, amelyikben a konfigurációelemet telepíti, ezt a beállítást engedélyezve lehetővé teheti a megfelelőségi beállítások értékének a karbantartási időszakon kívüli javítását. További információ a karbantartási időszakok: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Riasztás létrehozása** : Ha engedélyezi ezt a beállítást, konfigurálhat egy riasztást, mely akkor jön létre, ha a konfigurációelem megfelelősége a megadott napon és időpontban kisebb, mint a megadott százalék. Azt is megadhatja, hogy kíván-e riasztást küldeni a System Center Operations Manager alkalmazásnak.  

    -   **Adja meg a megfelelőség értékelésének ütemezését a konfigurációelemhez:** Azt az ütemezést adja meg, mely szerint a telepített konfigurációelem kiértékelése történik az ügyfélszámítógépeken. Az ütemezés egyszerű, illetve egyéni is lehet.  

5.  Az **OK** gombra kattintva zárja be a **Felhasználói adatok és profilok konfigurációs elemének központi telepítése** párbeszédpanelt a központi telepítés létrehozásához.  

## <a name="monitor-a-user-data-and-profiles-configuration-item"></a>Felhasználói adatokat és profilokat tartalmazó konfigurációelem figyelése  
 A konfigurációs elem típusát ugyanúgy figyelheti, hogy más megfelelőségi beállításokat figyelheti.  

 További információkért lásd: [megfelelőségi beállítások figyelése](../../compliance/deploy-use/monitor-compliance-settings.md).  

