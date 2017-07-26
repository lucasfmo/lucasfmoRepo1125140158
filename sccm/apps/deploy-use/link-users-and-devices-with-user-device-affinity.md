---
title: "Felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat |} Microsoft Docs"
description: "Felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolatot, és automatikusan a felhasználóhoz társított összes eszköz számára az alkalmazások telepítése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b30b0d5-722d-4d4b-9ed7-5a43de315461
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6b1393b2a329bcd017dc961366afb09fa7a77899
ms.openlocfilehash: 4e8e677851ad9ae7d027ab685e842a8ff5e35573
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="link-users-and-devices-with-user-device-affinity-in-system-center-configuration-manager"></a>Felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Felhasználó-eszköz kapcsolat a System Center Configuration Manager (a Configuration Manager) a felhasználó egy vagy több eszköz társítja. Ezzel a kapcsolattal nem szükséges tudni a felhasználók számára az alkalmazás központi telepítéséről a felhasználó eszközeinek nevét. Ahelyett, hogy a felhasználó minden eszközén telepítené az alkalmazást, elég azt központilag telepíteni a felhasználónál. Ezután a felhasználó és eszköz közti kapcsolat automatikusan biztosítja, hogy a rendszer az adott felhasználóhoz társított összes eszközön telepítse az alkalmazást.  

 Meghatározhatja az elsődleges eszközöket, általában azok az eszközök, felhasználók által használt a napi munkavégzéshez alapján. Amikor kapcsolatot hoz létre egy felhasználó és egy eszköz között, az alkalmazások telepítéséhez ettől kezdve további beállítások állnak rendelkezésre. Például ha egy felhasználónak a Microsoft Visio van szüksége, telepítheti azt a felhasználó elsődleges eszközén Windows Installer központi telepítéssel. Azonban az eszközön, amely nem elsődleges eszköz, telepíthet Visio virtuális alkalmazásként. Felhasználó-eszköz kapcsolat előre telepítsen szoftvereket a felhasználók eszközeire, ha a felhasználó nem jelentkezett be, hogy amikor a felhasználó bejelentkezik, az alkalmazás már telepítve és készen áll a futtatásra is használja.  

 A felhasználó-eszköz kapcsolat adatait kezelni kell a számítógépekre vonatkozóan. A Configuration Manager automatikusan kezeli a felhasználó-eszköz kapcsolatokat a beléptetett eszközökhöz.  

## <a name="manually-set-up-user-device-affinity"></a>Felhasználó-eszköz kapcsolat manuális beállítása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **eszközök**.  

3.  A listában jelöljön ki egy eszközt. Ezt követően a **Home** lap a **eszköz** csoportjában válassza **elsődleges felhasználók szerkesztése**.  

4.  Az a **elsődleges felhasználók szerkesztése** párbeszédpanelen keresse meg és válassza ki a kijelölt eszközre vonatkozóan elsődleges felhasználóként hozzáadja a felhasználókat. Válasszon **hozzáadása**.  

    > [!NOTE]  
    > A **elsődleges felhasználók** lista mutatja azokat a felhasználókat, akik már elsődleges felhasználók, az eszközt, és milyen módon minden egyes felhasználó-eszköz kapcsolatok hozzárendelése volt.  

## <a name="set-up-primary-devices-for-a-user"></a>Állítson be egy felhasználóra vonatkozóan elsődleges eszközként  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **felhasználók**.  

3.  A listában válasszon ki egy felhasználót. Ezt követően a **eszköz** lapra, majd **elsődleges eszközök szerkesztése**.  

4.  Az a **elsődleges eszközök szerkesztése** párbeszédpanelen keresse meg és válassza ki az eszközöket, ha szeretne hozzáadni a kijelölt felhasználóra vonatkozóan elsődleges eszközként. Válasszon **hozzáadása**.  

    > [!NOTE]  
    > A **elsődleges eszközök** lista mutatja azokat az eszközöket, amelyek már elsődleges eszközök, ezt a felhasználót, és milyen módon minden egyes felhasználó-eszköz kapcsolatok hozzárendelése lett beállítása.  

## <a name="automatically-create-user-device-affinities-windows-pcs-only"></a>Felhasználó és eszköz közti kapcsolat automatikus létrehozása (csak Windows rendszerű számítógépek esetén)  
 A Configuration Manager adatok a felhasználói jelentkezésekből a Windows eseménynaplójából olvassa be. Felhasználó-eszköz kapcsolatok automatikus létrehozására, be kell kapcsolnia a két kapcsolókról a helyi biztonsági házirend ügyfélszámítógépeken bejelentkezési eseményeket a Windows eseménynaplójában tároló:  

-   **Fiókbejelentkezés naplózása**  
-   **Bejelentkezés naplózása**  

 A Windows csoportházirend segítségével ezeket a beállításokat.  

> [!IMPORTANT]  
> Ha egy hiba hatására a Windows Eseménynapló nagyszámú bejegyzések létrehozásához, előfordulhat, hogy hozható létre új Eseménynapló. Ez akkor fordul elő, ha meglévő bejelentkezési események előfordulhat, hogy már nem lesznek elérhetőek a Configuration Manager.  
>   
> Legyen óvatos, ha bekapcsolja a **Fiókbejelentkezés naplózása** és **bejelentkezési események naplózása** beállítások a Windows XP rendszerben. Alapértelmezés szerint az adatmegőrzési 7 nap, és nagyon valószínű, hogy ezek az események betelik a biztonsági eseménynaplóba. Az általános jogú felhasználók nem fog tudni bejelentkezni, ha az Eseménynapló megtelt. A biztonsági eseménynaplóhoz, ennek megelőzése érdekében állítsa be a házirendet **adatmegőrzési mód** egy érték **események felülírása szükség szerint**. A felhasználó-eszköz kapcsolat, elegendő adatot is be a házirend maximális biztonsági eseménynapló méretének egy ésszerű értéket, mint 5-20 MB.  

### <a name="set-up-the-site-to-automatically-create-user-device-affinities"></a>Állítsa be a webhely felhasználói eszköz kapcsolatok automatikus létrehozására  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások**.  

2.  Az alapértelmezett ügyfélbeállítások módosításához válassza **alapértelmezett ügyfélbeállítások**, majd a a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**. Ügyfél ügynökéhez egyéni beállításokat létrehozásához válassza a **ügyfélbeállítások** csomópont, majd a a **Home** lap a **létrehozása** csoportjában válassza **egyéni ügyfél-Eszközbeállítás létrehozása**.  

    > [!NOTE]  
    > Az alapértelmezett ügyfélbeállítások módosítását a rendszer a hierarchia valamennyi számítógépén telepíti. Ügyfél-beállítások konfigurálásával kapcsolatos további információkért lásd: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md).  

3.  A **felhasználó-eszköz kapcsolat**, állítsa be a következőket:  

    -   **Felhasználó-eszköz kapcsolat küszöbértéke (perc)**. Adjon meg percek száma az eszköz használata előtt a felhasználó-eszköz kapcsolat jön létre.  

    -   **Felhasználó-eszköz kapcsolat küszöbértéke (nap)**. Adjon meg nap, amelyben a használat alapján létrehozott kapcsolat küszöbértékének mérése történik.  

    -   **A felhasználás adataiból felhasználó-eszköz kapcsolat automatikus konfigurálása**. Ahhoz, hogy a hely automatikusan létrehozza a felhasználó – eszköz kapcsolatokat, a legördülő listából, válassza ki a **igaz**. Ha bejelöli **hamis**, jóvá kell hagynia minden felhasználó-eszköz kapcsolat hozzárendelését.  

    > [!TIP]  
    > **Példa:** Ha **felhasználó-eszköz kapcsolat küszöbértéke (perc)** való **60** percet, és állítsa be **felhasználó-eszköz kapcsolat küszöbértéke (nap)** való**5** nap, a felhasználónak kell használnia az eszközt egy 5 napos időszakon át legalább 60 percig felhasználó-eszköz kapcsolat automatikus létrehozásához.  

Az automatikus felhasználó-eszköz kapcsolat létrehozása után a Configuration Manager továbbra is figyeli a felhasználó-eszköz kapcsolat küszöbértékeit. Ha a felhasználó aktivitása az eszközre a beállított küszöbértékek alá csökken, a rendszer eltávolítja a felhasználó-eszköz kapcsolatot. Állítsa be **felhasználó-eszköz kapcsolat küszöbértéke (nap)** értékének legalább **7** napig legyenek az olyan helyzetek, amelyben az automatikusa konfigurált felhasználó-eszköz kapcsolat megszakadt, miközben a felhasználó nincs bejelentkezve, például a hétvégén elkerülése érdekében.  

## <a name="import-user-device-affinities-from-a-file"></a>Felhasználó és eszköz közti kapcsolat importálása fájlból  
 Több kapcsolatot is létrehozhat, importálhatja a részletes több felhasználó-eszköz kapcsolatokat tartalmazó fájl. Az eljárás használatához az érintett eszközöket fel kell deríteni és erőforrásként szerepelniük a Configuration Manager-adatbázisba, vagy az eljárás végrehajtása sikertelen lesz.  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **felhasználók** vagy **eszközök**.  

2.  Az a **Home** lap a **létrehozása** csoportjában válassza **felhasználó-eszköz kapcsolat importálása**.  

3.  Az a felhasználói eszköz kapcsolat importálása varázsló a a **leképezés kiválasztása** lapján állítsa be ezeket az információkat:  

    -   **Fájlnév**. Adjon meg egy vesszővel tagolt (CSV) fájl, amely a felhasználók és eszközök, amelyek között kapcsolatot létrehozni kívánt listája. Ebben a fájlban minden felhasználó / eszköz párnak kell lennie a saját sorában egy vesszővel elválasztott értékeket. Használja a következő formátumot: <*tartomány*> &#92; <*felhasználónév*>, <*eszköz NetBIOS-név*>.  

    -   **Ez a fájl referenciaként használt oszlopfejlécekkel rendelkezik**. A .csv fájl fejléce felül, ha ezt a beállítást, és a fejlécsor a rendszer figyelmen kívül hagyja az importálás során.  

4.  Ha az éppen importált fájl minden egyes sorára kettőnél több elemet tartalmaz, akkor használhatja **oszlop** és **hozzárendelése** adhatja meg, melyik oszlop felel meg a felhasználók és eszközök számára, és figyelmen kívül hagyja az importálás során melyik oszlop.  

5.  Válasszon **tovább**, majd fejezze be a felhasználói eszköz kapcsolat importálása varázsló.  

## <a name="let-users-create-their-own-device-affinities"></a>Segítségével a felhasználók a saját eszköz kapcsolatok létrehozása  
 A következő eljárásokkal állíthatja be a felhasználó a Szoftverközpontban alkalmazás a saját felhasználó-eszköz kapcsolat létrehozásához.  

### <a name="set-up-the-site-to-allow-user-created-user-device-affinity-requests"></a>A hely beállítása a felhasználó által létrehozott felhasználó-eszköz kapcsolatokra vonatkozó kérések engedélyezése  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások**.  

2.  Az alapértelmezett ügyfélbeállítások módosításához válassza **alapértelmezett ügyfélbeállítások**, majd a a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**. Ügyfél ügynökéhez egyéni beállításokat létrehozásához válassza a **ügyfélbeállítások** csomópont, majd a a **Home** lap a **létrehozása** csoportjában válassza **hozzon létre egyedi ügyfélfelhasználó-beállítások**.  

    > [!NOTE]  
    > Az alapértelmezett ügyfélbeállítások módosítását a rendszer a hierarchia valamennyi számítógépén telepíti. Ügyfél-beállítások konfigurálásával kapcsolatos további információkért lásd: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).  

3.  Válassza a **Felhasználó-eszköz kapcsolat** ügyfélbeállítást, majd **A felhasználók definiálhassák elsődleges eszközeiket** legördülő listában válassza az **Igaz**elemet.  

### <a name="set-up-a-user-device-affinity"></a>Felhasználó-eszköz kapcsolat beállítása  

1.  Válassza ki az Alkalmazáskatalógushoz, **saját rendszerek**.  

2.  A beállításnak a **rendszeresen használom ezt a számítógépet a munkámhoz**.  

## <a name="manage-user-device-affinity-requests-from-users"></a>A felhasználóktól származó felhasználó és eszköz közti kapcsolatokra vonatkozó kérések kezelése  
 Ha **A felhasználó-eszköz kapcsolat automatikus konfigurálása a felhasználás adataiból** beállítás értéke **Hamis**, jóvá kell hagynia a felhasználó és eszköz közti kapcsolatra vonatkozó összes hozzárendelést.  

### <a name="approve-or-reject-a-user-device-affinity-request"></a>Hagyja jóvá vagy utasítsa el a felhasználói eszköz közti kapcsolatokra vonatkozó kérés  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség**.  

2.  Az **Eszközök és megfelelőség** munkaterületen válassza ki azt a felhasználó- vagy eszközgyűjteményt, amelyikre vonatkozóan kezelni szeretné a kapcsolatkéréseket.  

3.  Az a **Home** lap a **gyűjtemény** csoportjában válassza **kapcsolatokra vonatkozó kérések kezelése**.  

4.  Az a **felhasználói eszköz affinitási kérések kezelése** párbeszédpanelen jelölje ki a kapcsolatkérést, és válassza a **jóváhagyás** vagy **elutasítása**.  

