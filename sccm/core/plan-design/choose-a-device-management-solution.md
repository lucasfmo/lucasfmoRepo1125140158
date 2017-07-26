---
title: "Válasszon egy Eszközkezelési megoldás - Configuration Manager |} Microsoft Docs"
description: "További információk a számítógépek, kiszolgálók és eszközök kezelése a System Center Configuration Manager kínál a megoldások."
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: 14
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3eb48942c1259d2aa1b3c200fad73b39b11c0b8c
ms.openlocfilehash: 9989ea1bf4cb74a6286ebae9de7614ed622de5b6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>Eszközfelügyeleti megoldás választása a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager (más néven ConfgMgr vagy SCCM) számítógépek, kiszolgálók és eszközök kezelésére szolgáló különböző megoldásokat kínál. Kiválaszthatja a megfelelő meg a kívánt eszközplatformok kezeléséhez és a szükséges felügyeleti funkciók alapján megoldást.  


##  <a name="overview-of-device-management-solutions"></a>Eszköz megoldások áttekintése  
 Ez a cikk ismerteti a négy Eszközkezelési megoldásokkal: a Configuration Manager ügyfélalkalmazás, a helyi Configuration Manager-infrastruktúrát, a Microsoft Intune és az Exchange. A cikk arra a következtetésre jut, hasonlítsa össze a felügyeleti megoldásokra, egy alapuló, két táblákkal [támogatott mobileszközplatformok](#compare-device-management-solutions-based-on-supported-mobile-device-platforms), és egy alapján [felügyeleti funkció](#compare-mobile-device-management-solutions-based-on-management-functionality).


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Eszközök kezelése a Configuration Manager-ügyféllel  

Ezt a beállítást, amelyet telepíteni kell a Configuration Manager ügyfélalkalmazás az eszközökön, számítógépek, kiszolgálók és a környezet más eszközök kezelésére a legtöbb szolgáltatásokat biztosítja. További információkért lásd: [ügyféltelepítési módszerek a System Center Configuration Managerben](/sccm/core/clients/deploy/plan/client-installation-methods).  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>A Configuration Manager-infrastruktúrát a helyszíni eszközök kezelése  

Ez a beállítás bizonyos eszközplatformok operációs rendszereinek beépített eszközfelügyeleti képességeit használja. Amíg nem funkcionalitást, mint az ügyfélalapú felügyelet, a helyszíni mobileszköz-kezelés lehetővé teszi egy világosabb módszerrel használatával a helyi Configuration Manager erőforrások eléréséhez és az eszközök kezeléséhez. Vegye figyelembe, hogy ez a beállítás jelenleg csak a Windows 10-es számítógépekhez és Windows 10 Mobile támogatott eszközöket.  

További információkért lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>A Microsoft Intune (hibrid) eszközök kezelése  

Ez a beállítás a Microsoft Intune használatával regisztrálhat és kezelhet eszközöket, a Configuration Manager a helyi erőforrások használata helyett. Annak ellenére, hogy az Intune kezeli az eszközöket, a felügyeleti feladatok a Configuration Manager konzolon érhető el. Ez a beállítás az összes nagyobb mobil operációs rendszereket, beleértve a Windows 10 Mobile, Windows Phone, iOS, Mac OS X és Android támogatja. emellett pedig a szervezet Windows 8.1-es és Windows 10-es számítógépeinek felügyeletét is lehetővé teszi.  

További információk: [Hibrid mobileszköz-felügyelet a System Center Configuration Managerrel és a Microsoft Intune-nal](../../mdm/understand/hybrid-mobile-device-management.md).  

###  <a name="manage-devices-with-microsoft-exchange"></a>A Microsoft Exchange-eszközök kezelése  

Ez a beállítás az Exchange Server-összekötő használja a Configuration Manager több Exchange-kiszolgálóhoz csatlakozni. Ezzel biztosítva, amely képes csatlakozni az Exchange ActiveSync-eszköz felügyelete. Beállíthatja az Exchange mobileszköz-kezelési funkcióit, az eszköztartalom távoli törlését és a beállítások több Exchange-kiszolgáló, a Configuration Manager konzoljáról.  

További információkért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

Is használhatja e Eszközkezelési megoldásokkal, önmagukban vagy egymással kombinálva. Például az ügyfélalapú felügyeleti módszerrel segítségével kezelheti a számítógépek és kiszolgálók a szervezetében, és is az Intune használatával kezeli a mobileszközöket. Egyesítő megoldások ezzel a módszerrel, által is foglalkozik az összes a Configuration Manager konzoljáról felügyeleti eszköz igényeinek.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>A támogatott mobileszköz-platformok alapján az eszközfelügyeleti megoldások összehasonlítása  

|Platform|A Configuration Manager-ügyféllel|A Configuration Manager a Microsoft Intune (hibrid)|A\-helyszíni mobileszköz-kezelés|A Configuration Manager és az Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||Igen||Igen|  
|iOS||Igen||Igen|  
|Mac OS X|Igen|||Igen|  
|UNIX/Linux|Igen|||Igen|  
|Windows 10|Igen|Igen|Igen|Igen|  
|Windows 10 mobil verzió||Igen|Igen|Igen|  
|Windows (korábbi verziók)|Igen|Igen||Igen|  
|Windows CE|Igen (mobileszközön futó korábbi ügyféllel)|||Igen|  
|Windows Embedded|Igen||||  
|Windows Phone||Igen||Igen|  
|Windows Server|Igen|||Igen|  

 A támogatott platformok teljes listáját lásd: [operációs rendszerek támogatott ügyfelek és eszközök a System Center Configuration Manager](configs\supported-operating-systems-for-clients-and-devices.md).

##  <a name="bkmk_comp2"></a> A mobileszköz-felügyeleti megoldások összehasonlítása felügyeleti funkciók alapján  

|Felügyeleti funkció|A Configuration Manager-ügyféllel|A Configuration Manager a Microsoft Intune (hibrid)|A\-helyszíni mobileszköz-kezelés|A Configuration Manager és az Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Nyilvános kulcsokra épülő infrastruktúra (PKI) biztonsági a mobileszköz és a Configuration Manager (használ kölcsönös hitelesítéssel és SSL adatátviteli titkosítása) között|Igen|Igen|Igen||  
|Ügyféltelepítés|Igen||||  
|Internetes támogatás|Igen||||  
|Felderítés|Igen|||Igen|  
|Hardverleltár|Igen|Igen|Igen|Igen|  
|Szoftverleltár|Igen|||Igen|  
|Beállítások|Igen|Igen|Igen|Igen|  
|Szoftver központi telepítése|Igen|Igen|Igen||  
|Figyelés tartalék állapotkezelő ponttal|Igen||||  
|Csatlakozás felügyeleti pontokhoz|Igen||Igen||  
|Csatlakozás terjesztési pontokhoz|Igen||Igen||  
|A Configuration Manager blokk|Igen|Igen|Igen||  
|Karantén és kitiltás az Exchange Server (és a Configuration Manager)||||Igen|  
|Távoli törlés| |Igen|Igen|Igen|  

