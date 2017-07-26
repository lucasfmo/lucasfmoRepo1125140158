---
title: "Szükséges tanúsítványok beállítása |} Microsoft Docs"
description: "A helyszíni mobileszközök kezeléséhez a System Center Configuration Manager megbízható kommunikációhoz szükséges tanúsítványok beállítása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2a7d7170-1933-40e9-96d6-74a6eb7278e2
caps.latest.revision: 27
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 3d695a2a40fd86ad991a26db3dcecbbb9ca186cc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-certificates-for-trusted-communications-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>A megbízható kommunikációhoz szükséges tanúsítványok beállítása a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a\-helyszíni mobileszköz-kezelés megköveteli, hogy a beléptetési pont, beléptetési proxypont, terjesztési pont és eszközfelügyeleti pont helyrendszerszerepkör esetében állítható be a felügyelt eszközökkel való megbízható kommunikációhoz. Minden, a felsoroltak közül egy vagy több szerepkörrel rendelkező helyrendszer-kiszolgálónak olyan egyedi PKI-tanúsítvánnyal kell rendelkeznie, amely a webkiszolgálóhoz van kötve az adott rendszerben. Ahhoz, hogy megbízható kommunikációt lehessen létrehozni az eszközökkel, tárolni kell rajtuk egy olyan tanúsítványt, amelynek a legfelső szintű hitelesítésszolgáltatója azonos a kiszolgálók tanúsítványáéval.  

 A tartományhoz csatlakozó eszközök esetében az Active Directory tanúsítványszolgáltatások automatikusan telepítik az összes eszközre a szükséges tanúsítványt, a megfelelő legfelső szintű hitelesítésszolgáltatóval. A tartományhoz nem csatlakoztatott eszközök esetében más módon kell beszereznie egy olyan érvényes tanúsítványt, amelynek megbízható a legfelső szintű hitelesítésszolgáltatója. Ha a hely hitelesítésszolgáltatóját használja megbízható legfelső szintként (amely azonos az Active Directory által a tartományhoz csatlakoztatott eszközökhöz használt legfelső szinttel), akkor a beléptetési pont és a beléptetési proxypont helyrendszer-kiszolgálóinak az adott hitelesítésszolgáltató által kibocsátott tanúsítvánnyal kell rendelkezniük.  

 Minden felügyelendő eszközre is ugyanezzel a legfelső szintű hitelesítésszolgáltatóval rendelkező tanúsítványt kell telepíteni ahhoz, hogy támogassa a megbízható kommunikációt a helyrendszer-szerepkörökkel. A tömegesen beléptetett eszközök esetében a tanúsítványt belefoglalhatja a beléptetési csomagba, amelyet a regisztrálásnál hozzáad az eszközhöz, amikor a felhasználó első alkalommal indítja el az eszközt. A felhasználó által beléptetett eszközök esetében a tanúsítványt e-mailben, az internetről letölthető formában vagy más módszerrel kell biztosítania.  

 A tartományhoz nem csatlakoztatott eszközök esetében másik megoldásként használhat egy ismert nyilvános legfelső szintű hitelesítésszolgáltatót (például Verisign vagy GoDaddy) a kiszolgálótanúsítvány kibocsátásához. Ezzel elkerülheti azt, hogy kézzel kelljen telepíteni a tanúsítványt az eszközre, mert a legtöbb eszköz natív módon megbízhatónak tekinti azokat a kapcsolatokat, amelyek azonos nyilvános legfelső szintű hitelesítésszolgáltatót használnak. Ez hasznos alternatíva a felhasználók által regisztrált eszközök esetében, amikor is nem lehet minden eszközre a hely hitelesítésszolgáltatóján keresztül telepíteni a megbízható tanúsítványokat.  

> [!IMPORTANT]  
>  Számos módon állítsa be az eszközök és a helyrendszer-kiszolgálói közötti megbízható kommunikációhoz szükséges tanúsítványok a\-helyszíni mobileszköz-kezelés. A jelen cikkben szereplő információk példaként szolgálnak az egyik módszerre. Ehhez a módszerhez a helyen futnia kell egy olyan kiszolgálónak, amelyre telepítve van az Active Directory tanúsítványszolgáltatások szerepkör, valamint a Hitelesítésszolgáltató és Hitelesítésszolgáltató webes igénylése szerepkör-szolgáltatás. Erről Windows Server-szerepkörről az [Active Directory tanúsítványszolgáltatások](http://go.microsoft.com/fwlink/p/?LinkId=115018) témakörben talál további tájékoztatást és útmutatást.  

 A szükséges SSL-kommunikációhoz a Configuration Manager-hely beállításához\-helyszíni mobileszköz-kezelés, kövesse az alábbi magas szintű lépéseket:  

-   [A hitelesítésszolgáltató (CA) konfigurálása a CLR-közzétételhez](#bkmk_configCa)  

-   [A webkiszolgáló-tanúsítvány sablonjának létrehozása a hitelesítésszolgáltatón](#bkmk_certTempl)  

-   [Minden egyes helyrendszerszerepkörhöz a webkiszolgáló-tanúsítvány kérése](#bkmk_requestCert)  

-   [A tanúsítvány hozzákötése a webkiszolgálóhoz](#bkmk_bindCert)  

-   [A legfelső szintű tanúsítvány exportálása a webkiszolgáló-tanúsítvány](#bkmk_exportCert)  

##  <a name="bkmk_configCa"></a>A hitelesítésszolgáltató (CA) konfigurálása a CLR-közzétételhez  
 Alapértelmezés szerint a hitelesítésszolgáltató (CA) LDAP-alapú tanúsítvány-visszavonási listákat (CRL) használ, amelyek lehetővé teszik a kapcsolatlétesítést a tartományhoz csatlakozó eszközök számára. HTTP-alapú tanúsítvány-visszavonási listákat kell hozzáadnia a hitelesítésszolgáltatóhoz, hogy a tartományhoz nem csatlakoztatott eszközöket megbízhatónak lehessen tekinteni a hitelesítésszolgáltató által kibocsátott tanúsítványokkal. Ezek a tanúsítványok szükségesek a Configuration Manager helyrendszer-szerepkörök és az eszközök, a regisztrált üzemeltető kiszolgálók közötti SSL-kommunikációhoz\-helyszíni mobileszköz-kezelés.  

 Az alábbi lépésekkel konfigurálhatja a hitelesítésszolgáltatót a tanúsítvány-visszavonási információk automatikus közzétételére a tanúsítványok kibocsátásához, ami engedélyezi a tartományhoz csatlakoztatott és a tartományhoz nem csatlakoztatott eszközök közötti megbízható kapcsolatokat:  

1.  A hely hitelesítésszolgáltatóját futtató kiszolgálón kattintson a **Start** > **Felügyeleti eszközök** > **Hitelesítésszolgáltató** elemre.  

2.  A Hitelesítésszolgáltató konzolon kattintson a jobb gombbal a **Hitelesítésszolgáltató** elemre, és válassza a **Tulajdonságok** parancsot.  

3.  A hitelesítésszolgáltató tulajdonságai között kattintson a **Bővítmények** lapra, és győződjön meg arról, hogy a **Bővítmény kiválasztása** beállításnál a **CRL terjesztési pont (CDP)** van kiválasztva.  

4.  Válassza a következő lehetőséget: **http://<ServerDNSName\>/CertEnroll/<CAName\><CRLNameSuffix\><DeltaCRLAllowed\>.crl**. Válasszon a következő három lehetőség közül:  

    -   **Felvétel a listákba Ügyfelek használják a különbözeti Visszavonási helyek megkereséséhez.**  

    -   **Felvétel a kiállított tanúsítványok tanúsítványokon.**  

    -   **A kibocsátott CRL-ek IDP kiterjesztésébe felvenni**  

5.  Kattintson a **kilépési modul** lapra, majd **tulajdonságok...** , majd jelölje be **közzé kell tenni a fájlrendszerhez tanúsítványok engedélyezése**.  

6.  Kattintson az **OK** gombra, amikor értesítést kap arról, hogy újra kell indítani az Active Directory tanúsítványszolgáltatásokat.  

7.  Kattintson a jobb gombbal a **Visszavont tanúsítványok** elemre, és kattintson a **Minden feladat** elemre, majd a **Közzététel** elemre.  

8.  A CRL közzététele párbeszédpanelen válassza a **Csak különbözeti CRL** lehetőséget, és kattintson az **OK** gombra.  

##  <a name="bkmk_certTempl"></a>A webkiszolgáló-tanúsítvány sablonjának létrehozása a hitelesítésszolgáltatón  
 Miután közzétette az új tanúsítvány-visszavonási listát a hitelesítésszolgáltatón, a következő lépés az, hogy létre kell hoznia egy webkiszolgálótanúsítvány-sablont. Ez a sablon a beléptetési pont, a beléptetési proxypont, a terjesztési pont és az eszközfelügyeleti pont helyrendszerszerepkört üzemeltető kiszolgálók számára kibocsátott tanúsítványokhoz szükséges. Ezek a kiszolgálók lesznek a helyrendszerszerepkörök és a regisztrált eszközök közötti megbízható kommunikáció SSL-végpontjai.    Kövesse az alábbi lépéseket a tanúsítványsablon létrehozásához:  

1.  Hozzon létre egy **ConfigMgr MDM-kiszolgálók** nevű biztonsági csoportot, amely azokat a kiszolgálókat tartalmazza, amelyeknek megbízható kommunikációra van szükségük a beléptetett eszközökhöz.  

2.  A Hitelesítésszolgáltató konzolon kattintson a jobb gombbal a **Tanúsítványsablonok** elemre, majd kattintson a **Kezelés** elemre a Tanúsítványsablonok konzol betöltéséhez.  

3.  Az eredmények ablaktábláján kattintson a jobb gombbal arra a tételre, amelynél a **Sablon megjelenítendő neve** oszlopban a **Webkiszolgáló** érték jelenik meg, majd kattintson a **Sablon megkettőzése** elemre.  

4.  A **Sablon megkettőzése** párbeszédpanelen ellenőrizze, hogy a **Windows 2003 Server, Enterprise Edition** érték legyen megadva, majd kattintson az **OK**gombra.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást. A Configuration Manager nem támogatja a Windows Server 2008 tanúsítványsablonjait a HTTPS PROTOKOLLT használó megbízható kommunikációhoz.  

    > [!NOTE]  
    >  Ha az Ön által használt hitelesítésszolgáltató Windows Server 2012 rendszeren fut, akkor a rendszer nem kéri a tanúsítványsablon verziójának megadását, amikor a **Sablon megkettőzése** elemre kattint. Ehelyett a következő adatokat adja meg a tanúsítvány tulajdonságainak **Kompatibilitás** lapján:  
    >   
    >  **Hitelesítésszolgáltató**: **Windows Server 2003**  
    >   
    >  **Tanúsítvány kedvezményezettje**: **Windows XP / Server 2003**  

5.  **Az új sablon tulajdonságai** párbeszédpanel **Általános** lapján adja meg a sablon nevét a Configuration Manager helyrendszerein használni kívánt webes tanúsítványok előállításához, például a **ConfigMgr MDM-webkiszolgáló** nevet.  

6.  A **Tulajdonos neve** lapon válassza ki **Az Active Directoryból** elemet, és a tulajdonos nevének formátumánál válassza a **DNS-név** beállítást. Törölje a másodlagos tulajdonosnév jelölőnégyzetének jelölését, ha az **Egyszerű felhasználónév (UPN)** beállítást adta meg.  

7.  Kattintson a **Biztonság** fülre, távolítsa el a **Beléptetés** engedélyt a **Tartománygazdák** és a **Vállalati rendszergazdák** biztonsági csoportból.  

8.  Kattintson a **Hozzáadás** gombra, a szövegmezőbe írja be a **ConfigMgr IIS-kiszolgálók** értéket, majd kattintson az **OK** gombra.  

9. Ehhez a csoporthoz adja meg a **Beléptetés** engedélyt, és ne törölje az **Olvasás** engedélyt.  

10. Kattintson az **OK** gombra, és zárja be a Tanúsítványsablonok konzolt.  

11. A Hitelesítésszolgáltató konzolon kattintson a jobb gombbal a **Tanúsítványsablonok** elemre, és kattintson az **Új**, majd a **Kiállítandó tanúsítványsablon** elemre.  

12. A **Tanúsítványsablonok engedélyezése** párbeszédpanelen jelölje ki az imént létrehozott **ConfigMgr MDM-webkiszolgáló** nevű új sablont, majd kattintson az **OK** gombra.  

##  <a name="bkmk_requestCert"></a>Minden egyes helyrendszerszerepkörhöz a webkiszolgáló-tanúsítvány kérése  
 A regisztrált eszközök\-helyszíni mobileszköz-kezelés meg kell bízniuk a beléptetési pont, beléptetési proxypont, terjesztési pont és eszközfelügyeleti pont üzemeltető SSL-végpontokban.  A következő lépések leírják, hogyan igényelhető az IIS webkiszolgáló-tanúsítványa. Erre az egyes kiszolgálók (SSL-végponton) a szükséges helyrendszerszerepköröket az egyik üzemeltetésének\-helyszíni mobileszköz-kezelés.  

1.  Az elsődleges helykiszolgálón nyissa meg a parancssort rendszergazdai jogosultsággal, írja be az **MMC** parancsot, és nyomja meg az **Enter** billentyűt.  

2.  Az MMC-ben kattintson a **Fájl** > **Beépülő modul hozzáadása/eltávolítása** elemre.  

3.  A Tanúsítványok beépülő modulban válassza a **Tanúsítványok** lehetőséget, kattintson a **Hozzáadás** gombra, válassza a **Számítógépfiók** elemet, kattintson a **Tovább** gombra, kattintson a **Befejezés** gombra, végül kattintson az **OK** gombra a Beépülő modul hozzáadása/eltávolítása párbeszédpanel bezárásához.  

4.  Kattintson a jobb gombbal a **Személyes** elemre, majd kattintson a **Minden feladat** > **Új tanúsítvány kérése** elemre.  

5.  A Tanúsítványigénylés varázslóban kattintson a **Tovább** gombra, válassza az **Active Directory – igénylési házirend** elemet, és a kattintson a **Tovább** gombra.  

6.  Jelölje be a webkiszolgáló-tanúsítvány melletti jelölőnégyzetet (**ConfigMgr MDM-webkiszolgáló**), és kattintson a **Regisztrálás** elemre.  

7.  Miután megtörtént a tanúsítvány regisztrálása, kattintson a **Befejezés** gombra.  

 Mivel minden egyes kiszolgáló egyedi webkiszolgáló-tanúsítvány szükséges, meg kell ismételni ezt a folyamatot a szükséges helyrendszerszerepkörök egyike a üzemeltető összes kiszolgálón\-helyszíni mobileszköz-kezelés.  Ha egy kiszolgáló üzemelteti az összes helyrendszerszerepkört, akkor csak egy webkiszolgáló-tanúsítványt kell igényelnie.  

##  <a name="bkmk_bindCert"></a>A tanúsítvány hozzákötése a webkiszolgálóhoz  
 Az új tanúsítványt most hozzá kell kötni az egyes helyrendszer-kiszolgálók, a szükséges helyrendszerszerepköröket üzemeltető a kiszolgálóhoz való\-helyszíni mobileszköz-kezelés. Kövesse az alábbi lépéseket a beléptetési pont és a beléptetési proxypont helyrendszerszerepkört üzemeltető összes kiszolgáló esetében. Ha egy kiszolgáló üzemelteti az összes helyrendszerszerepkört, akkor csak egyszer kell végrehajtania az alábbi lépéseket. Ezt a feladatot nem kell végrehajtania a terjesztési pont és az eszközfelügyeleti pont helyrendszerszerepkör esetében, mivel ezek automatikusan kapják meg a szükséges tanúsítványt a regisztráció során.  

1.  A beléptetési pontot, a beléptetési proxypontot, a terjesztési pontot vagy az eszközfelügyeleti pontot üzemeltető kiszolgálón kattintson a **Start** > **Felügyeleti eszközök** > **IIS-kezelő** elemre.  

2.  A kapcsolatok listán keresse meg, és kattintson a jobb gombbal **alapértelmezett webhely**, és kattintson a **kötések szerkesztése...**  

3.  A webhely kötései párbeszédpanelen kattintson **https**, és kattintson a **szerkesztése...**  

4.  A Hely kötésének szerkesztése párbeszédpanelen az **SSL-tanúsítvány** beállításnál válassza ki az imént regisztrált tanúsítványt, és kattintson az **OK** gombra, majd a **Bezárás** gombra.  

5.  Az IIS-kezelő konzoljának Kapcsolatok listáján válassza ki a webkiszolgálót, majd a jobb oldali műveletpulton kattintson az **Újraindítás** elemre.  

##  <a name="bkmk_exportCert"></a>A legfelső szintű tanúsítvány exportálása a webkiszolgáló-tanúsítvány  
 Az Active Directory tanúsítványszolgáltatások általában telepítik a szükséges tanúsítványt a hitelesítésszolgáltatóról a tartományhoz csatlakoztatott összes eszközre. A tartományhoz nem csatlakoztatott eszközök azonban nem tudnak kommunikálni a helyrendszer-szerepkörökkel a legfelső szintű hitelesítésszolgáltatótól származó tanúsítvány nélkül. Az ilyen eszközök számára a helyrendszerszerepkörökkel folytatott kommunikációhoz szükséges tanúsítvány beszerzéséhez exportálhatja a webkiszolgálóhoz kötött tanúsítványt.  

 Kövesse az alábbi lépéseket a webkiszolgáló-tanúsítvány legfelső szintű tanúsítványának exportálásához.  

1.  Az IIS-kezelőben kattintson **alapértelmezett webhely**, majd kattintson a jobb oldali műveletpulton **kötések...**  

2.  A hely kötései párbeszédpanelen kattintson a **https**, és kattintson a **szerkesztése...**  

3.  Győződjön meg arról, hogy a webkiszolgáló-tanúsítvány van kiválasztva, és kattintson a **nézet...**  

4.  A webkiszolgáló-tanúsítvány tulajdonságainál kattintson a **Tanúsítványlánc** elemre, a tanúsítványlánc legfelső részén kattintson a legfelső szintű tanúsítványra, és kattintson a **Tanúsítvány megtekintése** elemre.  

5.  A legfelső szintű tanúsítvány tulajdonságainál kattintson **részletek**, és kattintson a **Másolás fájlba...**  

6.  A Tanúsítványexportáló varázslóban kattintson a **Tovább** gombra.  

7.  Győződjön meg arról, hogy **DER kódolású bináris X.509 (.CER)** a kiválasztott formátum, és kattintson a **Tovább** gombra.  

8.  A fájl nevét, kattintson a **Tallózás...** , mentette a tanúsítványfájlt, a nevet a fájlnak a helyét, és kattintson a **mentése**.  

     A regisztrálandó eszközöknek hozzá kell férniük ehhez a fájlhoz a legfelső szintű tanúsítvány importálásához, ezért olyan helyet válasszon, amelyhez a legtöbb számítógép és eszköz hozzáférhet, vagy mentse a fájlt egy tetszés szerinti helyre (például a C meghajtóra), és ezután helyezze át a megfelelő helyre.  

     Kattintson a **Tovább** gombra.  

9. Ellenőrizze a beállításokat, majd kattintson a **Befejezés** gombra.  

