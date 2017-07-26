---
title: "Végpontok közötti kommunikáció |} Microsoft Docs"
description: "További információk a System Center Configuration Manager-helyrendszerek és -összetevők közötti kommunikáció módját a hálózaton keresztül."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe0e7e-351e-4222-853a-877475adb589
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2ac9f98dc7b455d3b72d794d4311863186ed53ef
ms.openlocfilehash: cd94f9ccc7e196b30e5dc7ae9368d073b7cff5d2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="communications-between-endpoints-in-system-center-configuration-manager"></a>Végpontok közötti kommunikáció a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


##  <a name="Planning_Intra-site_Com"></a> Helyrendszerei közötti kommunikáció egy adott helyen  
 A Configuration Manager helyrendszerei vagy összetevői a hálózaton lévő más helyrendszerekkel vagy a hely a Configuration Manager-összetevők keresztül kommunikálnak, ha a hely konfigurálásától függően a következő protokollok egyikét használják:  

-   Server Message Block (SMB protokoll)  

-   HTTP  

-   HTTPS  

A helyeken a helykiszolgáló és a terjesztési pontok közötti kommunikáció kivételével bármikor lehetséges a kiszolgálók közötti kommunikáció, amelyhez nincs szükség hálózati sávszélességet szabályzó mechanizmusokra. Mivel a helyrendszerek közötti kommunikációt nem szabályozhatja, győződjön meg arról, gyors és a megfelelően csatlakoztatott hálózatok rendelkező helyeken található helyrendszer-kiszolgálók telepítése.  

A következőképpen felügyelheti a tartalom átvitelét a helykiszolgálóról a terjesztési pontokra:  

-   A terjesztési ponton állítsa be a hálózati sávszélesség szabályozását és az ütemezést. Ezek a beállítások a helyek közötti címek által használt konfigurációkra hasonlítanak, és gyakran használhatja ezt a konfigurációt egy másik Configuration Manager-hely telepítése, ha távoli hálózati helyekre történő tartalomátvitel a sávszélességgel kapcsolatos elsődleges szempont helyett.  

-   A terjesztési pontokat telepítheti előkészített terjesztési pontként. Az előkészített terjesztési pont lehetővé teszi olyan tartalom használatát, amelyet kézzel helyez el a terjesztési pont kiszolgálóján, és nincs szükség arra, hogy a hálózaton keresztül továbbítsa a tartalomfájlokat.  

További információkért lásd: [hálózati sávszélesség szabályozása a Tartalomkezelés](manage-network-bandwidth.md).


##  <a name="Planning_Client_to_Site_System"></a> Ügyfelek által kezdeményezett kommunikáció a helyrendszerekkel és a szolgáltatásokkal  
Ügyfelek kezdeményezik a kommunikációt a helyrendszer-szerepköröket, az Active Directory tartományi szolgáltatások és online szolgáltatások. Ahhoz, hogy ezeket az üzeneteket, a tűzfalnak engedélyeznie kell a hálózati forgalmat, ügyfelek és a kommunikáció végpontja között. Ilyen végpontok lehetnek például a következők:  

-   **Az Alkalmazáskatalógus weboldal-elérési pontja**: Támogatja a HTTP és HTTPS-kommunikációt

-   **Felhőalapú erőforrások**: Magában foglalja a Microsoft Azure és a Microsoft Intune  

-   **A Configuration Manager házirendmodul (NDES)**: Támogatja a HTTP és HTTPS-kommunikációt

-   **Terjesztési pontok**: Támogatja a HTTP és HTTPS-kommunikációt, és a HTTPS felhő alapú terjesztési pontok által igényelt  

-   **Tartalék állapotkezelő pont**: Támogatja a HTTP-kommunikációhoz  

-   **Felügyeleti pont**: Támogatja a HTTP és HTTPS-kommunikációt  

-   **Microsoft Update**  

-   **Szoftverfrissítési pontok** : Támogatja a HTTP és HTTPS-kommunikációt  

-   **Állapotáttelepítési pont**: Támogatja a HTTP és HTTPS-kommunikációt  

-   **Különböző tartományi szolgáltatások**  

Egy ügyfél képes kommunikálni a helyrendszer-szerepkör, mielőtt az ügyfél használja szolgáltatáskeresés olyan helyrendszerszerepkör, amely támogatja az ügyfél protokollt (HTTP vagy HTTPS). Alapértelmezés szerint az ügyfelek rendelkezésükre álló legbiztonságosabb módszert használják:  

-   A HTTPS protokoll használatához rendelkeznie kell nyilvános kulcsokra épülő infrastruktúrával (PKI), és telepítenie kell a PKI-tanúsítványokat az ügyfelekre és a kiszolgálókra. További információk a tanúsítványok használatáról: [A System Center Configuration Manager PKI-tanúsítványának követelményei](../../../core/plan-design/network/pki-certificate-requirements.md).  

-   Amikor az IIS-t (Internet Information Services) használó helyrendszerszerepkört telepít, amely támogatja az ügyfelekről érkező kommunikációt, meg kell adnia, hogy az ügyfelek a HTTP vagy a HTTPS protokoll használatával csatlakoznak-e a helyrendszerhez. A HTTP használata esetén meg kell fontolnia az aláírás és a titkosítás alkalmazását is. További információkért lásd: [az aláírási és titkosítási tervezési](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) a [tervezése a System Center Configuration Manager security](../../../core/plan-design/security/plan-for-security.md).  

További információk a szolgáltatások ügyfél általi kereséséről: [A System Center Configuration Managerben az ügyfelek által végzett helyerőforrás- és szolgáltatáskeresés ismertetése](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

További információk a fenti végpontokkal való kommunikáció során az ügyfelek által használt portokról és protokollokról: [a System Center Configuration Managerben használt portok](../../../core/plan-design/hierarchy/ports.md).  

###  <a name="BKMK_clientspan"></a> Az internetről vagy nem megbízható erdőből kapcsolódó ügyfelekkel folytatott kommunikáció esetén megfontolandó szempontok  
A következő helyrendszer-szerepkörök telepítve az elsődleges helyeken támogatási kapcsolatok olyan ügyfelektől, amelyek a nem megbízható helyen, például az interneten vagy nem megbízható erdőben. (A másodlagos helyek nem támogatják az ügyfelek kapcsolódását nem megbízható helyekről):  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Configuration Manager-házirendmodul  

-   Terjesztési pont (felhőalapú terjesztési pontok esetén HTTPS protokoll használata kötelező)  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont  

-   Szoftverfrissítési pont  

**Internetes webhely rendszerek:**   
Nem követelmény, hogy egy ügyfél erdőjében, és hogy a helyrendszer-kiszolgáló közötti bizalmi kapcsolat van. Azonban ha az egy internetes helyrendszert tartalmazó erdő megbízhatónak tekinti az erdő, amely a felhasználói fiókokat tartalmazza, ez a konfiguráció támogatja felhasználóalapú irányelveit eszközök az interneten engedélyezésekor a **ügyfélházirend** ügyfélbeállítás **internetes ügyfelek kérelmeinek felhasználói házirend engedélyezése**.  

A következő konfigurációk bemutatják, hogy az internetes ügyfélfelügyelet mikor támogatja az interneten lévő eszközökre vonatkozó felhasználói házirendeket:  

-   Az internetes felügyeleti pont a szegélyhálózatban található, ahol egy csak olvasható tartományvezérlő hitelesíti a felhasználót, és egy beavatkozó tűzfal engedélyezi az Active Directory-csomagokat.  

-   A felhasználói fiók az A erdőben (az intraneten), az internetes felügyeleti pont pedig a B erdőben (a szegélyhálózatban) található. A B erdő megbízhatónak tekinti az A erdőt, és egy beavatkozó tűzfal engedélyezi a hitelesítési csomagokat.  

-   A felhasználói fiók és az internetes felügyeleti pont az A erdőben (az intraneten) található. A felügyeleti pont proxy-webkiszolgáló (például a Forefront Threat Management Gateway) használatával van közzétéve az interneten.  

> [!NOTE]  
>  Ha a Kerberos-hitelesítés nem sikerül, a rendszer automatikusan az NTLM-hitelesítéssel próbálkozik.  

Amint az előző példa is mutatja, az internetes helyrendszereket elhelyezheti az intraneten, amikor proxy-webkiszolgáló, például az ISA Server és a Forefront Threat Management Gateway használatával teszi közzé azokat az interneten. Ezek a helyrendszerek az internetről érkező ügyfélkapcsolatot csak, vagy az internetes és intranetes ügyfélkapcsolatok konfigurálhatók. Ha proxy-webkiszolgálót használ, a Secure Sockets Layer (SSL)-hídképzés (Biztonságosabb) vagy az SSL-bújtatást az alábbiak szerint konfigurálhatja:  

-   **SSL–SSL hídképzés:**   
    Ha proxy webkiszolgálókat alkalmaz az internetalapú ügyfélfelügyelethez, javasolt beállítani az SSL–SSL hídképzést, amely SSL-lezárást használ hitelesítéssel. Az ügyfélszámítógépeket számítógép-hitelesítéssel kell hitelesíteni, míg a régebbi mobileszközügyfelek felhasználói hitelesítést használnak. A Configuration Manager által beléptetett mobileszközök nem támogatják az SSL-hídképzés.  

     A proxy webkiszolgálón történő SSL-lezárás előnye, hogy a rendszer megvizsgálja az internetről érkező csomagokat, mielőtt továbbítaná őket a belső hálózatra. A proxy-webkiszolgáló hitelesíti az ügyféltől érkező kapcsolatot, lezárja azt, majd új hitelesített kapcsolatot nyit az internetes helyrendszerek felé. Configuration Manager-ügyfelek proxy webkiszolgálót használ, amikor az ügyfél azonosítójának (GUID) tárolása biztonságosan történik a csomag tartalmát a, hogy a felügyeleti pont nem tekinti a proxy-webkiszolgálót az ügyfélnek. Adatközponthíd-képzés a Configuration Manager HTTP – HTTPS vagy HTTPS – HTTP nem támogatott.  

-   **Bújtatás**:   
    Ha a proxy webkiszolgáló nem támogatja az SSL-hídképzés követelményeit, vagy internetes támogatást a Configuration Manager által beléptetett mobileszközök konfigurálni szeretné, SSL-bújtatást is alkalmazhat. Ez a megoldás kevésbé biztonságos, mivel az internetről érkező SSL-csomagok SSL-lezárás nélkül jutnak el a helyrendszerekhez, ezért nem lehet ellenőrizni, hogy nincs-e bennük kártékony tartalom. SSL-bújtatás használata esetén a proxy webkiszolgáló nem végez hitelesítést.  

##  <a name="Plan_Com_X-Forest"></a> Active Directory-erdőkön keresztüli kommunikáció  
A System Center Configuration Manager-helyek és hierarchiák, amelyek több Active Directory-erdők támogatja.  

A Configuration Manager is támogatja, amelyek nem a helykiszolgálóval azonos Active Directory-erdőben lévő tartományi számítógépek és a munkacsoportban lévő számítógépek:  

-   **A helykiszolgáló számára nem megbízható erdőben lévő tartományi számítógépek támogatását**, akkor is:  

    -   Telepítsen helyrendszerszerepköröket a nem megbízható erdőben, és állítsa be a helyadatok közzétételét az Active Directory-erdő számára.  

    -   Ezeket a számítógépeket felügyelni, mintha munkacsoport-számítógépeket.  

  Telepítése helyrendszer-kiszolgálók a nem megbízható Active Directory-erdőben, az ügyfél – kiszolgáló kommunikáció az ügyfelektől, hogy a erdejében fog zajlani adott erdőben, a Configuration Manager Kerberos használatával képes hitelesíteni a számítógépet. Helyadatok közzétételéhez az ügyfél erdőjében, amikor a az ügyfelek számára előnyös az elérhető felügyeleti pontok listáját – például lekérése az Active Directory-erdejükben, nem pedig a hozzárendelt felügyeleti pontról töltse le ezt az információt.  

  > [!NOTE]  
  >  Ha interneten lévő eszközöket szeretne kezelni, internetalapú helyrendszerszerepköröket telepíthet a szegélyhálózatban, ha a helyrendszer-kiszolgálók Active Directory-erdőben találhatók. Ez a forgatókönyv nem igényel kétirányú megbízhatósági kapcsolattal a szegélyhálózat és a helykiszolgáló között.  

-   **Munkacsoportban lévő számítógépek támogatásához**a következőket kell tennie:  

    -   Manuálisan hagyja jóvá a munkacsoportban lévő számítógépeket, ha azok HTTP-ügyfélkapcsolattal csatlakoznak a helyrendszerszerepkörökhöz. Ennek oka az, a Configuration Manager nem tudja ezeket a számítógépeket képes Kerberos segítségével hitelesíteni.  

    -   A munkacsoport ügyfeleit konfigurálja a hálózatelérési fiókok használatára, hogy ezek a számítógépek lekérhessenek tartalmakat a terjesztési pontokról.  

    -   Biztosítson alternatív módszereket a felügyeleti pontok eléréséhez a munkacsoportban lévő ügyfelek számára. Használhatja a DNS-közzétételről, WINS, vagy közvetlenül a felügyeleti pontot rendelhet. Ez azért szükséges, mert ezek az ügyfelek nem kérhetnek le helyinformációkat az Active Directory tartományi szolgáltatásokból.  

    E tartalomtárhoz kapcsolódó erőforrások:  

    -   [Configuration Manager-ügyfelek ütköző rekordjainak kezelése](../../../core/clients/manage/manage-clients.md#BKMK_ConflictingRecords)  

    -   [Hálózati hozzáférési fiók](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#accounts-used-for-content-management)  

    -   [A Configuration Manager-ügyfelek telepítése munkacsoporthoz tartozó számítógépeken](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup)  

###  <a name="bkmk_span"></a> Forgatókönyvek a több tartományra és erdőre kiterjedő hely vagy hierarchia támogatásához  

#### <a name="communication-between-sites-in-a-hierarchy-that-spans-forests"></a>A több erdőre kiterjedő hierarchiában lévő helyek közötti kommunikáció  
Ebben a forgatókönyvben, amely támogatja a Kerberos-hitelesítés kétirányú, erdőszintű megbízható kapcsolatot igényel.  Ha nem rendelkezik kétirányú erdőszintű megbízható kapcsolattal, amely támogatja a Kerberos-hitelesítést, majd a Configuration Manager nem támogatja egy alárendelt helyre a távoli erdőben lévő.  

 **A Configuration Manager támogatja a gyermekhelyek telepítését olyan távoli erdőbe, amely rendelkezik a szükséges kétirányú megbízhatósági kapcsolattal a szülőhely erdő**  

-   Például elhelyezhet egy másodlagos hely az elsődleges szülőhelyük másik erdőben, amíg a szükséges megbízható kapcsolat fennáll.  

> [!NOTE]  
>  Egy alárendelt hely lehet elsődleges (ahol a központi adminisztrációs hely a fölérendelt hely) vagy egy másodlagos helyen.  

A Configuration Manager helyek közötti kommunikáció adatbázis-replikációt és fájlalapú átvitelt használ. Amikor helyet telepít, meg kell adnia a fiókot, amellyel a hely telepítéséhez a kijelölt kiszolgálón. Ez a fiók hozza létre és kezeli a helyek közötti kommunikációt is.  

Miután sikeresen befejeződött a hely telepítése, és elkezdődik a fájlalapú átvitel és az adatbázis-replikáció, nincs szükség további beállítások megadására a hellyel való kommunikációhoz.  

**Ha létezik kétirányú erdőszintű megbízható, nem igényli a Configuration Manager további konfigurációs lépéseket.**  

Alapértelmezés szerint amikor új helyet telepít egy másik hely gyermekeként Configuration Manager konfigurálja a következő:  

-   Helyek közötti fájlalapú replikációs útvonal minden olyan helyen, amely a helykiszolgálói számítógépfiókot használja. A Configuration Manager felveszi az egyes számítógépek számítógépfiókját az **SMS_SiteToSiteConnection_&lt;Helykód\>**  csoportba a célszámítógépen.  

-   Beállítja az adatbázis-replikációt az egyes helyeken található SQL Server rendszerek között.  

A következő beállításokat is meg kell adni:  

-   Beavatkozó tűzfalak vagy hálózati eszközök engedélyeznie kell a Configuration Managerhez szükséges hálózati csomagokat.  

-   A névfeloldásnak működnie kell az erdők között.  

-   Hely vagy helyrendszerszerepkör telepítéséhez olyan fiókot kell megadnia, amely helyi rendszergazdai engedélyekkel rendelkezik a megadott számítógépen.  

#### <a name="communication-in-a-site-that-spans-forests"></a>A több erdőre kiterjedő helyen folytatott kommunikáció  
Ez a forgatókönyv nem igényel kétirányú, erdőszintű megbízható kapcsolatot.  

**Az elsődleges helyek támogatják a helyrendszerszerepkörök telepítését a távoli erdőkben lévő számítógépekre**.  

-   Az Alkalmazáskatalógus webszolgáltatási pontja az egyetlen kivétel,  amely csak a helykiszolgálót tartalmazó erdőben támogatott.  

-   Ha a helyrendszerszerepkör fogadja az internetről érkező kapcsolatokat, biztonsági szempontból célszerű olyan helyre telepíteni a helyrendszerszerepköröket, ahol az erdő határa védelmet biztosít a helykiszolgáló számára (például szegélyhálózaton).  

**Helyrendszerszerepkör telepítése nem megbízható erdőben található számítógépekre:**  

-   Meg kell adnia egy **helyrendszer-telepítési fiók**, amely a helyrendszerszerepkör telepítésére fog szolgálni. (Ennek a fióknak helyi rendszergazdai hitelesítő adatokkal való csatlakozáshoz szükséges.) A megadott számítógépen telepítse a helyrendszerszerepköröket.  

-   Jelölje be a **Kapcsolatok kezdeményezésének megkövetelése a helykiszolgálótól ehhez a helyrendszerhez**helyrendszer-beállítást. Ez a konfiguráció lehetővé teszi, hogy a helykiszolgáló kapcsolatot hozzon létre a helyrendszer-kiszolgálóval az adatok átviteléhez. Ez megakadályozza, hogy a megbízható hálózatban helyrendszer-kiszolgáló kapcsolatot kezdeményezzen a nem megbízható helyen lévő számítógépet. Ezek a kapcsolatok a **helyrendszer-telepítési fiók**használatával működnek.  

**Nem megbízható erdőben telepített helyrendszerszerepkör használatához** a tűzfalnak akkor is engedélyeznie kell a hálózati forgalmat, ha az adatátvitelt a helykiszolgáló kezdeményezi.  

A következő helyrendszerszerepkörök emellett közvetlen hozzáférést igényelnek a helyadatbázishoz, Ezért a tűzfalnak engedélyeznie kell a nem megbízható erdőből a hely SQL Server megfelelő forgalmat:  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Felügyeleti pont  

-   Jelentéskészítési szolgáltatási pont  

-   állapotáttelepítési pont  

További információkért lásd: [a System Center Configuration Managerben használt portok](../../../core/plan-design/hierarchy/ports.md).  

**Előfordulhat, hogy konfigurálnia kell a helyrendszerszerepkört a helyadatbázis eléréséhez:**  

A felügyeleti pont és a beléptetési pont helyrendszerszerepkörei is csatlakoznak a helyadatbázishoz.  

-   Alapértelmezés szerint ha ezen helyrendszerszerepkörök vannak telepítve, a Configuration Manager szerint a helyrendszerszerepkör kapcsolatfiókjaként állítja be az új helyrendszer-kiszolgáló számítógépfiókját, és majd felveszi a fiókot az SQL Server megfelelő adatbázis-szerepkörébe.  

-   Amikor nem megbízható tartományba telepíti ezeket a helyrendszerszerepköröket, a helyrendszerszerepkör csatlakozási fiókját úgy kell beállítania, hogy engedélyezze a helyrendszerszerepkör számára az adatok lekérését az adatbázisból.  

Ha tartományi felhasználói fiókot konfigurál a helyrendszerszerepkör kapcsolatfiókjaként, ügyeljen arra, hogy az adott helyen a fióknak megfelelő hozzáférése legyen az SQL Server adatbázisához:  

-   Felügyeleti pont: **Felügyeleti pont adatbázis-csatlakozási fiókja**  

-   A beléptetési pont: **Beléptetési pont Kapcsolatfiókja**  

Vegye figyelembe a következő információt, amikor a más erdőkben használandó helyrendszerszerepköröket tervezi:  

-   Ha futtatja a Windows tűzfal, konfigurálja a megfelelő tűzfalprofilokat továbbítani a kommunikációt a Helyadatbázis-kiszolgáló és a távoli helyrendszerszerepköröket tartalmazzák, telepített számítógépek között. Hálózatitűzfal-profilok kapcsolatos információkért lásd: [hálózatitűzfal-profilok ismertetése](http://go.microsoft.com/fwlink/p/?LinkId=233629).  

-   Amikor az internetes felügyeleti pont megbízhatónak tekinti a felhasználói fiókokat tartalmazó erdőt, a rendszer támogatja a felhasználói irányelveket. Ellenkező esetben csak a számítógép-irányelvek támogatottak.  

#### <a name="communication-between-clients-and-site-system-roles-when-the-clients-are-not-in-the-same-active-directory-forest-as-their-site-server"></a>Az ügyfelek és a helyrendszerszerepkörök közötti kommunikáció, amikor az ügyfelek nem abban az Active Directory-erdőben találhatók, mint a helykiszolgálójuk  
A Configuration Manager a helykiszolgáló ugyanabban az erdőben lévő ügyfelek nem támogatja a következő esetekben:  

-   Nincs az erdőben, az ügyfél és a helykiszolgáló az erdő között kétirányú erdőszintű megbízható.  

-   A helyrendszer-szerepkör kiszolgálót az ügyféllel azonos erdőben található.  

-   Az ügyfél, amely nem rendelkezik egy kétirányú, erdőszintű megbízható a helykiszolgálóval, és a helyadatok tartományi számítógépen, az ügyfél erdőjében nincsenek telepítve a helyrendszerszerepköröket.  

-   Az ügyfél csatlakozik egy munkacsoportban működő számítógép.  

Egy tartományhoz csatlakozó számítógép található ügyfelek akkor használhatják szolgáltatáskeresésre az Active Directory tartományi szolgáltatások, amikor a helyük közzé van téve az Active Directory-erdejükben.  

Ha helyinformációkat szeretne közzétenni egy másik Active Directory-erdőbe, a következőket kell tennie:  

-   Adja meg az erdőt, majd engedélyezze a közzétételt az adott erdőbe a **Felügyelet** munkaterület **Active Directory-erdők** csomópontjában.  

-   Az egyes helyeket pedig konfigurálja úgy, hogy azok közzétegyék az adataikat az Active Directory tartományi szolgáltatásokba. Ez a konfiguráció lehetővé teszi, hogy az adott erdőben található ügyfelek lekérjék a helyadatokat és megkeressék a felügyeleti pontokat. Az olyan ügyfelek, amelyek nem használhatják szolgáltatáskeresésre az Active Directory tartományi szolgáltatások DNS, a WINS is használhatja, vagy az ügyfélhez rendelt felügyeleti pont.  

###  <a name="bkmk_xchange"></a> Az Exchange Server-összekötő elhelyezése egy távoli erdőben  
Ennek támogatásához ellenőrizze, hogy névfeloldás működik-e az erdők között (például állítsa be a DNS-továbbítást), és az Exchange Server-összekötő konfigurálásakor adja meg az intranetes Exchange Server teljes tartománynevét. További információkért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

