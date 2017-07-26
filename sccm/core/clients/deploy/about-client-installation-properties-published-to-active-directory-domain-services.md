---
title: "Ügyfél-telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban |} Microsoft Docs"
description: "Az Active Directory tartományi szolgáltatások a System Center Configuration Manager közzétett ügyfél-telepítési tulajdonságokról használja."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 744bc3792a02f13d3cf940cd1a4f2fd8749ee2f4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-installation-properties-published-to-active-directory-domain-services"></a>Információ az Active Directory Domain Servicesben közzétett ügyfélszoftver-telepítési tulajdonságokról

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Amikor kiterjeszti az Active Directory-sémát a System Center Configuration Manager, és a helyet közzéteszi az Active Directory tartományi szolgáltatásokban, számos ügyfél-telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban közzétett. Ha egy számítógép megtalálja ezeket az ügyfélszoftver telepítési tulajdonságokat, akkor használhatja azokat a Configuration Manager-ügyfél telepítésekor.  

 Az Active Directory tartományszolgáltatások használata az ügyféltelepítési tulajdonságok közzétételéhez a következő előnyökkel jár:  

-   Szoftverfrissítési ponton alapuló ügyfél esetén és a Csoportházirendes ügyféltelepítés nem igényli a telepítési paraméterek hozzanak létre minden olyan számítógépen.  

-   Ezek az információk automatikusan állnak elő, ami kiiktatja a telepítési tulajdonságok manuális megadásánál keletkező emberi hibákat.  

> [!NOTE]  
>  Az Active Directory-séma kiterjesztése a Configuration Manager és a hely közzététele kapcsolatban további információkért lásd: [sémakiterjesztések a System Center Configuration Manager](../../plan-design/network/schema-extensions.md).  

## <a name="client-installation-properties-published-to-active-directory-domain-services"></a>Az Active Directory tartományi szolgáltatásokban közzétett ügyfél-telepítési tulajdonságokról  
Az ügyfél-telepítési tulajdonságok listáját a következő: Alább felsorolt minden elemre vonatkozó további információkért lásd: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties.md).  

-   A Configuration Manager-hely kódja.  

-   A helykiszolgáló aláíró tanúsítványa.  

-   A megbízható legfelső szintű kulcs.  

-   A HTTP és a HTTPS protokollokhoz használt ügyfélkommunikációs portok.  

-   A tartalék állapotkezelő pont. Ha a helynek több tartalék állapotkezelő pont van, csak az első címtárra telepített közzé van téve az Active Directory tartományi szolgáltatásokban.  

-   A beállítás azt jelzi, hogy az ügyfélnek csak HTTPS protokollal lehet kommunikálnia.  

-   PKI-tanúsítványokra vonatkozó beállítások:  

   -   Használni kell-e az ügyfél PKI-tanúsítványát.  

   -   Választási feltételek a tanúsítványválasztáshoz. Erre akkor lehet szükség, mert az ügyfélnek több érvényes PKI-tanúsítvánnyal, amely használható a Configuration Manager van.  

   -   Ez a beállítás határozza meg, hogy melyik tanúsítványt használja, ha az ügyfélnek több érvényes tanúsítványa van a tanúsítványkiválasztási folyamat után.  

   -   A tanúsítványkiállítói lista, mely tartalmazza a megbízható gyökér szintű hitelesítésszolgáltatói tanúsítványok felsorolását.  

-   A Client.msi telepítési tulajdonságai, melyek az **Ügyfél** lapon vannak megadva a **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanelben.

Ügyféltelepítés (CCMSetup) használ a tulajdonságokat, amelyeket a rendszer közzéteszi az Active Directory tartományi szolgáltatások csak akkor, ha nincsenek más megadva a tulajdonságai a következő módszerek egyikével:  

-   A manuális telepítési módszer (a cikk későbbi részében leírt)

-   A Csoportházirenden alapuló telepítési módszer (a cikk későbbi részében leírt)

> [!NOTE]  
>  Az ügyfél telepítéséhez használt ügyfél-telepítési tulajdonságokat. Ezek a Tulajdonságok felülírhatják azokat a hozzárendelt helyről származó új beállítások után az ügyfél telepítve van, és sikeresen hozzá van rendelve egy Configuration Manager-hely.  

 A következő szakaszokban az olvasható információk segítségével határozza meg, mely a Configuration Manager ügyféltelepítési módszerek használják az Active Directory tartományi szolgáltatásokban az ügyféltelepítési tulajdonságok beszerzésére.  

## <a name="client-push-installation"></a>Ügyfél leküldéses telepítése  
 Az ügyfél leküldéses telepítése nem használja az Active Directory tartományszolgáltatásokat az ügyféltelepítési tulajdonságok beszerzésére.  

 Ehelyett az ügyfél-telepítési tulajdonságokat adhat meg a **ügyfél** lapján a **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanel megnyitásához. Ezeket a lehetőségek és az ügyfélhez kapcsolódó helybeállítások egy fájlban vannak eltárolva, melyet az ügyfél olvas az ügyféltelepítés közben.  

> [!NOTE]  
>  Nem kell megadnia semmilyen CCMSetup tulajdonságot az ügyfélleküldéses telepítéshez, a tartalék állapotkezelő ponthoz vagy a megbízható legfelső szintű kulcshoz az **Ügxfél** lapon. Ezek a beállítások automatikusan kerülnek az ügyfelekhez, amikor ügyfélleküldéses telepítés használatával telepíti azokat.  

 Semmilyen tulajdonságot, melyet a **ügyfél** lapon közzé az Active Directory tartományi szolgáltatásokban, ha a helyet közzéteszi az Active Directory tartományi szolgáltatásokban. Ezeket a beállítáokat olvassa be az ügyféltelepítés, ha a CCMSetup futását telepítési tulajdonságok nélkül indítják el.  

## <a name="software-update-point-based-installation"></a>Szoftverfrissítési ponton alapuló telepítés  
 A szoftverfrissítési ponton alapuló telepítési módszer nem támogatja a telepítési tulajdonságok hozzáadását a CCMSetup parancssorhoz.  

 Ha nincsenek megadva parancssori tulajdonságok az ügyfélszámítógépen a csoportházirend használatával, akkor a CCMSetup az Active Directory tartományszolgáltatásokban keres telepítési tulajdonságokat.  

## <a name="group-policy-installation"></a>Csoportházirend telepítése  
 A csoportházirenden alapuló telepítési módszer nem támogatja a telepítési tulajdonságok hozzáadását a CCMSetup parancssorhoz.  

 Ha nincsenek megadva parancssori tulajdonságok az ügyfélszámítógépen, akkor a CCMSetup az Active Directory tartományszolgáltatásokban keres telepítési tulajdonságokat.  

## <a name="manual-installation"></a>Manuális telepítés  
 A CCMSetup a következő esetekben keresi a telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban:  

-   A CCMSetup.exe parancs után nincsenek megadva parancssori tulajdonságok.  

-   A számítógép kiépítése nem csoportházirend használatával megadott telepítési tulajdonságokkal történt.  

## <a name="logon-script-installation"></a>Bejelentkezési parancsprogramfájl telepítése  
 A CCMSetup a következő esetekben keresi a telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban:  

-   A CCMSetup.exe parancs után nincsenek megadva parancssori tulajdonságok.  

-   A számítógép kiépítése nem csoportházirend használatával megadott telepítési tulajdonságokkal történt.  

## <a name="software-distribution-installation"></a>Szoftverterjesztéses telepítés  
 A CCMSetup a következő esetekben keresi a telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban:  

-   A CCMSetup.exe parancs után nincsenek megadva parancssori tulajdonságok.  

-   A számítógép kiépítése nem csoportházirend használatával megadott telepítési tulajdonságokkal történt.  

## <a name="installations-for-clients-that-cannot-access-active-directory-domain-services"></a>Az ügyfelek nem tudnak hozzáférni az Active Directory tartományi szolgáltatások telepítése  
Ezek az ügyfélszámítógépek nem tudja elolvasni vagy hozzáférni a közzétett telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokból.

 Ezek az ügyfelek a következők:  

-   Munkacsoport-számítógépeket.  

-   Nincs közzétéve az Active Directory tartományi szolgáltatásokban a Configuration Manager helyhez rendelt ügyfelek.  

-   Ha az interneten vannak telepített ügyfelek.  

