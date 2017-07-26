---
title: "Hardverleltár |} Microsoft dokumentumok |} Linux, UNIX "
description: "Megtudhatja, hogyan használják a Hardverleltár Linux és UNIX rendszeren a System Center Configuration Managerben."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1026d616-2a20-4fb2-8604-d331763937f8
caps.latest.revision: 6
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: b6776fbe0cfca23244d767cffd554a2ef4567a2d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="hardware-inventory-for-linux-and-unix-in-system-center-configuration-manager"></a>Hardverleltár Linux és UNIX rendszeren a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-ügyfél Linux és UNIX rendszerű Hardverleltár támogatja. Hardverleltár összegyűjtése után megtekintheti a hardverleltárat az erőforrás-kezelővel vagy a Configuration Manager-jelentések, és ezen információk használatával hozzon létre lekérdezéseket és gyűjteményeket, amelyek lehetővé teszik a következő műveleteket:  

-   Szoftver központi telepítése  

-   Karbantartási időszakok kényszerítése  

-   Egyedi ügyfélbeállítások központi telepítése  

 A Linux és UNIX rendszerű kiszolgálók hardverleltára szabványos Common Information Model- (CIM-) kiszolgálót használ. A CIM-kiszolgáló a szoftverfrissítési szolgáltatásként (vagy démonként) fut, és a Distributed Management Task Force (DMTF) szabványon alapuló felügyeleti infrastruktúrát biztosít. A CIM-kiszolgáló a Windows-alapú számítógépeken elérhető Windows Management Infrastructure (WMI) CIM-szolgáltatásaihoz hasonló funkciókat nyújt.  

 A Linux és UNIX rendszerekhez készült ügyfél 1. kumulatív frissítésétől kezdődően az **Open Group** nyílt forráskódú **omiserver**1.0.6-os verzióját használja. (Az 1. kumulatív frissítés előtt az ügyfél a **nanowbem** CIM-kiszolgálót használta).  

 A CIM-kiszolgáló a Linux és UNIX rendszerekhez készült ügyfél részeként települ. A Linux és UNIX rendszerekhez készült ügyfél közvetlenül kommunikál a CIM-kiszolgálóval, és nem használja annak WS-MAN felületét. A WS-MAN port a CIM-kiszolgálón le van tiltva az ügyfél telepítésekor. A Microsoft nyílt forráskódú, az Open Management Infrastructure (OMI) nevű projekten keresztül elérhetővé tett CIM-kiszolgálót fejlesztett ki. Az OMI projekttel kapcsolatos további információkért lásd [az Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) webhelyét.  

 A Linux és UNIX rendszerű kiszolgálókon a hardverleltár meglévő Win32 WMI-osztályoknak és tulajdonságoknak Linux- és UNIX-kiszolgálók által használt egyenértékű osztályokra és tulajdonságokra való leképezésével működik. Ez egy az egyhez típusú hozzárendelés osztályok és tulajdonságok lehetővé teszi, hogy a Linux és UNIX rendszerű Hardverleltár integrálását a Configuration Managerrel. A Configuration Manager konzol és a jelentéseknél Windows-alapú számítógépekről készlet együtt jelennek meg a leltáradatokat a Linux és UNIX rendszerű kiszolgálókról. Ez egységes heterogén felügyeleti felületet nyújt.  

> [!TIP]  
>  A különböző Linux és UNIX operációs rendszerek azonosításához a lekérdezésekben és gyűjteményekben az **Operating System** osztály **Caption** értékét használhatja.  

##  <a name="BKMK_ConfigHardwareforLnU"></a> Hardverleltár konfigurálása a Linux és UNIX rendszerű kiszolgálókhoz  
 Használhatja az alapértelmezett ügyfélbeállításokat, vagy létrehozhat egyéni ügyfél-eszközbeállításokat a hardverleltár konfigurálására. Egyéni ügyfél-eszközbeállítások használata esetén konfigurálhatja azon osztályokat és a tulajdonságokat, amelyeket csak a Linux és UNIX rendszerű kiszolgálókról kíván gyűjteni. Megadhat egyéni ütemezéseket is a Linux és UNIX rendszerű kiszolgálók teljes vagy különbözeti leltárainak összegyűjtésére vonatkozóan.  

 A Linux- és UNIX rendszerhez készült ügyfél a következő, Linux és UNIX rendszerű kiszolgálókon elérhető hardverleltárosztályokat támogatja:  

-   Win32_BIOS  

-   Win32_ComputerSystem  

-   Win32_DiskDrive  

-   Win32_DiskPartition  

-   Win32_NetworkAdapter  

-   Win32_NetworkAdapterConfiguration  

-   Win32_OperatingSystem  

-   Win32_Process  

-   Win32_Service  

-   Win32Reg_AddRemovePrograms  

-   SMS_LogicalDisk  

-   SMS_Processor  

 Leltárosztályok nem minden tulajdonságok engedélyezettek a Linux és UNIX rendszerű számítógépekhez a Configuration Managerben.  

##  <a name="BKMK_OperationsforHardwareforLnU"></a> Hardverleltárral kapcsolatos műveletek  
 Miután hardverleltár-adatokat gyűjtött Linux és UNIX rendszerű kiszolgálókról, ugyanúgy megtekintheti és használhatja ezt az információt, mint a más számítógépekről összegyűjtött leltárat:  

-   Az erőforrás-kezelő használata a Linux- és UNIX-kiszolgálókról begyűjtött hardverleltár részletes adatainak megtekintésére  

-   Lekérdezések létrehozása adott hardverkonfigurációk alapján  

-   Adott hardverkonfiguráción alapuló, lekérdezésalapú gyűjtemények létrehozása  

-   A hardverkonfigurációk részletes adatait megjelenítő jelentések futtatása  

 A Linux vagy UNIX-kiszolgálók hardverleltára az ügyfélbeállításokban megadott ütemezésnek megfelelően fut, alapértelmezés szerint hétnaponta. A Linux- és UNIX-ügyfél a teljes leltározási ciklusokat és a különbözeti leltározási ciklusokat is támogatja.  

 A Linux vagy UNIX rendszerű kiszolgálón lévő ügyfél emellett a hardverleltár azonnal futtatására is kényszeríthető. A hardverleltár futtatásához az adott ügyfélen használjon **gyökérszintű** hitelesítő adatokat a hardverleltár-ciklus elindításához a következő paranccsal: **/opt/microsoft/configmgr/bin/ccmexec - rs hinv**  

 A hardverleltárral kapcsolatos műveletek bekerülnek az ügyfél **scxcm.log**nevű naplófájljába.  

##  <a name="BKMK_CustomHINVforLinux"></a> Az Open Management Infrastructure használata egyéni hardverleltár létrehozásához  
 A Linux- és UNIX-ügyfél támogatja egyéni hardverleltár létrehozását az Open Management Infrastructure (OMI) használatával. Ehhez kövesse az alábbi lépéseket:  

1.  Hozzon létre egy egyéni leltárszolgáltatót az OMI-forrás használatával  

2.  Konfigurálja a számítógépeket az új szolgáltató használatára a leltár jelentéséhez  

3.  Az új szolgáltató támogatásához a Configuration Manager engedélyezése  

###  <a name="BKMK_LinuxProvider"></a> Hozzon létre egy egyéni hardverleltár-szolgáltatót a Linux és UNIX rendszerű számítógépekhez:  
 Hozzon létre egy egyéni Hardverleltár-szolgáltatót a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült, használja a **OMI Source - v.1.0.6** és kövesse az OMI Getting Started Guide utasításait. Ez a folyamat tartalmazza egy Managed Object Format (MOF) fájl létrehozását az új szolgáltató sémájának definiálásához. Később importálhatja a MOF-fájlt a Configuration Manager az új egyéni hardverleltárosztály támogatásának engedélyezéséhez.  

 Mind az OMI Source - v.1.0.6, mind az OMI Getting Started Guide letölthető [az Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) webhelyéről. A letöltések keresheti meg a **dokumentumok** lapján, a következő weblapot a OpenGroup.org webhelyen: [Nyissa meg a Management Infrastructure (OMI)](http://go.microsoft.com/fwlink/p/?LinkId=286805).  

###  <a name="BKMK_AddProvidertoLinux"></a> Konfigurálja az egyéni hardverleltár-szolgáltatóval mindegyik, Linux vagy UNIX rendszert futtató számítógépet:  
 Az egyéni leltárszolgáltató létrehozása után, másolja le, majd regisztrálja a szolgáltatói függvénytár fájlját minden olyan számítógépen, amely begyűjtendő leltárt tartalmaz.  

1.  Másolja a szolgáltatói függvénytárt minden Linux és UNIX rendszerű számítógépre, amelyről leltárt szeretne gyűjteni. A szolgáltatói függvénytár neve a következőhöz: **XYZ_MyProvider.so**  

2.  Ezután az egyes Linux és UNIX rendszerű számítógépeken regisztrálni kell az OMI-kiszolgálón a szolgáltatói függvénytárat. Az OMI-kiszolgáló telepítése a számítógépre, amikor telepíti a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült, de egyéni szolgáltatókat manuálisan kell regisztrálni. A következő parancssor segítségével regisztrálja a szolgáltatót: **/opt/microsoft/omi/bin/omireg XYZ_MyProvider.so**  

3.  Miután regisztrálta az új szolgáltatót, tesztelje azt az **omicli** eszköz használatával. A **omicli** eszköz minden egyes Linux és UNIX rendszerű számítógépen telepítve van, a Configuration Manager-ügyfél Linux és UNIX rendszerű telepítésekor. Ha például a létrehozott szolgáltató neve **XYZ_MyProvider** , futtassa a következő parancsot a számítógépen: **/opt/microsoft/omi/bin/omicli ei root/cimv2 XYZ_MyProvider**  

     További információt az **omicli** eszközről és az egyéni szolgáltatók teszteléséről az OMI Getting Started Guide című útmutatóban talál.  

> [!TIP]  
>  Egyéni szolgáltatók telepítéséhez és az egyéni szolgáltató regisztrálására Linux és UNIX rendszerű ügyfélszámítógépeken használja a szoftverterjesztést.  

###  <a name="BKMK_AddLinuxProvidertoCM"></a> Engedélyezze az új leltárosztályt a Configuration Managerben:  
 Ahhoz, hogy a Configuration Manager jelentést tudjon készíteni az új szolgáltató által a Linux és UNIX rendszerű számítógépekről jelentett leltárról, importálnia kell az egyéni szolgáltató sémáját definiáló Managed Object Format (MOF) fájlt.  

 Egyéni MOF-fájl importálása a Configuration Managerbe, lásd: [Hardverleltár konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

