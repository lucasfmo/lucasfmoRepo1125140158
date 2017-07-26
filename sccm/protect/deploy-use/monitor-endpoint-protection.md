---
title: "Az Endpoint Protection-állapot figyelése |} Microsoft Docs"
description: "Megtudhatja, hogyan Endpoint Protection figyelése a System Center Configuration Manager-hierarchiában."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b5771f4faebc06076bdbf84727848c881fc1dfb4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-endpoint-protection-status"></a>Az Endpoint Protection-állapot figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Figyelheti az Endpoint Protection a Microsoft System Center Configuration Manager hierarchia használatával a **Endpoint Protection állapota** csomópontjából **biztonsági** a a **figyelés** munkaterületen, a **Endpoint Protection** csomópontja a **eszközök és megfelelőség** munkaterületet, és jelentések segítségével.  

##  <a name="BKMK_1"></a>Az Endpoint Protection állapot csomópontjánál, a használatával az Endpoint Protection figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **biztonsági** majd **Endpoint Protection állapota**.  

3.  Az a **gyűjtemény** listára, válassza ki a gyűjteményt, amelynek szeretné megtekinteni az állapotadatait.  

    > [!IMPORTANT]  
    >  Gyűjtemények zónaaliasok a következő esetekben:  
    >   
    >  -   Ha bejelöli **az Endpoint Protection irányítópultjában tekintse meg a gyűjteményt** a a **riasztások** lapján a *< gyűjteménynév\>***tulajdonságok** párbeszédpanel megnyitásához.  
    > -   Ha az Endpoint Protection kártevőirtó-házirendet telepít a gyűjteményben.  
    > -   Ha engedélyezi, és telepítheti az Endpoint Protection-ügyfél beállításainak a gyűjteményben.  

4.  Tekintse át a megjelenő adatokat a **biztonsági állapotát** és **működési állapot** szakaszok. Az **Eszközök és megfelelőség** munkaterület **Eszközök** csomópontjának bármelyik állapothivatkozására kattintva létrehozhat ideiglenes gyűjteményt. Az ideiglenes gyűjtemény a kijelölt állapotú számítógépeket tartalmazza.  

    > [!IMPORTANT]  
    >  A megjelenített információk a **Endpoint Protection állapota** csomópont összesített a Configuration Manager-adatbázisba, és nem feltétlenül aktuálisak legutóbbi adatokon alapul. Ha szeretné lekérdezni a legfrissebb adatokat, kattintson a **Kezdőlap** lapon található **Összefoglalás futtatása**elemre, vagy kattintson az **Összefoglalás ütemezése** elemre az összefoglalás időközének módosításához.  

##  <a name="BKMK_2"></a>Az eszközök és megfelelőség munkaterületen az Endpoint Protection figyelése  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Az a **eszközök és megfelelőség** munkaterületen hajtsa végre az alábbi műveletek egyikét:  

    -   Kattintson a **eszközök**. Válasszon ki egy számítógépet az **Eszközök és megfelelőség** listából, majd kattintson a **Kártevő részletei** lapra.  

    -   Kattintson a **Eszközgyűjtemények**. Válasszon ki egy számítógépet az **Eszközgyűjtemények** listából, amely tartalmazza a figyelni kívánt számítógépet, majd kattintson a **Kezdőlap** csoport **Gyűjtemény** lapján lévő **Tagok megjelenítése**elemre.  

3.  Az a *< gyűjteménynév\>*  listában, válasszon ki egy számítógépet, és kattintson a **kártevő részletei** fülre.  

##  <a name="BKMK_3"></a>Az Endpoint Protection figyelése jelentések segítségével  
 Az alábbi jelentések segítségével tekintse meg az Endpoint Protection a hierarchiában. Ezek a jelentések segítségével esetleges Endpoint Protection problémáinak. Jelentéskészítés a Configuration Managerben konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md) és [naplófájlok a System Center Configuration Managerben](../../core/plan-design/hierarchy/log-files.md). Az Endpoint Protection jelentések az Endpoint Protection mappában találhatók.  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|**Kártevőirtó tevékenységgel kapcsolatos jelentés**|Megjeleníti a kártevőirtói tevékenység áttekintését a megadott gyűjteményben.|  
|**Fertőzött számítógépek**|Megjeleníti azon számítógépek listáját, amelyeken a rendszer a megadott fenyegetést észlelte.|  
|**Fenyegetettségeknek leginkább kitett felhasználók**|Megjeleníti a legtöbb észlelt fenyegetéssel rendelkező felhasználók listáját.|  
|**Felhasználói fenyegetések listája**|Megjeleníti a megadott felhasználói fiók esetén talált fenyegetések listáját.|  

## <a name="malware-alert-levels"></a>Kártevőriasztási szintek  
 Az alábbi táblázat segítségével azonosíthatja a különböző olyan Endpoint Protection riasztási szintek jelenhetnek meg a jelentésekben vagy a Configuration Manager konzolon.  

|Riasztási szint|Leírás|  
|-----------------|-----------------|  
|**Sikertelen**|Az Endpoint Protection nem tudta elhárítani a kártevőt. Tekintse meg a hiba részleteit a naplókat.<br /><br /> **Megjegyzés:** A Configuration Manager és Endpoint Protection naplófájlok listáját lásd az "Endpoint Protection" című szakaszában a [naplófájlok a System Center Configuration Managerben](../../core/plan-design/hierarchy/log-files.md) témakör.|  
|**Eltávolítva**|Az Endpoint Protection sikeresen eltávolította a kártevőt.|  
|**Karanténba helyezve**|Az Endpoint Protection áthelyezte a kártevőt egy biztonságos helyre, és megakadályozta a futását, amíg nem távolítható el, és engedélyezi azt.|  
|**Tisztítva**|A kártevő szoftver eltávolítása megtörtént a fertőzött fájlból.|  
|**Engedélyezett**|Egy rendszergazda engedélyezte a kártevőt tartalmazó szoftver futtatását.|  
|**Nincs művelet**|Az Endpoint Protection semmilyen műveletet a kártevő szoftvereket vett igénybe. Ez akkor fordulhat elő, ha a számítógép újraindult a kártevő szoftver észlelése után, és a kártevő már nem észlelhető. Ilyen eset például, ha egy korábban csatlakoztatott hálózati meghajtó, amelyen a rendszer kártevőt észlelt, nincs újracsatlakoztatva a számítógép újraindításakor.|  
|**Blokkolt**|Az Endpoint Protection letiltja a kártevő szoftver futtatását. Ez akkor fordulhat elő, ha a számítógépen futó folyamatban kártevő található.|

