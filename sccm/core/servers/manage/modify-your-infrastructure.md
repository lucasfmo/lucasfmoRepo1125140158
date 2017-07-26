---
title: "Infrastruktúra módosítása |} Microsoft Docs"
description: "Útmutató a módosításokat, vagy a telepített Configuration Manager-infrastruktúrát érintő műveletek végrehajtása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7975dc8-46ab-4dae-86b6-dc3e3cf3b2f0
caps.latest.revision: 19
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 52d2e088b8db3c2e9a0af640ca3db72b9fd7af60
ms.openlocfilehash: a5228c4984347be4b115bfa5563791fa2fb7319c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="modify-your-system-center-configuration-manager-infrastructure"></a>A System Center Configuration Manager infrastruktúrájának módosítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Egy vagy több hely telepítése után a konfigurációk módosítása vagy a telepített infrastruktúrát érintő műveletek végrehajtása válhat szükségessé.  


##  <a name="BKMK_ManageSMSprovider"></a>Az SMS-szolgáltató kezeléséről  
 Az SMS-szolgáltató (egy dinamikus csatolású függvénytár fájl: smsprov.dll) egy vagy több Configuration Manager konzol adminisztratív kapcsolódási pontot biztosít. Több SMS-szolgáltató telepítésével gondoskodhat a hely és a hierarchia felügyeletére szolgáló kapcsolódási pontok redundanciájáról.  

 Az egyes Configuration Manager-helyeken a telepítő újbóli futtatásával:  

-   Az SMS-szolgáltató (az SMS-szolgáltató minden további példányának kell lennie egy külön számítógépen) további példányának hozzáadása  

-   Az SMS-szolgáltató egy példányának eltávolítása (a hely utolsó SMS-szolgáltatójának eltávolításához távolítsa el a hely)  

 Az SMS-szolgáltató telepítésének vagy eltávolításának figyeléséhez a **ConfigMgrSetup.log** fájlt használhatja, amely a gyökérmappában található azon a helykiszolgálón, amelyen a telepítőt futtatja.  

 Mielőtt módosítaná az SMS-szolgáltatót egy helyen, tájékozódjon a következő cikkből: [A System Center Configuration Manager SMS-szolgáltatójának tervezése](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

#### <a name="to-manage-the-sms-provider-configuration-for-a-site"></a>Az SMS-szolgáltató helyre vonatkozó konfigurációjának kezelése  

1.  Futtatás **a Configuration Manager telepítő** a  **&lt;Configuration Manager hely telepítési mappája\>\BIN\X64\setup.exe**.  

2.  A **Kezdeti lépések** oldalon válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása** lehetőséget, és kattintson a **Tovább** gombra.  

3.  A **Helykarbantartás** lapon válassza az **SMS-szolgáltató konfigurációjának módosítása** lehetőséget, és kattintson a **Tovább** gombra.  

4.  Az **SMS-szolgáltatók kezelése** lapon válasszon egyet az alábbi lehetőségek közül, és fejezze be a varázslót a következő lehetőségek egyikének használatával:  

    -   További SMS-szolgáltató hozzáadása az adott helyhez:  

         Válassza az **Új SMS-szolgáltató hozzáadása** elemet, adja meg annak a számítógépnek a teljes tartománynevét, amely az SMS-szolgáltatót fogja tartalmazni és amelyen jelenleg nincs SMS-szolgáltató, majd kattintson a **Tovább** gombra.  

    -   SMS-szolgáltató eltávolítása kiszolgálóról:  

         Válassza az **SMS-szolgáltató eltávolítása** elemet, válassza ki annak a számítógépnek a nevét, amelyről el szeretné távolítani az SMS-szolgáltatót, kattintson a **Tovább** gombra, és erősítse meg a műveletet.  

        > [!TIP]  
        >  Ha az SMS-szolgáltatót egyik számítógépről egy másikra szeretné áthelyezni, előbb telepítenie kell az SMS-szolgáltatót az új számítógépre, majd el kell távolítania az eredeti helyről az SMS-szolgáltatót. Az SMS-szolgáltató nem helyezhető át egyetlen művelettel a számítógépek között.  

 A telepítővarázsló befejezésével elkészült az SMS-szolgáltató konfigurációja. A hely **Tulajdonságok** párbeszédpaneljének **Általános** lapján ellenőrizheti, hogy a helyek melyik számítógépein van telepítve SMS-szolgáltató.  

##  <a name="bkmk_Console"></a>A Configuration Manager konzol kezelése  
 Kezelheti a Configuration Manager konzolon elvégezhető feladatok a következők:  

-   **A Configuration Manager konzol nyelvének módosítása** - módosíthatja a telepített nyelvek tekintse meg a [kezelése a Configuration Manager konzol nyelvének](#BKMK_ManageConsoleLanguages) ebben a témakörben.  

-   **További konzolok telepítése** – a további konzolok telepítésével kapcsolatban lásd: [telepítése a System Center Configuration Manager konzolok](/sccm/core/servers/deploy/install/install-consoles).  

-   **DCOM konfigurálása** – szeretne csatlakozni, olvassa el a helykiszolgálótól távoli konzolok engedélyezése DCOM-engedély konfigurálásával [konfigurálása DCOM-engedélyek Configuration Manager-konzol](#BKMK_ConfigDCOMforRemoteConsole) ebben a témakörben.  

-   **Módosítsa az engedélyeket, mi a rendszergazda felhasználók is a konzolon látható elemek korlátozására** - rendszergazdai engedélyekkel, mely a korlátot, a felhasználók milyen is tekintse meg és a konzolon, olvassa el a [egy rendszergazda felhasználó felügyeleti hatókörének módosítása](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_ModAdminUser).     

###  <a name="BKMK_ManageConsoleLanguages"></a>Configuration Manager konzol nyelvének kezelése  
 Helykiszolgáló telepítése során a Configuration Manager konzoljának telepítési fájljait és a helyhez támogatott nyelvi csomagokat kerülnek a  **&lt;Configmgrtelepítésiútvonal\>\Tools\ConsoleSetup** almappa a helykiszolgálón.  

-   Ebből a mappából a helykiszolgálón a Configuration Manager konzol telepítésének indításakor, a Configuration Manager konzol és a támogatott nyelvi csomagok fájljai a számítógépre kerülnek  

-   Elérhető a számítógép jelenlegi nyelvbeállításához tartozó nyelvi csomag esetén a Configuration Manager konzol ezen a nyelven nyílik meg  

-   Ha a kapcsolódó nyelvi csomag nem érhető el a Configuration Manager konzolon, a konzol angol nyelven indul el  

Példaként vegyünk egy forgatókönyvet, ahol a Configuration Manager konzol telepítése angol, német és francia támogató helykiszolgálóról. Ha a számítógépen a Configuration Manager konzolt francia nyelv használatára konfigurált beállítással nyissa meg, megjelenik a konzol francia nyelven indul. Ha a számítógépen a Configuration Manager konzolt japán nyelv használatára konfigurált megnyitni, a konzol angol nyelven indul el, mert a japán nyelvi csomag nem érhető el.  

 Minden alkalommal, amikor a Configuration Manager-konzol megnyitása után, akkor határozza meg a számítógépen beállított nyelvtől, ellenőrzi, hogy a kérdéses nyelvi csomag a Configuration Manager konzolon érhető el, és majd a megfelelő nyelvi csomag használatával indul. Ha azt szeretné, hogy nyissa meg a Configuration Manager konzol azon a számítógépen beállított nyelvtől függetlenül mindenképpen angolul, kell manuálisan távolítsa el vagy nevezze át a számítógépen lévő nyelvi csomagok fájljait.  

 Az alábbi eljárások segítségével indítsa el a Configuration Manager konzolon a számítógép területi beállításaitól függetlenül angol nyelven.  

##### <a name="to-install-an-english-only-version-of-the-configuration-manager-console-on-computers"></a>A Configuration Manager konzol csak angol nyelvű verziójának telepítése számítógépeken  

1.  A Windows Intézőben keresse meg a  **&lt;Configmgrtelepítésiútvonal\>\Tools\ConsoleSetup\LanguagePack**  

2.  Nevezze át az **.msp** és **.mst** fájlokat. A **&lt;fájlnév\>.MSP** fájlt például **&lt;fájlnév\>.MSP.disabled** névre módosíthatja.  

3.  A Configuration Manager konzol telepítéséhez a számítógépen.  

    > [!IMPORTANT]  
    >  Amikor új kiszolgálónyelveket a kiszolgáló, az .msp és .mst fájlok való újra át lesznek másolva a **LanguagePack** mappa, ezért meg kell ismételnie ezt az eljárást csak angol nyelvű új Configuration Manager-konzol telepítéséhez.  

##### <a name="to-temporarily-disable-a-console-language-on-an-existing-configuration-manager-console-installation"></a>Telepített Configuration Manager-konzol nyelvének ideiglenes letiltása  

1.  A Configuration Manager konzolt futtató számítógépen zárja be a Configuration Manager konzolt.  

2.  A Windows Intézőben keresse meg a &lt; *Konzoltelepítésiútvonala*> \Bin\ a Configuration Manager konzol számítógépen.  

3.  Nevezze át a számítógépen beállított nyelvhez tartozó megfelelő nyelvi mappát. Ha például a számítógép nyelvbeállítása német, a **de** mappát átnevezheti **de.letiltva** névre.  

4.  A számítógéphez beállított nyelven a Configuration Manager konzol megnyitásához nevezze át a mappát az eredeti nevére. Például nevezze át a **de.letiltva** mappát **de** névre.  

##  <a name="BKMK_ConfigDCOMforRemoteConsole"></a>DCOM-engedélyek konfigurálása a távoli Configuration Manager-konzol  
 A Configuration Manager konzolt futtató felhasználói fiók hozzáférhet a helyadatbázishoz az SMS-szolgáltató használatával engedélyre van szüksége. Azonban a rendszergazda felhasználók számára a távoli Configuration Manager konzol használja is igényel **Távoli aktiválás** DCOM-engedély:  

-   A helykiszolgáló számítógép  

-   Minden, az SMS-szolgáltató egy példányát futtató számítógép  

 Az adott számítógépen az **SMS rendszergazdák** nevű biztonsági csoport engedélyezi a hozzáférést az SMS-szolgáltatóhoz, és a szükséges DCOM-engedélyek megadására is használható. (Ez a csoport nem a számítógép helyi, ha az SMS-szolgáltató tagkiszolgálón fut, és tartományi helyi csoport akkor, ha egy tartományvezérlőn fut az SMS-szolgáltató.)  

> [!IMPORTANT]  
>  A Configuration Manager konzol a Windows Management Instrumentation (WMI) használatával csatlakozik az SMS-szolgáltató, és a WMI belső módon használja a DCOM. Ezért a Configuration Manager a DCOM-kiszolgáló, az SMS-szolgáltatót tartalmazó számítógépen aktiválni, ha a Configuration Manager konzol az SMS Provider számítógép eltérő számítógépen fut. engedélyekkel kell rendelkeznie. Alapértelmezés szerint csak a beépített Rendszergazdák csoport tagjai számára távoli aktiválás kap. Ha az SMS rendszergazdák csoport számára megadja a Távoli aktiválás engedélyt, a csoport tagjai DCOM-támadást intézhetnek az SMS-szolgáltatót tartalmazó számítógép ellen. Ez a konfiguráció megnöveli a számítógép támadható felületét. A veszély csökkentéséhez körültekintően ellenőrizze az SMS rendszergazdák csoport tagjait.  

 A következő eljárással konfigurálhatja az egyes központi felügyeleti helyeket, elsődleges helykiszolgálón, és minden biztosítani a távoli Configuration Manager konzol elérését a rendszergazdák számára az SMS-szolgáltatót futtató számítógépen.  

#### <a name="to-configure-dcom-permissions-for-remote-configuration-manager-console-connections"></a>DCOM-engedélyek konfigurálása a távoli Configuration Manager konzol kapcsolataihoz  

1.  Nyissa meg a **Komponensszolgáltatásokat** a **Dcomcnfg.exe** futtatásával.  

2.  A **Komponensszolgáltatások**, kattintson a **konzolgyökér** >  **Komponensszolgáltatások** > **számítógépek**, és kattintson a **Sajátgép**. A **Művelet** menüben válassza a **Tulajdonságok** parancsot.  

3.  A **Sajátgép tulajdonságai** párbeszédpanel **COM-biztonság** lapjának **Indítási és aktiválási engedélyek** csoportjában kattintson a **Korlátok módosítása** gombra.  

4.  Az **Indítási és aktiválási engedély** párbeszédpanelen kattintson a **Hozzáadás** gombra.  

5.  Az a **felhasználó kiválasztása, számítógépek, szolgáltatásfiókok vagy csoportok** párbeszédpanel a **írja be a kijelölendő objektumok nevét (példák)** mezőbe írja be **SMS rendszergazdák**, és kattintson a **OK**.  

    > [!NOTE]  
    >  Előfordulhat, hogy az SMS rendszergazdák csoport megkereséséhez módosítania kell a **Helyek** beállítást. Ez a csoport helyi csoport a számítógépen, amikor az SMS-szolgáltató tagkiszolgálón fut, és tartományi helyi csoport, amikor az SMS-szolgáltató tartományvezérlőn fut.  

6.  Az **SMS rendszergazdák** csoportban jelölje be a **Távoli aktiválás** jelölőnégyzetet a távoli aktiválás engedélyezéséhez.  

7.  Kattintson az **OK** gombra, majd ismét kattintson az **OK** gombra, és zárja be a **Számítógép-kezelés** ablakot. A számítógép most már hozzáférhet a távoli Configuration Manager konzol az SMS rendszergazdák csoport tagjai számára van konfigurálva.  

 Ismételje meg az eljárást minden egyes SMS Provider számítógép, amely támogatja a távoli Configuration Manager konzolhoz.  

##  <a name="bkmk_dbconfig"></a>A Helyadatbázis konfigurációjának módosítása  
 Egy hely telepítése után úgy módosíthatja a helyadatbázis és a helyadatbázis-kiszolgáló konfigurációját, hogy futtatja a telepítőt egy központi felügyeleti helykiszolgálón vagy elsődleges helykiszolgálón. A helyadatbázist áthelyezheti az SQL Server új példányára ugyanazon a számítógépen, illetve az SQL Server támogatott verzióját futtató más számítógépre. Ezek és és az ezekhez kapcsolódó módosítások nem támogatottak a másodlagos helyek adatbázis-konfigurációjában.  

 A támogatás korlátairól további információt a következő cikkben talál: [Support policy for manual database changes in a Configuration Manager environment](https://support.microsoft.com/kb/3106512).  

> [!NOTE]  
>  Amikor módosítja egy hely adatbázis-konfigurációját, a Configuration Manager újraindítja vagy újratelepíti a Configuration Manager szolgáltatások a helykiszolgálón és az adatbázissal kommunikáló távoli helyrendszer-kiszolgálókat.  

**Az adatbázis-konfiguráció módosításához** futtassa a telepítőt a helykiszolgálón, és válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása** lehetőséget. Ezután válassza az **SQL Server konfigurációjának módosítása** beállítást. A következő helyadatbázis-konfigurációk módosíthatók:  

-   A Windows-alapú kiszolgáló, amelyen az adatbázist.  

-   Az SQL Server azon példányát, amely az SQL Server-adatbázist tároló kiszolgálón van használatban.  

-   AZ adatbázis neve.  

-   A Configuration Manager által használt SQL Server Port  

-   A Configuration Manager által használt SQL Server Service Broker port  

**Ha áthelyezi a helyadatbázist, konfigurálnia kell a következő:**  

-   **Hozzáférés konfigurálása:** Amikor új számítógépre helyezi át a helyadatbázist, adja hozzá a helykiszolgáló számítógépfiókjának a **helyi rendszergazdák** csoporthoz az SQL Server rendszert futtató számítógépen. Ha a helyadatbázist SQL Server-fürtön tárolja, a számítógépfiókot hozzá kell adni a **Helyi rendszergazdák** csoporthoz a Windows Server-fürt minden csomópont-számítógépén.  

-   **Engedélyezze a közös nyelvi futtatókörnyezet (CLR) integrációját:**  Ha az adatbázist áthelyezi az SQL Server új példányára vagy egy új SQL Server rendszerű számítógépre, engedélyeznie kell a közös nyelvi futtatókörnyezet (CLR) integrációját. Engedélyezze a közös nyelvi futtató környezet az **SQL Server Management Studio** csatlakozzon a helyadatbázist futtató SQL Server-példányához, és futtassa a következő tárolt eljárást lekérdezésként: **sp_configure 'clr enabled', 1; konfigurálja újra a**.  
-  **Gondoskodjon arról, hogy az új SQL Server hozzáfér a biztonsági mentési helyre:** Ha UNC tárolja a biztonsági másolat a helyhez, helyezze át az adatbázist egy SQL Server AlwaysOn rendelkezésre állási csoport áthelyezésre például az új kiszolgáló vagy SQL Server-fürtöt használ, győződjön meg arról, az új SQL-kiszolgáló számítógépfiókja rendelkezik **írási** engedélyek az UNC helyre.  


> [!IMPORTANT]  
>  Mielőtt áthelyez egy adatbázist, amelynek egy vagy több adatbázis-replikája van a felügyeleti pontokhoz, először el kell távolítania az adatbázis-replikákat. Az adatbázis áthelyezése után újrakonfigurálhatja az adatbázis-replikákat. További információ: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

##  <a name="bkmk_SPN"></a>Az egyszerű Szolgáltatásnevet a Helyadatbázis-kiszolgáló kezelése  
A következőképpen választhatja ki az SQL-szolgáltatásokat futtató fiókot a helyadatbázishoz:  

-   Ha a szolgáltatásokat a számítógép rendszerfiókja futtatja, a rendszer automatikusan regisztrálja az egyszerű szolgáltatásnevet.  

-   Ha a szolgáltatásokat egy tartományi helyi felhasználói fiók futtatja, manuálisan kell regisztrálnia az egyszerű szolgáltatásnevet annak biztosítása érdekében, hogy az SQL-ügyfelek és a helyrendszer más tagjai Kerberos-hitelesítést tudjanak végezni. Kerberos-hitelesítés nélkül az adatbázissal való kommunikáció meghiúsulhat.  

Az SQL Server dokumentációjában talál segítséget [az egyszerű szolgáltatásnév manuális regisztráláshoz](https://technet.microsoft.com/library/ms191153\(v=sql.120\).aspx), és tudhat meg többet az egyszerű szolgáltatásnevekről és a Kerberos-kapcsolatokról.  

> [!IMPORTANT]  
>  -   Amikor fürtözött SQL Server-példányhoz hoz létre egyszerű szolgáltatásnevet, az SQL Server-fürt virtuális nevét kell megadnia az SQL Server rendszert futtató számítógép neveként.  
> -   A parancs, amellyel az SQL Server megnevezett példányának egyszerű szolgáltatásneve regisztrálható, ugyanaz, mint amellyel egy alapértelmezett példány egyszerű szolgáltatásnevét is regisztrálhatja, azzal a különbséggel, hogy a portszámnak meg kell egyeznie a megnevezett példány által használt porttal.  

A helyadatbázis-kiszolgáló SQL Server-szolgáltatásfiókjához a **Setspn** eszközzel konfigurálhatja az egyszerű szolgáltatásnevet. A Setspn eszközt olyan számítógépen kell futtatni, amely az SQL Server tartományában található, és a futtatáshoz tartományi rendszergazdai hitelesítő adatokra van szükség.  

 Az alábbi eljárás példa arra, hogy hogyan kezelhető az SQL Server-szolgáltatásfiók a Setspn eszközzel a Windows Server 2008 R2 rendszerben. A Setspn eszközzel kapcsolatos útmutatót a [Setspn eszközt áttekintő cikkben](http://go.microsoft.com/fwlink/p/?LinkId=226343) vagy az adott operációs rendszerhez készült hasonló dokumentációban találja.  

> [!NOTE]  
>  Az alábbi eljárások a Setspn parancssori eszköz hivatkozhat. A Setspn parancssori eszköz a rendszer a Windows Server 2003 támogatási eszközeit telepíti CD-ről vagy a a [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=100114). A Windows támogatási eszközeinek CD-ről történő telepítéséhez lásd: [A Windows támogatási eszközeinek telepítése](http://go.microsoft.com/fwlink/p/?LinkId=62270).  

#### <a name="to-manually-create-a-domain-user-service-principal-name-spn-for-the-sql-server-service-account"></a>A tartományi felhasználó egyszerű szolgáltatásnév (SPN) az SQL Server szolgáltatásfiók kézi létrehozása  

1.  A **Start** menüben kattintson a **Futtatás** parancsra, és írja be a **cmd** parancsot a Futtatás párbeszédpanelen.  

2.  A parancssorban lépjen a Windows Server támogatási eszközeinek telepítési könyvtárába. Alapértelmezés szerint ezek az eszközök találhatók a **C:\Program Files\Support Tools** könyvtár.  

3.  Írjon be egy érvényes parancsot az egyszerű szolgáltatásnév létrehozásához. Az egyszerű szolgáltatásnév létrehozásához használhatja a NetBIOS-nevét vagy az SQL Servert futtató számítógép teljesen minősített tartománynevét (FQDN). Azonban mind a NetBIOS-névhez, mind a teljes tartománynévhez létre kell hozni egy egyszerű szolgáltatásnevet.  

    > [!IMPORTANT]  
    >  Amikor fürtözött SQL Server-példányhoz hoz létre egyszerű szolgáltatásnevet, az SQL Server-fürt virtuális nevét kell megadnia az SQL Server rendszert futtató számítógép neveként.  

    -   Hozzon létre egy egyszerű Szolgáltatásnevet az SQL Server számítógép NetBIOS-nevét, írja be a következő parancsot: **setspn - A MSSQLSvc /&lt;SQL Server számítógépének neve\>: 1433 &lt;tartomány\fiók >**  

    -   Hozzon létre egy egyszerű Szolgáltatásnevet az SQL Server rendszert futtató számítógép teljes tartományneveként, írja be a következő parancsot: **setspn - A MSSQLSvc /&lt;SQL Server teljes Tartományneve\>: 1433 &lt;tartomány\fiók >**  

    > [!NOTE]  
    >  A parancs, amellyel az SQL Server elnevezett példányának egyszerű szolgáltatásneve regisztrálható, ugyanaz, mint amellyel egy alapértelmezett példány egyszerű szolgáltatásnevét is regisztrálhatja, azzal a különbséggel, hogy a portszámnak meg kell egyeznie az elnevezett példány által használt porttal.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-by-using-the-setspn-command"></a>A Setspn parancs használata annak ellenőrzésére, hogy a tartományi felhasználó egyszerű szolgáltatásnevének regisztrációja megfelelő-e  

1.  A **Start** menüben kattintson a **Futtatás** parancsra, és írja be a **cmd** parancsot a **Futtatás** párbeszédpanelen.  

2.  A parancssorba írja be a következő parancsot: **setspn -L &lt;tartomány\sql-Szolgáltatásfiók >**.  

3.  Tekintse meg a regisztrált **ServicePrincipalName** beállítást annak ellenőrzéséhez, hogy érvényes egyszerű szolgáltatásnév jött-e létre az SQL Server számára.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-when-using-the-adsiedit-mmc-console"></a>Az ADSIEdit MMC konzol használata annak ellenőrzésére, hogy a tartományi felhasználó egyszerű szolgáltatásnevének regisztrációja megfelelő-e  

1.  A **Start** menüben kattintson a **Futtatás** parancsra, és írja be az **adsiedit.msc** parancsot az ADSIEdit MMC konzol indításához.  

2.  Ha szükséges, csatlakozzon a helykiszolgáló tartományához.  

3.  A konzol ablaktáblájában bontsa ki a helykiszolgáló tartományát, **DC =&lt;kiszolgáló megkülönböztető neve\>**, bontsa ki a **CN = Users**, kattintson a jobb gombbal **CN =&lt;szolgáltatásfiók felhasználója\>**, és kattintson a **tulajdonságok**.  

4.  Az a **CN =&lt;szolgáltatásfiók felhasználója\> tulajdonságok** párbeszédpanelen tekintse át a **servicePrincipalName** győződjön meg arról, hogy érvényes egyszerű szolgáltatásnév létrehozása és a megfelelő SQL Server-számítógéphez társított értéket.  

#### <a name="to-change-the-sql-server-service-account-from-local-system-to-a-domain-user-account"></a>Az SQL Server-szolgáltatásfiók módosítása a helyi rendszerről egy tartományi felhasználói fiókra  

1.  Hozzon létre vagy válasszon ki egy tartományi vagy helyi rendszerbeli felhasználói fiókot, amelyet az SQL Server szolgáltatásfiókjaként szeretne használni.  

2.  Nyissa meg az **SQL Server Configuration Manager** eszközt.  

3.  Kattintson a **SQL Server Services**, majd kattintson duplán **SQL Server&lt;PÉLDÁNYNÉV\>**.  

4.  A **Bejelentkezés** lapon válassza az **Ez a fiók** elemet, majd írja be az 1. lépésben a tartományi felhasználói fiókhoz létrehozott felhasználónevet és jelszót, vagy a **Tallózás** gombra kattintva keresse meg a felhasználói fiókot az Active Directory tartományi szolgáltatásokban, és kattintson az **Alkalmaz** gombra.  

5.  Kattintson az **Igen** gombra a **Módosítás megerősítése** párbeszédpanelen a szolgáltatásfiók módosításának megerősítéséhez és az SQL Server-szolgáltatás újraindításához.  

6.  Miután sikeresen módosította a szolgáltatásfiókot, kattintson az **OK** gombra.  

##  <a name="bkmk_reset"></a>Hely alaphelyzetbe állítása  
 A hely alaphelyzetbe állításának egy központi adminisztrációs helyen vagy elsődleges helyen való végrehajtásakor a hely a következőket végzi el:  

-   Újra alkalmazza a alapértelmezett Configuration Manager fájl és beállításjegyzék-engedélyeket  

-   Újratelepíti a helyen lévő összes helyösszetevőt és helyrendszerszerepkört.  

A másodlagos helyek nem támogatják a hely alaphelyzetbe állítását.  

A helyek alaphelyzetbe állítása végrehajtható manuálisan, de automatikusan is futtatható a hely konfigurációjának módosítása után.  

Például ha a Configuration Manager-összetevők által használt fiókok változás történt, érdemes manuális hely alaphelyzetbe állításával annak érdekében, hogy a hely összetevőinek frissítése használni az új fiók adatait. Azonban ha módosítja egy hely ügyfél- vagy kiszolgálónyelveket, a Configuration Manager automatikusan alaphelyzetbe állítja a helyet, mert az alaphelyzetbe állítás szükség, mielőtt egy helyet használhatja ezt a módosítást.  

> [!NOTE]  
>  A hely alaphelyzetbe állítása nem állítja alaphelyzetbe a hozzáférési engedélyek nem Configuration Manager - objektum.  

A következők történnek egy hely alaphelyzetbe állításakor:  

1.  A telepítő leállítja és újraindítja a **SMS_SITE_COMPONENT_MANAGER** szolgáltatás és a szálösszetevőit a **SMS_EXECUTIVE** szolgáltatás.  

2.  A telepítő eltávolítja, majd újra létrehozza a helyrendszer megosztási mappáját és a **SMS Executive** összetevőt a helyi számítógépen és a távoli helyrendszeri számítógépeken.  

3.  A telepítő újraindítja a **SMS_SITE_COMPONENT_MANAGER** szolgáltatást, ez a szolgáltatás telepíti az **SMS_EXECUTIVE** és a **SMS_SQL_MONITOR** szolgáltatások.  

A hely alaphelyzetbe állítása visszaállítja a következő objektumokat is:  

-   Az **SMS** vagy a **NAL** beállításkulcsot és a kulcs alatti alapértelmezett alkulcsokat.  

-   A Configuration Manager könyvtárfában, és bármely alapértelmezett fájlok és alkönyvtárak a könyvtárfában.  

**A hely alaphelyzetbe állításának előfeltételei**  

A hely alaphelyzetbe állításához használt fióknak a következő engedélyekkel kell rendelkezni:  

-   A hely alaphelyzetbe állításához használt fióknak a következő engedélyekkel kell rendelkezni:  

    -   **Központi adminisztrációs hely**: A hely ezen a helyen alaphelyzetbe állításához használt fióknak helyi rendszergazdai jogosultsággal kell rendelkeznie a központi felügyeleti hely kiszolgálóján, és egyenértékű jogosultságokkal kell rendelkeznie a **teljes körű rendszergazda** szerepköralapú felügyeleti biztonsági szerepkörével.  

    -   **Elsődleges hely**: A hely ezen a helyen alaphelyzetbe állításához használt fióknak helyi rendszergazdai jogosultsággal kell rendelkeznie az elsődleges hely kiszolgálóján, és egyenértékű jogosultságokkal kell rendelkeznie a **teljes körű rendszergazda** szerepköralapú felügyeleti biztonsági szerepkörével. Ha az elsődleges hely központi felügyeleti hellyel rendelkező hierarchiában van, ez a fiók a központi felügyeleti hely kiszolgálóján is helyi rendszergazdáé lehet.  

**A hely alaphelyzetbe állítása vonatkozó korlátozások**
  -    1602-es verziójától kezdve, módosíthatja a kiszolgáló állítja a helyet, és a nem felhasználói nyelvi csomagokat, feltéve, hogy a hierarchia támogatására van konfigurálva, a helyek telepített [ügyfélfrissítések tesztelése egy üzem előtti gyűjtemény](/sccm/core/clients/manage/upgrade/test-client-upgrades).

#### <a name="to-perform-a-site-reset"></a>Hely alaphelyzetbe állításának végrehajtása  

1.  Futtatás **a Configuration Manager telepítő** a  **&lt;Configuration Manager hely telepítési mappája\>\BIN\X64\setup.exe**.  

    > [!TIP]  
    >  Futtathatja a hely által a Configuration Manager telepítő indítása alaphelyzetbe állítja a **Start** menüjéből vagy a Configuration Manager forrás-adathordozóján a helykiszolgáló számítógépén.  

2.  A **Kezdeti lépések** oldalon válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása**lehetőséget, és kattintson a **Tovább**gombra.  

3.  A **Helykarbantartás** oldalon válassza az **A hely konfigurációs módosítások nélküli alaphelyzetbe állítása** lehetőséget, és kattintson a **Tovább** gombra.  

4.  A hely alaphelyzetbe állításának elkezdéséhez kattintson az **Igen** gombra.  

Amikor befejeződik a hely alaphelyzetbe állítása, az eljárás befejezéséhez kattintson a **Bezárás** gombra.  

##  <a name="bkmk_sitelang"></a>A hely nyelvi csomagjainak kezelése  
Egy hely telepítése után módosíthatja a kiszolgálókon és az ügyfeleken használt nyelvi csomagokat:  

**Kiszolgálói nyelvi csomagokat:**  

-   **Vonatkozik:**  

     Configuration Manager konzol telepítése  

     Az alkalmazható helyrendszerszerepkörök új telepítései  

-   **Részletek:**  

     Miután frissítette a helyen a kiszolgálói nyelvi csomagokat, a nyelvi csomagok támogatása a Configuration Manager konzolok is hozzáadhat.  

     A kiszolgálói nyelvi csomagnak támogatásához a Configuration Manager-konzolra, telepítenie kell a Configuration Manager konzolt a **ConsoleSetup** mappájában a helykiszolgálón, amely a használni kívánt nyelvi csomagot is tartalmazza. Ha a Configuration Manager konzol már telepítve van, akkor először el kell távolítani ahhoz, hogy az új telepítést, amelyiknél a támogatott nyelvi csomagok aktuális listáját.  

**Ügyféloldali nyelvi csomagokat:**  

-   **Vonatkozik:**  

     Az ügyfelek nyelvi csomagjainak változásai hatására úgy frissülnek az ügyféltelepítési forrásfájlok, hogy az ügyfelek új telepítései és frissítései az ügyfélnyelvek frissített listájához biztosítsanak támogatást.  

-   **Részletek:**  

     Miután a helyen frissítette az ügyféli nyelvi csomagokat, azokat az ügyféli nyelvi csomagokat is magába foglaló forrásfájlok használatával telepíteni kell minden olyan ügyfélnél, amelyik a nyelvi csomagot használni fogja.  

A Configuration Manager által támogatott ügyfél és kiszolgáló nyelvek kapcsolatos információkért lásd: [nyelvi csomagokat a System Center Configuration Managerben](../../../core/servers/deploy/install/language-packs.md)  

#### <a name="to-modify-the-language-packs-that-are-supported-at-a-site"></a>A hely által támogatott nyelvi csomagok összetételének megváltoztatása  

1.  A helykiszolgálón futtatja a Configuration Manager  **&lt;Configuration Manager hely telepítési mappája\>\BIN\X64\setup.exe.**  

2.  A **Kezdeti lépések** oldalon válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása** lehetőséget, és kattintson a **Tovább** gombra.  

3.  A **Helykarbantartás** oldalon válassza a **Nyelvkonfiguráció módosítása** lehetőséget, és kattintson a **Tovább** gombra.  

4.  Az **Előfeltételek letöltése** oldalon válassza a **Szükséges fájlok letöltése** lehetőséget, hogy megszerezze a nyelvi csomagokat, vagy válassza a **Korábban letöltött fájlok használata** lehetőséget, hogy a nyelvi csomagokat is tartalmazó előzőleg letöltött fájlokat használja a helyhez hozzáadásra. A **Tovább** gombra kattintva érvényesítheti a fájlokat és továbbléphet.  

5.  A **Kiszolgáló nyelvének kiválasztása** oldalon jelölje be a hely által támogatott kiszolgálói nyelveket, majd kattintson a **Tovább** gombra.  

6.  Az **Ügyfélnyelv kiválasztása** oldalon jelölje be a hely által támogatott ügyfélnyelveket, majd kattintson a **Tovább** gombra.  

7.  Kattintson a **Tovább** gombra, hogy módosítsa a hely nyelvi támogatását.  

    > [!NOTE]  
    >  A Configuration Manager kezdeményezi a hely alaphelyzetbe állítását, amelyik újratelepít minden helyrendszer-szerepkört a helyen.  

8.  Az eljárás befejezéséhez kattintson a **Bezárás** gombra.  

##  <a name="BKMK_ModDBAlert"></a>Az adatbázis-kiszolgáló riasztási küszöbértékének módosítása  
 Alapértelmezés szerint a Configuration Manager riasztásokat állít elő, ha kevés a szabad lemezterület egy Helyadatbázis-kiszolgálón. Alapértelmezés szerint 10 GB vagy kevesebb szabad lemezterület esetén figyelmeztetés, 5 GB vagy kevesebb szabad lemezterület esetén pedig kritikus riasztás jön létre. Az értékeket módosíthatja, vagy akár le is tilthatja a riasztásokat az egyes helyekhez.  

 A beállítások módosításához tegye a következőket:  

1.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Helyek**lehetőségre.  

2.  Válassza ki a helyet, amelyet szeretne konfigurálni, majd nyissa meg, hogy a hely **tulajdonságok**.  

3.  A hely **tulajdonságok** párbeszédpanelen jelölje ki a **riasztási** lapra, majd szerkessze a beállításokat.  

4.  Kattintson az **OK** gombra a helytulajdonságok párbeszédpanelének bezárásához.  

