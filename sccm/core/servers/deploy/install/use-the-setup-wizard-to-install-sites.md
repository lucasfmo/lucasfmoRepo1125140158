---
title: "A telepítő varázsló |} Microsoft Docs"
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f703376-5f2c-4fd2-8209-7028c931ddc7
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 14b4172ad713a3981b8a5abe182405e271d78c26
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-setup-wizard-to-install-system-center-configuration-manager-sites"></a>A telepítővarázsló segítségével a System Center Configuration Manager-helyek telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Az interaktív felhasználói felület használatával telepít egy új System Center Configuration Manager-hely, használhatja a Configuration Manager telepítő varázsló (setup.exe). A varázsló támogatja az elsődleges hely vagy központi adminisztrációs hely telepítése. A varázslót is használhatja [próbaverzió frissítése](../../../../core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md) a Configuration Manager teljes mértékben licencelt verzióra. Ha nem szeretné használni a varázslóban, használhatja az [telepítési parancsfájl](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md) és a felügyelet nélküli parancssori telepítés futtatása.

Másodlagos hely telepítéséhez telepítenie kell a helyet a Configuration Manager konzolon. A másodlagos helyek nem támogatják a parancssori parancsfájlból történő telepítést.

## <a name="bkmk_primary"></a>A központi adminisztrációs hely vagy elsődleges hely telepítése
Az alábbi eljárással a központi adminisztrációs hely vagy elsődleges hely telepítése vagy frissítése a próbaverziójának teljes mértékben licencelt Configuration Manager-hely.   

A telepítés megkezdése előtt ismernie kell a a részleteket a következő cikkeket:
 -  [Felkészülés a helyek telepítése](../../../../core/servers/deploy/install/prepare-to-install-sites.md)
 -  [Helyek telepítésének előfeltételei](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md)

Ha telepít egy központi adminisztrációs hely helybővítés részeként, tekintse át a [önálló elsődleges hely kibővítése](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) a témakör az alábbi eljárás használata előtt.

### <a name="bkmk_installpri"></a>Elsődleges vagy központi adminisztrációs hely telepítése

1.  A számítógépre, amelyre a hely telepítését, futtassa  **&lt;InstallationMedia\>\SMSSETUP\BIN\X64\Setup.exe** elindítani a **System Center Configuration Manager telepítő varázsló**.  

    > [!NOTE]  
    > A központi adminisztrációs hely önálló elsődleges hely kibővítéséhez telepítésekor, vagy új gyermek elsődleges hely telepítése egy már létező hierarchiában, a meglévő webhelyet vagy webhelyeket verziójának megfelelő telepítési adathordozó (Forrásfájlok) kell használnia. Ha telepítette a konzolon belüli frissítések, amelyek megváltoztak a már telepített helyeken verziója, az eredeti telepítési adathordozót ne használjon. Ehelyett használja a forrásfájlok a [CD-ről. Legújabb mappa](../../../../core/servers/manage/the-cd.latest-folder.md) frissített hely. A Configuration Manager megköveteli, hogy a meglévő helyet, amely az új hely kapcsolódni fog verziójának megfelelő forrásfájlokat használja.  

2.  Az a **előkészületek** lapon, válassza ki **következő**.  

3.  Az a **bevezetés** lapon, válassza ki a telepítendő hely típusát:  

    -   **Központi adminisztrációs hely**, az első hely új hierarchia, vagy egy önálló elsődleges hely kibővítésekor:  

        Válassza ki **Configuration Manager központi adminisztrációs hely telepítése**.  

         Egy későbbi lépésében ezt az eljárást felkínálja a választási lehetőség egy központi adminisztrációs hely telepítése egy új hierarchia első helyeként, vagy egy központi adminisztrációs helyet egy önálló elsődleges hely kibővítéséhez telepíti.  

    -    **Elsődleges hely**, egy önálló elsődleges helyet, amely egy új hierarchia első helyének vagy elsődleges gyermek:  

        Válassza ki **Configuration Manager elsődleges hely telepítése**.  

        > [!TIP]  
        > Általában csak a beállítást választja **használja a szokásos telepítési beállítások önálló elsődleges helyhez** kívánt önálló elsődleges hely telepítése egy tesztkörnyezetben. Ha ezt a beállítást, a telepítő:  

        > -   Automatikusan konfigurálja a hely önálló elsődleges helyként.  
        > -   Az alapértelmezett telepítési útvonalon.  
        > -   A Helyadatbázis az SQL Server alapértelmezett példányának helyi telepítését használja.  
        > -   A felügyeleti pont és terjesztési pontot telepít a helykiszolgáló számítógépén.  
        > -   Konfigurálja a hely az angol nyelvet és az elsődleges helykiszolgáló operációs rendszerének megjelenítési nyelvét, ha szerepel a Configuration Manager által támogatott nyelveket.  

4.  Az a **termékkulcs** lap:
    - Válassza ki, hogy a Configuration Manager próbaverzióját vagy licenccel rendelkező kiadását.  

      -   Ha licencelt kiadást választ, adja meg a termékkulcsot, és válassza a **következő**.  

      -   Ha próbaverziót választ ki, válassza a **következő**. (Frissítheti próbaverziót később teljes telepítésre.)  
    - 2016. októberi kiadása verzió 1606 alapszintű verziót tartalmazó adathordozó a System Center Configuration Manager-kezdve is megadhat a frissítési garancia szerződés lejárati dátuma. Ezen az oldalon lehetősége van a adja meg a **Software Assurance lejárati dátum** a dátumnak kényelmes ne feledje, hogy a licencelési feltételeit. Ha nem adja meg a telepítés során, adja meg azt később a Configuration Manager konzolon.

      > [!NOTE]   
      > A Microsoft nem ellenőrzi a megadott lejárati dátum, és ez a dátum nem használjuk a licenc-ellenőrzéshez. Ehelyett használhatja a lejárati dátum emlékeztetőként. Ez akkor hasznos, mert a Configuration Manager rendszeresen ellenőrzi a kínált online új szoftverfrissítések – és a megbízhatósági szoftverlicencek állapotának aktuális kell lennie, hogy Ön jogosult a további frissítések használatára.    

      További információkért lásd: [licencelés és a System Center Configuration Manager az](/sccm/core/understand/learn-more-editions).

5.  Az a **Microsoft szoftverlicenc-szerződés** lapon olvassa el és fogadja el a licencfeltételeket.  

6.  Az a **előfeltételként szükséges licencek** lapon olvassa el és fogadja el az előfeltételként szükséges szoftverek licencfeltételeit. A telepítő letölti és automatikusan telepíti a szoftvert a helyrendszereken vagy ügyfeleken, van szükség. A listák ellenőriznie kell, mielőtt továbblépne, a következő oldalra.  

7.  Az a **előfeltételként szükséges letöltések** csoportjában adja meg, hogy a Telepítő letöltse-e a legújabb, előfeltételként szükséges újraterjeszthető fájlokat az internetről, vagy a korábban letöltött fájlokat használja:  

    -   Ha azt szeretné, hogy a telepítő ekkor letöltse a fájlokat, jelölje ki a **szükséges fájlok letöltése** adja meg a fájlok tárolási helyét.  

    -   Ha korábban letöltötte a fájlokat a [a telepítő letöltési segédprogramja](../../../../core/servers/deploy/install/setup-downloader.md), jelölje be **korábban letöltött fájlok használata** és adja meg a letöltési mappát.  

        > [!TIP]  
        > Korábban letöltött fájlok használata esetén győződjön meg arról, hogy a letöltési mappa elérési útját tartalmazza-e a fájlok legújabb verziója.  

8.  Az a **kiszolgáló nyelvének kiválasztása** lapon, válassza ki a Configuration Manager konzol és a jelentésekhez elérhető nyelveket. (Angol alapértelmezés szerint engedélyezett, és nem távolítható el.)  

9. Az a **ügyfélnyelv kiválasztása** lapon, válassza ki azokat nyelveket, amelyek elérhetők az ügyfélszámítógépek számára, és adja meg, hogy az összes ügyfélnyelvet a mobileszközügyfelekhez engedélyezése. (Angol alapértelmezés szerint engedélyezett, és nem távolítható el.)  

    > [!IMPORTANT]  
    > A központi adminisztrációs hely használata esetén győződjön meg arról, hogy konfigurálnia a központi adminisztrációs helyen ügyfélnyelveket tartalmazza-e az összes ügyfélnyelvet, egyes gyermek elsődleges helyeken konfigurált. Ennek az az oka ügyfeleinek telepítését a terjesztési pontokról, amelyek hozzáférhetnek az ügyfél nyelveit a legfelső szintű helyről, amíg az ügyfelek a felügyeleti pont telepítését, amelyek hozzáférhetnek az ügyfél nyelveit a hozzájuk rendelt elsődleges hely.  

10. Az a **hely és telepítés beállításai** lapján adja meg az új hely telepítése a következőket:  

    -   **Helykód:** [A hierarchiában minden helykódnak egyedinek kell lennie](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_sitecodes) és három alfanumerikus számjegyből (A – Z) és 0 – 9 áll. Mivel a Helykód mappanevekben szerepel, ne használja a Windows számára fenntartott nevek a helyhez, beleértve:    
        -   AUX  
        -   CON    
        -   NUL    
        -   PRN    
        -   SMS  

        > [!NOTE]  
        > A telepítő nem ellenőrizni, hogy a megadott Helykód már használatban van, vagy egy fenntartott név rendelkezik.  

    -   **Hely neve:** Minden helyhez erre a rövid névre, amely segíthet a hely azonosításában van szükség.  

    -   **Telepítési mappa:** Ez az a Configuration Manager telepítésének elérési útja. A hely nem módosítható, a hely telepítése után. Az elérési út nem tartalmazhat Unicode-karaktereket vagy záró szóközöket.  

11. Az a **Helytelepítés** lapon, a forgatókönyvének megfelelő alábbi beállítást használja:  

    -   **A központi adminisztrációs helyet telepítek:**  

         Az a **központi adminisztrációs hely telepítése** lapon jelölje be **új hierarchia első helyének telepítése**, és válassza a **tovább** a folytatáshoz.  

    -   **Önálló elsődleges bővítek egy központi adminisztrációs hellyel rendelkező hierarchiára:**  

         A a **központi adminisztrációs hely telepítése** lapon jelölje be **hierarchiává bővít egy meglévő önálló elsődleges**, adja meg az önálló elsődleges hely kiszolgálójának teljes Tartománynevét, és válassza a **tovább** a folytatáshoz.  

         Az új központi adminisztrációs hely telepítéséhez használt adathordozónak meg kell egyeznie az elsődleges hely verziójával.  

    -   **Egy önálló elsődleges helyet telepítek:**  

         Az a **elsődleges hely telepítése** lapon jelölje be **az elsődleges hely telepítése önálló helyként**, és válassza a **következő**.  

    -   **A gyermek elsődleges helyet telepítek:**  

         Az a **elsődleges hely telepítése** lapon jelölje be **az elsődleges helyet csatolja egy meglévő hierarchiához**, adja meg a központi adminisztrációs hely teljes Tartománynevét, és válassza a **következő**.  

12. Az a **adatbázis-információ** lapján adja meg a következőket:  

    -   **SQL Server neve (FQDN):** Alapértelmezés szerint ez értéke lehet a helykiszolgáló számítógépén.  

    -   **Példány neve:** Ez alapértelmezés szerint az üres. Az alapértelmezett SQL-példányt használ a helykiszolgáló számítógépén.  

    -   **Adatbázis neve:** Alapértelmezés szerint a beállított érték CM_&lt;Helykód\>. Szabadon, akkor adjon meg másik nevet.  

    -   **Service Broker-Port:** Alapértelmezés szerint ez használatára van beállítva az alapértelmezett SQL Server Service Broker (SSB) port a 4022-es. SQL útján kommunikálnak közvetlenül a más helyeken lévő Helyadatbázis használja azt.  

13. A második **adatbázis-információ** lapján megadhatja, hogy az SQL Server adatfájljának és a naplófájl a Helyadatbázis nem alapértelmezett helyét:  

    -   Az SQL Server alapértelmezett fájlhelyek vannak megadva.  

    -   A lehetőség nem alapértelmezett fájlhelyek választására nem érhető el, ha az SQL Server-fürtöt használ.  

    -   Az előfeltétel-ellenőrző nem ellenőrzést futtatni a szabad lemezterület a nem alapértelmezett fájlhelyeket.  

14. Az a **SMS-szolgáltató beállításai** lapon adja meg a teljes Tartománynevet a kiszolgálóhoz, amelyen az SMS-szolgáltatót telepíteni szeretné.  

    -   Alapértelmezés szerint a helykiszolgáló van megadva.  

    -   A hely telepítése után további SMS-szolgáltatókat konfigurálhatja.  

15. Az a **ügyfélszámítógép kommunikációs beállításai** lapon, válassza ki az e állítani az összes helyrendszer csak HTTPS-kommunikációt fogad az ügyfelektől, vagy a kommunikációs módszer konfigurálását az egyes helyrendszer-szerepkör.  

    Ha bejelöli **összes helyrendszerszerepkör csak HTTPS-kommunikációt fogad az ügyfelek**, az ügyfélszámítógépnek érvényes PKI-tanúsítványt az ügyfél-hitelesítéshez kell rendelkeznie. További információ a nyilvános kulcsú infrastruktúra tanúsítványainak követelményeiről: [PKI-tanúsítványkövetelmények a Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    > [!NOTE]  
    > Ez a lépés csak akkor érvényes, az elsődleges hely telepítésekor. Ha egy központi adminisztrációs helyet telepít, hagyja ki ezt a lépést.  

16. Az a **Helyrendszerszerepkörök** lapon, válassza ki, hogy a felügyeleti ponttal vagy terjesztési ponton. Az egyes szerepkörökhöz, a telepítővel telepíteni kívánt:  

    -   Meg kell adnia a **FQDN** a számítógép, amely a szerepkört, és válassza ki az ügyfél, hogy a kiszolgáló támogatja (HTTP vagy HTTPS) kapcsolódási módszert.  

    -   Ha a kiválasztott **összes helyrendszerszerepkör csak HTTPS-kommunikációt fogad az ügyfelek** az előző lapon, az ügyfél-kapcsolódási beállítások automatikusan HTTPS-hez lesznek konfigurálva, és nem módosítható, kivéve, ha visszalép, és módosítsa a beállítást.  

    > [!NOTE]  
    > Ez a lépés csak akkor érvényes, az elsődleges hely telepítésekor. Ha egy központi adminisztrációs helyet telepít, hagyja ki ezt a lépést.  

    > [!NOTE]  
    > Helyrendszerszerepkörök telepítéséhez a telepítő használja a **rendszerfiók telepítési hely**. Alapértelmezés szerint ez az elsődleges hely számítógépfiókját használja. Ezt a fiókot egy távoli számítógépen a helyrendszerszerepkör telepítéséhez helyi rendszergazdának kell lennie. Ha ez a fiók nem rendelkezik a szükséges engedélyekkel, törölje a jelet a helyrendszer-szerepköröket, és később telepítse azokat a Configuration Manager konzolról, további fiókokat hely rendszer telepítési fiókok konfigurálása után.  

17. Az a **használati adatok** lapon tekintse át az adatokat a Microsoft által gyűjtött, és válassza a **következő**.  

18. A **Szolgáltatáskapcsolati pont beállítása** lap csak akkor áll rendelkezésre a telepítés során:  

    -   Amikor telepít egy önálló elsődleges helyet.  

    -   Amikor telepít egy központi adminisztrációs helyhez.  

    > [!NOTE]  
    > A gyermek elsődleges helyek telepítése, hagyja ki ezt a lépést (Ez a lap nem érhető el).  

     Ha a központi adminisztrációs hely telepítése helybővítés részeként, és ez a szerepkör már telepítve van az önálló elsődleges helyen, el kell távolítania ezt a szerepkört az önálló elsődleges helyről. Ezt a szerepkört csak egy példánya engedélyezett a hierarchiában, és csak a hierarchia legfelső szintű helyén.  

     Miután kiválasztotta a konfigurációt a **szolgáltatáskapcsolódási pont**, válassza a **tovább**. (A telepítés után módosíthatja ezt a konfigurációt a a Configuration Manager konzolról.)  

19. Az a **beállítások összegzése** lapján tekintse át a beállításokat, amelyek a kijelölt. Ha elkészült, válassza ki a **következő** az előfeltétel-ellenőrző indításához.  

20. Az a **Előfeltételek telepítésének ellenőrzése** lapon azonosítható problémák vannak felsorolva.  

    -   Ha az előfeltétel-ellenőrző problémát talál, válasszon ki egy elemet a listában a probléma megoldásával kapcsolatos részletekért.  

    -   Fel kell oldania az egyes elemek állapotú **sikertelen** továbbra is a hely telepítése előtt. Állapotú elemek **figyelmeztetés** fel kell oldani, de azok nem blokkolja a hely telepítését.  

    -   Problémák megoldása után válassza ki a **ellenőrzés futtatása** újra futtatni az előfeltétel-ellenőrzőt.  

     Ha az előfeltétel-ellenőrző fut, és nem ellenőrzi kap egy **sikertelen** állapota, dönthet úgy, **telepítés megkezdése** a hely telepítésének indításához.  

    > [!TIP]  
    > A varázslóban megadott visszajelzés mellett található előfeltétel-hibákkal kapcsolatos további információk megtekintésekor a **ConfigMgrPrereq.log** fájl a számítógép az telepítjük a rendszermeghajtó gyökérmappájában található. Telepítés előfeltételeinek szabályait és leírásukat listájáért lásd: [lista az Előfeltételek ellenőrzése a System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

21. Az a **telepítési** lapon a telepítés állapota látható. A központi helykiszolgáló telepítésének befejezésekor lehetőséget kell **Bezárás** a telepítési varázsló. A varázsló bezárásakor a telepítés és a kezdeti Helykonfigurációk a háttérben folytatódik.  

    -   Csatlakozhat a Configuration Manager konzol a helykiszolgáló telepítő befejezése előtt. Ez a konzol csak olvasásra csatlakozik, valamint lehetővé teszi, hogy megtekintheti az objektumokat és beállításokat, de nem végezhet módosításokat.  

    -   A telepítés után is csatlakoztathat egy konzolt, amelyek objektumokat és beállításokat szerkesztheti.  


## <a name="bkmk_expand"></a>Önálló elsődleges hely
Ha egy önálló elsődleges helyen telepített első helyként, lehetősége van a később bontsa ki, hogy a hely egy központi adminisztrációs hely telepítésével nagyobb hierarchiává.   

Amikor kibővít egy önálló elsődleges helyet, telepít egy új központi adminisztrációs helyet, amely a meglévő önálló elsődleges hely adatbázisát használja hivatkozásként. Az új központi adminisztrációs hely telepítése után az önálló elsődleges hely egy gyermek elsődleges hely funkcionál.

-   Csak egy önálló elsődleges helyet bővíthet ki új hierarchiába.  

-   Csak egy önálló elsődleges helyet bővíthet ki egy adott hierarchiába. Ez a beállítás nem használható további önálló elsődleges helyeket ugyanabba a hierarchiába csatlakozni. Ehelyett használja az áttelepítési adatok áttelepítéséhez egyik hierarchiából egy másik.  

-   Miután egy önálló helyet központi adminisztrációs hellyel rendelkező hierarchiává bővít, hozzáadhat további elsődleges gyermekhelyeket.  

-   Távolítsa el az elsődleges hely egy központi adminisztrációs hellyel rendelkező hierarchiára, el kell távolítania az elsődleges hely.  

Bontsa ki a helyet, használhatja a System Center Configuration Manager telepítő varázsló egy új központi adminisztrációs hely telepítéséhez a következő kikötésekkel:  

-   Telepítenie kell a központi adminisztrációs hely a Configuration Manager azonos verzióját használják, mint az önálló elsődleges helyen.  

-   Az a **bevezetés** lapján a telepítési varázsló egy központi adminisztrációs hely telepítése lehetőséget választotta. A telepítés későbbi szakaszában fogja választott egy meglévő önálló elsődleges hely kibővítéséhez.  

-   Amikor konfigurál a **ügyfélnyelv kiválasztása** lap az új központi adminisztrációs hely ugyanazokat az ügyfélnyelveket, vannak beállítva az önálló elsődleges helyen, most bővíteni kell választania.  

-   Az a **Helytelepítés** lap, az önálló elsődleges hely bővítésének lehetőséget választotta.  

Kibővít egy önálló elsődleges helyet, először tekintse meg a [hely bővítésének előfeltételei](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), majd az eljárás  *[elsődleges vagy központi adminisztrációs hely telepítése](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_installpri)*, ez a cikk a korábbi.


## <a name="bkmk_secondary"></a>Másodlagos hely telepítése
 A Configuration Manager konzol segítségével másodlagos helyet telepít.  

-   A konzol nem kapcsolódik az elsődleges hely, amely az új másodlagos hely szülőhelye lesz, ha a hely telepítéséhez a parancs replikálja az elsődleges hely helyes.  

-   A telepítés megkezdése előtt győződjön meg arról, hogy a felhasználói fiók rendelkezik-e a szükséges engedélyekkel, és, hogy a számítógépen az új másodlagos hely megfelel-e a szükséges előfeltételek maradéktalanul a másodlagos helykiszolgáló működik.  

-   A másodlagos hely telepítésekor a Configuration Manager konfigurálja az új hely az elsődleges szülőhelyen beállított ügyfél-kommunikációs portok használatára.  

### <a name="bkmk_installsecondary"></a>Másodlagos hely telepítése  


1.  A Configuration Manager-konzolon lépjen a **felügyeleti** > **Helykonfiguráció** > **helyek**. Válassza ki a helyet, amely az új másodlagos hely elsődleges szülőhelye lesz.  

2.  Válasszon **másodlagos hely létrehozása** elindítani a **másodlagos hely létrehozása varázsló**.  

3.  Az a **alapismeretek** lapon, győződjön meg arról, hogy az elsődleges hely jelenik a webhely, amelyet szeretne az új másodlagos hely szülőjeként. Válassza a **következő**.  

4.  Az a **általános** lapján adja meg a következőket:  

    -   **A Helykód**: A hierarchiában minden helykódnak kell lenniük, és három alfanumerikus számjegyből (A – Z) és 0 – 9 áll. Mivel a Helykód mappanevekben szerepel, ne használja a Windows számára fenntartott nevek a helyhez, beleértve:  

        -   AUX    
        -   CON    
        -   NUL    
        -   PRN  
        -   SMS  

       > [!NOTE]  
       > A telepítő nem ellenőrizni, hogy a megadott Helykód már használatban van, vagy egy fenntartott név esetén.  

    -   **Helykiszolgáló neve**: Ez az a kiszolgáló, ahol telepíti az új másodlagos hely teljes Tartományneve.  

    -   **Hely neve**: Minden helyhez erre a rövid névre, amely segíthet a hely azonosításában van szükség.  

    -   **Telepítési mappa**: Ez az a Configuration Manager telepítésének elérési útja. A hely nem módosítható, a hely telepítése után. Az elérési út nem tartalmazhat Unicode-karaktereket vagy záró szóközöket.  

    > [!IMPORTANT]  
    > Miután az adatok ezen a lapon adhatók meg, választhatja azt is **összegzése** az alapértelmezett beállításokat használja a másodlagos hely beállításainak hátralévő részére, és közvetlenül a **összegzése** a varázsló.  

    > -   Csak akkor használja ezt a beállítást, ha ismeri az alapértelmezett beállításokat a varázslóban, és ezeket a beállításokat szeretne használni.  
    > -   A határcsoportok nem a terjesztési ponthoz tartozó, ha az alapértelmezett beállításokat használja. Ezért amíg nem konfigurál a másodlagos helykiszolgálót tartalmazó határcsoportokat, az ügyfelek nem fogják igénybe a tartalom forráshelyeként másodlagos helyre telepített terjesztési pontot.  

5.  Az a **telepítési forrásfájlok** lapon, válassza ki, hogyan szerzi be a másodlagos hely számítógépén a hely telepítéséhez a forrásfájlokat.  

     A hálózaton található vagy a másodlagos hely számítógépén tárolt forrásfájlok használatakor:  

    -   A forrásfájl helyéhez tartalmaznia kell egy nevű mappát **Redist** , amely tartalmazza a telepítő letöltési segédprogramjával korábban letöltött összes fájlt.  

    -   Ha a fájlokat **Redist** nem érhető el, a telepítő nem tudja telepíteni a másodlagos helyet.  

    -   Rendelkeznie kell a másodlagos helykiszolgáló számítógép számítógépfiókjának **olvasási** engedélyekkel a forrás-fájl, mappa és a megosztáshoz.  

6.  Az a **SQL Server beállításai** lapon adja meg a használni kívánt SQL Server verzióját, és konfigurálja a kapcsolódó beállításokat.  

    > [!NOTE]  
    > A telepítő nem érvényesíteni a megadott információt ezen az oldalon mindaddig, amíg a telepítés megkezdése. A folytatás előtt ellenőrizze a beállításokat.  

     **Telepítse és konfigurálja az SQL Express helyi másolatát a másodlagos hely számítógépén**  

    -   **SQL Server-szolgáltatásport**: Adja meg az SQL Server Express által használandó SQL Server-szolgáltatásportot. A szolgáltatásport jellemzően az 1433-as TCP-port használatára van konfigurálva, azonban más port is beállítható.  

    -   **SQL Server Service Broker-port**: Adja meg az SQL Server Service Broker (SSB) port az SQL Server Express által használandó. A Service Broker jellemzően a 4022-es TCP-port használatára van konfigurálva, de be lehet állítani egy másik portra. Adjon meg egy érvényes portot használó más webhelyre vagy szolgáltatásba, és nincs tűzfal korlátozásai miatt.  

    > [!IMPORTANT]  
    > A Configuration Manager telepíti az SQL Server Expresst, ha az SQL Server Express 2012 telepíti szervizcsomag nélkül:  

    > -   A másodlagos hely támogatott a telepítést követően frissítenie kell a SQL Server Express 2012 [valamelyik támogatott verzióra](/sccm/core/plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).
    > -   Továbbá ha az új másodlagos hely telepítésének befejezése meghiúsul, de először befejezi az SQL Server Express 2012 telepítését, frissítenie kell az SQL Server Express ezen példányát a Configuration Manager sikeresen újra megkísérelhetné a másodlagos hely telepítése előtt.  

     **Meglévő SQL Server-példány használata**  

    -   **SQL Server teljes Tartományneve**: Ellenőrizze az SQL Servert futtató számítógép teljes Tartománynevét. SQL Server rendszert futtató helyi kiszolgálón kell használnia a másodlagos Helyadatbázis futtatásához, és ez a beállítás nem módosítható.  

    -   **SQL Server-példány**: Adja meg a másodlagos helyadatbázisként használni kívánt SQL Server példánya. Hagyja üresen az alapértelmezett példányt használja ezt a beállítást.  

    -   **ConfigMgr-Helyadatbázis neve**: Adja meg a másodlagos Helyadatbázis nevét.  

    -   **SQL Server Service Broker-port**: Adja meg az SQL Server Service Broker (SSB) port az SQL Server által használandó. Adjon meg egy érvényes portot használó más webhelyre vagy szolgáltatásba, és nem tiltanak tűzfalkorlátozások.  

    > [!TIP]  
    > Lásd: [támogatott SQL Server-verziók](../../../../core/plan-design/configs/support-for-sql-server-versions.md) , amely támogatja a System Center Configuration Manager SQL Server-verziók listáját.  

7.  Az a **terjesztési pont** lapon, a terjesztési pontot a másodlagos helykiszolgálón telepítendő beállításainak konfigurálása.  

     **Kötelező beállítások:**  

    -   **Adja meg, hogy ügyféleszközök hogyan kommunikáljanak a terjesztési pont**: Választás a HTTP és HTTPS.  

    -   **Hozzon létre egy önaláírt tanúsítványt, vagy importáljon egy PKI ügyféltanúsítványt**: Választhat egy önaláírt tanúsítvánnyal (amely lehetővé teszi a névtelen kapcsolódását a Configuration Manager-ügyfelek a tartalomtárhoz) vagy a PKI-ügyféltanúsítvány importálása.  

         A tanúsítvánnyal hitelesíthető a terjesztési pont egy felügyeleti ponthoz, mielőtt a terjesztési pont elküldi az állapotüzeneteket.  

         A tanúsítvány követelményeivel kapcsolatos további információkért lásd: [PKI-tanúsítványkövetelmények a Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    **Választható beállítások:**  

    -   **Telepítse és konfigurálja az IIS, ha a Configuration Manager által igényelt**: Válassza ezt a beállítást, hogy a Configuration Manager telepítése és konfigurálása az Internet Information Services (IIS) a kiszolgálón, ha még nincs telepítve. Az összes terjesztési ponton telepíteni kell az IIS.  

        > [!NOTE]  
        > Bár ez a beállítás nem kötelező, az IIS telepítenie kell a kiszolgálón a terjesztési pont sikeres telepítése előtt.  

    -   **BranchCache engedélyezése és konfigurálása a terjesztési pont számára**.  

    -   **Leírás**. Ez a rövid leírása a könnyebb felismerhetőség a terjesztési pontot.  

    -   **Engedélyezése e terjesztési pont használatát előzetesen beállított tartalomhoz**.  

8.  Az a **Meghajtóbeállítások** adja meg azokat a másodlagos hely terjesztési pontjára vonatkozó meghajtóbeállításokat.  

     Legfeljebb két lemezmeghajtót a tartalomtár és két lemezmeghajtót a csomagmegosztás számára is konfigurálhatja. A Configuration Manager azonban használhat további meghajtók, ha az első kettő eléri a beállított lemezterület-tartalékot. A **Meghajtóbeállítások** lap, ahol konfigurálhatja a prioritását a merevlemez-meghajtók és a szabad hely maradjon az egyes meghajtókon.  

    -   **Lemezterület-tartalék (MB)**: Az ezzel a beállítással megadható határozza meg a minimális szabad területet a meghajtón a Configuration Manager egy másik meghajtót választ, és folytatja a másolást, amelynek előtt. Tartalomfájlok több meghajtóra is átnyúlhatnak.  

    -   **Tartalom helye**: Adja meg a tartalom helyét. a tartalom és a csomagmegosztás megosztást. A Configuration Manager tartalmat az elsődleges tartalomhelyre másolja át, amíg a szabad terület mennyisége el nem éri a megadott érték **lemezterület-tartalék (MB)**.

     Alapértelmezés szerint a tartalomhelyekhez beállítás van megadva **automatikus**. Az elsődleges tartalomhely a telepítéskor a legtöbb lemezterülettel rendelkező lemezmeghajtó értéke. A másodlagos hely az elsődleges meghajtója után a legtöbb szabad területtel rendelkező meghajtó értéke. Ha az elsődleges és másodlagos meghajtó eléri a lemezterület-tartalék értékét, a Configuration Manager választja ki a legtöbb szabad lemezterülettel rendelkező másik elérhető meghajtók közül, és folytatja a másolást.  

9. Az a **Tartalomérvényesítés** lapján adja meg, hogy a terjesztési ponton lévő tartalomfájlok integritásának ellenőrzését.  

    -   Ha engedélyezi a tartalomérvényesítési ütemezés szerint, a Configuration Manager elindítja a megadott időpontban, és a terjesztési pont összes tartalmát ellenőrzi.  

    -   Beállíthatja úgy is a **érvényesítési prioritású tartalmat**.  

    -   A tartalomérvényesítési folyamat eredményeinek megtekintéséhez a Configuration Manager konzolon navigáljon **figyelés** > **terjesztés állapota** > **Tartalomállapot**. A tartalom az egyes csomagtípusok (például alkalmazás, szoftverfrissítési csomag és rendszerindító lemezkép) jelenik meg.  

10. Az a **Határcsoportok** lapján kezelhetők azok a határcsoportok ehhez a terjesztési ponthoz rendelt:  

    -   Tartalom központi telepítésekor az ügyfeleknek a terjesztési pont a tartalom forráshelyeként használni társított határcsoportban kell lenniük.  

    -   Kiválaszthatja a **tartalék forráshely engedélyezése a tartalom** a beállítást, hogy visszatérjenek, és a terjesztési pontokat használják a forráshely a tartalomhoz Ha nincsenek előnyben részesített terjesztési pontok érhetők el ezen határcsoportokon kívüli ügyfelek számára.  

     Előnyben részesített terjesztési pontokkal kapcsolatos információért tekintse meg a [a Tartalomkezelés alapvető fogalmai](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) témakör.  

11. Az a **összegzés** lapon ellenőrizze a beállításokat, és válassza a **tovább** a másodlagos hely telepítéséhez. Amikor megjelenik a varázsló a **befejezési** lap, bezárhatja a varázslót. A másodlagos hely telepítése a háttérben folytatódik.  


### <a name="bkmk_verify"></a>A másodlagos hely telepítési állapotának ellenőrzése  

1.  A Configuration Manager-konzolon lépjen a **felügyeleti** > **Helykonfiguráció** > **helyek**.  

2.  Jelölje ki a másodlagos helykiszolgálót végzi a telepítést, és válassza a **telepítési állapot megjelenítése**.  

    > [!TIP]  
    > Egyszerre csak egy másodlagos hely telepítésekor az előfeltétel-ellenőrző egyetlen hely egyszerre fut, és csak egy hely befejezése, a következő hely ellenőrzése megkezdése előtt.  

