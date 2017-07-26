---
title: "Felügyeleti átjáró beállítása |} Microsoft Docs"
description: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5a6fdc9a526c4fc3a9027dcedf1dd66a6fff5a7
ms.openlocfilehash: 97e1bc6585cee0ff433da0ec0b60b9604cb7348f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>A Configuration Manager felhő adatkezelési átjáró beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1610 verziójától kezdve felhő adatkezelési átjárót a Configuration Manager beállításához a folyamat a következő lépéseket tartalmazza:

## <a name="step-1-configure-required-certificates"></a>1. lépés: Szükséges tanúsítványok konfigurálása

## <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>(Ajánlott) 1 - beállítást használja a kiszolgálói hitelesítési tanúsítvány olyan nyilvános és a globálisan megbízható tanúsítvány szolgáltató (például a VeriSign szolgáltatótól)

Ha ezt a módszert használja, az ügyfelek automatikusan megbíznak a tanúsítványt, és nem kell saját kezűleg egy egyéni SSL-tanúsítvány létrehozásához.

1. Kanonikus név rekordot (CNAME) a vállalat nyilvános tartományi névszolgáltatás (DNS) a felhő felügyeleti átjáró szolgáltatás egy rövid nevet használt alias létrehozása a nyilvános tanúsítvány kell létrehozni.
Például a Contoso nevet a felhő management gateway szolgáltatás **GraniteFalls** lesz, amely az Azure-ban **GraniteFalls.CloudApp.Net**. Contoso-nyilvános DNS-contoso.com névtérben, a DNS-rendszergazda hoz létre egy új CNAME rekord **GraniteFalls.Contoso.com** a valódi név **GraniteFalls.CloudApp.net**.
2. Ezután olyan kiszolgálói hitelesítési tanúsítványt kérhet egy nyilvános szolgáltató segítségével az egyszerű név (CN) a CNAME-alias.
Például a Contoso használ **GraniteFalls.Contoso.com** a tanúsítvány CN.
3. A felhő management gateway szolgáltatás létrehozása a Configuration Manager konzolon, ezzel a tanúsítvánnyal.
    - Az a **beállítások** a felhő létrehozása kezelési átjáró varázslóban a kiszolgálói tanúsítvány a felhőalapú szolgáltatás hozzáadásakor oldalán (a **tanúsítványfájl**), a varázsló az állomásnév kinyerése a tanúsítvány CN a szolgáltatás nevére, és majd fűzze, amely a **cloudapp.net** (vagy **usgovcloudapp.net** az Azure Amerikai Egyesült államokbeli kormányzati felhő), a szolgáltatás FQDN a szolgáltatás létrehozása az Azure-ban.
Például, amikor a felhő adatkezelési átjáró létrehozása: Contoso, az állomásnév **GraniteFalls** a tanúsítvány CN, ki kell olvasni, hogy az Azure-ban a tényleges szolgáltatás jön létre **GraniteFalls.CloudApp.net**.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>2. lehetőség – hozzon létre egy egyéni SSL-tanúsítványa felhő adatkezelési átjáró egy felhőalapú terjesztési pont ugyanúgy

Felügyeleti átjáró egyéni SSL-tanúsítványa ugyanúgy teheti a felhő alapú terjesztési pontok is létrehozhat. Kövesse az utasításokat [a felhő alapú terjesztési pontok a szolgáltatástanúsítvány központi telepítése](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) , de eltérő tegye a következőket:

- Az új tanúsítványsablon beállításakor ad ** olvasási ** és **beléptetés** engedélyeket a biztonsági csoportnak, amely a Configuration Manager-kiszolgálók beállítása.
- Az egyéni webkiszolgáló-tanúsítvány igénylése, adja meg egy teljes Tartománynevet a tanúsítvány egyszerű neve, amely **cloudapp.net** felhő adatkezelési átjáró használatához az Azure nyilvános felhőjében vagy **usgovcloudapp.net** az Azure government felhő.


## <a name="step-2-export-the-client-certificates-root"></a>2. lépés: Az ügyféltanúsítvány főtanúsítvány exportálása

A legegyszerűbb módja exportálási gyökere ügyféltanúsítványt a hálózaton használt, egy a tartományhoz csatlakoztatott számítógépeken, amelyek egy ügyféltanúsítványt megnyitásához, és másolja.

> [!NOTE] 
>
> Ügyféltanúsítványok szükségesek kezelési átjáró a kezelése és a felügyeleti átjáró felhőcsatlakozót üzemeltető helyrendszer-kiszolgálón kattintson a kívánt számítógépen. Ha ügyfél-tanúsítvány hozzáadása bármelyik ezeknek a gépeknek szüksége, tekintse meg [központi telepítése a tanúsítvány a Windows ügyfélszámítógépek](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

1.  A Futtatás ablakba írja be a **mmc** nyomja le az ENTER.

2.  A Fájl menüből válassza a **beépülő modul hozzáadása/eltávolítása...** .

3.  A hozzáadása vagy eltávolítása beépülő modulok párbeszédpanelen válassza ki a **tanúsítványok** > **hozzáadása &gt;**   >  **számítógépfiók** > **tovább** > **helyi számítógép** > **Befejezés**. 

4.  Ugrás a **tanúsítványok** &gt; **személyes** &gt; **tanúsítványok**.

5.  Kattintson duplán a tanúsítványra, az ügyfél-hitelesítéshez a számítógépen, az Általános lapon válassza ki, és kattintson duplán a legfelső szintű hitelesítésszolgáltatóval (tetején az elérési út).

6.  Válassza ki a részleteket tartalmazó lapot **Másolás fájlba...** .

7.  Fejezze be a Tanúsítványexportáló varázsló segítségével az alapértelmezett tanúsítvány formátuma. Ellenőrizze, jegyezze fel a nevét, és a legfelső szintű tanúsítványt hoz létre. Szüksége lesz rájuk a felhő adatkezelési átjáró konfigurálása egy [később lépés](#step-4-set-up-cloud-management-gateway).

## <a name="step-3-upload-the-management-certificate-to-azure"></a>3. lépés: A felügyeleti tanúsítvány feltöltése az Azure-bA

Az Azure felügyeleti tanúsítvány megadása kötelező a Configuration Manager az Azure API eléréséhez és felhő adatkezelési átjáró konfigurálásához. További információt és útmutatást a felügyeleti tanúsítvány feltöltése az Azure dokumentációjának a következő cikkekben talál:

- [Azure Cloud Services tanúsítványok áttekintése](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Az Azure szolgáltatásfelügyeleti API Management-tanúsítvány feltöltése](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>Ügyeljen arra, hogy az előfizetés-azonosító, a felügyeleti tanúsítvány másolja. A Configuration Manager konzolján a felhőalapú adatkezelési átjáró konfigurálásához szüksége lesz rá a [tovább](#step-4-set-up-cloud-management-gateway).

### <a name="subordinate-ca-certificates-and-azure"></a>Alárendelt CA tanúsítványainak korlátozásában és Azure

Ha a tanúsítványt egy alárendelt CA (subCA), és a vállalati nyilvános kulcsokra ÉPÜLŐ infrastruktúra nem csatlakozik az internethez, használja ezt az eljárást a tanúsítvány feltöltése az Azure-bA. 

1. Az Azure-portálon, miután beállította a kezelési átjáró a, keresse meg a felhő management gateway szolgáltatás, és navigáljon a **tanúsítvány** fülre. Töltse fel a subCA tanúsítvány(ok) van. Ha egynél több subCA cert, töltse fel az összes szeretné. 
2. Miután a tanúsítvány feltöltése, jegyezze fel annak ujjlenyomata. 
3. Adja hozzá az ujjlenyomatot a parancsfájl helyadatbázishoz:
    
```

    DIM serviceCName
    DIM subCAThumbprints

    ' Verify arguments
    IF WScript.Arguments.Count <> 2 THEN
    WScript.StdOut.WriteLine "Usage: CScript UpdateSubCAThumbprints.vbs <ServiceCName> <SubCA cert thumbprints, separated by ;>"
    WScript.Quit 1
    END IF

    'Get arguments
    serviceCName = WScript.Arguments.Item(0)
    subCAThumbprints = WScript.Arguments.Item(1)

    'Find SMS Provider
    WScript.StdOut.WriteLine "Searching for SMS Provider for local site..."
    SET objSMSNamespace = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms")
    SET results = objSMSNamespace.ExecQuery("SELECT * From SMS_ProviderLocation WHERE ProviderForLocalSite = true")

    'Process the results
    FOR EACH var in results
    siteCode = var.SiteCode
    NEXT

    IF siteCode = "" THEN
    WScript.StdOut.WriteLine "Failed to locate SMS provider."
    WScript.Quit 1
    END IF

    WScript.StdOut.WriteLine "SiteCode = " & siteCode 

    ' Connect to the SMS namespace
    SET objWMIService = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms\site_" & siteCode)

    'Get instance of SMS_AzureService
    DIM query
    query = "SELECT * From SMS_AzureService WHERE ServiceType = 'CloudProxyService' AND ServiceCName = '" & serviceCName & "'"
    WScript.StdOut.WriteLine "Run WQL query: " &  query
    SET objInstances = objWMIService.ExecQuery(query)

    IF IsNull(objInstances) OR (objInstances.Count = 0) THEN
    WScript.StdOut.WriteLine "Failed to get Azure_Service instance."
    WScript.Quit 1
    END IF

    FOR EACH var IN objInstances
    SET azService = var
    NEXT

    WScript.StdOut.WriteLine "Update [SubCACertThumbprint] to " & subCAThumbprints

    'Update SubCA cert thumbprints
    azService.Properties_.item("SubCACertThumbprint") = subCAThumbprints

    'Save data back to provider
    azService.Put_

    WScript.StdOut.WriteLine "[SubCACertThumbprint] is updated successfully."
```


## <a name="step-4-set-up-cloud-management-gateway"></a>4. lépés: Felügyeleti átjáró beállítása

>[!NOTE]
>Verzióban 1610 felhő adatkezelési átjáró egy előzetes verziójú funkció. Az engedélyezéshez, lásd: [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **Felhőszolgáltatások** > **felhő adatkezelési átjáró**.
2. Válasszon **létrehozása kezelési átjáró a**.

3. A felhő létrehozása kezelési átjáró varázslóban, adja meg (az Azure felügyeleti portálján átmásolva) Azure-előfizetése Azonosítóját, és keresse meg a tanúsítványfájl meg Azure felügyeleti tanúsítvány feltöltéséhez használt. Válasszon **következő** , majd várjon néhány pillanatot, hogy a csatlakozik az Azure-konzolon.

4. Töltse ki a varázsló további részletek:

    - Adja meg a nevét, a szolgáltatás, amely fut, az Azure-ban. Szolgáltatás neve csak alfanumerikus karaktereket, és 3 – 24 karakter hosszúságúnak kell lennie.

    - Válassza ki azt szeretné, hogy a szolgáltatás futtatásához Azure-régiót.

    - Adja meg a szolgáltatás használni kívánt virtuális gépek számát. Az alapértelmezett érték 1, de a szolgáltatás legfeljebb 16 virtuális gépek is futtathatja.

    >[!NOTE]
    >Az internetes proxy használatakor a felhő felügyeleti átjáró csatlakozási pontjának a proxy portok számát a virtuális gépek használata esetén port 10124 kezdődő száma alapján növelnie kell.

    - Adja meg az egyéni SSL-tanúsítvány exportált titkos kulcs (.pfx fájlt).

    - Adja meg, hogy az ügyféltanúsítvány-ból exportált legfelső szintű tanúsítványát.

    -   Adja meg a szolgáltatás néven az új tanúsítványsablon létrehozásakor használt teljes tartománynév. Meg kell adnia a következő utótagokat a használ az Azure felhő alapú szolgáltatás tartománynév közül:

    Azure-felhő | Teljes tartománynév előtagja
    --------------|-------------
    Nyilvános (kereskedelmi) felhő | . cloudapp.net    
    Kormánya felhő | . usgovcloudapp.net

  - Törölje a jelölését **ügyfél tanúsítvány-visszavonás ellenőrzése** (kivéve, ha van nyilvánosan közzétételt a CRL-adatok).

  - Válasszon **következő** befejezése.

5. Felügyeleti átjáró felhőforgalom 14 napos küszöbértéket a figyelheti, válassza a küszöbérték-értesítés bekapcsolása a jelölőnégyzetet. Adja meg a küszöbérték, és a százalékos arányát, ahol a különböző riasztási szintű indíthat. Válasszon **következő** befejezése.

6. Tekintse át a beállításokat, és válassza a **következő**. A Configuration Manager elindítja a szolgáltatás beállítása. A varázsló bezárása után lépnek teljesen az Azure szolgáltatás kiépítése 5-15 perc között. Ellenőrizze a **állapot** oszlopában az újonnan telepítő felhő átjárót határozza meg, ha a szolgáltatás készen áll-e.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>5. lépés: Elsődleges hely ügyfél-hitelesítő hitelesítés konfigurálása

1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**.

2. Válassza ki az elsődleges helyen az ügyfelek kezelésére felhő adatkezelési átjáró keresztül, és válassza a kívánt **tulajdonságok**.

3. Az elsődleges hely tulajdonlapnak számítógép ügyfél-kommunikáció lapján ellenőrizze **használjon PKI-ügyféltanúsítvány (ügyfél-hitelesítés) Ha van ilyen**.

4. Győződjön meg arról, hogy törli az **ügyfelek ellenőrizze a visszavont tanúsítványok listáját (CRL) a helyrendszerekhez**. Ez a beállítás csak lenne szükséges, ha volt nyilvánosan közzétételt a CRL-t.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>6. lépés: Adja hozzá a felhő felügyeleti átjáró összekötőpontja

A felhőalapú felügyeleti átjáró összekötő pont egy új helyrendszer-szerepkör felügyeleti átjáró való kommunikációhoz. A felhő felügyeleti átjáró összekötőpontja hozzáadásához kövesse az utasításokat a [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](/sccm/core/servers/deploy/configure/add-site-system-roles).

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>7. lépés: Felügyeleti átjáró felhőforgalom szerepkörök konfigurálásához

Felügyeleti átjáró utolsó lépéseként, hogy a felhő felügyeleti átjáró forgalom fogadására a helyrendszer-szerepkörök konfigurálása. A technikai előzetes 1606 csak a felügyeleti pont, a terjesztési pont és a szoftver frissítés pont szerepkörök támogatottak felhő adatkezelési átjáró. Minden egyes szerepkör külön-külön kell konfigurálni.

1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.

2. Válassza ki a helyrendszer-kiszolgáló kezelési átjáró felhőforgalom konfigurálni szeretné a szerepkörhöz.

3. Válassza ki a szerepkört, és válassza a **tulajdonságok**.

4. Szerepkör tulajdonságai alapján ügyfélkapcsolatokat, válassza a **HTTPS**, melletti négyzetet **engedélyezése a Configuration Manager felhő felügyeleti átjáró forgalom**, és válassza a **OK**. Ismételje meg ezeket a lépéseket a fennmaradó szerepkörök.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>8. lépés: Felügyeleti átjáró ügyfelek konfigurálása

A felhőfelügyelet után átjáró és a helyrendszerszerepkörök teljesen konfigurálva, és fut, az ügyfelek automatikusan a következő helyére vonatkozó kérelmet a felhő felügyeleti átjáró szolgáltatás helyét fogja kapni. Az ügyfelek a felhő management gateway szolgáltatás helyét fogadására a vállalati hálózaton kell lennie. A lekérdezési ciklus helyére irányuló kérelmek 24 óránként van. Ha nem szeretné a szokásos módon ütemezett helyére vonatkozó kérelmet. várja meg, az SMS Ügynökállomás szolgáltatás (ccmexec.exe) a számítógép újraindításával kényszerítheti a kérelmet.

A felhő management gateway szolgáltatás az ügyfélhez konfigurált helyét akkor is automatikusan határozzák meg, hogy az intraneten vagy az interneten. Ha az ügyfél kapcsolatba lépni a tartományvezérlővel, vagy a helyi felügyeleti pont, azt fogja a Configuration Manager kommunikációhoz használni, azt, különben az van az internetes és a helyét, a felhő adatkezelési átjáró szolgáltatás való kommunikációhoz.

>[!NOTE]
> Beállíthatja, hogy az ügyfél mindig a felhő felügyeleti átjáró függetlenül attól, hogy az intraneten vagy az Internet használatára. Ehhez be kell állítani a következő beállításkulcsot az ügyfélszámítógépen: \
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

Győződjön meg arról, hogy az ügyfelek is képes kapcsolódni a Configuration Manager, a következő PowerShell-parancsot futtathatja az ügyfélszámítógépen:

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

A parancs megjeleníti a felügyeleti pontokat, az ügyfél vegye fel a kapcsolatot a felhő management gateway szolgáltatás is beleértve.

## <a name="next-steps"></a>További lépések

[Felügyeleti átjáró készült ügyfelek figyelése](monitor-clients-cloud-management-gateway.md)

