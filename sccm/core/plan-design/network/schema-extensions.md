---
title: "Sémakiterjesztések |} Microsoft Docs"
description: "System Center Configuration Manager támogatására az Active Directory-séma kiterjesztése."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7479e54b5db2eff893bf9fbaf52c104836cda519
ms.openlocfilehash: 5b5540c35c02df6e3d06e4aa9269b8da3238233e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>Sémakiterjesztések a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager támogatására az Active Directory-sémát kiterjesztheti. Ez szerkeszti egy erdő Active Directory-séma hozzáadása egy új tároló és számos attribútum, amely a Configuration Manager-helyek segítségével kulcsadatokat közzéteheti az Active Directoryban, ahol az ügyfelek biztonságosan használható. Ez az információ egyszerűbbé teheti a telepítését, és az ügyfelek és a segítségével ügyfelek konfigurációs helyerőforrások például kiszolgálók központilag telepített tartalmat, illetve hogy a különböző szolgáltatásokat nyújtanak az ügyfelek számára.  

-   Érdemes az Active Directory-séma kiterjesztése, de ez nem szükséges.  

[Az Active Directory-séma kiterjesztéséhez](https://msdnstage.redmond.corp.microsoft.com/en-US/library/mt345589\(TechNet.10\).aspx) jól kell ismernie az Active Directory tartományi szolgáltatásokat és tisztában kell lennie azzal, [hogyan lehet módosítani az Active Directory-sémát](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Az Active Directory-séma kibővítése a Configuration Manager szempontjai  

-   Az Active Directory-séma bővítményei a System Center Configuration Manager ugyanazok maradtak, mint a Configuration Manager 2007 és a Configuration Manager 2012 használó. Ha korábban már kiterjesztette a sémát valamelyik verzióhoz, a kiterjesztést nem kell újra végrehajtania.  

-   A séma kiterjesztése a egy erdőre kiterjedő, egyszeri, visszafordíthatatlan művelet.  

-   Csak a felhasználó ki-e a Sémagazdák csoport tagja, vagy ki rendelkezik megfelelő engedélyekkel a séma módosításához sémája bővíthető.  

-   Bár a előtt sémát kiterjesztheti, vagy a Configuration Manager telepítő futtatását követően, célszerű a séma kiterjesztése, a helyek és hierarchia beállításainak konfigurálása előtt. Ezzel számos későbbi konfigurációs lépés egyszerűbbé tehető.  

-   A séma kiterjesztése után az erdő replikálja az Active Directory globális katalógusát. Ezért tervezze meg a séma kiterjesztése, amikor a replikálás forgalma nem hat negatívan más hálózatfüggő folyamatokra:  

    -   A Windows 2000 verziójú erdőkben a séma kiterjesztése eredményezi a teljes globális katalógus teljes szinkronizálását.  

    -   A Windows 2003 verziótól csak az újonnan felvett attribútumok replikálódnak.  

**Eszközök és az Active Directory-sémát nem használó ügyfelek számára:**  

-   Az Exchange Server-összekötő által kezelt mobileszközök  

-   A Mac számítógépek ügyfélszoftvere  

-   A Linux és UNIX kiszolgálók ügyfélszoftvere  

-   A Configuration Manager által beléptetett mobileszközök  

-   A Microsoft Intune által beléptetett mobileszközök  

-   Mobileszközök régi ügyfélszoftverei  

-   Csak internetes ügyfélkezelésre konfigurált Windows ügyfelek  

-   A Configuration Manager által az interneten észlelt Windows ügyfelek  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>Képességek, melyekre előnyösen hat a séma kiterjesztése  
**Ügyfél számítógép telepítését és helyhozzárendelését** – amikor egy Windows rendszerű számítógépen egy új ügyfél telepítése, az ügyfél a telepítési tulajdonságokat az Active Directory tartományi szolgáltatások keres.  

-   **Megkerülő megoldások:** Ha a séma nincs kiterjesztve, a következő lehetőségek egyikének használatával adja meg, telepítenie kell a számítógép konfigurációs adatokat:  

    -   **Ügyfél leküldéses telepítése**. Egy ügyfél-telepítési módszer használata előtt győződjön meg arról, hogy a szükséges előfeltételek maradéktalanul teljesülnek-e. További információkért lásd: "A telepítési módszer függőségei" című [ügyfelek Windows rendszerű számítógépekre történő központi telepítéséhez szükséges előfeltételek](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers).  

    -   **Telepítse az ügyfeleket manuálisan** és adja meg az ügyfél telepítési tulajdonságokat a CCMSetup parancssori telepítési tulajdonságokkal. Ehhez legalább a következőket kell használni:  

        -   Adjon meg egy felügyeleti pontot vagy forrás elérési útja, amelyből a számítógép letöltheti a telepítési fájlokat a CCMSetup-tulajdonsággal **/mp: =&lt;felügyeleti pont neve számítógép neve\>**  vagy **/source:&lt;ügyfél forrásfájljainak elérési útját\> ** ügyfél telepítése során a CCMSetup parancssorban.  

        -   Adja meg az ügyfél számára, hogy azt a webhelyhez hozzárendelni, és ezután töltse le az ügyfél és a hely beállításait használja a kezdeti felügyeleti pontok listáját. Ehhez használja a CCMSetup Client.msi SMSMP tulajdonságát.  

    -   **A felügyeleti pont közzététele a DNS vagy a WINS névszolgáltatásban**, és az ügyfelek konfigurálása ezen szolgáltatáskeresési módszer használatára.  

**Port konfigurálása az ügyfél – kiszolgáló kommunikáció** – Ha egy ügyfél telepítése az Active Directoryban tárolt portadatokkal van konfigurálva. Ha később megváltoztatja az adott helyen az ügyfelek és a kiszolgálók közötti kommunikációhoz használt portot, az adott ügyfél ezt az új portbeállítást az Active Directory Domain Servicesből kérheti le.  

-   **Megkerülő megoldások:** Ha a séma nincs kiterjesztve, a következő lehetőségek egyikének használatával adja meg az új portbeállításokat a meglévő ügyfelek:  

    -   **Telepítse újra az ügyfelek** az új portot konfiguráló beállításokkal.  

    -   **Egyéni szkript üzembe helyezése az ügyfeleknek, amely frissíti a portadatokat**. Ha az ügyfelek a port módosítása miatt nem tudnak kommunikálni egy hellyel, a Configuration Manager központi telepítése a parancsfájl nem használhat. Erre például csoportházirend használható.  

**Tartalom központi telepítési forgatókönyvek** – Ha egy helyen hozza létre a tartalmat, és telepítését, hogy tartalmat egy másik helyhez a hierarchiában, a fogadó helynek képesnek kell lenni az aláírt tartalomadatok aláírásának ellenőrzésére. Ehhez szüksége van annak a forrási helynek a nyilvános kulcsára, amelyik az adatokat létrehozta. Ha az Active Directory-séma kiterjesztése a Configuration Manager, a hierarchia összes helyére a hely nyilvános kulcsának érhető el.  

-   **Megkerülő megoldás:** Ha a séma nincs kiterjesztve, használja a hierarchia-karbantartó eszközt **preinst.exe**a biztonsági kulcsok adatainak helyek közötti cseréjéhez.  

     Például ha tervezi olyan tartalom található egy elsődleges helyen hozhat létre és telepíthet ezt a tartalmat egy másik elsődleges hely alatti másodlagos helyre, akkor növelnie kell az Active Directory-sémát, hogy a másodlagos hely a forrás elsődleges hely nyilvános kulcsának, vagy használja a preinst.exe kulcsokat a két hely közötti megosztásához.  

## <a name="active-directory-attributes-and-classes"></a>Active Directory-attribútumok és osztályok  
Ha a séma kiterjesztése a System Center Configuration Manager, a következő osztályok és attribútumok kerülnek a séma, és elérhető az összes Configuration Manager-helyeken az adott Active Directory-erdőben.  

-   Attribútumok:  

    -   CN = mS-SMS-hozzárendelés--Helykód  

    -   CN = mS-SMS-képességek  

    -   CN = MS-SMS-alapértelmezett-felügyeleti csomag  

    -   CN = mS-SMS-Eszközfelügyeleti--pont  

    -   CN = mS-SMS-állapota  

    -   CN = MS-SMS-MP-cím  

    -   CN = MS-SMS-MP-neve  

    -   CN = MS-SMS-címkiosztási-IP-magas  

    -   CN = MS-SMS-címkiosztási-IP-alacsony  

    -   CN = MS-SMS-Roaming-határok  
        itt:  

    -   CN = MS-SMS-Helyhatárok  

    -   CN = MS-SMS-Helykód  

    -   CN = mS-SMS-forrás-erdő  

    -   CN = mS-SMS-verzió  

-   Osztályok:  

    -   CN = MS-SMS--pont  

    -   CN = MS-SMS-Roaming-határ-tartomány  

    -   CN = MS-SMS-kiszolgáló-lokátor-pont  

    -   CN = MS-SMS-hely  

> [!NOTE]  

>  A sémakiterjesztések tartalmazhatnak attribútumokat és osztályokat is, amelyek a termék előző verziójából áthozott, de nem a System Center Configuration Manager által használt. Példa:  

>   
>  -   Attribútum: cn = MS-SMS-Helyhatárok  
> -   Osztály: cn = MS-SMS-kiszolgáló-lokátor-pont  

A fenti listák naprakészek megtekintésével biztosítható a **ConfigMgr_ad_schema. LDF** fájlt a **\SMSSETUP\BIN\x64** mappa a System Center Configuration Manager telepítési adathordozóján.  

