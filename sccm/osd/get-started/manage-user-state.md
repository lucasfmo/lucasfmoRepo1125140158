---
title: "Felhasználói állapot - Configuration Manager kezelése |} Microsoft Docs"
description: "A System Center Configuration Manager használ a User State Migration Tool rögzítheti és visszaállíthatja a felhasználói állapotadatokat olyan operációsrendszer-telepítési helyzetekben."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8d5c345-1e91-410b-b8a9-0170dcfa846e
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: a0bd86587669c32377b1eafa6a890d37e10ac3f6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-user-state-in-system-center-configuration-manager"></a>A felhasználói állapot kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használhatja a System Center Configuration Manager feladatütemezések rögzítheti és visszaállíthatja a felhasználói állapotadatokat olyan operációsrendszer-telepítési helyzetekben hol szeretné megőrizni az aktuális operációs rendszer felhasználói állapotát. Példa:  

-   Olyan központi telepítések, amelyeknél szeretné rögzíteni egy számítógép felhasználói állapotát, majd egy másik számítógépen vissza kívánja azt állítani.  

-   Frissítéses telepítések, amelyeknél rögzíteni szeretné, majd ugyanazon a számítógépen szeretné visszaállítani a felhasználói állapotot.  

 Configuration Manager használ a felhasználói állapot áttelepítési eszköz (USMT) 10.0 áttelepítésének kezelése az a felhasználói állapot adatainak a forrásszámítógépről a célszámítógépre az operációs rendszer telepítésének befejezése után. A Felhasználóáttelepítő 10.0 esetében gyakran előforduló áttelepítési helyzetekről további információért lásd a  [Common Migration Scenarios](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)(Általános migrálási helyzetek) témakört.  

 A következő szakaszok segítségével rögzítéséhez és visszaállításához a felhasználói adatokat.


##  <a name="BKMK_StoringUserData"></a> Felhasználói állapotadatok tárolása  
 A felhasználói állapot rögzítésekor a felhasználói állapotadatokat a célszámítógépen vagy állapotáttelepítési ponton tárolhatja. A felhasználói állapotot állapotáttelepítési ponton a felhasználói állapot tárolására, a Configuration Manager helyrendszer-kiszolgáló, amelyen az állapotáttelepítési pont hely rendszer üzemel kell használnia. Ha a felhasználói állapotot a célszámítógépen kívánja tárolni, a feladatütemezésben be kell állítania az adatok helyi, hivatkozásokkal történő tárolását.  

> [!NOTE]  
>  A felhasználói állapot helyi tárolására szolgáló hivatkozások az ún. rögzített hivatkozások. Az USMT 10.0 eszközben a rögzített hivatkozások funkciója felhasználói fájlokat és beállításokat keres a számítógépen, majd létrehoz egy könyvtárat a talált fájlokra mutató rögzített hivatkozásoknak. A rögzített hivatkozások ezután a felhasználói adatok helyreállítására használhatók az új operációs rendszer telepítését követően.  

> [!IMPORTANT]  
>  Nem használhat állapotáttelepítési pontot és rögzített hivatkozásokat is egyszerre a felhasználói állapotadatok tárolására.  

 A rögzített felhasználói állapot adatai a következő módszerek egyikével állíthatók vissza:  

-   A felhasználó állapot adatait tárolhatja távoli helyen egy állapotáttelepítési pont konfigurálásával. A **Rögzítés** feladatütemezés elküldi az adatokat az állapotáttelepítési pontra. Az operációs rendszer központi telepítésének végrehajtása után pedig a **Visszaállítás** feladatütemezés lekéri az adatokat, és helyreállítja a felhasználói állapotot a célszámítógépen.  

-   A felhasználó állapot adatait tárolhatja helyben. Ebben az esetben a **Rögzítés** feladatütemezés a célszámítógép megadott helyére másolja a felhasználói adatokat. Az operációs rendszer központi telepítésének végrehajtása után a **Visszaállítás** feladatütemezés erről a helyről kéri le a felhasználói adatokat.  

-   Megadhat rögzített hivatkozásokat, amelyek használatával az eredeti helyükre állíthatja vissza a felhasználói adatokat. Ebben az esetben a felhasználói állapot adatai a meghajtón maradnak a régi operációs rendszer eltávolításakor. Az új operációs rendszer központi telepítésének végrehajtása után a **Visszaállítás** feladatütemezés a rögzített hivatkozások használatával állítja vissza a felhasználói állapot adatait az eredeti helyükre.  

###  <a name="BKMK_UserDataSMP"></a> Felhasználói adatok tárolása állapotáttelepítési ponton  
 Ha a felhasználói állapotadatokat állapotáttelepítési ponton szeretné tárolni, végezze el az alábbi lépéseket:  

1.  [Configure a state migration point](#BKMK_StateMigrationPoint) a felhasználói állapotadatok tárolásához.  

2.  [Create a computer association](#BKMK_ComputerAssociation) a forrás- és a célszámítógép között. A társítást még azelőtt kell létrehoznia, hogy rögzítené a felhasználói állapotot a forrásszámítógépen.  

3.  [Hozzon létre egy feladatütemezést, rögzítheti és visszaállíthatja a felhasználói állapotot a System Center Configuration Managerben](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). Pontosabban hozzá kell adnia az alábbi feladatütemezési lépések rögzíteni egy számítógép felhasználói adatokat, egy állapotáttelepítési ponton tárolja, és a felhasználói adatok visszaállítása számítógépre:  

    -   [Állapot tárolásának igénylése](../understand/task-sequence-steps.md#BKMK_RequestStateStore) a hozzáférés kéréséhez egy számítógép vagy az állapot számítógépre történő visszaállításakor állapot rögzítésekor egy állapotáttelepítési ponthoz.  

    -   [Felhasználói állapot rögzítése](../understand/task-sequence-steps.md#BKMK_CaptureUserState) rögzítéséhez és az állapotáttelepítési ponton a felhasználói állapotadatok tárolására.  

    -   [Felhasználói állapot visszaállítása](../understand/task-sequence-steps.md#BKMK_RestoreUserState) visszaállítása a felhasználói állapotot a célszámítógépen az adatok lekérése a felhasználói állapotot állapotáttelepítési ponton.  

    -   [Állapot tárolásának felszabadítása](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) értesíteni az állapotáttelepítési pontot a rögzítési vagy visszaállítási művelet befejezéséről.  

###  <a name="BKMK_UserDataDestination"></a> Felhasználói adatok helyi tárolása  
 A felhasználói állapotadatok helyi tárolásához a következőket kell tennie:  

-   [Hozzon létre egy feladatütemezést, a felhasználói állapot rögzítéséhez és visszaállításához](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). Egészen pontosan a következő lépéseket kell hozzáadnia a feladatütemezéshez ahhoz, hogy a számítógépről rögzítse, majd egy másik számítógépen rögzített hivatkozások segítségével visszaállítsa a felhasználói adatokat:  

    -   [Felhasználói állapot rögzítése](../understand/task-sequence-steps.md#BKMK_CaptureUserState) rögzítése és tárolása a felhasználói állapotadatokat helyi mappában rögzített hivatkozások segítségével.  

    -   [Felhasználói állapot visszaállítása](../understand/task-sequence-steps.md#BKMK_RestoreUserState) visszaállítása a felhasználói állapotot a célszámítógépen az adatok beolvasása a rögzített hivatkozások használatával.  

        > [!NOTE]  
        >  A rögzített hivatkozások által hivatkozott felhasználói állapotadatok azután is a számítógépen maradnak, miután a feladatütemezés eltávolítja a régi operációs rendszert. Ezek az adatok szolgálnak majd a felhasználói állapot visszaállítására az új operációs rendszer telepítésekor.  

##  <a name="BKMK_StateMigrationPoint"></a> Configure a state migration point  
 Az állapotáttelepítési pont tárolja azokat a felhasználói állapotadatokat, amelyeket az egyik számítógépről megszerzett, másik számítógépen helyreállított. Amikor viszont ugyanarról a számítógépről rögzíti a felhasználó az operációs rendszer központi telepítésével kapcsolatos beállításokat, például amikor frissíti a célszámítógépen az operációs rendszert, választhat, hogy az adatokat ugyanezen a számítógépen tárolja-e rögzített hivatkozások használatával, vagy pedig állapotáttelepítési pontot használ. Az egyes számítógépekre való központi telepítésre az állapottároló létrehozásakor a Configuration Manager automatikusan társítást hoz létre az állapottároló és a célszámítógép között. Az alábbi módszerekkel konfigurálhat állapotáttelepítési pontot a felhasználói állapotadatok tárolására:  

-   A **Helyrendszer-kiszolgáló létrehozása varázslóval** hozzon létre egy új helyrendszer-kiszolgálót az állapotáttelepítési pont számára.  

-   A **Helyrendszer-szerepkörök hozzáadása varázslóval** vegyen fel egy állapotáttelepítési pontot egy meglévő kiszolgálóra.  

 A varázslók az alábbi adatok megadását kérik az állapotáttelepítési ponthoz:  

-   A felhasználói állapotadatok tárolására szolgáló mappákat.  

-   Az ügyfelek maximális számát, amelyek adatokat tárolhatnak az állapotáttelepítési ponton.  

-   A minimális szabad lemezterületet az állapotáttelepítési ponton a felhasználói állapotadatok tárolására.  

-   A szerepkörre vonatkozó törlési házirendet. Beállíthatja, hogy a rendszer azonnal, vagy adott nap elteltével törölje-e a felhasználói állapotadatokat, miután visszaállítja azt egy számítógépen.  

-   Azt, hogy az állapotáttelepítési pont csak a felhasználói állapotadatok visszaállítására irányuló kérelmekre válaszoljon-e. Ha ezt engedélyezi, az állapotáttelepítési pontot nem használhatja felhasználói állapotadatok tárolására.  

 További információ az állapotáttelepítési pont és a konfigurálásához szükséges lépésekről: [állapotáttelepítési pont](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_ComputerAssociation"></a> Create a computer association  
 A számítógép-társítások létrehozásával kapcsolatot definiálhat a forrás- és a célszámítógép között, amikor új hardvereszközre telepít operációs rendszert, és szeretné rögzíteni és visszaállítani a felhasználói adatokat és beállításokat. A forrásoldali számítógépen egy meglévő számítógép, amely a Configuration Manager felügyeli. Amikor az új operációs rendszert a célszámítógépre telepíti, a forrásszámítógép tartalmazza a célszámítógépre áttelepített felhasználói állapotot.  

> [!NOTE]  
>  Az egy alárendelt helyen található számítógépekre a Configuration Manager szülő hely található számítógépek között számítógép-társítás létrehozása nem támogatott. Számítógép-társítások helyspecifikusak, és nem replikálhatók.  

#### <a name="to-create-a-computer-association"></a>Számítógép-hozzárendelés létrehozása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen kattintson a **Felhasználói állapot áttelepítése**elemre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Számítógép-hozzárendelés létrehozása**elemre.  

4.  A **Számítógépek társításának tulajdonságai** párbeszédpanel **Számítógépek társítása** lapján adja meg a rögzítendő felhasználói állapotot tartalmazó forrásszámítógépet, valamint a felhasználói állapotadatok visszaállítására szolgáló célszámítógépet.  

5.  A **Felhasználói fiókok** lapon adja meg a célszámítógépre áttelepíteni kívánt felhasználói fiókokat. Válasszon az alábbi beállítások közül:  

    -   **Összes felhasználói fiók rögzítése és helyreállítása**: Ez a beállítás rögzíti, és helyreállítja a felhasználói fiókokhoz. A beállítással több társítást hozhat létre ugyanahhoz a forrásszámítógéphez.  

    -   **Összes felhasználói fiók rögzítése és megadott fiókok helyreállítása**: Ez a beállítás a forrásoldali számítógép összes felhasználói fiókot rögzíti, és csak a célszámítógép megadott fiókokat állítja. Ezt a beállítást is használhatja akkor is, ha több társítást kíván létrehozni ugyanahhoz a forrásszámítógéphez.  

    -   **Megadott felhasználói fiók rögzítése és helyreállítása**: Ez a beállítás rögzíti, és csak a megadott fiókokat állítja. Ha ezt a beállítást választja, nem hozhat létre több társítást ugyanahhoz a forrásszámítógéphez.  

##  <a name="BKMK_MigrationFails"></a> A felhasználói állapotadatok visszaállítása az operációs rendszer központi telepítésének hibája esetén  
 Ha az operációs rendszer telepítése sikertelen, az USMT 10.0 LoadState funkciójával beolvashatók a telepítési folyamat során rögzített felhasználóiállapot-adatok. Ez érvényes az állapotáttelepítési ponton tárolt vagy célszámítógépre mentett adatokra is. További információ erről az USMT-szolgáltatásról: [LoadState szintaxis](https://technet.microsoft.com/library/mt299188\(v=vs.85\).aspx).  

