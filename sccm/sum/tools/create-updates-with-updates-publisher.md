---
title: "Frissítések létrehozása |} Microsoft Docs"
description: "Hozzon létre, és a System Center Updates Publisher szoftverfrissítéseket csomagot"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46a1a8ac-126c-4ee6-ae09-32dfbdb83368
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 33b188f4a9c14091429d1f49e07f1f17fbf98516
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="create--software-updates-and-update-bundles-with-updates-publisher"></a>Hozzon létre a szoftverfrissítések és a frissítési csomagok a frissítés-közzétevője

*Vonatkozik: A System Center frissítés-közzétevő*

A frissítés-közzétevője használható a **létrehozása frissítése** varázsló befejezésével hozza létre saját frissítéseit és a **csomagot hozzon létre** frissítések csomagok létrehozása varázsló.

Mivel ezek két varázslók hasonló munkafolyamat, frissítési csomag létrehozásának létrehozása a frissítések, csak a megfelelő eltérésekkel részletes hivatkozik.

## <a name="use-the-create-update-wizard"></a>A frissítés létrehozása varázsló
1.  Nyissa meg a a konzol **frissítések munkaterületen**, majd a a **első lépések** ablaktáblán válassza **frissítés** a a **Home** a menüszalag lapján. Ekkor megnyílik a **létrehozása frissítése** varázsló.

2.  Az a **csomag** lapon, az alábbi információk segítségével konfigurálhatja a frissítés:

    -   Válasszon **Tallózás** a szoftverfrissítési csomagot csomag forrásként használandó kereséséhez. Érvényes adatforrásokat tartalmaz. MSI-FÁJL. Az MSP, vagy. A következő EXE-fájlok. Frissítés-közzétevő létrehoz egy kivonatot, a fájl. Kivonatoló és fájlneve a frissítési metaadatokban majd használja a frissítés a létrehozásakor.

    -   Adja meg a frissítés a tartalom elérési útvonalát. Ha a tartalom egy helyi példányával, kiválaszthatja a jelölőnégyzet **használhat egy helyi forrásból software update tartalmának közzétételére** használata a [helyi közzétételi forrásútvonal](/sccm/sum/tools/updates-publisher-options#advanced) (és a speciális beállítás). Ha nem ezt a lehetőséget választja, meg kell adnia egy URL-címet, amelyen a frissítési található a weben. Az elérési út vagy URL-cím hozzáadódik a frissítéshez tartozó metaadatokat.

        Később amikor a frissítés közzé van téve a WSUS-kiszolgálót, Updates Publisher lekérdezi a frissítés bináris fájljait a megadott forráshelyről.

    -   Adja meg a **bináris nyelvi** a szoftverfrissítést.

    -   Adja meg **sikeres visszatérési kódok**, és **sikeres függőben lévő újraindítás kódok** a frissítés. Több visszatérési kódok elválasztásához vesszőt használatával. A visszatérési kódok segítségével határozza meg, ha a frissítés telepítése sikeres volt, és ha újraindítások volt szükség.

        -   A Windows installer-fájlok és a javítások (. MSI és. Az MSP-fájlok) automatikusan állítsa be ezeket az értékeket, és nem módosítható.

        -   A. A következő EXE frissíti, az alapértelmezett kódok határozzák meg a. EXE-fájl használhatók, ha nincs visszatérési kódok vannak megadva.

    -   Adja meg a szoftverfrissítés telepítéséhez szükséges parancssori argumentumokat.

        -   A Windows installer-fájlok és a javítások (. MSI és. Az MSP-fájlok) automatikusan beállítja ezeket az értékeket. Ezek fájltípushoz a argumentumot kell megadni,  **\[neve\]=\[érték\]**. Emellett minden beállítását, hogy kezdje egy  **/**  (például **/qn**) használata nem támogatott. MSI vagy. Az MSP szoftverfrissítéseket.

        -   A. A következő EXE-frissítések, minden argumentum érvényesek.

3.  Az a **információk** lapján adja meg a frissítés adatait, amelyek részét képezik, ha a frissítés van közzétéve, illetve nem exportálható. Részletek honosított tulajdonságokat, például a (cím) frissítések nevét és leírását tartalmazza. Ezt követően adja meg például a besorolás, a gyártó, a termék általános részletei, valamint további információt a frissítés helyét.

    ** A lokalizált tulajdonságai: **

    -   **Nyelvi**: Válasszon egy nyelvet, és adja meg nevét és leírását. Ezután kiválaszthatja további nyelveket, egy időben, és minden nyelven támogatása a saját nevét és leírását.

    -   **Cím**: Adja meg a frissítés neve. Ezt a nevet jeleníti meg a frissítés-közzétevő konzol frissítések munkaterületén.

    -   **Leírás**: A frissítés rövid leírása. A következők lehetnek a frissítés telepítése, és miért, vagy ha azt kell használni.

  **Besorolás:** Az alábbi táblázat a különböző besorolás közös leírása.

  -   **Frissítés**: Egy alkalmazás vagy a jelenleg telepített fájl frissítése.

  -   **Kritikus**: Széles körben kiadott frissítés egy adott probléma, amely nem kapcsolódó biztonsági kritikus hiba kezelésére szolgál.

  -   **Funkciócsomag**: Új termékszolgáltatások, amelyek termékkiadáson kívül terjesztett, és általában bekerülnek a soron következő teljes termékkiadásba.

  -   **Biztonsági**: Széles körben kiadott frissítés egy termékspecifikus problémára vonatkozó biztonsági.

  -   **Kumulatív frissítés**: Az egyszerű telepítés egy csomagba gyorsjavítások összesített csoportja. A gyorsjavítások lehetnek biztonsági frissítések, kritikus frissítések, szoftverfrissítések stb. Kumulatív frissítések általában egy konkrét területre, például biztonsági vagy egy termék szolgáltatás.

  -   **Szervizcsomag**: Egy alkalmazás által használt gyorsjavítások összesített csomagja. A gyorsjavítások lehetnek biztonsági frissítések, kritikus frissítések, szoftverfrissítések stb.

  -   **Eszköz**: Meghatározza egy eszköz vagy a teljes egy vagy több feladat funkciók.

  -   **Illesztőprogram**: Illesztőprogram frissítését.

 **Szállítói**: Adja meg a frissítés. A legördülő lista segítségével a frissítések, amelyek a tárházban található értékeket használja. Egy szállító megadása esetén a varázsló létrehoz egy mappát a szállító nevű **minden szoftverfrissítés** a a **frissítések munkaterület** Ha mappában már nem létezik. Nem lehet megadni a frissítéseket hoz létre a Windows Server Update Services (WSUS) szolgáltatás számára fenntartott nevek a következők:
 -   Microsoft Corporation
 -   Microsoft
 -   Frissítés
 -   Szoftverfrissítés
 -   Eszközök
 -   Eszköz
 -   Kritikus
 -   Kritikus frissítések
 -   Biztonság
 -   Biztonsági frissítések
 -   Szolgáltatáscsomag
 -   Kumulatív frissítés
 -   Szervizcsomag
 -   Illesztőprogram
 -   Illesztőprogram frissítése
 -   Csomag
 -   A kötegelt frissítés  <br /><br />

 **A termék**: Adja meg a termék, amely a frissítés típusa. A legördülő lista segítségével a frissítések, amelyek a tárházban található értékeket használja. Ugyanazt a listát, a WSUS szolgáltatás számára fenntartott nevét, amely nem használható a **szállító**, nem használható a **termék**.

 **További információ URL-címe**: Adja meg az URL-cím, ahol megtalálhatja a frissítésről további információk. A kisbetűk kell használnia **https** vagy **http** amikor beírja az URL-cím.

1.  Az a **választható információ** lapon konfigurálhatja a frissítéssel kapcsolatos további információkat tartalmazó részletei.

    -   **Közlemény azonosítója**: Közlemény azonosítók általában, de nem mindig által biztosított frissítési szállítókkal.

    -   **Cikk azonosítója**: Ha egy szoftver cikk frissítése nem érhető el, a cikk azonosítója számára lehetnek fontosak a frissítés további adatait kérő egyéni felhasználók számára.

    -   **CVE azonosítók:** Egy vagy több közös biztonsági rések, és adja meg a frissítés biztonsági adatait, vagy frissítse a csomagot Exposures (CVE) azonosítókat listázza. Listázásakor egynél több, például a CVEs elválasztásához használjon pontosvesszőt: *CVE1; CVE2.*

    -   **Támogatási URL-címe:** Az URL-címet, amely tartalmazza a támogatási információkat a frissítés listában, ha elérhető. A kisbetűk kell használnia **https** vagy **http** amikor beírja az URL-cím.

    -   **Súlyosság:** A frissítés súlyossági szintjének beállítása.

    -   **Hatása:** A következő beállítások segítségével adja meg a hatás:
        -   **Normál –** ezzel jelezheti, hogy a frissítéshez a tipikus telepítési eljárásokat.
        -   **Kisebb –** ezzel jelezheti, hogy a frissítéshez szükséges minimális telepítési eljárásokat.
        -   **Kizárólagos kezelése – igényel** ezzel jelezheti a frissítést önmagában, kizárólagos bármely frissítéseket kell telepíteni.   <br /><br />

    -   **Indítsa újra a viselkedést:** Ezzel a frissítések újraindítási műveletének kapcsolatos adatok megadása. Ez a beállítás nincs hatással a tényleges viselkedését a frissítés telepítésére.

        -   **Soha ne újraindulása**: A soha nem végzi a szoftverfrissítés telepítése után a rendszer újraindítása.
        -   **Mindig igényel újraindítást**: A számítógép mindig végzi a szoftverfrissítés telepítése után a rendszer újraindítása.
        -   **Újraindítás kérheti**: A szoftverfrissítés telepítése után a számítógép a rendszer újraindítása igényel, csak akkor, ha újraindítás szükséges. A felhasználó rendelkezik-e lehetőség halassza el az újraindítást. Ez az alapértelmezett beállítás. <br /><br />

2.  Az a **előfeltétel** adja meg azokat az előfeltételeket, amelyeket a számítógépen telepítve kell, ez a frissítés telepítése előtt. A szabályok nevezzük **detectoids**. Detectoids olyan magas szintű szabályok hasonló, amely a számítógépek CPU-kell a 64 bites processzort igényel. Detectoids is megadható a frissítéseket, amelyek a frissítés telepítése előtt telepíteni kell.

    -   A jobb teljesítmény érdekében használjon detectoids létrehozása helyett *telepíthető* és *szabályok telepítve* , amely a ugyanolyan ellenőrzést vagy a művelet végrehajtására.

 Az a keresési funkció használata **elérhető szoftverfrissítések és detectoids** adott detectoids találhatja. Például keresése **CPU** található a detectoids, amelyekkel korlátozhatja a telepítési adott CPU architektúra.

 Választhat egy vagy több detectoids előfeltételként hozzáadása egyszerre. Előfeltételek hozzáadásakor a kijelölt detectoids hozzá szeretné adni egy vagy több csoportjára. Ahhoz, hogy a telepítéshez, a számítógép minden egyes konfigurált csoport legalább egy tagot a követelménynek kell megfelelnie:

 -   Amikor rákattint **előfeltétel hozzáadása** kijelölt összes detectoids kerülnek külön, egyéni, csoportok. Ahhoz, hogy a frissítés, a számítógép kell felel meg ennek a csoportnak az Előfeltételek és adja át az konfigurált további csoportokra vonatkozó követelmények.

 -   Amikor rákattint **csoport hozzáadása** kijelölt összes detectoids egy egyetlen csoportba kerülnek. Ahhoz, hogy a frissítés, egy számítógép kell felel meg ennek a csoportnak az Előfeltételek közül legalább egy, és adja át az konfigurált további csoportokra vonatkozó követelmények.

1.  Az a **helyettesítési** adja meg azokat a felváltott (által felülírt frissítések) a frissítés. A frissítés meg van nyitva, a Configuration Manager jelöli, helyettesít frissítés **lejárt**. Az ügyfelek a frissítés helyett a felülírt frissítéseket telepíti.

2.  Az a **alkalmazhatósági** lapon a **szabály szerkesztő** szabályok, amelyek meghatározzák, hogy egy eszköz kell-e a frissítés meghatározásához. (Ez a lap hasonlít a **telepített** azt követő lapon.)

    Új szabály felvételéhez kattintson a ![Új szabály](media/newrule.png). Ekkor megnyílik a alkalmazhatósági szabályt lap, ahol konfigurálhatja a szabályok.

    Létrehozhat szabályok típusai a következők:

    -   **Fájl** – Ez a szabály segítségével szükségük van egy eszköz tulajdonságait, amelyek megfelelnek egy fájlt, vagy adja meg, ha a frissítés előtt további feltételeket is lehet alkalmazni.

    -   **Beállításjegyzék –** ennek használatával adja meg a beállításjegyzék adatait, amely szerepelnie kell egy eszköz akkor minősül a frissítés telepítése előtt.

    -   **Rendszer –** Ez a szabály alkalmazhatósági meghatározására: rendszeradatok használja. Itt választhat egy Windows-verzió, a Windows nyelv, a processzor architektúrájától meghatározása, vagy adja meg a WMI-lekérdezés azonosításához az eszközök operációs rendszer.

    -   **A Windows Installer –** használja ezt a szabálytípust egy telepített alapján alkalmazhatósági meghatározásához. MSI-fájl vagy a Windows Installer javítási (. AZ MSP). Ha a meghatározott összetevők vagy a szolgáltatások telepítését a követelmény részeként is ellenőrizheti.

        > [!IMPORTANT]  
        > A felügyelt deices, a Windows Update Agent nem észleli a Windows telepítése csomagok, amelyek felhasználói telepítve. Ezt a szabálytípust használatakor konfigurálása további alkalmazhatósági szabályok fájlverzió vagy beállításkulcs-értékeket, például, hogy a Windows Installer-csomag megfelelően észlelt függetlenül felhasználónként vagy rendszerenként alapul.

    -   **Szabály – mentett** Ez a beállítás lehetővé teszi található, és használja az Ön szabályok *szabályok munkaterületén hozott létre*.

        Miután létrehozott egy szabályt, a többi ikon használatával módosíthatja a szabályt, és ha több szabály, ezeket a szabályokat közötti kapcsolatok meghatározásához.

 Kész létrehozása, és szabályokat, kattintson az **OK** a a **szabály létrehozása** menteni az adott párbeszédpanel. Ezután létrehozhat egy **új** szabály és adhatja hozzá, amelyek is.

 Ha több szabály vagy beállítására hozzáadása egy frissítést, a logikai operátor használhatja a **szabály szerkesztő** a szabályok között, és milyen sorrendben feldolgozása feltételek meghatározására.

1.  Az a **telepített** lapon a **szabály szerkesztővel** , amelyek meghatározzák, hogy egy eszköz már telepítve a konfigurált frissítési szabályok megadása. (Ez a lap hasonlít a **alkalmazhatósági** oldal, ezen a lapon eltérő lehet.)

    A varázsló ezen lapja támogatja konfigurálása szabályok ilyen beállításokat és feltételeket, a **alkalmazhatósági** lap.

A varázsló befejezését követően az új frissítés hozzá legyen adva a csomópont a **frissítések munkaterület** , amely azonosítja a **szállító** frissítés használt nevére.

## <a name="use-the-create-bundle-wizard"></a>A csomag létrehozása varázsló
Mivel ez a varázsló használ ugyanabban a munkafolyamatban, mint a [létrehozása frissítése varázsló](#use-the-create-update-wizard), a munkafolyamat használja, de vegye figyelembe a következő különbség a csomagok:

1.  A varázsló elindításához a nyissa meg a konzol **frissítések munkaterület**, majd válassza ki **csomagot** a a **Home** a menüszalag lapján.

2.  Ellentétben a frissítés létrehozása varázsló nem csomag oldal van a csomag létrehozásakor.

3.  Az a **információk** lapján adja meg a frissítési csomagot, amelyek részét képezik, ha a frissítés közzététele, vagy exportált adatait.

4.  Az a **választható információ** lapon is beállíthat, amelyek további információval szolgálnak a frissítési csomag részleteit. Az elérhető beállítások ugyanazok, mint egy frissítés létrehozása. Azonban a hatás és a viselkedés indítsa újra a beállítások nem érhetők el, nem vonatkoznak a csomagok.

5.  Az a **előfeltétel** adja meg azokat az előfeltételeket, amelyeket a számítógépen telepítve kell, ez a csomag telepítése előtt. Ezek a szabályok ugyanazok, mint az egyes frissítések.

6.  Az a **helyettesítési** adja meg azokat a felváltott (által felülírt frissítések) a frissítési csomagot. Ezek a szabályok ugyanazok, mint az egyes frissítések.

7.  Az a **tagok** lapon kiválaszthat a frissítési csomag hozzáadandó frissítéseket. Csak a készített vagy az Updates Publisherbe importált frissítések érhetők el.

A varázsló befejezését követően az új frissítési csomag csomópontja hozzáadódik a **frissítések munkaterület** , amely azonosítja a **szállító** nevét, a frissítési csomagot használja.

