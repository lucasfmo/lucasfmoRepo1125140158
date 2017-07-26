---
title: "Szinkronizálja az adatokat |} Microsoft dokumentumok |} A Microsoft Operations Management Suite szolgáltatásban "
description: "Szinkronizálja az adatokat a System Center Configuration Manager a Microsoft Operations Management Suite szolgáltatásban."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: 9
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3acfaa2cf8c64ece5cef65b80372067336d6a815
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---


# <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Szinkronizálja az adatokat a Configuration Manager a Microsoft Operations Management Suite


*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Microsoft Operations Management Suite (OMS) összekötőt, hogy szinkronizálja az adatokat használhatja például a gyűjtemények System Center Configuration Manager az OMS szolgáltatáshoz a Microsoft Azure-ban. Így a Configuration Manager telepítési adatait OMS látható.
> [!TIP]
> Az OMS-összekötő egy előzetes verziójú funkció. További tudnivalókért lásd: [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/pre-release-features).

1702 verziójával kezdve használhatja az OMS-összekötő, amely a Microsoft Azure Government felhő OMS-munkaterület való kapcsolódáshoz. Ehhez módosítsa a konfigurációs fájlt, az OMS-összekötő telepítése előtt. Lásd: [az OMS-összekötő használata az Azure Government felhő](#fairfaxconfig) ebben a témakörben.

## <a name="prerequisites"></a>Előfeltételek
- Előtt az OMS-összekötő telepítése a Configuration Manager alkalmazásban, meg kell adnia a Configuration Manager engedélyekkel az OMS Szolgáltatáshoz. Pontosabban, meg kell adnia *közreműködői hozzáférés* az Azure-bA *erőforráscsoport* , amely tartalmazza az OMS Naplóelemzési munkaterület. A Naplóelemzési tartalom ehhez eljárásokat ismerteti. Lásd: [adja meg a Configuration Manager az OMS Szolgáltatáshoz engedélyekkel](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) az OMS-dokumentációban.

- Az OMS-összekötőt telepítenie kell a számítógépre, amelyen egy [szolgáltatáskapcsolódási pont](/sccm/core/servers/deploy/configure/about-the-service-connection-point) szerepel [online módban](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

  Ha OMS csatlakozott egy önálló elsődleges helyhez, és tervezze meg a központi adminisztrációs hely hozzáadása a környezetében, törölje az aktuális kapcsolatot, és az konfigurálja újra az összekötő az új központi adminisztrációs helyen.

- A Microsoft Monitoring Agent OMS együtt az OMS-összekötőt a szolgáltatáskapcsolódási pontnak telepítve kell telepítenie.  Az ügynök és az OMS-összekötő kell konfigurálni a ugyanazon **OMS-munkaterület**. Az ügynök telepítése, lásd: [töltse le és telepítse az ügynököt](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) az OMS-dokumentációban.

- Az összekötő és az ügynök telepítése után konfigurálnia kell az OMS használata a Configuration Manager-adatokat.  Ehhez az OMS-portálon az Ön [importálása a Configuration Manager gyűjteményeinek](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



## <a name="install-the-oms-connector"></a>Az OMS-összekötő telepítése  
1. A Configuration Manager konzolon konfigurálhatja a [előzetes kiadású szolgáltatások használandó](/sccm/core/servers/manage/pre-release-features), majd engedélyezze az OMS-összekötő használatát.  

2. Folytassa a **felügyeleti** > **Felhőszolgáltatások** > **OMS összekötő**. A menüszalagon kattintson a "Create kapcsolat Operations Management Suite". Ekkor megnyílik a **kapcsolat művelet felügyeleti csomag varázsló**. Válassza ki **következő**.  


3.    Az a **általános** lapon, győződjön meg arról, hogy rendelkezik a következő adatokat, majd válassza ki **következő**.  
  - A Configuration Manager regisztrált "Web Application and/or Web API" felügyeleti eszköz, és hogy rendelkezik a [ügyfél-azonosító az ehhez a regisztrációhoz](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).  
  - Létre egy ügyfélkulcsot a regisztrált felügyeleti eszköz az Azure Active Directoryban.  

  - Az Azure felügyeleti portálon megadott a regisztrált web app OMS-ben, hozzáféréssel a [adja meg a Configuration Manager az OMS Szolgáltatáshoz engedélyekkel](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms).  

4.    Az a **Azure Active Directory** lapon, a kapcsolat konfigurálása az OMS-be azáltal, hogy a **bérlői**, **ügyfél-azonosító**, és **titkos ügyfélkulcsot**, majd jelölje be **tovább**.  

5.    A a **OMS-kapcsolat konfigurációs** lapján adja meg a kapcsolat beállításait kitöltésével a **Azure-előfizetés**, **Azure erőforráscsoport**, és **Operations Management Suite-munkaterület**.  A munkaterület meg kell egyeznie a munkaterületen a Microsoft Management Agent ügynököt a szolgáltatáskapcsolódási pont telepített konfigurált.  

6.    Ellenőrizze, hogy a kapcsolat beállításait a **összegzés** lapon, majd válasszon **következő**. A **folyamatban** lapon megjelenik a kapcsolat állapotát, majd kell **Complete**.

Miután a Configuration Manager az OMS-be, adja hozzá vagy távolítson el gyűjteményt, és az OMS-kapcsolat tulajdonságainak megtekintéséhez.

## <a name="verify-the-oms-connector-properties"></a>Az OMS-összekötő tulajdonságainak ellenőrzése
1.    Nyissa meg a Configuration Manager konzol **felügyeleti** > **Felhőszolgáltatások**, majd válassza ki **OMS-összekötő** megnyitásához a **OMS kapcsolat ** lap**.
2.    Ezen a lapon belül van két lap található:
  - **Az Azure Active Directory:**   
    Ezen a lapon láthatók a **bérlői**, **ügyfél-azonosító**, **ügyfél titkos kulcs lejárati**, és lehetővé teszi, hogy ellenőrizze, hogy a titkos ügyfélkulcsot érvényessége lejárt.

  - **OMS kapcsolat tulajdonságai:**  
    Ezen a lapon láthatók a **Azure-előfizetés**, **Azure erőforráscsoport**, **Operations Management Suite-munkaterület**, valamint **eszközgyűjtemények, amely az Operations Management Suite adatokat kérhet**. Használja a **Hozzáadás** és **eltávolítása** gombok mely gyűjtemények módosítása engedélyezett.

## <a name="fairfaxconfig"></a> Az OMS-összekötő használata az Azure Government felhő


1.  Minden számítógépen, amely a Configuration Manager konzol telepítve van a következő konfigurációs fájlt a kormányzati felhőbe szerkesztése:  ***&lt;CM telepítési útvonala > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Szerkesztése:**

    A beállítás neve értékének módosításához *FairFaxArmResourceID* "https://management.usgovcloudapi.net/" egyenlőnek kell lennie

   - **Eredeti:** 
      &lt;Beállításnév = "FairFaxArmResourceId" serializeAs = "Karakterlánc" >   
      &lt;érték > &lt; /value >   
      &lt;/ Beállítás >

   - **Módosítani:**     
      &lt;beállítás neve "FairFaxArmResourceId" serializeAs = "Karakterlánc" = > &lt;érték > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ Beállítás >

  A beállítás neve értékének módosításához *FairFaxAuthorityResource* "https://login.microsoftonline.com/" egyenlőnek kell lennie

  - **Eredeti:** &lt;Beállításnév = "FairFaxAuthorityResource" serializeAs = "Karakterlánc" >   
    &lt;érték > &lt; /value >

    - **Módosítani:** &lt;Beállításnév = "FairFaxAuthorityResource" serializeAs = "Karakterlánc" >   
    &lt;érték > https://login.microsoftonline.com/ &lt; /value >

2.    A fájl két módosításainak mentése, után indítsa újra a ugyanazon a számítógépen a Configuration Manager konzolon, és ez a konzol segítségével az OMS-összekötő telepítése. Az összekötő telepítéséhez, olvassa el a [szinkronizálni az adatokat a Configuration Manager a Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), és válassza ki a **Operations Management Suite-munkaterület** , amely megtalálható a Microsoft Azure Government felhő.

3.    Az OMS-összekötő telepítése után a kormányzati felhőben nincs elérhető kapcsolat, amely kapcsolódik a helyhez egyetlen konzol használata esetén.

