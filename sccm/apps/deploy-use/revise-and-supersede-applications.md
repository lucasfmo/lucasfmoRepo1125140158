---
title: "Alkalmazások módosítása és felülírása |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager alkalmazás verzióival működnek, és felül az alkalmazásokat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30170d70-489f-47f7-bebf-9ed0115db26b
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a04ac74df97741f49d7aae7b599bb60d5725a592
ms.openlocfilehash: 28bea9210c9c58dabbb00a995e78cfedd1738291
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="revise-and-supersede-applications-in-system-center-configuration-manager"></a>A System Center Configuration Managerben alkalmazások módosítása és felülírása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben megismerheti a System Center Configuration Manager alkalmazás-verziók használata és egy új verziójával alkalmazások helyettesítéséről.  

##  <a name="application-revisions"></a>Alkalmazásváltozatok  
 Amikor egy alkalmazáson vagy egy alkalmazásban található központi telepítési típuson, a Configuration Manager új változatot hoz létre az alkalmazás. Mindegyik alkalmazásváltozatnál megjelenítheti az előzményeket. Megtekintheti a változatok tulajdonságait, vissza tudja állítani az alkalmazások korábbi változatait, illetve lehetősége van a régi változatok törlésére is.  

### <a name="to-display-an-application-revision-history"></a>Alkalmazások változáselőzményeinek megjelenítése  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**, és válassza ki a kívánt alkalmazásra.  

3.  Az a **Home** lap a **alkalmazás** csoportjában válassza **változat-nyilvántartása** megnyitásához a **alkalmazás változat-nyilvántartása** párbeszédpanel.  

### <a name="to-view-an-application-revision"></a>Alkalmazásváltozat megtekintése  

1.  Az a **alkalmazás változat-nyilvántartása** párbeszédpanelen jelölje ki az alkalmazás megfelelő változatát, és válassza **nézet**.  

2.  A **Tulajdonságok** párbeszédpanelen megvizsgálhatja a kiválasztott alkalmazás tulajdonságait.  

    > [!NOTE]  
    >  A megjelenített alkalmazástulajdonságok csak olvashatóak.  

3.  Zárja be a **Tulajdonságok** párbeszédpanelt.  

### <a name="to-restore-an-application-revision"></a>Alkalmazásváltozat visszaállítása  

1.  Az a **alkalmazás változat-nyilvántartása** párbeszédpanelen jelölje ki az alkalmazás megfelelő változatát, és válassza **visszaállítása**.  

2.  Az a **változat visszaállításának megerősítése** párbeszédpanelen válassza ki **Igen** a kiválasztott alkalmazásváltozat visszaállításához.  

### <a name="to-delete-an-application-revision"></a>Alkalmazásváltozat törlése  

1.  Az a **alkalmazás változat-nyilvántartása** párbeszédpanelen jelölje ki az alkalmazás megfelelő változatát, és válassza **törlése**.  

2.  Az a **Alkalmazásváltozat törlése** párbeszédpanelen válassza ki **Igen**.  

> [!IMPORTANT]  
>  Az aktuális alkalmazásváltozat csak törlése, ha az alkalmazás elavult, és nem rendelkezik.  

##  <a name="application-supersedence"></a>Alkalmazás-helyettesítés  
 A Configuration Manager alkalmazáskezelési lehetővé teszi, hogy frissítheti vagy lecserélheti a meglévő alkalmazások helyettesítési kapcsolat használatával. Amikor egy alkalmazást felülír, megadhatja a felülírt alkalmazás központi telepítési típusát lecseréli, és is döntse el, frissíteni vagy eltávolítani a felülírt alkalmazás előtt a felülírt alkalmazás telepítve van-e egy új központi telepítési típus.  

> [!IMPORTANT]  
>  Amikor a felülírt központi telepítési típus eltávolítását állítja be, a központi telepítés típusa nem írható felül olyan típussal, amelyet egy másik gyűjteménytípuson használtak.  Például egy eszközgyűjteményen végrehajtott központi telepítési típust nem lehet olyan központi telepítési típussal felülírni, amelyet felhasználók gyűjteményén hajtottak végre, ha meg van adva a felülírt központi telepítés eltávolítására vonatkozó beállítás.  

### <a name="decide-whether-to-upgrade-or-replace-an-application"></a>Döntés egy alkalmazás frissítése vagy lecserélése mellett  
 Az alkalmazás tulajdonságainak párbeszédpanelén található **Helyettesítési kapcsolat megadása** párbeszédpanelen adhatja meg, hogy frissíteni vagy cserélni szeretne-e egy adott alkalmazást. A helyettesítés típusa attól függ, hogy bejelöli-e az **Eltávolítás** elemet a párbeszédpanelen:  

-   Ha frissíti a (ilyen azonosítójú alkalmazás), az ugyanazon alkalmazás újabb verziója **nem** ellenőrizze **Eltávolítás**.  

-   Ha egy másik (eltérő alkalmazásazonosítóval rendelkező) alkalmazás használatára szeretne átállni, jelölje be az **Eltávolítás**elemet. El kell távolítania az alkalmazás felülírt verzióját.  

### <a name="supersede-dependent-applications"></a>Függő alkalmazások felülírása  
 Ebben a példában **alkalmazás fő** hivatkozik az alkalmazást központilag telepíteni, a függőségekkel rendelkezik.  

 Létrehozhat olyan helyettesítési kapcsolatot, amely új verzióra frissíti a függő alkalmazást.  

1.  Győződjön meg róla, hogy az eredeti és az új függő alkalmazás a főalkalmazás ugyanazon függőségi csoportjához tartozik.  

2.  Hozzon létre egy olyan helyettesítési kapcsolatot, amely felülírja az eredeti függő alkalmazást az újjal.  

 A főalkalmazás új telepítései során az új függő alkalmazás telepítve van. A főalkalmazás meglévő telepítéseit frissítődik az új függő alkalmazást.  

 A záró eredménye, hogy a főalkalmazás minden telepítése használja-e az új függő alkalmazást.  

### <a name="further-considerations"></a>További szempontok  

-   A függő alkalmazásokhoz több helyettesítési kapcsolatot is meghatározhat. A rendszer a helyettesítési láncban található legmagasabb szintű függő alkalmazást telepíti.  

-   A függő alkalmazásokat telepíteni kell az eszközt, amelyen a főalkalmazás is megtalálható, vagy a függő alkalmazások nem telepíthetők.  

-   Több függőség esetén a főalkalmazás új telepítéseinél a függőségi sorrend határozza meg, hogy a függő alkalmazás melyik verzióját telepíti a rendszer.  

### <a name="to-specify-a-supersedence-relationship"></a>Helyettesítési kapcsolat megadása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**, és válasszon egy másik alkalmazást felülíró alkalmazás.  

3.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok** megnyitni az alkalmazás neve **tulajdonságok** párbeszédpanel.  

4.  Az a **helyettesítési** lapján a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanelen válassza ki **Hozzáadás**.  

5.  A **Helyettesítési kapcsolat megadása** párbeszédpanelen kattintson a **Tallózás**gombra.  

6.  Az a **alkalmazás kiválasztása** párbeszédpanelen válassza ki az alkalmazást felülír, és válassza a kívánt **OK**.  

7.  Az a **helyettesítési kapcsolat megadása** párbeszédpanelen jelölje ki a központi telepítési típust, amely a felváltja a központi telepítési típusának a felülírt alkalmazás.  

    > [!NOTE]  
    >  Alapértelmezés szerint az új központi telepítési típus nem a központi telepítés típusának eltávolítása a felülírt alkalmazás. Ezt a megközelítést gyakran alkalmazzák olyan helyzetekben, amikor egy meglévő alkalmazás frissítését kell elvégezni központi telepítéssel. Válassza az **Eltávolítás** beállítást, ha az új központi telepítési típus telepítése előtt eltávolítja a meglévő központi telepítési típust. Ha úgy dönt, hogy frissít egy alkalmazást, feltétlenül tesztelje előbb laboratóriumi jellegű környezetben.  

8.  Válasszon **OK** bezárásához a **helyettesítési kapcsolat megadása** párbeszédpanel megnyitásához.  

9. Válasszon **OK** bezárásához a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

### <a name="to-display-applications-that-supersede-the-current-application"></a>A jelenlegi alkalmazást felülíró alkalmazások megjelenítése  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár**.  

2.  A a **szoftverkönyvtár** munkaterületet, bontsa ki a **Alkalmazáskezelés**, válassza a **alkalmazások**, és válassza ki a kívánt alkalmazásra.  

3.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok** megnyitásához a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel.  

4.  A a **hivatkozások** lapján a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanelen válassza ki **ezt az alkalmazást felülíró alkalmazások** a a **kapcsolattípus** legördülő listából választhatja ki.  

5.  Tekintse át a listában, alkalmazásokat, amelyek a kijelölt alkalmazást felülíró, és válassza a **OK** bezárásához a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

