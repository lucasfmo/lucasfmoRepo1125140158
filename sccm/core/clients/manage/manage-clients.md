---
title: "Ügyfelek kezelése |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager-ügyfelek kezeléséhez."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3a86924b2e5db3ac16eeda78b95ae6747ffd656f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Ügyfélszoftverek kezelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-ügyfél telepítése és a Configuration Manager-helyhez rendelése sikeresen megtörtént, az eszköz megjelenik a **eszközök és megfelelőség** munkaterületén a **eszközök** csomópont, és egy vagy több gyűjteményében a **Eszközgyűjtemények** csomópont. Az eszköz vagy egy gyűjtemény kiválasztásakor kezelési műveleteket hajthat végre. Azonban módon is más kezeléséhez az ügyfél, amely más munkaterületeit igényelhetik a konzolon, vagy olyan feladatokat, amelyek nem használják a Configuration Manager konzolon.  

> [!NOTE]  
>  A Configuration Manager-ügyfél előfordulhat, hogy telepítve, amely nem jelenik meg a Configuration Manager konzolon. Ez akkor fordulhat elő, ha az ügyfél még nem még sikeresen helyhez rendelt, vagy frissíteni kell a konzol vagy egy gyűjteménytagságot.  
>   
>  Ezenkívül egy eszköz akkor is megjelenhet a konzolon, ha a Configuration Manager-ügyfél nincs telepítve. Ez akkor fordulhat elő, ha az eszköz felderítése sikerült, de a Configuration Manager-ügyfél nincs telepítve és hozzárendelve. Az Exchange Server-összekötő, és a Microsoft Intune által beléptetett eszközök segítségével kezelt mobileszközök ne telepítse a Configuration Manager-ügyfél.  
>   
>  Használja a **ügyfél** oszlopot annak meghatározásához, hogy a Configuration Manager-ügyfél telepítve van, hogy a Configuration Manager konzolon kezelheti a Configuration Manager konzolon.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Ügyfelek kezelése az Eszközök csomópontból  

Vegye figyelembe, hogy az eszköz típusától függően a beállítások egy része nem feltétlenül érhető el.  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** >  **eszközök**.  

3.  Válassza ki egy vagy több eszközön, és válasszon egyet ezek ügyfélkezelési feladatot a menüszalagról, vagy kattintson a jobb gombbal az eszközre:  

    -   **A felhasználó-eszköz kapcsolatra vonatkozó információk kezelése**  

         Konfigurálja a felhasználók és eszközök közötti társításokat, így hatékony szoftverek telepítése a felhasználók számára.  

         Lásd: [Felhasználók és eszközök összekapcsolása felhasználó és eszköz közti kapcsolattal a System Center Configuration Managerben](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

    -   **Eszköz hozzáadása egy új vagy meglévő gyűjteményhez**  

         Adja hozzá az eszközt egy gyűjteményhez közvetlen szabály.  
         
    -   **Az ügyfél telepítése és újratelepítése az Ügyfél leküldése varázsló segítségével**  

         Telepítse, majd telepítse újra a Configuration Manager-ügyfél, javításának vagy újrakonfigurálásának a Windows rendszerű számítógépeken. Magában foglalja a webhely konfigurációs beállításai és az ügyfélleküldéses telepítés beállított client.msi-tulajdonságokat.  

        > [!TIP]  
        >  A Configuration Manager-ügyfél telepítésének (és újratelepítésének) számos különböző módja van. Bár az ügyfél leküldése varázsló kínál kényelmes ügyfél-telepítési módszer a konzolról futtatható, mert ez a módszer számos függőséggel rendelkezik, és a rendszer nem alkalmas minden környezethez. További információ a függőségekről: [Az ügyfélszoftverek Windows rendszerű számítógépekre történő központi telepítésével kapcsolatos előfeltételek a System Center Configuration Managerben](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md). További információk a többi ügyfél-telepítési módszerekről: [Ügyfél-telepítési módszerek a System Center Configuration Managerben](../../../core/clients/deploy/plan/client-installation-methods.md).  

         Lásd: [A Configuration Manager-ügyfelek telepítése ügyfélleküldés használatával](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Hely újbóli hozzárendelése**  

         Újból hozzárendelhet egy vagy több ügyfelet, köztük a kezelt mobileszközöket is egy másik elsődleges helyhez a hierarchiában. Az ügyfelek új helyhez való ismételt hozzárendelése elvégezhető egyenként, vagy több ügyfelet kijelölve csoportosan.  

    -   **Ügyfél távoli felügyelete**  

         Egy Windows-ügyfél hardver- és szoftverleltár adatainak megtekintéséhez, és a Távvezérlés, Távsegítség vagy Távoli asztal programok segítségével történő távoli felügyeletéhez futtathatja az erőforrás-kezelőt.  

         Lásd: [A hardverleltár megjelenítése az erőforrás-kezelővel a System Center Configuration Managerben](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) és [A szoftverleltár megjelenítése az erőforrás-kezelővel a System Center Configuration Managerben](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Lásd: [Windows rendszerű ügyfélszámítógépek távoli felügyelete a System Center Configuration Manager használatával](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Ügyfél jóváhagyása**  

         Ha az ügyfél kommunikál a helyrendszerekkel HTTP- és egy önaláírt tanúsítványt használ, ezek az ügyfelek megbízható számítógépekként azonosítsa azokat jóvá kell hagynia. A helykonfiguráció alapértelmezés szerint automatikusan jóváhagyja az azonos Active Directory-erdőben és a megbízható erdőkben lévő ügyfeleket, így Önnek nem kell saját kezűleg jóváhagynia minden egyes ügyfelet. Az Ön számára megbízható, munkacsoporthoz tartozó, illetve az Ön számára megbízható egyéb, de jóvá nem hagyott számítógépeket azonban saját kezűleg kell jóváhagynia.  

        > [!WARNING]  
        >  Habár bizonyos kezelési funkciók működhetnek a jóvá nem hagyott ügyfelek, ezt a Configuration Manager nem támogatott lehetőséget.  

         Nem kell jóváhagynia a mindig a helyrendszerek HTTPS-kapcsolaton keresztül kommunikáló ügyfelek vagy a HTTP-n keresztül helyrendszerekkel való kommunikáció során a PKI-tanúsítványt használó ügyfeleket. Ezek az ügyfelek a PKI-tanúsítványok segítségével megbízhatósági kapcsolatot.  

    -   **Ügyfél letiltása és a tiltás feloldása**  

         Letilt egy ügyfelet, már nem megbízható, ezáltal megakadályozhatja, hogy megkapja az ügyfélházirendet, és a Configuration Manager helyrendszerei kommunikálhatnak vele.  

        > [!WARNING]  
        >  Ügyfél letiltása csak megakadályozza, hogy a Configuration Manager helyrendszerei és az ügyfél közötti kommunikáció, és nem akadályozza meg a többi eszközzel való kommunikációra. Ezenkívül, amikor az ügyfél HTTP helyett HTTPS segítségével kommunikál a helyrendszerekkel, életbe lépnek bizonyos biztonsági korlátozások.  

         A letiltott ügyfél blokkolásának feloldásához. Ha azonban olyan Intel AMT-alapú számítógépet tilt le, amelyen letiltásakor ki volt építve az AMT, akkor további lépések szükségesek, mielőtt újból a sávon kívül kezelhetné ezt a számítógépet.  

         Lásd: [Annak meghatározása, hogy szükséges-e az ügyfelek blokkolása a System Center Configuration Managerben](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Szükséges PXE központi telepítés törlése**  

         Szükséges PXE központi telepítések a számítógép újratelepítése.  

         Lásd: [A Windows központi telepítése a hálózaton keresztül PXE segítségével a System Center Configuration Managerben](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **Ügyfél tulajdonságainak kezelése**  

         A felderítési adatokat és az ügyfél célzott központi telepítések megtekintése. Feladatütemezések használata operációs rendszer központi telepítése az eszközre változók is konfigurálhatja.  

    -   **Ügyfél törlése**  

        > [!WARNING]  
        >  Törölje az ügyfelet, ha azt szeretné, hogy a Configuration Manager-ügyfél eltávolításához, vagy egy gyűjteményből szeretné kivenni.  

         A **törlése** művelettel manuálisan törölheti az ügyfélrekordot a Configuration Manager-adatbázisból, és általában, ne használja a művelet kivéve a hibaelhárítás esetén ajánlott. Ha törli az ügyfélrekordot, és az ügyfél továbbra is és a Configuration Managerrel való kommunikációhoz, a Szívveréses felderítés újból létre fogja hozni az ügyfélrekordot, és az újból meg fog jelenni a Configuration Manager konzolban, miközben az ügyfélelőzmények és a korábbi társítások elvesznek.  

        > [!NOTE]  
        >  Ha töröl egy Configuration Manager által beléptetett mobileszközügyfelet, ezzel a művelettel a mobileszköz számára korábban kiadott PKI-tanúsítványt is visszavonja, és ez a tanúsítvány majd elutasította a felügyeleti ponttal, még akkor is, ha az IIS nem ellenőrzi a CRL-t. A hagyományos mobileszközügyfeleken lévő tanúsítványok nem kerülnek visszavonásra ezeknek az ügyfeleknek a törlésekor.  

         Az ügyfél eltávolításához lásd: [A Configuration Manager-ügyfél eltávolítása](#BKMK_UninstalClient).  

         Ügyfél kijelölése egy új elsődleges helyhez: [Ügyfélszoftverek helyhez rendelése a System Center Configuration Managerben](../../../core/clients/deploy/assign-clients-to-a-site.md).  

         Ha el szeretné távolítani az ügyfelet egy gyűjteményből, újra kell konfigurálnia a gyűjtemény tulajdonságait. Lásd: [Gyűjtemények kezelése a System Center Configuration Managerben](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Mobileszköz összes adatának törlése**  

         Az összes adat törlésére vonatkozó parancsot támogató mobileszközökről az összes adat törölhető.  

         Ez a művelet végleg törli a mobileszközön, beleértve a személyes beállítás és személyes adat összes adatot. Ezzel a művelettel általában visszaállítja a mobileszközön az alapértelmezett gyári beállításokat. Törlés mobileszközökre a mobil eszköz már nem megbízható, például, ha elveszett vagy ellopták.  

        > [!TIP]  
        >  A gyártó dokumentációjában olvashat arról, hogy a mobileszközök hogyan dolgozza fel a távoli törlési parancsot.  

         Késik gyakran mindaddig, amíg a mobileszköz megkapja a parancsot:  

        -   A mobil eszköz regisztrálva van a Configuration Manager vagy a Microsoft Intune-nal, ha az ügyfél megkapja a parancsot, amikor letölti az ügyfélházirendjét.  

        -   Ha a mobileszközt az Exchange Server-összekötővel kezeli, akkor kapja a parancsot, amikor Exchange szinkronizálják.  

         Használhatja a **Adattörlés állapota** oszlop figyelő észleli, ha az eszköz megkapja a parancsot. Amíg az eszköz küld a törlési visszaigazolás a Configuration Manager megszakíthatja a Törlés parancsot.  

    -   **Mobileszköz kivonása**  

         A **kivonás** beállítás csak az Intune-ban vagy a beléptetett mobileszközök támogatott\-helyszíni mobileszköz-kezelés.  

         További információkat lásd: [Az adatok védelme a System Center Configuration Manager segítségével végzett távoli törléssel, távoli zárolással és PIN-kód cserével](../../../mdm/deploy-use/wipe-lock-reset-devices.md).  

    -   **Egy eszköz tulajdonjogának módosítása**  

         Eszközök tulajdonjoga módosítható **vállalati** vagy **személyes** Ha egy eszköz nincs tartományhoz, és nincs telepítve a Configuration Manager-ügyfél.  

         Ez az érték használhatja alkalmazáskövetelményeket központi telepítések, és szabályozására, hogy mennyi leltáradatot gyűjtsön a rendszer a felhasználói eszközökről.  

        Előfordulhat, hogy kell hozzáadnia a **eszköz tulajdonos** a nézetet, kattintson a jobb gombbal bármely oszlopának fejlécére, és válassza az oszlop.

         További információk: [Hibrid mobileszköz-felügyelet a System Center Configuration Managerrel és a Microsoft Intune-nal](../../../mdm/understand/hybrid-mobile-device-management.md).  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> Ügyfelek kezelése az Eszközgyűjtemények csomópontból  
  Sok eszköz vagy a több eszközön végrehajtható feladatokat a **eszközök** csomópont gyűjtemények végezhető. Ez automatikusan alkalmazza a művelet a gyűjteményben lévő összes jogosult eszközre. Vegye figyelembe, hogy ez egy számos hálózati csomagot hoz létre, és növeli a CPU-használat a kiszolgálón.  

  Mielőtt gyűjteményszintű ügyfélkezelési feladatokat hajtana végre, gondolja át, hogy hány készülék található a gyűjteményben, ezek alacsony sávszélességű hálózati kapcsolat révén csatlakoznak-e, és mennyi ideig fog tartani a feladat befejezése az összes eszköz esetén. Miután elindult, a konzol a feladat nem állítható le.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>Ügyfelek kezelése az Eszközgyűjtemények csomópontból  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Eszközgyűjtemények**.  

3.  Válasszon ki egy gyűjteményt, és válasszon egyet a következő ügyfélkezelési feladatot a menüszalagról, vagy kattintson a jobb gombbal a gyűjteményben. Ezen ügyfél-felügyeleti feladatok is *csak* a gyűjtemény szintjén kell végrehajtani.  

    -   **Kártevők keresése a számítógépeken, és kártevőirtó-definíciós fájlok letöltése.**  

         Lásd: [a System Center Configuration Managerben az Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md).  

    -   **Szoftverek, alapkonfigurációk és feladatütemezések központi telepítése.**  

         Lásd:  

        -   [A System Center Configuration Manager szoftverfrissítések központi telepítése](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [Tervezze meg, és a System Center Configuration Manager megfelelőségi beállításainak konfigurálása](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **Energiagazdálkodási beállítások konfigurálása.**  

         Lásd: [Energiasémák létrehozása és alkalmazása a System Center Configuration Managerben](../../../core/clients/manage/power/create-and-apply-power-plans.md). Energiasémák csak olyan számítógépeken használhatók, amelyeken Windows fut.  

    -   **Számítógépek értesítése a házirend mihamarabbi letöltése érdekében.**  

         Az ügyfélértesítés használatával értesítheti a kijelölt Windows-ügyfelek a lehető leghamarabb kívül az ügyfélházirend lekérdezési időköze számítógép-házirend letöltése.  

         Az ügyfélértesítési feladatok a **Figyelés** munkaterület **Ügyfélműveletek** csomópontjában jelennek meg.  

##  <a name="BKMK_ClientCache"></a> A Configuration Manager-ügyfelekhez tartozó ügyfélgyorsítótár konfigurálása  
Az ügyfél gyorsítótárában tárolja az ideiglenes fájlok ügyfelek alkalmazások és programok telepítésekor. A szoftverfrissítések szintén az ügyfélgyorsítótárat használják, de nem korlátozza őket a gyorsítótár beállított mérete, is minden esetben megpróbálkoznak a gyorsítótárba való letöltéssel. Az ügyfélgyorsítótár beállításait, például méret és elhelyezkedés, beállíthatja a Configuration Manager ügyfél telepítésekor manuálisan, az ügyfélleküldéses telepítés használatakor vagy az ügyfél telepítése után.

Verziótól kezdődően a Configuration Manager verziója 1606 mappa gyorsítótárméret ügyfélbeállítások a Configuration Manager konzol használatával adhatja meg.   

 A Configuration Manager-ügyfélgyorsítótár alapértelmezett helye %*windir*%\ccmcache, alapértelmezett mérete pedig 5120 MB.  

> [!IMPORTANT]  
>  Az ügyfélgyorsítótárat tartalmazó mappát ne titkosítsa. A Configuration Manager nem tud tartalmat letölteni a titkosított mappákba.  

### <a name="about-client-cache"></a>Az ügyfélgyorsítótár ismertetése  

A Configuration Manager-ügyfél letölti a szükséges szoftverekhez tartozó tartalmat, miután megkapta a központi telepítési feladatot, de a futtatással vár, amíg a központi telepítés ütemezett időpontjáig. A megadott időpontban a Configuration Manager-ügyfél ellenőrzi, hogy a tartalom elérhető a gyorsítótárban. Ha a tartalom megtalálható a gyorsítótárban, és a megfelelő verzióját, az ügyfél használja a gyorsítótárazott tartalom. Ha a tartalom szükséges verziója megváltozott, vagy ha a tartalmát törölték, hogy helyet biztosítsanak az egy olyan másik csomaghoz, a tartalmat ismét letölti a gyorsítótár.  

Az ügyfél megpróbálja letölteni egy programhoz vagy alkalmazáshoz, a gyorsítótár méreténél nagyobb tartalmat, ha a központi telepítés elégséges méretű gyorsítótár miatt meghiúsul, és a Configuration Manager 10050-es Azonosítójú állapotüzenetet generál. Ha később megnövelik a gyorsítótár méretét, az eredmény a következő:  

-   Szükséges programoknál: Az ügyfél nem próbálja meg automatikusan újra letölteni a tartalmat. A csomag és a program központi telepítését újra el kell végeznie az ügyfélre.  
-   Szükséges alkalmazások esetén: Az ügyfél automatikusan újrapróbálkozik a tartalom letöltésével, amikor letölti az ügyfélházirendjét.  

Ha az ügyfél próbál meg letölteni egy csomagot, amely kisebb, mint a gyorsítótárban, de a gyorsítótár mérete teljes, az összes kötelező központi telepítések mindaddig, amíg a gyorsítótár-terület érhető el, amíg a letöltés időkorlátja le, vagy az Újrapróbálkozási korlát elérését a gyorsítótár-terület hiba továbbra is újrapróbálkozik. Ha később megnövelik a gyorsítótár méretét, a Configuration Manager-ügyfél megkísérli letölteni a csomagot a következő újrapróbálkozási időszak során újra. Az ügyfél négyóránként próbálja meg letölteni a tartalmat, amíg el nem éri a 18-szori próbálkozást.  

A gyorsítótárazott tartalmat nem törli automatikusan a rendszer: az legalább egy napig a gyorsítótárban marad azt követően, hogy az ügyfél felhasználta az adott tartalmat. Ha a csomagtulajdonságokban konfigurálja a tartalom megőrzését az ügyfélgyorsítótárban, az ügyfél nem törli automatikusan a csomagot a gyorsítótárból. Ha az ügyfélgyorsítótár területét elfoglalják a legutóbbi 24 órában letöltött csomagok, és az ügyfélnek új csomagokat kell letöltenie, akkor növelheti az ügyfélgyorsítótár méretét, vagy kiválaszthatja a törlési lehetőséget a megőrzött gyorsítótár-tartalmak törlése érdekében.  

 Az alábbi módszerekkel konfigurálhatja az ügyfélgyorsítótárat a manuális ügyféltelepítés során vagy az ügyféltelepítést követően.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>Az ügyfélgyorsítótár konfigurálása az ügyfelek manuális telepítésekor  

Futtassa a CCMSetup.exe parancsot a telepítés forráshelyéről, és adja meg szükség szerint a következő paramétereket szóközzel elválasztva:  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE:  

        > [!NOTE]
        > Verzió 1606, használja a gyorsítótár méretének beállításai **ügyfélbeállítások** SMSCACHESIZE helyett a Configuration Manager konzolon. További információk: [Az ügyfél gyorsítótár-beállításai](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

További információk a CCMSetup.exe ezen parancssori tulajdonságairól: [Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>Az ügyfélgyorsítótár mappájának konfigurálása az ügyfelek ügyfélleküldéses telepítésekor  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**.  

3.  Válassza ki a megfelelő helyet, és a a **Home** lap a **beállítások** csoportjában válassza **ügyfél-telepítési beállítások** > **telepítési tulajdonságai lap**.  

5.  Az alábbi tulajdonságokat, szóközökkel tagolva adja meg:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE:  

        > [!NOTE]
        > Verzió 1606, használja a gyorsítótár méretének beállításai **ügyfélbeállítások** SMSCACHESIZE helyett a Configuration Manager konzolon. További információk: [Az ügyfél gyorsítótár-beállításai](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

       További információk a CCMSetup.exe ezen parancssori tulajdonságairól: [Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>Az ügyfélgyorsítótár mappájának konfigurálása az ügyfélszámítógépen  

1.  Az ügyfélszámítógépen navigáljon **Configuration Manager** Vezérlőpult, és kattintson duplán a Tulajdonságok megnyitásához.  

2.  Az a **gyorsítótár** lapon a hely és a hely tulajdonságainak beállítása. Az alapértelmezett hely a *%windir%*\ccmcache mappa.  

5.  A gyorsítótár mappában lévő fájlok törléséhez válassza **törlése fájlok**.  

    > [!NOTE]
    > 
    > A gyorsítótár mappája a szokásos Windows-mappában,, így a Törlés a mappa tartalmát egy parancsfájl, a segédprogram használatával, vagy a PowerShell-parancsmaggal automatizálható `Remove-Item`. 


### <a name="to-configure-client-cache-size-in-client-settings"></a>Ügyfélgyorsítótár-méret konfigurálása az Ügyfélbeállításokban

1606 verziójától kezdve beállíthatja az ügyfélgyorsítótár-mappa méretét az ügyfél újratelepítése nélkül. Ehhez állítsa be az ügyfélgyorsítótár méretét a Configuration Manager konzolon az ügyfélbeállítások használatával.  

1. A Configuration Manager konzolon kattintson az **Adminisztráció** > **Ügyfélbeállítások**elemre.

2. Kattintson duplán az **Alapértelmezett ügyfélbeállítások**elemre.
  Egyedi ügyfélbeállításokat is létrehozhat, hogy a gyorsítótárméretet szelektívebben alkalmazhassa. További információk az alapértelmezett és az egyedi ügyfélbeállításokról: [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-settings.md).

 3. Válassza ki **Ügyfélgyorsítótár beállításait** válassza **Igen** a **ügyfélgyorsítótár méretének beállítása**, majd használja a **MB** vagy **lemezbeállításokat százaléka**. A gyorsítótár a kisebb mérethez igazodik.

     A következő ügyfélházirend letöltésekor a Configuration Manager-ügyfél ezekkel a beállításokkal fogja konfigurálni a gyorsítótárméretet.

##  <a name="BKMK_UninstalClient"></a> A Configuration Manager-ügyfél eltávolítása  
 Eltávolíthatja a Windows Configuration Manager-ügyfélszoftvert a számítógépről a **CCMSetup.exe** rendelkező a **/Uninstall** tulajdonság. A CCMSetup.exe parancsot futtathatja egyetlen számítógépen, vagy telepíthet központilag egy csomagot és programot az ügyfél több számítógépről való eltávolításához.  

> [!WARNING]  
>  A Configuration Manager-ügyfelet egy mobileszközről nem lehet eltávolítani. Ha el kell távolítania a Configuration Manager-ügyfelet egy mobileszközről, akkor ezt az eszközt, amely a mobileszköz összes adatát törli kitakarítása.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>A Configuration Manager-ügyfél eltávolítása a parancssorból  

1.  Nyisson meg egy Windows-parancssort, és lépjen abba a mappába, amelyben a CCMSetup.exe fájl található.  

2.  Írja be a **Ccmsetup.exe /uninstall**parancsot, majd nyomja meg az **Enter**billentyűt.  

> [!NOTE]  
>  Az eltávolítási folyamat nem jelenít meg eredményt a képernyőn. Ügyfél eltávolításának sikerességéről meggyőződhet, vizsgálja meg a naplófájl **CCMSetup.log** mappában *%windir%\ ccmsetup* az ügyfélszámítógépen.  

##  <a name="BKMK_ConflictingRecords"></a> A Configuration Manager-ügyfelek ütköző rekordjainak kezelése  
 A Configuration Manager a hardverazonosítók alapján megpróbálja azonosítani az ügyfeleket, előfordulhat, hogy ismétlődő, és figyelmeztet az ütköző rekordokra. Például ha újratelepít egy számítógépet, a Hardverazonosító változatlan marad, de a Configuration Manager által használt GUID megváltozhat.  

 A Configuration Manager tudja oldani az ütközést a számítógépfiókkal vagy egy PKI-tanúsítványt a Windows-hitelesítés használatával megbízható forrásból származik, az ütközés esetén automatikusan feloldani. Azonban ha a Configuration Manager nem tudja feloldani az ütközést, egy hierarchiabeállítást használ, vagy automatikusan egyesíti a rekordokat, amikor ismétlődő hardverazonosítókat (az alapértelmezett beállítás) észlel, vagy lehetővé teszi, hogy eldönthesse, mikor kell egyesíteni, letiltása, vagy új ügyfélrekordokat létrehozni. Ha úgy dönt, hogy az ismétlődő rekordok kézi kezelését, manuálisan kell feloldani a Configuration Manager konzolon az ütköző rekordokra.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>Az ütköző rekordok hierarchiabeállításának módosítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek** > **Hierarchiabeállítások**
2.  Az a **Ügyféljóváhagyás és ütköző rekordok** adja meg vagy **ütköző rekordok automatikus feloldása**, vagy **ütköző rekordok manuális feloldása**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Az ütköző rekordok manuális feloldása  

1.  Kattintson a Configuration Manager konzol **figyelés** > **rendszerállapot** > **ütköző rekordok**.  

3.  Jelöljön ki egy vagy több ütköző rekordot, és válassza a **ütköző rekord**.  

4.  Válasszon az alábbi lehetőségek közül:  

    -   **Egyesítési** egyesítése a létező ügyfélrekorddal az újonnan észlelt rekord.  

    -   **Új** – új rekord létrehozása az ütköző ügyfélrekordhoz.  

    -   **Blokkolás** – új rekord létrehozása az ütköző ügyfélrekordhoz, de blokkoltként megjelölve azt.  

## <a name="manage-duplicate-hardware-identifiers"></a>Ismétlődő hardverazonosítók kezelése
A Configuration Manager verziója 1610 kezdve hardverazonosítót, amely a Configuration Manager figyelmen kívül hagyja a PXE rendszerindítási és az ügyfélregisztráció során céljából listáját tartalmazzák. Nincsenek Ez segít cím két gyakori problémákat.

1. Számos új eszközöket, például a Surface Pro 3, nem tartalmaznak olyan beépített Ethernet port. Egy USB-Ethernet adapter szolgál az operációs rendszer központi telepítése céljából vezetékes kapcsolatot létesíteni. Azonban ezek a gyakran megosztott adapterek költség- és általános használhatóság miatt. Ez az adapter MAC-címét az eszköz azonosítására szolgál, mert további felügyeleti műveletek közötti minden egyes központi telepítés nélkül problematikus újból felhasználja az adapter lesz. Verziójáról 1610 kizárhatja Ez az adapter MAC-címét, hogy ebben a forgatókönyvben is újrahasznosíthatók.
2. Az SMBIOS azonosító egy egyedi hardverazonosító kell használni, amíg a néhány speciális hardvereszközök ismétlődő azonosítójú épülnek. Amíg nem a közös mint a fenti USB-Ethernet adapter eset, hardver-azonosítók listáját, valamint a probléma megoldására használható.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>A Configuration Manager figyelmen kívül hagyása hardverazonosítók hozzáadása  
1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**.
2. Az a **Home** lap a **helyek** csoportjában válassza **Hierarchiabeállítások**.
3. Az a **Ügyféljóváhagyás és ütköző rekordok** lapra, majd **Hozzáadás** a a **hardverazonosítók ismétlődő** szakasz új hardverazonosítók hozzáadása.

##  <a name="BKMK_PolicyRetrieval"></a> Házirend lekérésének kezdeményezése Configuration Manager-ügyfélhez  
 A Windows Configuration Manager-ügyfél letölti az ügyfélházirendet, ügyfélbeállításként konfigurált ütemezés szerint. Előfordulhat azonban, ha el szeretné indítani eseti lekérését az ügyfél, például hibaelhárítás vagy tesztelés alkalommal.  

Házirend lekérésének használatával is kezdeményezhető:


- [Ügyfélértesítés](#initiate-client-policy-retrieval-using-client-notification) 
- [A **műveletek** fülre az ügyfélen](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [A parancsfájl](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  További információ a Linux és UNIX rendszerű ügyfelek házirendjének lekéréséről: [Linux és UNIX rendszerű kiszolgálók ügyfélházirendje](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU).  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>Ügyfélházirend lekérésének ügyfélértesítéssel kezdeményezni  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Eszközgyűjtemények**.  

3.  Válassza ki a számítógépeket, amelyekre le szeretné tölteni a házirendet tartalmazó eszközgyűjteményt. Az a **Home** lap a **gyűjtemények** csoportjában válassza **Ügyfélértesítés** > **számítógép-házirend letöltése**.  

    > [!NOTE]  
    >  Ügyfélértesítéssel kezdeményezheti a házirend lekérését az **Eszközök** csomópont alatt megjelenő ideiglenes gyűjteménycsomópontban kijelölt egy vagy több eszközhöz is.  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Manuális kezdeményezését ügyfél műveletek lapján a Configuration Manager-ügyfél  

1.  Válassza a számítógép Vezérlőpultján a **Configuration Manager** elemet.  

2.  Az a **műveletek** lapon válassza a **számítógép-házirendek lekérési és kiértékelési ciklusa** kezdeményezni a számítógép-házirendet, és válassza a **Futtatás most**.  

4.  Válasszon **OK** a művelet megerősítéséhez.  

5.  Ismételje meg a 3. és 4. lépést minden egyéb szükséges művelettel, például a **Felhasználói házirendek lekérési és kiértékelési ciklusa** művelettel a felhasználói ügyfélbeállítások lekéréséhez.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Manuálisan ügyfél házirend lekérésének kezdeményezése parancsfájl  

1.  Nyisson meg egy szövegszerkesztőt, például a Jegyzettömböt.  

2.  Másolja a vágólapra a következő kódot, majd illessze be a fájlba:  

    ```  
    on error resume next  

    dim oCPAppletMgr 'Control Applet manager object.  
    dim oClientAction 'Individual client action.  
    dim oClientActions 'A collection of client actions.  

    'Get the Control Panel manager object.  
    set  oCPAppletMgr=CreateObject("CPApplet.CPAppletMgr")  
    if err.number <> 0 then  
        Wscript.echo "Couldn't create control panel application manager"  
        WScript.Quit  
    end if  

    'Get a collection of actions.  
    set oClientActions=oCPAppletMgr.GetClientActions  
    if err.number<>0 then  
        wscript.echo "Couldn't get the client actions"  
        set oCPAppletMgr=nothing  
        WScript.Quit  
    end if  

    'Display each client action name and perform it.  
    For Each oClientAction In oClientActions  

        if oClientAction.Name = "Request & Evaluate Machine Policy" then  
            wscript.echo "Performing action " + oClientAction.Name   
            oClientAction.PerformAction  
        end if  
    next  

    set oClientActions=nothing  
    set oCPAppletMgr=nothing  
    ```  

3.  Mentse a fájlt .vbs kiterjesztéssel.  

4.  Az ügyfélszámítógépen futtassa a fájlt az alábbi módszerek egyikével:  

    -   Navigáljon a fájlhoz a Windows Intézővel, és kattintson duplán a parancsfájlra.  

    -   Nyisson meg egy parancssort, és írja be: **cscript &lt;elérési_út\fájlnév.vbs >**.  

5.  Válasszon **OK** a a **Windows Script Host** párbeszédpanel megnyitásához.  

