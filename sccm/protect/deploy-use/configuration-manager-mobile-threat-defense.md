---
title: "Mobil fenyegetés védelmi |} System Center Configuration Managerben"
description: "Használja a Configuration Manager és az Intune Mobile fenyegetés védelmi partnerek eszköz, hálózati és alkalmazáskiszolgálókból kockázat alapján a vállalati erőforrásokhoz való hozzáférés korlátozása"
ms.custom: na
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 266897b7ac674a369931e8ed63ff464edc10c9d8
ms.openlocfilehash: 298d879638a2d20d421b19752cb5f20f6725df14
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Intune Mobile fenyegetés védelemmel az összekötők a Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A [hibrid MDM-telepítésben (SCCM az Intune-nal)](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) és az Intune-ban és a mobil fenyegetés védelmi partnerek közötti integrációt biztosítanak a vállalati erőforrásokhoz és adatokhoz eszköz kockázatbecslés alapján történő hozzáférés-vezérlésének lehetősége.

Intune Mobile fenyegetés védelmi összekötők használhatják fel a kiválasztott mobileszköz fenyegetés védelmi forgalmazójával, a megfelelőségi szabályzatok és a feltételes hozzáférési szabályai információforrásként teszik lehetővé. Ez lehetővé teszi a rendszergazdák számára a védelmi réteg hozzáadása a vállalati erőforrások, például az Exchange és Sharepoint, kifejezetten a sérült mobileszközök.

## <a name="what-problem-does-this-solve"></a>Milyen problémát ez megoldani?

A vállalatok kell megvédeni a bizalmas adatokat a megjelenő fenyegetéseket, beleértve a fizikai, alkalmazás-alapú és a hálózati alapú fenyegetéseket, valamint az operációs rendszer biztonsági réseket.
Hagyományosan vállalatok voltak proaktív rendszerű számítógépek védelme a támadásokra, amíg a mobileszközök lépjen a nem figyelt és nem védett. A mobileszköz-platformok rendelkezik beépített védelmet például elkülönítése és vetted fogyasztó alkalmazás-áruházak, de ezekhez a platformokhoz sebezhetővé maradnak. Ma több alkalmazott eszközök használata munkára, és hozzá kell férniük a bizalmas adatokat. Eszközök kell egyre kifinomult támadások elleni védelemre.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Az Intune Mobile fenyegetés védelmi összekötők működése?

Az összekötő hozzon létre egy Intune-ban és a kiválasztott mobileszköz fenyegetés védelmi szállító közötti kommunikációs csatorna védelmet nyújt a vállalati erőforrásokhoz. Intune Mobile fenyegetés védelmi partnerek egyszerűen elsajátítható, egyszerűen telepíthető alkalmazások aktívan beolvasása és elemzése a kártevőveszély-információ az Intune-nal, a jelentéskészítési és kényszerítési célokra megosztásához mobileszközökre vonatkozó ajánlatot. Például ha egy csatlakoztatott Mobile fenyegetés védelmi alkalmazást jelent a Mobile fenyegetés védelmi szállító, hogy a hálózaton a telefon jelenleg csatlakoztatva van a hálózaton található, amely érinti a Man ki a középső támadások, ezek az adatok megosztott és egy megfelelő szintre (alacsony/közepes vagy magas) – amely lehet össze kell vetni a beállított kockázati szint támogatás határozza meg, ha az Ön által választott egyes erőforrásokhoz való hozzáférés vissza kell vonni az Intune kategorizált közben a biztonság szempontjából sérül.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Ha egy eszköz akkor tekinthető Mobile fenyegetés védelmi-megoldás által fertőzött:

![](http://i.imgur.com/Li1WUOU.png)

Hozzáférése akkor biztosított, ha az eszköz javítja:

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Mobile fenyegetés védelmi partnerek

Útmutató a vállalati erőforrásokba eszköz, hálózati és a kockázatok alkalmazás alapján történő hozzáférés:

- [A lookout](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
