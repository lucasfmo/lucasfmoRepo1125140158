---
title: "Internet alapú ügyfélfelügyelethez |} Microsoft Docs"
description: "Hozzon létre egy csomagot, az internetes ügyfeleket a System Center Configuration Managerben kezeléséhez."
ms.custom: na
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 83a7c934-3b11-435d-ba22-cbc274951e83
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 90c30bfb22735f73422f1547301552bf42022bb9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-internet-based-client-management-in-system-center-configuration-manager"></a>Tervezze meg az Internet alapú ügyfélfelügyelethez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Internetes ügyfél-kezelés (más néven IBCM) segítségével kezelheti a System Center Configuration Manager ügyfelek, amikor nem csatlakoznak a vállalati hálózathoz, de rendelkeznek normál internetkapcsolattal. Ennek a megoldásnak több előnye is van, például csökkenti a költségeket azzal, hogy nem kell virtuális magánhálózatokat (VPN) futtatni, és a legalkalmasabb időpontban lehet végrehajtani a szoftverfrissítések központi telepítését.  

 A nyilvános hálózatban lévő ügyfelekkel kapcsolatos fokozottabb biztonsági követelmények miatt az internetalapú ügyfélfelügyelethez az szükséges, hogy PKI-tanúsítványt használjanak mind az ügyfelek, mind azok a helyrendszer-kiszolgálók, amelyekhez az ügyfelek csatlakoznak. Ez lehetővé teszi, hogy a kapcsolatokat független hitelesítésszolgáltató hitelesítse, valamint azt, hogy a helyrendszer-kiszolgálóknak küldött és a helyrendszer-kiszolgálók által küldött adatok titkosíthatók legyenek az SSL (Secure Sockets Layer) protokoll használatával.  

 Az ügyfelek internetalapú felügyeletének megtervezésekor vegye figyelembe a következő részekben foglalt információt:  

##  <a name="features-that-are-not-supported-on-the-internet"></a>Az interneten nem támogatott funkciók  
 Nem minden ügyfél-felügyeleti funkció alkalmas az interneten való használatra, ezért ezek a funkciók nem támogatottak, amikor az ügyfelek felügyelete az interneten történik. Az internetes felügyelet esetében nem támogatott funkciók jellemzően azok a funkciók, amelyek az Active Directory tartományi szolgáltatásokon alapulnak, illetve amelyek nem alkalmazhatók a nyilvános hálózatokban, például a hálózati felderítés és a hálózati ébresztés.  

 A következő funkciók nem támogatottak az internetalapú ügyfélfelügyelet esetében:  

-   Az ügyfelek központi telepítése az interneten keresztül, például az ügyfélleküldéses telepítés és a szoftverfrissítéses ügyféltelepítés. Ezek helyett kézi ügyféltelepítést kell használnia.  

-   Automatikus helyhozzárendelés.  

-   Hálózati ébresztés.  

-   Az operációs rendszer központi telepítése. Telepíthet azonban olyan feladatütemezéseket, amelyek nem az operációs rendszer központi telepítését hajtják végre, például olyan feladatütemezéseket, amelyek parancsfájlokat és karbantartási feladatokat futtatnak az ügyfeleken.  

-   Távvezérlés.  

-   A szoftverek központi telepítése a felhasználók számára, kivéve ha az internetes felügyeleti pont hitelesíteni tudja a felhasználót az Active Directory tartományi szolgáltatásokban Windows-hitelesítés (Kerberos vagy NTLM) használatával. Ez akkor lehetséges, amikor az internetes felügyeleti pont megbízhatónak tekinti azt az erdőt, amelyben a felhasználói fiók található.  

 Ezenkívül az internetes ügyfélfelügyelet nem támogatja a barangolást. A barangolás lehetővé teszi, hogy az ügyfelek mindig a legközelebbi terjesztési pontot találják meg a tartalom letöltéséhez. Az interneten felügyelt ügyfelek a hozzájuk rendelt helyről kommunikálnak a helyrendszerekkel, amikor ezek a helyrendszerek internetes teljes tartománynév használatára vannak beállítva, és a helyrendszerszerepkörök engedélyezik az internetről érkező ügyfélkapcsolatokat. Az ügyfelek nem determinisztikus módon választanak egy internetes helyrendszert, függetlenül a fizikai hely sávszélességtől.  

 Ha internetkapcsolatok fogadására konfigurált szoftverfrissítési ponttal rendelkezik, a Configuration Manager internetes ügyfélrendszerei a szükséges szoftverfrissítések megállapításához mindig ellenőrzik a szoftverfrissítési pontot. Ha azonban ezek az ügyfelek kapcsolódnak az internethez, elsőként nem az internetes terjesztési pontokról, hanem a Microsoft Update szolgáltatásból próbálják meg letölteni a szoftverfrissítéseket. Csak akkor próbálják internetes terjesztési pontról letölteni a szükséges szoftverfrissítéseket, ha ez a művelet nem sikerül. Ügyfelek, amelyek nem internetalapú ügyfélfelügyeletre vannak beállítva soha nem próbálkoznak a szoftverfrissítések letöltése a Microsoft Update szolgáltatásból, de mindig a Configuration Manager terjesztési pontokat használ.  

##  <a name="considerations-for-client-communications-from-the-internet-or-untrusted-forest"></a>Az internetről vagy nem megbízható erdőből kapcsolódó ügyfelekkel folytatott kommunikáció esetén megfontolandó szempontok  
 Elsődleges helyen való telepítés esetén a következő helyrendszerszerepkörök támogatják a nem megbízható helyen, például az interneten vagy nem megbízható erdőben található ügyfelektől érkező kapcsolatokat (a másodlagos helyek nem támogatják az ügyfelek kapcsolódását nem megbízható helyekről):  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Configuration Manager-házirendmodul  

-   Terjesztési pont (felhőalapú terjesztési pontok esetén HTTPS protokoll használata kötelező)  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont  

-   Szoftverfrissítési pont  

 **Az internetes helyrendszerekről:**   
Bár nem kötelező lehet egy ügyfél erdőjében, és hogy a helyrendszer-kiszolgáló közötti megbízhatósági kapcsolat, ha az Internet felé néző helyrendszert tartalmazó erdő megbízhatónak tekinti a felhasználói fiókokat tartalmazó erdőben van, ez a konfiguráció támogatja-e az ügyfélre az eszközök az interneten felhasználóalapú irányelveit, ha engedélyezi a **ügyfélházirend** ügyfélbeállítás **internetes ügyfelek kérelmeinek felhasználói házirend engedélyezése**.  

 A következő konfigurációk bemutatják, hogy az internetes ügyfélfelügyelet mikor támogatja az interneten lévő eszközökre vonatkozó felhasználói házirendeket:  

-   Az internetes felügyeleti pont a szegélyhálózatban található, ahol egy csak olvasható tartományvezérlő hitelesíti a felhasználót, és egy beavatkozó tűzfal engedélyezi az Active Directory-csomagokat.  

-   A felhasználói fiók az A erdőben (az intraneten), az internetes felügyeleti pont pedig a B erdőben (a szegélyhálózatban) található. A B erdő megbízhatónak tekinti az A erdőt, és egy beavatkozó tűzfal engedélyezi a hitelesítési csomagokat.  

-   A felhasználói fiók és az internetes felügyeleti pont az A erdőben (az intraneten) található. A felügyeleti pont proxy-webkiszolgáló (például a Forefront Threat Management Gateway) használatával van közzétéve az interneten.  

> [!NOTE]  
>  Ha a Kerberos-hitelesítés nem sikerül, a rendszer automatikusan az NTLM-hitelesítéssel próbálkozik.  

 Amint az előző példa is mutatja, az internetes helyrendszereket elhelyezheti az intraneten, amikor proxy-webkiszolgáló, például az ISA Server és a Forefront Threat Management Gateway használatával teszi közzé azokat az interneten. Ezek a helyrendszerek beállíthatók úgy, hogy csak az internetről érkező ügyfélkapcsolatokat fogadják, vagy úgy, hogy az internetről és az intranetről érkező kapcsolatokat is fogadják. Amikor proxy-webkiszolgálót használ, beállíthatja azt az SSL-hídképzés (biztonságosabb) vagy az SSL-protokollbújtatás használatára:  

-   **SSL–SSL hídképzés:**   
    Ha proxy webkiszolgálókat alkalmaz az internetalapú ügyfélfelügyelethez, javasolt beállítani az SSL–SSL hídképzést, amely SSL-lezárást használ hitelesítéssel. Az ügyfélszámítógépeket számítógép-hitelesítéssel kell hitelesíteni, míg a régebbi mobileszközügyfelek felhasználói hitelesítést használnak. A Configuration Manager által beléptetett mobileszközök nem támogatják az SSL-hídképzés.  

     A proxy webkiszolgálón történő SSL-lezárás előnye, hogy a rendszer megvizsgálja az internetről érkező csomagokat, mielőtt továbbítaná őket a belső hálózatra. A proxy-webkiszolgáló hitelesíti az ügyféltől érkező kapcsolatot, lezárja azt, majd új hitelesített kapcsolatot nyit az internetes helyrendszerek felé. Configuration Manager-ügyfelek proxy webkiszolgálót használ, amikor az ügyfél azonosítójának (GUID) tárolása biztonságosan történik az ügyfélidentitást a, hogy a felügyeleti pont nem tekinti a proxy-webkiszolgálót az ügyfélnek. Adatközponthíd-képzés a Configuration Manager HTTP – HTTPS vagy HTTPS – HTTP nem támogatott.  

-   **Bújtatás**:   
    Ha a proxy webkiszolgáló nem támogatja az SSL-hídképzés követelményeit, vagy internetes támogatást a Configuration Manager által beléptetett mobileszközök konfigurálni szeretné, SSL-bújtatást is alkalmazhat. Ez a megoldás kevésbé biztonságos, mivel az internetről érkező SSL-csomagok SSL-lezárás nélkül jutnak el a helyrendszerekhez, ezért nem lehet ellenőrizni, hogy nincs-e bennük kártékony tartalom. SSL-bújtatás használata esetén a proxy webkiszolgáló nem végez hitelesítést.  

##  <a name="planning-for-internet-based-clients"></a>Az internetalapú ügyfelek tervezése  
 El kell döntenie, hogy az interneten keresztül felügyelt ügyfélszámítógépek esetében intranetes és internetes, vagy csak internetes ügyfélfelügyeletet kíván-e alkalmazni. Az ügyfélfelügyelet módját csak az ügyfél telepítésekor lehet beállítani. Ha később változtatni szeretne rajta, újra kell telepíteni az ügyfelet.  

> [!NOTE]  
>  Ha egy internetkapcsolattal rendelkező felügyeleti pontot állít be, a felügyeleti ponthoz csatlakozó ügyfelek az elérhető felügyeleti pontokat tartalmazó listájuk következő frissítése után képesek lesznek csatlakozni az internethez.  

> [!TIP]  
>  A csak internetes ügyfélfelügyelet nemcsak az interneten, hanem az intraneten is használható.  

 A csak internetes ügyfélfelügyeletre konfigurált ügyfelek csak azokkal a helyrendszerekkel kommunikálnak, amelyeken engedélyezve vannak az internetes ügyfélkapcsolatok. Ez a konfiguráció olyan számítógépek esetén javasolt, amelyek biztosan soha nem csatlakoznak a vállalat belső hálózatához; például a távoli értékesítési pontokon elhelyezett számítógépek esetében. Azt is megfelelő lehet amikor az ügyfél-kommunikáció HTTPS csak (például a támogatási tűzfal- vagy korlátozott biztonsági házirend), és ha internetalapú helyrendszereket telepít a szegélyhálózaton, és ezek a kiszolgálók kezelése a Configuration Manager-ügyfél segítségével kívánja korlátozni szeretné.  

 Ha munkacsoport-ügyfeleket szeretne felügyelni az interneten, akkor a csak internetes felügyeleti módot válassza.  

> [!NOTE]  
>  Ha úgy állít be egy mobileszközügyfelet, hogy internetalapú felügyeleti pontot használjon, akkor az ügyfélfelügyelet automatikusan csak internetes lesz.  

 Másféle ügyfélszámítógépek esetén használhatja az internetes és intranetes ügyfélfelügyeletet. Ezek az ügyfelek automatikusan tudnak váltani az internetalapú és az intranetes ügyfélfelügyelet között, amikor észlelik, hogy megváltozott a hálózat. Ha ezek az ügyfelek talál, és az intranetes ügyfélkapcsolatokat konfigurált felügyeleti ponthoz csatlakoztatják ezek az ügyfelek rendszer intranetes ügyfélként kezeli, amelyek rendelkeznek a teljes Configuration Manager felügyeleti funkcióihoz. Ha az ügyfél nem talál olyan felügyeleti pontot, amely engedélyezi az intranetes ügyfélkapcsolatokat, vagy nem tud csatlakozni hozzá, akkor egy internetalapú felügyeleti ponthoz próbál kapcsolódni, és ha ez sikerül, akkor az internetalapú helyrendszer felügyeli az ügyfelet a hozzá társított helyen.  

 Internet alapú ügyfélfelügyelethez és intranetes ügyfélfelügyelet közti automatikus váltás azért előnyös, mert, hogy ügyfélszámítógépek automatikusan használhatják el az összes Configuration Manager-szolgáltatásokat, amíg az intranethez kapcsolódnak a fontos felügyeleti funkciók felügyeletét az interneten vannak. Emellett az intraneten megkezdett letöltések zökkenőmentesen folytatódnak az intraneten, illetve fordítva.  

##  <a name="prerequisites-for-internet-based-client-management"></a>Az internetalapú ügyfélfelügyelet előfeltételei  
 Internet alapú ügyfél kezelése a Configuration Manager a következő külső függőségekkel rendelkezik:  

-   Az interneten felügyelt ügyfeleknek rendelkezniük kell internetkapcsolattal.  

     Configuration Manager használ a meglévő internetszolgáltató (ISP) kapcsolatokat az internethez, ami állandó vagy ideiglenes kapcsolatok lehet. A mobil ügyféleszközöknek közvetlen internetkapcsolattal kell rendelkezniük, míg az ügyfélszámítógépeknek lehet közvetlen internetkapcsolata, vagy egy proxy webkiszolgálón keresztül is csatlakozhatnak.  

-   Az internetalapú ügyfélfelügyeletet támogató helyrendszernek rendelkeznie kell internetkapcsolattal, és egy Active Directory-tartományhoz kell tartoznia.  

     Az internetalapú helyrendszernek nem kell megbízhatósági kapcsolatban állnia a helykiszolgáló Active Directory-erdőjével. Ha az internetalapú felügyeleti pont hitelesíteni tudja a felhasználót Windows-hitelesítéssel, akkor a rendszer támogatja a felhasználói házirendeket. Ha a Windows-hitelesítés sikertelen, akkor a rendszer csak a számítógép-házirendeket támogatja.  

    > [!NOTE]  
    >  A felhasználói házirendek támogatásához **igaz** értékre kell állítani az **ügyfélházirendre** vonatkozó következő két ügyfélbeállítást:  
    >   
    >  -   **Felhasználói házirend engedélyezése az ügyfeleken**  
    > -   **Felhasználói házirend lekérésének engedélyezése internetes ügyfelektől**  

     Az internetalapú alkalmazáskatalógus weboldal-elérési pontnak is szüksége van Windows-hitelesítésre azon felhasználók esetében, akiknek a számítógépe az interneten van. Ez a követelmény független a felhasználói házirendektől.  

-   Rendelkeznie kell alkalmas nyilvános kulcsú infrastruktúrával (PKI), amely telepíti és kezeli a tanúsítványokat, amelyekre az ügyfeleknek szükségük van, és amelyeket az interneten és az internetalapú helyrendszer-kiszolgálókon kezelnek.  

     További információ: [PKI certificate requirements for System Center Configuration Manager](/sccm/core/plan-design/network/pki-certificate-requirements)(A System Center Configuration Manager PKI-tanúsítványának követelményei).  

-   Regisztrálni kell állomásbejegyzésként az internetalapú ügyfélkezelést támogató helyrendszerek internetes teljesen minősített tartománynevét (FQDN) a nyilvános DNS-kiszolgálókon.  

-   A beavatkozó tűzfalaknak és proxykiszolgálóknak engedélyezniük kell az internetalapú helyrendszerekhez kapcsolódó ügyfél-kommunikációt.  

     Ügyfél-kommunikációs követelmények:  

    -   HTTP 1.1 támogatása  

    -   Engedélyezze a többrészes MIME-mellékletek HTTP-tartalomtípusát (multipart/mixed és application/octet-stream).  

    -   Engedélyezze a következő HTTP-parancsokat az internetalapú felügyeleti pont számára:  

        -   HEAD  

        -   CCM_POST  

        -   BITS_POST  

        -   GET  

        -   PROPFIND  

    -   Engedélyezze a következő HTTP-parancsokat az internetalapú terjesztési pont számára:  

        -   HEAD  

        -   GET  

        -   PROPFIND  

    -   Engedélyezze a következő HTTP-parancsokat az internetalapú tartalék állapotkezelő pont számára:  

        -   POST  

    -   Engedélyezze a következő HTTP-parancsokat az internetalapú alkalmazáskatalógus weboldal-elérési pont számára:  

        -   POST  

        -   GET  

    -   Engedélyezze a következő HTTP-fejléceket az internetalapú felügyeleti pont számára:  

        -   Range:  

        -   CCMClientID:  

        -   CCMClientIDSignature:  

        -   CCMClientTimestamp:  

        -   CCMClientTimestampsSignature:  

    -   Engedélyezze a következő HTTP-fejléceket az internetalapú terjesztési pont számára:  

        -   Range:  

     A követelmények teljesítéséhez szükséges beállításokról a tűzfal vagy a proxykiszolgáló dokumentációjában talál részletes leírást.  

     Hasonló kommunikációs követelményeket kell teljesíteni abban az esetben is, ha szoftverfrissítési pontot használ az internetes ügyfélkapcsolatokhoz. Erről a Windows Server Update Services (WSUS) dokumentációjában olvashat. Például Windows Server 2003 rendszeren futó WSUS esetén tekintse meg [d függelék: Biztonsági beállítások](http://go.microsoft.com/fwlink/p/?LinkId=143368), biztonsági beállítások központi telepítési függeléket.

