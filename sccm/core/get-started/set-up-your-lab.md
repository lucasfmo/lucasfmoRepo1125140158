---
title: "System Center Configuration Manager tesztkörnyezet beállítása |} Microsoft Docs"
description: "Állítson be egy tesztkörnyezetet, hogy a Configuration Manager kiértékelése szimulált valósághű tevékenységekkel."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1970688-0cd2-404f-a17f-9e2aa4a78758
caps.latest.revision: 11
caps.handback.revision: 0
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0dc7992f35f488f99138a618bc4a408e8e0b837f
ms.openlocfilehash: 11f5d0c3c61d675a8182e985f82e6af363b34592
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-your-system-center-configuration-manager-lab"></a>System Center Configuration Manager tesztkörnyezet beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör útmutatása lehetővé teszi a állítson be egy tesztkörnyezetet, hogy a Configuration Manager kiértékelése szimulált valósághű tevékenységekkel.  

##  <a name="BKMK_LabCore"></a> Alapösszetevők  
 A System Center Configuration Manager környezetének beállításához szükséges néhány alapösszetevő, a Configuration Manager telepítésének támogatásához.    

-   **A tesztkörnyezet használja a Windows Server 2012 R2**, amelybe a System Center Configuration Manager telepítjük.  

     A Windows Server 2012 R2 próbaverzióját letöltheti a [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012).  

     Vegye figyelembe a módosítását vagy letiltását az Internet Explorer fokozott biztonsági beállításai ahhoz, hogy könnyebben hozzáférhessen a gyakorlatokban hivatkozott a letöltéseket. Tekintse át [Internet Explorer: Fokozott biztonsági beállítások](https://technet.microsoft.com/en-us/library/dd883248\(v=ws.10\).aspx) további információt.  

-   **A tesztkörnyezet a helyadatbázishoz SQL Server 2012 SP2-t** használ.  

     SQL Server 2012 próbaverzióját letöltheti a [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=29066).  

     SQL Server rendszer [SQL Server támogatott verziója](../../core/plan-design/configs/support-for-sql-server-versions.md#bkmk_SQLVersions) , amelyek teljesülése esetén használja a System Center Configuration Managerrel.  

    -   A Configuration Manager egy SQL Server a Helyadatbázis futtatásához 64 bites verziója szükséges.  

    -   **SQL_Latin1_General_CP1_CI_AS** . **SQL-hitelesítés helyett**   

    -   **Windows-hitelesítés**szükséges. [SQL Server-példányra](https://technet.microsoft.com/en-us/library/ms144284.aspx)szükséges. is required.  

    -   Egy dedikált **SQL Server-példány** szükséges.  

    -   Nem korlátozzák a **megcímezhető rendszermemória** az SQL Server.  

    -   Konfigurálja a **SQL Server-szolgáltatásfióknak** használatával fussanak a **tartományi helyi felhasználói** fiók.  

    -   Telepítenie kell a **SQL Server reporting Services szolgáltatás**.  

    -   **kijelölt helyrendszerszerepkörei közötti** helyen belüli kommunikáció  

    -   **Helyen belüli kommunikáció** között az SQL Server adatbázismotor és jelölje be a Configuration Manager helyrendszer-szerepkörök alapértelmezett TCP 1433 portot használja.  

-   **A tartományvezérlő használ-e a Windows Server 2008 R2** az Active Directory tartományi szolgáltatások telepítése. A tartományvezérlő olyan funkciókkal, mint a DHCP-állomás, és a DNS-kiszolgáló teljesen minősített tartománynevét használja.  

     További információkért tekintse át a [Active Directory tartományi szolgáltatások áttekintése](https://technet.microsoft.com/en-us/library/hh831484).  

-   **Néhány virtuális gépek Hyper-V használt** ellenőrzése, hogy a gyakorlatokban felügyeleti megtett várt módon működnek-e. Legalább három virtuális gép ajánlott, melyeken Windows 7 (vagy újabb) telepítve.  

     További információkért tekintse át a [Hyper-V áttekintése](https://technet.microsoft.com/en-us/library/hh831531.aspx).  

-   **rendszergazdai jogosultságok** szükségesek.  

    -   A Configuration Manager megköveteli a Windows Server környezetben helyi engedélyekkel rendelkező rendszergazda  

    -   Az Active Directory a séma módosításához szükséges engedélyekkel rendelkező rendszergazdát igényel  

    -   A virtuális gépek magukra a gépekre vonatkozó helyi engedélyeket igényelnek  

Bár nem kötelező megadni a tesztkörnyezethez, áttekintheti [a System Center Configuration Manager által támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md) további információt a System Center Configuration Manager megvalósításához szükséges követelményeknek. Tekintse meg a hivatkozott Itt eltérő szoftververziókkal dokumentációját.  

Miután telepítette ezeket az összetevőket, számos további lépéseket, amelyekkel a Windows-környezet konfigurálása a Configuration Manager.  

###  <a name="BKMK_LabADPrep"></a> Active Directory-tartalom előkészítése a tesztkörnyezethez  
 A tesztkörnyezethez létre kell hoznia egy biztonsági csoportot, majd egy tartományi felhasználót kell hozzáadnia ahhoz.  

-   Biztonsági csoport: **Értékelés**  

    -   Csoport hatóköre: **Univerzális**  

    -   Csoport típusa: **Biztonság**  

-   Tartományi felhasználó: **ConfigUser**  

     Normális körülmények között nem adna általános hozzáférést minden, a környezetben lévő felhasználó számára. Ezzel a felhasználóval azért kell így tennie, hogy leegyszerűsítse a tesztkörnyezet online állapotba hozását.  

A következő lépések szükségesek a Configuration Manager-ügyfelek lekérdezést Active Directory tartományi szolgáltatásokban helyerőforrások engedélyezéséhez a következő eljárásokkal fölé vannak felsorolva.  

###  <a name="BKMK_CreateSysMgmtLab"></a> A rendszerkezelési tároló létrehozása  
 A Configuration Manager nem automatikusan létrehozza a szükséges rendszerkezelési tárolót az Active Directory tartományi szolgáltatásokban a séma kiterjesztésekor. Ezért ezt létre kell hoznia a tesztkörnyezethez. Ehhez a lépéshez [telepítenie kell az ADSI-szerkesztőt.](https://technet.microsoft.com/en-us/library/cc773354\(WS.10\).aspx#BKMK_InstallingADSIEdit)  

 Mindenképpen olyan fiókkal jelentkezzen be, amely **Az összes gyermekobjektum létrehozása** engedéllyel rendelkezik a **rendszertárolón** az Active Directory tartományi szolgáltatásaiban.  

##### <a name="to-create-the-system-management-container"></a>A rendszerkezelési tároló létrehozása:  

1.  Futtassa az **ADSI-szerkesztő**szolgáltatást, és csatlakozzon ahhoz a tartományhoz, amelyben a helykiszolgáló található.  

2.  Bontsa ki a **tartomány&lt;számítógép teljesen minősített tartományneve\>**, bontsa ki a **< megkülönböztető név\>**, kattintson a jobb gombbal **CN = rendszer**, kattintson **új**, és kattintson a **objektum**.  

3.  Az **Objektum létrehozása** párbeszédpanelen válassza a **Tároló**elemet, majd kattintson a **Tovább**gombra.  

4.  Az **Érték** mezőbe írja be a **System Management**kifejezést, majd kattintson a **Tovább**gombra.  

5.  Az eljárás befejezéséhez kattintson a **Befejezés** gombra.  

###  <a name="BKMK_SetSecPermLab"></a> A rendszerkezelési tároló biztonsági engedélyeinek beállítása  
 A helykiszolgáló számítógépfiókjának adja meg a helyadatok a tárolóban való közzétételéhez szükséges engedélyeket. A feladathoz az ADSI-szerkesztőt is használnia kell.  

> [!IMPORTANT]  
>  A következő eljárás megkezdése előtt győződjön meg arról, hogy a helykiszolgáló tartományához csatlakozik.  

##### <a name="to-set-security-permissions-for-the-system-management-container"></a>A rendszerkezelési tároló biztonsági engedélyeinek beállítása:  

1.  A konzol ablaktáblájában bontsa ki a **helyrendszer-kiszolgáló tartománya**, bontsa ki a **DC =&lt;kiszolgáló megkülönböztető neve\>**, majd bontsa ki a **CN = rendszer**. Kattintson a jobb gombbal a **CN=Rendszerkezelés**elemre, majd válassza a **Tulajdonságok**parancsot.  

2.  A **CN=Rendszerkezelés tulajdonságai** párbeszédpanelen jelenítse meg a **Biztonság** lapot, majd kattintson a **Hozzáadás** gombra a helykiszolgáló számítógépfiókjának hozzáadásához. Adjon a fióknak **Teljes hozzáférés** engedélyt.  

3.  Kattintson a **speciális**, jelölje ki a helykiszolgáló számítógépfiókját, és kattintson a **szerkesztése**.  

4.  Az **Alkalmazás** listán válassza az **Ez az objektum és a gyermekobjektumok**beállítást.  

5.  Az **ADSI-szerkesztő** konzol bezárásához és az eljárás befejezéséhez kattintson az **OK** gombra.  

     Ez az eljárás további betekintést, tekintse át [az Active Directory-séma kiterjesztése a System Center Configuration Managerhez](../../core/plan-design/network/extend-the-active-directory-schema.md)  

###  <a name="BKMK_ExtADSchLab"></a> Az Active Directory-séma kiterjesztése az extadsch.exe eszközzel  
 Ki kell terjesztenie az Active Directory-sémát a tesztkörnyezethez, mivel ez teszi lehetővé, hogy az összes Configuration Manager-szolgáltatásokat és funkciókat használja a legkisebb rendszergazdai terheléssel. Az Active Directory-séma kibővítése a teljes erdőre kiterjedő konfigurációs beállítás, melyet minden erdőre egyszer kell végrehajtani. A séma kibővítése véglegesen módosítja az Active Directory alapkonfigurációjában lévő osztályok és attribútumok készletét. Ez a művelet nem vonható vissza. A séma kibővítése lehetővé teszi, hogy a Configuration Manager összetevő, amely lehetővé teszi, akkor a leghatékonyabban belül a hálózati környezet függvény eléréséhez.  

> [!IMPORTANT]  
>  Ügyeljen arra, hogy a séma-főkiszolgáló tartományvezérlőbe olyan fiókkal jelentkezzen be, amely a **Sémagazdák** biztonsági csoport tagja. Ha más hitelesítő adatokat próbál meg használni, a művelet sikertelen lesz.  

##### <a name="to-extend-the-active-directory-schema-using-extadschexe"></a>Az Active Directory-séma kiterjesztése az extadsch.exe eszközzel:  

1.  Készítsen biztonsági másolatot a séma-főkiszolgáló tartományvezérlő rendszerállapot. A fő tartományvezérlő biztonsági mentésével kapcsolatos további információkért lásd: [A Windows Server biztonsági másolat eszköze](https://technet.microsoft.com/en-us/library/cc770757.aspx)  

2.  Keresse meg a **\SMSSETUP\BIN\X64** mappát a telepítési adathordozón.  

3.  Futtassa a **extadsch.exe**parancsot.  

4.  Ellenőrizze, hogy sikeres volt-e a séma kiterjesztése: ehhez tekintse át az **extadsch.log** naplófájlt, amely a rendszermeghajtó gyökérmappájában található.  

     Ez az eljárás további betekintést, tekintse át [az Active Directory-séma kiterjesztése a System Center Configuration Manager](../../core/plan-design/network/extend-the-active-directory-schema.md).  

###  <a name="BKMK_OtherTasksLab"></a> Egyéb szükséges feladatok  
 A telepítés előtt a következő feladatokat is végre kell hajtania.  

 **Mappa létrehozása minden letöltött fájl tárolásához**  

 A gyakorlat során a telepítési adathordozó több összetevőjének letöltésére is szükség lesz. A telepítési eljárások megkezdése előtt határozzon meg egy helyet, ahonnan nem kell majd áthelyeznie ezeket a fájlokat, amíg nem kívánja leszerelni a tesztkörnyezetet. A letöltések tárolásához egyetlen, különálló almappákkal rendelkező mappa használata ajánlott.  

 **A .NET telepítése és a Windows Communication Foundation aktiválása**  

 Két .NET-keretrendszert kell telepítenie: először a .NET 3.5.1-et, majd a .NET 4.5.2 vagy újabb verziót. Emellett a Windows Communication Foundation (WCF) szolgáltatást is aktiválnia kell. A WCF szolgáltatást arra tervezték, hogy kezelhető megközelítést nyújtson az elosztott környezetekhez, a széleskörű együttműködési képességhez és a szolgáltatásirányítás közvetlen támogatásához, és egy szolgáltatásorientált programozási modell használatával egyszerűsítse az összekapcsolt alkalmazások fejlesztését. A WCF szolgáltatással kapcsolatban a [What Is Windows Communication Foundation?](https://technet.microsoft.com/en-us/subscriptions/ms731082\(v=vs.90\).aspx) című témakör nyújt további betekintést.  

##### <a name="to-install-net-and-activate-windows-communication-foundation"></a>A .NET telepítése és a Windows Communication Foundation aktiválása:  

1.  Nyissa meg a **Server Manager**t, majd keresse meg a **Kezelés**elemet. Kattintson a **Szerepkörök és szolgáltatások hozzáadása** lehetőségre a **Szerepkörök és szolgáltatások hozzáadása Wizard.**megnyitásához.  

2.  Tekintse át az **Előkészületek** panelen megadott információkat, majd kattintson a **Tovább**gombra.  

3.  Válassza a **Szerepköralapú vagy szolgáltatásalapú telepítés**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Válassza ki a kiszolgálót a **Kiszolgálókészletből**, majd kattintson az **Tovább**gombra.  

5.  Tekintse át a **Kiszolgálói szerepkörök** panelt, majd kattintson a **Tovább**gombra.  

6.  A listából kiválasztva adja hozzá a következő **Szolgáltatásokat** :  

    -   **.NET-keretrendszer 3.5 szolgáltatásai**  

        -   **.NET-keretrendszer 3.5 (tartalmazza a .NET 2.0 és 3.0 verziót)**  

    -   **.NET-keretrendszer 4.5 szolgáltatásai**  

        -   **.NET-keretrendszer 4.5**  

        -   **ASP.NET 4.5**  

        -   **WCF-szolgáltatások**  

            -   **HTTP-aktiválás**  

            -   **TCP-port megosztása**  

7.  Tekintse át a **Webkiszolgálói szerepkör (IIS)** és a **Szerepkör-szolgáltatások** képernyőt, majd kattintson a **Tovább**gombra.  

8.  Tekintse át a **Jóváhagyás** képernyőt, majd kattintson a **Tovább**gombra.  

9. Kattintson a **Telepítés** lehetőségre, és a **Kiszolgálókezelő** **Értesítések**ablaktábláján ellenőrizze, hogy a telepítés megfelelően fejeződött-e be.  

10. A .NET alaptelepítésének befejeződése után nyissa meg a [Microsoft letöltőközpontot](https://www.microsoft.com/en-us/download/details.aspx?id=42643) a .NET-keretrendszer 4.5.2-es verziója webes telepítőjének beszerzéséhez. Kattintson a **Letöltés** gombra, majd **futtassa** a telepítőt. Az automatikusan felismeri és telepíti a szükséges összetevőket a kiválasztott nyelven.  

Tekintse át a következő cikkeket azzal kapcsolatos további információért, hogy miért ezek a .NET-keretrendszerek szükségesek:  

-   [.NET Framework Versions and Dependencies](https://technet.microsoft.com/en-us/library/bb822049.aspx)  

-   [.NET Framework 4 RTM Application Compatibility Walkthrough](https://technet.microsoft.com/en-us/library/dd889541.aspx)  

-   [kézikönyv: Az ASP.NET 4 ASP.NET webes alkalmazás frissítése](https://technet.microsoft.com/en-us/library/dd483478\(VS.100\).aspx)  

-   [Microsoft .NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/en-us/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)  

-   [Belső kimeneti - CLR a folyamat egymás mellett](https://msdn.microsoft.com/en-us/magazine/ee819091.aspx)  

**A BITS, az IIS és az RDC engedélyezése**  

A [Háttérben futó intelligens átviteli szolgáltatás (BITS)](https://technet.microsoft.com/en-us/library/dn282296.aspx) fájlok az ügyfél és a kiszolgáló közötti aszinkron átvitelét igénylő alkalmazásokhoz használható. A háttérbeli és az előtérbeli átvitelek áramlásának mérésével a BITS megőrzi az egyéb hálózati alkalmazások válaszképességét. Emellett automatikusan folytatja a fájlok átvitelét, ha átviteli munkamenet megszakad.  

Azért kell telepítenie a BITS szolgáltatást a tesztkörnyezethez, mert a helykiszolgáló felügyeleti pontként is fog szolgálni.  

Az Internet Information Services (IIS) egy rugalmas, méretezhető webkiszolgáló, mellyel bármit szolgáltathat a hálózaton. A Configuration Manager által a helyrendszer-szerepkörök számú szolgál. Az IIS szolgáltatásban további információkért tekintse át [helyrendszer-kiszolgálók a System Center Configuration Managerben webhelyek](../../core/plan-design/network/websites-for-site-system-servers.md).  

A[Távoli különbözeti tömörítés (RDC)](https://technet.microsoft.com/en-us/library/cc754372.aspx) egy API-készlet, mellyel az alkalmazások meg tudják határozni, hogy történtek-e módosítások fájlok egy adott készletén. Az RDC lehetővé teszi az alkalmazások számára, hogy csak a fájlok módosított részeit replikálják, így minimalizálva a hálózati forgalmat.  

##### <a name="to-enable-bits-iis-and-rdc-site-server-roles"></a>A BITS, az IIS és az RDC helykiszolgálói szerepkörök engedélyezése:  

1.  Nyissa meg a **Server Manager**t helykiszolgálón. Keresse meg a **Kezelés**elemet. Kattintson a **Szerepkörök és szolgáltatások hozzáadása** lehetőségre a **Szerepkörök és szolgáltatások hozzáadása varázsló**megnyitásához.  

2.  Tekintse át az **Előkészületek** panelen megadott információkat, majd kattintson a **Tovább**gombra.  

3.  Válassza a **Szerepköralapú vagy szolgáltatásalapú telepítés**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Válassza ki a kiszolgálót a **Kiszolgálókészletből**, majd kattintson az **Tovább**gombra.  

5.  A listából kiválasztva adja hozzá a következő **Kiszolgálói szerepköröket** :  

    -   **Webkiszolgáló (IIS)**  

        -   **Általános HTTP-szolgáltatások**  

            -   **Alapértelmezett dokumentum**  

            -   **Könyvtár tallózása**  

            -   **HTTP-hibák**  

            -   **Statikus tartalom**  

            -   **HTTP-átirányítás**  

        -   **Állapot és diagnosztika**  

            -   **HTTP-naplózás**  

            -   **Naplózási eszközök**  

            -   **Kérésfigyelő**  

            -   **Nyomkövetés**  

    -   **Performance (Teljesítmény) (Teljesítmény)**  

        -   **Statikus tartalom tömörítése**  

        -   **Dinamikus tartalomtömörítés**  

    -   **Security**  

        -   **Kérelmek szűrése**  

        -   **Egyszerű hitelesítés**  

        -   **Ügyféltanúsítvány-hozzárendeléses hitelesítés**  

        -   **IP-cím és tartomány korlátozása**  

        -   **URL-engedélyezés**  

        -   **Windows-hitelesítés**  

    -   **Alkalmazásfejlesztés**  

        -   **.NET-bővíthetőség 3.5**  

        -   **.NET-bővíthetőség 4.5**  

        -   **ASP**  

        -   **ASP.NET 3.5**  

        -   **ASP.NET 4.5**  

        -   **ISAPI-bővítmények**  

        -   **ISAPI-szűrők**  

        -   **Kiszolgálóoldali beágyazás**  

    -   **FTP-kiszolgáló**  

        -   **FTP-szolgáltatás**  

    -   **Felügyeleti eszközök**  

        -   **IIS kezelése konzol**  

        -   **Kompatibilitás az IIS 6 kezelésével**  

            -   **Kompatibilitás az IIS 6 metabázisával**  

            -   **IIS 6 kezelése konzol**  

            -   **IIS 6-parancsfájlkezelő eszközök**  

            -   **IIS 6 WMI kompatibilitási mód**  

        -   **IIS 6-kezelő parancsfájlok és eszközök**  

        -   **Management Service**  

6.  A listából kiválasztva adja hozzá a következő **Szolgáltatásokat** :  

    -   -   **Háttérben futó intelligens átviteli szolgáltatás (BITS)**  

            -   **IIS kiszolgálóbővítmény**  

        -   **Távoli kiszolgálófelügyelet eszközei**  

            -   **Szolgáltatás-felügyeleti eszközök**  

                -   **BITS kiszolgálói bővítményeszközök**  

7.  Kattintson a **Telepítés** lehetőségre, és a **Kiszolgálókezelő** **Értesítések**ablaktábláján ellenőrizze, hogy a telepítés megfelelően fejeződött-e be.  

Alapértelmezés szerint az IIS néhány fájlkiterjesztés-típust és -helyet kizár a HTTP vagy a HTTPS használatával végzett kommunikációból. Ahhoz, hogy lehetővé tegye ezen fájlok az ügyfélrendszerekre való terjesztését, a terjesztési ponton kérelemszűrést kell konfigurálnia az IIS-hez. További információkért tekintse át [IIS-kérelemszűrés a terjesztési pontok](../../core/plan-design/network/prepare-windows-servers.md#BKMK_IISFiltering).  

##### <a name="to-configure-iis-filtering-on-distribution-points"></a>Az IIS szűrésének konfigurálása a terjesztési pontokon:  

1.  Nyissa meg az **IIS Manager** t, és válassza ki a kiszolgáló nevét az oldalsávon. Ekkor megjelenik a **kezdőképernyő** .  

2.  Győződjön meg róla, hogy a **kezdőképernyő** alján a **Szolgáltatások nézet** van kijelölve. Keresse meg az **IIS** elemet, és nyissa meg a **Kérelemszűrés**lehetőséget.  

3.  A **Műveletek** ablaktáblán kattintson a **Fájlnévkiterjesztés engedélyezése...**lehetőségre.  

4.  A párbeszédpanelen adja meg a **.msi** értéket, majd kattintson az **OK**gombra.  

###  <a name="BKMK_InstallCMLab"></a> A Configuration Manager telepítése  
Létrehozhat egy [mikor használjon elsődleges hely](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md#BKMK_ChoosePriimary) közvetlenül ügyfelek kezelésére. Ez lehetővé teszi a tesztkörnyezet támogassa a felügyeleti [helyrendszer méretezése](/sccm/core/plan-design/configs/size-and-scale-numbers) eszköz.  
A folyamat során telepítenie kell a Configuration Manager konzol használatával továbbítja a próbaeszközöket kezelheti.  

A telepítés megkezdése előtt indítsa el a [előfeltétel-ellenőrző](/sccm/core/servers/deploy/install/prerequisite-checker) Windows Server 2012 segítségével győződjön meg arról, hogy minden beállítás megfelelően engedélyezve van a kiszolgálón.  

##### <a name="to-download-and-install-configuration-manager"></a>A Configuration Manager letöltése és telepítése:  

1.  Keresse meg a [System Center Evaluations](https://www.microsoft.com/evalcenter/evaluate-system-center-2012-configuration-manager-and-endpoint-protection) lap a System Center Configuration Manager legújabb próbaverziójának letöltéséhez.  

2.  Bontsa ki a letöltési adathordozót az előre megadott helyre.  

3.  Kövesse a telepítési folyamatot: [a System Center Configuration Manager telepítő varázsló hely telepítése](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites). Ezen eljárás során a következő bemeneteket kell megadnia:  

    |A helytelepítési folyamat lépése|Választás|  
    |-----------------------------------------|---------------|  
    |4. lépés: a **Termékkulcs** lap|Válassza a **Próbaverzió**lehetőséget.|  
    |7. lépés:  **Előfeltételként szükséges letöltések**|Válassza a **Szükséges fájlok letöltése** lehetőséget, és adja meg az előre megadott helyet.|  
    |10. lépés: **Hely és telepítés beállításai**|-   **Helykód:LAB**<br />-   **Hely neve:Evaluation**<br />-   **Telepítési mappa:** adja meg az előre megadott helyet.|  
    |11. lépés: **Elsődleges hely telepítése**|Válassza **Az elsődleges hely telepítése önálló helyként**lehetőséget, majd kattintson a **Tovább**gombra.|  
    |12. lépés: **Adatbázis-telepítés**|-   **SQL-kiszolgáló neve (teljes tartománynév):** itt adja meg a teljes tartománynevet.<br />-   **Példány neve:** ezt a mezőt hagyja üresen, ugyanis az SQL korábban telepített alapértelmezett példányát fogja használni.<br />-   **Service Broker-port:** hagyja meg a 4022-es alapértelmezett portot.|  
    |13. lépés: **Adatbázis-telepítés**|Ezeknél a beállításoknál hagyja meg az alapértelmezett értékeket.|  
    |14. lépés: **SMS-szolgáltató**|Ezeknél a beállításoknál hagyja meg az alapértelmezett értékeket.|  
    |15. lépés: **Ügyfélszámítógép kommunikációs beállításai**|Győződjön meg róla, hogy a **Az összes helyrendszerszerepkör kizárólag HTTPS-kommunikációt fogad az ügyfelektől** beállítás nincs kijelölve|  
    |16. lépés: **Helyrendszer-szerepkörök**|Adja meg a teljes tartománynevet, és ellenőrizze, hogy **Az összes helyrendszerszerepkör kizárólag HTTPS-kommunikációt fogad az ügyfelektől** beállítás továbbra sincs kijelölve.|  

###  <a name="BKMK_EnablePubLab"></a>A Configuration Manager-hely közzétételének engedélyezése  
Minden egyes Configuration Manager-hely a rendszerkezelési tárolóhoz az Active Directory séma tartományi partíciójában belül teszi közzé a saját helyspecifikus információját. Ezen forgalom kezelésére kétirányú Active Directory és a Configuration Manager közötti kommunikációs csatornákat kell megnyitni. Emellett engedélyezze az erdőfelderítési szolgáltatást is az Active Directory bizonyos összetevőinek és a hálózati infrastruktúra meghatározásához.  

##### <a name="to-configure-active-directory-forests-for-publishing"></a>Active Directory-erdők közzétételhez konfigurálása:  

1.  A Configuration Manager konzol bal alsó sarkában kattintson **felügyeleti**.  

2.  A **Felügyelet** munkaterületen bontsa ki a **Hierarchiakonfiguráció**elemet, majd kattintson a **Felderítési eljárások**lehetőségre.  

3.  Válassza ki az **Active Directory-erdőfelderítés** elemet, majd kattintson a **Tulajdonságok**lehetőségre.  

4.  A **Tulajdonságok** párbeszédpanelen válassza az **Active Directory-erdőfelderítés engedélyezése**lehetőséget. A beállítás aktiválása után válassza az **Active Directory-helyhatárok automatikus létrehozása felderítésükkor**lehetőséget. Ekkor egy párbeszédpanel jelenik meg, mely a következő kérdést tartalmazza: **Szeretne teljes felderítést futtatni az első lehetséges alkalommal?** Az eljárás befejezéséhez kattintson a **Igen**.  

5.  A képernyő tetején található **Felderítési módszer** csoportban kattintson az **Erdőfelderítés futtatása most**lehetőségre, majd keresse meg az **Active Directory-erdők** elemet az oldalsávon. Az Active Directory-erdőnek meg kell jelennie a felderített erdők listájában.  

6.  Navigáljon a képernyő tetejére, az **Általános** laphoz.  

7.  A **Felügyelet** munkaterületen bontsa ki a **Hierarchiakonfiguráció**elemet, majd kattintson az **Active Directory-erdők**lehetőségre.  

##### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-your-active-directory-forest"></a>A helyadatok közzétételéhez az Active Directory-erdő a Configuration Manager-hely engedélyezése:  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Egy új erdőt kell konfigurálnia, amely még nem lett felderítve.  

3.  Az **Adminisztráció** munkaterületen kattintson az **Active Directory-erdők**elemre.  

4.  A hely tulajdonságainak **Közzététel** lapján válassza ki a csatlakoztatott erdőt, majd kattintson az **Ok** gombra a konfiguráció mentéséhez.

