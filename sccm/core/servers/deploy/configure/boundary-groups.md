---
title: "A határcsoportok megadása |} Microsoft Docs"
description: "Beléptetésihely-rendszerek a System Center Configuration Manager ügyfelek hivatkozó határcsoportok ismertetése."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 5684fd4fbfd0ffb8f3ffbcfa122eef3dafd77327
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>A határcsoportok konfigurálása a System Center Configuration Managerhez


*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Határ csoportok segítségével a System Center Configuration Managerben logikailag csoportosíthatja az egymáshoz kapcsolódó hálózati helyeket ([határok](/sccm/core/servers/deploy/configure/boundaries)) könnyebb az infrastruktúra kezelését. Ahhoz, hogy egy határcsoport használhatóvá váljon, előbb határokat kell hozzárendelnie.

Alapértelmezés szerint a Configuration Manager létrehoz egy alapértelmezett helyhatárcsoportba az egyes helyeken.

> [!IMPORTANT]  
>  **A határ groups szakaszában és annak gyermek szakaszokban található információk 1610 vagy újabb verziójára vonatkozik.** Ez a tartalom kell lennie a határcsoportokhoz a frissítés verziójával bevezetett tervezési módosítások jellemző módosítva lett.
>
> **Ha 1610 korábbi verziók**, lásd: [határcsoportjainak, System Center Configuration Manager verziója 1511-es, a 1602-es és a 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) használja, és határcsoportok konfigurálása ezekkel a termék verziókkal kapcsolatos.

A határcsoportok konfigurálásához határok (hálózati helyek) és a helyrendszer-kiszolgálókat, például a terjesztési pontok, a határcsoporthoz társítani. Ezzel a megoldással társítása ügyfelek helyrendszer-kiszolgálókon, például található terjesztési pontok közelében a hálózaton lévő ügyfelek.

Ha ugyanazt a határt több határcsoporthoz hozzárendelni, és rendelje hozzá a ugyanazon a helyen rendszer kiszolgálók, például a terjesztési pontok, több határcsoporthoz, hely rendszerek rendelkezésre állásának javítása a hálózati helyek szélesebb köre.

Az ügyfelek használhatják a határcsoporthoz:  

-   Automatikus helyhozzárendelés  
-   Egy helyrendszer-kiszolgálóra, amely képes biztosítani a szolgáltatás található többek között:
    - A tartalom helyéhez a terjesztési pontokon
    -    Szoftverfrissítési pontok (1702 verziójával kezdődően)
    - Állapotáttelepítési pontjai
    - Előnyben részesített felügyeleti pontok (ha előnyben részesített felügyeleti pontokat használja, engedélyeznie kell ezt a beállítást a hierarchiához és helyett a határcsoport konfigurációjának. Lásd: [előnyben részesített felügyeleti pontok használatának engedélyezése](#to-enable-use-of-preferred-management-points) ebben a témakörben.)

##  <a name="boundary-groups-and-relationships"></a>A határcsoportok és kapcsolatok
A határcsoportokhoz a hierarchiában akkor is lehet rendelni:

-  Egy vagy több határt. Ha egy ügyfél hálózati helye a van definiálva, a határ egy adott határcsoporthoz hozzárendelt, amelyek neve a **aktuális** határcsoporthoz. Egy ügyfél aktuális egynél több határcsoporthoz is rendelkezik.
- Egy vagy több helyrendszer-szerepkörök.  Ügyfelek mindig használhatják az aktuális határcsoporthoz társított helyrendszer-szerepkörök. Attól függően, hogy további beállításokat előfordulhat, hogy tudják további határcsoportokban helyrendszer-szerepkörök használatához.  

Egyes határcsoportokban hoz létre konfigurálhatja egy egyirányú hivatkozás egy másik határcsoportba. A kapcsolat neve a **kapcsolat**. A határcsoportok hivatkozott nevezzük **szomszédos** határcsoportokat. A határcsoport rendelkezhet több kapcsolatnak is tagja, az adott szomszéd határcsoportban.

Minden kapcsolat konfigurációja határozza meg, ha ügyfél, amely nem talál egy elérhető helyrendszer-kiszolgálóra az aktuális határcsoportban megkezdődhet az elérhető helyrendszer található szomszédos határcsoportban kereséséhez. Ez a keresés további csoportok nevezik **tartalék**.

## <a name="fallback"></a>Tartalék
Problémák megelőzése érdekében az ügyfelek Ha az aktuális határcsoportban nem talál egy elérhető helyrendszer tartalék viselkedését meghatározó határcsoportok közötti kapcsolatok meghatározása. Tartalék lehetővé teszi, hogy egy ügyfél, a keresés kiterjesztése az elérhető helyrendszer található további határcsoporthoz.

Kapcsolat egy határcsoport tulajdonságainak vannak konfigurálva **kapcsolatok** fülre. Ha kapcsolatot konfigurált, adja meg egy hivatkozást szomszédos határcsoportba. Az egyes helyrendszer-szerepkör, amely támogatott szomszédos határcsoportra tartalék független beállításait konfigurálhatja. Tegyük fel Ha egy adott határcsoporthoz kapcsolatot konfigurált beállíthatja tartalék terjesztési pontok helyett 120 az alapértelmezett 20 perc után. Lásd: [határcsoportok használatának példája](#example-of-using-boundary-groups) szélesebb körű például.

Ha egy ügyfél az elérhető helyrendszer-szerepkör a jelenlegi határcsoportban található, az ügyfél a tartalék idő után mennyi ideig elkezdődne keresés egy adott szomszédos határcsoporthoz társított elérhető helyrendszer meghatározására használja.  

Amikor egy ügyfél nem találja az elérhető helyrendszer, és kizár a szomszédos határcsoportok kereséséhez kezdődik, az növeli a elérhető helykiszolgálókról, használhat olyan módon, hogy a határcsoportok, és azok konfigurációja van definiálva.

- A határcsoport rendelkezhet egynél több kapcsolattal. Ez lehetővé teszi az egyes helyrendszer után a különböző időszakokra, más szomszédoknak tartalék konfigurálását.    
- Az ügyfelek csak tartalék lesz, amely egy közvetlen az aktuális határcsoportot szomszéd határcsoportba.
- Amikor egy ügyfél több határcsoporthoz is tagja, az aktuális határcsoporthoz, hogy az ügyfél határcsoportjaihoz Uniója típusúként van definiálva. Hogy az ügyfél eredeti határcsoportokhoz bármelyikének szomszédoknak majd tartalék is.

### <a name="the-default-site-boundary-group"></a>Az alapértelmezett helyhatárcsoportba
A határcsoportok létrehozása mellett minden hely egy alapértelmezett hely határcsoporthoz a Configuration Manager által létrehozott rendelkezik. Ez a csoport neve ***alapértelmezett –--Helyhatárcsoportba&lt;sitecode >***. A csoport a helynek az ABC volna neve például *alapértelmezett –--Helyhatárcsoportba&lt;ABC >.*

Mindegyik határcsoport létrehozása a Configuration Manager automatikusan hoz egy implicit alapértelmezett webhely határcsoportokhoz a hierarchiában.
-    Az implicit hivatkozás a beállítás alapértelmezett tartalék az aktuális határcsoportban a hely alapértelmezett határcsoporthoz, amely alapértelmezett tartalék ideje 120 perc.
-    Ügyfelek, amelyek nincsenek a hierarchiában egyetlen határcsoporthoz társított határra a hozzájuk rendelt hely az alapértelmezett helyhatárcsoportba segítségével azonosíthatja a érvénytelen helyrendszerszerepkörök használhatnak.

Az alapértelmezett hely határcsoporthoz tartalék kezelése:
- Keresse meg a hely alapértelmezett határcsoporthoz tulajdonságai, és módosítsa az értékeket a a **alapértelmezett viselkedés** fülre. Itt alkalmazása végrehajtott módosítások *összes* hallgatólagos ehhez a határcsoporthoz mutató hivatkozásokat tartalmaz. Ezek a beállítások konfigurálásakor a explicit hivatkozás az alapértelmezett hely határcsoporthoz a másik határcsoport felülbírálható lesz.
- Keresse meg a létrehozott határcsoport tulajdonságai, és módosítsa az alapértelmezett hely határcsoporthoz mutató explicit hivatkozás értékeit. Ha egy új idő tartalék vagy blokk tartalék percben, ez a módosítás csak a konfigurált hivatkozás hatással van. Az explicit hivatkozás konfigurációk felülírják a a **alapértelmezett viselkedés** egy alapértelmezett helyhatárcsoportba lapján.


## <a name="site-assignment"></a>Helyhozzárendelés  
 Mindegyik határcsoportnál konfigurálhat egy hozzárendelt helyet az ügyfelek számára.  

-   Az automatikus helyhozzárendelést használó, újonnan telepített ügyfelek lesz az ügyfél aktuális hálózati helyüket tartalmazó határcsoporthoz hozzárendelt helyhez csatlakoznak.  
-   A hely hozzárendelését követően az ügyfél nem módosítja a helyhozzárendelését, amikor hálózati helye módosul. Például ha az ügyfél egy határcsoportban, amelyhez eltérő helyhozzárendelés határ által képviselt új hálózati helyre barangol, az ügyfél hozzárendelt helye változatlan marad.  
-   Amikor az Active Directory-rendszerfelderítés új erőforrást derít fel, a felderített erőforrásra vonatkozó hálózati információkat a határcsoportokban található határokhoz képest értékeli ki. Ez a folyamat az új erőforrást egy hozzárendelt helyhez társítja, és ezt tudja használni az ügyfélleküldéses telepítési mód.  
-   Ha egy határ több, különböző hozzárendelt helyekkel rendelkező határcsoport tagja, az ügyfelek véletlenszerűen választanak a helyek között.  
-   A határcsoportok hozzárendelt helyének módosítása csak az új hely-hozzárendelési műveletekre van hatással. A korábban egy helyhez már hozzárendelt ügyfelek nem értékelik újra a helyhozzárendelésüket a határcsoport konfigurációjában (vagy a saját hálózati helyükön) végbement változások alapján.  

Az ügyfelek helyhozzárendeléséről kapcsolatos további információkért lásd: [automatikus helyhozzárendelés használata számítógépekhez](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) a [ügyfelek hozzárendelése a System Center Configuration Manager hely](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Terjesztési pontok

Amikor egy ügyfél a terjesztési pont helyét, a Configuration Manager az ügyfélnek elküld egy listát, amely tartalmazza a megfelelő típust a helyrendszeren, amelyet az ügyfelek aktuális hálózati helyét tartalmazó határcsoporthoz társított:

-   **Szoftverterjesztés közben**, az ügyfelek kérnek egy helyet a telepítési tartalom elérhető egy terjesztési pontot, vagy más érvényes tartalomforrás (például az ügyfél a társ-gyorsítótárazás).

-   **Operációs rendszer központi telepítése során**, az ügyfelek kérnek egy helyet elküldeni vagy fogadni az állapotáttelepítési adatokat.  

A tartalomterjesztés során, ha egy ügyfél tartalmat, amely nem érhető el az aktuális határcsoportban forrásból kér az ügyfél továbbra is, hogy közben az aktuális határcsoportban különböző tartalomforrások a szomszédos határcsoportban vagy az alapértelmezett helyhatárcsoportba tartalék időszak eléréséig tartalmat igénylő. Ha az ügyfél még nem talált meg a tartalmat, majd bővíti az tartalomforrás a szomszédos határcsoportok felvenni a keresést.

Azonban a tartalom terjesztése igény szerinti és egy terjesztési pontba, amennyiben az ügyfél által kért rendszeren nem érhető el, ha a folyamat az adott terjesztési pontra történő tartalomátvitelhez kezdődik, és előfordulhat, hogy az ügyfél megkeresi, hogy a kiszolgáló tartalomforrásként visszaváltás szomszédos határcsoportban használata előtt.

## <a name="software-update-points"></a>Szoftverfrissítési pontok
Ügyfelek 1702 verziójával kezdve új szoftverfrissítési pontot kereséséhez használja a határcsoportok. Azok a kiszolgálók egy ügyfél található vezérlőhöz eltérő határcsoportokban egyes szoftverfrissítési pontján adhat hozzá.

Előtt 1702 verziójából származó frissítésekor minden meglévő szoftverfrissítési pontok kerülnek az egyes helyeken alapértelmezett helyhatárcsoportba. Ezzel a megoldással a frissítés előtti viselkedését, ahol az ügyfelek kell választania egy szoftverfrissítési pontot a rendelkezésre álló szoftverfrissítési pontokról, amelyek a hierarchia már konfigurálta a készletből.  Ez a viselkedés megmarad, amíg a felhasználó eltérő határcsoportokban ellenőrzött és tartalék viselkedés egyes szoftverfrissítési pontok hozzáadása.

Ha egy új helyet telepít, amely 1702 verzióját futtatja, vagy később, hozzá kell rendelnie szoftverfrissítési pontok egy határcsoportban előtt ügyfelek keresése és használhatja őket.


A szoftverfrissítési pontokhoz tartozó tartalék például más helyrendszerszerepköröket van konfigurálva, azonban az alábbi korlátozásokkal rendelkezik:
- **Új ügyfelek határcsoportok segítségével válassza ki a szoftverfrissítési pontok.** 1702 verzió telepítése után új ügyfeleket telepít azoktól, amelyeket a konfigurált határcsoportok társított válassza ki a szoftverfrissítési pont.

  Ez a felváltja a korábbi viselkedését, ahol az ügyfelek a szoftverfrissítési pont véletlenszerűen egy listából választhatja ki, amely az ügyfél erdőjében megosztani.

- **Korábban telepített ügyfelek továbbra is az aktuális szoftverfrissítési pont tartalék csak egy új kereséséhez.** Ügyfelek, amelyeket korábban telepítettek és, hogy már rendelkezik egy szoftverfrissítési pont továbbra is a szoftverfrissítési pont használatára, amíg a kiszolgáló nem érhető el. Ez magában foglalja a szoftverfrissítési pontot, amely nincs az ügyfél aktuális határcsoporthoz társított további használatához.

  Ha egy ügyfél, amely már rendelkezik egy szoftverfrissítési pont nem sikerült elérni, az ügyfél is egy másik található majd tartalék. Tartalék használata esetén az ügyfél fogad az összes szoftverfrissítési pontok listája az aktuális határcsoporthoz. Ha az nem található elérhető kiszolgálót 120 perc, a következőket hajtja végre majd tartalék szomszédos határcsoportjait és az alapértelmezett hely határcsoporthoz. Mindkét határcsoportokhoz tartalék egyszerre oka az, hogy a szoftverfrissítési pontok szomszédos csoportok tartalék idő 120 percre van beállítva, és nem módosítható. 120 perc egyben az alapértelmezett hely határcsoporthoz tartalékként használt alapértelmezett időszak. Amikor egy ügyfél visszaáll mindkét szomszédos, és alapértelmezett helyhatárcsoportba, az ügyfél megkísérel kapcsolatba lépni a szomszédos határcsoport a szoftverfrissítési pontok előtt próbálja használni az alapértelmezett helyhatárcsoportba közül.

  Egy meglévő szoftverfrissítési pontot még akkor is, ha a kiszolgáló nem az ügyfél aktuális határcsoportban folyamatos használata szándékos. Ennek az az oka megváltoztak a szoftverfrissítési pont is nagy igénybe vett sávszélesség eredményezi, mivel az ügyfél szinkronizálja az adatokat az új szoftverfrissítési ponttal. Az átmeneti késleltetés elkerülése érdekében úgy az ügyfelek új szoftverfrissítési kapcsolót frissítenie kell pont egyidejűleg a hálózaton mágneses erősítő segítségével.

- **Tartalék idő konfigurációi:**  Tartalék konfigurációi a más helyrendszerszerepkörökkel szemben szoftverfrissítési pontok még támogatja konfigurálható időt percben. Ehelyett tartalék működése a következők:  
  - **Tartalék idő (percben):**  Ez a beállítás szürkén jelenik meg a szoftverfrissítési pontokhoz, és nem is konfigurálható. Érték 120 perc.
  -     **Soha ne tartalék:** Ez a konfiguráció használatakor a szoftverfrissítési pont szomszédos határcsoportba tartalék tilthatja le.

## <a name="preferred-management-points"></a>Előnyben részesített felügyeleti pontok

 Az előnyben részesített felügyeleti pontok lehetővé teszik, hogy az ügyfél azonosítson egy olyan felügyeleti pontot, amely az ügyfél aktuális hálózati helyéhez (határához) van társítva.  

-   Az ügyfél megkísérel előnyben részesített felügyeleti pontot használ a hozzárendelt helyről egy felügyeleti pont használatához a hozzárendelt helyről, amely nincs konfigurálva előnyben részesítettként.  
-   Használja ezt a beállítást, engedélyezi azt a hierarchiában, és úgy konfigurálnia a határcsoportokat az egyes elsődleges helyeken kell lennie az adott határcsoport társított határaihoz társított felügyeleti pontokat tartalmazza.  
-   Ha előnyben részesített felügyeleti pontok vannak konfigurálva, és egy ügyfél rendszerezi a felügyeleti pontok listáját, az ügyfél az előnyben részesített felügyeleti pontokat a hozzárendelt felügyeleti pontok listáját (amely tartalmazza az ügyfél hozzárendelt helyének összes felügyeleti pontja) tetején helyezi.  

> [!NOTE]  
>  Előfordulhat, hogy egy ügyfél barangolás közben (azaz hálózati helyének változtatásakor, például amikor egy laptopot egy távoli irodába szállítanak) a helyi felügyeleti pontot (vagy egy proxy felügyeleti pontját) használja, mielőtt megkísérelné egy felügyeleti pont használatát a hozzárendelt helyről (amely az előnyben részesített felügyeleti pontokat tartalmazza).  Lásd: [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) további információt.  

### <a name="overlapping-boundaries"></a>Átfedésben lévő határok  
 Configuration Manager a tartalmak helyénél támogatja az átfedésben lévő határokat tartalmazó konfigurációkat:  

-   **Amikor egy ügyfél tartalmat igényel**, és az ügyfél hálózati helye több határcsoporthoz tartozik, a Configuration Manager elküldi az ügyfélnek az összes olyan terjesztési pontot, amelyen megtalálható a tartalom listáját.  
-   **Amikor egy ügyfél kiszolgálót kér, hogy elküldeni vagy fogadni a állapotáttelepítési adatainak**, és az ügyfél hálózati helye több határcsoporthoz tartozik, a Configuration Manager elküldi az ügyfélnek az összes olyan állapotáttelepítési pont az ügyfél aktuális hálózati helyét tartalmazó határcsoporthoz társított listáját.  

Ez a viselkedés lehetővé teszi, hogy az ügyfél a legközelebbi kiszolgálót válassza ki, ahonnan a tartalmat vagy az állapotáttelepítési adatokat lekérdezi.  



## <a name="example-of-using-boundary-groups"></a>A határcsoportok használatával – példa
Az alábbi példában egy ügyfelet keres a tartalmat egy terjesztési pontról. Ez a példa alkalmazható más helyrendszerszerepköröket, amelyek használják a határcsoportokat. Azonban mivel a szoftverfrissítési pontok vonatkozik, vegye figyelembe, hogy szoftverfrissítési pontok nem támogatja egyszerre konfigurációjának szomszédos csoporthoz tartalékként percben, és mindig 120 perc.

Három határcsoportok határok vagy helyrendszer-kiszolgálók nem használó létrehozásával:
-    Terjesztési pontok DP_A1 és a csoporthoz tartozó DP_A2 BG_A csoport
-    Terjesztési pontok DP_B1 és a csoporthoz tartozó DP_B2 BG_B csoport
-    Terjesztési pontok DP_C1 és a csoporthoz tartozó DP_C2 BG_C csoport

Ügyfelek a hálózati helyeket felveheti határként csak a BG_A határcsoportot, és azt, majd a másik két határcsoportokhoz az adott határcsoport kapcsolatok konfigurálása:
-    Konfigurálja a terjesztési pontok az első *szomszédos* csoport (BG_B) használható 10 perc múlva. Ez a csoport tartalmazza a terjesztési pontok DP_B1 és DP_B2. Mindkettő jó csatlakozású, az első csoportok határ helyekre.
-    Konfigurálja a második *szomszédos* (BG_C) csoport 20 perc után használni. Ez a csoport tartalmazza a terjesztési pontok DP_C1 és DP_C2. A többi két határcsoport a WAN-KAPCSOLATON keresztüli mindkettő.
-    Is hozzáadhat egy további terjesztési ponton található a helykiszolgálón a hely alapértelmezett helyhatárcsoportba. Ez a legkevésbé preferált tartalom forráshelyeként, de központilag található, a határcsoporthoz.

    Példa a határcsoportokat és a tartalék alkalommal:

     ![BG_Fallack](media/BG_Fallback.png)


Ez a konfiguráció:
-    Az ügyfél megkezdi a tartalom a terjesztési pontokról a Keresés a *aktuális* határcsoport (BG_A), a keresés minden egyes terjesztési pontok a Váltás a következő terjesztési ponthoz a határcsoport két percet. Az ügyfelek készlete érvényes tartalomforrás helyek DP_A1 és DP_A2 tartalmaz.
-    Ha az ügyfél nem találja a tartalmat a *aktuális* határcsoport keresés 10 percig, után, majd hozzáadja a terjesztési pontokat a BG_B határcsoport a keresést. Majd továbbra is a terjesztési pontról a terjesztési pontok kombinált készlet, amely már tartalmazza a BG_A és a BG_B határcsoportok származó tartalom keresése. Az ügyfél továbbra is csatlakozni az egyes terjesztési pontok két percet, mielőtt Váltás a következő terjesztési pontra a készletből. Az ügyfelek készlete érvényes tartalomforrás helyek DP_A1, DP_A2, DP_B1 és DP_B2 tartalmazza.
-    Egy további 10 perc (összesen 20 perc) után az ügyfél még mindig rendelkezik nem található egy terjesztési pontot tartalommal, ha bővíti az elérhető terjesztési pontok közé tartoznak a második készlete *szomszédos* csoportban, BG_C határcsoporthoz. Az ügyfél most keresés (DP_A1, DP_A2, DP_B2, DP_B2, DP_C1 és DP_C2) 6 terjesztési pont van, és továbbra is fennáll, egy új terjesztési pont módosítása a kétpercenként, amíg a tartalom található.
-    Ha az ügyfél nem rendelkezik található tartalom összesen 120 perc után, akkor visszaáll közé tartozik a *alapértelmezett helyhatárcsoportba* folyamatos keresését részeként. A készlet a terjesztési pontok mostantól tartalmazza a három konfigurált határcsoportok minden terjesztési pontjait, és a végső terjesztési pont a helykiszolgáló számítógépen található.  Az ügyfél majd továbbra is használja a tartalomhoz, a keresési módosítása a terjesztési pontok kétpercenként, amíg a tartalom található.

A különböző szomszédos csoportok különböző időpontokban elérhető legyen konfigurálásával szabályozhatja a adott terjesztési pontot hozzá szeretné adni a tartalom forráshelyeként, és ha, vagy ha, az ügyfél használja az alapértelmezett hely határcsoporthoz tartalék biztonsági hálóként nem elérhető tartalom más helyről.






### <a name="update-existing-boundary-groups-to-the-new-model"></a>Frissítse az új modell meglevő határcsoportokhoz
Ha előtt 1610 verzióra frissíti, az alábbi konfigurációk automatikusan történik. Ezek biztosítani kívánják a jelenlegi tartalék viselkedése továbbra is elérhető, amíg nem konfigurál az új határcsoportokhoz és a kapcsolatokat.

-    Egy alapértelmezett helyhatárcsoportba hoz létre minden elsődleges helyhez, a név ***alapértelmezett –--Helyhatárcsoportba&lt;sitecode >.***
  -    A terjesztési pontok *tartalék forráshely engedélyezése a tartalom* be van jelölve, és állapotáttelepítési pontok az elsődleges helyeken hozzáadódnak a *alapértelmezett –--Helyhatárcsoportba&lt;Helykód >* az adott hely határcsoporthoz.
  -    1702 verziójával kezdve szoftverfrissítési pontok kerülnek egyes helyek *alapértelmezett –--Helyhatárcsoportba&lt;sitecode >*.
-    Másolatot minden meglévő határcsoporthoz, amely tartalmazza a helykiszolgáló konfigurálva lassú kapcsolaton keresztül történik. Az új csoport neve *** &lt;határ csoport neve >-&lt;eredeti határ csoport azonosítója >***:  
    -    Gyors kapcsolattal rendelkező helyrendszerek maradnak az eredeti határcsoporthoz.
    -    Beléptetésihely-rendszerek (a terjesztési pontok, a felügyeleti pontok), amely lassú kapcsolattal rendelkezik egy példányát a határcsoport példányát kerülnek. Az eredeti helyrendszerek lassú konfigurálva a visszamenőleges kompatibilitás érdekében az eredeti határcsoportokban maradnak, de nem használják a határcsoportokhoz.
    - A határ másolat nincs társítva határokat. Azonban tartalék kapcsolat jön létre az eredeti csoport és az új határ másolat, a tartalék ideje nulla között.  


- **Vonatkozó és a másodlagos helyek:**
  - A határcsoport jön létre, ha egy másodlagos helyen legalább egy terjesztési pontok és a *tartalék forráshely engedélyezése a tartalom* bejelölése vagy állapot-áttelepítő pont. A név a határcsoporthoz ***másodlagos-Site-szomszédos--Tmp&lt;Sitecode >.***
  - Az összes terjesztési pontok *tartalék forráshely engedélyezése a tartalom* be van jelölve, és állapotáttelepítési pontok hozzáadódnak a újonnan létrehozott másodlagos hely határcsoporthoz.
  - Tartalék kapcsolat jön létre az eredeti határcsoport és az újonnan létrehozott szomszédos határcsoport között, és a tartalék idő értéke nulla.


 A következő táblázat ismerteti az új tartalék viselkedés várható kombinációja az eredeti központi telepítési beállítások és a terjesztési pontok konfigurációi:

"Nem futtatja a programot" lassú hálózati az eredeti telepítési konfigurációja  |Eredeti terjesztési pont "Engedélyezése az ügyfél számára a tartalék forráshely használatát a tartalomhoz" konfigurációja  |Új tartalék viselkedése  
---------|---------|---------
Kijelölt     |  Kijelölt    |  **Nincs tartalék** -csak használják a terjesztési pontokat aktuális határcsoportban       
Kijelölt     |  Nincs kiválasztva|  **Nincs tartalék** -csak használják a terjesztési pontokat aktuális határcsoportban       
Nincs kiválasztva |  Nincs kiválasztva|  **A szomszédos tartalék** – a terjesztési pontok aktuális határcsoportban, majd a terjesztési pontok a szomszédos határ csoportból. Kivéve, ha az explicit kapcsolat az alapértelmezett hely határcsoporthoz van konfigurálva, az ügyfelek nem lesznek tartalék ehhez a csoporthoz.    
Nincs kiválasztva | Kijelölt        |   **Normál tartalék** -aktuális határcsoportban terjesztési pontokat használ, akkor azokat a szomszédos és a hely alapértelmezett határcsoportok

 Más szolgáltatástelepítési konfigurációk eredményez **normál tartalék**.  




## <a name="changes-from-prior-versions-for-ui-and-behavior-for-content-locations"></a>Változások a tartalom helyét viselkedésének és korábbi verziók felhasználói felülete
Az alábbiakban határcsoportokat, és hogyan ügyfelek található tartalom főbb módosításait. Ezek a változások történtek 1610 verziójával. Ezeket a módosításokat és fogalmak számos működnek együtt.


-    **Gyors vagy lassú konfigurációi törlődnek:** Már nem konfigurálhatja az egyes terjesztési pontok gyors vagy lassú.  Ehelyett a rendszer minden határcsoporthoz hozzárendelt helyrendszer azonos. Ez a változás miatt a **hivatkozások** a határcsoport tulajdonságainak lapján már nem támogatja a gyors vagy lassú konfigurációja.
-     **Új alapértelmezett határcsoport az egyes helyeken:**  Minden elsődleges hely rendelkezik nevű új alapértelmezett határcsoportba ***alapértelmezett –--Helyhatárcsoportba&lt;sitecode >***.  Ha egy ügyfél nem egy hálózati helyet, amelyhez tartozik egy határcsoporthoz, hogy az ügyfél a hozzárendelt helyről származó alapértelmezett csoporthoz rendelt helyrendszerek fogja használni. Ehhez a határcsoporthoz tartalék tartalmi helyet, amelynek helyettesítésére használni szeretne.      
 -    **"A tartalék tartalomhelyekről engedélyezése"** eltávolítása: Explicit módon már nem konfigurálja a terjesztési pont használható tartalék tartalomhelyként, és ez beállítások el lesznek távolítva a felhasználói felületen.

    Emellett az eredmény beállítás **ügyfelek használhatnak tartalék forráshely a tartalomhoz** üzemelő példányon az alkalmazások megváltozott. Ezt a beállítást a központi telepítési típus mostantól lehetővé teszi az ügyfél az alapértelmezett helyhatárcsoportba használják a tartalom forráshelyeként.

 -    **Határ csoportok kapcsolatokat:** Mindegyik határcsoporthoz egy vagy több további határcsoportok lehet társítani. Ezek a hivatkozások alkotnak az új határ csoport tulajdonságai lap nevű konfigurált kapcsolatok **kapcsolatok**:
     -    Minden ügyfél közvetlenül társított határcsoportban nevezik egy **aktuális** határcsoporthoz.  
    -     Egyetlen határcsoporthoz sem az ügyfél használhatja, hogy az ügyfélszámítógépek közötti társítás miatt *aktuális* határcsoport és egy másik csoport neve egy **szomszédos** határcsoporthoz.
    -  Szolgáltatás be van kapcsolva a **kapcsolatok** lap, amely akkor adja meg, amelyek változtatás nélkül használhatók határcsoportokat egy *szomszédos* határcsoporthoz. Beállíthatja úgy is egy időt percben, amely meghatározza, hogy amikor egy ügyfelet, amelyben a sikertelen lesz a tartalmat a terjesztési pontról a *aktuális* csoport megkezdődik a tartalom helyét a Keresés *szomszédos* határcsoportokat.

        Adja hozzá, vagy a határcsoport konfigurációjának módosításához, a beállítást kell blokk tartalék adott határcsoportra konfigurál, az adott csoportból.

    Az új konfiguráció használatához explicit társítások (hivatkozások) megadása az egy határcsoportban a másikra, valamint percben egyszerre társított csoport összes terjesztési pont konfigurálása. Konfigurálja az idő határozza meg, amikor egy ügyfél nem talál a tartalomforrás a *aktuális* határcsoport keresse meg az adott szomszédos határcsoport tartalomforrások kezdődhet.

    Explicit módon konfigurálnia a határcsoportokat, mellett határcsoporthoz van egy implicit hivatkozás az alapértelmezett hely határcsoporthoz. Ez a hivatkozás ekkor az alapértelmezett hely határcsoporthoz válik, amely lehetővé teszi az ügyfelek számára a terjesztési pontokat adott határcsoport társított tartalomforrásának helyként szomszédos határcsoportban 120 perc után aktívvá válik.

    Ez a viselkedés váltja fel, milyen volt korábban említett a tartalom tartalék módszerként.  Ez az alapértelmezett viselkedés 120 perc felülbírálhatja az alapértelmezett helyhatárcsoportba explicit módon társításával egy *aktuális* csoport, és beállításakor egy megadott idő percben, vagy blokkolja a tartalék teljesen a használat megelőzése érdekében.


-     **Ügyfelek próbálják beszerezni a tartalmat minden terjesztési pont legfeljebb 2 percig:** Amikor egy ügyfelet keres a tartalom forráshelyeként, megkísérli minden terjesztési pont el a 2 percet, majd próbálkozzon egy másik terjesztési pontot. Ez az egyik változás korábbi verzióiról ahol ügyfelek próbált kapcsolódni, hogy a terjesztési pont legfeljebb 2 órán át.

    - Első terjesztési pontról, amely az ügyfél megkísérel használni véletlenszerűen kiválasztott elérhető terjesztési pontok az ügyfél a készletből *aktuális* határcsoport (vagy csoportokat).

    - Két perc elteltével az ügyfél nem találja a tartalmat, ha azt vált egy új terjesztési pontra, és megkísérli beszerezni a tartalmat, hogy a kiszolgáló. Ez a folyamat addig, amíg az ügyfél megtalálja a tartalmat, vagy elérte a készlet legutóbbi kiszolgálót két percenként ismétlődik.

    - Ha ügyfél nem talál egy érvényes tartalomforrás helye az a *aktuális* készlet tartalékként történő időszak előtt egy *szomszédos* határcsoport éri el, az ügyfél hozzáadja a terjesztési pontokat, amelyek a *szomszédos* csoport számára, az aktuális lista végére, és majd megkeresi az adatforrás helyének kibontott csoport mindkét határcsoportok terjesztési pontjait tartalmazó.

        > [!TIP]  
        > Ha egy explicit hivatkozás az aktuális határcsoport létrehozása az alapértelmezett hely határcsoporthoz, és adja meg a tartalék időt, amely kisebb, mint a tartalék időt, hogy a szomszédos határcsoport mutató hivatkozást, ügyfelei megkezdik az alapértelmezett helyhatárcsoportba az adatforrás helyének keresése előtt, beleértve a szomszédos csoport.

    - Ha az ügyfél nem sikerült beszerezni a tartalmat a kiszolgáló a készletben, újra megkezdi a folyamatot.


## <a name="procedures-for-boundary-groups"></a>A határcsoportok eljárásai
Az alábbi eljárások 1610 vagy újabb verziójára vonatkoznak. Ha 1610 előtti verzióját használja, a eljárásaiban talál [határcsoportjainak, System Center Configuration Manager verziója 1511-es, a 1602-es és a 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).


### <a name="to-create-a-boundary-group"></a>Határcsoport létrehozása  
1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

2.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Határcsoport létrehozása**elemre.  

3.  A **Határcsoport létrehozása** párbeszédpanelen nyissa meg az **Általános** lapot, és a **Név** mezőben adjon meg nevet a határcsoport számára.  

4.  Az új határcsoport mentéséhez kattintson az **OK** gombra.  


### <a name="to-configure-a-boundary-group"></a>Határcsoport konfigurálása  
 1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

 2.  Válassza ki a módosítandó határcsoportot.  

 3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

 4.  A határcsoport **Tulajdonságok** párbeszédpanelén nyissa meg az **Általános** lapot a határcsoporthoz tagként tartozó határok módosításához:  

     -   Ha felvenni szeretne a csoportba határokat, kattintson a **Hozzáadás**gombra, jelölje be egy vagy több határ jelölőnégyzetét, majd kattintson az **OK**gombra.  

     -   Határok eltávolításához jelölje ki a megfelelő határt, majd kattintson az **Eltávolítás**gombra.  

 5.  Válassza a **Referenciák** lapot a helyhozzárendelésnek és a társított helyrendszer-kiszolgáló konfigurációjának a módosításához:  

     -   Ha ezt a határcsoportot helyhozzárendelés céljára engedélyezni szeretné az ügyfelek számára, jelölje be a **Használja ezt a határcsoportot a hely hozzárendeléséhez**jelölőnégyzetet, majd válasszon ki egy helyet a **Hozzárendelt hely** legördülő listában.  

     -   A határcsoporthoz társított elérhető helyrendszer-kiszolgálók konfigurálása:  

     1.  Kattintson a **Hozzáadás**gombra, majd jelölje be egy vagy több kiszolgáló jelölőnégyzetét. A kiszolgálókat a rendszer társított helyrendszer-kiszolgálóként adja hozzá a határcsoporthoz. Csak a telepített és támogatott helyrendszerszerepkörrel rendelkező kiszolgálók érhetők el.  

         > [!NOTE]  
         >  Az elérhető helyrendszerek bármilyen kombinációját kijelölheti a hierarchia bármelyik helyéről. A beállított helyrendszerek az ehhez a határcsoporthoz tagként tartozó egyes határok tulajdonságai közt a **Helyrendszerek** lapon láthatóak.  

     2.  Egy kiszolgáló határcsoportból való eltávolításához válassza ki a kiszolgálót, és kattintson az **Eltávolítás**lehetőségre.  

         > [!NOTE]  
         >  Ha nem akarja tovább használni ezt a határcsoportot helyrendszerek társításához, távolítsa el a társított helyrendszer-kiszolgálóként felsorolt összes kiszolgálót.  

 6.  Válassza ki a **kapcsolatok** lapján adja meg az eljárást:  

     - Kattintson a **Hozzáadás**, majd válassza ki a konfigurálni kívánt határcsoporthoz.

     - A terjesztési pontok egy tartalék idő beállítása. Ez bizonyos idő eltelte után, a kapcsolatok beállításakor határcsoportban lévő ügyfelek fog tudni kezdeni a keresést a tartalmat a terjesztési pontokat ad hozzá a határcsoporthoz.

     - Ahhoz, hogy a tartalék a meghatározott határcsoporthoz, beleértve a *alapértelmezett helyhatárcsoportba* alapértelmezés szerint van konfigurálva, válassza ki a határcsoportot, majd jelölje be a **soha tartalék**.   

 7.  A határcsoport tulajdonságainak bezárásához és a konfiguráció mentéséhez kattintson az **OK** gombra.  

#### <a name="to-associate-a-site-systme-server-with-a-boundary-group"></a>Egy helyrendszer-kiszolgáló webkiszolgálójához határcsoporthoz társítása  
 1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Hierarchiakonfiguráció** >  **Határcsoportok**.  

 2.  Válassza ki a módosítandó határcsoportot.  

 3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

 4.  A határcsoport **Tulajdonságok** párbeszédpanelén válassza a **Hivatkozások** lapot.  

 5.  A **Helyrendszer-kiszolgálók kiválasztása**csoportban kattintson a **Hozzáadás**gombra, jelölje be az ehhez a határcsoporthoz társítani kívánt helyrendszer-kiszolgálók melletti jelölőnégyzeteket, majd kattintson az **OK**gombra.  

 6.  A párbeszédpanel bezárásához és a határcsoport konfigurációjának mentéséhez kattintson az **OK** gombra.  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>Tartalék hely konfigurálása az automatikus helyhozzárendeléshez  

  1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** >  **helyek**.  

  2.  A **Kezdőlap** **Helyek** csoportjában kattintson a **Hierarchiabeállítások**elemre.  

  3.  Az **Általános** lapon jelölje be a **Tartalék hely használata**jelölőnégyzetet, majd válasszon egy helyet a **Tartalék hely** legördülő listáról.  

  4.  A konfiguráció mentéséhez kattintson az **OK** gombra.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Előnyben részesített felügyeleti pontok használatának engedélyezése  

 1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** > **helyek**, majd a a **Home** lapon válassza **Hierarchiabeállítások**.  

 2.  A Hierarchiabeállítások párbeszédpanel **Általános** lapján válassza **Az ügyfelek részesítsék előnyben a határcsoportokban megadott felügyeleti pontok használatát**lehetőséget.  

 3.  A párbeszédpanel bezárásához és a konfiguráció mentéséhez kattintson az **OK** gombra.  

