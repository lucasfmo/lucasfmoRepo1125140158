---

title: "Integráció a Windows Update for Business a Windows 10 rendszerben |} Microsoft Docs"
description: "A Windows Update for Business segítségével naprakész állapotban a Windows 10-alapú eszközök a szervezetben az eszközök a Windows Update szolgáltatáshoz való kapcsolódás."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 8bdbacd54632475ac69a0d0a9a34b2567c3daa13
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Integráció a Windows Update for Business szolgáltatással a Windows 10 rendszerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Windows Update for Business (WUfB) révén mindig naprakészen tarthatja a Windows 10-alapú eszközöket a szervezetben a legújabb biztonsági védelmekkel és Windows-szolgáltatásokkal, amikor ezek az eszközök közvetlenül a Windows Update (WU) szolgáltatáshoz csatlakoznak. A Configuration Manager képes a megkülönböztetni a szoftverfrissítéseket a wufb-t használó Windows 10-számítógépeket és a WSUS.  

 Egyes Configuration Manager szolgáltatások nem érhetők el, ha a Configuration Manager-ügyfelek megkapják a frissítéseket a WU-tól, beleértve a wufb-t vagy a Windows insider program résztvevői vannak konfigurálva:  

-   A Windows Update megfelelőségi jelentéskészítése:  

    -   A Configuration Manager nem fogja érzékelni a WU-n közzétett frissítéseket. Megjeleníti a Configuration Manager-ügyfelek, hogy fogadjanak frissítéseket a WU-tól konfigurált **ismeretlen** ezeket a frissítéseket a Configuration Manager konzolon.  

    -   Az összesített megfelelőségi állapot hibaelhárítása nehéz, mert az **ismeretlen** állapot korábban csak azoknál az ügyfeleknél volt használatos, amelyek nem jelentettek vissza vizsgálati állapotot a WSUS-nak.  Most is a Configuration Manager ügyfelek, amelyek megkapják a frissítéseket a WU-tól.  

    -   A frissítési megfelelőségi állapot alapján (a vállalati erőforrásokhoz való) feltételes hozzáférés nem működik megfelelően működni azon ügyfeleknél, amelyek megkapják a frissítéseket a WU-tól, mert azok soha nem felel meg a Configuration Manager megfelelőségi.  

    -   A definíciófrissítések megfelelősége a teljes megfelelőségi jelentéskészítés része, és szintén nem fog megfelelően működni.  A definíciófrissítési megfelelőség is része feltételes hozzáférési kiértékelésnek  

-   A Defender számára készített teljes Endpoint Protection-jelentés a frissítési megfelelőségi állapot alapján nem ad vissza pontos eredményeket a hiányzó vizsgálati adatok miatt.  

-   A Configuration Manager csak akkor tudja telepíteni a Microsoft-frissítések, például az Office, az Internet Explorer és a Visual Studio a frissítések fogadásához a wufb-hez csatlakozó ügyfelek.  

-   A Configuration Manager csak akkor tudja telepíteni a 3. fél frissítések WSUS közzétett és a Configuration Manager használatával kezelt frissítések fogadásához a wufb-hez csatlakozó ügyfelek számára.  

-   A szoftverfrissítési infrastruktúrát használó a Configuration Manager teljes ügyféltelepítése nem fog működni a frissítések fogadásához a wufb-hez csatlakozó ügyfelek.  

## <a name="identify-clients-that-use--wufb-for-windows-10-updates"></a>A Windows 10-frissítésekhez WUfB-t használó ügyfelek azonosítása  
 Az alábbi eljárás segítségével azonosítsa a Windows 10-frissítések beszerzéséhez a WUfB-t használó ügyfeleket, állítsa le ezeknél az ügyfeleknél a frissítéseknek a WSUS használatával történő letöltését, és telepítsen egy ügyfélügynök-beállítást a szoftverfrissítési munkafolyamat letiltására.  

 **Előfeltételek**  

-   Windows 10 Pro asztali verzió, Windows 10 Enterprise Edition, 1511-es verzió vagy újabb rendszerű ügyfelek  

-   Telepített[Windows Update for Business](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) , és az ügyfelek a WUfB-t használják a Windows 10-frissítések beszerzésére.  

#### <a name="to-identify-clients-that-use-wufb"></a>A WUfB-t használó ügyfelek azonosítása  

1.  Ha korábban engedélyezve lett, tiltsa le a Windows Update Agent szoftvert, hogy az ne keressen a WSUS szolgáltatásban.   
    A beállításkulcs **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer** annak jelzésére, hogy a számítógép van keres a WSUS vagy a Windows Update állítható be.  Ha az érték 2, akkor nem keres a WSUS.  

2.  Nincs egy új attribútum **UseWUServer**alatt a **Windows Update** Configuration Manager Resource Explorer csomópontja.  

3.  Hozzon létre egy gyűjteményt a **UseWUServer** attribútum alapján az összes számítógéphez, amely a WUfB szolgáltatáshoz csatlakozva szerzi be a frissítéseket és az új verziókat.  

4.  Hozzon létre egy ügyfélügynök-beállítást a szoftverfrissítési munkafolyamat letiltásához, és telepítése a beállítást a közvetlenül a WUfB szolgáltatáshoz csatlakozó számítógépek gyűjteményére.  

5.  Megjeleníti a wufb szolgáltatással felügyelt számítógépek **ismeretlen** megfelelőségi állapotánál és nem kell beleszámítani az összesített megfelelőségi arányba.  

