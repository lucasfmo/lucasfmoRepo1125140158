---
title: "A felderítési módszerek |} Microsoft Docs"
ms.custom: na
ms.date: 2/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 81d7516b814d2db74d4d857871071c8911755754
ms.openlocfilehash: 6e53f501281e31f2b7df54b9740eac970f108257
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>About discovery methods for System Center Configuration Manager (Tudnivalók a System Center Configuration Manager felderítési módjairól)

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager felderítési módszer az Active Directoryból a hálózat vagy az eszközök és a felhasználók különböző eszközökön található. A felderítési módszerek hatékony használatát, tisztában kell lennie az elérhető konfigurációk és korlátozások érvényesek.  

##  <a name="bkmk_aboutForest"></a>Active Directory-Erdőfelderítés  
 **Konfigurálható:** Igen  

 **Alapértelmezés szerint engedélyezve:** Nem  

 **Fiókok** segítségével futtassa ezt a módszert:  

-   **Active Directory Erdőfelderítési fiók** (felhasználó által definiált)  

-   **Számítógépfiók** a helykiszolgáló  

Active Directory-Erdőfelderítés más Active Directory felderítési módszerekkel szemben nem deríti fel erőforrásokat, amelyek segítségével kezelheti. Ehelyett ez a módszer deríti fel hálózati helyeket, amelyek az Active Directoryban konfigurált és azokon a helyeken átalakíthatja a hierarchiához használható határokként.  

Ezt a módszert a futtatásakor keresi a helyi Active Directory-erdőben, az összes megbízható erdőre és minden olyan további erdőre vonatkozik, amelyet megadtak a **Active Directory-erdők** csomópont a Configuration Manager konzol.  

Használja az Active Directory-Erdőfelderítési funkciójával hajthat végre:  

-   Active Directory – helyek és -alhálózatok felderítésére, és hozza létre a Configuration Manager határok adott hálózati hely alapján.  

-   Active Directory-helyhez van rendelve, és minden felsőbb szintű hálózatot észlel átalakítása egy IP-címtartományhatárt supernets azonosításához.  

-   Ha engedélyezve van a közzétételt az adott erdőbe, és a megadott Active Directory-erdő fiókjának jogosult az adott erdőbe tegye közzé az Active Directory tartományi szolgáltatások (AD DS) erdő.  

A Configuration Manager konzol található következő csomópontokban felügyelheti az Active Directory-Erdőfelderítés **Hierarchiakonfiguráció** a a **felügyeleti** munkaterület:  

-   **A felderítési módszerek**: Itt engedélyezheti az Active Directory Erdőfelderítés fusson a hierarchia legfelső szintű helyén. Adjon meg egy egyszerű ütemezést felderítést, és konfigurálja úgy, hogy automatikusan határokat hozzon létre az IP-alhálózatokat és Active Directory-helyekből is. Az Active Directory Erdőfelderítés nem futtatható, a gyermek elsődleges helyen vagy másodlagos helyen.  

-   **Active Directory-erdők**: Itt konfigurálhatja ismerje meg, adja meg az egyes erdőkhöz az Active Directory-erdő fiókjának használandó fiókot, és konfigurálja az egyes erdőkbe való közzététel kívánt további Active Directory-erdők. Emellett a felderítési folyamat figyelésére, és adja hozzá az IP-alhálózatokat és Active Directory-helyek a Configuration Manager határokat és a határcsoportok tagjaiként.  

Közzététel az Active Directory-erdő minden egyes hely esetében konfigurálhatja a hierarchiába, csatlakozzon a Configuration Manager konzolt a hierarchia legfelső szintű helyén. A **közzétételi** az Active Directory-helyek lapon **tulajdonságok** párbeszédpanel csak az aktuális hely és gyermekhelyei megjeleníthető. Erdő számára engedélyezve van a közzététel, és adott erdő sémája ki van bővítve a Configuration Manager, a következő információt teszi közzé helyeken, amelyek az adott Active Directory-erdőbe történő közzététel engedélyezve van:  

-    **SMS-Site -&lt;Helykód >**

-   **SMS-MP -&lt;Helykód >-&lt;helyrendszer-kiszolgáló neve >**  

-   **SMS-SLP -&lt;Helykód >-&lt;helyrendszer-kiszolgáló neve >**  

-   **SMS -&lt;Helykód >-&lt;Active Directory-hely neve vagy az alhálózat >**  

> [!NOTE]  
>  A másodlagos helyek mindig a másodlagos hely kiszolgálójának számítógépfiókját használják az Active Directoryban való közzétételhez. Ha azt szeretné, hogy a másodlagos helyeket szeretne közzétenni az Active Directory, győződjön meg arról, hogy a másodlagos helykiszolgáló számítógépfiókja rendelkezik-e engedélyei az Active Directoryban való közzétételhez. A másodlagos helyek nem tehetnek közzé adatokat egy nem megbízható erdőben.  

> [!CAUTION]  
>  Törölje a jelet a beállítás a hely közzététele az Active Directory erdőbe, amikor az adott helyhez, beleértve az elérhető helyrendszer szerepköröket, az összes, előzőleg közzétett információt eltávolítják az Active Directoryból.  

Az Active Directory Erdőfelderítési műveleteit rögzíti a következő naplók kapcsolódnak:  

-   Minden olyan művelet, kivéve a közzététellel kapcsolatos műveleteken kívül tárolja, amely a **ADForestDisc.Log** fájlt a  **&lt;Telepítésiútvonal > \Logs** mappájában a helykiszolgálón.  

-   Active Directory-Erdőfelderítés közzétételi műveleteit rögzíti a **hman.log** és **sitecomp.log** -fájlok a  **&lt;Telepítésiútvonal > \Logs** mappájában a helykiszolgálón.  

Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutGroup"></a>Active Directory-Csoportfelderítés  
**Konfigurálható:** Igen  

**Alapértelmezés szerint engedélyezve:** Nem  

**Fiókok** segítségével futtassa ezt a módszert:  

-   **Active Directory Csoportfelderítési fiók** (felhasználó által definiált)  

-   **Számítógépfiók** a helykiszolgáló  

> [!TIP]  
>  Ebben a szakaszban szereplő információkon, lásd: [közös szolgáltatások Active Directory-csoportot, a rendszer és a Felhasználófelderítés](#bkmk_shared).  

Ezt a módszert az Active Directory tartományi szolgáltatásokban azonosításához:  

-   Helyi, globális és univerzális biztonsági csoportok.  

-   A csoportok tagságát.  

-   A csoport és a felhasználók, akkor is, ha egy másik észlelési módszer nem korábban észlelte ezen számítógépek és felhasználók korlátozott mennyiségű információt.  

Ez a felderítési módszer olyan azonosíthatók a csoportok és a csoportok csoporttagok csoportkapcsolatai. Alapértelmezés szerint csak a biztonsági csoportokat deríti fel. Ha azt szeretné, a terjesztési csoportok tagságát is található, ellenőrizze a jelölését **terjesztési csoportok tagságának felderítésére** a a **beállítás** lapra a **Active Directory-Csoportfelderítés tulajdonságai** párbeszédpanel megnyitásához.  

Active Directory-Csoportfelderítés nem támogatja a kiterjesztett Active Directory-attribútumok, amelyek az Active Directory-Rendszerfelderítést vagy az Active Directory-Felhasználófelderítés használatával azonosíthatók. Mivel ez a felderítési módszer nincs optimalizálva, számítógépes és felhasználói erőforrások felderítéséhez, fontolja meg, ez a felderítési módszer futó Active Directory-Rendszerfelderítést és az Active Directory-Felhasználófelderítés futtatása után. Ennek oka az, ezzel a módszerrel hoz létre a csoportokat, de csak korlátozott adatfelderítési Rekordot a számítógépek és felhasználók, csoportok tagjai teljes felderítési adatrekordot (DDR).  

Szabályozhatja, hogy ez a módszer keresse az információt következő felderítési hatóköröket konfigurálhatja:  

-   **Hely**: Használjon helyet, ha egy vagy több Active Directory-tárolókban keresni szeretne. Ez a hatókör támogatja a rekurzív keresést a megadott Active Directory-tároló, amely a tárolóban megadott tárolóhoz is keres. A folyamat folytatódik, amíg nincs több gyermektároló találhatók.  

-   **Csoportok**: Csoportok használata, ha azt szeretné, hogy egy vagy több meghatározott Active Directory-csoportok kereséséhez. Konfigurálható **Active Directory-tartomány** az alapértelmezett tartomány és erdő használatára, vagy meghatározott tartományvezérlőre a keresés korlátozódjon. Emellett kereshet egy vagy több csoportot is megadhat. Ha nem ad meg legalább egy csoportot, a megadott található összes csoportot **Active Directory-tartomány** történik a keresés helyét.  

> [!CAUTION]  
>  A felderítési hatókör konfigurálásakor csak a felderítendő csoportok kiválasztása Ennek oka az, az Active Directory-Csoportfelderítés megpróbál felderíteni a felderítési hatókörben lévő minden egyes csoport tagjaihoz. Nagyméretű csoportok felderítése erősen igénybe sávszélesség és az Active Directory-erőforrások.  

> [!NOTE]  
>  Mielőtt a kiterjesztett Active Directory-attribútumok alapuló gyűjteményeket hozhat létre (és pontos felderítésének biztosításához eredmények felhasználók és számítógépek), futtassa Active Directory-Rendszerfelderítést vagy az Active Directory-Felhasználófelderítés, attól függően, hogy szeretné felderíteni.  

Az Active Directory-Csoportfelderítés műveleteit fájl tárolja, amely a **adsgdis.log** a a  **&lt;Telepítésiútvonal\>\LOGS** mappájában a helykiszolgálón.  

Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutSystem"></a>Active Directory-Rendszerfelderítés  
**Konfigurálható:** Igen  

**Alapértelmezés szerint engedélyezve:** Nem  

**Fiókok** segítségével futtassa ezt a módszert:  

-   **Active Directory Rendszerfelderítési fiók** (felhasználó által definiált)  

-   **Számítógépfiók** a helykiszolgáló  

> [!TIP]  
>  Ebben a szakaszban szereplő információkon, lásd: [közös szolgáltatások Active Directory-csoportot, a rendszer és a Felhasználófelderítés](#bkmk_shared).  

Ez a felderítési módszer segítségével keresse meg az Active Directory tartományi szolgáltatások helyein azokat a számítógép-erőforrásokra, gyűjtemények és lekérdezések létrehozásához használható. Az ügyfélleküldéses telepítés használatával felfedezett eszközön is telepíthet a Configuration Manager-ügyfél.  

Alapértelmezés szerint ez a módszer a számítógép, valamint a következő alapvető információit deríti fel:  

-   Számítógép neve  

-   Operációs rendszer és verzió  

-   Active Directory-tároló neve  

-   IP-cím  

-   Active Directory-hellyel  

-   Az utolsó bejelentkezés időbélyegzője  

Egy számítógép DDR sikeresen létrehozásához az Active Directory-Rendszerfelderítés azonosítani számítógépfiókját, és sikeresen oldja meg a számítógép nevét egy IP-címre képesnek kell lennie.  

Az a **Active Directory-Rendszerfelderítés tulajdonságai** párbeszédpanel a **Active Directory-attribútumok** lapon megtekintheti az Active Directory-Rendszerfelderítés visszatért az alapértelmezett objektumattribútumok teljes listáját. A metódus (kiterjesztett) további attribútumok felderítését is konfigurálhatja.  

Az Active Directory-Rendszerfelderítés műveleteit fájl tárolja, amely a **adsysdis.log** a a  **&lt;Telepítésiútvonal\>\LOGS** mappájában a helykiszolgálón.  

Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutUser"></a>Active Directory-Felhasználófelderítés  
**Konfigurálható:** Igen  

**Alapértelmezés szerint engedélyezve:** Nem  

**Fiókok** segítségével futtassa ezt a módszert:  

-   **Active Directory Felhasználófelderítési fiók** (felhasználó által definiált)  

-   **Számítógépfiók** a helykiszolgáló  

> [!TIP]  
>  Ebben a szakaszban szereplő információkon, lásd: [közös szolgáltatások Active Directory-csoportot, a rendszer és a Felhasználófelderítés](#bkmk_shared).  

Ez a felderítési módszer használatával felhasználói fiókok és a kapcsolódó attribútumok azonosításához Active Directory tartományi szolgáltatásokban. Alapértelmezés szerint ez a módszer a felhasználói fiók, beleértve a következő alapvető információit deríti fel:  

-   Felhasználónév  

-   Egyedi felhasználónév (tartalmazza a tartománynevet)  

-   Domain  

-   Active Directory-tároló neve  

Az a **Active Directory-Felhasználófelderítés tulajdonságai** párbeszédpanel a **Active Directory-attribútumok** lapon megtekintheti az Active Directory-Felhasználófelderítés visszatért címtárobjektum-attribútumok teljes alapértelmezett listáját. A metódus (kiterjesztett) további attribútumok felderítését is konfigurálhatja.

Az Active Directory-Felhasználófelderítés műveleteit fájl tárolja, amely a **adusrdis.log** a a  **&lt;Telepítésiútvonal\>\LOGS** mappájában a helykiszolgálón.  

Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutHeartbeat"></a>A Szívveréses felderítés  
**Konfigurálható:** Igen  

**Alapértelmezés szerint engedélyezve:** Igen  

**Fiókok** segítségével futtassa ezt a módszert:  

-   **Számítógépfiók** a helykiszolgáló  

Szívveréses felderítés eltér a más Configuration Manager felderítési módszereket. Alapértelmezés szerint engedélyezve van, és a számítógép ügyfeleken fut (ahelyett, hogy a helyrendszer-kiszolgálón) adatfelderítési Rekordot létrehozásához. A mobileszköz-ügyfelek esetében a DDR a felügyeleti pont a mobileszközön lévő ügyfél által használt hozta létre. A Configuration Manager-ügyfelek adatbázisrekord karbantartása érdekében ne tiltsa le a Szívveréses felderítés. Mellett a adatbázisrekord karbantartása, ez a módszer kényszerítheti a számítógépet egy új erőforrásrekord felderítése, vagy feltöltheti egy számítógép az adatbázisból törölt adatbázis adatait.  

A Szívveréses felderítés vagy a hierarchiában lévő ügyfelek számára beállított ütemezés szerint fut vagy kézzel is elindítható, egy adott ügyfélen futtassa a **felderítés adatgyűjtési ciklusa** a a **művelet** lapon egy ügyfél a Configuration Manager programban. A Szívveréses felderítés alapértelmezett ütemezését érték 7 naponta. Ha módosítja a Szívveréses felderítési időközt, győződjön meg arról, hogy gyakrabban fusson, mint a helykarbantartási feladat **elavult eszközfelderítési adatok törlése**, amely törli a helyadatbázisból inaktív ügyfélrekordokat. Konfigurálhatja a **elavult eszközfelderítési adatok törlése** feladatot csak az elsődleges helyek esetében.  

Szívveréses felderítés futáskor létrehoz egy DDR, amely rendelkezik az ügyfél aktuális információk. Az ügyfél majd ez kis fájl másolása (körülbelül 1 KB méretű) a felügyeleti ponthoz, hogy az elsődleges hely képes feldolgozni azt. A fájl rendelkezik a következő információkat:  

-   Hálózati hely  

-   NetBIOS-név  

-   Az ügyfél ügynökprogramjának verzióját.  

-   Működési állapot részletei  

A Szívveréses felderítés az egyetlen felderítési módszer, amely adatokat szolgáltat az ügyfél telepítési állapotáról. Az hajtja végre, és állítson be egy egyenlő a rendszererőforrás ügyfélattribútumát frissítésével **Igen**.  

> [!NOTE]  
>  Akkor is, ha a Szívveréses felderítés le van tiltva, DDR továbbra is létre, és az aktív mobileszközügyfelekről elküldve. Ez biztosítja, hogy a **elavult eszközfelderítési adatok törlése** feladat nem érinti az aktív mobileszközöket. Ez azért történik, mert amikor a **elavult eszközfelderítési adatok törlése** eltávolítja egy mobileszköz adatbázisrekordját, is visszavonja az eszköz tanúsítványát, és meggátolja a mobileszköz csatlakozzon a felügyeleti pontokhoz.  

A Szívveréses felderítés műveleteit a következő helyekről jelentkezett:  

-   Számítógép ügyfelek esetében a Szívveréses felderítés műveleteit rögzíti az ügyfél a **InventoryAgent.log** fájlt a *%Windir%\CCM\Logs* mappa.  

-   Mobileszközügyfelek esetében a Szívveréses felderítés műveleteit rögzíti a **DMPRP.log** fájlt a *% Program Files%\CCM\Logs* a felügyeleti pont által a mobileszközön lévő ügyfél használt mappát.  

Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutNetwork"></a>A hálózatfelderítés  
**Konfigurálható:** Igen  

**Alapértelmezés szerint engedélyezve:** Nem  

**Fiókok** segítségével futtassa ezt a módszert:  

-   **Számítógépfiók** a helykiszolgáló  

Ezt a módszert feltérképezi a hálózatot és az eszközök felderítésére a hálózaton, amelyek az IP-cím. A hálózatfelderítés megkeresi a hálózaton az IP-kompatibilis erőforrások lekérdezésével a DHCP Microsoft-implementációját futtató kiszolgálók, útválasztók, az SNMP-eszközök és az Active Directory-tartományok gyorsítótárazza Address Resolution Protocol (ARP).  

A hálózatfelderítés használata előtt meg kell adnia a *szint* felderítés. Is konfigurál egy vagy több felderítési mechanizmusokat, amelyek lehetővé teszik a hálózatfelderítés lekérdezze a hálózati szegmenseket vagy az eszközöket. Beállítások, amelyek segítségével a hálózati vezérlő felderítési műveleteket is konfigurálhatja. Végül adja meg egy vagy több hálózati felderítés futtatásának ütemezését.  

Ebben az esetben a sikeres észleléshez a hálózatfelderítés kell határozza meg az IP-cím és az alhálózati maszkot az erőforrás. Az objektumok alhálózati maszkjának azonosításához. a következő módszerek használhatók:  

-   **Útválasztó ARP-gyorsítótár:** A hálózatfelderítés lekérdezi az alhálózatra vonatkozó adatok megállapításához az útválasztó ARP-gyorsítótárát. Jellemzően az útválasztó ARP-gyorsítótárában lévő adatok rendelkezik egy rövid időn belül élettartamát. Ezért amikor a hálózatfelderítés lekérdezi az ARP-gyorsítótár, az ARP-gyorsítótár előfordulhat, hogy már nincs a kért objektumra vonatkozó adatokat.  

-   **DHCP:** A hálózatfelderítés lekérdezi az egyes DHCP-kiszolgáló, amely az eszközöket, amelyek a DHCP-kiszolgáló bérleti jogot biztosított felderítésre. A hálózatfelderítés csak a DHCP Microsoft-implementációját futtató DHCP-kiszolgálók támogatja.  

-   **SNMP-eszköz:** A hálózatfelderítés közvetlenül le tudja kérdezni az SNMP-eszköz. A hálózatfelderítést, hogy kérdezni egy eszközt az eszköz telepített helyi SNMP-ügynöknek kell rendelkeznie. Úgy kell konfigurálnia a hálózatfelderítés az SNMP-ügynök által használt logikaicsoport-nevét használja.  

Ha a felderítés azonosít egy IP-címmel rendelkező objektumot, és megállapíthatja, hogy az objektum alhálózati maszkját, az adott objektum adatfelderítési Rekordot hoz létre. Sokféle eszköz csatlakozhat a hálózaton, mert a hálózatfelderítéssel erőforrásokat, amelyek nem támogatják a Configuration Manager ügyfélszoftver. Ilyen – észlelhető de nem kezelt eszközök szerepelnek például nyomtatókat és útválasztókat.  

A hálózatfelderítés az általa létrehozott felderítési rekordjának részeként különböző attribútumokat adhat vissza. Ezek a következők:  

-   NetBIOS-név  

-   IP-címek  

-   Erőforrás-tartomány  

-   Szerepkörök  

-   SNMP logikai csoportnév  

-   MAC-címek  

Hálózati felderítés műveleteit a **Netdisc.log** fájlt  *&lt;Telepítésiútvonal\>\Logs* a felderítést futtató helykiszolgálón.  

 Ez a felderítési módszer konfigurálásával kapcsolatos további információkért lásd: [felderítési módszerek konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

> [!NOTE]  
>  Bonyolult hálózatok és alacsony sávszélességű kapcsolatok hálózatfelderítés lassan fut, és jelentős hálózati forgalmat okozhat. Ajánlott eljárásként a hálózatfelderítést csak akkor, ha a többi felderítési módszer nem találja az erőforrásokat, fel kell derítenie. Például használja a hálózati felderítés, ha a munkacsoport-számítógépeket fel kell derítenie. Más felderítési módszerekkel nem deríti fel a munkacsoport-számítógépeket.  

###  <a name="BKMK_NetDiscLevels"></a>A hálózatfelderítés szintjei  
A hálózatfelderítés konfigurálásakor kell megadni háromféle felderítési szint egyikét:  

|Felderítéshez|Részletek|  
|------------------------|-------------|  
|Topológia|Ez a szint felderíti az útválasztókat és alhálózatok, de nem határozza meg az objektumok alhálózati maszkot.|  
|Topológia és ügyfél|Topológia mellett ez a szint felderíti a lehetséges ügyfeleket, például a számítógépeket, és erőforrásokat, például nyomtatókat és útválasztókat. Ez a felderítési szint megkísérli az általa megtalált objektumok alhálózati maszkjának azonosításához.|  
|Topológia, ügyfél és ügyfél operációs rendszer|Topológia és a lehetséges ügyfelek mellett ez a szint megpróbál felderíteni a számítógép operációs rendszerének nevét és verzióját. Ez a szint a Windows böngészőt használja, és a Windows hálózati szolgáltatásait.|  

 A magasabb szinteken a hálózatfelderítés növeli a tevékenység és a hálózati sávszélesség-használat. Vegye figyelembe a hálózati forgalomra számíthat, mielőtt engedélyezné a hálózati felderítés teljes körű.  

 Például a hálózatfelderítés első használata esetén előfordulhat, hogy a kiindulási pont a topológia szintet a hálózati infrastruktúrák azonosítására. Majd újrakonfigurálhatja az objektumok és az eszközök operációs rendszereit felderítését. Beállíthatja úgy is, hogy a hálózatfelderítés korlátozása megadott tartományra hálózati szegmensek beállításait. Ily módon felderítené az objektumok igényelnek, és elkerülheti a felesleges hálózati forgalom, és felderíthetők az objektumok a végponti útválasztókon túli vagy a hálózati helyek a hálózaton kívülről.  

###  <a name="BKMK_NetDiscOptions"></a>A hálózatfelderítés beállításai  
IP-címmel rendelkező eszközöket keres a hálózati felderítés engedélyezéséhez konfigurálnia kell legalább egy, a következő beállításokat, adja meg, hogyan eszközök lekérdezésére vonatkozóan.  

> [!NOTE]  
>  A hálózatfelderítés a felderítést futtató helykiszolgáló számítógépfiókjának kontextusában fut. Ha a számítógép fióknak nincs engedélye egy nem megbízható tartományban, a tartomány és a DHCP-konfigurációk sikertelen lehet az erőforrások felderítéséhez.  

**DHCP:**  

Adja meg az egyes DHCP-kiszolgáló használni kívánt hálózati felderítés lekérdezés. (A hálózatfelderítés csak a DHCP Microsoft-implementációját futtató DHCP-kiszolgálók támogatja.)  

-   A hálózatfelderítés a DHCP-kiszolgálón az adatbázis távoli eljáráshívásokat használatával adatainak beolvasása.  

-   Hálózati felderítés lekérdezhet 32 és 64 bites DHCP-kiszolgálók ott regisztrált eszközök listája.  

-   A hálózatfelderítés a DHCP-kiszolgáló sikeresen lekérdezni a felderítést futtató kiszolgáló számítógépfiókjának a DHCP-kiszolgálón a DHCP-felhasználók csoport tagjának kell lennie. Például a hozzáférési szintet létezik, ha az alábbiak egyike igaz:  

    -   A megadott DHCP-kiszolgáló a DHCP-kiszolgáló a felderítést futtató kiszolgáló.  

    -   A felderítés és a DHCP-kiszolgálót futtató számítógép ugyanabban a tartományban vannak.  

    -   Kétirányú megbízhatósági kapcsolattal a felderítést futtató számítógép és a DHCP-kiszolgáló között van.  

    -   A kiszolgáló a DHCP-felhasználók csoport tagja.  

-   Amikor a hálózatfelderítés a DHCP-kiszolgáló enumerálása, azt nem mindig veszi észre a statikus IP-címeket. A hálózatfelderítés nem talál, amelyek részei egy kizárt IP-címeit a DHCP-kiszolgáló IP-címeket. Azt is nem deríti fel a kézi hozzárendelés céljából lefoglalt IP-címeket.  

**Tartományok:**  

Adja meg a használni kívánt hálózati felderítés lekérdezés tartományonként.  

-   A felderítést futtató helykiszolgáló számítógépfiókjának a tartományvezérlők a meghatározott tartományok mindegyikében olvasni engedélyekkel kell rendelkeznie.  

-   A helyi tartományi számítógépek felderítésére, engedélyeznie kell a számítógép-tallózási szolgáltatás legalább egy számítógépen, amely ugyanazon az alhálózaton, mint a hálózatfelderítést futtató helykiszolgáló van.  

-   A hálózatfelderítéssel minden számítógép, amelyet látni lehet a helykiszolgálóról a hálózat böngészése során.  

-   A hálózatfelderítés lekérdezi az IP-címet, és ezután egy Internet Control Message Protocol echo kérésével megpingeli a talált. A **ping** parancs segítségével meghatározhatók azok a számítógépek, amelyek jelenleg aktív.  

**SNMP-eszközök:**  

Adja meg a használni kívánt hálózati felderítés lekérdezés minden SNMP-eszköz.  

-   A hálózatfelderítés beolvassa a ipNetToMediaTable értéket minden SNMP-eszközről, amely válaszol a lekérdezésre. Ezt az értéket adja vissza, számítógépek vagy más erőforrások, például a nyomtatók, útválasztók és egyéb IP-címmel rendelkező eszköz IP-címeket tartalmazó tömb.  

-   Kérdezni egy eszközt, az IP-cím vagy az eszköz NetBIOS-nevét kell megadnia.  

-   Konfigurálnia kell a hálózatfelderítést, hogy az eszköz logikaicsoport-nevét használja, vagy az eszköz elutasítja az SNMP-alapú kérést.  

###  <a name="BKMK_LimitNetDisc"></a>A hálózatfelderítés korlátozása  
Amikor a hálózatfelderítés lekérdezi az Ön hálózat peremén egy SNMP-eszközt, az alhálózatok és SNMP-eszközök közvetlen hálózaton kívüli adatait is meghatározhatja. Használja a következő korlátozzák a hálózatfelderítést úgy konfigurálja az SNMP-eszközöket, hogy a felderítési adatokat képes kommunikálni a együtt, és mely hálózati szegmenseket lekérdezése alapján.  

**Alhálózatok:**  

Konfigurálása az alhálózatok, hogy a hálózatfelderítés lekérdez az SNMP- és DHCP-beállításokat használja. E két beállítás csak az engedélyezett alhálózatokra keresni.  

Például egy DHCP-kérés eszközökről adhat vissza helyek a teljes hálózaton keresztül. Ha szeretné felderíteni csak egy bizonyos alhálózat eszközeit, adja meg, és engedélyezze a kívánt alhálózatot a a **alhálózatok** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanel megnyitásához. Ha ad meg, és engedélyezi az alhálózatok, beállíthatja a jövőbeli DHCP- és SNMP felderítési feladatok az alhálózatok.  

> [!NOTE]  
>  Az alhálózati beállítások nem korlátozzák az objektumokat, amelyek a **tartományok** felderítési beállítása szerint.  

**SNMP logikai csoportnevek:**  

Ahhoz, hogy a hálózati felderítés sikeresen lekérdezni egy SNMP-eszközt, beállításai közt megadják az eszköz logikaicsoport-nevét. A hálózatfelderítés nem konfigurálható az SNMP-eszköz logikaicsoport-nevét, ha az eszköz elutasítja a kérést.  

**Az ugrások maximális száma:**  

Ha beállítja az útválasztók ugrásainak maximális számát, kevesebb hálózati szegmensek és útválasztók, a hálózati felderítés lekérdezhet az SNMP segítségével.  

Az ugrások beállított száma korlátozza az további eszközöket és a hálózati felderítés lekérdezhet az hálózati szegmensek számát.  

Például a topológiára korlátozott felderítés az **0** (nulla) ugrásával felderíti az alhálózat, amelyiken a forráskiszolgálón található. Ez magában foglalja az adott alhálózaton található útválasztókat.  

Az alábbi ábrán látható, hogy mi a topológiára korlátozott hálózatfelderítés lekérdezés amikor Server 1-es fut az útválasztók beállított 0 ugrásával megadott keresése: D alhálózat és 1-es útválasztó.  

 ![Felderítés nulla útválasztó Ugrás az képe](media/Disc-0.gif)  

 Az alábbi ábrán látható, milyen a topológia és ügyfél hálózatfelderítés lekérdezés talál amikor Server 1-es fut az útválasztók beállított 0 ugrásával megadott: D alhálózat és 1-es útválasztó és az összes lehetséges ügyfél a alhálózati D.  

 ![Ugrás a felderítés az egyetlen útválasztó képe](media/Disc-1.gif)  

 Ahhoz, hogy segítenek meghatározni, hogy hogyan további útválasztó ugrások növelheti a felderített hálózati erőforrások mennyiségét, vegye figyelembe a következő hálózati:  

 ![Két útválasztó ugráskor, felderítés képe](media/Disc-2.gif)  

 A topológiára korlátozott hálózatfelderítés futtató kiszolgáló 1 egy ugrásával a következőket deríti fel:  

-   1-es útválasztó és 10.1.10.0 című alhálózat (ezek találhatók nulla ugrásnál)  

-   10.1.20.0 és 10.1.30.0 alhálózat, A, és (található az első ugrásnál) útválasztó 2  

> [!WARNING]  
>  Az útválasztó ugrások száma minden egyes növelése jelentősen növelheti a felderíthető erőforrások számát, és növeli a hálózatfelderítés által használt hálózati sávszélességet.  

##  <a name="bkmk_aboutServer"></a>Kiszolgálófelderítés  
**Konfigurálható:** Nem  

A felhasználó által konfigurálható felderítési módszer mellett a Configuration Manager nevű folyamatot használ **Kiszolgálófelderítés** (SMS_WINNT_SERVER_DISCOVERY_AGENT). Ez a felderítési módszer készít erőforrásrekordokat beléptetésihely-rendszerek, például felügyeleti pontként konfigurált számítógép számítógépekhez.  

##  <a name="bkmk_shared"></a>Active Directory-Csoportfelderítés, a rendszer-felderítési és a Felhasználófelderítés az általános szolgáltatások  
Ez a szakasz információ olyan szolgáltatásokról, amelyek közösek az alábbi felderítési módszerekről nyújt:  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

-   Active Directory-felhasználófelderítés  

> [!NOTE]  
>  Az itt olvasható információk az Active Directory-Erdőfelderítés nem vonatkozik.  

A három felderítési módszer konfiguráció és működés hasonlóak. Használhatná azokat a számítógépeket, a felhasználók és az Active Directory tartományi szolgáltatásokban tárolt erőforrások csoporttagságaira vonatkozó információk felderítésére. A felderítési folyamat egy felderítési ügynököt futtat az egyes helyeken, ahol a felderítési történő futtatásra van konfigurálva a helykiszolgálón kezeli. Egy vagy több Active Directory-helyeken kereshet a helyi és távoli erdők helypéldányaiként felderítési módszer bármelyikét konfigurálhatja.  

Felderítés erőforrások nem megbízható erdőben keres, ha az ügynöknek fel kell tudnia oldani a sikeres a következő:  

-   Számítógépes erőforrás felderítéséhez az Active Directory-Rendszerfelderítés használatával, az ügynök kell tudni oldania az erőforrás teljes Tartománynevét. Az FQDN nem oldható fel, ha azt fogják megpróbálni az erőforrás oldani a NetBIOS-név.  

-   Egy felhasználó vagy csoport felderítéséhez az Active Directory-Felhasználófelderítés vagy Active Directory-Csoportfelderítés használatával, az ügynök kell tudnia oldani a tartományvezérlő neve az Active Directory-hely számára megadott teljes Tartományneve.  

Minden egyes megadott helyre külön keresési beállításokat, például az a hely Active Directory-gyermektárolók rekurzív keresését is beállíthat. Beállíthatja úgy is, hogy a hely kereséséhez egyedi fiókot. Ez a felderítési módszerek konfigurálása egy adott helyen több Active Directory-helyeken kereshet több erdők között, nem kell állítani egy olyan fiókot, amely jogosult az helyekre rugalmasságot biztosít.  

A három felderítési módszer bármelyikét futtatja, egy adott helyen, ha adott helyen a Configuration Manager helykiszolgáló az Active Directory-erőforrások felderítéséhez a megadott Active Directory-erdő legközelebbi tartományvezérlőjével lép kapcsolatba. A tartomány és az erdő bármelyik támogatott Active Directory-üzemmódot lehet. Az egyes helypéldányokhoz hozzárendelt fióknak rendelkeznie kell **olvasási** engedéllyel a megadott Active Directory-helyekhez.

Felderítési objektumok számára a megadott helyeken keresi, és megkísérli az objektumokra vonatkozó információk gyűjtése. A DDR jön létre, amikor elegendő információt egy erőforrásról azonosítható legyen. A szükséges információkat a használt felderítési módszer függ.  

Ha adja meg ugyanazt a felderítési módszert futtatását, hogy másik Configuration Manager-helyek igénybe vehesse a helyi Active Directory-kiszolgálók lekérdezését, mindegyik hely konfigurálható felderítési beállítások egyedi készletét. Felderítési adatokat a hierarchiában minden hely van megosztva, mivel ezek a konfigurációk derítsen fel minden erőforrást egy alkalommal között átfedés elkerülése. 

A kisebb környezetekhez érdemes lehet futtató egyes felderítési módszereket csak egy adott helyen a hierarchia csökkenteni az adminisztrációs terhelést és lehetséges, hogy több felderítési művelet is felderíti ugyanazokat az erőforrásokat. Amikor a felderítés futtatása csökkenthető a teljes hálózati sávszélesség adott felderítési helyek számának minimálisra csökkentése használ. A létrehozott és a Helykiszolgálók által feldolgozandó adatfelderítési rekordok teljes számát is csökkentheti.  

A felderítési módszerek beállításainak többsége magától értetődő. A következő részekben talál további információt a felderítési beállításokról, amelyek beállítása további ismereteket igényel.  

Az alábbi beállítások érhetők el, több Active Directory felderítési módszerei való használathoz:  

-   [Változásfelderítés](#bkmk_delta)  

-   [Elavult számítógéprekordok szűrése a tartományi bejelentkezés alapján](#bkmk_stalelogon)  

-   [Az elavult rekordok szűrése a számítógép jelszava alapján](#bkmk_stalepassword)  

-   [Testreszabott Active Directory-attribútumok keresése](#bkmk_customAD)  

###  <a name="bkmk_delta"></a>Változásfelderítés  
Az elérhető:  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

-   Active Directory-felhasználófelderítés  

A Változásfelderítés nem egy független felderítési módszer, hanem egy lehetséges megoldás, a megfelelő felderítési módszereket. A Változásfelderítés a megfelelő felderítési módszer utolsó teljes felderítési ciklus óta elvégzett módosítások az adott Active Directory-attribútumok keres. Az attribútum a változásokat elküldi a Configuration Manager adatbázishoz az erőforrás a felderítési rekordjának frissítése érdekében.  

A Változásfelderítés alapértelmezés szerint 5 perc ciklusban fut. Ez egy sokkal gyakoribb, mint a szokásos ütemezését a teljes felderítési ciklus.  Ez a gyakori ciklus lehetőség, mert a Változásfelderítés kevesebb helyrendszer-kiszolgálót használ, és a hálózati erőforrásokhoz, mint a teljes felderítési ciklus nem. Ha Változásfelderítést használ, csökkentheti az adott felderítési módszer teljes felderítési ciklus gyakoriságát.  

Változásfelderítés által észlelt leggyakoribb változások a következők:  

-   Új számítógépek és felhasználók felvétele az Active Directory  

-   Alapvető számítógép- és felhasználói adatok módosítása  

-   Új számítógépek és felhasználók felvétele egy csoportba  

-   Számítógépek és felhasználók eltávolítása egy csoportból  

-   Rendszercsoport objektumok módosításai  

Bár a Változásfelderítés észleli az új erőforrásokat és a csoportok tagságának változásait, azt nem tudja észlelni az erőforrás törölve lett az Active Directoryból. A Változásfelderítés által létrehozott adatfelderítési rekordokat hasonló módon a teljes felderítési ciklus által létrehozott adatfelderítési rekordokat dolgoznak.  

A Változásfelderítést állít be a **lekérdezés ütemezése** az egyes felderítési módszerek lapján.  

###  <a name="bkmk_stalelogon"></a>Elavult számítógéprekordok szűrése a tartományi bejelentkezés alapján  
Az elérhető:  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

Számítógépek kizárása a számítógép utolsó tartományi bejelentkezése alapján elavult számítógép rekordot a felderítést úgy állíthatja be. Ha ez a beállítás engedélyezve van, az Active Directory-Rendszerfelderítés kiértékeli minden olyan számítógépen, azonosítja. Active Directory-Csoportfelderítés kiértékeli minden számítógép, amely tagja egy felderített csoportnak.  

Ez a beállítás használata:  

-   Számítógépek frissítéséhez be kell állítani a **lastLogonTimeStamp** attribútum az Active Directory tartományi szolgáltatásokban.  

-   Az Active Directory-tartomány funkcionális szintje Windows Server 2003 vagy újabb verzióra kell beállítani.  

Az ehhez a beállításhoz használni kívánt utolsó bejelentkezés utáni idő konfigurálja, vegye figyelembe a tartományvezérlők közötti replikáció időtartamát.  

Szűrés konfigurálja a **beállítás** lapján a **Active Directory-Rendszerfelderítés tulajdonságai** és **Active Directory-Csoportfelderítés tulajdonságai** párbeszédpanel. Lehetőséget **csak számítógépek felderítése, amelyek jelentkeztek be egy tartományba egy adott időszakban**.  

> [!WARNING]  
>  Ez a szűrő konfigurálásakor és **elavult rekordok szűrése a számítógép jelszava alapján**, vagy szűrő feltételeket teljesítő számítógépek ki lettek zárva a felderítésből.  

###  <a name="bkmk_stalepassword"></a>Az elavult rekordok szűrése a számítógép jelszava alapján  
Az elérhető:  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

Számítógépek kizárása a számítógép által az utolsó fiókjelszó-módosítás alapján elavult számítógép rekordot a felderítést úgy állíthatja be. Ha ez a beállítás engedélyezve van, az Active Directory-Rendszerfelderítés kiértékeli minden olyan számítógépen, azonosítja. Active Directory-Csoportfelderítés kiértékeli minden számítógép, amely tagja egy felderített csoportnak.  

Ez a beállítás használata:  

-   Számítógépek frissítéséhez be kell állítani a **pwdLastSet** attribútum az Active Directory tartományi szolgáltatásokban.  

Konfigurálja ezt a beállítást, vegye figyelembe a ezt az attribútumot a tartományvezérlők közötti replikációs időköztől mellett frissítési időközt.  

Szűrés konfigurálja a **beállítás** lapján a **Active Directory-Rendszerfelderítés tulajdonságai** és **Active Directory-Csoportfelderítés tulajdonságai** párbeszédpanel. Lehetőséget **csak olyan számítógépek, amelyek egy adott időszakban frissítették számítógépfiókjuk jelszavát felderítése**.  

> [!WARNING]  
>  Ez a szűrő konfigurálásakor és **elavult rekordok szűrése a tartományi bejelentkezés alapján**, vagy szűrő feltételeket teljesítő számítógépek ki lettek zárva a felderítésből.  

###  <a name="bkmk_customAD"></a>Testreszabott Active Directory-attribútumok keresése  
 Az elérhető:  

-   Active Directory-rendszerfelderítés  

-   Active Directory-felhasználófelderítés  

Mindegyik felderítési módszer támogatja a felderíthető Active Directory-attribútumok egyéni listájának.  

Tekintheti meg és konfigurálhatja az egyéni attribútumok listáját a a **Active Directory-attribútumok** lapra a **Active Directory-Rendszerfelderítés tulajdonságai** és **Active Directory-Felhasználófelderítés tulajdonságai** párbeszédpanel.  

