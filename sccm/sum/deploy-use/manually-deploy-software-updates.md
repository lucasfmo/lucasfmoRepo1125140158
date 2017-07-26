---

title: "Szoftverfrissítések manuális központi telepítése |} Microsoft Docs"
description: "A frissítések manuális telepítéséhez válassza ki azokat a frissítéseket a Configuration Manager konzoljáról és manuálisan telepíteni őket, vagy frissítések frissítési csoportba való felvételéhez és a csoport központi telepítését."
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
ms.assetid: 57184274-5fea-4d79-a2b4-22e08ed26daf
ms.translationtype: Machine Translation
ms.sourcegitcommit: 78524abd4c45f0b7402d6f1e85afc60bb72ab0ee
ms.openlocfilehash: d736715f1f2c92b4c91f156ecb8abe3513811a34
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

#  <a name="BKMK_ManualDeploy"></a> Szoftverfrissítések manuális központi telepítése  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A manuális központi telepítés szoftverfrissítések kiválasztása a Configuration Manager konzolról, és manuálisan kezdeményezi a központi telepítési folyamat során a rendszer. Másik lehetőségként felveheti a kijelölt szoftverfrissítéseket egy frissítési csoportba, amelyet azután manuálisan telepít. A manuális központi telepítés általában az ügyféleszközök a szükséges szoftverfrissítésekkel való naprakész állapotba hozására használható az automatikus központi telepítési szabályok létrehozása előtt, melyek a későbbi havi szoftverfrissítések központi telepítéseit fogják kezelni. A sávon kívüli szoftverfrissítések telepítésekor is hasznos a manuális módszer. Ha segítségre van szüksége meghatározni, melyik központi telepítési módszer az Ön számára legmegfelelőbb című [szoftverfrissítések központi telepítése](deploy-software-updates.md).

 Az alábbi szakaszok azokat a lépéseket, a szoftverfrissítések manuális központi telepítése.  

##  <a name="BKMK_1SearchCriteria"></a>1. lépés: Adja meg a keresési feltételeknek, a szoftverfrissítések  
 Nincsenek potenciálisan több ezer szoftverfrissítés is megjelenhet a Configuration Manager konzolon. A szoftverfrissítések manuális központi telepítésének első lépéseként meg kell határozni a telepítendő szoftverfrissítéseket. Például megadhatja úgy a feltételeket, hogy lekérjenek minden olyan szoftverfrissítést, amelyre több mint 50 ügyféleszköznek szüksége van, és amelyek **biztonság** vagy **kritikus** besorolásúak.  

> [!IMPORTANT]  
>  Egy központi telepítés legfeljebb 1000 szoftverfrissítést tartalmazhat.  

#### <a name="to-specify-search-criteria-for-software-updates"></a>A szoftverfrissítésekre vonatkozó keresési feltételek megadása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson a **Minden szoftverfrissítés**lehetőségre. Ekkor megjelennek a szinkronizált szoftverfrissítések.  

    > [!NOTE]  
    >  Az a **minden szoftverfrissítés** csomópont, a Configuration Manager szoftverfrissítéseket jeleníti meg csak egy **kritikus** és **biztonsági** besorolási és az utolsó 30 napban adtak ki.  

3.  A keresési ablaktáblán szűréssel határozza meg a kívánt szoftverfrissítéseket, az alábbi lépések szerint:  

    -   Írja be a keresett szöveget a keresőmezőbe, hogy kiszűrje a szoftverfrissítést. Például beírhatja a kívánt szoftverfrissítéshez tartozó cikkazonosítót vagy közleményazonosítót, vagy egy olyan karakterláncot, amely több szoftverfrissítés címében is szerepel.  

    -   Kattintson a **Feltétel hozzáadása**lehetőségre, válassza ki azt a feltételt, amely szerint szűrni kívánja a szoftverfrissítéseket, kattintson a **Hozzáadás**gombra, és adja meg a megfelelő értékeket a feltétel számára.  

4.  A szoftverfrissítések szűréséhez kattintson a **Keresés** gombra.  

    > [!TIP]  
    >  Ha kívánja, mentheti a szűrőfeltételt a **Keresés** lap **Mentés** csoportjában található lehetőségekkel.  

##  <a name="BKMK_2UpdateGroup"></a>2. lépés: A szoftverfrissítéseket tartalmazó szoftverfrissítési csoport létrehozása  
 A szoftverfrissítési csoportok hatékony módszert kínálnak a szoftverfrissítésének megszervezésére a központi telepítés előkészítéseként. Kézzel is hozzáadhatja a szoftverfrissítések egy szoftverfrissítési csoport vagy a Configuration Manager automatikusan hozzáadhatja a szoftverfrissítéseket egy új vagy meglévő frissítési csoporthoz egy automatikus központi telepítési szabály használatával. Az alábbi eljárás szerint veheti fel manuálisan a szoftverfrissítéseket egy új szoftverfrissítési csoportba.  

#### <a name="to-manually-add-software-updates-to-a-new-software-update-group"></a>Szoftverfrissítések manuális hozzáadása egy új szoftverfrissítési csoporthoz  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen kattintson a **Szoftverfrissítések**elemre.  

3.  Válassza ki azokat a szoftverfrissítéseket, amelyeket fel szeretne venni az új szoftverfrissítési csoportba.  

4.  A **Kezdőlap** **Frissítés** csoportjában kattintson a **Szoftverfrissítési csoport létrehozása**lehetőségre.  

5.  Adja meg a szoftverfrissítési csoport nevét és leírását (ez utóbbi nem kötelező). A név és a leírás lehetőleg utaljon arra, hogy milyen típusú szoftverfrissítéseket tartalmaz a csoport. A folytatáshoz kattintson a **Létrehozás**gombra.  

6.  Kattintson a **Szoftverfrissítési csoportok** csomópontra, hogy megjelenjen az új szoftverfrissítési csoport.  

7.  Válassza ki a szoftverfrissítési csoportot, és a **Kezdőlap** **Frissítés** csoportjában kattintson a **Tagok megjelenítése** lehetőségre, amely megjeleníti a csoportban levő szoftverfrissítések listáját.  

##  <a name="BKMK_3DownloadContent"></a>3. lépés: A szoftverfrissítési csoporthoz tartozó tartalom letöltése  
 Lehetőség van arra, hogy a központi telepítés előtt letöltse a frissítési csoportban megadott szoftverfrissítések tartalmát. Ez olyankor hasznos, ha ellenőrizni szeretné, hogy elérhető-e a tartalom a terjesztési pontokon, mielőtt megkezdené a szoftverfrissítések központi telepítését. Ezzel a módszerrel elkerülhetők a tartalom kézbesítésével kapcsolatos váratlan problémák. Ezt a lépést kihagyhatja, és ebben az esetben a rendszer a központi telepítési folyamat részeként fogja letölteni és átmásolni a tartalmat a terjesztési pontokra. Az alábbi eljárás szerint töltheti le a frissítési csoportban szereplő szoftverfrissítések tartalmát.  



#### <a name="to-download-content-for-the-software-update-group"></a>A szoftverfrissítési csoporthoz tartozó tartalom letöltése
[!INCLUDE[downloadupdates](..\includes\downloadupdates.md)]
<!--- 1.  In the Configuration Manager console, click **Software Library**.  

2.  In the Software Library workspace, expand **Software Updates**, and click **Software Update Groups**.  

3.  Select the software update group for which you want to download content.  

4.  On the **Home** tab, in the **Update Group** group, click **Download**. The **Download Software Updates Wizard** opens.  

5.  On the **Deployment Package** page, configure the following settings:  

    1.  **Select deployment package**: Select this setting to use an existing deployment package for the software updates in the deployment.  

        > [!NOTE]  
        >  Software updates that have already been downloaded to the selected deployment package are not downloaded again.  

    2.  **Create a new deployment package**: Select this setting to create a new deployment package for the software updates in the deployment. Configure the following settings:  

        -   **Name**: Specifies the name of the deployment package. This must be a unique name that describes the package content. It is limited to 50 characters.  

        -   **Description**: Specifies the description of the deployment package. The package description provides information about the package contents and is limited to 127 characters.  

        -   **Package source**: Specifies the location of the software update source files.  Type a network path for the source location, for example, **\\\server\sharename\path**, or click **Browse** to find the network location. You must create the shared folder for the deployment package source files before you proceed to the next page.  

            > [!NOTE]  
            >  The deployment package source location that you specify cannot be used by another software deployment package.  

            > [!IMPORTANT]  
            >  The SMS Provider computer account and the user that is running the wizard to download the software updates must both have **Write** NTFS permissions on the download location. You should carefully restrict access to the download location in order to reduce the risk of attackers tampering with the software update source files.  

            > [!IMPORTANT]  
            >  You can change the package source location in the deployment package properties after Configuration Manager creates the deployment package. But if you do so, you must first copy the content from the original package source to the new package source location.  

     Click **Next**.  

6.  On the Distribution Points page, select the distribution points or distribution point groups that are used to host the software update files defined in the new deployment package, and then click **Next**.  

7.  On the Distribution Settings page, specify the following settings:  

    -   **Distribution priority**: Use this setting to specify the distribution priority for the deployment package. The distribution priority applies when the deployment package is sent to distribution points at child sites. Distribution packages are sent in priority order: **High**, **Medium**, or **Low**. Packages with identical priorities are sent in the order in which they were created. If there is no backlog, the package will process immediately regardless of its priority. By default, packages are sent using **Medium** priority.  

    -   **Distribute the content for this package to preferred distribution points**: Use this setting to enable on-demand content distribution to preferred distribution points. When this setting is enabled, the management point creates a trigger for the distribution manager to distribute the content to all preferred distribution points when a client requests the content for the package and the content is not available on any preferred distribution points. For more information about preferred distribution points and on-demand content, see [Content source location scenarios](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#bkmk_CSLscenarios).  

    -   **Prestaged distribution point settings**: Use this setting to specify how you want to distribute content to prestaged distribution points. Choose one of the following options:  

        -   **Automatically download content when packages are assigned to distribution points**: Use this setting to ignore the prestage settings and distribute content to the distribution point.  

        -   **Download only content changes to the distribution point**: Use this setting to prestage the initial content to the distribution point, and then distribute content changes to the distribution point.  

        -   **Manually copy the content in this package to the distribution point**: Use this setting to always prestage content on the distribution point. This is the default setting.  

         For more information about prestaging content to distribution points, see [Use Prestaged content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Click **Next**.  

8.  On the Download Location page, specify location that Configuration Manager will use to download the software update source files. As needed, use the following options:  

    -   **Download software updates from the Internet**: Select this setting to download the software updates from the location on the Internet. This is the default setting.  

    -   **Download software updates from a location on the local network**: Select this setting to download software updates from a local folder or shared network folder. Use this setting when the computer running the wizard does not have Internet access.  

        > [!NOTE]  
        >  When you use this setting, download the software updates from any computer with Internet access, and then copy the software updates to a location on the local network that is accessible from the computer running the wizard.  

     Click **Next**.  

9. On the Language Selection page, specify the languages for which the selected software updates are to be downloaded, and then click **Next**. Configuration Manager downloads the software updates only if they are available in the selected languages. Software updates that are not language-specific are always downloaded.  

10. On the Summary page, verify the settings that you selected in the wizard, and then click **Next** to download the software updates.  

11. On the Completion page, verify that the software updates were successfully downloaded, and then click **Close**. --->

#### <a name="to-monitor-content-status"></a>Tartalomállapot figyelése
1. Kattintson a szoftverfrissítéseket a tartalomállapot figyeléséről **figyelés** a Configuration Manager konzolon.  

2. A Figyelés munkaterületen bontsa ki a **Terjesztés állapota**csomópontot, majd kattintson a **Tartalom állapota**lehetőségre.  

3. Válassza ki azt a szoftverfrissítési csomagot, amelyet korábban a szoftverfrissítési csoportban lévő szoftverfrissítések letöltéséhez azonosított.  

4. A **Kezdőlap** lapon lévő **Tartalom** csoportban kattintson az **Állapot megtekintése**elemre.  

##  <a name="BKMK_4DeployUpdateGroup"></a>4. lépés: A szoftverfrissítési csoport telepítése  
 Miután eldöntötte, mely szoftverfrissítések központi telepítését szeretné elvégezni, és hozzáadta ezeket a szoftverfrissítéseket egy szoftverfrissítési csoporthoz, elvégezheti a szoftverfrissítési csoportban lévő szoftverfrissítések manuális központi telepítését. A következő eljárást követve végezheti el a szoftverfrissítési csoportban lévő szoftverfrissítések manuális központi telepítését.  

#### <a name="to-manually-deploy-the-software-updates-in-a-software-update-group"></a>Szoftverfrissítési csoportban lévő szoftverfrissítések manuális központi telepítése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson a **Szoftverfrissítési csoportok**lehetőségre.  

3.  Válassza ki azt a szoftverfrissítési csoportot, amelynek a központi telepítését el szeretné végezni.  

4.  A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre. Elindul a **Szoftverfrissítések központi telepítése varázsló** .  

5.  Az Általános lapon adja meg a következő beállításokat:  

    -   **Név**: Adja meg a központi telepítés nevét. A központi telepítést, amely leírja a központi telepítés célját, és megkülönbözteti azt a Configuration Manager-helyen lévő más központi telepítésektől egyedi nevet kell adni. Alapértelmezés szerint a Configuration Manager automatikusan elnevezi a központi telepítést, a következő formátumban: **A Microsoft Software Updates -** <*dátum*><*idő*>  

    -   **Leírás**: Adja meg a központi telepítés leírását. A leírás áttekintést nyújt az üzembe helyezési és egyéb olyan információkkal szolgál, amelyek segítségével azonosítható és megkülönböztethető a telepítését, többek között a Configuration Manager-hely. A leírást nem kötelező megadni, legfeljebb 256 karakterből állhat, és alapértelmezés szerint üres.  

    -   **Szoftverfrissítési/szoftverfrissítési csoport**: Ellenőrizze, hogy a megjelenített szoftverfrissítési csoport vagy szoftverfrissítés megfelelő.  

    -   **Válasszon telepítési sablont**: Adja meg, hogy a korábban mentett telepítési sablonok alkalmazására. A központi telepítési sablont konfigurálhatja úgy, hogy több gyakran használt központi szoftverfrissítés-telepítési tulajdonságot tároljon, majd alkalmazhatja a sablont, amikor a későbbiekben szoftverfrissítések központi telepítését végzi, hogy biztosítsa a hasonló központi telepítések egységességét, és időt takarítson meg.  

    -   **Gyűjtemény**: Adja meg a gyűjteményt a központi telepítéshez megfelelő. A gyűjtemény tagjai a központi telepítésben definiált szoftverfrissítéseket kapják meg.  

6.  A Központi telepítési beállítások lapon adja meg a következő beállításokat:  

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

7.  Az Ütemezés lapon adja meg a következő beállításokat:  

    -   **Ütemezés értékelése**: Adja meg, hogy a rendelkezésre álló idő és a telepítési határidők kiértékelése az Egyezményes vagy a Configuration Manager konzolt futtató számítógép helyi ideje.  

        > [!NOTE]  
        >  Amikor kiválasztja a helyi időt, és válassza ki **minél hamarabb** a a **szoftver rendelkezésre állási ideje** vagy **telepítési határidő**, a Configuration Manager konzol segítségével értékelje ki, ha frissítések érhetők el, vagy az ügyfélen telepített rendszert futtató számítógépen az aktuális idejét. Ha az ügyfél másik időzónában van, ezek a műveletek akkor történnek meg, amikor az ügyfélnél elérkezik az értékelés ideje.  

    -   **Szoftver rendelkezésre állási ideje**: Válassza ki a következő beállítások egyikének kiválasztásával adja meg, amikor a szoftverfrissítések az ügyfelek számára rendelkezésre áll:  

        -   **Amint lehetséges**: Válassza ki az ezzel a beállítással a szoftverfrissítéseket a központi telepítésben lévő elérhetővé tenni az ügyfelek számára a lehető leghamarabb. A központi telepítés létrehozásakor az ügyfélházirend frissül, majd az ügyfelek a következő ügyfélházirend-lekérdezési ciklusban értesülnek a központi telepítésről, és a szoftverfrissítések elérhetővé válnak a telepítésre.  

        -   **Adott időpont**: Válassza ezt a beállítást, ha a szoftverfrissítéseket a központi telepítésben lévő elérhetővé tenni az ügyfelek számára egy adott dátumot és időpontot. A központi telepítés létrehozásakor az ügyfélházirend frissül, majd az ügyfelek a következő ügyfélházirend-lekérdezési ciklusban értesülnek a központi telepítésről. A központi telepítésben lévő szoftverfrissítések azonban csak a megadott dátumon és időpontban válnak elérhetővé a telepítésre.  

    -   **Telepítési határidő**: Válassza ki a következő beállítások egyikének kiválasztásával adja meg, a központi telepítésben lévő szoftverfrissítések telepítési határidejét.  

        > [!NOTE]  
        >  A telepítési határidőt csak akkor állíthatja be, ha a **Központi telepítési típus** értéke **Kötelező** a Központi telepítési beállítások lapon.  

        -   **Amint lehetséges**: Ezt a beállítást automatikusan telepíthetik a szoftverfrissítéseket a lehető leghamarabb, a központi telepítés.  

        -   **Adott időpont**: Ezt a beállítást automatikusan telepíthetik a szoftverfrissítéseket adott dátummal és időponttal a telepítésben.  

        > [!NOTE]  
        >  A tényleges telepítési határidő a megadott időpontnál egy véletlen értékkel (legfeljebb 2 órával) későbbi időpont lesz. Ezzel a megoldással elkerülhető, hogy a célgyűjtemény összes ügyfélszámítógépe pontosan egyszerre telepítse a központi telepítésben lévő szoftverfrissítéseket.  
        >   
        >  A **Számítógépügynök** **Határidő véletlenszerűsítésének letiltása** ügyfélbeállításának konfigurálásával letilthatja a kötelező szoftverfrissítések véletlenszerű telepítési késleltetését. További információk: [Számítógépügynök](../../core/clients/deploy/about-client-settings.md#computer-agent).  

8.  A Felhasználói élmény lapon adja meg a következő beállításokat:  

    -   **Felhasználó értesítései**: Adja meg, hogy a szoftverfrissítések értesítési megjelenítés a Szoftverközpontban az ügyfélszámítógépen, a konfigurált **szoftver rendelkezésre állási ideje** és megjelenjen-e felhasználói értesítések az ügyfélszámítógépeken. Ha a **Központi telepítési típus** értéke **Elérhető** a Központi telepítési beállítások lapon, akkor az **Elrejtés a Szoftverközpontban és az összes értesítésben**lehetőséget nem választhatja ki.  

    -   **Viselkedés a határidőhöz**: * érhető el, csak ha **központi telepítési típus** * értéke **szükséges** *a központi telepítési beállítások lapon.*   
    Adja meg, hogy a szoftverfrissítés központi telepítési határidejének történjen. Adja meg, hogy sor kerüljön-e a központi telepítésben lévő szoftverfrissítések telepítésére. Adja meg emellett azt is, hogy a beállított karbantartási időszaktól függetlenül újrainduljon-e a rendszer a szoftverfrissítés telepítését követően. További információ a karbantartási időszakok: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Viselkedés az eszköz újraindításához**: * érhető el, csak ha **központi telepítési típus** * értéke **szükséges** *a központi telepítési beállítások lapon.*    
    Adja meg, hogy ne jelenjen meg többé a kiszolgálókon és munkaállomásokon a rendszer újraindítása után szoftverfrissítések telepítve vannak a rendszer újraindítása szükséges a telepítés befejezéséhez.  

        > [!IMPORTANT]  
        >  A rendszer újraindításának letiltása kiszolgálói környezetekben, illetve olyan esetekben lehet hasznos, amikor nem szeretné, hogy a szoftverfrissítéseket telepítő számítógépek alapértelmezés szerint újrainduljanak. Ilyenkor azonban a számítógépek állapota kevésbé biztonságossá válik, míg a kényszerített újraindítás engedélyezésével biztosítható, hogy a szoftverfrissítés telepítése a lehető leghamarabb befejeződjön.

    -   **Írási szűrő kezelése a Windows Embedded-eszközök**: Amikor engedélyezett írási szűrőkkel rendelkező Windows Embedded rendszerű eszközökön telepíti a frissítéseket, megadhatja a szoftverfrissítés telepítése az átmeneti területre történjen, és a változások véglegesítésére később, vagy hogy a változások véglegesítése a telepítési határidő lejártakor vagy karbantartási időszak alatt történjen. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újraindításra van szükség, és a változtatások megmaradnak az eszközön.  

        > [!NOTE]  
        >  Amikor szoftverfrissítést telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal.  

    - **A szoftverfrissítések központi telepítési újraértékelési viselkedése újraindítást**: A Configuration Manager verziója 1606, jelölje be ezt a beállítást, konfigurálhatja a szoftverfrissítések központi telepítését egy szoftverfrissítés-megfelelőségi ellenőrzést futtatása azonnal, miután egy ügyfél a szoftvertelepítést végzi ügyfelek kezdve frissíti, és újraindul. Ez lehetővé teszi az ügyfél számára, hogy olyan további szoftverfrissítéseket keressen, amelyek az ügyfél újraindítása után válnak alkalmazhatóvá, majd ugyanabban a karbantartási időszakban telepítse őket (elérve ezzel a megfelelőséget).

9. A riasztások lapon hogyan Configuration Manager és a System Center Operations Manager riasztásokat generál a központi telepítés konfigurálása. A riasztásokat csak akkor állíthatja be, ha a **Központi telepítési típus** értéke **Kötelező** a Központi telepítési beállítások lapon.  

    > [!NOTE]  
    >  A legújabb szoftverfrissítési riasztások a **Szoftverkönyvtár** munkaterület **Szoftverfrissítések** csomópontján tekinthetők meg.  

10. A Letöltési beállítások lapon adja meg a következő beállításokat:  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket, ha lassú hálózathoz vagy tartalék tartalomhelyhez kapcsolódik.  

    -   Adja meg, hogy az ügyfél letöltse és telepítse-e a szoftverfrissítéseket egy tartalék terjesztési pontról, ha az előnyben részesített terjesztési pontokon a szoftverfrissítések tartalma nem érhető el.  

    -   **Engedélyezése az ügyfelek számára az azonos alhálózatban lévő más ügyfelekkel tartalmat osszanak**: Adja meg, hogy engedélyezze a BranchCache használatát a tartalomletöltésekhez. A BranchCache szolgáltatással kapcsolatos további információkért lásd: [a Tartalomkezelés alapvető fogalmai](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Adja meg, hogy az intranethez kapcsolódó ügyfelek letöltsék-e a szoftverfrissítéseket a Microsoft Update webhelyről, ha a terjesztési pontokon nem érhetők el a szoftverfrissítések.  

    -   Adja meg, hogy engedélyezi-e az ügyfelek számára a telepítési határidő után történő letöltést, ha mért internetkapcsolatot használnak. Ha mért internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.  

    > [!NOTE]  
    >  Az ügyfelek egy felügyeleti ponttól kérik a központi telepítésben lévő szoftverfrissítések tartalomhelyét. A letöltési viselkedés a terjesztési pont, a központi telepítési csomag és az ezen a lapon szereplő beállítások konfigurációjától függ. További információk: [A tartalom forráshelyei – esetek](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

11. Ha elvégezte [3. lépés: A szoftverfrissítési csoporthoz tartozó tartalom letöltése](#BKMK_3DownloadContent), majd a központi telepítési csomag, a terjesztési pontok és a nyelv kiválasztása lap nem jelenik meg, és továbbléphet a varázsló 15. lépés-a.  

    > [!IMPORTANT]  
    >  A helykiszolgáló tartalomtárába korábban letöltött szoftverfrissítések nem lesznek újra letöltve. Ez akkor is igaz, ha új központi telepítési csomagot hoz létre a szoftverfrissítésekhez. Ha korábban már az összes szoftverfrissítés le lett töltve, a varázsló a **Nyelv kiválasztása** lapra lép (15. lépés).  

12. A Központi telepítési csomag lapon válasszon létező központi telepítési csomagot, vagy adja meg a következő beállításokat új központi telepítési csomag létrehozásához:  

    1.  **Név**: Adja meg a központi telepítési csomag nevét. Ennek a csomag tartalmát leíró egyedi névnek kell lennie. Legfeljebb 50 karakter hosszúságú lehet.  

    2.  **Leírás**: Adjon meg egy leírást, amely tájékoztatást ad azokról a központi telepítési csomagot. A leírás legfeljebb 127 karakter hosszúságú lehet.  

    3.  **Csomag forrása**: Adja meg a szoftverfrissítés forrásfájljainak helyét.  Írja be a forráshely hálózati elérési útját (például: **\\\\kiszolgáló\megosztásnév\elérési út**) vagy kattintson a **Tallózás** gombra a hálózati hely megkereséséhez. Mielőtt a következő lapra lép, létre kell hoznia a telepítőcsomag forrásfájljait tároló megosztott mappát.  

        > [!NOTE]  
        >  A telepítőcsomag megadott forráshelyét nem használhatja másik szoftvertelepítő csomag.  

        > [!IMPORTANT]  
        >  Az SMS Provider számítógép fiókjának és a varázslót a szoftverfrissítések letöltése céljából futtató felhasználónak is **Írás** NTFS-jogosultsággal kell rendelkeznie. Ügyeljen a letöltési hely hozzáférésének megfelelő korlátozására, hogy csökkentse a szoftverfrissítési forrásfájlok támadók általi módosításának kockázatát.  

        > [!IMPORTANT]  
        >  A Configuration Manager létrehoz a központi telepítési csomag után módosíthatja a csomag forráshelyét a telepítőcsomag tulajdonságaiban. Ekkor azonban a csomag eredeti forrásának tartalmát át kell másolnia az új forráshelyre.  

    4.  **Küldési prioritás**: Adja meg a központi telepítési csomag küldési prioritását. Configuration Manager terjesztési pontokra küldi a csomagot akkor használja a központi telepítési csomag küldési prioritását. Központi telepítési csomagok küldése a prioritásuk szerinti sorrendben történik: Magas, közepes vagy alacsony. Az azonos prioritású csomagokat a program a létrehozásuk sorrendjében küldi el. Ha nincs várakoztatás, a csomag feldolgozása azonnal elkezdődik, függetlenül a prioritásától.  

13. A Terjesztési pontok lapon adja meg a szoftverfrissítési fájlokat tartalmazó terjesztési pontokat vagy terjesztésipont-csoportokat. További információ a terjesztési pontokról: [A terjesztési pontok konfigurációi](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

14. A Letöltési hely lapon adja meg, hogy az internetről vagy a helyi hálózatról szeretné-e letölteni a szoftverfrissítési fájlokat. Adja meg a következő beállításokat:  

    -   **Szoftverfrissítések letöltése az internetről**: Válassza ezt a beállítást, a szoftverfrissítések letöltése egy adott helyen az interneten. A beállítás alapértelmezés szerint engedélyezve van.  

    -   **Szoftverfrissítések letöltése a helyi hálózatban lévő helyről**: Válassza ki az ezzel a beállítással a szoftverfrissítéseket egy helyi mappából vagy megosztott hálózati mappából töltheti le. A beállítás akkor lehet hasznos, ha a varázslót futtató számítógépen nincs internet-hozzáférés. A szoftverfrissítéseket előzetesen letöltheti internet-hozzáféréssel rendelkező számítógépre, majd a helyi hálózaton tárolhatja őket, hogy később elérhetők legyenek telepítés céljából.  

15. A Nyelv kiválasztása lapon adja meg azokat a nyelveket, amelyekhez a kiválasztott szoftverfrissítéseket le szeretné tölteni. A szoftverfrissítések csak akkor lesznek letöltve, ha elérhetők a kiválasztott nyelveken. A nem nyelvspecifikus szoftverfrissítések mindig letöltődnek. A varázsló alapértelmezés szerint kiválasztja azokat a nyelveket, amelyek a szoftverfrissítési pont tulajdonságaiban be vannak állítva. A következő lapra történő továbblépés előtt legalább egy nyelvet ki kell választani. Ha csak olyan nyelveket választ ki, amelyeket egy adott szoftverfrissítés nem támogat, akkor az adott szoftverfrissítés letöltése meghiúsul.  

16. Az Összegzés lapon ellenőrizze a beállításokat. A beállítások központi telepítési sablonba történő mentéséhez kattintson a **Mentés sablonként**elemre, írja be a sablon nevét, válassza ki a sablonban tárolni kívánt beállításokat, majd kattintson a **Mentés**gombra. Konfigurált beállítás módosításához kattintson a megfelelő varázslóoldalra, és módosítsa a beállítást.  

    > [!WARNING]  
    >  A sablon neve alfanumerikus ASCII-karaktereket, valamint **\\** (fordított perjel) és **‘** (szimpla idézőjel) karaktereket tartalmazhat.  

17. Kattintson a **Tovább** gombra a szoftverfrissítés központi telepítéséhez.  

 A varázsló befejezését követően a Configuration Manager letölti a szoftvert a helykiszolgálón lévő tartalomtárba frissítései, a szoftverfrissítések megadott terjesztési pontokra továbbítja, és ezután központilag telepíti a szoftverfrissítési csoportot a célgyűjteményben lévő ügyfelekre frissítse. További információ a központi telepítés folyamatáról: [Szoftverfrissítések központi telepítési folyamata](../understand/software-updates-introduction.md#BKMK_DeploymentProcess).

## <a name="next-steps"></a>További lépések
[Szoftverfrissítések figyelése](monitor-software-updates.md)

