---
title: "Az ügyfélállapot konfigurálása |} Microsoft Docs"
description: "Válassza ki az ügyfélállapot beállításai a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2275ba2-c83d-43e7-90ed-418963a707fe
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 060d63ab8bce9c3bb39d2db404580b9f59416d33
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-status-in-system-center-configuration-manager"></a>Az ügyfélállapot konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Előtt a System Center Configuration Manager az ügyfélállapot megfigyeléséhez, és javíthatja a talált problémákat, konfigurálnia kell a helyhez az ügyfeleket inaktívként megjelölő ügyfél tevékenységének adott küszöbérték alá esésekor riasztást adó beállításokat használt paraméterek. Meg is tilthatja a számítógépeken az ügyfél által talált problémák automatikus szervizelését.  

##  <a name="BKMK_1"></a>Ügyfélállapot konfigurálása  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, kattintson a **ügyfélállapot**, ezt követően a a **Home** lap a **ügyfélállapot** csoportjában kattintson **ügyfélállapot beállításai**.  

3.  Az a **ügyfél állapotának beállítási tulajdonságai** párbeszédpanelen adja meg a következő értékek megadásával határozza meg az ügyfél tevékenységét:  

    > [!NOTE]  
    >  Ha a beállítások egyike teljesül, az ügyfél inaktívként lesznek megjelölve.  

    -   **Ügyfélházirend kérése a következő napokon:** Adja meg a napok számát, egy ügyfél házirendkérése óta. Az alapértelmezett érték **7** nap.  

    -   **Szívverés felderítés a következő napokon:** Adja meg az ügyfélszámítógép Szívveréses felderítési adatrekordot küldött a hely adatbázisába óta eltelt napok számát. Az alapértelmezett érték **7** nap.  

    -   **Hardverleltározás a következő napokon:** Az azóta eltelt napok számát az ügyfélszámítógép Hardverleltár-adatrekordot küldött a hely adatbázisába. Az alapértelmezett érték **7** nap.  

    -   **Szoftverleltározás a következő napokon:** Az azóta eltelt napok számát az ügyfélszámítógép szoftverleltár-adatrekordot küldött a hely adatbázisába. Az alapértelmezett érték **7** nap.  

    -   **A következő napok állapotüzenetei:** Az azóta eltelt napok számát az ügyfélszámítógép állapotüzenetet küldött a helyadatbázishoz. Az alapértelmezett érték **7** nap.  

4.  Az a **ügyfél állapotának beállítási tulajdonságai** párbeszédpanelen adja meg a következő értékek megadásával határozza meg, mennyi ideig ügyfél állapotára vonatkozó őrződnek meg:  

    -   **Ügyfélállapot előzményeinek megőrzése a következő számú napra:** Adja meg, hogy mennyi ideig az ügyfélállapot előzményeinek a hely adatbázisában marad. Az alapértelmezett érték **31** nap.  

5.  Kattintson a **OK** a tulajdonságok mentéséhez és bezárásához a **ügyfél állapotának beállítási tulajdonságai** párbeszédpanel megnyitásához.  

##  <a name="BKMK_Schedule"></a>Az ügyfélállapothoz tartozó ütemezés beállítása  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A a **figyelés** munkaterületet, kattintson a **ügyfélállapot**, ezt követően a a **Home** lap a **ügyfélállapot** csoportjában kattintson **ügyfélállapot frissítésének ütemezése**.  

3.  Az a **ügyfélállapot frissítésének ütemezése** párbeszédpanelen konfigurálja, hogy milyen időközönként, amellyel ügyfélállapot frissítést, majd kattintson az OK gombra.  

    > [!NOTE]  
    >  Ha megváltoztatja az ügyfél állapotfrissítésének ütemezését, a frissítés nem lépnek érvénybe, amíg a következő ütemezett állapotfrissítése (a korábban konfigurált ütemezés szerint).  

##  <a name="BKMK_2"></a>Az ügyfélállapothoz tartozó riasztások konfigurálása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Kattintson az **Eszközök és megfelelőség** munkaterületen az **Eszközgyűjtemények**elemre.  

3.  Válassza ki az **Eszközgyűjtemények** listában azt a gyűjteményt, amelyre vonatkozóan a riasztásokat konfigurálni szeretné, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

    > [!NOTE]  
    >  Felhasználógyűjteményekre vonatkozóan nem lehet riasztásokat konfigurálni.  

4.  Az a **riasztások** lapján a  *&lt;gyűjtemény neve\>***tulajdonságok** párbeszédpanel, kattintson a **Hozzáadás**.  

    > [!NOTE]  
    >  A **Riasztások** lap csak akkor látható, ha a felhasználóhoz társított biztonsági szerepkör rendelkezik a riasztásokra vonatkozó engedélyekkel.  

5.  Az **Új gyűjteménnyel kapcsolatos riasztások hozzáadása** párbeszédpanelen válassza ki azokat a riasztásokat, amelyeket szeretne létrehozni, amennyiben az ügyfél állapot-küszöbértékei adott érték alá esnek, majd kattintson az **OK**gombra.  

6.  A **Riasztások** lap **Feltételek** listájában válassza ki egyenként az ügyfél állapotriasztásait, majd adja meg a következő információkat.  

    -   **Riasztás neve** – elfogadhatja az alapértelmezett nevet, vagy adjon meg egy új nevet a riasztáshoz.  

    -   **Riasztás súlyossága** – a legördülő listából válassza ki a riasztási szintet fog megjelenni a Configuration Manager konzolon.  

    -   **Riasztás** -adja meg a riasztásra vonatkozó százalékos küszöbérték.  

7.  Kattintson a **OK** bezárásához a  *&lt;gyűjtemény neve\>***tulajdonságok** párbeszédpanel megnyitásához.  

##  <a name="BKMK_3"></a>Számítógépek kizárása az automatikus Szervizelésből  

1.  Nyissa meg a Beállításszerkesztőt, amelynek le szeretné tiltani az automatikus szervizelésből az ügyfélszámítógépen.  

    > [!WARNING]  
    >  Helytelen használata a beállításjegyzék-szerkesztővel, Ön komoly problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem tudja garantálni, hogy a Beállításszerkesztő nem megfelelő használatából eredő problémákat meg tudja oldani. A Beállításszerkesztőt saját kockázatára használhatja.  

2.  Navigáljon a **HKEY_LOCAL_MACHINE\Software\Microsoft\CCM\CcmEval\NotifyOnly**.  

3.  Adja meg a beállításkulcshoz a következő értékek egyikét:  

    -   **Igaz** – az ügyfélszámítógép nem fogja automatikusan szervizelni a talált problémákat. Azonban így is riasztást kap a a **figyelés** munkaterület ügyféllel problémákkal kapcsolatban.  

    -   **Hamis** – az ügyfélszámítógép automatikusan szervizeli a problémák talált, és az értesítést fog kapni a **figyelés** munkaterületen. Ez az alapértelmezett beállítás.  

4.  Zárja be a Beállításszerkesztőt.  

 A ccmsetup ügyfelek is telepíthet **NotifyOnly** az automatikus szervizelésből telepítési tulajdonságot. Az ügyfél-telepítési tulajdonságról kapcsolatos további információkért lásd: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties.md).  

