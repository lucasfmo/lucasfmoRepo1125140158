1.  A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **szoftverfrissítések**.  

2.  Válassza ki a letölteni kívánt szoftverfrissítést a következő módszerek egyikével:  

    -   Jelöljön ki egy vagy több szoftverfrissítési csoportot a **Szoftverfrissítési csoportok**területen, majd a **Kezdőlap** lapon lévő **Frissítési csoport** csoportban kattintson a **Letöltés**elemre.  

    -   Jelöljön ki egy vagy több szoftverfrissítést a **Minden szoftverfrissítés**területen, majd a **Kezdőlap** lapon lévő **Frissítés** csoportban kattintson a **Letöltés**elemre.  

        > [!NOTE]  
        >  Az a **minden szoftverfrissítés** csomópont, a Configuration Manager szoftverfrissítéseket jeleníti meg csak egy **kritikus** és **biztonsági** besorolás, amely az elmúlt 30 napban adtak ki.  

        > [!TIP]  
        >  A **Feltétel hozzáadása** elemre kattintva szűrheti azokat a szoftverfrissítéseket, amelyek a **Minden szoftverfrissítés** csomóponton jelennek meg. A gyakran használt feltételeket mentheti, a mentett kereséseket pedig a **Keresés** lapon kezelheti.  

         Elindul a **Szoftverfrissítések letöltése varázsló** .  

3.  A **Központi telepítési csomag** lapon adja meg a következő beállításokat:  

    1.  **Központi telepítési csomag kiválasztása**: Válassza ezt a beállítást egy meglévő központi telepítési csomagot a szoftverfrissítések, a központi telepítésben lévő szoftverfrissítésekhez.  

        > [!NOTE]  
        >  A kiválasztott központi telepítési csomagba korábban már letöltött szoftverfrissítések nem lesznek újra letöltve.  

    2.  **Hozzon létre egy új központi telepítési csomag**: Válassza ezt a beállítást, amelyek a központi telepítésben lévő szoftverfrissítések egy új központi telepítési csomag létrehozásához. Adja meg a következő beállításokat:  

        -   **Név**: Megadja a központi telepítési csomag nevét. A csomagnak a csomag tartalmát röviden leíró egyedi nevet kell adni.  Legfeljebb 50 karakter hosszúságú lehet.  

        -   **Leírás**: Adja meg a központi telepítési csomag leírása. A csomag leírása a csomag tartalmáról ad információt, és legfeljebb 127 karakterből állhat.  

        -   **Csomag forrása**: Megadja a szoftverfrissítés forrásfájljainak helyét. Írja be a forráshely hálózati elérési útját (például: **\\\\kiszolgáló\megosztásnév\elérési út**) vagy kattintson a **Tallózás** gombra a hálózati hely megkereséséhez. Mielőtt a következő lapra lép, létre kell hoznia a telepítőcsomag forrásfájljait tároló megosztott mappát.  

            > [!NOTE]  
            >  A telepítőcsomag megadott forráshelyét nem használhatja másik szoftvertelepítő csomag.  

            > [!IMPORTANT]  
            >  Az SMS Provider számítógép fiókjának és a varázslót a szoftverfrissítések letöltése céljából futtató felhasználónak is **Írás** NTFS-jogosultsággal kell rendelkeznie. Ügyeljen a letöltési hely hozzáférésének megfelelő korlátozására, hogy csökkentse a szoftverfrissítési forrásfájlok támadók általi módosításának kockázatát.  

            > [!IMPORTANT]  
            >  A Configuration Manager létrehoz a központi telepítési csomag után módosíthatja a csomag forráshelyét a telepítőcsomag tulajdonságaiban. Ekkor azonban a csomag eredeti forrásának tartalmát át kell másolnia az új forráshelyre.  

     Kattintson a **Tovább** gombra.  

4.  Az a **terjesztési pontok** adja meg azokat a terjesztési pontokat vagy terjesztésipont-csoportokat, amelyek a szoftverfrissítési fájlokat tartalmazó, és kattintson a **következő**. További információ a terjesztési pontokról: [A terjesztési pontok konfigurációi](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

    > [!NOTE]  
    >  A Terjesztési pontok lap csak akkor érhető el, ha új szoftverfrissítési célú központi telepítési csomagot hoz létre.  

6.  Az a **terjesztési beállítások** lapján adja meg a következő beállításokat:  

    -   **Terjesztési prioritás**: Ez a beállítás segítségével megadhatja a központi telepítési csomag terjesztési prioritását. A terjesztési prioritás a központi telepítési csomag gyermekhelyeken lévő terjesztési pontokra történő küldése során érvényesül. Központi telepítési csomagok küldése a prioritásuk szerinti sorrendben történik: **High**, **Medium**, or **Low**. Az azonos prioritású csomagokat a program a létrehozásuk sorrendjében küldi el. Ha nincs várakoztatás, a csomag feldolgozása azonnal elkezdődik, függetlenül a prioritásától. Alapértelmezés szerint a csomagok küldése **Közepes** prioritással történik.  

    -   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az**: Ez a beállítás használatával engedélyezhető az igény szerinti tartalomterjesztést az előnyben részesített terjesztési pontokra. Ha ez a beállítás engedélyezve van, a felügyeleti pont eseményindítót hoz létre a terjesztéskezelő számára, hogy az összes előnyben részesített terjesztési pontra terjessze a tartalmat, ha egy ügyfél a csomaghoz tartozó tartalmat igényel, és a tartalom nem áll rendelkezésre egyetlen előnyben részesített terjesztési ponton sem. További tudnivalók az előnyben részesített terjesztési pontokról és az igény szerinti tartalomterjesztésről: [A tartalom forráshelyei – esetek](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

    -   **Manuálisan előkészített terjesztési pontok beállításai**: Ez a beállítás használatával adja meg, hogyan kívánja terjeszteni a tartalmakat a manuálisan előkészített terjesztési pontokra. Válasszon egyet az alábbi lehetőségek közül:  

        -   **Tartalom automatikus letöltése, amikor csomagok vannak hozzárendelve a terjesztési pontokra**: Ez a beállítás segítségével figyelmen kívül hagyhatja a manuális előkészítési beállításokat, és a terjesztési pontra továbbít tartalmat.  

        -   **Csak a tartalmi változások letöltése a terjesztési pontra**: A beállítás segítségével manuálisan előkészítheti az eredeti tartalmat a terjesztési pontra, és majd a terjesztési pontra tartalom változásait terjesztheti.  

        -   **Tartalmának manuális másolása a csomag a terjesztési pontra**: Ez a beállítás segítségével mindig manuálisan előkészíti a tartalmat a terjesztési ponton. Ez az alapértelmezett beállítás.  

         További információ a tartalom manuális előkészítéséről a terjesztési pontokon: [Manuálisan előkészített tartalom használata](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Kattintson a **Tovább** gombra.  

6.  Az a **letöltési hely** adja meg azokat a helyre, amely a Configuration Manager a szoftverfrissítési forrásfájlok letöltéséhez fog használni. Válasszon az alábbi lehetőségek közül:  

    -   **Szoftverfrissítések letöltése az internetről**: Válassza ezt a beállítást, a szoftverfrissítéseket az internetes helyről töltheti le. Ez az alapértelmezett beállítás.  

    -   **Szoftverfrissítések letöltése a helyi hálózatban lévő helyről**: Válassza ki az ezzel a beállítással a szoftverfrissítéseket egy helyi mappából vagy megosztott hálózati mappából töltheti le. Akkor használja ezt a beállítást, ha a varázslót futtató számítógépen nincs internet-hozzáférés.  

        > [!NOTE]  
        >  Ha ezt a beállítást használja, töltse le a szoftverfrissítéseket egy internet-hozzáféréssel rendelkező számítógépre, majd másolja őket a helyi hálózaton egy olyan helyre, amely elérhető a varázslót futtató számítógépről.  

     Kattintson a **Tovább** gombra.  

7.  Az a **nyelv kiválasztása** adja meg azokat a nyelveket, amelyek a kijelölt szoftverfrissítések tölthető le, majd **következő**. A Configuration Manager letölti a szoftverfrissítéseket, csak akkor, ha elérhetők a kiválasztott nyelveken. A nem nyelvspecifikus szoftverfrissítések mindig letöltődnek.  

8. Az a **összegzés** lapon ellenőrizze a varázslóban megadott beállításokat, és kattintson a **következő** gombra a szoftverfrissítések letöltéséhez.  

9. Az a **befejezési** lapon, győződjön meg arról, hogy a szoftverfrissítések letöltése sikeresen megtörtént-e, és kattintson a **Bezárás**.  
