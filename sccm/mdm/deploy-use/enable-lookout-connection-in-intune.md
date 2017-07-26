---
title: "Engedélyezze a Lookout MTP-hez, az Intune-ban |} Microsoft Docs"
description: "Engedélyezze a Lookout mobil veszélyforrások elleni védelem az Intune felügyeleti konzolon."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: f9ddbcc981fa1274a41ae16a6a939c0cdf739c3e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Az Intune felügyeleti konzoljában a Lookout MTP-kapcsolat engedélyezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör bemutatja, hogyan engedélyezze a Lookout MTP-kapcsolatot az Intune-ban. Kell már konfigurálta az Intune-összekötő a Lookout konzolon ez a lépés elvégzése előtt.  Ha még nem tette meg, tegye a témakörben ismertetett [Lookout mobil veszélyforrások elleni védelem előfizetés beállítása](set-up-your-subscription-with-lookout.md).

Az Intune-ban, a Lookout MTP-kapcsolat engedélyezése a **felügyeleti** lapját a [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com), válassza a **külső szolgáltatás integrálása**. Válasszon **Lookout állapot** , és engedélyezze **MTP-szinkronizálás** a váltógomb használatával.

![a kijelölt engedélyezése váltógomb rendelkező a Lookout szinkronizálási oldalát bemutató képernyőkép](media/lookout-intune-synchronization.png)

Ezzel befejeződik a telepítés a Lookout és az Intune integrálható az Intune felügyeleti konzolján.  A következő néhány lépést a megoldás megvalósításának tartalmaz, amely központi telepítése a [munkahelyi alkalmazásokat keressen](configure-and-deploy-lookout-for-work-apps.md) és beállítása a [megfelelőségi](enable-device-threat-protection-rule-compliance-policy.md) házirend.

>[!IMPORTANT]
> Ön **kell** keressen olyan munkahelyi alkalmazás létrehozása a megfelelőségi szabályzat előírásainak, és a feltételes hozzáférés konfigurálása előtt konfigurálja. Ez biztosítja, hogy az alkalmazás készen áll, és elérhető legyen a végfelhasználók számára, hogy e-mailek és más vállalati erőforrásokhoz való hozzáférés karanténüzenet telepítése.

## <a name="next-steps"></a>További lépések
[A Lookout munkahelyi alkalmazás konfigurálása](configure-and-deploy-lookout-for-work-apps.md)

