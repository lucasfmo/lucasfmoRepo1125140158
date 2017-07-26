---
title: "Alkalmazások fejlesztéséhez |} Microsoft Docs"
description: "Létrehozhat és telepíthet alkalmazásokat és központi telepítési típusok a System Center Configuration Managerrel."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: 14
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: da86fc2f61ce8229fb0d3f58a4f8a24d1514b30e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-applications-with-system-center-configuration-manager"></a>Alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager alkalmazásnak a fájlokat és a szoftverek eszközre telepítéséhez szükséges információkat. Az alkalmazás rendelkezik egy vagy több központi telepítési típusok, amely a telepítési fájlokból és a szoftver telepítéséhez szükséges információkat. A központi telepítési típus szabályokat, amelyek adja meg, mikor és hogyan a szoftver központi telepítése is rendelkezik.  

 A következő módszerekkel hozhatók létre alkalmazások:  

-   Az alkalmazás és központi telepítési típusok automatikus létrehozása a alkalmazástelepítő fájlok olvasásával.  

-   Az alkalmazás manuális létrehozása központi telepítési típusok későbbi hozzáadásával.  

-   Alkalmazás importálása fájlból.  

> [!NOTE]  
>  [Hozzon létre az alkalmazások mobileszközökre vonatkozó ](../../mdm/deploy-use/create-applications.md) iOS, Windows Phone és az Android-alkalmazások létrehozásának részletes információkat nyújt.  

Az alábbi lépések segítségével a Configuration Manager-alkalmazások és központi telepítési típusok.  

## <a name="start-the-create-application-wizard"></a>Alkalmazás létrehozása varázsló elindítása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása**.  

## <a name="specify-whether-you-want-to-automatically-detect-application-information-or-manually-define-the-information"></a>Adja meg, hogy alkalmazással kapcsolatos adatok automatikus észlelése és manuális megadása az információk  

-   Alkalmazásadatok automatikusan legyenek, ha azt szeretné, egy hasonló a Windows Installer-fájl, amely nem függőségekkel vagy követelményekkel rendelkezik egy egyetlen központi telepítési típussal rendelkező egyszerű alkalmazás hozható létre. Ha ezzel az eljárással hoz létre alkalmazást, ahhoz a későbbiekben igény szerint további központi telepítési típusokat adhat, illetve módosíthatja azokat, valamint kiegészítheti az alkalmazást észlelési módszerekkel, függőségekkel vagy követelményekkel.  

-   Több központi telepítési típusok, függőségekkel, észlelési módszerrel vagy követelményekkel rendelkező összetettebb alkalmazásokat hozhat létre az alkalmazás adatainak manuális megadása.  

### <a name="automatically-detect-application-information"></a>Alkalmazással kapcsolatos adatok automatikus észlelése  

1.  Az a **általános** a alkalmazás létrehozása varázsló, jelölje be **a telepítési fájlokból az alkalmazás adatainak automatikus észlelése**.  

2.  Az a **típus** legördülő listából válassza ki az alkalmazástelepítő fájltípust alkalmazással kapcsolatos információk észleléséhez használni kívánt. További információ az elérhető telepítési típusokról: [A Configuration Managerben támogatott központi telepítési típusok](/sccm/apps/deploy-use/create-applications#deployment-types-supported-by-configuration-manager) ebben a témakörben.  

3.  A a **hely** adja meg az UNC elérési utat (formájában  *\\ \\kiszolgáló\\megosztása\\\filename*) vagy tárolóhivatkozását az alkalmazással kapcsolatos információk észleléséhez használni kívánt alkalmazástelepítő fájl. A telepítőfájl helyét a **Tallózás** gombra kattintva is megadhatja.  

    > [!IMPORTANT]  
    >  Ha bejelöli **Windows Installer (\*.msi fájlt)** alkalmazás típusként, a megadott mappában lévő fájlok mindegyikét importálja az alkalmazással, és a terjesztési pontokra küldi. Győződjön meg arról, hogy a megadott mappában csak az alkalmazás telepítéséhez szükséges fájlokat tartalmazza. A Configuration Manager támogatására 20 000 alkalmazásfájl egy alkalmazáscsomagban fájljainak lett tesztelve. Ha az alkalmazás további fájlokat tartalmaz, érdemes lehet több alkalmazást létrehozni, amelyek kevesebb fájlt.  

    >  Az alkalmazás és az alkalmazástartalmak almappáit tartalmazó UNC elérési útnak hozzáféréssel kell rendelkeznie.  

4.  Az a **importálási adatok** lap az alkalmazás létrehozása varázsló, tekintse át a importálása adatokat, és válassza a **következő**. Ha szükséges, választhat **előző** lépjen vissza, és javítsa ki a hibákat.  

5.  Az a **általános információkat** lap az alkalmazás létrehozása varázslóban adja meg a következő adatokat:  

    > [!NOTE]  
    >  Lehetséges, hogy néhány, az alkalmazástelepítő fájlokból korábban beolvasott adat már ki van töltve. Emellett a megjelenített beállítások a létrehozott alkalmazástípustól függően eltérőek lehetnek.  

    -   Az alkalmazás általános adatait, például az alkalmazás nevét, a megjegyzéseket, a verziót és a egy nem kötelező hivatkozást, könnyebben megtalálható az alkalmazás a Configuration Manager konzolon.  

    -   **Telepítőprogram**– adja meg a telepítőprogramot és egyéb tulajdonságok, amelyek szükségesek ahhoz, hogy az alkalmazás központi telepítési típus telepítése szükséges.  

        > [!TIP]  
        >  Ha a telepítőprogram nem látható, válassza a **Tallózás** , és keresse meg a telepítési program helyre.  

    -   **Viselkedésmód telepítése**– adja meg, hogy az alkalmazás központi telepítési típus csak a jelenleg bejelentkezett felhasználó vagy az összes felhasználó számára telepíti. Megadhatja, hogy a központi telepítési típus telepíti az összes felhasználó szánt egy eszközt, vagy csak egy adott felhasználó számára felhasználónak szánt.  

    -   **Az automatikus VPN-kapcsolat használata (Ha be van állítva)**– Ha a VPN-profil van telepítve az eszközön, amelyre az alkalmazást elindítja, nyissa meg a VPN kapcsolatot az alkalmazás indításakor (Windows 8.1 és Windows Phone 8.1 esetén).  

         A Windows Phone 8.1-eszközökön az automatikus VPN-kapcsolatok nem támogatottak, ha egynél több VPN-profil van telepítve az eszközön.  

         VPN-profilokkal kapcsolatban bővebben lásd: [VPN-profilok](../../protect/deploy-use/vpn-profiles.md).  

6.  Válasszon **következő**, ellenőrizze az alkalmazás adatait a **összegzés** lapon, majd fejezze be az alkalmazás létrehozása varázsló.  

Az új alkalmazás megjelenik a **alkalmazások** a Configuration Manager konzolon, és csomópont végzett, az alkalmazás létrehozása. Ha további központi telepítési típusokat szeretne hozzáadni az alkalmazáshoz, tekintse át ennek a témakörnek [Az alkalmazás központi telepítési típusainak létrehozása](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application) című szakaszát.  

### <a name="manually-specify-application-information"></a>Alkalmazás adatainak manuális megadása  

1.  Az a **általános** a alkalmazás létrehozása varázsló, jelölje be **az alkalmazás adatainak manuális megadása**, és válassza a **következő**.  

2.  Az alkalmazás, például az alkalmazás nevét, a megjegyzéseket, a verziót és a egy nem kötelező hivatkozást, könnyebben megtalálható az alkalmazás a Configuration Manager konzolon általános információk megadása.  

3.  Az a **Alkalmazáskatalógus** lap az alkalmazás létrehozása varázslóban adja meg a következő adatokat:  

    -   **Választott nyelv**– a legördülő listában válassza ki a beállítani kívánt alkalmazás nyelvi verzióját. Válasszon **hozzáadása** állíthatja be az alkalmazás további nyelveket.  

    -   **Honosított alkalmazásnév**– adja meg az alkalmazás nevét a kiválasztott nyelvet a **választott nyelv** legördülő listából.  

        > [!IMPORTANT]  
        >  Meg kell adnia egy honosított alkalmazásnevet minden beállított nyelvi verzióhoz, amelynek beállítása.  

    -   **Felhasználói kategóriák**--válasszon **szerkesztése** Alkalmazáskategóriák megadása a kiválasztott nyelven a **választott nyelv** legördülő listából. A Szoftverközpont felhasználók itt kiválasztott kategóriák segítségével szűrhetik és rendezhetik az elérhető alkalmazásokat.  

    -   **Felhasználói dokumentáció**--válasszon **Tallózás** határozza meg az URL-címet, vagy UNC elérési út és fájlnév, a fájl nevét, amely a Szoftverközpont felhasználóinak tudja olvasni az alkalmazással kapcsolatos további információkért.  

    -   **Hivatkozás szövege**– adja meg az alkalmazás URL-címe helyett megjelenítendő szöveget.  

    -   **Alkalmazás adatvédelmi URL-címe**– adja meg az alkalmazás adatvédelmi nyilatkozatai mutató URL-címet.  

    -   **Honosított leírás**– adja meg egy leírást ehhez az alkalmazáshoz kiválasztott a **választott nyelv** legördülő listából.  

    -   **Kulcsszavak**– adja meg a kulcsszavak listáját a kiválasztott nyelven a **választott nyelv** legördülő listából. Ezek a kulcsszavak segítségével felhasználók a Szoftverközpont kereshetik meg az alkalmazást.  

    -   **Ikon**--válasszon **Tallózás** jelölje be az alkalmazás ikonját az elérhető ikonok közül. Ha nem ad meg ikont, alapértelmezett ikont az alkalmazás használható.  

    -   **Megjelenítés kiemelt alkalmazásként és kiemelés a vállalati portál**– ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazást a vállalati portálon.  

4.  Az a **központi telepítési típusok** lapon válassza ki az alkalmazás létrehozása varázsló **Hozzáadás** egy új központi telepítési típus létrehozásához.  

 További információkért lásd: [az alkalmazás központi telepítési típus létrehozása](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).  

5.  Válasszon **következő**, ellenőrizze az alkalmazás adatait a **összegzés** lapon, majd fejezze be az alkalmazás létrehozása varázsló.  

Az új alkalmazás megjelenik a **alkalmazások** csomópont a Configuration Manager konzol.  

##  <a name="create-deployment-types-for-the-application"></a>Az alkalmazás központi telepítési típus létrehozása  
 Ha bejelöli **a telepítési fájlokban a központi telepítési típus automatikus azonosítása** a a **általános** lapon a központi telepítési típus létrehozása varázsló nem szükség lehet néhány az alábbi eljárások lépéseinek befejezéséhez.  

## <a name="start-the-create-deployment-type-wizard"></a>A Központi telepítési típus varázsló elindítása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Válasszon ki egy alkalmazást, majd a a **Home** lap a **alkalmazás** csoportjában válassza **központi telepítési típus létrehozása**.  

> [!TIP]  
>  Is a központi telepítési típus létrehozása varázsló elindításához a az alkalmazás létrehozása varázsló segítségével, és onnan a **központi telepítési típusok** lapján a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel.  

## <a name="specify-whether-you-want-to-automatically-detect-deployment-type-information-or-manually-set-up-the-information"></a>Adja meg, hogy szeretné-e automatikusan a központi telepítési típussal kapcsolatos információk észleléséhez, vagy manuálisan állíthatja be az adatokat  
 Használja a következő eljárásokkal automatikusan észlelhetők vagy manuálisan állíthatja be a központi telepítési típussal kapcsolatos információk.  

### <a name="automatically-detect-deployment-type-information"></a>Központi telepítési típussal kapcsolatos információk automatikus észlelése  

1.  Az a **általános** a központi telepítési típus létrehozása varázsló, jelölje be **a telepítési fájlokban a központi telepítési típus automatikus azonosítása**.  

2.  Az a **típus** mezőben adja meg az alkalmazástelepítő fájltípust, amelyet a központi telepítési típussal kapcsolatos információk észleléséhez használni.  

3.  A a **hely** adja meg az UNC elérési utat (formájában  *\\ \\server\\megosztása\\Fájlnév*), vagy adja meg az alkalmazástelepítő fájlok és a központi telepítési típussal kapcsolatos információk észleléséhez használni kívánt tartalom áruházi hivatkozását. Dönthet úgy is **Tallózás** a telepítési fájl megkereséséhez.  

    > [!NOTE]  
    >  Az alkalmazás és az alkalmazástartalmak almappáit tartalmazó UNC elérési útnak hozzáféréssel kell rendelkeznie.  

4.  Az a **importálási adatok** lapon a központi telepítési típus létrehozása varázsló, tekintse át a importálása adatokat, és válassza a **következő**. Másik lehetőségként **előző** lépjen vissza, és javítsa ki a hibákat.  

5.  Az a **általános információkat** lapon a központi telepítési típus létrehozása varázslót, adja meg a következő adatokat:  

    > [!NOTE]  
    >  Lehetséges, hogy néhány központi telepítési típusra vonatkozó adat már szerepel a lapon, ha korábban már beolvasták őket az alkalmazástelepítő fájlokból. Emellett a megjelenített beállítások eltérőek lehetnek, attól függően, hogy a központi telepítési típust hoz létre.  

    -   A központi telepítési típussal kapcsolatos általános információkat, például a neve, a felügyeleti megjegyzések és a rendelkezésre álló nyelveket.  

    -   **Telepítőprogram**– adja meg a telepítési program és a központi telepítési típus telepítéséhez szükséges összes tulajdonságot.  

    -   **Viselkedésmód telepítése**– adja meg, hogy a központi telepítési típus az aktuális felhasználó vagy az összes felhasználó számára. Azt is megadhatja, hogy a központi telepítési típus minden felhasználó számára telepíteni, ha egy eszközre telepítik, vagy a központi telepítést, hogy írja be a felhasználó csak akkor, ha egy felhasználó számára telepítik.  

    -   **Az automatikus VPN-kapcsolat használata (Ha be van állítva)**– Ha a VPN-profil van telepítve az eszközön, amelyre az alkalmazást elindítja, nyissa meg a VPN kapcsolatot az alkalmazás indításakor (Windows 8.1 és Windows Phone 8.1 esetén). Ha több VPN-profilok a Windows 8.1-eszköz van telepítve, az első telepített VPN-profil alapértelmezés szerint használja.  

         A Windows Phone 8.1-eszközökön az automatikus VPN-kapcsolatok nem támogatottak, ha egynél több VPN-profil van telepítve az eszközön.  

         VPN-profilokkal kapcsolatban bővebben lásd: [VPN-profilok a System Center Configuration Managerben](../../protect/deploy-use/vpn-profiles.md).  

6.  Válasszon **következő**, majd folytassa a [Tartalombeállítások megadása a központi telepítési típus](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

### <a name="manually-set-up-the-deployment-type-information"></a>A központi telepítési típus adatainak manuális beállítása  

1.  Az a **általános** a központi telepítési típus létrehozása varázsló, jelölje be **a központi telepítési típus adatainak manuális megadása**.  

2.  Az a **típus** válassza ki azt az alkalmazástelepítő fájltípust, amelyet a központi telepítési típussal kapcsolatos információk észleléséhez használni. Választhat, hogy ugyanazokat a telepítési típusokat szeretné használni, ha automatikusan észleli a központi telepítési típussal kapcsolatos információk, és azt is megadhatja a központi telepítési típus parancsprogram.  

3.  Az a **általános információkat** lapon adja meg egy nevet a központi telepítési típus, megadhat egy leírást, és a nyelveket, amelyhez hozzá szeretné elérhetővé tenni a központi telepítési típus, és válassza a központi telepítési típus létrehozása varázsló **tovább**.  

4.  Lépjen a következőre: [Tartalombeállítások megadása a központi telepítési típushoz](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

##  <a name="specify-content-options-for-the-deployment-type"></a>Tartalombeállítások megadása a központi telepítési típushoz  

1.  Az a **tartalom** lapon a központi telepítési típus létrehozása varázslót, adja meg a következő adatokat:  

    -   **Tartalom helye**– adja meg a központi telepítési típus tartalmának helyét, vagy válasszon **Tallózás** kiválasztása a központi telepítési típus tartalommappáját.  

        > [!IMPORTANT]  
        >  A helykiszolgáló számítógép rendszer fiókjának a megadott tartalomhelyre engedélyekkel kell rendelkeznie.  

    -   **Tartalom megőrzése az ügyfél gyorsítótárában**– ezt a beállítást meg a tartalom megőrződjön-e az ügyfélszámítógép gyorsítótárában határozatlan ideig, még akkor is, ha már korábban lefutott. Bár ez a beállítás egyes központi telepítések, például a Windows Installer-alapú szoftvereknél, amelyek a forrás helyi példányának szükséges frissítések alkalmazása esetében hasznos lehet a rendelkezésre álló gyorsítótár-terület csökkenti. Ha ezt a beállítást, megakadályozhatja a nagyobb méretű központi telepítések később meghiúsulhatnak, ha az nem áll rendelkezésre elegendő szabad lemezterület.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**– ezzel a beállítással úgy csökkenthető a hálózat terhelése, így az ügyfelek más helyi ügyfelekről, amelyek már letöltötték és gyorsítótárba helyezték a tartalmat a hálózaton. Ez a beállítás a Windows BranchCache technológiáját használja.  

    -   **Telepítőprogram**– adja meg a nevét, a telepítőprogram és a szükséges telepítési paramétereket, vagy válasszon **Tallózás** a telepítési fájl megkereséséhez.  

    -   **Telepítés indul**– szükség esetén adja meg a központi telepítési típus telepítőprogramját tartalmazó mappát. A mappa megadható az ügyfélen abszolút elérési utat vagy a telepítőfájlokat tartalmazó terjesztésipont-mappa elérési útját.  

    -   **Távolítsa el a program**– szükség esetén adja meg az eltávolítóprogram és a szükséges paramétereket, vagy válasszon **Tallózás** megkeresését.  

    -   **Távolítsa el a start**– szükség esetén adja meg a mappa, amely a központi telepítési típus az eltávolítóprogram. A mappa megadható az ügyfélen abszolút elérési utat vagy egy a csomagot tartalmazó terjesztésipont-mappa alapján értelmezett relatív elérési.  

    -   **Futtassa a telepítési és az eltávolítóprogramot 32 bites folyamatként 64 bites ügyfeleken**--a 32 bites fájl- és beállításjegyzék-helyek használata Windows rendszerű számítógépeken a központi telepítési típus telepítőprogramját futtatásához.  

2.  Válasszon **következő**.  

## <a name="set-up-detection-methods-to-indicate-the-presence-of-the-deployment-type-windows-pcs-only"></a>A központi telepítési típus (csak Windows rendszerű számítógépek) meglétének jelzéséhez észlelési módszerek beállítása  
 Ez az eljárás beállítja, egy észlelési módszert, amely jelzi, hogy a központi telepítési típus már telepítve van.  

1.  Az a **észlelési módszer** a központi telepítési típus létrehozása varázsló, jelölje be **szabályok konfigurálása a központi telepítési típus meglétének észleléséhez**, és válassza a **záradék hozzáadása**.  

    > [!NOTE]  
    >  Ehelyett választhatja az **Egyéni parancsfájl használata a központi telepítési típus észleléséhez** lehetőséget is. További információkért lásd: [egyéni parancsfájl használata a központi telepítési típus meglétének ellenőrzése](/sccm/apps/deploy-use/create-applications#Use-a-custom-script-to-check-for-the-presence-of-a-deployment-type).  

2.  Az **Észlelési szabály** párbeszédpanel **Beállítás típusa** legördülő listájában válassza ki a központi telepítési típus meglétének észleléséhez használni kívánt módszert. A következő módszerek közül választhat:  

    -   **Fájlrendszer**– ezt a módszert használja, hogy egy adott fájl vagy mappa létezik-e egy eszközön, így jelezve, hogy telepítve van-e az alkalmazás észleléséhez.  

        > [!NOTE]  
        >  A **fájlrendszer** beállítástípus nem támogatja a hálózati megosztás UNC-útvonal az elérési út mezőbe. Csak az ügyféleszközön értelmezett helyi útvonalat lehet megadni.  
        >   
        >  Ellenőrizze a megadott fájl vagy mappa 32 bites fájl helyét, jelölje be a jelölőnégyzetet **a fájl vagy mappa egy 64 bites rendszereken futó 32 bites alkalmazással társított** első. Ha a fájl vagy mappa itt nem található, a keresés a 64 bites helyeken folytatódik.  

    -   **Beállításjegyzék**– ezt a módszert használja, hogy egy adott beállításkulcs vagy beállításazonosító létezik-e egy eszközön, így jelezve, hogy telepítve van-e az alkalmazás észleléséhez.  

        > [!NOTE]  
        >  32 bites beállításjegyzék helyeken szeretné keresni a megadott beállításkulcsot, választja **a beállításkulcs egy 64 bites rendszereken futó 32 bites alkalmazással társított** első. Ha a beállításkulcs itt nem található, a keresés a 64 bites helyeken folytatódik.  

    -   **A Windows Installer**– ezt a módszert használja, hogy egy adott Windows Installer-fájl létezik-e egy eszközön, így jelezve, hogy telepítve van-e az alkalmazás észleléséhez.  

3.  Az elem, hogy telepítve van-e a központi telepítési típus észleléséhez használni kívánt adatok megadása. Használhat például egy adott fájlt, mappát, beállításkulcsot, beállításazonosítót vagy Windows Installer-termékkódot is.  

4.  Adja meg a szükséges információkat arra az értékre vonatkozóan, amelynek alapján a központi telepítési típus telepített állapotának észleléséhez használt elemet ellenőrizni szeretné. Ha egy fájl segítségével ellenőrizze, hogy telepítve van a központi telepítési típus, választhatja például **a fájlrendszer beállításainak a célszámítógépen, az alkalmazás jelenlétének jelöléséhez léteznie kell**.  

5.  Válasszon **következő** bezárásához a **észlelési szabály** párbeszédpanel megnyitásához.  

###  <a name="use-a-custom-script-to-check-for-the-presence-of-a-deployment-type"></a>Egyéni parancsfájl használata a központi telepítési típus meglétének ellenőrzése  

1.  Az a **észlelési módszer** a központi telepítési típus létrehozása varázsló, jelölje be a **egyéni parancsfájl használata a központi telepítési típus meglétének észleléséhez** mezőbe, majd válassza a **szerkesztése**.  

2.  A **Parancsprogram-szerkesztő** párbeszédpanel **Parancsfájl típusa** legördülő listájában válassza ki a központi telepítési típus észleléséhez használni kívánt parancsnyelvet.  

3.  Az a **parancsfájl tartalmát** mezőbe írja be a használni kívánt parancsfájlt. Is ebbe a mezőbe illessze be egy meglévő parancsfájl tartalmát, vagy válasszon **nyitott** tallózással keresse meg a meglévő mentett parancsfájlok. A Configuration Manager az eredményeket a parancsfájlból a parancsfájlból a Standard Out (STDOUT) kimeneti adatfolyamba, a Standard Error (STDERR) kimeneti adatfolyamba és a kilépési kód írt értékek beolvasásával ellenőrzi. Ha a kilépési kód nem nulla, akkor a parancsfájl futtatása sikertelen volt, és az alkalmazásészlelés állapota ismeretlen. Ha a kilépési kód nulla, STDOUT adatokat tartalmaz, akkor az alkalmazásészlelés állapota telepítve van.  

 Az alábbi táblázat segítségével ellenőrizze, hogy telepítve van-e az alkalmazás a parancsfájl kimenete használata című részben találja.  

|Parancsfájl kimeneti kódja|Részletek|
|--------------------------------|-----------------|
|0|**STDOUT adatsorból beolvasott adatok**– üres<br /><br /> **STDERR adatsorból beolvasott adatok**– üres<br /><br /> **Parancsfájl eredménye**– sikeres<br /><br /> **Alkalmazásészlelési állapot**– nincs telepítve|  
|0|**STDOUT adatsorból beolvasott adatok**– üres<br /><br /> **STDERR adatsorból beolvasott adatok**– nem üres.<br /><br /> **Parancsfájl eredménye**– hiba<br /><br /> **Alkalmazásészlelési állapot**– ismeretlen|  
|0|**STDOUT adatsorból beolvasott adatok**– nem üres.<br /><br /> **STDERR adatsorból beolvasott adatok**– üres<br /><br /> **Parancsfájl eredménye**– sikeres<br /><br /> **Alkalmazásészlelési állapot**– telepítve|  
|0|**STDOUT adatsorból beolvasott adatok**– nem üres.<br /><br /> **STDERR adatsorból beolvasott adatok**– nem üres.<br /><br /> **Parancsfájl eredménye**– sikeres<br /><br /> **Alkalmazásészlelési állapot**– telepítve|  
|Nem nulla|**STDOUT adatsorból beolvasott adatok**– üres<br /><br /> **STDERR adatsorból beolvasott adatok**– üres<br /><br /> **Parancsfájl eredménye**– hiba<br /><br /> **Alkalmazásészlelési állapot**– ismeretlen|  
|Nem nulla|**STDOUT adatsorból beolvasott adatok**– üres<br /><br /> **STDERR adatsorból beolvasott adatok**– nem üres.<br /><br /> **Parancsfájl eredménye**– hiba<br /><br /> **Alkalmazásészlelési állapot**– ismeretlen|  
|Nem nulla|**STDOUT adatsorból beolvasott adatok**– nem üres.<br /><br /> **STDERR adatsorból beolvasott adatok**– üres<br /><br /> **Parancsfájl eredménye**– hiba<br /><br /> **Alkalmazásészlelési állapot**– ismeretlen|  
|Nem nulla|**STDOUT adatsorból beolvasott adatok**– nem üres.<br /><br /> **STDERR adatsorból beolvasott adatok**– nem üres.<br /><br /> **Parancsfájl eredménye**– hiba<br /><br /> **Alkalmazásészlelési állapot**– ismeretlen|  

A következő táblázat a Microsoft Visual Basic (VB) minta parancsfájlok, melyekkel a saját alkalmazásészlelési parancsfájlok írása rendelkezik.  

|Visual Basic-parancsfájlminta|Leírás|  
|--------------------------------|-----------------|  
|**WScript.Quit(1)**|A parancsfájl nem nulla kimeneti kódot ad vissza, ami azt jelzi, hogy a futása sikertelen volt. Ilyenkor az alkalmazásészlelési állapot ismeretlen.|  
|**WScript.StdErr.Write "Parancsfájl sikertelen"**<br /><br /> **WScript.Quit(0)**|A parancsfájl nulla kimeneti kódot ad vissza, de az STDERR értéke nem üres, ami azt jelzi, hogy a parancsfájl futása sikertelen volt. Ilyenkor az alkalmazásészlelési állapot ismeretlen.|  
|**WScript.Quit(0)**|A parancsfájl nulla kimeneti kódot ad vissza, ami azt jelzi, hogy sikeresen lefutott. Az STDOUT értéke azonban üres, ami azt jelenti, hogy az alkalmazás nincs telepítve.|  
|**WScript.StdOut.Write "az alkalmazás telepítve van"**<br /><br /> **WScript.Quit(0)**|A parancsfájl nulla kimeneti kódot ad vissza, ami azt jelzi, hogy sikeresen lefutott. Az STDOUT értéke nem üres, ami azt jelenti, hogy az alkalmazás telepítve van.|  
|**WScript.StdOut.Write "az alkalmazás telepítve van"**<br /><br /> **WScript.StdErr.Write "Kész"**<br /><br /> **WScript.Quit(0)**|A parancsfájl nulla kimeneti kódot ad vissza, ami azt jelzi, hogy sikeresen lefutott. Az STDOUT és az STDERR értékei nem üresek, ami azt jelenti, hogy az alkalmazás telepítve van.|  

 > [!NOTE]  
 >  A parancsfájl maximális mérete 32 kilobájt (kB) lehet.  

4.  Válasszon **OK** bezárásához a **parancsprogram-szerkesztő** párbeszédpanel megnyitásához.  

## <a name="specify-user-experience-options-for-the-deployment-type"></a>Felhasználói élménnyel kapcsolatos beállítások megadása a központi telepítési típushoz  
 Ezek a beállítások megadják, hogyan lehet az alkalmazás telepítve az eszközökön, és a felhasználó megjelenik.  

1.  Az a **felhasználói élmény** lapon a központi telepítési típus létrehozása varázslót, adja meg a következő adatokat:  

    -   **Telepítési viselkedésmód**– a legördülő listában válassza ki a következő lehetőségek közül:  

        -   **Telepítés felhasználó számára**– az alkalmazás csak annak a felhasználónak, akinek az alkalmazás központi telepítése.  

        -   **A telepítést egy rendszer**– az alkalmazás csak egyszer lesz telepítve, és minden felhasználó számára érhető el.  

        -   **Telepítés rendszer számára, ha az erőforrás egy eszköz; Ellenkező esetben telepítése felhasználóként**– Ha egy eszközre telepítik az alkalmazást, az telepíti az összes felhasználó számára. Ha egy felhasználó számára telepítik az alkalmazást, azt csak adott felhasználó számára telepíti.  

    -   **Bejelentkezéshez szükséges követelmény**--bejelentkezési követelmények megadása a központi telepítési típus a következő lehetőségek közül:  

        -   **Csak amikor van bejelentkezett felhasználó**  

        -   **-E a bejelentkezett felhasználó**  

        -   **Csak amikor nincs bejelentkezett felhasználó**  

        > [!NOTE]  
        >  Ez a beállítás alapértelmezés szerint az **csak amikor van bejelentkezett felhasználó**, és nem lehet módosítani, ha a kiválasztott **telepítés felhasználó számára** a a **telepítési viselkedésmód** legördülő listából.  

    -   **Telepítőprogram láthatósága**– adja meg, amelyben a központi telepítési típus ügyféleszközökön futtatásának módját. A következő lehetőségek állnak rendelkezésre:  

        -   **Teljes méretű**– a központi telepítési típus teljes méretben fut az ügyféleszközökön. A felhasználók minden telepítési tevékenységet látnak.  

        -   **Normál**– a központi telepítési típus fut, a rendszer és a program alapértelmezett értékei szerinti normál módban. Ez az alapértelmezett futtatási mód.  

        -   **Kisméretű**– a központi telepítési típus kis méretben fut az ügyféleszközökön. A felhasználók láthatják a telepítési tevékenységet az értesítési területen vagy a tálcán.  

        -   **Rejtett**– a központi telepítési típus rejtett módban fut az ügyféleszközökön, és a felhasználók nem telepítési tevékenységet látnak.  

    -   **Felhasználók megtekintése és a program telepítésébe való beavatkozást**– adja meg, hogy a felhasználók beavatkozhatnak-e a telepítési beállítások megadása a központi telepítési típus telepítésébe együtt.  

        > [!NOTE]  
        >  Ez a beállítás alapértelmezés szerint engedélyezve van, ha bejelölte a **telepítés felhasználó számára** beállítást a **telepítési viselkedésmód** legördülő listából.  

    -   **Maximálisan engedélyezett futási idő (perc)**– adja meg a program az ügyfélszámítógépen futtassa várható maximális idejét. A beállítás értékeként nullánál nagyobb egész számot kell megadni. Az alapértelmezett érték 120 perc.  

         Ez az érték a következőkre használható:  

        -   A központi telepítési típus eredményeinek figyelése.  

        -   Ellenőrizze, hogy a központi telepítési típus esetén telepítve lesz az ügyféleszközökön karbantartási időszakok vannak definiálva. Ha karbantartási időszak van beállítva, a program elindul, csak akkor, ha a karbantartási időszakban elegendő idő áll rendelkezésre a **maximálisan engedélyezett futási idő** beállítást.  

        > [!IMPORTANT]  
        >  Ütközést okozhat, ha a **maximálisan engedélyezett futási idő** hosszabb, mint az ütemezett karbantartási időszaknál. Ha a felhasználó a maximálisan engedélyezett futási időt bármely elérhető karbantartási időszaknál hosszabbra állítja, akkor a központi telepítési típus futtatására nem kerül sor.  

2.  **Várható telepítési idő (percekben)**– a központi telepítési típus telepítéséhez szükséges becsült idő. Ez az érték a Szoftverközpont felhasználóinak jelenik meg.  

## <a name="specify-requirements-for-the-deployment-type"></a>Követelmények megadása a központi telepítési típushoz  

1.  A a **követelmények** lapon válassza ki a központi telepítési típus létrehozása varázsló **Hozzáadás** megnyitásához a **követelmény létrehozása** párbeszédpanel mezőbe, és új követelmény hozzáadásához.  

    > [!NOTE]  
    >  Az új követelményeket is hozzáadhat a **követelmények** lapján a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel.  

2.  A **Kategória** legördülő listában válassza ki, hogy az adott követelmény eszközre vagy felhasználóra vonatkozik-e, vagy válassza az **Egyéni** lehetőséget egy korábban létrehozott globális feltétel használatához. Ha bejelöli **egyéni**, dönthet úgy is **létrehozása** új globális feltétel létrehozása. Globális feltételek kapcsolatban bővebben lásd: [globális feltételek létrehozása](../../apps/deploy-use/create-global-conditions.md).  

    > [!IMPORTANT]  
    >  Bármely kategóriájú követelményt **felhasználói** feltétellel **elsődleges eszköz** figyelmen kívül hagyja az alkalmazást egy eszközgyűjteménybe központi telepítésekor.  
    >   
    >  Ha a System Center 2012 R2 Configuration Manager SP1 létrehozott egy olyan Windows-csomagot és -programot vagy feladatütemezést, amelynek követelménye a Windows 10 használata, majd frissít a System Center Configuration Managerre, a Windows 10-re vonatkozó követelményt a rendszer eltávolítja. A probléma megoldásához állítsa be ismét a követelményeket. Vegye figyelembe, hogy bár a követelmény a követelmények megjelenítési el lett távolítva, továbbra is a feldolgozása megfelelő eszközökön.  

3.  Az a **feltétel** legördülő listára, válassza ki a feltételt, annak ellenőrzéséhez, hogy a felhasználó vagy az eszköz megfelel-e a telepítési követelményeknek használni kívánt. A lista tartalma a választott kategóriától függ.  

4.  Az a **operátor** legördülő listára, válassza ki az operátort, amelynek használatával összehasonlítja a választott feltételt és a megadott értéket annak ellenőrzéséhez, hogy a felhasználó vagy az eszköz megfelel-e a telepítési követelményeknek. Az elérhető operátorok a választott feltételtől függenek.  

    > [!IMPORTANT]  
    >  A rendelkezésre álló követelmények eltérőek lehetnek attól függően, hogy az eszköz típusa, amely a központi telepítési típust használ.  

5.  Az a **érték** adja meg az értékeket, amelyeket a rendszer a kiválasztott feltétellel és operátorral együtt kiértékelheti, hogy a felhasználó vagy az eszköz megfelel-e a telepítési követelményeknek. Az elérhető értékek a választott feltételtől és a választott operátortól függenek.  

6.  Válasszon **OK** a követelmény mentéséhez és bezárásához a **követelmény létrehozása** párbeszédpanel megnyitásához.  

## <a name="specify-dependencies-for-the-deployment-type"></a>A központi telepítési típus függőségeinek megadása  
 A függőségek egy vagy több olyan, más alkalmazásból származó központi telepítési típust határoznak meg, amelyeket telepíteni kell a központi telepítési típus telepítése előtt. Állíthatja be a függőséget okozó központi telepítési típusok telepítése automatikusan egy központi telepítési típus telepítése előtt.  

> [!IMPORTANT]  
>  Egyes esetekben a központi telepítési típus Ez függ a központi telepítési típus függőségei is vannak. Egymásra épülő függőséget támogatott maximális száma öt.  

1.  Az a **függőségek** lapon válassza ki a központi telepítési típus létrehozása varázsló **Hozzáadás** Ha szeretne-e a központi telepítési típusokat, amelyek a központi telepítési típus telepítése előtt telepíteni kell megadni.  

    > [!IMPORTANT]  
    >  Az új függőségeket is felvehet a **függőségek** lapján a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel.  

2.  Az a **függőség hozzáadása** párbeszédpanelen válassza ki **Hozzáadás**.  

3.  Az a **szükséges alkalmazás megadása** párbeszédpanelen válassza ki egy létező alkalmazást és egy központi telepítési típust a függőség beállításához.  

    > [!TIP]  
    >  Választhat **nézet** a kiválasztott alkalmazás vagy központi telepítési típus tulajdonságainak megjelenítéséhez.  

4.  Válasszon **OK** bezárásához a **szükséges alkalmazás megadása** párbeszédpanel megnyitásához.  

5.  Ha azt szeretné, hogy a függő alkalmazást automatikusan telepíti, válassza ki a **automatikus telepítés** a függő alkalmazás mellett.  

    > [!NOTE]  
    >  A függő alkalmazást nem kell üzembe helyezni automatikusan települ.  

6.  Az a **függőség hozzáadása** párbeszédpanel **függőségi csoport neve**, adjon meg egy nevet az alkalmazásfüggőségek e csoportjának megnevezéséhez.  

7.  Használhatja a **prioritás növelése** és **Prioritás csökkentése** gombokkal módosíthatja az egyes függőségek kiértékelésének sorrendjét.  

8.  Válasszon **OK** bezárásához a **függőség hozzáadása** párbeszédpanel megnyitásához.  

## <a name="confirm-the-deployment-type-settings-and-finish-the-wizard"></a>A központi telepítési típus beállításainak megerősítése és a varázsló  

1.  Az a **összegzés** lapon ellenőrizze a varázsló által elvégzendő műveleteket a központi telepítési típus létrehozása varázsló. Válasszon **következő** a központi telepítési típus létrehozásához, vagy válasszon **előző** visszalép, és a központi telepítési típus beállításainak módosításához.  

2.  Után a **folyamatban** lapon befejeződik, tekintse át a végrehajtandó műveleteket a varázsló tartott, és válassza a **Bezárás** a varázsló befejezéséhez.  

3.  Ha a központi telepítési típus létrehozása varázsló az alkalmazás létrehozása varázslóból indította, visszatér a **központi telepítési típusok** az alkalmazás létrehozása varázsló.  

## <a name="set-up-additional-options-for-deployment-types-that-contain-virtual-applications"></a>Adja meg további beállításokat virtuális alkalmazásokat tartalmazó központi telepítési típusokhoz  
 Az alábbi eljárások segítségével adja meg a virtuális alkalmazásokat tartalmazó központi telepítési típusok további beállításait.  

### <a name="set-up-content-options-for-application-virtualization-app-v-deployment-types"></a>Tartalombeállítások megadása a központi telepítési típusok Application Virtualization (App-V) beállítása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **alkalmazások**.  

2.  Az a **alkalmazások** listára, válassza ki az alkalmazás az App-V központi telepítési típust. Ezt követően a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

3.  Az a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel a **központi telepítési típusok** lapon, válassza ki az App-V központi telepítési típust, majd válassza **szerkesztése**.  

4.  Az a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel a **tartalom** lapon állítsa be a következő beállításokat, szükség esetén:  

    -   **Tartalom megőrzése az ügyfél gyorsítótárában**– ezt a beállítást annak érdekében, hogy a központi telepítési típus tartalma ne törlődjön a Configuration Manager-ügyfél gyorsítótárában.  

    -   **Tartalom betöltése az App-V gyorsítótárba indítás előtt**– ezt a beállítást annak érdekében, hogy a virtuális alkalmazás összes tartalmát betöltse az App-V gyorsítótárba az alkalmazás indítása előtt. Ez a beállítás kiválasztása biztosítja azt, hogy az alkalmazás tartalmát a gyorsítótárban nem rögzítve van, és törölheti is szükség szerint.  

5.  Válasszon **OK** bezárásához a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

6.  Válasszon **OK** bezárásához a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

### <a name="set-up-publishing-options-for-app-v-deployment-types"></a>Állítsa be a közzétételi beállítások App-V központi telepítési típusokhoz  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **alkalmazások**.  

3.  Az a **alkalmazások** listára, válassza ki az alkalmazás az App-V központi telepítési típust. Ezt követően a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel a **központi telepítési típusok** lapon, válassza ki az App-V központi telepítési típust, majd válassza **szerkesztése**.  

5.  Az a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel a **közzétételi** lapra, jelölje ki a virtuális alkalmazás közzétenni kívánt elemeket.  

6.  Válasszon **OK** bezárásához a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

7.  Válasszon **OK** bezárásához a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel megnyitásához.  

## <a name="import-an-application"></a>Alkalmazás importálása  
 A következő eljárással importálhat egy alkalmazást a Configuration Managerbe. További tudnivalókat az alkalmazások exportálásáról: [System Center Configuration Manager-alkalmazásokkal kapcsolatos felügyeleti feladatok](../../apps/deploy-use/management-tasks-applications.md).  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.   

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás importálása**.  

4.  A a **általános** oldalán a **alkalmazás importálása varázsló**, válassza a **Tallózás**, és adja meg egy UNC elérési útját a .zip-fájlt, amely rendelkezik az importálni kívánt alkalmazást.  

5.  Az a **fájltartalom** lapon, válassza ki a végrehajtandó műveletet végezni, ha az importálni próbált alkalmazás egy meglévő alkalmazás ismétlődése. Hozzon létre egy új alkalmazást vagy figyelmen kívül az ismétlődést, és adja hozzá a rendszer új változatot ad a meglévő alkalmazáshoz.  

6.  Az a **összegzés** lapon tekintse át a végrehajtandó műveleteket, és majd a varázsló befejezéséhez.  

 Az új alkalmazás megjelenik az **Alkalmazások** csomópontban.  

> [!TIP]  
>  A Windows PowerShell-parancsmag **Import-CMApplication** rendelkezik a fenti eljárással azonos funkciót. További információkért lásd: [Import-CMApplication](https://technet.microsoft.com/library/jj821738.aspx) a Microsoft System Center 2012 Configuration Manager SP1 parancsmag-referencia.  

##  <a name="deployment-types-supported-by-configuration-manager"></a>A Configuration Manager által támogatott központi telepítési típusok  

|Központi telepítés típusának neve|További információ|  
|--------------------------|----------------------|  
|**A Windows Installer (\*.msi fájlt)**|Egy Windows Installer-fájlból jön létre a telepítési típus.|  
|**Windows-alkalmazáscsomag (\*.appx, \*.appxbundle)**|Központi telepítési típust hoz létre a Windows 8, a Windows RT vagy valamely újabb operációs rendszerhez egy Windows-alkalmazáscsomagfájlból vagy egy Windows-alkalmazáskötegcsomagból.|  
|**Windows-alkalmazáscsomag (a Windows áruházban)**|Központi telepítéstípust hoz létre a Windows 8, Windows RT, vagy később egy hivatkozást az alkalmazáshoz a Windows áruházból, vagy jelölje be a szükséges alkalmazás áruházban.<br /><br /> Ha azt szeretné, hogy az alkalmazás telepítése a Windows Áruházra mutató hivatkozást, győződjön meg arról, hogy a csoportházirend-beállítás **az áruház alkalmazás kikapcsolása** értéke **letiltott** vagy **nincs konfigurálva**. Ha engedélyezi ezt a beállítást, a kliensgépek nem tudnak csatlakozni a Windows Áruházhoz, így nem tudják onnan letölteni a telepíteni kívánt alkalmazásokat.<br /><br /> A rendszer azokat a Windows 8-as központi telepítési típusokat, amelyek áruházra hivatkoznak, mindig a többi központi telepítési típus előtt értékelik, prioritástól függetlenül.|  
|**Parancsfájl telepítő**|A központi telepítési típus, amely meghatározza egy parancsfájlt, amely fut az ügyféleszközökön megadásával telepít tartalmat vagy a művelet elvégzéséhez.|  
|**Microsoft Application Virtualization 4**|Egy Microsoft Application Virtualization 4-jegyzékfájlból jön létre a központi telepítési típus.|  
|**Microsoft Application Virtualization 5**|Microsoft Application Virtualization 5-csomagfájlból hoz létre központi telepítéstípust.|  
|**Windows Phone alkalmazáscsomag (\*.xap fájl)**|Egy Windows Phone-alkalmazáscsomagból jön létre a központi telepítési típus.|  
|**Windows Phone alkalmazáscsomag (a Windows Phone áruházban)**|A központi telepítési típus létrehozásához meg kell adni egy Windows Phone Áruházbeli alkalmazásra mutató hivatkozást.|  
|**Windows Mobile kabinet**|Egy Windows Mobile-kabinetfájlból (.cab) jön létre a központi telepítési típus a Windows Mobile rendszerű eszközökhöz.|  
|**Alkalmazáscsomag iOS rendszerhez (\*.ipa-fájl)**|Egy iOS-alkalmazáscsomagból jön létre a központi telepítési típus.|  
|**Alkalmazáscsomag az iOS App Store-ból**|A központi telepítési típus létrehozásához meg kell adni egy hivatkozást, amely egy App Store áruházbeli iOS-alkalmazásra mutat.|  
|**Alkalmazáscsomag az Androidhoz (\*.apk file)**|Egy Android-alkalmazáscsomagból jön létre a központi telepítési típus.|  
|**Alkalmazáscsomag az Androidhoz a Google Playről**|A központi telepítési típus létrehozásához meg kell adni egy Google Play áruházbeli alkalmazásra mutató hivatkozást.|  
|**Mac OS X**|A CMAppUtil eszközzel létrehozott .cmmac fájlból hoz létre központi telepítéstípust Mac számítógépek számára.<br /><br /> Csak a Configuration Manager-ügyfelet futtató Mac számítógépekre vonatkozik.|  
|**Webalkalmazás**|A központi telepítési típus létrehozásához meg kell adni egy webalkalmazásra mutató hivatkozást. A központi telepítési típus telepíti egy helyi a webes alkalmazás a felhasználó eszközén.<br /><br /> Ha már telepítette az Intune managed browser iOS vagy Android-eszközökön, amelyeket Ön kezel, gondoskodjon arról, hogy felhasználók csak a segítségével a felügyelt böngészőben nyissa meg az alkalmazást. Ehhez használja a következő formátumok egyikét az alkalmazásra mutató hivatkozásra cseréli megadásakor **http:** rendelkező **http-intunemam:** vagy **https:** rendelkező **https-intunemam:**<br /><br /> - **HTTP-intunemam: / / < elérési út a webes alkalmazás\>**<br /><br /> - **HTTPS-intunemam: / / < elérési út a webes alkalmazás\>**<br /><br /> A Configuration Manager alkalmazáskövetelményeket segítségével győződjön meg arról, hogy a felügyelt böngésző társítani kívánt alkalmazásokat csak telepítve vannak az iOS és Android-eszközökön.<br /><br /> Az Intune managed browser kapcsolatban bővebben lásd: [kezelése Internet-hozzáférés felügyelt böngészőszabályzatokkal](../../apps/deploy-use/manage-internet-access-using-managed-browser-policies.md).|  
|**A Windows Installer MDM-en keresztül (\*.msi)**|Ezt a telepítőtípust lehetővé teszi az alkalmazások létrehozását és telepítését Windows Installer-alapú Windows 10-et futtató számítógépeken.<br /><br /> Ennek a telepítőtípusnak a használatakor a következőket kell figyelembe venni:<br><br>-Csak feltöltheti egy egyetlen msi-fájlt.<br /><br /> – A fájl a termékkód és -verzióját használja az alkalmazások észlelésére.<br /><br /> -A az alkalmazás alapértelmezett újraindítási viselkedését fogja használni. A Configuration Manager nem szabályozza ezt.<br /><br /> – Felhasználónkénti MSI-csomagok fognak települni egy-egy felhasználóhoz.<br /><br /> -Számítógépenkénti MSI-csomagok fognak települni az eszköz minden felhasználójához.<br /><br /> -A kettős üzemmódú MSI-csomagok jelenleg csak telepíteni az eszköz minden felhasználójához.<br /><br /> -Alkalmazások frissítése akkor támogatott, ha minden verzió MSI-termékkód azonos.|  

