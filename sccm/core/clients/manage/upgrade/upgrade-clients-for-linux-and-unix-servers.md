---
itle: 'Upgrade clients | Microsoft Docs | Linux UNIX '
description: "A Linux vagy UNIX rendszerű kiszolgálón a System Center Configuration Manager ügyfél frissítéséhez."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 394ba7c236c05cc90a3d7f99eb6146b15d620f11
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>A Linux és UNIX rendszerű kiszolgálókhoz készült ügyfelek frissítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Linux és UNIX rendszerű számítógépeken az aktuális ügyfélszoftver eltávolítása nélkül is frissítheti az ügyfél verzióját. Ehhez új ügyfél-telepítési csomagot kell a számítógépre telepíteni a **-keepdb** parancssori tulajdonság használatával. Linux vagy UNIX rendszerű ügyfél telepítésekor a meglévő ügyféladatokat felülírják az új ügyfél fájljai. Azonban a **- keepdb** parancssori tulajdonság arra utasítja a telepítési folyamatot, hogy az ügyfelek egyedi azonosítóját (GUID), helyi adatbázis adatait megőrzi, és a tanúsítványtárolót. A rendszer ezt az információt használja majd az új ügyfél telepítésekor.  

 Például, van egy RHEL5 x64 számítógépe, amelyen a Configuration Manager Linux és UNIX rendszerű ügyfélszoftver eredeti kiadása fut. Ez az ügyfél frissítéséhez az ügyfél verzióját az 1. összegző frissítéssel, manuális futtatása a **telepítése** a megfelelő ügyfél telepítéséhez az 1. összegző frissítéssel, azonban kiegészül a parancsfájl a **- keepdb** parancssori kapcsolóval. A használt parancssor a következőhöz hasonló: **. / - felügyeleti csomag telepítése < hostname\> - sitecode < kód\> ccm-Universal-x64 - keepdb. < build\>.tar**  

## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>A Linux és UNIX rendszerű kiszolgálók ügyfélszoftverének frissítése szoftver központi telepítése útján  
 Központi szoftvertelepítéssel is frissítheti a Linux és UNIX rendszerű kiszolgálók ügyfélszoftverét. A System Center Configuration Manager-ügyfél azonban közvetlenül nem futtatható a telepítési parancsfájlt az új ügyfél telepítéséhez, mert egy új ügyfél telepítését, először el kell távolítania a jelenlegit. Ez akkor végén a Configuration Manager ügyfél-folyamat, amely a telepítési parancsfájlt futtatja, az új ügyfél a telepítés megkezdése előtt. Sikeres használatához a szoftver központi telepítése az új ügyfél telepítéséhez, úgy kell ütemeznie a telepítés által az operációs rendszer beépített ütemezési szolgáltatása futtassa és egy későbbi időpontban el.  

 Ez megvalósítható központi szoftvertelepítéssel: először másolja az új ügyfél-telepítési csomaghoz szükséges fájlokat az ügyfélszámítógépre, majd központi telepítéssel futtasson parancsfájlt az ügyfél-telepítési folyamat ütemezéséhez. A parancsfájl használja az operációs rendszer beépített **:** parancs késlelteti az indítást. Ezt követően a parancsfájl futtatása, ha a művelet az ügyfél operációs rendszerét, és nem a Configuration Manager-ügyfél a számítógép kezeli. Ez lehetővé teszi, hogy először távolítsa el a Configuration Manager-ügyfél és az a Linux vagy UNIX rendszerű számítógépen ügyfélfrissítési folyamat befejezéseként új ügyfelet, majd telepítse a parancsfájl által meghívott parancssor. A frissítés befejezése után a frissített ügyfelet a Configuration Manager által felügyelt marad.  

 Az alábbi eljárás segítségével konfigurálhatja a központi szoftvertelepítést a Linux és UNIX rendszerű számítógépek ügyfelekének frissítésére: A következő lépések és példák bemutatják, hogyan frissíthető egy, az ügyfél eredeti kiadását futtató RHEL5 x 64 számítógép az 1. összegző frissítéssel.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>A Linux és UNIX rendszerű kiszolgálók ügyfélszoftverének frissítése szoftver központi telepítése útján  

1.  Az új ügyféltelepítési csomag fájljait másolja a frissíteni kívánt Configuration Manager-ügyfelet futtató számítógép.  

     Tegyük fel, hogy az ügyféltelepítési csomagot és az 1. összegző frissítés telepítési parancsfájlját az ügyfélszámítógép következő helyére másolhatja: **/tmp/PATCH**  

2.  Hozzon létre egy parancsfájlt a Configuration Manager-ügyfél frissítését felügyeli, és helyezze a parancsfájl egy példányát abban a mappában, az ügyfélszámítógépen, 1. lépésben az Ügyféltelepítő fájlokat.  

     A parancsfájl nem szükséges egy adott névvel, de elegendő, az ügyfél-telepítési fájlok használatához az ügyfélszámítógépen egy helyi mappából, és az ügyfél-telepítési csomag telepítése segítségével parancssorokat tartalmaznia kell a **- keepdb** parancssori tulajdonság. Használja a **- keepdb** parancssori tulajdonság segítségével karbantartása az új ügyfél telepítésekor használja az aktuális ügyfél egyedi azonosítója.  

     Tegyük fel, hogy létrehoz egy **upgrade.sh** nevű, a következő sorokat tartalmazó parancsfájlt, majd azt az ügyfélszámítógép **/tmp/PATCH** mappájába másolja:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

3.  A szoftver központi telepítése lehetővé teszi, hogy az egyes ügyfelek a számítógépek beépített **at** parancsát használva, rövid késleltetés után futtassák az **upgrade.sh** parancsfájlt.  

     Például a következő parancs segítségével futtassa a parancsfájlt: **a -f /tmp/upgrade.sh -m most + 5 perc**  

 Miután az ügyfél sikeresen ütemezi a **upgrade.sh** parancsfájl futtatását, állapotüzenetet küld arról, hogy a szoftver központi telepítése sikeresen befejeződött. Azonban a tényleges ügyféltelepítést a késleltetést követően végzi és felügyeli a számítógép. Az ügyfél frissítése után a telepítést az ügyfélszámítógépen található **/var/opt/microsoft/scxcm.log** fájl megtekintésével ellenőrizheti. Ezenkívül ellenőrizheti, hogy az ügyfél telepítve és kommunikál a hellyel részleteinek megtekintése az ügyfél által a **eszközök** csomópontjának a **eszközök és megfelelőség** munkaterület a Configuration Manager konzolon.  

