---
title: "A Windows rendszer kezelése szolgáltatásként - a Configuration Manager |} Microsoft Docs"
description: "Windows állapotának megtekintése a Configuration Manager szolgáltatásként, létrehozhat karbantartási terveket telepítési körök kialakításához, és megtekintheti a riasztásokat, amikor a Windows 10-ügyfelek végéhez közelednek."
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da1e687b-28f6-43c4-b14a-ff2b76e60d24
caps.latest.revision: 26
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 2c2c0f81736c1b00ea487ae1261803a8105bb5e4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-windows-as-a-service-using-system-center-configuration-manager"></a>A Windows mint szolgáltatás kezelése System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A System Center Configuration Managerben, megtekintheti az állapot a Windows szolgáltatásként a környezetében, létrehozhat karbantartási terveket telepítési körök kialakításához és győződjön meg arról, hogy a Windows 10 aktuális ág rendszerek mindig naprakészek maradjanak új buildek kiadásakor, és megtekintheti a riasztásokat, amikor a Windows 10-ügyfelek az aktuális ág (CB) vagy az aktuális ág buildjénél a támogatásuk támogatási üzleti (CBB) végéhez közelednek.  

 A Windows 10 szervizelési lehetőségeiről további információért lásd:  [Windows 10 servicing options for updates and upgrades](https://technet.microsoft.com/library/mt598226\(v=vs.85\).aspx)(A Windows 10 szervizelési lehetőségei frissítések és verziófrissítések esetén).  

 A következő szakaszok segítségével a Windows mint szolgáltatás kezelése.

##  <a name="BKMK_Prerequisites"></a> Előfeltételek  
 Az adatok a Windows 10 karbantartási irányítópulton való megtekintéséhez tegye a következőket:  

-   Windows 10-es számítógépeken kell használnia a Configuration Manager szoftverfrissítés a Windows Server Update Services (WSUS) a szoftverfrissítés kezeléséhez. Ha a számítógép a Windows Update for Business (vagy a Windows Insiders) programot használja a szoftverfrissítések felügyeletéhez, akkor a rendszer nem értékeli a számítógépet a Windows 10-es karbantartási tervek keretében. További információkért lásd: [Integráció a Windows Update for Business szolgáltatással a Windows 10 rendszerben](../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md).  

-   A szoftverfrissítési pontokon és a helykiszolgálókon telepítve kell lennie a WSUS 4.0-s verziójának a [3095113-as számú gyorsjavítással](https://support.microsoft.com/kb/3095113) . Ez a gyorsjavítás a **Frissítések** szoftverfrissítési besorolás felvételére szolgál. További információkért lásd: [szoftverfrissítéseinek előfeltételei](../../sum/plan-design/prerequisites-for-software-updates.md).  

-   A WSUS 4.0-s verziójának a [gyorsjavítás 3159706](https://support.microsoft.com/kb/3159706) telepíteni kell a szoftverfrissítési pontokon és a számítógép frissítése a Windows 10 évforduló frissítése, valamint a későbbi verziók helykiszolgálókon. Manuális lépések ismertetését a támogatási továbbítania kell a gyorsjavítás. További információkért lásd: a [nagyvállalati mobilitással és biztonsággal foglalkozó blogban](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/05/update-your-configmgr-1606-sup-servers-to-deploy-the-windows-10-anniversary-update/).

-   Engedélyezze a szívveréses felderítést. A Windows 10 karbantartási irányítópulton megjelenő adatokat a rendszer a felderítéssel keresi meg. További információkért lásd: [A szívveréses felderítés konfigurálása](../../core/servers/deploy/configure/configure-discovery-methods.md#a-namebkmkconfighbdisca-configure-heartbeat-discovery).  

     A felderítés során a rendszer a következő információkat azonosítja a Windows 10-ágak és -buildek kapcsán, és a következő attribútumokban tárolja azokat:  

    -   **Operációs rendszer – felkészítési ág**: Adja meg az operációs rendszer ág. Például **0** = CB (nem legyenek késleltetve a frissítések), **1** = CBB (legyenek késleltetve a frissítések), **2** = hosszú távú karbantartási ág (LTSB)

    -   **Operációs rendszer Build**: Az operációs rendszer build megadott. Például **10.0.10240** (RTM) vagy **10.0.10586** (1511-es verzió)  

-   A szolgáltatáskapcsolódási pontnak telepítve kell lennie, és **Online, állandó kapcsolattal** üzemmódban kell működnie ahhoz, hogy a Windows 10-karbantartási irányítópulton megjelenjenek az adatok. Offline üzemmódban van, akkor addig nem jelennek meg adatfrissítések az irányítópulton, amíg a Configuration Manager karbantartás-kezelő frissítések kap.   
     További információkért lásd: [a szolgáltatáskapcsolódási pont kapcsolatos](../../core/servers/deploy/configure/about-the-service-connection-point.md).  


-   Internet Explorer 9-es vagy újabb rendszerre telepíthető a Configuration Manager konzolt futtató számítógépen.  

-   A szoftverfrissítéseknek konfigurálva és szinkronizálva kell lenniük. Ki kell választania a **frissítések** besorolási és szinkronizálja a szoftverfrissítéseket, a Windows 10-szolgáltatásfrissítések megjelenjenek a Configuration Manager konzolon elérhetővé válása előtt. További információkért lásd: [a szoftver előkészítése frissíti management](../../sum/get-started/prepare-for-software-updates-management.md).  

##  <a name="BKMK_ServicingDashboard"></a> Windows 10 karbantartási irányítópult  
 A Windows 10-karbantartási irányítópult különböző információkat biztosít a környezetben futó Windows 10-es számítógépekről, az aktív karbantartási tervekről, a megfelelőségről és más elemekről. A Windows 10-karbantartási irányítópulton megjelenő adatok köre attól függ, hogy telepítve van-e a szolgáltatáskapcsolódási pont. Az irányítópulton a következő csempék találhatók:  

-   **Windows 10 használata csempe**:  A Windows 10 nyilvános buildjeinek bontásban. A Windows Insiders-buildek és a hely számára még nem ismert buildek „ **egyéb** ” besorolással jelennek meg. A szolgáltatáskapcsolódási pont letölti azokat a metaadatokat, amelyek a Windows-buildekről nyújtanak információkat, majd összeveti ezeket a felderítési adatokkal.  

-   **Windows 10-körök csempe**:  A Windows 10 ág és készültségi állapot szerinti bontásban. LTSB szegmens összes LTSB-verziót fogja (míg az első csempe a különböző verziókat. Ha például a Windows 10 LTSB 2015. A **megjelenésre kész** szegmens az aktuális ágnak (CB), az **üzleti felhasználásra kész** szegmens pedig az aktuális üzleti ágnak (CBB) felel meg.  

-   **A csempe Service-csomag létrehozása**:   A karbantartási terv gyors lehetőséget kínál. Önnek csak a nevet, a gyűjteményt (csak a tíz legkisebb méretű gyűjtemény jelenik meg), a központi telepítési csomagot (csak a tíz legutóbb módosított csomag jelenik meg) és a készültségi állapotot kell megadnia. A további beállításokhoz a rendszer alapértelmezett értékeket használ. Kattintson a **Speciális beállítások** elemre a Karbantartási terv létrehozása varázsló elindításához, amelyben a karbantartási terv valamennyi beállítását konfigurálhatja.  

-   **Lejárt csempe**: A százalékos arányát, amelyek a Windows 10-élettartama build eszközöket jeleníti meg. A Configuration Manager a százalékos arányt, hogy a szolgáltatáskapcsolódási pont letölti és a felderítési adatokkal összevetett metaadatok alapján állapítja meg. A lejárt élettartamú buildek már nem kapják meg a biztonsági frissítéseket is tartalmazó havi összesítő frissítéseket. Az ebbe a kategóriába tartozó számítógépeket a következő buildverzióra kell frissíteni. A Configuration Manager a következő egész számra kerekít. Ha például 10 000 számítógépből csak egy lejárt build van, a csempén 1% fog megjelenni.  

-   **A csempe hamarosan lejár**: A százalékos arányát, amelyek a build élettartama hamarosan (körülbelül négy hónapon belül), hasonló a számítógépek jeleníti meg a **lejárt** csempére. A Configuration Manager a következő egész számra kerekít.  

-   **Riasztások csempe**: Aktív riasztásokat jeleníti meg.  

-   **Karbantartási terv figyelése csempe**: Megjeleníti a karbantartási tervek létrehozott és azok megfelelőségi diagramjait. Ez gyors áttekintést ad a karbantartási tervek aktuális állapotáról. Ha egy korábbi központi telepítési kör eleget tesz a megfelelőségi elvárásainak, akkor választhat egy későbbi karbantartási tervet (központi telepítési kört), és ha az **Azonnali telepítés** parancsra kattint, akkor nem kell megvárnia a karbantartási tervhez kapcsolódó szabályok automatikus aktiválását.  

-   A **Windows 10-buildek csempe**:  Megjelenítési, akkor áttekintése a Windows 10 buildek, amely jelenleg kiadott, és lehetővé teszi az általános meghatározni, hogy mikor biztosító sor buildek rögzített rendszerkép egyszerre ismerhetik állapotot váltani.  

> [!IMPORTANT]  
>  A Windows 10-karbantartási irányítópulton látható információk (például a Windows 10-verziók támogatási életciklusa) csak tájékoztatásként szolgál a vállalaton belüli használatra. A frissítések megfelelőségének ellenőrzésekor ne hagyatkozzon kizárólag erre az információra. Mindenképpen ellenőrizze az információk pontosságát.  

## <a name="servicing-plan-workflow"></a>A karbantartási tervhez tartozó munkafolyamat  
 Windows 10 karbantartási tervet a Configuration Manager sokkal olyanok, mint a szoftverfrissítések automatikus központi telepítési szabályokat. A következő feltételeket kell megadnia, amely kiértékeli a Configuration Manager létrehoz egy karbantartási tervet:  

-   **Frissítések besorolás**: Csak a frissítések a **frissítések** besorolás kiértékelése.  

-   **Készültségi állapot**: A karbantartási tervben definiált készültségi állapotot a rendszer összehasonlítja a verziófrissítés készültségi állapotával. Amikor a szolgáltatáskapcsolódási pont frissítéseket keres, a rendszer lekéri a verziófrissítés metaadatait.  

-   **Halasztás**: A beállításhoz megadott napok száma **egy új frissítés Microsoft általi kiadását követően hány napig szeretne központi telepítése a környezetben** a karbantartási tervben. A Configuration Manager értékeli ki, hogy e frissítés szerepeljenek a központi telepítést, ha az aktuális dátumot követően a kiadási dátum plusz a beállított napok száma.  

 Ha egy verziófrissítés megfelel a feltételeknek, a karbantartási terv hozzáadja a frissítést a központi telepítési csomaghoz, továbbítja a csomagot a terjesztési pontokra, és a karbantartási tervben megadott beállítások alapján telepíti a frissítést a gyűjteményben.  A központi telepítések állapotát a Windows 10 karbantartási irányítópult Karbantartási terv figyelése csempéjén követheti nyomon. További információkért lásd: [szoftverfrissítések figyelése](../../sum/deploy-use/monitor-software-updates.md).  

##  <a name="BKMK_ServicingPlan"></a> Windows 10 karbantartási terv  
 A Windows 10 CB központi telepítésekor akár több karbantartási tervet is létrehozhat a környezetben kívánt központi telepítési körök meghatározásához, majd a Windows 10 karbantartási irányítópulton megfigyelheti őket.   
A karbantartási tervek csak a **Frissítések** szoftverfrissítés-besorolást használják, a Windows 10 összesítő frissítéseit nem. Ez utóbbiakat továbbra is a szoftverfrissítési munkafolyamattal kell telepítenie.  A karbantartási terv és a szoftverfrissítések felhasználói kezelése megegyezik, beleértve a karbantartási tervben konfigurálható beállításokat is.  

> [!NOTE]  
>  A verziófrissítéseket feladatütemezéssel is telepítheti központilag az egyes Windows 10-buildekhez, ez azonban jóval több manuális munkát igényel. A frissített forrásfájlokat operációs rendszer verziófrissítő csomagjaként kell importálnia, majd létre kell hoznia és a megfelelő számítógépcsoporton telepítenie kell a feladatütemezést. A feladatütemezés ugyanakkor további testreszabható lehetőségeket is kínál, például központi telepítés előtti és utáni műveleteket.  

 A Windows 10 karbantartási irányítópulton létrehozhat egy alapszintű karbantartási tervet. Miután megadta a nevét, a gyűjteményt gyűjtemény (csak jelenik meg a tíz legkisebb méretű), központi telepítési csomagot (csak a tíz legutóbb módosított megjelenítése), és a készültségi állapot, a Configuration Manager a további beállításoknál az alapértelmezett értékekkel létrehozza a karbantartási tervet. A beállítások emellett a Karbantartási terv létrehozása varázslóval is konfigurálhatók. A következő eljárással hozhat létre karbantartási tervet a Karbantartási terv létrehozása varázslóval.  

> [!NOTE]  
>  A Configuration Manager 1602-es verziójával kezdve kezelheti a magas kockázatú központi telepítések működése. A magas kockázatú központi telepítés olyan központi telepítés, amely automatikusan történik, és nem várt eredményeket okozhat. Egy **Kötelező** célú, a Windows 10-et központilag telepítő feladatütemezés például magas kockázatú központi telepítésnek minősül. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

#### <a name="to-create-a-windows-10-servicing-plan"></a>Windows 10 karbantartási terv létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki **A Windows 10 karbantartása**csomópontot, majd kattintson a **Karbantartási tervek**elemre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Karbantartási terv létrehozása**elemre. Megnyílik a Karbantartási terv létrehozása varázsló.  

4.  Az **Általános** lapon adja meg a következő beállításokat:  

    -   **Név**: Adja meg a karbantartási terv nevét. A nevét kell egyedinek lennie, a szabály célját leíró, és a többi szabálytól a Configuration Manager-hely.  

    -   **Leírás**: Adja meg a karbantartási terv leírását. A leírás áttekintést a karbantartási tervről, továbbá egyéb olyan információkkal szolgál, amelyek segítségével a Configuration Manager-hely többek között a terv azonosítható és megkülönböztethető kell biztosítania. A leírást nem kötelező megadni, legfeljebb 256 karakterből állhat, és alapértelmezés szerint üres.  

5.  A Karbantartási terv lapon adja meg a következő beállításokat:  

    -   **Célgyűjtemény**: A karbantartási tervhez használandó célgyűjteményt adja meg. A célgyűjtemény tagjai kapják meg a karbantartási tervben definiált Windows 10-frissítéseket.  

        > [!NOTE]  
        >  Magas kockázatú telepítés például karbantartási tervet, központi telepítésekor a Configuration Manager verziója 1602, kezdve a **gyűjtemény választása** ablak csak azokat az egyéni gyűjteményeket, amelyek megfelelnek a központi telepítés ellenőrzési beállításai a hely tulajdonságai konfigurált jeleníti meg.
        >    
        > A magas kockázatú központi telepítések mindig az egyéni, a felhasználó által létrehozott, valamint a beépített **Ismeretlen számítógépek** gyűjteményre korlátozódnak. Magas kockázatú központi telepítés létrehozásakor nem jelölhet ki olyan beépített gyűjteményeket, mint például a **Minden rendszer**. Törölje a jelet **elrejtése gyűjtemények száma nagyobb, mint a hely minimális méretre vonatkozó konfigurációja** megtekintéséhez az összes olyan egyéni gyűjtemények, amelyek a beállított maximális számnál kevesebb ügyfelet tartalmaznak. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >  
        > A központi telepítés ellenőrzési beállításai a gyűjtemény aktuális tagságától függenek. A karbantartási terv központi telepítése után a rendszer nem értékeli újra a gyűjteménytagságot a magas kockázatú központi telepítési beállításokra vonatkozóan.  
        >  
        > Például tételezzük fel, **alapértelmezett méret** 100 és a **maximális mérete** beállításé pedig 1000. Magas kockázatú központi telepítés létrehozásakor a **Gyűjtemény választása** ablak csak azokat a gyűjteményeket jeleníti meg, amelyek 100-nál kevesebb ügyfelet tartalmaznak. Ha törli a **elrejtése gyűjtemények száma nagyobb, mint a hely minimális méretre vonatkozó konfigurációja** beállítás, az ablak megjeleníti az 1000-nél kevesebb ügyfelet tartalmazó gyűjteményeket.  
        >
        > Helyszerepkört tartalmazó gyűjtemény kiválasztásakor az alábbiak érvényesek:    
        >   
        >    - Ha a gyűjtemény helyrendszer-kiszolgálót tartalmaz, és a központi telepítés ellenőrzési beállításai között a helyrendszer-kiszolgálókat tartalmazó gyűjtemények blokkolását adta meg, akkor hiba történik, és nem folytathatja a műveletet.    
        >    - Ha a gyűjtemény helyrendszer-kiszolgálót tartalmaz, és a központi telepítés ellenőrzési beállításai között megadta, hogy a rendszer figyelmeztesse a helyrendszer-kiszolgálókat tartalmazó gyűjteményekre, akkor ha a gyűjtemény meghaladja az alapértelmezett méretértéket, illetve ha a gyűjtemény kiszolgálót tartalmaz, a Szoftver központi telepítése varázsló magas kockázatra vonatkozó figyelmeztetést jelenít meg. Meg kell erősítenie, hogy magas kockázatú központi telepítést kíván létrehozni, és a rendszer létrehoz egy naplózott állapotüzenetet.  

6.  A Központi telepítési kör lapon adja meg a következő beállításokat:  

    -   **Adja meg a Windows készültségi állapotára, amelyre alkalmazni kell a karbantartási terv**: Válasszon az alábbi lehetőségek közül:  

        -   **Megjelenésre kész (aktuális ág)**: A CB karbantartási modell funkció frissítések érhetők el, amint Microsoft kiadja azokat.

        -   **Üzleti felhasználásra kész (aktuális üzleti ág)**: A CBB karbantartási ág általában széles körű központi telepítéshez használt. A karbantartási ág CBB a Windows 10-ügyfelek a CB csak egy későbbi időpontban karbantartási ág, mint a Windows 10 azonos buildjét kapnak.

        További információk olvashatók karbantartási ágak, és milyen beállítások esetén ajánlott használni,: [ágak karbantartási](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).

    -   **Az új frissítés Microsoft általi kiadását követően hány napig várjon a saját környezetben való telepítés előtt**: A Configuration Manager értékeli ki, hogy verziófrissítést a telepítés után a kiadási dátum plusz ezzel a beállítással megadható napok számát az aktuális dátum esetén.

    -   A Configuration Manager verziója 1602-es előtti kattintson **előzetes** a a készültségi állapothoz társított Windows 10-es frissítések megtekintéséhez.  

    További információkért lásd: [ágak karbantartási](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).
7.  A Configuration Manager 1602-es verziójával kezdve a frissítések lapon adja meg a keresési feltételek beállításával szűrheti a karbantartási tervhez hozzáadandó frissítéseket. Csak a megadott feltételeknek megfelelő frissítések lesznek hozzáadva a társított központi telepítéshez.  

     Kattintson az **Előnézet** elemre a megadott feltételeknek megfelelő frissítések megtekintéséhez.  

8.  A Központi telepítési ütemezés lapon adja meg a következő beállításokat:  

    -   **Ütemezés értékelése**: Adja meg, hogy a Configuration Manager értékeli ki a rendelkezésre álló idő és a telepítési határidőket UTC vagy a Configuration Manager konzolt futtató számítógép helyi ideje.  

        > [!NOTE]  
        >  Amikor kiválasztja a helyi időt, és válassza ki **minél hamarabb** a a **szoftver rendelkezésre állási ideje** vagy **telepítési határidő**, a Configuration Manager konzol segítségével értékelje ki, ha frissítések érhetők el, vagy az ügyfélen telepített rendszert futtató számítógépen az aktuális idejét. Ha az ügyfél másik időzónában van, ezek a műveletek akkor történnek meg, amikor az ügyfélnél elérkezik az értékelés ideje.  

    -   **Szoftver rendelkezésre állási ideje**: Válassza ki a következő beállítások egyikének kiválasztásával adja meg, ha a szoftverfrissítések érhetők el az ügyfelek számára:  

        -   **Amint lehetséges**: Válassza ezt a beállítást, a szoftverfrissítéseket, amelyek szerepelnek a központi telepítés rendelkezésre állása az ügyfélszámítógépek számára a lehető leghamarabb el. Ha a központi telepítés létrehozásához engedélyezi ezt a beállítást, a Configuration Manager frissíti az ügyfélházirendet. Ezután a legközelebbi ügyfélházirend-lekérdezési ciklusban az ügyfelek értesülnek a központi telepítésről, és hozzáférhetnek a telepítésre elérhető frissítésekhez.  

        -   **Adott időpont**: Válassza ezt a beállítást, hogy egy adott napon és időpontban az ügyfélgépeken elérhető központi telepítésben lévő szoftverfrissítéseket. Ha a központi telepítés létrehozásához engedélyezi ezt a beállítást, a Configuration Manager frissíti az ügyfélházirendet. Ezután a legközelebbi ügyfélházirend-lekérdezési ciklusban az ügyfelek értesülnek a központi telepítésről. A központi telepítésben lévő szoftverfrissítések azonban csak a megadott dátumon és időpontban válnak elérhetővé a telepítésre.  

    -   **Telepítési határidő**: Válassza ki a következő beállítások egyikének kiválasztásával adja meg, a központi telepítésben lévő szoftverfrissítések telepítési határidejét:  

        -   **Amint lehetséges**: Ezt a beállítást automatikusan telepíthetik a szoftverfrissítéseket a lehető leghamarabb, a központi telepítés.  

        -   **Adott időpont**: Ezt a beállítást automatikusan telepíthetik a szoftverfrissítéseket adott dátummal és időponttal a telepítésben. A Configuration Manager meghatározza, hogy a szoftverfrissítések telepítéséhez adja hozzá a konfigurált határidő **megadott idő** időközt a **szoftver rendelkezésre állási ideje**.  

            > [!NOTE]  
            >  A tényleges telepítési határidő a megjelenített időpontnál egy véletlen értékkel (legfeljebb 2 órával) későbbi időpont lesz. Ezzel a megoldással elkerülhető, hogy a célgyűjtemény összes ügyfélszámítógépe pontosan egyszerre telepítse a központi telepítésben lévő frissítéseket.  
            >   
            >  A **Határidő véletlenszerűsítésének letiltása** **Számítógépügynök** ügyfélbeállítással letilthatja a kötelező frissítések véletlenszerű telepítési késleltetését. További információkért L.: [Számítógépügynök](../../core/clients/deploy/about-client-settings.md#computer-agent).  

9. A Felhasználói élmény lapon adja meg a következő beállításokat:  

    -   **Felhasználó értesítései**: Adja meg, hogy az értesítés a frissítésekről megjelenítés a Szoftverközpontban az ügyfélszámítógépen, a konfigurált **szoftver rendelkezésre állási ideje** és megjelenjen-e felhasználói értesítések az ügyfélszámítógépeken.  

    -   **Viselkedés a határidőhöz**: Adja meg, hogy a központi telepítési határidejének történjen. Adja meg, hogy sor kerüljön-e a központi telepítésben lévő frissítések telepítésére. Adja meg emellett azt is, hogy a beállított karbantartási időszaktól függetlenül újrainduljon-e a rendszer a frissítés telepítését követően. Karbantartási időszakok kapcsolatos további információkért lásd: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Viselkedés az eszköz újraindításához**: Adja meg, hogy ne jelenjen meg többé a kiszolgálókon és munkaállomásokon a rendszer újraindítása után a rendszer telepíti a frissítéseket, és a telepítés befejezéséhez újraindítás szükséges.  

    -   **Írási szűrő kezelése a Windows Embedded-eszközök**: Ha engedélyezett írási szűrőkkel rendelkező Windows Embedded rendszerű eszközökön központilag a frissítéseket, megadhatja a frissítés telepítése az átmeneti területre történjen, és a változások véglegesítésére később, vagy hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

        > [!NOTE]  
        >  Amikor frissítést telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal.  

10. A Központi telepítési csomag lapon válasszon létező központi telepítési csomagot, vagy adja meg a következő beállításokat új központi telepítési csomag létrehozásához:  

    1.  **Név**: Adja meg a központi telepítési csomag nevét. Ennek a csomag tartalmát leíró egyedi névnek kell lennie. Legfeljebb 50 karakter hosszúságú lehet.  

    2.  **Leírás**: Adjon meg egy leírást, amely tájékoztatást ad azokról a központi telepítési csomagot. A leírás legfeljebb 127 karakter hosszúságú lehet.  

    3.  **Csomag forrása**: Megadja a szoftverfrissítés forrásfájljainak helyét.  Írja be a forráshely hálózati elérési útját (például: **\\\\kiszolgáló\megosztásnév\elérési út**) vagy kattintson a **Tallózás** gombra a hálózati hely megkereséséhez. Mielőtt a következő lapra lép, létre kell hoznia a telepítőcsomag forrásfájljait tároló megosztott mappát.  

        > [!NOTE]  
        >  A telepítőcsomag megadott forráshelyét nem használhatja másik szoftvertelepítő csomag.  

        > [!IMPORTANT]  
        >  Az SMS Provider számítógép fiókjának és a varázslót a szoftverfrissítések letöltése céljából futtató felhasználónak is **Írás** NTFS-jogosultsággal kell rendelkeznie. Ügyeljen a letöltési hely hozzáférésének megfelelő korlátozására, hogy csökkentse a szoftverfrissítési forrásfájlok támadók általi módosításának kockázatát.  

        > [!IMPORTANT]  
        >  A Configuration Manager létrehoz a központi telepítési csomag után módosíthatja a csomag forráshelyét a telepítőcsomag tulajdonságaiban. Ekkor azonban a csomag eredeti forrásának tartalmát át kell másolnia az új forráshelyre.  

    4.  **Küldési prioritás**: Adja meg a központi telepítési csomag küldési prioritását. Configuration Manager terjesztési pontokra küldi a csomagot akkor használja a központi telepítési csomag küldési prioritását. Központi telepítési csomagok küldése a prioritásuk szerinti sorrendben történik: Magas, közepes vagy alacsony. Az azonos prioritású csomagokat a program a létrehozásuk sorrendjében küldi el. Ha nincs várakoztatás, a csomag feldolgozása azonnal elkezdődik, függetlenül a prioritásától.  

11. A Terjesztési pontok lapon adja meg a frissítési fájlokat tartalmazó terjesztési pontokat vagy terjesztésipont-csoportokat. Terjesztési pontokkal kapcsolatos további információkért lásd: [a terjesztési pont](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_configs).

    > [!NOTE]  
    >  Ez a lap csak akkor érhető el, ha új szoftverfrissítési célú központi telepítési csomagot hoz létre.  

12. A Letöltési hely lapon adja meg, hogy az internetről vagy a helyi hálózatról szeretné-e letölteni a frissítési fájlokat. Adja meg a következő beállításokat:  

    -   **Szoftverfrissítések letöltése az internetről**: Válassza ezt a beállítást, az interneten egy megadott internetcímről töltheti le a frissítéseket. A beállítás alapértelmezés szerint engedélyezve van.  

    -   **Szoftverfrissítések letöltése a helyi hálózatban lévő helyről**: Válassza ezt a beállítást, a frissítéseket egy helyi könyvtárból vagy megosztott mappából töltheti le. A beállítás akkor lehet hasznos, ha a varázslót futtató számítógépen nincs internet-hozzáférés. A frissítések bármely, internet-hozzáféréssel rendelkező számítógépre letölthetők előzetesen, majd a helyi hálózaton egy olyan helyre másolhatók, amely elérhető a varázslót futtató számítógépről.  

13. A Nyelv kiválasztása lapon adja meg azokat a nyelveket, amelyekhez a kiválasztott frissítéseket le szeretné tölteni. A frissítések csak akkor lesznek letöltve, ha elérhetők a kiválasztott nyelveken. A nem nyelvspecifikus frissítések mindig letöltődnek. A varázsló alapértelmezés szerint kiválasztja azokat a nyelveket, amelyek a szoftverfrissítési pont tulajdonságaiban be vannak állítva. A következő lapra történő továbblépés előtt legalább egy nyelvet ki kell választani. Ha csak olyan nyelveket választ ki, amelyeket egy adott frissítés nem támogat, akkor az adott frissítés letöltése meghiúsul.  

14. Az Összefoglalás lapon tekintse át a beállításokat, majd kattintson a **Tovább** gombra a karbantartási terv létrehozásához.  

 A varázsló befejezését követően megkezdődik a karbantartási terv futtatása. A megadott feltételeknek megfelelő frissítések szoftverfrissítési csoportba kerülnek, a frissítések letöltődnek a helykiszolgálón lévő tartalomtárba, sor kerül a frissítések megadott terjesztési pontokra való terjesztésére, majd megtörténik a szoftverfrissítési csoport központi telepítése a célgyűjteményben lévő ügyfelekre.  

##  <a name="BKMK_ModifyServicingPlan"></a> Karbantartási terv módosítása  
Miután a Windows 10 karbantartási irányítópulton létrehozhat egy alapszintű karbantartási tervet, vagy módosítania kell egy meglévő karbantartási terv beállításait, lépjen a karbantartási terv tulajdonságaihoz.

> [!NOTE]
> Konfigurálhatja a beállításokat, amelyek nem érhető el a varázslóban, a karbantartási tervek létrehozásakor a karbantartási terv tulajdonságainak. A varázsló alapértelmezett beállításokat használja a beállítások a következő: Töltse le a beállításokat, a központi telepítési beállítások és a riasztásokat.  

A karbantartási terv tulajdonságait a következő eljárással módosíthatja.  

#### <a name="to-modify-the-properties-of-a-servicing-plan"></a>A karbantartási terv tulajdonságainak módosítása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki **A Windows 10 karbantartása**csomópontot, kattintson a **Karbantartási tervek**elemre, és válassza ki a módosítani kívánt karbantartási tervet.  

3.  A **Kezdőlap** lapon kattintson a **Tulajdonságok** elemre a kiválasztott karbantartási terv tulajdonságainak megnyitásához.

    A következő beállítások érhetők el a varázsló nem konfigurált karbantartási terv tulajdonságai:

    **Központi telepítési beállítások**: A központi telepítési beállítások lapon adja meg a következő beállításokat:  

    -   **Központi telepítési típus**: Adja meg a központi telepítési típus a szoftverfrissítés központi telepítéséhez. A **Kötelező** beállítás kiválasztásával kötelező központi szoftverfrissítés-telepítést hozhat létre, amelyben a szoftverfrissítések ügyfelekre való telepítése automatikusan történik meg a beállított telepítési határidőig. Az **Elérhető** beállítás megadásával választható központi szoftverfrissítés-telepítést hozhat létre, amelyet a felhasználók a Szoftverközpontból telepíthetnek.  

        > [!IMPORTANT]  
        >  A központi szoftverfrissítés-telepítés létrehozását követően a központi telepítési típus már nem módosítható.  

        > [!NOTE]  
        >  A **Kötelező** beállítással telepített szoftverfrissítési csoport letöltése a háttérben történik és figyelembe veszi a BITS-beállításokat, amennyiben azok konfigurálva lettek.  
        > Az **Elérhető** beállítással telepített frissítési csoportok letöltése azonban az előtérben történik és figyelmen kívül hagyja a BITS-beállításokat.  

    -   **Hálózati ébresztés használata az ügyfelek felébresztéséhez a szükséges központi telepítések**: Adja meg, hogy engedélyezze a hálózati ébresztés számára a határidő lejártakor, hogy ébresztési csomagokat küldjön azoknak a számítógépeket, amelyek a központi telepítésben lévő szoftverfrissítéseket. A telepítési határidő lejártakor alvó üzemmódban lévő számítógépek fel lesznek ébresztve, hogy megkezdődhessen a szoftverfrissítések telepítése. Azok az alvó üzemmódban lévő ügyfelek, amelyeken nincs szükség a központi telepítésben lévő szoftverfrissítések telepítésére, nem lesznek elindítva. Alapértelmezés szerint ez a beállítás nincs engedélyezve, és csak akkor érhető el, ha a **Központi telepítési típus** értéke **Kötelező**.  

        > [!WARNING]  
        >  E lehetőség használatához a számítógépeken és a hálózatokban be kell állítani a hálózati ébresztést.  

    -   **Részletességi szint**: Adja meg az ügyfélszámítógépek által jelentett állapotüzeneteinek részletességi szintjét.  

    **Letöltési beállítások**: A letöltési beállítások lapon adja meg a következő beállításokat:  

    - Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket, ha lassú hálózathoz vagy tartalék tartalomhelyhez kapcsolódik.  

    - Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket egy tartalék terjesztési pontról, ha az előnyben részesített terjesztési pontokon a szoftverfrissítések tartalma nem érhető el.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: Adja meg, hogy engedélyezze a BranchCache használatát a tartalomletöltésekhez. A BranchCache szolgáltatással kapcsolatos további információkért lásd: [a Tartalomkezelés alapvető fogalmai](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Adja meg, hogy letölthető a szoftver ügyfelek frissíti a Microsoft Update szolgáltatásból, ha a szoftverfrissítések nem érhetők el a terjesztési pontokon.
        > [!IMPORTANT]
        > Ne használja ezt a beállítást a Windows 10 karbantartása frissítéseket. A Configuration Manager (legalább verzió 1610 keresztül) a Microsoft Update a Windows 10 karbantartása frissítések letöltése sikertelen lesz.

    -   Adja meg, hogy engedélyezi-e az ügyfelek számára a telepítési határidő után történő letöltést, ha mért internetkapcsolatot használnak. Ha forgalmi díjas internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.   

    **Riasztások**: Az értesítések lapon hogyan Configuration Manager és a System Center Operations Manager riasztásokat generál a központi telepítés konfigurálása. A riasztásokat csak akkor állíthatja be, ha a **Központi telepítési típus** értéke **Kötelező** a Központi telepítési beállítások lapon.  

    > [!NOTE]  
    >  A legújabb szoftverfrissítési riasztások a **Szoftverkönyvtár** munkaterület **Szoftverfrissítések** csomópontján tekinthetők meg.  

