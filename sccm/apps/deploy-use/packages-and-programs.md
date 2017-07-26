---
title: "Csomagok és programok |} Microsoft Docs"
description: "Csomagok és programok vagy alkalmazások használatával a System Center Configuration Managerrel végrehajtott támogatja."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6c5b23270501c11ed5aba9a6045734c73095d1bf
ms.openlocfilehash: 6146bcf4e5aa9df6fe0b8cf71898e488ecf217cc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="packages-and-programs-in-system-center-configuration-manager"></a>Csomagok és programok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager továbbra is fennáll, a Configuration Manager 2007-ben csomagok és programok használt támogatásához. A csomagokat és programokat használó központi telepítések akkor lehetnek megfelelőbbek, mint az alkalmazást használó központi telepítések, ha a következők egyikét telepíti:  

- Linux és UNIX rendszerű kiszolgálók alkalmazások
- Olyan parancsfájlok, amelyek nem telepítenek alkalmazást egy számítógépre, például a számítógép lemezmeghajtójának töredezettségmentesítését végző parancsfájl.
- „Egyszeri” használatú parancsfájlok, amelyek nem igényelnek folyamatos figyelést.  
- Ismétlődő ütemezés szerint futtatott parancsfájlok, melyekhez nem használható globális kiértékelés.

Ha csomagokat telepít át a Configuration Manager korábbi verziója, akkor telepítheti azokat a Configuration Manager-hierarchiában. Az áttelepítés befejezése után a csomagok megjelennek a **Csomagok** csomópontban a **Szoftverkönyvtár** munkaterületen.

Módosíthatja, és ezeket a csomagokat szoftverterjesztéssel pontosan ugyanúgy telepítése. A **csomag importálása definícióból varázsló** marad a Configuration Manager örökölt csomagok importálásához. Ha az áttelepítés a Configuration Manager 2007 Configuration Manager-hierarchiába áttelepítéskor a hirdetményeket központi telepítések alakítja.  

> [!NOTE]  
>  Microsoft System Center Configuration Manager Csomagkonverzió-kezelője segítségével a csomagok és programok átalakítása a Configuration Manager-alkalmazásokkal.  
>   
>  További információ: [A Configuration Manager csomagkonverzió-kezelője](https://technet.microsoft.com/library/hh531519.aspx).  

Csomagok használhatják egyes új funkcióit a Configuration Manager, például a terjesztésipont-csoportok és a figyelést. Microsoft Application Virtualization (App-V) alkalmazások a csomagok és programok a Configuration Manager használatával nem terjeszthetők. Virtuális alkalmazások terjesztéséhez, létre kell hoznia azokat a Configuration Manager-alkalmazásként.  

##  <a name="create-a-package-and-program"></a>Csomag és program létrehozása  
 Használja az alábbi eljárásokkal hozhat létre, illetve importálhat csomagokat és programokat.  

### <a name="create-a-package-and-program-using-the-create-package-and-program-wizard"></a>Csomag és program létrehozása a Csomag és program létrehozása varázslóval  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **csomagok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **csomag létrehozása**.  

4.  Az a **csomag** oldalán a **létrehozása csomag és Program varázsló**, adja meg a következőket:  

    -   **Név**: Adja meg a csomag nevét, mely legfeljebb 50 karakter hosszú lehet.  

    -   **Leírás**: Adjon meg egy leírást a csomag egy legfeljebb 128 karakter hosszú lehet.  

    -   **Gyártó** (nem kötelező): Megadhatja a gyártó nevét, hogy könnyen azonosíthassa a csomagot a Configuration Manager konzolon. Ez legfeljebb 32 karakter hosszúságú lehet.

    -   **Nyelvi** (nem kötelező): Adja meg a csomag nyelvi verziója egy legfeljebb 32 karakter hosszú lehet.  

    -   **Verzió** (nem kötelező):  Adjon meg egy verziószámot a csomag egy legfeljebb 32 karakter hosszú lehet.

    -   **Ez a csomag forrásfájlokat tartalmaz**: Ez a beállítás azt jelzi, hogy a csomag igényli-e forrásfájlok meglétét az ügyféleszközökön. Alapértelmezés szerint a jelölőnégyzet nincs bejelölve, és a Configuration Manager nem használ terjesztési pontokat a csomaghoz. Ha a jelölőnégyzet be van jelölve, a rendszer terjesztési pontokat használ.  

    -   **Forrásmappa**: Ha a csomag forrásfájlokat tartalmaz, válassza a **Tallózás** megnyitásához a **forrásmappa** párbeszédpanel mezőben, és adja meg a csomag forrásfájljainak helyét.  

        > [!NOTE]  
        >  A helykiszolgáló számítógépfiókjának olvasási hozzáférési engedélyekkel kell rendelkeznie a megadott forrásmappához.  

5.  Az a **programtípust** oldalán a **létrehozása csomag és Program varázsló**, válassza ki a program létrehozásához, és válassza a **tovább**. Létrehozhat egy programot egy számítógép vagy eszköz számára, vagy kihagyhatja ezt a lépést, és létrehozhat egy programot később.  

    > [!TIP]  
    >  Hozzon létre egy új programot egy meglévő csomaghoz, először jelölje ki a csomagot. Ezt követően a a **Home** lap a **csomag** csoportjában válassza **Program létrehozása** megnyitásához a **Program létrehozása varázsló**.  

6.  Egy normál program vagy egy eszközprogram létrehozásához használja az alábbi eljárások egyikét.  

    #### <a name="create-a-standard-program"></a>Normál program létrehozása  

  1.  A a **programtípust** oldalán a **létrehozása csomag és Program varázsló**, válassza a **normál Program**, és válassza a **tovább**.     

    2.  Az a **normál Program** lapján adja meg a következőket:  

        -   **név:** Adjon meg egy nevet a program egy legfeljebb 50 karakter hosszú lehet.  

            > [!NOTE]  
            >  A program nevének a csomagon belül egyedinek kell lennie. A programok neve a létrehozásuk után nem módosítható.  

        -   **Parancssori**: Adja meg a parancssor használatával, a program elindításához, vagy válasszon **Tallózás** a fájl helyének kikeresését.  

            Ha egy fájl neve nem rendelkezik a megadott kiterjesztéssel, a Configuration Manager megkísérli .com, .exe és .bat lehetséges kiterjesztéseket használja.  

             A program egy ügyfélen futtatásakor a Configuration Manager először a csomagon belül, ezután a helyi Windows-mappában, a parancssori fájl nevére keresi, és majd keres a helyi *% path %*. Ha a fájl nem található, a program futtatása sikertelen lesz.  

        -   **Kezdőmappa** (nem kötelező): Adja meg a mappát, amelyből a program fut, legfeljebb 127 karakter hosszú lehet. A mappa megadható az ügyfélen abszolút elérési utat vagy egy a csomagot tartalmazó terjesztésipont-mappa alapján értelmezett relatív elérési.

        -   **Futtatás**: Adja meg a program az ügyfélszámítógépeken fut a módban. Válasszon az alábbi lehetőségek közül:  

            -   **Normál**: A program a rendszer és a program alapértelmezett értékei szerinti normál módban fut. Ez az alapértelmezett futtatási mód.  

            -   **Kisméretű**: A program kis méretben fut az ügyféleszközökön. Felhasználók láthatják a telepítési tevékenységet az értesítési területen vagy a tálcán.  

            -   **Teljes méretű**: A program teljes méretben fut az ügyféleszközökön. Minden telepítési tevékenységet látnak a felhasználók.  

            -   **Rejtett**: A program rejtett módban fut az ügyféleszközökön. Nem minden telepítési tevékenységet látnak.  

        -   **A program futtatható**: Adja meg, hogy a program csak akkor, ha van bejelentkezett felhasználó, csak akkor, ha a felhasználó nem alá van írva a, vagy attól függetlenül, hogy a bejelentkezett felhasználó az ügyfélszámítógépen fut-e.  

        -   **Futtatási mód**: Adja meg, hogy a program fut-e a jelenleg bejelentkezett felhasználó engedélyeivel vagy rendszergazdai engedélyekkel.  

        -   **Felhasználók megtekintése és a program telepítésébe való beavatkozást**: Használja ezt a beállítást, ha elérhető, adja meg, hogy a felhasználók számára a program telepítésébe való beavatkozást. A jelölőnégyzet akkor érhető el, csak ha **csak amikor nincs bejelentkezett felhasználó** vagy **-e a bejelentkezett felhasználó** van kiválasztva a **a Program futtatható** és mikor **Futtatás rendszergazdai jogosultságokkal** van kiválasztva a **futtatási mód**.  

        -   **Meghajtó mód**: Adja meg a program a hálózaton működésével kapcsolatos információkat. Válasszon egyet az alábbi lehetőségek közül:  

            -   **UNC-névvel fut**: Adja meg, hogy a program egy univerzális elnevezési konvenció (UNC) szerinti névvel fut-e. Ez az alapértelmezett beállítás.  

            -   **Meghajtóbetűjel szükséges**: Adja meg, hogy a program igényel a helyének teljes minősítéséhez egy meghajtóbetűjelet. Ezt a beállítást, a Configuration Manager bármely elérhető meghajtóbetűjelet használhatja az ügyfélen.  

            -   **Egyedi meghajtóbetűjelet igényel** : Adja meg, hogy a program igényel-e meg kell adnia a helyének teljes minősítéséhez megadott meghatározott meghajtóbetűjel (például **Z:**). Ha a megadott meghajtóbetűjel már használatban van egy ügyfélen, a program nem futtatható.  

        -   **Újracsatlakozás a terjesztési ponthoz bejelentkezésnél a**: Használja ezt a jelölőnégyzetet annak jelzésére, hogy az ügyfélszámítógép újracsatlakozik a terjesztési pontot a felhasználó bejelentkezésekor. A jelölőnégyzet alapértelmezés szerint nincs bejelölve.  

  3.  Az a **követelmények** oldalán a **létrehozása csomag és Program varázsló** adja meg a következőket:  

        -   **Egy másik programot futtasson először**: Ez a beállítás segítségével egy csomagot és programot, amelyen a csomag és program futtatása előtt.  

        -   **Platform-követelmények**: Válassza ki **Ez a program bármilyen platformon futtatható** vagy **Ez a program csak egyes platformokon futtatható**, majd válassza az operációs rendszereket futtató ügyfelek telepíthetik a csomag és program kell.  

        -   **Becsült lemezterület**: Adja meg a lemezterület méretét, amelyre a szoftvernek szüksége van a számítógépen történő futtatásával. Ehhez az **Unknown** (Ismeretlen) értéket (ez az alapértelmezett beállítás), vagy egy nullánál nem kisebb egész számot adhat meg. Ha megad egy értéket, az érték mértékegységét is meg kell adnia.  

        -   **Maximálisan engedélyezett futási idő (perc)**: Adja meg a program az ügyfélszámítógépen futtassa várható maximális idejét. Ehhez az **Unknown** (Ismeretlen) értéket (ez az alapértelmezett beállítás), vagy egy nullánál nem kisebb egész számot adhat meg.  

             Az alapérték 120 perc.  

            > [!IMPORTANT]  
            >  Ha karbantartási időszakokat alkalmaz a gyűjteményt, amelyen a program fut, ütközést akkor fordulhat elő, ha a **maximálisan engedélyezett futási idő** hosszabb, mint az ütemezett karbantartási időszaknál. Ha a maximálisan engedélyezett futási idő értéke azonban **ismeretlen**, a program elindul a karbantartási időszak alatt, és továbbra is fut, szükség esetén az időszak vége után. Ha a felhasználó a meghatározott maximális futási időt egy meghatározott időszak, bármely elérhető karbantartási időszaknál hosszabbra állítja, a program nem futtatható.  

             Ha a változó értéke **ismeretlen**, a Configuration Manager állítja a maximálisan engedélyezett futási időt 12 órára (720 percre).  

            > [!NOTE]  
            >  Ha az túllépi a maximálisan engedélyezett futási időt (akár a felhasználó által vagy az alapértelmezett érték), a Configuration Manager leállítja a programot, ha **Futtatás rendszergazdai jogosultságokkal** kijelölt és **felhasználók megtekintése és a program telepítésébe való beavatkozást** nincs kiválasztva.  

  4.  Válasszon **következő**.  

    #### <a name="create-a-device-program"></a>Eszközprogram létrehozása  

  1.  A a **programtípust** oldalán a **létrehozása csomag és Program varázsló**, jelölje be **eszközhöz tartozó Program**, és válassza a **következő**.  

  2.  Az a **eszközhöz tartozó Program** lapján adja meg a következőket:  

        -   **Név**: Adjon meg egy nevet a program egy legfeljebb 50 karakter hosszú lehet.  

            > [!NOTE]  
            >  A program nevének a csomagon belül egyedinek kell lennie. A programok neve a létrehozásuk után nem módosítható.  

        -   **Megjegyzés** (nem kötelező): Adja meg az eszközprogramhoz tartozó megjegyzést, mely legfeljebb 127 karakter hosszú lehet.  

        -   **Letöltési mappa**: Adja meg annak a mappának a nevét, a Windows CE rendszerű eszközön, a csomag forrásfájljai tárolva. Az alapértelmezett érték **\Temp\\\**.  

        -   **Parancssori**: Adja meg a parancssor használatával, a program elindításához, vagy válasszon **Tallózás** a fájl helyének kikeresését.  

        -   **Parancssor futtatása a letöltési mappában található**: A beállítással futtathatja a programot a korábban megadott letöltési mappából.  

        -   **Parancssor futtatása ebből a mappából**: Válassza ki az ezzel a beállítással megadhat egy másik mappát, amelyből a program futtatásához.  

    3.  Az a **követelmények** lapján adja meg a következőket:  

        -   **Becsült lemezterület**: Adja meg a szoftver számára szükséges lemezterület. Ez jelenik meg a mobileszközök felhasználói számára a program telepítése előtt.  

        -   **Töltse le a program**: Adja meg a program mikor tölthető le mobileszközökre vonatkozó adatokat. A következő értékeket adhatja meg: **Amint lehetséges**, **Csak gyors hálózaton keresztül** vagy **Csak ha az eszköz dokkolva van**.  

        -   **További követelmények**: Adja meg a programra vonatkozó esetleges további követelményeket. A szoftver telepítése előtt ezek jelennek meg a felhasználók számára. Értesítheti a felhasználókat például arról, hogy minden más alkalmazást be kell zárniuk a program futtatása előtt.  

  4.  Válasszon **következő**.  

  7.  Az a **összegzés** lapján tekintse át a végrehajtandó műveleteket megnyílik, és fejezze be a varázslót.  

 Ellenőrizze, hogy az új csomag és program megjelenik-e a a **csomagok** csomópontjának a **szoftverkönyvtár** munkaterületen.  

## <a name="create-a-package-and-program-from-a-package-definition-file"></a>Csomag és program létrehozása csomagdefiníciós fájlból  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **csomagok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **csomag létrehozása definícióból**.  

4.  Az a **Csomagdefiníció** oldalán a **csomag létrehozása a definíciós varázsló segítségével**, válasszon egy meglévő csomagdefiníciós fájlt, vagy válasszon **Tallózás** egy új csomagdefiníciós fájl megnyitásához. Egy új csomagdefiníciós fájl megadása után válassza ki azt a **Csomagdefiníció** listában, és válassza a **következő**.  

5.  Az a **forrásfájlok** lapon adja meg a csomaghoz és programhoz esetlegesen szükséges forrásfájlok adatait, és válassza a **következő**.  

6.  Ha a csomag forrásfájlokat igényel, a a **forrásmappa** csoportjában adja meg a helyet, ahol a forrásfájlokat olvashatók be, és válassza a **következő**.  

7.  Az a **összegzés** lapján tekintse át a végrehajtandó műveleteket megnyílik, és fejezze be a varázslót. Az új csomag és program megjelenik a **csomagok** csomópontjának a **szoftverkönyvtár** munkaterületen.  

 További információ a csomagdefiníciós fájlok: [információk a csomagdefiníciós fájlformátumról](/sccm/apps/deploy-use/packages-and-programs#about-the-package-definition-file-format) ebben a témakörben.  

##  <a name="deploy-packages-and-programs"></a>Csomagok és programok központi telepítése  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **csomagok**.  

2.  Válassza ki a csomagot, amelyet szeretne telepíteni, majd a a **Home** lapján a **telepítési** csoportjában válassza ki **telepítés**.  

3.  Az a **általános** oldalán a **szoftver központi telepítése varázsló**, adja meg a csomag nevét, és telepíti, a gyűjteményt, amelyhez a csomag és program és opcionálisan megjegyzéseket is fűzhet a központi telepítés központi telepítését kívánja használni kívánt programot.  

     Válassza **A gyűjteményhez társított alapértelmezett terjesztésipont-csoportok használata** lehetőséget, ha a csomag tartalmát a gyűjtemény alapértelmezett terjesztésipont-csoportján kívánja tárolni. Ha Ön nem társította a kijelölt gyűjteményt egy terjesztésipont-csoportba, ez a beállítás nem érhető el.  

4.  Az a **tartalom** lapon, válassza ki **Hozzáadás**, majd válassza ki a terjesztési pontokat vagy terjesztésipont-csoportokat, amelyre a csomaghoz és programhoz társított tartalmat a telepíteni kívánt.  

5.  Az a **központi telepítési beállítások** lapon válassza ki a központi telepítés célját, és adja meg a beállításokat az ébresztési csomagok és a forgalmi díjas kapcsolatokhoz:  

    -   **Cél**: A következő lehetőségek közül választhat:  

        -   **Rendelkezésre álló**: Ha egy felhasználó számára telepítik az alkalmazást, a felhasználó megkeresheti a közzétett csomagot és programot az alkalmazáskatalógusban, és igény szerint kérheti. Ha a csomag és program központi telepítése egy eszközön, a felhasználó a Szoftverközpontban látja, és igény szerint telepítheti.  

        -   **Szükséges**: A csomag és program automatikus, központi telepítése a konfigurált ütemezésnek megfelelően. A felhasználó azonban nyomon követheti a csomag és program központi telepítésének állapotát, és telepítheti azt a határidő előtt a Szoftverközpontból.  

    -   **Az ébresztési csomagok küldése**: Ha a központi telepítési céllal van megadva **szükséges** és ezt a lehetőséget választja, a ébresztési csomagot küld a rendszer számítógépekre felébressze a telepítési határidő lejártakor alvó állapotból a számítógépet a központi telepítés előtt. E lehetőség használatához a számítógépeken be kell állítani a hálózati ébresztést.  

    -  **Annak engedélyezése, hogy az ügyfelek mért internetkapcsolatot használjanak a tartalom letöltésére, miután elérkezett a telepítés határideje költségnövekedéssel járhat**: Válassza ki, ha ez szükséges.  

    > [!NOTE]  
    >  Az **Előzetes központi telepítés a felhasználó elsődleges eszközén** beállítás csomag és program központi telepítésekor nem érhető el.  

6.  Az a **ütemezés** lapján konfigurálhatja, amikor az adott csomagot és programot kell telepíteni vagy elérhetővé tenni az ügyféleszközök.  

     Ezen a lapon beállítások változhatnak attól függően, hogy a központi telepítés céljának beállítása **elérhető** vagy **szükséges**.  

7.  Ha a központi telepítési céllal van megadva **szükséges**, a program újrafuttatási viselkedését az **Újrafuttatási viselkedés** legördülő menü. Az alábbi lehetőségek közül választhat:  

    |Újrafuttatási viselkedés|További információ|  
    |--------------------|----------------------|  
    |Soha ne fusson újra a központilag telepített program|A program nem futtatható az ügyfélen, még akkor is, ha a program eredeti futása sikertelen volt, vagy ha a programfájlok megváltoztak.|  
    |Mindig fusson újra a program|A program mindig újra fut az ügyfélen, ha a központi telepítés ütemezve van, még akkor is, ha korábban már sikeresen futott. Ez akkor lehet hasznos, ha ismétlődő központi telepítéseket használ, amelyekben a program rendszeresen frissül, például víruskereső szoftverek esetén.|  
    |Újrafuttatás, ha az előző próbálkozás sikertelen volt|A program akkor fut újra, ha a központi telepítés ütemezve van, csak akkor, ha a futtatására tett előző kísérlet sikertelen volt.|  
    |Újrafuttatás, ha az előző próbálkozás sikeres volt|A program akkor fut újra, csak akkor, ha azt korábban már sikeresen futott az ügyfélen. Ez akkor hasznos, ha ismétlődő hirdetményeket használ, amelyekben a program rendszeresen frissül, és amelyekben minden frissítés egy korábbi frissítés sikeres telepítését igényli.|  

8. A **Felhasználói élmény** lapon adja meg a következő adatokat:  

    -   **A felhasználók számára a program hozzárendelésektől**: Ha engedélyezve van, felhasználók telepíthetik a szoftvert a Szoftverközpontból ütemezett telepítési időpontoktól függetlenül.  

    -   **Szoftvertelepítés**: Lehetővé teszi, hogy a szoftver telepítése a beállított karbantartási időszakokon kívül történjen.  

    -   **Rendszer újraindítása (Ha a telepítés befejezéséhez szükséges)**: A Szoftvertelepítés befejezéséhez eszköz újraindítása szükséges, ha engedélyezi ezt a beállított karbantartási időszakokon kívül megtörténjen.  

    -   **Embedded-eszközök**: Amikor Windows Embedded-eszközökre, amelyek az engedélyezett írási szűrőkkel csomagokat és programokat telepít, megadhatja, hogy csomagok és programok telepíteni az ideiglenes rétegen történjen, és véglegesítse változások később. Alternatív megoldásként a módosítások véglegesítéséhez, a telepítési határidő vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő vagy karbantartási időszakban véglegesíti, újraindításra szükség, és a változtatások megmaradnak az eszközön.  

        > [!NOTE]  
        >  Amikor egy csomagot és programot telepít egy Windows Embedded rendszerű eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal. Hogyan karbantartási időszakok használata, amikor Windows Embedded-eszközökre telepít csomagokat és programokat kapcsolatos további információkért lásd: [Windows Embedded alkalmazások létrehozása](../../apps/get-started/creating-windows-embedded-applications.md).  

9. A **Terjesztési pontok** lapon adja meg a következő adatokat:  

    -   **Telepítési lehetőségek**: Adja meg a műveleteket hajtson végre egy ügyfél futtatásához. Megadhat viselkedést arra az esetre, ha az ügyfél gyors hálózathatáron belül van, vagy ha lassú vagy nem megbízható hálózathatáron belül van.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: A beállítással úgy csökkenthető a hálózat terhelése így az ügyfelek egyéb ügyfelekről, amelyek már letöltötték és gyorsítótárba helyezték a tartalmat a hálózaton. Ez a beállítás a Windows BranchCache szolgáltatást használja, és Windows Vista SP2 vagy újabb operációs rendszerű számítógépeken használható.  

    -   **Az ügyfelek számára a tartalom tartalék forráshelyének engedélyezése**:  

        -  **1610 rendszernél korábbi verziókban**: Kiválaszthatja a **tartalék forráshely engedélyezése a tartalom jelölőnégyzetet** az ezeken a határcsoportokon kívüli ügyfelek használják a terjesztési csoportok pont a tartalom forráshelyeként Ha más terjesztési pontok nem érhetők el.

        - **1610 és újabb verzióit**: Már nem konfigurálható **tartalék forráshely engedélyezése a tartalom**.  Ehelyett konfigurálnia a határcsoportokat, amelyek meghatározzák, amikor egy ügyfél akkor kezdhető meg egy érvényes tartalomforrás helye további határcsoportjainak kereséséhez közötti kapcsolatokat.

10. Az a **összegzés** lapján tekintse át a végrehajtandó műveleteket megnyílik, és fejezze be a varázslót.  

     A központi telepítést megtekintheti a **Figyelés** munkaterület **Központi telepítések** csomópontjában a csomagok központi telepítése lap részletező ablaktábláján, amikor kijelöli a központi telepítést. További információkért lásd: [csomagok és programok figyelése](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs) ebben a témakörben.  

> [!IMPORTANT]  
>  Ha a beállítás konfigurálva **program futtatása a terjesztési pontról** a a **terjesztési pontok** oldalán a **szoftver központi telepítése varázsló**, ne törölje a beállítást **a csomag tartalmának másolása a terjesztési pontok egy csomagmegosztásába** ez ugyanis a csomag nem lesz futtatható a terjesztési pontokról.  

##  <a name="monitor-packages-and-programs"></a>A figyelő csomagok és programok  
 Csomag és program központi telepítéseinek figyeléséhez, mint az alkalmazások figyeléséhez használt ugyanezeket az eljárásokat használhatja [alkalmazások figyeléséhez](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Csomagok és programok is számos olyan beépített jelentéseket, amelyek lehetővé teszik a csomagok és programok központi telepítési állapotára vonatkozó információk megfigyelésére. Ezek a jelentések a **Szoftverterjesztés – Csomagok és programok** és a **Szoftverterjesztés – Csomag és program központi telepítési állapot** jelentéskategóriába tartoznak.  

 Jelentéskészítés a Configuration Managerben konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

##  <a name="manage-packages-and-programs"></a>Csomagok és programok kezelése  
 A a **szoftverkönyvtár** munkaterületet, bontsa ki a **Alkalmazáskezelés**, válassza a **csomagok**, válassza ki a kezelni kívánt csomagot, és válassza ki a kezelési feladatot az alábbi táblázatban:  

|Feladat|További információ|  
|----------|----------------------|  
|**Előkészített tartalom fájljának létrehozása**|Megnyitja a **manuálisan előkészített tartalomfájl létrehozása varázsló**, amely lehetővé teszi, hogy hozzon létre egy más helyeken manuálisan importált lehet csomagtartalmat tartalmazó fájlt. Ez azokban az esetekben hasznos, melyekben alacsony a sávszélesség a helykiszolgáló és a terjesztési pont között.|  
|**Hozzon létre programot**|Megnyitja a **Program létrehozása varázsló**, amely lehetővé teszi, hogy hozzon létre egy új programot az adott csomaghoz.|  
|**Exportálásálás**|Megnyitja a **csomag exportálása varázsló**, amely lehetővé teszi egy fájlba exportálhatja a kiválasztott csomagot és annak tartalmát.<br /><br /> További információ a csomagok és programok importálásáról: [csomagok és programok létrehozása](/sccm/apps/deploy-use/packages-and-programs#create-packages-and-programs) ebben a témakörben.|  
|**Telepítés**|Megnyitja a **szoftver központi telepítése varázsló**, amely lehetővé teszi a kiválasztott csomag és program központi telepítése egy gyűjteménybe. További információkért lásd: [csomagok és programok központi](/sccm/apps/deploy-use/packages-and-programs#deploy-packages-and-programs) ebben a témakörben.|  
|**Tartalom terjesztése**|Megnyitja a **a tartalom terjesztése varázsló**, amely lehetővé teszi, hogy a csomag és program kiválasztott terjesztési pontokat vagy terjesztésipont-csoportokhoz társított tartalom küldése.|  
|**Terjesztési pontok frissítése**|A terjesztési pontok frissítése a kiválasztott csomag és program legújabb tartalmával.|  

##  <a name="about-the-package-definition-file-format"></a>Információk a csomagdefiníciós fájlformátumról  
 Csomagdefiníciós fájlok olyan parancsfájlok, melyekkel automatizálhatja a csomagok és programok létrehozását a Configuration Managerrel. Minden Configuration Manager létre kell hoznia egy csomagot és programot, kivéve a csomag forrásfájljainak helyét információkat biztosítanak. Minden csomagdefiníciós fájl egy ASCII vagy UTF-8 kódolású szövegfájl, amely a .ini fájlformátumot használja, és tartalmazza a következő szakaszok:  

###  <a name="pdf"></a>[PDF]  
 Ez a szakasz azonosítja a fájlt csomagdefiníciós fájlként. A következő adatokat tartalmazza:  

-   **Verzió**: Adja meg a csomagdefiníciós fájlformátum a fájl által használt verzióját. Ez megfelel a telepített System Management Server (SMS) vagy a Configuration Manager, amelyhez a fájl készült. A bejegyzés megadása kötelező.  

###  <a name="package-definition"></a>[Package Definition]  
 Adja meg a csomag és program tulajdonságait. A következő adatokat tartalmazza:  

-   **Név**: A a csomag neve, mely legfeljebb 50 karakter hosszú lehet.  

-   **Verzió** (nem kötelező): A a csomag verziója, mely legfeljebb 32 karakter hosszú lehet.  

-   **Ikon** (nem kötelező): A csomag telepítéséhez használni kívánt ikont tartalmazó fájl. Ha meg van adva, erre az ikonra az alapértelmezett csomagikon a Configuration Manager konzol váltja fel.

-   **A Publisher**: Az a csomag közzétevője, mely legfeljebb 32 karakter hosszú lehet.

-   **Nyelvi**: A nyelvi verzióját a csomagot, mely legfeljebb 32 karakter hosszú lehet.

-   **Megjegyzés** (nem kötelező): Megjegyzés a csomagot, legfeljebb 127 karakter hosszú lehet.

-   **ContainsNoFiles**: Ez a bejegyzés azt jelzi, hogy-e forrás társítva a csomaghoz.  

-   **Programok**: Az adott csomaghoz definiált programok. Minden egyes program neve az adott csomagdefiníciós fájl egy **[Program]** szakaszának felel meg.  

     Például:  

     `Programs=Typical, Custom, Uninstall`  

-   **MIFFileName**: Legfeljebb 50 karakter hosszú lehet a csomag állapotát tartalmazó Management Information Format (MIF) fájl neve.  

-   **MIFName**: Legfeljebb 50 karakter hosszú lehet (a MIF egyeztetéséhez), a csomag nevét.  

-   **MIFVersion**: Legfeljebb 32 karakter hosszú lehet (a MIF egyeztetéséhez), a csomag verziószámát.  

-   **MIFPublisher**: Legfeljebb 32 karakter hosszú lehet (a MIF egyeztetéséhez), a csomag szoftverkiadója.  

###  <a name="program"></a>[Program]  
 Minden egyes megadott program a **programok** bejegyzést a **[Package Definition]** , a csomagdefiníciós fájl tartalmaznia kell egy [Program] szakaszt, amely meghatározza az adott programot. Minden Program szakasz a következő adatokat tartalmazza:  

-   **Név**: A program, legfeljebb 50 karakter hosszú lehet neve. Ennek a bejegyzésnek a csomagon belül egyedinek kell lennie. Ezt a nevet a rendszer hirdetmények definiálásakor használja. Az ügyfélszámítógépeken a program neve a Vezérlőpult **Hirdetett programok futtatása** szakaszában jelenik meg.  

-   **Ikon** (nem kötelező): Adja meg az ehhez a programhoz használni kívánt ikont tartalmazó fájlt. Ha meg van adva, erre az ikonra a felváltja az alapértelmezett programikon a Configuration Manager konzolon, és az ügyfélszámítógépeken a program hirdetésekor jelenik meg.

-   **Megjegyzés** (nem kötelező): A program, legfeljebb 127 karakter hosszú lehet megjegyzést.

-   **CommandLine**: Adja meg a parancssor a program, legfeljebb 127 karakter hosszú lehet. A parancs a csomag forrásmappájához képest relatív.

-   **StartIn**: Adja meg, legfeljebb 127 karakter hosszú lehet a program munkamappáját. Ez a bejegyzés lehet abszolút elérési utat az ügyfélszámítógépen vagy a csomag forrásmappájához képest relatív elérési utat.

-   **Futtatás**: Adja meg a program módját, amelyben a program futtatása. A megadható értékek a következők: **Minimized** (Kisméretű) **Maximized** (Teljes méretű) és **Hidden** (Rejtett). Ha ez a bejegyzés nincs megadva, a program normál üzemmódban fut.  

-   **AfterRunning**: Adja meg az esetleges további műveleteket a program sikeres végrehajtása után következik be. Az elérhető lehetőségek a következők: **SMSRestart**, **ProgramRestart** és **SMSLogoff**. Ha ez a bejegyzés nincs megadva, akkor a program nem további műveletet futtatni.  

-   **EstimatedDiskSpace**: Adja meg a lemezterület méretét, amelyre a szoftvernek szüksége van a számítógépen történő futtatásával. Ehhez az **Unknown** (Ismeretlen) értéket (ez az alapértelmezett beállítás), vagy egy nullánál nem kisebb egész számot adhat meg. Ha megad egy értéket, az érték mértékegységét is meg kell adnia.  

     Például:  

     `EstimatedDiskSpace=38MB`  

-   **EstimatedRunTime**: Adja meg a becsült időtartama (perc) várt a program futtatásához az ügyfélszámítógépen. Ehhez az **Unknown** (Ismeretlen) értéket (ez az alapértelmezett beállítás), vagy egy nullánál nem kisebb egész számot adhat meg.  

     Például:  

     `EstimatedRunTime=25`  

-   **SupportedClients**: Adja meg a processzorok és operációs rendszerek, amelyeken ez a program fut. A megadott platformokat vesszővel kell elválasztani. Ha ez a bejegyzés nincs megadva, támogatott platformok ellenőrzése le van tiltva a program.  

-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Adja meg a kezdő-tartományának a megadott operációs rendszerek verziószámai a **SupportedClients** bejegyzés.  

     Például:  

    ```  
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999   
    ```  

-   **AdditionalProgramRequirements** (nem kötelező): Adja meg a bármely egyéb információ vagy az ügyfélszámítógépekre, legfeljebb 127 karakter hosszú lehet vonatkozó követelmény.

-   **CanRunWhen**: Adja meg a felhasználói állapotot, a program igényel az ügyfélszámítógépen futtatásához. Az elérhető értékek a következők: **UserLoggedOn** (Van bejelentkezett felhasználó), **NoUserLoggedOn** (Nincs bejelentkezett felhasználó) és **AnyUserStatus** (Bármely felhasználói állapot). Az alapértelmezett érték **UserLoggedOn** (Van bejelentkezett felhasználó).  

-   **UserInputRequired**: Adja meg, hogy a program igényel-e a felhasználói. A lehetséges értékek a következők: **True** (Igaz) és **False** (Hamis). Az alapértelmezett érték **True** (Igaz). A bejegyzés értéke **False** lesz, ha a **CanRunWhen** bejegyzés értéke nem **UserLoggedOn**.  

-   **AdminRightsRequired**: Adja meg, hogy a program futtatásához a számítógépen rendszergazdai hitelesítő adatokat igényel-e. A lehetséges értékek a következők: **True** (Igaz) és **False** (Hamis). Az alapértelmezett érték **False** (Hamis). A bejegyzés értéke **True** (Igaz), ha a **CanRunWhen** bejegyzés értéke nem **UserLoggedOn**.  

-   **UseInstallAccount**: Adja meg, hogy a program az ügyfél-telepítési fiókot használja, amikor fut az ügyfélszámítógépeken. Alapértelmezés szerint ez az érték **False** (Hamis). Ez az érték akkor is **False** (Hamis) lesz, ha a **CanRunWhen** értéke **UserLoggedOn** (Van bejelentkezett felhasználó).  

-   **DriveLetterConnection**: Adja meg, hogy a program igényel-e a terjesztési ponton található csomagfájlokhoz egy meghajtóbetűjel kapcsolódjon. A megadható értékek **True7** (Igaz) és **False** (Hamis). Az alapértelmezett érték **hamis**, amely lehetővé teszi, hogy a program egy univerzális elnevezési konvenció (UNC) szerinti kapcsolatot használjon. Ha ez az érték beállítása **igaz**, a következő elérhető meghajtóbetűjelet használja (a Z:-tól visszafelé haladva).  

-   **SpecifyDrive** (nem kötelező): Adja meg, hogy a terjesztési ponton található csomagfájlokhoz való kapcsolódását igényli a program egy meghajtóbetűjelet. Ez az meghatározás kényszeríti a megadott meghajtóbetűjel használatát a terjesztési pontokhoz való ügyfélkapcsolatokban.

-   **ReconnectDriveAtLogon**: Adja meg, hogy a számítógép újracsatlakozik a terjesztési pontot a felhasználó bejelentkezésekor. A lehetséges értékek a következők: **True** (Igaz) és **False** (Hamis). Az alapértelmezett érték **False** (Hamis).  

-   **DependentProgram**: Adjon meg egy programot a csomag, amely az aktuális program előtt kell futtatni. A bejegyzés a **DependentProgram**=<**ProgramNeve>** formátumot használja, ahol a **<ProgramNeve>\>** az adott, a csomagdefiníciós fájlban lévő program **Name** bejegyzése. Ha nincsenek függő programok, hagyja üresen ezt a bejegyzést.  

     Például:  

     DependentProgram=Admin  
    DependentProgram=  

-   **Hozzárendelés**: Adja meg, hogy a program hogyan van hozzárendelve felhasználók. Az érték lehet: **FirstUser** (csak az első felhasználó, aki bejelentkezik az ügyfél futtatja a programot) vagy **EveryUser** (minden felhasználó számára kérelmezni futtatja a programot). Ha a **CanRunWhen** értéke nem **UserLoggedOn** (Van bejelentkezett felhasználó), akkor a bejegyzés értéke **FirstUser** (Első felhasználó) lesz.  

-   **Letiltott**: Adja meg, hogy a program hirdethető-e az ügyfelek számára. A lehetséges értékek a következők: **True** (Igaz) és **False** (Hamis). Az alapértelmezett érték **False** (Hamis).  

