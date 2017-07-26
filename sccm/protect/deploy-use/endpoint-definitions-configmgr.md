---
title: "Az Endpoint Protection kártevő-definíciók |} Microsoft Docs"
description: "Ismerkedjen meg a Configuration Manager szoftverfrissítéseinek beállítása a definíciófrissítések ügyfélszámítógépekre."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3b9c4027-a98b-406b-935c-ccabcfe713df
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: ca40c2c745ea516b56b637249b892cd44e570a9d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

#  <a name="using-configuration-manager-software-updates-to-deliver-definition-updates"></a>A Configuration Manager szoftverfrissítéseinek használata a definíciófrissítések

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A definíciófrissítések ügyfélszámítógépekre Configuration Manager szoftverfrissítések konfigurálása Ezt automatikus központi telepítési szabályok konfigurálásával végezheti el. Automatikus központi telepítési szabályok létrehozása előtt győződjön meg arról, hogy konfigurálta-e a Configuration Manager szoftverfrissítések. További információkért lásd: [szoftver bemutatása frissíti a System Center Configuration Managerben](/sccm/sum/understand/software-updates-introduction).

> [!NOTE]
>  Ez a lehetőség csak a kifejezetten konfigurálni kell az Endpoint Protection elemeket. Az automatikus központi telepítési szabály létrehozása varázslóval kapcsolatos további információkért lásd: [szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="to-configure-an-automatic-deployment-rule-to-deliver-definition-updates"></a>Automatikus központi telepítési szabály konfigurálása a definíciófrissítések továbbításához

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson az **Automatikus központi telepítési szabályok**elemre.

3.  A **Kezdőlap** lapon lévő **Létrehozás** csoportban kattintson az **Automatikus központi telepítési szabály létrehozása**elemre.

4.  Az **Automatikus központi telepítési szabály létrehozása varázsló** **Általános**oldalán adja meg a következő információkat:

    -   **Név**: Adjon meg egy egyedi nevet az automatikus központi telepítési szabályhoz.

    -   **Gyűjtemény**: Válassza ki a gyűjteményt, az ügyfélszámítógépek, amelyre át szeretné telepíteni a definíciófrissítéseket.

        > [!NOTE]
        >  Felhasználók gyűjteményére nem lehet definíciófrissítéseket központilag telepíteni.

5.  Kattintson a **Hozzáadás létező szoftverfrissítés-csoporthoz**elemre.

6.  Jelölje be a  **Központi telepítés engedélyezése a szabály futtatása után** jelölőnégyzetet, majd kattintson a **Tovább**gombra.

7.  A varázsló **Központi telepítési beállítások** oldalán a **Részletességi szint** listán válassza ki a **Minimális**elemet, majd kattintson a **Tovább**gombra.

    > [!NOTE]
    >  Az a **részletességi szint** listáról válassza ki **minimális** (szervizcsomag nélküli Configuration Manager) vagy **csak hibaüzenetek** (Configuration Manager). Ez csökkenti a definíciók központi telepítésekor visszaadott állapotüzenetek számát. Ez a konfiguráció segít csökkenteni a Processzor feldolgozásra való használatát a Configuration Manager-kiszolgálókon.

8.  A **Tulajdonságszűrők** listán jelölje be a **Frissítési besorolás** jelölőnégyzetet.

9. Az a **keresési feltételek** listában, kattintson **< keresendő elemek\>**. Ezután a **Keresési feltételek** párbeszédpanelen, az **Adja meg a keresett értéket** listáról válassza ki a **Definíciófrissítések**lehetőséget.

10. Kattintson az **OK** gombra a **Keresési feltételek** párbeszédpanel bezárásához.

11. A **Tulajdonságszűrők** listán jelölje be a **Termék** jelölőnégyzetet.

12. Az a **keresési feltételek** listában, kattintson **< keresendő elemek\>**. Ezt követően a **Keresési feltételek** párbeszédpanelen az **Adja meg a keresendő értéket** listáról válassza ki a **Forefront Endpoint Protection 2010** elemet a Windows 8.1-es és korábbi verziókhoz, vagy a **Windows Defender** elemet a Windows 10-es és újabb verziókhoz.

13. Kattintson az **OK** gombra a **Keresési feltételek** párbeszédpanel bezárásához, majd kattintson a **Tovább**gombra.

14. A **Tulajdonságszűrők** listán jelölje be a **Felváltott** jelölőnégyzetet.

15. Az a **keresési feltételek** listában, kattintson **< keresendő elemek\>**. Ezután a **Keresési feltételek** párbeszédpanelen, az **Adja meg a keresendő értéket** listáról válassza ki a **Nem**lehetőséget.

16. Kattintson az **OK** gombra a **Keresési feltételek** párbeszédpanel bezárásához, majd kattintson a **Tovább**gombra.

17. A varázsló **Értékelési ütemezés** oldalán válassza ki a **Szabály ütemezés szerinti futtatásának engedélyezése**lehetőséget, majd adja meg a definíciófrissítések letöltésének ütemezését. Minimális értékként megadhatja, hogy a szabály a szoftverfrissítési pont minden szinkronizációja után két órával induljon el. Kattintson a **Tovább**gombra.

18. A varázsló **Központi telepítési ütemezés** lapján adja meg a következő beállításokat:

    -   **Idő alapján**: Válassza ki **UTC** Ha azt szeretné, hogy minden ügyfél egyszerre telepítse a legújabb definíciókat a hierarchiában. A tényleges telepítési idő körülbelül két órát vesz igénybe. E beállítás megadása az egyik leginkább javasolt lehetőség.

    -   **Szoftver rendelkezésre állási ideje**: Adja meg a telepítésben Ez a szabály által létrehozott mennyi ideig. Legalább egy órával az automatikus központi telepítési szabály futtatása utáni időpontot adhat meg. Ez segítséget nyújt annak érdekében, hogy elég idő legyen a tartalmat a terjesztési pontokra replikálni a hierarchiában. Néhány definíciófrissítés a kártevőirtó motor frissítéseit is tartalmazhatja, amelyek lehet, hogy hosszabb idő alatt jutnak el a terjesztési pontokra.

    -   **Telepítési határidő**: Válassza ki **minél hamarabb**.

        > [!NOTE]
        >  A szoftverfrissítési határidők kétórás időszakon belül változnak, hogy ne tudjon minden ügyfél egyszerre frissítést kérni.

19. Kattintson a **Tovább**gombra.

20. A varázsló **Felhasználói élmény** lapján válassza a **Felhasználói értesítések** listáról az **Elrejtés a Szoftverközpontban és az összes értesítésben**elemet.   Ez biztosítja, hogy a definíciófrissítések telepítése beavatkozás nélkül fusson. Kattintson a **Tovább**gombra.

21. A varázsló **Riasztások** lapján nem kell beállítania semmilyen riasztást. Az Endpoint Protection a Configuration Manager létrehoz minden riasztást, amelyekre szükség lehet. Kattintson a **Tovább** gombra.

22. A varázsló **Letöltési beállítások** lapján válassza ki a szükséges szoftverfrissítések letöltési viselkedését, és kattintson a **Tovább**gombra.

23. A **Központi telepítési csomag** lapon válasszon egy létező központi telepítési csomagot, vagy hozzon létre egy új központi telepítési csomagot, amely magában foglalja a szabályhoz társított szoftverfrissítési fájlokat.

    > [!NOTE]
    >  Fontolja meg, hogy olyan csomagban helyezi el a definíciófrissítéseket, amely nem tartalmaz más szoftverfrissítést. Ezt a stratégiát követve a definíciófrissítési csomag kisebb lesz, amely lehetővé teszi, hogy gyorsabban replikálódjon a terjesztési pontokra.

24. A varázsló **Terjesztési pontok** lapján válasszon ki egy vagy több terjesztési pontot, amelyre át lesz másolva a csomag tartalma, és kattintson a **Tovább**gombra.

25. A **Letöltési hely** lapon jelölje ki a **Szoftverfrissítések letöltése az internetről**lehetőséget, és kattintson a **Tovább**gombra.

26. A **Nyelv kiválasztása** lapon jelölje ki a letöltendő frissítések nyelvi verzióit, és kattintson a **Tovább**gombra.

27. Végezze el az Automatikus központi telepítési szabály létrehozása varázsló lépéseit.

28. Ellenőrizze, hogy az új szabály megjelenik-e a **automatikus központi telepítési szabályok** csomópont a Configuration Manager konzol.


> [!div class="button"]
[Következő lépés >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Vissza >](endpoint-configure-alerts.md)

