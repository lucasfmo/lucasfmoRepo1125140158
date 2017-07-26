---
title: "Mennyiségi programban vásárolt iOS-alkalmazások felügyelete |} Microsoft Docs"
description: "Telepíthetik, felügyelhetik és nyomon követheti az alkalmazások az iOS app store keretében vásárolt licencek."
ms.custom: na
ms.date: 05/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Mennyiségi programban vásárolt iOS-alkalmazások felügyelete a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*



 Az iOS app store lehetővé teszi egy olyan alkalmazáshoz, a vállalatban futtatni kívánt több licencet vásárolhat. Ezzel a megoldással csökkenthetők az adminisztratív terhek vásárolt alkalmazások különböző példányainak nyilvántartásával.  

 A System Center Configuration Manager segítségével telepítheti, és importálja a licencadatokat az app store-ból, és nyomon követni a felhasznált licencek számát a programon keresztül vásárolt iOS-alkalmazásokat kezeléséhez.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Nagy mennyiségben vásárolt alkalmazások felügyelete iOS-eszközökön  
 Az iOS-alkalmazások keresztül az Apple Volume Purchase Program (VPP) több licencet vásárol. Ebbe beletartozik az Apple VPP-fiók beállítása az Apple webhelyén, és az Apple VPP-token feltöltése a Configuration Manager alkalmazást, amelyet a következő lehetőségeket biztosítja:  

-   A mennyiségi vásárlás adatait a Configuration Manager szinkronizálni. 
 
- Az Apple Volume Purchase Program for Business, mind az Apple Volume Purchase Program oktatási célokra származó alkalmazások szinkronizálása.

- Több Apple volume purchase program-tokenek társítsa a Configuration Managerrel.

-   Vásárolt alkalmazások jelennek meg a Configuration Manager konzolon.  

-   Alkalmazások telepítése, ezek az alkalmazások figyeléséhez és nyomon követheti a minden alkalmazás felhasznált licencek számát.  

-   A Configuration Manager segítségével központilag telepített mennyiségi programban vásárolt alkalmazások eltávolításával szükség esetén licencek visszanyeréséhez.  

## <a name="before-you-start"></a>Előkészületek  
 Mielőtt elkezdené, meg kell szereznie a VPP-tokent az Apple-től, és töltse fel a Configuration Manager.  

-   Ha korábban VPP-tokent egy másik MDM-termékhez a meglévő Apple VPP-fiók, létre kell hoznia egy új Configuration Manager által használt.  
-   A tokenek egy évig érvényesek.  
-   Alapértelmezés szerint a Configuration Manager szinkronizál az Apple VPP szolgáltatásával naponta kétszer annak érdekében, hogy a licenceket a Configuration Manager vannak szinkronizálva.  
      Csak a licencek módosítása vannak szinkronizálva. De hét naponta, a teljes szinkronizálás történik.  
      Ha úgy dönt, **szinkronizálási** manuális szinkronizálás azonban ez fogja mindig tegye a teljes szinkronizálás.  
-   Ha szeretné helyreállítani, vagy a Configuration Manager-adatbázis visszaállítása, azt javasoljuk, hogy ezt követően, hogy a szinkronizált Licencadatok naprakész manuális szinkronizálást végezzen.  
-   Ezen felül kell importált egy érvényes Apple Push Notification szolgáltatás (APNs) tanúsítványát az Apple-től lehetővé teszi, hogy az iOS-eszközök, beleértve az alkalmazások telepítésének kezelése. További információkért lásd: [iOS hibrid Eszközkezelés beállítása](enroll-hybrid-ios-mac.md).  
-   A Configuration Manager támogatja legfeljebb 3000 VPP-tokenek hozzáadása.

A System Center Configuration Manager 1702 kezdve, most már telepítheti licencelt alkalmazások eszközök, valamint a felhasználók. Attól függően, hogy az alkalmazások képesek támogatni eszközlicencelési megfelelő licencre lesz engedte telepítésekor, az alábbiak szerint:

|||||
|-|-|-|-|
|Configuration Manager verziója|Alkalmazás licencelésre eszköz?|Központi telepítés gyűjtemény típusa|Az igényelt licenc|
|Korábbi, mint 1702|Igen|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Igen|Eszköz|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Eszköz|Felhasználói licenc|
|1702 és újabb verziók|Igen|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Nem|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Igen|Eszköz|Eszköz-licenc|
|1702 és újabb verziók|Nem|Eszköz|Felhasználói licenc|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>1. lépés – Apple VPP-token beszerzése és feltöltése  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Felhőszolgáltatások** > **Apple Volume Purchase Program-tokenek**.   

3.  Az a **Home** lap a **Apple Volume Purchase Program-tokenek** csoportjában válassza **hozzáadása Apple mennyiségi vásárlási Program Token**.  

4.  Az a **általános** oldalán a **hozzáadása Apple mennyiségi vásárlási Program Token** varázsló, állítsa be a következőket:   

    -   **Név** – Itt adhatja meg a token nevét, amely megjelenik a Configuration Manager konzolon.  

    -   **Token** -válasszon **Tallózás**, majd válassza a VPP-tokent az Apple webhelyről letöltött.  

         Válassza ki a **tekintse meg az Apple VPP-fiók** hivatkozásra, és ha még nem tette meg, iratkozzon fel az üzleti vagy oktatási mennyiségi vásárlási program. Miután jelentkezett, le az Apple VPP-tokent fiókjához.  

    -   **Leírás** : nem kötelezően, adjon meg egy leírást, amely segít azonosítani a VPP-tokent a Configuration Manager konzolon.  

    -   **Kategóriák a Keresés és szűrés javítása érdekében hozzárendelt** : nem kötelezően, Kategóriák hozzárendelése a VPP-token használatával könnyebben keresse meg a Configuration Manager konzolon.  
    -   **Apple ID** -adja meg a VPP-Token társított apple e-mail Azonosítóját.
    -   **Jogkivonattípushoz** -válassza ki a használni kívánt VPP-tokent. Választhat **üzleti** és **oktatási** lexikális elem típusa.

5.  Válasszon **következő**, majd fejezze be a varázslót.  

Az a **Apple Volume Purchase Program-tokenek** csomópont, megtekintheti az Apple VPP-token beleértve az utolsó frissítés idejét, a lejárat idejét, valamint hogy mikor volt utoljára szinkronizálva kapcsolatos információkat.

Teljes mértékben lehet szinkronizálni az adatokat, és a Configuration Managerben az Apple által tárolt bármikor kiválasztásával **szinkronizálási** a a **Home** lapra a **szinkronizálási** csoport.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>2. lépés – Mennyiségi programban vásárolt alkalmazás telepítése  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **Áruházbeli alkalmazások Licencadatai**.  

3.  Válassza ki az alkalmazást, amelyet szeretne telepíteni, majd a a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása**.
A Configuration Manager-alkalmazás, amely jön létre a Windows Áruházbeli alkalmazás rendelkezik. Ezután telepítheti és figyelheti az alkalmazás, mint bármely más Configuration Manager-alkalmazás.

    > [!IMPORTANT]  
    > Ki kell választania egy központi telepítési céllal **szükséges**. Rendelkezésre álló telepítések jelenleg nem támogatottak.

 Az alkalmazás központi telepítésekor licenc szolgál, mely felhasználó vagy eszköz telepíti, minden eszközön, amelyhez telepíti az alkalmazást.  Ha célként egy olyan alkalmazással, hogy az eszköz licencelésre eszközgyűjteményt, egy eszköz licencet igényelnek.  Ha célként egy olyan alkalmazással, amely nem támogatja az eszköz licencelési eszközgyűjteményt, felhasználói licencet igényelnek. 

 Ha az alkalmazást hoz létre a **Áruházbeli alkalmazások Licencadatai** csomópont, az alkalmazás társítva a kiválasztott alkalmazás lexikális eleme licencei.  Megjelenhet például ugyanahhoz az alkalmazáshoz, a csomópont két verziója. Ennek oka az, az alkalmazás minden verziója társítva egy másik Apple VPP-tokent.  Akkor lehetett majd létrehozása alkalmazások minden jogkivonatból, és azok seperately.

 A licencek visszanyeréséhez létre kell hoznia egy új központi telepítést, az alkalmazás központi telepítési művelettel **Eltávolítás**. A központi telepítési műveletet az eredeti telepítés nem módosítható. A licenc az alkalmazás eltávolítása után felszabadul.  

## <a name="step-3---monitor-ios-vpp-apps"></a>3. lépés – iOS VPP-alkalmazások figyelése  
 A **Áruházbeli alkalmazások Licencadatai** csomópontjának a **szoftverkönyvtár** munkaterület a mennyiségi programban vásárolt iOS-alkalmazások információit jeleníti meg. Az információ tartalmazza a minden alkalmazás saját licencek számát és a szám, amellyel telepítették. Emellett a nézet jeleníti meg, mely VPP-tokent, az alkalmazás társítva van, és a lexikális elem típusa

 Minden VPP-alkalmazások használatával beszerezte a licenchasználatot is figyelheti a **Apple Volume Purchase Program-alkalmazások iOS licencszámokkal** jelentés.  

 Ez a jelentés tartalmazza a licencek számát és minden alkalmazás nevét, hogy vásárolta, a rendelkezésre álló licencek számát és további.  

 A Configuration Manager jelentések futtatása, lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

