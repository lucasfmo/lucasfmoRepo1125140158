---
title: "Globális feltételek létrehozása |} Microsoft Docs"
description: "Egy alkalmazás tételének és ügyféleszközökre hogyan adhatja meg a globális feltételek létrehozása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d5f871a-19dc-4bd3-a3ad-4230c7a69f1b
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 85e254f1074e02a52fea6a3cda21a37c332f249e
ms.openlocfilehash: 8a59a1769eec4cd6d78d7686a1d8008e832dd924
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-global-conditions-in-system-center-configuration-manager"></a>Globális feltételek létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben, a globális feltételek szabályok, amelyek üzleti vagy műszaki feltételeket, amelyek segítségével adja meg, hogyan alkalmazás tételének és ügyféleszközökre. A globális feltételek a Központi telepítési típus varázsló **Követelmények** lapján érhetők el.  

> [!NOTE]  
>  Globális feltételek helyén találhassuk helyről szerkesztheti.  

 Az alábbi eljárások segítségével a Configuration Manager globális feltételek létrehozása.  

## <a name="provide-basic-information-about-the-global-condition"></a>A globális feltétel alapvető adatainak megadása  
 A globális feltételek különböző típusúak lehetnek. A globális feltételek különböző típusaihoz különböző beállítások tartoznak. Amikor kiválaszt egy adott globális feltétel típusát, a Configuration Manager, amelyek érvényesek a kiválasztott lehetőségeket mutatja be.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **globális feltételek**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **globális feltétel létrehozása**.  

4.  A **Globális feltétel létrehozása** párbeszédpanelen adja meg a globális feltétel nevét és leírását (utóbbi nem kötelező).  

5.  Az a **eszköztípus** legördülő menüben válassza ki, hogy van-e a globális feltétel a egy **Windows** számítógépet vagy egy **Windows Mobile** eszköz.  

6.  A **Feltétel típusa** legördülő listán válasszon egyet a következő lehetőségek közül:  

    -   **Beállítás** – Ez a beállítás ellenőrzi egy vagy több elem meglétét az ügyféleszközökön. Ellenőrizheti például, hogy a fájl, mappa, vagy beállításkulcs-érték létezik-e egy eszközön.  

    -   **Kifejezés** – Ez a beállítás lehetővé teszi összetett szabályok beállítása ellenőrizze, hogy ha a feltétel teljesül-e az ügyféleszközökön. Ellenőrizheti például, ha a számítógép fizikai memóriája 2 GB és 4 GB közé esik, vagy ha egy mobileszköz használ-e érintésvezérlést.  

## <a name="set-up-rules-for-the-global-condition"></a>A globális feltétel szabályainak beállítása  
 A globális feltétel szabályainak definiálásához az eljárás eltér attól függően, hogy konfigurál egy beállítást vagy kifejezést. A beállítás vagy a globális feltétel kifejezésének létrehozásához használja a megfelelő műveletet.  

### <a name="to-set-up-a-setting-for-the-global-condition"></a>A beállítás a globális feltétel beállítása  

1.  A **Feltétel típusa** legördülő listán válassza a **Beállítás**lehetőséget.  

2.  A **Beállítás típusa** legördülő listán válassza ki azt az elemet, amelyet feltételként kíván használni a követelmények ellenőrzéséhez. A következő beállítástípusok és konfigurációk érhetők el.  

    -   **Active Directory-lekérdezés**  

        -   **LDAP-előtag** – Adjon meg egy érvényes LDAP-előtagot az Active Directory tartományi szolgáltatások lekérdezéséhez, amellyel ellenőrzi az ügyfélszámítógépek megfelelését. A következők bármelyikét használhatja: **LDAP://** vagy **GC://**.  

        -   **Megkülönböztető név (DN)** -adja meg a objektumának megkülönböztető nevét, az Active Directory tartományi szolgáltatásokban, amely ellenőrzi az ügyfélszámítógépek megfelelését.  

        -   **Keresési szűrő** – Adjon meg egy LDAP-szűrőt (nem kötelező), amellyel pontosíthatja az Active Directory tartományi szolgáltatások lekérdezésének eredményét a megfelelés ellenőrzéséhez az ügyfélszámítógépeken.  

        -   **A keresés hatóköre** – Adja meg a keresés hatókörét az Active Directory tartományi szolgáltatásokban:  

            -   **Alap** -csak a megadott objektumot kérdezi le.  

            -   **Egy szint** – Ez a beállítás nem használható a Configuration Manager jelen verziójával.  

            -   **Részfa** -lekérdezi a megadott objektumot és az ahhoz tartozó teljes részfát a könyvtárban.  

        -   **Tulajdonság** – Adja meg az Active Directory tartományi szolgáltatások objektumának azon tulajdonságát, amelyet a megfelelés ellenőrzéséhez kíván használni az ügyfélszámítógépeken.  

        -   **Lekérdezés** -jeleníti meg a értékekből összeállított LDAP-lekérdezést **LDAP-előtag**, **megkülönböztető név (DN)**, **keresési szűrő** Ha meg van adva, és **tulajdonság**. Ezzel a lekérdezéssel hajtható végre a megfelelés ellenőrzése az ügyfélszámítógépeken.  

    -   **Szerelvény**  

        -   **Szerelvény neve** – A keresendő szerelvény objektum neve. A név nem lehet ugyanaz, mint az azonos típusú egyéb szerelvény objektumok, és a névnek szerepelnie kell a globális szerelvény-gyorsítótárban. A szerelvény neve legfeljebb 256 karakter lehet.  

        > [!NOTE]  
        >  A szerelvények olyan kódrészletek, amelyek megoszthatók az alkalmazások között. A .dll vagy .exe kiterjesztésű szerelvényeknek is. A globális szerelvény-gyorsítótár a *%systemroot%\assembly* nevű mappa azokon az ügyfélszámítógépeken, amelyek a megosztott szerelvényeket tárolják.  

    -   **Fájlrendszer**  

        -   **Típus** – a legördülő listából válassza ki, hogy szeretné-e keresni egy **fájl** vagy egy **mappa**.  

        -   **Elérési út** – Adja meg a választott fájl van mappa elérési útját az ügyfélszámítógépeken. Az elérési útban megadhat rendszerszintű környezeti változókat és a *%USERPROFILE%* környezeti változót.  

            > [!NOTE]  
            >  Ha megadja a *%USERPROFILE%* környezeti változót az **Elérési út** vagy a **Fájl- vagy mappanév** mezőben, az alkalmazás minden felhasználói profilban keresni fog az ügyfélszámítógépen. Ez azt eredményezheti, hogy a fájlt vagy a mappát több példányban is megtalálhatja.  

        -   **Fájl- vagy mappanév** – Adja meg a keresendő fájl vagy mappa típusú objektum nevét. A fájl- vagy mappanévben megadhat rendszerszintű környezeti változókat és a *%USERPROFILE%* környezeti változót is. Használhatja a * és? a fájlnév helyettesítő karaktereket.  

            > [!NOTE]  
            >  Ha a fájl- vagy mappanév megadásakor helyettesítő karaktereket használ, előfordulhat, hogy ez nagy mennyiségű találatot fog eredményezni. Emiatt lefoglalhatja az ügyfélszámítógép és a nagy hálózati forgalmat a Configuration Manager eredmények jelentésekor.  

        -   **Az almappákban is** – Akkor válassza ezt a lehetőséget, ha a megadott elérési úthoz tartozó almappákban is szeretne keresni.  

        -   **Ez a fájl vagy mappa egy 64 bites alkalmazáshoz társítva** -válassza ki, hogy a 64 bites rendszerfájlok tárolóhelyén (*% windir %*\system32) a 32 bites rendszerfájlok tárolóhelyén kívül (*% windir %*\syswow64) a Windows 64 bites verzióját futtató Configuration Manager-ügyfelek.  

            > [!NOTE]  
            >  Ha ugyanaz a fájl vagy mappa a 64 bites és a 32 bites rendszerfájl-tárolóhelyen is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel több fájlt fog eredményül adni.  

         A **Fájlrendszer** beállítástípus nem támogatja hálózati megosztásra mutató UNC elérési út megadását az **Elérési út** mezőben.  

    -   **IIS-metabázis**  

        -   **Metabázis elérési útja** – Adja meg az IIS-metabázis érvényes elérési útját.  

        -   **Tulajdonságazonosító** – Adja meg az IIS-metabázis beállítás számtulajdonságát.  

    -   **Beállításkulcs**  

        -   **Hive** – a legördülő listából válassza ki a beállításjegyzék-struktúrát, amelyet meg szeretne keresni.  

        -   **Kulcs** – Adja meg a keresendő beállításkulcsnevet. A használandó formátum a következő: *kulcs\alkulcs*.  

        -   **Ez a beállításkulcs egy 64 bites alkalmazáshoz van társítva** – Megadja, hogy az alkalmazás keressen-e a 64 bites beállításkulcsok között is a 32 bites beállításkulcsokon kívül a Windows 64 bites verzióját futtató ügyfeleken.  

            > [!NOTE]  
            >  Ha ugyanaz a beállításkulcs a beállításjegyzék 64 bites és 32 bites helyén is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel mindkét beállításkulcsot eredményül adja.  

    -   **Beállításazonosító**  

        -   **Struktúra** – A legördülő listából válassza ki azt a beállításjegyzék-struktúrát, amelyben keresni szeretne.  

        -   **Kulcs** – Adja meg a keresendő beállításkulcsnevet. A használandó formátum a következő: *kulcs\alkulcs*.  

        -   **Érték** – Adja meg azt az értéket, amelynek szerepelnie kell a megadott beállításkulcsban.  

        -   **Ez a beállításkulcs egy 64 bites alkalmazáshoz van társítva** – Megadja, hogy az alkalmazás keressen-e a 64 bites beállításkulcsok között is a 32 bites beállításkulcsokon kívül a Windows 64 bites verzióját futtató ügyfeleken.  

            > [!NOTE]  
            >  Ha ugyanaz a beállításkulcs a beállításjegyzék 64 bites és 32 bites helyén is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel mindkét beállításkulcsot eredményül adja.  

    -   **Parancsfájl**  

        -   **Felderítési parancsfájl** – válasszon **Hozzáadás** adja meg, vagy tallózással keresse meg a használandó parancsfájlt. A Windows PowerShell, VBScript vagy JScript parancsfájlokat használhat.  

        -   **Futtassa a parancsfájlokat a bejelentkezett felhasználó hitelesítő adatainak használatával** – Ha engedélyezi ezt a beállítást, a parancsfájl használatával fog futni az ügyfélszámítógépeken a bejelentkezett felhasználó hitelesítő adatait.  

            > [!NOTE]  
            >  Az alkalmazás a parancsfájl által visszaadott értéket fogja használni a globális feltétel megfelelésének ellenőrzéséhez. Például a VBScript használata esetén használhatja a **WScript.Echo eredmény** parancs sikeresen lefut az eredmény változó értékét a globális feltételnek.  
            >   
            >  A parancsfájl több értéket ad eredményül, ha ezek az értékek egy sorba kell lennie, és pontosvesszővel elválasztva. Ha külön-külön sorba kerülnek az értékek, a kiértékelés sikertelen lesz.  

    -   **SQL-lekérdezés**  

        -   **SQL Server-példány** – Válassza ki, hogy az SQL-lekérdezést az alapértelmezett példányon, az összes példányon vagy egy megadott adatbázispéldány-néven kívánja-e futtatni.  

            > [!NOTE]  
            >  A példánynévnek az SQL Server helyi példányára kell hivatkoznia. Ha fürtben részt vevő SQL Server-példányra kíván hivatkozni, használjon parancsfájl-beállítást.  

        -   **Adatbázis** – Adja meg annak a Microsoft SQL Server-adatbázisnak a nevét, amelyre vonatkozóan futtatni szeretné az SQL-lekérdezést.  

        -   **Oszlop** – Adja meg a Transact-SQL-utasítás által visszaadott oszlopnevet, amelyet az alkalmazás a globális feltétel megfelelésének ellenőrzéséhez használ.  

        -   **Transact-SQL-utasítás** – Adja meg a globális feltételhez használandó teljes SQL-lekérdezést. Másik lehetőségként **nyissa meg a** megnyitásához meglévő SQL-lekérdezést.  

    -   **WQL-lekérdezés**  

        -   **Névtér** – Adja meg azt a WMI-névteret, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelését ellenőrizni kell az ügyfélszámítógépeken. Az alapértelmezett érték a következő: Root\cimv2.  

        -   **Osztály** – Adja meg azt a WMI-osztályt, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelését ellenőrizni kell az ügyfélszámítógépeken.  

        -   **Tulajdonság** – Adja meg azt a WMI-tulajdonságot, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelését ellenőrizni kell az ügyfélszámítógépeken.  

        -   **WQL-lekérdezés WHERE kifejezéssel** – A **WQL-lekérdezés WHERE kifejezéssel** lehetőséget használhatja annak a WHERE kifejezésnek a megadására, amely a megadott névtérre, osztályra és tulajdonságra lesz alkalmazva az ügyfélszámítógépeken.  

    -   **XPath-lekérdezés**  

        -   **Elérési út** – Adja meg az ügyfélgépeken tárolt azon XML-fájl elérési útját, amelyet a megfelelőség kiértékeléséhez szeretne használni. A Configuration Manager támogatja az összes windowsos rendszerkörnyezeti változó és a *% USERPROFILE %* felhasználói változó használatát az elérési útban.  

        -   **XML-fájl neve** -adja meg a fájlnevet, amely tartalmazza az ügyfélszámítógépek számára a megfelelőség ellenőrzéséhez használ az XML-lekérdezést.  

        -   **Az almappákban is** – Akkor válassza ezt a lehetőséget, ha a megadott elérési úthoz tartozó almappákban is szeretne keresni.  

        -   **Ez a fájl egy 64 bites alkalmazáshoz társítva** -válassza ki, hogy a 64 bites rendszerfájlok tárolóhelyén (*% windir %*\system32) a 32 bites rendszerfájlok tárolóhelyén kívül (*% windir %*\syswow64) a Windows 64 bites verzióját futtató Configuration Manager-ügyfelek.  

        -   **XPath-lekérdezés** – Adjon meg érvényes teljes XPath-lekérdezést, amelyet az alkalmazás a megfelelés ellenőrzéséhez fog használni az ügyfélszámítógépeken.  

        -   **Névterek** – Megnyitja az **XML-névterek** párbeszédpanelt, amelyen megadhatók az XPath-lekérdezésben használandó névterek és előtagok.  

3.  Az **Adattípus** legördülő listán válassza ki azt a formátumot, amelyet a feltétel az adatok visszaadásához fog használni, mielőtt az alkalmazás felhasználja a követelmények ellenőrzéséhez.  

    > [!NOTE]  
    >  A **adattípus** legördülő listából válassza ki az összes beállítás nem jelenik.  

4.  Állítsa be az alábbi ezzel a beállítással kapcsolatban további részleteket a **beállítástípus** legördülő listából. Az elemek állíthat be a választott beállítástípustól függenek.  

5.  Válasszon **OK** a szabály mentéséhez és bezárásához a **globális feltétel létrehozása** párbeszédpanel megnyitásához.  

### <a name="set-up-an-expression-for-the-global-condition"></a>A globális feltétel kifejezésének beállítása  

1.  A **Feltétel típusa** legördülő listán válassza a **Kifejezés**lehetőséget.  

2.  Válasszon **záradék hozzáadása** megnyitásához a **záradék hozzáadása** párbeszédpanel megnyitásához.  

3.  A **Kategória választása** legördülő listán válassza ki, hogy az adott kifejezés eszközre vagy felhasználóra vonatkozik-e. Az **Egyéni** lehetőség választásával korábban konfigurált globális feltételt is használhat.  

4.  A **Válasszon állapotot** legördülő listán válassza ki azt az állapotot, amelyet annak ellenőrzésére fog használni, hogy a felhasználó vagy az eszköz megfelel-e a szabály követelményeinek. A lista tartalma a választott kategóriától függ.  

5.  A **Szolgáltató választása** legördülő listán válassza ki azt az operátort, amellyel az alkalmazás összehasonlítja a választott feltételt és a megadott értéket annak ellenőrzéséhez, hogy a felhasználó vagy az eszköz megfelel-e a szabály követelményeinek. Az elérhető operátorok a választott feltételtől függenek.  

6.  Az **Érték** mezőben adja meg azokat az értékeket, amelyeket az alkalmazás a választott feltétellel és operátorral együtt annak ellenőrzésére használ, hogy a felhasználó vagy az eszköz megfelel-e a szabály követelményeinek. Az elérhető értékek a választott feltételtől és a választott operátortól függenek.  

7.  Válasszon **OK** gombra a kifejezés mentéséhez és bezárásához a **záradék hozzáadása** párbeszédpanel megnyitásához.  

8.  Ha befejezte a globális feltétel záradékainak megadását, válassza ki a **OK** bezárásához a **globális feltétel létrehozása** párbeszédpanel bezárásához és a globális feltétel mentéséhez.  

