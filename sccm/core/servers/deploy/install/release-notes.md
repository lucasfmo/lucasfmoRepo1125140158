---
title: "Kibocsátási megjegyzések – Configuration Manager |} Microsoft Docs"
description: "Lépjen kapcsolatba a sürgős hibákat tartalmazzák, amely még nincs kijavítva a termékben vagy a Microsoft Tudásbázis megfelelő cikkében ismertetett ezek a megjegyzések."
ms.custom: na
ms.date: 05/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 41
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: 9da6f9678a7fb5c76f365a3522f5e5e0fdfec037
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="release-notes-for-system-center-configuration-manager"></a>Kibocsátási megjegyzések a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerrel, a kiadási megjegyzései korlátozva a sürgős hibákat tartalmazzák, amely még nincs kijavítva a termékben (a konzolon belüli frissítésével érhető el), vagy a Microsoft Tudásbázis megfelelő cikkében ismertetett.  

 Az alapvető felhasználási helyzeteket érintő ismert hibák kapcsán ezeket az információkat a System Center Configuration Manager online dokumentációtárában tesszük közzé.  

> [!TIP]  
>  Ez a témakör kibocsátási megjegyzések a System Center Configuration Manager aktuális ágának. Tekintse meg a System Center Configuration Manager Technical Preview [a System Center Configuration Manager Technical Preview](../../../../core/get-started/technical-preview.md)  

## <a name="setup-and-upgrade"></a>Telepítés és verziófrissítés  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Miután frissítette a Configuration Manager konzol ConsoleSetup.exe fájllal a hely kiszolgáló mappából, legutóbbi módosult nyelvi csomagokkal nem érhetők el
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
Miután lefuttatta a helybeni frissítést konzolhoz ConsoleSetup.exe fájllal egy helyrendszer-kiszolgálók telepítési mappájából, újonnan telepített nyelvi csomagok nem feltétlenül mavenen. Ez akkor fordul elő, ha:
- A webhely 1610 vagy 1702 verzióját futtatja.
- A konzol frissül helyben ConsoleSetup.exe fájllal a hely server telepítési mappájából.

Ez a probléma akkor fordul elő, amikor az újratelepített konzol nem használja a legújabb megfelelő nyelvi csomagokat konfigurált. Nem jelez hibát, de a rendszer nem módosult a nyelvi csomagok véve a konzolhoz.  

**Megkerülő megoldás:** Távolítsa el a jelenlegi konzolt, és telepítse az új telepítést a konzolt. A hely kiszolgálók telepítési mappájából ConsoleSetup.exe is használhatja. A telepítés során ügyeljen arra, hogy válassza ki a használni kívánt nyelvi csomagok fájljait.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>1702 verziójával az alapértelmezett hely határcsoporthoz van beállítva a hely hozzárendeléséhez
<!--  SMS 486380   Applicability should only be to 1702. -->
1702 verziójával, az alapértelmezett webhely határ csoportok hivatkozás lapon rendelkezik ellenőrzi a **használja ezt a határcsoportot a hely hozzárendeléséhez**, azok a helyek, a **hozzárendelt hely**, és szürkén jelenik meg, hogy a konfiguráció nem szerkesztésének vagy eltávolításának.

**Megkerülő megoldás:** Nincs. Ez a beállítás figyelmen kívül hagyhatja. Bár a helyhozzárendelés engedélyezett a csoport, az alapértelmezett hely határcsoporthoz nem használatos a hely hozzárendeléséhez. A 1702 Ez a konfiguráció biztosítja a megfelelő hely az alapértelmezett hely határcsoporthoz tartozik.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>A hosszú távú szolgáltatás fiókirodai hely 1606 verzió telepítésekor telepítve van-e az aktuális ág hely
<!-- Consider move to core content  -->
Használatakor a verzió 1606 alapszintű verziót tartalmazó adathordozó a 2016. októberi kiadás a hosszú távú karbantartási ág (LTSB) hely telepítéséhez a telepítő ehelyett aktuális ág hely telepítésére. Ennek oka az, a szolgáltatáskapcsolódási pontot telepíteni a hely telepítését a beállítás nincs bejelölve.

 - Bár a szolgáltatáskapcsolódási pont nincs szükség, ki kell választania egy LTSB hely telepítéséhez telepíteni.

A telepítés után eltávolíthatja a szolgáltatáskapcsolódási pont.  Azonban rendelkeznie kell egy szolgáltatáskapcsolódási pont offline vagy online módban, telemetriai adatokat küldeni, biztonsági frissítések beszerzéséhez a aktuális ág és a LTSB helyek.

Ha a hely telepítve, mint az aktuális ág webhely, de a LTSB telepíteni, eltávolítani a helyet, és telepítse újra. Alternatív megoldásként hívása [Microsoft Help és támogatás](http://go.microsoft.com/fwlink/?LinkId=243064) segítségért.  

Mely telepítve, a konzol fiókirodai megerősítéséhez **felügyeleti** > **Helykonfiguráció** > **helyek**, és nyissa meg a **Hierarchiabeállítások**. A beállítás aktuális ág helyhez alakíthatja át a helyet csak érhető el, a hely a LTSB futtatásakor.  

**Megkerülő megoldás:**  Nincs.   



### <a name="the--sql-server-backup-model-in-use-by-configuration-manager-can-change-from-full-to-simple"></a>A Configuration Manager által használt SQL Server biztonsági mentési modell teljesről egyszerűre változhat  
<!-- Confirm applicability for upgrade to later baselines. 1511 is out of support. 1606 is minmum supported baseline  -->

 A System Center Configuration Manager 1511 verzióra való frissítés esetén a Configuration Manager által használt SQL Server biztonsági mentési modell teljesről egyszerűre válthat.  

-   Ha egyéni SQL Server biztonsági mentési feladatot használ a teljes biztonsági mentési modellel (a Configuration Manager beépített biztonsági mentési feladata helyett), a frissítés során a rendszer a teljes modellről egyszerű biztonsági mentési modellre válthat.  

**Megkerülő megoldás**: 1511-es verzióra való frissítés után tekintse át az SQL Server konfigurációját, és állítsa vissza a teljes biztonsági mentést szükséges.  



### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>A frissítés Letöltés állapottal elakad a Configuration Manager konzol Frissítés és karbantartás csomópontjánál  
<!-- Source bug pending. Consider move to core content.  -->
Online szolgáltatáskapcsolati pont által végzett automatikus frissítésletöltés során egy frissítés Letöltés állapottal elakad. A letöltés elakadásakor a jelzett naplófájlokba a következőkhöz hasonló tartalmú bejegyzések kerülnek:  

DMPdownloader napló:  

-   HIBA: Nem sikerült letölteni a parancs redisturl http://go.microsoft.com/fwlink/?LinkID=724436 csomagját http://go.microsoft.com/fwlink/?LinkID=724434 paranccsal 112015/noui "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist" 037cd17e-4d7b-40e1-802b-14bb682364c7  

ConfigMgrSetup.log:  

-   Hiba: nem sikerült ellenőrizni a d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi authenticode-aláírását.  

-   Hiba: a fájl aláírásának ellenőrzése sikertelen: d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**Megkerülő megoldás**: A helykiszolgálón módosítsa a következő beállításkulcsot felel meg a következőt, és majd indítsa újra az SMS_Executive szolgáltatást, vagy Várjon 24 órát, akár a következő automatikus letöltési ciklusig.  

-   **Szerkesztendő kulcs**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software közzététele  

-   **Érték**:  Beállítása **146944** decimális vagy **0x00023e00** hexadecimális  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>A CD-ről redist fájlok használata esetén a telepítés meghiúsul. Legújabb mappa jegyzék ellenőrzési hiba
<!-- Source bug pending  -->

Amikor a telepítő futtatásával CD-ről. Legújabb mappa 1606 verziójához készült, és a CD-n található terjeszthető csomagját a fájlokat használja. Legfrissebb mappát, a telepítés meghiúsul és a Configuration Manager telepítő naplóját a következő hibákat:

  - HIBA: Defaultcategories.dll fájl kivonata ellenőrzése nem sikerült
  - HIBA: Jegyzékének ellenőrzése sikertelen. Hibás verziójú jegyzékfájl?

**Megkerülő megoldás:**  Használja az alábbiak egyikét:
 - A telepítés során válassza töltheti le a legfrissebb redist fájlok használata helyett a CD-n szereplő Microsoft. Legfrissebb mappát.
 - Törölje kézzel a *cd.latest\redist\languagepack\zhh* mappát, majd futtassa újra a telepítőprogramot.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Szolgáltatáskapcsolódási eszközt kivételt jelez, ha SQL server távoli, vagy le van tiltva, a megosztott memória
1606 verziójával kezdve a szolgáltatáskapcsolódási eszköz generál kivétel az alábbiak egyike igaz:  
 -    A Helyadatbázis távoli a számítógépről, amely a szolgáltatáskapcsolódási pontot futtatja, valamint egy nem szabványos portot (eltérő 1433-as port)
 -     A Helyadatbázis nem azon a szolgáltatáskapcsolódási pont, de az SQL-protokoll ugyanarra a kiszolgálóra **megosztott memória** le van tiltva

A kivétel: a következőhöz hasonló:
 - *Nem kezelt kivétel: System.Data.SqlClient.SqlException: A hálózattal kapcsolatos vagy példányspecifikus hiba történt az SQL-kiszolgálóhoz való kapcsolódás során. A kiszolgáló nem található vagy nem érhető el. Győződjön meg arról, hogy a példány neve helyesen-e, és hogy az SQL Server konfigurálva van-e távoli kapcsolatok lehetővé tételéhez. (szolgáltató: Nevesített csövek szolgáltató, hiba: 40 - nem nyitható meg az SQL-kiszolgálóval) –*

**Megkerülő megoldás**: Az eszköz használata során módosítania kell az SQL Server portja vonatkozó információval a szolgáltatáskapcsolódási pontot futtató kiszolgáló beállításjegyzékében:

   1.    Az eszköz használata előtt szerkessze a következő beállításkulcsot, és vegye fel a portot, amelyet az SQL Server nevét használja száma:
    - Kulcs:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Érték: &lt;SQL-kiszolgáló neve >
    - Adja hozzá: **,&lt;PORT >**

    Ahhoz például, hogy a port hozzáadása *15001* nevű kiszolgálóra *testserver.test.net*, az eredményül kapott kulcs a következő lenne: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.    Után a port hozzáadása a beállításjegyzéket, az eszköz kell működhetnek.  

   3.    A használatára az eszköz befejezése után, mind a **-csatlakozás** és **-importálása** lépéseket, a beállításkulcs állítsa vissza az eredeti érték.  




<!-- No current Backup and Recovery relenotes
## Backup and recovery
-->



## <a name="client-deployment-and-upgrade"></a>Ügyfelek központi telepítése és frissítése  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Ügyfél telepítése nem sikerül, 0x8007064c. Hibakód:
<!--- SMS 486973 -->

Ha az ügyfél Windows rendszerű számítógépekre telepíti, a telepítés sikertelen lesz. A ccmsetup.log fájl tartalmaz egy "fájl"C:\WINDOWS\ccmsetup\Silverlight.exe"1612 kilépési hibakódot adott vissza. Sikertelen a telepítés""InstallFromManifest sikertelen 0x8007064c"követ.

**Megkerülő megoldás** ennek oka a Silverlight sérült, a korábban telepített verzióját. Próbálja meg az érintett számítógépen kijavítására a következő eszközt futtató: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed) 




## <a name="operating-system-deployment"></a>Operációs rendszer központi telepítése  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Probléma a Windows 10 rendszerhez készült Windows ADK 1511-es verziójával  
A Szoftverközpontból, a Windows ADK 10, amikor a számítógép újraindult a Windows előtelepítési környezettel, 1511-es verziójában a Windows PE v.10.0.10586 rendszerindító lemezképet használó feladatütemezés futtatásakor, amikor a "Hardvereszközök inicializálása" hibaüzenettel meghiúsul: **A Windows PE inicializálása nem sikerült. Hibakód: 0x80220014**  

**Megkerülő megoldás**: Használja az eredeti Windows 10 ADK. További információkért tekintse meg a következő System Center Configuration Manager Team Blog: [A Windows ADK for Windows 10 probléma](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>A dinamikus alkalmazástelepítés egy sikeresen befejeződő feladatütemezés során leáll  
Amikor az **Alkalmazások telepítése a dinamikus változók listájának megfelelően** beállítást használó feladatütemezést telepít, és az alkalmazások valamelyike bármely okból sikertelen, a feladatütemezés sikeres befejezést jelent, függetlenül attól, hogy hogyan konfigurálja a következő beállításokat:  

-   **Folytatás hiba esetén** (az Alkalmazás telepítése lépés Beállítások lapján)  

-   **Ha egy alkalmazás telepítése nem sikerül, akkor folytassa a listában szereplő többi alkalmazás telepítését** (az Alkalmazás telepítése lépés Tulajdonságok lapján)  

Az smsts.log fájlból megállapíthatja, hogy van-e olyan alkalmazás, melynek telepítése nem sikerült.  

**Megkerülő megoldás**: Használja a **_TSAppInstallStatus** változó a feltétellel, a feladatütemezés sikertelen lesz, ha a dinamikus alkalmazástelepítések egyike hiba történt a feladatütemezés következő lépéseinek feltételeként.  

### <a name="smb-might-not-work-properly-after-you-use-a-task-sequence-to-install-windows-10"></a>Az SMB bizonyos esetekben nem működik megfelelően a Windows 10 telepítését célzó feladatütemezések használatát követően  
Ha feladatütemezés segítségével és lemezkép használatával végez Windows 10-telepítést, előfordulhat, hogy a Configuration Manager-ügyfél telepítését követően az SMB nem működik megfelelően. Például nem sikerül végrehajtani a következő feladatütemezési lépéseket:  

-   Felhasználói állapot visszaállítása állapotáttelepítési ponttal  

-   Csatlakozás hálózati mappához  

Az F8 megnyomására megnyíló rendszergazdai parancssorból PING-elhető a számítógép, de az SMB hálózati forgalom (például a parancssorból kiadott NET USE parancs) meghiúsul a következővel: 1231-es hiba – A hálózati hely nem érhető el.  

**Megkerülő megoldás**:  
A folyamat leállítása érdekében a Windows és ConfigMgr beállítása feladatütemezési lépést követően vegyen fel egy Parancssor futtatása lépést, majd indítsa el a Munkaállomás szolgáltatást a következőképpen:    
**net stop munkaállomás /y & net start munkaállomás**  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>A karbantartási tervek az alapértelmezések használatával nagyszámú duplikált szoftverfrissítési csoportot és központi telepítést hoznak létre  
Alapértelmezés szerint a Karbantartási terv létrehozása varázsló minden szoftverfrissítés szinkronizálását követően lefut. Amikor a varázsló fut, új szoftverfrissítési csoportot és központi telepítést hoz létre. Ha például naponta több alkalommal futó szoftverfrissítés-szinkronizálási ütemezéssel rendelkezik, a Karbantartási terv létrehozása varázsló minden egyes nap több, valószínűleg egymással megegyező szoftverfrissítési csoportot és telepítést is létrehoz.  

**Megkerülő megoldás**:    
A karbantartási terv létrehozását követően nyissa meg a terv tulajdonságait, lépjen az **Értékelési ütemezés** lapra, válassza **A szabály ütemezés szerint fusson** lehetőséget, kattintson a **Testreszabás** elemre, és hozzon létre egyéni ütemezést. Beállíthatja például, hogy a karbantartási terv csak 60 naponta fusson.  

### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Amikor egy nagy kockázatú üzemelő példányt párbeszédpanel egy felhasználó számára látható, további magas kockázatú párbeszédpanelek hamarabb határidővel nem jelenik meg
Miután létrehozott és a magas kockázatú központi telepítés felhasználók számára, a felhasználó egy nagy kockázatú párbeszédpanel jelenik meg. Ha a felhasználó nem zárja be a párbeszédpanelt, hozhat létre és engedélyezhet, mint az első hamarabb határidővel magas kockázatú központi telepítés egy másik, a felhasználó nem kap egy frissített párbeszédpanel csak azokat az eredeti párbeszédpanel bezárása után. A központi telepítések továbbra is a konfigurált határidők fognak futni.

**Megkerülő megoldás**:  
A felhasználó zárja be a párbeszédpanelt a első magas kockázatú központi telepítés a következő magas kockázatú központi telepítés a párbeszédpanel megjelenítéséhez.

## <a name="mobile-device-management"></a>Mobil eszközök felügyelete  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>Nem lehet létrehozni regisztrálási profilt egy elsődleges helyen  
A rendszergazda nem tud regisztrálási profilt létrehozni a System Center Configuration Manager felügyeleti konzolján, amely egy elsődleges helyhez csatlakozik. Amikor regisztrálni próbál, a rendszergazda hibaüzenetet kap "DEP-token nem lett frissítve. A DEP-token feltöltése"a beléptetési profil varázslóban. A hiba annak ellenére jelentkezik, hogy fel lett töltve egy érvényes DEP-token a központi adminisztrációs helyre.  

**Megkerülő megoldás**: Beléptetési profil létrehozása a System Center Configuration Manager konzolon láthatja, hogy központi adminisztrációs helyhez csatlakozik.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>A DEP nem tud nem alfanumerikus karaktereket használni a regisztrálási profilokban  
Az Apple eszközregisztrációs profiljával (DEP) társított regisztrációs profilok nem tudnak nem alfanumerikus karaktereket használni a profil **Név**, **Leírás**, **Részleg** és **Telefonszám** mezőiben, ha engedélyezve van a DEP. Ezekben a mezőkben nem alfanumerikus karaktereket használva létrejön egy regisztrálási profil, de a profil nem tölthető fel az Apple-hez. Nem érkezik hiba vagy figyelmeztetés az Apple kiszolgálójáról, és profilok nem települnek a DEP által felügyelt eszközökre.  

**Megkerülő megoldás**: Nincs.

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Az adatok teljes törlése funkció letiltja 4 GB RAM-nál kevesebbel rendelkező Windows 10-es eszközöket.

Az adatok teljes törlése funkció hasznavehetetlenné teheti a 4 GB RAM-nál kevesebbel rendelkező Windows 10 RTM-eszközöket (az 1511-es verziónál korábbi kiadásúakat). Az adatok törlése után az eszköz nem indul el és nem válaszol.

**Megkerülő megoldás**: Győződjön meg arról, a Windows 10 RTM rendszerű számítógépen kell legalább 4 GB RAM memóriával az eszközön a teljes törlés végrehajtása előtt. A Windows 10-es eszközök verziószámának megtekintéséhez írja be a „winver” parancsot a parancssorba. Amennyiben már végrehajtotta eszközén az adatok teljes törlését és az eszköz nem válaszol, rendszerindításra alkalmas Windows 10 USB-meghajtó segítségével indítsa újra az eszközt.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Ha egy felhasználó két vagy több olyan gyűjtemény tagja, amelybe használati feltételekre vonatkozó házirend települ, a felhasználó az azonos feltételeket több példányban látja  

Ha egy rendszergazda feltételeket telepít több felhasználói gyűjteménybe, és a felhasználó ezen gyűjtemények közül egynél többnek tagja, a felhasználó számára azonos feltételek több példánya jelenik meg a céges portál megnyitásakor.  Például, ha a "SampleUser" nevű felhasználó két különböző felhasználói gyűjteménynek tagja, egyet a neve "CompanyEmployeesFTE" és "companyemployeesna" gyűjteménybe is telepítették, "és a használati feltételek"CompanyTerms"nevű a rendszer CompanyEmployeesFTE és a companyemployeesna gyűjteménybe is telepítették, a SampleUser companyterms két azonos készlet megjelenik a feltételek elfogadását kérő lapon. Mivel a felhasználók csak az összes feltétel elfogadását vagy elutasítását hajthatják végre, nem áll fenn az elfogadás olyan nem egyértelmű állapotának veszélye, melyben a felhasználó elfogadta és el is utasította a feltételeket. A használati feltételek elfogadására vonatkozó jelentés a használati feltételek minden készletéhez egyetlen sort fog tartalmazni az egyes felhasználók esetében, így a jelentés nem tartalmaz hibákat. Egyetlen hatása az, hogy a felhasználó két példányban látja a feltételeket az elfogadást kérő lapon.  

**Megkerülő megoldás**: Győződjön meg arról, hogy minden felhasználónak csak része egy gyűjteményt, amelyhez a feltételek telepítve vannak a.  

### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android Tanúsítványalapú hitelesítés használatára a munkahelyi e-mail profilok esetében a rendszer nem alkalmazza eszközök
<!--  487657 -->
Az Android for Work e-mail-profil létrehozásakor két módon a hitelesítéshez. Egy felhasználónév és jelszó, és egyéb tanúsítványok. Ilyenkor a tanúsítványokat a beállítás nem működik. Ha a profil létrehozása és a hitelesítési módra beállított **tanúsítványok**, a profil nem alkalmazható az eszközt, és kéri a felhasználó manuálisan adja meg az e-mail fiók adatait.

**MEGKERÜLŐ MEGOLDÁS**: Nincs. Rendszergazdák kell vagy használja a **felhasználónév és jelszó** lehetőséget, vagy várja meg a probléma megoldódott.

## <a name="reports-and-monitoring"></a>Jelentések és figyelés  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>Az Állapotigazolási jelentés üres, pedig a rendszer korábban gyűjtött állapotigazolási adatokat  
Amikor egy rendszergazda felhasználó, akinek biztonsági szerepköréhez az **Állapotigazolás** engedélycsoportra vonatkozó **Olvasás** engedély is hozzátartozik, megnyitja az állapotigazolási jelentést, a jelentés üres, nem jelennek meg adatok. Ennek az az oka, hogy az állapotigazolási jelentésben szereplő adatokra vonatkozó engedély a **Felhasználó-eszköz kapcsolat** engedélycsoporthoz, és nem az Állapotigazolás engedélycsoporthoz tartozik.  

A probléma hatással van a System Center Configuration Manager 1602-es frissítés beállítására, és egy következő frissítés fogja megoldani.  

**Megkerülő megoldás**: Rendelje hozzá a rendszergazda felhasználó egy biztonsági csoportot, amely tartalmazza a **olvasási** engedéllyel a **felhasználó-eszköz kapcsolatokat** engedélycsoport.  

### <a name="conditional-access"></a>Feltételes hozzáférés  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>Egy adott felhasználógyűjteményt egyszerre a kivétel- és a célgyűjteményhez is hozzá lehet adni.  
Ez akkor fordul elő, ha az adott **felhasználógyűjteményt** **előbb** adja hozzá a **Kivételgyűjtemény** oldalhoz, mint a **Célgyűjtemény** oldalhoz.  Ha a **felhasználógyűjteményt** először a **Célgyűjtemény** oldalhoz adja hozzá, és ezt követően ugyanezt a **felhasználógyűjteményt** megpróbálja hozzáadni a **Kivételgyűjtemény** oldalhoz, megjelenik a szokásos tiltóüzenet.  

Ezt a hibát észleli a System Center Configuration Manager feltételes hozzáférés a **a helyszíni Exchange** az 1602- es várt egy következő frissítés fogja megoldani.  

**Megkerülő megoldás:** Adja hozzá a **Felhasználógyűjteményt** a **Célgyűjtemények** oldalhoz, mielőtt kijelölné **Felhasználógyűjteményt** a a **Kivételgyűjtemény** oldalon, vagy ellenőrizze, hogy nem ad hozzá azonos **Felhasználógyűjteményt** a megcélzott és a Kivételgyűjtemény.

## <a name="endpoint-protection"></a>Endpoint Protection
<!--  Product Studio bug 485370 added by Nathbarn 04 19 2017 -->
### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Kártevőirtó-házirend nem tudja alkalmazni a Windows Server 2016 Core
Kártevőirtó-házirend nem tudja alkalmazni a Windows Server 2016 Core.  A hiba kódja: 0x80070002.  A ConfigSecurityPolicy.exe Hiányzó függőség van.

**Megkerülő megoldás:**  Ez a probléma megoldásához [Tudásbázis 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) elosztott 2017. május 9. 

