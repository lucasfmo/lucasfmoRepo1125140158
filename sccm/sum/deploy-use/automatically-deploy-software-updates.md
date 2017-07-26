---
title: "Szoftverfrissítések automatikus központi telepítése |} Microsoft Docs"
description: "Szoftverfrissítések automatikus központi telepítését, új frissítések egy aktív központi telepítéssel társított frissítési csoporthoz való hozzáadásával vagy automatikus központi telepítési szabályok használatával."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b27682de-adf8-4edd-9572-54886af8f7fb
ms.translationtype: Machine Translation
ms.sourcegitcommit: 78524abd4c45f0b7402d6f1e85afc60bb72ab0ee
ms.openlocfilehash: 34b0819957ffcc3711ee354a5b821d78fa7445cb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

#  <a name="BKMK_AutoDeploy"></a> Szoftverfrissítések automatikus központi telepítése  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Szoftverfrissítések automatikusan telepíthet új szoftverfrissítéseket egy aktív központi telepítéssel társított frissítési csoporthoz való hozzáadásával, vagy használhatja az automatikus központi telepítési szabály (ADR). Általában használandó automatikus központi telepítési szabályok havi szoftverfrissítések (általában ismerik javítás kedd frissítések) központi telepítéséhez és definíciófrissítések kezeléséhez. Ha segítségre van szüksége meghatározni, melyik központi telepítési módszer az Ön számára legmegfelelőbb című [szoftverfrissítések központi telepítése](deploy-software-updates.md)

##  <a name="BKMK_AddUpdatesToExistingGroup"></a> Szoftverfrissítések felvétele központilag telepített frissítési csoportba  
Miután létrehozott és a szoftverfrissítési csoport telepítése, szoftverfrissítések adhatók a csoporthoz, és automatikusan telepíti.  

> [!IMPORTANT]  
>  Ha egy meglévő, központilag telepített szoftverfrissítési csoporthoz ad szoftverfrissítéseket, több percbe is telhet, amíg az újonnan hozzáadott szoftverfrissítések bekerülnek a központi telepítésbe.  

Kövesse az alábbi eljárást a szoftverfrissítések meglévő frissítési csoportba való felvételéhez.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>Szoftverfrissítések felvétele meglévő szoftverfrissítési csoportba  

1.  A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **áttekintése** > **szoftverfrissítések**.  

2.  Válassza ki azokat a szoftverfrissítéseket, amelyeket fel szeretne venni az új szoftverfrissítési csoportba.  

3.  A **Kezdőlap** lapon lévő **Frissítés** csoportban kattintson a **Tagság szerkesztése**elemre.  

4.  Válassza ki azt a szoftverfrissítési csoportot, amelybe a szoftverfrissítéseket fel szeretné venni tagként.  

5.  Kattintson a **Szoftverfrissítési csoportok** csomópontra a szoftverfrissítési csoport megjelenítéséhez.  

6.  Kattintson a szoftverfrissítési csoportra, majd a **Kezdőlap** lapon lévő **Frissítés** csoportban kattintson a **Tagok megjelenítése** elemre a csoportban lévő szoftverfrissítések listájának megjelenítéséhez.  

##  <a name="BKMK_CreateAutomaticDeploymentRule"></a> Automatikus központi telepítési szabály (ADR) létrehozása  
Automatikus központi telepítési szabály használatával automatikusan is elvégezheti a szoftverfrissítések jóváhagyását és központi telepítését. A szabállyal hozzáadhatja a szoftverfrissítéseket egy új szoftverfrissítési csoporthoz a szabály minden futásakor, vagy egy meglévő szoftverfrissítési csoporthoz is hozzáadhatja a szoftverfrissítéseket. Amikor egy szabály lefut, és hozzáadja a szoftverfrissítéseket egy meglévő csoporthoz, a szabály eltávolítja az összes szoftverfrissítést a csoportból, és hozzáadja azokat a szoftverfrissítéseket, amelyek megfelelnek a csoporthoz megadott feltételeknek. Ha például minden nap automatikus központi telepítési szabályt szeretne futtatni az új szoftverfrissítések megkereséséhez és az ügyfelekre való telepítéséhez, akkor az új szoftverfrissítési csoport létrehozását kell választania, nem a szoftverfrissítések meglévő csoporthoz való hozzáadását.  

> [!WARNING]  
>  Automatikus központi telepítési szabály első alkalommal történő létrehozása előtt győződjön meg arról, hogy a szoftverfrissítések szinkronizálása befejeződött az adott helyen. Ez akkor különösen fontos, ha a Configuration Manager nem angol nyelvű verzióját futtatja, mivel a szoftverfrissítések besorolásai az első szinkronizálás előtt angolul jelennek meg, és formában jelennek meg az adott nyelvre honosított szoftverfrissítés-szinkronizálást követően. A szoftverfrissítések szinkronizálása előtt létrehozott szabályok a szinkronizálást követően a szöveges karakterláncok esetleges eltérései miatt nem mindig működnek megfelelően.  

 Az alábbi eljárással hozhat létre automatikus központi telepítési szabályt.  

#### <a name="to-create-an-adr"></a>Automatikus központi telepítési szabály (ADR) létrehozása  

1.  A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** **áttekintése** > **szoftverfrissítések** > **automatikus központi telepítési szabályok**.  

2.  A **Kezdőlap** lapon lévő **Létrehozás** csoportban kattintson az **Automatikus központi telepítési szabály létrehozása**elemre. Elindul az Automatikus központi telepítési szabály létrehozása varázsló.  

3.  Az **Általános** lapon adja meg a következő beállításokat:  

    -   **Név**: Adja meg az automatikus központi telepítési szabály nevét. A nevét kell egyedinek lennie, a szabály célját leíró, és a többi szabálytól a Configuration Manager-hely.  

    -   **Leírás**: Adja meg az automatikus központi telepítési szabály leírását. A leírás áttekintést a központi telepítési szabályról, továbbá egyéb olyan információkkal szolgál, amelyek segítségével a Configuration Manager-hely többek között a szabály azonosítható és megkülönböztethető kell biztosítania. A leírást nem kötelező megadni, legfeljebb 256 karakterből állhat, és alapértelmezés szerint üres.  

    -   **Válasszon telepítési sablont**: Adja meg, hogy a korábban mentett telepítési sablonok alkalmazására. A központi telepítési sablont konfigurálhatja úgy, hogy több gyakran használt központi szoftverfrissítés-telepítési tulajdonságot tároljon, amelyek az automatikus központi telepítési szabályok létrehozásakor felhasználhatók. A sablonokkal biztosíthatja a hasonló központi telepítések egységességét, és időt takaríthat meg.  

         Az Automatikus központi telepítési szabály létrehozása varázslóban a szoftverfrissítés beépített központi telepítési sablonjai közül választhat. A **Definíciófrissítések** sablon azokat a beállításokat tartalmazza, amelyeket a definíciós szoftverfrissítések telepítésekor használhat. A **Frissítő kedd** sablon azokat a beállításokat tartalmazza, amelyeket akkor használhat, amikor havonta telepíti a szoftverfrissítéseket.  

    -   **Gyűjtemény**: A központi telepítéshez használt célgyűjteményt adja meg. A gyűjtemény tagjai a központi telepítésben definiált szoftverfrissítéseket kapják meg.  

    -   Döntse el, hogy a szoftverfrissítéseket új vagy meglévő szoftverfrissítési csoportba szeretné-e felvenni. A legtöbb esetben valószínűleg új szoftverfrissítési csoportot alkalmaz majd az automatikus központi telepítési szabály futtatásakor. Ha azonban a szabály szigorúbb ütemezés szerint fut, érdemes lehet egy meglévő csoportot választani. Ha például naponta szeretné futtatni a szabályt a definíciók frissítéséhez, akkor egy meglévő szoftverfrissítési csoporthoz is hozzáadhatja a szoftverfrissítéseket.  

    -   **Központi telepítés engedélyezése a szabály futtatása után**: Adja meg, hogy a szoftver központi telepítésének engedélyezése az automatikus központi telepítési szabály futtatása után. Ezzel kapcsolatban vegye figyelembe a következőket:  

        -   Az automatikus központi telepítés engedélyezésekor a szabályban definiált feltételeknek megfelelő szoftverfrissítések szoftverfrissítési csoportba kerülnek, a tartalmak szükség szerint letöltődnek és a megadott terjesztési pontokra kerülnek, majd megtörténik a szoftverfrissítések központi telepítése a célgyűjteményben lévő ügyfelekre.  

        -   Ha nem engedélyezi a központi telepítést, akkor a szabályban definiált feltételeknek megfelelő szoftverfrissítések szoftverfrissítési csoportba kerülnek, és megtörténik a szoftverfrissítések központi telepítési házirendjének konfigurálása is, de a szoftverfrissítések letöltésére és ügyfelekre való központi telepítésére nem kerül sor. Ilyen esetben van ideje arra, hogy igény szerint előkészítse a szoftverfrissítések központi telepítését, és ellenőrizze a feltételeket teljesítő szoftverfrissítések megfelelőségét; a központi telepítést később is engedélyezheti.  

4.  A Központi telepítési beállítások lapon adja meg a következő beállításokat:  

    -   **Hálózati ébresztés használata az ügyfelek felébresztéséhez a szükséges központi telepítések**: Megadja, hogy a hálózati ébresztés számára a határidő lejártakor, hogy ébresztési csomagokat küldjön azoknak a számítógépeket, amelyek a központi telepítésben lévő szoftverfrissítések engedélyezéséhez. A telepítési határidő lejártakor alvó üzemmódban lévő számítógépeket a rendszer felébreszti, hogy megkezdődhessen a szoftverfrissítések telepítése. Azok az alvó üzemmódban lévő ügyfelek, amelyeken nincs szükség a központi telepítésben lévő szoftverfrissítések telepítésére, nem lesznek elindítva. Alapértelmezés szerint ez a beállítás nem engedélyezett.  

        > [!WARNING]  
        >  E lehetőség használatához a számítógépeken és a hálózatokban be kell állítani a hálózati ébresztést.  

    -   **Részletességi szint**: Adja meg az ügyfélszámítógépek által jelentett állapotüzeneteinek részletességi szintjét.  

        > [!IMPORTANT]  
        >  Definíciófrissítések központi telepítésekor állítsa a részletességi szintet **Csak hiba** értékre, hogy az ügyfél csak akkor küldjön állapotüzenetet, ha egy definíciófrissítést nem sikerül telepíteni az ügyfélre. Ellenkező esetben az ügyfél számos állapotüzenetet fog küldeni, ami hatással lehet a helykiszolgáló teljesítményére.  

    -   **Licencfeltételek beállítása**: Adja meg, hogy a licencfeltételeket tartalmazó szoftverfrissítések automatikus központi telepítését. Egyes szoftverfrissítések, például a szervizcsomagok licencfeltételekhez vannak kötve. A szoftverfrissítések automatikus központi telepítésekor a licencfeltételek nem jelennek meg, és nincs lehetőség azok elfogadására. Beállíthatja, hogy a licencfeltételektől függetlenül engedélyezi a szoftverfrissítések automatikus központi telepítését, vagy azt is, hogy csak a licencfeltételeket nem tartalmazó szoftverfrissítések központi telepítését engedélyezi.  

        > [!NOTE]  
        >  Szoftverfrissítés licencfeltételeinek megtekintéséhez jelölje ki a kérdéses szoftverfrissítést a **Szoftverkönyvtár** munkaterület **Minden szoftverfrissítés** csomópontján, majd a **Kezdőlap** lapon lévő **Frissítés** csoportban kattintson a **Licenc áttekintése**elemre.  
        >   
        >  A licencfeltételeket tartalmazó szoftverfrissítések megkereséséhez adja hozzá a **Licencfeltételek** oszlopot a **Minden szoftverfrissítés** csomópont eredményeket megjelenítő ablaktáblájához, majd kattintson az oszlop fejlécére a licencfeltételeket tartalmazó szoftverfrissítések szerinti rendezéshez.  

5.  A Szoftverfrissítések lapon állítsa be az automatikus központi telepítési szabály által lekért és a szoftverfrissítési csoporthoz hozzáadott szoftverfrissítésekre vonatkozó feltételeket.  

    > [!IMPORTANT]  
    >  Az automatikus központi telepítési szabály legfeljebb 1000 szoftverfrissítést határozhat meg. Annak biztosítása érdekében, hogy az ezen a lapon megadott feltételek 1000-nél kevesebb szoftverfrissítést határozzanak meg, érdemes beállítani ugyanezeket a feltételeket a **Szoftverkönyvtár** munkaterület **Minden szoftverfrissítés** csomópontján is.  

    > [!NOTE]
    > A Configuration Manager verziója 1610 kezdődően szűrheti a szoftverfrissítések automatikus központi telepítési szabályokat a tartalom méretét. Például beállíthatja a **tartalom mérete (KB)** kiszűrik **< 2048** csak letölteni a szoftverfrissítéseket, amelyek 2 MB-nál kisebb. Szűrővel megakadályozza, hogy a nagy szoftverfrissítések jobban alacsonyabb szintű karbantartását, ha hálózati sávszélessége korlátozott egyszerűsített támogatási a Windows automatikusan letöltését. További információkért lásd: [Configuration Manager és a Windows karbantartási egyszerűsített le szint operációs rendszerre](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

6.  Az Értékelési ütemezés lapon adja meg, hogy engedélyezi-e az automatikus központi telepítési szabály ütemezett futtatását. Ha engedélyezi, kattintson a **Testreszabás** elemre az ismétlődő ütemezés beállításához.  

    > [!IMPORTANT]  
    >  Megjelenik a szoftverfrissítési pont szinkronizálási ütemezése, hogy segítsen az értékelési ütemezés gyakoriságának meghatározásában. Soha ne állítson be az értékelési ütemezéshez a szoftverfrissítések szinkronizálási ütemezésénél nagyobb gyakoriságot. Az ütemezés kezdő időpontjának beállítása a Configuration Manager konzolt futtató számítógép helyi idejére alapul.  

    > [!NOTE]  
    >  Az automatikus központi telepítési szabály manuális futtatásához jelölje ki a szabályt, majd kattintson a **Futtatás most** lehetőségre a **Kezdőlap** lapon lévő **Automatikus központi telepítési szabály** csoportban. Az automatikus központi telepítési szabály manuális futtatása előtt győződjön meg arról, hogy a szoftverfrissítések szinkronizálását futtatva lett a szabály legutóbbi futtatása óta.  

    > [!IMPORTANT]  
    >  Az automatikus központi telepítési szabály értékelése akár naponta háromszor is futtatható.  

7.  A Központi telepítési ütemezés lapon adja meg a következő beállításokat:  

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
        >  A tényleges telepítési határidő a megjelenített időpontnál egy véletlen értékkel (legfeljebb 2 órával) későbbi időpont lesz. Ezzel a megoldással elkerülhető, hogy a célgyűjtemény összes ügyfélszámítógépe pontosan egyszerre telepítse a központi telepítésben lévő szoftverfrissítéseket.  
        >   
        >  A **Számítógépügynök** **Határidő véletlenszerűsítésének letiltása** ügyfélbeállításának konfigurálásával letilthatja a kötelező szoftverfrissítések véletlenszerű telepítési késleltetését. További információk: [Számítógépügynök](../../core/clients/deploy/about-client-settings.md#computer-agent).  

8. A Felhasználói élmény lapon adja meg a következő beállításokat:  

    -   **Felhasználó értesítései**: Adja meg, hogy a szoftverfrissítések értesítési megjelenítés a Szoftverközpontban az ügyfélszámítógépen, a konfigurált **szoftver rendelkezésre állási ideje** és megjelenjen-e felhasználói értesítések az ügyfélszámítógépeken.  

    -   **Viselkedés a határidőhöz**: Adja meg, hogy a szoftverfrissítés központi telepítési határidejének történjen. Adja meg, hogy sor kerüljön-e a központi telepítésben lévő szoftverfrissítések telepítésére. Adja meg emellett azt is, hogy a beállított karbantartási időszaktól függetlenül újrainduljon-e a rendszer a szoftverfrissítés telepítését követően. Karbantartási időszakok kapcsolatos további információkért lásd: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Viselkedés az eszköz újraindításához**: Adja meg, hogy ne jelenjen meg többé a kiszolgálókon és munkaállomásokon a rendszer újraindítása után szoftverfrissítések telepítve vannak a rendszer újraindítása szükséges a telepítés befejezéséhez.  

        > [!IMPORTANT]  
        >  A rendszer újraindításának letiltása kiszolgálói környezetekben, illetve olyan esetekben lehet hasznos, amikor nem szeretné, hogy a szoftverfrissítéseket telepítő számítógépek alapértelmezés szerint újrainduljanak. Ilyenkor azonban a számítógépek állapota kevésbé biztonságossá válik, míg a kényszerített újraindítás engedélyezésével biztosítható, hogy a szoftverfrissítés telepítése a lehető leghamarabb befejeződjön.  

    -   **Írási szűrő kezelése a Windows Embedded-eszközök**: Amikor engedélyezett írási szűrőkkel rendelkező Windows Embedded rendszerű eszközökön telepíti a frissítéseket, megadhatja a szoftverfrissítés telepítése az átmeneti területre történjen, és a változások véglegesítésére később, vagy hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

        > [!NOTE]  
        >  Amikor szoftverfrissítést telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal.  

    - **A szoftverfrissítések központi telepítési újraértékelési viselkedése újraindítást**: A Configuration Manager verziója 1606, jelölje be ezt a beállítást, konfigurálhatja a szoftverfrissítések központi telepítését egy szoftverfrissítés-megfelelőségi ellenőrzést futtatása azonnal, miután egy ügyfél a szoftvertelepítést végzi ügyfelek kezdve frissíti, és újraindul. Ez lehetővé teszi az ügyfél számára, hogy olyan további szoftverfrissítéseket keressen, amelyek az ügyfél újraindítása után válnak alkalmazhatóvá, majd ugyanabban a karbantartási időszakban telepítse őket (elérve ezzel a megfelelőséget).

9. A riasztások lapon hogyan Configuration Manager és a System Center Operations Manager riasztásokat generál a központi telepítés konfigurálása.  

    > [!NOTE]  
    >  A legújabb szoftverfrissítési riasztások a **Szoftverkönyvtár** munkaterület **Szoftverfrissítések** csomópontján tekinthetők meg.  

10. A Letöltési beállítások lapon adja meg a következő beállításokat:  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket, ha lassú hálózathoz vagy tartalék tartalomhelyhez kapcsolódik.  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket egy tartalék terjesztési pontról, ha az előnyben részesített terjesztési pontokon a szoftverfrissítések tartalma nem érhető el.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: Adja meg, hogy engedélyezze a BranchCache használatát a tartalomletöltésekhez. További információk a BranchCache szolgáltatásról: [Tartalomkezelés fogalmai](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Adja meg, hogy az intranethez kapcsolódó ügyfelek letöltsék-e a szoftverfrissítéseket a Microsoft Update webhelyről, ha a terjesztési pontokon nem érhetők el a szoftverfrissítések.  

    -   Adja meg, hogy engedélyezi-e az ügyfelek számára a telepítési határidő után történő letöltést, ha mért internetkapcsolatot használnak. Ha mért internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.  

    > [!NOTE]  
    >  Az ügyfelek egy felügyeleti ponttól kérik a központi telepítésben lévő szoftverfrissítések tartalomhelyét. A letöltési viselkedés a terjesztési pont, a központi telepítési csomag és az ezen a lapon szereplő beállítások konfigurációjától függ. További információk: [A tartalom forráshelyei – esetek](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

11. A Központi telepítési csomag lapon válasszon létező központi telepítési csomagot, vagy adja meg a következő beállításokat új központi telepítési csomag létrehozásához:  

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

12. A Terjesztési pontok lapon adja meg a szoftverfrissítési fájlokat tartalmazó terjesztési pontokat vagy terjesztésipont-csoportokat. További információ a terjesztési pontokról: [A terjesztési pontok konfigurációi](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

    > [!NOTE]  
    >  Ez a lap csak akkor érhető el, ha új szoftverfrissítési célú központi telepítési csomagot hoz létre.  

13. A Letöltési hely lapon adja meg, hogy az internetről vagy a helyi hálózatról szeretné-e letölteni a szoftverfrissítési fájlokat. Adja meg a következő beállításokat:  

    -   **Szoftverfrissítések letöltése az internetről**: Válassza ezt a beállítást, a szoftverfrissítések letöltése egy adott helyen az interneten. A beállítás alapértelmezés szerint engedélyezve van.  

    -   **Szoftverfrissítések letöltése a helyi hálózatban lévő helyről**: Válassza ki az ezzel a beállítással a szoftverfrissítéseket egy helyi könyvtárból vagy megosztott mappából töltheti le. A beállítás akkor lehet hasznos, ha a varázslót futtató számítógépen nincs internet-hozzáférés. A szoftverfrissítések bármely, internet-hozzáféréssel rendelkező számítógépre letölthetők előzetesen, majd a helyi hálózaton egy olyan helyre másolhatók, amely elérhető a varázslót futtató számítógépről.  

14. A Nyelv kiválasztása lapon adja meg azokat a nyelveket, amelyekhez a kiválasztott szoftverfrissítéseket le szeretné tölteni. A szoftverfrissítések csak akkor lesznek letöltve, ha elérhetők a kiválasztott nyelveken. A nem nyelvspecifikus szoftverfrissítések mindig letöltődnek. A varázsló alapértelmezés szerint kiválasztja azokat a nyelveket, amelyek a szoftverfrissítési pont tulajdonságaiban be vannak állítva. A következő lapra történő továbblépés előtt legalább egy nyelvet ki kell választani. Ha csak olyan nyelveket választ ki, amelyeket egy adott szoftverfrissítés nem támogat, akkor az adott szoftverfrissítés letöltése meghiúsul.  

15. Az Összegzés lapon ellenőrizze a beállításokat. A beállítások központi telepítési sablonba történő mentéséhez kattintson a **Mentés sablonként**elemre, írja be a sablon nevét, válassza ki a sablonban tárolni kívánt beállításokat, majd kattintson a **Mentés**gombra. Konfigurált beállítás módosításához kattintson a megfelelő varázslóoldalra, és módosítsa a beállítást.  

    > [!NOTE]  
    >  A sablon neve alfanumerikus ASCII-karaktereket, valamint **\\** (fordított perjel) és **‘** (szimpla idézőjel) karaktereket tartalmazhat.  

16. Az automatikus központi telepítési szabály létrehozásához kattintson a **Tovább** gombra.  

 A varázsló befejezését követően megkezdődik a rendszer futtatja az automatikus központi telepítési szabályt. A megadott feltételeknek megfelelő szoftverfrissítések szoftverfrissítési csoportba kerülnek, a szoftverfrissítések letöltődnek a helykiszolgálón lévő tartalomtárba, sor kerül a szoftverfrissítések megadott terjesztési pontokra való terjesztésére, majd megtörténik a szoftverfrissítési csoport központi telepítése a célgyűjteményben lévő ügyfelekre.  

##  <a name="BKMK_AddDeploymentToADR"></a> Új központi telepítés hozzáadása létező automatikus központi telepítési szabályhoz  
 Az automatikus központi telepítési szabály létrehozása után további központi telepítéseket is hozzáadhat a szabályhoz. Ennek segítségével egyszerűbben felügyelheti a különböző frissítések különböző gyűjteményekbe történő központi telepítését. Minden egyes új központi telepítés rendelkezik az összes funkcióval, és a központi telepítés figyelésének lehetőségével.  

#### <a name="to-add-a-new-deployment-to-an-existing-adr"></a>Új központi telepítés hozzáadása létező automatikus központi telepítési szabályhoz  

1.  A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **áttekintése** > **szoftverfrissítések** > **automatikus központi telepítési szabályok**, majd válassza ki a kívánt szabályt.  

2.  A **Kezdőlap** lap **Automatikus központi telepítési szabály** csoportjában kattintson a **Központi telepítés hozzáadása**parancsra. Megnyílik a Központi telepítés hozzáadása varázsló.  

3.  A **Gyűjtemény** lapon adja meg a következő beállításokat:  

    -   **Gyűjtemény**: A központi telepítéshez használt célgyűjteményt adja meg. A gyűjtemény tagjai a központi telepítésben definiált szoftverfrissítéseket kapják meg.  

    -   **Központi telepítés engedélyezése a szabály futtatása után**: Adja meg, hogy a szoftver központi telepítésének engedélyezése az automatikus központi telepítési szabály futtatása után. Ezzel kapcsolatban vegye figyelembe a következőket:  

        -   Az automatikus központi telepítés engedélyezésekor a szabályban definiált feltételeknek megfelelő szoftverfrissítések szoftverfrissítési csoportba kerülnek, a tartalmak szükség szerint letöltődnek és a megadott terjesztési pontokra kerülnek, majd megtörténik a szoftverfrissítések központi telepítése a célgyűjteményben lévő ügyfelekre.  

        -   Ha nem engedélyezi a központi telepítést, akkor a szabályban definiált feltételeknek megfelelő szoftverfrissítések szoftverfrissítési csoportba kerülnek, és megtörténik a szoftverfrissítések központi telepítési házirendjének konfigurálása is, de a szoftverfrissítések letöltésére és ügyfelekre való központi telepítésére nem kerül sor. Ilyen esetben van ideje arra, hogy igény szerint előkészítse a szoftverfrissítések központi telepítését, és ellenőrizze a feltételeket teljesítő szoftverfrissítések megfelelőségét; a központi telepítést később is engedélyezheti.  

4.  A Központi telepítési beállítások lapon adja meg a következő beállításokat:  

    -   **Hálózati ébresztés használata az ügyfelek felébresztéséhez a szükséges központi telepítések**: Megadja, hogy a hálózati ébresztés számára a határidő lejártakor, hogy ébresztési csomagokat küldjön azoknak a számítógépeket, amelyek a központi telepítésben lévő szoftverfrissítések engedélyezéséhez. A telepítési határidő lejártakor alvó üzemmódban lévő számítógépeket a rendszer felébreszti, hogy megkezdődhessen a szoftverfrissítések telepítése. Azok az alvó üzemmódban lévő ügyfelek, amelyeken nincs szükség a központi telepítésben lévő szoftverfrissítések telepítésére, nem lesznek elindítva. Alapértelmezés szerint ez a beállítás nem engedélyezett.  

        > [!WARNING]  
        >  E lehetőség használatához a számítógépeken és a hálózatokban be kell állítani a hálózati ébresztést.  

    -   **Részletességi szint**: Adja meg az ügyfélszámítógépek által jelentett állapotüzeneteinek részletességi szintjét.  

        > [!IMPORTANT]  
        >  Definíciófrissítések központi telepítésekor állítsa a részletességi szintet **Csak hiba** értékre, hogy az ügyfél csak akkor küldjön állapotüzenetet, ha egy definíciófrissítést nem sikerül telepíteni az ügyfélre. Ellenkező esetben az ügyfél számos állapotüzenetet fog küldeni, ami hatással lehet a helykiszolgáló teljesítményére.  

5.  A Központi telepítési ütemezés lapon adja meg a következő beállításokat:  

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
        >  A tényleges telepítési határidő a megjelenített időpontnál egy véletlen értékkel (legfeljebb 2 órával) későbbi időpont lesz. Ezzel a megoldással elkerülhető, hogy a célgyűjtemény összes ügyfélszámítógépe pontosan egyszerre telepítse a központi telepítésben lévő szoftverfrissítéseket.  
        >   
        >  A **Számítógépügynök** **Határidő véletlenszerűsítésének letiltása** ügyfélbeállításának konfigurálásával letilthatja a kötelező szoftverfrissítések véletlenszerű telepítési késleltetését. További információk: [Számítógépügynök](../../core/clients/deploy/about-client-settings.md#computer-agent).  

6.  A Felhasználói élmény lapon adja meg a következő beállításokat:  

    -   **Felhasználó értesítései**: Adja meg, hogy a szoftverfrissítések értesítési megjelenítés a Szoftverközpontban az ügyfélszámítógépen, a konfigurált **szoftver rendelkezésre állási ideje** és megjelenjen-e felhasználói értesítések az ügyfélszámítógépeken.  

    -   **Viselkedés a határidőhöz**: Adja meg, hogy a szoftverfrissítés központi telepítési határidejének történjen. Adja meg, hogy sor kerüljön-e a központi telepítésben lévő szoftverfrissítések telepítésére. Adja meg emellett azt is, hogy a beállított karbantartási időszaktól függetlenül újrainduljon-e a rendszer a szoftverfrissítés telepítését követően. Karbantartási időszakok kapcsolatos további információkért lásd: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Viselkedés az eszköz újraindításához**: Adja meg, hogy ne jelenjen meg többé a kiszolgálókon és munkaállomásokon a rendszer újraindítása után szoftverfrissítések telepítve vannak a rendszer újraindítása szükséges a telepítés befejezéséhez.  

        > [!IMPORTANT]  
        >  A rendszer újraindításának letiltása kiszolgálói környezetekben, illetve olyan esetekben lehet hasznos, amikor nem szeretné, hogy a szoftverfrissítéseket telepítő számítógépek alapértelmezés szerint újrainduljanak. Ilyenkor azonban a számítógépek állapota kevésbé biztonságossá válik, míg a kényszerített újraindítás engedélyezésével biztosítható, hogy a szoftverfrissítés telepítése a lehető leghamarabb befejeződjön.  

    -   **Írási szűrő kezelése a Windows Embedded-eszközök**: Amikor engedélyezett írási szűrőkkel rendelkező Windows Embedded rendszerű eszközökön telepíti a frissítéseket, megadhatja a szoftverfrissítés telepítése az átmeneti területre történjen, és a változások véglegesítésére később, vagy hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

        > [!NOTE]  
        >  Amikor szoftverfrissítést telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal.  

7.  A riasztások lapon hogyan Configuration Manager és a System Center Operations Manager riasztásokat generál a központi telepítés konfigurálása.  

    > [!WARNING]  
    >  A legújabb szoftverfrissítési riasztások a **Szoftverkönyvtár** munkaterület **Szoftverfrissítések** csomópontján tekinthetők meg.  

8. A Letöltési beállítások lapon adja meg a következő beállításokat:  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket, ha lassú hálózathoz vagy tartalék tartalomhelyhez kapcsolódik.  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket egy tartalék terjesztési pontról, ha az előnyben részesített terjesztési pontokon a szoftverfrissítések tartalma nem érhető el.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: Adja meg, hogy engedélyezze a BranchCache használatát a tartalomletöltésekhez. További információk a BranchCache szolgáltatásról: [Tartalomkezelés fogalmai](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Adja meg, hogy az intranethez kapcsolódó ügyfelek letöltsék-e a szoftverfrissítéseket a Microsoft Update webhelyről, ha a terjesztési pontokon nem érhetők el a szoftverfrissítések.  

    -   Adja meg, hogy engedélyezi-e az ügyfelek számára a telepítési határidő után történő letöltést, ha mért internetkapcsolatot használnak. Ha mért internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.  

    > [!NOTE]  
    >  Az ügyfelek egy felügyeleti ponttól kérik a központi telepítésben lévő szoftverfrissítések tartalomhelyét. A letöltési viselkedés a terjesztési pont, a központi telepítési csomag és az ezen a lapon szereplő beállítások konfigurációjától függ. További információk: [A tartalom forráshelyei – esetek](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

További információ a központi telepítés folyamatáról: [Szoftverfrissítések központi telepítési folyamata](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).

## <a name="next-steps"></a>További lépések
[Szoftverfrissítések figyelése](monitor-software-updates.md)

