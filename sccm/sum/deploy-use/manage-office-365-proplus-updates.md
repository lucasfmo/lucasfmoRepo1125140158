---
title: "Office 365 ProPlus-frissítések kezelése |} Microsoft Docs"
description: "A Configuration Manager szinkronizálja az Office 365 ügyfélfrissítéseit a WSUS-katalógusban a kiszolgálóra a ügyfelekre történő központi telepítéséhez rendelkezésre álló frissítések."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 016580dc6ee3c5268833db941d42416a976d201c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="manage-office-365-proplus-with-configuration-manager"></a>Kezelheti az Office 365 ProPlus a Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager szinkronizálja az Office 365 asztali ügyfél frissítéseit, és elérhetővé válnak ügyfelekre történő központi telepítéséhez és az Office 365 telepítve. A Configuration Manager verziója 1610 kezdve áttekintheti Office 365 ügyfél-információ az Office 365-ügyfél kezelési irányítópulton.

A Configuration Manager 1602-es verziójával kezdve a Configuration Manager képes kezelni az Office 365 asztali ügyfél frissítéseit a szoftverfrissítés-felügyeleti munkafolyamat használatával rendelkezik. Amikor a Microsoft egy új Office 365-ügyfél frissítését a az Office Content Delivery Network (CDN), a Microsoft is közzétesz egy frissítési csomagot, a Windows Server Update Services (WSUS). A Configuration Manager szinkronizálja az Office 365 ügyfélfrissítés a WSUS-katalógusban a helykiszolgálóra, miután a frissítés érhető el ügyfelekre történő központi telepítéséhez.

1702 verziójától kezdve, megkezdheti az Office 365 Installer segítségével kezdeti Office 365 könnyebb élmény telepítése az Office 365-ügyfél kezelési irányítópulton. A varázsló lehetővé teszi Office 365-telepítési beállítások konfigurálása, fájlokat tartalom kézbesítési hálózatokon (tartalomtovábbító), töltse le és alkalmazás létrehozását és telepítését egy parancsfájl a tartalomhoz.

## <a name="office-365-client-management-dashboard"></a>Az Office 365-ügyfél kezelési irányítópult  
A Configuration Manager verziója 1610 kezdve, az Office 365-ügyfél kezelési irányítópult érhető el a Configuration Manager konzolon. Az irányítópult megtekintéséhez lépjen **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése**.

Az irányítópult a következő diagramot jelenít meg:

- Office 365-ügyfelek száma
- Az Office 365-ügyfél verziója
- Az Office 365 ügyfélnyelveket
- Az Office 365-ügyfél csatornák     
További információkért lásd: [frissítés áttekintése az Office 365 ProPlus csatornák](https://technet.microsoft.com/library/mt455210.aspx).
<!--- - Automatic deployment rules with Office 365 apps (have Office 365 Client selected in the set of available products). --->

<!---You can take the following actions on the dashboard:
- --->

Az irányítópult tetején, használja a **gyűjtemény** legördülő a beállítást, ha az irányítópult adatokat egy adott gyűjtemény tagjai.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Adatok megjelenítése az Office 365-ügyfél kezelési irányítópult
Az Office 365-ügyfél kezelési irányítópulton megjelenő adatok Hardverleltár származik. A Hardverleltár engedélyezni kell és ki kell választania a **Office 365 ProPlus konfigurációk** hardverleltárosztály előtt az irányítópulton megjelenő adatok.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Adatok megjelenítése az Office 365-ügyfél kezelési irányítópult
1. Hardverleltár engedélyezése, ha még nincs engedélyezve. További információkért lásd: [konfigurálása a Hardverleltár](\sccm\core\clients\manage\configure-hardware-inventory).
2. A Configuration Manager-konzolon lépjen a **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  
3. A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  
4. Az **Alapértelmezett ügyfélbeállítások** párbeszédpanelen kattintson a **Hardverleltár**elemre.  
5. Válassza az **Eszközbeállítások** lista **Osztályok beállítása**elemét.  
6. Az a **Hardverleltárosztályok** párbeszédpanelen jelölje ki **Office 365 ProPlus konfigurációk**.  
7.  A módosítások mentéséhez kattintson az **OK** gombra, és zárja be a **Hardverleltárosztályok** párbeszédpanelt.  
Az Office 365-ügyfél kezelési irányítópult adatok megjelenítése Hardverleltár jelentésekor elindul.

## <a name="deploy-office-365-updates-with-configuration-manager"></a>Office 365-frissítések a Configuration Managerrel
A következő lépésekkel telepítheti az Office 365-frissítések Configuration Managerbe:

1.  [A követelmények ellenőrzéséhez](https://technet.microsoft.com/library/mt628083.aspx) számára az Office 365-ügyfélfrissítések kezelése a Configuration Manager segítségével a **Office 365-ügyfélfrissítések kezelése a Configuration Manager segítségével követelményei** a témakör szakaszát.  

2.  [Konfigurálja a szoftverfrissítési pontok](../get-started/configure-classifications-and-products.md) az Office 365-ügyfél szinkronizálása érdekében. Állítsa be **frissítések** a besorolás, és válassza ki a **Office 365-ügyfél** termék. Lehetséges, hogy legalább egy alkalommal, mielőtt az Office 365-ügyfél termék kiválaszthatja szoftverfrissítések szinkronizálását. Kell szinkronizálja a szoftverfrissítéseket, Miután konfigurálta a szoftverfrissítési pontok használata a **frissítések** besorolást.
3.  Engedélyezi az Office 365-ügyfelek is kaphatnak frissítéseket a Configuration Manager alkalmazásból. Ehhez használja a Configuration Manager-ügyfél beállításainak, vagy a csoportházirenddel. Ahhoz, hogy az ügyfél használja a következő módszerek egyikét:  
    - 1. módszer: A Configuration Manager verziója 1606 verziótól kezdve használhatja a Configuration Manager-ügyfél kezelése az Office 365-ügyfélügynök beállítása. Miután konfigurálja ezt a beállítást, és Office 365-frissítéseket, a Configuration Manager-ügyfél ügynöke Office 365-frissítések letöltése a terjesztési pontról, és telepítheti az Office 365 ügyfélügynök kommunikál. A Configuration Manager az Office 365 ProPlus ügyfél beállítások leltárt készít.
      1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **áttekintése** > **ügyfélbeállítások**.  

      2.  Nyissa meg a megfelelő eszközbeállítások az ügyfélügynök engedélyezése. További információ az alapértelmezett és egyéni ügyfélbeállítások: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md).  

      3.  Kattintson a **szoftverfrissítések** válassza **Igen** a a **az Office 365 ügyfélügynök-kezelés engedélyezéséhez** beállítás.  

    - 2. módszer: [Engedélyezi az Office 365-ügyfelek is kaphatnak frissítéseket](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient) a Configuration Manager az Office-telepítő eszköz vagy a csoportházirend használatával.  

4. [Az Office 365-frissítések](deploy-software-updates.md) az ügyfelek számára.   

> [!Important]
> Ha egy Office 365-ügyfél egynél több nyelv, és kevesebb nyelvű frissítések letöltése, a frissítések telepítése sikertelen lesz. Például tegyük fel, az Office 365-ügyfél en-us és de-de. A helykiszolgálón, hogy letöltési és központi telepítése csak en-us tartalom az Office 365 alkalmazható frissítés. Amikor a felhasználó megkezdi a telepítését, a frissítés a Szoftverközpontból, a frissítés lefagy a tartalom letöltése során. Töltse le, és az Office 365-ügyfélként azonos nyelvű frissítések központi telepítéséhez.  


## <a name="add-other-languages-for-office-365-update-downloads"></a>Adja hozzá a többi nyelvet az Office 365 letölthető frissítés
A Configuration Manager verziója 1610 verziótól kezdve támogatás a Configuration Manager letölteni a frissítéseket a függetlenül attól, hogy azok támogatottak a Configuration Manager Office 365 által támogatott nyelvet adhat hozzá.
> [!IMPORTANT]  
> További Office 365 frissítési nyelveket konfigurálása egy olyan helyre kiterjedő beállítás. Az alábbi eljárás segítségével hozzáadta a nyelveket, az összes Office 365 frissítéseit a rendszer letölti azokat a nyelveket, valamint a nyelveket, amelyek a nyelv kiválasztása lapon töltse le a szoftverfrissítéseket és a szoftverfrissítések központi telepítése varázslók.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>Letölteni a frissítéseket további nyelvek támogatását
Az alábbi eljárással a központi adminisztrációs hely vagy önálló elsődleges hely, ahol telepítve van-e az a szoftverfrissítési pont hely rendszer szerepkört.
1. A parancssorba írja be az *wbemtest* egy rendszergazda felhasználóként nyissa meg a Windows Management Instrumentation – tesztelés.
2. Kattintson a **Connect**, majd írja be *root\sms\site_&lt;Helykód&gt;*.
3. Kattintson a **lekérdezés**, és futtassa a következő lekérdezés: *válassza ki a &#42; SMS_SCI_Component a ahol most letölthető a KomponensNév = "SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![A WMI-lekérdezés](..\media\1-wmiquery.png)
4. Az eredménypanelen kattintson duplán az objektum a központi adminisztrációs hely vagy önálló elsődleges hely helykódját.
5. Válassza ki a **tulajdonságai** tulajdonság, kattintson a **tulajdonság szerkesztése**, és kattintson a **nézet beágyazott**.
![Tulajdonságainak szerkesztése](..\media\2-propeditor.png)
6. Az első lekérdezés eredménye kezdődő nyissa meg az egyes objektumok, amíg meg nem látja a másikat **AdditionalUpdateLanguagesForO365** a a **PropertyName** tulajdonság.
7. Válassza ki **érték2** kattintson **tulajdonság szerkesztése**.  
![A érték2 tulajdonság szerkesztése](..\media\3-queryresult.png)
8. Adja hozzá a további nyelveket a **érték2** tulajdonság, és kattintson **tulajdonság mentése**.  
Például, pt-pt (a portugál - Portugália), af-za (a Afrikaans - Dél-afrikai), nn-no (a norvég (Nynorsk) - Norvégia), stb.  
![A Tulajdonságszerkesztő nyelvek hozzáadása](..\media\4-props.png)  
9. Kattintson **Bezárás**, kattintson **Bezárás**, kattintson **tulajdonság mentése**, kattintson **objektum mentése** (ha kattint **Bezárás** itt nem őrződnek meg az értékeket), kattintson **Bezárás**, és kattintson a **kilépéshez** kilép a Windows Management Intstrumentation tesztelés.
10. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése** > **az Office 365 frissítéseit**.
11. Most, amikor Office 365-frissítéseket tölt le, a frissítések a rendszer letölti a varázslóban a nyelvet és a nyelveket, ez az eljárás során konfigurált. Győződjön meg arról, hogy a frissítések letöltötte azokat a nyelveket, nyissa meg a csomag forrás-a frissítés, és keresse meg a fájlnév nyelvkódot fájlok.  
![További nyelvek fájlnevek](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>A frissítés csatorna módosítása Office 365-ügyfelek kapják a frissítéseket a Configuration Manager engedélyezése után
Office 365-ügyfelek kapják a frissítéseket a Configuration Manager engedélyezése után a frissítés csatorna módosításához a csoportházirend használatával terjesztheti a beállításjegyzék-kulcs értéke módosítás az Office 365-ügyfelek számára. Módosítsa a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** beállításkulcsot a következő értékek egyikét kell használnia:

- Jelenlegi csatorna:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- A késleltetett csatorna:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- A jelenlegi csatorna első verziójának:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- Első kiadása késleltetett csatorna:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf

## <a name="deploy-office-365-apps"></a>Az Office 365-alkalmazások telepítése  
1702 verziójától kezdve, megkezdheti az Office 365 telepítő az Office 365-ügyfél kezelési irányítópulton a kezdeti Office 365-alkalmazásra telepítés könnyebb tapasztalhat. A varázsló lehetővé teszi Office 365-telepítési beállítások konfigurálása, fájlokat tartalom kézbesítési hálózatokon (tartalomtovábbító), töltse le és alkalmazás létrehozását és telepítését egy parancsfájl a fájlokat.

Ez akkor hasznos, mert az Office 365 frissítéseit nem alkalmazható az ügyfelek nélkül telepített Office 365. Verzió 1702, mielőtt Office 365-alkalmazásokat telepíteni az ügyfeleken, először meg kell manuálisan töltse le az Office 365 központi telepítési eszköz (ODT) és az Office 365 telepítési forrásfájlok, például az összes van szüksége, nyelvi csomagokat, és a Configuration.xml fájlt, amely meghatározza a megfelelő Office-verziót és a csatorna létrehozása. Ezt követően kellene hozhat létre és telepíthet egy örökölt csomagot vagy a parancsprogram-alkalmazás az ügyfelek számára az Office 365-alkalmazások telepítéséhez.

> [!NOTE]
> - A számítógépen, amelyen az Office 365 telepítő internetkapcsolattal kell rendelkeznie.  
> - Az Office 365 telepítő futtatását végző felhasználónak rendelkeznie kell **olvasási** és **írási** a tartalom helyének megosztás eléréséhez valósul meg a varázslóban.
> - 404-es letöltési hibaüzenetet kap, ha a következő fájlokat másolja a felhasználói % temp % mappában:
>    - [releasehistory.XML](http://officecdn.microsoft.com.edgesuite.net/wsus/releasehistory.cab)
>    - [o365client_32bit.XML](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  
> - Miután létrehozott és az Office 365-telepítő használata Office 365-alkalmazások központi telepítését, a Configuration Manager nem az Office frissítéseinek kezelésére a alapértelmezés szerint. Ahhoz, hogy az Office 365-ügyfelek kapják a frissítéseket a Configuration Manager alkalmazásból, lásd: [telepítése Office 365 frissíti a Configuration Manager](#deploy-office-365-updates-with-configuration-manager).

### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Office 365 alkalmazásokat telepíteni az ügyfelek számára az Office 365-ügyfél kezelési irányítópulton
1. A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése**.
2. Kattintson a **Office 365 telepítő** a jobb felső ablaktáblán. Az Office 365 Ügyféltelepítő varázsló megnyílik.
3. Az a **Alkalmazásbeállítások** lapon adjon nevet és leírást az alkalmazás, adja meg a fájlok letöltési helyét, és kattintson a **következő**. Vegye figyelembe, hogy a helyen kell megadni az űrlap &#92; &#92; *server*&#92; *megosztás*.
4. Az a **ügyfélbeállítások importálása** lapon, válassza ki, hogy az Office 365-ügyfél beállítások importálása egy meglévő konfigurációs XML-fájl, vagy manuálisan adja meg a beállításokat, és kattintson **tovább**.  

    Ha a konfigurációs fájlt, adja meg a fájl helyét, és ugorjon a 7. Vegye figyelembe, hogy a helyen kell megadni az űrlap &#92; &#92; *server*&#92; *megosztás*&#92;* Fájlnév*. XML-KÓD.
5. Az a **ügyfél termékek** lapon válassza ki az Office 365 csomag Ön által használt, válassza ki az alkalmazásokat tartalmazza, válassza ki a további Office termékeket kell meg lehet adni, és kattintson a kívánt **következő**.
6. Az a **ügyfélbeállítások** lapon, válassza ki a beállítások közé tartoznak, és kattintson a **következő**.
7. Az a **telepítési** lapon, válassza ki, hogy az alkalmazás központi telepítése, és kattintson a **következő**.  
Ha nem kíván a varázslóban a csomag központi telepítéséhez, folytassa a 9.
8. A varázsló lapjai részében konfigurálhatók, mint a szokásos alkalmazások telepítése. További információkért lásd: [hozzon létre és telepítsen egy alkalmazást](/sccm/apps/get-started/create-and-deploy-an-application).
9. Fejezze be a varázslót.
10. Telepítése, illetve az alkalmazás szerkesztése, ugyanúgy, mint bármely más alkalmazás a Configuration Manager a **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **alkalmazások**.   

> [!IMPORTANT]
> Az Office 365-alkalmazást, amelynek létrehozása és telepítése az Office 365 varázsló a Configuration Manager használatával nem automatikusan kezeli a Configuration Manager által amíg nem engedélyezi a **felügyeletének engedélyezése az Office 365 ügyfél újra a** beállítás szoftverfrissítések ügyfélügynöke. További információkért lásd: [kapcsolatos](/sccm/core/clients/deploy/about-client-settings).

>[!NOTE]
>Office 365-alkalmazások telepítése után az alkalmazások karbantartásához automatikus központi telepítési szabályokat is létrehozhat. Az Office 365-alkalmazások automatikus telepítési szabály létrehozásához kattintson a **egy automatikus központi telepítési szabály létrehozása** az Office 365-ügyfél kezelése irányítópultot, és válassza ki a **Office 365-ügyfél** Ha úgy dönt, hogy a termék. További információkért lásd: [szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates).

<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->

