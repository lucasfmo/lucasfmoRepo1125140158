---
title: "A kockázat alapján hozzáférés korlátozása |} Microsoft Docs"
description: "Eszköz-, hálózati és kockázat alapján a vállalati erőforrásokhoz való hozzáférés korlátozása."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 250671660c1c6da0ca9b593b06b8f344dfe17ad6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Eszköz, hálózati és alkalmazás kockázat alapján vállalati erőforrásokhoz való hozzáférés kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mobile fenyegetés védelmi összekötők használhatják fel a kiválasztott mobileszköz fenyegetés védelmi forgalmazójával, a megfelelőségi szabályzatok és a feltételes hozzáférési szabályai információforrásként teszik lehetővé. Ez lehetővé teszi a rendszergazdák számára a védelmi réteg hozzáadása a vállalati erőforrások, például az Exchange és Sharepoint, kifejezetten a sérült mobileszközök.

## <a name="what-problem-does-this-solve"></a>Milyen problémát ez megoldani?

A vállalatok kell megvédeni a bizalmas adatokat a megjelenő fenyegetéseket, beleértve a fizikai, alkalmazás-alapú és a hálózati alapú fenyegetéseket, valamint az operációs rendszer biztonsági réseket.
Hagyományosan vállalatok voltak előjelzéses rendszerű számítógépek védelme a támadásokra, amíg a mobileszközök lépjen a nem figyelt és nem védett. A mobileszköz-platformok rendelkezik beépített védelmet például elkülönítése és vetted fogyasztó alkalmazás-áruházak, de ezekhez a platformokhoz sebezhetővé maradnak. Ma több alkalmazott eszközök használata munkára, és hozzá kell férniük a bizalmas adatokat. Eszközök kell egyre kifinomult támadások elleni védelemre.

A [hibrid MDM-telepítésben (SCCM az Intune-nal)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) lehetőséget nyújt a vállalati erőforrásokhoz és adatokhoz eszköz threat protection megoldások, például Mobile fenyegetés védelmi partnerek biztosító kockázatbecslés alapján történő hozzáférés szabályozása.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Az Intune Mobile fenyegetés védelmi összekötők működése?

Az összekötő hozzon létre egy Intune-ban és a kiválasztott mobileszköz fenyegetés védelmi szállító közötti kommunikációs csatorna védelmet nyújt a vállalati erőforrásokhoz. Intune Mobile fenyegetés védelmi partnerek egyszerűen elsajátítható, egyszerűen telepíthető alkalmazások aktívan beolvasása és elemzése a kártevőveszély-információ az Intune-nal, a jelentéskészítési és kényszerítési célokra megosztásához mobileszközökre vonatkozó ajánlatot. Például ha egy csatlakoztatott Mobile fenyegetés védelmi alkalmazást jelent a Mobile fenyegetés védelmi szállító, hogy a hálózaton a telefon jelenleg csatlakoztatva van a hálózaton található, amely érinti a Man ki a középső támadások, ezek az adatok megosztott és egy megfelelő szintre (alacsony/közepes vagy magas) – amely lehet össze kell vetni a beállított kockázati szint támogatás határozza meg, ha az Ön által választott egyes erőforrásokhoz való hozzáférés vissza kell vonni az Intune kategorizált közben a biztonság szempontjából sérül.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Ha egy eszköz akkor tekinthető Mobile fenyegetés védelmi-megoldás által fertőzött:

![Mobile fenyegetés védelmi fertőzött eszköz](../media/mtp/MTD-image-1.png)

Hozzáférése akkor biztosított, ha az eszköz javítja:

![Mobile fenyegetés védelmi hozzáféréssel rendelkezik](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>További lépések

Útmutató a vállalati erőforrásokba eszköz, hálózati és a kockázatok alkalmazás alapján történő hozzáférés:

- [A lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
