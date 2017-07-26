---

title: "A szoftverfrissítések beállításainak kezelése |} Microsoft Docs"
description: "További tudnivalók az ügyfélbeállítások, amelyek a hely szoftverfrissítéseinek a szoftverfrissítési pont telepítése után."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/26/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 0d484c1a-e903-4bff-9e9b-e452c62e38a8
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fe4a8f56e0b554e206bcc4503a0268dc761ded81
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

#  <a name="BKMK_ManageSUSettings"></a>A szoftverfrissítések beállításainak kezelése  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután a Configuration Manager szoftverfrissítéseket szinkronizálja, konfigurálása, és ellenőrizze a beállításokat az alábbi szakaszok az.

##  <a name="BKMK_ClientSettings"></a> A szoftverfrissítésekhez tartozó ügyfélbeállítások  
A szoftverfrissítési pont telepítése után a szoftverfrissítések alapértelmezés szerint engedélyezve vannak az ügyfélgépeken, továbbá az ügyfélbeállítások **Szoftverfrissítések** oldalán az alapértelmezett értékek találhatók. Az ügyfélbeállítások helyszintű használatosak, és hatással vannak a szoftverfrissítések megfelelőségi vizsgálata, és hogyan és mikor történjen a szoftverfrissítések telepítése az ügyfélszámítógépeken. Szoftverfrissítések telepítése előtt győződjön meg arról, hogy az ügyfél beállításai megfelelőek-e a hely szoftverfrissítéseinek.  

> [!IMPORTANT]  
>  A **Szoftverfrissítések engedélyezése az ügyfeleken** beállítás alapértelmezés szerint engedélyezett. Ha törli ezt a beállítást, a Configuration Manager eltávolítja a meglévő központi telepítési házirendek az ügyfél.  

Ügyfél-beállítások konfigurálásával kapcsolatos további információkért lásd: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).  

Az ügyfél beállításaival kapcsolatos további információkért lásd: [kapcsolatos](../../core/clients/deploy/about-client-settings.md).  

##  <a name="BKMK_GroupPolicy"></a> A szoftverfrissítésekhez tartozó csoportházirend-beállítások  
A Windows Update Agent (WUA) meghatározott csoportházirend-beállításokat használ az ügyfélgépeken a szoftverfrissítési pontokon futó WSUS szolgáltatásokhoz való csatlakozáshoz. Ezek a csoportházirend-beállítások a szoftverfrissítés megfelelőségének sikeres vizsgálatához, valamint a szoftverfrissítések, valamint a WUA automatikus frissítéséhez is használhatók.

### <a name="specify-intranet-microsoft-update-service-location-local-policy"></a>Az intraneten futó Microsoft frissítési szolgáltatás helye házirend megadása  
Amikor szoftverfrissítési pontot hoz létre egy helyhez, a rendszer elküld az ügyfélgépeknek egy számítógép-házirendet, mely tartalmazza a szoftverfrissítési pont kiszolgálónevét, és beállítja **Az intraneten futó Microsoft frissítési szolgáltatás helye** helyi házirendet a számítógépen. A WUA lekéri az **Intranetes frissítési szolgáltatás beállítása frissítések észleléséhez** beállításban megadott kiszolgálónevet, majd csatlakozik ehhez a kiszolgálóhoz, amikor a szoftverfrissítések megfelelőségét vizsgálja. **Az intraneten futó Microsoft frissítési szolgáltatás helye** beállításhoz létrehozott tartományi házirend felülírja a helyi házirendet, és lehetővé teszi a WUA kapcsolódását a szoftverfrissítési pontoktól eltérő kiszolgálókhoz. Ha ez bekövetkezik, előfordulhat, hogy az ügyfél ellenőrzi a szoftverfrissítések megfelelőségét különböző termékek, besorolások és nyelvek szerint. Ennek megfelelően javasoljuk, hogy ne állítson be Active Directory házirendet az ügyfélgépekhez.  

### <a name="allow-signed-content-from-intranet-microsoft-update-service-location-group-policy"></a>Az intraneten futó Microsoft frissítési szolgáltatás helyéről származó aláírt tartalom engedélyezése  
Engedélyezni kell **Az intraneten futó Microsoft frissítési szolgáltatás helyéről származó aláírt tartalom engedélyezése** csoportházirendet, mielőtt a számítógépeken futó WUA keresni kezdi a System Center frissítés-közzétevője által létrehozott és közzétett szoftverfrissítéseket. Ha engedélyezve van a házirend beállítása, a WUA elfogadja az intranetes helyeken keresztül beérkező szoftverfrissítéseket, ha a szoftverfrissítések alá vannak írva a **Megbízható közzétevők** tanúsítvány-áruházban a helyi számítógépen. Ha további információkat szeretne a frissítés-közzétevő által igényelt csoportházirend-beállításokról, tanulmányozza az [Updates Publisher 2011 dokumentumkönyvtárát](http://go.microsoft.com/fwlink/p/?LinkId=232476).  

### <a name="automatic-updates-configuration"></a>Automatikus frissítések konfigurációja  
Az automatikus frissítések lehetővé teszik a biztonsági frissítések és egyéb fontos letöltések fogadását az ügyfélszámítógépeken. Az automatikus frissítéseket az **Automatikus frissítések konfigurációja** csoportházirend-beállításon vagy a helyi számítógép Vezérlőpultján keresztül lehet konfigurálni. Ha engedélyezve vannak az automatikus frissítések, az ügyfélszámítógépek értesítéseket kapnak a frissítésekről, és letöltik, majd telepítik a szükséges frissítéseket, a megadott beállításoktól függően. Ha egy időben vannak beállítva az automatikus frissítések és a szoftverfrissítések, előfordulhat, hogy az ügyfélszámítógépek ikonok és felugró ablakok formájában is értesítéseket jelenítenek meg ugyanarról a frissítésről. Ezenkívül előfordulhat, hogy ha újraindításra van szükség, minden ügyfélszámítógép újraindítást kérő párbeszédpanelt jelenít meg ugyanahhoz a frissítéshez.  

### <a name="self-update"></a>Önfrissítés  
Ha az automatikus frissítések engedélyezve vannak az ügyfélszámítógépeken, a WUA automatikusan önfrissítést hajt végre, amikor egy frissebb verzió elérhetővé válik, vagy ha problémák adódnak egy WUA-összetevővel. Ha az automatikus frissítések nincsenek konfigurálva vagy le vannak tiltva, és az ügyfélszámítógépek a WUA egy korábbi verzióját futtatják, az ügyfélszámítógépeken futtatni kell a WUA telepítőfájlját.  

## <a name="software-updates-properties"></a>A szoftverfrissítések tulajdonságai
A szoftverfrissítési tulajdonságok a szoftverfrissítésekről és a velük társított tartalmakról szolgálnak információval. Ezekkel a tulajdonságokkal a szoftverfrissítések beállításait is konfigurálhatja. Ha több szoftverfrissítéshez nyitja meg a tulajdonságokat, akkor csak a **Maximális futási idő** és az **Egyedi súlyosság** lap jelenik meg.   

A szoftverfrissítések tulajdonságainak megnyitásához kövesse az alábbi eljárást.  

#### <a name="to-open-software-update-properties"></a>Szoftverfrissítések tulajdonságainak megnyitása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  
2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések**csomópontot, majd kattintson a **Minden szoftverfrissítés**lehetőségre.  
3.  Jelöljön ki egy vagy több szoftverfrissítést, majd a **Kezdőlap** lapon lévő **Tulajdonságok** csoportban kattintson a **Tulajdonságok** gombra.  

   > [!NOTE]  
   >  Az a **minden szoftverfrissítés** csomópont, a Configuration Manager csak a szoftverfrissítéseket jeleníti meg a **kritikus** és **biztonsági** besorolású, az elmúlt 30 napban adtak ki.  

###  <a name="BKMK_SoftwareUpdatesInformation"></a> Szoftverfrissítési információk felülvizsgálata  
A szoftverfrissítési tulajdonságokban áttekintheti a szoftverfrissítéssel kapcsolatos részletes információkat. A részletes információk nem jelennek meg, ha egynél több szoftverfrissítést jelöl ki. A következő szakaszok a kiválasztott szoftverfrissítéssel kapcsolatos információkkal foglalkoznak.  

####  <a name="BKMK_SoftwareUpdateDetails"></a> Szoftverfrissítési információk  
A **Frissítés adatai** lapon a következő összefoglaló információkat tekintheti meg a kiválasztott szoftverfrissítésről:  

- **Közlemény azonosítója**: A biztonsági szoftverfrissítésekhez tartozó közleményazonosítót. A biztonsági közlemények részletei a [Microsoft Security Bulletin Search](http://go.microsoft.com/fwlink/p/?LinkId=58313) weboldalon találhatók meg a közleményazonosítóra rákeresve.  

- **Cikk azonosítója**: A szoftverfrissítés Cikkazonosítóját adja meg. A hivatkozott cikk részletesebb információkkal szolgál a szoftverfrissítésről, valamint a szoftverfrissítés által megoldott vagy enyhített problémáról.  

- **Dátuma**: Meghatározza, hogy a szoftverfrissítés legutóbbi módosításának dátumát.  

- **Maximális fontossági besorolás**: Megadja a szoftverfrissítés forgalmazó által meghatározott fontossági besorolását.  

- **Leírás**: Áttekintést állapotról a szoftverfrissítés által kijavított vagy enyhített biztosít.  

- **Alkalmazható nyelvek**: A szoftverfrissítés alkalmazható nyelveket sorolja fel.  

- **Érintett termékek**: A szoftverfrissítés alkalmazható termékeket sorolja fel.  

####  <a name="BKMK_ContentInformation"></a> Tartalom adatai  
A **Tartalom adatai** lapon a következő információkat tekintheti át a kiválasztott szoftverfrissítéshez kapcsolódó tartalomról:  

-   **Tartalomazonosító**: A szoftverfrissítés Tartalomazonosítóját határozza meg.  

-   **Letöltött**: Azt jelzi, hogy a Configuration Manager sikeresen letöltötte a szoftverfrissítési fájlokat.  

-   **Nyelvi**: A szoftverfrissítés nyelveit adja meg.  

-   **Forrás elérési útja**: Meghatározza a szoftverfrissítés forrásfájljainak elérési útvonalát.  

-   **Méret (MB)**: Adja meg a szoftverfrissítés forrásfájljainak méretét.  

####  <a name="BKMK_CustomBundleInformation"></a> Egyéni csomaginformáció  
Az **Egyéni csomaginformáció** lapon a szoftverfrissítéssel kapcsolatos egyéni csomaginformációkat tekintheti át. Ha a kiválasztott szoftverfrissítés együtt csomagolt szoftverfrissítéseket tartalmaz, amelyek a szoftverfrissítési fájlban találhatók, ezek a **Csomaginformáció** szakaszban jelennek meg. Ezen a lapon nem jelennek meg az olyan csomagolt szoftverfrissítések, amelyek a **Tartalom adatai** lapon láthatók, például a különböző nyelvekhez tartozó frissítési fájlok.  

####  <a name="BKMK_SupersedenceInformation"></a> Helyettesítési információk  
A **Helyettesítési információk** lapon a következő információkat tekintheti meg a szoftverfrissítés helyettesítési tulajdonságairól:  

- **A frissítés felül lett írva a következő szoftverfrissítések**: Adja meg a szoftverfrissítéseket, amelyek felülírják ezt a frissítést, ami azt jelenti, hogy a felsorolt frissítések újabbak. A legtöbb esetben a szoftverfrissítést felülíró elemek valamelyikét fogja központilag telepíteni. A listán megjelenített szoftverfrissítések olyan weboldalakra mutató hivatkozásokat tartalmaznak, amelyek további információkkal szolgálnak a szoftverfrissítésekről. Ha az adott frissítés nincs felülírva, a **Nincs** felirat látható.  

- **A frissítés a következő szoftverfrissítéseket írja felül**: Adja meg a szoftverfrissítéseket, amelyek a szoftverfrissítési, ami azt jelenti, hogy a szoftverfrissítés újabb náluk. A legtöbb esetben a szoftverfrissítést az általa felülírt elemek leváltására fogja központilag telepíteni. A listán megjelenített szoftverfrissítések olyan weboldalakra mutató hivatkozásokat tartalmaznak, amelyek további információkkal szolgálnak a szoftverfrissítésekről. Ha az adott frissítés nem ír felül más frissítéseket, a **Nincs** felirat látható.  

###  <a name="BKMK_SoftwareUpdatesSettings"></a> A szoftverfrissítések beállításainak konfigurálása  
A tulajdonságok között egy vagy több szoftverfrissítés beállításait konfigurálhatja. A legtöbb szoftverfrissítési beállítást csak a központi adminisztrációs helyen vagy önálló elsődleges helyen konfigurálhatja. A következő szakaszok a szoftverfrissítések beállításainak konfigurálásához nyújtanak segítséget.  

####  <a name="BKMK_SetMaxRunTime"></a> Maximális futási idő beállítása  
A **Maximális futási idő** lapon adja meg a szoftverfrissítés számára engedélyezett maximális időt a frissítés befejezéséhez az ügyfélszámítógépeken. Ha a frissítés tovább tart, mint a maximális futási időnél, a Configuration Manager állapotüzenetet hoz létre, és leállítja a szoftverfrissítések telepítése központi telepítésének figyelését. Ezt a beállítást csak a központi adminisztrációs helyen vagy önálló elsődleges helyen konfigurálhatja.  

Configuration Manager is használja ezt a beállítást annak megállapításához, hogy kezdeményezheti a szoftverfrissítés telepítését egy konfigurált karbantartási időszakban. Ha a maximális futási idő nagyobb, mint a karbantartási időszakból hátralévő elérhető idő, a szoftverfrissítések telepítése a következő karbantartási időszak kezdetére lesz elhalasztva. Ha több szoftverfrissítést kell telepíteni egy olyan ügyfélszámítógépre, amelyen karbantartási időszak (időkeret) van beállítva, a legrövidebb maximális futási idővel rendelkező szoftverfrissítés telepítése történik meg elsőként, majd ezt követi a következő legrövidebb futási idejű frissítés telepítése, és így tovább. Mielőtt telepítené az egyes szoftverfrissítéseket, az ügyfél ellenőrzi, hogy a karbantartási időszakból hátralévő idő elegendő-e a szoftverfrissítés telepítésére. Ha egy szoftverfrissítés már megkezdte a telepítést, az a karbantartási időszak végének elérését követően is folytatódik. További információ a karbantartási időszakokról: [Karbantartási időszakok használata a System Center Configuration Managerben](../../core/clients/manage/collections/use-maintenance-windows.md).  

A **Maximális futási idő** lapon a következő beállításokat tekintheti meg és konfigurálhatja:  

- **Maximálisan engedélyezett futási időt**: A szoftverfrissítés telepítése előtt a telepítés figyelését a Configuration Manager által kiosztott perc maximális számát határozza meg. A rendszer ezt a beállítást használja annak a megállapításához is, hogy a karbantartási időszakból hátralévő idő elegendő-e a frissítés telepítéséhez. Az alapértelmezett érték 60 perc a szervizcsomagok esetében. Egyéb szoftverek frissítés típusok esetén az alapértelmezett érték 10 perc új telepítést végrehajtani a Configuration Manager verziója 1511-es vagy magasabb szintű és 5 perc, ha egy korábbi verziójáról frissített tette. Az érték 5 és 9999 perc között lehet.  

> [!IMPORTANT]  
>  Ügyeljen arra, hogy a maximális futási időt mindig rövidebbre állítsa a karbantartási időszakhoz beállított időnél. Ellenkező esetben a szoftverfrissítés soha nem fog elindulni.  

####  <a name="BKMK_SetCustomSeverity"></a> Egyedi súlyosság beállítása  
A szoftverfrissítés tulajdonságai között egyéni fontossági értékeket állíthat be a szoftverfrissítések számára a **Fontosság testreszabása** lapon. Erre akkor lehet szükség, ha az előre meghatározott fontossági értékek nem felelnek meg az igényeknek. Az egyéni értékek a **egyéni fontossági** oszlop a Configuration Manager konzolon. Rendezheti a szoftverfrissítéseket az egyéni fontossági értékek szerint, illetve lekérdezéseket és jelentéseket készíthet, ezeket az értékeket alkalmazva szűrőként. Ez a beállítás csak a központi adminisztrációs helyen és az önálló elsődleges helyeken adható meg.  

A következő beállításokat lehet megadni a **Fontosság testreszabása** lapon.  

- **Egyéni fontosság**: Beállítja a szoftverfrissítések egyéni fontossági értékét. Válassza ki a megfelelő értéket a listából: **kritikus**, **fontos**, **mérsékelt**vagy **alacsony** . Az egyéni fontosság alapértelmezésben üres.

## <a name="crl-checking-for-software-updates"></a>CRL-ellenőrzés a szoftverfrissítések
Alapértelmezés szerint a visszavont tanúsítványok listáját (CRL) nem kerül ellenőrzésre a System Center Configuration Manager szoftverfrissítések tartozó aláírás ellenőrzésekor. A visszavonttanúsítvány-lista minden alkalommal történő ellenőrzése nagyobb védelmet kínál a visszavont tanúsítványokkal szemben, de csatlakozási késedelmet és többlet feldolgozást eredményez a CRL-ellenőrzést végző számítógépeken.  

Ha használ, a CRL-ellenőrzés engedélyeznie kell a szoftverfrissítéseket feldolgozó Configuration Manager-konzol.  

#### <a name="to-enable-crl-checking"></a>A CRL-ellenőrzés engedélyezése  
A termék DVD-JÉRŐL, a CRL-ellenőrzést végrehajtó számítógépen futtassa a parancssorból a következő: **\SMSSETUP\BIN\X64\\**<*nyelvi*>**\UpdDwnldCfg.exe /checkrevocation**.  

Például angol (amerikai) futtatása **\SMSSETUP\BIN\X64\00000409\UpdDwnldCfg.exe /checkrevocation**  

