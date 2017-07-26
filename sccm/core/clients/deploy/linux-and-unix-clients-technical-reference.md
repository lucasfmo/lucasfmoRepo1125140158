---
title: "UNIX/Linux rendszerű ügyfél Komponensszolgáltatások és parancsok |} Microsoft Docs"
description: "Komponensszolgáltatások és a Linux és UNIX rendszerű ügyfeleken a System Center Configuration Managerben parancsok megismerése."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 89668f3e2e0a3e2e0178e5b2c91b2508f583649f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="linux-and-unix-clients-component-services-and-commands-for-system-center-configuration-manager"></a>Linux és UNIX rendszerű ügyfelek Komponensszolgáltatások és parancsok a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A következő táblázat ismerteti az ügyfélszolgáltatások összetevőt a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült.  

|Fájlnév|További információ|  
|---------------|----------------------|  
|ccmexec.bin|Ez a szolgáltatás megegyezik a Windows-alapú ügyfelek ccmexc szolgáltatásával. A Configuration Manager helyrendszer-szerepkörök folytatott kommunikáció minden esetben felelős, és a helyi számítógép hardverleltárának összegyűjtéséhez az omiserver.bin szolgáltatással is kommunikál.<br /><br /> A támogatott parancssori argumentumok listájának megjelenítéséhez futtassa a **ccmexec -h**parancsot.|  
|omiserver.bin|Ez a szolgáltatás a CIM-kiszolgáló. A CIM-kiszolgáló keretet biztosít a szolgáltatónak nevezett beépülő szoftvermodulokhoz. A szolgáltatók a Linux és UNIX-alapú számítógép-erőforrásokkal együttműködve összegyűjtik a hardverleltár adatait. A Linux-számítógépek **folyamatszolgáltatója** például a Linux operációs rendszer folyamataihoz tartozó adatokat gyűjti.|  

 A következő táblázatok felsorolják azokat a parancsokat, amelyekkel elindíthatók, leállíthatók és újraindíthatók az ügyfélszolgáltatások (ccmexec.bin és omiserver.bin) a Linux és a UNIX egyes verzióiban. Amikor elindítja vagy leállítja a ccmexec szolgáltatást, az omiserver szolgáltatás szintén elindul vagy leáll.  

|Operációs rendszer|Parancsok|  
|----------------------|--------------|  
|Univerzális ügynök<br /><br /> RHEL 4 és SLES 9|Indítás: **/etc/init d/ccmexecd start**<br /><br /> Leállítás: **/etc/init d/ccmexecd stop**<br /><br /> Újraindítás: **/etc/init d/ccmexecd restart**|  
|Solaris 9|Indítás: **/etc/init d/ccmexecd start**<br /><br /> Leállítás: **/etc/init d/ccmexecd stop**<br /><br /> Újraindítás: **/etc/init d/ccmexecd restart**|  
|Solaris 10|Indítás:<br /><br /> **svcadm engedélyezése -s svc: / alkalmazás/felügyeleti/omiserver**<br /><br /> **svcadm engedélyezése -s svc: / alkalmazás/felügyeleti/ccmexecd**<br /><br /> Leállítás:<br /><br /> **svcadm -s svc letiltása: / alkalmazás/felügyeleti/ccmexecd**<br /><br /> **svcadm -s svc letiltása: / alkalmazás/felügyeleti/omiserver**|  
|Solaris 11|Indítás:<br /><br /> **svcadm engedélyezése -s svc: / alkalmazás/felügyeleti/omiserver**<br /><br /> **svcadm engedélyezése -s svc: / alkalmazás/felügyeleti/ccmexecd**<br /><br /> Leállítás:<br /><br /> **svcadm -s svc letiltása: / alkalmazás/felügyeleti/ccmexecd**<br /><br /> **svcadm -s svc letiltása: / alkalmazás/felügyeleti/omiserver**|  
|AIX|Indítás:<br /><br /> **startsrc -s omiserver**<br /><br /> **startsrc -s ccmexec**<br /><br /> Leállítás:<br /><br /> **stopsrc -s ccmexec**<br /><br /> **stopsrc -s omiserver**|  
|HP-UX|Indítás: **/sbin/init.d/ccmexecd start**<br /><br /> Leállítás: **/sbin/init.d/ccmexecd stop**<br /><br /> Újraindítás: **/sbin/init.d/ccmexecd restart**|  

