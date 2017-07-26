---
title: "Virtuális asztali infrastruktúra (VDI) ügyfél-felügyeleti |} Microsoft Docs "
description: "System Center Configuration Manager ügyfelek virtuális asztali infrastruktúrában (VDI) kezelésére."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d73daf6427b8c58d21d579f3b41df513cc3e3b0b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>Szempontok a System Center Configuration Manager ügyfelek a virtuális asztali infrastruktúra (VDI) kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a Configuration Manager-ügyfél telepítése az alábbi virtuális asztali infrastruktúra (VDI) használó esetekben támogatja:  

-   **Személyes virtuális gépek** -személyes virtuális gépek általában szükségesek, ha azt szeretné, győződjön meg arról, hogy a felhasználói adatok és beállítások megmaradjanak a virtuális gépen a munkamenetek között.  

-   **Távoli asztali szolgáltatások munkamenetei** -távoli asztali szolgáltatások használatával egy kiszolgáló több egyidejű ügyfélmunkamenetet is. Felhasználók kapcsolódhatnak egy munkamenethez, és alkalmazásokat futtathatnak a kiszolgálón.  

-   **Készletbe vont virtuális gépek** -készletbe vont virtuális gépek nem maradnak meg munkamenetek között. Ha a munkamenet lezárult, minden adatot és beállítást nem őrződnek meg. Készletbe vont virtuális gépek hasznosak, ha a távoli asztali szolgáltatások nem használható, mert egy szükséges vállalati alkalmazás nem futtatható a Windows Server, amely futtatja az ügyfél-munkamenetek.  

 A következő táblázat kezelése a Configuration Manager-ügyfél virtuális asztali infrastruktúrában szempontjai.  

|Virtuális gép típusa|Megfontolások|  
|--------------------------|--------------------|  
|Személyes virtuális gépek|A Configuration Manager a személyes virtuális gépeket egy fizikai számítógéppel megegyezően. A Configuration Manager-ügyfél előtelepíthető a virtuális gép lemezképére, vagy telepíthető központilag a virtuális gép kiépítése után.|  
|Távoli asztali szolgáltatások|A Configuration Manager-ügyfél nincs telepítve az egyes távoli asztali munkamenetekhez. Ehelyett az ügyfél csak telepítve van egy alkalommal a távoli asztali szolgáltatások kiszolgálóján. Az összes Configuration Manager-szolgáltatásokat is használható a távoli asztali szolgáltatások kiszolgálóján.|  
|Készletbe vont virtuális gépek|Amikor készletbe vont virtuális gép le van szerelve, a Configuration Manager használatával végzett módosítások elvesznek.<br /><br /> Például Hardverleltár, szoftverleltár és szoftverhasználat-mérés előfordulhat, hogy nem felelnek meg az igényeinek mert a virtuális gép esetleg csak rövid ideig működik a Configuration Manager szolgáltatások által visszaadott adatokat. Fontolja meg a készletbe vont virtuális gépek kivéve a készletfeladatokból.|  

 Mivel virtualizálással több Configuration Manager-ügyfél ugyanazon a fizikai számítógépen fut, sok ügyfélművelet beépített véletlenszerű késleltetést használ az ütemezett műveletekhez, például a hardver és szoftver-nyilvántartási, kártevőirtó megvizsgálja, Szoftvertelepítés és szoftverfrissítési vizsgálat frissítése. Ez a késés segíti a Processzor kapacitásának elosztását és adatok adatátvitelt olyan számítógépen, amelyen több virtuális gép, amely a Configuration Manager-ügyfél számára.  

> [!NOTE]  
>  Windows Embedded-ügyfelek, amelyek karbantartási üzemmódban, kivételével a virtualizált környezetet nem futtató Configuration Manager-ügyfelek szintén ezt véletlenszerű késleltetést használják. Ha sok központilag telepített ügyfele van, ez a viselkedés segít elkerülni a hálózati sávszélesség csúcsait, és csökkenti a processzorigényt a Configuration Manager helyrendszerei, például a felügyeleti ponton és a helykiszolgálón. A késleltetés időtartama a Configuration Manager egyik funkciója függően változik.  
>   
>  A véletlenszerű késleltetés alapértelmezésben le van tiltva a kötelező szoftverfrissítések és az alkalmazástelepítések használatával a következő ügyfélbeállítással: **Számítógépügynök**: **Határidő véletlenszerűsítésének letiltása**.

