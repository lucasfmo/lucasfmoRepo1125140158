---
title: "Konfigurálja a jelentéskészítési |} Microsoft Docs"
description: "Olvassa el, hogyan állíthat be a Configuration Manager-hierarchiában, beleértve az SQL Server Reporting Services jelentési."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: aed95333b6509b0aa7061f23969381f1ce8aff7f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-reporting-in-system-center-configuration-manager"></a>A jelentéskészítés konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt létrehozása, módosítása és jelentések futtatása a System Center Configuration Manager-konzolon, egy sor konfigurációs feladatot kell elvégeznie. Ez a témakör következő részeiben használatával alakítsa ki a Configuration Manager-hierarchia jelentéskészítési beállítások konfigurálásához:  

 Mielőtt folytatná telepítése és konfigurálása a Reporting Services a hierarchiában, tekintse át a következő Configuration Manager jelentéskészítési témakörök:  

-   [A System Center Configuration Manager jelentéskészítésének bemutatása](../../../core/servers/manage/introduction-to-reporting.md)  

-   [A System Center Configuration Managerben a jelentéskészítés tervezése](../../../core/servers/manage/planning-for-reporting.md)  

##  <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 Az SQL Server Reporting Services egy kiszolgálóalapú jelentéskészítési platform, amely átfogó jelentéskészítési funkciókat biztosít a különféle adatforrásokhoz. A jelentéskészítési szolgáltatási pontot a Configuration Manager SQL Server Reporting Services Configuration Manager-jelentések másolása a megadott jelentésmappába, konfigurálja a Reporting Services beállításait és a Reporting Services biztonsági beállításaival kommunikál. A Reporting Services csatlakozik a Configuration Manager Helyadatbázis beolvasni a jelentések futtatásakor visszaadott adatokat.  

 A jelentéskészítési szolgáltatási pontot a Configuration Manager-hely telepítése előtt, telepítenie és konfigurálnia kell az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont helyrendszerszerepkört üzemeltető helyrendszeren. További információ a Reporting Services telepítéséről: [SQL Server TechNet könyvtár](http://go.microsoft.com/fwlink/p/?LinkId=266389).  

 A következő művelettel ellenőrizheti, hogy az SQL Server Reporting Services telepítve van-e és megfelelően működik-e.  

#### <a name="to-verify-that-sql-server-reporting-services-is-installed-and-running"></a>Az SQL Server Reporting Services telepítésének és működésének ellenőrzése  

1.  Kattintson a **Start**gombra, és válassza a **Minden program**, a **Microsoft SQL Server 2008 R2**, a **Konfigurációs eszközök**, és végül a **Reporting Services Configuration Manager**parancsot.  

2.  A **Reporting Services konfigurációs kapcsolata** párbeszédpanelen adja meg az SQL Server Reporting Services szolgáltatásokat futtató kiszolgáló nevét, a menüben válassza ki azt az SQL Server-példányt, amelyre az SQL Reporting Services szolgáltatásokat telepítette, és kattintson a **Csatlakozás**gombra. Megnyílik a Reporting Services Configuration Manager.  

3.  A **Jelentéskészítő kiszolgáló állapota** lapon ellenőrizze, hogy a **Jelentéskészítési szolgáltatás állapota** elem **Elindítva**értékű-e. Ha nem, kattintson az **Indítás**elemre.  

4.  A **Webszolgáltatás URL-címe** lapon kattintson a **Jelentéskészítési szolgáltatás webszolgáltatásának URL-címei** beállításnál lévő URL-címre a jelentéseket tartalmazó mappával létrehozott kapcsolat ellenőrzéséhez. Előfordulhat, hogy megjelenik a **Windows rendszerbiztonság** párbeszédpanel, és kéri a biztonsági hitelesítő adatainak megadását. Alapértelmezés szerint az Ön felhasználói fiókja jelenik meg. Írja be a jelszavát, és kattintson az **OK**gombra. Ellenőrizze, hogy megjelenik-e a weblap. Zárja be a böngészőablakot.  

5.  Az **Adatbázis** lapon ellenőrizze, hogy a **Jelentéskészítő kiszolgáló üzemmódja** beállítás **Natív**értékű-e.  

6.  A **Jelentéskezelő URL-címe** lapon kattintson a **Jelentéskezelő webhely azonosítása** beállításnál lévő URL-címre a Jelentéskezelő virtuális könyvtárával létrehozott kapcsolat ellenőrzéséhez. Előfordulhat, hogy megjelenik a **Windows rendszerbiztonság** párbeszédpanel, és kéri a biztonsági hitelesítő adatainak megadását. Alapértelmezés szerint az Ön felhasználói fiókja jelenik meg. Írja be a jelszavát, és kattintson az **OK**gombra. Ellenőrizze, hogy megjelenik-e a weblap. Zárja be a böngészőablakot.  

    > [!NOTE]  
    >  Reporting Services Jelentéskezelője nem szükséges a jelentéskészítéshez a Configuration Managerben, de akkor szükség, ha a jelentések futtatásához a böngészőben, vagy a Jelentéskezelő használatával szeretné kezelni.  

7.  Kattintson a **kilépési** Reporting Services Configuration Manager bezárásához.  

##  <a name="BKMK_ReportBuilder3"></a> A jelentéskészítés konfigurálása a Jelentéskészítő 3.0 használatára  

#### <a name="to-change-the-report-builder-manifest-name-to-report-builder-30"></a>A Jelentéskészítő jegyzékfájlnevének megváltoztatása a Jelentéskészítő 3.0 verzióra  

1.  A Configuration Manager konzolt futtató számítógépen nyissa meg a Windows Beállításszerkesztőt.  

2.  Keresse meg a **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**bejegyzést.  

3.  Kattintson duplán a **ReportBuilderApplicationManifestName** kulcsra az érték szerkesztéséhez.  

4.  A **ReportBuilder_2_0_0_0.application** értéket módosítsa a **ReportBuilder_3_0_0_0.application**értékre, és kattintson az **OK**gombra.  

5.  Zárja be a Windows Beállításszerkesztőt.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> Jelentéskészítési szolgáltatási pont telepítése  
 A jelentéskészítési szolgáltatási pontot telepíteni kell arra a helyre, amelyen jelentéseket szeretne kezelni. A jelentéskészítési szolgáltatási pont átmásolja a jelentésmappákat és a jelentéseket az SQL Server Reporting Services szolgáltatásokba, alkalmazza a jelentések és a mappák biztonsági irányelveit, és megadja a konfigurációs beállításokat a Reporting Services szolgáltatásokban. Konfigurálnia kell egy jelentéskészítési szolgáltatási pontot ahhoz jelentések jelennek meg a Configuration Manager konzolon, és a Configuration Manager jelentések kezeléséhez. A jelentéskészítési szolgáltatási pont egy helyrendszerszerepkör, amelyet olyan kiszolgálón kell konfigurálni, amelyen telepítve van és működik a Microsoft SQL Server Reporting Services. Előfeltételeivel kapcsolatos további információkért lásd: [a jelentéskészítés előfeltételei](prerequisites-for-reporting.md).  

> [!IMPORTANT]  
>  Amikor helyet választ a jelentéskészítési szolgáltatási pont telepítéséhez, vegye figyelembe, hogy jelentésekhez hozzáférő felhasználóknak ugyanabban a biztonsági hatókörben kell lenniük, mint annak a helynek, amelyre a jelentéskészítési szolgáltatási pontot telepíti.  

> [!IMPORTANT]  
>  Miután telepített egy jelentéskészítési szolgáltatási pontot egy helyrendszerre, ne módosítsa a jelentéskészítő kiszolgáló URL-címét. Ha hoz létre, a jelentéskészítési szolgáltatási pontot, majd a Reporting Services Configuration Manager alkalmazásban módosítja a jelentéskészítő kiszolgáló URL-CÍMÉT, például a Configuration Manager konzol továbbra is a régi URL-címet használja, és nem lehet futtatása, szerkesztése vagy létrehozása a jelentések a konzolon. Ha meg kell változtatnia a jelentéskészítő kiszolgáló URL-címét, távolítsa el a jelentéskészítési szolgáltatási pontot, módosítsa az URL-címet, majd telepítse újra a jelentéskészítési szolgáltatási pontot.  

 A jelentéskészítési szolgáltatási pontot a következő művelet végrehajtásával telepítheti.  

#### <a name="to-install-the-reporting-services-point-on-a-site-system"></a>A jelentéskészítési szolgáltatási pont telepítése helyrendszerre  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**lehetőségre.  

    > [!TIP]  
    >  Ha csak azokat a helyrendszereket kívánja megjeleníteni, amelyek tartalmazzák a jelentéskészítési szolgáltatási pont helyrendszerszerepkört, az egér jobb gombjával kattintson a **Kiszolgálók és helyrendszerszerepkörök** elemre, és válassza a **Jelentéskészítési szolgáltatási pont**lehetőséget.  

3.  Vegye fel a jelentéskészítési szolgáltatási pont helyrendszerszerepkört új vagy meglévő helyrendszerbe a következő lépésben leírtak szerint:  

    > [!NOTE]  
    >  További információ a helyrendszerek konfigurálásáról lásd: [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](../deploy/configure/add-site-system-roles.md).  

    -   **Új helyrendszer**: A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Helyrendszer-kiszolgáló létrehozása** lehetőségre. Megjelenik a **Helyrendszer-kiszolgáló létrehozása varázsló** .  

    -   **Meglévő helyrendszer**: Kattintson arra a kiszolgálóra, amely a jelentéskészítési szolgáltatási pont helyrendszerszerepkört telepíteni kívánja. Amikor rákattint egy kiszolgálóra, az eredmények ablaktáblájában megjelenik a kiszolgálóra már telepített helyrendszerszerepkörök listája.  

         A **Kezdőlap** **Kiszolgáló** csoportjában kattintson a **Helyrendszerszerepkörök hozzáadása**lehetőségre. Megjelenik a **Helyrendszer-szerepkörök hozzáadása varázsló** .  

4.  Az **Általános** lapon adja meg a helyrendszer-kiszolgáló általános beállításait. Amikor a jelentéskészítési szolgáltatási pontot egy meglévő helyrendszer-kiszolgálóra veszi fel, ellenőrizze a korábban megadott értékeket.  

5.  A **Rendszerszerepkör kiválasztása** lapon az elérhető szerepkörök listájából válassza ki a **Jelentéskészítési szolgáltatási pont** elemet, majd kattintson a **Tovább**gombra.  

6.  A **Jelentéskészítési szolgáltatási pont** lapon adja meg a következő beállításokat:  

    -   **Helyadatbázis-kiszolgáló neve**: Adja meg a Configuration Manager helyadatbázisát futtató kiszolgáló nevét. A varázsló rendszerint a kiszolgáló teljes tartománynevét kéri le. Adatbázispéldány megadásához használja a formátum &lt; *kiszolgálónév*>\&lt; *Példány neve*>.  

    -   **Az adatbázisnév**: Adja meg a Configuration Manager Helyadatbázis nevét, és kattintson **ellenőrizze** annak ellenőrzéséhez, hogy a varázsló hozzáfér a helyadatbázishoz.  

        > [!IMPORTANT]  
        >  A jelentéskészítési szolgáltatási pontot létrehozó felhasználói fióknak **Olvasás** hozzáféréssel kell rendelkeznie a helyadatbázishoz. Ha a kapcsolat ellenőrzése sikertelen, piros figyelmeztető ikon jelenik meg. A hiba részleteinek megjelenítéséhez vigye a mutatót erre az ikonra. Javítsa ki a hibát, és kattintson a **Tesztelés** gombra.  

    -   **Mappa neve**: Adja meg a létrehozott és a Reporting Services Configuration Manager jelentések futtatására használt mappa nevét.  

    -   **Reporting Services szolgáltatások kiszolgálópéldánya**: A listában jelölje ki a példány az SQL Server Reporting Services rendszerhez. Ha csak egy példány érhető el, alapértelmezés szerint ki van jelölve. Ha nincsenek példányok, ellenőrizze, hogy az SQL Server Reporting Services szolgáltatások telepítve vannak-e és be vannak-e állítva, valamint azt, hogy az SQL Server Reporting Services szolgáltatások el vannak-e indítva a helyrendszeren.  

        > [!IMPORTANT]  
        >  A Configuration Manager kapcsolódott az aktuális felhasználó környezetében a Windows Management Instrumentation (WMI) szolgáltatással a választott helyrendszeren lekérni az SQL Server-példányt a Reporting Services. Az aktuális felhasználónak **Olvasás** engedéllyel kell rendelkeznie a WMI eléréséhez a helyrendszeren, máskülönben a Reporting Services-példány nem kérhető le.  

    -   **Jelentéskészítési szolgáltatási pont fiókja**: Kattintson a **beállítása**, és jelölje ki a fiókot használja az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont csatlakozik a Configuration Manager helyadatbázishoz a jelentésekben megjelenített adatok lekéréséhez. Válassza ki **létező fiók** adjon meg egy Windows felhasználói fiókot, amely már be lett állítva a Configuration Manager-fiókként, vagy válasszon **új fiók** meg egy Windows felhasználói fiókot, amely a Configuration Manager fiók nincs beállítva. A Configuration Manager automatikusan hozzáférést a megadott felhasználónak a helyadatbázishoz. A felhasználó megjelenik az **Adminisztráció** munkaterület **Biztonság** csomópontjának **Fiókok** almappájában a **ConfigMgr jelentési szolgáltatási pont** fióknévvel.  

         A Reporting Services futtatásához használt fióknak a tartomány **Windows-hitelesítés hozzáférési csoport**helyi biztonsági csoportjához kell tartoznia, és az **Olvasás** engedélyének **Engedélyezés**értékűnek kell lennie.  

         A megadott Windows felhasználói fiókot és jelszót a Reporting Services adatbázisa tárolja titkosított formában. A Reporting Services e fiók és jelszó használatával kéri le a jelentések adatait a helyadatbázisból.  

        > [!IMPORTANT]  
        >  A megadott fióknak rendelkeznie kell a **Helyi bejelentkezés engedélyezése** engedéllyel a Reporting Services adatbázisát tartalmazó számítógépen.  

7.  A **Jelentéskészítési szolgáltatási pont** lapon kattintson a **Tovább**gombra.  

8.  Az **Összefoglalás** lapon ellenőrizze a beállításokat, majd kattintson a **Tovább** gombra.  

     A varázsló befejezése után létrejönnek a jelentésmappák, és a Configuration Manager jelentései másolja a megadott jelentésmappákba.  

    > [!NOTE]  
    >  Létrejönnek a jelentésmappák, és a jelentések jelentéskészítő kiszolgálóra történő átmásolása, a Configuration Manager meghatározza az objektumoknak megfelelő nyelvet. Ha a kapcsolódó nyelvi csomag telepítve van a helyen, a Configuration Manager a helyen, a jelentéskészítő kiszolgálón futó operációs rendszer nyelvével azonos nyelven hozza létre az objektumokat. Ha a nyelv nem érhető el, a jelentések angol nyelven készülnek el és jelennek meg. Amikor nyelvi csomagok nélkül telepít jelentéskészítési szolgáltatási pontot egy helyre, a jelentések angol nyelven lesznek telepítve. Ha a jelentéskészítési szolgáltatási pont telepítése után telepít nyelvi csomagot, el kell távolítania, majd újra kell telepítenie a jelentéskészítési szolgáltatási pontot, hogy a jelentések a megfelelő nyelvi csomag nyelvén legyenek elérhetők. További információ a nyelvi csomagok: [nyelvi csomagokat a System Center Configuration Managerben](../deploy/install/language-packs.md).  

###  <a name="BKMK_FileInstallationAndSecurity"></a> Fájlok telepítése és jelentésmappák biztonsági jogosultságai  
 A Configuration Manager telepítéséhez a jelentéskészítési szolgáltatási pont és a Reporting Services konfigurálásához a következő műveleteket hajtja végre:  

> [!IMPORTANT]  
>  A következő listán szereplő műveletek végrehajtása az SMS_Executive szolgáltatáshoz beállított fiók hitelesítő adataival történik; ez általában a helyrendszer helyi rendszerfiókja.  

-   Telepíti a jelentéskészítési szolgáltatási pont helyrendszerszerepkört.  

-   Létrehozza az adatforrást a Reporting Services szolgáltatásokban a varázslóban megadott hitelesítő adatok használatával. Ezek az adatok a Windows felhasználói fiók és jelszó, amelyet a Reporting Services a helyadatbázishoz való csatlakozáshoz használ a jelentések futtatásakor.  

-   Hoz létre a Configuration Manager gyökérmappáját a Reporting Services szolgáltatásokban.  

-   Felveszi a **ConfigMgr jelentés felhasználói** és a **ConfigMgr jelentés rendszergazdái** biztonsági szerepkört a Reporting Services szolgáltatásokba.  

-   Létrehozza az almappákat, és telepíti a Configuration Manager jelentéseit a %ProgramFiles%\SMS_SRSRP mappából a Reporting Services.  

-   Hozzáadja a **ConfigMgr jelentés felhasználói** szerepkört a Reporting Services felhasználói fiókok a Configuration Manager rendelkező gyökérmappájához **hely olvasása** jogok.  

-   Hozzáadja a **ConfigMgr jelentés rendszergazdái** szerepkört a Reporting Services felhasználói fiókok a Configuration Manager rendelkező gyökérmappájához **hely módosítása** jogok.  

-   Lekéri a jelentésmappák és a Configuration Manager biztonságos objektumtípusai (őrzi meg a rendszer a Configuration Manager Helyadatbázis) közötti leképezést.  

-   A következő jogosultságok a rendszergazda felhasználók részére a Configuration Manager úgy konfigurálja a Reporting Services meghatározott jelentésmappáira:  

    -   Hozzáadja a felhasználókat, és hozzárendeli a **ConfigMgr jelentés felhasználói** szerepkört azon rendszergazda felhasználók, akik rendelkeznek a társított jelentésmappához **jelentés futtatása** a Configuration Manager objektum engedélyeit.  

    -   Hozzáadja a felhasználókat, és hozzárendeli a **ConfigMgr jelentés rendszergazdái** szerepkört azon rendszergazda felhasználók, akik rendelkeznek a társított jelentésmappához **jelentés módosítása** a Configuration Manager objektum engedélyeit.  

     A Configuration Manager csatlakozik a Reporting Serviceshez, és a Configuration Manager és a Reporting Services legfelső szintű mappák és meghatározott jelentésmappáihoz rendelt felhasználók engedélyeinek megadása. A jelentéskészítési szolgáltatási pont első telepítése után a Configuration Manager csatlakozik a Reporting Services egy 10 perces időközt ellenőrizze, hogy a jelentésmappákon konfigurált felhasználói jogosultságok a Configuration Manager-felhasználók számára beállított, társított jogosultságok. Ha ad hozzá felhasználókat vagy módosítanak felhasználói jogosultságokat a jelentéseket tartalmazó mappával a Reporting Services Jelentéskezelője segítségével, a Configuration Manager a helyadatbázisban tárolt, szerepkörön alapuló hozzárendeléseket használva felülírja ezeket a módosításokat. A Configuration Manager eltávolítja a felhasználók, amelyek nem rendelkeznek jelentéskészítési jogosultságokkal a Configuration Manager alkalmazásban is.  

##  <a name="BKMK_SecurityRoles"></a> A Reporting Services a Configuration Manager alkalmazáshoz használható biztonsági szerepkörei  
 A Configuration Manager telepíti a jelentéskészítési szolgáltatási pontot, ha az a következő biztonsági szerepköröket veszi fel a Reporting Services:  

-   **ConfigMgr jelentés felhasználói**: A biztonsági szerepkörrel rendelkező felhasználók csak futtatni tudják a Configuration Manager-jelentések.  

-   **ConfigMgr jelentés rendszergazdái**: A biztonsági szerepkörrel rendelkező felhasználók a Configuration Manager jelentéskészítéssel kapcsolatos minden feladatot elvégezhetnek.  

##  <a name="BKMK_VerifyReportingServicesPointInstallation"></a> A jelentéskészítési szolgáltatási pont telepítésének ellenőrzése  
 A jelentéskészítési szolgáltatási pont helyszerepkörének hozzáadása után meghatározott állapotüzeneteket és naplófájlbejegyzéseket átnézve ellenőrizheti a telepítést. A következő eljárás segítségével ellenőrizheti, hogy a jelentéskészítési szolgáltatási pont telepítése sikerült-e.  

> [!WARNING]  
>  Ezt az eljárást kihagyhatja, ha a jelentések megjelenjenek a **jelentések** almappájában a **jelentéskészítési** csomópontja a **figyelés** munkaterület a Configuration Manager konzolon.  

#### <a name="to-verify-the-reporting-services-point-installation"></a>A jelentéskészítési szolgáltatási pont telepítésének ellenőrzése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen bontsa ki a **Rendszer állapota**elemet, majd kattintson az **Összetevő állapota**lehetőségre.  

3.  Az összetevők listájában kattintson az **SMS_SRS_REPORTING_POINT** elemre.  

4.  A **Kezdőlap** **Összetevő** csoportjában kattintson az **Üzenetek megjelenítése**, majd a **Mind**elemre.  

5.  Adjon meg egy, a jelentéskészítési szolgáltatási pont telepítését megelőző időszakot, és kattintson az **OK**gombra.  

6.  Ellenőrizze, hogy a listában szerepel-e a 1015-ös azonosítóval rendelkező állapotüzenet, amely azt jelzi, hogy a jelentéskészítési szolgáltatási pont telepítése sikeresen megtörtént. Másik lehetőségként megnyithatja a Srsrp.log fájlt, amely az &lt; *ConfigMgr telepítési útvonala*> \Logs, és megnézheti **a telepítés sikerült**.  

     A Windows Intézőben navigáljon &lt; *ConfigMgr telepítési útvonala*> \Logs.  

7.  Nyissa meg a Srsrp.log fájlt, és kezdje el lépésenként ellenőrizni a naplófájlt attól az időponttól kezdve, amikor a jelentéskészítési szolgáltatási pont telepítése sikeresen megtörtént. Ellenőrizze, hogy a telepítő létrehozta-e a jelentésmappákat, telepítette-e jelentéseket, és jóváhagyta-e a biztonsági házirendet mindegyik mappán. Keresse a **Sikeres ellenőrzés. Az SRS webszolgáltatás problémamentesen működik a kiszolgálón** üzenetet a biztonságiházirend-jóváhagyások utolsó sora után.  

##  <a name="BKMK_Certificate"></a> Önaláírt tanúsítvány konfigurálása a Configuration Manager konzol számítógépeihez  
 Többféleképpen készíthet SQL Server Reporting Services-jelentéseket. Ha hoz létre vagy szerkeszt jelentéseket, a Configuration Manager konzolon, a Configuration Manager környezetként használandó jelentéskészítő nyitja meg. Függetlenül attól, hogy a Configuration Manager-jelentések készítésének módjától önaláírt tanúsítványt a helykiszolgáló adatbázis-kiszolgáló hitelesítéséhez szükség. A Configuration Manager automatikusan telepíti a tanúsítványt a helykiszolgáló és a számítógépek van telepítve SMS-szolgáltató. Ezért hozzon létre vagy szerkeszt jelentéseket, a Configuration Manager konzolról, az egyik a számítógépek futás során. Azonban ha hoz létre vagy módosít jelentéseket, amelyek egy másik számítógépre telepített Configuration Manager konzol, kell exportálja a tanúsítványt a helykiszolgálóról, és majd hozzá a **megbízható személyek** a Configuration Manager konzolt futtató számítógép tanúsítványtárolójába.  

> [!NOTE]  
>  Az SQL Server Reporting Serviceshez használható jelentéskészítési környezetekről bővebben lásd [A jelentéskészítési környezetek összehasonlítása](http://go.microsoft.com/fwlink/p/?LinkId=242805) c. részt az SQL Server 2008 online könyvekben.  

 Az alábbi eljárással példa bemutatja, hogyan viheti át az önaláírt tanúsítvány egy példányát a helykiszolgálóról egy másik számítógépre, amelyen a Configuration Manager konzolon, ha mindkét számítógépen a Windows Server 2008 R2. Ha az Ön számára ez az eljárás nem megfelelő, mert eltérő verziójú az operációs rendszere, akkor a megfelelő eljárás megtalálásában az operációs rendszer dokumentációjára támaszkodhat.  

#### <a name="to-transfer-a-copy-of-self-signed-certificate-from-the-site-server-to-another-computer"></a>Az önaláírt tanúsítvány egy példányának átmásolása a helykiszolgálóról egy másik számítógépre  

1.  Az önaláírt tanúsítvány exportálásához végezze el az alábbi lépéseket a helykiszolgálón:  

    1.  Kattintson a **Start**gombra, a **Futtatás**pontra, majd írja be az **mmc.exe**parancsot. Az üres konzolban kattintson a **Fájl**pontra, majd a **Beépülő modul hozzáadása/eltávolítása**elemre.  

    2.  A **Beépülő modul hozzáadása/eltávolítása** párbeszédpanelen válassza ki a **Tanúsítványok** lehetőséget az **Elérhető beépülő modulok**listájából, majd kattintson a **Hozzáadás**gombra.  

    3.  A **Tanúsítványkezelő beépülő modul** párbeszédpanelen válassza ki a **Számítógépfiók**lehetőséget, majd kattintson a **Tovább**gombra.  

    4.  A **Számítógép kiválasztása** párbeszédpanelen győződjön meg arról, hogy a **Helyi számítógép (az a számítógép, amelyen ez a konzol fut)** be van jelölve, majd kattintson a **Befejezés**elemre.  

    5.  Kattintson a **Beépülő modul hozzáadása/eltávolítása** párbeszédpanelen az **OK**gombra.  

    6.  A konzolon bontsa ki a **Tanúsítványok (Helyi számítógép)**, **Megbízható személyek**csomópontot, és jelölje ki a **Tanúsítványok**elemet.  

    7.  Kattintson a jobb gombbal a rövid nevű tanúsítványra &lt; *hely kiszolgálójának teljes Tartománynevét*>, kattintson a **feladataival**, majd válassza ki **exportálása**.  

    8.  Az alapértelmezett beállításokat használva fejezze be a **Tanúsítványexportáló varázslót** , és mentse el a tanúsítványt a **.cer** fájlnévkiterjesztéssel.  

2.  Az önaláírt tanúsítvány felvétele a megbízható személyek tanúsítványtárolójához a Configuration Manager konzolt futtató számítógép hajtsa végre a következő lépéseket:  

    1.  A fenti 1.a–1.e lépéseket megismételve konfigurálhatja a **tanúsítvány** MMC beépülő a felügyeleti pont számítógépén.  

    2.  A konzolban bontsa ki a **Tanúsítványok (Helyi számítógép)**, **Megbízható személyek**csomópontot, az egér jobb gombjával kattintson a **Tanúsítványok**elemre, és válassza **Az összes feladat**, majd az **Importálás** lehetőséget a **Tanúsítványimportáló varázsló**elindításához.  

    3.  Az **Importálandó fájl** lapon jelölje ki az 1.h lépésben mentett tanúsítványt, és kattintson a **Tovább**gombra.  

    4.  A **Tanúsítványtároló** lapon jelölje be a **Minden tanúsítvány tárolása ebben a tárolóban**választógombot, a **Tanúsítványtároló** beállításban adja meg a **Megbízható személyek**lehetőséget, és kattintson a **Tovább**gombra.  

    5.  A varázsló bezárásához kattintson a **Befejezés** gombra, és végezze el a tanúsítvány konfigurálását a számítógépen.  

##  <a name="BKMK_ModifyReportingServicesPoint"></a> A jelentéskészítési szolgáltatási pont beállításainak módosítása  
 Miután telepítette a jelentéskészítési szolgáltatási pontot, módosíthatja a helyadatbázis kapcsolati és hitelesítési beállításait a jelentéskészítési szolgáltatási pont tulajdonságai között. A jelentéskészítési szolgáltatási pont beállításait a következő eljárással módosíthatja.  

#### <a name="to-modify-reporting-services-point-settings"></a>A jelentéskészítési szolgáltatási pont beállításainak módosítása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd a helyrendszerek listájának megjelenítéséhez kattintson a **Kiszolgálók és helyrendszerszerepkörök** lehetőségre.  

    > [!TIP]  
    >  Ha csak azokat a helyrendszereket kívánja megjeleníteni, amelyek tartalmazzák a jelentéskészítési szolgáltatási pont helyrendszerszerepkört, az egér jobb gombjával kattintson a **Kiszolgálók és helyrendszerszerepkörök** elemre, és válassza a **Jelentéskészítési szolgáltatási pont**lehetőséget.  

3.  Jelölje ki azt a helyrendszert, amelyik azt a jelentéskészítési szolgáltatási pontot tárolja, amelyiken módosítani szeretné a beállításokat, majd válassza a **Jelentéskészítési szolgáltatási pont** elemet a **Helyrendszerszerepkörök**közül.  

4.  A **Helyszerepkör** lap **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

5.  A **Jelentéskészítési szolgáltatási pont tulajdonságai** párbeszédpanelen a következő beállításokat módosíthatja:  

    -   **Helyadatbázis-kiszolgáló neve**: Adja meg a Configuration Manager helyadatbázisát futtató kiszolgáló nevét. A varázsló rendszerint a kiszolgáló teljes tartománynevét kéri le. Adatbázispéldány megadásához használja a formátum &lt; *kiszolgálónév*>\&lt; *Példány neve*>.  

    -   **Az adatbázisnév**: Adja meg a System Center 2012 Configuration Manager Helyadatbázis neve, és kattintson **ellenőrizze** annak ellenőrzéséhez, hogy a varázsló hozzáfér a helyadatbázishoz.  

        > [!IMPORTANT]  
        >  A jelentéskészítési szolgáltatási pontot létrehozó felhasználói fióknak Olvasás hozzáféréssel kell rendelkeznie a helyadatbázishoz. Ha a kapcsolat ellenőrzése sikertelen, piros figyelmeztető ikon jelenik meg. A hiba részleteinek megjelenítéséhez vigye a mutatót erre az ikonra. Javítsa ki a hibát, és kattintson a **Tesztelés** gombra.  

    -   **Felhasználói fiók**: Kattintson a **beállítása**, majd válassza ki, amely az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont fiókja összekapcsolja a Configuration Manager helyadatbázishoz a jelentésekben megjelenített adatok lekéréséhez. Válassza ki **létező fiók** adjon meg egy Windows felhasználói fiókot, amely meglévő Configuration Manager-jogosultságokkal rendelkezik, vagy válasszon **új fiók** , amely jelenleg nem rendelkezik jogosultságokkal a Configuration Manager Windows felhasználói fiókot szeretne megadni. A Configuration Manager automatikusan hozzáférést ad a megadott felhasználói fiókot a helyadatbázishoz. A fiók a **ConfigMgr SRS jelentéskészítési pont** fiókként jelenik meg az **Adminisztráció** munkaterület **Biztonság** csomópontjának **Fiókok** almappájában.  

         A megadott Windows felhasználói fiókot és jelszót a Reporting Services adatbázisa tárolja titkosított formában. A Reporting Services e fiók és jelszó használatával kéri le a jelentések adatait a helyadatbázisból.  

        > [!IMPORTANT]  
        >  Ha a helyadatbázis egy távoli helyrendszeren található, az Ön által megadott fióknak a **Helyi bejelentkezés engedélyezése** engedéllyel kell rendelkeznie a számítógépre vonatkozóan.  

6.  A módosítások mentéséhez és a párbeszédpanel bezárásához kattintson az **OK** gombra.  

## <a name="upgrading-sql-server"></a>Az SQL Server frissítése  
 A frissítés befejezése után az SQL Server és SQL Server Reporting Services a jelentéskészítési szolgáltatási pont az adatforrásként használt hibákat eredményezhet, amikor futtat vagy szerkeszt jelentéseket, a Configuration Manager konzoljáról. A jelentéskészítés megfelelően működjön, a Configuration Manager konzolról, a jelentéskészítési szolgáltatási pont helyrendszerszerepkört a hely eltávolítása és újra kell telepítenie. Egy internetböngészőből azonban a frissítést követően is sikeresen futtathatja és szerkesztheti a jelentéseket.  

##  <a name="BKMK_ConfigureReportOptions"></a> A jelentések beállításainak konfigurálása  
 A jelentéskészítési szolgáltatási pont a jelentéseinek kezeléséhez használt alapértelmezett kiválasztásához használja a Configuration Manager-hely jelentési beállításait. Habár egy helyen egyszerre több jelentéskészítési szolgáltatási pont is lehet, a jelentések kezelését csak a jelentések beállításai között megadott, alapértelmezett jelentéskiszolgáló végzi. A következő eljárással konfigurálhatja a hely jelentési beállításait.  

#### <a name="to-configure-report-options"></a>A jelentések beállításainak konfigurálása  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen bontsa ki a **Jelentéskészítés**csomópontot, majd kattintson a **Jelentések**elemre.  

3.  A **Kezdőlap** **Beállítások** csoportjában kattintson a **Jelentésbeállítások**elemre.  

4.  A listában jelölje ki az alapértelmezett jelentéskiszolgálót, majd kattintson az **OK**gombra. Ha a listában nem szerepel egyetlen jelentéskészítési szolgáltatási pont sem, akkor ellenőrizze, hogy a hely rendelkezik-e sikeresen telepített és konfigurált jelentéskészítési szolgáltatási ponttal.  

## <a name="next-steps"></a>További lépések
[Műveletek és karbantartás a jelentéskészítéshez](operations-and-maintenance-for-reporting.md)

