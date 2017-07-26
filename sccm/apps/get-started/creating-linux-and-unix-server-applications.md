---
title: "Linux és UNIX kiszolgálók alkalmazásainak létrehozása |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozása és központi telepítésekor a Linux és UNIX rendszerű eszközökhöz készült alkalmazások."
ms.custom: na
ms.date: 04/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79cd131a-1a24-4751-87c8-7f275e45d847
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4b9261db93c9bf72c492e3c9be5b30f81835134a
ms.openlocfilehash: 72ebd8bd29b5ecdd817631e447291c04f49d9808
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-linux-and-unix-server-applications-with-system-center-configuration-manager"></a>Linux és UNIX kiszolgálók alkalmazásainak létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Hajtson végre az alábbiakat is figyelembe létre és telepíthet a Linux és UNIX rendszerű számítógépekre készült alkalmazások.  

## <a name="general-considerations"></a>Általános megfontolások  
 A Configuration Manager-ügyfél támogatja a Linux és UNIX rendszerű **csomagokat és programokat használó központi szoftvertelepítést**. A Linux és UNIX rendszerű számítógépekre a Configuration Manager-alkalmazások nem lehet telepíteni.  

 A Linux és UNIX alapú szoftverek központi telepítése az alábbi lehetőségeket nyújtja:  

-   Szoftver telepítése Linux és UNIX rendszerű kiszolgálók, beleértve a következőket:  

    -   Új szoftvereket központi telepítéssel  

    -   Szoftverfrissítések, amelyek még egy számítógép-programok  

    -   Javításokat az operációs rendszerhez  

-   Natív Linux és UNIX-parancsok, és a Linux és UNIX rendszerű kiszolgálókon található parancsfájlok  

-   Az operációs rendszerek, meg kell adnia a program beállítás bejelölésével korlátozott telepítések **csak megadott ügyfélplatformokon**

-   Karbantartási időszakokkal szabályozhatja, ha a szoftver telepítése

-   A központi telepítési állapotüzenetek központi telepítéseinek figyeléséhez  

-   A beállítás az ügyfél számára késleltetési hálózathasználatot, amikor szoftver letöltése, a terjesztési pontról  

### <a name="differences-between-deploying-to-linux-and-unix-computers-and-deploying-to-windows-devices"></a>Linux és UNIX rendszerű számítógépre történő telepítésének és központi telepítése Windows rendszerű eszközök közötti különbségek
Csomagok és programok központi telepítése Linux és UNIX rendszerű számítógépekre, és a csomagok és programok telepítése Windows rendszerű eszközök közötti fő különbségek a következők:  

|Configuration|Részletek|  
|-------------------|-------------|  
|Csak azok a konfigurációk vannak azokra a számítógépekre, és ne használjon a konfigurációkat, amelyek célja a felhasználók használni.|A Configuration Manager-ügyfél Linux és UNIX rendszerű nem támogatja a felhasználókra irányuló konfigurációkat.|  
|Konfigurálja a szoftver letöltése a terjesztési pontról, és a programok futtatását az ügyfél helyi gyorsítótárába.|A Linux és UNIX rendszerekhez készült Configuration Manager-ügyfél nem támogatja a szoftverek futtatását a terjesztési pontról. Ehelyett a szoftvert, hogy az ügyfél letölti, és majd telepíteni kell konfigurálni.<br /><br /> Miután a Linuxhoz és UNIX-hoz készült ügyfél telepít egy szoftvert, a rendszer alapértelmezés szerint törli a szoftvert az ügyfél gyorsítótárából. Kivételt képeznek ez alól a **Tartalom megtartása az ügyfélgyorsítótárban** beállítással konfigurált csomagok, amelyek nem törlődnek az ügyfélről, hanem a szoftver telepítése után is az ügyfél gyorsítótárában maradnak.<br /><br /> A Linux- és UNIX-ügyfél nem támogatja az ügyfélgyorsítótár konfigurálását, a gyorsítótár maximális méretét pedig csak az ügyfélszámítógép szabad lemezterülete korlátozza.|  
|A hálózatelérési fiókot a terjesztési pont elérésére konfigurálja.|A Linux és a UNIX a számítógépek munkacsoportban történő működtetésére hivatott. A Configuration Manager helykiszolgáló tartományában lévő terjesztési pont csomagokat szeretne, konfigurálnia kell a helyhez tartozó hálózatelérési fiókot. Szoftverek központi telepítéséhez a fiókot szoftverterjesztési összetevő-tulajdonságként kell kijelölnie, majd el kell végeznie a konfigurálást.<br /><br /> Egy helyen több hálózatelérési fiókot is beállíthat. A Linux- és UNIX-ügyfél bármelyiket használhatja a hálózatelérésre konfigurált fiókok közül.<br /><br /> További információkért lásd: [A System Center Configuration Manager helyösszetevői](../../core/servers/deploy/configure/site-components.md).|  

 A csomagokat és programokat telepítheti csak Linux- és UNIX-ügyfeleket tartalmazó gyűjteményekben, vagy különböző ügyféltípusokat vegyesen tartalmazó gyűjteményekben, például a **Minden rendszer**gyűjteményben is. Azonban a nem Linux- és nem UNIX-ügyfelek nem telepíti a szoftver vagy a jelentés hiba.  

 Ha a Configuration Manager-ügyfél Linux és UNIX rendszerű fogad, és a központi telepítés futtat, állapotüzeneteket generál. Ezek az állapotüzenetek megtekintheti a Configuration Manager konzolon, vagy a központi telepítés állapotának figyelésére szolgáló jelentések segítségével.  

 Csomagok és programok használatával kapcsolatos információkért lásd: [csomagok és programok](../../apps/deploy-use/packages-and-programs.md).  

##  <a name="configure-packages-programs-and-deployments-for-linux-and-unix-servers"></a>Csomagok, programok és központi telepítése Linux és UNIX rendszerű kiszolgálók konfigurálása  
 Hozzon létre, és a csomagok és programok központi telepítése elérhető alapértelmezett beállításai a Configuration Manager konzol segítségével. Az ügyfél ehhez nem igényel külön konfigurációt.  

 A következő szakaszok a csomagok és programok, valamint a központi telepítések konfigurálását mutatják be.  

### <a name="packages-and-programs"></a>Csomagok és programok  
 Csomag és program létrehozása a Linux vagy UNIX-kiszolgálóhoz, használja a **létrehozása csomag és Program varázsló** a Configuration Manager konzoljáról. A Linux- és UNIX-ügyfél a legtöbb csomag- és programbeállítást támogatja, néhány kivétellel. Csomag és program létrehozásakor és konfigurálásakor ügyeljen az alábbiakra:  

-   A cél számítógépek által támogatott fájltípusokat tartalmazza.  

-   Adja meg a parancssorokat, amelyek használhatók a célszámítógépen.  

-   Ne feledje, hogy interakciót folytató felhasználók beállítások nem támogatottak.  

Az alábbi táblázat a Tulajdonságok csomagok és programok, amelyek nem támogatottak:  

|Csomag és program tulajdonsága|Viselkedés|További információ|  
|----------------------------------|--------------|----------------------|  
|Csomagmegosztási beállítások:<br /><br /> – Az összes beállítások|Hiba történik, és a szoftver telepítése meghiúsul|Az ügyfél nem támogatja ezt a konfigurációt. Az ügyfélnek ehelyett HTTP- vagy HTTPS-kapcsolaton keresztül kell letöltenie a szoftvereket, majd a helyi gyorsítótárából kell futtatnia a parancssort.|  
|Csomagfrissítési beállítások:<br /><br /> -Felhasználók leválasztása a terjesztési pontokról|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja ezt a konfigurációt.|  
|Az operációs rendszer központi telepítési beállításai:<br /><br /> – Az összes beállítások|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja ezt a konfigurációt.|  
|Jelentéskészítés:<br /><br /> – Használja a csomag tulajdonságait állapot MIF egyeztetéséhez<br /><br /> -A mezők használja az állapot MIF egyeztetéséhez|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja a MIF-állapotfájlok használatát.|  
|**Futtatás**:<br /><br /> – Az összes beállítások|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél minden esetben felhasználói felület nélkül futtatja a csomagokat.<br /><br /> Az ügyfél a Futtatás szakasz összes konfigurációs beállítását figyelmen kívül hagyja.|  
|Futtatás után:<br /><br />-Configuration Manager újraindítja a számítógépet<br /><br /> -Program vezérli az újraindítást<br /><br /> -Configuration Manager kijelentkezik a felhasználói|Hiba történik, és a szoftver telepítése meghiúsul|A rendszer újraindítása a beállítás, és a felhasználó által megadott beállítások nem támogatottak.<br /><br /> Ha a **Beavatkozás nem szükséges** beállításon kívül bármely másik beállítást használja, az ügyfél hibát generál, és nem hajt végre semmilyen műveletet, csak folytatja a szoftver telepítését.|  
|A program futtatható:<br /><br /> -Csak amikor van bejelentkezett felhasználó|Hiba történik, és a szoftver telepítése meghiúsul|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> A beállítás használata esetén az ügyfél hibát generál, és a szoftver telepítése sikertelen lesz.<br /><br /> A többi beállítást az ügyfél figyelmen kívül hagyja, és a szoftver telepítése folytatódik.|  
|Futtatási mód:<br /><br /> -Futtatás felhasználói jogosultságokkal|A rendszer nem veszi figyelembe a beállításokat.|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> Azonban az ügyfél támogatja a rendszergazdai jogosultságokkal rendelkező futtató konfiguráció.<br /><br /> Ha a **Futtatás rendszergazdai jogosultságokkal**, a Configuration Manager-ügyfél saját rendszergazdai hitelesítő adatait használja.<br /><br /> Ez a beállítás nem generál hibát vagy naplóbejegyzést. A szoftver telepítése meghiúsul, ha az ügyfél az előfeltétel-konfigurációhoz hibát generál **a Program futtatható** = **csak amikor van bejelentkezett felhasználó**.|  
|Felhasználók megtekintése és a program telepítésébe való beavatkozást|A rendszer nem veszi figyelembe a beállításokat.|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> A rendszer figyelmen kívül hagyja a beállítást, és folytatja a szoftver telepítését.|  
|Meghajtó mód:<br /><br /> – Az összes beállítások|A rendszer nem veszi figyelembe a beállításokat.|Ez a beállítás nem támogatott, mivel az ügyfél minden esetben letölti és helyileg futtatja a tartalmat.|  
|Egy másik programot futtasson először|Hiba történik, és a szoftver telepítése meghiúsul|A rekurzív programtelepítés nem támogatott.<br /><br /> Ha a program először egy másik program futtatására van beállítva, a szoftvertelepítés sikertelen lesz, és a másik program telepítése sem indul el.|  
|Program számítógéphez történő hozzárendelése esetén:<br /><br /> -Egyszeri futtatás minden bejelentkező felhasználó számára kérelmezni|A rendszer nem veszi figyelembe a beállításokat.|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> Az ügyfél azonban egyszer fut, a számítógép konfigurálását támogatja.<br /><br /> Ez a beállítás nem generál hibát vagy naplóbejegyzést, mivel a rendszer már létrehozott egy hibát és naplóbejegyzést **A program futtatható** = **Csak amikor van bejelentkezett felhasználó**.|  
|A program értesítéseinek elrejtése|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem jelenít meg felhasználói felületet.<br /><br /> Ha a beállítás aktív, a rendszer figyelmen kívül hagyja, és folytatja a szoftver telepítését.|  
|Program letiltása minden számítógépen, ahol központilag telepítették|A rendszer nem veszi figyelembe a beállításokat.|A beállítás nem támogatott, és nincs hatással a szoftver telepítésére.|  
|A program központi telepítés helyett a csomag telepítése feladatütemezés telepítésének engedélyezése||Az ügyfél nem támogatja a feladatütemezéseket.<br /><br /> A beállítás nem támogatott, és nincs hatással a szoftver telepítésére.|  
|Windows Installer:<br /><br /> – Az összes beállítások|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja a Windows Installer fájljait és beállításait.|  
|OpsMgr karbantartási mód:<br /><br /> – Az összes beállítások|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja ezt a konfigurációt.|  

### <a name="deploy-software-to-a-linux-or-unix-server"></a>Szoftver központi telepítése Linux vagy UNIX-kiszolgálóra
 Szoftver központi telepítése egy Linux vagy UNIX-kiszolgálóhoz csomag és program használatával, használhatja a **szoftver központi telepítése varázsló** a Configuration Manager konzoljáról. A legtöbb központi telepítési beállítások támogatottak az ügyfél Linux és UNIX rendszerekhez készült. Azonban számos beállítás nem támogatott. Amikor szoftvert telepít központilag, vegye figyelembe a következőket:  

-   A csomagot legalább egy olyan terjesztési pontra el kell juttatnia, amely a tartalom helyéhez beállított határcsoporthoz tartozik.  

-   Lehet, hogy az ügyfél Linux és UNIX rendszerű, amely megkapja a központi telepítés fér hozzá a terjesztési pontot a saját hálózati helyét.  

-   A Linux- és UNIX-ügyfél letölti a csomagot a terjesztési pontról, és a helyi számítógépen futtatja a programot.  

-   A Linux- és UNIX-ügyfél megosztott mappákból nem képes csomagokat letölteni, Csomagok HTTP vagy HTTPS-t támogató IIS-t támogató terjesztési pontról tölti le.  

 Az alábbi táblázatban a központi telepítések esetében nem támogatott tulajdonságok szerepelnek:  

|Központi telepítés tulajdonsága|Viselkedés|További információ|  
|-------------------------|--------------|----------------------|  
|Központi telepítési beállítások – Cél:<br /><br /> -Érhető el<br /><br /> -A szükséges|A rendszer nem veszi figyelembe a beállításokat.|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> Az ügyfél ugyanakkor a **Kötelező**beállítást támogatja, amely előírja az ütemezett telepítési időt, az ütemezett időpont előtti manuális telepítés azonban nem lehetséges.|  
|Ébresztési csomagok küldése|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja ezt a konfigurációt.|  
|Hozzárendelési ütemezés:<br /><br /> -bejelentkezés<br /><br /> -Kijelentkezés|Hiba történik, és a szoftver telepítése meghiúsul|Felhasználó által megadott beállítások nem támogatottak.<br /><br /> Az ügyfél azonban az **Amint lehetséges**beállítást támogatja.|  
|Értesítési beállítások:<br /><br /> – Engedélyezze a felhasználók számára a program hozzárendelésektől|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem jelenít meg felhasználói felületet.|  
|Az ütemezett hozzárendelési idő elérésekor a következő tevékenységek végrehajtásának engedélyezése a karbantartási időszakon kívül:<br /><br /> -A rendszer újraindítása (Ha a telepítés befejezéséhez szükséges)|Hiba történik.|Az ügyfél nem támogatja a rendszer újraindítását.|  
|Gyors (LAN) hálózatra vonatkozó központi telepítési beállítás:<br /><br /> -Program futtatása a terjesztési pontról|Hiba történik, és a szoftver telepítése meghiúsul|Az ügyfél nem képes szoftvert futtatni a terjesztési pontról, hanem le kell töltenie a programot a futtatáshoz.|  
|Központi telepítési beállítás, ha az ügyfél lassú vagy nem megbízható hálózathatáron belül van, illetve ha tartalék forráshelyet használ a tartalom számára:<br /><br /> -Engedélyezése azonos alhálózaton található ügyfelek számára|A rendszer nem veszi figyelembe a beállításokat.|Az ügyfél nem támogatja az egyenrangú társak közötti tartalommegosztást.|  

 A tartalom helyével kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 A központi telepítés létrehozásával kapcsolatos további információkért lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).  

##  <a name="manage-network-bandwidth-for-software-downloads-from-distribution-points"></a>Hálózati sávszélesség szabályozása a szoftverek letöltése a terjesztési pontokról  
 A Linux és UNIX rendszerű ügyfél támogatja a hálózati sávszélesség szabályozását, amikor szoftver letöltése, a terjesztési pontról.  

 Az ügyfél beállításai a háttérben futó intelligens átviteli (BITS), amely a Configuration Manager-ügyfél beállításainak konfigurálása, de nem alkalmazza a BITS szolgáltatást. Ehelyett szoftverek letöltése esetén az ügyfél a hálózati sávszélesség használatának korlátozására a HTTP-kérelmek adattömbméretét és az adattömbök közötti késleltetés hosszát szabályozza.  

 Ha egy ügyfélen szeretné beállítani a hálózati sávszélesség szabályozását, konfigurálja a **Háttérben futó intelligens átvitel** ügyfélbeállításait, majd alkalmazza a beállításokat az ügyfélszámítógépre. A sávszélesség-vezérlés használatához az ügyfélnek úgy kell megkapnia a **háttérben futó intelligens átvitel** konfigurálva, a következő beállításokkal **Igen**:  

-   **Korlátozza a maximális hálózati sávszélességet a háttérben futó BITS-adatátvitelek számára**  

 Az ügyfél az alábbi konfigurációs beállítások használatát támogatja a Háttérben futó intelligens átvitelhez:  

    -   **Szabályozó ablak indítási időpontja**  

    -   **Szabályozó ablak végidőpontja**  

    -   **Maximális átviteli sebesség a szabályozó ablakon belül (kb/s)**  

    -   **Maximális átviteli sebesség a szabályozó ablakon kívül (kbps)**  

A Linux- és UNIX-ügyfél a Háttérben futó intelligens átvitelhez kapcsolódó alábbi konfigurációs beállítások használatát nem támogatja, és figyelmen kívül hagyja:  

-   **BITS-letöltések engedélyezése a szabályozó ablakon kívül**  

 Ha le a terjesztési pontról ügyfélre történő Szoftverletöltés megszakad, a Linux és UNIX rendszerű ügyfél folytatja. Ehelyett a a teljes szoftvercsomag letöltését újraindítja.  

##  <a name="configure-operations-for-software-deployments"></a>Központi szoftvertelepítési műveletek konfigurálása  
 Hasonlóképpen a Windows-ügyfélhez, a Configuration Manager-ügyfél Linux és UNIX rendszerű és felderíti az új központi szoftvertelepítéseket kérdezze le az új házirendek. Az új házirendek keresési gyakorisága az ügyfélbeállításoktól függ. A központi szoftvertelepítések ideje karbantartási időszakokkal szabályozható.  

 A Linux- és UNIX-kiszolgálókra történő központi szoftvertelepítések konfigurálása a csomagok, a programok és a központi telepítések tulajdonságaival lehetséges.  

 Amikor az ügyfél központi telepítésre vonatkozó házirendet kap, állapotüzenetet küld. Akkor is állapotüzenetet küld a szoftver, és ha a telepítés befejeződik, vagy sikertelen telepítés indításakor.  

 Szoftverek központi telepítésére szolgáló programokat a rendszergazdai hitelesítő adatokkal, amely futtatja a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült. A rendszer a programparancs kilépési kódja alapján határozza meg, hogy a telepítés sikeres volt-e. A 0 (nulla) kilépési kód sikeres telepítést jelent. Emellett ha a naplózási szint INFO vagy TRACE, a rendszer az **stdout** (szabványos kimeneti folyam) vagy az **stderr** (szabványos hibafolyam) kódot másolja a naplófájlba  

> [!TIP]  
>  Ha a telepíteni kívánt szoftverek a Linux- vagy UNIX-kiszolgáló által elérhető hálózati fájlrendszeren (NFS) található, nem kell terjesztési pontot használnia a csomag letöltéséhez. Amikor azonban a csomagot létrehozza, ne jelölje be az **Ez a csomag forrásfájlokat tartalmaz**négyzetet, majd a program konfigurálásakor adja meg a megfelelő parancssori műveletet a hálózati fájlrendszer csatlakozási pontján található csomag közvetlen eléréséhez.  

