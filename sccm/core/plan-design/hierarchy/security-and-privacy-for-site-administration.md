---
title: "Hely felügyelet biztonsági és adatvédelmi |} Microsoft Docs"
description: "Biztonság és adatvédelem a System Center Configuration Manager helyfelügyeletéhez optimalizálása."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d58176e-abc0-4087-8583-ce70deb4dcf5
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: a60b8c103a303dcae0bd66f3060d5a8f17d1cef9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-site-administration-in-system-center-configuration-manager"></a>Helyfelügyelet biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör biztonsági és adatvédelmi információ a System Center Configuration Manager helyeinek és hierarchiájának.

##  <a name="BKMK_Security_Sites"></a>A helyfelügyelet biztonsági védelmének bevált gyakorlata  
 A következő ajánlott biztonsági eljárások használatával alakítsa ki biztonságos System Center Configuration Manager helyeinek és hierarchiájának.  

 **Futtassa a telepítőt csak megbízható forrásból származik, és a kommunikációs csatornát a telepítési adathordozót és a helykiszolgáló között.**  

 Valaki a a forrásfájlok illetéktelen módosításának megelőzése érdekében futtassa a telepítőt megbízható forrásból származik. Ha a fájlokat a hálózatban tárolja, lássa el védelemmel az adott hálózati helyet.  

 Futtassa a telepítőt hálózati helyről, ha súgójában, a hálózaton keresztül zajlik a fájlok illetéktelen módosításának megakadályozására használja az IPsec vagy Server Message Block (SMB) aláírás a telepítőfájlok forráshelye és a helykiszolgáló között.  

 Emellett ha a segédprogram használatával töltse le a telepítéshez szükséges fájlokat, győződjön meg arról is biztonságossá a helyet, ha ezek a fájlok tárolják, és ezen a helyen a kommunikációs csatorna biztonságáról, ha futtatja a telepítőt.  

 **Az Active Directory-séma kiterjesztése a System Center Configuration Manager, és tegye közzé a helyeket az Active Directory tartományi szolgáltatásokban.**  

 Sémakiterjesztések nem szükségesek a System Center Configuration Manager futtatásához, de a segítségükkel biztonságosabb környezet alakítható, mert a Configuration Manager-ügyfelek és helyrendszer-kiszolgálók tudják lekérni az adatokat egy megbízható forrásból.  

 Ha az ügyfelek nem megbízható tartományban találhatók, központi telepítése a következő helyrendszerszerepköröket az ügyfelek tartományokban:  

-   Felügyeleti pont  

-   Terjesztési pont  

-   Alkalmazáskatalógus weboldal-elérési pontja  

> [!NOTE]  
>  A Configuration Manager megbízható tartomány Kerberos-hitelesítést igényel. Ez azt jelenti, ha ügyfelek egy másik erdőben, amely nem rendelkezik kétirányú erdőszintű megbízható kapcsolattal a helykiszolgáló erdőjével, ezek az ügyfelek nem megbízható tartományban lévőknek tekintendők. Külső megbízhatósági kapcsolat nem elegendő erre a célra.  

 **A helyrendszer-kiszolgálók és a helyek közötti kommunikáció biztonságossá tételéhez használja az IPsec protokollt.**  

 Bár a Configuration Manager közötti kommunikáció biztonságossá a helykiszolgáló és az SQL Server rendszert futtató számítógépen, a Configuration Manager nem védik a helyrendszerszerepkörök és az SQL Server közötti kommunikáció. Csak néhány helyrendszer (a beléptetési pont és az alkalmazáskatalógus webszolgáltatási pontja) állítható be HTTPS használatára a helyen belüli kommunikáció esetében.  

 Ha nem használ további megoldásokat a kiszolgálók közötti csatornák védelmére, a támadók különböző hamisítási és betolakodó illetéktelen személyek általi támadásokkal veszélyeztethetik a helyrendszereket. Ha nem tudja használni az IPsec protokollt, használja az SMB-aláírást.  

> [!NOTE]  
>  A helykiszolgáló és a csomagok forrásaként működő kiszolgáló közötti kommunikációs csatorna védelme rendkívül fontos. Ez a kommunikáció az SMB protokollt használja. Ha nem tudja az IPsec protokollt használni a kommunikáció védelméhez, az SMB-aláírás segítségével akadályozhatja meg a fájlok illetéktelen módosítását, mielőtt az ügyfelek letöltik és futtatják azokat.  

 **Ne változtassa meg a biztonsági csoportokat, amelyek a Configuration Manager hoz létre és felügyel a helyrendszer kommunikációjának védelméhez.**  

 Biztonsági csoportok:  

-   **SMS_SiteSystemToSiteServerConnection_MP_&lt;Helykód\>**  

-   **SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;Helykód\>**  

-   **SMS_SiteSystemToSiteServerConnection_Stat_&lt;Helykód\>**  

A Configuration Manager automatikusan hoz létre és felügyeli ezeket a biztonsági csoportokat. Ebbe beletartozik a számítógépfiókok eltávolítása is a helyrendszerszerepkörök eltávolításakor.  

A szolgáltatás folytonosságának és a minimálisan szükséges jogosultságok biztosításához ne szerkessze kézzel ezeket a csoportokat.  

**Ha az ügyfelek nem tudják lekérdezni a globális katalógus kiszolgálójától a Configuration Manager információt, kezelheti a megbízható legfelső szintű kulcs létesítésének folyamatát kell használnia.**  

Ha az ügyfelek nem tudják lekérdezni a globális katalógusból a Configuration Manager-információt, alkalmazniuk a megbízható legfelső szintű kulcs érvényes felügyeleti pontok hitelesítéséhez. A megbízható legfelső szintű kulcsot az ügyfél beállításjegyzéke tárolja, és csoportházirend használatával vagy kézi konfigurálással állítható be.  

Ha az ügyfél nem rendelkezik a megbízható legfelső szintű kulcs példányával, mielőtt első alkalommal csatlakozik egy felügyeleti ponthoz, megbízhatónak fogja tekinteni az első felügyeleti pontot, amellyel kommunikál. Ha csökkenteni kívánja annak kockázatát, hogy a támadók nem hitelesített felügyeleti pontra irányítják át az ügyfeleket, előzetesen elláthatja az ügyfeleket a megbízható legfelső szintű kulccsal. További információkért lásd: [a megbízható legfelső szintű kulcs tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

**Használjon nem alapértelmezett portszámokat.**  

Nem alapértelmezett portszámok használatával növelheti a biztonságot, mert azok nehezebben támadók számára a környezet felderítését a támadás előkészítésekor. Ha nem alapértelmezett portok használata mellett dönt, tervezze meg őket, előtt a Configuration Manager telepítése, és használja őket portokat következesen a hierarchiában található összes helyen. Ügyfélkérelmekhez használt portokról és a hálózati ébresztés példák használhat nem alapértelmezett portszámokat.  

**Különítse el a szerepköröket a helyrendszereken.**  

Bár az összes helyrendszerszerepkört telepítheti ugyanarra a számítógépre, ezt a megoldást ritkán alkalmazzák a munkakörnyezeti hálózatokban, mivel ez hibalehetőséget teremt.  

**Csökkentse a támadható felületet.**  

Minden helyrendszerszerepkör más kiszolgálón elkülönítése csökkenti annak esélyét, hogy egy helyrendszeren biztonsági rések elleni támadásoknak lehet helyrendszer használja. Több helyrendszerszerepkör szükséges a telepítés az Internet Information Services (IIS) szolgáltatást a helyrendszeren, és ez növeli a támadási felületet. Ha a hardverrel kapcsolatos költségek csökkentése érdekében kombináltan kell alkalmaznia a helyrendszerszerepköröket, az IIS helyrendszerszerepkört csak olyan más helyrendszerszerepkörökkel kombinálja, amelyek igénylik az IIS használatát.  

> [!IMPORTANT]  
>  A tartalék állapotkezelő pont szerepköre kivétel ez. Mivel a helyrendszerszerepkör elfogadja a nem hitelesített adatokat az ügyfelektől, azt javasoljuk, hogy nem minden eddiginél rendel a tartalék állapotkezelő pont szerepkörét bármely más Configuration Manager helyrendszer-szerepkör.  


**Alkalmazza a Windows Server legjobb biztonsági megoldásait, és futtassa a Biztonság beállítása varázslót az összes helyrendszeren.**  

A Biztonság beállítása varázsló segítségével létrehozhat egy olyan biztonsági házirendet, amelyet a hálózatban lévő bármelyik kiszolgálón alkalmazhat. Miután telepítette a System Center Configuration Manager-sablon, a biztonság beállítása varázsló felismeri a Configuration Manager helyrendszer-szerepkörök, szolgáltatások, portokat és alkalmazásokat. Ezután engedélyezi a kommunikációt, amelyre a Configuration Manager szükség, és letiltja a szükségtelen kommunikáció.  

A biztonság beállítása varázsló használata a System Center 2012 Configuration Manager, amely letölthető a Microsoft Download Center eszközkészlete tartalmazza: [A System Center 2012 – Configuration Manager Component Add-ons and Extensions](http://go.microsoft.com/fwlink/p/?LinkId=251931).  

**Állítson be statikus IP-címeket a helyrendszerekhez.**  

A statikus IP-címeket könnyebb védeni a névfeloldásos támadások ellen.  

Statikus IP-címeket is megkönnyítik az IPsec konfigurációját. Az IPsec használata a biztonsági szempontból ajánlott a Configuration Manager helyrendszerei közötti kommunikáció biztonságossá tételéhez.  

**Ne telepítsen más alkalmazásokat a helyrendszer-kiszolgálókra.**  

Ha más alkalmazásokat is telepít a helyrendszer-kiszolgálókon, a Configuration Manager és a kockázati kompatibilitási problémák növeli a támadási felületet.  

**Írja elő helybeállításként az aláírást és engedélyezze a titkosítást.**  

Engedélyezze az aláírási és a titkosítási beállításokat a helyre vonatkozóan. Győződjön meg arról, hogy az összes ügyfél támogatja az SHA-256 kivonatoló algoritmust, majd engedélyezze a **SHA-256 megkövetelése**.  

**Korlátozza és figyelje a Configuration Manager rendszergazda felhasználókat, és a szerepköralapú felügyelet használatával adja meg a számukra szükséges minimális engedélyeket.**  

Hozzáférést felügyeleti a Configuration Manager csak azoknak a felhasználóknak, hogy megbízik, és adja meg számukra a minimálisan a beépített biztonsági szerepkörök használatával vagy a biztonsági szerepkörök testreszabásával. Rendszergazda felhasználók, akik létrehozása, módosítása, és telepíthetik az alkalmazások, a feladatütemezést, a szoftverfrissítések, a konfigurációs elemek és alapkonfigurációkat, a Configuration Manager hierarchiájában található eszközöket is vezérelhetik.  

Rendszeres időközönként ellenőrizze a rendszergazdai jogosultságok kiosztását és a jogosultsági szinteket, és vizsgálja meg, hogy nincs-e szükség változtatásokra.  

További információ szerepköralapú adminisztráció konfigurálásáról: [Szerepköralapú adminisztráció konfigurálása a System Center Configuration Managerben](../../../core/servers/deploy/configure/configure-role-based-administration.md).  

**A Configuration Manager biztonsági mentések biztonságos, és a kommunikációs csatorna biztonságáról, amikor biztonsági mentése és visszaállítása.**  

A Configuration Manager biztonsági, ezen információk közé tartozik, tanúsítványokat és más bizalmas adatokat, a támadó a megszemélyesítéshez használható.  

Használjon SMB-aláírást vagy az IPsec protokollt, amikor a hálózaton keresztül küldi ezeket az adatokat, és lássa el megfelelő védelemmel a biztonsági mentést tároló helyet.  

**Amikor Ön objektumokat exportál vagy importál a Configuration Manager-konzolon egy hálózati helyre, tegye biztonságossá a helyet, és a hálózati csatorna biztonságáról.**  

Korlátozza a hálózati mappához hozzáférő felhasználók körét.  

Használjon SMB-aláírást vagy az IPSec protokollt, valamint a hálózati hely és a helykiszolgáló között az server rendszert futtató számítógépen a Configuration Manager konzol és a hely, hogy az exportált adatok illetéktelen módosításának megakadályozására. Használja az IPsec protokollt az adatok titkosításához a hálózatban az információ felfedésének megakadályozására.  

**Ha egy helyrendszer nem megfelelően eltávolítani, vagy nem működik, és nem állítható vissza, manuálisan távolítsa el a Configuration Manager tanúsítványokat, a kiszolgáló más Configuration Manager-kiszolgálókat.**  

A helyrendszer és helyrendszer-szerepkörök eredetileg létrehozott Társkapcsolat eltávolításához kézzel törölje a Configuration Manager a meghibásodott kiszolgálóhoz tartozó tanúsítványait a **megbízható személyek** többi helyrendszer-kiszolgáló tanúsítványtárolójában. Ez különösen fontos, ha újbóli formázás nélkül kívánja újból használni a kiszolgálót.  

Ezekről a tanúsítványokról további információ: a szakasz **titkosítási funkciók kiszolgálói kommunikációhoz** a [a kriptográfiai szolgáltató szabályozza technikai útmutató a System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

**Ne konfiguráljon internetes helyrendszereket hídként a szegélyhálózathoz és az intranethez.**  

Ne konfiguráljon a helyrendszer-kiszolgálók kell lennie a többhelyű, hogy a peremhálózat és az intranethez való csatlakozáshoz. Bár ez a konfiguráció lehetővé teszi, hogy az internetes helyrendszerek fogadják az internetről és az intranetről érkező ügyfélkapcsolatokat, de kiiktatja a biztonsági határt a szegélyhálózat és az intranet között.  

**Ha a helyrendszer-kiszolgáló nem megbízható hálózatban található (például szegélyhálózatban), állítsa be a helykiszolgálót úgy, hogy kapcsolatokat kezdeményezzen a helyrendszerrel.**  

Alapértelmezés szerint a helyrendszerek kezdeményeznek kapcsolatokat a helykiszolgálóhoz az adatok átvitele céljából, ami biztonsági kockázatot jelenthet, amikor a kezdeményezett kapcsolat nem megbízható hálózatból irányul a megbízható hálózatba. Amikor a helyrendszerek fogadják az internetről érkező kapcsolatokat vagy nem megbízható erdőben találhatók, adja meg a **Kapcsolatok kezdeményezésének megkövetelése a helykiszolgálótól ehhez a helyrendszerhez** helyrendszer-beállítást, hogy a helyrendszer és a helyrendszerszerepkörök telepítése után minden kapcsolat kezdeményezése a megbízható hálózatból történjen.  

**Ha proxy-webkiszolgálót használ az internetes ügyfélfelügyelethez, használja az SSL-hídképzést az SSL-hez lezárásos hitelesítéssel.**  

 Amikor beállítja az SSL-lezárást a proxy-webkiszolgálón, a rendszer megvizsgálja az internetről érkező csomagokat, mielőtt továbbítja azokat a belső hálózatba. A proxy-webkiszolgáló hitelesíti az ügyféltől érkező kapcsolatot, lezárja azt, majd új hitelesített kapcsolatot nyit az internetes helyrendszerek felé.  

 Configuration Manager ügyfélszámítógépeinek proxy-webkiszolgáló használatával csatlakoznak az internetalapú helyrendszerekhez, az ügyfél azonosítójának (GUID) tárolása biztonságosan történik csomagszinten, így a felügyeleti pont nem tekinti a proxy-webkiszolgálót az ügyfélnek. Ha a proxy-webkiszolgáló nem támogatja az SSL-hídképzés követelményeit, az SSL protokollbújtatás is használható. Ez kevésbé biztonságos megoldás, mert a rendszer lezárás nélkül továbbítja az internetről érkező SSL-csomagokat a helyrendszerekbe, így nem vizsgálható meg, hogy nem tartalmaznak-e rosszindulatú tartalmat.  

 Ha a proxy-webkiszolgáló nem támogatja az SSL-hídképzés követelményeit, az SSL-protokollbújtatás is használható. Ez azonban kevésbé biztonságos megoldás, mert a rendszer lezárás nélkül továbbítja az internetről érkező SSL-csomagokat a helyrendszerekbe, így nem vizsgálható meg, hogy nem tartalmaznak-e rosszindulatú tartalmat.  

> [!WARNING]  
>  A Configuration Manager által beléptetett mobileszközök nem használható SSL-hídképzés követelményeinek, és SSL-protokollbújtatást kell használniuk.  

**Használandó konfigurációk, ha a helyet úgy állítja be, hogy felébressze a számítógépeket a szoftvertelepítéshez.**  

-   Ha hagyományos ébresztési csomagok használata esetén használja az alhálózat által vezérelt szórás helyett egyedi.  

-   Ha alhálózat által vezérelt szórást kell használnia, konfigurálja az útválasztókat, hogy az IP-vezérelt szórást csak a helykiszolgálóról és csak a nem alapértelmezett portszámot.  

A különböző hálózati ébresztési technológiákkal kapcsolatos további információkért lásd: [tervezése a System Center Configuration Manager ügyfelek felébresztése](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

**E-mail értesítés használata esetén hitelesített hozzáférést konfiguráljon az SMTP-levelezőkiszolgálóhoz.**  

Amikor csak lehetséges, hogy támogatja a hitelesített hozzáférést olyan levelezőkiszolgálót használjon, és a helykiszolgáló számítógépfiókját használják a hitelesítéshez. Ha felhasználói fiókot kell megadnia a hitelesítéshez, olyan fiókot használjon, amely a lehető legkevesebb jogosultsággal rendelkezik.  

##  <a name="BKMK_Security_SiteServer"></a>A helykiszolgáló biztonsági védelmének bevált gyakorlata  
 Használja a következő ajánlott biztonsági eljárások segítségével a Configuration Manager-helykiszolgáló biztosíthatja.  

 **Telepítse a Configuration Manager rendszert ne tartományvezérlőre, hanem tagkiszolgálóra.**  

 A Configuration Manager hely kiszolgáló és a helyrendszerek nem kell tartományvezérlőre telepíteni. A tartományvezérlők a tartomány-adatbázison kívül nem rendelkeznek helyi biztonsági fiókkezelő (SAM) adatbázissal. Ha telepíti a Configuration Manager azon a tagkiszolgálón, akkor is fenntartható a Configuration Manager-fiókok a tartomány-adatbázis helyett a helyi SAM-adatbázisban.  

 Ez az eljárás a tartományvezérlők támadási felületét is csökkenti.  

 **Másodlagos hely telepítésekor lehetőleg ne a hálózaton keresztül másolja a szükséges fájlokat a másodlagos hely kiszolgálójára.**  

 Futtassa a telepítőt, és hozzon létre egy másodlagos hely nem választja átmásolni a fájlokat a szülőhelyről a másodlagos helyre, és ne használjon hálózati forráshelyet. Ha a hálózaton keresztül másol fájlokat, egy gyakorlott támadó eltérítheti a másodlagos hely telepítési csomagját, és a telepítés előtt illetéktelenül módosíthatja a fájlokat – bár egy ilyen jellegű támadás igen nehezen időzíthető. A támadás kivédhető, ha IPsec vagy SMB protokollt használ a fájlok átviteléhez.  

 Helyett a fájlok másolása a hálózaton, a másodlagos helykiszolgálón, másolja a forrásfájlokat egy helyi mappába media mappájából. Amikor a telepítő futtatásával egy másodlagos helyet hoz létre a a **telepítési forrásfájlok** lapon jelölje be **a másodlagos hely számítógépén (Ez a legbiztonságosabb lehetőség) a következő helyen lévő forrásfájlok használata**, majd adja meg a mappát.  

 További információ: [A telepítővarázsló használata helyek telepítéséhez](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) című témakör [Másodlagos hely telepítése](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_secondary) című szakasza.  

##  <a name="BKMK_Security_SQLServer"></a>Ajánlott biztonsági eljárások az SQL Server  
 A Configuration Manager az SQL Server a háttér-adatbázisként. Ha az adatbázis biztonsága megsérül, a támadók képes megkerülése Configuration Manager, és közvetlenül a Configuration Manager használatával támadásokat indíthatnak SQL-kiszolgáló elérhető. Vegye figyelembe a támadások rendkívül nagy kockázatot és annak megfelelően SQL-kiszolgálón.  

 A következő ajánlott biztonsági eljárások segítségével biztosíthatja az SQL Server Configuration Manager segítségével.  

 **Ne használja a Configuration Manager Helyadatbázis-kiszolgálón más SQL Server-alkalmazások futtatására.**  

 Ha növeli a Configuration Manager Helyadatbázis-kiszolgáló eléréséhez, ez növeli a Configuration Manager adatait fenyegető veszélyek kockázata. Ha a Configuration Manager-Helyadatbázis biztonsága sérül, ugyanazon SQL Server-számítógépen más alkalmazásokra majd szintén veszélynek van.  

 **Az SQL Servert Windows-hitelesítés használatára konfigurálja.**  

 Bár a Configuration Manager Windows-fiókkal és Windows-hitelesítés használatával fér hozzá a helyadatbázishoz, is továbbra is lehet konfigurálni az SQL Server által használandó SQL Server vegyes üzemmód. SQL Server vegyes üzemmód lehetővé teszi, hogy további SQL bejelentkezések elérni az adatbázist, amely nincs szükség, és növeli a támadási felületet.  

 **Fokozottan ügyeljen arra, hogy az SQL Server Expresst használó másodlagos helyeken telepítve legyenek a legújabb szoftverfrissítések.**  

 Egy elsődleges hely telepítésekor a Configuration Manager letölti az SQL Server Express programot a Microsoft Download Center, és az elsődleges hely kiszolgálójára másolja a fájlokat. Ha másodlagos helyet telepít, és válassza ki az SQL Server Express telepítésére vonatkozó beállítást, a Configuration Manager a korábban letöltött verziót telepíti, és nem ellenőrzi, hogy elérhetők-e új verziók. Győződjön meg arról, hogy a másodlagos helykiszolgáló rendelkezik-e a legújabb verziójú, hajtsa végre az alábbi műveletek közül:  

-   A másodlagos hely telepítése után futtassa a Windows Update a másodlagos helykiszolgálón.  

-   A másodlagos hely telepítése előtt manuális módszerrel telepítse az SQL Server Expresst azon a számítógépen, amely a másodlagos hely kiszolgálóját fogja futtatni, és mindenképpen a legújabb verziót telepítse, az összes szoftverfrissítéssel együtt. Ezután a másodlagos hely telepítése, és válassza a meglévő SQL Server-példány lehetőséget.  

Rendszeresen futtassa a Windows Update szolgáltatást a helyek és az SQL Server valamennyi telepített verziójának frissítéséhez annak érdekében, hogy mindig a legújabb szoftverfrissítésekkel rendelkezzenek.  

**Kövesse az SQL Serverhez ajánlott eljárásokat.**  

Ismerje meg és kövesse az adott SQL Server-verzióra vonatkozó ajánlott eljárásokat. Ezzel együtt vegye figyelembe az alábbi követelmények a Configuration Manager:  

-   A helykiszolgáló számítógépfiókjának a Rendszergazdák csoport tagjának kell lennie az SQL Servert futtató számítógépen. Ha az SQL Server ajánlását követi "konfigurálta a rendszergazda rendszerbiztonsági tagok explicit módon", a futtatásához használt fióknak a helykiszolgálón a telepítő az SQL-felhasználók csoport tagjának kell lennie.  

-   Ha tartományi felhasználói fiókkal telepíti az SQL Servert, ügyeljen arra, hogy a helykiszolgáló számítógépfiókja az Active Directory tartományi szolgáltatásokban közzétett egyszerű szolgáltatásnévvel legyen konfigurálva. Az egyszerű szolgáltatásnév hiányában a Kerberos-hitelesítés nem sikerül, és a Configuration Manager telepítése sikertelen.  

##  <a name="BKMK_Security_IIS"></a>Ajánlott biztonsági eljárások az IIS-t futtató helyrendszerekhez  
Több helyrendszer-szerepkörök a Configuration Manager az IIS-t igényelnek. A folyamat az IIS védelme lehetővé teszi, hogy a Configuration Manager számára a megfelelő működést, és csökkenti a biztonsági támadások kockázatát. Gyakorlati, amikor az IIS szolgáltatást igénylő kiszolgálók számának minimalizálása érdekében. például csak annyi felügyeleti pontot futtasson, amennyire feltétlenül szükség van az ügyfelek támogatásához, figyelembe véve az internetalapú ügyfélfelügyelet magas rendelkezésre állási és hálózati elkülönítési követelményeit.  

 Az IIS-t futtató helykiszolgáló biztonságáról az alábbi ajánlott eljárásokkal gondoskodhat.  

 **Tiltsa le az IIS-funkciókat, amelyek nem igényelnek.**  

 Csak a telepített helyrendszerszerepkörhöz minimálisan szükséges IIS-funkciókat telepítse. További információk: [Hely és helyrendszer előfeltételei](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Konfigurálja a helyrendszerszerepköröket úgy, hogy HTTPS-kapcsolatot tegyenek kötelezővé.**  

 A helyrendszerhez HTTPS- helyett HTTP-kapcsolaton keresztül csatlakozó ügyfelek Windows-hitelesítést használnak, amely adott esetben NTLM-hitelesítésre állhat vissza Kerberos-hitelesítés helyett. NTLM-alapú hitelesítés esetén fennáll a veszélye, hogy az ügyfél engedélyezetlen kiszolgálóhoz csatlakozik.  

 Az ajánlott biztonsági eljárás alól kivételt jelenthetnek a terjesztési pontok, ugyanis a csomag-hozzáférési fiókok nem működnek, ha a terjesztési pont HTTPS-kapcsolatra van konfigurálva. A csomag-hozzáférési fiókok lehetővé teszik az engedélyeztetést, amivel korlátozható, hogy mely felhasználók férhetnek hozzá a tartalomhoz. További információkért lásd: [a Tartalomkezelés biztonsági védelmének bevált gyakorlata](../../../core/plan-design/hierarchy/security-and-privacy-for-content-management.md#BKMK_Security_ContentManagement).  

**Az IIS szolgáltatásban állítsa be a megbízható tanúsítványok listáját a helyrendszerszerepkörökhöz.**  

Helyrendszerszerepkörök:  

-   A HTTPS-hez konfigurált terjesztési pont  

-   A felügyeleti pont a HTTPS használatára konfigurált és engedélyezett a mobileszközök támogatásához

A megbízható tanúsítványok listája (CTL) a megbízható legfelső szintű hitelesítésszolgáltatók előre definiált listája. CTL-listát, csoportházirendet és a nyilvános kulcsokra épülő infrastruktúra (PKI) központi telepítés használatakor CTL-listát lehetővé teszi, hogy kiegészíti a meglévő megbízható legfelső szintű hitelesítésszolgáltató a hálózaton, például azokkal, amelyek automatikusan telepített Microsoft Windows vagy a Windows vállalati legfelső szintű hitelesítésszolgáltatók hozzáadva konfigurált. Azonban ha CTL-listát az IIS-ben van konfigurálva, akkor egy részhalmazt határoz meg azokat a megbízható legfelső szintű hitelesítésszolgáltatók.  

Ez erősebb biztonságot tesz lehetővé, hiszen a CTL-lista a benne szereplő hitelesítésszolgáltatók által kibocsátott tanúsítványokra korlátozza az elfogadható ügyfél-tanúsítványok körét. A Windows például jól ismert, harmadik fél hitelesítésszolgáltató tanúsítványait, például VeriSign, Thawte számos tartalmaz.

Alapértelmezés szerint az IIS-t futtató számítógép megbízhatónak tartja azokat a tanúsítványokat, amelyek ezektől az ismert hitelesítésszolgáltatóktól származnak. Ha az IIS nem konfigurál CTL-listát a felsorolt helyrendszerszerepkörökhöz, mint érvényes Configuration Manager ügyfél elfogadható minden olyan eszköz, amely az említett hitelesítésszolgáltatóktól származó ügyféltanúsítvánnyal rendelkezik. Ha az IIS-ben konfigurált CTL-listán nem szerepelnek ezek a hitelesítésszolgáltatók, a csatlakozni kívánó ügyfél tanúsítványa azonban ezek valamelyikétől származik, a rendszer elutasítja az ügyfélkapcsolatot. Azonban a Configuration Manager-ügyfelek el kell fogadni a felsorolt helyrendszerszerepkörökhöz, konfigurálnia kell az IIS CTL-listát, amely a Configuration Manager-ügyfelek által használt hitelesítésszolgáltatóknak.  

> [!NOTE]  
>  Csak a felsorolt helyrendszerszerepkörökhöz kell CTL-listát konfigurálni az IIS-ben. A tanúsítványkibocsátók listáját, amelyek a Configuration Manager használ a felügyeleti pontok HTTPS-alapú felügyeleti pontokhoz csatlakozó ügyfélszámítógépek biztosít ugyanezeket a funkciókat.  

Az IIS dokumentációja további információval szolgál arról, miként konfigurálható a megbízható hitelesítésszolgáltatók listája az IIS szolgáltatásban.  

**A helykiszolgálót ne telepítse IIS-t futtató számítógépre.**  

A szerepkörök elkülönítése csökkenti a támadási felületet és javítja a helyreállíthatóságot. Emellett a helykiszolgáló számítógépfiókja jellemzően rendszergazdai jogosultságokkal rendelkezik az összes helyrendszerszerepkör (és valószínűleg a Configuration Manager-ügyfelek, ha ügyfélleküldéses telepítést használ).  

**Használjon dedikált IIS-kiszolgálókat a Configuration Manager.**  

Bár az IIS-kiszolgálókkal, a Configuration Manager által is használt több webalapú alkalmazásokhoz, ez az eljárás jelentősen csökkenti a támadási felületet. Egy nem megfelelően konfigurált alkalmazás egy támadó ahhoz, hogy a vezérlő egy Configuration Manager helyrendszer, amely egy támadó a hierarchia irányítását.  

A Configuration Manager helyrendszerei más webes alkalmazásokat is kell futtatnia, ha a Configuration Manager helyrendszerei egyéni webhely létrehozása.  

**Egyéni webhely használatára.**  

IIS-t futtató helyrendszerek beállíthatja az alapértelmezett webhely helyett egyéni webhelyet használjon az IIS a Configuration Manager. Ha más webalkalmazásokat futtat a helyrendszeren, egyedi webhelyet kell használnia. A beállítás nem egy helyre kiterjedő beállítás helyett egy konkrét helyrendszerre beállítást.  

Az egyéb biztonsági lépések mellett mindenképpen egyedi webhelyet kell használnia, ha más webalkalmazásokat is futtat a helyrendszeren.  

**Ha úgy vált alapértelmezett webhelyről egyéni webhelyre, hogy előtte már terjesztési pontot is telepített, távolítsa el az alapértelmezett virtuális könyvtárakat.**  

Amikor az alapértelmezett webhelyről egyéni webhely használatára vált, a Configuration Manager nem távolítja el a régi virtuális könyvtárakat. Távolítsa el a Configuration Manager az alapértelmezett webhelyen eredetileg létrehozott virtuális könyvtárakat.  

Terjesztési pont esetében például az alábbi virtuális könyvtárakat kell törölnie:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Kövesse az IIS Serverhez ajánlott eljárásokat.**  

Ismerje meg és kövesse az adott IIS Server-verzió ajánlott eljárásait. Azonban vegye figyelembe a követelményeket, amely a Configuration Manager rendelkezik az adott helyrendszer-szerepköröket. További információk: [Hely és helyrendszer előfeltételei](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

##  <a name="BKMK_Security_ManagementPoint"></a>Ajánlott biztonsági eljárások a felügyeleti pont  
 Felügyeleti pontok jelentik az elsődleges kapcsolódási felületet az eszközök és a Configuration Manager között. Fontolja meg a felügyeleti pont és az azt futtató kiszolgálóra a rendkívül nagy kockázatot, és megfelelően elleni támadásokat. Kövesse az összes releváns ajánlott biztonsági eljárást, és figyelje az esetleges szokatlan tevékenységeket.  

 A következő ajánlott biztonsági eljárások segítségével biztonságossá tétele a felügyeleti pontot a Configuration Manager alkalmazásban.  

**Amikor telepíti a Configuration Manager-ügyfél a felügyeleti pont, rendelje hozzá a felügyeleti pont helyéhez.**  

 Kerülje a forgatókönyvet, ahol a Configuration Manager-ügyfél, amely a felügyeleti pont helyrendszeren eltérő a felügyeleti pont helyéhez egy helyhez van rendelve.  

 Ha telepít át, egy korábbi System Center Configuration Manager telepítse át a felügyeleti ponton lévő ügyfélszoftvert a System Center Configuration Manager amint lehetséges.  

##  <a name="BKMK_Security_FSP"></a>Ajánlott biztonsági eljárások a tartalék állapotkezelő pont  
 Használja a következő ajánlott biztonsági eljárások a tartalék állapotkezelő pont a Configuration Manager telepíti.  

 A tartalék állapotkezelő pontok telepítésekor megfontolandó biztonsági szempontokról további információért lásd: [Tartalék állapotkezelő pont szükségességének megállapítása](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md#determine-if-you-need-a-fallback-status-point).  


**Ne futtassa más helyrendszerszerepköröket a helyrendszeren, és ne telepítse a tartalék állapotkezelő pontot tartományvezérlőn.**  

 Mivel a tartalék állapotkezelő pont kialakításából eredően hitelesítés nélküli kommunikációt is fogad bármilyen számítógépről, a más helyrendszerszerepkörökkel vagy tartományvezérlőn való futtatás igen nagy kockázattal jár az adott kiszolgáló számára.  

**A Configuration Manager ügyfél-kommunikációhoz PKI-tanúsítványokat használ, a telepítést, ha a tartalék állapotkezelő pont az ügyfelek telepítése előtt.**  

 Ha a Configuration Manager helyrendszerei nem fogadja el a HTTP ügyfél-kommunikációt, esetleg nem tudja, hogy az ügyfelek PKI-tanúsítvánnyal kapcsolatos problémák miatt nem felügyelt. Azonban ha az ügyfelek egy tartalék állapotkezelő ponthoz legyenek rendelve, a tanúsítvány problémák által jelentett a tartalék állapotkezelő pont.  

 Biztonsági okokból nem rendelhet tartalék állapotkezelő pont az ügyfelek telepítés után. Ehelyett rendelhet hozzá ezt a szerepkört csak az ügyfél telepítése során.  

**Kerülje a tartalék állapotkezelő pont használatát szegélyhálózatban.**  

 A kiépítése szerint a tartalék állapotkezelő pont bármely ügyféltől fogad adatokat. Bár a szegélyhálózatban a tartalék állapotkezelő pont segítheti az internet alapú ügyfelek hibaelhárítását, egyensúlyozni kell a hibaelhárítás előnyei és annak kockázata között, ha olyan a helyrendszer, hogy elfogadja a nyilvánosan elérhető hálózat hitelesítés nélküli adatait.  

 Ha telepíti a tartalék állapotkezelő pontot szegélyhálózatra vagy megbízható hálózatra, konfigurálja a helykiszolgálót adatátvitelek kezdeményezése helyett az alapértelmezett beállítás, amely lehetővé teszi, hogy a tartalék állapotkezelő pont használatával kezdeményeznek kapcsolatot a helykiszolgálóval.  

##  <a name="BKMK_SecurityIssues_Clients"></a>A helyfelügyelet biztonsági problémái  
 Tekintse át a következő biztonsági problémákra a Configuration Manager:  

-   A Configuration Manager nem rendelkezik védelemmel az meghatalmazott rendszergazda felhasználók számára a Configuration Manager használ a hálózati támadásokkal szemben. A jogosulatlan rendszergazda felhasználók nagy biztonsági kockázatot jelentenek, és többek között a következő stratégiák számos támadást indíthatnak:  

    -   Használhatnak központi szoftvertelepítést, hogy automatikusan telepítsenek és futtassanak kártevő szoftvert minden Configuration Manager ügyfélszámítógépeken a vállalaton belül.  

    -   A Configuration Manager-ügyfél ügyféli engedély nélkül távvezéreljék a távvezérlés használatával.  

    -   Konfigurálhatnak hirtelen lekérdezési időközöket és rengeteg leltári adatot, hogy szolgáltatásmegtagadási támadást intézzenek az ügyfelek és kiszolgálók ellen.  

    -   Használhatják az egyik hely hierarchiáját, hogy adatokat írjanak a másik hely Active Directory adataihoz.  

    A hely hierarchiája biztonsági határ. Fontolja meg a helyek csak felügyeleti határok legyenek.  

    Naplózzon minden rendszergazda felhasználói tevékenységet, rendszeresen kövesse nyomon a bejegyzéseket. A felhasználóknak minden Configuration Manager felügyeleti kell ahhoz, hogy menjenek és az ellenőrzések rendszeres megkövetelése az alkalmazás feltételeként is a háttér-ellenőrzéssel változni.  

-   Ha a beléptetési pont biztonsága sérül, a támadó megszerezhet hitelesítési tanúsítványokat és ellophatja azon felhasználók hitelesítési adatait, akik beléptetik mobileszközeiket.  

    A beléptetési pont kommunikál a tanúsítványszolgáltatóval, és létrehozhat, módosíthat és törölhet Active Directory objektumokat. Soha ne telepítse a beléptetési pont a szegélyhálózatban, és mindig figyelje a szokatlan tevékenységeket.  

-   Ha a felhasználói profilok használatát megengedi az internet alapú ügyfélfelügyelethez vagy konfigurálja az alkalmazáskatalógus weboldal-elérési pontját a felhasználók részére, amikor azok az interneten vannak, növeli a profil elleni támadás kockázatát.  

    Azon kívül, hogy PKI-tanúsítványokat használ az ügyfélről kiszolgálóhoz való csatlakozásokhoz, ezek a konfigurációk Windows hitelesítést igényelnek, ami esetleg tartaléka lehet a Kerberos helyetti NTLM hitelesítésnek. Az NTLM sebezhető a megszemélyesítés és támadás-indítás vonatkozásában. Az interneten lévő felhasználó sikeres hitelesítéséhez lehetővé kell tenni az internet alapú helyrendszer-kiszolgálóról a tartományvezérlőre csatlakozást.  

-   Az Admin$ megosztás szükséges a helyrendszer-kiszolgálókon.  

    A Configuration Manager helykiszolgáló az Admin$ megosztást használja, és a helyrendszerek szolgáltatási műveleteket hajtson végre. Ne tiltsa le és ne távolítsa el az Admin$ megosztást.  

-   Configuration Manager csatlakozni más számítógépekhez névfeloldási szolgáltatást használ, és ezek a Szolgáltatások erősen biztonságosak az olyan biztonsági támadások ellen, például az IP-hamisítás, illetéktelen módosítás, letagadhatóság, információfelfedés, szolgáltatásmegtagadás és jogok kiterjesztése.  

    Fel és meg kell ismernie a névfeloldáshoz használt DNS és WINS verziójának megfelelő biztonság bevált gyakorlatát, és annak megfelelően kell eljárnia.  

##  <a name="BKMK_Privacy_Cliients"></a>Adatvédelmi tájékoztatás a felderítéshez  
 Felderítés a hálózati erőforrásokról rekordokat hoz létre, és a System Center Configuration Manager-adatbázisban tárolja. Adatfelderítési rekordok tartalmazza a számítógép információit – például az IP-címek, a operációs rendszerek és a számítógép nevét. Az Active Directory felderítési módszerei konfigurálhatók úgy is, hogy felderítsék az Active Directory tartományi szolgáltatásokban tárolt információt is.  

 Az egyetlen felderítési módszer, amely alapértelmezés szerint engedélyezve van a Szívveréses felderítés, de ez a módszer csak felderíti a számítógépek, amelyek már telepítve van a System Center Configuration Manager ügyfél szoftver.  

 A program nem küld felderítési adatokat a Microsoftnak. Ehelyett tárolódik a Configuration Manager adatbázisába. Adatok addig maradnak az adatbázisban, amíg a 90 naponta nem törli azokat a helykarbantartási feladat **elavult eszközfelderítési adatok törlése**.  

 Mielőtt további felderítési módszereket konfigurálna,  vagy kiterjesztené az Active Directory felderítését, vegye számításba az adatvédelmi követelményeket.  

