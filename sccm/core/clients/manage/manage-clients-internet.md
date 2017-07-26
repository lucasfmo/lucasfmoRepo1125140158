---
title: "Az Internet - Configuration Manager-ügyfelek kezeléséhez |} Microsoft Docs"
description: "Ismerje meg a felhő adatkezelési átjáró és az Internet alapú ügyfél kezelése a Configuration Manager-ügyfelek felügyeletére."
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 1b6752be448e1062c97a3225db4fa8af9f4832a6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Az interneten a Configuration Manager ügyfelek kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Általában a Configuration Managerben a számítógépek és a felügyelt kiszolgálók többsége fizikailag a hálózaton belső személyes vagy vállalati kezelési funkció végrehajtására helyrendszer-kiszolgálóként. Azonban kezelheti ügyfélszámítógépek a vállalati hálózaton kívül, ha kapcsolódik az internethez anélkül, hogy az ügyfelek csatlakozhatnak virtuális magánhálózatok a hely eléréséhez a rendszer kiszolgálók használatával.

A Configuration Manager az internetre csatlakozó ügyfelek kezelésére két lehetőséget biztosít:

-   Felügyeleti átjáró

-   Internetalapú ügyfélkezelés

## <a name="cloud-management-gateway"></a>Felügyeleti átjáró

1610 verziójától kezdve a Configuration Manager felhő adatkezelési átjáró vezet be. A metódus egy felhőalapú szolgáltatás, a Microsoft Azure és az új helyrendszerszerepkör, amely az adott szolgáltatással kommunikál telepített kombinációjával Internet alapú ügyfelek kezelése lehetőséget biztosít. Az ügyfelek ezután a szolgáltatás segítségével kommunikál a Configuration Managerrel.

Előnyök:

-   Nincs szükség további infrastruktúrát.

-   Az internetre a helyszíni infrastruktúrára nem fed fel.

-   Felhő virtuális gépek, amelyek a szolgáltatás futtatásához az Azure teljes körűen felügyelt, és nincs karbantartás szükséges.

-   Könnyen és konfigurálva a Configuration Manager konzolon.

Hátrányok:

-   A felhőalapú előfizetés költség.

-   Felügyeleti adatokat küldött keresztül történik.

További információkért lásd: [felhő adatkezelési átjáró tervezése](plan-cloud-management-gateway.md).

## <a name="internet-based-client-management"></a>Internetalapú ügyfélkezelés

Ez a módszer az internetes helyrendszer-kiszolgálók, amelyhez az ügyfelek felügyelet céljából kommunikálnak támaszkodik. Ennél a módszernél ügyfelek és helyrendszer-kiszolgálók konfigurálását az Internet alapú felügyeleti.

Előnyök:

-   Nincs cloud service függőség.

-   További költség nélkül társított cloud-előfizetésekhez.

-   Teljes hozzáférés a kiszolgálók és a szolgáltatást biztosító szerepkörök.

Hátrányok:

-   További infrastruktúra beruházást igényelnek.

-   Munkaterhet és a további infrastruktúra működési költségek.

-   Az Internet infrastruktúra kell észlelnie.

További információkért lásd: [az internetalapú ügyfélfelügyelet tervezése](plan-internet-based-client-management.md).

