---
title: "A Technical Preview-ban 1605 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1605 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 8b3d472c586e704ee48e9825138c72f655d89492
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>A rendszer 1605 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1605 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

 **A Technical Preview kiadással kapcsolatos ismert problémák:**  

-   A Technical Preview 1605 Ha a felügyeleti pont tulajdonságainak frissítéséhez, a telepítés után jelenhet meg a konzol hiba, amely arra kényszeríti a konzol bezárásához.  Ha ez történik, távolítsa el a felügyeleti pont, és telepítse újra a felügyeleti pont használatával a kívánt beállításokat. Alternatív megoldásként a felügyeleti pont Technical Preview 1605 telepítése előtt módosíthatja.  

-   Ha a Technical Preview 1604 az üzleti szolgáltatás a Windows áruház használja, majd frissítsen a Technical Preview 1605, a bevezetési adatokat már nem tekintheti meg. Minden más funkcionálisan továbbra is működik. Ha Ön előkészítve a Technical Preview 1604 rendelkező, marad, előkészítve technikai előzetes 1605 telepítése, és semmilyen további műveletet kell tenniük után.  

 **Új funkciókat próbálhatja ki ebben a következők:**  

##  <a name="BKMK_PerAppVPN"></a>Alkalmazásonkénti VPN Windows 10-eszközök  
 Windows 10-es eszközök felügyelete a Configuration Managerbe integrált Intune használata esetén adja hozzá azokat az alkalmazásokat, amelyek automatikusan meg, amelyet a Configuration Manager felügyeleti konzol segítségével konfigurált VPN-kapcsolat. Lehetősége van a VPN-forgalmát korlátozása alkalmazásokra, vagy továbbra is az összes forgalom a VPN-kapcsolaton keresztül.  

 **Követelmények**:  

-   A Configuration Manager Intune-nal  

-   Legalább egy eszköz a telepített Windows 10 VPN-profil  

##  <a name="BKMK_InstallSU"></a>A telepítés szoftver frissítések feladatütemezés fejlesztései  
 A következő fejlesztéseken ment a szoftverfrissítések telepítése feladatütemezés:  

-   Új feladatütemezési változót, SMSTSSoftwareUpdateScanTimeout, így a időtúllépés történt a szoftverfrissítési keresés vezérelhetik a telepítés szoftver frissítések feladatütemezési lépés során érhető el. Az alapértelmezett érték 30 perc.  

-   Továbbfejlesztett naplózás törölték. Az smsts.log naplófájl más naplófájlokat, amelyek segítséget nyújtanak a szoftverfrissítés-telepítési folyamata során elhárítása hivatkozó új naplóbejegyzések fogja tartalmazni.  

##  <a name="BKMK_PrepareConfigMgrClient"></a>Rögzítése feladatütemezési lépés készítse elő a ConfigMgr-ügyfél fejlesztései  
 A ConfigMgr-ügyfél előkészítése a lépést most is teljesen eltávolítja a Configuration Manager-ügyfél csak a fontos információk eltávolítása helyett. Ha a feladatütemezés a rögzített operációsrendszer-lemezképet telepíti azt telepíti egy új Configuration Manager-ügyfél minden alkalommal.  

##  <a name="BKMK_Grace"></a>Kötelező alkalmazások központi telepítése a türelmi időszak  
 Bizonyos esetekben célszerű minden konfigurált határidők túl alkalmazástelepítések telepítése több időt hagy a felhasználók. Például ha a felhasználó csak adott vissza a szabadsága, előfordulhat, hogy rendelkeznek long vár, amíg a lejárt alkalmazásként telepíti a központi telepítések. Ezek azonban továbbra is azonnal telepítheti az alkalmazást szeretnék bármikor.  

 Ez a probléma megoldásához most definiálhat egy **türelmi időszak** Configuration Manager ügyfél beállítások telepítésével egy gyűjteményhez.  

 A türelmi időszak konfigurálásához hajtsa végre a következő műveleteket:  

1.  Az a **Számítógépügynök** lap, az ügyfélbeállítások konfigurálása az új tulajdonság **türelmi idő a kényszerítésre a telepítés utáni határidő (óra)** közötti értékű **1** és **120** óra.  

2.  Az új alkalmazástelepítés, vagy egy meglévő központi telepítési tulajdonságai a a **ütemezés** lapon, a jelölőnégyzet bejelölésével **felhasználói beállítások szerint a telepítés kényszerítésének késleltetés**, legfeljebb az ügyfélbeállításokban meghatározott türelmi időszak.  

     Minden, a jelölőnégyzet, kijelölve, és amely, amelyen szintén telepítve az ügyfél-eszközbeállítást eszközökre irányuló telepítést fogja használni a türelmi időszak.  

 Ebben a kiadásban a türelmi időszak konfigurálása ügyféleszközökön nem használja. Konfigurálja a türelmi időszak, és jelölje be a jelölőnégyzetet, ha az alkalmazás az első nem üzleti ablak, amely a felhasználó konfigurált határidő után lesznek telepítve.  

 Hasonló beállítások érhetőek el a szoftverfrissítések központi telepítési varázsló, az automatikus központi telepítési szabályok varázslóban és a Tulajdonságok lap. Azonban ezek jelenleg nem használhatók a technical Preview.  

##  <a name="BKMK_Remote"></a>Új élmény a távoli eszközök műveletei  
 Javult a felhasználói élmény a távoli eszközök műveletei végrehajtásához a Configuration Manager konzoljáról.  
Gyakori műveleteket, mint **eltávolítási és törlési**, **új PIN-kód**, **távoli zárolás**, és **az aktiválási zár megkerülése** most már megtalálható a **távoli eszközök műveletei** menüjéből érhető el a **eszközök és megfelelőség** munkaterületen.  

 ![Új távoli eszközök műveletei képernyőképe](media/New-Remote-Device-Actions.png)  

 Az állapot az egyes ezeket a műveleteket a következő helyen található:  

-   A részleteket tartalmazó ablaktáblán, ha kijelöl egy eszközt a a **eszközök** csomópont.  

-   Az a **tulajdonságok** lap egy eszköz számára.  

-   A fő lapján a **eszközök** csomópont (nem minden oszlopa is láthatják őket alapértelmezés szerint).  

 IOS aktiválási zár megkerülésének kapcsolatos további információkért lásd: [az iOS-eszközök aktiválási zár megkerülésével a Configuration Manager védelme](/sccm/mdm/deploy-use/manage-ios-activation-lock), különösen a **a Configuration Manager Technical Preview-megkerülés jelenlegi ismert problémák az aktiválási zár** szakasz.  

##  <a name="BKMK_WSFB"></a>Üzletági alkalmazások a Windows áruházban  
 A [vállalati Windows áruház](https://www.microsoft.com/business-store) hol található, és alkalmazásokat vásárolhat a szervezete számára egyenként vagy nagyobb mennyiségben. Ha összekapcsolja az áruházat a Configuration Manager, kezelheti mennyiségi programban vásárolt alkalmazásokat a Configuration Manager konzolról, például:  

-   Szinkronizálhatja a megvásárolt alkalmazások listáját a Configuration Managerrel  

-   A szinkronizált alkalmazások megjelennek-e a Configuration Manager konzolon, és telepítheti őket a többi alkalmazáshoz hasonlóan  

-   24 óránként, a Configuration Manager alkalmazás licencelési információkat letölti a tárolóból, és tekintse át ennek a Configuration Manager konzolon  

 A 1604 technikai előzetes kiadásaiban sikerült szinkronizálása és a vállalati Windows áruházból származó alkalmazások megtekintése a Configuration Manager konzolon. Ebben a kiadásban jelentek meg a szinkronizált áruházbeli alkalmazások Configuration Manager-alkalmazások létrehozása és telepítése lehetőséget.  

### <a name="set-up-windows-store-for-business-synchronization"></a>Üzleti szinkronizálási Windows áruház beállítása  

1.  Az Azure Active Directoryban regisztrálja a Configuration Manager "Web Application and/or Web API" felügyeleti eszközként. Ekkor kap egy ügyfél-Azonosítót, amely később szüksége lesz.  

    1.  Az Active Directory csomópontjában [https://manage.windowsazure.com](https://manage.windowsazure.com), válassza ki az Azure Active Directoryban, majd kattintson a **alkalmazások** > **Hozzáadás**.  

    2.  Kattintson a **a szerveztem által fejlesztett alkalmazás hozzáadása**.  

    3.  Adjon meg egy nevet az alkalmazásnak, válassza a **webes alkalmazás** és/vagy **Web API**, majd kattintson a **tovább** nyílra.  

    4.  Adja meg az URL-CÍMÉRE mind a **bejelentkezési URL-cím** és **App ID URI**. Az URL bármi lehet, és nem kell valódi címre mutatnia. Megadhat például **https://&lt;tartomanynev > / sccm**.  

    5.  Fejezze be a varázslót.  

2.  Az Azure Active Directoryban hozzon létre egy ügyfélkulcsot a regisztrált felügyeleti eszközhöz.  

    1.  Jelölje ki az imént létrehozott alkalmazást, majd kattintson **konfigurálása**.  

    2.  A **kulcsok**, válasszon egy időtartamot a listából, és kattintson a **mentése**. Ezzel létrehoz egy új ügyfélkulcsot. Ne lépjen ki erről az oldalról, amíg sikeresen vállalati a Configuration Manager előkészítve a Windows áruház.  

3.  A vállalati Windows áruházban konfigurálja a Configuration Manager áruházi kezelőeszközként.  

    1.  Nyissa meg [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools) és jelentkezzen be a kérésre.  

    2.  Ha szükséges, fogadja el a használati feltételeket.  

    3.  A **kezelőeszközök**, kattintson a **felügyeleti eszköz hozzáadása**.  

    4.  A **keressen rá név szerint az eszköz**, írja be a korábban létrehozott az aad-ben az alkalmazás nevét, majd kattintson a **Hozzáadás**.  

    5.  Kattintson a **aktiválás** imént importált alkalmazás neve mellett.  

    6.  Az a **offline licencelt alkalmazások** varázsló, kattintson a **Igen** Ha azt szeretné, hogy az offline licencelt alkalmazások vásárlását.  

4.  Vásároljon legalább egy alkalmazást a vállalati Windows áruházban.  

5.  A a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **Cloud Services**, majd kattintson a **a vállalati Windows áruházban.**  

6.  Az a **Home** lap a **létrehozása** csoportjában kattintson a **hozzáadása a Windows áruház-fiók üzleti**.  

7.  A bérlő azonosítója, az ügyfél-azonosító és az ügyfél kulcs hozzáadása az Azure Active Directoryból, majd fejezze be a varázslót.  

8.  Ha elkészült, látni fogja a beállított fiók megjelenik a **Windows Áruházbeli fiókok üzleti** lista a Configuration Manager konzolon.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja meg végrehajtani a következő feladatot, és tudassa velünk, milyen eredménnyel járt keresztül elérhető visszajelzési űrlapra a [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) oldalon, a Microsoft Connect webhelyen:  

 Létrehozhat és telepíthet a Configuration Manager-alkalmazás a Windows áruházból üzleti offline licencelt alkalmazások.  

1.  Az a **szoftverkönyvtár** a Configuration Manager konzol munkaterületén bontsa ki a **Alkalmazáskezelés**, majd kattintson a **Áruházbeli alkalmazások Licencadatai**.  

2.  Válassza ki a kívánt alkalmazást, telepíti, ezt követően a a **Home** lap a **létrehozása** csoportjában kattintson a **alkalmazás létrehozása**.  

 Configuration Manager-alkalmazás jön létre, amely tartalmazza a Windows Áruházbeli alkalmazás. Ezután telepítheti és figyelheti az alkalmazás, mint bármely más Configuration Manager-alkalmazás.  

> [!IMPORTANT]  
>  Ha a Configuration Manager-alkalmazás az offline licencelt alkalmazásra egyetlen központi telepítési típust hoz létre, ez rendelkező MDM által felügyelt és a Configuration Manager-ügyfél is kezelt eszközökre is telepíthető. Ha több központi telepítési típust az alkalmazás telepítése, a telepítés sikertelen lesz.  
>   
>  Jelenleg nem telepíthet Configuration Manager online licencelt alkalmazások.  

##  <a name="BKMK_VPP2"></a>Általános fejlesztések a mennyiségi programban vásárolt alkalmazások  

-   Ebben a kiadásban, a vállalati Windows áruházból mennyiségi programban vásárolt alkalmazásokat és az iOS app store ugyanazt a nézetet, az engedélyezés **tárolására alkalmazások Licencadatai**.  

-   Mennyiségi programban vásárolt iOS alkalmazások esetén az Apple Volume Purchase Program lapon el lett távolítva a **alkalmazáscsomag az iOS böngészőhöz** párbeszédpanel az alkalmazás létrehozása varázslóban. Egy mennyiségi programban vásárolt iOS-alkalmazás létrehozásához használja az alábbi lépéseket:  

    1.  1.  Az a **szoftverkönyvtár** a Configuration Manager konzol munkaterületén bontsa ki a **Alkalmazáskezelés**, majd kattintson a **Áruházbeli alkalmazások Licencadatai**.  

    2.  2.  Válassza ki a kívánt alkalmazást, telepíti, ezt követően a a **Home** lap a **létrehozása** csoportjában kattintson a **alkalmazás létrehozása**.  

-   Az beszerzése és feltöltése az Apple VPP-token a mennyiségi programban vásárolt alkalmazásokat a Configuration Manager konzol segítségével helye megváltozott. Most ezt megteheti a **Admin** munkaterület a **Felhőszolgáltatások** > **Apple Volume Purchase Program-tokenek** csomópont.  

##  <a name="BKMK_VPP"></a>Enterprise Data Protection (EDP)  
 Konfigurációelemek, amelyek lehetővé teszik a nagyvállalati adatvédelmi (EDP) szabályzatok, és válassza ki a védett alkalmazások, az EDP-védelmi szintek és a vállalati adatokat a hálózaton található, így például telepítése is létrehozhat. EDP kapcsolatos további információkért lásd a következő témaköröket:  

-   [Enterprise data protection (EDP) használatával vállalati adatok védelme](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [Hozzon létre, és a System Center Configuration Manager enterprise data protection (EDP) házirend telepítése](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a>A végfelhasználók is telepíthet alkalmazásokat a vállalati portálról  
 A helyszíni MDM jelent a System Center Configuration Manager 1511-es verzió. A korábbi verziókban az MDM által felügyelt Windows 10-eszközökön a központi telepítési céllal telepíthet **szükséges** telepítés helyszíni MDM által felügyelt eszközök számára.  

 Ebben a kiadásban, mostantól telepíthet alkalmazásokat a központi telepítési céllal **elérhető** felhasználója számára a helyszíni MDM által felügyelt Windows 10-es számítógépeken, és a felhasználók most már telepítheti ezeket az alkalmazásokat magukat a vállalati portálról.
Ez a technical preview a vállalati portál nyitva, több mint 15 percig, ha a végfelhasználó jelenik meg hibaüzenet. A probléma megoldása érdekében indítsa újra a vállalati portálon.  

### <a name="before-you-start"></a>Előkészületek  

#### <a name="server-prerequisites"></a>Server rendszerrel kapcsolatos előfeltételek  

-   .NET 4.5-ös vagy újabb rendszer (újraindítást igényel)  

-   A PowerShell 3.0 konfigurációs parancsprogram (újraindítást igényel)  

#### <a name="client-prerequisites"></a>Ügyfél előfeltételei  

-   Windows 10 1511-es asztali (OS build 10586.218) vagy újabb verzió  

#### <a name="general-prerequisites"></a>Általános előfeltételek  

-   Győződjön meg arról, hogy végrehajtotta a [előkészítő lépések helyszíni mobileszközök kezeléséhez](https://technet.microsoft.com/library/mt613153.aspx) és [az eszközök regisztrálását](https://technet.microsoft.com/library/mt627870.aspx).  

-   A legjobb alkalmazás telepítése élmény a vállalati portál használata esetén, győződjön meg arról, hogy a Configuration Manager aktív kapcsolat a Microsoft Intune.  

-   Ha a tömeges-beiktatási beállítást választja, konfigurálhatja a regisztrált eszköz felhasználó-eszköz kapcsolat előtt ebben a forgatókönyvben.  

### <a name="configuration-steps"></a>Konfigurációs lépés  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>Az Alkalmazáskatalógus szerepkör telepítését és a mobileszköz-felügyelet támogatásának engedélyezése  

1.  Az Alkalmazáskatalógus webszolgáltatás és a webhely szerepkörök hozzáadása  

    1.  Válassza ki **HTTPS mód** és a **mobileszközök használja ezt az Alkalmazáskatalógus webszolgáltatás pontot** lehetőséget.  

    2.  Ez a Technical Preview korlátozások:  

        -   A mobileszközök csatlakozni a beállítás kiválasztása előtt el kell távolítania minden meglévő Alkalmazáskatalógus szerepköröket.  

        -   Ellenőrizze, hogy csak egy készletét Alkalmazáskatalógus szerepköröket, és a szerepkörök közös találhatók a beléptetési pont és beléptetési Proxy pont szerepköre ugyanarra a hely rendszerre.  

2.  Ellenőrizze, hogy a következő összetevők működési a Configuration Manager konzol összetevő-állapot csomópontján:  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>Határok konfigurálása  
 A terjesztési pont csak intranetes szükséges határok konfigurálása.  

> [!NOTE]  
>  Csak IPv4-tartományok határait mobileszköz-kezelés most támogatottak.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>Telepítse a vállalati portál alkalmazás és a konfiguráció  

1.  A technical preview konfigurációs parancsprogramja segítségével készítse elő a vállalati portál központi telepítése és konfigurálása:  

    1.  Egy rendszergazda jogú PowerShell-parancsablak megnyitása.  

    2.  Futtatás **set-executionPolicy RemoteSigned**  

    3.  A mappából  **&lt;SCCM telepítőkönyvtár\>\cd.latest\SMSSETUP\TOOLS\MDM** futtatása **.\ConfigurationScript.ps1**  

     A konfigurációs parancsfájl a következőket teszi:  

    1.  A Windows alkalmazás központi telepítési típus használatával hoz létre a Configuration Manager-alkalmazás **CompanyPortalOnPremisesMDM.appx** ugyanabban a mappában.  

    2.  Létrehoz egy konfigurációelemet és alapkonfigurációt, amely beállítja a vállalati portál.  

    3.  Mind a referenciakonfigurációt, és az alkalmazás központi telepítését, és hozzáadja az alkalmazás összes terjesztési pontra.  

    > [!NOTE]  
    >  Ha az Alkalmazáskatalógus szerepköröket nem közös helyen az elsődleges hellyel, hajtsa végre a következő műveleteket:  
    >   
    >  -   Az a **eszközök és megfelelőség** munkaterületen keresse meg a **OnPremMDM portál konfigurációs CI - kiszolgáló URL-címei** konfigurációs elem  
    > -   Módosítsa a **megfelelőségi szabályok** érték a teljes tartománynévvel a helyrendszer az Alkalmazáskatalógus szerepköröket hol találhatók.  

2.  A vállalati portál alkalmazás és konfigurációja vannak telepítve, ellenőrizze az alkalmazás és a konfigurációs alaptervhez megfelelőek az adott eszköz használatára vonatkozó **központi telepítések** szakasz a Configuration Manager konzol. A vállalati portálon jelenik meg **vállalati portál (Technical Preview-ban)** a Start menüben, az eszközön.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja meg a következő feladatok végezhetők, és tudassa velünk, milyen eredménnyel járt keresztül elérhető visszajelzési űrlapra a [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) oldalon, a Microsoft Connect webhelyen:  

1.  Támogatott központi telepítési típusok több alkalmazások központi telepítését a központi telepítési céllal felhasználógyűjteményekre **elérhető**. A jelen technikai előzetes a rendszergazdai jóváhagyást igénylő alkalmazások nem támogatottak, és a vállalati portálon nem lesznek megjelenítve.  

2.  Felhasználók is, majd tallózással keresse meg és telepíthet alkalmazásokat a vállalati portálról.  

     Után, nyissa meg a vállalati portált, megjelenik egy párbeszédpanel nevű **System Center Configuration Manager** adja meg a felhasználó Active Directory hitelesítő adatok (vagy formájában user@domain vagy tartomány\felhasználó) a bejelentkezéshez.  

##  <a name="BKMK_SW1"></a>A frissítések és az operációs rendszerek a Szoftverközpont új lapok  
 Ebben a kiadásban a következő módosítások lettek bevezetve azzal, hogy a Szoftverközpont alkalmazás javítása érdekében:  

-   A **alkalmazások** lap felosztása a három különálló lap **frissítések**, **operációs rendszerek** (amely mindkét korábban találhatók a **szűrők** lista), és **alkalmazások**.  

##  <a name="BKMK_ServerGroups"></a>A kiszolgálócsoport szolgáltatás  
 Technical Preview-ban a System Center Configuration Manager, 1511-es verziójában hozzon létre egy gyűjteményt, ahol a gyűjteményben található összes eszköz alkotó-e a csoport olyan tartalmazza. Ezután sikerült server csoporthoz tartozó vezérlőelem százalékos aránya a számítógépekre, amelyek egy adott időpontban szoftverfrissítések telepítésekor használhat csoport beállításainak konfigurálása, és konfigurálja a központi telepítés előtti és utáni PowerShell-parancsfájlokat egyéni műveletek futtatása.  

 Technical Preview-ban a System Center Configuration Manager, a verzió 1605, hozzáadja a számítógép a kiszolgálót, hogy Ön meghatározását, hozzáadja a számítógépek állapotának megtekintése a kiszolgálócsoport fokozott ellenőrzés és lehetővé teszi a telepítési zárolásait, amely akkor hasznos, ha az ügyfelek telepíthetik a szoftverfrissítéseket nem sikerült, és megakadályozzák, más ügyfelek a szoftverfrissítések telepítése után megadott sorrendben frissítése.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja meg a következő feladatok végezhetők, és tudassa velünk, milyen eredménnyel járt keresztül elérhető visszajelzési űrlapra a [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) oldalon, a Microsoft Connect webhelyen:  

-   Képes vagyok létrehozni egy gyűjteményt, amely a csoport jelöli. A teszteléshez konfigurálhatja a gyűjteménytagsági szabályokat, hogy a gyűjtemény 2 számítógépet tartalmazzon.   

-   Képes vagyok meghatározni, hogy a számítógép a kiszolgáló szoftverfrissítések telepítése a beállítások a gyűjtemény alapján meghatározott sorrendben. Az eljárás mintaparancsfájljainak segítségével megadhatja a központi telepítés előtti és utáni parancsfájlokat.  

-   Képes vagyok központilag telepíteni egy szoftverfrissítést a gyűjteményhez. Tekintse át a start.txt és az end.txt (létrehozott fájlokat a minta parancsfájlok alapján) a C:\temp, és a központi telepítést a számítógép a kiszolgálón a kezdő és záró időpontjának ellenőrzéséhez. Tekintse át az UpdatesDeployment.log fájlt további információt.  

#### <a name="to-create-a-collection-for-a-server-group"></a>A kiszolgáló csoport gyűjtemény létrehozása  

1.  [Hozzon létre egy eszközgyűjteményt](https://technet.microsoft.com/library/gg712295.aspx) , amely tartalmazza a számítógép a kiszolgálón.  

2.  Az a **eszközök és megfelelőség** munkaterületet, kattintson a **Eszközgyűjtemények**, kattintson a jobb gombbal a számítógép a kiszolgáló tartalmazó gyűjteményt, és kattintson a **tulajdonságok**.  

3.  Az a **általános** csoportjában válassza **minden eszköz a azonos kiszolgálói csoport részét képező**, és kattintson a **beállítások**.  

4.  Az a **kiszolgálói csoportbeállításokat** csoportjában adja meg a következő beállítások egyikét:  

    -   **Lehetővé teszi a gépek egyszerre frissítendő százalékaként**: Meghatározza, hogy csak bizonyos százalékát ügyfelek egyszerre frissülnek. Ha például a gyűjteményhez tartozik 10 ügyfél, és a gyűjtemény egy időben, 30 %-ügyfelek frissítése csak 3-ügyfelek telepítése szoftverfrissítéseket egy adott időpontban.  

    -   **Lehetővé teszi a gépek egyszerre frissítendő számos**: Meghatározza, hogy csak bizonyos számú ügyfél egyszerre frissülnek.  

    -   **Adja meg a karbantartás során**: Megadja, hogy a gyűjteményben lévő ügyfelek frissített egyszerre csak egy Ön által konfigurált a sorrendben. Egy ügyfél csak szoftverfrissítéseket telepíti, amely azt előre a listán az ügyfél befejezte a szoftverfrissítések telepítése után.  

5.  Adja meg, hogy a központi telepítés előtti (a csomópont kiürítésekor) vagy (a Csomópont fürttevékenységének újraindításakor) telepítés utáni parancsfájl használatára.  

    > [!TIP]  
    >  Az alábbiakban példákat is használhatja a központi telepítés előtti tesztelése és a központi telepítés utáni parancsfájlok, amelyek szöveges fájlba írni az aktuális idő:  
    >   
    >  **Központi telepítés előtti**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Telepítés után**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-group-and-monitor-status"></a>A szoftverfrissítések központi telepítése a kiszolgáló csoport és a figyelő állapota  

1.  [Szoftverfrissítések központi telepítése](https://technet.microsoft.com/library/gg712304.aspx) a kiszolgáló csoport gyűjteményhez.  

2.  [A szoftverfrissítések központi telepítésének](https://technet.microsoft.com/library/gg712304.aspx). A szoftverfrissítések a szokásos figyelési nézet mellett egy új állapot leírása akkor látható, ha egy ügyfél arra vár, hogy a szoftverfrissítések telepítéséhez a kapcsolja. **Várakozás a zárolás** az új állapot jelenik meg.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>A számítógépek egy kiszolgálócsoport-telepítési zárolások törlése  

1.  A a **eszközök és megfelelőség** munkaterületet, kattintson a **Eszközgyűjtemények**, és kattintson a gyűjtemény törlése Fürttelepítési zárolások feloldása.  

2.  Az a **Home** lap a **telepítési** csoportjában kattintson **egyértelmű Server csoport telepítési zárolja**. Ha az ügyfelek telepíthetik a szoftverfrissítéseket nem sikerült, és megakadályozzák, más ügyfelek a szoftverfrissítések telepítése után, a fürttelepítési zárolások feloldása manuálisan törölhetők.  

##  <a name="BKMK_ATP"></a>A Windows Defender Advanced Threat Protection szolgáltatás támogatása  
 Windows Defender Advanced Threat Protection (ATP) az új szolgáltatás, amely segít a vállalatok számára, hogy észlelni, vizsgálja meg és a hálózat a speciális támadások válaszolni. További információ [Windows Defender ATP](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection). A Configuration Manager alapképességeivel, és figyelheti a felügyelt Windows 10 évforduló Edition ügyféleszközökön.  

### <a name="try-it-now"></a>Próbálja ki most!  
 Próbálja meg a következő feladatok végezhetők, és tudassa velünk, milyen eredménnyel járt keresztül elérhető visszajelzési űrlapra a [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) oldalon, a Microsoft Connect webhelyen:  

-   Az eszközök regisztrálásához a Windows Defender Advanced Threat Protection (ATP) online szolgáltatáshoz  

-   A felügyelt eszközök a Windows Defender ATP telepítésének figyelése  

 **Előfeltételek**  

-   Előfizetés a Windows Defender Advanced Threat Protection online szolgáltatáshoz  

-   Windows 10-es évforduló Edition (build 14328 és nagyobb) rendszert futtató ügyfelek  

-   Egy ügyfél bevezetési konfigurációs fájl létrehozása  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>Az előkészítési konfigurációs fájl létrehozása  

    1.  Jelentkezzen be a Windows Defender ATP online szolgáltatás  

    2.  Kattintson a **ügyfél előkészítésének** menüpont  

    3.  Válassza ki **System Center Configuration Manager** kattintson **letöltőcsomag**.  

    4.  Töltse le a tömörített (.zip) fájlt, és csomagolja ki annak tartalmát.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>A Windows Defender ATP az eszközök regisztrálásához  

1.  A Configuration Manager-konzolon lépjen a **eszközök és megfelelőség** > **áttekintése** > **Endpoint Protection** > **a Windows Defender ATP-házirendek** kattintson **létrehozása a Windows Defender ATP-házirend**. A Windows Defender ATP-házirend varázsló megnyílik.  

2.  Típus a **neve** és **leírás** a Windows Defender ATP-házirend, és válassza ki a **bevezetési**. Kattintson a Tovább gombra.  

3.  **Tallózás** a szervezet Windows Defender ATP-felhőszolgáltatásokat igénybe vevő által biztosított konfigurációs fájlból. Kattintson a **Tovább** gombra.  

4.  Adja meg a fájlminták gyűjtött és megosztott elemzéshez felügyelt eszközökről.  

    -   **Nincs** – minta fájlokat összegyűjtött elemzés  

    -   **Hordozható végrehajtható fájlok** – például fájlok programfájlok (.exe), dinamikus függvénytár-hivatkozás (.dll) fájlok, fájljai, és a hasonló fájlok, amelyek cyberattacks hasznosítható gyűjtött, és ossza meg elemzés céljából  

     Kattintson a **Tovább** gombra.  

5.  Tekintse át az összefoglalást, és fejezze be a varázslót.  

6.  Most már telepítheti a Windows Defender ATP-házirend a felügyelt ügyfélszámítógépek kattintva **telepítés**.  

##### <a name="monitor-windows-defender-atp"></a>A Windows Defender ATP figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **biztonsági** majd **Windows Defender ATP**.  

2.  Tekintse át a Windows Defender Advanced Threat Protection-irányítópult.  

    -   **A Windows Defender ügynök telepítési állapota** – a száma és a Windows Defender ATP-házirend active előkészítve jogosult felügyelt ügyfélszámítógépek százaléka  

    -   **A Windows Defender ATP ügyfélállapot** – a Windows Defender ATP-ügynök állapota reporting számítógép ügyfeleinek százalékos aránya  

        -   **Kifogástalan** -megfelelően működik-e  

        -   **Inaktív** -nincsenek időszakban szolgáltatásnak küldött adatok  

        -   **Ügynök állapota** – a rendszer az ügynök a Windows szolgáltatás nem fut  

        -   **Nincs előkészítve** - házirend alkalmazta, de az ügynök nem jelentette a házirend előkészítéséről  

##  <a name="BKMK_DHA"></a>Helyszíni Készülékállapot-igazolás  
 Az Eszközállapot-igazolás Windows 10-eszközök most már beállítható úgy, hogy a helyszíni infrastruktúrát használja kommunikációra. A rendszergazdák adhat meg, hogy jelentéskészítés a felhő használatával történik vagy a helyszíni erőforrások. Ha a helyszíni állapotigazolási jelentés van jelölve, majd egy URL-cím is megadható a szolgáltatás. Ez lehetővé teszi az ügyfélszámítógépeken az internet-hozzáférés nélküli engedélyezése és az Eszközállapot-igazolás eszközöket kezelheti.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>Az Eszközállapot-igazolás a helyszíni eszközök engedélyezése  
 1605, az azt korábban rögzített néhány hibákat észlelt a Technical Preview 1604.  A kipróbáláshoz konfigurálja a helyszíni Állapotigazolási szolgáltatás ügyfélügynök-beállításokkal.  

1.  A Configuration Manager-konzolon lépjen a **felügyeleti** > **áttekintése** > **ügyfélbeállítások**, és utána állítsa be **helyszíni Állapotigazolási szolgáltatás** való **Igen**.  

2.  Adja meg a **Helyszíni állapotigazolási szolgáltatás URL-címét**, majd kattintson az **OK**gombra.  

##  <a name="BKMK_RestartOptions"></a>Új szoftverfrissítések telepítése után indítsa újra a beállítások a Windows 10-ügyfelek  
 Amikor egy szoftverfrissítés, amelyhez újraindítás van telepítve, a Configuration Manager és a számítógépen telepített, függőben lévő újraindul, és újraindítást kérő párbeszédpanelt jelenik meg. Jelenleg a Windows 8 és újabb verzióiban állítsa le vagy indítsa újra a számítógépet a Windows energiagazdálkodási lehetőségek (ahelyett, hogy az újraindítás párbeszédpanelről), a újraindítás párbeszédpanel marad a számítógép újraindul, és a számítógép után újra kell indítania a konfigurált határidő lejártakor. A technical Preview beállítás **frissül és újraindul** és **frissítés és a leállítási** is elérhető legyen a Windows energiagazdálkodási beállítások Windows 10 rendszerű számítógépeket, amennyiben a Configuration Manager szoftverfrissítés egy függőben lévő újraindítás. E két lehetőség valamelyikének választása esetén az újraindítási párbeszédpanel nem jelenik meg a számítógép újraindítását követően.  

##  <a name="BKMK_IMEI"></a>Vállalati tulajdonban lévő eszközök IMEI- vagy iOS sorozatszámmal előzetes bejelentése  
 Vállalat által birtokolt eszközök most azonosíthatja az állomás nemzetközi mobilkészülék-azonosító (IMEI) számokat importálásával. Feltöltheti az eszközök IMEI-számának tartalmazó vesszővel tagolt (.csv) fájlt, vagy meg manuálisan is beírhatja az eszközadatokat.  Az iOS-eszközök sorozatszámokat is importálhat.  Importált adatok állítja be a "Céges" eszközként regisztrálni eszközök tulajdonjogát.  Intune-licencet a szolgáltatáshoz hozzáférő mindegyik felhasználóhoz továbbra is szükség.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja meg a következő feladatok végezhetők, és tudassa velünk, milyen eredménnyel járt keresztül elérhető visszajelzési űrlapra a [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) oldalon, a Microsoft Connect webhelyen:  

-   Importáljon egy IMEI-számokkal egy CSV-fájlban. Minden egyes sorára az IMEI-szám, amelyet a részleteket tartalmazó mező tartalmazhat.  

-   IMEI-számokkal manuálisan importálhat a Configuration Manager konzolon.  

-   Importáljon egy iOS-sorozatszámokat egy CSV-fájlban. Ebben az esetben mindegyik sor tartalmazza az eszköz minden adatát követ.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>IMEI- vagy iOS-sorozatszámú céges eszközök előzetes bejelentése  

1.  Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **minden vállalati tulajdonú eszközök** > **Pre-declared eszközök**, és kattintson a **létrehozása Pre-declared eszközök**. Megnyílik a Pre-declared eszközök varázsló.  

2.  Adja meg, hogyan szeretné eszközadatokat hozzáadása:  

    -   **IMEI-számokat és eszközadatokat tartalmazó CSV-fájl feltöltése** – való feltöltése számból álló lista, tekintse meg a #3. lépés.  

    -   **IMEI-számok és eszközadatok manuális felvétele** - és adja meg manuálisan az adatokat, írja be az IMEI-számmal vagy iOS-sorozatszám és az eszközök adatait, majd folytassa a 4. lépés.  

3.  A feltöltött fájlok tallózással keresse meg a vállalat által birtokolt eszközök előzetes bejelentése információt tartalmazó .csv fájlt. A fájl a következő formátumban, kivéve a felső sorban (csak útmutatást előírt) kell rendelkeznie:  

    |**IMEI #**|**iOS soros**|**AZ OPERÁCIÓS RENDSZER**|**Részletek**|
    |---|---|---|---|
    |123456789012345||WINDOWS|Vállalati tulajdonban lévő Windows-eszköz|
    |123456789012|A0BCD0EFGH0J|IOS|Vállalat által birtokolt iOS-eszközök|
    |123456789012346||ANDROID|Android-eszköz vállalati által birtokolt|

     **Oszlopok:**  

    -   1. oszlop: IMEI-számmal – minden egyes sorára vagy egy IMEI számának vagy iOS sorozatszám.  

    -   2. oszlop: iOS-sorozatszám – csak iOS-sorozatszámokat lehet előre bejelentett. IMEI-számmal használja az egyéb eszközplatformhoz  

    -   3. oszlop: Operációs rendszer az eszköz (kis-és nagybetűk szükséges):  

        -   IOS – összes iOS-eszközök  

        -   WINDOWS – Windows Phone, Windows 10 Mobile és Windows rendszerű számítógépeket tartalmaz  

        -   ANDROID – az összes Android-eszközök  

    -   4. oszlop: Részletek – további eszköz a Configuration Manager-konzolon megjelenő adatok  

     Kattintson a **Tovább** gombra.  

4.  Tekintse át a fájl importálása eredményét. Korábban importált imei-Azonosítót vagy sorozatszámot kell új adatokkal frissíteni az adatait.  Kattintson a **következő** folytatja vagy **vissza** frissített részletek megőrzése, és fejezze be a varázslót.  

