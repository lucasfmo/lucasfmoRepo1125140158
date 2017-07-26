---
title: "Ügyfél által felügyelt Windows rendszerű számítógépek - Configuration Manager konfigurációelemek létrehozása |} Microsoft Docs"
description: "Kezelheti a Windows rendszerű számítógépek és kiszolgálók egyéni Windows asztali számítógépek és kiszolgálók konfigurációs elem beállításait."
ms.custom: na
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1eb2fcaf-acac-4388-9b31-6cccafacaabe
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: e040c6b3a951d1bdf5a46dd82f1bd92b45c2e71d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-system-center-configuration-manager-client"></a>Egyéni konfigurációelemek létrehozása a System Center Configuration Manager-ügyfél használatával felügyelt Windows asztali és kiszolgáló számítógépekhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Manager használata **egyéni Windows asztali számítógépek és kiszolgálók** konfigurációs elem számára a Windows rendszerű számítógépek és kiszolgálók, a Configuration Manager-ügyfél által felügyelt beállításainak kezelését.  

## <a name="start-the-create-configuration-item-wizard"></a>A konfigurációelem létrehozása varázsló elindítása

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Konfigurációelemek**.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  

4.  A **Konfigurációelem létrehozása varázsló** **Általános** lapján adja meg a konfigurációelem nevét, és nem kötelezően leírást is megadhat hozzá.  

5.  A **Határozza meg a létrehozandó konfigurációelem típusát** csoportban válassza a **Windows asztali számítógépek és kiszolgálók (egyéni)** elemet.  

    > [!TIP]  
    >  Ha szeretné megadni az észlelési módszer beállításait, amelyekkel ellenőrizhető az alkalmazás megléte, jelölje be az **Ez a konfigurációelem alkalmazások beállításait tartalmazza** jelölőnégyzetet.  

6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  

## <a name="provide-detection-method-information"></a>Észlelési módszerre vonatkozó adatok megadása  
 Ezzel az eljárással adhatja meg észlelési módszer adatait a konfigurációs elemhez.  

> [!NOTE]  
>  Csak akkor alkalmazható, ha bejelölte az **Ez a konfigurációelem alkalmazások beállításait tartalmazza** jelölőnégyzetet a varázsló **Általános** lapján.  

 A Configuration Manager észlelési módszer annak észleléséhez, hogy telepítve van-e egy alkalmazás egy számítógépen használt szabályokat tartalmaz. Az észlelésre a konfigurációs elem megfelelőségének ellenőrzése előtt kerül sor. Annak észleléséhez, hogy az alkalmazás telepítve van, ellenőrizheti az alkalmazás Windows Installer-fájljának jelenlétét, egyéni parancsfájlt használhat, vagy választhatja a **Mindig feltételezze, hogy az alkalmazás telepítve van** lehetőséget a konfigurációelem megfelelőségének ellenőrzéséhez függetlenül attól, hogy az alkalmazás telepítve van-e.  

 Ezek az eljárások segítségével észlelési módszerek konfigurálása a System Center Configuration Managerben.  

### <a name="to-detect-an-application-installation-by-using-the-windows-installer-file"></a>Egy alkalmazás telepítésének észlelése a Windows Installer-fájl használatával  

1.  A **Konfigurációelem létrehozása varázsló** **Észlelési módszerek** lapján jelölje be az **Észlelés a Windows Installer segítségével** jelölőnégyzetet.  

2.  Kattintson a **Megnyitás** gombra, tallózással keresse meg a Windows Installer (.msi) fájlt, amelyet észlelni szeretne, és kattintson a **Megnyitás** gombra.  

3.  A **Verzió** mezőt a rendszer automatikusan kitölti a kijelölt Windows Installer-fájl verziószámával. Ebben a mezőben egy új verziószámot adhat meg, ha a megjelenített érték nem megfelelő.  

4.  Jelölje be **Az alkalmazás egy vagy több felhasználónál telepítve van** jelölőnégyzetet, ha a számítógép minden felhasználói profiljában szeretné észlelni.  

### <a name="to-detect-a-specific-application-and-deployment-type"></a>Egy adott alkalmazás és központi telepítési típus észlelése  

1.  A **Konfigurációelem létrehozása varázsló** **Észlelési módszerek** lapján jelölje be az **Adott alkalmazás és központi telepítési típus észlelése** jelölőnégyzetet, majd kattintson a **Kiválasztás** gombra.  

2.  Az **Alkalmazás megadása** párbeszédpanelen válassza ki az alkalmazást és egy társított központi telepítési típust, amelyet észlelni szeretne.  

### <a name="to-detect-an-application-installation-by-using-a-custom-script"></a>Egy alkalmazás telepítésének észlelése egyéni parancsfájl használatával  

1.  A **Konfigurációelem létrehozása varázsló** **Észlelési módszerek** lapján jelölje be az **Egyéni parancsfájl használata az alkalmazás észlelésére** jelölőnégyzetet.  

2.  A listában válassza ki a megnyitni kívánt parancsfájl nyelvét. Az alábbi parancsfájlok közül választhat:  

    -   **VBScript**  

    -   **JScript használata**  

    -   **PowerShell**  

3.  Kattintson a **Megnyitás** gombra, tallózással keresse meg a használni kívánt parancsfájlt, és kattintson a **Megnyitás** gombra.  

##  <a name="configure-settings"></a>Beállítások konfigurálása  
 Ezen eljárás használatával adja meg a beállításokat a konfigurációs elemben.  

 A beállítások azon üzleti vagy technikai feltételeket jelentik, amelyek a megfelelőség az ügyféleszközökön való értékeléséhez használ. Megadhat új beállításokat, vagy kereshet a meglévő beállítások között egy referencia-számítógépen.  

1.  A **Konfigurációelem létrehozása varázsló** **Beállítások** lapján kattintson az **Új** gombra.  

2.  A **Beállítás létrehozása** párbeszédpanel **Általános** lapján adja meg a következő adatokat:  

    -   **név:** Adjon meg egy egyedi nevet a beállítás. Legfeljebb 256 karakter használható.  

    -   **Leírás:** Adja meg a jelentés leírását. Legfeljebb 256 karakter használható.  

    -   **Beállítás típusa:** A listában válassza ki, és konfigurálja a beállítás használatához a következő beállítástípusok egyikét:  

        -   **Active Directory-lekérdezés**  

             **LDAP-előtag** – Adjon meg egy érvényes előtagot az Active Directory tartományi szolgáltatások lekérdezéséhez, amellyel ellenőrzi az ügyfélszámítógépek megfelelését. Használhatja az **LDAP: / /**, illetve – ha a globális katalógusban szeretne keresést végrehajtani – a **GC: / /** előtagot.  

             **Megkülönböztető név (DN)** – Adja meg az Active Directory tartományi szolgáltatások azon objektumának megkülönböztető nevét, amelynek megfelelését ellenőrizni kívánja az ügyfélszámítógépen.  

             Ha például szeretné kiértékelni a corp.contoso.com tartományban egy, a John Smith nevű felhasználóhoz kapcsolódó értéket, írja be  a következőt:  

            -   **Keresési szűrő** – Adjon meg egy LDAP-szűrőt (nem kötelező), amellyel pontosíthatja az Active Directory tartományi szolgáltatások lekérdezésének eredményét a megfelelés ellenőrzéséhez az ügyfélszámítógépeken.  

                 A lekérdezés összes eredményének visszaadásához írja be: **(objectclass=\*)**.  

            -   **A keresés hatóköre** – Adja meg a keresés hatókörét az Active Directory tartományi szolgáltatásokban/válasszon a következők közül:  

                -   **Alap** – Csak a megadott objektumot kérdezi le.  

                -   **Egy szint** – Ez a beállítás nem használható a Configuration Manager jelen verziójával.  

                -   **Részfa** – Lekérdezi a megadott objektumot és az ahhoz tartozó teljes részfát a címtárban.  

            -   **Tulajdonság** – Adja meg az Active Directory tartományi szolgáltatások objektumának azon tulajdonságát, amelyet a megfelelés ellenőrzéséhez kíván használni az ügyfélszámítógépeken.  

                 Például, ha le szeretné kérdezni a **badPwdCount** Active Directory-tulajdonságot, amely tárolja, hogy a felhasználó hányszor írt be helytelen jelszót, adja meg a következőt ebben a mezőben: **badPwdCount**.  

            -   **Lekérdezés** – Megjeleníti az **LDAP-előtag**, a **Megkülönböztető név (DN)**, a **Keresési szűrő** (ha meg van adva) és a **Tulajdonság** bejegyzésekből összeállított lekérdezést, amelyet a megfelelés ellenőrzéséhez lehet használni az ügyfélszámítógépeken.  

             Az LDAP-lekérdezések összeállításáról további információt a Windows Server dokumentációjában talál.  

        -   **Szerelvény**  

             Ehhez a beállítástípushoz az alábbi elemeket konfigurálja:  

            -   **Szerelvény neve:** Adja meg a keresendő assembly objektum neve. A név nem egyezhet meg az azonos típusú egyéb Assembly objektumok nevével, és a névnek szerepelnie kell a globális szerelvény-gyorsítótárban. A szerelvény neve legfeljebb 256 karakter hosszúságú lehet.  

             A szerelvények olyan kódrészletek, amelyek megoszthatók az alkalmazások között. A szerelvények fájlkiterjesztése .dll vagy .exe lehet. A globális szerelvény-gyorsítótár a *%systemroot%\Assembly* nevű mappa azokon az ügyfélszámítógépeken, amelyek a közös szerelvényeket tárolják.  

        -   **Fájlrendszer**  

            -   **Típus** – A lista **Fájl** vagy **Mappa** elemének kiválasztásával adja meg a keresni kívánt elemet.  

            -   **Elérési út** – Adja meg a választott fájl van mappa elérési útját az ügyfélszámítógépeken. Az elérési útban megadhat rendszerszintű környezeti változókat és a *%USERPROFILE%* környezeti változót.  

                > [!NOTE]  
                >  Ha használja a *% USERPROFILE %* környezeti változót az **Elérési út** vagy **Fájl- vagy mappanév** mezőben, a keresés az ügyfélszámítógép összes felhasználói profiljában történik, aminek eredményeként a fájl vagy mappa több példánya is szerepelhet a találatok között.  
                >   
                >  Ha a megfelelőségi beállítások nem rendelkeznek hozzáféréssel a megadott elérési úthoz, egy észlelési hiba jön létre. Továbbá ha a keresett fájl jelenleg használatban van, észlelési hiba jön létre.  

            -   **Fájl- vagy mappanév** – Adja meg a keresendő fájl vagy mappa típusú objektum nevét. A fájl- vagy mappnévben megadhat rendszerszintű környezeti változókat és a *%USERPROFILE%* környezeti változót is. Használhatja a * és a ? helyettesítő karaktereket is a fájl nevében.  

                > [!NOTE]  
                >  Ha egy fájl vagy mappa nevét adja meg, és helyettesítő karaktereket használ, ez a kombináció előfordulhat, hogy a nagy mennyiségű találatot eredményez, és lefoglalhatja az ügyfélszámítógép és a nagy hálózati forgalmat eredményezhet, ha a jelentési eredményeket a Configuration Manager.  

            -   **Az almappákban is** – Akkor válassza ezt a lehetőséget, ha a megadott elérési úthoz tartozó almappákban is szeretne keresni.  

            -   **Ez a fájl vagy mappa egy 64 bites alkalmazáshoz van társítva** – Ha engedélyezve van, csak a 64 bites fájlrendszer-helyeket (például *% ProgramFiles %*) ellenőrzi a program 64 bites számítógépeken. Ha ez a beállítás nincs engedélyezve, akkor a 32 bites (például *ProgramFiles(x86) %*) és 64 bites helyeket egyaránt ellenőrzi a program.  

                > [!NOTE]  
                >  Ha ugyanaz a fájl vagy mappa a 64 bites és a 32 bites rendszerfájl-tárolóhelyen is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel több fájlt fog eredményül adni.  

             A **Fájlrendszer** beállítástípus nem támogatja hálózati megosztásra mutató UNC elérési út megadását az **Elérési út** mezőben.  

        -   **IIS-metabázis**  

            -   **Metabázis elérési útja** – Adja meg az Internet Information Services- (IIS-) metabázis érvényes elérési útját.  

            -   **Tulajdonságazonosító** – Adja meg az IIS-metabázis beállítás számtulajdonságát.  

        -   **Beállításkulcs**  

            -   **Struktúra** – A listából válassza ki azt a beállításjegyzék-struktúrát, amelyben keresni szeretne.  

            -   **Kulcs** – Adja meg a keresendő beállításkulcsnevet. Használja a *kulcs\alkulcs* formátumot.  

            -   **Ez a beállításkulcs egy 64 bites alkalmazáshoz van társítva** – Megadja, hogy az alkalmazás keressen-e a 64 bites beállításkulcsok között is a 32 bites beállításkulcsokon kívül a Windows 64 bites verzióját futtató ügyfeleken.  

                > [!NOTE]  
                >  Ha ugyanaz a beállításkulcs a beállításjegyzék 64 bites és 32 bites helyén is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel mindkét beállításkulcsot eredményül adja.  

        -   **Beállításazonosító**  

            -   **Struktúra** – A listából válassza ki azt a beállításjegyzék-struktúrát, amelyben keresni szeretne.  

            -   **Kulcs** – Adja meg a keresendő beállításkulcsnevet. Használja a *kulcs\alkulcs* formátumot.  

            -   **Érték** – Adja meg azt az értéket, amelynek szerepelnie kell a megadott beállításkulcsban.  

            -   **Ez a beállításkulcs egy 64 bites alkalmazáshoz van társítva** – Megadja, hogy az alkalmazás keressen-e a 64 bites beállításkulcsok között is a 32 bites beállításkulcsokon kívül a Windows 64 bites verzióját futtató ügyfeleken.  

                > [!NOTE]  
                >  Ha ugyanaz a beállításkulcs a beállításjegyzék 64 bites és 32 bites helyén is megtalálható ugyanazon a 64 bites számítógépen, a globális feltétel mindkét beállításkulcsot eredményül adja.  

             A **Tallózás** gombra kattintva tallózással is megkeresheti a beállításjegyzékbeli helyet a helyi vagy távoli számítógépen. Távoli számítógép tallózásához rendszergazdai jogosultságokkal kell rendelkeznie az adott távoli számítógépen, és futnia kell rajta a távoli beállításjegyzék szolgáltatásnak.  

        -   **Parancsfájl**  

            -   **Felderítési parancsfájl** – A **Hozzáadás** gombra kattintva adja meg, vagy tallózással keresse meg a használandó parancsfájlt. Windows PowerShell, VBScript vagy Microsoft JScript parancsfájlokat használhat.  

            -   **A parancsfájlokat a bejelentkezett felhasználó hitelesítő adatainak használatával futtassa** – Ha engedélyezi ezt a beállítást, a parancsfájl a bejelentkezett felhasználó hitelesítő adatait használó ügyfélszámítógépeken fut.  

                > [!NOTE]  
                >  Az alkalmazás a parancsfájl által visszaadott értéket használja a globális feltétel megfelelésének ellenőrzéséhez. Például a VBScript használata esetén a **WScript.Echo Result** paranccsal adhatja át az *Eredmény* változó értékét a globális feltételnek.  

        -   **SQL-lekérdezés**  

            -   **SQL Server-példány** – Válassza ki, hogy az SQL-lekérdezést az alapértelmezett példányon, az összes példányon vagy egy megadott adatbázispéldány-néven kívánja-e futtatni.  

                > [!NOTE]  
                >  A példánynévnek az SQL Server helyi példányára kell hivatkoznia. Ha fürtben részt vevő SQL Server-példányra kíván hivatkozni, használjon parancsfájl-beállítást.  

            -   **Adatbázis** – Adja meg annak a Microsoft SQL Server-adatbázisnak a nevét, amelyre vonatkozóan futtatni szeretné az SQL-lekérdezést.  

            -   **Oszlop** – Adja meg a Transact-SQL-utasítás által visszaadott oszlopnevet, amelyet az alkalmazás a globális feltétel megfelelésének ellenőrzéséhez használ.  

            -   **Transact-SQL-utasítás** – Adja meg a globális feltételhez használandó teljes SQL-lekérdezést. A **Megnyitás** gombra kattintva meglévő SQL-lekérdezést is megnyithat.  

                > [!IMPORTANT]  
                >  Az SQL-lekérdezés beállításai nem támogatják az adatbázist módosító SQL-parancsokat. Az SQL-parancsokat csak az adatoknak az adatbázisból való beolvasására használhatja.  

        -   **WQL-lekérdezés**  

            -   **Névtér** – Adja meg azt a Windows Management Instrumentation- (WMI-) névteret, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelőségét ellenőrizni kell az ügyfélszámítógépeken. Az alapértelmezett érték a következő: Root\cimv2.  

            -   **Osztály** – Adja meg azt a WMI-osztályt, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelőségét ellenőrizni kell az ügyfélszámítógépeken.  

            -   **Tulajdonság** – Adja meg azt a WMI-tulajdonságot, amelyet azon WQL-lekérdezés összeállításához kell használni, amelynek megfelelőségét ellenőrizni kell az ügyfélszámítógépeken.  

            -   **WQL-lekérdezés WHERE kifejezéssel** – A **WQL-lekérdezés WHERE kifejezéssel** lehetőséget használhatja annak a WHERE kifejezésnek a megadására, amely a megadott névtérre, osztályra és tulajdonságra lesz alkalmazva az ügyfélszámítógépeken.  

        -   **XPath-lekérdezés**  

            -   **Elérési út** – Adja meg az ügyfélszámítógépeken tárolt, a megfelelőség kiértékeléséhez használt .xml-fájl elérési útját. A Configuration Manager támogatja az összes windowsos rendszerkörnyezeti változó és a *% USERPROFILE %* felhasználói változó használatát az elérési útban.  

            -   **XML-fájl neve** – Adja meg annak a fájlnak a nevét, amely azt az XML-lekérdezést tartalmazza, amelyet a megfelelőség ellenőrzéséhez használ az ügyfélszámítógépeken.  

            -   **Az almappákban is** – Akkor válassza ezt a lehetőséget, ha a megadott elérési úthoz tartozó almappákban is szeretne keresni.  

            -   **Ez a fájl egy 64 bites alkalmazáshoz társítva** -válassza ki, hogy a 64 bites rendszerfájlok tárolóhelyén (*% windir %*\System32) kívül a 32 bites rendszerfájlok tárolóhelyén (*% windir %*\Syswow64) a Configuration Manager-ügyfelek, amelyek a Windows 64 bites verzióját futtatja.  

            -   **XPath-lekérdezés** – Adjon meg érvényes teljes XPath-lekérdezést, amelyet a megfelelőség ellenőrzéséhez használ az ügyfélszámítógépeken.  

            -   **Névterek** – Megnyitja az **XML-névterek** párbeszédpanelt, amelyen megadhatók az XPath-lekérdezésben használandó névterek és előtagok.  

             Ha titkosított .xml-fájl észlelését kísérli meg, a megfelelőségi beállítások megtalálják a fájlt, de az XPath-lekérdezés nem ad vissza találatot, és nem jön létre hiba.  

             Ha az XPath-lekérdezés nem érvényes, a beállítás az ügyfélszámítógépeken nem kompatibilisként lesz kiértékelve.  

    -   **Adattípus:** A listában adja meg, amelyben a feltétel visszaadja az adatokat a beállítás kiértékeléséhez használata előtt formátumát. Az **Adattípus** lista a beállítástípustól függően érhető el.  

        > [!NOTE]  
        >  A **Lebegőpontos szám** adattípus csak 3 tizedesjegyet támogat.  

3.  Konfigurálja a beállítás további részleteit a **Beállítás típusa** listában. A konfigurálható elemek a választott beállítástípustól függenek.  

    > [!NOTE]  
    >  **Fájlrendszer**, **Beállításkulcs** és **Beállításazonosító** típusú beállítások létrehozásakor a **Tallózás** gombra kattintva a referencia-számítógépen található értékek alapján konfigurálhatja a beállítást. Ahhoz, hogy egy távoli számítógépen beállításkulcsokat vagy beállításazonosítókat kereshessen, az adott távoli számítógépen engedélyezve kell lennie a távoli beállításjegyzék szolgáltatásnak.  

4.  Kattintson az **OK** gombra a beállítás mentéséhez és a **Beállítás létrehozása** párbeszédpanel bezárásához.  

##  <a name="configure-compliance-rules"></a>Megfelelőségi szabályok konfigurálása  
 A konfigurációs elemek megfelelőségi szabályait a következő eljárással konfigurálhatja.  

 A megfelelőségi szabályok megadják azon feltételeket, amelyek a konfigurációelemek megfelelőségét definiálják. A beállítások megfelelőségi kiértékelése előtt rendelkezniük kell legalább egy megfelelőségi szabállyal. A WMI-, a beállításjegyzék- és a parancsfájl-beállítások lehetővé teszik a nem megfelelőnek bizonyult értékek javítását. Létrehozhat új szabályokat, vagy tallózással megkereshet meglévő beállításokat bármelyik konfigurációs elemben a benne található szabályok kijelöléséhez.  

### <a name="to-create-a-compliance-rule"></a>Megfelelőségi szabály létrehozása  

1.  A **Konfigurációelem létrehozása varázsló** **Megfelelőségi szabályok** lapján kattintson az **Új** gombra.  

2.  A **Szabály létrehozása** párbeszédpanelen adja meg az alábbi adatokat:  

    -   **név:** Adja meg a megfelelőségi szabály nevét.  

    -   **Leírás:** Adja meg a megfelelőségi szabály leírását.  

    -   **Kiválasztott beállítás:** Kattintson a **Tallózás** megnyitásához a **beállítás kiválasztása** párbeszédpanel megnyitásához. Válassza a beállítást, amelyhez szabályt szeretne definiálni, vagy kattintson az **Új beállítás** elemre. Amikor végzett, kattintson a **Kijelölés** gombra.  

        > [!NOTE]  
        >  A **Tulajdonságok** elemre kattintva megnézheti az aktuálisan kijelölt elemre vonatkozó információkat.  

    -   **Szabály típusa:** Válassza ki a megfelelőségi szabályt, amely a használni kívánt típusát:  

        -   **Érték:** Olyan szabályt hoz létre, amely a konfigurációelem által visszaadott értéket összehasonlítja egy Ön által megadott értékkel.  

        -   **Meglétet vizsgáló:** Olyan szabályt hoz létre, amely kiértékeli a szabályt attól függően, hogy megtalálható-e egy eszközön, illetve hogy hányszor található meg.  

    -   Az **Érték** szabálytípus esetén adja meg az alábbi adatokat:  

        -   **A beállításnak meg kell felelnie a következő szabálynak** – Jelöljön ki egy operátort és egy értéket, amelyet megfelelőség szempontjában a kijelölt beállítással ellenőrizni kell. Az alábbi operátorok használhatók:  

            |Művelet|További információ|  
            |--------------|----------------------|  
            |Egyenlő|Nem áll rendelkezésre további információ|  
            |Nem egyenlő|Nem áll rendelkezésre további információ|  
            |Nagyobb, mint|Nem áll rendelkezésre további információ|  
            |Kisebb, mint|Nem áll rendelkezésre további információ|  
            |Két érték között|Nem áll rendelkezésre további információ|  
            |Nagyobb, vagy egyenlő|Nem áll rendelkezésre további információ|  
            |Kisebb, vagy egyenlő|Nem áll rendelkezésre további információ|  
            |Az egyik|A szövegmezőben egy bejegyzést adjon meg soronként.|  
            |Egyik sem|A szövegmezőben egy bejegyzést adjon meg soronként.|  

        -   **Nem megfelelő szabályok szervizelése (ha támogatott)** – Jelölje be ezt a jelölőnégyzetet, ha azt szeretné, hogy a Configuration Manager automatikusan javítsa a nem megfelelő szabályokat. A Configuration Manager automatikusan javítani tudja a következő szabálytípusokat:  

            -   **Beállításazonosító** – Javítja az értéket, ha az nem megfelelő, és létrehozza, ha nem létezik.  

            -   **Parancsfájl** (automatikus szervizelési parancsfájl futtatásával).  

            -   **WQL-lekérdezés**  

            > [!IMPORTANT]  
            >  Csak akkor javíthatja a nem megfelelő szabályokat, ha a szabály operátor **Egyenlő**.  

        -   **Nem megfelelőségi jelentést ad, ha a beállításpéldány nem található** – Ha ez a beállítás nem található az ügyfélszámítógépeken, a konfigurációelem meg nem felelést jelent.  

        -   **Meg nem felelés súlyossága jelentésekhez:** Adja meg (a Configuration Manager-jelentések) Ha a megfelelőségi szabályt nem jelentett súlyossági szint. A választható súlyossági szintek az alábbiak:  

            -   **Nincs** a megfelelőségi szabályt nem teljesítő számítógépek nem adják meg a hiba súlyosságát.  

            -   **Információ** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **információk**.  

            -   **Figyelmeztetés** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **figyelmeztetés**.  

            -   **Kritikus** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus**.  

            -   **Kritikus eseménnyel** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus**. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  

        -   A **Meglétet vizsgáló** szabálytípus esetén adja meg az alábbi adatokat:  

            > [!NOTE]  
            >  A beállítások attól a beállítástípustól függően változhatnak, amelyhez szabályt ad meg.  

            -   **A beállításának léteznie kell az ügyféleszközökön**  

            -   **A beállítás nem szerepelhet az ügyféleszközökön**  

            -   **A beállítás a következő számú alkalommal fordul elő:**  

        -   **Meg nem felelés súlyossága jelentésekhez:** Adja meg (a Configuration Manager-jelentések) Ha a megfelelőségi szabályt nem jelentett súlyossági szint. A választható súlyossági szintek az alábbiak:  

            -   **Nincs** a megfelelőségi szabályt nem teljesítő számítógépek nem adják meg a hiba súlyosságát.  

            -   **Információ** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **információk**.  

            -   **Figyelmeztetés** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **figyelmeztetés**.  

            -   **Kritikus** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus**.  

            -   **Kritikus eseménnyel** a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus**. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  

3.  Az **OK** gombra kattintva zárja be a **Szabály létrehozása** párbeszédpanelt.  

##  <a name="specify-supported-platforms"></a>Támogatott platformok megadása  
 A támogatott platformok azok az operációs rendszerek, amelyen az adott konfigurációelem értékelve van a megfelelőség szempontjából.  

**Konfigurációelem létrehozása varázsló** **Támogatott platformok** lapján jelölje ki azon Windows-verziókat a listában, amelyeknél értékelni szeretné megfelelőség szempontjából a konfigurációelemet, vagy kattintson **Az összes kiválasztása** gombra.  

## <a name="complete-the-wizard"></a>Fejezze be a varázslót  
 A varázsló **Összegzés** oldalán ellenőrizze a végrehajtandó műveleteket, majd fejezze be a varázslót. Az új konfigurációelem az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** csomópontjában látható.  

