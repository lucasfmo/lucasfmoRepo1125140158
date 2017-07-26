---
title: "Hibaelhárítási Windows Defender vagy az Endpoint Protection ügyfél |} Microsoft Docs"
description: "Útmutató a Windows Defender és az Endpoint Protection problémáinak elhárítása."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d837253e-fcc2-422a-9e2c-c78b938dfd8c
caps.latest.revision: 7
caps.handback.revision: 0
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: 1b096e71f5131214fb4e235e84d0b7f63e566831
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="troubleshooting-windows-defender-or-endpoint-protection-client"></a>A Windows Defender vagy az Endpoint Protection ügyfél elhárítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Ha problémát tapasztal a Windows Defender vagy az Endpoint Protection használata közben, forduljon a biztonsági rendszergazdához. Az alábbiakkal kapcsolatos hibákat is megpróbálhatja elhárítani:  

-   [A Windows Defender vagy az Endpoint Protection frissítése](#update-windows-defender-or-endpoint-protection)  
-   [A Windows Defender vagy az Endpoint Protection szolgáltatás elindítása](#starting-windows-defender-or-endpoint-protection-service)  
-   [Internetcsatlakozási problémák](#internet-connection-issues)  
-   [Észlelt fenyegetés helyrehozhatatlanok](#detected-threat-cant-be-remediated)  
-   [Az Endpoint Protection ügyfél telepítése](#install-the-endpoint-protection-client)  

##  <a name="update-windows-defender-or-endpoint-protection"></a>A Windows Defender vagy az Endpoint Protection frissítése  
 A Windows Defender vagy az Endpoint Protection automatikusan együttműködve Microsoft Update használatával győződjön meg arról, hogy a vírus- és kémprogram-definíciók mindig naprakészek legyenek.  

 **Tünetek**  

 Ez a cikk az automatikus frissítésekkel kapcsolatos gyakori problémákkal foglalkozik, beleértve az alábbi eseteket:  

-   A frissítések sikertelenségét jelző hibaüzenetek jelennek meg.  

-   Frissítések keresésekor a rendszer hibaüzenetet küld, amelyben azt jelzi, hogy a vírus- és kémprogram-definíciók keresése, letöltése vagy telepítése nem lehetséges.  

-   Annak ellenére, hogy csatlakozik az internethez, a frissítés sikertelen.  

-   A frissítések automatikus telepítése nem történik meg az ütemezésnek megfelelően.  

 **Ok**  

 A frissítési hibákat leggyakrabban az internetkapcsolat problémái okozzák. Ha azonban biztos benne, hogy csatlakozik az internethez, mert más webhelyeket fel tud keresni, lehetséges, hogy a problémát a Windows Internet Explorer beállításaival való ütközések okozzák.  

> [!IMPORTANT]  
>  A lépések elvégzéséhez ki kell lépnie az Internet Explorerből. Ezért nyomtassa ki, írja fel vagy másolja át őket egy másik fájlba, majd lássa el könyvjelzővel a témakört a későbbi eléréshez.  

### <a name="step-1-reset-your-internet-explorer-settings"></a>1. lépés: Az Internet Explorer beállításainak alaphelyzetbe állítása  

1.  Lépjen ki az összes megnyitott programból, az Internet Explorert is beleértve.  

    > [!NOTE]  
    >  Ha alaphelyzetbe állítja ezeket a beállításokat az Internet Explorerben, törlődnek az ideiglenes fájlok, a cookie-k, a böngészési előzmények és az online jelszavak. A kedvencek azonban megmaradnak.  

2.  A **Start** menü keresőmezőjébe írja be az **inetcpl.cpl**parancsot, majd nyomja le az **Enter**billentyűt.  

3.  Az **Internetbeállítások** párbeszédpanelen kattintson a **Speciális** lapra.  

4.  **Az Internet Explorer beállításainak visszaállítása**lehetőségnél kattintson az **Alaphelyzet**elemre, majd az **Alaphelyzetbe állítás** gombra.  

5.  Várjon, amíg az Internet Explorer befejezi a beállítások alaphelyzetbe állítását, majd kattintson az **OK**gombra.  

6.  Nyissa meg az Internet Explorert.  

7.  Nyissa meg a Microsoft Security Essentialst, kattintson a **Frissítés** lapra, majd a **Frissítés**parancsra.  

8.  Ha a probléma továbbra is fennáll, folytassa a következő lépéssel.  

### <a name="step-2-set-internet-explorer-as-the-default-browser"></a>2. lépés: Az Internet Explorer beállítása alapértelmezett böngészőként  

1.  Lépjen ki az összes megnyitott programból, az Internet Explorert is beleértve.  

2.  A **Start** menü keresőmezőjébe írja be az **inetcpl.cpl**parancsot, majd nyomja le az **Enter**billentyűt.  

3.  Az **Internetbeállítások** párbeszédpanelen kattintson a **Programok** lapra.  

4.  Az **Alapértelmezett webböngésző**lehetőségnél kattintson az **Alapértelmezetté tesz**parancsra.  

5.  Kattintson az **OK** gombra.  

6.  Nyissa meg a Windows Defender vagy az Endpoint Protection. Kattintson a **Frissítés** lapra, majd a **Frissítés**parancsra.  

7.  Ha a probléma továbbra is fennáll, folytassa a következő lépéssel.  

### <a name="step-3-ensure-that-the-date-and-time-are-set-correctly-on-your-computer"></a>3. lépés: Hogy a dátum és idő helyes beállításának ellenőrzése a számítógépen  

1.  Nyissa meg a Windows Defender vagy az Endpoint Protection.  

2.  Ha a kapott hibaüzenet a 0x80072f8f kódot tartalmazza, a problémát valószínűleg a számítógépen helytelenül beállított dátum vagy idő okozza.  

3.  A dátum és idő visszaállításához kövesse a [Hibás parancsikon, pontatlan rendszeridő, 0x80072f8f hibakód](http://go.microsoft.com/fwlink/?LinkId=155579) témakörben ismertetett lépéseket (http://go.microsoft.com/fwlink/?LinkId=155579).  

### <a name="step-4-rename-the-software-distribution-folder-on-your-computer"></a>4. lépés: A számítógépen a szoftverterjesztési mappa átnevezése  

1. Állítsa le az Automatikus frissítések szolgáltatást  

    1.  A **Start** menü keresőmezőjébe írja be a **services.msc**parancsot, majd kattintson az **OK**gombra.  

    2.  Kattintson a jobb gombbal az **Automatikus frissítések szolgáltatás**lehetőségre, majd a **Leállítás**lehetőségre.  

    3.  Tegye kis méretűvé a Szolgáltatások beépülő modult.  

2.  Nevezze át a **SoftwareDistribution** címtárat a következőképpen:  

    1.  A **Start** menü keresőmezőjébe írja be a  **cmd**parancsot, majd kattintson az **OK**gombra.  

    2.  Írja be a **cd %windir%**parancsot, majd nyomja le az **Enter**billentyűt.  

    3.  Írja be a **ren SoftwareDistribution SDTemp**parancsot, majd nyomja le az **Enter**billentyűt.  

    4.  Írja be a **exit**parancsot, majd nyomja le az **Enter**billentyűt.  

3.  Indítsa el az Automatikus frissítések szolgáltatást a következő módon:  

    1.  Tegye teljes méretűvé a Szolgáltatások beépülő modult.  

    2.  Kattintson a jobb gombbal az **Automatikus frissítések szolgáltatás**elemre, majd kattintson az **Indítás**lehetőségre.  

    3.  Zárja be a Szolgáltatások beépülő modul ablakát.  

### <a name="step-5-reset-the-microsoft-antivirus-update-engine-on-your-computer"></a>5. lépés: A számítógépen a Microsoft víruskereső-frissítési eszköz visszaállítása  

1.  A **Start** menü keresőmezőjébe írja be a  **cmd**parancsot, kattintson az **OK**gombra, majd a jobb gombbal kattintson a **Parancssor**elemre, és válassza a **Futtatás rendszergazdaként**lehetőséget.  

2.  Írja be az alábbi parancsokat a **Parancssor** ablakába, és az egyes parancsok után nyomja le az **Enter** billentyűt:  

     **CD-ről\\**  

     **CD program files\windows defender**  

     **Mpcmdrun - RemoveDefinitions-minden**  

     **Kilépés**  

3.  Indítsa újra a számítógépet.  

4.  Nyissa meg a Windows Defender vagy  
          Az Endpoint Protection, kattintson a **frissítés** fülre, majd **frissítés**.  

5.  Ha a probléma továbbra is fennáll, folytassa a következő lépéssel.  

### <a name="step-6-manually-install-the-virus-and-spyware-definition-updates"></a>6. lépés: A vírus- és kémprogram-definíciók frissítéseinek manuális telepítése  

-   Ha 32 bites Windows operációs rendszert futtat, a legújabb frissítéseket a [http://go.microsoft.com/fwlink/?LinkID=87342](http://go.microsoft.com/fwlink/?LinkID=87342) (http://go.microsoft.com/fwlink/?LinkID=87342) webhelyről töltheti le manuálisan.  

-   Ha 64 bites Windows operációs rendszert futtat, a legújabb frissítéseket a [http://go.microsoft.com/fwlink/?LinkID=87341](http://go.microsoft.com/fwlink/?LinkID=87341) (http://go.microsoft.com/fwlink/?LinkID=87341) webhelyről töltheti le manuálisan.  

-   Kattintson a **Futtatás**elemre. Megtörtént a legújabb frissítések manuális telepítése a számítógépre.  


### <a name="step-7-contact-support"></a>7. lépés: Forduljon a támogatási szolgálathoz  

-   Ha a fenti lépések nem oldották meg a problémát, vegye fel a kapcsolatot a támogatási szolgáltatással. További információk: [Ügyfélszolgálat](http://go.microsoft.com/fwlink/?LinkID=196174) (http://go.microsoft.com/fwlink/?LinkID=196174).  

##  <a name="starting-windows-defender-or-endpoint-protection-service"></a>A Windows Defender vagy az Endpoint Protection szolgáltatás elindítása  
 **Tünet**  

 Hibaüzenet jelenik meg, amely értesíti, hogy **a Windows Defender vagy az Endpoint Protection nem figyeli a számítógépet, mert a program szolgáltatása leállt. Most kell újraindítani.** 

 **Megoldás**  

### <a name="step-1-restart-your-computer"></a>1. lépés: Indítsa újra a számítógépet.  

-   Zárja be az összes alkalmazást, és indítsa újra a számítógépet.  

### <a name="step-2-make-sure-the-windows-defender-or-endpoint-protection-service-is-set-to-automatic-and-is-started"></a>2. lépés: Győződjön meg arról, hogy a "Windows Defender" vagy "Az Endpoint Protection szolgáltatás" automatikusra van beállítva, és elindult  

1.  A **Start** menü keresőmezőjébe írja be a **services.msc**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  Keressen rá a **Microsoft kártevőirtó szolgáltatás**kifejezésre. Kattintson rá a jobb gombbal, és válassza a **Tulajdonságok** lehetőséget, vagy kattintson rá duplán a szolgáltatás megnyitásához.  

3.  Győződjön meg róla, hogy az „**Indítási típus**” értéke „**Automatikus**”.  

4.  A **Start** gombra kattintva indítsa el a szolgáltatást. Ha a **Start** gomb nem érhető el, kattintson a **Leállítás** gombra, majd a **Start** gombra a szolgáltatás újraindításához.  

5.  A folyamat során megjelenő összes hibát jegyezze fel, küldjön egy esetet az online támogatás számára, és adja meg a hibákra vonatkozó információkat.  

### <a name="step-3-remove-any-existing-internet-security-programs"></a>3. lépés: A meglévő internetes biztonsági programok eltávolítása  

1.  A **Start** menü keresőmezőjébe írja be az **appwiz.cpl**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  A telepített programok listájából távolítsa el a harmadik felek internetes biztonsági programjait.*  

3.  Indítsa újra a számítógépet, majd próbálja meg telepíteni a Windows Defender vagy  
          Az Endpoint Protection újra.  

> [!NOTE]  
>  Egyes internetes biztonsági programokat nem lehet teljesen eltávolítani. Előfordulhat, hogy az előző biztonsági alkalmazás teljes eltávolításához le kell töltenie és futtatnia kell egy lemezkarbantartó segédprogramot.  

> [!CAUTION]  
>  Ha eltávolítja az internetes biztonsági programokat, a számítógép védtelenné válik. Ha problémába ütközik telepítése   
>       Az Endpoint Protection, miután eltávolította a meglévő internetes biztonsági programokat, forduljon a Windows Defender vagy  
>       Az Endpoint Protection támogatási által jelentse az esetet az online (további információkért lásd: [hogyan eset online bejelentése](http://www.microsoft.com/en-ph/security_essentials/Support/8c9074b6-1558-4d14-bc39-d294ced11096.aspx)).  

### <a name="step-4-uninstallreinstall-endpoint-protection"></a>4. lépés: Az Endpoint Protection eltávolítása/újratelepítése  

1.  A **Start** menü keresőmezőjébe írja be az **appwiz.cpl**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  A telepített programok listájában kattintson az **Endpoint Protection**elemre, majd távolítsa el.  

3.  Ha a rendszer kéri, indítsa újra a számítógépet, majd próbálja újból telepíteni az Endpoint Protection programot.  

##  <a name="internet-connection-issues"></a>Internetcsatlakozási problémák  
 Ahhoz, hogy a számítógépe megkapja a Windows Update legújabb frissítéseit, csatlakoznia kell az internethez.  

### <a name="step-1-verify-that-your-computer-is-connected-to-the-internet"></a>1. lépés: Győződjön meg arról, hogy a számítógép csatlakozik az internethez  

1.  A **Start**menü keresőmezőjébe írja be a **ncpa.cpl**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  Kattintson a jobb gombbal a kapcsolat nevére, majd kattintson az **Állapot**elemre.  

3.  Ha a számítógép csatlakoztatva van, a Windows XP rendszerben a kapcsolat állapota **Csatlakoztatva**, **Engedélyezett**vagy **Hitelesítés** sikeres értékű. Windows Vista és Windows 7 rendszerben az **IPv4** állapota **Internet**.  

4.  Ha nem úgy tűnik, hogy a számítógép csatlakoztatva lenne, kattintson a jobb gombbal a kapcsolat nevére, majd kattintson a **Csatlakozás**, **Engedélyezés**, **Hitelesítés**vagy **Javítás**elemre.  

### <a name="step-3-restart-your-computer"></a>3. lépés: Indítsa újra a számítógépet  

-   Zárja be a nyitott alkalmazásokat, és indítsa újra a számítógépet.  

### <a name="step-4-if-you-still-cant-connect-to-the-internet-check-your-connections"></a>4. lépés: Ha még nem csatlakozik az internethez, ellenőrizze a kapcsolatokat.  

1.  Ha telefonos kapcsolatot használ, győződjön meg arról, hogy a fali aljzat és a modem telefonkábeles kapcsolatai megfelelően illeszkednek.  

2.  Ha kábelmodemet használ, győződjön meg arról, hogy a modell kábeles kapcsolata és a modemtől a számítógépig érő kábeles kapcsolat megfelelően illeszkedik.  

3.  Ha kábelmodemet vagy DSL útválasztót használ, győződjön meg arról, hogy az útválasztó és a számítógép kapcsolatai megfelelően illeszkednek. Próbálja meg leválasztani és kikapcsolni az útválasztót és a modemet. Várjon néhány percig, először csatlakoztassa a modemet, várjon egy percig, majd csatlakoztassa az útválasztót, és indítsa újra a számítógépet.  

##  <a name="detected-threat-cant-be-remediated"></a>Észlelt fenyegetés helyrehozhatatlanok  
 Ha a Windows Defender vagy  
      Az Endpoint Protection egy tömörített fájl, .zip fájlnévkiterjesztéssel, vagy egy hálózati megosztásban rejtőző lehetséges veszélyforrást észlel, megkísérli annak karanténba helyezését vagy eltávolítását a fenyegetés kezelésére.  

### <a name="remove-or-scan-the-file"></a>A fájl eltávolítása vagy vizsgálata  

-   Ha a program a veszélyforrást egy .zip-fájlban észlelte, keresse meg a .zip-fájlt, majd távolítsa el, vagy vizsgálja meg jobb gombbal a fájlra kattintva és a **Vizsgálat a Windows Defender használatával** vagy a **Vizsgálat az Endpoint Protection használatával**lehetőséget választva. Ha a Windows Defender vagy az Endpoint Protection további veszélyforrásokat észlel a fájlban, értesítést küld róluk, és lehetővé teszi a megfelelő művelet kiválasztását.  

-   Ha a program a veszélyforrást egy hálózati megosztáson észlelte, keresse meg a hálózati megosztást, majd a jobb gombbal rákattintva és a **Vizsgálat a Windows Defender használatával** vagy a **Vizsgálat az Endpoint Protection használatával**lehetőséget választva vizsgálja meg. Ha a Windows Defender vagy az Endpoint Protection további veszélyforrásokat észlel a hálózati megosztásban, értesítést küld róluk, és lehetővé teszi a megfelelő művelet kiválasztását.  

-   Ha nem biztos a fájl eredetében, az egyik legjobb megoldás, ha teljes vizsgálatot hajt végre a számítógépen. A teljes vizsgálat elvégzése időigényes lehet, de lehetővé teszi, hogy a Windows Defender vagy az Endpoint Protection megkeresse a fertőzés forrását, és megtisztítsa tőle a számítógépet.  

##  <a name="install-the-endpoint-protection-client"></a>Az Endpoint Protection ügyfél telepítése  

> [!NOTE]  
>  A Windows Defender az operációs rendszerrel együtt települ a Windows 10 rendszerű számítógépeken.  

 **Tünetek**  

 A telepítés ismeretlen okból meghiúsul, vagy a rendszer a következő hibakódok egyikét tartalmazó hibaüzenetet küld: 0x80070643, 0X8007064A, 0x8004FF2E, 0x8004FF01, 0x8004FF07, 0x80070002, 0x8007064C, 0x8004FF00, 0x80070001, 0x80070656, 0x8004FF40, 0xC0000156, 0x8004FF41 0x8004FF0B, 0x8004FF11, 0x80240022, 0x8004FF04, 0x80070660, 0x800106B5, 0x80070715, 0x80070005, 0x8004EE00, 0x8007003, 0x800B0100, 0x8007064E vagy 0x8007007E.  

 Ha a számítógépén Windows XP Service Pack 2 (SP2) fut, a következő hibaüzenetek jelenhetnek meg (akár több is):  

-   Hiányzik egy szűrőkezelő összesítőcsomag, amelyre a telepítő varázslónak szüksége van a telepítés befejezéséhez.  

-   KB914882 telepítési hiba, A telepítő nem tudja frissíteni a Windows XP-fájlokat, mert a telepített rendszer nyelve eltér a frissítés nyelvétől.  

 **Ok**  

 Az Endpoint Protection nem telepíthető olyan számítógépre, amelyen más biztonsági programok is futnak. Egyes esetekben a biztonsági programok az eltávolításkor sem törlődnek teljesen. Az Endpoint Protection telepítéséhez eredeti Windows operációs rendszerrel kell rendelkeznie.  

 **Megoldás**  

> [!IMPORTANT]  
>  A probléma megoldása során újra kell indítania a számítógépet. Lássa el könyvjelzővel ezt az oldalt (jelölje meg Kedvencként), hogy könnyebben megtalálja a témakört, vagy nyomtassa ki az egyszerűbb használat érdekében.  

### <a name="step-1-remove-any-existing-security-programs"></a>1. lépés: A meglévő biztonsági programok eltávolítása  
**Az Endpoint Protection csak**

1.  Távolítsa el teljesen a meglévő internetes biztonsági programokat.  

2.  Indítsa újra a számítógépet.  

3.  Telepítse újra az Endpoint Protection szolgáltatást. Ha ez nem oldja meg a problémát, folytassa a következő lépéssel.  

### <a name="step-2-ensure-that-the-windows-installer-service-is-running"></a>2. lépés: Győződjön meg arról, hogy a Windows Installer szolgáltatás fut  

1.  A **Start** menü keresőmezőjébe írja be a **services.msc**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  Kattintson a jobb gombbal a **Windows Installer**elemre, majd kattintson az **Indítás**parancsra. Ha az **Indítás** lehetőség nem érhető el, a **Leállítás** és **Újraindítás** azonban igen, akkor a szolgáltatás már elindult.  

3.  A **Szolgáltatások** lap **Fájl** menüjében kattintson a **Kilépés**lehetőségre.  

4.  Kattintson a **Start** keresse meg a **parancssor**. Kattintson a jobb gombbal a **Parancssor**elemre, majd kattintson a **Futtatás rendszergazdaként**parancsra.  

5.  Írja be az **MSIEXEC /REGSERVER**parancsot, majd nyomja le az **Enter**billentyűt.  

    > [!NOTE]  
    >  A rendszer nem jelzi, hogy a parancs végrehajtása sikeres vagy sikertelen volt-e.  

6.  Telepítse újra az Endpoint Protection szolgáltatást. Ha ez nem oldja meg a problémát, folytassa a következő lépéssel.  

### <a name="step-3-start-windows-in-selective-startup-mode"></a>3. lépés: A Windows indítása szelektív indítási módban  

1.  A **Start** menü keresőmezőjébe írja be az **msconfig**parancsot, majd nyomja le az **Enter**billentyűt.  

2.  Kattintson az **Általános** lapon a **Szelektív indítás**lehetőségre, és törölje a jelölést az **Indítási elemek betöltése** opció jelölőnégyzetéből.  

3.  Jelölje be a **Szolgáltatások** lapon **Az összes Microsoft-szolgáltatás elrejtése** opció jelölőnégyzetét, majd törölje a jelölést a listában maradó összes szolgáltatás jelölőnégyzetéből.  

4.  Az **OK**, majd az **Újraindítás** gombra kattintva indítsa újra a számítógépet.  

5.  Próbálja újból telepíteni az Endpoint Protection szolgáltatást.  



### <a name="see-also"></a>További információ  
 [Endpoint Protection-ügyfél gyakran ismételt kérdések](../../protect/deploy-use/endpoint-protection-client-faq.md)   

 [Az Endpoint Protection-ügyfél súgója](../../protect/deploy-use/endpoint-protection-client-help.md)

