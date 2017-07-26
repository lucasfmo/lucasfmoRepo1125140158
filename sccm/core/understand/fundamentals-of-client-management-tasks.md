---
title: "Ügyfél-felügyeleti – alapok |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager-ügyfelek kezeléséhez futtatott feladatok."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86b90b8e591e1ae4f58cb361a5e544db6b09cce1
ms.openlocfilehash: 0fee4f4ba462e59859ac93c4218b67cb26bdd6f6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>A System Center Configuration Manager ügyfélfelügyeleti feladataival kapcsolatos alapvető tudnivalók

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután telepítette a System Center Configuration Manager ügyfelek, nincsenek az ügyfelek felügyeletéhez futtató több feladatot.  A feladatok futnak, a Configuration Manager konzoljáról. Egyéb feladatok a Configuration Manager ügyfélalkalmazás futnak. A Configuration Manager ügyfélalkalmazás a Configuration Manager ügyfélszoftver együtt települ.

## <a name="configuration-manager-console-tasks"></a>A Configuration Manager konzol feladatai
 A Configuration Manager konzol különböző ügyfélkezelési feladatokat végezheti el:  

-   Alkalmazások, szoftverfrissítések, karbantartási parancsfájlok és operációs rendszerek központi telepítése. Telepítésének konfigurálása egy adott dátumot és időpontot a, a szoftverfrissítések elérhetővé a felhasználók telepíthetnek, amikor erre felkérést kapnak, vagy konfigurálhatja az alkalmazásokat kell eltávolítani.  

-   Segíthet megvédeni a számítógépeket a kártevőktől és biztonsági kockázatoktól, és értesítést kérhet a problémák észlelésekor.  

-   Figyelése és szervizelése, ha nem megfelelőek kívánt ügyfél-konfigurációs beállítások megadása.  

-   Gyűjthet hardver- és szoftverleltári adatokat, beleértve a Microsoft licencinformációinak figyelését és egyeztetését is.  

-   Táveléréssel hibaelhárítást végezhet a számítógépeken.  

-   Kialakíthat energiatakarékossági beállításokat is, hogy kezelje és figyelje a számítógépek energiafelhasználását.  

A Configuration Manager konzol figyeli a korábbi műveletek közel valós időben. Minden tevékenység értesítési és állapot adatait a Configuration Manager konzolon érhető el. Adatok és az előzmények trendjének rögzítéséhez, használja az SQL Server Reporting Services integrált jelentéskészítési képességeit. Az ügyfelek adatokat küldenek a hely számára az ügyfélállapotról.  Ügyfélállapot-adatokat az ügyfél működőképességéről és aktivitásáról állapotával kapcsolatos adatokat biztosít, és a konzolon vagy a beépített jelentések segítségével a Configuration Manager használatával tekinthetők. Ezen adatok segítenek kiválasztani azokat a számítógépeket, amelyek nem válaszolnak, és néhány esetben a problémák automatikusan javítja.  

 További információ az ügyfélkezelési feladatokról: [Ügyfelek kezelése a System Center Configuration Managerben](../../core/clients/manage/manage-clients.md) és [A Linux és UNIX rendszerű kiszolgálókhoz készült ügyfelek kezelése a System Center Configuration Managerben](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md). A jelentések használatának ismertetését lásd:   
            [A System Center Configuration Manager jelentéskészítésének bemutatása](../../core/servers/manage/introduction-to-reporting.md).  

## <a name="configuration-manager-client-application"></a>A Configuration Manager ügyfélalkalmazás  
 Ha a Configuration Manager-ügyfélszoftvert telepíti, a Configuration Manager ügyfélalkalmazás túl telepítve van. A Szoftverközponttól eltérően a Configuration Manager ügyfélalkalmazás az ügyfélszolgálat, nem pedig a végfelhasználó számára készült. Néhány konfigurálási beállításhoz helyi rendszergazdai engedélyek szükségesek, és a legtöbbhöz a Configuration Manager ügyfélalkalmazás működésének szakszerű ismerete szükséges. Ez az alkalmazás használható az ügyfélre vonatkozó következő feladatok elvégzéséhez:  

-   Tulajdonságok az ügyfélről, mint a buildszám, a hozzárendelt helyről, a felügyeleti pont akkor nézet kommunikál, és hogy az ügyfél használ-e a nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítványt vagy önaláírt tanúsítványt.  

-   Győződjön meg arról, hogy az ügyfél sikeresen letöltötte az ügyfél-házirendet az ügyfél első telepítése után. Emellett győződjön meg arról, hogy az ügyfélbeállítások engedélyezésekor vagy letiltásakor a vártnak megfelelően az ügyfélbeállítások a Configuration Manager-konzolon konfigurált.  

-   Indítsa el a műveletet. Például töltse le az ügyfélházirendet, ha megváltozott a legutóbbi konfigurációs a Configuration Manager konzolon, és nem szeretné megvárni, amíg a következő ütemezett időpontban.  

-   Manuálisan rendelje hozzá az ügyfelet a Configuration Manager-hely, vagy próbálja meg megtalálni egy helyet. Adja meg a felügyeleti pontok közzététele a DNS Szolgáltatásban, a tartománynévrendszer (DNS) utótag.  

-   Állítsa be az ideiglenes fájlokat tároló ügyfél gyorsítótárában. Ha a szoftver telepítéséhez több lemezterületre van szüksége, törölje a gyorsítótárban lévő fájlokat.  

-   Konfigurálja az internet alapú ügyfél-felügyeleti beállításokat.  

-   Nézze meg az ügyfélhez központilag telepített referenciakonfigurációkat, kezdeményezze a megfelelőségi kiértékelést, és tekintse meg a megfelelőségi jelentéseket.  

