---
title: "UNIX/Linux-ügyfelek központi telepítése |} Microsoft Docs"
description: "Ismerje meg, hogyan kell telepíteni egy ügyfelet UNIX vagy Linux-kiszolgálóra a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 15a4e323-9f42-4fea-bb14-f2b905d1f77c
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d61d53daa5ef3d9c986cba8791d4471fea94d29d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-unix-and-linux-servers-in-system-center-configuration-manager"></a>Ügyfelek üzembe helyezése UNIX- és Linux-kiszolgálókon a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt a Linux vagy UNIX rendszerű kiszolgálón a System Center Configuration Managerrel, telepítenie kell a Configuration Manager-ügyfél Linux és UNIX rendszerű minden egyes Linux vagy UNIX-kiszolgálón. Az ügyfelet manuálisan is telepítheti az egyes számítógépekre, vagy héjparancsfájlt is használhat az ügyfél távoli telepítéséhez. A Configuration Manager támogatja a használatát az ügyfél leküldéses telepítését Linux vagy UNIX rendszerű kiszolgálókon. Az ügyfél Linux- vagy UNIX-kiszolgálókon való telepítésének automatizálásához Runbookot konfigurálhat a System Center Orchestratorben.  

 Az adott telepítési módtól függetlenül a telepítési folyamat kezeléséhez egy **install** nevű szkript szükséges. A parancsprogram a Linuxra és UNIX-ra készült ügyféllel együtt töltődik le.  

 A Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült telepítési parancsprogram támogatja a parancssori tulajdonságok. Vannak kötelező és nem kötelező parancssori tulajdonságok. Az ügyfél telepítésekor például meg kell adnia egy felügyeleti pontot arról a helyről, amelyet a Linux- vagy UNIX-kiszolgáló a hellyel történő első kapcsolatfelvételre használ. A parancssori tulajdonságok teljes listáját lásd: [Parancssori tulajdonságok az ügyfél Linux- és UNIX-kiszolgálókon történő telepítéséhez](#BKMK_CmdLineInstallLnUClient).  

 Az ügyfél telepítése után a Configuration Manager konzolon az ügyfélügynök konfigurálására a Windows rendszerű ügyfelek ugyanúgy az ügyfélbeállítások. További információ: [A Linux és UNIX rendszerű kiszolgálók ügyfélbeállításai](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ClientSettingsforLnU).  

##  <a name="BKMK_AboutInstallPackages"></a> Az ügyfél-telepítési csomagok és az univerzális ügynök  
 Ha telepíteni szeretné a Linuxra és UNIX-ra készült ügyfelet egy adott platformon, annak a számítógépnek megfelelő ügyfél-telepítési csomagot kell használnia, amelyen az ügyfelet telepíti. A [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkID=525184)letölthető ügyfelek a megfelelő ügyféltelepítési csomagot is tartalmazzák. Az ügyféltelepítési csomag mellett a letölthető ügyfél az **install** szkriptet is tartalmazza, amely felügyeli az ügyfél telepítését az egyes számítógépeken.  

 Az ügyfelek telepítéséhez a használt ügyfél-telepítési csomagtól függetlenül ugyanazt a folyamatot és parancssori tulajdonságokat használhatja.  

 További információ az operációs rendszerek, a platformok és a Linux és UNIX rendszerekhez készült Configuration Manager-ügyfél különböző kiadásai által támogatott ügyfél-telepítési csomagokról: [Linux és UNIX rendszerű kiszolgálók](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#linux-and-unix-servers).  

##  <a name="BKMK_InstallLnUClient"></a> Az ügyfél telepítése Linux- és UNIX-kiszolgálókon  
 Az ügyfél Linux- vagy UNIX-kiszolgálóra történő telepítéséhez egy parancsprogramot kell futtatnia minden egyes Linux vagy UNIX rendszerű számítógépen. A szkript neve **install** , és a telepítés folyamatát módosító, valamint az ügyféltelepítési csomagra hivatkozó parancssori tulajdonságokat támogatja. Az install parancsfájlnak és az ügyfél-telepítési csomagnak az ügyfélgépen kell lennie. Az ügyfél-telepítési csomag tartalmazza a Configuration Manager-ügyfél fájljait egy adott Linux vagy UNIX operációs rendszerhez és platformhoz.
Minden egyes ügyfél-telepítési csomag tartalmazza az összes szükséges fájlt az ügyfél telepítéséhez, és a Windows-alapú számítógépektől eltérően nem tölt le további fájlokat felügyeleti pontról vagy más forrásból.  

 Miután telepítette a Configuration Manager-ügyfél Linux és UNIX rendszerű, nem kell újraindítania a számítógépet. Amint a szoftver telepítése befejeződött, az ügyfél már működőképes is. Ha újraindítja a számítógépet, a Configuration Manager-ügyfél automatikusan újraindul.  

 A telepített ügyfél rendszergazdai hitelesítő adatokkal fut. A rendszergazdai hitelesítő adatok a hardver-leltározási adatok gyűjtéséhez és a szoftverek központi telepítéséhez szükségesek.  

 A parancs formátuma a következő:  

 **. / - felügyeleti csomag telepítése &lt;számítógép\> - sitecode &lt;Helykód\> &lt;tulajdonság #1 > &lt;tulajdonság #2 > &lt;ügyfél-telepítési csomag\>**  

-   Az**install** annak a szkriptfájlnak a neve, amely az ügyfél Linuxra és UNIX-ra való telepítését végzi. Ez a fájl megtalálható az ügyfélszoftverben.  

-   **-mp &lt;számítógép** a az ügyfél által használandó kezdeti felügyeleti pontot adja meg.  

     Például: smsmp.contoso.com  

-   **-sitecode &lt;Helykód\>**  határozza meg a helykódot, amely az ügyfél hozzá van rendelve.  

     Például: S01  

-   &lt;tulajdonság #1 > &lt;tulajdonság #2 > a telepítési parancsfájl használata a parancssori tulajdonságokat adja meg.  

    > [!NOTE]  
    >  További információ: [Parancssori tulajdonságok az ügyfél Linux- és UNIX-kiszolgálókon történő telepítéséhez](#BKMK_CmdLineInstallLnUClient)  

-   Az**ügyféltelepítési csomag** az adott operációs rendszerhez, verzióhoz és CPU-architektúrához tartozó ügyféltelepítési .tar-csomag neve. Az ügyfél-telepítési .tar-fájlt utolsóként kell megadni.  

     Példa: ccm-Universal-x64. &lt;build\>.tar  

###  <a name="BKMK_ToInstallLnUClinent"></a> A Configuration Manager-ügyfél telepítése Linux- és UNIX-kiszolgálókon  

1.  Windows-számítógép esetén [töltse le a megfelelő ügyfélfájlt a felügyelni kívánt Linux- vagy UNIX-kiszolgálóra](http://go.microsoft.com/fwlink/?LinkID=525184) .  

2.  Futtassa az önkicsomagoló .exe fájlt a Windows-számítógépen a telepítési parancsfájl és az ügyfél-telepítési .tar fájl kibontásához.  

3.  Másolja, majd illessze be az **install** szkriptet és a .tar-fájlt egy mappába a felügyelni kívánt kiszolgálón.  

4.  UNIX- vagy Linux-kiszolgáló esetén futtassa a következő parancsot a szkript programként történő futtatásának engedélyezéséhez: **chmod +x install**  

    > [!IMPORTANT]  
    >  Az ügyfél telepítéséhez rendszergazdai hitelesítő adatok használata szükséges.  

5.  Ezt követően a következő parancsot a Configuration Manager-ügyfél telepítéséhez: **. / - felügyeleti csomag telepítése &lt;állomásnév\> - sitecode &lt;kód\> ccm-Universal-x64.&lt; Build\>.tar**  

     A parancs beírásakor további parancssori tulajdonságok használatára is szükség lehet.  A parancssori tulajdonságok listájáért tekintse meg a [Parancssori tulajdonságok az ügyfél Linux- és UNIX-kiszolgálókon történő telepítéséhez](#BKMK_CmdLineInstallLnUClient)című témakört.  

6.  A szkript futtatását követően ellenőrizze a telepítést a **/var/opt/microsoft/scxcm.log** fájl megtekintésével. Ezenkívül ellenőrizheti, hogy az ügyfél telepítve és kommunikál a hellyel részleteinek megtekintése az ügyfél által a **eszközök** csomópontjának a **eszközök és megfelelőség** munkaterület a Configuration Manager konzolon.  

###  <a name="BKMK_CmdLineInstallLnUClient"></a> Parancssori tulajdonságok az ügyfél Linux- és UNIX-kiszolgálókon történő telepítéséhez  
 Az alábbi tulajdonságokkal tudja módosítani a telepítési szkript viselkedését:  

> [!NOTE]  
>  Használja a **-h** tulajdonságot a támogatott tulajdonságok megjelenítéséhez.  

-   **-mp &lt;kiszolgálójának teljes Tartományneve\>**  

     Kötelező. A teljes tartománynév alapján meghatározza azt a felügyeleti pontként működő kiszolgálót, amelyet az ügyfél első kapcsolati pontként fog használni.  

    > [!IMPORTANT]  
    >  A tulajdonsággal nem határozható meg, hogy az ügyfél a telepítést követően melyik felügyeleti ponthoz legyen rendelve.  

    > [!NOTE]  
    >  Ha az **-mp** tulajdonsággal olyan felügyeleti pontot ad meg, amely csak HTTPS-alapú ügyfélkapcsolatok fogadására van konfigurálva, akkor a **-UsePKICert** tulajdonságot is használnia kell.  

-   **-sitecode &lt;Helykód\>**  

     Kötelező. Adja meg a Configuration Manager ügyfél a Configuration Manager elsődleges hely.  

     Például: -sitecode S01  

-   **-fsp &lt;Kiszolgáló_teljes_tartományneve >**  

     Nem kötelező. A teljes tartománynévvel megadja azt a tartalék állapotkezelő pontot, amelyet az ügyfél az állapotjelző üzenetek küldésére használ.  

     További információ a tartalék állapotkezelő pontról: [A tartalék állapotkezelő pont szükségességének eldöntése](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#determine-if-you-need-a-fallback-status-point).  


-   **-dir &lt;könyvtár\>**  

     Nem kötelező. A Configuration Manager-ügyfél fájljainak telepítéséhez alternatív helyet határoz meg.  

     Alapértelmezés szerint az ügyfél a következő helyre lesz telepítve: **/opt/microsoft**.  

-   **-nostart**  

     Nem kötelező. Megakadályozza, hogy a Configuration Manager-ügyfélszolgáltatás automatikus elindítását **ccmexec.bin**, az ügyfél telepítésének befejezése után.  

     Az ügyfél telepítése után így manuális módszerrel kell elindítania az ügyfélszolgáltatást.  

     Alapértelmezés szerint az ügyfélszolgáltatás az ügyfél telepítését, illetve a számítógép újraindítását követően minden alkalommal elindul.  

-   **-clean**  

     Nem kötelező. Arra utasítja a telepítőt, hogy az új telepítés elindítása előtt távolítsa el a korábban telepített, Linuxra és UNIX-ra készült ügyfélhez kapcsolódó összes fájlt, Ezzel eltávolítja az ügyfél adatbázisát és tanúsítványtárolóját.  

-   **-keepdb**  

     Nem kötelező. Meghatározza, hogy a telepítő őrizze meg és használja fel újra az ügyfél helyi adatbázisát az ügyfél újratelepítésekor. Alapértelmezés szerint az ügyfél újratelepítésekor az adatbázis törlődik.  

-   **-UsePKICert &lt;paraméter\>**  

     Nem kötelező. Egy X.509 PKI-ügyféltanúsítvány teljes elérési útját és fájlnevét adja meg a szabványos nyilvános kulcsú tanúsítványok (PKCS #12) formátumában. A tanúsítvány az ügyfél hitelesítésére szolgál. Ha a telepítés során nincs megadva tanúsítvány, és egy új tanúsítvány hozzáadására vagy egy meglévő módosítására van szükség, használja a **certutil** segédprogramot. A certutil segédprogrammal kapcsolatos további információ: [Tanúsítványok kezelése a Linux és UNIX rendszerekhez készült ügyfélben](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts).  

     A **-UsePKICert**használatakor meg kell adnia a **-certpw** parancssori paraméter segítségével a PKCS#12-fájlhoz tartozó jelszót is.  

     Ha nem ad meg PKI-tanúsítványt ezzel a tulajdonsággal, abban az esetben az ügyfél önaláírt tanúsítványt használ, és a helyrendszerek felé minden kommunikáció HTTP-kapcsolaton keresztül zajlik.  

     A telepítő nem jelez hibát, ha érvénytelen tanúsítványt ad meg az ügyfél-telepítési parancssorban. Ennek az az oka, hogy a tanúsítvány ellenőrzése az ügyfél telepítése után történik. Ha az ügyfél elindul, a tanúsítványok érvényesítése a felügyeleti ponttal, és ha valamelyik tanúsítvány nem a következő üzenet jelenik meg **scxcm.log**, a Unix és Linux a Configuration Manager ügyfél naplófájlja: **Nem sikerült érvényesíteni a felügyeleti pont tanúsítványát**. A naplófájl alapértelmezett helye a következő:  **/var/opt/microsoft/scxcm.log**.  

    > [!NOTE]  
    >  Ezt a tulajdonságot akkor kell megadnia, ha ügyfelet telepít, és az **-mp** tulajdonsággal olyan felügyeleti pontot ad meg, amely csakis HTTPS-alapú ügyfélkapcsolatok fogadására van konfigurálva.  

     Példa: - UsePKICert &lt;teljes elérési út és fájlnév\> - certpw &lt;jelszó\>  

-   **-certpw &lt;paraméter\>**  

     Nem kötelező. A **-UsePKICert** tulajdonsággal megadott PKCS#12-fájlhoz tartozó jelszót határozza meg.  

     Példa: - UsePKICert &lt;teljes elérési út és fájlnév\> - certpw &lt;jelszó\>  

-   **-NoCRLCheck**  

     Nem kötelező. Arra utasítja az ügyfelet, hogy ne ellenőrizze a visszavont tanúsítványok listáját (CRL), amikor HTTPS-kapcsolaton keresztül kommunikál PKI-tanúsítvány használatával. Ha a kapcsoló nincs megadva, az ügyfél ellenőrzi a CRL-listát, mielőtt HTTPS-kapcsolatot létesítene PKI-tanúsítvánnyal. További információ az ügyfelek CRL-ellenőrzéséről: A PKI-tanúsítványok visszavonásának tervezése.  

     Példa: - UsePKICert &lt;teljes elérési út és fájlnév\> - certpw &lt;jelszó\> - NoCRLCheck  

-   **-rootkeypath &lt;fájl helye\>**  

     Nem kötelező. Megadja a teljes elérési útja és a fájl nevét a Configuration Manager megbízható legfelső szintű kulcsot. A Configuration Manager megbízható legfelső szintű kulcs egy módszert kínál, amely Linux és UNIX rendszerű ügyfelek használatával győződjön meg arról, hogy a megfelelő hierarchiához tartozó helyrendszerhez kapcsolódnak-e.  

     Ha nem adja meg a megbízható legfelső szintű kulcsot a parancssorban, az ügyfél megbízhatónak fogja tartania az első felügyeleti pontot, amellyel kommunikál, és automatikusan erről a felügyeleti pontról fogja lekérni a megbízható legfelső szintű kulcsot.  

     További információk: [A megbízható legfelső szintű kulcs tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

     Példa: - rootkeypath &lt;teljes elérési út és fájlnév\>  

-   **-httpport &lt;port\>**  

     Nem kötelező. Meghatározza azt a portot, amelyet az ügyfél a felügyeleti pontokon használ, amikor HTTP-kapcsolaton keresztül kommunikál velük. Ha a port nincs megadva, a 80-as alapértelmezett érték lesz érvényben.  

     Példa: -httpport 80  

-   **-httpsport &lt;port\>**  

     Nem kötelező. Meghatározza azt a portot, amelyet az ügyfél a felügyeleti pontokon használ, amikor HTTPS-kapcsolaton keresztül kommunikál velük. Ha a port nincs megadva, a 443-as alapértelmezett érték lesz érvényben.  

     Példa: - UsePKICert &lt;teljes elérési útja és a tanúsítvány neve\> - httpsport 443  

-   **-ignoreSHA256validation**  

     Nem kötelező. Arra utasítja az ügyfél telepítőjét, hogy hagyja ki az SHA-256 algoritmussal történő ellenőrzést. Akkor használja ezt a kapcsolót, ha az ügyfelet olyan operációs rendszeren telepíti, amelyhez nem tartozik az SHA-256 algoritmust támogató OpenSSL-verzió. További információk: [Az SHA-256 algoritmust nem támogató Linux- és UNIX-alapú operációs rendszerek](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_NoSHA-256).  

-   **-signcertpath &lt;fájl helye\>**  

     Nem kötelező. Megadja a helykiszolgáló exportált, önaláírt tanúsítványának teljes elérési útját és a **.cer** -fájl nevét. Ha nem érhetők el PKI-tanúsítványokat, a Configuration Manager helykiszolgálón, az automatikusan önaláírt tanúsítványokat hoz létre.  

     Ezek a tanúsítványok annak ellenőrzésére szolgálnak, hogy a felügyeleti pontról letöltött ügyfélházirendek a megfelelő helyről érkeztek-e. Ha a telepítés során nem adta meg, vagy meg kell változtatnia az önaláírt tanúsítványt, használja a **certutil** segédprogramot. A certutil segédprogrammal kapcsolatos további információ: [Tanúsítványok kezelése a Linux és UNIX rendszerekhez készült ügyfélben](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts).  

     Ez a tanúsítvány az **SMS** tanúsítványtárolóból kérhető le, a tulajdonos neve **Helykiszolgáló** , a rövid neve pedig **Helykiszolgáló aláíró tanúsítványa**.  

     Ha ez a kapcsoló nincs megadva a telepítés során, a Linuxra vagy UNIX-ra készült ügyfél megbízhatónak fogja tartani az első felügyeleti pontot, amellyel kommunikál, és automatikusan erről a felügyeleti pontról fogja lekérni az aláíró tanúsítványt.  

     Példa: - signcertpath &lt;teljes elérési útja és neve\>  

-   **-rootcerts**  

     Nem kötelező. További olyan importálandó PKI-tanúsítványokat ad meg, amelyek nem tartoznak a felügyeleti pontok hitelesítésszolgáltatói hierarchiájába. Ha több tanúsítványt ad meg a parancssorban, vesszővel válassza el őket.  

     Akkor használja ezt a kapcsolót, ha olyan PKI-ügyféltanúsítványokat használ, amelyek nincsenek hozzákapcsolva a hely felügyeleti pontjain megbízhatónak minősülő hitelesítésszolgáltatói főtanúsítványhoz. Felügyeleti pontok fogják utasítani az ügyfelet, ha az ügyféltanúsítvány nincs hozzákapcsolva a hely tanúsítványkibocsátói listájában megbízható főtanúsítványt.  

     Ha nem használja ezt a kapcsolót, a Linuxra vagy UNIX-ra készült ügyfél csak a **-UsePKICert** kapcsolóval megadott tanúsítvány segítségével fogja ellenőrizni a bizalmi hierarchiát.  

     Példa: - rootcerts &lt;teljes elérési útja és neve\>,&lt;teljes elérési útja és neve\>  

###  <a name="BKMK_UninstallLnUClient"></a> Az ügyfél eltávolítása Linux- és UNIX-kiszolgálókról  
 A Linux és UNIX rendszerű segédprogramot, használja a Configuration Manager-ügyfél eltávolításához **Eltávolítás**. Alapértelmezés szerint ez a fájl az ügyfélszámítógép **/opt/microsoft/configmgr/bin/** mappájában található. Az uninstall parancs nem támogatja a parancssori paraméterek használatát, és az ügyfélszoftverhez kapcsolódó valamennyi fájlt eltávolítja a kiszolgálóról.  

 Az ügyfél eltávolításához használja a következő parancssort: **/opt/microsoft/configmgr/bin/uninstall**  

 Nem kell újraindítania a számítógépet, a Configuration Manager-ügyfél Linux és UNIX rendszerű eltávolítása után.  

##  <a name="BKMK_ConfigLnUClientCommuincations"></a> Kérelemportok konfigurálása a Linux- és UNIX-ügyfélhez  
 A Windows-alapú ügyfelekhez hasonlóan, a Configuration Manager-ügyfél Linux és UNIX rendszerű HTTP és HTTPS való kommunikációra használja a Configuration Manager-helyrendszerekkel. A Configuration Manager-ügyfél való kommunikációhoz használt portokat a kérelmek portjait nevezzük.  

 Telepítésekor a Configuration Manager-ügyfél Linux és UNIX rendszerű ügyfelek alapértelmezett kérelemportjainak megadásával módosíthatja a **- httpport** és **- httpsport** telepítési tulajdonságokat. Ha nem adja meg a telepítési tulajdonságot egy egyéni értékkel, az ügyfél az alapértelmezett értékeket fogja használni. Az alapértelmezett érték HTTP-forgalom esetében **80** , HTTPS-forgalom esetében **443** .  

 Az ügyfél telepítése után a kérelemport konfigurációja már nem módosítható. A portkonfiguráció módosításához újra kell telepítenie az ügyfelet, és meg kell adnia az új portkonfigurációt. Amikor a portszámok módosítása céljából telepíti újra az ügyfelet, az új ügyfelek telepítéséhez hasonló módon futtassa az **install** parancsot, de használja még a **-keepdb**parancssori tulajdonságot is. Ez a kapcsoló arra utasítja a telepítőt, hogy őrizze meg az ügyfél adatbázisát és fájljait, köztük a GUID azonosítót és a tanúsítványtárolót is.  

 További információ az ügyfél kommunikációs portjainak számáról: [Az ügyfélszoftverek kommunikációjához használt portok konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-communication-ports.md).  

##  <a name="BKMK_ConfigClientMP"></a> A Linuxra és UNIX-ra készült ügyfél konfigurálása a felügyeleti pontok megtalálásához  
 Linux és UNIX rendszerekhez készült Configuration Manager-ügyfél telepítésekor kezdeti kapcsolati pontként felügyeleti pontot kell megadnia.  

 A Configuration Manager-ügyfél Linux és UNIX rendszerű felveszi a kapcsolatot a felügyeleti pont az ügyfél telepíti egyidejűleg. Ha az ügyfél nem tud kapcsolódni a felügyeleti ponthoz, az ügyfélszoftver addig próbálkozik újra, amíg sikerrel nem jár.  

 További információ arról, hogyan találnak az ügyfelek felügyeleti pontokat: [Felügyeleti pontok megtalálása](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points).

