---
title: "Feladatok automatizálása feladatütemezések kezelése |} Microsoft Docs"
description: "Létrehozása, szerkesztése, telepítheti, importálja, és azokat kezelheti a System Center Configuration Manager-környezetben feladatütemezéseket exportál."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1f099f1-e9b5-4189-88b3-f53e3b4e4add
caps.latest.revision: 10
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 113fa73bf0bd1b3b8a4754eb1e96549c520d7995
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-task-sequences-to-automate-tasks-in-system-center-configuration-manager"></a>Feladatütemezések kezelése a folyamatok automatizálásához a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezések használatával a automatizálhat lépéseket a System Center Configuration Manager környezetben. Egy lépés telepíthet egy operációsrendszer-lemezképet egy adott célszámítógépre, elkészítheti vagy rögzítheti egy operációs rendszer lemezképét a rendszer telepítési fájljai alapján, illetve rögzítheti vagy visszaállíthatja a felhasználói állapotinformációkat. A Configuration Manager konzol feladatütemezések található **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezést**. A **feladatütemezés** csomópontot és annak az almappáját, replikálódik a Configuration Manager-hierarchiában. A tervezéssel kapcsolatos tudnivalókat lásd: [tervezési megfontolások a feladatok automatizálásához](../plan-design/planning-considerations-for-automating-tasks.md).  

 Feladatütemezések kezeléséhez a következő szakaszok egyikét használhatja.

##  <a name="BKMK_CreateTaskSequence"></a> Feladatütemezések létrehozása  
 A Feladatütemezés létrehozása varázsló segítségével készíthet feladatütemezéseket. Az alábbi típusú feladatütemezések hozhatók létre a varázslóval:  

|Feladatütemezés típusa|További információ|  
|------------------------|----------------------|  
|[Feladatütemezés egy operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md)|Ez a feladatütemezés-típus egy operációs rendszer telepítésének lépéseit hozza létre, valamint lehetőséget biztosít a felhasználói adatok áttelepítésére, szoftverfrissítések hozzáadására és alkalmazások telepítésére.|  
|[Feladatütemezés egy operációs rendszer verziófrissítéséhez](create-a-task-sequence-to-upgrade-an-operating-system.md)|Ez a feladatütemezés-típus egy operációs rendszer verziófrissítésének lépéseit hozza létre, valamint lehetőséget biztosít szoftverfrissítések hozzáadására és alkalmazások telepítésére.|  
|[Feladatütemezés egy operációs rendszer rögzítéséhez](create-a-task-sequence-to-capture-an-operating-system.md)|Ez a feladatütemezés-típus egy operációs rendszer egy referencia-számítógépről való felépítésének és rögzítésének lépéseit hozza létre. A lemezkép rögzítése előtt szoftverfrissítéseket adhat hozzá és alkalmazásokat telepíthet a referencia-számítógépen.|  
|[Felhasználói állapot rögzítéséhez és visszaállításához feladatütemezés](create-a-task-sequence-to-capture-and-restore-user-state.md)|Ez a feladatütemezés biztosítja a lépéseket, melyek egy meglévő feladatütemezéshez adhatók hozzá a felhasználói állapotadatok rögzítése és visszaállítása céljából.|  
|[Virtuális merevlemezek kezelése feladatütemezés](use-a-task-sequence-to-manage-virtual-hard-disks.md)|Ez a feladatütemezés-típus egy virtuális Merevlemezt, beleértve az operációs rendszer és alkalmazások, közzéteheti a System Center Virtual Machine Manager (VMM) a Configuration Manager konzoljáról telepítése létrehozásához szükséges lépéseket tartalmazza.|  
|[Egyéni feladatütemezés](create-a-custom-task-sequence.md)|Ez a feladatütemezés-típus nem ad hozzá lépéseket a feladatütemezéshez. A feladatütemezés létrehozása után Önnek kell szerkesztenie azt és hozzáadni a lépéseket.|  

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>A feladatütemezés sikertelen lesz, ha az előző laphoz való visszatéréshez
A Configuration Manager verziója 1702 verziótól kezdve térhet vissza az előző oldalra a feladatütemezés futtatása, és hiba történik. Ez a kiadás előtt indítsa újra a feladatütemezés, ha hiba történt a kellett. Használhatja például a **előző** gombra a következő esetekben:

- A számítógép Windows PE környezetben indul, amikor a feladat feladatütemezési rendszerindítási párbeszédpanelen megjelenítheti előtt a feladatütemezés érhető el. Ha a Tovább lehetőségre kattintás ebben a forgatókönyvben, a feladatütemezés utolsó lapján, hogy nincsenek nem feladatütemezések üzenetet jeleníti meg. Most, rákattinthat **előző** keresni az elérhető feladatütemezéseket. Ez az eljárás megismétlésével addig, amíg a feladatütemezés nem érhető el.
- Ha a feladatütemezés futtatása, de függő tartalomcsomagokkal még nem állnak rendelkezésre a terjesztési pontokon, a feladatütemezés sikertelen lesz. Most tartalmának terjesztése az hiányzó (Ha ez nem volt terjesztve van még), vagy várjon, amíg a tartalom a terjesztési pontokon elérhetővé válik, és kattintson **előző** szeretné, hogy a feladat feladatütemezési keres újra a tartalmat.

##  <a name="BKMK_ModifyTaskSequence"></a> Feladatütemezés szerkesztése  
 Módosíthatja a feladatütemezést, ha feladatütemezési lépéseket vagy csoportokat szeretne felvenni vagy törölni, vagy meg szeretné változtatni a lépések sorrendjét. A meglévő feladatütemezés módosításához kövesse az alábbi eljárást.  

> [!IMPORTANT]  
>  A Feladatütemezés létrehozása varázslóval létrehozott ütemezésekben a lépés neve a lépéshez tartozó műveletet vagy a lépés típusát jelzi. Például láthatja a lépést, amely a neve "0 lemez particionálása", típus a lépéshez tartozó művelet [lemez formázása és particionálása](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk). Minden feladatütemezési lépés típus szerint van dokumentálva, és nem feltétlenül a szerkesztőben megjelenő lépésnév szerint.  

#### <a name="to-edit-a-task-sequence"></a>Feladatütemezés szerkesztése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezés** listán válassza ki a szerkeszteni kívánt feladatütemezést.  

4.  A **Kezdőlap** **Feladatütemezés** csoportjában kattintson a **Szerkesztés**lehetőségre, és végezze el a megfelelő műveletet az alábbiak közül:  

    -   Feladatütemezési lépés hozzáadásához kattintson a **Hozzáadás**parancsra, válassza ki a lépés típusát, majd kattintson a hozzáadni kívánt feladatütemezési lépésre. Ha például a Parancssor futtatása lépést szeretné hozzáadni, kattintson a **Hozzáadás**parancsra, válassza az **Általános**lehetőséget, majd kattintson a **Parancssor futtatása**elemre.  

         Az eljárás leírását követő táblázatban megtekintheti az összes feladatütemezési lépést és azok típusát.  

    -   Ha egy csoportot szeretne felvenni a feladatütemezésbe, kattintson a **Hozzáadás**parancsra, majd az **Új csoport**lehetőségre. A csoport hozzáadása után felveheti a megfelelő lépéseket a csoportba.  

    -   Ha módosítani szeretné a feladatütemezés lépéseinek és csoportjainak sorrendjét, válassza ki az áthelyezni kívánt lépést vagy csoportot, és használja az **Elem feljebb vitele** vagy az **Elem lejjebb vitele** ikont. Egyszerre csak egy lépést vagy csoportot lehet áthelyezni.  

    -   Ha törölni szeretne egy lépést vagy csoportot, válassza ki a nem kívánt elemet, és kattintson az **Eltávolítás**parancsra  

5.  A változtatások mentéséhez kattintson az **OK** gombra.  

 A rendelkezésre álló feladatütemezési lépések listáját lásd: [feladatütemezési lépéseket](../understand/task-sequence-steps.md).  

## <a name="configure-high-impact-task-sequence-settings"></a>Nagy jelentőségű feladatütemezés beállításainak konfigurálása
A Configuration Manager verziója 1702 verziótól kezdve feladatütemezés állítja be nagy hatású és, hogy a feladatütemezés futtatásakor a felhasználók megkapják az üzenetek testreszabhatók.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>A feladatütemezés állítja be a nagy jelentőségű feladatütemezés
A következő eljárással feladatütemezés állítja be nagy jelentőségű.
> [!NOTE]
> Bizonyos feltételeknek megfelelő feladatütemezési automatikusan nagy jelentőségű típusúként van definiálva. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **felhasználói értesítés** csoportjában válassza **Ez a nagy jelentőségű feladatütemezés**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Magas kockázatú telepítések az egyéni értesítés létrehozása
A következő eljárással hozhat létre egy egyéni értesítés nagy jelentőségű telepítésekhez.
1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **felhasználói értesítés** csoportjában válassza **használja az egyéni szöveg**.
>  [!NOTE]
>  Felhasználói értesítés szövegéhez csak állítható amikor a **Ez a nagy jelentőségű feladatütemezés** van kiválasztva.

4. A következő beállításokat (a 255 karakteres minden szövegmező maximális):

  **Felhasználói értesítés főcím szövegét**: Itt adhatja meg, amely megjeleníti a Szoftverközpont felhasználói értesítés kék színű szövegre. Például az alapértelmezett felhasználói értesítés, ez a szakasz hasonlót "Megerősítése frissíti az operációs rendszer ezen a számítógépen".

  **Felhasználói értesítő üzenet szövege**: Adja meg az egyéni értesítés a szervezet három szövegmezőt van. Összes beviteli mező szükséges, adja hozzá szöveget.
  - 1. szövegmező: Megadja a szöveg, amelyet általában az a felhasználó kapcsolatos utasításokat tartalmazó fő törzsét. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található valami például "az operációs rendszer frissítése időt vesz igénybe, és a számítógép többször is újraindulhat."
  - 2. szövegmező: Megadja a szöveg fő törzs félkövér szövegét. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található valami például "a frissítés az új operációs rendszert telepít, és automatikusan áttelepíti az alkalmazásokat, adatokat és beállításokat."
  - 3. szövegmező: Megadja a félkövérrel a szöveg utolsó sort. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található hasonlót "gombra kattintva megkezdheti. Ellenkező esetben kattintson a Mégse gombra."   

  Tegyük fel, konfigurálja a következő egyéni értesítés tulajdonságai.

    ![Egy feladatütemezés egyéni értesítés](..\media\user-notification.png)

    A következő értesítést fog megjelenni, ha a végfelhasználó nyit meg a telepítést a Szoftverközpontból.

    ![Egy feladatütemezés egyéni értesítés](..\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>A Szoftverközpont tulajdonságainak konfigurálása
A következő eljárással konfigurálhatja a feladatütemezés a szoftverközpontban megjelenített adatokat. Ezek az adatok csak tájékoztatásra szolgálnak.  
1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **általános** lapon, a Szoftverközpont a következő beállítások érhetők el:
  - **Újraindítás szükséges**: Lehetővé teszi, hogy a felhasználó tudja, hogy újraindítás szükséges a telepítés során.
  - **Méret (MB) letöltése**: Itt adható meg, hány mérete (MB) a Szoftverközpontban a feladatütemezéshez.  
  - **Futási idő (percekben) becsült**: Megadja a becsült futási idő percben megadva, ameddig a feladatütemezést a Szoftverközpontban jelenik meg.

##  <a name="BKMK_DistributeTS"></a> Egy feladatütemezés által hivatkozott tartalom terjesztése  
 Mielőtt az ügyfelek tartalomra hivatkozó feladatütemezést futtatnának, el kell végezni a tartalom terjesztését a terjesztési pontokra. A feladatütemezést bármikor kiválaszthatja, és elvégezheti a tartalma terjesztését, hogy új referenciacsomag-listát készítsen a terjesztéshez. Ha frissített tartalommal módosítja a feladatütemezést, újra kell terjesztenie a tartalmat ahhoz, hogy az elérhető legyen az ügyfelek számára. A feladatütemezésben hivatkozott tartalom terjesztéséhez kövesse az alábbi eljárást.  

#### <a name="to-distribute-referenced-content-to-distribution-points"></a>Hivatkozott tartalom terjesztése terjesztési pontokra  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezés** listán jelölje ki a terjeszteni kívánt feladatütemezést.  

4.  A Tartalom terjesztése varázsló elindításához kattintson a **Kezdőlap** **Központi telepítés** csoportjában található **Tartalom terjesztése** elemre.  

5.  Az **Általános** lapon győződjön meg arról, hogy a megfelelő feladatütemezés van kiválasztva a terjesztéshez, majd kattintson a **Tovább**gombra.  

6.  A **Tartalom** lapon ellenőrizze a terjeszteni kívánt tartalmat, például a feladatütemezés által hivatkozott rendszerindító lemezképet, és kattintson a **Tovább**gombra.  

7.  A **Tartalom célhelye** adja meg azokat a gyűjteményeket, illetve azt a terjesztési pontot vagy terjesztésipont-csoportot, amely(ek)re a feladatütemezés tartalmát terjeszteni szeretné, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  Ha a kiválasztott feladatütemezés olyan tartalomra hivatkozik, amely már terjesztve van egy adott terjesztési pontra, akkor a kérdéses terjesztési pontot a varázsló nem jeleníti meg.  

8.  Fejezze be a varázslót.  

 A feladatütemezésben hivatkozott tartalmat előkészítheti. Configuration Manager létrehoz egy tömörített, manuálisan előkészített tartalomfájlt, amely tartalmazza a fájlokat, társított függőségeket és a kiválasztott tartalomhoz kapcsolódó metaadatokkal. A tartalmat ezután manuálisan importálhatja egy helykiszolgálón, másodlagos helyen vagy terjesztési ponton. További információt a tartalomfájlok manuális előkészítéséről tekintse meg a [előkészítheti a tartalmakat](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkprestagea-use-prestaged-content).  

##  <a name="BKMK_DeployTS"></a> Feladatütemezés központi telepítése  
 A következő eljárással feladatütemezés központi telepítését végezheti el gyűjtemény számítógépei számára.  

> [!WARNING]  
>  A magas kockázatú, feladatütemezéssel végzett központi telepítések működése felügyelhető. A magas kockázatú központi telepítés olyan központi telepítés, amely automatikusan történik, és nem várt eredményeket okozhat. Egy **Kötelező** célú, operációs rendszert központilag telepítő feladatütemezés például magas kockázatú központi telepítésnek minősül. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

> [!NOTE]  
>  A feladatütemezés központi telepítésének állapotüzenetei az elsődleges helyeken az Üzenet ablakban láthatók, de a központi adminisztrációs helyeken nem jelennek meg.  

#### <a name="to-deploy-a-task-sequence"></a>Feladatütemezés központi telepítése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezés** listán jelölje ki a központilag telepíteni kívánt feladatütemezést.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.  

    > [!NOTE]  
    >  Ha a **Központi telepítés** lehetőség nem érhető el, akkor a feladatütemezés érvénytelen hivatkozást tartalmaz.  Javítsa ki a hivatkozást, és próbálkozzon újra a feladatütemezés központi telepítésével.  

5.  Az **Általános** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés**: Adja meg a feladatütemezést, amely számára telepíteni kívánja. Alapértelmezés szerint ebben a mezőben a kiválasztott feladatütemezés jelenik meg.  

    -   **Gyűjtemény**: Adja meg a feladatütemezést futtató számítógépeket tartalmazó gyűjteményt.  

         Kerülje az olyan feladatütemezések központi telepítését, amelyek nem megfelelő gyűjteményekbe telepítenek operációs rendszereket, például a **Minden rendszer** gyűjteménybe. Győződjön meg arról, hogy a kijelölt gyűjtemény csak azokat a számítógépeket tartalmazza, amelyeken a feladatütemezést futtatni szeretné.  

        > [!NOTE]  
        >  Magas kockázatú telepítés például az operációs rendszerek központi telepítésekor a **gyűjtemény választása** ablak csak azokat az egyéni gyűjteményeket, amelyek megfelelnek a központi telepítés ellenőrzési beállításai a hely tulajdonságai konfigurált jeleníti meg. A magas kockázatú központi telepítések mindig az egyéni, a felhasználó által létrehozott, valamint a beépített **Ismeretlen számítógépek** gyűjteményre korlátozódnak. Magas kockázatú központi telepítés létrehozásakor nem jelölhet ki olyan beépített gyűjteményeket, mint például a **Minden rendszer**. Törölje a jelet **elrejtése gyűjtemények száma nagyobb, mint a hely minimális méretre vonatkozó konfigurációja** megtekintéséhez az összes olyan egyéni gyűjtemények, amelyek a beállított maximális számnál kevesebb ügyfelet tartalmaznak. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >   
        >  A központi telepítés ellenőrzési beállításai a gyűjtemény aktuális tagságától függenek. A feladatütemezés központi telepítése után a rendszer nem értékeli újra a gyűjteménytagságot a magas kockázatú központi telepítési beállításokra vonatkozóan.  
        >   
        >  Például tételezzük fel, **alapértelmezett méret** 100 és a **maximális mérete** beállításé pedig 1000. Magas kockázatú központi telepítés létrehozásakor a **Gyűjtemény választása** ablak csak azokat a gyűjteményeket jeleníti meg, amelyek 100-nál kevesebb ügyfelet tartalmaznak. Ha törli a **elrejtése gyűjtemények száma nagyobb, mint a hely minimális méretre vonatkozó konfigurációja** beállítás, az ablak megjeleníti az 1000-nél kevesebb ügyfelet tartalmazó gyűjteményeket.  
        >   
        >  Helyszerepkört tartalmazó gyűjtemény kiválasztásakor az alábbiak érvényesek:  
        >   
        >  -   Ha a gyűjtemény helyrendszer-kiszolgálót tartalmaz, és a központi telepítés ellenőrzési beállításai között a helyrendszer-kiszolgálókat tartalmazó gyűjtemények blokkolását adta meg, akkor hiba történik, és nem folytathatja a műveletet.  
        > -   Ha a gyűjtemény helyrendszer-kiszolgálót tartalmaz, és a központi telepítés ellenőrzési beállításai között megadta, hogy a rendszer figyelmeztesse a helyrendszer-kiszolgálókat tartalmazó gyűjteményekre, akkor ha a gyűjtemény meghaladja az alapértelmezett méretértéket, illetve ha a gyűjtemény kiszolgálót tartalmaz, a Szoftver központi telepítése varázsló magas kockázatra vonatkozó figyelmeztetést jelenít meg. Meg kell erősítenie, hogy magas kockázatú központi telepítést kíván létrehozni, és a rendszer létrehoz egy naplózott állapotüzenetet.  

    -   **Megjegyzések (nem kötelező)**: Adja meg a feladatütemezés adott központi telepítését ismertető kiegészítő tudnivalókat.  

6.  A **Központi telepítési beállítások** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Cél**: A legördülő listából válassza ki a következő lehetőségek közül:  

        -   **Rendelkezésre álló**: Ha a felhasználó a feladatütemezést központilag telepíti, a felhasználó a közzétett feladatütemezést az alkalmazáskatalógusban látja, és igény szerint kérheti. Ha a feladatütemezés központi telepítése egy eszköznél történik meg, a felhasználó a Szoftverközpontban látja, és igény szerint telepítheti.  

        -   **Szükséges**: A feladatütemezés központi telepítése automatikusan megtörténik, a beállított ütemezés szerint. A felhasználó azonban nyomon követheti a feladatütemezés központi telepítésének állapotát (amennyiben az állapot nem rejtett), és a Szoftverközpont használatával a határidő előtt telepítheti.  

    -   **Automatikus központi telepítés ütemezése a felhasználói bejelentkezéssel vagy anélkül**: Ez a beállítás nem érhető el, a feladatütemezés központi telepítésekor.  

    -   **Az ébresztési csomagok küldése**: Ha a központi telepítési céllal van megadva **szükséges** és ezt a lehetőséget választja, a ébresztési csomagot küld a számítógépekre felébressze a telepítési határidő lejártakor alvó állapotból a számítógépet a központi telepítés előtt. E lehetőség használatához a számítógépeken és a hálózatokban be kell állítani a hálózati ébresztést.  

    -   **Annak engedélyezése, hogy az ügyfelek mért internetkapcsolatot használjanak a tartalom letöltésére, miután elérkezett a telepítés határideje költségnövekedéssel járhat**: Ha olyan feladatütemezést, amely alkalmazást telepít, de nem telepít operációs rendszert, megadhatja, hogy az ügyfelek a tartalom letöltésére, miután egy telepítési határidőt használata mért internetkapcsolatot. Ha forgalmi díjas internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.  

        > [!NOTE]  
        >  A mért internetkapcsolat használata működhet ugyan az operációs rendszer központi telepítését nem végző feladatütemezéseknél, de nincs támogatva.  

    -   **Rendszergazdai jóváhagyás megkövetelése, ha a felhasználók ezt az alkalmazást kérik**: Ez a beállítás nem érhető el, a feladatütemezés központi telepítésekor.  

    -   **Elérhetővé tétel a következők**: Adja meg, hogy a feladatütemezés a Configuration Manager ügyfelek, az adathordozók vagy a PXE számára elérhető.  

        > [!IMPORTANT]  
        >  Feladatütemezések automatizált központi telepítése esetén használja a **Csak média és PXE (rejtett)** beállítást. Engedélyezze az **Operációs rendszer felügyelet nélküli központi telepítésének engedélyezése** beállítást, és állítsa be az SMSTSPreferredAdvertID változót az adathordozó részeként, hogy a számítógép automatikusan, felhasználói beavatkozás nélkül indítsa el a központi telepítést. További információ a feladatütemezési változók: [feladat beépített változók a feladatütemezésekhez](../understand/task-sequence-built-in-variables.md)  

7.  Az **Ütemezés** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    > [!IMPORTANT]  
    >  A Windows PE-ügyfél PXE- vagy rendszerindító adathordozóról történő indításakor az ügyfél nem értékel ki a telepítési ütemterveket (a kezdési és elévülési időpontokat, valamint határidőket). Csak olyan ügyféltelepítésekben konfiguráljon ütemezéseket, amelyeket a teljes Windows operációs rendszerből indít el. Fontolja meg egyéb módszerek, például karbantartási időszakok alkalmazását azon aktív feladatütemezések szabályozása érdekében, amelyeket a Windows előtelepítési környezetből elindított ügyfelek számára telepít.  

    -   **A központi telepítés elérhetővé válásának ütemezése**: Adja meg, a dátumot és időpontot, amikor a feladatütemezés a célszámítógépen futtatható. Ha bejelöli a **UTC** jelölőnégyzetet, a beállítás hatására a feladatütemezés egyszerre lesz elérhető több célszámítógép számára, nem pedig eltérő időpontokban, a célszámítógépek helyi ideje szerint.  

         Ha a kezdési időpont a megkövetelt időpontnál korábbi, az ügyfél a megadott kezdési időpontban tölti le a feladatütemezést.  

    -   **A központi telepítés lejáratának ütemezése**: Adja meg a dátum és idő, amikor a feladatütemezés érvényessége lejár a célszámítógépen. Ha bejelöli a **UTC** jelölőnégyzetet, a beállítás hatására a feladatütemezés egyszerre jár le több célszámítógépen, nem pedig eltérő időpontokban, a célszámítógépek helyi ideje szerint.  

    -   **A hozzárendelési ütemezés**: Adja meg az előírt feladatütemezés a célszámítógépen való futtatásakor. Több ütemezés is hozzáadható.  

         Megadható az ütemezés indításának dátuma és ideje, futtatási gyakorisága (hetente, havonta vagy egyéni időközönként), valamint az is, hogy a feladatütemezés fusson-e egy esemény (például a számítógépre való bejelentkezés vagy a számítógépről való kijelentkezés) után.  

        > [!NOTE]  
        >  Ha egy előírt feladatütemezéshez a dátum korábbi a kezdési időt és az időpontot, amikor a feladatütemezés elérhető, a Configuration Manager-ügyfél tölti le a feladatütemezést az ütemezett kezdési időpontban, annak ellenére, hogy a feladatütemezés korábbi időpontban érhető.  

    -   **Újrafuttatási viselkedés**: Adja meg a feladatütemezés újrafuttatásának. A következő beállítások közül választhat.  

        -   **Soha ne fusson újra a központilag telepített program**: A feladatütemezés nem fut újra az ügyfélen, ha a feladatütemezés korábban már futott az ügyfélen. A feladatütemezés akkor sem fut újra, ha a futása korábban meghiúsult vagy ha a feladatütemezési fájlok megváltoztak.  

        -   **Mindig fusson újra a program**: A feladatütemezés mindig újra fut az ügyfélen, ha a központi telepítés ütemezve van, még akkor is, ha a feladatütemezés korábban már sikeresen futott. Ez a beállítás különösen akkor hasznos, ha ismétlődő központi telepítéseket használ, amelyekben a feladatütemezés rendszeresen frissül.  

            > [!IMPORTANT]  
            >  Habár ez a beállítás alapértelmezés szerint engedélyezve van, nincs hatása, amíg hozzá nem rendel egy kötelező központi telepítést. Az elérhető központi telepítéseket a felhasználó bármikor újrafuttathatja.  

        -   **Újrafuttatás, ha az előző próbálkozás sikertelen volt**: A feladatütemezés akkor fut újra, ha a központi telepítés ütemezése esetén, ha a feladatütemezés futtatása korábban nem sikerült. Ez a beállítás különösen a kötelező központi telepítések esetén hasznos, mert így automatikusan újrapróbálkoznak a futással a hozzárendelési ütemezés szerint, ha a legutóbbi futtatás sikertelen volt.  

        -   Újrafuttatás, ha az előző próbálkozás sikeres volt: A feladatütemezés akkor fut újra, csak akkor, ha azt már korábban már sikeresen futott az ügyfélen. Ez a beállítás akkor hasznos, ha ismétlődő központi telepítéseket használ, amelyekben a feladatütemezés rendszeresen frissül, és amelyekben minden frissítés egy korábbi frissítés sikeres telepítését igényli.  

        > [!NOTE]  
        >  Mivel a felhasználó újrafuttathatja a feladatütemezés elérhető központi telepítését, mielőtt egy elérhető feladatütemezés központi telepítését elvégzi egy adott termékkörnyezetben, gondosan értékelje ki és tesztelje, mi történik, ha a felhasználó többször is újrafuttatja a feladatütemezést.  

8.  A **Felhasználói élmény** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Engedélyezi, hogy a felhasználó számára a program hozzárendelésektől**: Adja meg, hogy a felhasználó a kötelező feladatütemezés futtatása függetlenül a központi telepítés hozzárendeléseitől.  

    -   **Feladatütemezés előrehaladásának megjelenítése**: Adja meg, hogy a Configuration Manager-ügyfél a feladatütemezés végrehajtását jeleníti meg.  

    -   **Szoftvertelepítés**: Adja meg, hogy a felhasználó számára az ütemezett időpont után telepítse a szoftvert a konfigurált karbantartási időszakon kívül.  

    -   **Rendszer újraindítása (Ha a telepítés befejezéséhez szükséges)**: Adja meg, hogy a felhasználó számára a számítógép újraindítása után a szoftver telepítését egy konfigurált karbantartási időszakon kívül a hozzárendelési időpont után.  

    -   **A feladatütemezés az interneten lévő ügyfél számára való futás engedélyezése**: Adja meg, hogy a feladatütemezés futtatásához olyan internetalapú ügyfélen, amely a Configuration Manager az interneten lévőnek észlel. Ez a beállítás nem használható olyan műveletek esetén, amelyek valamilyen szoftvert, például operációs rendszert telepítenek. Ezt a beállítást csak általános parancsfájlalapú feladatütemezésekhez használja, amelyek a szabványos operációs rendszerben végeznek műveleteket.  

9. A **Riasztások** lapon adja meg a feladatütemezés telepítésére vonatkozó riasztási beállításokat, majd kattintson a **Tovább**gombra.  

10. A **Terjesztési pontok** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   **Telepítési lehetőségek**: Adja meg a következő lehetőségek közül:  

        > [!NOTE]  
        >  Ha az operációs rendszer központi telepítéséhez csoportos küldést használ, a tartalmat igény szerint, vagy a feladatütemezés futtatása előtt kell letölteni a célszámítógépekre.  

        -   Adja meg, hogy az ügyfelek a feladatütemezés igényei szerint töltik le a tartalmat a terjesztési pontról a célszámítógépre.  

        -   Adja meg, hogy az ügyfelek a feladatütemezés futtatása előtt minden tartalmat letöltenek a terjesztési pontról a célszámítógépre. Ez a beállítás nem jelenik meg, ha a feladatütemezést elérhetővé tette PXE és rendszerindítási adathordozók használatával végzett központi telepítésekhez (lásd a **Központi telepítési beállítások** lapot).  

        -   Adja meg, hogy az ügyfelek a terjesztési pontról futtatják a tartalmat. Ez a beállítás csak akkor érhető el, ha a feladatütemezéssel társított összes csomag számára engedélyezve van, hogy csomagmegosztást használjanak a terjesztési ponton. A csomagmegosztás használatát az egyes csomagok **Tulajdonságok** párbeszédpanelének **Adatelérés** lapján engedélyezheti a tartalom számára.  

    -   **Nincs helyi terjesztési pont nem érhető el, használjon távoli terjesztési pontot**: Adja meg, hogy használhatja-e az ügyfelek a feladatütemezés által igényelt tartalom letöltéséhez lassú és megbízhatatlan hálózatokon lévő terjesztési pontokra.  

11. Fejezze be a varázslót.  

##  <a name="BKMK_ExportImport"></a> Feladatütemezések exportálása és importálása  
 A feladatütemezéseket kapcsolódó objektumaikkal együtt és azok nélkül is exportálhatja és importálhatja. Ilyen objektumok például az operációsrendszer-lemezképek, a rendszerindító lemezképek, az ügyfélügynök-csomagok, az illesztőprogram-csomagok, valamint a függőségekkel rendelkező alkalmazások.  

 A feladatütemezések exportálásakor és importálásakor vegye figyelembe a következőket.  

-   A feladatütemezésben tárolt jelszavak exportálására nem kerül sor. Ha jelszavakat tartalmazó feladatütemezést exportál és importál, a jelszavakat az importált feladatütemezés szerkesztésével újra meg kell adnia. Adjon meg jelszavakat [csatlakozás tartományhoz vagy munkacsoporthoz](../understand/task-sequence-steps.md#BKMK_JoinDomainorWorkgroup), [csatlakoztassa a hálózati mappába](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder), és [parancssor futtatása](../understand/task-sequence-steps.md#BKMK_RunCommandLine) műveletek.  

- A feladatütemezés exportálásakor a **Dynanmic változók beállítása** lépésben értékek használatára konfigurált változók exportálják a **titkos érték** beállítást. Ezek a változók értékeit újra meg kell adnia a feladatütemezés importálása után.

-   Bevált gyakorlat, hogy több elsődleges hely esetében a feladatütemezések importálását a központi adminisztrációs helyen végzik.  

 Használja a következő eljárásokat a feladatütemezések exportálásához és importálásához.  

#### <a name="to-export-task-sequences"></a>Feladatütemezések exportálása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezés** listán jelölje ki az exportálni kívánt feladatütemezést. Ha egynél több feladatütemezést választ ki, azok egyetlen exportfájlba kerülnek.  

4.  A **Kezdőlap** lap **Feladatütemezés** csoportjában kattintson az **Exportálás** elemre a Feladatütemezés exportálása varázsló elindításához.  

5.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   A **Fájl** mezőben adja meg az exportfájl helyét és nevét. Ha a fájlnevet közvetlenül írja be, ne hagyja ki a .zip fájlnévkiterjesztést. Ha az exportfájlt tallózással keresi meg, a varázsló automatikusan hozzáadja a fájlnévkiterjesztést.  

    -   Törölje a jelet **Az összes feladatütemezés-függőség exportálása** négyzetből, ha a feladatütemezések függőségeit nem szeretné exportálni. Alapértelmezés szerint a varázsló megkeresi az összes kapcsolódó objektumot, és a feladatütemezéssel együtt exportálja azokat. Idetartoznak az alkalmazások függőségei is.  

    -   Törölje a jelet **A kiválasztott feladatütemezések és függőségek összes tartalmának exportálása** jelölőnégyzetből, ha nem szeretné átmásolni a tartalmat a csomagforrásból az exportálás helyére. Ha ez a jelölőnégyzet be van jelölve, a Feladatütemezés importálása varázsló az importálási útvonalat használja a csomag új forráshelyeként.  

    -   A **Rendszergazdai megjegyzések** mezőben adja meg az exportálandó feladatütemezések leírását.  

6.  Fejezze be a varázslót.  

 A varázsló a következő kimeneti fájlokat hozza létre:  

-   Ha nem exportál tartalmat, akkor egy .zip fájlt.  

-   Ha exportál tartalmat, akkor egy .zip fájlt és egy *export*_files nevű mappát, ahol az *export* az exportált tartalmat magában foglaló .zip fájl neve.  

 Ha tartalmat ad hozzá egy feladatütemezés exportálásakor, ne feledjen másolatot készíteni a .zip fájlról és az *export*_files mapppáról, különben az importálás sikertelen lesz.  

#### <a name="to-import-task-sequences"></a>Feladatütemezések importálása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés importálása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés importálása** elemre.  

4.  Az **Általános** lapon adja meg az exportált .zip fájlt, majd kattintson a **Tovább**gombra.  

5.  A **Fájltartalom** lapon jelölje ki minden egyes importált objektumhoz a kívánt műveletet. Ezen a lapon látható az összes objektum, amely a Configuration Manager importálni fogja.  

    -   Ha az objektum még soha nem volt importálva, válassza az **Új létrehozása**lehetőséget.  

    -   Ha az objektum már volt korábban importálva, válasszon egyet a következő műveletek közül:  

        -   **Ismétlődés figyelmen kívül hagyása** (alapértelmezett): Ez a művelet nem importálja az objektumot. Ehelyett a varázsló összekapcsolja a meglévő objektumot a feladatütemezéssel.  

        -   **Írja felül**: Ez a művelet felülírja a meglévő objektumot az importált objektummal. Alkalmazások esetében egy újabb verzió hozzáadásával frissítheti a meglévő alkalmazást, vagy újat hozhat létre.  

6.  Fejezze be a varázslót.  

 A feladatütemezés importálása után annak szerkesztésével megadhatja az eredeti feladatütemezésben szereplő jelszavakat. Biztonsági okokból a rendszer nem exportálja a jelszavakat.  

##  <a name="BKMK_CreateTSVariables"></a> Feladatütemezési változók létrehozása számítógépekhez és gyűjteményekhez  
 Testre szabott feladatütemezési változókat hozhat létre számítógépekhez és gyűjteményekhez. A számítógépekhez definiált változókat számítógépes feladatütemezési változókként ismerjük. A gyűjteményekhez definiált változókat gyűjteményi feladatütemezési változókként ismerjük. Ütközés esetén a számítógépes változók elsőbbséget élveznek a gyűjteményi változók fölött. Ez azt jelenti, hogy az adott számítógéphez hozzárendelt feladatütemezési változók automatikusan magasabb prioritást kapnak, mint a számítógépet tartalmazó gyűjteményhez hozzárendelt változók.  

 Például ha az SBC gyűjteményhez változót rendelünk hozzá, és az ABC részét képező XYZ számítógéphez ugyanazzal a névvel szintén változót rendelünk, az XYZ számítógéphez hozzárendelt változó magasabb prioritással bír, mnt az ABC gyűjteményhez hozzárendelt változó.  

 Számítógépes és gyűjteményi változók elrejthetők, hogy azok nem láthatók a Configuration Manager konzolon. Ha meg szeretné szüntetni a változók elrejtését, törölje azokat, majd definiálja újra anélkül, hogy kiválasztaná az elrejtésükre vonatkozó opciókat. A **Ne jelenjen meg ez az érték a Configuration Manager konzolon**beállítás megadása esetén a változó értéke nem jelenik meg, de a feladatütemezés a futtatásakor továbbra is használhatja.  

 A számítógépes változókat egy elsődleges helyen vagy egy központi felügyeleti helyen kezelheti. A Configuration Manager nem támogatja a több mint 1000 hozzárendelt változót számítógép számára.  

> [!WARNING]  
>  Ha gyűjteményi változókat használ feladatütemezésekhez, vegye figyelembe a következőket:  
>   
>  -   Mivel a gyűjtemények módosításai mindig replikálásra kerülnek a hierarchiában, a gyűjteményi változók módosítása nem csak az aktuális hely tagjaira, hanem a gyűjtemény összes tagjára érvényes lesz a hierarchiában.  
> -   Ha töröl egy gyűjteményt, ezzel egyúttal a gyűjteményhez beállított feladatütemezési változókat is törli.  

 Az alábbi eljárásokkal hozhat létre feladatütemezési változókat számítógépekhez vagy gyűjteményekhez.  

#### <a name="to-create-task-sequence-variables-for-a-computer"></a>Feladatütemezési változók létrehozása számítógéphez  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a gyűjteményt, amely azt a számítógépet tartalmazza, amelyikhez a változót hozzá szeretné adni.  

3.  Jelölje ki a számítógépet, majd kattintson a **Tulajdonságok**elemre.  

4.  A **Tulajdonságok** párbeszédpanelen kattintson a **Változók** lapra.  

5.  Minden létrehozni kívánt változóhoz kattintson az **új** ikonra a **< új\> változó** párbeszédpanel és adja meg a nevét és a feladatütemezési változó értékét. Törölje a jelet a **ne jelenjen meg ez az érték a Configuration Manager konzol** jelölőnégyzetet, ha el szeretné rejteni a változókat, hogy azok nem láthatók a Configuration Manager konzolon.  

6.  Miután az összes változót hozzáadta a számítógéphez, kattintson az **OK**gombra.  

#### <a name="to-create-task-sequence-variables-for-a-collection"></a>Feladatütemezési változók létrehozása gyűjteményhez  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az **Eszközök és megfelelőség** munkaterületen jelölje ki a gyűjteményt, amelyhez hozzá szeretné adni a változót, majd kattintson a **Tulajdonságok**elemre.  

3.  A **Tulajdonságok** párbeszédpanelen kattintson a **Gyűjteményi áltozók** lapra.  

4.  Minden létrehozni kívánt változóhoz kattintson az **új** ikonra a **< új\> változó** párbeszédpanel és adja meg a nevét és a feladatütemezési változó értékét. Törölje a jelet a **ne jelenjen meg ez az érték a Configuration Manager konzol** jelölőnégyzetet, ha el szeretné rejteni a változókat, hogy azok nem láthatók a Configuration Manager konzolon.  

5.  Szükség esetén adja meg a Configuration Manager a feladatütemezési változók kiértékeléséhez használt prioritást.  

6.  Miután az összes változót hozzáadta a gyűjteményhez, kattintson az **OK**gombra.  

##  <a name="BKMK_AdditionalActionsTS"></a> Feladatütemezések kezeléséhez használható további műveletek  
 A feladatütemezések kezeléséhez további műveletek is rendelkezésre állnak a feladatütemezések kijelölésekor.  

#### <a name="to-select-a-task-sequence-to-manage"></a>Kezelni kívánt feladatütemezés kiválasztása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A **Feladatütemezés** listában jelölje ki a kezelni kívánt feladatütemezést, majd válasszon a rendelkezésre álló lehetőségek közül.  

 A feladatütemezések kezeléséhez használható további műveletekről az alábbi táblázatban tájékozódhat.  

|Művelet|Leírás|  
|------------|-----------------|  
|**Másolás**|Másolatot készít a kijelölt feladatütemezésről. Ez a művelet különösen akkor lehet hasznos, ha új feladatütemezést szeretne létrehozni egy meglévő alapján.<br /><br /> Ha egy feladatütemezésről másolatot készít egy mappában, a másolat az adott mapppában látható, amíg a feladatütemezési csomópontot nem frissíti.  Frissítést követően a másolat a gyökérmappában lesz látható.|  
|**Letiltás**|Letiltja a feladatütemezést, mely nem lesz futtatható számítógépeken. A letiltott feladatütemezések központilag telepíthetők számítógépekre, de a számítógépek nem futtatják a feladatütemezést, amíg az nincs engedélyezve.|  
|**Engedélyezés**|Engedélyezi a feladatütemezést, mely így futtathatóvá válik. Engedélyezés után nincs szükség egy központilag telepített feladatütemezés ismételt központi telepítésére.|  
|**Előkészített tartalom fájljának létrehozása**|Elindítja a Manuálisan előkészített tartalomfájl létrehozása varázslót a feladatütemezés tartalmának manuális előkészítéséhez. A manuálisan előkészített tartalomfájl létrehozásával kapcsolatos további információkért lásd: [előkészítheti a tartalmakat](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkprestagea-use-prestaged-content).|  
|**Áthelyezés**|A kijelölt feladatütemezést áthelyezi másik mappába.|  
|**Adatelérés**|Nyissa meg a kijelölt feladatütemezéshez tartozó **Tulajdonságok** párbeszédpanelt. Ezen a párbeszédpanelen módosíthatja a feladatütemezési objektum viselkedését. Ne feledje ugyanakkor, hogy a feladatütemezés lépéseit ezen a párbeszédpanelen nem módosíthatja.|  

## <a name="next-steps"></a>További lépések
[A vállalati operációs rendszerek központi telepítésének forgatókönyvei](scenarios-to-deploy-enterprise-operating-systems.md)

