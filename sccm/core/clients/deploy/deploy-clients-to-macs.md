---
title: "Mac-ügyfelek központi telepítése |} Microsoft Docs"
description: "Útmutató: az ügyfelek központi telepítése Mac számítógépekre a System Center Configuration Managerben."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 6ce212c6745b70a47553891e5dbc124b4c4e50fa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-macs"></a>Ügyfélszoftverek központi telepítése Mac-számítógépekre

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ismerteti, hogyan helyezhet üzembe és karbantartása a Configuration Manager-ügyfél Mac számítógépeken. Rendelkezik konfigurálása előtt ügyfelek központi telepítése Mac számítógépekre, lásd: [ügyfélszoftver központi telepítése Mac-számítógépekre történő előkészítéséhez](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients).

Ha egy új ügyfél Mac számítógépekre telepíti, lehetséges, hogy is a Configuration Manager frissítéseinek tükrözzék az új ügyfélinformációk megjelenjenek a Configuration Manager konzol telepítéséhez.

Ezekkel az eljárásokkal az ügyféltanúsítványok telepítése két lehetősége van. További információk a Mac számítógépek ügyféltanúsítványainak [ügyfélszoftver központi telepítése Mac-számítógépekre történő előkészítéséhez](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements).  

-   Használja a Configuration Manager beléptetést a [CMEnroll eszköz](#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). A beléptetési folyamat nem támogatja az automatikus tanúsítványmegújítást, ezért a Mac számítógépeket a telepített tanúsítvány lejárta előtt újra be kell léptetni.    

-   [A tanúsítvány lekérését és telepítését módszer, amely független a Configuration Manager](#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager). 

>[!IMPORTANT]
>  Az ügyfél eszközökre telepíteni kívánt macOS Sierra fut, a tulajdonos nevét a felügyeleti pont tanúsítványának kell megfelelően kell konfigurálni, például a a felügyeletipont-kiszolgáló teljes Tartományneve.


## <a name="configure-client-settings-for-enrollment"></a>A beléptetéshez szükséges ügyfélbeállítások konfigurálása  
 Kell használnia a [alapértelmezett ügyfélbeállítások](../../../core/clients/deploy/about-client-settings.md) beléptetés Mac számítógépekhez; beállítása nem használhat egyéni ügyfélbeállításokat.  

 Erre azért szükség a Configuration Manager használatával igényelhet és telepíteni tudja a tanúsítványt a Mac  

### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>Az alapértelmezett ügyfélbeállítások a Configuration Manager segítségével igényelhessen tanúsítványokat a Mac számítógépekhez konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válassza ki a **beléptetési** szakaszt, és adja meg ezeket a beállításokat:  

    1.  **Felhasználók regisztrálhatnak a mobileszközök és Mac számítógépek: Igen**  

    2.  **Beléptetési profil:** Válasszon **profil megadása**.  

6.  Az a **mobileszköz-beléptetési profilok** párbeszédpanelen válassza ki **létrehozása**.  

7.  A **Beléptetési profil létrehozása** párbeszédpanelen adjon nevet ennek a beléptetési profilnak, majd adja meg a **Felügyeleti hely kódja**beállítás értékét. Válassza ki a Configuration Manager elsődleges helyet, amely a Mac számítógépeket kezelő felügyeleti pontokat tartalmazza.  

    > [!NOTE]  
    >  Ha nem lehet kijelölni a helyet, akkor ellenőrizze, hogy a helyen legalább egy felügyeleti pont be legyen állítva a mobileszközök kezelésére.  

8.  Válasszon **hozzáadása**.  

9. Az a **hitelesítésszolgáltató hozzáadása mobileszközökhöz** párbeszédpanelen jelölje ki a hitelesítésszolgáltató (CA) kiszolgáló, amely tanúsítványokat fog kibocsátani a Mac számítógépek.  

10. Az a **beléptetési profil létrehozása** párbeszédpanelen válassza ki azt a Mac számítógép-tanúsítvány a 3. lépésben létrehozott sablont.  

11. Kattintson a **OK** bezárásához a **beléptetési profil** párbeszédpanelen, majd a **alapértelmezett ügyfélbeállítások** párbeszédpanel megnyitásához.  

    > [!TIP]  
    >  Ha az ügyfél házirend időközt módosítani kívánja, **ügyfélházirend lekérdezési időköze** a a **ügyfélházirend** beállításcsoportban.  

 Minden felhasználó teszi ezekkel a beállításokkal a következő alkalommal ügyfélházirendet töltenek. Egy ügyfél házirend lekérésének kezdeményezéséhez, lásd: [Házirendlekérésről kezdeményezése a Configuration Manager-ügyfél](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 A beléptetési ügyfélbeállításokon kívül konfigurálja a következő ügyfél-Eszközbeállítás biztosítja:  

-   **Hardverleltár**: Engedélyezze és konfigurálja ezt, ha azt szeretné, hogy a Mac és a Windows ügyfélszámítógépekről Hardverleltár összegyűjtéséhez. További információkért lásd: [a System Center Configuration Managerben a Hardverleltár bővítése](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

-   **Megfelelőségi beállítások**: Engedélyezze és konfigurálja ezt, ha azt szeretné, kiértékelheti és javíthatja a Mac és a Windows-ügyfélszámítógépek beállításait. További információkért lásd: [tervezése és konfigurálása a megfelelőségi beállítások](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

> [!NOTE]  
>  A Configuration Manager-ügyfél beállításaival kapcsolatos további információkért lásd: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-settings.md).  

## <a name="download-the-client-source-files-for-macs"></a>Az ügyfél forrásfájljainak letöltése Mac számítógépekhez  

1.  Töltse le a Mac OS X ügyfélfájlcsomagját ( **ConfigmgrMacClient.msi**), és mentse a fájlt egy Windows rendszerű számítógépre.  

     Ez a fájl nem található meg a Configuration Manager telepítési adathordozójáról. Ezt a fájlt a [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkID=525184)töltheti le.  

2.  Futtassa a Windows számítógépen **ConfigmgrMacClient.msi** kibontásához a Mac ügyfél csomag, a helyi lemez egy mappájába Macclient.dmg (alapértelmezés szerint **C:\Program Files (x86) \Microsoft\System Center 2012 Configuration Manager Mac Client\\**).  

3.  Másolja a Macclient.dmg fájlt a Mac számítógép egyik mappájába.  

4.  A Mac számítógépen futtassa a Macclient.dmg fájlt a fájlok mappa a helyi lemezen.  

5.  A mappában győződjön meg arról, hogy a Ccmsetup és a CMClient.pkg fájl ki van bontva, és létrejött egy Tools (Eszközök) nevű mappa, amelyben megtalálható a CMDiagnostics, a CMUninstall, a CMAppUtil és a CMEnroll eszköz.

    -  **Ccmsetup**: A Configuration Manager-ügyfél a Mac számítógépekre telepíti.  

    -   **CMDiagnostics**: A Configuration Manager-ügyfél a Mac számítógépeken kapcsolatos diagnosztikai adatokat gyűjt.  

    -   **CMUninstall**: Eltávolítja az ügyfél a Mac számítógépekről.  

    -   **CMAppUtil**: Konvertálja az Apple-alkalmazáscsomagokat olyan formátumra, amely a Configuration Manager-alkalmazás telepíthető központilag.  

    -   **CMEnroll**: Kéri le és telepíti az ügyféltanúsítványt egy Mac számítógéphez, hogy telepíthesse a Configuration Manager-ügyfél.   

## <a name="install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>Telepítse az ügyfelet, és ezután regisztrálhatják az ügyféltanúsítványt a Mac gépen  

Az egyes ügyfelek regisztrálhatja a [Mac számítógép beléptetési varázslójának](#enroll-the-client-with-the-mac-computer-enrollment-wizard).

Amely lehetővé teszi a sok ügyfél igénylése automation, használja a [CMEnroll eszköz](#client-and-certificate-automation-with-cmenroll).   


###  <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>Az ügyfél és a Mac számítógép beléptetési varázslójának regisztrálása  

1.  Miután az ügyfél telepítése befejeződött, a számítógép beléptetési varázslójának nyílik meg. Ha a varázsló nem lehet megnyitni, vagy ha véletlenül bezárja azt, kattintson a **beléptetés** a a **Configuration Manager** beállításlapján való megnyitásához.  

2.  A varázsló második lapján adja meg:  

    -   **User name** (Felhasználónév) – A felhasználónév az alábbi formátumokban lehet:  

        -   "TARTOMÁNY\név". Példa: 'contoso\mnorth'  

        -   'user@domain'. Például: "mnorth@contoso.com"  

            > [!IMPORTANT]  
            >  Használatakor egy e-mail címet feltöltése a **felhasználónév** mezőben a Configuration Manager automatikusan használja az e-mail cím tartománynevével és a beléptetési proxypont kiszolgálójának alapértelmezett neve feltöltése a **kiszolgálónév** mező. Ha a tartománynév és kiszolgálónév nem egyezik a beléptetési proxypont kiszolgálójának nevét, kérje meg a felhasználókat a megfelelő nevét, amikor beléptetik Mac számítógépüket.  

         A felhasználónévnek és a hozzá tartozó jelszónak egyeznie kell egy olyan Active Directory-fiókkal, amely rendelkezik olvasási és beléptetési engedéllyel a Mac ügyféltanúsítvány-sablonhoz.  

    -   **Jelszó** -adja meg a megadott felhasználónévhez tartozó jelszót.  

    -   **Kiszolgálónév** -adja meg a beléptetési proxypont kiszolgálójának nevét.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>Ügyfél és a tanúsítvány automatizálása a CMEnroll  

Ezzel az eljárással az ügyfél telepítése és igénylése automatizálását és regisztrálása a CMEnroll eszközzel ügyféltanúsítványokat. Az eszköz futtatásához rendelkeznie kell egy Active Directory-felhasználói fiókot.

1.  A Mac számítógépen keresse meg a mappát, amelyikbe kibontotta a Macclient.dmg fájl tartalmát.  

2.  Írja be a következő parancssort: **sudo ./ccmsetup**  

3.  Várjon, amíg megjelenik a **Completed installation** (A telepítés kész) üzenet. Bár a telepítő most újraindítást kérő üzenetet jelenít meg, ne indítsa újra, és folytassa a következő lépéssel.  

4.  A Mac számítógép eszközök mappájában írja be a következőt: **sudo. / CMEnroll -s &lt;beléptetési_proxykiszolgáló_neve > - ignorecertchainvalidation -u &lt;felhasználónév ' >**  

    Az ügyfél telepítése után megnyílik a Mac számítógép Computer Enrollment (Számítógép beléptetése) varázslója a Mac számítógép beléptetéséhez. Ha ezzel a a módszerrel kívánja beléptetni az ügyfelet, olvassa el a témakör [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) című szakaszát.  

5. Írja be az Active Directory felhasználói fiók jelszavát.  Ez a parancs beírásakor a rendszer két jelszót kéri: Először a felügyelői fiók a parancs futtatásához van. Másodjára az Active Directory-fiók jelszavát kell beírni. A jelszókérések egyformák, ezért győződjön meg arról, hogy a megfelelő sorrendben írja be a jelszavakat.  

    A felhasználónév az alábbi formátumokban lehet:  

    -   "TARTOMÁNY\név". Példa: 'contoso\mnorth'  

    -   'user@domain'. Például: "mnorth@contoso.com"  

     A felhasználónévnek és a hozzá tartozó jelszónak egyeznie kell egy olyan Active Directory-fiókkal, amely rendelkezik olvasási és beléptetési engedéllyel a Mac ügyféltanúsítvány-sablonhoz.  

     Például: Ha a beléptetési proxypont kiszolgálójának neve **server02.contoso.com**, és a felhasználónevet **contoso\mnorth** lett engedélyeket a Mac ügyféltanúsítvány-sablonjához, írja be a következőt: **sudo. / CMEnroll -s server02.contoso.com – ignorecertchainvalidation -u 'contoso\mnorth'**  

    > [!NOTE]  
    >  Ha a felhasználónév a karakterek valamelyikét tartalmazza  **&lt;> "+=,** beléptetés sikertelen lesz. Szerezzen be egy sávon kívüli tanúsítványt, amelyben a felhasználónév nem tartalmazhatja a következő karaktereket.  
    >  
    >  A zökkenőmentes felhasználói élmény érdekében a telepítési lépésekről és parancsokról készíthet egy parancsfájlt, hogy a felhasználóknak csak a felhasználónevet és a jelszót kelljen megadniuk.  

5.  Várjon, amíg megjelenik a **Successfully enrolled** (A beléptetés sikerült) üzenet.  

6.  A regisztrált tanúsítvány a Configuration Manager, a Mac számítógépen nyisson meg egy terminálablakot, és hajtsa végre a következő módosításokat:  

    a.  Írja be a következő parancsot: **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**  

    b.  A a **Keychain Access** párbeszédpanel a **Keychains** területen válassza a **rendszer**, majd a a **kategória** területen válassza a **kulcsok**.  

    c.  Az ügyfél tanúsítványainak megtekintéséhez bontsa ki a kulcsokat. Ha az imént telepített privát kulccsal azonosította a tanúsítványt, kattintson duplán a kulcsra.  

    d.  Az a **hozzáférés-vezérlés** lapra, majd **megerősítés hozzáférés engedélyezése előtt**.  

    e.  Keresse meg a **Library/Application Support/Microsoft/CCM**, jelölje be **CCMClient**, és válassza a **Hozzáadás**.  

    f.  Válasszon **módosítások mentése** és zárja be a **Keychain Access** párbeszédpanel megnyitásához.  

7.  Indítsa újra a Mac számítógépet.  

 Ellenőrizze az ügyféltelepítés sikerességét a Mac számítógép **System Preferences** (Rendszerbeállítások) beállításában a **Configuration Manager** elem megnyitásával. Frissítheti és megtekintheti a **Minden rendszer** gyűjteményt is, és meggyőződhet arról, hogy a Mac számítógép része a gyűjteménynek mint felügyelt ügyfél.  

> [!TIP]  
>  A Mac-ügyfél megoldhatja, használhatja a következő diagnosztikai információt gyűjthet a Mac OS X ügyfélcsomag részét képező CMDiagnostics programot:  
>   
>  -   Futó folyamatok listája  
> -   A Mac OS X operációs rendszer verziója  
> -   Mac OS X rendszer a Configuration Manager-ügyfél, beleértve a vonatkozó jelentések **CCM\*.crash** és **System Preference.crash**.  
> -   A Anyagjegyzékfájl (BOM) és tulajdonságlistafájl (.plist) hozta létre a Configuration Manager-ügyfél telepítésére.  
> -   A /Library/Application Support/Microsoft/CCM/Logs mappa tartalma.  
>   
>  A CmDiagnostics által gyűjtött adatok egy zip-fájl, amely a számítógép asztalára ment és nevű cmdiag - hozzáadódik*< hostname\>***-***&gt;dátum és idő\>*. zip.* **


##  <a name="use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a>A tanúsítvány lekérését és telepítését módszer, amely független a Configuration Manager  

Először, ezek folyamatban speciális feladatokat a [ügyfélszoftver központi telepítése Mac-számítógépekre történő előkészítéséhez](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients):

1. [Helyrendszer-kiszolgálók egy webkiszolgáló-tanúsítvány telepítése](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-web-server-certificate-to-site-system-servers)

2. [Ügyfél-hitelesítési tanúsítvány központi telepítése a helyrendszer-kiszolgálókon](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-client-authentication-certificate-to-site-system-servers)

3. [A felügyeleti pont és terjesztési pont konfigurálása](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#configure-the-management-point-and-distribution-point)

4. [Nem kötelező: A jelentéskészítési szolgáltatási pont telepítése](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#install-the-reporting-services-point)

Ezután hajtsa végre ezeket a feladatokat:

5. [Az ügyfél forrásfájljainak letöltése Mac számítógépekhez](#download-the-client-source-files-for-macs) .  
6. Kövesse az utasításokat, amelyek a kiválasztott tanúsítvány lekéréséhez és telepítéséhez az ügyféltanúsítványt a Mac számítógép központi telepítési módszerét kísérik.  
7.  Keresse meg azt a mappát, amelyikbe kibontotta a Microsoft letöltőközpontból beszerzett Macclient.dmg fájl tartalmát.  

3.  Írja be a következő parancssort: **sudo. / ccmsetup – MP < felügyeleti pont internetes teljes tartománynév\> - SubjectName < tanúsítvány tárgy értéke\>**.  A tanúsítvány tárgyában a kisbetűket és nagybetűket pontosan ugyanúgy kell megadni, ahogy a tanúsítvány részleteinél látható.  

     Például: Ha az internetes FQDN a helyrendszer tulajdonságainál van **server03.contoso.com** és a Mac ügyfél tanúsítványán az FQDN **mac12.contoso.com** közös névként a tanúsítvány tárgyában csupa kisbetűvel, írja be: **sudo. / ccmsetup – MP server03.contoso.com – SubjectName mac12.contoso.com**  

4.  Várjon, amíg megjelenik a **Completed installation** (A telepítés kész) üzenet, és indítsa újra a Mac számítógépet.  

5.  Győződjön meg arról, hogy elérhető-e a Configuration Manager, a Mac számítógépen-e a tanúsítvány, nyisson meg egy terminálablakot, és ezeket a módosításokat:  

    a.  Írja be a következő parancsot: **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**  

    b.  A a **Keychain Access** párbeszédpanel a **Keychains** területen válassza a **rendszer**, majd a a **kategória** területen válassza a **kulcsok**.  

    c.  Az ügyfél tanúsítványainak megtekintéséhez bontsa ki a kulcsokat. Ha az imént telepített privát kulccsal azonosította a tanúsítványt, kattintson duplán a kulcsra.  

    d.  Az a **hozzáférés-vezérlés** lapra, majd **megerősítés hozzáférés engedélyezése előtt**.  

    e.  Keresse meg a **Library/Application Support/Microsoft/CCM**, jelölje be **CCMClient**, és válassza a **Hozzáadás**.  

    f.  Válasszon **módosítások mentése** és zárja be a **Keychain Access** párbeszédpanel megnyitásához.  

6.  Ha egynél több tanúsítványa van, amelyikben a tárgy értéke ugyanaz, meg kell adnia a tanúsítvány sorozatszámát, hogy azonosítsa a Configuration Manager-ügyfél használni kívánt tanúsítványt. Ehhez a következő paranccsal: **sudo defaults write com.microsoft.ccmclient SerialNumber-data "< sorozatszám\>"**.  

     Például így: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Győződjön meg arról, hogy az ügyfél telepítése sikeres megnyitásával a **Configuration Manager** elemnek, **rendszerbeállítások** a macre. Is frissítheti és megtekintheti a **minden rendszer** győződjön meg arról, hogy a Mac megjelenik-e a gyűjteménynek mint felügyelt ügyfél-gyűjteményben.  

## <a name="renewing-the-mac-client-certificate"></a>A Mac-ügyfél tanúsítványának megújítása  
 A Mac számítógépeken a számítógép tanúsítványának megújítása előtt használja a következő eljárást.  

 Ez a folyamat eltávolítja az SMS-azonosítót, ez azért szükséges, hogy az ügyfél a Mac számítógépen az új vagy megújított tanúsítványt használja.  

> [!IMPORTANT]  
>  Amikor eltávolítja és pótolja ügyfélelőzmény, köztük a leltár tárolt ügyfél korábbi törlődik, az ügyfél a Configuration Manager konzoljáról törlése után.  

### <a name="to-renew-the-mac-client-certificate"></a>A Mac-ügyfél tanúsítványának megújítása  

1.  Hozzon létre, és egy eszközgyűjteményt azon Mac számítógépek számára, amely megújítja a számítógép-tanúsítványok feltöltése.  

2.  Az **Eszközök és megfelelőség** munkaterületen indítsa el a **Konfigurációelem létrehozása varázslót**.  

3.  A varázsló **Általános** lapján adja meg az alábbi adatokat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Típus:Mac OS X**  

4.  A varázsló **Támogatott platformok** lapján győződjön meg arról, hogy a Mac OS X minden verziója ki van jelölve.  

5.  A varázsló **Beállítások** lapján kattintson az **Új** elemre, és a **Beállítás létrehozása** párbeszédpanelen adja meg a következő adatokat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Beállítás típusa:Parancsfájl**  

    -   **Adattípus:Karakterlánc**  

6.  A **Beállítás létrehozása** párbeszédpanelen a **Felderítési parancsfájl**beállításban kattintson a **Parancsfájl hozzáadása** lehetőségre olyan parancsfájl megadásához, amely felderíti a konfigurált SMS-azonosítóval rendelkező Mac számítógépeket.  

7.  A **Felderítési parancsfájl szerkesztése** párbeszédpanelen adja meg a következő héjparancsfájlt:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Válasszon **OK** bezárásához a **felderítési parancsfájl szerkesztése** párbeszédpanel megnyitásához.  

9. Az a **beállítás létrehozása** párbeszédpanelen a **szervizelési parancsfájl (nem kötelező)**, válassza a **parancsfájl hozzáadása** adhatja meg, hogy eltávolítja az SMS-AZONOSÍTÓT, a Mac számítógépeken talált parancsprogramot.  

10. A **Szervizelési parancsfájl létrehozása** párbeszédpanelen adja meg a következő héjparancsfájlt:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Válasszon **OK** bezárásához a **szervizelési parancsfájl létrehozása** párbeszédpanel megnyitásához.  

12. A a **megfelelőségi szabályok** lapon válassza ki a varázsló **új**, majd a a **szabály létrehozása** párbeszédpanelen adja meg a következő információkat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Kiválasztott beállítás:** Válasszon **Tallózás** , és jelölje ki a korábban megadott felderítési parancsfájlt.  

    -   A **következő értékek** mezőbe írja be a következőt: **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Engedélyezze a **Futtassa a megadott szervizelési parancsfájlt, ha a beállítás nem megfelelő**beállítást.  

13. Fejezze be a Konfigurációelem létrehozása varázslót.  

14. Hozzon létre egy referenciakonfigurációt, amely tartalmazza az előbb létrehozott konfigurációs elemet, és ezt telepítse központilag az 1. lépésben létrehozott eszközgyűjteményre.  

     Hozzon létre és alapkonfigurációk központi telepítése kapcsolatos további információkért lásd: [referenciakonfigurációk létrehozása a System Center Configuration Managerben](../../../compliance/deploy-use/create-configuration-baselines.md).  

15. Miután olyan új tanúsítványt telepített Mac számítógépekre, amelyikről az SMSID el lett távolítva, futtassa a következő parancsot, hogy az ügyfelet az tanúsítvány használatára konfigurálja:  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <Subject_Name_of_New_Certificate>  
    ```  

16. Ha egynél több tanúsítványa van, amelyikben a tárgy értéke ugyanaz, akkor meg kell adni a tanúsítvány sorozatszámát, hogy azonosítsa a Configuration Manager-ügyfél használni kívánt tanúsítványt. Ehhez a következő paranccsal: **sudo defaults write com.microsoft.ccmclient SerialNumber-data "< sorozatszám\>"**.  

     Például így: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. Indítsa újra.  


## <a name="see-also"></a>További információ

[Mac rendszerű ügyfelek kezelése](/sccm/core/clients/manage/maintain-mac-clients)

