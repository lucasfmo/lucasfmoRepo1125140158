---
title: "Endpoint Protection-ügyfél gyakori kérdések |} Microsoft Docs"
description: "A Windows Defender és az Endpoint Protection gyakran feltett kérdésekre adott válaszok."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3aaa9d2-a40e-42b1-ad75-5a115351729e
caps.latest.revision: 15
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: b88bc5f734b85527b81e5848deb0617db4c8dfbc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection-client-frequently-asked-questions"></a>Endpoint Protection-ügyfél gyakran ismételt kérdések

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Ezeket a gyakori kérdéseket azon felhasználók számára állítottuk össze, akik felügyelt számítógépére a rendszergazda a Windows Defender vagy az Endpoint Protection szolgáltatást telepítette. A tartalom itt nem feltétlenül vonatkozik az egyéb kártevőirtó szoftvert. Microsoft System Center Endpoint Protection a Windows Defender a Windows 10 kezeli. Azt is telepítheti, és a Windows 10 előtti rendszerrel működő számítógépeken az Endpoint Protection ügyfél kezelése. Bár a jelen cikkben a Windows Defender leírását olvashatja, az információk az Endpoint Protection szolgáltatásra szintúgy érvényesek.  

-   [Miért szükséges a vírusirtó és kémprogramirtó szoftver?](#why-do-i-need-antivirus-and-antispyware-software)  
-   [Hogyan állapítható meg, ha a számítógép megfertőződött kártevő?](#how-can-i-tell-if-my-computer-is-infected-with-malicious-software)
-   [Hogyan tudhatom meg a Windows Defender verzióját?](#how-can-i-find-the-version-of-windows-defender)
-   [Mit tegyek, ha a Windows Defender vagy az Endpoint Protection kártevő szoftvert észlel a számítógépemen?](#what-should-i-do-if-windows-defender-or-endpoint-protection-detects-software-on-my-computer)  
-   [Mi az a vírus?](#what-is-a-virus)  
-   [Mi az a kémprogram?](#what-is-spyware)  
-   [Mi a különbség a vírusok, kémprogramok és más potenciálisan ártalmas szoftverek között?](#hat-s-the-difference-between-viruses-spyware-and-other-potentially-harmful-software)  
-   [Honnan vírusok, kémprogramok és más potenciálisan nemkívánatos szoftverek származnak?](#where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from)  
-   [Kaphatok kártevő tudtomon?](#can-i-get-malicious-software-without-knowing-it)  
-   [Miért fontos átolvasni a licencszerződéseket a szoftverek telepítése előtt?](#why-is-it-important-to-review-license-agreements-before-installing-software)  
-   [Mi az a különbség az Endpoint Protection és a Windows Defender között?](#what-s-the-difference-between-endpoint-protection-and-windows-defender)  
-   [Miért nem észleli a cookie-kat a Windows Defender?](#why-doesn-t-windows-defender-detect-cookies)  
-   [Hogyan védekezhetek a kártevő?](#how-can-i-prevent-malware)  
-   [Mik a vírus- és kémprogram-definíciókat?](#what-are-virus-and-spyware-definitions)  
-   [Hogyan tarthatom vírus- és kémprogram-definíciók naprakészen?](#how-do-i-keep-virus-and-spyware-definitions-up-to-date)  
-   [Hogyan távolítsa el vagy a Windows Defender vagy az Endpoint Protection által karanténba helyezett elemek visszaállítása?](#how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection)  
-   [Mi az a valós idejű védelem?](#what-is-real-time-protection)  
-   [Hogyan állapítható meg, hogy, hogy a Windows Defender vagy az Endpoint Protection fut a számítógépemen?](#how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer)
-   [A Windows Defender vagy az Endpoint Protection-riasztások beállítása hogyan?](#how-to-set-up-windows-defender-or-endpoint-protection-alerts)  

##  <a name="why-do-i-need-antivirus-and-antispyware-software"></a>Miért szükséges a vírusirtó és kémprogramirtó szoftver?  

 Rendkívül fontos, hogy a számítógépen fusson kártevőszoftverek elleni védelmet nyújtó program. A kártevő szoftverek, amelyek közé vírusok, kémprogramok és más, potenciálisan nemkívánatos szoftverek tartoznak, bármikor megpróbálhatnak települni a számítógépre, amikor az internethez csatlakozik. Akkor is megfertőzhetik a számítógépet, amikor CD-ről, DVD-ről vagy más cserélhető adathordozóról telepít egy programot. A kártevő szoftverek úgy is programozhatók, hogy ne csupán a telepítéskor, hanem váratlan időpontokban is fussanak.  

 A Windows Defender és az Endpoint Protection három lehetőséget kínál, amelyekkel megvédheti számítógépét a kártevő szoftverek támadásaitól:  

-   **A valós idejű védelem** - valós idejű védelem lehetővé teszi, hogy a Windows Defender folyamatosan figyelje a számítógépet az idő és a riasztás, ha a kártevő szoftverek, beleértve a vírusok, kémprogramok és más potenciálisan nemkívánatos szoftverek próbálják telepíteni maga futtatását a számítógépen. A Windows Defender ezután felfüggeszti a szoftver működését, és lehetővé teszi a felhasználónak a javasolt vagy valamilyen alternatív művelet végrehajtását.  

    |**Valós idejű védelmi beállítást** |**célja** |

    |-|-|  
    | Minden letöltött fájl vizsgálata |} Ez a beállítás figyeli a fájlok és programok letöltött, beleértve a fájlokat, automatikusan letöltött Windows Internet Explorer és a Microsoft Outlook® Express, például a ActiveX® vezérli és a szoftvertelepítő programokat. Ezeket a fájlokat a böngésző töltheti le, telepítheti és futtathatja. A fájlok között kártevő szoftverek, például vírusok, kémprogramok és más, vélhetően nemkívánatos szoftverek is előfordulhatnak, amelyeket a rendszer a felhasználó tudta nélkül telepít.<br /><br /> Ha használja a valós idejű védelmi beállítást, a Windows Defender folyamatosan figyeli a számítógépet, esetlegesen letöltött kártevő fájlok és programok után kutatva. Ez azt jelenti, hogy a Windows Defender lassítsa le a böngészést nem szükséges, vagy e-mail-élmény bármely ellenőrzésével fájlokat vagy programokat hasznos lehet a figyelési funkció. |}  
    | Fájl- és programtevékenység figyelése a számítógépen |} Ez a beállítás figyeli a fájlok és programok indítsa el a számítógépen fut, és majd értesítést kaphat az összes általuk vagy rajtuk végrehajtott műveletekről. Ez azért fontos, mert a kártevő szoftverek képesek arra, hogy a telepített programok biztonsági réseit kihasználva a felhasználó tudta nélkül kártevő vagy nemkívánatos szoftvereket futtassanak. Például kémprogramok futhatnak a háttérben a gyakran használt programok elindításakor. A Windows Defender figyeli a programokat, és riasztást küld, ha gyanús tevékenységet észlel. |}  
    | Viselkedésfigyelés engedélyezése |} Ezt a beállítást olyan gyanús mintázatok, előfordulhat, hogy hagyományos víruskereső módszerekkel nem lehetne észlelni viselkedésében előfordulnak figyeli. |}  

    | Hálózatfelügyeleti rendszer engedélyezése |} Ez a beállítás segít megvédeni a számítógépet az ismert biztonsági rések "nulladik napon" való, jelenleg között eltelt időszakot csökkentése a biztonsági rés felfedezése és a frissítés alkalmazása. |}  

-   **Vizsgálati beállítások** -használhatja a Windows Defender a potenciális fenyegetések, például vírusok, kémprogramok és más, kártevő szoftverek, előfordulhat, hogy vannak-e a számítógép veszélyben vizsgálatához. Emellett rendszeres vizsgálatokat is ütemezhet, és eltávolíthatja a vizsgálat során észlelt kártevő szoftvereket.  

-   **Microsoft Active Protection Service Közösség** – az online Microsoft Active Protection Service Közösség segítségével tájékozódhat arról mások hogyan kezelik azokat, amelyek kockázatait még nem besorolt szoftver. Ezek az információk segíthetnek annak eldöntésében, hogy egy adott szoftvert engedélyezzen-e a számítógépén. Ráadásul ha részt vesz a visszajelzések küldésében, az Ön döntései is befolyásolják a közösség értékelését, és segíthetnek másoknak egy-egy kérdéses helyzetben.  

##  <a name="how-can-i-tell-if-my-computer-is-infected-with-malicious-software"></a>Hogyan állapítható meg, ha a számítógép megfertőződött kártevő?  

 A számítógépen valamilyen kártevő szoftver, például vírus, kémprogram vagy más potenciálisan nemkívánatos szoftver szerepelhet, ha:  

-   Új eszköztárakat, hivatkozásokat vagy kedvenceket észlel, amelyeket nem szándékosan adott a böngészőhöz.  

-   A kezdőlapja, egérmutatója vagy keresőprogramja váratlanul módosul.  

-   Egy adott webhely, például egy keresőmotor címét írja be, de értesítés nélkül egy másik webhelyre kerül.  

-   A rendszer automatikusan töröl fájlokat a számítógépről.  

-   A számítógépé más számítógépek támadásához használják fel.  

-   Felugró hirdetéseket lát akkor is, amikor nem használja az internetet.  

-   A számítógépe hirtelen lassabban kezd működni, mint általában. A számítógépen nem az összes teljesítményproblémát okozza kártevő szoftver, de a kártevő szoftverek, különösen a kémprogramok észrevehető változást okozhatnak.  

Akkor is lehet kártevő szoftver a számítógépén, ha nem lát tüneteket. Ez a szoftvertípus információkat gyűjthet Önről és a számítógépéről a tudta és beleegyezése nélkül. Az adatai és a számítógépe védelme érdekében mindig futtassa a Windows Defender vagy Endpoint Protection szolgáltatást.  

## <a name="how-can-i-find-the-version-of-windows-defender"></a>Hogyan tudhatom meg a Windows Defender verzióját?
 A Windows Defender a számítógépen futó verziójának megtekintéséhez nyissa meg a Windows Defender (kattintson **Start** majd keresse meg a **Windows Defender**), kattintson a **beállítások**, és a Windows Defender beállításokat található alján görgessen **verzióinformáció**.

##  <a name="what-should-i-do-if-windows-defender-or-endpoint-protection-detects-malicious-software-on-my-computer"></a>Mit tegyek, ha a Windows Defender vagy az Endpoint Protection kártevő szoftvert észlel a számítógépemen?  

 Ha a Windows Defender kártevő vagy potenciálisan nemkívánatos szoftvert észlel a számítógépen (a számítógép valós idejű védelem segítségével történő figyelésekor vagy egy vizsgálatot követően), az észlelt elemről a képernyő jobb alsó sarkában megjelenő üzenetben értesíti a felhasználót.  

 Az üzenet tartalmaz egy **Számítógép megtisztítása** gombot és egy **Részletek megjelenítése** hivatkozást. Utóbbira kattintva további információkat tekinthet meg az észlelt elemről. Kattintson a **Részletek megjelenítése** hivatkozásra, és a megnyíló **Lehetséges veszélyforrás részletei** ablakban elolvashatja az észlelt elemmel kapcsolatos további információkat. Ezután eldöntheti, hogy melyik műveletet hajtja végre az elemen, vagy egyszerűen a **Számítógép megtisztítása**gombra kattinthat. Ha segítségre van szüksége az észlelt elemen végrehajtandó művelet kiválasztásához, döntsön a riasztási szint alapján, amelyet a Windows Defender az elemhez rendelt (további információ: A riasztási szintek ismertetése).  

 A riasztási szintek segítségével eldöntheti, milyen választ adjon a vírusokra, kémprogramokra és más, vélhetően nemkívánatos szoftverekre. Bár a Windows Defender azt javasolja, hogy minden vírust és kémprogramot távolítson el, nem minden megjelölt szoftver kártevő vagy nemkívánatos. A következő információk segítségével eldöntheti, hogy mi a teendő, ha a Windows Defender potenciálisan nemkívánatos szoftvert érzékel a számítógépen.  

 A riasztási szinttől függően a következő műveletek egyikét hajthatja végre az észlelt elemen:  

-   **Távolítsa el** – Ez a művelet végleg törli a szoftvert a számítógépről.  

-   **Karantén** – ezzel a művelettel karanténba helyezheti a szoftvert, hogy nem lesz futtatható. Egy szoftver karanténba tételekor a Windows Defender áthelyezi azt a számítógépen egy másik helyre, és megakadályozza a futtatását, amíg a felhasználó vissza nem állítja vagy el nem távolítja azt a számítógépről.  

-   **Engedélyezése** – ezzel a művelettel hozzáadhatja a szoftvert a Windows Defender által engedélyezettek listájához, és futtathatja a számítógépen. A Windows Defender ezt követően nem küld figyelmeztetést a kockázatokról, amelyeket a szoftver az adatok védelmére vagy a számítógépre nézve jelent.  

 Ha egy elem, például egy szoftver esetében az **Engedélyezés** lehetőséget választja, a Windows Defender a továbbiakban nem küld figyelmeztetést a kockázatokról, amelyeket a szoftver az adatok védelmére vagy a számítógépre nézve jelent. Ezért csak akkor adjon hozzá szoftvereket az engedélyezettek listájához, ha az adott szoftvereket és a közzétevőjüket is megbízhatónak tartja.  

### <a name="how-to-remove-potentially-harmful-software"></a>Potenciálisan káros szoftverek eltávolítása

A Windows Defender által észlelt összes nemkívánatos vagy potenciálisan káros elem gyors és egyszerű eltávolításához használja a **Számítógép tisztítása** lehetőséget.  

1.  Amikor látja az értesítési területen megjelenített értesítő üzenetet, miután a rendszer lehetséges fenyegetéseket észlelt, kattintson a **Számítógép tisztítása**elemre.  

2.  A Windows Defender eltávolítja a potenciális fenyegetést (vagy fenyegetéseket), majd értesíti, amikor végzett a számítógép tisztításával.  

3.  Az összes észlelt fenyegetésről további információért kattintson az **Előzmények** lapra, majd válassza a **Minden észlelt elem**lehetőséget.  

4.  Ha nem látja az összes észlelt elemet, kattintson a **Részletek megtekintése**parancsra. Ha a számítógép rendszergazdai jelszót vagy megerősítést kér, adja meg a jelszót, illetve erősítse meg a műveletet. Windows XP rendszert futtató gépeken lehet, hogy rendszergazdaként kell bejelentkeznie a számítógépre.  

> [!NOTE]  
>  Amikor lehetséges, a számítógép tisztításakor a Windows Defender csak a fájl fertőzött részét távolítja el, nem a teljes fájlt.  

##  <a name="what-is-a-virus"></a>Mi az a vírus?  
 A számítógépvírusok olyan szoftverprogramok, amelyeket kifejezetten úgy alakítottak ki, hogy megzavarják a számítógép működését, adatokat rögzítsenek, károsítsanak vagy töröljenek, vagy más számítógépeket fertőzzenek meg az interneten keresztül. A vírusok gyakran lassítják a gépet és más problémákat is okoznak a folyamat során.  

##  <a name="what-is-spyware"></a>Mi az a kémprogram?  
 A kémprogram olyan szoftver, amely az Ön értesítése, beleegyezése és irányítása nélkül telepíti magát a számítógépére, illetve futhat azon. Lehetséges, hogy a kémprogram nem okoz tüneteket a számítógép megfertőzése után, de sok kártevő vagy nemkívánatos program befolyásolhatja a számítógép működését. A kémprogram figyelheti például az online tevékenységeit, információkat gyűjthet (beleértve a személyes azonosításra alkalmas vagy más bizalmas adatokat), módosíthatja a számítógépe beállításait, illetve lelassíthatja annak működését.  

##  <a name="whats-the-difference-between-viruses-spyware-and-other-potentially-harmful-software"></a>Mi a különbség a vírusok, kémprogramok és más potenciálisan ártalmas szoftverek között?  
 A vírusok és a kémprogramok is az Ön tudta nélkül lesznek telepítve a számítógépre, és mindkettő zavaró és ártalmas lehet. Ezenkívül információkat rögzíthetnek a számítógépen, és károsíthatják vagy törölhetik ezeket az információkat. Mindkettő negatív hatással lehet a számítógép teljesítményére.  

 A vírusok és kémprogramok közötti fő különbség az, ahogy viselkednek a számítógépen. A vírusok, más élő organizmusokhoz hasonlóan meg szeretnék fertőzni a számítógépet, sokszorozódni kívánnak, és a lehető legtöbb számítógépre el szeretnének jutni. A kémprogramok, azonban több mint egy vakondokhoz – "helyezze át" a számítógép, és nem marad mindaddig, amíg lehetséges, a küldő értékes információt egy külső forrásnak, miközben a számítógép nincs kíván.  

##  <a name="where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from"></a>Honnan vírusok, kémprogramok és más potenciálisan nemkívánatos szoftverek származnak?  
 A nemkívánatos szoftvereket, például a vírusokat webhelyek vagy letöltött, illetve CD-ről, DVD-ről, külső merevlemezről vagy egy eszközről telepített programok telepíthetik. A kémprogramokat a leggyakrabban ingyenes szoftvereken, például fájlmegosztáson, képernyővédőkön vagy keresési eszköztárakon keresztül telepítik.  

##  <a name="can-i-get-malicious-software-without-knowing-it"></a>Kaphatok kártevő tudtomon?  
 Igen, néhány kártevő szoftver egy webhely beágyazott parancsfájlján vagy egy weblap programra keresztül is kell telepíteni. Néhány kártevő szoftver telepítéséhez az Ön közreműködésére van szükség. Ez a szoftver webes felugró ablakokat vagy ingyenes szoftvereket használ, amelyekhez el kell fogadnia egy letölthető fájlt. De ha a Microsoft Windows® rendszert naprakészen tartja, és nem csökkenti a biztonsági beállításokat, minimalizálhatja a fertőzés kockázatát.  

##  <a name="why-is-it-important-to-review-license-agreements-before-installing-software"></a>Miért fontos átolvasni a licencszerződéseket a szoftverek telepítése előtt?  
 Amikor webhelyeket látogat, automatikusan nem fogadja el semmilyen a helyet kínál a letöltést. Ha ingyenes szoftvert tölt le, például fájlmegosztó programokat vagy képernyővédőket, olvassa el körültekintően a licencszerződést. Keressen olyan záradékokat, amelyek szerint el kell fogadnia a vállalattól érkező hirdetéseket és felugró elemeket, vagy hogy a szoftver bizonyos információkat visszaküldhet a szoftver kiadójának.  

##  <a name="whats-the-difference-between-endpoint-protection-and-windows-defender"></a>Mi az a különbség az Endpoint Protection és a Windows Defender között?  
 A Endpoint Protection egy kártevőirtó szoftver, vagyis úgy van kialakítva, hogy észlelje és segítsen megvédeni a gépet a különböző kártevő szoftverek, beleértve a vírusok, kémprogramok és más potenciálisan nemkívánatos szoftverek ellen. A Windows Defender, amely a Windows operációs rendszerrel együtt automatikusan telepítve van egy, a kémprogramokat észlelő és leállító szoftver.  

##  <a name="why-doesnt-windows-defender-detect-cookies"></a>Miért nem észleli a cookie-kat a Windows Defender?  
 A cookie-k kis méretű szöveges fájlok, webhelyek vannak-e az Ön kapcsolatos információk tárolása és a beállítások a számítógépen. Webhelyek cookie-k használatát, nyújtanak testreszabott élmént és gyűjtenek információkat a webhely használatával kapcsolatban. A Windows Defender nem észleli a cookie-kat, mert azt nem tekinti azokat fenyegetésnek az adatvédelem és a számítógép biztonsága tekintetében. A legtöbb internetes böngészőprogram lehetővé teszi cookie-k blokkolását.  

##  <a name="how-can-i-prevent-malware"></a>Hogyan védekezhetek a kártevő?  
 A mai számítógép-felhasználók két legnagyobb aggodalmát a vírusok és a kémprogramok jelentik. Míg ezek problémát jelenthetnek, mindkét esetben egyszerűen megvédheti magát egy kis előrelátó tervezéssel:  

-   A számítógép szoftvereit naprakészen, és ne feledje telepíteni a javításokat. Ne feledje el rendszeresen frissíteni az operációs rendszert.  

-   Győződjön meg arról, hogy a vírusirtó és kémprogramirtó szoftver (Windows Defender) a legújabb frissítéseket használja a potenciális fenyegetések ellen (lásd: Hogyan tarthatom naprakészen a vírus- és kémprogram-definíciókat?). Ezenkívül győződjön meg arról, hogy mindig a Windows Defender legújabb verzióját használja.  

-   Csak megbízható helyekről töltsön le frissítéseket. A Windows operációs rendszerek esetén mindig látogasson el [Microsoft Update](http://go.microsoft.com/fwlink/?LinkID=96304) (http://go.microsoft.com/fwlink/?LinkID=96304) és egyéb szoftverek mindig használjon a vállalat vagy személy webhelyeit.  

-   Ha e-mailes mellékletet kap, és nem ismerős a forrása, akkor azonnal törölje azt. Nem az ismeretlen forrásból származó alkalmazások és fájlok letöltéséhez, és legyen körültekintő, amikor más felhasználókkal fájlokat cserél.  

-   Telepítsen és használjon tűzfalat. Ajánlott engedélyezni a Windows tűzfalat.  

##  <a name="what-are-virus-and-spyware-definitions"></a>Mik a vírus- és kémprogram-definíciókat?  
 A Windows Defender vagy az Endpoint Protection használatához fontos, hogy naprakész vírus- és kémprogram-definíciókkal rendelkezzen. A definíciók olyan fájlok, amelyek a lehetséges szoftveres veszélyforrások folyamatosan bővülő enciklopédiájaként működnek. A Windows Defender vagy az Endpoint Protection a definíciók segítségével dönti el, hogy az észlelt szoftver vírus, kémprogram vagy más, vélhetően nemkívánatos szoftver-e, majd riasztást küld a szoftver jelentette lehetséges kockázatokról. Annak érdekében, hogy a definíciók mindig naprakészek legyenek, a Windows Defender vagy az Endpoint Protection a Microsoft Update szolgáltatással együttműködve automatikusan telepíti a kiadott új definíciókat. Azt is beállíthatja, hogy a Windows Defender vagy az Endpoint Protection a vizsgálat előtt frissített definíciókat keressen az interneten.  

##  <a name="how-do-i-keep-virus-and-spyware-definitions-up-to-date"></a>Hogyan tarthatom vírus- és kémprogram-definíciók naprakészen?  
 A vírus- és kémprogram-definíciók az ismert kártevő szoftverek, például vírusok, kémprogramok és más, potenciálisan nemkívánatos szoftverek enciklopédiájaként működnek. Mivel a kártevő szoftvereket folyamatosan fejlesztik, a Windows Defender vagy az Endpoint Protection naprakész definíciók segítségével dönti el, hogy a számítógépére telepített, azon futtatandó vagy a beállításokat módosítani kívánó szoftver vírus, kémprogram vagy más potenciálisan nemkívánatos szoftver-e.  

### <a name="to-automatically-check-for-new-definitions-before-scheduled-scans-recommended"></a>(Ajánlott) ütemezett vizsgálatok előtt új definíciók automatikus keresése  

1.  A **Start menüből** , vagy az értesítési területen lévő ikonra kattintva nyissa meg a Windows Defender- vagy az Endpoint Protection-ügyfelet.  

2.  Kattintson a **Beállítások**, majd az **Ütemezett vizsgálat**elemre.  

3.  Győződjön meg arról, hogy be van jelölve a **Legújabb vírus- és kémprogram-definíciók ellenőrzése ütemezett vizsgálat futtatása előtt** jelölőnégyzet, majd kattintson a **Módosítások mentése**gombra. Ha a számítógép rendszergazdai jelszót vagy megerősítést kér, adja meg a jelszót, illetve erősítse meg a műveletet.  

### <a name="to-check-for-new-definitions-manually"></a>Az új definíciók kézi ellenőrzése

 A Windows Defender vagy az Endpoint Protection automatikusan frissíti a számítógépen a vírus- és kémprogram-definíciókat. Ha a definíciók már nem frissültek (például egy hétig nem kapcsolta be a számítógép) több mint hét napja, a Windows Defender vagy az Endpoint Protection értesíti Önt, hogy a definíciók elavultak.  

1.  A **Start menüből** , vagy az értesítési területen lévő ikonra kattintva nyissa meg a Windows Defender- vagy az Endpoint Protection-ügyfelet.  

2.  Az új definíciók kézi ellenőrzéséhez kattintson a **Frissítés** lapra, majd a **Definíciók frissítése**parancsra.  

##  <a name="how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Hogyan távolítsa el vagy a Windows Defender vagy az Endpoint Protection által karanténba helyezett elemek visszaállítása?  

 Egy szoftver karanténba tételekor a Windows Defender vagy az Endpoint Protection áthelyezi azt a számítógépen, és megakadályozza a működését, amíg a felhasználó visszaállítja vagy eltávolítja azt a számítógépről.  

 Ha a számítógép rendszergazdai jelszót vagy megerősítést kér az itt ismertetett eljárás bármelyik lépéséhez, adja meg a jelszót, illetve erősítse meg a műveletet.  

###  <a name="to-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>A Windows Defender vagy az Endpoint Protection által karanténba helyezett elemek eltávolítása és visszaállítása


1.  Kattintson az **Előzmények** lapra, válassza a **Karanténba zárt elemek**, majd ismét a **Karanténba zárt elemek** lehetőséget.  

2.  Az összes elem megtekintéséhez kattintson a **Részletek megtekintése** elemre.  

3.  Tekintse át az egyes elemeket, majd mindegyik esetében kattintson az **Eltávolítás** vagy a **Visszaállítás**lehetőségre. Ha minden karanténba helyezett elemet el szeretne távolítani a számítógépről, kattintson **Az összes eltávolítása**lehetőségre.  

##  <a name="what-is-real-time-protection"></a>Mi az a valós idejű védelem?  

 A valós idejű védelem lehetővé teszi, hogy a Windows Defender folyamatosan figyelje a számítógépet, és riasztást küldjön, amikor potenciális fenyegetések, például vírusok és kémprogramok próbálnak meg települni vagy futni a számítógépen. Mivel ez a funkció fontos része a számítógép Windows Defender általi védelmének, meg kell győződnie arról, hogy a valós idejű védelem mindig be van kapcsolva. Ha a valós idejű védelem kikapcsol, a Windows Defender értesíti, és megváltoztatja a számítógépen "™ â" œAt riskâ "s állapotát.  

 Amikor a valós idejű védelem fenyegetést vagy potenciális fenyegetést észlel, a Windows Defender egy értesítést jelenít meg. Az alábbi lehetőségek közül választhat:  

-   Kattintson a **Számítógép megtisztítása** gombra az észlelt elem eltávolításához. A Windows Defender automatikusan eltávolítja az elemet a számítógépről.  

-   Kattintson a **Részletek megjelenítése** hivatkozásra a Lehetséges veszélyforrás részletei ablak megnyitásához, majd válassza ki, hogy mely műveletet alkalmazza az észlelt elemre.  

 Kiválaszthatja, hogy a Windows Defender melyik szoftvereket és beállításokat figyelje, de a javasolt megoldás a valós idejű védelem bekapcsolása és az összes valós idejű védelmi beállítás engedélyezése. A következő táblázat az elérhető beállításokat ismerteti.  

|||  
|-|-|  
|**A valós idejű védelem beállításai**|**Cél**|  
|Minden letöltött fájl vizsgálata|Ezzel a beállítással figyelheti a letöltött fájlokat és programokat, beleértve a Windows Internet Explorer és a Microsoft Outlook® Express által automatikusan letöltött fájlokat, például az ActiveX® vezérlőket és a szoftvertelepítő programokat. Ezeket a fájlokat a böngésző töltheti le, telepítheti és futtathatja. A fájlok között kártevő szoftverek, például vírusok, kémprogramok és más, vélhetően nemkívánatos szoftverek is előfordulhatnak, amelyeket a rendszer a felhasználó tudta nélkül telepít.<br /><br /> Ha használja a valós idejű védelmi beállítást, a Windows Defender folyamatosan figyeli a számítógépet, esetlegesen letöltött kártevő fájlok és programok után kutatva. Ez a figyelési funkció lehetővé teszi, hogy a Windows Defender ne lassítsa le a böngészést és a levelezést az egyes letölteni kívánt fájlok és programok ellenőrzésével.|  
|Fájl- és programtevékenység figyelése a számítógépen|Ezzel a beállítással figyelheti a számítógépen elinduló fájlokat és programokat, és értesítést kaphat az általuk vagy rajtuk elvégzett műveletekről. Ez azért fontos, mert a kártevő szoftverek képesek arra, hogy a telepített programok biztonsági réseit kihasználva a felhasználó tudta nélkül kártevő vagy nemkívánatos szoftvereket futtassanak. Például kémprogramok futhatnak a háttérben a gyakran használt programok elindításakor. A Windows Defender figyeli a programokat, és riasztást küld az észlelt gyanús tevékenységekről.|  
|Viselkedésfigyelés engedélyezése|Ezzel a beállítással azt figyelheti, hogy a rendszer viselkedésében előfordulnak-e olyan gyanús mintázatok, amelyeket a hagyományos víruskereső módszerekkel nem lehetne észlelni.|  
|Hálózatfelügyeleti rendszer engedélyezése|Ez a beállítás segít megvédeni a számítógépet: "œzero dayâ" biztonsági réseket ismert biztonsági rések, jelenleg között eltelt időszakot csökkentése a biztonsági rés felfedezése és a frissítés alkalmazása.|  

### <a name="to-turn-off-real-time-protection"></a>A valós idejű védelem kikapcsolása  

1.  Kattintson a **Beállítások**, majd a **Valós idejű védelem**elemre.  

2.  Törölje a kikapcsolni kívánt valós idejű védelmi lehetőségek melletti jelölőnégyzet jelölését, majd kattintson a **Módosítások mentése**parancsra. Ha a számítógép rendszergazdai jelszót vagy megerősítést kér, adja meg a jelszót, illetve erősítse meg a műveletet.  

##  <a name="how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer"></a>Hogyan állapítható meg, hogy, hogy a Windows Defender vagy az Endpoint Protection fut a számítógépemen?  

 Miután telepítette a Windows Defendert a számítógépre, bezárhatja a fő ablakot, és hagyhatja, hogy a Windows Defender csendben fusson a háttérben. A Windows Defender továbbra is fut a számítógépen, megfigyeli azt, és segít a fenyegetések elleni védelemben.  

 Természetesen a Windows Defender futásáról mindig értesül, amikor értesítési üzeneteket jelenít meg az értesítési területen. Ezek az értesítések riasztják a Windows Defender által észlelt potenciális fenyegetésekről.  

 Más riasztási értesítéseket is kap, ha például valamiért ki van kapcsolva a valós idejű védelem, ha nem frissítette a vírus- és kémprogram-definíciókat néhány napig, vagy amikor a program frissítései elérhetővé válnak. A Windows Defender egy rövid értesítést is megjelenít, hogy tudja, éppen vizsgálja a számítógépet.  

> [!TIP]  

>Ha nem látja az értesítési területen a Windows Defender ikonra, kattintson a az értesítési területen lévő nyílra a rejtett ikonok, beleértve a Windows Defender ikon megjelenítése.  


 Az ikon színe a számítógép jelenlegi állapotától függ:  

-   A zöld állapot azt jelzi, hogy a számítógép „védett” állapotú.  

-   A sárga állapot azt jelzi, hogy a számítógép „potenciálisan védtelen” állapotú.  

-   A vörös állapot azt jelzi, hogy a számítógép „veszélyben” állapotú.  

##  <a name="how-to-set-up-windows-defender-or-endpoint-protection-alerts"></a>A Windows Defender vagy az Endpoint Protection-riasztások beállítása hogyan?  
 Ha a számítógépén fut a Windows Defender, automatikusan riasztást küld a vírusok, kémprogramok vagy más, vélhetően nemkívánatos szoftverek észlelésekor. Azt is beállíthatja, hogy a Windows Defender riasztást küldjön a még nem vizsgált szoftverek futtatásakor, vagy akkor, ha egy szoftver módosítást hajt végre a számítógépen.  

### <a name="to-set-up-alerts"></a>Riasztások beállítása  

1.  Kattintson a **Beállítások**, majd a **Valós idejű védelem**elemre.  

2.  Győződjön meg róla, hogy a **Valós idejű védelem bekapcsolása (ajánlott)** jelölőnégyzet be van jelölve.  

3.  Jelölje be a futtatni kívánt valós idejű védelmi lehetőségek melletti jelölőnégyzeteket, majd kattintson a **Módosítások mentése**gombra. Ha a számítógép rendszergazdai jelszót vagy megerősítést kér, adja meg a jelszót, illetve erősítse meg a műveletet.  

### <a name="see-also"></a>További információ  
 [A Windows Defender vagy az Endpoint Protection ügyfél elhárítása](troubleshoot-endpoint-client.md)   

 [Az Endpoint Protection-ügyfél súgója](endpoint-protection-client-help.md)

