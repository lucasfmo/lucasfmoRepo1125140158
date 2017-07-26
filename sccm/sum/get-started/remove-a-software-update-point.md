---

title: "Távolítsa el a szoftverfrissítési pont |} Microsoft Docs"
description: "Az alábbi eljárás segítségével távolítsa el a szoftverfrissítési pont hely rendszer szerepkört a helyen a Configuration Manager konzolról."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 2486375c-d4a2-4cf2-9124-9bee02bbf173
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 22de02c51be3a0cd66b1be0f04b2fbdeb897858c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
#  <a name="BKMK_RemoveSUP"></a> A szoftverfrissítési pont helyrendszerszerepkörének eltávolítása  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Eltávolíthatja a szoftverfrissítési pont hely rendszer szerepkört a helyen a Configuration Manager konzoljáról. Frissítse az ügyfélházirendet, ha el szeretné távolítani a szoftverfrissítési pontot a listáról. Miután az utolsó szoftverfrissítési pontot is eltávolította a helyen, a szoftverfrissítési pontok listája kiürül, és a szoftverfrissítések gyakorlatilag le lesznek tiltva a helyen. Új szoftverfrissítési pontot kell beállítani a helyen szinkronizációs forrásként, ha egynél több szoftverfrissítési pont található egy elsődleges helyen, és eltávolította a szinkronizációs forrásként beállított szoftverfrissítési pontot.  

> [!NOTE]  
>  Miután eltávolította a szoftverfrissítési pont helyszerepkörét egy helyrendszerből, várjon legalább 15 percet, mielőtt újratelepíti a szoftverfrissítési pont helyszerepkörét.  

 A szoftverfrissítési pontok eltávolításához kövesse az alábbi eljárást.  

#### <a name="to-remove-the-software-update-point"></a>Szoftverfrissítési pont eltávolítása  

1.  A **Configuration Manager** -konzolon kattintson az **Adminisztráció**elemre.  

2.  Az Adminisztráció munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**lehetőségre.  

3.  Jelölje ki az eltávolítani kívánt szoftverfrissítési pontot tartalmazó helyrendszer-kiszolgálót, majd a **Helyrendszerszerepkörök**területen válassza a **Szoftverfrissítési pont**lehetőséget.  

4.  A **Helyszerepkör** lap **Helyszerepkör** csoportjában kattintson a **Szerepkör eltávolítása**elemre. Erősítse meg, hogy szeretné távolítani a szoftverfrissítési pontot, vagy a többi szoftverfrissítési pont számára a helyen új szinkronizációs forrást választ.  

