---
title: "Ügyfél biztonsági és adatvédelmi |} Microsoft Docs"
description: "További tudnivalók a biztonság és adatvédelem a System Center Configuration Manager-ügyfelek."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c1d71899-308f-49d5-adfa-3a3ec0163ed8
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 1d871b0e1a2897c236d17211a23c9c7d93e42313
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-clients-in-system-center-configuration-manager"></a>Az ügyfelek biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a cikk tartalmazza, biztonsági és adatvédelmi tudnivalók a System Center Configuration Manager-ügyfelek és az Exchange Server-összekötő által felügyelt mobileszközök esetén:  

##  <a name="BKMK_Security_Cliients"></a>Ajánlott biztonsági eljárások ügyfelekhez  
 Amikor a Configuration Manager fogad adatokat a Configuration Manager-ügyfelet futtató eszközökről, ez azzal a kockázattal jár, hogy az ügyfelek megtámadhatják a helyet. például nem megfelelően formázott leltárat küldhetnek, vagy megkísérelhetik túlterhelni a helyrendszereket. A Configuration Manager-ügyfelet csak megbízható eszközökre telepítse. Emellett az alábbi ajánlott biztonsági eljárásokkal erősítheti a hely védelmét a rosszindulatú vagy veszélyeztetett biztonságú eszközökkel szemben:  

 **Használjon nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítványokat az IIS-t futtató helyrendszerek ügyfél-kommunikáció.**  

-   A hely tulajdonságainál a **Helyrendszer beállításai** elemet állítsa **Csak HTTPS** értékre.  

-   A **/UsePKICert** CCMSetup-tulajdonsággal telepítse az ügyfeleket  

-   Használja a visszavont tanúsítványok listáját (CRL), és ügyeljen arra, hogy a lista mindig elérhető legyen az ügyfelek és a kommunikáló kiszolgálók számára.  

 Ezek a tanúsítványok a mobileszközügyfelekhez és az interneten keresztül csatlakozó ügyfélszámítógépekhez szükségesek, és használatuk a terjesztési pontok kivételével az intraneten folytatott minden ügyfél-kommunikációhoz ajánlott.  

 További információ a PKI-tanúsítványának követelményeiről és azok használata a Configuration Manager védelme érdekében: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 **Automatikusan hagyja jóvá a megbízható tartományból csatlakozó ügyfélszámítógépeket és manuálisan ellenőrizze és hagyja jóvá a többi számítógépet**  

 A hierarchiában beállíthat manuális jóváhagyást, a megbízható tartományba tartozó számítógépek automatikus jóváhagyását, illetve az összes számítógép automatikus jóváhagyását. A legbiztonságosabb jóváhagyási módszer a megbízható tartományba tartozó ügyfelek automatikus jóváhagyása, majd az összes többi számítógép manuális ellenőrzése és jóváhagyása. Az összes ügyfél automatikus jóváhagyása csak abban az esetben ajánlott, ha más hozzáférés-szabályozási funkciókat használ annak megakadályozására, hogy a nem megbízható számítógépek hozzáférjenek a hálózathoz.  

 Jóváhagyással azonosíthatja azokat a felügyelendő a Configuration Manager PKI-alapú hitelesítés használatakor nem megbízható számítógép.  

 További információ a számítógépek manuális jóváhagyásáról: [Ügyfelek kezelése az Eszközök csomópontból](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode).  

 **Ne használja a akadályozza az ügyfelek hozzáférését a Configuration Manager-hierarchia**  

 Blokkolt ügyfeleket a Configuration Manager-infrastruktúra visszautasítja, hogy azok nem kommunikálhatnak helyrendszerek tölthetnek le házirendeket, tölthet fel leltári adatokat vagy küldhetnek állapotinformációkat vagy -üzeneteket. Azonban ne használja a Configuration Manager-hierarchia védje a nem megbízható számítógépekkel, amikor a helyrendszerek fogadják a HTTP-ügyfélkapcsolatokat. Ebben az esetben ugyanis a blokkolt ügyfelek egy új önaláírt tanúsítvánnyal és új hardverazonosítóval újracsatlakozhatnak a helyhez. A blokkolás az elveszett vagy sérült biztonságú rendszerindító adathordozók letiltására szolgál olyan esetekben, amikor központilag telepít operációs rendszert ügyfelekre, és az összes helyrendszer fogadja a HTTPS-ügyfélkapcsolatokat. Amennyiben olyan nyilvános kulcsú infrastruktúrát (PKI) használ, amely támogatja a visszavont tanúsítványok listáját (CRL), érdemes a tanúsítványok visszavonását használnia elsődleges védelmi vonalként a potenciálisan veszélyeztetett tanúsítványokkal szemben. A Configuration Manager ügyfelek blokkolása másodlagos védelmi vonalként szolgálhat-hierarchia védelmére.  

 További információ: [Annak meghatározása, hogy szükséges-e az ügyfelek blokkolása a System Center Configuration Managerben](../../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

 **Ez a legbiztonságosabb ügyfél-telepítési módszer, amelyek a környezetnek gyakorlati használata:**  

-   Tartományi számítógépek esetén a csoportházirendre, illetve a szoftverfrissítésre alapuló ügyfél-telepítési módszerek biztonságosabb megoldást nyújtanak az ügyfélleküldéses telepítésnél.  

-   A lemezképkészítés és a manuális telepítés a megfelelő hozzáférés-szabályozási és változáskezelési intézkedések használata esetén rendkívül biztonságos megoldást nyújthat.  

 Az ügyfélleküldéses telepítés a számos függőségi viszony – például a helyi rendszergazdai engedélyek, az Admin$-megosztás és a számos tűzfalkivétel – miatt az összes ügyfél-telepítési módszer közül a legkevésbé biztonságos. Ezek a függőségi viszonyok növelik a támadási felületet.  

 További információ a különböző ügyféltelepítési módszerekről: [Ügyféltelepítési módszerek a Configuration Managerben](../../../../core/clients/deploy/plan/client-installation-methods.md).  

 Emellett ahol csak lehetséges, egy ügyfél telepítési módszert válasszon, amelyhez a legalacsonyabb biztonsági engedélyek szükségesek a Configuration Managerben, és korlátozza az olyan, amely tartalmazza az engedélyeket, hiszen olyan célokra is ügyféltelepítés használható biztonsági szerepkörökhöz rendelt rendszergazdai felhasználók számát. Az automatikus ügyfélfrissítéshez például **Teljes körű rendszergazda** biztonsági szerepkör szükséges, amely minden biztonsági engedélyt megad a rendszergazdának.  

 A függőségek és az egyes ügyféltelepítési módszerek szükséges biztonsági engedélyekkel kapcsolatos további információkért lásd "A telepítési módszer függőségei" a [a számítógépes ügyfelek előfeltételei](../../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md#BKMK_prereqs_computers).  

 **Ha ügyfélleküldéses telepítést kell használnia, további lépésekkel biztonságos az Ügyfélleküldéses telepítési fiók**  

 Bár ennek a fióknak a helyi tagjának kell lennie **rendszergazdák** csoportba az minden olyan számítógépen, a Configuration Manager ügyfélszoftvert, semmiképpen ne vegye fel az Ügyfélleküldéses telepítési fiókot a **Tartománygazdák** csoport. Ehelyett hozzon létre egy globális csoportot, és vegye fel azt a helyi **Rendszergazdák** csoportba az ügyfélszámítógépeken. Ezen felül olyan csoportházirend-objektumot is létrehozhat, amellyel egy „Korlátozott csoport”-beállítással hozzáadhatja az ügyfélleküldéses telepítési fiókot a helyi **Rendszergazdák** csoporthoz.  

 A biztonság további erősítése érdekében több ügyfélleküldéses telepítési fiókot is létrehozhat, amelyek mind korlátozott számú számítógéphez rendelkezhetnek rendszergazdai hozzáféréssel, így ha az egyik fiók biztonsága sérül, csak az adott fiók által elérhető ügyfélszámítógépek kerülnek veszélybe.  

 **Távolítsa el az ügyfélszámítógépekről lemezképet készítene előtt**  

 Ha lemezkép-készítési technológiával szeretne központi ügyféltelepítést végezni, a lemezkép rögzítése előtt mindig távolítsa el az ügyféloldali hitelesítő adatokat tartalmazó (például PKI-) és az önaláírt tanúsítványokat. Ha nem távolítja el ezeket, az ügyfelek megszemélyesíthetik egymást, így az egyes ügyfelekhez tartozó adatok ellenőrzése lehetetlenné válik.  

 A Windows központi telepítési dokumentációjában részletesebb tájékoztatást olvashat a Sysprep eszköz használatáról a számítógépek előkészítésére lemezképkészítés előtt.  

 **Győződjön meg arról, hogy a a Configuration Manager ügyfélszámítógépei hiteles példányt kapjanak a tanúsítványok beolvasása:**  

-   A Configuration Manager megbízható legfelső szintű kulcs  

     Ha nem lett kibővítve az Active Directory-sémát a Configuration Manager számára, és az ügyfelek nem használnak PKI-tanúsítványok felügyeleti pontokkal való kommunikáció során, az ügyfelek támaszkodnak a Configuration Manager megbízható legfelső szintű kulcsát használják az érvényes felügyeleti pontok hitelesítéséhez. Ebben a helyzetben az ügyfelek egyedül a megbízható legfelső szintű kulcs használatával ellenőrizhetik, hogy a felügyeleti pont megbízható-e a hierarchia számára. A megbízható legfelső szintű kulcs nélkül a gyakorlott támadók rosszindulatú felügyeleti ponthoz irányíthatják az ügyfeleket.  

     Ha az ügyfelek nem tudják letölteni a Configuration Manager megbízható legfelső szintű kulcsot, a globális katalógusból vagy PKI-tanúsítványok használatával, előre adja meg az ügyfeleknek a megbízható legfelső szintű kulcsot, győződjön meg arról, hogy nem irányíthatják őket rosszindulatú felügyeleti ponthoz. További információ: [A megbízható legfelső szintű kulcs tervezése](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

-   A helykiszolgáló aláíró tanúsítványából  

     Az ügyfelek a helykiszolgáló aláíró tanúsítványával ellenőrizhetik, hogy a helykiszolgáló aláírta-e a felügyeleti pontról letöltött ügyfélházirendet. A tanúsítványt a helykiszolgáló maga írja alá és teszi közzé az Active Directory tartományi szolgáltatásokban.  

     Ha az ügyfelek nem tudják letölteni a helykiszolgáló aláíró tanúsítványát a globális katalógusból, alapértelmezés szerint a felügyeleti pontról fogják azt letölteni. Ha a felügyeleti pont nem megbízható hálózathoz kapcsolódik (például az internethez), manuálisan telepítse a helykiszolgáló aláíró tanúsítványát az ügyfeleken, így gondoskodhat arról, hogy az ügyfelek nem futtathatnak illetéktelenül módosított ügyfélházirendeket veszélyeztetett biztonságú felügyeleti pontokról.  

     A helykiszolgáló aláíró tanúsítványának manuális telepítéséhez használja a CCMSetup eszköz **SMSSIGNCERT** client.msi-tulajdonságát. További információ: [Tudnivalók a System Center Configuration Manager ügyféltelepítési tulajdonságairól](../../../../core/clients/deploy/about-client-installation-properties.md).  

 **Ne használjon automatikus helyhozzárendelést, ha az ügyfél fogja letölteni a megbízható legfelső szintű kulcsot az első felügyeleti pontról, amelyhez csatlakozik**  

 Ez az ajánlott biztonsági eljárás az előző bejegyzéshez kapcsolható. Annak elkerülése érdekében, hogy egy új ügyfél rosszindulatú felügyeleti pontról töltse le a megbízható legfelső szintű kulcsot, kizárólag a következő helyzetekben használjon automatikus helyhozzárendelést:  

-   Az ügyfél hozzáférhet az Active Directory tartományi szolgáltatásokban közzétett helyinformációkat Configuration Manager.  

-   Ha előre ellátja az ügyfelet a megbízható legfelső szintű kulccsal.  

-   Ha PKI-tanúsítványokat használ egy vállalati hitelesítésszolgáltatótól ahhoz, hogy megbízhatósági kapcsolatot létesítsen az ügyfél és a felügyeleti pont között.  

 További információ a megbízható legfelső szintű kulcsról: [A megbízható legfelső szintű kulcs tervezése](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 **Ügyfélszámítógépek telepítse a CCMSetup Client.msi beállítással SMSDIRECTORYLOOKUP = NoWINS**  

 Az Active Directory Domain Services biztosítja az ügyfeleknek a legbiztonságosabb szolgáltatás-helymeghatározási módszert a helyek és felügyeleti pontok megtalálására. Ha ez nem lehetséges, például az Active Directory-sémája nem bővíthető a Configuration Manager, vagy mert az ügyfelek nem megbízható erdőben vagy munkacsoportban, akár is használhatja a DNS-közzététel egy alternatív szolgáltatás-helymeghatározó módszert. Ha a fentiek közül egyik módszer sem működik, az ügyfelek visszatérhetnek a WINS használatára, ha a felügyeleti pont nincs beállítva a HTTPS-ügyfélkapcsolatok kezelésére.  

 Mivel a WINS-közzététel a többi közzétételi módszernél kevésbé biztonságos, az „SMSDIRECTORYLOOKUP=NoWINS” beállítással gondoskodjon arról, hogy az ügyfélszámítógépek ne térjenek vissza a WINS használatára. Ha a WINS szolgáltatás helyének kell használnia, az SMSDIRECTORYLOOKUP = winssecure konfigurációs BEÁLLÍTÁSSAL (az alapértelmezett beállítás), amely a Configuration Manager megbízható legfelső szintű kulcs segítségével ellenőrzi a felügyeleti pont önaláírt tanúsítványát.  

> [!NOTE]  
>  Ha az ügyfél az SMSDIRECTORYLOOKUP = winssecure konfigurációs BEÁLLÍTÁSSAL, és talál egy felügyeleti pontot a WINS SZOLGÁLTATÁSBÓL, az ügyfél ellenőrzi a Configuration Manager megbízható legfelső szintű kulcsát a WMI-ben példányát. Az a felügyeleti pont tanúsítványának aláírása megfelel a megbízható legfelső szintű kulcs példányának az ügyfélen, ha a rendszer érvényesíti a tanúsítványt, és az ügyfél a WINS segítségével talált felügyeleti ponttal kommunikál. A felügyeleti pont tanúsítványának aláírása nem egyezik meg a megbízható legfelső szintű kulcs példányának az ügyfélen, ha a tanúsítvány érvénytelen, és az ügyfél nem fog kommunikálni a WINS segítségével talált felügyeleti ponttal.  

 **Győződjön meg arról, hogy a karbantartási időszakok kellőképpen hosszúak legyenek a kritikus szoftverfrissítések telepítésére**  

 Eszközgyűjtemények, amelyekkel korlátozható az, hogy a Configuration Manager mikor telepíthet szoftvereket az ezeknek az eszközöknek karbantartási időszakokat állíthat be. Túl rövid karbantartási időszak konfigurálása esetén előfordulhat, hogy az ügyfél nem tudja telepíteni a kritikus szoftverfrissítéseket, így védtelen marad azokkal a támadásokkal szemben, amelyek elhárítására az érintett frissítések hivatottak.  

 **A Windows embedded-eszközökön, amelyeken írási szűrők, további biztonsági intézkedésekre van csökkenteni a támadási felületet, ha a Configuration Manager letiltja az írási szűrőket a szoftvertelepítések és-módosítások végrehajtásához**  

 Ha az írási szűrők engedélyezve vannak a Windows Embedded-eszközön, a szoftvertelepítések és -módosítások kizárólag az átmeneti területet fogják érinteni, és a készülék újraindításával elvesznek. Ha a Configuration Manager segítségével átmenetileg letiltja az írási szűrőket a szoftvertelepítések és -módosítások, ebben az időszakban, az embedded-eszköz téve az összes kötet, beleértve a megosztott mappákat is.  

 Bár a Configuration Manager a a számítógép erre az időre zárolja, így csak a helyi rendszergazdák bejelentkezhet, amikor csak lehetséges, további biztonsági intézkedésekkel erősítse a számítógép védelmét. például engedélyezzen további korlátozásokat a tűzfalon, vagy válassza le az eszközt a hálózatról.  

 Ha karbantartási időszakokat használ a tartós módosítások végrehajtására, körültekintően tervezze meg az ütemezést úgy, hogy az írási szűrők minél rövidebb ideig legyenek letiltva, de elegendő ideig ahhoz, hogy a szoftvertelepítések és -újraindítások befejeződhessenek.  

 **Ha szoftverfrissítés-alapú ügyféltelepítést használ, és az ügyfél egy későbbi verzióját telepíti a helyen, frissítse az, hogy az ügyfélre a legújabb verzió jusson a szoftverfrissítési ponton közzétett szoftverfrissítést**  

 Ha az ügyfél egy későbbi verziót telepíti a helyre – például a hely frissítése esetén –, a rendszer nem frissíti automatikusan a szoftverfrissítési ponton közzétett szoftverfrissítést, amely az ügyfél központi telepítésére szolgál. Újra tegye közzé a szoftverfrissítési pontot, majd kattintson a Configuration Manager-ügyfél **Igen** gombra a verziószám frissítéséhez.  

 További információkért lásd: a Configuration Manager-ügyfél közzététele a szoftverfrissítési ponton"" eljárás a [Configuration Manager-ügyfelek telepítése által alapú telepítés](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

 **A számítógép ügynök ügyféleszköz-beállítást felfüggeszteni a BitLocker PIN-kód bevitelének újraindítás közben csak a megbízható számítógépek esetében mindig értékre konfigurálja, és, korlátozott fizikai hozzáféréssel rendelkező**  

 Ezt az ügyfélbeállítást beállításakor **mindig**, a Configuration Manager tudja fejezni a szoftvertelepítést, így biztosítható, hogy a kritikus szoftverfrissítések telepítve vannak-e, és a szolgáltatások folytatódnak. Ha azonban egy támadó elfogja az újraindítási folyamatot, akkor átveheti a számítógép irányítását. Csak akkor használja ezt a beállítást, ha megbízik a számítógépben, és ha a számítógéphez való fizikai hozzáférés korlátozott. Ez a beállítás megfelelő lehet például egy adatközpont kiszolgálói számára.  

 **Ne konfigurálja a Számítógépügynök ügyfél Eszközbeállítás PowerShell végrehajtási házirend áteresztő értékre.**  

 Ez az ügyfélbeállítás engedélyezi a Configuration Manager-ügyfél számára aláíratlan PowerShell-parancsfájlok futtathatók, ami lehetővé teheti kártevő szoftverek futtatását az ügyfélszámítógépeken. Ha mindenképp ezt a beállítást kell megadnia, használjon egyéni ügyfélbeállítást, és csak azokhoz az ügyfélszámítógépekhez rendelje hozzá, amelyeken szükséges az aláíratlan PowerShell-parancsfájlok futtatása.  

##  <a name="bkmk_mobile"></a>Ajánlott biztonsági eljárások mobileszközökhöz  
 **Mobileszközök regisztrálása a Configuration Managerrel, és az interneten támogatja: Telepítse a beléptetési proxypontot egy peremhálózatra, a beléptetési pontot pedig az intranetre**  

 A szerepkörök ilyen elválasztása hozzájárul a beléptetési pont támadások elleni védelméhez. Ha a beléptetési pont biztonsága sérül, a támadó megszerezhet hitelesítési tanúsítványokat és ellophatja azon felhasználók hitelesítési adatait, akik beléptetik mobileszközeiket.  

 **Mobileszközök esetén: Konfigurálja a jelszóbeállításokat a mobileszközök illetéktelen hozzáférés elleni segítségével**  

 A Configuration Manager által beléptetett mobileszközök: A mobileszköz konfigurációelemének segítségével konfigurálja a jelszó erősségét a PIN-kódot, és legalább az alapértelmezett hosszt a minimális jelszóhosszhoz.  

 Mobil eszközök, amelyeken nincs telepítve a Configuration Manager-ügyfél, azonban a Exchange Server-összekötő által kezelt: Konfigurálja a **jelszóbeállítások** az Exchange Server-összekötőhöz, hogy a jelszó erősségét a PIN-kód, és adjon meg legalább az alapértelmezett hosszt a minimális jelszóhosszhoz.  

 **Mobileszközök esetén: Így az alkalmazások futását csak akkor, ha azok cégek írták alá, hogy megbízik, és nem teszik lehetővé aláíratlan fájlok telepítését és az állapotinformációk illetéktelen módosításának megelőzése érdekében**  

 A Configuration Manager által beléptetett további mobileszközök kezeléséhez: A biztonsági beállítások konfigurálása a mobileszköz konfigurációelemének segítségével **aláíratlan alkalmazások** , **tiltott** és konfigurálása **aláíratlan fájlok telepítése** beállítást pedig egy megbízható forrásra.  

 Mobil eszközök, amelyeken nincs telepítve a Configuration Manager-ügyfél, azonban a Exchange Server-összekötő által kezelt: Konfigurálja a **Alkalmazásbeállítások** az Exchange Server-összekötőhöz, hogy **aláíratlan fájlok telepítése** és **aláíratlan alkalmazások** értéke, mert **tiltott**.  

 **Mobileszközök esetén: A mobil eszköz zárolását, amikor a rendszer nem használja jogok kiterjesztéséből adódó támadások megelőzése érdekében**  

 A Configuration Manager által beléptetett további mobileszközök kezeléséhez: A mobileszköz konfigurációelemének használja a jelszó beállításának konfigurálásához **üresjárati idő (percben) mobil eszköz zárolása előtt**.  

 Mobil eszközök, amelyeken nincs telepítve a Configuration Manager-ügyfél, azonban a Exchange Server-összekötő által kezelt: Konfigurálja a **jelszóbeállítások** az Exchange Server-összekötő konfigurálása **üresjárati idő (percben) mobil eszköz zárolása előtt**.  

 **Mobileszközök esetén: Korlátozza, hogy a felhasználók, akik beléptethetik a mobileszközeiket jogok kiterjesztésének megelőzése érdekében.**  

 Az alapértelmezettek helyett használjon egyéni ügyfélbeállításokat, amelyek csak a hitelesített felhasználóknak engedélyezik a mobileszközük beléptetését.  

 **Mobileszközök esetén: Ne telepítsen alkalmazásokat az alábbi esetekben a Configuration Manager vagy a Microsoft Intune által beléptetett mobileszközökkel rendelkező felhasználók számára:**  

-   Ha a mobileszközt többen használják.  

-   Ha az eszközt egy rendszergazda léptette be egy felhasználó nevében.  

-   Ha az eszközt átruházzák egy másik személyre kiléptetés és újbóli beléptetés nélkül.  

 Beléptetés közben létrejön egy felhasználó-eszköz kapcsolat, amely a beléptetést végző felhasználót hozzárendeli a mobileszközhöz. Ha egy másik felhasználó használja a mobileszközt, tudja futtatni az eredeti felhasználó számára központilag telepített alkalmazásokat, ami a jogok kiterjesztésével járhat. Hasonlóképpen, ha egy rendszergazda belépteti a mobileszközt egy felhasználó számára, akkor a felhasználónak központilag telepített alkalmazások nem települnek a mobileszközre, hanem előfordulhat, hogy helyettük a rendszergazda számára központilag telepített alkalmazások kerülnek rá.  

 Ellentétben a Windows rendszerű számítógépek felhasználó-eszköz kapcsolatot, akkor nem lehet manuálisan definiálni a felhasználó-eszköz kapcsolatára vonatkozó Microsoft Intune által beléptetett mobileszközök információkat.  

 Ha az Intune által beléptetett mobileszköz tulajdonjogát, a mobileszköz kivonása az Intune a felhasználó-eszköz kapcsolat eltávolítása, és majd kérje meg az új felhasználót, hogy léptesse be újra az eszközt.  

 **Mobileszközök esetén: Győződjön meg arról, hogy a felhasználók a saját mobileszközök regisztrálása a Microsoft Intune**  

 Mivel a beléptetést végző felhasználót a mobileszközhöz rendelő felhasználó-eszköz kapcsolat beléptetéskor jön létre, ha egy rendszergazda végzi el a mobileszköz beléptetését a felhasználó helyett, akkor a felhasználó számára központilag telepített alkalmazások nem települnek a mobileszközre, hanem előfordulhat, hogy helyettük a rendszergazda számára központilag telepített alkalmazások kerülnek rá.  

 **Az Exchange Server-összekötőhöz: Győződjön meg arról, hogy a Configuration Manager helykiszolgálón és az Exchange-kiszolgáló közötti kapcsolat védett**  

 Használjon IPsec-et, ha az Exchange Server helyszíni; a szolgáltatott Exchange automatikusan SSL-t használ a kapcsolat biztonságossá tételére.  

 **Az Exchange Server-összekötőhöz: Használja a legalacsonyabb jogosultságok elvét az összekötőhöz**  

 Az Exchange Server-összekötő számára szükséges minimális parancsmagok listáját itt találja: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange segítségével](../../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

##  <a name="bkmk_macs"></a>Ajánlott biztonsági eljárások Mac számítógépekhez  
 **Mac számítógépek esetén: Tárolja, és az ügyfél forrásfájljait hozzáférni a biztonságos helyről.**  

 A Configuration Manager nem ellenőrzi, hogy az ügyfél forrásfájljait módosították mielőtt telepíti vagy belépteti az ügyfelet a Mac számítógépen. A fájlokat megbízható forrásból töltse le, és a tárolásukat és a hozzáférésüket biztonságosan végezze.  

 **Mac számítógépek esetén: Függetlenül a Configuration Manager alkalmazásból, figyeléséhez, és nyomon követéséhez beléptető tanúsítvány érvényességi időszaka a felhasználók számára.**  

 Az üzletmenet folytonosságának biztosításához figyelje és kövesse a Mac számítógépekhez használt tanúsítvány érvényességi időtartamát. A Configuration Manager nem támogatja a tanúsítvány automatikus megújítását, és figyelmezteti, hogy a tanúsítvány érvényessége hamarosan lejár. Az érvényesség általában 1 év.  

 Tudnivalók a tanúsítvány megújításáról: [A Mac-ügyfél tanúsítványának manuális megújítása](../../../../core/clients/deploy/deploy-clients-to-macs.md#renewing-the-mac-client-certificate).  

 **Mac számítógépek esetén: Fontolja meg, hogy a megbízható legfelső szintű Hitelesítésszolgáltatói tanúsítványt úgy, hogy a megbízható az SSL protokollra, a jogok kiterjesztése elleni védelemhez.**  

 Ha Mac számítógépeket léptet kezelése a Configuration Manager-ügyfél felhasználói tanúsítvány automatikusan települ, azzal a megbízható legfelső szintű tanúsítvánnyal, amely a felhasználói tanúsítvány láncot alkot, hogy együtt. Ha a legfelső szintű tanúsítvány megbízhatóságát korlátozni szeretné csak az SSL protokollra, azt az alábbi módon teheti meg.  

 Ez az eljárás befejezése után a legfelső szintű tanúsítvány nem lesz megbízható az SSL - például biztonságos levelezés (S/MIME), bővíthető hitelesítési (EAP) vagy kódaláírás eltérő protokollok érvényesítésére.  

> [!NOTE]  
>  Is használhatja ezt az eljárást, ha telepítette az ügyféltanúsítvány egymástól függetlenül a Configuration Manager alkalmazásból.  

 A legfelső szintű tanúsítvány korlátozása az SSL protokollra:  

1.  A Mac számítógépen nyisson meg egy terminálablakot.  

2.  Írja be a következő parancsot: **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**  

3.  A **Keychain Access** (Kulcscsomó-hozzáférés) párbeszédpanelen a **Keychains** (Kulcscsomók) szakaszban kattintson a **System** (Rendszer) elemre, majd a **Category** (Kategória) szakaszban a **Certificates** (Tanúsítványok) lehetőségre.  

4.  Keresse meg a legfelső szintű hitelesítésszolgáltatói tanúsítványt a Mac ügyféltanúsítványhoz, és kattintson rá duplán.  

5.  A legfelső szintű hitelesítésszolgáltatói tanúsítvány párbeszédpanelén bontsa ki a **Trust** (Megbízhatóság) szakaszt, és hajtsa végre a következő módosításokat:  

    1.  A **When using this certificate** (A tanúsítvány használatakor) beállításban módosítsa az **Always Trust** (Mindig megbízható) alapértelmezett értéket **Use System Defaults** (A rendszer alapértelmezéseinek használata) értékre.  

    2.  A **Secure Sockets Layer (SSL)** beállítást módosítsa a **no value specified** (nincs megadva érték) értékről **Always Trust** (Mindig megbízható) értékre.  

6.  Zárja be a párbeszédpanelt, és amikor a rendszer kéri, adja meg a rendszergazdai jelszót, és kattintson **frissítési beállítások**.  

##  <a name="BKMK_SecurityIssues_Clients"></a>A Configuration Manager-ügyfelek biztonsági problémái  
 A következő biztonsági problémákra nincs megoldás:  

-   Az állapotüzenetek nincsenek hitelesítve  

     Az állapotüzeneteken nem történik hitelesítés. Ha egy felügyeleti pont elfogadja a HTTP-ügyfélkapcsolatokat, bármely eszköz küldhet állapotüzeneteket a felügyeleti pontra. Ha a felügyeleti pont csak a HTTPS-ügyfélkapcsolatokat fogadja el, az eszköznek érvényes ügyfél-hitelesítési tanúsítványt kell beszereznie egy megbízható legfelső szintű hitelesítésszolgáltatótól, de ezután bármilyen állapotüzenetet küldhet. Ha egy ügyfél érvénytelen állapotüzenetet küld, azt a rendszer elveti.  

     Létezik néhány lehetséges támadás ezen biztonsági rés ellen. A támadó küldhet hamis állapotüzenetet, hogy tagságot szerezzen egy olyan gyűjteményben, amely állapotüzenet-lekérdezéseken alapul. Bármely ügyfél elindíthat egy szolgáltatásmegtagadási támadást a felügyeleti pont ellen úgy, hogy elárasztja állapotüzenetekkel. Ha az állapotüzenetek műveleteket váltanak ki állapotüzenet-szűrő szabályokban, akkor a támadó elindíthatja az állapotüzenet-szűrő szabályt. A támadó küldhet olyan állapotüzenetet is, amely az információjelentést pontatlanná teszi.  

-   A házirendek átirányíthatók általuk nem érintett ügyfelekre  

     A támadók többféleképpen irányíthatják át az egyik ügyfélnek szánt házirendet egy másik ügyfélre. Egy megbízható ügyfélről induló támadás például hamis leltár- vagy felderítési információt küldhet, hogy a számítógép bekerüljön egy olyan gyűjteménybe, amelyben nem szabadna benne lennie, majd megkapja a gyűjteményhez rendelt összes központi telepítést. Léteznek vezérlők, amelyekkel csökkenthető annak az esélye, hogy a támadók közvetlenül módosítsák a házirendet, azonban a támadók egy meglévő házirenddel is újraformázást végezhetnek és újratelepíthetik az operációs rendszert, majd elküldhetik azt egy másik számítógépre, szolgáltatásmegtagadást idézve elő. Ilyen típusú támadásokat pontos időzítés és a Configuration Manager infrastruktúrájának alapos ismerete szükséges.  

-   Az ügyfél naplóihoz hozzáférnek a felhasználók  

     Az ügyfél összes naplófájljához olvasási hozzáférése van a felhasználóknak és írási hozzáférése az interaktív felhasználóknak. Ha engedélyezi a részletes naplózást, a támadók olvashatják a naplófájlokat, és azokban megkereshetik a megfelelőséggel vagy a rendszer biztonsági réseivel kapcsolatos információkat. A felhasználó környezetében futó folyamatoknak, mint például a szoftvertelepítés, alacsony jogosultságszintű felhasználói fiókkal kell írási hozzáférést kapniuk a naplófájlokhoz. Ez azt jelenti, hogy a támadó is alacsony jogosultságszintű fiókkal tud a naplókba írni.  

     A legnagyobb veszély az, hogy a támadó törölhet olyan adatokat a naplófájlból, amelyekre a rendszergazdának szüksége lehet a rendszer vizsgálatához és a behatolások észleléséhez.  

-   Egy számítógép felhasználható olyan tanúsítvány beszerzésére, amely a mobileszközök beléptetésére szolgál  

     Ha a Configuration Manager feldolgoz egy beléptetési kérést, nem tudja ellenőrizni, hogy a kérés mobileszközről, nem pedig egy olyan számítógépről származik-e. Ha a kérés egy olyan számítógépről, telepíthet egy PKI-tanúsítvánnyal, amely lehetővé teszi a Configuration Manager regisztrálni. Ilyen esetben a jogok kiterjesztését felhasználó támadások megelőzése érdekében csak a megbízható felhasználóknak engedélyezze a mobileszközeik beléptetését, és körültekintően figyelje a beléptetési aktivitást.  

-   A kapcsolat egy ügyfél és a felügyeleti pont között nem szakad meg, ha letilt egy ügyfelet, és a letiltott ügyfél továbbra is küldhet ügyfél-értesítési csomagokat a felügyeleti pontra életben tartási üzenetekként  

     Ha letilt egy ügyfelet, amely már nem bízik, és az létesített ügyfél-értesítési kommunikációt, a Configuration Manager nem választja le a munkamenetet. A letiltott ügyfél továbbra is küldhet csomagokat a felügyeleti pontjára, amíg az ügyfél le nem kapcsolódik a hálózatról. Ezek a csomagok csak kicsi, életben tartási csomagok, és ezeket az ügyfeleket nem tudja felügyelni a Configuration Manager által mindaddig, amíg a tiltásukat fel nem oldják.  

-   Amikor automatikus ügyfélfrissítést használ, és az ügyfél egy felügyeleti pontra van irányítva az ügyfél-forrásfájlok letöltéséhez, a felügyeleti pont mint forrás megbízhatóságát nem ellenőrzi a rendszer  

-   Amikor a felhasználók először léptetnek be Mac számítógépet, fennáll a címlopás veszélye  

     Amikor a Mac számítógép kapcsolódik a beléptetési proxypontra beléptetéskor, nem valószínű, hogy a Mac számítógép már rendelkezik a legfelső szintű hitelesítésszolgáltatói tanúsítvánnyal. Ekkor a Mac számítógép nem bízik meg a kiszolgálóban, és megkérdezi a felhasználót, hogy folytatja-e a műveletet. Ha a beléptetési proxypont teljes nevét feloldja egy engedélyezetlen DNS-kiszolgáló, az a Mac számítógépet egy engedélyezetlen beléptetési proxypontra irányíthatja, és tanúsítványokat telepíthet egy nem megbízható forrásból. A kockázat csökkentése érdekében kövesse a bevált gyakorlatokat, amelyekkel elkerülheti a címlopást a környezetében.  

-   A Mac beléptetése nem korlátozza a tanúsítványkéréseket  

     A felhasználók mindig újból beléptethetik a Mac gépüket, amikor új ügyféltanúsítványt kérnek. A Configuration Manager nem ellenőrzi a többszörös kéréseket, és korlátozza az egyetlen számítógépről kért tanúsítványok számát. Egy rosszindulatú felhasználó futtathat olyan parancsfájlt, amely megismétli a parancssori beléptetési kérést, ezzel szolgáltatásmegtagadást okozva a hálózaton vagy a kibocsátó hitelesítésszolgáltatónál. Hogy ennek a veszélyét csökkentse, körültekintően figyelje a kibocsátó hitelesítésszolgáltató esetleges ilyen típusú gyanús viselkedését. Olyan számítógépre, amelyen a viselkedésmintát azonnal blokkolni kell a Configuration Manager hierarchiából.  

-   A törlési visszaigazolás nem ellenőrzi, hogy az eszköz tartalmának törlése sikeres volt-e  

     Egy törlési művelet kezdeményezésekor a mobileszköz és a Configuration Manager jeleníti meg a tartalomtörlési állapotot kell, az ellenőrzés arra vonatkozik, hogy a Configuration Manager sikeresen elküldte az üzenetet, és nem, akkor az eszköz intézkedni rajta. Az Exchange Server-összekötő által felügyelt mobileszközök esetén a tartalomtörlési visszaigazolás azt ellenőrzi, hogy az Exchange (nem az eszköz) fogadta-e a parancsot.  

-   Ha a változtatások véglegesítésének beállításait használja a Windows Embedded-eszközökön, a fiókok zárolása a vártnál hamarabb történhet meg.  

     Ha a Windows Embedded-eszközön fut, amely a Windows 7 rendszernél korábbi operációs rendszert, és a felhasználó megpróbál bejelentkezni, amíg az írási szűrők le vannak tiltva, a Configuration Manager által végrehajtott változtatások véglegesítéséhez, engedélyezettek, mielőtt a fiók zárolva van, sikertelen bejelentkezési kísérletek száma megfeleződik. Ha például a **Fiókzárolás küszöbértéke** beállítás értéke 6, és a felhasználó 3 alkalommal helytelenül írja be a jelszavát, a rendszer zárolja a fiókot, és szolgáltatásmegtagadási helyzet jön létre.  Ha a felhasználóknak ebben a helyzetben kell bejelentkezniük a beágyazott eszközökre, figyelmeztesse őket arra, hogy valószínűleg kevesebb bejelentkezési próbálkozásra van lehetőségük.  

##  <a name="BKMK_Privacy_Cliients"></a>A Configuration Manager-ügyfelekre vonatkozó adatvédelmi információ  
 A Configuration Manager-ügyfél telepítésekor kell adnia az ügyfélbeállításokat, a Configuration Manager felügyeleti funkciói. A funkciók konfigurálására használt beállítások a Configuration Manager-hierarchiában, függetlenül attól, hogy közvetlenül a vállalati hálózathoz, távoli kapcsolaton keresztül csatlakoznak vagy csatlakozik az internethez, de a Configuration Manager által támogatott összes ügyfélre érvényesek lehetnek.  

 Ügyfél-információ a Configuration Manager-adatbázis tárolja, és a Microsoftnak nem küldi el. Ezek az adatok addig maradnak az adatbázisban, amíg a 90 naponta végrehajtott **Elavult eszközfelderítési adatok törlése** helykarbantartási feladat nem törli azokat. Beállíthatja a törlési időközt.  

 A Configuration Manager-ügyfél konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

### <a name="privacy-information-for-mobile-devices-that-are-enrolled-by-configuration-manager"></a>A mobileszközre telepített és a Configuration Manager által beléptetett ügyfelekre vonatkozó adatvédelmi információ  
 Adatvédelmi információ a mobileszköz a Configuration Manager által beléptetett: [System Center Configuration Manager adatvédelmi nyilatkozata – mobileszközökre vonatkozó kiegészítése](../../../../core/misc/privacy/privacy-statement-mobile-device-addendum.md).  

### <a name="client-status"></a>Ügyfélállapot  
 A Configuration Manager figyeli az ügyfelek tevékenységét, és rendszeresen kiértékeli, és javítani tudja a Configuration Manager-ügyfelet és annak függőségeit. Az ügyfélállapot alapértelmezés szerint engedélyezve van, és kiszolgálóoldali metrikákat használ az ügyféltevékenység ellenőrzéséhez, illetve a ügyféloldali műveleteket az önellenőrzéshez, a szervizeléshez, valamint az ügyfélállapot információkat a Configuration Manager-hely. Az ügyfél az Ön által konfigurált ütemezés szerint futtatja az önellenőrzéseket. Az ügyfél elküldi az ellenőrzések eredményeit a Configuration Manager-hely. Az adatok átvitele titkosított formában történik.  

 Ügyfélállapot-adatokat a Configuration Manager-adatbázis tárolja, és a Microsoftnak nem küldi el. A helyadatbázis titkosítás nélkül tárolja az információt. Ez az információ mindaddig az adatbázisban marad, amíg le nem telik **Az ügyfélállapot előzményeinek megőrzése a következő számú napra** ügyfélállapot-beállításnak megfelelő időtartam. A beállítás alapértelmezett értéke 31 nap.  

 Ügyfél telepítése előtt a Configuration Manager az ügyfél állapotának ellenőrzését, gondolja át az adatvédelmi követelményeit.  

##  <a name="BKMK_Privacy_ExchangeConnector"></a>Az Exchange Server-összekötő használatával felügyelt mobileszközökre vonatkozó adatvédelmi információ  
 Az Exchange Server-összekötő megkeresi és felügyeli azokat az eszközöket, amelyek az ActiveSync protokoll használatával kapcsolódnak a helyszíni vagy szolgáltatott Exchange Server-kiszolgálóhoz. Az Exchange Server-összekötő által talált rekordokat a Configuration Manager adatbázisában tárolódnak. Az adatok összegyűjtése az Exchange Server-kiszolgálóról történik. A kiszolgáló csak azokat az adatokat tartalmazza, amelyeket a mobileszközök küldenek az Exchange Server-kiszolgálónak.  

 A program nem küld a mobileszközökre vonatkozó adatokat a Microsoftnak. A mobileszközökre vonatkozó adatokat a Configuration Manager adatbázisban tárolódik. Ezek az adatok addig maradnak az adatbázisban, amíg a 90 naponta végrehajtott **Elavult eszközfelderítési adatok törlése** helykarbantartási feladat nem törli azokat. Beállíthatja a törlési időközt.  

 Az Exchange Server-összekötő telepítése és konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

