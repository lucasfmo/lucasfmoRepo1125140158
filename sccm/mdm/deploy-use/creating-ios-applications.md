---
title: "IOS-alkalmazások fejlesztéséhez |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozása és központi telepítésekor az iOS-eszközökhöz készült alkalmazások."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 349fcf335e7faddbcbd2ffe0ece7e711465f28df
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>IOS-alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager alkalmazás rendelkezik egy vagy több központi telepítési típust, amely a telepítési fájlokat és információkat tartalmazzák, amelyek szükségesek a szoftverek eszközre telepítéséhez. A központi telepítési típus szabályokat, amelyek adja meg, mikor és hogyan a szoftver központi telepítése is rendelkezik.  

 A következő módszerekkel hozhatók létre alkalmazások:  

-   Az alkalmazás és központi telepítési típusok automatikus létrehozása a alkalmazástelepítő fájlok olvasásával.  

-   Az alkalmazás manuális létrehozása központi telepítési típusok későbbi hozzáadásával.  

-   Alkalmazás importálása fájlból.  

Lásd: [alkalmazás létrehozása varázsló elindítása](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) a Configuration Manager-alkalmazások létrehozása és központi telepítési típusok szükséges lépéseket. Emellett vegye az alábbiakat is figyelembe létrehozása és központi telepítésekor az iOS-eszközökhöz készült alkalmazások.  

## <a name="general-considerations"></a>Általános megfontolások  
 A Configuration Manager a következő alkalmazástípusok telepítését támogatja:  

|Eszköz típusa|Támogatott fájlok|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> A System Center Configuration Managerben, akkor nem kell megadnia a tulajdonságlista (.plist) fájljában iOS-alkalmazások importálásakor.|  

 A következő központi telepítési műveletek támogatottak:  

|Eszköz típusa|Támogatott műveletek|  
|-----------------|-----------------------|  
|iOS|**Rendelkezésre álló**, **szükséges**. A felhasználónak bele kell egyeznie a telepítése vagy eltávolítása.

> [!IMPORTANT]  
>  Jelenleg a végfelhasználók számára nem tud telepíteni vállalati alkalmazásokat az iOS rendszerhez készült Microsoft Intune vállalati portál alkalmazásából. Ennek az az oka, hogy az iOS App Store-ban közzétett alkalmazások elhelyezett korlátozások vonatkoznak (lásd az App Store felülvizsgálati irányelveinek 2. szakaszát). A felhasználók úgy telepíthetnek vállalati alkalmazásokat (akár felügyelt App Store-beli alkalmazásokat és üzleti alkalmazáscsomagokat is), ha megnyitják az Intune webes portált az eszközükön (portal.manage.microsoft.com). Az Intune vállalati portál alkalmazás által engedélyezett a mobileszköz-kezelési képességekre vonatkozó további információkért lásd: [Eszközkezelési lehetőségeit a Microsoft Intune-ban regisztrált](https://technet.microsoft.com/library/dn600287.aspx).  

