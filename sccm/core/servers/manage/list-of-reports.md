---
title: "A jelentések listájának |} Microsoft Docs"
description: "Tekintse át a listában, a jelentések, amelyeket a Configuration Managerrel. A jelentések különböző kategóriákban jelennek meg."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7332ed3-8003-454b-bb12-1fdf8721425c
caps.latest.revision: 10
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 1480c38a6a3afef76b2e8759eaafd47d28f978f4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="list-of-reports-in-system-center-configuration-manager"></a>A jelentések listája a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Számos beépített jelentést megadva, a System Center Configuration Managerrel, végrehajtani kívánt jelentéskészítési feladatok nagy lefedik. A jelentésekben található SQL-utasítások használatával saját jelentéseket is írhat. Olvassa el ebben a témakörben további tudnivalók a jelentések, amelyeket a Configuration Managerrel.  

## <a name="list-of-built-in-configuration-manager-reports"></a>A Configuration Manager beépített jelentések listája  
 Az alábbi jelentések érhetők el a Configuration Managerrel. A jelentések különböző kategóriákban jelennek meg.  

### <a name="administrative-security"></a>Rendszergazdai biztonság  
 Az alábbi jelentések találhatók a **felügyeleti biztonsági** kategóriát.  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Felügyeleti tevékenység naplója**|Megjeleníti a rendszergazdai felhasználók, biztonsági szerepkörök, biztonsági hatókörök és gyűjtemények felügyeleti módosításainak a rekordját.|  
|**Rendszergazda felhasználók biztonsági hozzárendelései**|Megjeleníti a rendszergazda felhasználókat, a hozzájuk társított biztonsági szerepköröket és az egyes felhasználók biztonsági szerepköreihez társított biztonsági hatóköröket.|  
|**Egy biztonsági hatókör által biztonságossá tett objektumok**|Megjeleníti a megadott biztonsági hatókör által biztonságossá tett és csak a biztonsági hatókörhöz rendelt objektumokat. Ez a jelentés nem jeleníti meg az egynél több biztonsági hatókörhöz társított objektumokat.|  
|**Egy vagy több Configuration Manager objektum biztonsága**|Megjeleníti a biztonságossá tehető objektumokat, az objektumokhoz társított biztonsági hatóköröket, valamint azt, hogy mely rendszergazda felhasználók rendelkeznek jogosultságokkal az objektumokhoz.|  
|**Biztonsági szerepkörök összegzése**|Biztonsági szerepkörök és az egyes szerepkörökhöz társított Configuration Manager-rendszergazdák jeleníti meg.|  
|**Biztonsági hatókörök összegzése**|Biztonsági hatókörök és a Configuration Manager rendszergazda felhasználóhoz és biztonsági csoportok egyes hatókörökhöz társított jeleníti meg.|  

### <a name="alerts"></a>Riasztások  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Riasztási stratégiai mutatószámrendszer**|Megjeleníti a megadott kezdési és befejezési dátum között létrehozott, elhalasztott riasztások összegzését.|  
|**Leggyakrabban létrehozott riasztások**|Megjeleníti a megadott szolgáltatásterületre vonatkozóan leggyakrabban létrehozott riasztások összegzését a folyó naptól kezdve visszafelé a megadott dátumig.|  

### <a name="asset-intelligence"></a>Eszközintelligencia  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Hardver 01A – egy adott gyűjtemény számítógépeinek összefoglalása**|Megjeleníti a megadott gyűjteményben lévő számítógépek Eszközintelligencia összegzését.|  
|**Hardver 03A – elsődleges felhasználók**|Megjeleníti a felhasználókat és azon számítógépek számát, amelyen ők az elsődleges felhasználók.|  
|**Hardver 03B – a megadott elsődleges konzolfelhasználóhoz tartozó számítógépek**|Megjeleníti az összes számítógépet, amelyek esetében a megadott felhasználó az elsődleges konzolfelhasználó.|  
|**Hardver 04A – több felhasználóval (megosztott) rendelkező számítógépek**|Megjeleníti azokat a számítógépeket, amelyek nem rendelkeznek elsődleges felhasználóval, mert egyik felhasználó %-os bejelentkezési ideje sem haladja meg a 66%-ot a konzolon.|  
|**Hardver 05A – egy adott számítógép konzolfelhasználói**|Megjeleníti a megadott számítógép összes konzolfelhasználóját.|  
|**Hardver 06A – azonosítatlan felhasználók nem határozható meg számítógépek**|Segítségével a rendszergazda felhasználók azonosíthatják azokat a számítógépeket, amelyeken a biztonsági naplózást be kell kapcsolni.|  
|**Hardver 07A – USB-eszközök gyártónként**|Megjeleníti az USB-eszközöket gyártó szerint csoportosítva.|  
|**Hardver 07b – USB-eszközök gyártól és leírások alapján**|Megjeleníti az USB-eszközöket gyártó és leírás szerint csoportosítva.|  
|**Hardver 07C – megadott USB-eszközzel rendelkező számítógépek**|Megjeleníti a megadott USB-eszközzel rendelkező összes számítógépet.|  
|**Hardver 07D – egy adott számítógép USB-eszközök**|Megjeleníti az adott számítógép összes USB-eszközét.|  
|**Hardver 08A – a hardver nem áll készen szoftverfrissítésre**|Megjeleníti a minimális hardverkövetelményeknek meg nem felelő hardvereket.|  
|**Hardver 09A – számítógépek keresése**|Az Eszközkezelő számítógépek kulcsszószűrő egyezéseinek a számítógép nevét, a Configuration Manager-hely, tartomány, felső szintű konzolfelhasználó, operációs rendszer, gyártó vagy modell összegzését jeleníti meg.|  
|**Hardver 10A – egy meghatározott gyűjtemény megadott időkeretén belül módosított számítógépek**|Azon megadott gyűjtemény számítógépeit jelenít meg, amelyben a hardverosztály módosítva lett a megadott időtartam során.|  
|**Hardver 10B – adott számítógépen meghatározott időkereten belül végrehajtott módosítások**|Megjeleníti a megadott számítógépen a megadott időtartam során módosított osztályokat.|  
|**Licenc 01A – Microsoft nagybani Licencbeadási főkönyve licenc**|Megjeleníti a Microsoft mennyiségi licencelési programjában elérhető összes Microsoft-szoftver leltárát.|  
|**01B licenc - Microsoft mennyiségi licenc főkönyvének eleme eladási csatornánként**|Azonosítja és megjeleníti a leltározott Microsoft mennyiségi licencelési szoftverek értékesítési csatornáját.|  
|**Licenc 01C – adott Microsoft nagybani Licencbeadási főkönyvvel rendelkező elemek és értékesítési csatornák**|Azonosítja és megjeleníti a Microsoft Nagybani Licencbeadási főkönyv megadott elemével rendelkező számítógépeket.|  
|**Licenc 01D – megadott számítógép Microsoft nagybani Licencbeadási Főkönyv termékei**|Azonosítja és megjeleníti a Microsoft Nagybani Licencbeadási főkönyvnek a megadott számítógépen található termékeit.|  
|**Licenc 02A - hamarosan lejáró időtartományonként licencek száma**|Megjeleníti a lejárathoz közeledő licencek számát a megadott időtartomány alapján. A megjelenített termékek licencét a szoftverlicencelési szolgáltatás kezeli.|  
|**Licenc 02B - hamarosan lejáró licenccel rendelkező számítógépek**|Megjeleníti a hamarosan lejáró licencekkel rendelkező, megadott számítógépeket.|  
|**Licenc 02C - licencinformációk egy bizonyos számítógépen**|Megjeleníti a megadott számítógép azon termékeit, amelyek licencét a szoftverlicencelési szolgáltatás kezeli.|  
|**Licenc 03A – licencek licencállapotonként száma**|Megjeleníti azon termékeket licencállapot alapján, amelyek licenceit a szoftverlicencelési szolgáltatás kezeli.|  
|**Licenc 03B – meghatározott licencállapotú számítógépek**|Megjeleníti azon megadott licencállapotú termékeket, amelyek licenceit a szoftverlicencelési szolgáltatás kezeli.|  
|**Licenc 04A - a szoftverlicencelés által kezelt termékek száma**|Megjeleníti azon termékek számát, amelyek licencét a szoftverlicencelési szolgáltatás kezeli.|  
|**Licenc 04B – szoftverlicencelési szolgáltatás által kezelt termékekkel rendelkező számítógépek**|Megjeleníti a szoftverlicencelési szolgáltatás által kezelt azon számítógépeket, amelyek a megadott terméket tartalmazzák.|  
|**Licenc 05A – kulcskezelő szolgáltatást biztosító számítógépek**|Megjeleníti a kulcskezelési kiszolgálóként működő számítógépeket.|  
|**Licenc 06A – processzorok száma processzoronkénti licencelésű termékeknél**|Megjeleníti a processzoronkénti licencelést támogató Microsoft-termékeket használó számítógépek processzorainak a számát.|  
|**Licenc 06B – processzoronkénti licencelést támogató megadott termékkel rendelkező számítógépek**|Megjeleníti azon számítógépek listáját, amelyeken telepítve lett a processzoronkénti licencelést támogató megadott Microsoft-termék.|  
|**Licenc 14A – Microsoft nagybani Licencbeadási egyeztető jelentés**|Megjeleníti a Microsoft mennyiségi licencszerződésén keresztül vásárolt szoftverlicencek és a ténylegesen leltározott darabszámok egyeztetését.|  
|**Licenc 14B – az mvls-ben nem található Microsoft szoftverleltár listája**|Ez a jelentés azon használatban lévő Microsoft-szoftvercímeket jeleníti meg, amelyek nem találhatók meg a Microsoft mennyiségi licencszerződésében.|  
|**Licenc 15A – általános licencegyeztetési jelentés**|Megjeleníti a vásárolt általános szoftverlicencek és a ténylegesen leltározott darabszámok egyeztetését.|  
|**Licenc 15B – a számítógép általános licencegyeztetési jelentése**|Megjeleníti a licencelt terméket a megadott verzióval telepítő számítógépeket.|  
|**Szoftver 01A – egy megadott gyűjtemény telepített szoftvereinek összegzése**|Megjeleníti a telepített szoftverek összegzését a leltárban található példányok száma szerint.|  
|**Szoftver 02A – egy adott gyűjtemény termékcsaládjai**|Megjeleníti a megadott gyűjteményben található termékcsaládokat és a család szoftvereinek a számát.|  
|**Szoftver 02B – egy megadott termékcsalád termékkategóriái**|Megjeleníti a megadott termékcsaládban található termékkategóriákat és a kategória szoftvereinek a számát.|  
|**Szoftver 02C – egy megadott termékcsalád és termékkategória szoftverei**|Megjeleníti a megadott termékcsaládban és kategóriában található összes szoftvert.|  
|**Szoftver 02D – meghatározott szoftverrel rendelkező számítógépek**|Megjeleníti a megadott szoftverrel rendelkező összes számítógépet.|  
|**Szoftver 02E – adott számítógépre telepített szoftver**|Megjeleníti az adott számítógépre telepített összes szoftvert.|  
|**Szoftver 03A – nem kategorizált szoftverek**|Megjeleníti az ismeretlenként besorolt vagy nem besorolt szoftvereket.|  
|**Szoftver 04A – szoftvereket a számítógépeken automatikus futtatásra konfigurált**|Megjeleníti a számítógépeken automatikus futtatásra konfigurált szoftverek listáját.|  
|**Szoftver 04B – automatikus futtatásra konfigurált szoftverekkel rendelkező számítógépek**|Megjeleníti automatikus futtatásra konfigurált szoftverekkel rendelkező összes számítógépet.|  
|**Szoftver 04C – megadott számítógép automatikus futtatásra konfigurált szoftverek**|Megjeleníti a megadott számítógépen telepített, automatikus futtatásra konfigurált szoftvereket.|  
|**Szoftver 05A – böngésző segédobjektumai**|Megjeleníti a megadott gyűjtemény számítógépeire telepített böngésző segédobjektumait.|  
|**Szoftver 05B – megadott böngésző Segédobjektummal rendelkező számítógépek**|Megjeleníti a megadott böngésző segédobjektummal rendelkező összes számítógépet.|  
|**05C szoftverek - Böngészősegítő objektumok egy bizonyos számítógépen**|Megjeleníti a megadott számítógép összes böngésző segédobjektumát.|  
|**Szoftver 06A – telepített szoftver keresése**|Ez a jelentés a telepített szoftverek összegzését jeleníti meg a terméknévre, közzétevőre vagy verzióra vonatkozó keresési feltételeknek megfelelő példányok száma alapján rendezve.|  
|**Szoftver 06B – szoftverek terméknév alapján**|Megjeleníti a telepített szoftverek összegzését a megadott terméknévnek megfelelő példányok száma alapján rendezve.|  
|**Szoftver 07A – mostanában használt végrehajtható programok a számítógépek száma szerint**|Megjeleníti a mostanában használt végrehajtható programokat azon számítógépek számával, amelyeken használták a programokat. A jelentés megtekintéséhez engedélyezni kell a szoftverhasználat-mérést a hely számára.|  
|**Szoftver 07B – mostanában használt számítógépek egy megadott végrehajtható programot**|Megjeleníti azon számítógépeket, amelyeken a megadott végrehajtható programot mostanában használtak, ha engedélyezte a szoftverhasználat-mérési ügyfélbeállítást.|  
|**Szoftver 07C – mostanában használt végrehajtható programok a számítógép**|Megjeleníti azon végrehajtható fájlokat, amelyeket mostanában a megadott számítógépen használtak, ha engedélyezte a szoftverhasználat-mérési ügyfélbeállítást.|  
|**Szoftver 08A – mostanában használt végrehajtható programok a felhasználók száma szerint**|Megjeleníti a mostanában használt végrehajtható programokat a programokat használó felhasználók számával együtt, ha engedélyezte a szoftverhasználat-mérési ügyfélbeállítást.|  
|**Szoftver 08B – mostanában használó felhasználók a megadott végrehajtható programot**|Megjeleníti a megadott végrehajtható programot mostanában használó felhasználókat, ha engedélyezte a szoftverhasználat-mérési ügyfélbeállítást.|  
|**Szoftver 08C – mostanában használt végrehajtható programok által egy adott felhasználó**|Megjeleníti azon végrehajtható programokat, amelyeket mostanában a megadott felhasználó használt, ha engedélyezte a szoftverhasználat-mérési ügyfélbeállítást.|  
|**Szoftver 09A – ritkán használt szoftverek**|Megjeleníti a megadott időtartam során nem használt szoftvereket.|  
|**Szoftver 09B - számítógépekre telepített ritkán használt szoftverekkel rendelkező**|Megjeleníti azon számítógépeket, amelyek telepített szoftvereit nem használták a megadott időtartam során. A megadott időtartam a „Szoftver 09A – Ritkán használt szoftverek” jelentésben megadott értéken alapul.|  
|**Szoftver 10A – szoftver adott több egyéni címkével**|Megjeleníti a megadott egyénicímke-feltételek mindegyikének megfelelő szoftvereket. Legfeljebb három egyéni címke jelölhető ki a szoftverek keresésének finomításához.|  
|**Szoftver 10B – telepített egyéni címkével rendelkező szoftver adott rendelkező számítógépek**|Megjeleníti a gyűjtemény összes olyan számítógépét, amelyen a megadott egyéni címkével rendelkező szoftver telepítve lett.|  
|**Szoftver 11A – megadott egyéni címkével rendelkező szoftverek listáját.**|Megjeleníti a megadott egyénicímke-feltételek legalább egyikének megfelelő szoftvereket.|  
|**Szoftver 12A – egyéni címkével nem rendelkező szoftverek nevét**|Megjeleníti a meghatározott egyéni címkével nem rendelkező szoftvereket.|  
|**14A szoftver - engedélyezett szoftverazonosító címkével engedélyezett ellátott szoftverek keresése**|Megjeleníti az engedélyezett szoftverazonosító címkével ellátott, telepített szoftverek számát.|  
|**14B szoftver - meghatározott szoftverazonosító címkével rendelkező számítógépek ellátott, telepített szoftverek**|Megjeleníti a megadott engedélyezett szoftverazonosító címkével ellátott, telepített szoftverekkel rendelkező számítógépeket.|  
|**Telepített szoftverek 14C - szoftver szoftverazonosító címkével ellátott szoftver egy adott számítógépen**|Megjeleníti a megadott engedélyezett szoftverazonosító címkével ellátott, a megadott számítógépen telepített szoftvereket.|  

### <a name="client-push"></a>Ügyfél leküldése  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Ügyfélleküldés telepítési állapotának részletei**|Információkat jelenít meg az ügyfélleküldés telepítési folyamatával kapcsolatban az összes helyre vonatkozóan.|  
|**Ügyfélleküldés telepítési állapotának részletei az adott hely**|Információkat jelenít meg az ügyfélleküldés telepítési folyamatával kapcsolatban a megadott helyre vonatkozóan.|  
|**Ügyfélleküldés telepítési állapotának összegzése**|Összegzési nézetet jelenít meg az ügyfélleküldés telepítési állapotával kapcsolatban az összes helyre vonatkozóan.|  
|**Ügyfélleküldés telepítési állapotának összegzése az adott hely**|Összegzési nézetet jelenít meg az ügyfélleküldés telepítési állapotával kapcsolatban a megadott helyre vonatkozóan.|  

### <a name="client-status"></a>Ügyfélállapot  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Ügyfél szervizelési részletei**|Az ügyfél szervizelési műveleteivel kapcsolatos részleteket jelenít meg a megadott gyűjteményre vonatkozóan.|  
|**Ügyfél szervizelési összegzése**|Megjeleníti az ügyfél szervizelési műveleteinek az összegzését a megadott gyűjteményre vonatkozóan.|  
|**Az ügyfél állapotelőzményei**|Megjeleníti az ügyfél átfogó állapotelőzményeinek a nézetét a helyre vonatkozóan.|  
|**Ügyfélállapot összegzése**|Megjeleníti a megadott gyűjtemény aktív ügyfeleinek ügyfél-ellenőrzési eredményeit.|  
|**Ügyfél kérelmezési ideje házirend**|Megjeleníti az elmúlt 30 napban legalább egyszer házirendet kérő ügyfelek százalékos arányát. Az egyes napok a ciklus első napja óta házirendet kérő összes ügyfél százalékos arányát jelenítik meg.|  
|**Részletek ügyfélellenőrzésekkel rendelkező sikertelen**|Részleteket jeleníti meg azon ügyfelekkel kapcsolatban, amelyek ügyfélellenőrzése sikertelen volt a megadott gyűjtemény esetében.|  
|**Inaktív ügyfelek részletei**|Megjeleníti a megadott gyűjtemény inaktív ügyfeleinek részletes listáját.|  

### <a name="company-resource-access"></a>Vállalati erőforrás-hozzáférés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Tanúsítványkiadási előzmények**|Megjeleníti a tanúsítványregisztrációs pont által a megadott dátumtartományban a felhasználók és eszközök számára kibocsátott tanúsítványok előzményeit.|  
|**Tanúsítványkiadási állapot szerint rendezett eszközlista**|Megjeleníti a megadott tanúsítványprofil értékelése után a megadott tanúsítványkiadási állapotban lévő eszközöket vagy felhasználókat.|  
|**A hamarosan lejáró tanúsítvánnyal rendelkező eszközök listája**|Megjeleníti a megadott dátumon vagy az előtt lejáró tanúsítványokkal rendelkező eszközöket vagy felhasználókat.|  

### <a name="compliance-and-settings-management"></a>Megfelelőség- és beállításkezelési ügynök  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Az alapkonfiguráció megfelelőségi előzményei**|Megjeleníti az alapkonfiguráció megfelelőségi változásainak az előzményeit a megadott dátumtartományra vonatkozóan.|  
|**Konfigurációs elem megfelelőségi előzményei**|Megjeleníti a konfigurációs elem megfelelőségi változásainak az előzményeit a megadott dátumtartományra vonatkozóan.|  
|**Az eszközhöz tartozó alapkonfiguráció konfigurációs elemek megfelelő szabályainak részletei**|Megjeleníti a megadott eszköz vagy felhasználó megadott konfigurációs elemére vonatkozóan a megfelelőként értékelt szabályokkal kapcsolatos információkat.|  
|**Az eszközhöz tartozó alapkonfiguráció konfigurációs elemek ütköző szabályainak részletei**|A megadott felhasználó vagy eszköz számára üzembe helyezett konfigurációs elem azon szabályaival kapcsolatban jelenít meg információkat, amelyek ütköznek az ugyanazon vagy egy másik üzembe helyezett konfigurációs elem más szabályaival.|  
|**Az eszközhöz tartozó alapkonfiguráció konfigurációs elemek hibái**|Megjeleníti a megadott eszköz vagy felhasználó adott konfigurációs eleme által létrehozott hibákkal kapcsolatos információkat.|  
|**Az eszközhöz tartozó alapkonfiguráció konfigurációs elemeire nem kompatibilisnek értékelt szabályok részletei**|Megjeleníti a megadott eszköz vagy felhasználó megadott konfigurációs elemére vonatkozóan a nem megfelelőként értékelt szabályokkal kapcsolatos információkat.|  
|**Az eszközhöz tartozó alapkonfiguráció konfigurációs elemeire vonatkozó szervizelt szabályok részletei**|Megjeleníti a megadott eszköz vagy felhasználó megadott konfigurációs eleme által szervizelt szabályokkal kapcsolatos információkat.|  
|**Eszközök listája az alapkonfiguráció konfigurációs elemének megfelelőségi állapota alapján**|Megjeleníti a megadott konfigurációs elem értékelése után a megadott megfelelőségi állapotban lévő eszközöket vagy felhasználókat.|  
|**Az alapkonfiguráció megfelelőségi állapot szerint rendezett eszközlista**|Megjeleníti a megadott alapkonfiguráció értékelése után a megadott megfelelőségi állapotban lévő eszközöket vagy felhasználókat.|  
|**Az eszközhöz tartozó szabályával ütköző szabályok listája**|Megjeleníti a megadott eszközön üzembe helyezett konfigurációs elemre vonatkozó, megadott szabállyal ütköző szabályok listáját.|  
|**Az alapkonfiguráció ismeretlen eszközök listája**|Megjeleníti azon eszközök vagy felhasználók listáját, amelyek még nem jelentettek megfelelőségi adatokat a megadott alapkonfigurációra vonatkozóan.|  
|**Egy konfigurációs elem ismeretlen eszközök listája**|Megjeleníti azon eszközök vagy felhasználók listáját, amelyek még nem jelentettek megfelelőségi adatokat a megadott konfigurációs elemre vonatkozóan.|  
|**Szabályai és hibái az eszközhöz tartozó alapkonfiguráció konfigurációs elemek**|Megjeleníti a megadott eszköz vagy felhasználó számára üzembe helyezett, megadott konfigurációs elemre vonatkozó szabályok és beállítási hibák megfelelőségi állapotának az összegzését.|  
|**Megfelelőségi összegzés alapkonfigurációnként**|Megjeleníti a hierarchiában üzembe helyezett alapkonfigurációk átfogó megfelelőségének az összegzését.|  
|**Az alapkonfiguráció konfigurációs elemének megfelelőségi összegzése**|Megjeleníti a megadott alapkonfigurációban lévő konfigurációs elemek megfelelőségének az összegzését.|  
|**Konfigurációs házirendek összegző megfelelősége**|Megjeleníti a konfigurációs házirendek megfelelőségének összegzését.|  
|**A gyűjtemény az alapkonfiguráció megfelelőségi összegzése**|Megjeleníti a megadott gyűjteményben üzembe helyezett, megadott alapkonfiguráció átfogó megfelelőségének az összegzését.|  
|**Nem megfelelő alkalmazásainak és eszközeinek egy adott felhasználó listája**|Azon felhasználókról és eszközökről jelenít meg adatokat, akik vagy amelyek a beállított szabályzatnak nem megfelelő alkalmazásokkal rendelkeznek.|  
|**Nem megfelelő alkalmazásokkal rendelkező felhasználók összegzése**|Azon felhasználókról jelenít meg adatokat, akik a beállított szabályzatnak nem megfelelő alkalmazásokat használnak.|  
|**Feltételek és kikötések elfogadása**|Megjeleníti a feltételeket és kikötéseket tartalmazó elemeket, illetve hogy az egyes felhasználók ezek mely verzióját fogadták el.|  

### <a name="device-management"></a>Eszközkezelés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Összes mobileszköz ügyfél**|Információkat jelenít meg az összes mobileszköz-ügyféllel kapcsolatban. Az Exchange Server-összekötő által kezelt eszközöket a jelentés nem tartalmazza.|  
|**A Windows CE Configuration Manager-ügyfél által kezelt és, amelyek nem kifogástalan állapotú mobileszközök tanúsítványproblémái**|A részletes a Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök tanúsítványproblémáival kapcsolatos adatokat jeleníti meg.|  
|**A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök központi telepítési problémái**|Részletes információit jeleníti meg a Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök központi telepítési problémáiról.|  
|**A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök ügyfél központi telepítési állapotának részletei**|A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök állapotára vonatkozó információkat jeleníti meg.|  
|**A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök sikeres központi**|Részletes információit jeleníti meg a Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök sikeres központi telepítéseivel kapcsolatban.|  
|**A Windows CE Configuration Manager-ügyfél által kezelt és, amelyek nem kifogástalan állapotú mobileszközök kommunikációs problémái**|Ez a jelentés a Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök kommunikációs problémáiról részletes információkat tartalmaz.|  
|**Az Exchange Server-összekötő által kezelt mobileszközök megfelelőségi állapota**|Megjeleníti az alapértelmezett Exchange ActiveSync postaláda-házirendnek való megfelelőségi állapot összegzését az Exchange Server-összekötő által kezelt mobileszközökre vonatkozóan.|  
|**Által mobileszközök száma megjelenítési beállítások**|Ez a jelentés a mobileszközök számát jeleníti meg a megjelenítési beállítások alapján.|  
|**Operációs rendszer által a mobileszközök száma**|Megjeleníti a mobileszközök számát az operációs rendszer alapján.|  
|**Mobileszközök programmemória alapján száma**|Megjeleníti a mobileszközök számát a programmemória alapján.|  
|**Mobileszközöket a tárolómemória beállításai alapján**|Mobileszközök száma a tárolómemória beállításai alapján|  
|**A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközökre vonatkozó állapottal kapcsolatos adatok**|A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközökre vonatkozó állapottal kapcsolatos részletes jeleníti meg.|  
|**A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök állapotinformációi**|A Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök állapotösszegzési információkat jeleníti meg.|  
|**Az Exchange Server-összekötő által kezelt inaktív mobileszközök**|Megjeleníti az Exchange Server-összekötő használatával kezelt és az Exchange Server kiszolgálóhoz a megadott számú napig nem csatlakozott mobileszközöket.|  
|**A Microsoft Intune-ban felhasználónként regisztrált eszközök listája**|A felhasználó a Microsoft Intune által regisztrált összes eszközt megjeleníti.|  
|**Eszközök listája feltételes hozzáférési állapot szerint**|Az eszközök aktuális megfelelőségi és feltételes hozzáférési állapotáról jelenít meg információkat. Ezt a jelentést a feltételes hozzáférési házirendekhez használhatja. A jelentés a Configuration Manager 1602-es verziójától érhető el.|  
|**Felhasználó feltételes hozzáférési megfelelősége**|Részletes feltételes hozzáférési megfelelőségi információkat nyújt egy adott felhasználó kapcsán, többek között az eszköz nevét és platformját, az eszköz megfelelőségi állapotát, valamint az eszköz legutóbbi értékelésének időpontját. A jelentés a Configuration Manager 1602-es verziójától érhető el.|  
|**A Windows CE Configuration Manager-ügyfél által kezelt és, amelyek nem kifogástalan állapotú mobileszközök helyi ügyfelekkel kapcsolatos problémái**|Ez a jelentés a Windows CE Configuration Manager-ügyfél által felügyelt mobileszközök helyi ügyfelekkel kapcsolatos problémáiról részletes információkat tartalmaz.|  
|**Mobileszköz ügyfél-információ**|Megjeleníti a Configuration Manager-ügyféllel rendelkező mobileszközökkel kapcsolatos információkat. Ezzel a jelentéssel ellenőrizheti, hogy mely eszközök tudnak sikeresen kommunikálni egy felügyeleti ponttal.|  
|**Mobileszközök megfelelőségi adatai az Exchange Server-összekötőhöz**|Megjeleníti a mobileszközök megfelelőségi adatait az Exchange Server-összekötővel konfigurált alapértelmezett Exchange ActiveSync postaláda-házirendre vonatkozóan.|  
|**Mobileszközök operációs rendszerek alapján**|Megjeleníti a mobileszközöket az operációs rendszer alapján.|  
|**Jailbreakelt vagy rootolt mobileszközök**|Megjeleníti a jailbreakelt vagy rootolt mobileszközöket.|  
|**Nélküliek, mert nem sikerült a helyhez rendelt de beléptetett mobileszközök**|Mobileszközöket jeleníti meg a Configuration Manager segítségével sikeresen beléptetett és tanúsítvánnyal rendelkező, de nem sikerült végzik a helyhozzárendelést.|  
|**Meghatározott mennyiségű szabad programmemóriával rendelkező mobileszközök**|Megjeleníti a megadott mennyiségű szabad programmemóriával rendelkező összes mobileszközt.|  
|**Meghatározott mennyiségű szabad eltávolítható memóriával rendelkező mobileszközök**|Megjeleníti a megadott mennyiségű szabad eltávolítható memóriával rendelkező összes mobileszközt.|  
|**Tanúsítvány megújításával kapcsolatos problémákkal rendelkező mobileszközök**|Megjeleníti a tanúsítványukat nem megújító, beléptetett mobileszközöket. Ha a tanúsítvány megújítása nem történik meg a lejárati idő előtt, a mobileszközök nem lesznek kezelhetők.|  
|**Kevés programmemóriával rendelkező mobileszközök (kevesebb mint a megadott szabad KB érték) program**|Megjeleníti azon mobileszközöket, amelyek programmemóriája kisebb a KB-ban megadott méretnél.|  
|**Alacsony eltávolítható tárolómemóriával (kevesebb mint a megadott szabad KB érték) rendelkező mobileszközök**|Megjeleníti azon mobileszközöket, amelyek eltávolítható tárolómemóriája kisebb a KB-ban megadott méretnél.|  
|**A Windows Intune-ban felhasználónként regisztrált eszközök száma**|Ez a jelentés megjeleníti a Microsoft Intune-előfizetés használatára jogosult felhasználókat, és a regisztrált eszközök teljes száma minden felhasználóhoz.|  
|**Mobileszközök függőben lévő törlési kérése**|Megjeleníti a mobileszközökre vonatkozóan függőben lévő törlési kéréseket.|  
|**A közelmúltban beléptetett és hozzárendelt mobileszközök**|A Configuration Manager a közelmúltban beléptetett és sikeresen helyhez rendelt mobileszközöket jeleníti meg.|  
|**Közelmúltban törölt mobileszközök**|Megjeleníti a közelmúltban sikeresen törölt mobileszközök listáját.|  
|**Összegzés az Exchange Server-összekötő által felügyelt mobileszközökre vonatkozó beállítások**|Megjeleníti az Exchange Server-összekötő által kezelt alapértelmezett Exchange ActiveSync postaláda-házirendek beállításait alkalmazó mobileszközök számát.|  
|**Windows RT saját telepítési kulcs részletes állapota**|Megjeleníti a megadott Windows RT közvetlen telepítési kulcs részletes állapotinformációit.|  
|**Windows RT saját telepítési kulcsok összegzése**|Megjeleníti a Windows RT közvetlen telepítési kulcsok állapotát.|  

### <a name="driver-management"></a>Illesztőprogram-kezelő  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Összes illesztőprogramja**|Megjeleníti az összes illesztőprogram listáját.|  
|**Adott platformhoz tartozó összes illesztőprogram**|Megjeleníti a megadott platform összes illesztőprogramját.|  
|**Adott rendszerindító lemezkép összes illesztőprogramja**|Megjeleníti a megadott rendszerindító lemezképben lévő összes illesztőprogramot.|  
|**Adott kategória összes illesztőprogramja**|Megjeleníti a megadott kategóriában lévő összes illesztőprogramot.|  
|**Egy adott csomag összes illesztőprogramja**|Megjeleníti a megadott csomagban lévő összes illesztőprogramot.|  
|**Egy adott illesztőprogram kategóriáit**|Megjeleníti a megadott illesztőprogram kategóriáit.|  
|**Nem sikerült telepíteni az illesztőprogramokat egy adott gyűjtemény számítógépek**|Megjeleníti azon számítógépeket, amelyek nem telepítettek illesztőprogramokat a megadott gyűjtemény számára.|  
|**Illesztőprogram-katalógus adott gyűjteményre vonatkozó egyezési jelentése**|Megjeleníti az illesztőprogram-katalógusnak a megadott gyűjteményre vonatkozó egyezési jelentését.|  
|**Illesztőprogram-katalógus adott számítógépre vonatkozó egyezési jelentése**|Megjeleníti az illesztőprogram-katalógusnak a megadott számítógépre vonatkozó egyezési jelentését.|  
|**Illesztőprogram-katalógus egyezési jelentése egy adott eszközhöz egy bizonyos számítógépen**|Megjeleníti az illesztőprogram-katalógusnak a megadott számítógép megadott eszközére vonatkozó egyezési jelentését.|  
|**Illesztőprogram-katalógus számítógépeire vonatkozó egyezési jelentését egy adott gyűjteményben található meghatározott eszközzel rendelkező**|Megjeleníti az illesztőprogram-katalógusnak a megadott eszközzel rendelkező megadott gyűjtemény számítógépeire vonatkozó egyezési jelentését.|  
|**Az adott számítógépre sikertelenül telepített illesztőprogramok**|Megjeleníti a megadott számítógépre sikertelenül telepített illesztőprogramokat.|  
|**Egy adott illesztőprogram támogatott platformjai**|Megjeleníti a megadott illesztőprogram támogatott platformjait.|  

### <a name="endpoint-protection"></a>Endpoint Protection  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Kártevőirtó tevékenységgel kapcsolatos jelentés**|Megjeleníti a kártevőirtói tevékenységek áttekintését.|  
|**Kártevőirtó összesített állapota és előzményei**|Megjeleníti a kártevőirtó átfogó állapotát és előzményeit.|  
|**Számítógép kártevőinek részletei**|Megjeleníti a megadott számítógép részleteit és az azon található kártevők listáját.|  
|**Fertőzött számítógépek**|Megjeleníti azon számítógépek listáját, amelyeken a megadott fenyegetést észlelte a rendszer.|  
|**Fenyegetettségeknek leginkább kitett felhasználók**|Megjeleníti a legtöbb észlelt fenyegetéssel rendelkező felhasználók listáját.|  
|**Felhasználói fenyegetések listája**|Megjeleníti a megadott felhasználói fiók esetén talált fenyegetések listáját.|  

### <a name="hardware---cd-rom"></a>Hardver – CD-ROM  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy adott számítógép CD-ROM adatai**|Megjeleníti a megadott számítógép CD-ROM-meghajtóival kapcsolatos információkat.|  
|**Egy adott CD-ROM gyártó által számítógépek**|Megjeleníti a megadott gyártó által készített CD-ROM-meghajtót tartalmazó számítógépek listáját.|  
|**CD-ROM-meghajtók száma gyártónként**|Megjeleníti a gyártónként leltárazott CD-ROM-meghajtók számát.|  
|**Előzmények – egy adott számítógép CD-ROM előzményei**|Megjeleníti a megadott számítógép CD-ROM-meghajtóinak leltárelőzményeit.|  

### <a name="hardware---disk"></a>Hardver – lemez  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy meghatározott méretű merevlemezzel rendelkező számítógépek**|Megjeleníti a megadott méretű merevlemezzel rendelkező számítógépek listáját.|  
|**Kevés szabad lemezterület (kevesebb mint a megadott % szabad) rendelkező számítógépek**|Megjeleníti a megadott gyűjtemény azon számítógépeinek listáját, amelyek a megadott szabad lemezterületnél kevesebb lemezterülettel rendelkeznek.|  
|**A kevés szabad tárhellyel számítógépek (a megadottnál kevesebb szabad MB)**|Megjeleníti azon számítógépek és lemezek listáját, amelyek kevés szabad területtel rendelkeznek. Az ellenőrizendő szabad lemezterület mennyisége MB-ban van megadva.|  
|**Fizikailemez-konfigurációk száma**|Megjeleníti a lemezkapacitás alapján leltározott merevlemezek számát.|  
|**Egy adott számítógép – logikai lemezek lemezadatai**|Megjeleníti a megadott számítógép logikai lemezeivel kapcsolatos összegző információkat.|  
|**Egy adott számítógép - partíciók lemezadatai**|Megjeleníti a megadott számítógép lemezpartícióival kapcsolatos összegző információkat.|  
|**Egy adott számítógép - fizikai lemezek lemezadatai**|Megjeleníti a megadott számítógép fizikai lemezeivel kapcsolatos összegző információkat.|  
|**Előzmények – logikai lemezek egy adott számítógépen**|Megjeleníti a megadott számítógép logikailemez-meghajtóinak leltárelőzményeit.|  

### <a name="hardware---general"></a>Hardver – általános  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy egyedi számítógép információi**|Megjeleníti a megadott számítógép összegző információit.|  
|**A megadott munkacsoportban vagy tartományban található számítógépek**|Megjeleníti a megadott munkacsoportban vagy tartományban található számítógépek listáját.|  
|**Adott gyűjteményhez társított leltározási osztályok**|Megjeleníti a megadott gyűjteményhez rendelt leltározási osztályokat.|  
|**Egy adott számítógépen engedélyezett leltározási osztályok**|Megjeleníti a megadott számítógépen engedélyezett leltározási osztályokat.|  

### <a name="hardware---memory"></a>Hardver – memória  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Módosított fizikai memóriával rendelkező számítógépek**|Megjeleníti azon számítógépek listáját, amelyeken a RAM mennyisége megváltozott az utolsó leltározási ciklus óta.|  
|**A meghatározott RAM mennyiséggel rendelkező számítógépek**|Megjeleníti a megadott mennyiségű RAM-mal rendelkező számítógépek listáját (a legközelebbi MB-ra kerekített teljes fizikai memória).|  
|**(Kisebb vagy egyenlő, mint az előírt Megabájtnál) kevés memóriával rendelkező számítógépek**|Megjeleníti a kevés memóriával rendelkező számítógépek listáját. Az ellenőrizendő memória mennyisége MB-ban van megadva.|  
|**Memóriakonfigurációk száma**|Megjeleníti a RAM mennyisége alapján leltározott számítógépek számát.|  
|**Egy adott számítógép memóriájának adatai**|Megjeleníti a megadott számítógép memóriájával kapcsolatos összegző információkat.|  

### <a name="hardware---modem"></a>Hardver – Modem  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy adott modemgyártók tartozó számítógépek**|Megjeleníti a megadott gyártó által készített modemmel rendelkező számítógépek listáját.|  
|**Modemek száma gyártónként**|Megjeleníti az egyes modemgyártók szerint leltárazott modemek számát.|  
|**Egyedi számítógép modemmel kapcsolatos információi**|Megjeleníti a megadott számítógép modemjével kapcsolatos összegző információkat.|  

### <a name="hardware---network-adapter"></a>Hardver – hálózati kártya  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A megadott hálózati adapterrel rendelkező számítógépek**|Megjeleníti a megadott hálózati adapterrel rendelkező számítógépek listáját.|  
|**A hálózati kártyák száma típusonként**|Megjeleníti a leltárazott hálózati adapterek típusonkénti számát.|  
|**Egy adott számítógép hálózati adapter adatai**|Megjeleníti a megadott számítógépen telepített hálózati adapterekkel kapcsolatos információkat.|  

### <a name="hardware---processor"></a>Hardver – processzor  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott processzorsebességgel rendelkező számítógépek**|Megjeleníti a megadott sebességű processzorral rendelkező számítógépek listáját.|  
|**(Nagyobb vagy egyenlő a megadott órajelű) nagy sebességű processzorokkal rendelkező számítógépek**|Megjeleníti a megadott sebességnél nagyobb sebességű processzorokkal rendelkező számítógépek listáját.|  
|**(Kisebb vagy egyenlő a megadott órajelű) alacsony sebességű processzorokkal rendelkező számítógépek**|Megjeleníti a megadott órajelsebességen vagy az alatt futó processzorokkal rendelkező számítógépek listáját.|  
|**Count processzorsebesség alapján leltározott számítógépek**|Megjeleníti a processzorsebesség alapján leltárazott számítógépek számát.|  
|**Egy egyedi számítógép processzorával kapcsolatos információk**|Megjeleníti a megadott számítógépen telepített processzorokkal kapcsolatos információkat.|  

### <a name="hardware---scsi"></a>Hardver – SCSI  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott SCSI-kártyával rendelkező számítógépek**|Megjeleníti a megadott SCSI-kártyával rendelkező számítógépek listáját.|  
|**Count SCSI-Kártyatípusok**|Megjeleníti a leltárazott SCSI-kártyák számát kártyatípus alapján.|  
|**Egyedi számítógép SCSI-kártyájának információi**|Megjeleníti a megadott számítógépen telepített SCSI-kártyákkal kapcsolatos információkat.|  

### <a name="hardware---sound-card"></a>Hardver – hangkártya  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott hangkártyával rendelkező számítógépek**|Megjeleníti a megadott hangkártyával rendelkező számítógépek listáját.|  
|**Hangkártyák száma**|Megjeleníti az egyes hangkártyatípusok alapján leltárazott számítógépek számát.|  
|**Egy adott számítógép hangkártya-információi**|Megjeleníti a megadott számítógép hangkártyáival kapcsolatos összegző információkat.|  

### <a name="hardware---video-card"></a>Hardver – videokártya  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott videokártyával rendelkező számítógépek**|Megjeleníti a megadott videokártyával rendelkező számítógépek listáját.|  
|**Videokártyák száma típusonként**|A számítógépekre telepített összes videokártya listáját jeleníti meg az egyes videokártya-típusok számával együtt.|  
|**Egyedi számítógép videokártya információi**|Az egy adott számítógépre telepített videokártyák összegző információit jeleníti meg.|  

### <a name="migration"></a>Áttelepítés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A kizárási listán szereplő ügyfelek**|Az áttelepítésből kizárt ügyfeleket jeleníti meg.|  
|**Függőség egy Configuration manager-gyűjteménytől**|A forráshierarchia gyűjteményétől függő objektumokat jeleníti meg.|  
|**Áttelepítési feladat tulajdonságai**|Ez a jelentés a megadott áttelepítési feladat tartalmait jeleníti meg.|  
|**Áttelepítési feladatok**|Ez a jelentés az áttelepítési feladatok listáját jeleníti meg.|  
|**Sikertelenül telepített objektumok**|Az utolsó kísérlet során sikeretlenül áttelepített objektumok listáját jeleníti meg.|  

### <a name="network"></a>Hálózat  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**IP-címeinek száma alhálózat**|Az egyes IP-alhálózatokhoz leltárazott IP-címek számát jeleníti meg.|  
|**IP - alhálózati maszk összes alhálózata**|Megjeleníti az IP-alhálózatok és az alhálózati maszkok listáját.|  
|**IP – megadott alhálózat számítógépei**|Megjeleníti az adott IP-alhálózat számítógépeinek és IP-információinak listáját.|  
|**IP – megadott számítógép információi**|Az adott számítógépen lévő IP összegző információit jeleníti meg.|  
|**IP – meghatározott IP-cím adatai**|Az adott IP-cím összegző információit jeleníti meg.|  
|**MAC – azonos MAC-címhez tartozó számítógépek**|Az adott MAC-címmel rendelkező számítógépek nevét és IP-címét jeleníti meg.|  

### <a name="network-access-protection"></a>Hálózatelérés védelme  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A NAP szervizelés és a szoftverfrissítés központi telepítései által telepített szoftverfrissítések összehasonlítása.**|A telepített szoftverfrissítések összehasonlító összegzését jeleníti meg szoftverfrissítés-telepítések és NAP-szervizelés alapján.|  
|**Gyakoriság egy számítógép volt egy megadott időszakban szervizelésen átesett**|Ez a jelentés a megadott időszakban a számítógépek szervizelésének gyakoriságát jeleníti meg.|  
|**A megadott időszakon belül megadott szoftverfrissítést telepített számítógépek listája**|Azon számítógépek listáját jeleníti meg, amelyek adott szoftverfrissítést telepítettek szervizelés útján a megadott időszakban (napokban).|  
|**A kijelölt szoftverfrissítések alapján adott szoftverfrissítésekkel nem kompatibilis számítógépek listája**|A kiválasztott szoftverfrissítések alapján nem kompatibilis számítógépeket jeleníti meg.|  
|**Amennyiben nem észlelhető NAP-szolgáltatás számítógépek listája**|Azon számítógépek listáját jeleníti meg, ahol nem észlelhető a NAP-szolgáltatás.|  
|**NAP-kompatibilis számítógépek listája**|Azon számítógépek listáját jeleníti meg, ahol a NAP-szolgáltatás nem fut, vagy az állapota ismeretlen.|  
|**A Network Access Protection házirendek listája**|A hálózatvédelmi házirendeket jeleníti meg az érvényességi dátumukkal együtt.|  
|**A legutolsó lekérdezési időköztől számított szervizelés alatt nem kompatibilis számítógépek listája**|A szerviz alatt álló nem kompatibilis számítógépek listáját jeleníti meg az utolsó ismert értékelési idővel együtt.|  
|**Egy megadott időszakban szervizelésen átesett nem kompatibilis számítógépek listája**|A megadott időszakban szervizelés alatt álló nem kompatibilis számítógépek listáját jeleníti meg.|  
|**Adott időszakban fellépő szervizelési hibák listája**|A szervizelési hibák számát jeleníti meg a megadott napok számára vonatkozóan.|  
|**Szervizelésen keresztül telepített szoftverfrissítések listája**|A szervizelésen keresztül telepített szoftverfrissítéseket jeleníti meg a megadott időszakra vonatkozóan.|  
|**A legutolsó lekérdezési időköztől számított szervizelés alatt nem kompatibilis számítógépek összegzése**|Az utolsó lekérdezési időköz óta szervizelés alatt álló nem kompatibilis számítógépek összegzését jeleníti meg.|  
|**Egy megadott időszakban szervizelésen átesett nem kompatibilis számítógépek összegzése**|A megadott időszakban szervizelésen átesett nem kompatibilis számítógépek összegzését jeleníti meg.|  

### <a name="operating-system"></a>Operációs rendszer  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A számítógép operációs rendszer verziójának előzményei**|Az adott számítógépen lévő operációs rendszer leltárelőzményeit jeleníti meg.|  
|**Adott operációs rendszerrel rendelkező számítógépek**|Az adott operációs rendszerrel rendelkező számítógépeket jeleníti meg.|  
|**Egy adott operációs rendszerrel és szervizcsomaggal rendelkező számítógépek**|Az adott operációs rendszerrel és szervizcsomaggal rendelkező számítógépeket jeleníti meg.|  
|**Operációs rendszer verzióinak száma**|Az operációs rendszer szerint leltárazott számítógépek számát jeleníti meg.|  
|**Operációs rendszerek és szervizcsomagok száma**|Az operációs rendszer és szervizcsomag kombinációk szerint leltárazott számítógépek számát jeleníti meg.|  
|**Szolgáltatások – megadott szolgáltatást futtató számítógépek**|Az adott szolgáltatást futtató számítógépek listáját jeleníti meg.|  
|**Szolgáltatások – távelérési kiszolgálót futtató számítógépek**|A Távelérési kiszolgálót futtató számítógépek listáját jeleníti meg.|  
|**Szolgáltatások – megadott számítógép szolgáltatási adatai**|Az adott számítógépen lévő szolgáltatások összegző információit jeleníti meg.|  
|**Windows Server rendszerű számítógépek**|A Windows Server operációs rendszert futtató számítógépek listáját jeleníti meg.|  

### <a name="out-of-band-management"></a>Sávon kívüli felügyelet  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Sávon kívüli felügyeletvezérlőkkel rendelkező számítógépek**|Megjeleníti azon számítógépek listáját, amelyek sávon kívüli felügyeletvezérlőkkel rendelkeznek.|  
|**Sávon kívüli felügyelet konzoljának tevékenysége**|A sávon kívüli felügyeleti konzolja tevékenységeit azonosító állapotüzenetek listáját jeleníti meg.|  
|**Sávon kívüli felügyeletre kiépített ügyfél állapota**|Megjeleníti azon számítógépek listáját, amelyek sávon kívüli felügyelethez vannak kiépítve.|  

### <a name="power-management"></a>Energiagazdálkodás  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Energiagazdálkodás - számítógépes tevékenység**|Egy adott gyűjtemény megfigyelési, számítógépes és felhasználói tevékenységeit mutató grafikont jelenít meg az adott időszakra vonatkozóan.|  
|**Energiagazdálkodás - számítógépes tevékenység számítógépenként**|Egy adott számítógép megfigyelési, számítógépes és felhasználói tevékenységeit mutató grafikont jelenít meg az adott dátumra vonatkozóan.|  
|**Energiagazdálkodás - számítógépes tevékenység részletei**|A megadott gyűjteményben lévő számítógépek alvási és ébresztési képességeinek listáját jeleníti meg a megadott dátumra és időpontra vonatkozóan.|  
|**Energiagazdálkodás – számítógép részletei**|Az adott számítógépre alkalmazott energiaellátási lehetőségek, energiaellátási beállítások és energiasémák részletes információit jeleníti meg.|  
|**Energiagazdálkodás – számítógép nem küld részleteket**|Azon számítógépek listáját jeleníti meg, amelyek nem jelentenek energiatevékenységeket a megadott dátumra és időpontra vonatkozóan.|  
|**Energiagazdálkodás – kizárt számítógépek**|Az energiasémából kizárt számítógépek listáját jeleníti meg.|  
|**Energiagazdálkodás - több energiasémával rendelkező számítógépek**|Megjeleníti azon számítógépek listáját, amelyekre több, ütköző energiaséma érvényes.|  
|**Energiagazdálkodás – energiafogyasztás**|Adott gyűjtemény teljes havi energiafogyasztását jeleníti meg (kWh-ban) az adott időszakra vonatkozóan.|  
|**Energiagazdálkodás - napi energiafogyasztás**|Adott gyűjtemény teljes energiafogyasztását jeleníti meg (kWh-ban) az elmúlt 31 napra vonatkozóan.|  
|**Energiagazdálkodás – energiaköltségek**|Adott gyűjtemény teljes havi energiafogyasztásának költségét jeleníti meg az adott időszakra vonatkozóan.|  
|**Energiagazdálkodás - napi energiaköltség**|Adott gyűjtemény teljes energiafogyasztásának költségét jeleníti meg az elmúlt 31 napra vonatkozóan.|  
|**Energiagazdálkodás – környezeti hatás**|Az adott gyűjtemény által kibocsátott széndioxidot (CO2-t) mutató grafikont jelenít meg az adott időszakra vonatkozóan.|  
|**Energiagazdálkodás - napi környezeti hatás**|Az adott gyűjtemény által kibocsátott CO2-t mutató grafikont jelenít meg az elmúlt 31 napra vonatkozóan.|  
|**Energiagazdálkodás - az alvó üzemmódra képtelen számítógépek részletei**|Olyan számítógépek részletes információit jeleníti meg, amelyek nem voltak alvó vagy hibernált állapotban a megadott időszakban.|  
|**Energiagazdálkodás - az alvó üzemmódra képtelen jelentés**|Azon általános okok listáját jeleníti meg, amelyek meggátolták a számítógépek alvó vagy hibernált állapotba lépését és az adott időszakban az egyes okok által befolyásolt számítógépek számát.|  
|**Energiagazdálkodás - energiaellátási lehetőségek**|A megadott gyűjteményben lévő számítógépek energiagazdálkodási lehetőségeit jeleníti meg.|  
|**Energiagazdálkodás – energiaellátási beállítások**|A megadott gyűjteményben a számítógépek által használt energiaellátási beállítások összesített listáját jeleníti meg.|  
|**Energiagazdálkodás – energiaellátási beállítások részletei**|A megadott számítógépek kapcsolatos további információk megjelenítéséhez használt a **energiagazdálkodás - energiaellátási beállítások** jelentés.|  

### <a name="replication-traffic"></a>Replikációs forgalom  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Globális adatok Adatreplikálási forgalma Csatlakozásonként (vonaldiagram)**|A megadott csatlakozásra vonatkozóan a megadott számú napokon történt összes globális adatreplikációs forgalmat jeleníti meg.|  
|**Globális adatok Adatreplikálási forgalma Csatlakozásonként (kördiagram)**|A megadott csatlakozásra vonatkozóan a megadott számú napokon történt összes globális adatreplikációs forgalmat jeleníti meg.|  
|**Hierarchia Csatlakozásonkénti replikálási forgalma**|A hierarchiában lévő csatlakozások esetében a megadott számú napokon történt összes replikációs forgalmat jeleníti meg.|  
|**Hierarchia első 10 replikációs csoportjának forgalma Csatlakozásonként (kördiagram)**|A csatlakozás által azonosított teljes hierarchiában lévő első tíz replikációs csoport replikációs forgalmát jeleníti meg.|  
|**Hivatkozásreplikálás forgalma**|Az összes adat a megadott számú napokon történt összes replikációs forgalmát jeleníti meg.|  
|**Replikációs csoport forgalma csatlakozásonként**|A megadott számú napokon a megadott adatbázis-replikációs csatlakozáson keresztüli hálózati forgalmat jeleníti meg a replikációs csoportra vonatkozóan.|  
|**Csatlakozásonként hely-replikációs forgalom (vonaldiagram)**|A megadott csatlakozás esetében a megadott számú napokon történt teljes helyi adatreplikációs forgalmat jeleníti meg.|  
|**Csatlakozásonként hely-replikációs forgalom (kördiagram)**|A megadott csatlakozás esetében a megadott számú napokon történt teljes helyi adatreplikációs forgalmat jeleníti meg.|  
|**A teljes hierarchia replikálási forgalma (vonaldiagram)**|A megadott számú napokon az összes csatlakozás minden irányának összesített hierarchiabeli globális és helyi adatreplikációját jeleníti meg.|  
|**A teljes hierarchia replikálási forgalma (kördiagram)**|A megadott számú napokon az összes csatlakozás minden irányának összesített hierarchiabeli globális és helyi adatreplikációját jeleníti meg.|  

### <a name="site---client-information"></a>Hely – ügyfél-információ  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Ügyfél-hozzárendelés részletes állapotjelentése**|Az ügyfél-hozzárendelés állapotának részletes információit jeleníti meg.|  
|**Ügyfél-hozzárendelési hiba részletei**|Az ügyfél-hozzárendelési hibák részletes információit jeleníti meg.|  
|**Ügyfél-hozzárendelés állapotrészletei**|Az ügyfél-hozzárendelés állapotának áttekintő információit jeleníti meg.|  
|**Sikeres ügyfél-hozzárendelés részletei**|A sikeresen hozzárendelt ügyfelek részletes információit jeleníti meg.|  
|**Ügyfél-központitelepítési hiba jelentése**|A sikertelenül telepített ügyfelek részletes információit jeleníti meg.|  
|**Ügyfél központi telepítési állapotának részletei**|Az ügyféltelepítések állapotának összegző információit jeleníti meg.|  
|**Ügyfél-központitelepítési jelentés**|A sikeresen telepített ügyfelek részletes információit jeleníti meg.|  
|**HTTPS-kommunikációra nem alkalmas ügyfelek**|A helyen lévő olyan ügyfelek részletes információit jeleníti meg, amelyek a HTTPS Communication Readiness Tool eszközt futtatták és a jelentések szerint nem tudnak kommunikálni HTTPS-en keresztül.|  
|**Rendelt de nem egy adott helyhez telepített számítógépek**|Megjeleníti azon számítógépek listáját, amelyek adott helyhez vannak rendelve, de nem jelentenek azon hely számára.|  
|**A Configuration Manager ügyfélszoftver egyedi verzióját rendelkező számítógépek**|A Configuration Manager ügyfélszoftver adott verzióját futtató számítógépek listáját jeleníti meg.|  
|**Ügyfelek száma és a kommunikációhoz használt protokoll**|Az ügyfelek által használt kommunikációs módszerek összegzését jeleníti meg (HTTP vagy HTTPS).|  
|**Társított és telepített minden egyes hely esetében az ügyfelek száma**|Az egyes helyekhez társított és telepített számítógépek számát jeleníti meg. A több hellyel társított hálózati hellyel rendelkező ügyfelek csak akkor számítanak telepítettnek, ha jelentenek a hely számára.|  
|**HTTPS-kommunikációra alkalmas ügyfelek száma**|A helyen lévő olyan ügyfelek részletes információit jeleníti meg, amelyek a HTTPS Communication Readiness Tool eszközt futtatták és a jelentések szerint tudnak vagy nem tudnak kommunikálni HTTPS-en keresztül.|  
|**A helyekhez tartozó ügyfelek száma**|Helykóddal telepített Configuration Manager-ügyfelek számát jeleníti meg.|  
|**Ügyfél-verziónkénti száma a Configuration Manager-ügyfelek**|A Configuration Manager ügyfélverzió által észlelt számítógépek számát jeleníti meg.|  
|**Egy adott gyűjtemény tartalék állapotkezelő pontja számára jelentett problémák részletei**|Adott gyűjteményben lévő ügyfelek által jelentett problémák részletes információit jeleníti meg, ha tartalék állapotkezelő pont van hozzájuk rendelve.|  
|**Az adott hely tartalék állapotkezelő pontja számára jelentett problémák részletei**|Adott helyen lévő ügyfelek által jelentett problémák részletes információit jeleníti meg, ha tartalék állapotkezelő pont van hozzájuk rendelve.|  
|**A tartalék állapotkezelő pont számára jelentett problémák összegzése**|Az ügyfelek által jelentett összes probléma részletes információit jeleníti meg, ha tartalék állapotkezelő pont van hozzájuk rendelve.|  
|**Egy adott gyűjtemény tartalék állapotkezelő pontja számára jelentett problémák összegzése**|Adott gyűjteményben lévő ügyfelek által jelentett problémák összegző információit jeleníti meg, ha tartalék állapotkezelő pont van hozzájuk rendelve.|  

### <a name="site---discovery-and-inventory-information"></a>Hely – felderítési- és Kiszolgálóleltárral kapcsolatos információk  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Ügyfelek, amelyek nem jelentettek nemrég (a megadott számú nap óta)**|A felderítési adatokat, hardverleltárat vagy szoftverleltárat a megadott számú napok során nem jelentett ügyfelek listáját jeleníti meg.|  
|**Adott hely által felderített számítógépek**|Adott hely által felderített számítógépek listáját és a legutóbbi felderítés dátumát jeleníti meg.|  
|**Közelmúltban felderített számítógépek felderítési eljárás alapján**|A megadott számú napok során felderített számítógépek listáját és az azokat felderítő ügynököket jeleníti meg. Egy számítógép többször is megjelenhet a listában, ha több ügynök is felderítette azt.|  
|**Nemrég (a megadott számú nap óta) nem felderített számítógépek**|Az utóbbi időben nem felderített számítógépek listáját és a felderítésük óta eltelt napok számát jeleníti meg.|  
|**Számítógépek amelyeknek nem történt mostanában (megadott számú nap óta)**|A közelmúltban nem leltárazott számítógépek listáját és a leltározásuk utolsó időpontját jeleníti meg.|  
|**Előfordulhat, hogy az azonos egyedi Configuration Manager-azonosítót használó számítógépek**|Megjeleníti azon számítógépek listáját, amelyek neve módosult. Név egyik lehetséges oka az, hogy a számítógép megosztja a Configuration Manager egyedi azonosítóját egy másik számítógépen.|  
|**Azonos MAC-címmel rendelkező számítógépek**|A MAC-címen osztozó számítógépeket jeleníti meg.|  
|**Az erőforrás-tartományban vagy munkacsoportban található számítógépek száma**|Az erőforrás-tartományokban vagy munkacsoportokban lévő számítógépek számát jeleníti meg.|  
|**Egy adott számítógép felderítési adatai**|Az adott számítógépet felderítő ügynökök és helyek listáját jeleníti meg.|  
|**Megadott számítógép leltározási dátumai**|A megadott számítógépen legutóbb futtatott leltár dátumát és időpontját jeleníti meg.|  

### <a name="site---general"></a>Hely – Általános  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy megadott hely számítógépei**|Adott helyen található ügyfélszámítógépek listáját jeleníti meg.|  
|**Hely állapota a hierarchiában**|A hierarchiában lévő helyek listáját és a helyállapot-információkat jeleníti meg.|  
|**A hierarchián belüli Configuration Manager-frissítés állapota**|A Configuration Manager hely frissítése a hierarchiában információit jeleníti meg.|  

### <a name="site---server-information"></a>Hely – Kiszolgálóinformáció  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Helyrendszer-szerepkörök és a megadott hely helyrendszer-kiszolgálók**|Az adott hely helyrendszer-kiszolgálóit és azok helyrendszer-szerepkörei listáját jeleníti meg.|  

### <a name="software---companies-and-products"></a>Szoftver – vállalatok és termékek  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott szoftvercég leltározott termékei**|Adott szoftvercégtől származó leltárazott szoftvertermékek és verziók listáját jeleníti meg.|  
|**Összes szoftvervállalat neve**|A leltárazott szoftvereket gyártó összes vállalat listáját jeleníti meg.|  
|**Minden Windows-alkalmazás**|A telepített Windows-alkalmazások összegzését jeleníti meg a példányok száma alapján rendezve az alkalmazásnév, architektúra vagy kiadó keresési feltétel alapján.|  
|**Megadott termékkel rendelkező számítógépek**|Azon számítógépek listáját jeleníti meg, amelyeken a megadott termék leltárazva van, valamint a termék verzióit.|  
|**Adott terméknévvel és verzióval rendelkező számítógépek**|Azon számítógépek listáját jeleníti meg, amelyeken a megadott termékverzió leltárazva van.|  
|**A Programok telepítése/törlése lehetőséggel regisztrált megadott szoftverrel rendelkező számítógépek**|A Programok telepítése és törlése vagy a Programok és szolgáltatások eszközben regisztrált megadott szoftverrel rendelkező összes számítógép összegzését jeleníti meg.|  
|**Az összes leltározott szoftvertermék és verzió száma**|A leltárazott szoftvertermékek és -verziók listáját jeleníti meg, valamint az azokat futtató számítógépek számát.|  
|**Leltározott termékei és termék verziója**|Az adott termék leltárazott verzióinak listáját jeleníti meg, valamint az azokat futtató számítógépek számát.|  
|**A Programok telepítése és törlése regisztrált szoftver példányainak száma**|Az adott gyűjteményben lévő számítógépeken telepített, és a Programok telepítése és törlése lehetőséggel vagy a Programok és szolgáltatások lehetőséggel regisztrált szoftverek összes példányának összegzését jeleníti meg.|  
|**A Programok telepítése és törlése regisztrált szoftver példányainak száma**|A telepített és a Programok telepítése és törlése vagy a Programok és szolgáltatások segítségével regisztrált megadott szoftvercsomagok példányszámát jeleníti meg.|  
|**Megadott Windows-alkalmazások telepítései**|Ez a jelentés az adott Windows-alkalmazást futtató összes számítógépet listázza|  
|**Egy adott számítógépen található termékek**|Az adott számítógépen leltárazott szoftvertermékek és azok gyártóinak összegzését jeleníti meg.|  
|**Egy adott számítógépen a Programok telepítése/törlése regisztrált szoftver**|Az adott számítógépen telepített és a Programok telepítése és törlése vagy a Programok és szolgáltatások lehetőséggel regisztrált szoftver összegzését jeleníti meg.|  
|**A megadott felhasználó számára telepített Windows-alkalmazások**|A megadott felhasználó számára telepített összes Windows-alkalmazást jeleníti meg|  

### <a name="software---files"></a>Szoftver – Fájlok  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A termék összes leltározott fájlok**|Az adott szoftvertermékhez társított leltárazott fájlok összegzését jeleníti meg.|  
|**Egy adott számítógép összes leltározott fájlok**|Az adott számítógépen leltárazott összes fájl összegzését jeleníti meg.|  
|**Szoftverleltározás két gép összehasonlítása**|Két adott számítógéphez jelentett szoftverleltárak közötti különbségeket jeleníti meg.|  
|**Megadott fájlt tartalmazó számítógépek**|Megjeleníti az adott fájlnévhez szoftverleltárt gyűjtő számítógépek listáját. Egy számítógép többször is megjelenhet a listában, ha a fájl több másolatát tartalmazza.|  
|**Megadott fájlnévvel rendelkező számítógépek száma**|Megjeleníti az adott fájlhoz szoftverleltárt gyűjtő számítógépek számát.|  

### <a name="software-distribution---application-monitoring"></a>Szoftverterjesztés – Alkalmazásfigyelés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Minden alkalmazás-KözpontiTelepítés (összetett)**|Az összes alkalmazástelepítés részletes összegző információit jeleníti meg.|  
|**Minden alkalmazás-KözpontiTelepítés (egyszerű)**|Az összes alkalmazástelepítés összegző információit jeleníti meg.|  
|**Alkalmazás megfelelősége**|A megadott gyűjteményben lévő kiválasztott alkalmazás megfelelőségi információit jeleníti meg.|  
|**Alkalmazás telepítései eszközönként**|A megadott eszközhöz vagy felhasználóhoz telepített alkalmazásokat jeleníti meg.|  
|**Alkalmazás infrastruktúrájára vonatkozó hibák**|Az alkalmazásinfrastruktúra hibáit jeleníti meg.  Ezek belső infrastruktúrahibák lehetnek, valamint érvénytelen követelményszabályokból eredő hibák.|  
|**Alkalmazás használatának részletes állapota**|A telepített alkalmazások használatának részleteit jeleníti meg.|  
|**Alkalmazás használatának összegzési állapota**|A telepített alkalmazások használatának összegzését jeleníti meg.|  
|**Feladat alkalmazást tartalmazó Feladatütemező központi telepítések**|Adott alkalmazást telepítő feladatütemező telepítéseket jelenít meg.|  
|**Android alkalmazásra vonatkozó felhasználói kérések**|Android-alkalmazás telepítését kérő felhasználókat jelenít meg.|  
|**iOS-alkalmazások sikertelen központi telepítéssel (az alkalmazás már telepítve van)**|A kijelölt, az „Alkalmazáscsomag iOS rendszerhez az App Store áruházból” beállítással telepített, és egy mobilalkalmazás-felügyeleti szabályzathoz társított iOS-alkalmazás megfelelőségi adatait jeleníti meg. Ezzel a jelentéssel azok a felhasználók és eszközök jeleníthetők meg, akik vagy amelyek esetében az alkalmazás központi telepítése nem sikerült, mert azt már manuálisan telepítette a felhasználó.|  

### <a name="software-distribution---collections"></a>Szoftverterjesztés – Gyűjtemények  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Minden gyűjtemény**|A hierarchiában lévő összes gyűjteményt megjeleníti.|  
|**Egy adott gyűjtemény összes erőforrása**|Az adott gyűjteményben található összes erőforrást megjeleníti.|  
|**Meghatározott ügyfél számára elérhet karbantartási időszak**|Az adott ügyfélre érvényes összes karbantartási időszakot megjeleníti.|  

### <a name="software-distribution---content"></a>Szoftverterjesztés – Tartalom  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Összes aktív tartalomterjesztés**|Az összes olyan terjesztési pontot megjeleníti, amelyen jelenleg tartalmat telepítenek vagy távolítanak el.|  
|**Minden tartalom**|A helyen lévő összes alkalmazást és csomagot megjeleníti.|  
|**Egy adott terjesztési pont összes tartalma**|Az adott terjesztési pontra jelenleg telepített összes tartalmat megjeleníti.|  
|**Összes terjesztési pont**|Az egyes helyek terjesztési pontjainak információit jeleníti meg.|  
|**Egy adott terjesztési pont meghatározott csomagjának összes állapotüzenete**|Az adott terjesztési ponton lévő adott csomag összes állapotüzenetét megjeleníti.|  
|**Alkalmazás tartalmának terjesztési állapota**|Az alkalmazástartalom terjesztési állapotának információit jeleníti meg.|  
|**Terjesztésipont-csoportot megcélzó alkalmazások**|Az adott terjesztésipont-csoportra telepített alkalmazástartalmak információit jeleníti meg.|  
|**Pont nem egy megadott terjesztési szinkronizált alkalmazásai**|Azon alkalmazásokat jeleníti meg, amelyek esetében a megadott terjesztésipont-csoporton nem lettek frissítve a társított tartalomfájlok a legújabb verzióra.|  
|**Terjesztésipont-csoport**|Az adott terjesztésipont-csoporthoz megadott információkat jeleníti meg.|  
|**Terjesztési pontok használatának összegzése**|Az egyes terjesztési pontok terjesztésipont-használatának összegzését jeleníti meg.|  
|**Meghatározott csomag terjesztési állapota**|Az egyes terjesztési pontokon megadott csomagtartalom terjesztési állapotát jeleníti meg.|  
|**Terjesztésipont-csoportot célzó csomagok**|Az adott terjesztésipont-csoportot célzó csomagok információit jeleníti meg.|  
|**Nem szinkronizált egy megadott terjesztési csomagok terjesztésipont-csoport**|Azon csomagokat jeleníti meg, amelyek esetében a megadott terjesztésipont-csoporton nem lettek frissítve a társított tartalomfájlok a legújabb verzióra.|  

### <a name="software-distribution---package-and-program-deployment"></a>Szoftverterjesztés – csomag és Program központi telepítése  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A megadott csomag és program összes központi telepítése**|Adott csomag és program összes központi telepítésének információit jeleníti meg.|  
|**Összes csomag és program-központitelepítése**|A helyen lévő összes csomag- és program-központitelepítést megjeleníti.|  
|**Egy gyűjtemény összes csomag- és program központitelepítése**|Az adott gyűjtemény minden csomag- és program-központitelepítését megjeleníti.|  
|**Összes csomag- és program központi telepítés az adott számítógépre**|Az adott számítógép minden csomag- és program-központitelepítését megjeleníti.|  
|**Összes csomag- és program központi telepítés egy megadott felhasználó számára**|Az adott felhasználó minden csomag- és program-központitelepítését megjeleníti.|  

### <a name="software-distribution---package-and-program-deployment-status"></a>Szoftverterjesztés – csomag és Program központi telepítési állapot  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Az összes rendszererőforrás csomag és program-központitelepítése valamint állapota**|A hely minden csomag- és program-központitelepítését megjeleníti az egyes telepítések összegző állapotával.|  
|**Meghatározott állapotú csomag- és program KözpontiTelepítés rendszererőforrásai**|Adott állapotú adott csomag- és programtelepítés erőforrásainak listáját jeleníti meg.|  
|**Diagram - központitelepítések órára lebontott csomag és program befejezési állapota**|Azon számítógépek százalékát jeleníti meg, amelyek sikeresen telepítették a csomagot a csomag- és programtelepítés létrehozása óta eltelt minden egyes órában. A csomag- és programtelepítés átlagos idejének követésére használható.|  
|**A megadott ügyfél és a központi telepítési csomag és program központi telepítési állapotát**|Adott számítógéphez és csomag- és program-központitelepítéshez jelentett állapotüzeneteket jelenít meg.|  
|**A megadott csomag és program központi telepítés állapota**|Adott csomag- és program-központitelepítés állapotösszegzését jelenít meg.|  

### <a name="software-metering"></a>Szoftverhasználat-mérés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Szoftverhasználat-mérési szabályokat, a helyre**|A helyen lévő összes szoftverhasználat-mérési szabályt megjeleníti.|  
|**Egy mért használatú program rendelkező számítógépek telepítve, de nem futtatták a programot a megadott dátum óta**|A megadott mért alkalmazást futtató összes olyan számítógépet megjeleníti a szoftverleltár jelentése alapján, amelyek nem futtatták a programot a megadott dátum óta.|  
|**Egy meghatározott mért használatú szoftvert futtató számítógépek**|A megadott hónapban és évben az adott szoftverhasználat-mérési szabálynak megfelelő programokat futtató számítógépek listáját jeleníti meg.|  
|**Az összes mért használatú szoftverek egyidejű használata**|Azon felhasználók maximális számát jeleníti meg, akik egy időben futtattak minden egyes mért szoftverprogramot a megadott hónap és év során.|  
|**Az adott mért használatú szoftver egyidejű használatra vonatkozó trendelemzés**|Azon felhasználók maximális számát jeleníti meg, akik egy időben futtatták az adott mért szoftverprogramot az elmúlt év hónapjai során.|  
|**Telepítési bázisa összes mért használatú szoftver**|Megjeleníti a szoftverleltár alapján telepített mért szoftverprogramokkal rendelkező számítógépek számát. Ehhez a jelentéshez a szoftverleltárat be kell gyűjteni a mért számítógépeken.|  
|**Szoftver-mérés összegzési folyamata**|Azon időpontot jeleníti meg, amikor a legújabb összegzett mérési adatok fel lettek dolgozva a helykiszolgálón.  A szoftverhasználat-mérési jelentésben csak az ezen dátumok előtt feldolgozott mérési adatok láthatók.|  
|**Adott mért használatú szoftver napon belüli használati összefoglaló ideje**|Adott program átlagos használatainak számát jeleníti meg az elmúlt 90 napra vonatkozóan, óra és nap szerint bontva.|  
|**Programok mért használatú szoftver teljes használata**|Azon felhasználók számát jeleníti meg, akik az egyes szoftverhasználat-mérési szabályoknak megfelelő programokat futtattak helyileg vagy a Terminálszolgáltatásokkal a megadott hónapban és évben.|  
|**A Windows terminálkiszolgálókon levő összes mért használatú szoftver programok teljes használata**|Azon felhasználók számát jeleníti meg, akik a szoftverhasználat-mérési szabályoknak megfelelő programokat futtattak a Terminálszolgáltatásokkal a megadott hónapban és évben.|  
|**Adott mért használatú szoftver teljes használati trendelemzése**|Azon felhasználók számát jeleníti meg, akik az adott szoftverhasználat-mérési szabálynak megfelelő programokat futtattak helyileg vagy a Terminálszolgáltatásokkal az elmúlt év egyes hónapjaiban.|  
|**A Windows terminálkiszolgálókon levő megadott mért szoftverprogramot teljes használati trendelemzése**|Azon felhasználók számát jeleníti meg, akik az adott szoftverhasználat-mérési szabálynak megfelelő programokat futtattak a Terminálszolgáltatásokkal az elmúlt év egyes hónapjaiban.|  
|**Egy meghatározott mért használatú szoftvert futtató felhasználók**|A megadott hónapban és évben az adott szoftverhasználat-mérési szabálynak megfelelő programokat futtató felhasználók listáját jeleníti meg.|  

### <a name="software-updates---a-compliance"></a>Szoftverfrissítések – A megfelelőség  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**1. megfelelőség – összesített megfelelőség**|A szoftverfrissítési csoport összesített megfelelőségi adatait jeleníti meg.|  
|**2. megfelelőség – meghatározott szoftverfrissítés**|Az adott szoftverfrissítés megfelelőségi adatait jeleníti meg.|  
|**3. megfelelőség – frissítési csoport (frissítések alapján)**|Egy szoftverfrissítési csoportban meghatározott szoftverfrissítések megfelelési adatait jeleníti meg.|  
|**Megfelelőség 4 - szállító frissítései hónap év**|Egy szállító által az adott hónapban és évben kiadott szoftverfrissítések megfelelőségi adatait jeleníti.|  
|**5. megfelelőség – megadott számítógép**|Ez a jelentés egy adott számítógép szoftverfrissítés-megfelelőségi adatait adja vissza.  A visszaadott információk mennyiségének korlátozásához megadhatja a szállító és a szoftverfrissítés besorolását.|  
|**Megfelelőségi 6 – meghatározott szoftverfrissítés állapotai (másodlagos)**|Az adott szoftverfrissítés különböző megfelelőségi állapotú számítógépeinek számát és százalékos arányát jeleníti meg.|  
|**7. megfelelőség – (másodlagos) szoftverfrissítési csoport számára adott megfelelőségi állapottal rendelkező számítógépek**|Egy gyűjteményben lévő összes olyan számítógépet megjeleníti, amelyek a megadott összesített megfelelőségi állapottal rendelkeznek a szoftverfrissítési csoportban.|  
|**8. megfelelőség – egy adott megfelelőségi állapottal számítógépek (másodlagos) frissítési**|Egy gyűjteményben lévő összes olyan számítógépet megjeleníti, amelyek a megadott megfelelőségi állapottal rendelkeznek a szoftverfrissítéshez.|  

### <a name="software-updates---b-deployment-management"></a>Szoftverfrissítések – B KözpontiTelepítés-felügyelet  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**1. kezelő – frissítési csoport központi telepítései**|Az adott szoftverfrissítési csoportban meghatározott összes szoftverfrissítést tartalmazó összes központi telepítést megjeleníti.|  
|**2 kezelő - a frissítések szükséges de központilag nem telepített**|Az összes olyan szállítóspecifikus szoftverfrissítést megjeleníti, amelyeket kötelezőként észleltek az ügyfeleken, de amelyek nincsenek telepítve egy megadott gyűjteménybe.|  
|**3. kezelő – a központi telepítés frissítései**|Az adott központi telepítésben lévő szoftverfrissítéseket jeleníti meg.|  
|**4. kezelő – gyűjteményt célzó központi telepítések**|Az adott gyűjteményt célzó összes szoftverfrissítés-telepítést megjeleníti.|  
|**5. kezelő – számítógépet címző központi telepítések**|Az adott számítógépre telepített összes szoftverfrissítés-telepítést megjeleníti.|  
|**6. kezelő – megadott frissítést tartalmazó központi telepítések**|Az adott szoftverfrissítést tartalmazó összes telepítést és a központi telepítéshez társított célgyűjteményt jeleníti meg.|  
|**7. kezelő – hiányos tartalmú telepítések frissíti**|Az adott telepítésben lévő azon szoftverfrissítéseket jeleníti meg, amelyekhez nincs lekérve az összes társított tartalom, így az ügyfelek nem tudják telepíteni a frissítést, és nem érik el a telepítés 100%-os megfelelőségét.|  
|**8. kezelő – hiányos tartalommal (másodlagos) rendelkező számítógépek**|A terjesztési ponton nem létesített megadott központi telepítésben szereplő adott szoftverfrissítést igénylő összes számítógépet megjeleníti.|  

### <a name="software-updates---c-deployment-states"></a>Szoftverfrissítések – C központi telepítési állapotok  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Állapotok 1 – központi telepítés kényszerítési állapotai**|Egy adott szoftverfrissítés-telepítés kényszerítési állapotát jeleníti meg, amely általában a telepítések felmérésének második fázisa.|  
|**Állapotok 2 – központi telepítés értékelési állapotai**|Egy adott szoftverfrissítés-telepítés értékelési állapotát jeleníti meg, amely általában a telepítések felmérésének első fázisa.|  
|**Állapotok 3 – központi telepítés és számítógép állapota**|Az adott számítógép megadott központi telepítésében lévő összes szoftverfrissítés állapotait megjeleníti.|  
|**Állapotok 4 – (másodlagos) központi telepítés meghatározott állapotban lévő számítógépei**|Minden olyan számítógépet megjelenít, amelyek a szoftverfrissítés központi telepítésének megadott állapotával rendelkeznek.|  
|**Állapotok 5 – (másodlagos) központi telepítés egy frissítésének állapotai**|Az adott központi telepítés által megcélzott megadott szoftverfrissítés állapotainak összegzését jeleníti meg.|  
|**Állapotok 6 – (másodlagos) frissítés számára meghatározott kényszerítési állapotú számítógépek**|Minden olyan számítógépet megjelenít, amelyek az adott szoftverfrissítés esetében a megadott kényszerítési állapottal rendelkeznek.|  

### <a name="software-updates---d-scan"></a>Szoftverfrissítések – D vizsgálat  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**1. ellenőrzés – gyűjtemény legutóbbi ellenőrzési állapota**|Az utolsó megfelelőségi vizsgálat során az ügyfelek által visszaadott megfelelőségi vizsgálati állapotú adott gyűjtemény számítógépeinek számát jeleníti meg.|  
|**2. ellenőrzés – hely utolsó állapotellenőrzése**|Az utolsó megfelelőségi vizsgálat során az ügyfelek által visszaadott megfelelőségi vizsgálati állapotú adott helyhez rendelt számítógépek számát jeleníti meg.|  
|**3. ellenőrzés – (másodlagos) meghatározott állapotot jelentő gyűjtemény ügyfelei**|Adott gyűjtemény összes számítógépét és az utolsó megfelelőségi vizsgákat során megadott megfelelőségi vizsgálati állapotot jeleníti meg.|  
|**4. ellenőrzés – a hely (másodlagos) meghatározott állapotot jelentő ügyfelei**|Adott helyhez rendelt összes számítógépet és az utolsó megfelelőségi vizsgálat során megadott megfelelőségi vizsgálati állapotot jeleníti meg.|  

### <a name="software-updates---e-troubleshooting"></a>Szoftverfrissítések – E hibaelhárítás  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Hibaelhárítás 1 - vizsgálattal kapcsolatos hibák történtek**|A helyen felmerülő vizsgálati hibákat és a hibát tapasztaló számítógépek számát jeleníti meg.|  
|**Hibaelhárítás 2 – központi telepítési hibák**|A helyen felmerülő telepítési hibákat és a hibát tapasztaló számítógépek számát jeleníti meg.|  
|**Hibaelhárítás 3 – (másodlagos) megadott ellenőrzési hiba miatt sikertelenül működő számítógépek**|Azon számítógépek listáját jeleníti meg, amelyeken a megadott hiba miatt nem feleltek meg a vizsgálaton.|  
|**Hibaelhárítás 4 – (másodlagos) egy adott központi telepítési hiba miatt sikertelenül működő számítógépek**|Azon számítógépek listáját jeleníti meg, amelyeken a frissítés telepítése a megadott hiba miatt hiúsult meg.|  

### <a name="state-migration"></a>Állapotáttelepítés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Adott forrásoldali számítógép állapotáttelepítési információi**|Az adott számítógép állapottelepítési információit jeleníti meg.|  
|**Meghatározott állapotáttelepítési pont állapotáttelepítési információi**|Az adott állapotáttelepítési pont állapottelepítési információit jeleníti meg.|  
|**Egy megadott hely állapotáttelepítési pontjai**|Az adott hely állapotáttelepítési pontjait jeleníti meg.|  

### <a name="status-messages"></a>Állapotüzenetek  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy adott üzenetek üzenet azonosítója**|Megjeleníti azon állapotüzenetek listáját, amelyek az adott üzenetazonosítóval rendelkeznek.|  
|**Egy adott helyen az utolsó 12 órában hibát jelentett ügyfelek**|Az elmúlt 12 órában hibákat jelentő számítógépek és összetevők listáját és a jelentett hibák számát jeleníti meg.|  
|**Az utolsó 12 óra összetevő-üzenetei**|Az elmúlt 12 óra összetevő-üzeneteinek listáját jeleníti meg a megadott helykódhoz, számítógéphez és összetevőhöz.|  
|**Az elmúlt egy óra állapotüzenetei**|Megjeleníti az elmúlt órában a Configuration Manager-helyen a megadott számítógép meghatározott összetevője által létrehozott állapotüzenetek listáját.|  
|**Egy adott helyen az elmúlt egy óra összetevő-üzenetek száma**|Az állapotüzenetek számát jeleníti meg összetevő és az elmúlt órában jelentett súlyosság szerint a megadott helyen.|  
|**Az utolsó 12 órában fellépő hibák száma**|Az elmúlt 12 órában előforduló kiszolgálóösszetevő-állapotüzenetek számát jeleníti meg.|  
|**Súlyos hibák (összetevő szerint)**|A súlyos hibákat jelentő számítógépek listáját jeleníti meg (összetevő szerint).|  
|**Súlyos hibák (a számítógép neve) szerint**|A súlyos hibákat jelentő számítógépek listáját jeleníti meg (számítógépnév alapján).|  
|**Utolsó 1000 üzenete (hibák és figyelmeztetések) egy adott számítógép**|Az adott számítógép utolsó 1000 hiba és figyelmeztetés típusú összetevő-állapotüzeneteinek összegzését jeleníti meg.|  
|**Utolsó 1000 üzenete (hibák figyelmeztetések és információk) egy adott számítógép**|Az adott számítógép utolsó 1000 hiba, figyelmeztetés és információs típusú összetevő-állapotüzeneteinek összegzését jeleníti meg.|  
|**Utolsó 1000 üzenete (hibák) számítógép**|Az adott számítógép utolsó 1000 hiba típusú kiszolgálóösszetevő-állapotüzeneteinek összegzését jeleníti meg.|  
|**Egy adott kiszolgáló-összetevő utolsó 1000 állapotüzenete**|Az adott kiszolgáló-összetevő utolsó 1000 állapotüzenetének összegzését jeleníti meg.|  

### <a name="status-messages---audit"></a>Állapotüzenetek – Naplózás  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Összes naplózási üzenete egy adott felhasználó**|Az adott felhasználó összes naplózási állapotüzenetének összegzését jeleníti meg. A naplózási üzenetek műveleteit tartalmazzák a Configuration Manager konzolon adja hozzá, módosítsa vagy törölje annak objektumát a Configuration Manager alkalmazásban.|  
|**Távvezérlés – megadott felhasználó által távvezérelt számítógépek**|Az ügyfélszámítógépek adott felhasználó általi távvezérlését jelző állapotüzenetek összegzését jeleníti meg.|  
|**Távvezérlés – távvezérléssel kapcsolatos összes információ**|Az ügyfélszámítógépek távvezérlésével kapcsolatos állapotüzenetek összegzését jeleníti meg.|  

### <a name="task-sequence---deployment-status"></a>Feladatütemező – központi telepítési állapota  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy feladatütemezési központi telepítés meghatározott állapotban lévő rendszererőforrásai**|Az adott telepítési állapotú megadott feladatütemezési központi telepítés célszámítógépeinek listáját jeleníti meg.|  
|**Minden olyan rendszererőforrás egy feladatütemezési központi telepítés, amely egy adott állapotú Ismeretlen számítógépek számára elérhető**|Az adott telepítési állapotú megadott feladatütemezési központi telepítés célszámítógépeinek listáját jeleníti meg.|  
|**A feladat feladatütemezési központi telepítési hozzárendeléssel rendelkező még nem futtatott rendszererőforrások száma**|Azon számítógépek számát jeleníti meg, amelyek fogadtak feladatütemezést, de nem futtatták azt.|  
|**Egy számítógép feladatütemezési központi telepítés előzményei**|Megjeleníti az adott feladatütemezési központi telepítés minden egyes lépésének állapotát a megadott célszámítógépen. Ha a rendszer nem ad vissza rekordot, a feladatütemezés még nem indult el a számítógépen.|  
|**A megadott futási idejét, hogy egy feladatütemezési központi telepítés túllépő célszámítógépek listája**|Azon célszámítógépeket jeleníti meg, amelyek meghaladták a feladatütemezés futtatásának megadott idejét.|  
|**Egy adott feladatütemezési központi telepítés meghatározott célszámítógépen futási idejét**|A teljes időt jeleníti meg, amely az adott számítógépen az adott feladatütemezés sikeres végrehajtásához szükséges volt.|  
|**Egy feladatütemezési központi telepítés egyes lépéseihez szükséges idő a célszámítógépen futtassa**|Megjeleníti az adott feladatütemezési központi telepítés minden egyes lépéséhez szükséges időt a megadott célszámítógépen.|  
|**Egy adott számítógép adott feladatütemezési központi telepítés állapota**|Adott számítógép adott feladatütemezési központi telepítésének állapotösszegzését jeleníti meg.|  
|**Egy feladatütemezési központi telepítés ismeretlen célszámítógépen állapota**|Megjeleníti az adott feladatütemezési központi telepítés állapotát a megadott ismeretlen célszámítógépen.|  
|**Egy megadott feladatütemezési központi telepítés állapotának összegzése**|A telepítés által célzott összes erőforrás állapotösszegzését jeleníti meg.|  
|**Egy megadott feladatütemezési központi telepítés Ismeretlen számítógépek számára elérhető állapot összegzése**|Az ismeretlen számítógépeket tartalmazó gyűjtemény számára elérhető adott központi telepítés által célzott összes erőforrás állapotösszegzését jeleníti meg.|  

### <a name="task-sequence---deployments"></a>Feladatütemezés – központi telepítések  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Jelenleg az egy adott csoportjában vagy fázisában levő egy megadott feladatütemezési központi telepítés rendszererőforrásai**|Az adott feladatütemezési központi telepítés adott csoportjában vagy fázisában jelenleg futó számítógépek listáját jeleníti meg.|  
|**Minden olyan rendszererőforrás, ahol egy feladatütemezési központi telepítés nem sikerült egy megadott csoportban vagy fázisban**|Az adott feladatütemezési központi telepítés megadott csoportjában/fázisában meghiúsult számítógépek listáját jeleníti meg.|  
|**A Feladatütemező összes telepítése**|A jelenlegi helyről indított összes feladatütemezési központi telepítés részleteit jeleníti meg.|  
|**A Feladatütemező összes telepítése ismeretlen számítógépek számára elérhető**|A helyről indított és az ismeretlen számítógépeket tartalmazó gyűjteményekre telepített összes feladatütemezési központi telepítés részleteit jeleníti meg.|  
|**Minden egyes fázisának vagy csoportjának feladatütemezési hibáinak száma**|Az adott feladatütemezés egyes fázisaiban vagy csoportjaiban lévő hibák számát jeleníti meg.|  
|**Minden egyes fázisának vagy csoportjának egy adott feladatütemezési központi telepítés hibáinak száma**|Az adott feladatütemezési központi telepítés egyes fázisaiban vagy csoportjaiban lévő hibák számát jeleníti meg.|  
|**Az összes feladatütemezési központi telepítések központi telepítési állapotát.**|Az összes feladatütemezési központi telepítés összesített állapotát jeleníti meg.|  
|**Feladatütemezés végrehajtási állapota**|Megjeleníti az adott feladatütemezés végrehajtási állapotát.|  
|**A futó feladatütemezés központi telepítésének végrehajtási állapota**|Megjeleníti az adott feladatütemezés központi telepítésének összegző információit.|  
|**Megadott feladatütemezés összes központi telepítésének végrehajtási állapota**|Megjeleníti az adott feladatütemezés összes központi telepítésének végrehajtási állapotát.|  
|**Egy feladatütemezési központi telepítés összegzési jelentése**|Megjeleníti az adott feladatütemezés központi telepítésének összegző információit.|  

### <a name="task-sequence---progress"></a>Feladatütemező – Folyamat  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Diagram – feladatütemezés hetekre lebontott végrehajtási állapota**|A feladatütemezés hetekre lebontott végrehajtási állapotát jeleníti meg a központi telepítés dátumától kezdve.|  
|**Egy feladatütemezés végrehajtását**|Megjeleníti az adott feladatütemezés végrehajtási állapotát.|  
|**Az összes feladatütemezés végrehajtási állapota**|Összegzést jelenít meg az összes feladatütemezés végrehajtási állapotáról.|  
|**Az operációs rendszert központilag telepítő feladatütemezés végrehajtási állapota**|Megjeleníti az operációs rendszereket központilag telepítő összes feladatütemezés végrehajtási állapotát.|  
|**Az összes ismeretlen számítógép állapota**|Azon számítógépek listáját jelenti meg, amelyek a feladatütemezés központi telepítésének futtatásakor ismeretlenek voltak, valamint azt, hogy jelenleg ismertek-e.|  

### <a name="task-sequences---references"></a>Feladatütemező – Hivatkozások  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Megadott feladatütemezés által hivatkozott tartalom**|Megjeleníti az adott feladatütemezés által hivatkozott tartalmat.|  

### <a name="upgrade-assessment"></a>Frissítés felmérése  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Egy adott számítógép**|Megjeleníti a számítógépen telepített alkalmazásoknak az adott operációs rendszerre vonatkozó kompatibilitását.|  
|**Egy megadott gyűjtemény számítógépeinek**|Megjeleníti a gyűjteményben található számítógépek általános állapotát, így az egyes számítógépek alkalmazásai alapján értékelheti az adott operációs rendszerre való frissítést. A jelentés segítségével az operációs rendszer telepítése előtt meghatározhatja, hogy melyik számítógépek rendelkeznek kompatibilis alkalmazásokkal.|  
|**Alkalmazás állapotának összegzése**|Összegzést jelenít meg az adott operációs rendszerre vonatkozó alkalmazásállapotokról. A jelentés segítségével az operációs rendszer telepítése előtt meghatározhatja az alkalmazások kompatibilitását.|  
|**A meghatározott telepített alkalmazásokkal rendelkező számítógépek**|Megjeleníti azokat a számítógépeket, amelyeken egy adott alkalmazás telepítve van.|  
|**Megadott hardvereszközzel rendelkező számítógépek**|Megjeleníti az adott hardvereszközzel rendelkező számítógépeket.|  
|**Megadott számítógép hardvereszközének állapota**|Megjeleníti az adott számítógép hardvereszközeinek az adott operációs rendszerre vonatkozó kompatibilitási állapotát.|  
|**Megadott gyűjteményen belüli számítógépek hardvereszközeinek állapota**|Megjeleníti az adott gyűjteményben található számítógépek hardvereszközeinek az adott operációs rendszerre vonatkozó általános állapotát. A jelentés segítségével az operációs rendszer telepítése előtt meghatározhatja a hardver kompatibilitását.|  
|**Hardvereszköz állapotösszegzése**|Összegzést jelenít meg az adott operációs rendszerre vonatkozó hardvereszköz-állapotról. A jelentés segítségével az operációs rendszer telepítése előtt meghatározhatja a hardvereszközök kompatibilitását.|  
|**Operációs rendszerre vonatkozó hardverkövetelmény**|Megjeleníti az operációs rendszerekre vonatkozó minimális és ajánlott hardverkövetelményeket.|  
|**Operációs rendszerre vonatkozó követelmények állapota egy megadott gyűjtemény számítógépei esetén**|Megjeleníti az adott operációs rendszerre vonatkozó követelmények állapotát egy adott gyűjtemény számítógépei esetén. A jelentés segítségével meghatározhatja, hogy az egyes számítógépek teljesítik-e az adott operációs rendszer processzorsebességre, memóriaméretre és merevlemez-területre vonatkozó követelményeit.|  
|**Frissítési felmérés összegzése**|Megjeleníti a frissítési felmérés összegzését. A jelentés segítségével felmérheti a frissítés kompatibilitásának általános állapotát.|  

### <a name="user---device-affinity"></a>Felhasználó - eszköz kapcsolat  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Függőben lévő felhasználói eszköz affinitási társításai gyűjteményenként**|Ez a jelentés megjeleníti az összes függőben lévő, használati adatokon alapuló, felhasználó és eszköz közötti kapcsolati hozzárendelést egy gyűjtemény tagjai esetén.|  
|**A felhasználói eszköz affinitási társításai gyűjteményenként**|Megjeleníti az adott gyűjteményhez tartozó összes felhasználó-eszköz társítást, és azokat gyűjteménytípus (például felhasználó vagy eszköz) szerint csoportosítja.|  

### <a name="user-data-and-profiles-health"></a>Felhasználói adatok és profilok állapota  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Mappaátirányítás állapotjelentése - részletek**|Megjeleníti a mappaátirányítási állapot részleteit egy adott felhasználóhoz tartozó minden átirányított mappa esetén.|  
|**Barangoló felhasználói profil állapotjelentése - részletek**|Megjeleníti egy adott felhasználóhoz tartozó barangoló felhasználói profil állapotának részleteit.|  
|**Felhasználói adat és Profilállapot jelentés - részletek**|Megjeleníti a mappaátirányításra vagy a barangoló felhasználói profilra vonatkozó hiba vagy figyelmeztetés részleteit az összegző jelentésből a számlálóba való lehatoláskor.|  
|**Felhasználói adat és Profilállapot jelentés - összegzés**|Megjeleníti a mappaátirányítás és a barangoló felhasználói profilok állapotának összegzését.|  

### <a name="users"></a>Felhasználók  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**A megadott felhasználónévvel rendelkező számítógépek**|Megjeleníti az adott felhasználó által használt számítógépek listáját.|  
|**Felhasználók tartományonkénti száma**|Megjeleníti az egyes tartományokban lévő felhasználók számát.|  
|**A megadott tartomány felhasználói**|Listát jelenít meg egy adott tartományban lévő felhasználókról és számítógépeikről.|  

### <a name="virtual-applications"></a>Virtuális alkalmazások  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**App-V virtuális környezetének eredményei**|Információkat jelenít meg egy adott virtuális környezetről, amely egy meghatározott állapotban van egy adott gyűjtemény esetén.|  
|**App-V virtuális környezet eredményei az eszköz**|Információkat jelenít meg egy adott virtuális környezetről egy meghatározott eszközhöz és bármely központi telepítéstípushoz az adott virtuális környezetben.|  
|**App-V virtuális környezet állapota**|Megfelelőségi információkat jelenít meg egy adott virtuális környezethez egy adott gyűjtemény esetén.|  
|**Egy adott virtuális alkalmazással rendelkező számítógépek**|Megjeleníti azon számítógépek összegzését, amelyek rendelkeznek az adott App-V alkalmazás parancsikonjával, az Application Virtualization Management Sequencer használatával történő létrehozásuk szerint.|  
|**Egy adott virtuális alkalmazási csomaggal rendelkező számítógépek**|Megjeleníti az adott App-V alkalmazáscsomaggal rendelkező számítógépek összegzését.|  
|**Virtuális alkalmazáscsomagok összes példányának száma**|Megjeleníti az észlelt App-V alkalmazáscsomagok számát.|  
|**A virtuális alkalmazások példányainak száma**|Megjeleníti az észlelt App-V alkalmazások számát.|  

### <a name="wake-on-lan"></a>Hálózati ébresztés  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Hálózati ébresztésre kijelölt számítógépek**|Megjeleníti azon számítógépek listáját, amelyek a megadott típusú központi telepítés során hálózati ébresztésre vannak kijelölve.|  
|**Összes függőben lévő ébresztési tevékenységet végző objektum**|Az ébresztésre ütemezett objektumokat jeleníti meg.|  
|**Hálózati ébresztés engedélyezett összes hely**|Megjeleníti a hierarchiában a hálózati ébresztésre engedélyezett összes hely listáját.|  
|**Hibaüzenetek érkeztek az ébresztési csomagok számára meghatározott ideig történő küldése közben**|Megjeleníti az ébresztési csomagok számítógépekre történő küldése során észlelt hibákat egy adott időszakban.|  
|**Hálózati ébresztési tevékenység előzményei**|Megjeleníti az ébresztési tevékenység egy megadott idő óta történt előzményeit.|  
|**Az ébresztési Proxy telepítési állapotának részletei**|Megjeleníti az ébresztési proxy telepítési állapotára vonatkozó információkat egy adott gyűjtemény minden eszköze esetén.|  
|**Az ébresztési Proxy telepítési állapotának összegzése**|Megjeleníti az ébresztési proxy telepítési állapotára vonatkozó összegzést egy adott gyűjtemény esetén.|  

