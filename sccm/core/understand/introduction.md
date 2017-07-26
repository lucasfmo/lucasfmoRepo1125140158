---
title: "Bevezetés |} Microsoft Docs"
description: "Alapvető információk, a System Center Configuration Manager bemutatása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3343eccf-bf09-41cd-9e68-03e893c7f904
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 916aac9a8f724e37044884cd73de5fea1f1a8f97
ms.openlocfilehash: 76f907b17df0dd2f102e34ca3cfb3ffc813c0004
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-system-center-configuration-manager"></a>A System Center Configuration Manager bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Microsoft System Center termékcsomagot megoldások a termék System Center Configuration Manager segítségével kezelheti az eszközöket és a felhasználók a helyszínen és a felhőben.  

**A Configuration Manager használatával alakítsa ki:**   
-   Informatikai termelékenységet és hatékonyságot növeléséhez a manuálisan végzett feladatok csökkentésével, és lehetővé teszi, hogy nagy értékű projektekre összpontosítson.  
-   Maximalizálja hardver- és szoftverbefektetéseit.  
-   A felhasználók termelékenységére ellenőrizniük a megfelelő szoftver megfelelő időben való biztosításával.  

**A Configuration Manager kézbesíti hatékonyabb IT szolgáltatásokat engedélyezésével nyújt segítséget:**  

-   Biztonságos és méretezhető szoftvertelepítést.  
-   Megfelelőségi beállítások kezelése.  
-   A kiszolgálókra, asztali számítógépekre, laptopokra és mobileszközökre kiterjedő átfogó eszközkezelés  

**A Configuration Manager terjeszti ki, és problémamentesen együttműködik velük a meglévő Microsoft-technológiák és -megoldások.**  

Például a Configuration Manager integrálható a:  

-   A Microsoft Intune mobileszköz-platformok számos kezeléséhez.  
-   Windows Server Update Services (WSUS) szoftverfrissítések kezeléséhez.  
-   A tanúsítványszolgáltatás.  
-   Exchange Server és az Exchange online-hoz.  
-   A Windows csoportházirend.
-   DNS.   
-   A Windows automatikus telepítési csomag (Windows ADK) és a User State Migration Tool (USMT).  
-   Windows-telepítési szolgáltatások (WDS).  
-   Távoli asztal és a Távsegítség.  

A Configuration Manager is használja:  

-   Az Active Directory tartományi szolgáltatásokat használja a biztonsági funkciókhoz, a szolgáltatáshelyek megállapításához, a konfigurációhoz, illetve a felügyelendő felhasználók és eszközök felderítéséhez.  
-   Microsoft SQL Server management elosztott Változáskezelő adatbázisként –, és jól integrálható az SQL Server Reporting Services (SSRS) szükséges a figyelő és nyomon követése felügyeleti tevékenységek jelentéseket.  
-   Helyrendszer-szerepkörök, amelyek kiterjesztése felügyeleti funkciókat, és az Internet Information Services (IIS) webes szolgáltatásait használják.
-   A háttérben futó intelligens átviteli szolgáltatást (BITS) és a BranchCache-t használja a rendelkezésre álló hálózati sávszélesség felügyeletére.  

A Configuration Manager sikeres legyen, először alaposan tervezze meg, és tesztelje a felügyeleti szolgáltatásokat, mielőtt éles környezetben a Configuration Manager. Átfogó felügyeleti alkalmazásként a Configuration Manager rendelkezzen a szervezet összes számítógépére hatással lehet a lehetséges. Amikor központi telepítése és kezelése a Configuration Manager rendszert körültekintően megtervezve és az üzleti igények figyelembevételével, a Configuration Manager csökkentheti az adminisztratív munkaterhet és a teljes birtoklási költség.  

A következő témakörök és a jelen témakör további részei segítségével a Configuration Manager alkalmazásáról további.  


**Kapcsolódó témakörök a jelen dokumentációs könyvtárban:**  

-   [Funkciók és képességek a System Center Configuration Managerben](../../core/plan-design/changes/features-and-capabilities.md)  
-   [A System Center Configuration Manager eszköz felügyeleti megoldás kiválasztása](../../core/plan-design/choose-a-device-management-solution.md)  
-   [A System Center Configuration Manager a System Center 2012 Configuration Manager változások](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)
-   [A System Center Configuration Manager alapja](../../core/understand/fundamentals.md)  
-   [System Center Configuration Manager kiértékelése saját laborkörnyezet kiépítésével](/sccm/core/get-started/set-up-your-lab)
-   [Segítség keresése a System Center Configuration Managerrel](../../core/understand/find-help.md)  
-   [Megszűnt és elavult funkciók a System Center Configuration Managerhez](../../core/plan-design/changes/removed-and-deprecated-features.md)  

##  <a name="BKMK_Console"></a> A Configuration Manager-konzol  
 A Configuration Manager telepítése után segítségével a Configuration Manager konzolon konfigurálhatja a helyeket és -ügyfeleket, és futtathatja és figyelheti a felügyeleti feladatokat. Ez a konzol az adminisztráció központi felülete, amely több hely felügyeletét teszi lehetővé.  

 A konzol segítségével másodlagos konzolokat is futtathat, amelyek segítségével speciális ügyfél-felügyeleti műveletek végezhetők. Ezek közé tartoznak az alábbiak:  

-   **Erőforrás-kezelő**: a hardver- és szoftverleltár adatainak megtekintésére szolgál.  
-   **Távvezérlés**: távoli csatlakozás az ügyfélszámítógépekhez hibaelhárítási műveletek végrehajtása céljából.  

A Configuration Manager konzol telepítése további számítógépekre, és korlátozza a hozzáférést, és korlátozza a rendszergazda felhasználók csoportszűrést a konzolon a Configuration Manager szerepköralapú felügyelet használatával.  

További információ: [System Center Configuration Manager konzolok telepítése](../../core/servers/deploy/install/install-consoles.md).

##  <a name="BKMK_ApplicationCatalog"></a> Az alkalmazáskatalógus, a Szoftverközpont és a vállalati portál  
 Az **alkalmazáskatalógus** egy olyan webhely, ahol a felhasználók szoftvereket kereshetnek és kérhetnek Windows-alapú számítógépükre. Az alkalmazáskatalógus használatához telepítenie kell az alkalmazáskatalógus webszolgáltatási és webhelyelérési pontját.  

 **A Szoftverközpont** olyan alkalmazás, amely telepítve van, ha a Configuration Manager-ügyfél telepítve van a Windows-alapú számítógépeken. Felhasználók igényelhetik és felügyelhetik a szoftvereket, amelyeket a Configuration Manager telepíti őket az alkalmazást futtatva. A Szoftverközponttal a következő műveleteket végezhetik el a felhasználók:  

-   Tallózással keresse meg és a szoftver telepítése az alkalmazáskatalógusból.  
-   A szoftverigénylési előzményeik megtekintése.  
-   Konfigurálja, ha a Configuration Manager mikor telepíthet szoftvereket az eszközeikre.  
-   Távvezérlés hozzáférési beállításainak konfigurálása, ha egy rendszergazda felhasználó engedélyezte a távvezérlést.  

**A vállalati portál** egy alkalmazás vagy webhely, amely hasonló funkciókat biztosít az Alkalmazáskatalógus, a Microsoft Intune által beléptetett mobileszközök.  

További információkért lásd: [Ismerkedés a System Center Configuration Manager alkalmazáskezelési műveleteibe](../../apps/understand/introduction-to-application-management.md).  

###  <a name="BKMK_Client"></a>A Configuration Manager tulajdonságai (Windows rendszerű számítógépek)  
 A Configuration Manager-ügyfél telepítésekor a Windows rendszerű számítógépekre a Configuration Manager telepítve van, a Vezérlőpulton. Általában nem kell konfigurálnia ezt az alkalmazást, mert az ügyfél-konfigurációt a Configuration Manager konzolon történik. Az alkalmazás segítségével a rendszergazda felhasználók és a támogatási szolgálat munkatársai hibaelhárítási műveleteket végezhetnek egyedi ügyfeleken.  

 További információk az ügyféltelepítésről: [Ügyfél-telepítési módszerek a System Center Configuration Managerben](../../core/clients/deploy/plan/client-installation-methods.md).  

##  <a name="BKMK_ExampleScenarios"></a> Példaforgatókönyvek a Configuration Managerhez  
 Az alábbi példaforgatókönyvek bemutatják, hogyan a Trey Research nevű vállalat használ a felhasználók számára a System Center Configuration Manager:  

-   Hatékonyabb legyen.  
-   Megfelelőségének egységes kezelése az eszközök korszerűbb felügyeleti élmény.
-   Eszközfelügyeletnek köszönhetően az informatikai működési költségek csökkentése érdekében.  

Mindegyik forgatókönyvben Ádám fő rendszergazdája a Configuration Manager.  

###  <a name="BKMK_ScenarioEmpower"></a>Példa: Felhasználók hatékony munkájának támogatása való elérhetőségének biztosításával alkalmazások bármely eszközről  
 A Trey Research győződjön meg arról, hogy az alkalmazottak hozzáférhetnek az alkalmazásokhoz szükséges, lehető leghatékonyabb módon. Ádám ezeket a vállalati követelményeket a következő esetekhez rendeli hozzá:  

|Követelmény|Jelenlegi ügyfél-felügyeleti állapot|Jövőbeli ügyfél-felügyeleti állapot|  
|-----------------|-------------------------------------|------------------------------------|  
|Az új alkalmazottak az első munkanapjuktól fogva hatékonyan dolgozhatnak.|Amikor az alkalmazottak a vállalathoz, azok kell várniuk az alkalmazások telepítését követően azok először bejelentkezik.|Amikor az alkalmazottak a vállalathoz, bejelentkeznek, és az alkalmazások telepítve és használatra kész.|  
|Az alkalmazottak gyorsan és egyszerűen igényelhetnek további szükséges szoftvereket.|Ha az alkalmazottaknak további alkalmazásokat, azok a fájl a támogatási szolgálat igénylést. Majd akkor általában két napot várni az igénylés feldolgozására és az alkalmazások telepítését.|Ha az alkalmazottaknak további alkalmazásokat, egy webhelyről igényelhetik őket. Azonnal települnek, ha nincsenek licencelési korlátozások. Licencelési korlátozások esetén a felhasználóknak jóváhagyást kell kérniük az alkalmazás telepítéséhez.<br /><br /> A webhely felhasználók csak azokat az alkalmazásokat tartalmazza, amelyeket telepíthetnek azok van.|  
|Az alkalmazottak munka céljára használhatják a mobileszközeiket, ha az eszközök megfelelnek a folyamatosan figyelemmel kísért és érvényesített biztonsági házirendeknek.<br /><br /> Ezek a házirendek kényszerítése egy erős jelszót, az eszközök zárolása meghatározott tétlen időszak után, és távolról törölhesse az elveszett vagy ellopott eszközök közé tartozik.|Az alkalmazottak kapcsolódnak a mobileszközök Exchange Server e-mail szolgáltatáshoz. De korlátozottak a jelentési lehetőségek annak ellenőrzésére, hogy vannak-e felelnek meg az alapértelmezett Exchange ActiveSync postaláda-házirendek biztonsági házirendjeinek. Fennáll annak a veszélye, hogy le kell tiltani a mobileszközök személyes használatát, amennyiben az IT nem tudja megerősíteni a megfelelést a házirendeknek.|Az IT-szervezet jelentést tud készíteni a mobileszközök előírt biztonsági beállításoknak való megfelelőségéről. Az ily módon nyert megerősítés lehetővé teszi, hogy a felhasználók továbbra is használhassák a mobileszközüket munka céljára. Felhasználók távolról törölhetik a mobileszköze Ha elveszett vagy ellopták, és a támogatási szolgálat törölni tudja az adatokat, amelyek az elvártnak megfelelően mobileszköz bármely felhasználó elveszett vagy ellopták.<br /><br /> A mobileszközökhöz PKI-környezetben való beléptetés biztosítható a még szélesebb körű biztonság és szabályozhatóság érdekében.|  
|Az alkalmazottak produktív munkavégzést akkor is, ha azok még nem az asztaluknál.|Amikor az alkalmazottak nincsenek az asztaluknál, és nem rendelkezik a hordozható számítógépek, a teljes képernyős számítógépen, amelyek a vállalatnál nem érhetik el alkalmazásokat.|A munkatársak számítógép-állomásokon (kioszkokon) is hozzáférhetnek alkalmazásaikhoz és adataikhoz.|  
|A folyamatos üzletmenet általában elsőbbséget élvez a szükséges alkalmazások és szoftverfrissítések telepítésével szemben.|A szükséges alkalmazások és szoftverfrissítések telepítése nappal történik, ami gyakran megzavarja a felhasználók munkáját, mivel számítógépük lelassul vagy újraindul a telepítés során.|A felhasználók beállíthatják megakadályozhatja, hogy a szükséges szoftver a számítógépre, miközben a számítógép használatát munkaidőben.|  

 A követelmények teljesítéséhez Ádám ezeket a Configuration Manager felügyeleti lehetőségeit és konfigurációs beállításait:  

-   Alkalmazáskezelés  
-   Mobil eszközök felügyelete  

Alkalmazza ezeket a konfigurációs lépések segítségével a következő táblázatban:  

|Konfigurációs lépés|Eredmény|  
|-------------------------|-------------|  
|Ádám ellenőrzi, hogy az új felhasználók Active Directory felhasználói fiókkal rendelkeznek, és létrehoz egy új lekérdezés alapú gyűjtemények a Configuration Manager ezen felhasználók. Ezt követően felhasználó-eszköz kapcsolatot határoz meg a felhasználókhoz egy olyan fájl létrehozásával, amely az egyes fiókokat a felhasználók által használt elsődleges számítógéphez rendeli, majd ezt a fájlt importálja a Configuration Manager rendszerbe.<br /><br /> Az alkalmazások, amelyeknek az új felhasználók kell a Configuration Manager már létre vannak hozva. Telepíti az alkalmazásokat, amelyek célja az új felhasználókat tartalmazó gyűjteményt kell majd.|A felhasználó-eszköz kapcsolat információkat, mert az alkalmazások egyes felhasználók elsődleges számítógép vagy számítógépek előtt telepített a felhasználó bejelentkezik.<br /><br /> Az alkalmazások készen áll, amint a felhasználó bejelentkezésekor sikeresen használja.|  
|Ádám telepíti és konfigurálja az alkalmazáskatalógus helyrendszerszerepköreit, hogy a felhasználók tallózhassanak a telepíthető alkalmazások között. „Elérhető” állapotú alkalmazástelepítéseket hoz létre, majd az új felhasználókat tartalmazó gyűjteménybe telepíti az alkalmazásokat.<br /><br /> A korlátozott számú licenccel rendelkező alkalmazásokat úgy konfigurálja, hogy a telepítésükhöz jóváhagyásra legyen szükség.|Felhasználók most már használhatja az Alkalmazáskatalógus van engedélyezve a telepítendő alkalmazások tallózásához. Csak akkor az alkalmazás telepítése azonnal, vagy jóváhagyás-igénylést, és térjen vissza az alkalmazáskatalógushoz, hogy telepítse őket, miután a támogatási szolgálat jóváhagyta kérelmüket.|  
|ADAM létrehoz egy Exchange Server-összekötőt a Configuration Manager kezelje a vállalat a helyszíni Exchange Serverhez csatlakozó mobileszközöket. Ez az összekötő egy erős jelszót állíthat be, és adott ideig tartó tétlenség után zárolják a mobileszközt időben történő biztonsági beállításokkal konfigurálja azokat.<br /><br /> Windows Phone 8, Windows RT és iOS rendszerű eszközök felügyeletéhez Ádám egy Microsoft Intune-előfizetést. Ezt követően a szolgáltatási kapcsolódási pont helyrendszerszerepkörének telepít. Ezzel a mobileszköz-felügyeleti megoldással a vállalat szélesebb körű funkcionalitást vehet igénybe az ilyen eszközök támogatására, Ez magában foglalja, amellyel az alkalmazások a felhasználók ezeket az eszközöket és számos különböző beállítást meghatározhat telepíthető. Emellett a mobileszköz-kapcsolatok biztonságáról automatikusan létrehozott és az Intune által telepített PKI-tanúsítványok segítségével.<br /><br /> A szolgáltatáskapcsolódási pont és az előfizetés használja a Configuration Manager konfigurálása után az Ádám e-mailt küld a felhasználókat, akik a mobileszközök tulajdonosainak egy hivatkozással, amellyel elindíthatják a beléptetési folyamatot.<br /><br /> Be kell léptetni a Microsoft Intune-nal a mobileszközök megfelelőségi beállításokat alkalmaz a mobileszközök biztonsági beállításainak konfigurálása. Ezek a beállítások tartalmazzák a követelmény egy erős jelszót, és adott ideig tartó tétlenség után zárolják a mobileszközt.|Ezzel a két mobileszköz-felügyeleti megoldással az IT-szervezet jelentéskészítésre alkalmas információt biztosíthat a vállalati hálózaton használt mobileszközökről és a konfigurált biztonsági beállításoknak való megfelelőségükről.<br /><br /> A felhasználóknak távolról törölhetik az Alkalmazáskatalógusból vagy a vállalati portál használatával, ha mobil eszközüket, netán ellopnák hogyan megjelenik. A támogatási szolgálat egyben arra utasítást, hogyan törölhetik távolról a felhasználók mobileszközeit a Configuration Manager konzol használatával.<br /><br /> Ezenkívül a Microsoft Intune által beléptetett mobileszközök kezeléséhez Ádám emellett már telepíthető alkalmazásokat biztosíthat a felhasználók telepíthetik, több leltáradatot gyűjthet az eszközökről, és rendelkezik ezeknek az eszközöknek hatékonyabban felügyelheti őket több beállítással.|  
|A Trey Research számos kioszkszámítógéppel rendelkezik, amelyet az irodába látogató munkatársak használhatnak. Az alkalmazottak szeretnék, ahol bejelentkeznek az rendelkezésükre áll. Azonban Adam nem szeretné helyileg telepíteni az alkalmazásokat minden olyan számítógépen.<br /><br /> ezért létrehozza a szükséges alkalmazásokat, amelyek kétféle telepítési típussal rendelkezhetnek:<br /><br /> **Az első:** Egy teljes helyi telepítése – az alkalmazás egy követelményt, hogy csak telepíthető-e a felhasználó elsődleges eszközén.<br /><br /> **A második:** A követelmény, hogy nem kell telepítenie a felhasználó elsődleges eszközén az alkalmazás virtuális verziója.|Az alkalmazottak jelentkezzen be a teljes képernyős számítógépre meglátogatásakor akkor jelenik meg a szükséges alkalmazások, az asztalon látható ikonok jelennek meg. Az alkalmazás futtatásakor virtuális alkalmazásként továbbítja adatfolyamként. Ezzel a módszerrel azok éppolyan hatékonyan, mintha csak azok az asztali ülne.|  
|ADAM lehetővé teszi a felhasználók tudják, hogy azok konfigurálhatja a munkaidejüket a Szoftverközpontban, és kiválaszthatja a miként tilthatják szoftvertelepítési műveleteket ebben az időszakban, és a számítógép bemutató üzemmódban van.|Mivel a felhasználók szabályozhatják, amikor a Configuration Manager telepítse a szoftvereket a számítógépükre, így hatékonyabb munkaidejük folyamán.|  

 Ezekkel a konfigurációs lépésekkel és eredményekkel a Trey Research sikeresen elláthatja munkatársait a szükséges alkalmazásokkal, amelyekhez így bármely eszközről hozzáférhetnek.  

###  <a name="BKMK_ScenarioUnify"></a>Példa: Egységesíti az eszközök megfelelőségének felügyeletét  
 A Trey Research olyan egységesített ügyfél-felügyeleti megoldást igényel, amely gondoskodik a vállalati számítógépeken futó vírusvédelmi szoftverek automatikus frissítéséről – tehát olyat, amelyben:  

-   A Windows tűzfal engedélyezve van.  
-   Kritikus szoftverfrissítések telepítve vannak.  
-   Meghatározott beállításkulcsokról vannak beállítva.  
-   Kezelt mobileszközök nem lehet telepíteni vagy futtathatnak aláíratlan alkalmazásokat.  

A vállalat emellett szeretné kiterjeszteni a védelmet az internetre is, az intranetről az internetre váltó laptopok felügyelete érdekében.  

Ádám ezeket a vállalati követelményeket a következő esetekhez rendeli hozzá:  

|Követelmény|Jelenlegi ügyfél-felügyeleti állapot|Jövőbeli ügyfél-felügyeleti állapot|  
|-----------------|-------------------------------------|------------------------------------|  
|Minden számítógép naprakész definíciós fájlokkal rendelkező vírusvédelmi szoftvert futtat, aktív Windows tűzfallal.|A különböző számítógépeken különböző vírusvédelmi megoldások, amelyek nem mindig naprakészek futnak. Bár a Windows tűzfal alapértelmezés szerint engedélyezve van, a felhasználók időnként letiltják azt.<br /><br /> A felhasználóknak a támogatási szolgálathoz kell fordulniuk, ha kártékony programot észlelnek számítógépükön.|Minden számítógépen ugyanaz a kártevővédelmi megoldás fut, amely automatikusan letölti a legújabb definíciófrissítő fájlokat, és automatikusan újraaktiválja a Windows tűzfalat, ha a felhasználó letiltotta.<br /><br /> A támogatási szolgálat e-mailben automatikus értesítést kap arról, ha a rendszer kártevőt észlel.|  
|A kritikus szoftverfrissítéseket minden számítógép a megjelenést követő egy hónapon belül telepíti.|Bár a számítógépekre telepített szoftverfrissítéseket, sok számítógép automatikusan csak a két-három hónappal követően azok még ne telepítse. Mindeddig ezek a számítógépek védtelenek maradnak a támadásokkal szemben.<br /><br /> A számítógépek, amelyek nem telepítik a kritikus szoftverfrissítéseket, a támogatási szolgálat először e-mail üzenetet küld kérni a felhasználókat a frissítések telepítéséhez. A továbbra is nem megfelelő számítógépeken az informatikusok távolról csatlakozva manuálisan telepíthetik a hiányzó szoftverfrissítéseket.|Az adott hónapban az aktuális megfelelőségi arány növelése 95 % e-mailek elküldése nélkül, vagy a támogatási szolgálat általi manuális telepítés nélkül.|  
|Biztonsági beállítások adott alkalmazásokra vonatkozó rendszeresen be van jelölve, és szükség esetén javítva.|A számítógépek indításakor futtatott bonyolult parancsfájlok a számítógép csoporttagságai alapján visszaállítják a megfelelő alkalmazások beállításkulcsait.<br /><br /> Mivel ezek a parancsfájlok csak indításkor futnak, és egyes számítógépeken a napig maradnak, a támogatási szolgálat a kellő rendszerességgel konfigurációs eltéréseket nem lehet ellenőrizni.|A rendszer ellenőrzi és automatikusan javítja a beállításkulcsokat, a számítógép csoporttagságaitól függetlenül és újraindítása nélkül.|  
|Mobileszközök nem telepíthetnek vagy futtathatnak nem biztonságos alkalmazásokat.|Felhasználó felkérést kap, nem a letöltése és futtatása nem biztonságos alkalmazásokat az internetről. Azonban nem szabályozza, hogy felügyelik vagy érvényesítik.|Microsoft Intune vagy a Configuration Manager automatikusan kezelt mobil eszközök megakadályozzák az aláírás nélküli alkalmazások telepítését és futtatását.|  
|Fenn kell tartani az intranetről az internetre váltó laptopok biztonságát.|Az utazó felhasználók gyakran nem kapcsolódnak naponta a VPN-kapcsolaton keresztül. A laptopok, nem megfelelő biztonsági követelmények válnak.|A laptopok biztonsági megfelelőségének fenntartásához csupán internetkapcsolat szükséges. Felhasználó nem rendelkezik a bejelentkezéshez vagy a VPN-kapcsolat használata.|  

 A követelmények teljesítéséhez Ádám ezeket a Configuration Manager felügyeleti lehetőségeit és konfigurációs beállításait:  

-   Endpoint Protection  
-   Szoftverfrissítések  
-   Megfelelőségi beállítások  
-   Mobil eszközök felügyelete  
-   Internetalapú ügyfélkezelés  

Alkalmazza ezeket a konfigurációs lépések segítségével a következő táblázatban:  

|Konfigurációs lépés|Eredmény|  
|-------------------------|-------------|  
|Ádám konfigurálja az Endpoint Protection. Ezután lehetővé teszi, hogy a más kártevővédelmi megoldások eltávolítására ügyfélbeállítást, és lehetővé teszi, hogy a Windows tűzfal. Automatikus központi telepítési szabályokat konfigurál, hogy a számítógépek rendszeresen ellenőrizzék és telepítsék a legújabb definíciófrissítéseket.|A kártevőirtó megoldás önmagában minimális felügyeleti terhek mellett gondoskodik az összes számítógép védelméről. A támogatási szolgálat értesítést automatikusan e-mailt kap, ha észlelt kártevőkről, mert a problémák gyorsan megoldhatók. és megakadályozhatók a számítógépekre irányuló támadások.|  
|A megfelelőségi arány növelése érdekében Ádám automatikus központi telepítési szabályokat használ, karbantartási időszakokat definiál a kiszolgálók és pedig megvizsgálja a előnyeit és hátrányait a hibernált számítógépekhez helyi hálózati ébresztés használata.|A kritikus szoftverfrissítések szempontjából szélesebb körű megfelelőség érhető el, a felhasználóknak és a támogatási szolgálatnak pedig kevesebb szoftverfrissítést kell manuálisan telepítenie.|  
|Ádám megfelelőségi beállításokkal ellenőrzi a meghatározott alkalmazások jelenlétét. Amikor a rendszer észleli az alkalmazásokat, konfigurációs elemek ellenőrizze a beállításkulcs-értékeket, és automatikusan javítja őket, ha nem megfelelő.|A konfigurációs elemeket és referenciakonfigurációkat, minden számítógépe és minden nap megfelelőség ellenőrzése telepített, már nincs szüksége a különálló parancsfájlok a csoporttagságot és a számítógép újraindítása.|  
|Ádám a beléptetett mobileszközök megfelelőségi beállításait használja, és az Exchange Server-összekötő konfigurálásával megakadályozza a nem aláírt alkalmazások telepítését és futtatását mobileszközökön.|Aláíratlan alkalmazások tiltott, mert mobil eszközök automatikus védelmet potenciálisan káros alkalmazásokkal szemben.|  
|Ádám ellenőrzi, hogy a helyrendszer-kiszolgálók és számítógépek rendelkeznek a PKI-tanúsítványokat, amelyek a Configuration Manager megköveteli a HTTPS-kapcsolatoknál. Majd további helyrendszerszerepköröket telepít a peremhálózaton, amelyek fogadják az internetről érkező ügyfélkapcsolatokat.|A Configuration Manager automatikusan folytatja az intranetről az internetre váltó számítógépek felügyeletét, amíg azok internetkapcsolattal rendelkeznek. Ezek a számítógépek ne hagyatkozzon felhasználók jelentkezzen be a számítógépre, vagy a VPN-kapcsolathoz való kapcsolódás.<br /><br /> A rendszer továbbra is felügyeli a kártevőirtó programot, a Windows tűzfalat, a szoftverfrissítéseket és a konfigurációs elemeket. Ennek köszönhetően a megfelelőségi szint automatikusan nő.|  

 A fenti konfigurációs lépésekkel és eredményekkel a Trey Research sikeresen egységesíti az eszközök megfelelőségének felügyeletét.  

###  <a name="BKMK_ScenarioSimplify"></a>Példa: Az eszközök egyszerűbb ügyfélfelügyelete  
 A Trey Research minden új számítógép automatikusan telepítené a vállalat Windows 7 rendszerű. Ezeken a számítógépeken az operációs rendszer lemezképének telepítése után azok felügyeletére és a felhasználók által telepített további szoftverek figyelésére is. A fokozottan bizalmas információkat tároló számítógépeken a többinél szigorúbb felügyeleti házirendek szükségesek – például a támogatási szolgálat munkatársai nem csatlakozhatnak hozzájuk távolról, az újraindításhoz meg kell adni a BitLocker PIN-kódját, és csak a helyi rendszergazdák telepíthetnek szoftvereket.  

 Ádám ezeket a vállalati követelményeket a következő esetekhez rendeli hozzá:  

|Követelmény|Jelenlegi ügyfél-felügyeleti állapot|Jövőbeli ügyfél-felügyeleti állapot|  
|-----------------|-------------------------------------|------------------------------------|  
|Az új számítógépekre Windows 7 telepítése szükséges.|A támogatási szolgálat telepíti és konfigurálja a Windows 7 a felhasználók számára, és ezután elküldi a számítógép a megfelelő helyre.|Új számítógépek rögtön a végső rendeltetési Ugrás, vannak csatlakoztatva a hálózathoz, és automatikusan telepítése és konfigurálása Windows 7.|  
|A számítógépek felügyelete és megfigyelése szükséges, Ez magában foglalja annak meghatározásához, licencelőírások hardver- és leltáradatok gyűjtéséhez.|A Configuration Manager-ügyfél központi telepítése automatikus ügyfélleküldéses módszerrel. A támogatási szolgálat pedig megvizsgálja a telepítési hibákat és az ügyfelek leltáradatokat ne küldjön, amikor várhatóan.<br /><br /> Hibák a gyakori, amelyek nem feleltek meg a telepítési függőségei és az ügyfél WMI-hibája miatt.|Az ügyfélrendszer telepítése és a számítógépről összegyűjtött leltáradatok megbízhatóbbak, és kevesebb beavatkozást igényelnek a támogatási szolgálat részéről. A jelentések információt nyújtanak a szoftverek használatáról a licencmegfelelőség ellenőrzéséhez.|  
|Egyes számítógépeken szigorúbb felügyeleti házirendre van szükség.|A szigorúbb felügyeleti házirendek miatt ezen számítógépek vannak jelenleg nem Configuration Manager által felügyelt.|Ezeken a számítógépeken kezeli a Configuration Manager használatával zajlik, kivételek nélkül jár extra felügyeleti terhekkel.|  

 A követelmények teljesítéséhez Ádám ezeket a Configuration Manager felügyeleti lehetőségeit és konfigurációs beállításait:  

-   Operációs rendszer központi telepítése  
-   Ügyfél központi telepítése és ügyfélállapot  
-   Megfelelőségi beállítások  
-   Ügyfélbeállítások  
-   Készlet módszerek és az Eszközintelligencia szolgáltatás  
-   Szerepköralapú adminisztráció  

Alkalmazza ezeket a konfigurációs lépések segítségével a következő táblázatban:  

|Konfigurációs lépés|Eredmény|  
|-------------------------|-------------|  
|ADAM egy olyan számítógépen, amelyen telepítve a Windows 7 operációs rendszer lemezképét rögzíti, és a vállalati specifikációknak van konfigurálva. Ezt követően ismeretlen számítógép támogatásával és PXE használatával központilag telepíti az operációs rendszert az új számítógépekre. A Configuration Manager-ügyfél az operációs rendszer központi telepítésének részeként is telepíti.|Az új számítógépek a támogatási szolgálat beavatkozása nélkül gyorsabban hozhatók használatra kész állapotba.|  
|Ádám konfigurálja az automatikus helyi szintű ügyfélleküldéses telepítés Configuration Manager-ügyfél telepítéséhez bármely felderített számítógépre. Ez biztosítja, hogy azokkal a számítógépekkel, amelyről nem készült ügyféllel rendszerkép, telepíti az ügyfelet, hogy a számítógép felügyeletét a Configuration Manager által.<br /><br /> Ádám konfigurálja az ügyfél állapotát, hogy minden felderített ügyfélhibát automatikusan kijavítson. Ügyfélbeállítások, amelyek lehetővé teszik a szükséges, és konfigurálja az Eszközintelligencia leltározási adatgyűjtés is konfigurálja.|Az ügyfél és az operációs rendszer telepítése hatékonyabb és sokkal megbízhatóbb, mint hogy felderítse a számítógépet a Configuration Manager várakozik, és majd megpróbálja telepíteni az ügyfél forrásfájljait a számítógépen. Azonban az automatikus ügyfélleküldéses távozó engedélyezi a beállítást, akkor adja meg egy biztonsági mentési módszer egy számítógép, amely már rendelkezik az ügyfél telepítéséhez, ha a számítógép csatlakozik a hálózatra telepített operációs rendszer.<br /><br /> Az ügyfélbeállítások lehetővé teszik az ügyfelek számára, hogy a leltáradatokat rendszeresen elküldjék az adott helynek. Ezzel, az ügyfél állapota tesztek mellett megakadályozhatja az ügyfél a támogatási szolgálat minimális beavatkozásával működjön. A WMI-hibákat például észleli és automatikusan kijavítja a rendszer.<br /><br /> Az eszközintelligencia-jelentések segítséget nyújtanak a szoftverhasználat és a licencek figyelésében.|  
|ADAM létrehoz egy gyűjteményt a számítógépek, amelyek a szigorúbb házirend-beállításokat kell rendelkeznie. Ezután létrehoz egy egyéni ügyféleszköz-beállítást ehhez a gyűjteményhez, amely letiltja a távvezérlés lehetővé teszi, hogy a BitLocker PIN-kód bevitelének és lehetővé teszi, hogy a szoftver telepítése csak a helyi rendszergazdák.<br /><br /> Ádám szerepkör alapú felügyelet állít be, így a támogatási szolgálat szakemberei ezen számítógépek gyűjteménye nem látható. Ezzel biztosíthatja, hogy ezek a számítógépek véletlenül nem felügyelt normál számítógépként.|Ezek a számítógépek kezelése mostantól a Configuration Manager által, de a beállításokkal, nem szükséges új helyet.<br /><br /> Az ezen számítógépek gyűjteménye nem látható a támogatási szolgálat munkatársai számára. Ezzel csökkenthető a számítógépek véletlenül küldött központi telepítések és parancsfájlok szabványos számítógépek lehetőségét.|  

 A fenti konfigurációs lépésekkel és eredményekkel a Trey Research sikeresen egyszerűsíti az eszközök ügyfélfelügyeletét.  

##  <a name="BKMK_NextSteps"></a> További lépések  
 A Configuration Manager telepítése előtt ismernie néhány rendszerhez kapcsolódó alapfogalommal és kifejezéssel a Configuration Manager válhat.  

-   Ha ismeri a System Center 2012 Configuration Manager, lásd: [történt változások a System Center Configuration Manager a System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md) az új képességekről.  
-   Magas szintű műszaki áttekintés a System Center Configuration Manager: [a System Center Configuration Manager – alapok](../../core/understand/fundamentals.md).  

Ha ismeri az alapfogalmakat, segítségével a System Center Configuration Manager dokumentációs sikeres központi telepítésében, és használja a Configuration Manager.  

