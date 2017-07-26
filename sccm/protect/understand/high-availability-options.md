---
title: "Magas rendelkezésre állású |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager telepítését a beállításokat, amelyek karbantartása egy magas szintű rendelkezésre állásának megőrzésében."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a38421d-24c1-4fef-bf6c-42fce53109ac
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: d3e9afb90cdc85bc7299626b642c52be659e3bdf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="high-availability-options-for-system-center-configuration-manager"></a>Magas rendelkezésre állású lehetőség a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*



System Center Configuration Manager-beállítások, amelyek magas szintű rendelkezésre állásának megőrzésében karbantartása használatával telepítheti.   

Magas rendelkezésre állást támogató lehetőségeket:   

-   Hely helyrendszer-kiszolgáló számára fontos szolgáltatásokat nyújthatnak az ügyfeleknek több példányát támogatják.  

-   A központi adminisztrációs helyek és elsődleges helyek támogatják a Helyadatbázis biztonsági mentését. A Helyadatbázis tartalmazza a helyek és ügyfelek a konfigurációkat, és a központi adminisztrációs helyet tartalmazó hierarchiában lévő helyek között megosztott.  

-   Beépített helyreállítási lehetőségek csökkenthetik a kiszolgálók állásidejét, és olyan fejlett beállításokat kínálnak, amelyek egyszerűbbé válik a helyreállítás egy központi adminisztrációs hellyel rendelkező hierarchiát.  

-   Az ügyfelek automatikusan javítani tudja a legjellemzőbb problémákat rendszergazdai beavatkozás nélkül.  

-   Helyek riasztásokat generálnak azokról az ügyfelekről, amelyek nem küldenek friss adatokat, így a potenciális problémákról rendszergazdák értesülhetnek.  

-   A Configuration Manager kínál számos olyan beépített jelentéseket, amelyek segítségével azonosíthatja a problémákat és a trendeket, mielőtt azok veszélyeztetnék a kiszolgálók vagy ügyfél működését.  

 A Configuration Manager nem tartalmazza a valós idejű szolgáltatást, és továbbítása a rendszerben némi adatok késedelemmel kell várt. Ezért kicsi az egy átmeneti szolgáltatáskimaradás kritikus problémát okozzon szolgáltatást érintő, azt. Konfigurálta a helyek és hierarchiák magas rendelkezésre állással kapcsolatos szempontokat, amikor állásidőt minimalizálható, fenntartható a rendszer, és a szolgáltatás magas szintű megadott.  

 Például Configuration Manager-ügyfelek jellemzően önállóan, ismert működési ütemezés és konfiguráció üzemelnek, és rendszeres időközönként adatokat küldenek a helynek feldolgozás céljából történő használatával.  

-   Ha az ügyfelek nem lehet kapcsolatba lépni a hellyel, azok gyorsítótár adatok elküldését, amíg nem tud kapcsolatba lépni a hellyel.  

-   Ügyfelek, amelyek a hely nem tud kapcsolatba lépni folytatják működésüket az utolsó ismert ütemezés és a gyorsítótárazott információk – például a korábban letöltött alkalmazás futtatandó vagy telepíteni, amíg nem tud kapcsolatba lépni a hellyel, és kapják az új házirendeket.  

-   A hely figyeli a hozzá tartozó helyrendszerek és ügyfelek rendszeres állapotfrissítéseit, és riasztást generál, ha ezek regisztrációja elmarad.  

-   Beépített jelentések betekintést nyújtanak a folyamatban lévő műveletek, valamint a múltbeli működési és a trendeket. A Configuration Manager támogatja, amelyek közel valós idejű információkat nyújtanak a folyamatos működéshez állapotalapú üzeneteket is.  

  Használja a témakörben szereplő információkat az alábbi cikkekben található információkkal:
-   [Ajánlott hardver](../../core/plan-design/configs/recommended-hardware.md)
-   [Hely rendszer serveres támogatott operációs rendszerek](../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  

-   [Hely és hely rendszer Előfeltételek](../../core/plan-design/configs/site-and-site-system-prerequisites.md)


##  <a name="bkmk_snh"></a>Magas rendelkezésre állás a helyekhez és hierarchiákhoz  
 **SQL Server-fürtöt használja a Helyadatbázis futtatására:**  

 SQL Server-fürtöt használ egy központi adminisztrációs hely vagy elsődleges hely adatbázisához, használja az SQL Server beépített feladatátvételi támogatást.  

 A másodlagos helyek nem használhatnak SQL Server-fürtöt, és nem támogatják a biztonsági mentési vagy a hely adatbázisának visszaállítása. A másodlagos hely helyreállítása a szülő elsődleges helyről másodlagos hely újratelepítésével történő.  

 **Egy SQL Server AlwaysOn rendelkezésre állási csoport használata a Helyadatbázis futtatására:**  

 1602-es verziójától kezdve használhatja az SQL Server AlwaysOn rendelkezésre állási csoportok elsődleges helyeken és a magas rendelkezésre állású és vész-helyreállítási megoldásként a központi adminisztrációs helyen a Helyadatbázis futtatására. További információkért lásd: [SQL Server AlwaysOn magas rendelkezésre állású Helyadatbázis a System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

 **Egy helyhierarchiát egy központi adminisztrációs helyet, és egy vagy több gyermek elsődleges helyek telepítéséhez:**  

 Ez a konfiguráció képes hibatűrést biztosítani, ha a helyek a hálózat egymást átfedő szegmenseit felügyelik. Ez a konfiguráció emellett egy másik helyen elérhető megosztott adatbázis információk segítségével építse újra a helyreállított helyen a Helyadatbázis egy másik helyreállítási módszert biztosít. Ez a beállítás segítségével cserélje le a hibás helynek adatbázis hibás vagy nem áll rendelkezésre biztonsági másolatot.  

 **Készítsen rendszeres biztonsági mentést a központi adminisztrációs helyek és az elsődleges helyeken:**  

 Létrehozásakor, és tesztelje a rendszeres hely biztonsági mentése, gondoskodjon arról, hogy rendelkezik-e a helyreállításához szükséges adatok egy helyen, és a lehető legrövidebb idő alatt helyreállíthassa a helyet a kezelését.  

 **Helyrendszerszerepkörök több példányának telepítése:**  

 Ha például a felügyeleti és terjesztési pont kritikus helyrendszerszerepkörökből több példányt telepít, akkor redundáns kapcsolódási pontokat biztosíthat kapcsolódási ügyfelek abban az esetben, ha egy adott helyrendszer-kiszolgáló offline állapotban.  

 **Egy hely SMS-szolgáltató több példányának telepítése:** Az SMS-szolgáltató egy vagy több Configuration Manager konzol adminisztratív kapcsolódási pontot biztosít. Több SMS-szolgáltató telepítésével gondoskodhat a hely és a hierarchia felügyeletére szolgáló kapcsolódási pontok redundanciájáról.  

##  <a name="bkmk_ssr"></a>Magas rendelkezésre állás a helyrendszer-szerepkörök  
 Az egyes helyeken kell telepíteni a helyrendszerszerepköröket az ügyfelek által az adott helyen használandó szolgáltatások biztosításához. A helyadatbázist a hely és az összes ügyfél konfigurációs információkat tartalmazza. Egy vagy több, a rendelkezésre álló lehetőségek segítségével biztosítja a Helyadatbázis magas rendelkezésre állás és a hely és a Helyadatbázis szükség esetén a helyreállítás.  

 **A fontos helyrendszerszerepkörök redundanciája:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Terjesztési pont  

-   Felügyeleti pont  

-   Szoftverfrissítési pont  

-   állapotáttelepítési pont  

 A jelentéskészítési szolgáltatások pont szerepkör redundanciájának biztosítása a helyek és ügyfelek több példányát is telepítheti.

 PowerShell segítségével telepítse a szoftverfrissítési pont hely rendszer szerepkört a Windows hálózati terheléselosztási (NLB) fürt gondoskodhat a feladatátvétel támogatásáról  


 **Hely beépített biztonsági mentése:**  

 A Configuration Manager tartalmaz egy beépített biztonsági mentési feladattal segíti a helyek és a kritikus információk rendszeres biztonsági mentését. Ezen kívül a Configuration Manager telepítő varázsló támogatja a visszaállítás Webhelyműveletek segítséget nyújtanak a hely visszaállítása műveletekhez.  

 **Active Directory tartományi szolgáltatások és a DNS-közzététel:**  

 Minden hely beállítható úgy, hogy közzétegye a helyrendszer-kiszolgálókkal és -szolgáltatásokkal kapcsolatos adatokat az Active Directory Domain Servicesben és a DNS szolgáltatásban. Ez lehetővé teszi az ügyfelek a hálózaton a legkönnyebben elérhető kiszolgáló azonosítására szolgál, illetve annak felismerését, ha új helyrendszer-kiszolgáló számára fontos szolgáltatásokat, például felügyeleti pontok érhetők el.  

 **SMS-szolgáltató és a Configuration Manager konzol:**  

 Több SMS-szolgáltató, mindegyik példány külön számítógépen, a Configuration Manager konzol több kapcsolódási pont biztosítható a telepítése a Configuration Manager támogatja. Ez biztosítja, hogy egy SMS-szolgáltató számítógépe elérhetetlenné válik, ha megmaradjanak is megtekinthetők és Újrakonfigurálhatók a Configuration Manager-helyek és ügyfelek lehetőséget.  

 A Configuration Manager konzol csatlakozik egy helyhez, amikor csatlakozik egy adott helyen az SMS-szolgáltató példánya. Az SMS-szolgáltató példánya nem determinisztikus módon választ. Ha a kiválasztott SMS-szolgáltató nem érhető el, akkor a következő beállításokat:  

-   Csatlakozzon újra a konzolt a helyhez. Minden új kapcsolódási kérelmet véletlenszerűen hozzá van rendelve az SMS-szolgáltató példányát, és előfordulhat, hogy az új kapcsolat hozzá lesz rendelve egy elérhető példányhoz.  

-   Csatlakoztassa a konzolt egy másik Configuration Manager-hely, és erről a kapcsolatról felügyelje a konfigurációt. Az azzal, hogy a konfigurációs módosításokban néhány perc múlva legfeljebb egy kis idő. Miután a hely SMS-szolgáltató online, a Configuration Manager konzol közvetlenül a kezelni kívánt helyhez csatlakoztathatja újra.  

 A Configuration Manager konzolt telepítheti a rendszergazda felhasználók számára több számítógépen. Minden egyes SMS-szolgáltató-példányokhoz több Configuration Manager-konzol.  

 **Felügyeleti pont:**  

 Minden elsődleges helyen több felügyeleti pontot telepít, és engedélyezze a helyek számára a helyadatok közzététele az Active Directory infrastruktúrával, és a DNS Szolgáltatásban.  

 Több felügyeleti pontot sok ügyfél bármely egyetlen felügyeleti pont súgó terheléselosztásához. Ezenkívül telepítheti egy vagy több adatbázis-replikák beállítása felügyeleti pontokhoz, csökkentheti a CPU-intenzív műveleteinek terhelését a felügyeleti pont, és növelheti a kritikus fontosságú helyrendszerszerepkör rendelkezésre állását.  

 Mivel csak egy felügyeleti pont egy másodlagos helyre, amely a másodlagos helykiszolgálón kell lennie, a másodlagos helyeken lévő felügyeleti pontok nem tekinthetők magas rendelkezésre állású konfigurációval rendelkezik.  

> [!NOTE]  
>  A helyszíni mobileszköz-kezelés által felügyelt eszközök egy elsődleges helyen csak egy felügyeleti ponthoz kapcsolódni. A felügyeleti pont van rendelve a Configuration Manager által a mobil eszköz a beléptetés során, és ezután nem változik. Ha több felügyeleti pontot telepít és engedélyez mobileszközök, a a mobileszközügyfelekhez rendelt felügyeleti pont nem determinisztikus.  
>   
>  A mobileszközön lévő ügyfél használó felügyeleti pont nem érhető el, ha kell, hogy a felügyeleti ponttal a probléma megoldásához vagy törölni szeretné a mobileszközön és megújítása a mobileszközt, így rendelhető hozzá egy operatív felügyeleti ponthoz, a mobileszközökhöz engedélyezett.  

 **Terjesztési pont:**  

 Több terjesztési pontot telepítsen, és a tartalom több terjesztési pontot. Beállíthatja annak érdekében, hogy minden egyes alhálózaton található ügyfelek számára elérhető központi telepítés két vagy több terjesztési pontot a tartalom helyéhez átfedő határcsoportokat. Végül fontolja meg, hogy egy vagy több terjesztési pontot a tartalom tartalék tartalomhelyként.  

 További információ a tartalék tartalomhelyekről: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 **Az Alkalmazáskatalógus webszolgáltatási pontja és az Alkalmazáskatalógus weboldal-elérési pontja:**  

 Minden egyes helyrendszerszerepkörhöz, valamint a legjobb teljesítmény érdekében több példányt telepítsen, legalább egy ugyanazon a számítógépen a hely system telepítéséhez.  

 Minden egyes Alkalmazáskatalógus-helyrendszerszerepkör ugyanazokat az információkat, függetlenül a helykiszolgáló szerepkörön a hierarchia helyét helyrendszerszerepkörnek a többi futó példányát tartalmazza. Ezért amikor egy ügyfél kérelmet küld az alkalmazáskatalógushoz, és konfigurálta az alapértelmezett Alkalmazáskatalógus weboldal-elérési pontja ügyféleszköz-beállítás automatikusan észleli, az ügyfél egy elérhető példányhoz irányítható. Helyi Alkalmazáskatalógus helyrendszer-kiszolgálók, az ügyfél aktuális hálózati helye alapján elsőbbséget.  

 További információ az ügyfél és az automatikus észlelés működésével: a [Számítógépügynök](../../core/clients/deploy/about-client-settings.md#computer-agent) szakasz a [információ a System Center Configuration Manager ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md) témakör.  

##  <a name="bkmk_client"></a>Magas rendelkezésre állás az ügyfelek  
 **Az ügyfél műveleteivel autonóm rendszer:**  

 A Configuration Manager ügyfél önállóan az alábbiakat tartalmazza:  

-   Az ügyfelek nem igényelnek folyamatos kapcsolatot bármely adott helyrendszer-kiszolgálókkal. Ismert konfigurációk előre konfigurált műveleteket ütemezés szerint használják.  

-   Ügyfelek bármely olyan helyrendszerszerepkör, amely ügyfeleknek nyújt szolgáltatásokat rendelkezésre álló példányát használhatják, és addig próbálnak ismert kiszolgálóhoz csatlakozni, amíg elérhető kiszolgálót nem található.  

-   Ügyfelek a helyrendszer-kiszolgálókat tartalmazó készlet, központi szoftvertelepítést és hasonló ütemezett műveleteket végezni közvetlen kapcsolattól függetlenül is futtatni.  

-   A tartalék állapotkezelő pont használatára konfigurált ügyfelek is küldhetnek adatokat a tartalék állapotkezelő pont, amikor nem tudnak kommunikálni egy felügyeleti ponttal.  

 **Az ügyfelek képesek önmagukat javítani:**  

 Az ügyfelek automatikusan elhárítani a legjellemzőbb problémákat közvetlen rendszergazdai beavatkozás nélkül:  

-   Ügyfelek rendszeres időközönként kiértékelik saját állapotukat, és hajtsa végre a műveletet a javításához a lépéseket és javítási forrásfájlokat egy helyi gyorsítótár segítségével gyakran előforduló problémák elhárításához.  

-   Ha egy ügyfél állapota adatokat küld a hely nem sikerül, a hely riasztást generálhat. Rendszergazdák, akik megkapják ezeket a riasztásokat az ügyfél normál működésének visszaállításához azonnali lépéseket tehetnek.  

 **Az ügyfelek gyorsítótárba helyezik a adatokat jövőbeni használatra:**  

 Amikor egy ügyfél egy felügyeleti ponttal kommunikál, akkor az ügyfél beszerzése, és gyorsítótárazza a következő információkat:  

-   Ügyfélbeállítások.  

-   Az ügyfelekre vonatkozó ütemezéseket.  

-   Információ a szoftverek központi telepítéséhez és egy letölthető a szoftver az ügyfél telepítése, amikor a függőség a művelet van ütemezve.  

 Ha egy ügyfél nem tud csatlakozni a felügyeleti pont az ügyfelek helyben gyorsítótárazza az állapota, az állapot és az ügyfél információkat, a helynek jelentendő és továbbítják azokat képes-e csatlakozni a felügyeleti pontot.  

 **Ügyfelek is elküldhetik állapotukat a tartalék állapotkezelő pont számára:**  

 Ha egy ügyfél egy tartalék állapotkezelő pont használatára állítja be, meg kell adnia egy kiegészítő kapcsolattartót az ügyfél számára a működésével kapcsolatos fontos részleteket nyújt. A tartalék állapotkezelő pont használatára konfigurált ügyfelek továbbra is küldhet kapcsolatos állapot helyrendszerszerepkörnek akkor is, ha az ügyfél nem tud kommunikálni egy felügyeleti ponttal.  

 **Központi felügyeleti ügyféladatok és ügyfél-azonosító:**  

 A Helyadatbázis ahelyett, hogy az egyes ügyfelek, az ügyfelek identitásával fontos információkat, és rendeli hozzá egy adott számítógépet vagy felhasználót. Ez azt jelenti, hogy:  

-   Az ügyfél forrásfájljait a számítógépre is távolíthatók el és nem befolyásolja a előzményrekordjaira, a számítógép, amelyen az ügyfél telepítve van-e telepíteni.  

-   Ügyfélszámítógép hibája nincs hatással az adatbázisban tárolt adatok sértetlenségét. Ezek az információk érhetők el, jelentések maradjanak.  

##  <a name="bkmk_nonHAoptions"></a>Beállítások a helyek és helyrendszer-szerepkörök, amelyek nem magas rendelkezésre állású  
 Helyrendszer támogatja több példánya a helyen, vagy a hierarchiában. Ezek az információk segítségével felkészülhet arra, hogy ezek a helyrendszerek offline állapotra vált.  

 **A helykiszolgáló (hely):**  

 A Configuration Manager nem támogatja a helykiszolgáló telepítése a Windows Server-fürtön vagy NLB-fürtben lévő minden egyes helyhez.  

 A következő információk segítségével felkészülhet arra, ha egy helykiszolgáló meghibásodik, vagy nem működőképes:  

-   A beépített biztonsági mentési feladat segítségével rendszeresen készítsen biztonsági másolatot a helyhez. Egy tesztkörnyezetben, rendszeresen gyakorlat helyek visszaállítása egy biztonsági másolatból.  

-   Több Configuration Manager elsődleges hely a hierarchiában redundancia megteremtése érdekében egy központi adminisztrációs hely telepítéséhez. Ha hellyel kapcsolatos hibát észlel, fontolja meg a Windows csoport vagy bejelentkezési parancsfájl használatával az ügyfelek működőképes helyhez hozzárendelni.  

-   A központi adminisztrációs hellyel rendelkező hierarchiára Helyadatbázis helyreállítása egy másik helyet a hierarchiában a beállítás használatával helyreállíthatja a központi adminisztrációs hely vagy elsődleges gyermekhelyet.  

-   A másodlagos helyek nem állítható vissza, és újra kell telepíteni.  

 **Eszközintelligencia szinkronizációs pontja (hierarchia):**  

 A helyrendszerszerepkör nem számít kritikusnak kritikus és a Configuration Manager opcionális funkcionalitást biztosít. Ha a helyrendszer offline állapotba kerül, használja az alábbi lehetőségek egyikét:  

-   Hárítsa el a problémát, a helyrendszer offline állapotát okozza.  

-   A szerepkör eltávolítása az aktuális kiszolgálóról, és a szerepkör telepítése egy új kiszolgálóra.  

 **Endpoint Protection-pont (hierarchia):**  

 A helyrendszerszerepkör nem számít kritikusnak kritikus és a Configuration Manager opcionális funkcionalitást biztosít. Ha a helyrendszer offline állapotba kerül, használja az alábbi lehetőségek egyikét:  

-   Hárítsa el a problémát, a helyrendszer offline állapotát okozza.  

-   A szerepkör eltávolítása az aktuális kiszolgálóról, és a szerepkör telepítése egy új kiszolgálóra.  

 **Beléptetési pont (hely):**  

 A helyrendszerszerepkör nem számít kritikusnak kritikus és a Configuration Manager opcionális funkcionalitást biztosít. Ha a helyrendszer offline állapotba kerül, használja az alábbi lehetőségek egyikét:  

-   Hárítsa el a problémát, a helyrendszer offline állapotát okozza.  

-   A szerepkör eltávolítása az aktuális kiszolgálóról, és a szerepkör telepítése egy új kiszolgálóra.  

 **Beléptetési proxypont (hely):**  

 A helyrendszerszerepkör nem számít kritikusnak kritikus és a Configuration Manager opcionális funkcionalitást biztosít. Azonban a helyrendszerszerepkör a helyre, és több helyen több példánya is telepíthető a hierarchiában. Ha a helyrendszer offline állapotba kerül, használja az alábbi lehetőségek egyikét:  

-   Hárítsa el a problémát, a helyrendszer offline állapotát okozza.  

-   A szerepkör eltávolítása az aktuális kiszolgálóról, és a szerepkör telepítése egy új kiszolgálóra.  

 Ha egy helyen egynél több beléptetési proxykiszolgálóval rendelkezik, a DNS-alias használata a kiszolgáló nevét. Ha használja ezt a konfigurációt, a DNS ciklikus multiplexelés nyújt bizonyos mértékű hibatűrést és terheléselosztást amikor a felhasználók beléptetik a mobileszközeiket.  

 **Tartalék állapotkezelő pont (hely vagy hierarchia):**  

 A helyrendszerszerepkör nem számít kritikusnak kritikus és a Configuration Manager opcionális funkcionalitást biztosít. Ha a helyrendszer offline állapotba kerül, használja az alábbi lehetőségek egyikét:  

-   Hárítsa el a problémát, a helyrendszer offline állapotát okozza.  

-   A szerepkör eltávolítása az aktuális kiszolgálóról, és a szerepkör telepítése egy új kiszolgálóra. Az ügyfelek hozzá vannak rendelve a tartalék állapotkezelő pont ügyfél telepítése alatt, mert szüksége lesz a meglévő ügyfeleket az új helyrendszer-kiszolgáló használatára.  

### <a name="see-also"></a>További információ  
 [A System Center Configuration Manager támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md)

