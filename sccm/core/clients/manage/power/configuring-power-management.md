---
title: "Az energiagazdálkodás konfigurálása |} Microsoft Docs"
description: "Az energiagazdálkodás a System Center Configuration Manager beállítása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: e111ac2545dd9e0b96a50c10246bb75d286a737a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-power-management-in-system-center-configuration-manager"></a>Az energiagazdálkodás konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az energiagazdálkodás használhatja a System Center Configuration Managerben, akkor végezze az alábbi konfigurációs lépéseket.  

## <a name="enable-and-configure-power-management-client-settings"></a>Energiagazdálkodási ügyfélbeállítások engedélyezése és konfigurálása  
 Ezzel az eljárással konfigurálhatja az energiagazdálkodás alapértelmezett ügyfélbeállításait, amelyek a hierarchia minden számítógépére érvényesek lesznek. Ha csak néhány számítógépen szeretné alkalmazni ezeket a beállításokat, hozzon létre egyéni ügyfélbeállítást az eszközökhöz, és rendelje hozzá egy olyan gyűjteményhez, amely tartalmazza azokat a számítógépeket, amelyeken energiagazdálkodást szeretne használni. Egyéni Eszközbeállítás létrehozásáról további információk: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-settings.md).  

#### <a name="to-enable-power-management-and-configure-client-settings"></a>Az energiagazdálkodás engedélyezése és ügyfélbeállítások konfigurálása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Kattintson az **Adminisztráció** munkaterületen az **Ügyfél beállításai**elemre.  

3.  Kattintson az **Alapértelmezett ügyfélbeállítások**elemre.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

5.  Az **Alapértelmezett ügyfélbeállítások** párbeszédpanelen kattintson az **Energiagazdálkodás**elemre.  

6.  Adja meg az energiagazdálkodás ügyfélbeállításainak alábbi értékét:  

    -   **Az eszközök energiagazdálkodásának engedélyezése** – A legördülő listában az **Igaz** elemet választva engedélyezheti az energiagazdálkodást.  

7.  Adja meg a szükséges ügyfélbeállításokat. Energiagazdálkodási ügyfélbeállítások konfigurálható listájáért lásd: a [energiagazdálkodás](../../../../core/clients/deploy/about-client-settings.md#power-management) szakasz a [információ a System Center Configuration Manager ügyfélbeállításainak](../../../../core/clients/deploy/about-client-settings.md) témakör.  

8.  Kattintson az **OK** gombra az **Alapértelmezett ügyfélbeállítások** párbeszédpanel bezárásához.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egyetlen ügyfél házirendlekérésének kezdeményezéséről a [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../../core/clients/manage/manage-clients.md) című témakör nyújt tájékoztatást.  

## <a name="exclude-computers-from-power-management"></a>Számítógépek kizárása az energiagazdálkodásból  
 Az energiagazdálkodási beállítások fogadásából kizárhat számítógép-gyűjteményeket. Ha egy számítógép az energiagazdálkodási beállítások fogadásából kizárt bármely gyűjtemény tagja, akkor sem alkalmaz energiagazdálkodási beállításokat, ha tagja egy másik gyűjteménynek, amelyre energiagazdálkodási beállítások érvényesek.  

 Számítógépeket az alábbi okok bármelyike miatt kizárhat az energiagazdálkodásból:  

-   A számítógépeknek vállalati követelmények miatt folyamatosan bekapcsolt állapotban kell lenniük.  

-   Létrehozott egy kontroll számítógép-gyűjteményt, amelyen nem kíván energiagazdálkodási beállításokat alkalmazni.  

-   A számítógépek némelyike nem képes energiagazdálkodási beállításokat alkalmazni.  

-   A Windows Server rendszerű számítógépeket ki szeretné zárni az energiagazdálkodásból.  

> [!NOTE]  
>  Ha az ügyfélbeállításokban konfigurálta **A felhasználók kizárhassák az eszközeiket az energiagazdálkodásból** beállítást, a felhasználók a Szoftverközpont használatával kizárhatják a saját számítógépeiket az energiagazdálkodásból.  

 A **Kizárt számítógépek**jelentés futtatásával megtudhatja, hogy mely számítógépeket zárt ki az energiagazdálkodásból. Ez a jelentés kapcsolatos további információk: [kizárt számítógépek](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Excluded) a [figyelés és tervezés a System Center Configuration Managerben az energiagazdálkodás hogyan](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  A Windows XP vagy a Windows Server 2003 rendszerű számítógépeken alkalmazott energiaellátási beállításokat nem állítja vissza a rendszer az eredeti értékekre, még ha ki is zárja a számítógépet az energiagazdálkodásból. Ha a Windows újabb verzióiban kizár egy számítógépet az energiagazdálkodásból, az összes energiaellátási beállítás visszaáll az eredeti értékére. Az egyes energiaellátási beállítások nem állíthatók vissza az eredeti értékükre.  

#### <a name="to-exclude-a-collection-of-computers-from-power-management"></a>Számítógép-gyűjtemény kizárása az energiagazdálkodásból  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Kattintson az **Eszközök és megfelelőség** munkaterületen az **Eszközgyűjtemények**elemre.  

3.  Az **Eszközgyűjtemények** listában jelölje ki azt a gyűjteményt, amelyet ki szeretne zárni az energiagazdálkodásból, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Az a **energiagazdálkodás** lapján a *< gyűjteménynév\>***tulajdonságok** párbeszédpanelen jelölje ki **soha ne alkalmazzon energiagazdálkodási beállításokat a gyűjtemény számítógépeire**.  

5.  Kattintson a **OK** bezárásához a *< gyűjteménynév\>***tulajdonságok** párbeszédpanel bezárásához és a beállítások mentéséhez.  

