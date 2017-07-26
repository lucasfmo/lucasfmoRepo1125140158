---
title: "Hardverleltár konfigurálása |} Microsoft dokumentumok |} mobileszközök"
description: "A Microsoft Intune és a System Center Configuration Manager által beléptetett mobileszközök esetében a Hardverleltár beállításának."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 78a0aecc-f775-451e-aa05-56377ec91b1f
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 7ab9042a525e07b8e3107479cedeec6b99f7bc86
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-hardware-inventory-for-mobile-devices-enrolled-by-microsoft-intune-and-system-center-configuration-manager"></a>A Microsoft Intune és a System Center Configuration Manager által beléptetett mobileszközök esetében a Hardverleltár konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Managerben hozhatja létre a hardverleltárt az iOS, Android és Windows eszközökhöz a Microsoft Intune-összekötő használatával. Hardverleltár konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Managerben a Hardverleltár bővítése](../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 A Microsoft Intune-ban eszközök beléptetésének módjával kapcsolatos információkért lásd: [mobileszközök kezelése a Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).  

## <a name="hardware-inventory-for-mobile-devices"></a>Mobileszközökhöz tartozó hardverleltárak  
 A következő táblázat azokat a leltárosztályokat érhető el, a Hardverleltár leggyakrabban használt mobileszköz-platformok között.  

 **iOS**  

|Hardverleltárosztály|iOS|  
|------------------------------|---------|  
|Név|Device_ComputerSystem.DeviceName|  
|Az eszköz egyedi azonosítója|Device_ComputerSystem.UDID|  
|Sorozatszám|Device_ComputerSystem.SerialNumber|  
|E-mail cím|Device_Email.OwnerEmailAddress|  
|Operációs rendszer típusa|Nem alkalmazható|  
|Operációs rendszer verziója|Device_OSInformation.OSVersion|  
|Alverziószám|Nem alkalmazható|  
|Szervizcsomag főverziója|Nem alkalmazható|  
|Szervizcsomag alverziója|Nem alkalmazható|  
|Operációs rendszer nyelve|Nem alkalmazható|  
|Teljes tárolóhely|Device_Memory.DeviceCapacity|  
|Szabad tárolóhely|Device_Memory.AvailableDeviceCapacity|  
|Nemzetközi mobilkészülék-azonosító (IMEI)|Device_ComputerSystem.IMEI|  
|Mobilkészülék-azonosító szám (MEID)|Device_ComputerSystem.MEID|  
|Gyártó|Nem alkalmazható|  
|Modell|Modellnév|  
|Telefonszám<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Előfizető szolgáltatója|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Mobiltechnológia|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **Android--**  

> [!NOTE]  
>  **MEGJEGYZÉS:** Android leltározási osztályok az Androidos vállalati portál alkalmazás használatakor érhetők el.  

|Hardverleltárosztály|Android|  
|------------------------------|-------------|  
|Név|Nem alkalmazható|  
|Az eszköz egyedi azonosítója|Nem alkalmazható|  
|Sorozatszám|Device_ComputerSystem.SerialNumber|  
|E-mail cím|Nem alkalmazható|  
|Operációs rendszer típusa|Device_OSInformation.Platform|  
|Operációs rendszer verziója|Device_OSInformation.Version|  
|Alverziószám|Nem alkalmazható|  
|Szervizcsomag főverziója|Nem alkalmazható|  
|Szervizcsomag alverziója|Nem alkalmazható|  
|Operációs rendszer nyelve|Nem alkalmazható|  
|Teljes tárolóhely|Device_Memory.StorageTotal|  
|Szabad tárolóhely|Device_Memory.StorageFree|  
|Nemzetközi mobilkészülék-azonosító (IMEI)|Device_ComputerSystem.IMEI|  
|Mobilkészülék-azonosító szám (MEID)|Nem alkalmazható|  
|Gyártó|Device_Info.Manufacturer|  
|Modell|Device_Info.Model|  
|Telefonszám<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Előfizető szolgáltatója|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Mobiltechnológia|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **Windows Phone 8 vagy 8.1**  

|Hardverleltárosztály|Windows Phone 8 és Windows Phone 8.1|  
|------------------------------|-------------------------------------------|  
|Név|Device_ComputerSystem.DeviceName|  
|Az eszköz egyedi azonosítója|Device_ComputerSystem.DeviceClientID|  
|Sorozatszám|Nem alkalmazható|  
|E-mail cím|Device_Email.OwnerEmailAddress|  
|Operációs rendszer típusa|Device_OSInformation.Platform|  
|Operációs rendszer verziója|Device_ComputerSystem.SoftwareVersion|  
|Alverziószám|Nem alkalmazható|  
|Szervizcsomag főverziója|Nem alkalmazható|  
|Szervizcsomag alverziója|Nem alkalmazható|  
|Operációs rendszer nyelve|Device_OSInformation.Language|  
|Teljes tárolóhely|Nem alkalmazható|  
|Szabad tárolóhely|Nem alkalmazható|  
|Nemzetközi mobilkészülék-azonosító (IMEI)|Nem alkalmazható|  
|Mobilkészülék-azonosító szám (MEID)|Nem alkalmazható|  
|Gyártó|Device_ComputerSystem.DeviceManufacturer|  
|Modell|Device_ComputerSystem.DeviceModel|  
|Telefonszám<sup>1</sup>|Nem alkalmazható|  
|Előfizető szolgáltatója|Nem alkalmazható|  
|Mobiltechnológia|Nem alkalmazható|  
|Wi-Fi MAC|Nem alkalmazható|  

 **Windows RT**  

|Hardverleltárosztály|Windows RT|  
|------------------------------|----------------|  
|Név|Device_ComputerSystem.DeviceName|  
|Az eszköz egyedi azonosítója|Device_ComputerSystem.DeviceName|  
|Sorozatszám|Nem alkalmazható|  
|E-mail cím|Device_Email.OwnerEmailAddress|  
|Operációs rendszer típusa|CCM_OperatingSystem .SystemType|  
|Operációs rendszer verziója|Win32_OperatingSystem.Version|  
|Alverziószám|Win32_OperatingSystem.BuildNumber|  
|Szervizcsomag főverziója|Win32_OperatingSystem.ServicePackMajorVersion|  
|Szervizcsomag alverziója|Win32_OperatingSystem.ServicePackMinorVersion|  
|Operációs rendszer nyelve|Nem alkalmazható|  
|Teljes tárolóhely|Win32_PhysicalMemory.Capacity|  
|Szabad tárolóhely|Win32_OperatingSystem.FreePhysicalMemory|  
|Nemzetközi mobilkészülék-azonosító (IMEI)|Nem alkalmazható|  
|Mobilkészülék-azonosító szám (MEID)|Nem alkalmazható|  
|Gyártó|Win32_ComputerSystem.Manufacturer|  
|Modell|Win32_ComputerSystem.Model|  
|Telefonszám<sup>1</sup>|Nem alkalmazható|  
|Előfizető szolgáltatója|Nem alkalmazható|  
|Mobiltechnológia|Nem alkalmazható|  
|Wi-Fi MAC|Win32_NetworkAdapter.MACAddress|  

 <sup>1</sup> A telefonszám az utolsó 4 számjegy kivételével * karakterekkel van maszkolva.  

 A telefonszámot tároló leltár létrehozásához az eszköznek SIM kártyával, a SIM kártyának pedig a szolgáltató által kirendelt telefonszámmal kell rendelkeznie.  

