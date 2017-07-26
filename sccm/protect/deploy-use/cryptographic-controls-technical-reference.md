---
title: "Titkosítási funkciók műszaki útmutatója |} Microsoft Docs"
description: "További információk a hogyan aláírási és titkosítási segít megvédeni támadások a System Center Configuration Manager adatainak olvasása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c63dcc5-a1bd-4037-959a-2e6ba0fd1b2c
caps.latest.revision: 6
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 09d319ce817c925ac002a27733d2ce35464eeca7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="cryptographic-controls-technical-reference"></a>Titkosítási funkciók műszaki útmutatója

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


System Center Configuration Manager védelme a Configuration Manager-hierarchiában lévő eszközök kezeléséhez használja az aláírásra és titkosításra. Az aláírás, ha az adatok módosulnak az átvitel során, a rendszer elveti. Titkosítás megakadályozza, hogy egy támadó olvashassa az adatokat egy hálózati protokollelemző eszköz használatával.  

 Által a Configuration Manager az aláíráshoz használt elsődleges kivonatoló algoritmus az SHA-256. Két Configuration Manager-hely kommunikál egymással, amikor bejelentkeznek a kommunikációt az SHA-256. A Configuration Manager megvalósított elsődleges titkosítási algoritmus a 3DES. Az adatok tárolását a Configuration Manager-adatbázis és az ügyfél HTTP-kommunikációhoz használatos. Ügyfél-kommunikáció HTTPS-KAPCSOLATON keresztül használatakor konfigurálhatja a nyilvános kulcsokra épülő infrastruktúra (PKI), hogy RSA-tanúsítványokat használ a megadott legerősebb kivonatoló algoritmusokkal és leghosszabb kulcsokkal, ismertetett [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md).  

 A Windows-alapú operációs rendszerek legtöbb titkosítási műveleteket a Configuration Manager a Windows CryptoAPI kódtárából (Rsaenh.dll) az SHA-2, 3DES és AES és RSA algoritmust használja.  

> [!IMPORTANT]  
>  Az SSL biztonsági réseivel kapcsolat javasolt módosításokról adatainak megjelenítéséhez [kapcsolatos SSL biztonsági réseivel](#about-ssl-vulnerabilities).  

##  <a name="cryptographic-controls-for-configuration-manager-operations"></a>Titkosítási funkciók a Configuration Manager műveleteihez  
 Információk a Configuration Manager aláírhatók és titkosíthatók, függetlenül attól, hogy PKI-tanúsítványokat használ a Configuration Managerrel.  

### <a name="policy-signing-and-encryption"></a>Házirend aláírása és titkosítása  
 Az ügyfélházirend-hozzárendeléseket a helykiszolgáló önaláírt aláíró tanúsítványa írja alá, hogy megelőzhető legyen az a biztonsági kockázat, hogy egy sérült integritású felügyeleti pont küld illetéktelenül módosított házirendeket. Ez azért fontos, ha Internet alapú ügyfélfelügyelethez használnak, mert ebben a környezetben az internetes kommunikációnak kitett felügyeleti pont szükséges.  

 A házirend a 3DES titkosított, amikor a bizalmas adatokat tartalmaz. A bizalmas adatokat tartalmazó házirendet csak a hitelesített ügyfelek kapják meg. A bizalmas adatokat nem tartalmazó házirendet a rendszer nem titkosítja.  

 Ha házirend tárolják az ügyfeleken, az a Data Protection alkalmazásprogramozási felületet (DPAPI) titkosított.  

### <a name="policy-hashing"></a>Házirend-kivonatolás  
 Ha a Configuration Manager-ügyfelek házirendre vonatkozó kérelmet, akkor először házirend-hozzárendelést kapnak, hogy tudják, hogy mely házirendek vonatkoznak rájuk, majd csak ezeket a házirendtörzseket kérnek. Minden házirend-hozzárendelés tartalmazza a megfelelő házirendtörzs kiszámított kivonatát. Az ügyfél lekéri a megfelelő házirendtörzseket, majd kiszámítja a kivonatot az adott törzshöz. Ha a letöltött házirendtörzs kivonata nem egyezik meg a házirend-hozzárendelésben lévő kivonattal, az ügyfél elveti a házirendtörzset.  

 A házirendek kivonatolása SHA-1 és SHA-256 algoritmussal történik.  

### <a name="content-hashing"></a>Tartalomkivonatolás  
 A helykiszolgáló terjesztéskezelő szolgáltatása kivonatolja a tartalomfájlokat az összes csomaghoz. A házirend-szolgáltató felveszi a kivonatot a szoftverterjesztési házirendbe. A Configuration Manager-ügyfél letölti a tartalmat, amikor az ügyfél helyben újragenerálja a kivonatot, és összehasonlítja a házirendben lévővel. Ha a kivonatok megegyeznek, akkor a tartalmat nem módosították, így az ügyfél telepíti azt. Ha a tartalom akár egyetlen bájtja is módosult, akkor a kivonatok nem egyeznek meg, és a szoftver nem települ. Ez az ellenőrzés hozzájárul ahhoz, hogy a megfelelő szoftver települjön, mert a tényleges tartalmat hasonlítja össze a házirenddel.  

 A tartalmak alapértelmezett kivonatoló algoritmusa az SHA-256. Ha módosítani szeretné az alapértelmezett értéket, az a Configuration Manager Software Development Kit (SDK) dokumentációjában találhat.  

 Nem minden eszköz támogatja a tartalomkivonatolást. A kivételek a következők:  

-   Windows rendszerű ügyfelek App-V tartalom adatfolyamként való továbbításakor.  

-   Windows Phone-ügyfelek esetében, ha ezek az ügyfelek ellenőrzik a megbízható forrás által aláírt alkalmazás aláírását.  

-   Windows RT-alapú ügyfél abban az esetben, ha ezek az ügyfelek ellenőrzik az alkalmazások aláírását, amely egy megbízható forrás által aláírt és a csomag teljes nevének (PFN) érvényesítése is használhatja.  

-   iOS, abban az esetben, ha ezek az ügyfelek ellenőrzik a megbízható forrás bármely fejlesztői tanúsítványával által aláírt alkalmazás aláírását.  

-   Nokia-ügyfél, azonban ezek az ügyfelek ellenőrzik az önaláírt tanúsítványt használó alkalmazások aláírását. illetve a megbízható forrásból származó tanúsítvány aláírását, és a tanúsítvánnyal aláírhatók a Nokia Symbian Installation Source (SIS) telepítési forrású alkalmazások.  

-   Android. Ezenkívül ezek az eszközök nem használnak aláírás-ellenőrzést az alkalmazástelepítéshez.  

-   Az SHA-256-ot nem támogató Linux- vagy UNIX-verziókon futó ügyfelek. További információkért lásd: [Linux és UNIX rendszerű számítógépekre a System Center Configuration Manager ügyfél központi telepítésének tervezése](../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

### <a name="inventory-signing-and-encryption"></a>A szoftverleltár-aláíráshoz és titkosításhoz  
 Az ügyfelek által a felügyeleti pontokra küldött leltárt mindig aláírják az eszközök, függetlenül attól, hogy HTTP vagy HTTPS használatával kommunikálnak a felügyeleti pontokkal. Ha HTTP-t használnak, választhatja ezen adatok titkosítását a bevált biztonsági gyakorlat szerint.  

### <a name="state-migration-encryption"></a>Állapotáttelepítés titkosítása  
 Az operációsrendszer-telepítésre szolgáló állapotáttelepítési pontokon tárolt adatokat a Felhasználóáttelepítő (USMT) mindig titkosítja 3DES használatával.  

### <a name="encryption-for-multicast-packages-to-deploy-operating-systems"></a>Operációs rendszerek központi telepítéséhez csoportos küldésű csomagok titkosítása  
 Az operációs rendszerek központi telepítésére szolgáló minden csomaghoz engedélyezheti a titkosítást, ha a csomagot csoportos küldéssel továbbítják a számítógépekre. A titkosítás Advanced Encryption Standard (AES) algoritmussal történik. Ha engedélyezi a titkosítást, nincs szükség további tanúsítványkonfigurálásra. A csoportos küldésre képes terjesztési pont automatikusan generál szimmetrikus kulcsokat a csomag titkosításához. Minden csomagnak más a titkosítási kulcsa. A kulcsot a csoportos küldésre képes terjesztési pont tárolja normál Windows API-k használatával. Amikor az ügyfél csatlakozik a csoportos küldési munkamenethez, végbemegy a kulcscsere egy PKI-kiadású ügyfél-hitelesítési tanúsítvánnyal (ha az ügyfél HTTPS-t használ) vagy az önaláírt tanúsítvánnyal (ha az ügyfél HTTP-t használ) titkosított csatornán. Az ügyfél a kulcsot csak a csoportos küldési munkamenet idejére tárolja a memóriában.  

### <a name="encryption-for-media-to-deploy-operating-systems"></a>Operációs rendszerek központi telepítéséhez adathordozók titkosítása  
 Amikor adathordozóval telepít központilag operációs rendszereket, és jelszót ad meg az adathordozó védelmére, a környezeti változók Advanced Encryption Standard (AES) algoritmussal vannak titkosítva. Az adathordozón lévő más adatok, köztük a csomagok és az alkalmazástartalmak nincsenek titkosítva.  

### <a name="encryption-for-content-that-is-hosted-on-cloud-based-distribution-points"></a>A felhő alapú terjesztési pontokon szolgáltatott tartalom titkosítása  
 A System Center 2012 Configuration Manager SP1, kezdve felhő alapú terjesztési pontok, a terjesztési pontokra feltöltött tartalom Advanced Encryption Standard (AES) algoritmussal egy 256 bites kulcshosszal titkosítottak. A tartalmat a rendszer minden tartalomfrissítéskor újra titkosítja. Amikor az ügyfelek letöltik a tartalmat, azt a HTTPS-kapcsolat titkosítja és védi.  

### <a name="signing-in-software-updates"></a>Szoftverfrissítések aláírása  
 Minden szoftverfrissítést megbízható közzétevőnek kell aláírnia az illetéktelen módosítással szembeni védelem érdekében. Az ügyfélszámítógépeken a Windows Update Agent (WUA) keresi a katalógusban lévő frissítéseket, de nem telepíti a frissítést, ha nem találja meg a digitális tanúsítványt a Megbízható közzétevők tárban a helyi számítógépen. Ha önaláírt tanúsítványt (például WSUS Publishers Self-signed) használtak a frissítéskatalógus közzétételére, a tanúsítványnak szerepelnie kell a megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárában is a helyi számítógépen a tanúsítvány érvényességének ellenőrzéséhez. A WUA azt is ellenőrzi, hogy **Az intraneten futó Microsoft frissítési szolgáltatás helyéről származó aláírt tartalom engedélyezése** csoportházirend-beállítás engedélyezve van-e a számítógépen. Ezt a házirend-beállítást engedélyezni kell ahhoz, hogy a WUA tudjon olyan frissítéseket keresni, amelyeket a frissítés-közzétevővel hoztak létre és tettek közzé.  

 Amikor a szoftverfrissítéseket a System Center frissítés-közzétevő teszi közzé, egy digitális tanúsítvány aláírja a szoftverfrissítéseket, amikor azok közzététele megtörténik egy frissítési kiszolgálón. Megadhat egy PKI-tanúsítványt, vagy konfigurálhatja a System Center frissítés-közzétevőt önaláírt tanúsítvány létrehozására a szoftverfrissítés aláírásához.  

### <a name="signed-configuration-data-for-compliance-settings"></a>Aláírt konfigurációs adatok a megfelelőségi beállításokhoz  
 Amikor konfigurációs adatokat importál, a Configuration Manager ellenőrzi a fájl digitális aláírását. Ha a fájlok nincsenek aláírva, vagy ha a digitális aláírás nem felel meg az ellenőrzésen, a rendszer figyelmezteti és rákérdez az importálás folytatására. Csak akkor folytassa a konfigurációs adatok importálását, ha kimondottan megbízik a közzétevőben és a fájlok integritásában.  

### <a name="encryption-and-hashing-for-client-notification"></a>Titkosítás és kivonatolás az ügyfélértesítéshez  
 Ha ügyfélértesítést használ, akkor minden kommunikáció a TLS protokollt, valamint a kiszolgáló és az ügyfél operációs rendszere által egyeztetett legerősebb titkosítást használja. Például egy Windows 7 rendszerű ügyfél és egy Windows Server 2008 R2 rendszerű felügyeleti pont támogathatja a 128 bites AES titkosítást, míg egy Vista rendszerű ügyfélszámítógép ugyanazzal a felügyeleti ponttal 3DES titkosítást fog egyeztetni. Ugyanez az egyeztetés zajlik le az ügyfélértesítés közben továbbított csomagok kivonatolásához, ami SHA-1 vagy SHA-2 algoritmust használ.  

##  <a name="certificates-used-by-configuration-manager"></a>A Configuration Manager által használt tanúsítványok  
 A nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítványokat, amelyek segítségével a Configuration Manager, semmilyen különleges követelmények vagy -korlátozások listáját, és hogyan használják a tanúsítványokat, [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md). A lista tartalmazza a támogatott kivonatoló algoritmusokat és kulcshosszokat. A legtöbb tanúsítvány támogatja az SHA-256 algoritmust és a 2048 bites kulcshosszt.  

> [!NOTE]  
>  Configuration Manager által használt minden tanúsítvány csak egybájtos karaktereket a tulajdonos neve vagy a tulajdonos alternatív nevének tartalmaznia kell.  

 Az alábbi helyzetekben PKI-tanúsítványok szükségesek:  

-   Amikor Ön felügyeli a Configuration Manager-ügyfelek az interneten.  

-   Amikor Ön felügyeli a mobileszközökön a Configuration Manager-ügyfelek.  

-   Ha Mac számítógépeket felügyel.  

-   Ha felhőalapú terjesztési pontokat használ.  

-   Ha Intel AMT-alapú számítógépeket felügyel sávon kívül.  

 A legtöbb más Configuration Manager-kommunikációhoz, amely tanúsítványt igényel a hitelesítési, aláírási vagy titkosítási célokra, a Configuration Manager automatikusan PKI-tanúsítványokat használ, ha ilyenek. Ha nem érhető el, a Configuration Manager önaláírt tanúsítványokat hoz létre.  

 A Configuration Manager használ a PKI-tanúsítványokat, amikor mobileszközöket felügyel az Exchange Server-összekötővel.  

### <a name="mobile-device-management-and-pki-certificates"></a>Mobileszköz-felügyelet és PKI-tanúsítványok  
 Ha a mobileszközt nem tiltotta le a mobilszolgáltató, is használhatja a Configuration Manager vagy a Microsoft Intune használatával igényelhet és telepíthet ügyféltanúsítványt. Ezt a tanúsítványt az ügyfél a mobileszköz és a Configuration Manager helyrendszerei vagy a Microsoft Intune szolgáltatások közötti kölcsönös hitelesítést biztosít. Ha a mobileszköz le van tiltva, nem használhat a Configuration Manager vagy az Intune szolgáltatást tanúsítványok központi telepítésére.  

 Ha engedélyezi a hardverleltárt a mobileszközök kezeléséhez, a Configuration Manager vagy az Intune szintén leltárba veszi a mobileszközön telepített tanúsítványokat.  

### <a name="out-of-band-management-and-pki-certificates"></a>Sávon kívüli felügyelet és PKI-tanúsítványok  
 Az Intel AMT-alapú sávon kívüli felügyelet legalább két típusú PKI-kiadású tanúsítványt használ: AMT kiépítési tanúsítványt és webkiszolgálói tanúsítványt.  

 A sávon kívüli szolgáltatási pont AMT-kiépítési tanúsítvánnyal készíti elő a számítógépeket a sávon kívüli felügyeletre. A kiépítendő AMT-alapú számítógépeknek meg kell bízniuk a sávon kívüli felügyeleti pont által bemutatott tanúsítványban. Alapértelmezésben az AMT-alapú számítógépeket külső hitelesítésszolgáltatók (például VeriSign, Go Daddy, Comodo és Starfield) használatára konfigurálja a számítógép gyártója. Ha szerez be az egyik külső hitelesítésszolgáltatótól, és a Configuration Manager a kiépítési tanúsítvány használatára konfigurálja, AMT-alapú számítógépek meg fognak bízni a kiépítési tanúsítvány Hitelesítésszolgáltatójában, és a kiépítés sikeres lehet. Azonban bevált biztonsági gyakorlat az AMT-kiépítési tanúsítvány saját belső hitelesítésszolgáltatóval történő kibocsátása.  

 Az AMT-alapú számítógépek egy webkiszolgáló-összetevőt futtatnak belső vezérlőprogramjukban, és ez a webkiszolgáló-összetevő titkosítja a kommunikációs csatornát a sávon kívüli szolgáltatási ponttal Transport Layer Security (TLS) használatával. Az AMT BIOS-ához nincs felhasználói felület, ahol manuálisan lehetne konfigurálni a tanúsítványt, így Microsoft vállalati hitelesítésszolgáltatóra van szükség, amely automatikusan jóváhagyja a kérelmező AMT-alapú számítógépekről érkező tanúsítványkéréseket. A kérelem a kérelemformátumhoz PKCS#10 szabványt használ, amely PKCS#7 szabvánnyal továbbítja a tanúsítványadatokat az AMT-alapú számítógépre.  

 Bár az AMT-alapú számítógép hitelesítve van az azt felügyelő számítógép számára, nincs ennek megfelelő PKI-ügyféltanúsítvány a felügyelő számítógépen, ezért ezek a kommunikációk Kerberos vagy HTTP Digest hitelesítést használnak. HTTP Digest használatakor a titkosítás TLS protokollal történik.  

 A sávon kívüli AMT-alapú számítógépek felügyeletéhez még egy tanúsítványtípus lehet szükséges: egy opcionális ügyféltanúsítvány a 802.1X-alapú hitelesítéssel rendelkező vezetékes és vezeték nélküli hálózatokhoz. Az ügyféltanúsítványra szüksége lehet az AMT-alapú számítógépnek a RADIUS-kiszolgálón történő hitelesítéshez. Ha a RADIUS-kiszolgáló EAP-TLS hitelesítésre van konfigurálva, mindig szükség van ügyféltanúsítványra. Ha a RADIUS-kiszolgáló EAP-TTLS/MSCHAPv2 vagy PEAPv0/EAP-MSCHAPv2 hitelesítésre van konfigurálva, a RADIUS-konfiguráció megadja, hogy szükség van-e ügyféltanúsítványra. Ezt a tanúsítványt az AMT-alapú számítógép kérelmezi ugyanazzal az eljárással, mint a webkiszolgálói tanúsítvány igénylésekor.  

### <a name="operating-system-deployment-and-pki-certificates"></a>Operációs rendszer központi telepítése és PKI-tanúsítványok  
 Használatakor a Configuration Manager operációs rendszerek központi telepítéséhez, és a felügyeleti pont HTTPS-ügyfélkapcsolatokat igényel, az ügyfélszámítógépnek is rendelkeznie kell tanúsítvánnyal kommunikálni a felügyeleti ponttal, akkor is, ha átmeneti fázisban vannak, például egy feladatütemezési adathordozóról vagy egy PXE-képes terjesztési pontról végeznek rendszerindítást. Ez a forgatókönyv támogatásához létre kell hoznia PKI ügyfél-hitelesítési tanúsítványt és és titkos kulcs exportálása és importálhatja a helykiszolgáló tulajdonságaiba és is hozzáadhat a felügyeleti pointâ "™ s megbízható legfelső szintű Hitelesítésszolgáltatói tanúsítvány.  

 Ha rendszerindító adathordozót hoz létre, akkor a rendszerindító adathordozó létrehozásakor importálja az ügyfél-hitelesítési tanúsítványt. Állítson be jelszót a rendszerindító adathordozón a titkos kulcs és a feladatütemezésben konfigurált többi bizalmas adat védelme érdekében. A rendszerindító adathordozóról indított minden számítógép ugyanazt a tanúsítványt mutatja be a felügyeleti pontnak, amely szükséges az ügyfélfunkciókhoz, például az ügyfélházirend igényléséhez.  

 Ha PXE-rendszerindítást végez, akkor importálja az ügyfél-hitelesítési tanúsítványt a PXE-t támogató terjesztési pontra, így a rendszer ugyanazt a tanúsítványt használja minden ügyfélhez, amely erről a PXE-t támogató terjesztési pontról indul. A bevált biztonsági gyakorlatnak megfelelően tegye kötelezővé a számítógépüket PXE szolgáltatáshoz csatlakoztató felhasználóknak jelszó megadását a titkos kulcs és a feladatütemezésben lévő többi bizalmas adat védelme érdekében.  

 Ha az ügyfél-hitelesítési tanúsítványok bármelyikének integritása sérül, tiltsa le a tanúsítványokat a **Tanúsítványok** beállításban az **Adminisztráció** munkaterület **Biztonság** csomópontjában. A tanúsítványok kezeléséhez rendelkeznie kell **Operációs rendszer központi telepítéséhez szükséges tanúsítvány kezelése** jogosultsággal.  

 Miután az operációs rendszer telepítve lesz, és a Configuration Manager telepítve van, az ügyfélnek szüksége van a saját PKI ügyfél-hitelesítési tanúsítvány HTTPS ügyfél-kommunikációhoz.  

### <a name="isv-proxy-solutions-and-pki-certificates"></a>Független Szoftverszállítói proxymegoldások és PKI-tanúsítványok  
 A független szoftverszállítók (ISV) rendszert a Configuration Manager bővítő alkalmazásokat hozhat létre. Például létrehozhatnak olyan bővítményeket, amelyek támogatják a nem Windows-alapú ügyfélplatformokat (például Macintosh vagy UNIX rendszerű számítógépeket). Ha viszont a helyrendszerek HTTPS ügyfélkapcsolatokat igényelnek, ezeknek az ügyfeleknek a hellyel való kommunikációhoz is PKI-tanúsítványokat kell használniuk. A Configuration Manager lehetővé teszi a rendeljen hozzá egy tanúsítványt az ISV-proxyhoz, lehetővé téve a kommunikációt az ISV-proxy ügyfelek és a felügyeleti pont között. Ha olyan bővítményeket használ, amelyekhez ISV-proxytanúsítvány szükséges, nézze meg az adott termék dokumentációját. ISV-proxytanúsítványok létrehozásával kapcsolatos további információkért lásd: a Configuration Manager szoftver szoftverfejlesztői készletét (SDK).  

 Ha az ISV-tanúsítvány integritása sérül, tiltsa le a tanúsítványt a **Tanúsítványok** beállításban az **Adminisztráció** munkaterület **Biztonság** csomópontjában.  

### <a name="asset-intelligence-and-certificates"></a>Eszközintelligencia és tanúsítványok  
 Egy X.509 tanúsítvánnyal, amely az Eszközintelligencia szinkronizálási pont használatával kapcsolódik a Microsoft a Configuration Manager telepíti. Configuration Manager ezt a tanúsítványt az ügyfél-hitelesítési tanúsítványt kérhet a Microsoft tanúsítványszolgáltatástól. Az ügyfél-hitelesítési tanúsítvány települ az Eszközintelligencia szinkronizációs pontjának helyrendszer-kiszolgálójára, és a kiszolgáló ezzel lesz hitelesítve a Microsoft számára. A Configuration Manager az ügyfél-hitelesítési tanúsítvánnyal tölti le az Eszközintelligencia-katalógust és tölti fel a szoftvereket.  

 Ennek a tanúsítványnak a kulcsa 1024 bites.  

### <a name="cloud-based-distribution-points-and-certificates"></a>Felhőalapú terjesztési pontok és tanúsítványok  
 A System Center 2012 Configuration Manager SP1 kezdve felhő alapú terjesztési pontok szükséges egy felügyeleti tanúsítvány (önaláírt vagy PKI) a Microsoft Azure feltöltött. Ehhez a felügyeleti tanúsítványhoz kiszolgálóhitelesítési funkció és 2048 bites tanúsítványkulcs szükséges. Ezenkívül minden felhőalapú terjesztési ponthoz konfigurálni kell egy szolgáltatástanúsítványt, amely nem lehet önaláírt, de kiszolgálóhitelesítési funkcióval és legalább 2048 bites tanúsítványkulccsal kell rendelkeznie.  

> [!NOTE]  
>  Az önaláírt felügyeleti tanúsítvány csak tesztelési célokat szolgál, nem használható éles hálózati környezetben.  

 Az ügyfeleknek nem szükséges PKI-tanúsítvánnyal rendelkezniük a felhőalapú terjesztési pontokhoz; hitelesíthetik magukat a felügyelet felé akár önaláírt tanúsítvánnyal, akár PKI-ügyféltanúsítvánnyal. A felügyeleti pont majd kibocsátja a Configuration Manager hozzáférési tokent az ügyfélnek, és ezt mutatja be az ügyfél a felhőalapú terjesztési pontot. A jogkivonat érvényessége 8 óra.  

### <a name="the-microsoft-intune-connector-and-certificates"></a>A Microsoft Intune Connectort és tanúsítványok  
 A Microsoft Intune mobileszközöket léptet be, amikor egy Microsoft Intune-összekötő létrehozásával kezelheti ezeket a mobileszközöket a Configuration Manager alkalmazásban. Az összekötő PKI-tanúsítványt használ az ügyfél-hitelesítésre alkalmas hitelesítésére a Configuration Manager a Microsoft Intune és az összes információt továbbít köztük az SSL protokoll használatával. A tanúsítvány 2048 bites kulcshosszt és SHA-1 kivonatoló algoritmust használ.  

 Az összekötő telepítésekor létrejön egy aláírási tanúsítvány, amelyet a helykiszolgáló tárol a kulcsok közvetlen telepítéséhez, valamint egy titkosítási tanúsítvány, amelyet a tanúsítványregisztrációs pont tárol az Egyszerű tanúsítványigénylési protokoll (SCEP) kérdésének titkosításához. Ezen tanúsítványok is 2048 bites kulcshosszt és SHA-1 kivonatoló algoritmust használnak.  

 Intune mobileszközöket léptet be, amikor telepíti a mobileszköz azokon PKI-tanúsítványt. Ez a tanúsítvány alkalmas az ügyfél-hitelesítésre, 2048 bites kulcshosszt és SHA-1 kivonatoló algoritmust használ.  

 A PKI-tanúsítványok automatikus kérhetők, jön létre, és a Microsoft Intune által telepített.  

### <a name="crl-checking-for-pki-certificates"></a>CRL-ellenőrzés a PKI-tanúsítványok  
 A PKI visszavont tanúsítványainak listája (CRL) növeli az adminisztrációs és feldolgozási terheket, de a biztonságot is. Ha azonban a CRL ellenőrzése engedélyezett, ám a CRL nem érhető el, akkor a PKI-kapcsolat sikertelen lesz. További információkért lásd: [biztonsága és adatvédelme a System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

 Visszavont tanúsítványok listáját (CRL) ellenőrzése az IIS-ben, alapértelmezés szerint engedélyezve van, egy tanúsítvány-visszavonási listát használ a nyilvános kulcsokra épülő infrastruktúra központi telepítésére, ha nincs szükség további konfigurációra a legtöbb Configuration Manager helyrendszerei, IIS-t futtató. Kivételt képeznek a szoftverfrissítések; ezekhez szükség van egy manuális lépésre annak engedélyezéséhez, hogy a CRL-ellenőrzés vizsgálhassa a szoftverfrissítési fájlok aláírását.  

 A CRL-ellenőrzés alapértelmezésben engedélyezve van az ügyfélszámítógépekhez, ha HTTPS-ügyfélkapcsolatokat használnak. A CRL-ellenőrzés alapértelmezésben nincs engedélyezve, amikor a sávon kívüli felügyeleti konzolt futtatja egy AMT-alapú számítógéphez történő kapcsolódáshoz, de engedélyezhető ez a beállítás. CRL-ellenőrzés a Configuration Manager SP1 vagy újabb Mac számítógépeken lévő ügyfelek nem tiltható le.  

 A CRL-ellenőrzés nem támogatott a következő kapcsolatokhoz a Configuration Manager alkalmazásban:  

-   Kiszolgálók közötti kapcsolatok.  

-   A Configuration Manager által beléptetett mobileszközök.  

-   A Microsoft Intune által beléptetett mobileszközök.  

##  <a name="cryptographic-controls-for-server-communication"></a>Titkosítási funkciók kiszolgálói kommunikációhoz  
 Configuration Manager az alábbi titkosítási funkciókat használja a kiszolgálói kommunikációhoz.  

### <a name="server-communication-within-a-site"></a>Egy helyen belüli kiszolgálói kommunikáció  
 Minden helyrendszer tanúsítványt használ az adatok átvitele a Configuration Manager ugyanazon a helyen belüli más helyrendszerekbe. Egyes helyrendszeri szerepkörök szintén tanúsítványokat használnak a hitelesítéshez. Ha például az egyik kiszolgálóra telepíti a beléptetési proxypontot, egy másik kiszolgálóra pedig a beléptetési pontot, akkor ezzel az identitástanúsítvánnyal tudják egymást hitelesíteni. Ha a Configuration Manager tanúsítványt használ ehhez a kommunikációhoz, ha van elérhető, amely rendelkezik a kiszolgáló hitelesítésére alkalmas PKI-tanúsítvány, a Configuration Manager automatikusan használja azt; Ha nem, a Configuration Manager létrehoz egy önaláírt tanúsítványt. Ez az önaláírt tanúsítvány kiszolgáló-hitelesítési képességgel rendelkezik, és SHA-256 algoritmust és 2048 bites kulcshosszt használ. A Configuration Manager másolja a tanúsítványt más helyrendszer-kiszolgálókon, amelyekre szüksége lehet a helyrendszer megbízhatóként való megbízható személyek tárolójához. Ezután a helyrendszerek megbízhatnak egymásban ezen tanúsítványok és a társmegbízhatóság használatával.  

 Ezt a tanúsítványt az egyes helyrendszer-kiszolgálók, valamint a Configuration Manager riasztást egy önaláírt tanúsítványt, a legtöbb helyrendszeri szerepkörhöz. Ha egy helyen a helyrendszeri szerepkör több példánya is megtalálható, akkor ugyanazt a tanúsítványt használják. Például egy helyen belül rendelkezhet több felügyeleti ponttal vagy beléptetési ponttal. Ez az önaláírt tanúsítvány szintén SHA-256 algoritmust és 2048 bites kulcshosszt használ. Bekerül a Megbízható személyek tárba azokon a helyrendszer-kiszolgálókon is, amelyeknek szüksége lehet a tanúsítvány megbízhatóként való azonosítására. Az alábbi helyrendszeri szerepkörök hozzák létre ezt a tanúsítványt:  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Tanúsítványregisztrációs pont  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont  

-   Csoportos küldésre képes terjesztési pont  

-   Sávon kívüli szolgáltatási pont  

-   Jelentéskészítési szolgáltatási pont  

-   Szoftverfrissítési pont  

-   Állapotáttelepítési pont  

-   Rendszerállapot-érvényesítő pont  

-   Microsoft Intune-összekötő  

 Ezek a tanúsítványok automatikusan Configuration Manager által felügyelt, és ahol szükséges, automatikusan létrehozza.  

 A Configuration Manager ügyfél-hitelesítési tanúsítványt is használ az állapotüzenetek küldésére a terjesztési pontról a felügyeleti pont. Ha a felügyeleti pont csak HTTPS-ügyfélkapcsolatokhoz van konfigurálva, akkor PKI-tanúsítványt kell használni. Ha a felügyeleti pont fogadja a HTTP-kapcsolatokat, használhat PKI-tanúsítványt, vagy választhatja ügyfél-hitelesítésre alkalmas, SHA-256 algoritmust alkalmazó, 2048 bit hosszúságú önaláírt tanúsítvány használatát.  

### <a name="server-communication-between-sites"></a>Helyek közötti kiszolgálói kommunikáció  
 A Configuration Manager adatbázis-replikációt és fájlalapú replikációt a helyek közötti adatátvitelt. További információkért lásd: [a System Center Configuration Managerben végpontok közötti kommunikáció](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

 A Configuration Manager automatikusan konfigurálja a helyek közötti adatbázis-replikálást, és kiszolgálóhitelesítési funkcióval rendelkezik, ha elérhetők; PKI-tanúsítványokat használ Ha nem, a Configuration Manager server-hitelesítés önaláírt tanúsítványokat hoz létre. A helyek közötti hitelesítés mindkét esetben a társmegbízhatóságot használó Megbízható személyek tárban lévő tanúsítványokkal történik. Ennek a tanúsítványtárnak annak biztosítására szolgál, hogy csak a Configuration Manager-hierarchia által használt SQL Server számítógépek részt a helyek közötti replikálás. Míg az elsődleges helyek és a központi felügyeleti hely tudják replikálni a konfigurációs változásokat a hierarchia minden helyére, a másodlagos helyek csak saját szülőhelyükre tudják replikálni azokat.  

 A helykiszolgálók a helyek közötti kommunikációt automatikusan végbemenő biztonságos kulcscserével hozzák létre. A küldő helykiszolgáló létrehoz egy kivonatot, és aláírja azt saját titkos kulcsával. A fogadó helykiszolgáló ellenőrzi az aláírást a nyilvános kulccsal, és összehasonlítja a kivonatot egy helyileg generált értékkel. Ha megegyeznek, a fogadó hely elfogadja a replikált adatokat. Ha az értékek nem egyeznek, a Configuration Manager elutasítja a replikált adatokat.  

 A Configuration Manager adatbázis-replikáció az SQL Server Service Broker használatával a következő mechanizmusok alapján helyek közötti adattovábbításra:  

-   SQL Server közötti kapcsolat: Ez Windows hitelesítő adatok használatával kiszolgáló hitelesítése és pedig 1024 bites önaláírt tanúsítványokat az adatok aláírására és titkosítására az Advanced Encryption Standard (AES) használatával. Ha elérhetők kiszolgálóhitelesítésre alkalmas PKI-tanúsítványok, akkor a rendszer ezeket használja. A tanúsítványnak a számítógép tanúsítványtárolójának személyes tanúsítványokat tartalmazó tárolójában kell lennie.  

-   SQL Service Broker: Ez önaláírt tanúsítványokat 2048 bites használ a hitelesítéshez, és az adatok aláírására és titkosítására az Advanced Encryption Standard (AES) használatával. A tanúsítványnak az SQL Server főadatbázisában kell lennie.  

 A fájlalapú replikáció SMB protokollt használ, és SHA-256 algoritmussal írja alá az adatokat, amelyek nem titkosítottak, de nem tartalmaznak bizalmas információt. Ha szeretné titkosítani az adatokat, IPsec alkalmazhat, és meg kell valósítania a egymástól függetlenül a Configuration Manager alkalmazásból.  

##  <a name="cryptographic-controls-for-clients-that-use-https-communication-to-site-systems"></a>Titkosítási funkciók a helyrendszerekkel HTTPS-kommunikációt használó ügyfelek számára  
 Ha a helyrendszeri szerepkörök fogadják az ügyfélkapcsolatokat, konfigurálhatja őket a HTTPS- és a HTTP-kapcsolatok vagy csak a HTTPS-kapcsolatok fogadására. Azok a helyrendszeri szerepkörök, amelyek fogadnak kapcsolatokat az internetről, csak a HTTPS-t használó ügyfélkapcsolatokat fogadják el.  

 A HTTPS-t használó ügyfélkapcsolatok magasabb szintű biztonságot kínálnak a nyilvános kulcsokra épülő infrastruktúrával (PKI) való integráción keresztül az ügyfél és a kiszolgáló közötti kommunikáció védelme érdekében. Ha azonban a HTTPS-ügyfélkapcsolatokat a PKI tervezésének, központi telepítésének és működtetésének alapos ismerete nélkül konfigurálja, továbbra is sebezhető maradhat a rendszer. Ha például nem biztosítja a legfelső szintű hitelesítésszolgáltató védelmét, a támadók a teljes PKI infrastruktúra megbízhatóságát veszélyeztethetik. Ha a PKI-tanúsítványokat nem kontrollált és biztonságos eljárásokkal telepíti és felügyeli, az felügyelet nélkül maradt ügyfeleket eredményezhet, amelyek nem kapják meg a kritikus szoftverfrissítéseket és csomagokat.  

> [!IMPORTANT]  
>  Az ügyfél-kommunikációban használt PKI-tanúsítványok csak az ügyfél és bizonyos helyrendszerek között védik a kommunikációt. Nem védik meg a kommunikációs csatornát a helykiszolgáló és a helyrendszerek között, valamint a helykiszolgálók között.  

### <a name="communication-that-is-unencrypted-when-clients-use-https-communication"></a>Ha az ügyfelek a HTTPS-kommunikációra nem titkosított kommunikációt  
 Ha az ügyfelek HTTPS használatával kommunikálnak a helyrendszerekkel, a kommunikáció titkosítása általában SSL használatával történik. Azonban az alábbi helyzetekben az ügyfelek titkosítás nélkül kommunikálnak a helyrendszerekkel:  

-   Az ügyfél nem tud HTTPS-kapcsolatot létrehozni az intraneten, és HTTP-t használ helyette, ha a helyrendszerek ezt lehetővé teszik  

-   Kommunikáció a következő helyrendszeri szerepkörökkel:  

    -   Az ügyfelek állapotüzeneteket küldenek a tartalék állapotkezelő pontra  

    -   Az ügyfél PXE-kérelmeket küld egy PXE-t támogató terjesztési pontra  

    -   Az ügyfél értesítési adatokat küld egy felügyeleti pontra  

 A jelentéskészítési szolgáltatási pontok HTTP vagy HTTPS használatára vannak konfigurálva az ügyfél-kommunikáció módjától függetlenül.  

##  <a name="cryptographic-controls-for-clients-chat-use-http-communication-to-site-systems"></a>Titkosítási funkciók ügyfelek Csevegés beléptetésihely-rendszerek HTTP-kommunikációt használnak  
 Ha az ügyfelek HTTP-kommunikációt a helyrendszer-szerepköröket, a az ügyfél-hitelesítéshez, vagy önaláírt tanúsítványokat, amelyek a Configuration Manager riasztást használhatnak PKI-tanúsítványokat. A Configuration Manager önaláírt tanúsítványokat hoz létre, amikor azok rendelkeznek egy egyéni objektumazonosítóval az aláíráshoz és titkosításhoz, és ezek a tanúsítványok egyedileg azonosítják az ügyfelet szolgálnak. A támogatott operációs rendszerekben (a Windows Server 2003 rendszer kivételével) ezek az önaláírt tanúsítványok SHA-256 algoritmust és 2048 bites kulcsot használnak. A Windows Server 2003 rendszerben SHA1 algoritmust és 1024 bites kulcsot használnak.  

### <a name="operating-system-deployment-and-self-signed-certificates"></a>Operációs rendszer központi telepítése és önaláírt tanúsítványokat  
 A Configuration Manager használatával központilag telepít operációs rendszereket önaláírt tanúsítványokat, amikor egy ügyfélszámítógép is rendelkeznie kell egy tanúsítványt a felügyeleti ponttal való kommunikáció akkor is, ha a számítógép átmeneti fázisban vannak, például egy feladatütemezési adathordozóról vagy egy PXE-képes terjesztési pontról végeznek rendszerindítást. Ez a forgatókönyv támogatása HTTP-ügyfélkapcsolatokat, a Configuration Manager generál magának önaláírt tanúsítványokat, amelyek rendelkeznek egy egyéni objektumazonosítóval az aláíráshoz és titkosításhoz, és ezek a tanúsítványok egyedileg azonosítják az ügyfelet szolgálnak. A támogatott operációs rendszerekben (a Windows Server 2003 rendszer kivételével) ezek az önaláírt tanúsítványok SHA-256 algoritmust és 2048 bites kulcsot használnak. A Windows Server 2003 rendszerben SHA1 algoritmust és 1024 bites kulcsot használnak. Ha az önaláírt tanúsítványok integritása sérül, tiltsa le a tanúsítványokat a **Tanúsítványok** csomópontban, az **Adminisztráció** munkaterület **Biztonság** csomópontjában annak érdekében, hogy az esetleges támadók ne tudják megszemélyesíteni a megbízható ügyfeleket.  

### <a name="client-and-server-authentication"></a>Ügyfél és kiszolgáló-hitelesítés  
 Ha az ügyfelek HTTP-kapcsolaton keresztül csatlakoznak, akkor a felügyeleti pontok hitelesítéséhez vagy Active Directory tartományi szolgáltatások használatával, vagy a Configuration Manager megbízható legfelső szintű kulcs használatával. Az ügyfelek nem hitelesítenek más helyrendszerszerepköröket, például az állapotáttelepítési pontokat vagy a szoftverfrissítési pontokat.  

 Amikor egy felügyeleti pont kezdetben hitelesít egy ügyfelet az önaláírt ügyféltanúsítvány segítségével, akkor ez a módszer minimális mértékű biztonságot nyújt, mivel minden számítógép létre tud hozni önaláírt tanúsítványt. Ennek a forgatókönyvnek a használata esetén az ügyfélidentitás bizonyítási eljárását jóváhagyással kell megerősíteni. Csak megbízható számítógépeket kell jóváhagyni, automatikusan a Configuration Manager által, vagy manuálisan, egy rendszergazda felhasználónak. További információkért lásd: című témakör jóváhagyással [a System Center Configuration Managerben végpontok közötti kommunikáció](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

##  <a name="about-ssl-vulnerabilities"></a>Az SSL biztonsági réseivel kapcsolatos  
 A Configuration Manager-kiszolgálók biztonságának javítása érdekében javasoljuk, hogy tiltsa le az SSL 3.0-t, és engedélyezze a TLS 1.1-et és 1.2-t, valamint rendelje újra a TLS-hez kapcsolódó titkosítási csomagokat. A műveletek végrehajtásának leírását [ebben a tudásbáziscikkben találja](https://support.microsoft.com/en-us/kb/245030/). Ez a művelet nem befolyásolja a Configuration Manager működését.  

