---
title: "Eszközmegfelelőségi szabályzatok |} Microsoft Docs"
description: "Útmutató a System Center Configuration Managerben való feltételes hozzáférés megfelelő tehetik az eszközöket megfelelőségi házirendjeinek kezelése szabályzatok."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: 18
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcaa2a9b5474e06bf344dc4fd47dbb160ea36297
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>Eszközmegfelelőségi szabályzatok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

**Megfelelőségi szabályzatok** a System Center Configuration Managerben meghatározzák azon szabályokat és beállításokat, hogy egy eszköz kell felelnie, hogy előírásainak feltételes hozzáférési házirendek legyen. A megfelelőségi házirendekkel a feltételes hozzáféréstől függetlenül is megfigyelheti és javíthatja a megfelelőséggel kapcsolatos hibákat.  


> [!IMPORTANT]  
>  Ez a cikk a Microsoft Intune által felügyelt eszközök megfelelőségi szabályzatait ismerteti.    A System Center Configuration Manager által felügyelt számítógépek megfelelőségi szabályzatainak ismertetése [Az Office 365-szolgáltatásokhoz való hozzáférés kezelése a System Center Configuration Manager által felügyelt számítógépek esetében](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md) című témakörben található.  

 Ezek a szabályok közé tartozik például a követelmények:  

-   PIN-kód és jelszavak eszköz

-   Az eszközön tárolt adatok titkosítása

-   Az, hogy az eszközt feltörték-e  

-   Hogy az eszközön a levelezés kezelése egy Intune-szabályzatot, vagy az eszköz nem megfelelő állapotát jelentette által a Windows Eszközállapot-igazolási szolgáltatás.
-   Az eszköz nem telepíthetők alkalmazások.


 Felhasználógyűjtemények számára megfelelőségi házirendeket telepít. Amikor felhasználók számára telepít megfelelőségi házirendet, a rendszer az összes felhasználói eszköz megfelelőségét ellenőrzi.  

 A következő táblázatban a megfelelőségi házirendek által támogatott eszköztípusok és a nem megfelelő beállítások kezelésének módja szerepel, amikor a házirendet feltételes hozzáférési házirenddel használják.  

|Szabály|Windows 8.1 és újabb|Windows Phone 8.1 és újabb verziók|iOS 6.0 és újabb verziók|Android 4.0-s és újabb verziók Samsung KNOX szabvány 4.0-s és újabb, Android for Work|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**PIN-kód vagy jelszó konfigurálása**|Kijavítva|Kijavítva|Kijavítva|Karanténba helyezve|  
|**Eszköztitkosítás**|–|Kijavítva|Kijavítva (PIN-kód beállításával)|Karanténba helyezve<br>(Android for Work mindig titkosítja)|  
|**Jailbreakelt vagy rootolt eszköz**|–|–|Karanténba helyezve (nem beállítás)|Karanténba helyezve (nem beállítás)|  
|**E-mail profil**|–|–|Karanténba helyezve|–|  
|**Operációs rendszer minimális verziója**|Karanténba helyezve|Karanténba helyezve|Karanténba helyezve|Karanténba helyezve|  
|**Operációs rendszer maximális verziója**|Karanténba helyezve|Karanténba helyezve|Karanténba helyezve|Karanténba helyezve|  
|**Az Eszközállapot-igazolás (1602-es frissítés)**|A beállítás nem vonatkozik a Windows 8.1-re<br /><br /> Windows 10 és Windows 10 Mobile karanténba helyezve.|–|–|–|  
|**Nem telepíthető alkalmazások**|–|–|Karanténba helyezve|Karanténba helyezve|

 **Kijavítva** = Az eszköz operációs rendszere kikényszeríti a megfelelőséget (a felhasználót például PIN-kód beállítására kényszeríti).  A beállítás mindig megfelelő.  

 **Karanténba helyezve** = Az eszköz operációs rendszere nem kényszeríti ki a megfelelőséget (az Android-eszközök például nem kényszerítik a felhasználót az eszköz titkosítására).  Ebben az esetben:  

-   Az eszköz le lesz tiltva, ha a felhasználót feltételes hozzáférési házirend célozza meg.  

-   A vállalati portál vagy webes portál értesíti a felhasználót a megfelelőséggel kapcsolatos problémákról.  


### <a name="next-steps"></a>További lépések  
[Egy eszköz megfelelőségi szabályzat létrehozása és telepítése](create-compliance-policy.md)
### <a name="see-also"></a>További információ  
 [A System Center Configuration Manager-szolgáltatásokhoz való hozzáférés kezelése](../../protect/deploy-use/manage-access-to-services.md)

