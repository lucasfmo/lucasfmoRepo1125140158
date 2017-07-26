---
title: "Telepítő parancssori kapcsolói |} Microsoft Docs"
description: "Használja fel adatokat a cikk konfigurálásához a parancsfájlokat, vagy a System Center Configuration Manager telepítése a parancssorból."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 04fe7b3e674287c4255563ab4a308e54d0b6c3aa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="command-line-options-for-setup-in-system-center-configuration-manager"></a>A System Center Configuration Manager telepítéshez használható parancssori kapcsolók

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 Használja az alábbi információkat, konfigurálhatja a parancsfájlok vagy a System Center Configuration Manager telepítése a parancssorból.  

##  <a name="bkmk_setup"></a>A telepítő parancssori kapcsolóit  
 **/ DEINSTALL**  
 Eltávolítja a helyet. A helykiszolgáló számítógépen kell futtassa a telepítőt.  

 **/ DONTSTARTSITECOMP**  
 Telepíti a helyet, de megakadályozza, hogy a Helyösszetevő-kezelő szolgáltatás elindítása. A Helyösszetevő-kezelő szolgáltatás elindul, amíg a hely nincs aktív. A Helyösszetevő-kezelő telepíti és indítja az SMS_Executive szolgáltatást, és a hely további folyamatait felelős. A hely telepítésének befejezése után a Helyösszetevő-kezelő szolgáltatás indításakor, akkor telepíti az SMS_Executive szolgáltatást és a hely működéséhez szükséges egyéb folyamatokat.  

 **/ REJTETT**  
 Elrejti a felhasználói felületet a telepítés során. Használja ezt a beállítást csak a **/SCRIPT** lehetőséget. A felügyelet nélküli telepítés parancsfájljában minden szükséges beállításnak biztosítania kell, különben a telepítés meghiúsul.  

 **/ NOUSERINPUT**  
 Letiltja a felhasználói bevitelt telepítés közben, de a telepítő varázsló megjeleníti. Használja ezt a beállítást csak a **/SCRIPT** lehetőséget. A felügyelet nélküli telepítés parancsfájljában minden szükséges beállításnak biztosítania kell, különben a telepítés meghiúsul.  

 **/ RESETSITE**  
 A hely alaphelyzetbe állítása, amely a hely adatbázisának és szolgáltatásfiókjainak alaphelyzetbe állítja. A telepítő futtatásával kell  **<* Configuration Manager telepítési útvonala*> \BIN\X64** a helykiszolgálón. A hely alaphelyzetbe állításáról kapcsolatos további információkért tekintse meg a [hely alaphelyzetbe állításának](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_reset) szakasz [a System Center Configuration Manager infrastruktúra](../../../../core/servers/manage/modify-your-infrastructure.md).  

 **/ TESTDBUPGRADE <*példánynév*>\\<*adatbázis neve*>**  
 Teszteli a győződjön meg arról, hogy az adatbázis frissítés képes a Helyadatbázis biztonsági másolatainak készítésekor. Meg kell adnia a példány nevét és a Helyadatbázis nevét. Ha csak az adatbázis nevét adja meg, a telepítő az alapértelmezett példánynevet használja.  

> [!IMPORTANT]  
>  Ne futtassa ezt a parancssori kapcsolót az élesben használt helyadatbázison. Ezt a parancssori kapcsolót az élesben használt helyadatbázison futtató frissíti a helyadatbázist, és működésképtelenné teheti a helyet.  

 **/ FRISSÍTÉSE**  
 Futtatja a hely felügyelt frissítését. Amikor **/frissítés**, meg kell adnia a termékkulcsot, kötőjelekkel (-). Emellett meg kell adnia a korábban letöltött telepítéshez szükséges fájlok elérési útja.  

 Például: `setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

 További információ a telepítéshez szükséges fájlok: [a telepítő letöltési segédprogramja](setup-downloader.md).  

 **/ SCRIPT <*beállítási parancsprogram elérési útja*>**  
 Felügyelet nélküli telepítést végez. Telepítőinicializálási fájl szükséges használata esetén a **/SCRIPT** lehetőséget. Felügyelet nélküli telepítéssel kapcsolatos további információkért lásd: [telepítése a parancssor használatával helyek](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).  

 **/ SDKINST <*SMS-szolgáltató teljes Tartományneve*>**  
 A megadott számítógépre telepíti az SMS-szolgáltatót. Meg kell adnia az SMS-szolgáltató számítógép teljesen minősített tartománynevét (FQDN). Az SMS-szolgáltató kapcsolatos további információkért lásd: [az SMS-szolgáltató tervezése a System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

 **/ SDKDEINST <*SMS-szolgáltató teljes Tartományneve*>**  
 Eltávolítja az SMS-szolgáltatót a megadott számítógépen. Meg kell adnia az SMS Provider számítógép teljes Tartománynevét.  

 **/ MANAGELANGS <*nyelvi parancsfájl elérési útja*>**  
 Egy előzőleg telepített helynél telepített nyelvek kezelésére szolgál. Ez a beállítás használatához futtatnia kell a telepítőt  **<* Configuration Manager telepítési útvonala*> \BIN\X64** a helykiszolgálón és adni a nyelvi beállításokat tartalmazó nyelvi parancsfájl elérési útját. A nyelvbeállítási parancsfájlban elérhető nyelvi beállításokkal kapcsolatos további információkért lásd: [nyelvek kezelése parancssori kapcsolók](#bkmk_Lang) ebben a témakörben.  

##  <a name="bkmk_Lang"></a>Nyelvek kezelése parancssori kapcsolók  
 **Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** ManageLanguages  

    -   **Részletek:** A kiszolgáló, az ügyfél és a mobil ügyfél a hely nyelvi támogatását kezeli.  

**Paraméterek**  

-   **Kulcsnév:** AddServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Adja meg a kiszolgálónyelveket, amelyeket a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok számára használható. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** AddClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Az ügyfélszámítógépek számára elérhető nyelveket határozza meg. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** DeleteServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Meghatározza a törölni kívánt nyelveket, és amely többé nem érhető el a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** DeleteClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Meghatározza a törölni kívánt nyelveket, és amelyek nem lesznek többé elérhetők az ügyfélszámítógépek számára. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** MobileDeviceLanguage  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Meghatározza, hogy az ügyfél mobileszköz nyelvei telepítve vannak-e.  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltése  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha az érték például **0**, a telepítő letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*telepítéshez szükséges fájlok elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

##  <a name="bkmk_Unattended"></a>Felügyelet nélküli telepítési parancsfájl kulcsai  
 A következő részekben hozhat létre a parancsfájlt a felügyelet nélküli telepítés. A lista megjelenítése a telepítési parancsfájl elérhető kulcsai, hozzájuk tartozó értékek, kötelezőségük, mely telepítéstípusokhoz használhatók, és a kulcs rövid leírása.  

### <a name="unattended-install-for-a-central-administration-site"></a>A központi adminisztrációs hely felügyelet nélküli telepítése  
 Az alábbiakban olvasható információk segítségével központi adminisztrációs helyet telepíthet egy felügyelet nélküli telepítési parancsfájllal.  

**Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** InstallCAS  

    -   **Részletek:** Központi adminisztrációs hely telepítésére szolgál.  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *vagy* Eval  

    -   **Részletek:** Adja meg a Configuration Manager telepítési termékkulcsa, kötőjelekkel. Adja meg **Eval** a próbaverzió a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helykód*>  

    -   **Részletek:** Meghatározza a három alfanumerikus karaktert, amely egyedileg azonosítja a helyet a hierarchiában.  

-   **Kulcsnév:** Hely neve  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*hely neve*>  

    -   **Részletek:** Megadja a hely nevét.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Configuration Manager telepítési útvonala*>  

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni.  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltése  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha az érték például **0**, a Telepítőprorgram letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*telepítéshez szükséges fájlok elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = join  

    -   **Részletek:** Való csatlakozást adja meg a felhasználói élmény fokozása Program (CEIP).  

-   **Kulcsnév:** AddServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Adja meg a kiszolgálónyelveket, amelyeket a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok számára használható. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** AddClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Az ügyfélszámítógépek számára elérhető nyelveket határozza meg. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** DeleteServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** A helynek a telepítés után. Meghatározza a törölni kívánt nyelveket, és amely többé nem érhető el a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** DeleteClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** A helynek a telepítés után. Meghatározza a törölni kívánt nyelveket, és amelyek nem lesznek többé elérhetők az ügyfélszámítógépek számára. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** MobileDeviceLanguage  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Meghatározza, hogy az ügyfél mobileszköz nyelvei telepítve vannak-e.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SQL-kiszolgáló neve*>  

    -   **Részletek:** Megadja a nevét, a kiszolgáló vagy fürtözött példány SQL Server rendszerű, és amely a helyadatbázist fogja tartalmazni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helyadatbázis neve*> vagy <*példánynév*>\\<*Helyadatbázis neve*>  

    -   **Részletek:** Adja meg az SQL Server-adatbázis létrehozása vagy a központi adminisztrációs hely adatbázisának telepítése során használja az SQL Server-adatbázis nevét.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*SSB-port száma*>  

    -   **Részletek:** SQL Server által használt SQL Server Service Broker (SSB) portot határozza meg. Az SSB általában úgy van beállítva a 4022-es TCP-port használatára, de már egy másik portot is használhat.  

-   **Kulcsnév:** SQLDataFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.mdb-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .mdb-adatbázisfájlt létrehozásához alternatív helyet határoz meg.  

-   **Kulcsnév:** SQLLogFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.ldf-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .ldf-adatbázisfájl létrehozásához alternatív helyet határoz meg.  

**CloudConnectorOptions**  

-   **Kulcsnév:** CloudConnector  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy ezen a helyen a szolgáltatáskapcsolódási pont telepítéséhez. A szolgáltatáskapcsolódási pont csak a hierarchia legfelső szintű helyén telepíthető, mert ez az érték lehet **0** az alárendelt elsődleges hely.  

-   **Kulcsnév:** CloudConnectorServer  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*szolgáltatási kapcsolódási pont kiszolgálójának teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatási kapcsolódási pont helyrendszerszerepkörének futtató kiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** UseProxy  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a szolgáltatáskapcsolódási pont használja-e a proxykiszolgálót.  

-   **Kulcsnév:** ProxyName  

    -   **Szükséges:** Szükséges, ha **UseProxy** értéke 1  

    -   **Értékek:** <*proxykiszolgáló teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel használandó proxykiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** ProxyPort  

    -   **Szükséges:** Szükséges, ha **UseProxy** értéke 1  

    -   **Értékek:** <*Port száma*>  

    -   **Részletek:** Adja meg a portszámot a proxykiszolgáló port használatára.  

### <a name="unattended-install-for-a-primary-site"></a>Az elsődleges hely felügyelet nélküli telepítése  
Az alábbiakban olvasható információk segítségével elsődleges helyet telepíthet egy felügyelet nélküli telepítési parancsfájllal.  

**Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** InstallPrimarySite  

    -   **Részletek:** Elsődleges hely telepítésére szolgál.  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *vagy* Eval  

    -   **Részletek:** Adja meg a Configuration Manager telepítési termékkulcsa, kötőjelekkel. Adja meg **Eval** a próbaverzió a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helykód*>  

    -   **Részletek:** Meghatározza a három alfanumerikus karaktert, amely egyedileg azonosítja a helyet a hierarchiában.  

-   **Kulcsnév:** SiteName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*hely neve*>  

    -   **Részletek:** Megadja a hely nevét.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Configuration Manager telepítési útvonala*>

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni.  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltése  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha az érték például **0**, a Telepítőprorgram letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*telepítéshez szükséges fájlok elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = join  

    -   **Részletek:** Megadja, hogy a csatlakozik a CEIP-hez.  

-   **Kulcsnév:** ManagementPoint  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*felügyeleti pont helykiszolgálójának teljes Tartományneve*>  

    -   **Részletek:** A felügyeleti pont helyrendszerszerepkörrel futtató kiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** ManagementPointProtocol  

    -   **Szükséges:** Nem  

    -   **Értékek:** HTTPS *vagy* HTTP  

    -   **Részletek:** A felügyeleti ponthoz használt protokollt adja meg.  

-   **Kulcsnév:** DistributionPoint  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*terjesztési pont helykiszolgálójának teljes Tartományneve*>  

    -   **Részletek:** A terjesztési ponthoz használt protokollt adja meg.  

-   **Kulcsnév:** DistributionPointProtocol  

    -   **Szükséges:** Nem  

    -   **Értékek:** HTTPS *vagy* HTTP  

    -   **Részletek:** A terjesztési ponthoz használt protokollt adja meg.  

-   **Kulcsnév:** RoleCommunicationProtocol  

    -   **Szükséges:** Igen  

    -   **Értékek:** EnforceHTTPS *vagy* HTTPorHTTPS  

    -   **Részletek:** Megadja, hogy az csak HTTPS-kommunikációt fogad az ügyfelektől, vagy a kommunikációs módszer konfigurálását az egyes helyrendszer-szerepkör az összes helyrendszert úgy konfigurálja. Ha bejelöli a **EnforceHTTPS**, ügyfélszámítógép az ügyfél-hitelesítéshez érvényes nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítvánnyal kell rendelkeznie.  

-   **Kulcsnév:** ClientsUsePKICertificate  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs használja  

         1 = használata  

    -   **Részletek:** Meghatározza, hogy az ügyfelek használjanak egy ügyfél PKI-tanúsítvánnyal kommunikálni a helyrendszer-szerepköröket.  

-   **Kulcsnév:** AddServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Adja meg a kiszolgálónyelveket, amelyeket a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok számára használható. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** AddClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** Az ügyfélszámítógépek számára elérhető nyelveket határozza meg. Alapértelmezés szerint angol nyelven érhető el.  

-   **Kulcsnév:** DeleteServerLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** A helynek a telepítés után. Meghatározza a törölni kívánt nyelveket, és amely többé nem érhető el a Configuration Manager konzolon, a jelentések és a Configuration Manager-objektumok. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** DeleteClientLanguages  

    -   **Szükséges:** Nem  

    -   **Értékek:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, vagy ZHH  

    -   **Részletek:** A helynek a telepítés után. Meghatározza a törölni kívánt nyelveket, és amelyek nem lesznek többé elérhetők az ügyfélszámítógépek számára. Angol alapértelmezés szerint mindig elérhető, és nem távolítható el.  

-   **Kulcsnév:** MobileDeviceLanguage  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Meghatározza, hogy az ügyfél mobileszköz nyelvei telepítve vannak-e.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SQL-kiszolgáló neve*>  

    -   **Részletek:** Megadja a nevét, a kiszolgáló vagy fürtözött példány SQL Server rendszerű, és amely a helyadatbázist fogja tartalmazni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helyadatbázis neve*> vagy <*példánynév*>\\<*Helyadatbázis neve*>  

    -   **Részletek:** Adja meg az SQL Server-adatbázis létrehozása vagy az elsődleges Helyadatbázis telepítése során használja az SQL Server-adatbázis nevét.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*SSB-port száma*>  

    -   **Részletek:** Az SQL Server által használt SSB-portot határozza meg. Az SSB általában úgy van beállítva a 4022-es TCP-port használatára, de már egy másik portot is használhat.  

-   **Kulcsnév:** SQLDataFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.mdb-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .mdb-adatbázisfájlt létrehozásához alternatív helyet határoz meg.  

-   **Kulcsnév:** SQLLogFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.ldf-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .ldf-adatbázisfájl létrehozásához alternatív helyet határoz meg.  

**HierarchyExpansionOption**  

-   **Kulcsnév:** CCARSiteServer  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*központi adminisztrációs hely teljes Tartományneve*>  

    -   **Részletek:** Adja meg a központi adminisztrációs hely, amely egy elsődleges hely kapcsolódni fog, amikor bekerül a Configuration Manager-hierarchiában. Meg kell adnia a központi adminisztrációs hely telepítése során.  

-   **Kulcsnév:** CASRetryInterval  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*Interval*>  

    -   **Részletek:** Megadja az újrapróbálkozási időköz (percben) a központi adminisztrációs helyhez való után a kapcsolat hibája esetén. Például a Kapcsolódás a központi adminisztrációs helyhez sikertelen, ha az elsődleges hely annyi percig megadott a a **CASRetryInterval** értékét, majd újrapróbálkozik a kapcsolódással.  

-   **Kulcsnév:** WaitForCASTimeout  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*Timeout*>  

         Érték **0** való **100**  

    -   **Részletek:** Meghatározza a maximális időkorlátot (percben) az elsődleges hely a központi adminisztrációs helyhez való kapcsolódáshoz. Például akkor, ha egy elsődleges hely nem tud kapcsolódni egy központi adminisztrációs helyet, az elsődleges hely újrapróbálja a kapcsolódást a központi adminisztrációs hely alapján a **CASRetryInterval** érték csak a **WaitForCASTimeout** időtartamot. Értéket is megadhat **0** való **100**.  

**CloudConnectorOptions**  

-   **Kulcsnév:** CloudConnector  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy ezen a helyen a szolgáltatáskapcsolódási pont telepítéséhez. A szolgáltatáskapcsolódási pont csak a hierarchia legfelső szintű helyén telepíthető, mert ez az érték lehet **0** az alárendelt elsődleges hely.  

-   **Kulcsnév:** CloudConnectorServer  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*szolgáltatási kapcsolódási pont kiszolgálójának teljes Tartományneve*\>  

    -   **Részletek:** A szolgáltatási kapcsolódási pont helyrendszerszerepkörének futtató kiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** UseProxy  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a szolgáltatáskapcsolódási pont használja-e a proxykiszolgálót.  

-   **Kulcsnév:** ProxyName  

    -   **Szükséges:** Szükséges, ha **UseProxy** értéke 1  

    -   **Értékek:** <*proxykiszolgáló teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel használandó proxykiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** ProxyPort  

    -   **Szükséges:** Szükséges, ha **UseProxy** értéke 1  

    -   **Értékek:** <*Port száma*>  

    -   **Részletek:** Adja meg a portszámot a proxykiszolgáló port használatára.  

### <a name="unattended-recovery-for-a-central-administration-site"></a>A központi adminisztrációs hely felügyelet nélküli helyreállítása  
 A következő adatok segítségével helyreállíthat egy központi adminisztrációs helyet egy felügyelet nélküli telepítési parancsfájllal.  

**Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** RecoverCCAR  

    -   **Részletek:** Központi adminisztrációs hely helyreállítására szolgál.  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.

**RecoveryOptions**  

-   **Kulcsnév:** ServerRecoveryOptions  

    -   **Szükséges:** Igen  

    -   **Értékek:** 1, 2 vagy 4  

         1 = helykiszolgáló helyreállítása és az SQL Server.  

         2 = csak a helykiszolgáló helyreállítása.  

         4 = csak az SQL Server helyreállítása.  

    -   **Részletek:** Megadja, hogy a telepítő állítja helyre a helykiszolgálót, az SQL Server, vagy mindkettőt. A kapcsolódó kulcsok akkor szükségesek, amikor a következő értéket a **ServerRecoveryOptions** beállítást:  

        -   Érték = 1: Lehetősége van a adjon meg egy értéket a **SiteServerBackupLocation** kulcs a hely biztonsági másolat használatával állítsa helyre a helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   Érték = 2: Lehetősége van a adjon meg egy értéket a **SiteServerBackupLocation** kulcs a hely biztonsági másolat használatával állítsa helyre a helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   Érték = 4: A **BackupLocation** kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

-   **Kulcsnév:** DatabaseRecoveryOptions  

    -   **Szükséges:** Ezt a kulcsot meg kell adni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **4**.  

    -   **Értékek:** 10, 20, 40 vagy 80  

         10 = a hely adatbázisának visszaállítása biztonsági másolatból.  

         20 = más módszer alkalmazásával manuálisan helyreállított helyadatbázis használata.  

         40 = új adatbázis létrehozása a helyhez. Ezt a lehetőséget akkor kell használni, ha nem áll rendelkezésre biztonsági másolat a helyhez. A globális és a helyadatokat más helyekről történő replikációval állítja helyre a rendszer.  

         80 = az adatbázis helyreállításának kihagyása.  

    -   **Részletek:** Meghatározza, hogy a telepítő hogyan állítja helyre a helyadatbázist az SQL Server.  

-   **Kulcsnév:** ReferenceSite  

    -   **Szükséges:** Ezt a kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** beállítás értéke **40**.  

    -   **Értékek:** <*referenciahely teljes Tartományneve*>  

    -   **Részletek:** Megadja a referencia elsődleges helyet, amellyel a központi adminisztrációs hely helyreállítja a globális adatokat, ha az adatbázis biztonsági másolata régebbi, mint a változások követése megőrzési idő, vagy ha a hely biztonsági másolat nélküli helyreállítása.  

         Ha nem ad meg referenciahelyet, és a biztonsági másolat régebbi, mint a változások követése megőrzési idő, minden elsődleges hely újra lesz inicializálva a központi adminisztrációs helyről visszaállított adatokkal.  

         Ha nem ad meg referenciahelyet, és a biztonsági mentés esik-e a változások követése megőrzési időtartam, csak a biztonsági mentés lesznek replikálva az elsődleges helyekről után végzett módosításokat. Ha a különböző elsődleges helyekről származó módosítások ütköznek, a központi adminisztrációs hely az első fogadott módosítást használja.  

-   **Kulcsnév:** SiteServerBackupLocation  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*helykiszolgáló biztonságimásolat-készletének elérési útja*>  

    -   **Részletek:** Meghatározza a helykiszolgáló biztonságimásolat-készletének elérési útvonalát. Ezt a kulcsot nem kötelező megadni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **2**. A helynek a róla készített biztonsági másolat használatával történő helyreállításához adjon meg értéket a **SiteServerBackupLocation** kulcshoz. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

-   **Kulcsnév:** BackupLocation  

    -   **Szükséges:** A kulcs mindenképpen szükséges, ha az érték **1** vagy **4** a a **ServerRecoveryOptions** kulcsát, és konfigurálja a érték **10** a a **DatabaseRecoveryOptions** kulcsát.  

    -   **Értékek:** <*Helyadatbázis biztonságimásolat-készletének elérési útja*>  

    -   **Részletek:** Meghatározza a Helyadatbázis biztonságimásolat-készletének elérési útvonalát.  

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *vagy* Eval  

    -   **Részletek:** Adja meg a Configuration Manager telepítési termékkulcsa, kötőjelekkel. Adja meg **Eval** a próbaverzió a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helykód*>  

    -   **Részletek:** Meghatározza a három alfanumerikus karaktert, amely egyedileg azonosítja a helyet a hierarchiában. Meg kell adnia a helykódot, amely a hely a hiba előtt használt.

-   **Kulcsnév:** SiteName  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*hely neve*>  

    -   **Részletek:** Megadja a hely nevét.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Configuration Manager telepítési útvonala*>  

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. Az SMS-szolgáltatót a hiba előtt futtató kiszolgáló nevét kell megadni.  

         A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni. Az SMS-szolgáltató kapcsolatos további információkért lásd: [az SMS-szolgáltató tervezése a System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltése  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha az érték például **0**, a telepítő letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*telepítéshez szükséges fájlok elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Ezt a kulcsot meg kell adni, kivéve, ha a **ServerRecoveryOptions** beállítás értéke **4**.  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = join  

    -   **Részletek:** Megadja, hogy a csatlakozik a CEIP-hez.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SQL-kiszolgáló neve*>  

    -   **Részletek:** Megadja a nevét, a kiszolgáló vagy fürtözött példány SQL Server rendszerű, és amely a helyadatbázist fogja tartalmazni. A helyadatbázist a hiba előtt futtató kiszolgáló nevét kell megadni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helyadatbázis neve*> vagy <*példánynév*>\\<*Helyadatbázis neve*>  

    -   **Részletek:** Adja meg az SQL Server-adatbázis létrehozása vagy a központi adminisztrációs hely adatbázisának telepítése során használja az SQL Server-adatbázis nevét. A hiba előtt használttal azonos adatbázisnevet kell megadni.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SSB-port száma*>  

    -   **Részletek:** Az SQL Server által használt SSB-portot határozza meg. Az SSB általában úgy van beállítva a 4022-es TCP-port használatára. A hiba előtt használttal azonos SSB-portot kell megadni.  

-   **Kulcsnév:** SQLDataFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.mdb-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .mdb-adatbázisfájlt létrehozásához alternatív helyet határoz meg.  

-   **Kulcsnév:** SQLLogFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.ldf-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .ldf-adatbázisfájl létrehozásához alternatív helyet határoz meg.  

**CloudConnectorOptions**  

-   **Kulcsnév:** CloudConnector  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy ezen a helyen a szolgáltatáskapcsolódási pont telepítéséhez. A szolgáltatáskapcsolódási pont csak a hierarchia legfelső szintű helyén telepíthető, mert ez az érték lehet **0** az alárendelt elsődleges hely.  

-   **Kulcsnév:** CloudConnectorServer  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*szolgáltatási kapcsolódási pont kiszolgálójának teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatási kapcsolódási pont helyrendszerszerepkörének futtató kiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** UseProxy  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a szolgáltatáskapcsolódási pont használja-e a proxykiszolgálót.  

-   **Kulcsnév:** ProxyName  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*proxykiszolgáló teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel használandó proxykiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** ProxyPort  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*Port száma*>  

    -   **Részletek:** Adja meg a portszámot a proxykiszolgáló port használatára.  

### <a name="unattended-recovery-for-a-primary-site"></a>Elsődleges hely felügyelet nélküli helyreállítása  
 Az alábbiakban olvasható információk segítségével helyreállíthat egy elsődleges helyet egy felügyelet nélküli telepítési parancsfájllal.  

**Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*RecoverPrimarySite*>  

    -   **Részletek:** Elsődleges hely helyreállítására szolgál.  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.    

**RecoveryOptions**  

-   **Kulcsnév:** ServerRecoveryOptions  

    -   **Szükséges:** Igen  

    -   **Értékek:** 1, 2 vagy 4  

         1 = helykiszolgáló helyreállítása és az SQL Server.  

         2 = csak a helykiszolgáló helyreállítása.  

         4 = csak az SQL Server helyreállítása.  

    -   **Részletek:** Megadja, hogy a telepítő állítja helyre a helykiszolgálót, az SQL Server, vagy mindkettőt. A kapcsolódó kulcsok akkor szükségesek, amikor a következő értéket a **ServerRecoveryOptions** beállítást:  

        -   Érték = 1: Lehetősége van a adjon meg egy értéket a **SiteServerBackupLocation** kulcs a hely biztonsági másolat használatával állítsa helyre a helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   Érték = 2: Lehetősége van a adjon meg egy értéket a **SiteServerBackupLocation** kulcs a hely biztonsági másolat használatával állítsa helyre a helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   Érték = 4: A **BackupLocation** kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

-   **Kulcsnév:** DatabaseRecoveryOptions  

    -   **Szükséges:** Ezt a kulcsot meg kell adni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **4**.  

    -   **Értékek:** 10, 20, 40 vagy 80  

         10 = a hely adatbázisának visszaállítása biztonsági másolatból.  

         20 = más módszer alkalmazásával manuálisan helyreállított helyadatbázis használata.  

         40 = új adatbázis létrehozása a helyhez. Ezt a lehetőséget akkor kell használni, ha nem áll rendelkezésre biztonsági másolat a helyhez. A globális és a helyadatokat más helyekről történő replikációval állítja helyre a rendszer.  

         80 = az adatbázis helyreállításának kihagyása.  

    -   **Részletek:** Meghatározza, hogy a telepítő hogyan állítja helyre a helyadatbázist az SQL Server.  

-   **Kulcsnév:** SiteServerBackupLocation  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*helykiszolgáló biztonságimásolat-készletének elérési útja*>  

    -   **Részletek:**  

         Meghatározza a helykiszolgáló biztonságimásolat-készletének elérési útvonalát. Ezt a kulcsot nem kötelező megadni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **2**. A helynek a róla készített biztonsági másolat használatával történő helyreállításához adjon meg értéket a **SiteServerBackupLocation** kulcshoz. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

-   **Kulcsnév:** BackupLocation  

    -   **Szükséges:** A kulcs mindenképpen szükséges, ha az érték **1** vagy **4** a a **ServerRecoveryOptions** kulcs, és érték **10** a a **DatabaseRecoveryOptions** kulcs.  

    -   **Értékek:** <*Helyadatbázis biztonságimásolat-készletének elérési útja*>  

    -   **Részletek:** Meghatározza a Helyadatbázis biztonságimásolat-készletének elérési útvonalát.  

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:** *xxxxx-xxxxx-xxxxx-xxxxx-xxxxx* vagy *Eval*  

    -   **Részletek:** Adja meg a Configuration Manager telepítési termékkulcsa, kötőjelekkel. Adja meg **Eval** a próbaverzió a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Helykód*>  

    -   **Részletek:** Meghatározza a három alfanumerikus karaktert, amely egyedileg azonosítja a helyet a hierarchiában. Meg kell adnia a helykódot, amely a hely a hiba előtt használt.

-   **Kulcsnév:** SiteName  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*hely neve*>  

    -   **Részletek:** Megadja a hely nevét.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*Configuration Manager telepítési útvonala*>  

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. Az SMS-szolgáltatót a hiba előtt futtató kiszolgáló nevét kell megadni. A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni. Az SMS-szolgáltató kapcsolatos további információkért lásd: [az SMS-szolgáltató tervezése a System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltése  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha az érték például **0**, a telepítő letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*telepítéshez szükséges fájlok elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Ezt a kulcsot meg kell adni, kivéve, ha a **ServerRecoveryOptions** beállítás értéke **4**.  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = join  

    -   **Részletek:** Megadja, hogy a csatlakozik a CEIP-hez.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SQL-kiszolgáló neve*>  

    -   **Részletek:** Megadja a nevét, a kiszolgáló vagy fürtözött példány SQL Server rendszerű, és amely a helyadatbázist fogja tartalmazni. A helyadatbázist a hiba előtt futtató kiszolgáló nevét kell megadni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:**  <*Helyadatbázis neve*> vagy <*példánynév*>\\<*Helyadatbázis neve*>

    -   **Részletek:**  

         Adja meg az SQL Server-adatbázis létrehozása vagy a központi adminisztrációs hely adatbázisának telepítése során használja az SQL Server-adatbázis nevét. A hiba előtt használttal azonos adatbázisnevet kell megadni.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Igen  

    -   **Értékek:** <*SSB-port száma*>  

    -   **Részletek:** Az SQL Server által használt SSB-portot határozza meg. Az SSB általában a 4022-es TCP-port használatára van konfigurálva. A hiba előtt használttal azonos SSB-portot kell megadni.  

-   **Kulcsnév:** SQLDataFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.mdb-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .mdb-adatbázisfájlt létrehozásához alternatív helyet határoz meg.  

-   **Kulcsnév:** SQLLogFilePath  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*.ldf-adatbázisfájl elérési útja*>  

    -   **Részletek:** Az .ldf-adatbázisfájl létrehozásához alternatív helyet határoz meg.  

**HierarchyExpansionOptions**  

-   **Kulcsnév:** CCARSiteServer  

    -   **Szükséges:** A Részletek területen.  

    -   **Értékek:** <*hely központi felügyeleti hely kódját*>  

    -   **Részletek:** Adja meg a központi adminisztrációs hely, amelyhez egy elsődleges hely kapcsolódni fog, amikor bekerül a Configuration Manager-hierarchiában. Ez a beállítás kötelező, ha az elsődleges hely központi adminisztrációs helyhez volt csatlakoztatva a hiba előtt. Azt a helykódot kell megadni, amely a hiba előtt volt beállítva a központi adminisztrációs helyhez.  

-   **Kulcsnév:** CASRetryInterval  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*Interval*>  

    -   **Részletek:** Megadja az újrapróbálkozási időköz (percben) a központi adminisztrációs helyhez való után a kapcsolat hibája esetén. Például a Kapcsolódás a központi adminisztrációs helyhez sikertelen, ha az elsődleges hely annyi percig megadott a a **CASRetryInterval** értékét, majd újrapróbálkozik a kapcsolódással.  

-   **Kulcsnév:** WaitForCASTimeout  

    -   **Szükséges:** Nem  

    -   **Értékek:** <*Timeout*>  

    -   **Részletek:** Meghatározza a maximális időkorlátot (percben) az elsődleges hely a központi adminisztrációs helyhez való kapcsolódáshoz. Például akkor, ha egy elsődleges hely nem tud kapcsolódni egy központi adminisztrációs helyet, az elsődleges hely újrapróbálja a kapcsolódást a központi adminisztrációs hely alapján a **CASRetryInterval** érték csak a **WaitForCASTimeout** időtartamot. Értéket is megadhat **0** való **100**.  

**CloudConnectorOptions**  

-   **Kulcsnév:** CloudConnector  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy ezen a helyen a szolgáltatáskapcsolódási pont telepítéséhez. A szolgáltatáskapcsolódási pont csak a hierarchia legfelső szintű helyén telepíthető, mert ez az érték lehet **0** az alárendelt elsődleges hely.  

-   **Kulcsnév:** CloudConnectorServer  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*szolgáltatási kapcsolódási pont kiszolgálójának teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatási kapcsolódási pont helyrendszerszerepkörének futtató kiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** UseProxy  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** 0 vagy 1  

         0 = nincs nem telepítése  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a szolgáltatáskapcsolódási pont használja-e a proxykiszolgálót.  

-   **Kulcsnév:** ProxyName  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*proxykiszolgáló teljes Tartományneve*>  

    -   **Részletek:** A szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel használandó proxykiszolgáló teljes Tartománynevét adja meg.  

-   **Kulcsnév:** ProxyPort  

    -   **Szükséges:** Szükséges, ha **CloudConnector** értéke 1  

    -   **Értékek:** <*Port száma*>  

    -   **Részletek:** Adja meg a portszámot a proxykiszolgáló port használatára.  

