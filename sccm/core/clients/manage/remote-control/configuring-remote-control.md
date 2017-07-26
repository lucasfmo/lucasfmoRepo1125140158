---
title: "A Távvezérlés konfigurálása |} Microsoft Docs"
description: "Állítsa be a System Center Configuration Manager Távvezérlés."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3a386c23c81f413d7d161780bdc0ab3a5b9eccae
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>A Távvezérlés konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Ez az eljárás ismerteti a távvezérlés alapértelmezett ügyfélbeállítások konfigurálása. Ezek a beállítások a hierarchiában lévő összes számítógépre vonatkoznak. Ha azt szeretné, hogy ezeket a beállításokat csak néhány számítógépen szeretné alkalmazni, rendelje hozzá egy egyéni ügyfélbeállítást az eszközökhöz azokat a számítógépeket tartalmazó gyűjteményhez. További információt lásd: a [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-settings.md). 

Távsegítség vagy távoli asztal használatához, telepíteni és konfigurálni kell a Configuration Manager konzolt futtató számítógépen. A Távsegítség vagy a Távoli asztal telepítéséről és konfigurálásáról a Windows dokumentációjában olvashat bővebben.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>Távvezérlés engedélyezése és ügyfélbeállítások konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett** párbeszédpanelen válassza ki **Táveszközök**.  

6.  A távvezérlés, Távsegítség és távoli asztali ügyfél beállításainak konfigurálása. Konfigurálható ügyfélbeállításait távoli eszközök listájáért lásd: [Táveszközök](../../../../core/clients/deploy/about-client-settings.md#remote-tools).  

    A **ConfigMgr távvezérlés** párbeszédpanelen megjelenő vállalatnevet **A Szoftverközpontban megjelenített név** értékének megadásával módosíthatja a **Számítógépügynök** ügyfélbeállításaiban.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egyetlen ügyfél házirendlekérésének kezdeményezéséről a [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../../core/clients/manage/manage-clients.md) című témakör nyújt tájékoztatást.  

#### <a name="enable-keyboard-translation"></a>Billentyűzet fordítási engedélyezése

Alapértelmezés szerint a Configuration Manager kulcs pozíciója a megjelenítő helyről a megosztó helyre továbbítja. Ez billentyűzet konfigurációkat, amelyek különböznek az megosztó viewer problémát jelenthet. Például az angol billentyűzet használatával egy megjelenítőt írja be az "A", de a megosztó francia billentyűzet gondoskodik a "Q". Most már rendelkezik a távvezérlés beállíthatja, hogy a karakter, maga a megjelenítő billentyűzetről átkerülnek a megosztó, és a megjelenítő százalékát írja be a megosztó érkezik.

Billentyűzet fordítási bekapcsolása a **Configuration Manager Távvezérlés**, válassza a **művelet**, és válassza **billentyűzet fordítási engedélyezése** kulcs pozíciójának átviteléhez.

> [!NOTE]
>
> Különleges kulcsok, például a ~! #@ $%, nem lesz megfelelően fordítva.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>A távvezérlés megjelenítőjében használható billentyűparancsok

|Billentyűparancs|Leírás|  
|-----------------------|-----------------|  
|Alt+Page Up|Váltás a futó programok között, balról jobbra.|  
|Alt+Page Down|Váltás a futó programok között, jobbról balra.|  
|Alt+Insert|Váltás a futó programok között abban a sorrendben, ahogy meg lettek nyitva.|  
|Alt+Home|A **Start** menü megnyitása.|  
|Ctrl+Alt+End|A Windows rendszerbiztonság párbeszédpanel megnyitása (Ctrl+Alt+Del).|  
|Alt+Delete|A Windows menü megnyitása.|  
|Ctrl+Alt+mínuszjel (a számbillentyűzeten)|A helyi számítógép aktív ablakának másolása a távoli gép vágólapjára.|  
|Ctrl+Alt+pluszjel (a számbillentyűzeten)|A helyi számítógép teljes ablakterületének másolása a távoli számítógép vágólapjára.|  

