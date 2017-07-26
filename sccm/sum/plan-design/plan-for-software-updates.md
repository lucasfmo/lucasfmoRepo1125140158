---

title: "Szoftverfrissítések tervezése |} Microsoft Docs"
description: "A szoftverfrissítési pont infrastruktúrájának tervének elengedhetetlen, éles környezetben a System Center Configuration Manager szoftverfrissítéseinek használata előtt."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: d071b0ec-e070-40a9-b7d4-564b92a5465f
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 703adc87b9498e39a1db71b94f1bc1a05a4889ec
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="plan-for-software-updates-in-system-center-configuration-manager"></a>Szoftverfrissítések tervezése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Szoftverfrissítések akkor használhatja a System Center Configuration Managerrel éles környezetben, fontos, hogy halad át a tervezési folyamat. A szoftverfrissítési pont infrastruktúrájának egy jó terv, akkor a kulcs sikeres szoftver frissítések megvalósításához.

## <a name="capacity-planning-recommendations-for-software-updates"></a>Kapacitástervezési javaslatok szoftverfrissítésekhez  
 A következőkben ismertetett javaslatok kiindulópontot nyújthatnak a szükséges kapacitástervezési információk összegyűjtéséhez az adott környezetben megfelelő szoftverfrissítési megoldás kialakítása céljából. A tényleges kapacitási követelmények eltérhetnek a jelen témakörben leírtaktól, és a következő tényezőktől függnek: az adott hálózati környezettől, a szoftverfrissítési pont helyrendszerének üzemeltetésére szolgáló hardvertől, a telepített ügyfelek számától és a kiszolgálóra telepített helyrendszerszerepköröktől.  

###  <a name="BKMK_SUMCapacity"></a> A szoftverfrissítési pont kapacitástervezése  
 A támogatott ügyfelek száma a szoftverfrissítési ponton futó Windows Server Update Services (WSUS) verziójától, valamint attól is függ, hogy a szoftverfrissítési pont helyrendszerszerepkör kiszolgálóján van-e másik helyrendszerszerepkör telepítve:  

-   A szoftverfrissítési pont akár 25 000 ügyfél támogatására is alkalmas lehet, ha a szoftverfrissítési pont számítógépén fut a WSUS szolgáltatás, és a szoftverfrissítési pont kiszolgálóján másik helyrendszerszerepkör is üzemel.  

-   A szoftverfrissítési pont legfeljebb 150 000 ügyfelet is támogatni, ha a távoli számítógép megfelel a WSUS, WSUS és a Configuration Managerben használt, és konfigurálja a következő:

    IIS-alkalmazáskészletek:
    - Növelje a WsusPool várólista hosszát 2000 értékre
    - Növelje a WsusPool privát memóriakorlátját x4 időpontokat, vagy adja meg a 0 (korlátlan)      

    A szoftverfrissítési pont hardverkövetelményekkel kapcsolatos részletekért lásd: [ajánlott hardver helyrendszerek](/sccm/core/plan-design/configs/recommended-hardware#a-namebkmkscalesiesystemsa-site-systems).

-   Alapértelmezés szerint a Configuration Manager nem támogatja a konfigurálása szoftverfrissítési pontok NLB fürtökként. A Configuration Manager verziója 1702, mielőtt a Configuration Manager SDK segítségével legfeljebb négy szoftverfrissítési pont konfigurálása NLB-fürtön. Azonban a Configuration Manager verziója 1702 kezdődően szoftverfrissítési pontok NLB fürtökként nem támogatottak és frissítések a Configuration Manager verziója 1702 le lesz tiltva, ha ez a konfiguráció észleli.

### <a name="capacity-planning-for-software-updates-objects"></a>Kapacitástervezés szoftverfrissítési objektumokhoz  
 A szoftverfrissítési objektumokkal kapcsolatos tervezéshez vegye igénybe az alábbi kapacitástervezési információkat.  

-   **Egy központi telepítés legfeljebb 1000 szoftverfrissítést tartalmazzon**  

     A szoftverfrissítések száma az egyes központi telepítésekben ne haladja meg az 1000-et. Automatikus központi telepítési szabály létrehozásakor határozzon meg egy feltételt a visszaadott szoftverfrissítések számának korlátozására. Ha a megadott feltétel több mint 1000 szoftverfrissítést ad vissza, az automatikus központi telepítési szabály futtatása sikertelen lesz. Az automatikus központi telepítési szabály állapotát ellenőrizheti a **automatikus központi telepítési szabályok** csomópont a Configuration Manager konzolon. Amikor kézzel telepíti a frissítéseket, ne válasszon 1000-nél több telepítendő frissítést.  

     Emellett ne haladja meg az alapkonfiguráció 1000 szoftverfrissítés alkalmazása száma. További információkért lásd: [referenciakonfigurációk létrehozása](../../compliance/deploy-use/create-configuration-baselines.md).

##  <a name="BKMK_SUPInfrastructure"></a> A szoftverfrissítési pontok infrastruktúrájának meghatározása  
 A központi felügyeleti helynek és az összes elsődleges gyermekhelynek rendelkeznie kell egy szoftverfrissítési ponttal, ahová a szoftverfrissítések eljuttathatók. A szoftverfrissítési pont infrastruktúrájának megtervezésekor meg kell határoznia a következő függőségek:
 - a szoftverfrissítési pontot a hely telepítésének helyéről
 - mely helyek igényelnek olyan szoftverfrissítési pontot, amely internetes ügyfelektől érkező kommunikációt fogad
 - hogy szükséges-e a szoftverfrissítési pont egy másodlagos hely frissítését.

A szoftverfrissítési pontok infrastruktúrájának megtervezéséhez az alábbi szakaszok nyújtanak segítséget.  

> [!IMPORTANT]  
>  A szoftverfrissítésekhez szükséges belső és külső függőségi kapcsolatos információkért lásd: [szoftverfrissítéseinek előfeltételei](prerequisites-for-software-updates.md).  

 A Configuration Manager elsődleges helyen több szoftverfrissítési pontot is hozzáadhat. Egy helyen több szoftverfrissítési pont használata a hálózati terheléselosztás (NLB) összetettsége nélkül biztosít hibatűrést. A szoftverfrissítési pontok számának növelésével elért feladatátvételi képesség ugyanakkor nem annyira hatékony, mint a kizárólag terheléselosztásra használt NLB-konfiguráció, hanem inkább csak a hibatűrés erősítésére szolgál. Emellett a szoftverfrissítési pontok feladatátvételi kialakítása eltérő a felügyeleti pontok esetében alkalmazott tiszta véletlenszerűsítésre épülő modelltől. A felügyeleti pontok működésétől eltérően az új szoftverfrissítési pontra való átváltás hatással van az ügyfél és a hálózat teljesítményére. Amikor az ügyfél új WSUS-kiszolgálóra vált a szoftverfrissítések vizsgálata céljából, azzal növekszik a katalógus mérete, ami nagyobb ügyféloldali és hálózati terhelést eredményez. Az ügyfél ezért fenntartja a kapcsolatot azzal a szoftverfrissítési ponttal, amely számára a legutóbbi sikeres vizsgálatot végrehajtotta.  

 Az elsődleges helyen telepített első szoftverfrissítési pont szolgál szinkronizálási forrásként az elsődleges helyen felvett összes további szoftverfrissítési pont számára. A kívánt szoftverfrissítési pontok hozzáadása és a szoftverfrissítések szinkronizálásának elindítása után a **Figyelés** munkaterület **Szoftverfrissítési pont szinkronizálási állapota** csomópontjában tekintheti meg a szoftverfrissítési pontok és a szinkronizálási forrás állapotát.  

 Ha valamelyik szoftverfrissítési pont meghibásodik, és ez a szoftverfrissítési pont van beállítva a hely többi szoftverfrissítési pontjának szinkronizálási forrásaként, abban az esetben manuális módszerrel el kell távolítania a hibás szoftverfrissítési pontot, és újat kell választania szinkronizálási forrásként. További információ a eltávolítani egy szoftverfrissítési pontról, lásd a [távolítsa el a szoftverfrissítési pont hely rendszer szerepkörre](../get-started/remove-a-software-update-point.md).  

###  <a name="BKMK_SUPList"></a> A szoftverfrissítési pontok listája  
 A Configuration Manager ellátja az ügyfelet a szoftverfrissítési pontok listája a következő esetekben a: Ha egy új ügyfél megkapja a szoftverfrissítések engedélyezésére vonatkozó házirendet, vagy ha egy ügyfél nem tud csatlakozni a szoftverfrissítési pont és a kell váltania másik szoftverfrissítési pontra. Az ügyfél véletlenszerűen kiválaszt egy szoftverfrissítési pontot a listából, és priorizálja az azonos erdőben lévő szoftverfrissítési pontokat. A Configuration Manager-ügyfelek, amelyeken az ügyfél különböző listákat biztosít.  

-   **Intranetalapú ügyfelek**: Olyan listát kapnak a szoftverfrissítési pontokról, amelyek csak az intranetről érkező kapcsolatokat engedélyezi. beállíthatja, vagy a szoftverfrissítési pontokról, amelyek lehetővé teszik az internetes és intranetes ügyfélkapcsolatok listáját.  

-   **Internetalapú ügyfelek**: Olyan listát kapnak a szoftverfrissítési pontokról, amelyek megadta, hogy csak az internetről érkező kapcsolatok engedélyezése, vagy a szoftverfrissítési pontokról, amelyek lehetővé teszik az internetes és intranetes ügyfélkapcsolatok listáját.  

###  <a name="BKMK_SUPSwitching"></a> Váltás a szoftverfrissítési pontok között  
> [!NOTE]
> 1702 verziójával kezdve az ügyfelek a határcsoportok használatával egy új szoftverfrissítési pont található, és tartalék és keresése egy új szoftverfrissítési pont, ha már nem érhető el a jelenlegivel. Azok a kiszolgálók egy ügyfél található vezérlőhöz eltérő határcsoportokban egyes szoftverfrissítési pontján adhat hozzá. További információkért lásd: [szoftverfrissítési pontok](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) a a [határcsoportok konfigurálása](/sccm/core/servers/deploy/configure/boundary-groups) témakör.

Ha egy helyen több szoftverfrissítési pontot használ, és az egyik meghibásodik vagy elérhetetlenné válik, az ügyfelek másik szoftverfrissítési ponthoz fognak csatlakozni, és továbbra is keresni fogják a legújabb szoftverfrissítéseket. Miután a rendszer hozzárendeli az ügyfelet egy szoftverfrissítési ponthoz, az ügyfél egészen addig ehhez a szoftverfrissítési ponthoz lesz rendelve, amíg sikeresen tudja rajta ellenőrizni a szoftverfrissítéseket.  

A hibás szoftverfrissítés-vizsgálatok különböző újrapróbálkozásos és újrapróbálkozás nélküli hibakódokat adhatnak vissza. Ha a vizsgálat újrapróbálkozásos hibakódot ad vissza, az ügyfél újra megpróbálja ellenőrizni a szoftverfrissítéseket a szoftverfrissítési ponton. Újrapróbálkozásos hibakód jellemzően akkor fordul elő, ha a WSUS-kiszolgáló nem érhető el vagy átmenetileg túlterhelt. Ha a szoftverfrissítések vizsgálata sikertelen, az ügyfél az alábbi lépéseket hajtja végre:  

1.  Az ügyfél az ütemezett időpontban ellenőrzi a szoftverfrissítéseket, illetve ha ezt az ügyfélszámítógépen a Vezérlőpulton vagy az SDK-val kezdeményezik. Ha a vizsgálat sikertelen, az ügyfél 30 perc elteltével újra megpróbálja elvégezni azt, ugyanazon a szoftverfrissítési ponton.  

2.  Az ügyfél legalább négy alkalommal megpróbálja újra végrehajtani a vizsgálatot, 30 perces időközönként. A negyedik hiba után további két percet várakozik, majd a következő szoftverfrissítési pontra vált a szoftverfrissítési pontok listáján.  

3.  Az ügyfél végighalad az új szoftverfrissítési ponton ugyanazt a folyamatot. A sikeres vizsgálat után az ügyfél továbbra is az új szoftverfrissítési pontra való kapcsolódáshoz.

 Az alábbi lista további információkkal szolgál azokhoz az esetekhez, amelyekben újrapróbálkozás vagy a szoftverfrissítési pont váltása szükséges:  

-   Ha az ügyfél nem csatlakozik a vállalati intranethez, és emiatt nem képes szoftverfrissítéseket keresni, nem fog másik szoftverfrissítési pontra váltani. Ez egy várt hiba, hiszen az ügyfél nem tudja elérni a vállalati hálózat, sem a szoftverfrissítési pontot, amely az intranetről érkező kapcsolatokat engedélyezi. A Configuration Manager-ügyfél meghatározza, hogy az intranetes szoftverfrissítési pont rendelkezésre állását.  

-   Ha engedélyezve van az internetes ügyfélfelügyelet, és több szoftverfrissítési pont is fogad kommunikációt az interneten lévő ügyfelektől, úgy a váltási folyamat az előző példában leírt szokásos újrapróbálkozási eljárást fogja követni.  

-   Ha a vizsgálat elindult, de az ügyfelet még a vizsgálat befejezése előtt kikapcsolták, azt a rendszer nem tekinti vizsgálati hibának, és nem számítja bele a négy újrapróbálkozási lehetőségbe.  

Amikor a Configuration Manager kap a Windows Update Agent következő hibakódok, hogy az ügyfél újrapróbálkozási a kapcsolat fog rendelkezni:  

2149842970, 2147954429, 2149859352, 2149859362, 2149859338, 2149859344, 2147954430, 2147747475, 2149842974, 2149859342, 2149859372, 2149859341, 2149904388, 2149859371, 2149859367, 2149859366, 2149859364, 2149859363, 2149859361, 2149859360, 2149859359, 2149859358, 2149859357, 2149859356, 2149859354, 2149859353, 2149859350, 2149859349, 2149859340, 2149859339, 2149859332, 2149859333, 2149859334, 2149859337, 2149859336, 2149859335

Kereshet egy hibakódot szerinti, kell a decimális hibakód átalakítása hexadecimális, és keressen egy helyet a hexadecimális érték, mint a [a Windows Update Agent - hiba kódok Wiki](https://social.technet.microsoft.com/wiki/contents/articles/15260.windows-update-agent-error-codes.aspx).


###  <a name="BKMK_ManuallySwitchSUPs"></a>Manuálisan váltson az ügyfelek egy új szoftverfrissítési pontra
A Configuration Manager 1606-os kiadásával kezdődően engedélyezheti, hogy a Configuration Manager-ügyfelek új szoftverfrissítési pontra váltsanak, ha az aktív szoftverfrissítési ponttal probléma adódik. Ez a beállítás csak akkor okoz változást, ha az ügyfél több szoftverfrissítési pontot kap egy felügyeleti pontról.  

Ezt a beállítást eszközgyűjteményen vagy eszközök egy kiválasztott csoportján engedélyezze. Engedélyezése esetén a következő keresés során az ügyfelek másik szoftverfrissítési pontot fognak keresni. A WSUS-konfigurációs beállításoktól – azaz a frissítési besorolásoktól, attól, hogy a szoftverfrissítési pontok közös WSUS-adatbázissal rendelkeznek-e stb. – függően az új szoftverfrissítési pontra való váltás megnövekedett hálózati forgalmat eredményez. Ennek megfelelően csak szükséges esetben használja ezt a beállítást.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>A szoftverfrissítési pont váltására szolgáló beállítás engedélyezése  

1.  A Configuration Manager-konzolon kattintson az **Eszközök és megfelelőség > Áttekintés Eszközgyűjtemények** elemre.  

2.  A **Kezdőlap** **Gyűjtemény** csoportjában kattintson az **Ügyfélértesítés**elemre, majd a **Váltás a következő szoftverfrissítési pontra**lehetőségre.  


###  <a name="BKMK_SUP_CrossForest"></a> Nem megbízható erdőben lévő szoftverfrissítési pontok  
 Egy helyen több szoftverfrissítési pontot is létrehozhat a nem megbízható erdőben található ügyfelek támogatására. Ha másik erdőben szeretne szoftverfrissítési pontot felvenni, először telepítsen és konfiguráljon egy WSUS-kiszolgálót az adott erdőben, Indítsa el a varázsló a Configuration Manager helykiszolgáló a szoftverfrissítési pont hely rendszer szerepkört hozzáadni. A varázslóban a nem megbízható erdőben lévő WSUS-kiszolgálóhoz való sikeres kapcsolódáshoz az alábbi beállításokat konfigurálja:  

-   Adjon meg egy Helyrendszer-telepítési fiókot, amely jogosult az erdőben lévő WSUS-kiszolgáló elérésére.  

-   Adja meg a WSUS-kiszolgálóhoz való kapcsolódáshoz használandó WSUS-kiszolgálói kapcsolatfiókot.  

 Tegyük fel például, hogy „A” erdőben lévő elsődleges helyen két szoftverfrissítési pont található (SZFP1 és SZFP2). Emellett ugyanehhez az elsődleges helyhez két további szoftverfrissítési pont tartozik a „B” erdőben: SZFP3 és SZFP4. Ebben az esetben ha váltás történik, az ügyféllel azonos erdőben lévő szoftverfrissítési pontok kerülnek előrébb a rangsorban.  

###  <a name="BKMK_WSUSSyncSource"></a> Meglévő WSUS-kiszolgáló használata szinkronizálási forrásként a legfelső szintű helyen  
 Jellemzően a hierarchia legfelső szintű helye van beállítva a szoftverfrissítési metaadatok szinkronizálására a Microsoft Update szolgáltatással. A vállalati biztonsági házirend nem engedélyezi a hozzáférést az Internet elérését a legfelső szintű helyről, konfigurálhatók az olyan meglévő WSUS-kiszolgálót, amely nem szerepel a Configuration Manager-hierarchia legfelső szintű hely szinkronizálási forrását. Előfordulhat például, hogy a szegélyhálózaton telepítve van egy WSUS-kiszolgáló, amely internetkapcsolattal rendelkezik, a legfelső szintű hely azonban nem. Ebben az esetben a szegélyhálózaton lévő WSUS-kiszolgálót is beállíthatja a szoftverfrissítési metaadatok szinkronizálási forrásaként. Győződjön meg arról, hogy a Szegélyhálózaton lévő WSUS-kiszolgáló szoftverfrissítéseket szinkronizáljon, amelyek a Configuration Manager-hierarchiában szükséges feltételeknek. ellenkező esetben előfordulhat, hogy a felső szintű hely nem a várt szoftverfrissítéseket szinkronizálja. A szoftverfrissítési pont telepítésekor állítson be egy WSUS-kapcsolatfiókot, amely hozzáfér a szegélyhálózaton lévő WSUS-kiszolgálóhoz, és győződjön meg arról, hogy a tűzfal engedélyezi az adatforgalmat a megfelelő portokon. További információkért tekintse át a [által a szoftverfrissítési pont a szinkronizálás forrásához használt portokkal](../../core/plan-design/hierarchy/ports.md#BKMK_PortsSUP-WSUS).  

###  <a name="BKMK_NLBSUPSP1"></a> Hálózati terheléselosztás (NLB) használatára konfigurált szoftverfrissítési pont  
 A szoftverfrissítési pontok közötti váltás valószínűleg megoldást jelent a hibatűréssel kapcsolatos problémákra. Alapértelmezés szerint a Configuration Manager nem támogatja a konfigurálása szoftverfrissítési pontok NLB fürtökként. A Configuration Manager verziója 1702, mielőtt a Configuration Manager SDK segítségével legfeljebb négy szoftverfrissítési pont konfigurálása NLB-fürtön. Azonban a Configuration Manager verziója 1702 kezdődően szoftverfrissítési pontok NLB fürtökként nem támogatottak és frissítések a Configuration Manager verziója 1702 le lesz tiltva, ha ez a konfiguráció észleli. A Set-CMSoftwareUpdatePoint PowerShell-parancsmaggal kapcsolatban további információkért lásd: a [Set-CMSoftwareUpdatePoint](http://go.microsoft.com/fwlink/?LinkId=276834).

###  <a name="BKMK_SUPSecSite"></a> Szoftverfrissítési pont egy másodlagos helyen  
 A másodlagos helyeken nem kötelező szoftverfrissítési pontnak lennie. Ha egy másodlagos helyre telepít szoftverfrissítési pontot, a WSUS-adatbázis lesz beállítva az alapértelmezett szoftverfrissítési pont replikájaként az elsődleges szülőhelyen. Egy másodlagos helyre csak egy szoftverfrissítési pont telepíthető. Ha a másodlagos helyen nincs szoftverfrissítési pont, akkor a másodlagos helyhez társított eszközök a szülőhelyen található szoftverfrissítési pontot fogják használni. Általában olyankor telepítenek szoftverfrissítési pontot egy másodlagos helyre, ha korlátozott a sávszélesség a másodlagos helyhez társított eszközök és az elsődleges szülőhelyen lévő szoftverfrissítési pontok között, vagy ha a szoftverfrissítési pont megközelíti a kapacitási korlátot. Miután megtörtént a szoftverfrissítési pont telepítése és beállítása a másodlagos helyen, a rendszer frissíti a helyszintű házirendet a helyhez tartozó ügyfélszámítógépeken, és azok használni kezdik az új szoftverfrissítési pontot.  

##  <a name="BKMK_SUPInstallation"></a>Szoftverfrissítési pont telepítésének tervezése  
 Mielőtt létrehozna egy szoftverfrissítési pont hely rendszer szerepkörre a Configuration Manager alkalmazásban, nincsenek attól függően, hogy a Configuration Manager infrastruktúrájának figyelembe kell venni néhány követelményt. Ha beállítja az SSL használatát a szoftverfrissítési ponton, akkor különösen fontos elolvasni ezt a szakaszt, mert további lépéseket is el kell végeznie ahhoz, hogy megfelelően működjenek a hierarchia szoftverfrissítési pontjai. Ebből a részből megtudhatja, milyen lépések szükségesek a szoftverfrissítési pont telepítésének tervezéséhez és előkészítéséhez.  

###  <a name="BKMK_SUPSystemRequirements"></a> A szoftverfrissítési pont követelményei  
 A szoftverfrissítési pont hely rendszer szerepkört olyan helyrendszerre, amely megfelel a WSUS vonatkozó minimális követelményeknek és a Configuration Manager-helyrendszerek támogatott konfigurációi rendszerre telepíthető.  

-   A Windows Server 2012 rendszer WSUS kiszolgálói szerepkörének minimális követelményeivel kapcsolatos további információkért lásd: [tekintse át a szempontok és a rendszerkövetelmények](https://technet.microsoft.com/library/hh852344.aspx#BKMK_1.1) a Windows Server 2012 dokumentációs könyvtárában.  

-   A Configuration Manager-helyrendszerek támogatott konfigurációival kapcsolatos további információkért lásd: [hely és hely rendszerkövetelmények](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

###  <a name="BKMK_PlanningForWSUS"></a> A WSUS telepítésének tervezése  

A szoftverfrissítésekhez telepíteni kell a WSUS támogatott verzióját az összes helyrendszer-kiszolgálóra, amelyen be szeretné állítani a szoftverfrissítési pont helyrendszerszerepkört. Ha nem a helykiszolgálóra telepíti a szoftverfrissítési pontot, akkor telepíteni kell a WSUS felügyeleti konzolját a helykiszolgáló számítógépre (ha még nem történt meg). Ez teszi lehetővé, hogy a helykiszolgáló kommunikáljon a szoftverfrissítési ponton futó WSUS szolgáltatással.  

 Ha Windows Server 2012 WSUS használja, konfigurálnia kell a további engedélyt, hogy **WSUS-Konfigurációkezelő** a Configuration Manager csatlakozhasson a WSUS szolgáltatáshoz, és elvégezhesse a rendszeres ellenőrzi. Az engedélyek beállításához válasszon az alábbi lehetőségek közül:  

-   Vegye fel a **SYSTEM** fiókot a **WSUS-rendszergazdák** csoportba  

-   Adja hozzá az **NT AUTHORITY\SYSTEM** fiókot a WSUS-adatbázis (SUSDB) felhasználóihoz, és állítsa be számára minimálisan a webszolgáltatás adatbázis-szerepkört  

 További információk arról, hogyan kell telepíteni a WSUS-t a Windows Server 2012 kiszolgálón: [Install the WSUS Server Role](http://go.microsoft.com/fwlink/p/?LinkId=272355) (A WSUS kiszolgálói szerepkör telepítése) a Windows Server 2012 dokumentációs könyvtárában.  

 Ha több szoftverfrissítési pontot telepít egy elsődleges helyre, akkor ugyanazt a WSUS-adatbázist kell használni minden olyan pont esetében, amelyek ugyanabban az Active Directory-erdőben vannak. Az adatbázis megosztása jelentősen csökkenti, bár nem szünteti meg teljesen az ügyfél és a hálózat teljesítményében bekövetkező változást, amely olyankor figyelhető meg, amikor az ügyfelek egy másik szoftverfrissítési pontra váltanak. A rendszer akkor is végez változáskeresést, ha az ügyfél egy olyan szoftverfrissítési pontra vált, amely az előzővel közös adatbázist használ, de ez a keresés sokkal takarékosabb, mint ha a WSUS-kiszolgálónak külön adatbázisa lenne.  

####  <a name="BKMK_CustomWebSite"></a> A WSUS beállítása egy egyéni webhely használatára  
 A WSUS telepítésekor választhat, hogy a meglévő alapértelmezett IIS-webhelyet kívánja használni, vagy létrehoz egy egyéni WSUS-webhelyet. Hozzon létre egyéni webhelyet a WSUS Szolgáltatáshoz, így az IIS kiszolgálója dedikált virtuális webhelyen, nem osztja meg ugyanazt a webhelyet a más Configuration Manager helyrendszerei vagy más alkalmazások által használt a WSUS szolgáltatásokat. Ez különösen igaz abban az esetben, amikor a helykiszolgálóra telepíti a szoftverfrissítési pont helyrendszerszerepkört. WSUS Windows Server 2012 vagy Windows Server 2016 futtatásakor a WSUS a 8530-as portot használja a HTTP és a 8531-es portot HTTPS alapértelmezés szerint van konfigurálva. A szoftverfrissítési pont létrehozásakor meg kell adni ezeket a portbeállításokat.  

####  <a name="BKMK_WSUSInfrastructure"></a> Meglévő WSUS-infrastruktúra használata  
 Kiválaszthatja, hogy a WSUS-kiszolgálót, amely már aktív volt, a Configuration Manager olyan szoftverfrissítési pontként telepítése előtt. Amikor konfigurálva van a szoftverfrissítési pont, meg kell adnia a szinkronizálási beállításokat. Configuration Manager kapcsolódik a szoftverfrissítési pont kiszolgálójának futtatja, és ugyanazokkal a beállításokkal konfigurálja a WSUS WSUS-kiszolgáló. Ha egy szoftverfrissítési pontként termékeket és besorolásokat, amely a szoftverfrissítési pont szinkronizálási beállításai részeként nem konfigurálta a konfigurálása előtt szinkronizálta WSUS, a szoftverfrissítések metaadatait a termékek és besorolások szinkronizálva az összes szoftverfrissítési metaadatokat a WSUS-adatbázisban, konfigurálta a szoftverfrissítési pont szinkronizálási beállításaitól függetlenül. Emiatt nem várt szoftverfrissítési metaadatok is lehetnek a helyadatbázisban. A kívánt viselkedést eredményező beállítást fog tapasztalni, ha közvetlenül a a WSUS felügyeleti konzoljának fel termékeket és besorolásokat, és azonnal kezdeményezik a szinkronizálást. Alapértelmezés szerint óránként a Configuration Manager kapcsolódik a WSUS szolgáltatáshoz a szoftverfrissítési ponton, és visszaállít minden beállítást, amely a Configuration Manager kívül módosították. A rendszer lejártként jelöli meg azokat a szoftverfrissítéseket, amelyek nem felelnek meg a szinkronizálási beállítások között megadott termékeknek és besorolásoknak, és törli azokat a helyadatbázisból.

 Ha a WSUS-kiszolgálót egy szoftverfrissítési pontként van konfigurálva, tudunk már nem használható önálló WSUS-kiszolgáló. Ha egy külön önálló WSUS-kiszolgáló a Configuration Manager által nem kezelt, konfigurálnia kell azt egy másik kiszolgálón.

####  <a name="BKMK_WSUSAsReplica"></a> A WSUS beállítása replikakiszolgálóként  
 Ha egy elsődleges helykiszolgálón hoz létre szoftverfrissítési pontot, nem használhat olyan WSUS-kiszolgálót, amely replikaként van beállítva. Ha a WSUS-kiszolgáló replikaként van beállítva, a Configuration Manager nem tudja konfigurálni a WSUS-kiszolgáló és a WSUS szinkronizációja is sikertelen lesz. Amikor a szoftverfrissítési pontot egy másodlagos helyen hoznak létre, a Configuration Manager konfigurálja a WSUS szolgáltatást az elsődleges szülőhelyen a szoftverfrissítési ponton futó WSUS kiszolgálót. Az elsődleges helyen elsőként telepített szoftverfrissítési pont az alapértelmezett. A hely további szoftverfrissítési pontjai az alapértelmezett szoftverfrissítési pont replikáiként vannak beállítva.  

####  <a name="BKMK_WSUSandSSL"></a> Döntés arról, hogy konfigurálja-e a WSUS szolgáltatást az SSL használatára  
 Az SSL protokoll segítségével gondoskodhat a szoftverfrissítési ponton futó WSUS biztonságáról. A WSUS az SSL segítségével hitelesíti az ügyfélszámítógépeket és az alsóbb rétegbeli WSUS-kiszolgálókat a WSUS-kiszolgáló számára. A WSUS a szoftverfrissítési metaadatok titkosítására is használja az SSL-t. Ha a WSUS biztonsága érdekében használni kívánja az SSL-t, elő kell készíteni a WSUS-kiszolgálót, mielőtt telepítené a szoftverfrissítési pontot.  

 A szoftverfrissítési pont telepítésekor és konfigurálásakor jelölje be az **SSL-kommunikáció engedélyezése a WSUS-kiszolgálóhoz** beállítást. Ellenkező esetben a Configuration Manager a WSUS szolgáltatást nem SSL használatára konfigurálja. Ha egy szoftverfrissítési ponton futó WSUS szolgáltatás számára engedélyezi az SSL használatát, a gyermekhelyeken működő szoftverfrissítési pontokon futó WSUS szolgáltatásnak szintén engedélyezni kell az SSL-kommunikációt.  

###  <a name="BKMK_ConfigureFirewalls"></a> Tűzfalak konfigurálása  
 A szoftverfrissítések a Configuration Manager központi adminisztrációs hely szoftverfrissítési pontja, amely viszont a szinkronizálási forrással kommunikál is szinkronizálhatja a szoftverfrissítéseket metaadatok futó WSUS kommunikálni. A gyermekhelyen futó szoftverfrissítési pontok a szülőhely szoftverfrissítési pontjával kommunikálnak. Ha több szoftverfrissítési pont található egy elsődleges helyen, a további szoftverfrissítési pontoknak a helyen telepített első – egyben alapértelmezett – szoftverfrissítési ponttal kell kommunikálniuk.  

 A tűzfal lehet, hogy be kell állítani a következő esetekben WSUS által használt HTTP vagy HTTPS-portok fogadását: Ha a Configuration Manager szoftverfrissítési pont és; az Internet között vállalati tűzfal Ha egy szoftverfrissítési ponttal rendelkezik, és a fölérendelt szinkronizálási forrás tartozik; vagy ha a további szoftverfrissítési pontok. A Microsoft Update szolgáltatással való kapcsolat HTTP-kommunikációhoz mindig a 80-as, HTTPS-kommunikáció esetén pedig a 443-as portot használja. A gyermek- és a szülőhely szoftverfrissítési pontjain futó WSUS-kiszolgálók közötti kapcsolathoz egyéni portot is használhat. Ha a biztonsági házirend nem engedélyezi a kapcsolatot, exportálással és importálással kell megoldania a szinkronizálást. További tájékoztatást a jelen témakör [Szinkronizálási forrás](#BKMK_SyncSource) című szakaszában olvashat. A WSUS által használt portokkal kapcsolatos további információkért lásd: [A WSUS szolgáltatásban használt portok beállításainak megállapítása a System Center Configuration Managerben](../get-started/install-a-software-update-point.md#wsus-settings).  

#### <a name="restrict-access-to-specific-domains"></a>A hozzáférés korlátozása adott tartományokra  
 Ha a szervezeti szabályok nem teszik lehetővé, hogy a portok és a protokollok minden cím számára nyitva legyenek a tűzfalon az aktív szoftverfrissítési pont és az internet között, a hozzáférést az alábbi tartományokra korlátozhatja annak érdekében, hogy a WSUS és az automatikus frissítési funkció kommunikálhasson a Microsoft Update szolgáltatással:  

-   http://windowsupdate.microsoft.com

-   http://*.windowsupdate.microsoft.com  

-   https://*.windowsupdate.microsoft.com  

-   http://*.update.microsoft.com  

-   https://*.update.microsoft.com  

-   http://*.windowsupdate.com  

-   http://download.windowsupdate.com  

-   http://download.microsoft.com  

-   http://*.download.windowsupdate.com  

-   http://test.stats.update.microsoft.com  

-   http://ntservicepack.microsoft.com  

 Elképzelhető, hogy az alábbi címeket hozzá kell adnia a két helyrendszer között található tűzfalhoz abban az esetben, ha a gyermekhelyek szoftverfrissítési ponttal rendelkeznek, vagy egy helyen távoli aktív internetes szoftverfrissítési pont működik:  

 **Szoftverfrissítési pont a gyermekhelyen**  

-   http://<*FQDN szoftverek frissítése pont a gyermekhelyen*>  

-   https://<*FQDN szoftverek frissítése pont a gyermekhelyen*>  

-   http://<*FQDN szoftverek frissítése a fölérendelt helyen lévő*>  

-   https://<*FQDN szoftverek frissítése a fölérendelt helyen lévő*>  

##  <a name="BKMK_SyncSettings"></a> A szinkronizálási beállítások tervezése  
 A szoftverfrissítések szinkronizálását a Configuration Managerben az Ön által konfigurált feltételeknek megfelelő szoftverfrissítési metaadatok lekérését jelenti. A szoftverfrissítések szinkronizálását a Microsoft Update szolgáltatásból a hierarchia legfelső szintű helye végzi, amely a központi adminisztrációs hely vagy egy önálló elsődleges hely lehet. Lehetősége van a legfelső szintű hely meglévő WSUS-kiszolgáló, a Configuration Manager hierarchiában nem szinkronizálja a szoftverfrissítési pont konfigurálása. A gyermek elsődleges helyek a központi adminisztrációs helyen lévő szoftverfrissítési pontról szinkronizálják a szoftverfrissítési metaadatokat. A szoftverfrissítési pontok telepítése és konfigurálása előtt olvassa el az alábbi szakaszt a szinkronizálási beállítások megtervezéséhez.  

###  <a name="BKMK_SyncSource"></a> Szinkronizálási forrás  
 A szoftverfrissítési pont szinkronizálási forráshoz kapcsolódó beállításai határozzák meg, hogy a szoftverfrissítési pont honnan kéri le a szoftverfrissítési metaadatokat, és azt, hogy a rendszer létrehozzon-e WSUS jelentési eseményeket a szinkronizálási folyamat során.  

-   **Szinkronizálási forrás:** A szoftverfrissítési pont a legfelső szintű helyen konfigurálja a szinkronizálási forrást a Microsoft Update alapértelmezés szerint. A felső szintű hely meglévő WSUS-kiszolgálóról is szinkronizálható. A gyermek elsődleges helyek szoftverfrissítési pontjának szinkronizálási forrásaként a rendszer alapértelmezés szerint a központi adminisztrációs hely szoftverfrissítési pontját konfigurálja.  

    > [!NOTE]  
    >  Az elsődleges helyen telepített első – egyben alapértelmezett – szoftverfrissítési pont a központi adminisztrációs hellyel szinkronizál, az elsődleges hely további szoftverfrissítési pontjai pedig a hely alapértelmezett szoftverfrissítési pontjával.  

     Ha egy szoftverfrissítési pont nem csatlakozik a Microsoft Update szolgáltatáshoz vagy a fölérendelt frissítési kiszolgálóhoz, le is tilthatja a konfigurált forrással való szinkronizálást, és a WSUSUtil eszköz exportálási és importálási funkciójával is szinkronizálhatja a szoftverfrissítéseket. Erről bővebben lásd: [Szoftverfrissítések szinkronizálása leválasztott szoftverfrissítési pontról](../get-started/synchronize-software-updates-disconnected.md).  

-   **WSUS jelentési események:** Az ügyfélszámítógépeken a Windows Update Agent hozhat létre WSUS jelentési használt eseményüzenetek. Ezek az események nem használja a szoftverfrissítést a Configuration Manager alkalmazást, és ezért a **ne hozzon létre WSUS jelentési események** beállítás alapértelmezés szerint. Ha ezekre az eseményekre nincs szükség, az ügyfélszámítógép csak a szoftverfrissítések értékelési és megfelelőségi vizsgálatai közben csatlakozik a WSUS-kiszolgálóhoz. Ha az eseményekre szükség van a Configuration Manager szoftverfrissítési funkcióján kívüli jelentések, akkor módosíthatja ezt a beállítást, hogy hozzon létre WSUS jelentési eseményeket.  

###  <a name="BKMK_SyncSchedule"></a> Szinkronizálás ütemezése  
 A szinkronizálási ütemezés csak a legfelső szintű helyen a Configuration Manager-hierarchiában a szoftverfrissítési ponton konfigurálható. A szinkronizálási ütemezés konfigurálása esetén a szoftverfrissítési pont a megadott napon és időpontban szinkronizál a forrással. Az egyéni ütemezés lehetővé teszi a szoftverfrissítések adott napon és időpontban való szinkronizálását, amikor a WSUS-kiszolgáló, a helykiszolgáló és a hálózat terhelése alacsony, például hetente egyszer hajnali 2:00-kor. Másik lehetőségként is kezdeményezhető a legfelső szintű hely szinkronizálási használatával a **szoftverfrissítések szinkronizálása** művelet a **minden szoftverfrissítés** vagy **szoftverfrissítési csoportok** csomópont a Configuration Manager konzolon.  

> [!TIP]  
>  A környezetnek megfelelő időszakra ütemezze a szoftverfrissítések szinkronizálását. Gyakori például, hogy a szoftverfrissítések szinkronizálásának időpontját röviddel a Microsoft rendszeres biztonsági frissítései után ütemezik, amelyek minden hónap második keddjén jelennek meg („Frissítő kedd”). Jellemző még például az is, hogy a szoftverfrissítések szinkronizálását napi rendszerességgel ütemezik arra az időpontra, amikor szoftverfrissítésekkel az ügyfelekre juttatják az Endpoint Protection definíció- és keresőmotor-frissítéseit.  

 Miután a szoftverfrissítési pont sikeresen végrehajtotta a szinkronizálást, a rendszer szinkronizálási kérelmet küld a gyermekhelyekre. Ha egy elsődleges helyen több szoftverfrissítési pont van, a rendszer az összesre szinkronizálási kérelmet küld. A folyamat a hierarchia összes helyén megismétlődik.  

###  <a name="BKMK_UpdateClassifications"></a> Frissítési besorolások  
 Minden szoftverfrissítéshez tartozik egy frissítési besorolás, amely a különböző típusú frissítések rendszerezésében nyújt segítséget. A szinkronizálási folyamat a megadott besorolás szoftverfrissítési metaadatait szinkronizálja. A Configuration Manager lehetővé teszi a szoftverfrissítések szinkronizálását a következő frissítési besorolásokkal:  

-   **Kritikus frissítések:** Megadja, széles körben kiadott frissítés egy adott probléma, amely kritikus, nem biztonsági hiba kezelésére szolgál.  

-   **Definíciófrissítések:** Megadja a vírus- vagy egyéb definíciós fájlok frissítése.  

-   **Szolgáltatáscsomagok:** Adja meg az új termékszolgáltatások, amelyek egy termékkiadásba és a szolgáltatás kívül terjesztett, amelyek általában bekerülnek a soron következő teljes termékkiadásba.  

-   **Biztonsági frissítések:** Megadja, széles körben kiadott frissítés egy termékspecifikus biztonsági problémára.  

-   **Szervizcsomagok:** Meghatározza az adott alkalmazásnál alkalmazott gyorsjavítások összesített csomagja. A gyorsjavítások lehetnek biztonsági frissítések, kritikus frissítések, szoftverfrissítések stb.  

-   **Eszközök:** Megadja a szolgáló segédprogramok vagy funkciók, amelyek egy vagy több feladat végrehajtására.  

-   **Kumulatív frissítések:** Megadja az egyszerű telepítés egy csomagba gyorsjavítások összesített csomagja. A gyorsjavítások lehetnek biztonsági frissítések, kritikus frissítések, szoftverfrissítések stb. A kumulatív frissítések általában egy konkrét területre összpontosítanak, például a biztonságra vagy egy termékösszetevőre.  

-   **Frissítések:** Megadja egy alkalmazás vagy a jelenleg telepített fájl frissítése.  

 A frissítési besorolások beállításainak konfigurálása csak a legfelső szintű helyen lehetséges. A frissítési besorolások beállításai a gyermekhelyek szoftverfrissítési pontjain nem konfigurálhatók, mivel a szoftverfrissítési metaadatokat a rendszer a felső szintű helyről replikálja a gyermek elsődleges helyekre. A frissítési besorolások kiválasztásakor tartsa szem előtt, hogy minél több besorolást választ ki, annál több ideig tart a szoftverfrissítési metaadatok szinkronizálása.  

> [!WARNING]  
>  Javasoljuk, hogy a szoftverfrissítések első szinkronizálása előtt törölje az összes besorolás jelölését. A kezdeti szinkronizálást követően a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen válassza ki a besorolásokat, majd indítsa el újra a szinkronizálást.  

###  <a name="BKMK_UpdateProducts"></a> Termékek  
 A szoftverfrissítések metaadatai meghatároznak egy vagy több terméket, amelyre a frissítés alkalmazható. A termék egy operációs rendszer vagy alkalmazás adott kiadását jelenti. Termék például a Microsoft Windows Server 2008. A termékcsalád az az operációs rendszer vagy alkalmazás, amelyből az egyes termékek származnak. Termékcsalád például a Microsoft Windows, amelynek az egyik tagja a Microsoft Windows Server 2008. Termékcsaládot is választhat, vagy konkrét termékeket is kijelölhet egy adott termékcsaládon belül.  

 Szoftverfrissítés több termékre érvényes, és legalább az egyik terméket kijelölte szinkronizálásra, ha az összes termék megjelenik a Configuration Manager konzolon még akkor is, ha bizonyos termékek nem lettek kiválasztva. Ha például a Windows Server 2012 az egyetlen operációs rendszer, amelyre előfizetett, egy adott szoftverfrissítés pedig a Windows Server 2012 és a Windows Server 2012 Datacenter Edition kiadásra érvényes, akkor mindkét termék szerepelni fog a helyadatbázisban.  

 A termékbeállítások konfigurálása csak a legfelső szintű helyen lehetséges. A termékbeállítások a gyermekhelyek szoftverfrissítési pontjain nem konfigurálhatók, mivel a szoftverfrissítési metaadatokat a rendszer a felső szintű helyről replikálja a gyermek elsődleges helyekre. Termékek kiválasztásakor tartsa szem előtt, hogy minél több terméket választ ki, annál több ideig tart a szoftverfrissítési metaadatok szinkronizálása.  

> [!IMPORTANT]  
>  A Configuration Manager-termékek és termékcsaládok, hogy Ön az alkalmazás első telepítésekor a szoftverfrissítési pont listáját tárolja. Termékek és termékcsaládok, amelyek a Configuration Manager kiadása után nem feltétlenül érhető el, amíg be nem fejezi a szoftverfrissítések szinkronizálását, frissül a választható termékek és termékcsaládok, amelyről választhat listája kiválasztásához. Javasoljuk, hogy a szoftverfrissítések első szinkronizálása előtt törölje az összes termék jelölését. A kezdeti szinkronizálást követően a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen válassza ki a termékeket, majd indítsa el újra a szinkronizálást.  

###  <a name="BKMK_SupersedenceRules"></a>Helyettesítési szabályok  
 Amikor egy szoftverfrissítés egy másik szoftverfrissítés helyébe lép (helyettesíti, felülírja azt), általában legalább egyet végrehajt az alábbiak közül:  

-   Javít, fejleszt vagy frissít egy korábbi frissítésekben már megjelent javítást.  

-   Javítja a frissítés telepítésének jóváhagyása esetén az ügyfélszámítógépekre telepített, felülírt frissítési fájlcsomag hatékonyságát. A felülírt frissítés tartalmazhat például olyan fájlokat, amelyek már nem relevánsak a javítás vagy az új frissítés által támogatott operációs rendszer szempontjából, ezért ezeket a fájlokat a frissítést felülíró fájlcsomag nem tartalmazza.  

-   Frissíti egy termék újabb verzióit. Más szóval egy termék régebbi verzióira vagy konfigurációira már nem alkalmazható verziókat frissíti. A frissítések más frissítéseket is felülírhatnak, ha azokat a nyelvi támogatás bővítése érdekében módosították. Előfordulhat például, hogy a Microsoft Office termékfrissítésének egy újabb verziójával megszűnik egy régebbi operációs rendszer támogatása, azonban újabb támogatott nyelvek kerülhetnek a frissítés eredeti kiadásába.  

 A szoftverfrissítési pont tulajdonságai között beállíthatja, hogy a felülírt szoftverfrissítések azonnal lejárjanak, ami megakadályozza, hogy bekerüljenek az új központi telepítésekbe, míg a már meglévő központi telepítéseket megjelöli, és ezzel jelzi, hogy egy vagy több lejárt szoftverfrissítést tartalmaznak. Ehelyett ugyanakkor beállíthatja azt is, hogy a felülírt szoftverfrissítések csak adott idő elteltével járjanak le, így továbbra is telepítheti őket központilag. Vegyük például a következő helyzeteket, amelyekben szüksége lehet egy felülírt szoftverfrissítés központi telepítésére:  

-   Egy felülíró szoftverfrissítés egy operációs rendszernek csak az újabb verzióit támogatja, és néhány ügyfélszámítógépen az operációs rendszer korábbi verziói futnak.  

-   Egy felülíró szoftverfrissítés alkalmazhatósága korlátozottabb, mint a felülírt szoftverfrissítésé. Ebben az esetben nem lenne megfelelő egyes ügyfélszámítógépek számára.  

-   Egy felülíró szoftverfrissítés központi telepítését nem hagyták jóvá az Ön által használt munkakörnyezetben.  

###  <a name="BKMK_UpdateLanguages"></a> Nyelvek  
 A szoftverfrissítési pont nyelvi beállításai lehetővé teszik, hogy konfigurálja a nyelveket, amelyekhez az összefoglaló információk (a szoftverfrissítés metaadatai) szinkronizálásra kerülnek szoftverfrissítések esetén, illetve a szoftverfrissítési fájlok nyelveit, amelyek a szoftverfrissítéshez letöltésre kerülnek.  

#### <a name="software-update-file"></a>Szoftverfrissítési fájl  
 A szoftverfrissítési pont tulajdonságai között található **Szoftverfrissítés fájlja** beállításban megadott nyelvek határozzák meg azt az alapértelmezett nyelvkészletet, amely rendelkezésére áll, amikor szoftverfrissítéseket tölt le egy helyre. Az alapértelmezés szerint kiválasztott nyelveket a szoftverfrissítések minden egyes letöltésénél vagy központi telepítésénél módosíthatja. A letöltési folyamat során a konfigurált nyelvekhez tartozó szoftverfrissítési fájlok letöltődnek a központi telepítési csomag forráshelyére, ha a szoftverfrissítési fájlok elérhetők a kiválasztott nyelven. Ezt követően a rendszer a helykiszolgálón lévő tartalomtárba, majd a csomaghoz konfigurált terjesztési pontokra másolja a fájlokat.  

 A szoftverfrissítési fájl nyelvi beállításainál az adott környezetben leggyakrabban használt nyelveket kell megadni. Ha a helyhez társított ügyfélszámítógépek leggyakrabban például az angol és a japán nyelvet használják az operációs rendszerhez vagy az alkalmazásokhoz, és a helyen használt egyéb nyelvek száma csekély, akkor a szoftverfrissítés letöltésekor vagy központi telepítésekor válassza az angol és a japán nyelvet a **Szoftverfrissítés fájlja** oszlopban, és a többi nyelvet törölje. Ez lehetővé teszi, hogy az alapértelmezett beállításokat használja a központi telepítés **Nyelv kiválasztása** lapján, és varázslókat töltsön le. Ezzel a szükségtelen frissítési fájlok letöltését is megelőzi. Ez a beállítás konfigurálni kell a Configuration Manager-hierarchia minden szoftverfrissítési pontjánál.  

#### <a name="summary-details"></a>Összefoglaló információk  
 A szinkronizálási folyamat közben a szoftverfrissítések összefoglaló információi (a szoftverfrissítés metaadatai) a megadott nyelveken frissülnek. A metaadatok a szoftverfrissítésről adnak információt: név, leírás, a frissítés által támogatott termékek, frissítési besorolás, cikk azonosítója, letöltési URL, alkalmazhatósági szabályok stb.  

 Az összefoglaló információkkal kapcsolatos beállítások konfigurálása kizárólag a legfelső szintű helyen történik. Az összefoglaló információk konfigurálása azért nem a gyermekhelyeken lévő szoftverfrissítési ponton történik, mert a szoftverfrissítések metaadatai a központi adminisztrációs helyről replikálódnak ezekre a helyekre fájlalapú replikáció révén. Az összefoglaló információk nyelveinek kiválasztásakor csak olyan nyelveket válasszon, amelyekre szüksége van az adott környezetben. Minél több nyelvet választ ki, annál több ideig tart a szoftverfrissítési metaadatok szinkronizálása. A Configuration Manager szoftverfrissítési metaadatokat, amelyben a Configuration Manager konzol futó operációs rendszer területi beállításaiban jeleníti meg. Ha a szoftverfrissítések honosított tulajdonságai nem érhetők el az operációs rendszer területi beállításaiban, a szoftverfrissítés adatai angolul jelennek meg.  

> [!IMPORTANT]  
>  Fontos, hogy az összefoglaló információk nyelveit, amelyre szüksége lesz a Configuration Manager-hierarchiában található összes választotta. Amikor a legfelső szintű helyen lévő szoftverfrissítési pont szinkronizál a szinkronizálási forrással, az összefoglaló információkhoz választott nyelvek határozzák meg a beolvasott szoftverfrissítési metaadatokat. Ha módosítja az összefoglaló információk nyelveit, miután a szinkronizálás legalább egyszer lefutott, akkor az összefoglaló információk módosított nyelveihez csak az új vagy frissített szoftverfrissítések esetén történik meg a szoftverfrissítési metaadatok lekérése. A már szinkronizált szoftverfrissítések nem frissülnek a módosított nyelvekhez tartozó, új metaadatokkal, kivéve, ha megváltozott a szoftverfrissítés a szinkronizálási forráson.  

##  <a name="BKMK_MaintenanceWindow"></a> Szoftverfrissítések számára kijelölt karbantartási időszak tervezése  
 Kijelölhet egy, a szoftverfrissítések telepítésére szolgáló karbantartási időszakot. Ezzel a módszerrel az általános karbantartási időszakon kívül egy másik karbantartási időszakot is konfigurálhat a szoftverfrissítések telepítéséhez. Ha általános és szoftverfrissítésre szolgáló karbantartási időszakot is konfigurál, az ügyfelek csak a szoftverfrissítésre kijelölt időszakban telepítenek frissítéseket. További információ a karbantartási időszakok: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="BKMK_RestartOptions"></a> Újraindítási lehetőségek Windows 10-ügyfelek számára szoftverfrissítés telepítése után
Amikor egy szoftverfrissítés, amelyhez újraindítás van telepítve, a Configuration Manager és a számítógépen telepített, függőben lévő újraindul, és újraindítást kérő párbeszédpanelt jelenik meg.

A Configuration Manager 1606-os verziójával kezdődően a Windows 10-et futtató számítógépek Windows-energiagazdálkodási lehetőségei között rendelkezésre áll a **Frissítés és újraindítás**és a **Frissítés és leállítás** lehetőség a Configuration Manager szoftverfrissítésével kapcsolatos függőben lévő újraindítás esetén. E két lehetőség valamelyikének választása esetén az újraindítási párbeszédpanel nem jelenik meg a számítógép újraindítását követően.

A korábbi verziókban a Configuration Manager, amikor függőben egy újraindítás a Windows 8 és újabb rendszerű számítógépek, és állítsa le és indítsa újra a számítógépet a Windows energiagazdálkodási lehetőségek (ahelyett, hogy az újraindítás párbeszédpanelről), a újraindítás párbeszédpanel marad után a számítógép újraindul, és a számítógép továbbra is újra kell indítania a konfigurált határidő lejártakor.

## <a name="next-steps"></a>További lépések
Ha azt tervezi, a szoftverfrissítések, tekintse meg a [a szoftver előkészítése frissíti management](../get-started/prepare-for-software-updates-management.md).

