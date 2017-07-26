---
title: "A kiszolgálócsoport szolgáltatás |} Microsoft Docs"
description: "A System Center Configuration Manager konzol riasztások és a frissítések és megfelelőségének figyeléséhez állapotok biztosít."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.translationtype: Machine Translation
ms.sourcegitcommit: af5f58dd5fe1f19d7a70cb9516af159c6682d194
ms.openlocfilehash: ae09a02dd5d67113b9a7e2ce146c844efa4caf55
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
>[!IMPORTANT]
>Ez a tulajdonság előzetes verziójú Configuration Manager verziója 1606 és 1610 verzió érhető el. Az előzetes funkciók azért kerülnek be a termékbe, hogy üzemi környezetben is tesztelhessék őket, ugyanakkor nem tekintendők úgy, hogy készen állnak az üzemi működésre. Be kell kapcsolnia ezt a szolgáltatást ahhoz, hogy elérhető legyen. További információk a következő helyen találhatók: [A frissítésekben biztosított előzetes funkciók használata](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).


# <a name="service-a-server-group"></a>Kiszolgálócsoport karbantartása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager verziója 1606 indítása, konfigurálhatja a kiszolgálói csoportbeállításokat gyűjtemény hány, milyen százalékos definiálásához vagy milyen sorrendben a gyűjteményben szereplő számítógépek telepíti a szoftverfrissítéseket. Beállíthatja úgy is központi telepítés előtti és utáni PowerShell-parancsfájlokat egyéni műveletek futtatása.

Amikor telepíti a frissítéseket egy gyűjteményhez, amely rendelkezik beállított kiszolgálói csoportbeállításokat, a Configuration Manager határozza meg, hány a gyűjteményben szereplő számítógépek telepítheti a szoftverfrissítéseket egy adott időpontban, és elérhetővé teszi a fürttelepítési zárolások feloldása azonos számú. Csak azok a számítógépek, amelyek a központi telepítés zárolni elindul a szoftverfrissítés telepítése. Telepítési zárolás nem érhető el, a számítógép lekérdezi a telepítési zárolás, a szoftverfrissítéseket telepíti, és majd telepítési zárolás feloldása, amikor a szoftverfrissítések telepítése sikeresen befejeződött. Ezt követően a telepítési zárolás más számítógépek számára elérhetővé válik. A számítógép nem tud egy központi telepítési zárolás feloldása, ha a gyűjtemény összes kiszolgáló csoport Fürttelepítési zárolások manuálisan is megjelenhetnek.

>[!IMPORTANT]
>A gyűjteményben a számítógépek ugyanahhoz a helyhez kell rendelni.

#### <a name="to-create-a-collection-for-a-server-group"></a>A kiszolgáló csoport gyűjtemény létrehozása  
A beállítások egy eszközgyűjteményt tulajdonságainak vannak konfigurálva. A szolgáltatás egy olyan kiszolgálócsoportot, a gyűjtemény összes tag ugyanazon a helyen kell rendelni. Az alábbi lépések segítségével hozzon létre egy gyűjteményt, és adja meg a csoport beállításait:
1.  [Hozzon létre egy eszközgyűjteményt](../../core/clients/manage/collections/create-collections.md) , amely tartalmazza a számítógép a kiszolgálón.  

2.  Az a **eszközök és megfelelőség** munkaterületet, kattintson a **Eszközgyűjtemények**, kattintson a jobb gombbal a számítógép a kiszolgáló tartalmazó gyűjteményt, és kattintson a **tulajdonságok**.  

3.  Az a **általános** lapon jelölje be **minden eszköz a azonos kiszolgálói csoport részét képező**, és kattintson a **beállítások**.  

4.  Az a **kiszolgálói csoportbeállításokat** csoportjában adja meg a következő beállítások egyikét:  

    -   **Lehetővé teszi a gépek egyszerre frissítendő százalékaként**: Meghatározza, hogy csak bizonyos százalékát ügyfelek egyszerre frissülnek. Ha például a gyűjteményhez tartozik 10 ügyfél, és a gyűjtemény egy időben, 30 %-ügyfelek frissítése csak 3-ügyfelek telepítése szoftverfrissítéseket egy adott időpontban.  

    -   **Lehetővé teszi a gépek egyszerre frissítendő számos**: Meghatározza, hogy csak bizonyos számú ügyfél egyszerre frissülnek.  

    -   **Adja meg a karbantartás során**: Megadja, hogy a gyűjteményben lévő ügyfelek frissített egyszerre csak egy Ön által konfigurált a sorrendben. Egy ügyfél csak szoftverfrissítéseket telepíti, amely azt előre a listán az ügyfél befejezte a szoftverfrissítések telepítése után.  

5.  Adja meg, hogy a központi telepítés előtti (a csomópont kiürítésekor) vagy (a Csomópont fürttevékenységének újraindításakor) telepítés utáni parancsfájl használatára.  

    > [!WARNING]
    > Egyéni parancsfájlok nem Microsoft által aláírt. A feladata a parancsfájl egységének fenntartására szolgáló módszert.

    > [!TIP]  
    > Az alábbiakban példákat is használhatja a központi telepítés előtti tesztelése és a központi telepítés utáni parancsfájlok, amelyek szöveges fájlba írni az aktuális idő:  
    >   
    >  **Központi telepítés előtti**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Telepítés után**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>Szoftverfrissítések központi telepítése a kiszolgáló csoport és a figyelő állapota  
A tipikus telepítési folyamat használatával telepít a kiszolgáló csoport gyűjtési szoftverfrissítéseket. A szoftverfrissítések telepítése után a szoftver központi telepítéséhez a Configuration Manager konzolon figyelheti meg.
1.  [Szoftverfrissítések központi telepítése](manually-deploy-software-updates.md) a kiszolgáló csoport gyűjteményhez.   

2.  [A szoftverfrissítések központi telepítésének](monitor-software-updates.md). A figyelési nézetei frissítések telepítése, a standard mellett a **Várakozás a zárolás** állapot jelenik meg, ha egy ügyfél arra vár, hogy a kapcsolja a szoftverfrissítések telepítéséhez. További információ az UpdatesDeployment.log fájlt tekintheti meg.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>A csoport számítógépeinek telepítési zárolásait  
Ha a számítógép nem egy központi telepítési zárolás feloldására, a gyűjtemény összes kiszolgáló csoport Fürttelepítési zárolások manuálisan is megjelenhetnek. Törölje a jelet zárolásokat, csak akkor, ha a központi telepítés Beragadt gyűjtemény frissítése és a számítógépek vannak, amelyek még nem megfelelő.  
1.  A a **eszközök és megfelelőség** munkaterületet, kattintson a **Eszközgyűjtemények**, és kattintson a gyűjtemény törlése Fürttelepítési zárolások feloldása.  

2.  A a **Home** lap a **telepítési** csoportjában kattintson a **egyértelmű Server csoport telepítési zárolja**. Ha az ügyfelek telepíthetik a szoftverfrissítéseket nem sikerült, és megakadályozzák, más ügyfelek a szoftverfrissítések telepítése után, a fürttelepítési zárolások feloldása manuálisan törölhetők.  

