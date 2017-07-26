---
title: "Egy eszköz megfelelőségi szabályzat létrehozása és telepítése |} Microsoft Docs"
description: "Megtudhatja, hogyan létrehozása és telepítése az eszközmegfelelőségi szabályzatok a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 216d288aa7b7f2b98df86f59355d879366dcd44d
ms.openlocfilehash: 4baa6e0fe009f5f7dc33f5ab4adb1ec5e5c5271b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="create-and-deploy-a-device-compliance-policy"></a>Egy eszköz megfelelőségi szabályzat létrehozása és telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


## <a name="create-a-compliance-policy"></a>Megfelelőségi szabályzat létrehozása

1.  Kattintson a System Center Configuration Manager konzol **eszközök és megfelelőség**.

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások**, és válassza a **megfelelőségi szabályzatok**.

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **megfelelőségi szabályzat létrehozása**.

4.  Az a **általános** lap a megfelelőségi szabályzat létrehozása varázslót, adja meg a következő adatokat:

  * **Név**. Adjon meg egy egyedi nevet a megfelelőségi házirend számára. A maximális hossz 256 karaktert használhat.

  * **Leírás**. Adjon meg egy leírást, amely áttekintést nyújt a VPN-profilok, és azonosítja a Configuration Manager konzolon. A maximális hossz 256 karaktert használhat.

  * **Megfelelőségi szabályzat típusa**. Válassza ki a szabályzatot, amely szeretne létrehozni, attól függően, hogy az eszköz a Configuration Manager által felügyelt típusát. Ez vonatkozik, vagy újabb verzióra.<br /><br /> Az Intune által felügyelt eszközök esetében válassza **A Configuration Manager-ügyfél nélkül felügyelt eszközök megfelelőségi szabályai** beállítást. Ha ezt a lehetőséget választja, válassza ki a platform ezt a házirendet alkalmazni kívánt típusát.

  * **Meg nem felelés súlyossága jelentésekhez**. Itt adhatja meg, hogy milyen súlyossági szintről készüljön jelentés, ha ez a megfelelőségi szabályzat nem megfelelőnek minősül. A használható súlyossági szintek a következők:

     * **Nincs**. A megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.
     * **Információ**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** a Configuration Manager jelentésekben.   
     * **Figyelmeztetés**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.
     * **Kritikus**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.
     * **Kritikus eseménnyel**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.      

5.  Az a **által támogatott platformok** lapon, válassza ki az eszközplatformokat, amelyeknek ez a megfelelőségi szabályzat értékelve lesz, vagy válasszon **válassza ki az összes** az összes eszközplatform kiválasztásához. A támogatott platformok a következők: Windows 7, Windows 8.1 és Windows 10. A Windows Server 2008 R2, Windows Server 2012, a Windows Server 2012 R2 és a Windows Server 2016.

6.  A **Szabályok** lapon adhat meg egy vagy több szabályt annak meghatározáshoz, hogy az eszközök milyen konfigurációval értékelhetők megfelelőnek. Megfelelőségi szabályzat létrehozásakor egyes szabályok alapértelmezés szerint engedélyezettek, de akár szerkesztheti vagy törölheti is őket. A szabályok teljes listáját lásd: a "Megfelelőségi szabályzat előírásainak" című szakaszban található ebben a témakörben.

  > [!NOTE]  
  >  A Windows rendszerű számítógépeken Windows 8.1 operációs rendszer verziója az elvártnak megfelelően 8.1 helyett 6.3. Ha az operációs rendszer verzió a szabály a Windows 8.1 van megadva, a Windows, majd az eszköz rendszer nem megfelelőként még akkor is, ha az eszköz Windows 8.1. Győződjön meg arról, hogy a megfelelő *jelentett* verzióját Windows adja meg a minimális és maximális operációs rendszer szabályoknak. A verziószámnak meg kell egyeznie a verziója, amely a **winver** parancsot adja vissza. Windows-telefonok esetén nem jelentkezik ez a hiba, a verziószám az elvártnak megfelelően 8.1. Windows-számítógépekhez a Windows 10 operációs rendszert, a verziót kell beállítani: **10.0** plusz a szám, amely operációsrendszer-verzióval a **winver** parancsot adja vissza.

7.  Az a **összegzés** oldalon a varázsló, tekintse át a beállításokat végzett, és majd a varázsló.

 Az új szabályzat megjelenik a **megfelelőségi szabályzatok** csomópontjának a **eszközök és megfelelőség** munkaterületen.

## <a name="deploy-a-compliance-policy"></a>Megfelelőségi házirend telepítése

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség**.

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások**, és válassza a **megfelelőségi szabályzatok**.

3.  A a **Home** lap a **telepítési** csoportjában válassza **telepítés**.

4.  Az a **megfelelőségi szabályzat telepítése** párbeszédpanelen válassza ki **Tallózás** jelölje be a felhasználógyűjteményt, amelyre a szabályzatot telepíteni szeretné.

     Emellett riasztásokat, ha a házirend nem megfelelő, és állítsa be az ütemezést, amely ezzel a házirend-megfelelőség szempontjából kiértékelendő beállítások is választhat.

5.  Amikor elkészült, válassza ki a **OK**.

## <a name="monitor-the-compliance-policy"></a>A megfelelőségi házirend megfigyelése

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Az alábbi módon tekintheti meg a megfelelési eredményeket a Configuration Manager konzolon:

1.  Kattintson a Configuration Manager konzol **figyelés**.

2.  Az a **figyelés** munkaterületen, válassza a **központi telepítések**.

3.  Válassza ki a **Központi telepítések** listából a megfelelőségi szabályzat azon telepítését, amelynek meg szeretné tekinteni a megfelelőségi információit.

4.  A szabályzat központi telepítésének megfelelőségére vonatkozó összefoglaló információkat a főoldalon tudja ellenőrizni. Részletesebb adatok megtekintéséhez válassza ki a központi telepítést, majd a a **Home** lap a **telepítési** csoportjában válassza **állapotának megtekintése** megnyitásához a **központi telepítési állapot** lap.

    A **központi telepítési állapot** lap tartalmaz az alábbi fülekkel:

    -   **Megfelelő**. Az érintett eszközök száma alapján a szabályzat megfelelőségének megjelenítése. Választhat egy szabályt, amely hozzon létre egy ideiglenes csomópont alatt a **felhasználók** vagy **eszközök** munkaterület a **eszközök és megfelelőség** munkaterület, amely tartalmazza az összes felhasználó vagy eszköz, amelyek megfelelnek a következő szabálynak. A **eszköz adatai** ablaktábla megjeleníti azokat a felhasználókat vagy eszközöket, amelyek megfelelnek a házirendet. Kattintson duplán a kívánt felhasználóra vagy eszközre a listában további hibakeresési adatok megjelenítése.

    -   **Hiba**. Az érintett eszközök száma alapján szabályzatok kiválasztott telepítésével kapcsolatos összes hiba listáját tartalmazza. Választhat egy szabályt, amely hozzon létre egy ideiglenes csomópont alatt a **felhasználók** vagy **eszközök** csomópontjának a **eszközök és megfelelőség** munkaterület, amely tartalmazza az összes felhasználó vagy eszköz, a szabállyal kapcsolatban hibát okozó. Amikor kiválaszt egy felhasználót vagy eszközt, a **eszköz adatai** ablaktábla megjeleníti azokat a felhasználókat vagy eszközöket, amelyek egy probléma érint. Kattintson duplán a kívánt felhasználóra vagy eszközre a listában a probléma további információkat jelenít meg.

    -   **Nem megfelelő**. A házirend, az érintett eszközök száma alapján nem megfelelő szabályok teljes listáját tartalmazza. Választhat egy szabályt, amely hozzon létre egy ideiglenes csomópont alatt a **felhasználók** vagy **eszközök** csomópontjának a **eszközök és megfelelőség** munkaterület, amely tartalmazza az összes felhasználó vagy eszköz, amelyek nem felelnek meg a következő szabálynak. Amikor kiválaszt egy felhasználót vagy eszközt, a **eszköz adatai** ablaktábla megjeleníti azokat a felhasználókat vagy eszközöket, amelyek egy probléma érint. Kattintson duplán a kívánt felhasználóra vagy eszközre a listában megjelenítése további információt a problémáról.

    -   **Ismeretlen**. Összes felhasználók és eszközök, amelyek nem jelentettek megfelelőséget, az eszközök aktuális ügyfélállapotával együtt a szabályzatok kiválasztott telepítésével kapcsolatos listáját tartalmazza.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Az egyes eszközök megfelelőségi állapotának figyelése

1.  A Configuration Manager konzolon kattintson a **eszközök és megfelelőség** munkaterületen.

2.  Válasszon **eszközök**.

3.  Kattintson a jobb gombbal az oszlopokat további oszlopok engedélyezéséhez.

  A következő oszlopokat is hozzáadhat:

  - **Azure Active Directory-Eszközazonosító**.  Az Azure Active Directoryban az eszköz egyedi azonosítója.

  - **Megfelelőségi hiba részletes adatait**.  Hiba – részletek a végpont folyamat hibás működés vagy művelet során. Ha ez az oszlop üres, az azt jelenti, nincs hiba, és sikeresen történt a következő megfelelőségi állapotát.

  - **Megfelelőségi helyének**.  Ha a megfelelőségi nem további részleteket. Ha ez az oszlop üres, az azt jelenti, nincs hiba, és sikeresen történt a következő megfelelőségi állapotát. Ha a megfelelőségi folyamat meghiúsulhat példái: 
      - ConfigMgr-ügyfél
      - Felügyeleti pont
      - Intune
      - Az Azure Active Directory
<br></br>
  - **Megfelelőségi értékelés időpontjához**. Utolsó megfelelőségi be lett jelölve.

  - **Megfelelőségi idő beállítása**. Utolsó megfelelőségi módosításának időpontja az Azure Active Directoryhoz.

  - **Feltételes hozzáférés megfelelő**.  -E a gép megfelel a feltételes hozzáférési szabályzatokat.

  > [!IMPORTANT]
  > Ezekben az oszlopokban alapértelmezés szerint nem jelennek meg.

#### <a name="to-view-intune-compliance-policies-charts"></a>Intune megfelelőségi házirendek diagramok megtekintése
1. Válasszon 1610 a Configuration Manager verziója, a Configuration Manager konzolon kezdve **figyelés**.

2. Az a **figyelés** munkaterületén válassza **áttekintése** > **megfelelőségi beállítások** > **megfelelőségi szabályzatok**.

   Az alábbi diagramokon jelennek meg:

    - **Általános eszköz megfelelőségi**. Az összes megfelelőségi szabályzatok eszközök összesített megfelelőségének jeleníti meg.
    - **Meg nem felelés oka felső**. Azt mutatja meg a felső házirendeket mely eszközök megfelelőek.

3. Adja meg a szakasz vagy a diagram az eszközöket, amelyeket belül lebontva.

#### <a name="to-view-a-health-attestation-report"></a>Állapotigazolási jelentés megtekintése

1.  -Es verziótól 1602-es verziójában a Configuration Manager, a Configuration Manager konzolon válassza a **figyelés**.

2.  Eszközmegfelelőségi állapot szerinti az eszközök aktuális állapotát összesítő jelentés megtekintéséhez válassza **biztonsági**, és válassza a **az Eszközállapot-igazolás**.

3.  Minden eszköz és az összes állapotigazolási attribútumot felsoroló jelentés megtekintéséhez válassza **biztonsági**, és válassza a **az Eszközállapot-igazolás**.

## <a name="compliance-policy-rules"></a>Megfelelőségi szabályzat előírásainak
* **Jelszó igénylése mobileszközökön**. A felhasználók csak jelszó beírása után az eszköz eléréséhez lehet szükség.

  **Támogatja:**
    * Legalább Windows Phone 8
    * Legalább iOS 6
    * Android 4.0+
    * Samsung KNOX szabvány 4.0+

* **Az inaktív eszközök zárolásának feloldásához jelszó szükséges** (1602-es frissítés). A felhasználók csak jelszó beírása eszközhöz való hozzáféréshez zárolt lehet szükség.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **Ennyi perc inaktivitás után kell jelszót beírni** (1602-es frissítés). Az üresjárati idő előtt a felhasználónak kell írja be újból a jelszót is megadhat. Állítsa az értékét a rendelkezésre álló lehetőségek egyikére: **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 hour**.

  Ez a szabály használható **tétlen eszközök zárolásának feloldásához jelszó szükséges**. Az itt beállított érték határozza meg, amikor az eszköz tekinti tétlennek és zárolva van. Ha **tétlen eszközök zárolásának feloldásához jelszó szükséges** értéke **igaz**, a felhasználónak meg kell adnia egy jelszót a zárolt eszközhöz való hozzáféréshez.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Windows RT/8.1
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **Automatikus frissítések kötelezővé tétele** (1602-es frissítés). Eszközök, Windows 8.1 vagy újabb verziója szükséges telepítse a frissítéseket automatikusan, és megadhatja, hogy milyen besorolású frissítéseket.

  Az értéket kell megadni **nincs** akadályozza automatikus telepítését, a **ajánlott** automatikusan telepíteni az összes ajánlott frissítést vagy **fontos** csak a fontos besorolású frissítéseket telepíteni.

  **Támogatja:**
  * Legalább Windows Phone 8

* **Egyszerű jelszavak engedélyezése**. A felhasználók számára hozzon létre egyszerű jelszavak, például az "1234" vagy "1111." Ez a beállítás alapértelmezés szerint le van tiltva.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Legalább iOS 6

* **Jelszó minimális hossza**. Megadhatja a legkevesebb számjegyek vagy karakterek, hogy a jelszót kell-e (alapértelmezés szerint 6).

  **Támogatja:**
  * Legalább Windows Phone 8
  * Windows 8.1
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

  >[!NOTE]
  >A Windows rendszerű és Microsoft-fiókkal biztosított eszközök esetén a megfelelőségi házirend kiértékelése helytelen, ha meghiúsul **jelszó minimális hossza** hosszabb 8 karakternél, vagy ha **karakterkészletek minimális száma** több, mint 2.

* **Fájltitkosítás mobilkészüléken**. Megkövetelheti az eszközt titkosítani kell erőforrásokhoz való csatlakozáshoz. A Windows Phone 8-telefonok automatikusan titkosítva vannak. Az iOS rendszerű eszközök a **Jelszó igénylése mobileszközökön**beállítás konfigurálásával titkosíthatók. A beállítás alapértelmezés szerint engedélyezve van.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Windows 8.1
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **Eszköz nem lehet függetlenített vagy feltört eszköz**. Ha engedélyezi ezt a beállítást, (iOS) függetlenített vagy feltört (Android) eszközökön nincsenek megfelelő. Ez a beállítás alapértelmezés szerint le van tiltva.

  **Támogatja:**
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **E-mail profil az Intune által felügyeltnek kell**. Ha a beállítás **Igen**, az eszköz az eszközre telepített e-mail profilt kell használnia. Az eszköz nem minősíthető megfelelőnek, ha a levelezési profil nem a megfelelőségi házirend által célzott felhasználói csoportra van telepítve.

  Akkor sem lehet megfelelő, ha a felhasználó már beállított egy, az eszközre telepített Intune levelezési profillal egyező e-mail-fiókot az eszközön. Az Intune nem írhatja felül a felhasználó által létesített profilt, így nem kezelheti. A felhasználó is megfelelőségének az eszköz eltávolítása a meglévő e-mail beállításokat, amely lehetővé teszi az Intune-ban, telepítse a felügyelt levelezési profilt.

  A levelezési profilokról a [Hozzáférés engedélyezése a vállalati e-mailekhez a Microsoft Intune e-mail profiljaival](https://technet.microsoft.com/library/dn800672.aspx)című témakörben talál további információt. Ez a beállítás alapértelmezés szerint le van tiltva.

  **Támogatja:**
  * Legalább iOS 6

* **E-mail profil**. Ha **E-mail fiókot az Intune által felügyeltnek kell** van kiválasztva, válassza a **válasszon** eszközök felügyelni kívánt levelezési profil kiválasztásához. A levelezési profilnak megtalálhatónak kell lennie az eszközön.

  **Támogatja:**
  * Legalább iOS 6

* **Operációs rendszer szükséges minimális verziója**. Ha egy eszköz nem felel meg a minimális verziójára vonatkozó követelményt, amely megadja, hogy nem megfelelőként. Megjelenik egy hivatkozás a verziófrissítésre vonatkozó információk. A felhasználó választhat frissítheti az eszközt, amely után azok fog tudni hozzáférni a vállalati erőforrásokhoz.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Windows 8.1
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **Maximálisan engedélyezett operációsrendszer-verzió**. Ha egy eszköz operációsrendszer-verziótól újabb fut, amely a szabályban használja, a vállalati erőforrásokhoz való hozzáférés le van tiltva, és a felhasználónak kapcsolatba kell lépnie az informatikai rendszergazdával. Amíg nem módosítja a szabály, amely engedélyezi az operációs rendszer verziója, az eszköz nem használható vállalati erőforrások eléréséhez.

  **Támogatja:**
  * Legalább Windows Phone 8
  * Windows 8.1
  * Legalább iOS 6
  * Android 4.0+
  * Samsung KNOX szabvány 4.0+

* **Eszközök kifogástalanként való jelentésének megkövetelése** (1602-es frissítés). Beállíthat egy szabályt, a kell jelenteni a Windows 10-es eszközöket kifogástalan állapotúként az új vagy meglévő megfelelőségi házirendekben. Ha engedélyezi ezt a beállítást, a Windows 10-es eszközöket a rendszer értékeli a állapotfigyelő igazolási szolgáltatáson (HAS) keresztül ki a következő adatpontokhoz:

  - **A BitLocker engedélyezve van**. Ha a BitLocker, az eszköz, amely a meghajtón a jogosulatlan hozzáféréstől, amikor a rendszer ki van kapcsolva vagy hibernálva van adatainak védelemmel való.

   A Windows BitLocker meghajtótitkosítás a Windows operációs rendszer kötetén tárolt összes adatot titkosítja. A BitLocker a TPM a Windows operációs rendszer és a felhasználói adatok védelme érdekében. Annak érdekében, hogy a számítógép nem módosították, még akkor is, ha felügyelet nélküli, elveszett vagy ellopott hagyják segít.
   
   Ha a számítógépen kompatibilis TPM található, a BitLocker a TPM használatával zárolja az adatokat védő a titkosítási kulcsokat. Ezért a kulcsok nem érhetők el addig, amíg a TPM nem ellenőrizte a számítógép állapotát.

  - **A kódintegritás engedélyezett**. A kódintegritási szolgáltatás ellenőrzi az illesztőprogramok vagy a fájlrendszer integritását minden alkalommal, amikor a rendszer betölti azt a memóriába. A kódintegritás észleli, hogy egy aláíratlan illesztőt vagy rendszerfájlt fájl töltődött be a kernelbe. Azt is észleli, hogy megváltozott-e egy rendszerfájlt rendszergazdai jogosultságokkal rendelkező felhasználói fiók által elindított szoftverek.

  - **A biztonságos rendszerindítás engedélyezett**. Ha a biztonságos rendszerindítás engedélyezve van, a rendszer kényszeríti a gyárilag megbízható állapotban indul el. Is ha a biztonságos rendszerindítás engedélyezve van, a számítógép elindításához használt alapvető összetevőknek megfelelő titkosítási aláírásokkal, amelyekben az eszközt gyártó szervezet által megbízhatónak kell rendelkeznie. Az UEFI belső vezérlőprogram ellenőrzi ezt, mielőtt engedélyezi a számítógép elindítását. Ha bármely fájl nem eredeti, az aláírás feltörésével, a rendszer nem fog elindulni.

  - **A korai indítású kártevőirtó engedélyezett**. Ez a beállítás csak számítógépekre vonatkozik. A korai indítású kártevőirtó (ELAM) védelmet biztosít a hálózatban található számítógépeknek indításkor és a külső gyártóktól származó illesztőprogramok inicializálása előtt.
  
   Ez a szabály alapértelmezés szerint ki van kapcsolva.

  A HAS szolgáltatás működésével kapcsolatos információért lásd: [Állapotigazolási CSP](https://msdn.microsoft.com/library/dn934876.aspx).

  **Támogatja:**
  * Windows 10 és Windows 10 Mobile

- **Az eszköz nem telepíthető alkalmazások**. Felhasználók telepíteni az alkalmazást a rendszergazda nem megfelelő alkalmazások listájának, ha le lesz tiltva Ha próbálnak hozzáférni a vállalati e-mailek és más vállalati erőforrások, amelyek támogatják a feltételes hozzáférés. Ez a szabály szükséges az alkalmazás neve és az alkalmazás Azonosítóját, ha egy alkalmazás hozzáadása a nem megfelelőek listájához határozzák meg a rendszergazdával. Az alkalmazás kiadóját kettőhöz lehet hozzáadni, de ez nem szükséges.

    **Támogatja:**
      * Legalább iOS 6
      * Android 4.0+
      * Samsung KNOX szabvány 4.0+

### <a name="find-an-app-id"></a>Az alkalmazás azonosítója található

Az Alkalmazásazonosító, amely egyedileg azonosítja az alkalmazást az Apple és Google alkalmazásszolgáltatások belül azonosító, amely. Példa: com.contoso.myapp. Kereséséhez:

- **Android--**
    - Az alkalmazást a Google Play-azonosító tárolja az alkalmazás létrehozásához használt URL-cím található. Egy példa alkalmazás-azonosító: *...? id=com.companyname.appname & hl = en*

- **iOS**
    1. Az iTunes tárolja az URL-címet, keresse meg a azonosítószámát, például az ebben a példában: */id875948587? mt = 8*

    2. Egy webböngészőben nyissa meg a következő URL-cím, az szám cseréje az azonosítószámát, amely (ebben az esetben, az előző példában) található: https://itunes.apple.com/lookup?id=875948587

    3. Töltse le és nyissa meg a szöveges fájlt.
  
    4. A szöveg keresése **BundleID azonosítót**.

    Egy példa alkalmazás-azonosító: "*BundleID azonosítót*": "*com.companyname.appname*" 


