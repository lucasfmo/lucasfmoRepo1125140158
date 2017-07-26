---
title: "Új verzió 1702 |} Microsoft Docs"
description: "Ezzel adatokat kapjon módosítások és a System Center Configuration Manager 1702 verziójában bevezetett új képességekkel rendelkezik."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: a2954b3c6f9a09b7246347e780c4cfc49ba39ca1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>Mi &#39; verzió 1702 a System Center Configuration Manager újdonságai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1702 frissítése a System Center Configuration Manager aktuális ág már telepített helyeken az 1602-es, 1606 vagy 1610 verzióját futtató konzolon belüli frissítésként érhető el. Azt is rendelkezésre áll, egy alapkonfigurációt, akkor hasznosak, ha újonnan történő telepítése.

> [!TIP]  
> Új hely telepítése egy alapkonfigurációt a Configuration Manager kell használnia.  
>  További információ:    
>   - [Új helyek telepítése](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Helyfrissítések telepítése](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

A következő szakaszok részletesen bemutatják a módosításokat, és a Configuration Manager 1702 verziójában bevezetett új képességekkel rendelkezik.  

## <a name="deprecated-features-and-operating-systems"></a>Elavult funkciók és operációs rendszerek
Ahhoz, azok végrehajtását a támogatási változásainak megismeréséhez [megszűnő támogatású és elavult funkciók](/sccm/core/plan-design/changes/removed-and-deprecated-features).

1702 elhagyta verziója támogatja a következő termékek:
- **SQL Server 2008 R2**, a hely adatbázis-kiszolgálóin. Támogatási elavulása lett [bejelentése](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) 2015. július 10. Az SQL Server jelen verziójában továbbra is támogatja, a Configuration Manager-1702-es vagy korábbi verziójának használatakor.
- **Windows Server 2008 R2**, a helyrendszer-kiszolgálók és a legtöbb helyrendszerszerepkör. Támogatási elavulása lett [bejelentése](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) 2015. július 10. A Windows ezen verziójához továbbra is támogatja, a Configuration Manager-1702-es vagy korábbi verziójának használatakor.  
- **Windows Server 2008**, a helyrendszer-kiszolgálók és a legtöbb helyrendszerszerepkör. Támogatási elavulása lett [bejelentése](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) 2015. július 10.
- **Windows XP Embedded**, ügyfél operációs rendszert. Érvénytelenítése lett [bejelentése](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) 2015. július 10. A Windows ezen verziójához továbbra is támogatja, a Configuration Manager-1702-es vagy korábbi verziójának használatakor.




## <a name="site-infrastructure"></a>Helyinfrastruktúra

### <a name="improvements-for-in-console-search"></a>A konzolon belüli keresési fejlesztései
Keresés a Configuration Manager konzol használatával kapcsolatos fejlesztések a következők:
 - **Objektum elérési útja:**  
  Sok objektum mostantól támogatja a nevű oszlop **objektumelérési út**.  Ha keresni, és a megjelenített eredmények tartalmazza ezt az oszlopot, láthat minden objektum elérési útja. Például, ha futtatja a alkalmazások keresése az alkalmazások csomópontban, és alárendelt csomópontok is keres a *objektumelérési út* az eredmények ablaktábláján oszlop bemutatja, minden visszaadott objektum elérési útja.   

- **Keresett szöveg megőrzése:**  
  Adja meg a szöveget a keresőmezőbe szöveg, és utána váltsanak keresése egy alárendelt csomópont és az aktuális csomópont között, ha a beírt szöveg most továbbra is fennáll, és még egyszer nélkül új keresés elérhetők maradnak.

- **Kereshet az alárendelt csomópont a döntési megőrzése:**  
 A választott keresés lehetőséget a *aktuális csomópont* vagy *összes alárendelt csomópont* most továbbra is fennáll a csomópont dolgozik módosításakor. Ez a viselkedés azt jelenti, hogy nem kell folyamatosan alaphelyzetbe állítja a döntés, akkor a konzol Navigálás. Alapértelmezés szerint a konzol megnyitásakor megkeresésének lehetősége csak az aktuális csomópont kereséséhez.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Visszajelzés küldése a Configuration Manager konzolról

 A konzolon belüli visszajelzési lehetőségek segítségével közvetlenül a fejlesztői csapat küldhet visszajelzést.

 Megtalálhatja az **visszajelzés** lehetőséget:
 -  A menüszalagon látható, minden egyes csomópont kezdőlap lapján bal.  
    ![Szalagon](./media/feedback-home.png)

 -  Amikor a jobb gombbal a konzolon bármely objektumon.   
     ![Jogosultságot kattintást](./media/feedback-option.png)   

 Kiválasztása **visszajelzés** megnyitja a böngészőt, hogy a [Configuration Manager UserVoice visszajelzési webhely](https://go.microsoft.com/fwlink/?linkid=617029).


###  <a name="changes-for-updates-and-servicing"></a>Módosítások történtek a frissítések és karbantartás
A módosítások a frissítések és karbantartás a következők:

- **Hely**   
  1702, verziójának telepítése után a **frissítés és karbantartás** csomópont jelenik meg a legfelső szintű csomópontja **felügyeleti**. Már nem az alábbi gyermekcsomópontja **Felhőszolgáltatások**.

- **Új állapotok**  
  Rendelkezésre álló frissítéseket a konzolon való megtekintésekor van két új állapotok:  
  - **Elérhető telepítés** – Ez a frissítés, amely le lett letöltve és készen állnak a telepítésre.
  - **Készen áll a letöltésre** – a frissítés érhető el, de nem lett letöltve. Dönthet úgy, a frissítés letöltéséhez, de azt egy újabb frissítés felül lett írva.


- **Egyszerűbb frissítési lehetőségek**  
  Amikor legközelebb az infrastruktúra címtársémának megfelelően két vagy több frissítéshez, csak a legfrissebb lesznek letöltve. Például, ha az aktuális hely verziója két vagy több verziója régebbi, mint a legutóbbi elérhető, csak a legfrissebb verzió automatikusan letölti.  

  Ha szeretné, töltse le és telepítse a többi rendelkezésre álló frissítések, akkor is, ha azok nem a legújabb verzióját. Ha régebbi frissítés letöltéséhez kapni fog egy figyelmeztetés, hogy a frissítés újabb egy lett lecserélve. A frissítés letöltése *elérhető letöltésre*, válassza ki a frissítést a konzolon, és kattintson a **letöltése**.

- **A régebbi frissítések továbbfejlesztett karbantartása**   
  Hozzáadott egy automatikus karbantartás függvény, amely a szükségtelen letöltéseket törlése a "EasySetupPayload" mappában található a helykiszolgálón. Ez 1702 verziójával jelenik meg, mert tisztítás kezdődik, például egy kumulatív frissítést vagy a jövőbeli frissített verzióra egy későbbi frissítés telepítése után működéséhez.  


### <a name="data-warehouse-service-point"></a>Data Warehouse szolgáltatási pont
 A Data Warehouse pont használatával tárolja, és a Configuration Manager telepítéshez hosszú távú múltbeli adatok jelentése.

 Az adatraktár legfeljebb 2 TB adat, a változások követése Timestamp támogatja. Adatok tárolása az adatraktár-adatbázis a Configuration Manager helykiszolgáló helyadatbázisból automatizált szinkronizálások úgy érhető el. Ez az információ a jelentéskészítési szolgáltatási pont az majd érhető el.

 További információkért lásd: [az adatraktár szolgáltatási pont](/sccm/core/servers/manage/data-warehouse).


### <a name="peer-cache-improvements"></a>Társközi gyorsítótár fejlesztései
 1702 verziójával kezdve társközi gyorsítótár forrásoldali számítógép elutasítják tartalmat kér, amikor a társközi gyorsítótár forrásoldali számítógép megfelel-e az alábbi feltételek bármelyike:  
  -  Alacsony töltöttségű telepre vonatkozó módban van.
  -  CPU-terhelés meghaladja a 80 % időpontjában a tartalmat.
  -  Lemezes i/o-rendelkezik egy *AvgDiskQueueLength* , amely meghaladja a 10.
  -  Nincs több elérhető kapcsolódást a számítógéphez van.   
További információkért lásd: **korlátozott mértékben férhet hozzá a társ-gyorsítótárazási forrástól** a [Configuration Manager-ügyfelek számára társ-gyorsítótárazás](/sccm/core/plan-design/hierarchy/client-peer-cache).   

Ezenkívül három új jelentést a jelentéskészítési pont lettek hozzáadva. Ezek a jelentések használatával megérthetik, hogy a visszautasított tartalomkérelmek, mely határ beleértve csoport, számítógép és a tartalom alkalmazta-e további információt. Lásd: [figyelés](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring) társközi gyorsítótár témakörben.

### <a name="content-library-cleanup-tool"></a>Tartalomtár Lemezkarbantartó eszköz
 Használja a [tartalomtár Lemezkarbantartó eszköz](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) tartalom eltávolítása terjesztési pontokat, amikor ezt a tartalmat egy alkalmazás már nem tartozik.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Az OMS-összekötő használatára az Azure Government felhővel
Az OMS-összekötő segítségével csatlakoztatása a Microsoft Azure Government felhőben OMS szolgáltatáshoz. Ehhez telepítenie kell egy konfigurációs fájl módosítása, hogy az összekötő a kormányzati cloud együttműködik az OMS-összekötő telepítése előtt. További információkért lásd: [az OMS-összekötő használata az Azure Government felhő](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig).

### <a name="software-update-points-are-added-to-boundary-groups"></a>Szoftverfrissítési pontok kerülnek a határcsoportok
1702 verziójával kezdve az ügyfelek a határcsoportok használatával egy új szoftverfrissítési pont található, és tartalék és keresése egy új szoftverfrissítési pont, ha már nem érhető el a jelenlegivel. Azok a kiszolgálók egy ügyfél található vezérlőhöz eltérő határcsoportokban egyes szoftverfrissítési pontján adhat hozzá. További információkért lásd: [szoftverfrissítési pontok](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) a a [határcsoportok konfigurálása](/sccm/core/servers/deploy/configure/boundary-groups) témakör.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>Megfelelőségi beállítások

### <a name="new-compliance-settings-for-ios"></a>Az IOS rendszerhez készült új megfelelőségi beállítások

A következőkkel egészült ki számos új beállítások az iOS-eszközök megfelelő elérhető Microsoft Intune-nal.
Az összes rendelkezésre álló beállítások listájáért lásd: [konfigurációs elemek létrehozása az iOS és Mac OS X-eszközök Intune-nal felügyelt](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).


## <a name="application-management"></a>Alkalmazáskezelés

### <a name="improved-support-for-windows-store-for-business-apps"></a>Az üzletági alkalmazások a Windows áruház továbbfejlesztett támogatása

Most már telepítheti online licencelt alkalmazások vállalati Windows áruházból Windows 10 rendszerű számítógépekre, amelyeket a Configuration Manager-ügyfél használatával felügyel.
További információkért lásd: [alkalmazások kezelése a vállalati Windows áruházban](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### <a name="check-for-running-executable-files-before-installing-an-application"></a>Ellenőrizze a végrehajtható fájlok futtatásának egy alkalmazás telepítése előtt

Az a **tulajdonságok** központi telepítés párbeszédpanelen írja be, a a **telepítése viselkedés** lapon megadhat egy további végrehajtható fájlok, ha fut, blokkolja a központi telepítési típus telepítése. A felhasználónak be kell zárnia a működő végrehajtható fájl (vagy lezárása automatikusan céllal megadott központi telepítéseknél kötelező) előtt a központi telepítési típus telepíthetővé válna.

Ha az alkalmazás lett telepítve, mint a **elérhető**, és a felhasználó megpróbál telepíteni egy alkalmazást, zárjon be minden futó végrehajtható fájlok, a telepítés folytatásához, akkor a megadott kéri.

Ha az alkalmazás lett telepítve, mint a **szükséges**, és a beállítás **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** van kiválasztva, akkor fog látni egy párbeszédpanelt, amely közli, hogy a megadott végrehajtható fájlok automatikusan bezáródik az alkalmazás telepítési határidő elérésekor.

### <a name="app-management-improvements-for-hybrid-mdm"></a>A hibrid mobileszköz-kezelési alkalmazás a kezelési fejlesztések

- [Eszközgyűjtemények mennyiségi programban vásárolt iOS-alkalmazások telepítése](#deploy-volume-purchased-ios-apps-to-device-collections)
- [Támogatás az iOS Volume Purchase Program oktatási célokra](#support-for-ios-volume-purchase-program-for-education)
- [Több volume purchase program-tokenek támogatása](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>Operációs rendszer központi telepítése

### <a name="expire-stand-alone-media"></a>Különálló adathordozó lejár
Amikor önálló adathordozót hoz létre, új beállítások állnak rendelkezésre a választható érvényességének kezdő és záró dátumának beállítása az adathordozón. Ezek a beállítások alapesetben le vannak tiltva. A dátum a számítógép rendszerideje összehasonlítja a különálló adathordozó futtatása előtt. Amikor a rendszer pontos ideje a kezdési időpontnál korábbi vagy későbbi, mint a lejárati idő, a különálló adathordozó nem indult el. Ezek a beállítások is elérhetők a New-CMStandaloneMedia PowerShell-parancsmag használatával. További információkért lásd: [különálló adathordozó létrehozása](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="package-id-displayed-in-task-sequence-steps"></a>Feladatütemezési lépések jelennek Csomagazonosító
Feladatütemezés bármely lépése egy csomag, illesztőprogram-csomagot, operációs rendszer lemezképét, rendszerindító lemezkép vagy operációs rendszer verziófrissítő csomagjára hivatkozó most jelenik meg a hivatkozott objektum Csomagazonosítóját. Ha a feladatütemezéshez egy lépést az alkalmazás hivatkozik, jeleníti meg az objektum azonosítójával.

### <a name="support-for-additional-content-in-stand-alone-media"></a>Támogatja a különálló adathordozót a további tartalmat
További tartalmat mostantól támogatják a különálló adathordozót. Kiválaszthatja a további csomagokat, illesztőprogram-csomagokat és alkalmazásokat és az egyéb, a feladatütemezésben hivatkozott tartalom az adathordozón átmenetileg tárolva. Csak a feladatütemezésben hivatkozott tartalom korábban, az önálló adathordozó lett előkészített. További információkért lásd: [különálló adathordozó létrehozása](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="hardware-inventory-collects-uefi-information"></a>Hardverleltár UEFI adatokat gyűjt.
Egy új hardverleltárosztály (**SMS_Firmware**) és a tulajdonság (**UEFI**) elérhető segítségével meghatározhatja, hogy a számítógép UEFI üzemmódban indul. Ha a számítógép UEFI módban indul el a **UEFI** tulajdonsága **igaz**. Ez a Hardverleltár alapértelmezés szerint engedélyezve van. Hardverleltár kapcsolatos további információkért lásd: [konfigurálása a Hardverleltár](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>A Szoftverközpont figyelmeztető üzenetek nagy jelentőségű feladatütemezésekhez fejlesztései
Ebben a kiadásban a Szoftverközpont figyelmeztető üzenetek nagy jelentőségű központi telepítésére vonatkozó feladatütemezés a következő fejlesztéseket tartalmazza:

- A feladatütemezés tulajdonságai konfigurálhat feladatütemezési, többek között operációs rendszert nem tartalmazó feladatütemezések, mint a magas kockázatú telepítés. Bizonyos feltételeknek megfelelő feladatütemezési automatikusan nagy jelentőségű típusúként van definiálva. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges](/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- A feladatütemezés tulajdonságai Ha szeretné, használja az alapértelmezett értesítési üzenetet, vagy hozzon létre saját egyéni értesítési üzenet nagy jelentőségű telepítésekhez.
- A feladatütemezés tulajdonságai a Szoftverközpont tulajdonságai, például egy újraindítás szükséges, ügyeljen a letöltési mérete, a feladatütemezés és konfigurálható a becsült futási időt.
- Az alapértelmezett nagy jelentőségű telepítési üzenet helyben most, hogy az alkalmazások, adatok és beállítások települnek át automatikusan állapotok frissíti. Korábban, az alapértelmezett üzenetet az egyetlen operációs rendszer telepítése azt mutatták ki, hogy az összes, adatok, beállítások és alkalmazások elveszhetnek, amelyet a rendszer nem igaz a helyben frissítés.

További információkért lásd: [nagy jelentőségű feladatütemezés beállításainak konfigurálása](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>A feladatütemezés sikertelen lesz, ha az előző laphoz való visszatéréshez
Most visszatérhet az előző oldalra a feladatütemezés futtatása, és hiba történik. Ez a kiadás előtt indítsa újra a feladatütemezés, ha hiba történt a kellett. Használhatja például a **előző** gombra a következő esetekben:

- A számítógép indításakor a Windows PE környezetben, a feladat feladatütemezési rendszerindítási párbeszédpanelen előfordulhat, hogy megjeleníti, mielőtt a feladatütemezés érhető el. Ha a Tovább lehetőségre kattintás ebben a forgatókönyvben, a feladatütemezés utolsó lapján, hogy nincsenek nem feladatütemezések üzenetet jeleníti meg. Most, rákattinthat **előző** keresni az elérhető feladatütemezéseket. Ez az eljárás megismétlésével addig, amíg a feladatütemezés nem érhető el.
- Ha a feladatütemezés futtatása, de függő tartalomcsomagokkal még nem állnak rendelkezésre a terjesztési pontokon, a feladatütemezés sikertelen lesz. Most tartalmának terjesztése az hiányzó (Ha ez nem volt terjesztve van még), vagy várjon, amíg a tartalom a terjesztési pontokon elérhetővé válik, és kattintson **előző** szeretné, hogy a feladat feladatütemezési keres újra a tartalmat.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Elérhető központi telepítések és a feladatütemezés tartalmának előzetes gyorsítótárazása
A feladatütemezés elérhető központi telepítéséhez 1702, verziójától kezdve dönthet úgy előzetes használatára. Előzetes lehetővé teszi a beállítás lehetővé teszi az ügyfél csak a megfelelő tartalom letöltésére, amint azt a központi telepítés kap. Ezért, amikor a felhasználó kattint **telepítése** a Szoftverközpontban, készen áll a tartalmat, és a telepítés megkezdése gyorsan, mert a tartalom a helyi merevlemez-meghajtón. További információkért lásd: [előzetes konfigurálása](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>A BIOS átalakítása UEFI helybeni frissítés során
Windows 10 Creators frissítés egy egyszerű konverzió eszközt, amely automatizálja a folyamat az UEFI-kompatibilis hardveres a merevlemez újraparticionálása, és az átalakítás eszközzel integrálódik a Windows 7, Windows 10 helyi frissítési folyamat vezet be. Ha az eszköz együttesen az operációs rendszer frissítési feladatütemezés és az OEM-eszközt, amely a belső vezérlőprogram a BIOS UEFI alakítja, átválthat a számítógépek BIOS UEFI helyben frissítés a Windows 10 Creators frissítés során. További információkért lásd: [feladatütemezési lépéseket BIOS kezeléséhez UEFI alakításához](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>Az alkalmazások telepítése feladatütemezés fejlesztései. lépés:
Ebben a verzióban bevezetett a következő fejlesztéseket kínálja:
- Alkalmazások telepítése esetén a 99 maximális számának növekedését a **alkalmazások telepítése** feladatütemezési lépés. Az előző maximális szám 9-es alkalmazások volt.
- -Alkalmazások hozzáadásakor a **alkalmazások telepítése** feladatütemezési lépést a feladatütemezés-szerkesztő, mostantól kiválaszthatja azon származó alkalmazásokat a **válassza ki a telepítendő alkalmazást** ablaktáblán.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>Az illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezés fejlesztései
Új feladatütemezési változók is elérhető az időtúllépés értéke konfigurálása az illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezési lépés a HTTP-katalógus kérések meghozásakor. A következő változók és az alapértelmezett értékek (másodpercben) érhetők el:
   - SMSTSDriverRequestResolveTimeOut  
     Alapértelmezett: 60
   - SMSTSDriverRequestConnectTimeOut  
     Alapértelmezett: 60
   - SMSTSDriverRequestSendTimeOut  
     Alapértelmezett: 60
   - SMSTSDriverRequestReceiveTimeOut  
     Alapértelmezett: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>A Windows 10 ADK buildszámát követik nyomon
A Windows 10 ADK Mostantól követi nyomon a Windows 10-es rendszerindító lemezképek testreszabásához, győződjön meg arról, hogy egy több támogatott élmény buildszámát. Például ha a webhely használ a Windows ADK for Windows 10, verziója 1607, csak rendszerindító lemezképek 10.0.14393 verziójával testreszabható a konzolon. WinPE-verziókat testreszabásával kapcsolatos részletekért lásd: [rendszerindító lemezképek testreszabása](/sccm/osd/get-started/customize-boot-images).

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>Alapértelmezett rendszerindító lemezkép forrásának elérési útvonalára már nem módosítható.
Alapértelmezett rendszerindító lemezképek a Configuration Manager által felügyelt, és az alapértelmezett rendszerindító lemezkép forrásának elérési útvonalára már nem módosítható a Configuration Manager konzolon, vagy a Configuration Manager SDK használatával. Továbbra is adja meg egy egyéni forrás elérési útját az egyéni rendszerindító lemezképeket.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>Alapértelmezett rendszerindító lemezképek rendszer újra létrehozza a rendszer a Configuration Manager egy új verziójára történő frissítés után
Ebben a kiadásban a Windows ADK-verzió frissítése és a majd használja a frissítések és karbantartás a Configuration Manager legújabb verziójának telepítéséhez verziótól kezdve a Configuration Manager újragenerálja az alapértelmezett rendszerindító lemezképeket. Ez magában foglalja a új Windows PE verziót a frissített Windows ADK, az új verziót a Configuration Manager-ügyfél, illesztőprogramok, testreszabások, stb. Egyéni rendszerindító lemezképeket nem módosulnak. További információkért lásd: [rendszerindító lemezképek kezelése](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault).

## <a name="software-updates"></a>Szoftverfrissítések

### <a name="deploy-office-365-apps-to-clients"></a>Office 365-alkalmazásokat telepíteni az ügyfelek számára
Az Office 365-ügyfél kezelési irányítópulton 1702, verziójától kezdve megkezdheti az Office 365-telepítő, amely lehetővé teszi az Office 365-telepítési beállítások konfigurálása, fájlokat tartalom kézbesítési hálózatokon (tartalomtovábbító) töltse le és telepíti a fájlokat a Configuration Manager alkalmazásként. További információkért lásd: [Office 365 ProPlus kezelése frissíti](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).

> [!IMPORTANT]
> Az Office 365-alkalmazást, amelynek létrehozása és telepítése az Office 365 varázsló a Configuration Manager használatával nem automatikusan kezeli a Configuration Manager által amíg nem engedélyezi a **felügyeletének engedélyezése az Office 365 ügyfél újra a** beállítás szoftverfrissítések ügyfélügynöke. További információkért lásd: [kapcsolatos](/sccm/core/clients/deploy/about-client-settings).

### <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10-es frissítés esetén expressz telepítési fájlokat kezelése
A Configuration Manager 1702 verziójától kezdve a Windows 10-frissítéseket támogatja az expressz telepítési fájlok. Ha a Windows 10 támogatott verzióját használja, a Configuration Manager beállítások segítségével csak az aktuális hónap a Windows 10 összegző frissítése és az előző hónap frissítés közötti változások letöltése. Az Expressz telepítés fájljai nélkül Configuration Manager letölti a teljes Windows 10-es összesítő frissítéssel (beleértve az előző hónap összes frissítését) minden hónapban. Az expressz telepítési fájlok használatával biztosít a kisebb tölt le és gyorsabb telepítési idejét, az ügyfeleken. További információkért lásd: [expressz telepítési fájlok kezelni a Windows 10 frissítései](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Mobil eszközök felügyelete

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android és iOS verziója már nem nem targetable a létrehozási varázslók a hibrid MDM

A hibrid mobileszköz-kezelés (MDM) 1702 verziójától kezdve már nem kell átadnia Android és iOS adott verzió új házirendek és profilok az Intune által felügyelt eszközök létrehozásakor. Ehelyett választhat a következő eszköztípusok esetében:

- Android
- Samsung KNOX szabvány 4.0 és újabb verziók
- iPhone
- iPad

Ez a módosítás érinti a varázsló a következő elemek létrehozásához:

- Konfigurációelemek
- Megfelelőségi szabályzatok
- Tanúsítványprofilok
- E-mail profilok
- A VPN-profilok
- Wi-Fi profilok

Ez a változás a hibrid telepítések is támogatást nyújt a gyorsabban új Android és iOS verziója egy új Configuration Manager-kiadás vagy a bővítmény anélkül. Az Intune önálló verziójának új verzió támogatott, ha felhasználók tudják verzió frissítése a mobileszközeiket.

A Configuration Manager korábbi verzióiról történő frissítése során előforduló problémák megelőzéséhez, mobil operációsrendszer-verziók továbbra is elérhetők ezek az elemek tulajdonságok lapját. Ha továbbra is szeretné egy adott verziójához, az új elem létrehozása, és adja meg a megcélzott verziója az újonnan létrehozott elemet a Tulajdonságok lapján.

### <a name="android-for-work-support"></a>Android munkahelyi támogatásához
1702 verziótól kezdődően hibrid mobileszköz-kezelés az Intune mostantól támogatja az Android munkahelyi eszközök regisztrációja és kezelése. Az útmutató a munkahelyi eszközök felügyelt Android:

- [Android munkahelyi eszközök regisztrálása](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Jóváhagyhatja és telepítheti az Android munkahelyi alkalmazások](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Konfigurációelemek létrehozása a munka androidhoz](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [A szelektív törlést az Android a munkahelyi eszközökön](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [E-mail profilok munka androidhoz](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Megfelelőségi szabályzatok Android for Work](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Eszközgyűjtemények mennyiségi programban vásárolt iOS-alkalmazások telepítése

Eszközök, valamint a felhasználók most már telepítheti az licencelt alkalmazások. Attól függően, hogy az alkalmazások képesek támogatni eszközlicencelési megfelelő licencre lesz engedte telepítésekor, az alábbiak szerint:

|||||
|-|-|-|-|
|Configuration Manager verziója|Alkalmazás licencelésre eszköz?|Központi telepítési gyűjtemény típusa|Az igényelt licenc|
|Korábbi, mint 1702|Igen|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Igen|Eszköz|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Eszköz|Felhasználói licenc|
|1702 és újabb verziók|Igen|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Nem|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Igen|Eszköz|Eszköz-licenc|
|1702 és újabb verziók|Nem|Eszköz|Felhasználói licenc|

Mennyiségi programban vásárolt iOS-alkalmazásokkal kapcsolatos további információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások felügyelete](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-ios-volume-purchase-program-for-education"></a>Támogatás az iOS Volume Purchase Program oktatási célokra

Most is telepítheti és nyomon követheti a vásárolt alkalmazásokat az IOS Volume Purchase Program oktatási célokra.
Mennyiségi programban vásárolt iOS-alkalmazásokkal kapcsolatos további információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások felügyelete](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>Több volume purchase program-tokenek támogatása

Több Apple volume purchase program-tokenek a Configuration Manager mostantól társíthat.
Mennyiségi programban vásárolt iOS-alkalmazásokkal kapcsolatos további információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások felügyelete](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>Az üzletági alkalmazások vállalati Windows áruházban támogatása

Most szinkronizálhatja az egyéni üzletági alkalmazások a vállalati Windows áruházban.

### <a name="conditional-access-device-compliance-policy-improvements"></a>Feltételes hozzáférés eszköz megfelelőségi házirend fejlesztései

Új eszköz megfelelőségi házirend szabály könnyíti meg blokkolni a hozzáférést a vállalati erőforrásokhoz, amelyek támogatják a feltételes hozzáférést, ha a felhasználók a nem megfelelő alkalmazások listája részét képező alkalmazásokat használnak. A nem megfelelő alkalmazások listája a rendszergazda által adható meg az új kompatibilis szabály hozzáadásakor **, amely nem telepíthető alkalmazások**. Ez a szabály van szükség a rendszergazdát, hogy adja meg a **alkalmazásnév**, a **Alkalmazásazonosító**, és a **alkalmazás kiadóját** (választható), amikor egy alkalmazás hozzáadását a nem megfelelő listájához. Ez a beállítás csak iOS és Android-eszközökre vonatkozik.

Ezenkívül ez segít a szervezeteknek csökkenthető az adatszivárgás keresztül nem biztonságos alkalmazásokat, és meg kell akadályozni az egyes alkalmazásokkal túl sok adatot fogyasztás.

- További [eszközmegfelelőségi szabályzatok működése](/sccm/mdm/deploy-use/device-compliance-policies).
- További [eszköz megfelelőségi házirendek létrehozásáról](/sccm/mdm/deploy-use/create-compliance-policy).

### <a name="new-mobile-threat-defense-monitoring-tools"></a>Új Mobile fenyegetés védelmi figyelési eszközök

1702 verziójától kezdve, hogy új módjai a figyelheti a Mobile fenyegetés védelmi szolgáltató megfelelőségi állapotát.

- További [Mobile fenyegetés védelmi megfelelőségi figyelése](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="protect-devices"></a>Eszközök védelme

### <a name="detect-outdated-antimalware-client-versions"></a>Elavult kártevőirtó ügyfélprogram verziói észlelése
1702 verziójával kezdve, hogy az Endpoint Protection-ügyfelek nem elavult riasztásokat lehet beállítani. További információkért lásd: [riasztási elavult kártevő-ügyfél](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions).

### <a name="device-health-attestation-updates"></a>Eszköz állapota tanúsítvány frissítése
Eszközállapot-igazolási szolgáltatás a helyi ügyfelek most is konfigurálhatók és kezelhetők a felügyeleti pontról. További információkért lásd: [az Eszközállapot-igazolás](/sccm/core/servers/manage/health-attestation).

### <a name="certificate-profiles-for-windows-hello-for-business"></a>A tanúsítványprofilok a vállalati Windows Hello

Ha szeretné tárolni a tanúsítványprofilok a Windows Hello-üzleti kulcstároló, és a tanúsítványprofil használja az intelligens kártya bejelentkezési EKU, konfigurálnia kell a kulcs regisztrációt, hogy a tanúsítvány helyesen érvényességéről engedélyeit.
További információkért lásd: [üzleti beállítások a Windows Hello-](/sccm/protect/deploy-use/windows-hello-for-business-settings).

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>Új Windows Hello-üzleti értesítés a végfelhasználók számára
Egy új Windows 10-értesítés tájékoztatja a végfelhasználók számára, hogy további műveletek végrehajtásához Windows Hello for Business telepítő (például a PIN-kód beállítása) szükséges.

