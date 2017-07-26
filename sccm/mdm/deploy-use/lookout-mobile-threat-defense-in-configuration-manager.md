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
ms.openlocfilehash: 21841d97387f07f53993d957641f9ad892d723c2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Eszköz, hálózati és alkalmazás kockázat alapján vállalati erőforrásokhoz való hozzáférés kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A mobileszközökről a vállalati erőforrások eléréséhez, a Lookout, egy eszköz fenyegetés adatvédelmi megoldást, amely integrálva van a Microsoft Intune által végzett kockázatbecslés alapján szabályozhatja. A kockázat telemetriai adatokból, hogy a Lookout szolgáltatás gyűjti össze az eszközök operációs rendszer biztonsági rések, a telepített rosszindulatú alkalmazásokat és a rosszindulatú hálózati profilok alapul. 

A Lookout által jelentett kockázatbecslés engedélyezve van a System center configuration manager (SCCM) megfelelőségi házirendek alapján, feltételes hozzáférési házirendek konfigurálása és engedélyezése vagy letiltása az eszközöket, amelyek ezeken az eszközökön észlelt fenyegetéseket miatt bizonyul megbizonyosodott.

A [hibrid MDM-telepítésben (SCCM az Intune-nal)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) által biztosított a vállalati erőforrásokhoz és adatokhoz való hozzáférést lehessen alapján kockázatbecslés eszköz fenyegetés információvédelmi megoldásokat, mint ahogy a Lookout nyújt.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>Hogyan a hibrid MDM-telepítésben, és a Lookout veszélyforrások elleni eszközvédelem segítik a vállalati erőforrások védelmét?
Mobilalkalmazás lookout meg (munka keressen), a mobileszközökön futó, rögzíti a fájlrendszer, a hálózati vermet, eszköz- és telemetria (ha elérhető), és elküldi a Lookout eszköz threat protection felhőalapú szolgáltatás egy összesített eszköz kockázat mobil fenyegetések kiszámításához. A kockázati szintjét a Lookout konzol saját követelményeinek megfelelően veszélyek felmérésére osztályozása is módosíthatja.  

A megfelelőségi házirend, az SCCM most már tartalmaz egy új szabályt, a Lookout mobil veszélyforrások elleni védelem, amely a Lookout eszköz fenyegetés kockázatbecslés alapul. Ha ez a szabály engedélyezve van, az eszköz megfelelőségi kiértékelése.

Ha az eszköz nem megfelelő, és a megfelelőségi szabályok határozzák meg, például az Exchange Online és SharePoint Online erőforrások hozzáférése feltételes hozzáférési szabályzatokkal. Hozzáférés le van tiltva, a végfelhasználók számára rendelkezésre álló olyan forgatókönyv, hogy a probléma megoldásához és a vállalati erőforrásokhoz való hozzáférést. Ez a forgatókönyv segítségével keressen olyan munkahelyi alkalmazás nincs elindítva.

## <a name="supported-platforms"></a>A támogatott platformok:
* **Android 4.1-es és újabb verziók**, és a Microsoft Intune-ban regisztrált.
* **iOS 8 és újabb verziók**, és a Microsoft Intune-ban regisztrált.
Platformok és nyelvek, amely támogatja a Lookout kapcsolatos információkért tekintse meg a [cikk](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Előfeltételek:
* [A hibrid MDM-telepítésben](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Előfizetés a Microsoft Intune és az Azure Active Directoryban.
* A Lookout Mobile végpont biztonsági nagyvállalati előfizetéssel.  További információkért lásd: [Lookout Mobile végpontok közötti védelem](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="example-scenarios"></a>Példaforgatókönyvek
Az alábbiakban néhány gyakori helyzetek:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>A rosszindulatú alkalmazásokból fenyegetés alapján elérés:
Az eszköz rosszindulatú alkalmazásokat, például a kártevő észlelésekor blokkolhatja az ilyen eszközöket:
* Kapcsolódik a vállalati e-mail a fenyegetés feloldása előtt.
* Vállalati fájlokat a onedrive vállalati verzió használatával munkahelyi alkalmazások szinkronizálása.
* Üzleti szempontból kritikus fontosságú alkalmazásokhoz fér hozzá.

**A hozzáférés le van tiltva, rosszindulatú alkalmazásokat észlelésekor:**

![ábra feltételes hozzáférési házirend hozzáférés blokkolása: Ha eszköz határozzák meg a nem kompatibilis az eszköz rosszindulatú alkalmazásokat miatt](media/config-mgr-maliciousapps_blocked.png)

**Eszköz feloldva, és képes hozzáférni a vállalati erőforrásokhoz, amikor a fenyegetés javítja:**

![hozzáférés biztosítása, amikor az eszköz határozza meg a szervizelés után meg kell felelnie a feltételes hozzáférési házirend bemutató ábra](media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>A hálózati fenyegetést alapján elérés:
Észleli a veszélyeket-átjárójának például a hálózathoz, és korlátozza a hozzáférést az eszköz kockázat alapján Wi-Fi hálózatok.

**A Wi-Fi hálózathoz hozzáférése:**

![ábra: a feltételes hozzáférés hálózati fenyegetések alapján blokkoló Wi-Fi-hozzáférés](media/config-mgr-network-wifi-blocked.png)

**A szervizelés biztosított hozzáférést:**

![feltételes hozzáférés lehetővé teszi a hozzáférést a fenyegetés szervizelésének a bemutató ábra](media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>SharePoint Online hálózati fenyegetést alapján való hozzáférést:

Észleli a veszélyeket-átjárójának például a hálózathoz, és a szinkronizálás a vállalati fájlok, az eszköz kockázat alapján.

**A hozzáférése a SharePoint Online hálózati veszéllyel fenyegetett az eszközön alapján:**

![Ábra: a feltételes hozzáférés SharePoint online-hoz fenyegetések észlelése alapján eszközök hozzáférésének blokkolása](media/config-mgr-network-spo-blocked.png)


**A szervizelés biztosított hozzáférést:**

![Hozzáférés engedélyezése után a hálózati fenyegetés javítja feltételes hozzáférés bemutató ábra](media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>További lépések
Hajtsa végre a megoldás megvalósításának fő lépései a következők:
1.    [A Lookout mobil veszélyforrások elleni védelem előfizetés beállítása](set-up-your-subscription-with-lookout.md)
2.    [Az Intune-ban a Lookout MTP-kapcsolat engedélyezése](enable-lookout-connection-in-intune.md)
3.  [Konfigurálhatja és telepítheti a Lookout munkahelyi alkalmazás](configure-and-deploy-lookout-for-work-apps.md)
4.    [Megfelelőségi szabályzat konfigurálása](enable-device-threat-protection-rule-compliance-policy.md)
5.    [A Lookout integrációs hibaelhárítása](troubleshoot-lookout-integration.md)

