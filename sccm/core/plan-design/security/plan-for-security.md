---
title: "A System Center Configuration Manager security tervezése |} Microsoft Docs"
description: "Ajánlott eljárások és a biztonsággal kapcsolatos további információk a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a216814-ca8c-4d2e-bcef-dc00966a3c9f
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 6145cb69c69dba1eb1b9842079ee1a33686bb18a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-security-in-system-center-configuration-manager"></a>Biztonsági tervezés a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

##  <a name="BKMK_PlanningForCertificates"></a>Tanúsítványok tervezése (önaláírt és PKI)  
 Configuration Manager önaláírt tanúsítványokat és a nyilvános kulcsokra épülő infrastruktúrájú (PKI) tanúsítványokat használ.  

 Legjobb biztonsági megoldásként használjon PKI-tanúsítványokat, amikor csak lehetséges. PKI-tanúsítványkövetelmények kapcsolatban bővebben lásd: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md). Amikor a Configuration Manager PKI-tanúsítványokat igényel, például a mobileszközök és az Intel Active Management Technology (AMT) átadásához, a regisztráció során kell használnia Active Directory tartományi szolgáltatások és a vállalati hitelesítésszolgáltató. A többi PKI-tanúsítvány akkor kell telepítenie és felügyelnie azokat egymástól függetlenül a Configuration Manager alkalmazásból.  

 PKI-tanúsítványok is szükségesek, amikor az ügyfélszámítógépek internetalapú helyrendszerekhez csatlakoznak, és azt javasoljuk, hogy PKI-tanúsítványokat használ, amikor az ügyfelek csatlakoznak a helyrendszerekhez, az Internet Information Services (IIS). További ügyfél-kommunikáció beállításairól lásd: [ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-communication-ports.md).  

 PKI használata esetén a kiszolgáló-kiszolgáló közötti kommunikáció biztonságossá helyrendszerek helyen, a helyek között, és más számítógépek közötti adatátvitel segítségével is használhatja a IPsec. IPsec végrehajtásának nem függ a Configuration Manager alkalmazásból.  

 A Configuration Manager automatikusan önaláírt tanúsítványokat hozhat létre, amikor nem érhetők el PKI-tanúsítványokat, és néhány tanúsítványa a Configuration Manager mindig saját aláírással. A legtöbb esetben a Configuration Manager automatikusan felügyeli az önaláírt tanúsítványokat, és nincs további teendője. Az egyetlen lehetséges kivétel a helykiszolgáló aláíró tanúsítványa. A helykiszolgáló aláíró tanúsítványa mindig önaláírt tanúsítvány, és azt igazolja, hogy az ügyfelek által a felügyeleti pontról letöltött ügyfélházirendek a helykiszolgálóról származnak, és nem lettek illetéktelenül módosítva.  

### <a name="plan-for-the-site-server-signing-certificate-self-signed"></a>A helykiszolgáló aláíró tanúsítványát (önaláírt) tervezése  
 Az ügyfelek biztonságosan kérheti le a helykiszolgáló aláíró tanúsítványának másolatát, Active Directory tartományi szolgáltatásokból és az ügyfélleküldéses telepítésből. Ha az ügyfelek nem olvasható be a helykiszolgáló aláíró tanúsítványának másolatát egy ezek a mechanizmusok, biztonsági szempontból ajánlott példányának telepítése a helykiszolgáló aláíró tanúsítványát az ügyfél telepítésekor. Ez akkor kifejezetten fontos, ha az ügyfél első kommunikációja a hellyel az interneten, mivel a felügyeleti pont nem megbízható hálózathoz csatlakozik, ezért támadásokkal szemben. Ha nem hajtja végre ezt a kiegészítő lépést, az ügyfelek automatikusan letöltik a felügyeleti pontról a helykiszolgáló aláíró tanúsítványának példányát.  

 Ha az ügyfelek biztonságosan nem lehet lekérni a hely kiszolgálói tanúsítvány egy példányát a következők:  

-   Az ügyfelet nem ügyfélleküldéssel telepíti, és igaz az alábbi feltételek bármelyike:  

    -   Az Active Directory-séma nincs kibővítve a Configuration Manager számára.  

    -   Az ügyfél helye nincs közzétéve az Active Directory tartományi szolgáltatásokban.  

    -   Az ügyfél nem megbízható erdőhöz vagy munkacsoporthoz tartozik.  

-   Akkor telepíti az ügyfelet, amikor az az interneten található.  

##### <a name="to-install-clients-with-a-copy-of-the-site-server-signing-certificate"></a>Az ügyfelek telepítése a helykiszolgáló aláíró tanúsítványával együtt  

1.  Keresse meg a helykiszolgáló aláíró tanúsítványát az ügyfél elsődleges hely kiszolgálóján. A tanúsítványt a **SMS** tanúsítványtároló tárolja, a tulajdonos neve **helykiszolgáló** és a következő felhasználóbarát név **helykiszolgáló aláíró tanúsítványa**.  

2.  Exportálja a titkos kulcs nélküli tanúsítványt, és tárolja a fájlt biztonságos helyen férjen hozzá csak biztonságos csatornán, például kiszolgáló-üzenetblokk (SMB) aláírás vagy az IPsec használatával.  

3.  A Client.msi-tulajdonsággal telepítse az ügyfelet **SMSSIGNCERT =***&lt;teljes elérési útja és neve\>*, ccmsetup.exe.  

###  <a name="BKMK_PlanningForCRLs"></a>PKI-tanúsítványok visszavonásának tervezése  
Ha PKI-tanúsítványokat használ a Configuration Managerrel, terv hogyan és kell-e az ügyfelek és kiszolgálók használjanak-e a visszavont tanúsítványok listáját (CRL) a csatlakozó számítógépen lévő tanúsítvány ellenőrzéséhez. A tanúsítvány-visszavonási listát egy fájlt, amely a hitelesítésszolgáltató (CA) hozza létre és bejelentkezhet, és, a hitelesítésszolgáltató kiállított, de visszavont tanúsítványok listáját. A Hitelesítésszolgáltatói rendszergazda vissza tudja vonni a tanúsítványokat, például ha a kiállított tanúsítvány tudható vagy gyanítható, megsértik.  

> [!IMPORTANT]  
>  A tanúsítvány-visszavonási lista helyét adja a tanúsítványt, ha egy CA ki azt, mert arra ügyeljen, hogy a visszavont tanúsítványok listájához semmilyen Configuration Manager által használt PKI-tanúsítványok központi telepítése előtt.  

Alapértelmezés szerint az IIS mindig ellenőrzi az ügyfél-tanúsítványok CRL-t, és a Configuration Manager alkalmazásban ez a konfiguráció nem módosítható. Alapértelmezés szerint a Configuration Manager-ügyfelek mindig ellenőrzik a tanúsítvány-visszavonási listát a helyrendszerekhez. Ezt a beállítást letilthatja egy helytulajdonság és egy CCMSetup tulajdonság megadásával. Intel AMT-alapú számítógépek sávon kívüli kezelésekor is engedélyezheti a CRL-ellenőrzés a sávon kívüli szolgáltatási pont és a sávon kívüli felügyeleti konzolt futtató számítógépekre.  

Számítógépek, amelyek használják a tanúsítvány-visszavonási ellenőrzést, de nem található a tanúsítvány-visszavonási listát fognak működni, mintha a tanúsítványláncban lévő összes tanúsítvány vissza lenne vonva, mert nem lehetett leellenőrizni, ezek hiányában a listából. Ebben az esetben sikertelen lesz az összes olyan kapcsolat, amely tanúsítványt igényel és tanúsítvány-visszavonási listát használ.  

A tanúsítvány-visszavonási lista minden alkalommal történő ellenőrzése nagyobb védelmet kínál a visszavont tanúsítványokkal szemben, de csatlakozási késedelmet és feldolgozási többletet eredményez az ügyfélen. Ezt a kiegészítő biztonsági ellenőrzést akkor érdemes beállítania, ha az ügyfelek az interneten vagy nem megbízható hálózatban vannak.  

Tekintse át a nyilvános kulcsokra épülő infrastruktúra rendszergazdái, mielőtt eldönti, hogy a Configuration Manager-ügyfelek kell ellenőrzi a CRL-t, valamint annak megfontolása tartja ezt a beállítást engedélyezve van a Configuration Manager alkalmazásban az alábbi két feltétel teljesülése esetén:  

-   A nyilvános kulcsokra ÉPÜLŐ infrastruktúra támogatja a visszavont tanúsítványok Listáját, és van közzétéve, ahol az összes Configuration Manager ügyfél meg tudja találni. Ne feledje, hogy ebbe beletartozhatnak az interneten lévő ügyfelek is, ha internetalapú ügyfélfelügyeletet használ, valamint a nem megbízható erdőkben található ügyfelek is.  

-   Az a követelmény, ellenőrzi a CRL-t minden olyan helyrendszert, amely PKI-tanúsítvány használatára van beállítva kapcsolat érték nagyobb, mint a követelmény a gyorsabb kapcsolatok, hatékony feldolgozás az ügyfél és az ügyfelek nem tudnak csatlakozni kiszolgálók, ha nem találják a CRL-t kockázatát.  

###  <a name="BKMK_PlanningForRootCAs"></a>Tervezze meg az a nyilvános kulcsokra épülő infrastruktúra megbízható legfelső szintű tanúsítványok és a tanúsítványkibocsátók listájának  
Ha az IIS-helyrendszerei PKI-ügyféltanúsítványokat használnak az ügyfél-hitelesítéshez a HTTP protokollon vagy az ügyfél-hitelesítéshez és a titkosításhoz a HTTPS protokollon, előfordulhat, hogy a hitelesítésszolgáltató főtanúsítványát helytulajdonságként kell importálnia. Az alábbiakban a két esetben:  

-   Configuration Manager használatával telepít operációs rendszert, és a felügyeleti pontok csak HTTPS-ügyfélkapcsolatokat fogadnak el.  

-   Olyan PKI-ügyféltanúsítványokat használ, amelyek nincsenek hozzákapcsolva a felügyeleti pontokon megbízhatónak minősülő hitelesítésszolgáltatói főtanúsítványhoz.  

    > [!NOTE]  
    >  Amikor attól a hitelesítésszolgáltatótól származó PKI-ügyféltanúsítványokat állít ki, amelyik a felügyeleti pontokhoz használt kiszolgálói tanúsítványokat állítja ki, akkor nem kell megadnia ezt a főtanúsítványt. Azonban több Hitelesítésszolgáltatói hierarchiát használ, és nem biztos abban, hogy hogy ezek megbízhatósági kapcsolat áll fenn, ha importálhatók a legfelső szintű Hitelesítésszolgáltatót az ügyfelek Hitelesítésszolgáltatói hierarchiájába.  

Ha importálnia kell legfelső szintű hitelesítésszolgáltató tanúsítványának a Configuration Manager számára, exportálja azokat a kiállító Hitelesítésszolgáltatóról vagy az ügyfélszámítógépről. Ha a tanúsítványt a kiállító hitelesítésszolgáltatóról exportálja, és az egyúttal a legfelső szintű hitelesítésszolgáltató is, ügyeljen arra, hogy a titkos kulcsot ne exportálja. Az exportált tanúsítványfájlt az illetéktelen biztonságos helyen tárolja. Érhetik el a fájlt, a hely telepítésekor kell lennie. Ha a hálózaton keresztül éri el a fájlt, győződjön meg arról, hogy a kommunikáció védelméhez használjon SMB-aláírást vagy IPsec védett legyen.  

Ha a legfelső szintű Hitelesítésszolgáltatói tanúsítványt importált megújulásakor, importálnia kell a megújított tanúsítvány.  

Ezek importált főtanúsítványok és a legfelső szintű Hitelesítésszolgáltatói tanúsítványt az egyes felügyeleti pontok létrehozása a tanúsítványkibocsátók listáját, hogy a Configuration Manager használnak a következőképpen:  

-   Ha az ügyfelek csatlakoznak a felügyeleti pontokhoz, a felügyeleti pont ellenőrzi a, hogy az ügyfél kapcsolódik egy megbízható legfelső szintű tanúsítvány-e a hely tanúsítványkibocsátói listájában. Ha nem, akkor a felügyeleti pont elutasítja a tanúsítványt, és nem lehet létrehozni a PKI-kapcsolatot.  

-   Ha az ügyfelek PKI-tanúsítványt választanak, és a tanúsítványkibocsátók listájának rendelkezik, olyan tanúsítványt választanak egy megbízható főtanúsítványhoz kapcsolódik a tanúsítványkibocsátók listájának a. Ha nem találnak ilyen tanúsítványt, az ügyfelek nem választanak PKI-tanúsítványt. További információt az ügyféltanúsítvány kiválasztásáról tekintse meg a [PKI-ügyféltanúsítvány kiválasztásának tervezése](#BKMK_PlanningForClientCertificateSelection) című részben.  

A webhely-konfigurációból független, előfordulhat, hogy is legfelső szintű Hitelesítésszolgáltatói tanúsítvány importálásához, amikor a mobileszközök beléptetéséhez, léptetnek be Mac számítógépet, és állítsa be az Intel AMT-alapú számítógépek vezeték nélküli hálózatok.  

###  <a name="BKMK_PlanningForClientCertificateSelection"></a>PKI-ügyféltanúsítvány kiválasztásának tervezése  
 Ha az IIS-helyrendszerei fog használni PKI-ügyféltanúsítványokat az ügyfél-hitelesítéshez HTTP protokollon és az ügyfél-hitelesítési és titkosítási HTTPS protokollon, tervezze meg a Windows-ügyfelek hogyan válassza ki a Configuration Manager használni kívánt tanúsítványt.  

> [!NOTE]  
>  Egyes eszközök nem támogatják a tanúsítványválasztás módszerét. Ehelyett azok automatikusan válassza ki az első tanúsítvány, amely megfelel a tanúsítványokkal szemben támasztott követelmények. Például a Mac számítógépek és mobileszközök ügyfelek nem támogatják a tanúsítványválasztás módszerét.  

Sok esetben elegendő az alapértelmezett konfiguráció és működés. A Windows rendszerű számítógépekre a Configuration Manager-ügyfél több tanúsítvány feltételek alapján szűri ki ezeket az itt megadott sorrendben:  

1.  A tanúsítványkibocsátók listája: A felügyeleti pont által megbízhatónak minősített főtanúsítványhoz kapcsolódik.  

2.  A tanúsítvány az alapértelmezett **Személyes**tanúsítványtárolóban található.  

3.  A tanúsítvány érvényes, nincs visszavonva és nem járt le. Az érvényesség ellenőrzése ellenőrzi, hogy elérhető-e a titkos kulcsot, és, hogy a tanúsítvány nem jön létre egy 3-as verziójú tanúsítványsablont, amely nem kompatibilis a Configuration Managerrel együtt.  

4.  A tanúsítvány rendelkezik ügyfél-hitelesítési funkcióval, vagy a számítógép nevére van kiállítva.  

5.  A tanúsítvány a leghosszabb érvényességi idővel rendelkezik.  

Az ügyfelek a következő műveletekkel állíthatók be a tanúsítványkibocsátók listájának használatára:  

-   A Configuration Manager helyinformációkat az Active Directory tartományi szolgáltatásokban van közzétéve.  

-   Az ügyfelek telepítése ügyfélleküldéssel történik.  

-   Az ügyfelek letöltik a felügyeleti pontról, miután sikeresen hozzá lettek rendelve a helyükhöz.  

-   Ügyféltelepítés ccmcertissuers CCMSetup client.msi tulajdonság van megadva.  

Ügyfelek, amelyek nem rendelkeznek tanúsítványkibocsátói listával, telepítve legyenek, és még nincsenek hozzárendelve a helyhez kihagyja az ellenőrzést. Ha az ügyfelek rendelkeznek tanúsítványkibocsátói listával, és nem rendelkeznek a PKI-tanúsítványt, hogy a tanúsítványkibocsátók listájának egy megbízható főtanúsítványhoz kapcsolódik, tanúsítványválasztás sikertelen lesz, és az ügyfelek ne hajtsa végre a többi tanúsítványválasztási feltétellel.  

A legtöbb esetben a Configuration Manager-ügyfél helyesen ismeri egyedi és megfelelő PKI-tanúsítványt. Azonban ha ez nem sikerül, az ügyfél-hitelesítési funkción alapuló helyett állíthat be két alternatív kiválasztási módszerek:  

-   Részleges karakterlánc-egyezés a tanúsítvány Tulajdonos neve mezőjében. Ebben az esetben nem számít különbségnek a kis- és nagybetűs írásmód, és akkor alkalmazható, ha a mezőben egy számítógép teljes tartományneve van megadva, és a tanúsítványválasztáshoz a tartományutótagot szeretné használni, például **contoso.com**. Ezzel a választási módszerrel bármely olyan karaktersorozatot azonosíthat a tanúsítvány Tulajdonos neve mezőjében lévő értéken belül, amely megkülönbözteti a tanúsítványt a tanúsítványtárolóban lévő többi tanúsítványtól.  

    > [!NOTE]  
    >  A részleges karakterlánc-egyeztetés nem használható a Tulajdonos alternatív neve helybeállítással. Bár a CCMSetup eszközzel megadhat részleges karakterlánc-egyeztetést a tulajdonos alternatív nevéhez, a hely tulajdonságai ezt a következő esetekben felül fogják írni:  
    >   
    >  -   Ha az ügyfelek az Active Directory tartományi szolgáltatásokban közzétett helyinformációkat kérnek le.  
    > -   Ha az ügyfelek telepítése ügyfélleküldéssel történik.  
    >   
    >  Használjon részleges karakterlánc-egyeztetést a tulajdonos alternatív nevének, csak akkor, ha az ügyfelek manuális telepítése, és ha azok nem kérhetnek le helyinformációkat az Active Directory tartományi szolgáltatások. Ilyenek például a csak internetes ügyfelek.  

-   Egyeztetés az ügyféltanúsítvány tulajdonosnevének vagy a tulajdonos alternatív nevének attribútumértékeivel. Ez a kis-és nagybetűket egyezés megfelelő, ha egy X500 használatával megkülönböztető nevét vagy ezzel egyenértékű objektumazonosítóit (OID) RFC 3280 szabványnak, és azt szeretné, hogy a tanúsítványkiválasztás az attribútumértékek alapján. Csak azokat az attribútumokat és -értékeket kell megadnia, amelyek szükségesek a tanúsítvány egyedi azonosításához vagy érvényesítéséhez, illetve a tanúsítvány megkülönböztetéséhez a tanúsítványtár többi tagjától.  

A következő táblázat az attribútum értékeket, amelyeket a Configuration Manager támogatja az ügyfél-tanúsítvány kiválasztási feltételeinek.  

|Objektumazonosító attribútuma|Megkülönböztető név attribútuma|Attribútumdefiníció|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|Tartomány-összetevő|  
|1.2.840.113549.1.9.1|E vagy E-mail|E-mail cím|  
|2.5.4.3|CN|Köznapi név|  
|2.5.4.4|SN|Tulajdonos neve|  
|2.5.4.5|SERIALNUMBER|Sorozatszám|  
|2.5.4.6|C|Országkód|  
|2.5.4.7|L|Helység|  
|2.5.4.8|S vagy ST|Állam vagy megye neve|  
|2.5.4.9|STREET|Utca, házszám|  
|2.5.4.10|O|Szervezet neve|  
|2.5.4.11|OU|Szervezeti egység|  
|2.5.4.12|T vagy Title|Cím|  
|2.5.4.42|G vagy GN vagy GivenName|Utónév|  
|2.5.4.43|I vagy Initials|Monogram|  
|2.5.29.17|(nincs érték)|Tulajdonos alternatív neve|  

Ha egynél több megfelelő tanúsítvány található a kiválasztási feltétel alkalmazása után, felülbírálhatja az alapértelmezett konfiguráció a leghosszabb érvényességi időszakkal rendelkező tanúsítvány kiválasztása és, adja meg, hogy nincs tanúsítvány van kiválasztva. Ebben a forgatókönyvben az ügyfél nem lesz képes kommunikálni az IIS-helyrendszerei PKI-tanúsítvánnyal. Az ügyfél hibaüzenetet küld a hozzárendelt tartalék állapotkezelő pont figyelmezteti a tanúsítványkiválasztás hibájáról, így módosíthatja vagy pontosíthatja a tanúsítványválasztási feltételeket. Ebben az esetben az ügyfél viselkedése attól függ, hogy a sikertelen kapcsolódás HTTPS- vagy HTTP-kapcsolaton keresztül történt-e:  

-   Ha a sikertelen kapcsolódás HTTPS protokollal történt: Az ügyfél HTTP-kapcsolaton keresztül csatlakozni próbál, és az ügyfél önaláírt tanúsítványát használja.  

-   Ha a sikertelen kapcsolódás HTTP protokollal történt: Az ügyfél megpróbálja újra HTTP Protokollon keresztül az önaláírt ügyféltanúsítvány használatával.  

Egyedi PKI-ügyféltanúsítvány azonosításának megkönnyítésére adja meg az alapértelmezett értéktől eltérő egyéni tárolót **személyes** a a **számítógép** tárolja. Azonban létre kell hoznia a tároló egymástól függetlenül a Configuration Manager alkalmazásból, és tanúsítványokat telepítenie az egyéni tárolóba, majd megújítani őket az érvényességi idejük lejárata előtt képesnek kell lennie.  

Az ügyféltanúsítványok beállításainak konfigurálásával kapcsolatos további információkért lásd: a [beállítások megadása a PKI-ügyféltanúsítványok](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) szakasz a [a biztonság konfigurálása a System Center Configuration Managerben](../../../core/plan-design/security/configure-security.md) cikk.  

###  <a name="BKMK_PlanningForPKITransition"></a>A PKI-tanúsítványok és az Internet alapú ügyfélfelügyelethez áttérési stratégia tervezése  
A rugalmas konfigurációs beállításai a Configuration Manager teszik a fokozatos áttérést ügyfelekkel és a webhely biztonságos ügyfélvégpontok PKI-tanúsítványokat használ. PKI-tanúsítványok nagyobb biztonságot, és lehetővé teszik az internetes ügyfelek felügyeletére.  

Konfigurációs beállításai és lehetőségei a Configuration Manager számát, mert nincs egyetlen mód való áttéréshez egy hely összes ügyfél HTTPS-kapcsolat használata. Az alábbi lépések ugyanakkor iránymutatásként szolgálhatnak ehhez:  

1.  A Configuration Manager-helyet telepít, és konfigurálja úgy, hogy a helyrendszerek HTTPS-és HTTP-kapcsolatok fogadására.  

2.  Konfigurálja a **ügyfélszámítógép-kommunikáció** lapon a hely tulajdonságai ezt a **helyrendszer beállításai** van **HTTP vagy HTTPS**, és válassza ki **használjon PKI-ügyféltanúsítvány (ügyfél-hitelesítési képesség) Ha van ilyen**.  További információkért lásd: a [PKI-ügyféltanúsítványok beállításainak konfigurálása](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) szakasz a [a biztonság konfigurálása a System Center Configuration Managerben](../../../core/plan-design/security/configure-security.md) cikk.  

3.  Próbaüzemben vezesse be a PKI-ügyféltanúsítványok használatát. Telepítését bemutató példát lásd: a *központi telepítése a tanúsítvány a Windows ügyfélszámítógépek* szakasz a [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) cikk.  

4.  Ügyfélleküldéses módszerrel telepítse az ügyfeleket. További információkért lásd: a [Configuration Manager-ügyfelek telepítése Ügyfélleküldés használatával hogyan](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush) szakasz a [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) cikk.  

5.  A Configuration Manager konzol segítségével jelentéseivel és információival figyelje az ügyfél központi telepítését és állapotát.  

6.  Az **Eszközök** csomópont **Eszközök és megfelelőség** munkaterületén az **Ügyféltanúsítvány** oszlopban kísérje figyelemmel, hogy hány ügyfél használ PKI-tanúsítványt.  

     Is telepítheti a Configuration Manager HTTPS Readiness Assessment eszközt (**cmHttpsReadiness.exe**) számítógépek és a jelentéseken megtekintheti, hogy hány számítógépen használhatja egy ügyfél PKI ügyféltanúsítványt a Configuration Managerrel.  

    > [!NOTE]  
    >  A Configuration Manager-ügyfél telepítésekor, a **cmHttpsReadiness.exe** eszköz telepítve van a *% windir %***\CCM** mappa. Amikor ügyfélen futtatja az eszközt, az alábbi kapcsolókat használhatja:  
    >   
    >  -   /-Tárolóba:&lt;neve\>  
    > -   / Kiállítók:&lt;listája\>  
    > -   / Feltételek:&lt;feltételek\>  
    > -   /SelectFirstCert  
    >   
    >  Ezek a kapcsolók a **CCMCERTSTORE**, a **CCMCERTISSUERS**, a **CCMCERTSEL**illetve a **CCMFIRSTCERT** Client.msi-tulajdonságokhoz kapcsolódnak. Ezekről a beállításokról bővebben: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties.md).  

7.  Ha meggyőződött arról, hogy elegendő számú ügyfél sikeresen használ a PKI-ügyféltanúsítványt a hitelesítéshez HTTP Protokollon keresztül, kövesse az alábbi lépéseket:  

    1.  Telepítsen webkiszolgálói PKI-tanúsítványt egy tagkiszolgálóra, amely kiegészítő felügyeleti pontot fog futtatni a helyhez, majd konfigurálja a tanúsítványt az IIS-ben. További információkért lásd: a *a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS* szakasz a [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) cikk.  

    2.  Telepítse a felügyeleti pont szerepkört ezen a kiszolgálón, majd a felügyeleti pont tulajdonságai között állítsa az **Ügyfélkapcsolatok** beállítást **HTTPS**értékre.  

8.  Győződjön meg arról, hogy a PKI-tanúsítvánnyal rendelkező ügyfelek az új felügyeleti pontot használják HTTPS-kapcsolaton keresztül. Ennek ellenőrzéséhez használhatja az IIS naplóit vagy teljesítményszámlálóit.  

9. Konfigurálja újra a többi helyrendszerszerepkört HTTPS-alapú ügyfélkapcsolatok használatára. Ha az interneten szeretné felügyelni az ügyfeleket, győződjön meg arról, hogy a helyrendszerek internetes teljes tartománynévvel (FQDN) rendelkeznek, és konfiguráljon külön felügyeleti és terjesztési pontokat az internetről érkező ügyfélkapcsolatok fogadására.  

    > [!IMPORTANT]  
    >  Helyrendszer-szerepkörök beállítása az internetről érkező kapcsolatok fogadására, előtt olvassa el a tervezési információkat és az internetalapú ügyfélfelügyelet előfeltételei. További információkért lásd: [a System Center Configuration Managerben végpontok közötti kommunikáció](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

10. Kiterjeszti a PKI-tanúsítványok bevezetését az ügyfeleken és a helyrendszeren, amelyet az IIS-t futtató, és állítsa be a helyrendszerszerepköröket HTTPS-ügyfélkapcsolatok és internetes kapcsolatok, szükség szerint.  

11. A maximális biztonság: Ha meggyőződött arról, hogy minden ügyfél PKI-tanúsítványt használ hitelesítésre és titkosításra, módosítsa a hely tulajdonságait csak HTTPS PROTOKOLLT használja.  

 Kövesse a terv fokozatosan kívánja bevezetni a PKI-tanúsítványokat, amikor először a hitelesítéshez csak a HTTP Protokollon keresztül, majd a hitelesítéshez és a titkosításhoz a HTTPS PROTOKOLLOKON keresztül csökken a kockázata, hogy az ügyfelek felügyelet nélküli ügyfelekké válnak. Emellett a Configuration Manager által támogatott legmagasabb biztonsági élvezheti.  

##  <a name="BKMK_PlanningForRTK"></a>A megbízható legfelső szintű kulcs tervezése  
A Configuration Manager megbízható legfelső szintű kulcs lehetővé teszi a Configuration Manager-ügyfelekre, ellenőrizhetik, hogy helyrendszerek saját hierarchiájukhoz tartoznak-e. Minden helykiszolgáló generál egy helycserekulcsot a többi hellyel való kommunikációhoz. A megbízható legfelső szintű kulcs a hierarchia legfelső szintű helyétől származó helycserekulcs.  

A függvény a megbízható legfelső szintű kulcs a Configuration Manager főtanúsítványára hasonlít a nyilvános kulcsú infrastruktúra abban, hogy a megbízható legfelső szintű kulcs titkos kulcsával aláírt minden elem megbízhatóvá válik a hierarchia valamennyi. Például a felügyeleti pont tanúsítványának aláírása a megbízható legfelső szintű kulcspár titkos kulcsával, és a megbízható legfelső szintű kulcspár nyilvános kulcs másolatával elérhetővé teszi az ügyfelek számára, ügyfelek képesek megkülönböztetni a hierarchiában lévő felügyeleti pontok és felügyeleti pontok, amelyek nincsenek a hierarchiában. Az ügyfelek a Windows Management Instrumentation (WMI) segítségével tárolják a megbízható legfelső szintű kulcs másolatát a **root\ccm\locationservices** névtér.  

Az ügyfelek kétféle módon képesek automatikusan lekérni a megbízható legfelső szintű kulcs nyilvános példányát:  

-   Az Active Directory-séma ki van bővítve a Configuration Manager, a helyet közzéteszi az Active Directory tartományi szolgáltatásokban, és az ügyfelek egy globáliskatalógus-kiszolgálóról lekérhetik ezeket a helyinformációkat.  

-   Az ügyfelek telepítése ügyfélleküldéssel történik.  

Ha az ügyfelek nem tudják lekérni a megbízható legfelső szintű kulcsot a fenti módszerek egyikével, azt a megbízható legfelső szintű kulcsot fogják használni, amelyet a velük először kapcsolatba lépő felügyeleti pont biztosít számukra. Ebben a forgatókönyvben egy ügyfél házirendét egy támadó felügyeleti pontba, amennyiben kapja a rosszindulatú felügyeleti pontról. Ehhez ugyanakkor igen kifinomult támadás szükséges, amely csak korlátozott ideig mehet végbe, mielőtt az ügyfél egy érvényes felügyeleti pontról lekérné a megbízható legfelső szintű kulcsot. Azonban egy támadó irányítsa át az ügyfeleket rosszindulatú felügyeleti ponthoz a kockázatok csökkentése, ha is előre ellátja az ügyfelek a megbízható legfelső szintű kulcsot.  

Az alábbi eljárásokkal történő előzetes kiépítésére és a Configuration Manager-ügyfelet a megbízható legfelső szintű kulcs ellenőrzése:  

-   Kiépítés előtti ügyfelet a megbízható legfelső szintű kulccsal fájl használatával.  

-   Kiépítés előtti ügyfelet a megbízható legfelső szintű kulccsal fájl nélkül.  

-   A megbízható legfelső szintű kulcs ellenőrzése az ügyfélen.  

> [!NOTE]  
>  Nincs előre létre az ügyfelet a megbízható legfelső szintű kulcs használatával, ha kaphatnak Ez az Active Directory tartományi szolgáltatásokból, vagy a leküldéses telepítés. Ezenkívül nem rendelkezik ügyfelek előzetes ellátásához, mert megbízható kapcsolat PKI-tanúsítványok használata a felügyeleti pontok a HTTPS-kommunikációt.  

Eltávolíthatja a megbízható legfelső szintű kulcs egy ügyfél a Client.msi-tulajdonsággal **RESETKEYINFORMATION = TRUE**, ccmsetup.exe. A megbízható legfelső szintű kulcs cseréjéhez telepítse újra az ügyfelet az új kulccsal, például ügyfélleküldéses módszerrel, vagy az **SMSPublicRootKey** Client.msi-tulajdonság használatával a CCMSetup.exe eszközzel.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-by-using-a-file"></a>Ügyfél előre ellátása a megbízható legfelső szintű kulccsal fájl használatával  

1.  Egy szövegszerkesztőben nyissa meg a fájlt  *&lt;Configuration Manager-könyvtár\>***\bin\mobileclient.tcf**.  

2.  Keresse meg a bejegyzést **SMSPublicRootKey =**, másolja át a kulcsot a sorból, és zárja be a fájlt módosítás nélkül.  

3.  Hozzon létre egy új szövegfájlt, és illessze be a kulccsal kapcsolatos adatokat, a mobileclient.tcf fájlból másolt.  

4.  Mentse a fájlt, és helyezze a helyen, ahol minden számítógép hozzáférhet, de ha a fájl védett az illetéktelen.  

5.  Telepítse az ügyfelet bármely olyan telepítési módszerrel, amely támogatja a Client.msi-tulajdonságokat, és adja meg a Client.msi-tulajdonsággal **SMSROOTKEYPATH =***&lt;teljes elérési útja és neve\>*.  

    > [!IMPORTANT]  
    >  Ügyfél telepítése során a fokozott biztonság a megbízható legfelső szintű kulcs megadása esetén meg kell adnia a helykódot a Client.msi-tulajdonsággal **SMSSITECODE =&lt;Helykód\>**.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-without-using-a-file"></a>Ügyfél előre ellátása a megbízható legfelső szintű kulccsal fájl nélkül  

1.  Egy szövegszerkesztőben nyissa meg a fájlt  *&lt;Configuration Manager-könyvtár\>***\bin\mobileclient.tcf**.  

2.  Keresse meg a bejegyzést, SMSPublicRootKey =, vegye figyelembe a kulcsot a sorból, vagy másolja a vágólapra, és zárja be a fájlt módosítás nélkül.  

3.  Telepítse az ügyfelet bármely olyan telepítési módszerrel, amely támogatja a Client.msi-tulajdonságokat, és adja meg a Client.msi-tulajdonsággal **SMSPublicRootKey =***&lt;kulcs\>*, ahol  *&lt;kulcs\>*  van a mobileclient.tcf fájlból másolt karakterláncot.  

    > [!IMPORTANT]  
    >  Ügyfél telepítése során a fokozott biztonság a megbízható legfelső szintű kulcs megadása esetén meg kell adnia a helykódot a Client.msi-tulajdonsággal **SMSSITECODE =&lt;Helykód\>**.  

#### <a name="to-verify-the-trusted-root-key-on-a-client"></a>A megbízható legfelső szintű kulcs ellenőrzése az ügyfélen  

1.  A a **Start** menüben válasszon **futtatása**, és írja be **Wbemtest**.  

2.  Az a **Windows Management Instrumentation – tesztelés** párbeszédpanelen válassza ki **Connect**.  

3.  Az a **Connect** párbeszédpanel a **Namespace** adja meg a **root\ccm\locationservices**, és válassza a **Connect**.  

4.  Az a **a Windows Management Instrumentation – tesztelés** párbeszédpanel a **IWbemServices** területen válasszon **osztályok enumerálása**.  

5.  Az a **Szuperosztály adatai** párbeszédpanelen válassza ki **rekurzív**, és válassza a **OK**.  

6.  A **Lekérdezés eredménye** ablakban görgessen a lista végére, majd kattintson duplán a **TrustedRootKey ()**elemre.  

7.  Az a **TrustedRootKey objektumszerkesztője** párbeszédpanelen válassza ki **példányok**.  

8.  Az új **lekérdezés eredménye** ablak, amely megjeleníti a példányát **TrustedRootKey**, kattintson duplán a **TrustedRootKey = @**.  

9. Az a **TrustedRootKey objektumszerkesztője = @** párbeszédpanel a **tulajdonságok** területen görgessen le a **TrustedRootKey CIM_STRING**. A jobb oldali oszlopban lévő karakterlánc a megbízható legfelső szintű kulcs. Győződjön meg arról, hogy megegyezik a **SMSPublicRootKey** értékét a fájlban,  *&lt;Configuration Manager-könyvtár\>***\bin\mobileclient.tcf**.  

##  <a name="BKMK_PlanningForSigningEncryption"></a>Az aláírási és titkosítási terv  
 Amennyiben minden ügyfél-kommunikációhoz PKI-tanúsítványokat használ, nincs szüksége aláírás és titkosítás alkalmazásának megtervezésére az ügyfél-adatkommunikáció védelméhez. De ha beállította a HTTP-ügyfélkapcsolatokat engedélyezi az IIS-t futtató helyrendszerek, el kell döntenie, az ügyfél-kommunikációhoz a hely biztonságának.  

 Az ügyfelek felügyeleti pontokra küldött adatok védelme érdekében megkövetelheti az adatok aláírását. Ezenkívül azt is megkövetelheti, hogy a HTTP protokollt használó ügyfelektől érkező összes aláírt adat az SHA-256 algoritmus használatával legyen aláírva. Bár ez egy biztonságosabb beállítás, csak akkor engedélyezze, ha az összes ügyfél támogatja az SHA-256 algoritmust. Sok operációs rendszer natív módon támogatja az SHA-256-ot, a régebbi rendszereknél azonban frissítés vagy gyorsjavítás lehet szükséges. A Windows Server 2003 SP2 rendszert futtató számítógépeken például a [938397-es számú tudásbáziscikk](http://go.microsoft.com/fwlink/p/?LinkId=226666)által ismertetett gyorsjavítást kell telepíteni.  

 Míg az aláírás az adatok módosítása ellen nyújt védelmet, a titkosítás az információfelfedés ellen védi azokat. Lehetősége van a 3DES titkosítás engedélyezésére a leltáradatok és az ügyfelek által a hely felügyeleti pontjainak küldött állapotüzenetek esetén. Nincs frissítéseket telepíteni az ügyfeleken, így támogatja ezt a beállítást, de vegye figyelembe a igényel az ügyfelek és a felügyeleti pontot ehhez a titkosítás és visszafejtés megnövekedett processzorhasználatot.  

 További információt az aláírási és titkosítási beállítások konfigurálásáról, tekintse meg a [konfigurálása aláírási és titkosítási](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) szakasz a [a biztonság konfigurálása a System Center Configuration Managerben](../../../core/plan-design/security/configure-security.md) cikk.  

##  <a name="BKMK_PlanningForRBA"></a>Szerepköralapú felügyelet tervezése  
 További információ: [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="see-also"></a>További információ
[Titkosítási funkciók technikai útmutató a System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

