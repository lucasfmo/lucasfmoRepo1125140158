---
title: "Virtualizálás támogatása |} Microsoft Docs"
description: "A virtualizálási környezetben a System Center Configuration Manager-ügyfél és a hely helyrendszerszerepkörök telepítéséhez szükséges beolvasása."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10192da2633555ab3bae60dbb1156d1926f9a4a0
ms.openlocfilehash: b49bd179da850cee35b2487a353bb1788df03d58
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>Virtualizálási környezetek támogatása a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager támogatja az ügyfél telepítése és helyrendszerszerepkörök a támogatott operációs rendszerek, a cikkben szereplő virtualizálási környezetekben a virtuális gépeket futtató. A támogatás abban az esetben is érvényes, ha a virtuális gép állomása (virtualizálási környezet) ügyfélként vagy helykiszolgálóként nem támogatott.  

 Például ha Microsoft Hyper-V Server 2012-egy virtuális gép, amelyen Windows Server 2012 segítségével, telepítheti az ügyfél vagy a helyrendszer-szerepköröket a virtuális gép (Windows Server 2012), de nem az állomáson (Microsoft Hyper-V Server 2012).  

|Virtualizálási környezet|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|
|Windows Server 2016 <sup>(lásd: *vegye figyelembe a 1*)</sup>|
|Microsoft Hyper-V Server 2016 <sup>(lásd: *vegye figyelembe a 1*)|
-  *Megjegyzés: 1*: A Configuration Manager nem támogatja a [beágyazott virtualizálási](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/what-s-new-in-hyper-v-on-windows#a-namebkmknestedanested-virtualization-new), amelyek Újdonságok a Windows Server 2016.


 Minden egyes virtuális számítógépet használ kell felelnie legalább a azonos hardver- és szoftverkövetelmények szeretné használni a Configuration Manager fizikai számítógép számára.  

 Ellenőrizheti, hogy virtualizálási környezetét a Configuration Manager támogatja a Server Virtualization Validation Program és az online virtualizálási támogatási házirend varázslóját. A Kiszolgálóvirtualizálás-ellenőrző programmal kapcsolatos további információkért lásd: [Windows Server Virtualization Validation Program](https://www.windowsservercatalog.com/svvp.aspx).  

> [!NOTE]  
>  A Configuration Manager nem támogatja a Virtual PC és Virtual Server vendég operációs rendszerek a Mac számítógépeken futó.  

A Configuration Manager nem tudja kezelni a virtuális gépek, kivéve, ha azok online. Egy kapcsolat nélküli virtuálisgép-lemezkép nem lehet frissíteni, sem a készlet gyűjthetők a Configuration Manager-ügyfél használatával az állomáson.  

A virtuális gépekre semmilyen különleges megfontolás nem vonatkozik. Például a Configuration Manager előfordulhat, hogy nem határozza meg hogy frissítés van-e újra a virtuális gép képére alkalmazni, ha a virtuális gép leállítása és újraindítása a virtuális gép, amelyre a rendszer frissítés állapotának mentése nélkül.  

##  <a name="bkmk_Azure"></a> Microsoft Azure-alapú virtuális gépek  
 A Configuration Manager futtathatja az Azure virtuális gépeken, ugyanúgy, mint a helyszíni futása fizikai vállalati hálózaton belül. A Configuration Manager használatával az Azure virtuális gépek a következő esetekben:  

-   **1. forgatókönyv:** Futtassa a Configuration Manager egy Azure virtuális gépen, és az egyéb Azure virtuális gépeken telepített ügyfelek kezelésére használhatja.  

-   **2. forgatókönyv:** Futtassa a Configuration Manager egy Azure virtuális gépen, és nem az Azure-on futó ügyfelek kezelésére használhatja.  

-   **3. forgatókönyv:** Azure virtuális gépeken futó másik Configuration Manager helyrendszer-szerepkörök futtathatja közben (rendelkező kommunikációhoz megfelelő hálózati kapcsolattal) fizikai vállalati hálózatban más szerepköröket futtat.  

A hálózatok, a támogatott konfigurációk és hardverkövetelmények való telepítésére a Configuration Manager a helyi fizikai vállalati hálózaton azonos System Center Configuration Manager-követelményei telepítése Azure virtuális gépeken is vonatkozik.  

További információkért lásd: [Azure – gyakran ismételt kérdések a Configuration Manager](/sccm/core/understand/configuration-manager-on-azure).

> [!IMPORTANT]  
>  Configuration Manager-helyek és az Azure virtuális gépeken működő ügyfelek ugyanazok a licenckövetelmények vonatkoznak, mint a helyszíni telepítésekre vonatkoznak.  

