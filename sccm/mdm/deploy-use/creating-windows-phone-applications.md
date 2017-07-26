---
title: "Windows Phone-alkalmazások fejlesztéséhez |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozásakor és központi telepítése a Windows Phone-eszközökhöz készült alkalmazások."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 6cbf2389a72c0c384ef8e84a1755ac77b64bfc6d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-phone-applications-with-system-center-configuration-manager"></a>Windows Phone-alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager alkalmazás rendelkezik egy vagy több központi telepítési típust, amely a telepítési fájlokat és információkat tartalmazzák, amelyek szükségesek a szoftverek eszközre telepítéséhez. A központi telepítési típus szabályokat, amelyek adja meg, mikor és hogyan a szoftver központi telepítése is rendelkezik.  

 A következő módszerekkel hozhatók létre alkalmazások:  

-   Az alkalmazás és központi telepítési típusok automatikus létrehozása a alkalmazástelepítő fájlok olvasásával.  

-   Az alkalmazás manuális létrehozása központi telepítési típusok későbbi hozzáadásával.  

-   Alkalmazás importálása fájlból.  

Lásd: [alkalmazás létrehozása varázsló elindítása](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) a Configuration Manager-alkalmazások létrehozása és központi telepítési típusok szükséges lépéseket. Emellett vegye az alábbiakat is figyelembe létrehozása és központi telepítésekor a Windows Phone-eszközökhöz készült alkalmazások.  

## <a name="general-considerations"></a>Általános megfontolások  
 A következő alkalmazás típusú központi telepítése a Configuration Manager támogatja:  

|Eszköz típusa|Támogatott fájltípusok|  
|-----------------|---------------------|  
|Windows Phone 8|.xap|  
|Windows Phone 8.1|.xap, .appx, .appxbundle|
|Windows 10 mobil verzió|.xap, .appx, .appxbundle|

 A következő központi telepítési műveletek támogatottak:  

|Eszköz típusa|Támogatott műveletek|  
|-----------------|-----------------------|  
|Windows Phone 8, Windows Phone 8.1 és Windows 10 mobil verzió|Elérhető, Szükséges, Eltávolítás|  

## <a name="steps-to-deploy-the-latest-windows-phone-company-portal-app-with-supersedence"></a>A legújabb Windows Phone vállalati portál alkalmazás telepítése helyettesítéssel lépései  
 Az alábbi táblázat a Windows Phone 8-as vállalati portál alkalmazás létrehozásának és központi telepítésének lépéseit ismerteti.  

|Lépés|További információ|  
|----------|----------------------|  
|**1. lépés:** Töltse le a legfrissebb vállalati portál alkalmazást.|Töltse le a [Windows Phone 8-as vállalati portál alkalmazást](http://go.microsoft.com/fwlink/?LinkId=268440).|  
|**2. lépés:** Aláírhatja a vállalati portál alkalmazást a Symantec-tanúsítványával.|A vállalati portál alkalmazás aláírásáról további információkért lásd: [a System Center Configuration Manager és a Microsoft Intune Windows Phone és Windows 10 Mobile hibrid Eszközkezelés beállítása](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**3. lépés:** Hozzon létre egy új alkalmazást a vállalati portál alkalmazás legújabb verzióját, és adjon meg egy helyettesítési kapcsolatot.|További információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md) és [felülvizsgálata és az alkalmazások helyettesítéséről](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**4. lépés:** Vegye fel az alkalmazást a Microsoft Intune-előfizetés varázsló.|További információkért lásd: [a System Center Configuration Manager és a Microsoft Intune Windows Phone és Windows 10 Mobile hibrid Eszközkezelés beállítása](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**5. lépés:** Törölje a központi telepítés, amely automatikusan jön létre, amikor a vállalati portál alkalmazást felvette a Microsoft Intune-előfizetés varázsló.|A Microsoft Intune-előfizetést hozott létre automatikus központi telepítést az alkalmazáshoz, ugyanis a központi telepítés nem fogja támogatni a helyettesítést.|  
|**6. lépés:** Az alkalmazás egy új központi telepítés létrehozásához. Az a **központi telepítési beállítások** oldalán a **szoftver központi telepítése varázsló**, ellenőrizze **automatikus frissítését bármely helyét az alkalmazás verzióinak**.|A helyettesítési kapcsolattal létrehozott alkalmazással hozzon létre egy új központi telepítést helyettesítéssel.|  
|**7. lépés (nem kötelező):** Alapértelmezés szerint a helyettesítő alkalmazásokat az eszközön 7 nap után telepíti. Központi telepítéséhez a vállalati portál alkalmazás hamarabb a korábban regisztrált eszközökre, módosítsa a **központi telepítése újraértékelésének ütemezése** alacsonyabb értékűre.<br /><br /> Ezt az értéket az alapértelmezettnél alacsonyabb érték megadásával, hátrányosan befolyásolhatja a hálózat és az ügyfélszámítógépek számítógépek teljesítményétől.|Nem áll rendelkezésre további információ.|  

