---
title: "Biztonság és adatvédelem az operációs rendszer központi telepítése |} Microsoft Docs"
description: "Ismerje meg a biztonsági és adatvédelmi gyakorlati tanácsok az operációs rendszer központi telepítéséhez a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ee5928f-3d72-4b00-8156-1e0d1030a96c
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 5632a753fc565312a80b2ed69ce438335b3fad50
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-operating-system-deployment-in-system-center-configuration-manager"></a>Az operációs rendszerek központi telepítésének biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör biztonsági és adatvédelmi információ az operációs rendszer központi telepítéséhez a System Center Configuration Managerben.  

##  <a name="BKMK_Security_HardwareInventory"></a>Ajánlott biztonsági eljárások az operációs rendszer központi telepítése  
 Használja az alábbi ajánlott biztonsági eljárásokat a Configuration Manager operációs rendszerek központi telepítésekor:  

-   **Alkalmazzon hozzáférés-vezérlést a rendszerindító adathordozók védelméhez**  

     Amikor rendszerindító adathordozót hoz létre, mindig használjon jelszót az adathordozó védelméhez. A rendszer azonban még jelszó használata esetén is csak a bizalmas adatokat tartalmazó fájlokat titkosítja, és minden fájl felülírható.  

     Korlátozza az adathordozó fizikai hozzáférését annak megakadályozásához, hogy a támadók kriptográfiai támadásokkal meg tudják szerezni az ügyfél-hitelesítési tanúsítványt.  

     A rendszer kivonatot készít a tartalomból, és azt az eredeti házirenddel együtt kell használni, ezzel akadályozható meg, hogy az ügyfelek illetéktelenül módosított tartalmat vagy ügyfélházirendet telepítsenek.  Ha a tartalomkivonat érvénytelen, vagy a tartalom nem felel meg a házirendnek, az ügyfél nem fogja tudni használni a rendszerindító adathordozót. Csak a tartalomhoz készül kivonat, a házirendhez nem, viszont jelszó használata esetén a rendszer titkosítja és védelemmel látja el a házirendet, ami megnehezíti a támadók számára a házirend módosítását.  

-   **Használjon biztonságos helyet, az operációs rendszeri lemezképek részére adathordozó létrehozásakor**  

     Ha jogosulatlan felhasználók hozzáférhetnek a helyhez, illetéktelenül módosíthatják a létrehozott fájlokat, és lefoglalhatják az összes szabad lemezterületet, megakadályozva ezzel az adathordozó létrehozását.  

-   **Tanúsítványfájlokat (.pfx) erős jelszóval védeni, és tárolja ezeket a hálózaton, ha biztonságos a hálózati csatornát, amikor importálja a fájlokat a Configuration Managerbe**  

     Ha jelszó kell a rendszerindító adathordozóhoz használt ügyfél-hitelesítési tanúsítvány importálásához, ez segít megvédeni a tanúsítványt a támadóktól.  

     A hálózati hely és a helykiszolgáló között használja az SMB-aláírást vagy az IPsec protokollt, hogy megakadályozza a tanúsítványfájl támadók általi illetéktelen módosítását.  

-   **Ha az ügyféltanúsítvány biztonsága sérül, blokkolja a tanúsítványt a Configuration Manager alkalmazásból, és vonja vissza, ha a PKI-tanúsítványról szó**  

     Ha rendszerindító adathordozó és PXE-rendszerindítás használatával telepít központilag operációs rendszert, rendelkeznie kell ügyfél-hitelesítési tanúsítvánnyal és titkos kulccsal. Ha a tanúsítvány biztonsága sérül, blokkolja a tanúsítványt a **Felügyelet** munkaterület **Biztonság** csomópontjában található **Tanúsítványok** csomópontban.  

-   **Ha az SMS-szolgáltató egy vagy a helykiszolgálótól eltérő számítógépen, biztonságos rendszerindító lemezképek védelméhez a kommunikációs csatorna**  

     Amikor módosítja a rendszerindító lemezképeket, és az SMS-szolgáltató a helykiszolgálótól különböző kiszolgálón fut, a rendszerindító lemezképek ki vannak téve a támadás veszélyének. SMB-aláírás vagy az IPsec protokoll használatával védheti az ilyen számítógépek közötti hálózati csatornát.  

-   **Terjesztési pontokat a PXE-ügyfélkommunikációt csak a biztonságos hálózati szegmensekben engedélyezése**  

     Amikor egy ügyfél PXE-rendszerindítási kérelmet küld, nincs mód annak ellenőrzésére, hogy a kérelmet a PXE-t támogató érvényes terjesztési pont szolgálja-e ki. Ez a helyzet a következő biztonsági kockázatokat vonja maga után:  

    -   A PXE-kérelmekre válaszoló támadó szándékú terjesztési pont illetéktelenül módosított lemezképet küldhet az ügyfeleknek.  

    -   A PXE által használt TFTP protokollt betolakodó illetéktelen személyek általi támadások érhetik, és a támadók rosszindulatú kódot küldhetnek az operációs rendszer fájljaiban, vagy létrehozhatnak támadó ügyfelet, amely közvetlenül a terjesztési pontnak küld TFTP-kérelmeket.  

    -   A támadók rosszindulatú ügyfél használatával szolgáltatásmegtagadási támadást indíthatnak a terjesztési pont ellen.  

     Használjon mélységi védelmet az olyan hálózati szegmensek védelméhez, ahol az ügyfelek PXE-kérelmek küldéséhez fognak hozzáférni a terjesztési pontokhoz.  

    > [!WARNING]  
    >  A felsorolt biztonsági kockázatok miatt ne engedélyezze a PXE-kommunikációt olyan terjesztési pont esetében, amely nem megbízható hálózatban, például szegélyhálózatban található.  

-   **PXE-képes terjesztési pontok csak a megadott hálózati felületeken PXE-kérésekre való válaszolás konfigurálása**  

     Ha a terjesztési pontot úgy állítja be, hogy minden hálózati felületen válaszoljon a PXE-kérelmekre, ezzel veszélyeztetheti a PXE szolgáltatást a nem megbízható hálózatokban  

-   **A PXE-rendszerindítást jelszó kérése**  

     Amikor PXE-rendszerindításhoz szükséges jelszó, ezzel biztosít biztonsági szintet a PXE-rendszerindítási folyamat, és megakadályozhatja, hogy támadó ügyfelek csatlakozzanak a Configuration Manager-hierarchiában.  

-   **Ne vegyen fel üzleti alkalmazásokat és szoftvereket, a PXE vagy csoportos küldéshez használandó lemezképekbe bizalmas adatokat tartalmazó**  

     A PXE-rendszerindításhoz és a csoportos küldéshez kapcsolódó biztonsági kockázatok miatt csökkentse annak veszélyét, hogy rosszindulatú számítógépek letölthetik az operációs rendszer lemezképét.  

-   **Ne vegyen fel üzleti alkalmazásokat és szoftvereket, a feladatütemezési változók használatával telepített szoftvercsomagok bizalmas adatokat tartalmazó**  

     Amikor feladatütemezési változók használatával hajtja végre a szoftvercsomagok központi telepítését, a telepített szoftverhez a használatára nem jogosult számítógépek és felhasználók is hozzáférhetnek.  

-   **A felhasználói állapot áttelepítésekor SMB-aláírást vagy IPsec használatával biztonságos az ügyfél és az állapotáttelepítési pont közötti hálózati csatornát.**  

     A kezdeti HTTP-csatlakozás után a felhasználói állapot áttelepítéséhez szükséges adatok átvitele az SMB protokoll használatával történik.  Ha nem védi a hálózati csatornát, a támadók olvashatják és módosíthatják ezeket az adatokat.  

-   **A felhasználói állapot áttelepítési eszköz (USMT) Configuration Manager által támogatott legújabb verzióját használja**  

     A Felhasználóiállapot-áttelepítő eszköz legújabb verziója biztonsági javításokat tartalmaz, és több beállítási lehetőséget kínál a felhasználói állapot adatainak áttelepítésekor.  

-   **Törölje kézzel a mappákat az állapotáttelepítési pont leszerelt**  

     Ha állapotáttelepítési pont valamelyik mappáját eltávolítja a Configuration Manager konzolon az állapotáttelepítési pont tulajdonságainál, a fizikai mappa nem törlődik. A felhasználói állapot adatait úgy védheti az információ felfedése ellen, hogy kézzel szünteti meg a hálózati megosztást és kézzel törli a mappát.  

-   **Nem konfigurálja a törlési házirendet a felhasználói állapot azonnali törlésére**  

     Ha az állapotáttelepítési ponton úgy állítja be a törlési házirendet, hogy a törlésre jelölt adatok azonnal törlődjenek, és egy támadó hozzá tud férni a felhasználói állapot adataihoz, mielőtt egy hitelesített számítógép tenné meg ezt, a felhasználói állapot adatai azonnal törlődnének. A **Törlés** időtartamot állítsa olyan hosszúságúra, hogy biztosítani tudja a felhasználói állapot adatainak sikeres helyreállítását.  

-   **Manuálisan törölje a számítógép-hozzárendeléseket, ha a felhasználói állapot adatainak helyreállítása befejeződött és ellenőrizve**  

     A Configuration Manager automatikusan nem távolítja el számítógép-hozzárendeléseket. A felhasználóiállapot-adatok azonosságának védelméhez kézzel törölje a feleslegessé vált számítógép-hozzárendeléseket.  

-   **Manuálisan készítsen biztonsági másolatot a felhasználói állapot áttelepítési adatait az állapotáttelepítési ponton**  

     A Configuration Manager biztonsági mentés nem tartalmazza a felhasználói állapot áttelepítési adatait.  

-   **Engedélyezze a BitLocker az operációs rendszer telepítése után**  

     Ha a számítógép támogatja a Bitlockert, az operációs rendszer felügyelet nélküli telepítéséhez azt egy feladatütemezési lépés használatával le kell tiltania. A Configuration Manager nem engedélyezi a Bitlockert az operációs rendszer telepítése után úgy kell manuálisan újra nem engedélyezi a BitLocker.  

-   **Alkalmazzon hozzáférés-vezérlést az előkészített adathordozók védelméhez**  

     Korlátozza az adathordozó fizikai hozzáférését annak megakadályozásához, hogy a támadók kriptográfiai támadásokkal meg tudják szerezni az ügyfél-hitelesítési tanúsítványt és a bizalmas adatokat.  

-   **Alkalmazzon hozzáférés-vezérlést a referencia-számítógépet lemezkép-készítési folyamatának védelméhez**  

     Ügyeljen arra, hogy az operációs rendszer lemezképének elkészítéséhez használt referencia-számítógép biztonságos környezetben legyen, és alkalmazzon megfelelő hozzáférés-vezérlési beállításokat annak megakadályozásához, hogy nem várt vagy rosszindulatú szoftvereket lehessen telepíteni, és így azok bekerüljenek a rögzített lemezképbe. Amikor rögzíti a lemezképet, ügyeljen arra, hogy a célként használt hálózati fájlmegosztás helye biztonságos legyen, hogy a lemezképet ne lehessen illetéktelenül módosítani a rögzítése után.  

-   **Mindig telepítse a legújabb biztonsági frissítéseket a referencia-számítógépen**  

     Ha a referencia-számítógépen naprakészek a biztonsági frissítések, csökken az első alkalommal elindított új számítógépek sebezhetőségének mértéke.  

-   **Ha ismeretlen számítógépre telepítenie kell az operációs rendszerek, alkalmazzon hozzáférés-vezérlést, hogy a jogosulatlan számítógépek csatlakozzanak a hálózathoz**  

     Bár az ismeretlen számítógépek kiépítése kényelmes megoldásként alkalmazható az új számítógépek igény szerinti központi telepítéséhez, azzal a kockázattal is jár, hogy a támadók megbízható ügyfélként jutnak be a hálózatba. Korlátozza a hálózat fizikai hozzáférését, és figyelje az ügyfeleket a jogosulatlan számítógépek felismeréséhez. Az operációs rendszer PXE környezetből kezdeményezett központi telepítésére válaszoló számítógépeken megsemmisülhet az összes adat az operációs rendszer telepítése után, ami a véletlenül formázott rendszerek elérhetőségének megszűnését eredményezheti.  

-   **Engedélyezze a csoportos küldésű csomagok titkosítása**  

     Minden operációs rendszer központi telepítési csomag lehetősége van a titkosítás engedélyezésére, amikor a Configuration Manager a csomag csoportos küldéssel. Ezzel a konfigurációval megakadályozható, hogy a támadó számítógépek csatlakozzanak a csoportos küldési munkamenethez, és a támadók illetéktelenül módosítsák az átvitt adatokat.  

-   **A jogosulatlan csoportos küldésre képes terjesztési pontok figyelése**  

     Ha a támadók hozzáférést szereznek a hálózathoz, támadó csoportos küldésű kiszolgálókat konfigurálhatnak az operációs rendszer központi telepítésének meghamisításához.  

-   **Amikor feladatütemezéseket exportál egy hálózati helyre, tegye biztonságossá a helyet, és a hálózati csatorna biztonságáról**  

     Korlátozza a hálózati mappához hozzáférő felhasználók körét.  

     A hálózati hely és a helykiszolgáló között használja az SMB-aláírást vagy az IPsec protokollt, hogy megakadályozza az exportált feladatütemezés támadók általi illetéktelen módosítását.  

-   **Ha feltölt egy virtuális merevlemezt a Virtual Machine Manager a kommunikációs csatorna biztonságáról.**  

     Ha a hálózaton keresztül továbbított adatok illetéktelen megakadályozásához használja az IP-biztonság (IPsec) vagy kiszolgálói üzenetblokk (SMB) a Configuration Manager konzolt futtató számítógép és a Virtual Machine Managert futtató számítógép között.  

-   **Ha a feladat feladatütemezési futtató fiókot kell használnia, további biztonsági intézkedésekkel**  

     Ha a fiókként futó feladatütemezést használja, hajtsa végre a következő óvintézkedéseket:  

    -   Használjon olyan fiókot, amelyhez csak a minimálisan szükséges engedélyek vannak megadva.  

    -   Ne használja a Hálózati hozzáférés fiókot ebben az esetben.  

    -   Ne tegye soha a fiókot tartományi rendszergazdává.  

     Továbbá:  

    -   Ehhez a fiókhoz ne konfiguráljon soha barangolási profilt. Amikor a feladatütemezés fut, le fogja tölteni a fiók barangolási profilját, ami a profilt a helyi számítógépen való hozzáféréshez sebezhetőnek hagyja.  

    -   Korlátozza a fiók hatókörét. Például különböző fiókként futó feladatütemezést hozzon létre az egyes feladatütemezésekhez, így ha az egyik fiók biztonsága sérül, csak az adott fiók által elérhető ügyfélszámítógépek kerülnek veszélybe. Ha a parancssornak a számítógépen rendszergazdai hozzáférésre van szüksége, fontolja meg olyan helyi rendszergazdai fiók létrehozását, amely minden számítógépen futtatja a feladatütemezést, és törölje ezt a fiókot rögtön, ha már nincs rá szükség.  

-   **Korlátozza és figyelje a az operációs rendszer központi telepítője biztonsági szerepkörrel rendelkező rendszergazdai felhasználók**  

     Az operációs rendszer központi telepítője biztonsági szerepkörrel rendelkező rendszergazdák önaláírt tanúsítványokat, amelyek ezután felhasználhatók ügyfél megszemélyesítése, és megszerezhetik az ügyfélházirendet a Configuration Manager hozhat létre.  

### <a name="security-issues-for-operating-system-deployment"></a>Az operációs rendszerek központi telepítésével kapcsolatos biztonsági problémák  
 Bár az operációs rendszer központi telepítése kényelmes megoldás lehet a legbiztonságosabb operációs rendszerek és konfigurációk központi telepítésekor a hálózatban lévő számítógépekre, számolni kell a következő biztonsági kockázatokkal:  

-   Információfelfedés és szolgáltatásmegtagadás  

     Ha egy támadó megszerzi a Configuration Manager infrastruktúrájának irányítását, tetszőleges feladatütemezést, beleértve például az összes ügyfélszámítógép merevlemezének formázását futtathat. A konfigurált feladatütemezések tartalmazhatnak bizalmas adatokat, például a tartományhoz valós csatlakozáshoz szükséges fiókokat és mennyiségi licenckulcsokat.  

-   Megszemélyesítés és a jogosultsági szint megemelése  

     A feladatütemezések tartományhoz csatlakoztathatják a számítógépet, ami hitelesített hálózati hozzáféréshez juttathatja a támadó számítógépeket. Az operációs rendszerek központi telepítésével kapcsolatos további fontos biztonsági teendő a rendszerindító adathordozóval és a PXE-rendszerindítással végzett központi telepítéshez használt ügyfél-hitelesítési tanúsítvány védelme. Ha rögzíti az ügyfél-hitelesítési tanúsítványt, a támadók hozzáférhetnek a nyilvános kulcshoz, majd ezzel érvényes ügyfelet személyesíthetnek meg a hálózatban.  

     Ha egy támadó megszerzi a rendszerindító adathordozóval és PXE rendszerindítás során használt, ez a tanúsítvány segítségével a Configuration Manager érvényes ügyfél megszemélyesítése. Ez esetben a támadó gép bizalmas adatokat tartalmazó házirendeket is letölthet.  

     Ha a kliensgépek Hálózati hozzáférés fiók használatával férnek hozzá az állapotáttelepítési ponton tárolt adatokhoz, ezek a kliensgépek a Hálózati hozzáférés fiókot használó valamely másik kliensgép azonosítóját használják, és hozzáférhetnek annak adataihoz az állapotáttelepítési pontra vonatkozóan. Az adatok titkosítása csak az eredeti kliensgép számára teszi lehetővé az olvasásukat, viszont illetéktelenek is hozzáférhetnek az adatokhoz, vagy törölhetik azokat.  

-   Ügyfél-hitelesítést az állapotáttelepítési pont egy Configuration Manager-jogkivonatot, amely a felügyeleti pont által kiadott használatával érhető el.  

     Emellett a Configuration Manager nem korlátozza vagy kezeli az állapotáttelepítési ponton tárolt adatok mennyisége és a támadó feltöltve a rendelkezésre álló lemezterületet és szolgáltatásmegtagadást okozhat.  

-   Gyűjteményváltozók használata esetén a helyi rendszergazdák bizalmas adatokhoz férhetnek hozzá.  

     Bár a gyűjteményváltozók rugalmas megoldást kínálnak az operációs rendszerek telepítésére, nemkívánatos információfelfedést okozhatnak.  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Adatvédelmi információ az operációs rendszer központi telepítéséhez  
 Amellett, hogy operációs rendszer nélküli számítógépek operációs rendszerek telepítésére, a Configuration Manager segítségével a felhasználói fájlok és beállítások áttelepítése egyik számítógépről a másikra. A rendszergazda adja meg az átvinni kívánt adatokat, köztük a személyes adatfájlokat, beállításokat és a böngésző által használt cookie-kat.  

 A rendszer az állapotáttelepítési pontokon tárolja az információkat, és átvitel, illetve tárolás közben titkosítja azokat. Az információkat az állapotadattal kapcsolatba hozott új számítógép is lekérheti. Ha az új számítógép elveszíti az információk lekéréséhez szükséges kulcsot, a Configuration Manager egy rendszergazdája hozzáférhet az adatokhoz és új számítógéphez társíthatja azokat, amennyiben a rendszergazda jogosult megtekinteni a helyreállítási adatokat a számítógép-társítási objektumpéldányokon. Miután az új számítógép helyreállította az állapotadatokat, egy nap után alapértelmezés szerint törli az adatokat. Tetszés szerint beállíthatja, hogy az állapotáttelepítési pont mikor távolítja el a törlésre megjelölt adatokat. Az állapotáttelepítési pontra vonatkozó adatokat a rendszer nem tárolja a helyadatbázisban és nem küldi el a Microsoftnak.  

 Ha rendszerindító adathordozókat használ az operációs rendszer képének telepítéséhez, alkalmazza mindig az alapértelmezett opciót, mely jelszavas védelemmel látja el a rendszerindító adathordozót. A jelszó titkosítja a feladatütemezésben található összes változót, viszont a változókon kívül tárolt adatok sebezhetőek maradhatnak.  

 Az operációs rendszer telepítése során feladatütemezéssel számos különböző feladat hajtható végre, mint például alkalmazások és szoftverfrissítések telepítése. A feladatütemezés konfigurálása során a szoftvertelepítés adatvédelmi vonatkozásaival is tisztában kell lennie.  

 Ha anélkül tölt fel egy virtuális merevlemezt a Virtual Machine Managerbe, hogy előbb a Sysprep használatával törölné a képet, a feltöltött virtuális merevlemez személyes adatokat tartalmazhat az eredeti képből.  

 A Configuration Manager valósítja meg az operációs rendszer központi telepítése alapértelmezés szerint, és több konfigurációs lépésre van szükség, mielőtt felhasználói állapotadatokat gyűjthet vagy készíthet feladatütemezéseket vagy rendszerindító lemezképeket.  

 Az operációs rendszer telepítésének konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

