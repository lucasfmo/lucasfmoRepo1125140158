---
title: "Hozzon létre egy MDM-gyűjteményt, a System Center Configuration Manager |} Microsoft Docs"
description: "Hozzon létre egy MDM-gyűjteményt, a System Center Configuration Managerrel."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: fabbcfd2d5656d4fa8cb87feffe87e17998df145
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>Az MDM-gyűjtemény létrehozása a System Center Configuration Manager és a Microsoft Intune

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Adja meg a felhasználók regisztrálhatják az eszközeiket a felügyeletbe szükséges a Configuration Manager felhasználói gyűjteményt. Csak használhatja a felhasználói gyűjtemények (helyett eszközgyűjtemények), mert a felhasználó által hozzárendelt Intune-licencek.

> [!NOTE]
> Regisztrálhatják az eszközeiket az Intune-nal, nem szükséges licencek kiosztása a felhasználók számára az Office 365 portál vagy az Azure Active Directory portálon. Beleértve a felhasználók egy gyűjteményt, amely lekérdezi az Intune-előfizetéshez társított (az egy [később lépés](configure-intune-subscription.md)), amely szükséges az összes.

Tesztelési célokra állíthat be egy **közvetlen szabály** , és adja hozzá az adott felhasználók, akik beléptethetik az eszközöket. Athe Configuration Manager konzolon kattintson, **eszközök és megfelelőség** > **Felhasználógyűjtemények**, kattintson a **Home** lapon > **létrehozása** csoportból, és kattintson a **Felhasználógyűjtemény létrehozása**. Szélesebb körű terjesztési érdemes használni a **szabályok lekérdezése** felhasználók meghatározásához. További információ a gyűjtemények: [gyűjtemények](https://technet.microsoft.com/library/mt629371.aspx).

![Mobileszköz-kezelési felhasználói gyűjtemény létrehozása](../media/mdm-create-user-collection.png)

> [!div class="button"]
[Következő lépés >](confirm-dns.md)

