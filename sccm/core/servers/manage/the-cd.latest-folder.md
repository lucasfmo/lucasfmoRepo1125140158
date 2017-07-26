---
title: "A CD-n. Legújabb mappa |} Microsoft Docs"
description: "Ismerje meg az új frissítési folyamatot, amely továbbítja a terméket a Configuration Manager konzolon belüli frissítéseket."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 5c39e09b44500fa2f356f83579bb2fb2c1d0e937
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="the-cdlatest-folder-for-system-center-configuration-manager"></a>A System Center Configuration Manager CD.Latest mappája

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager bevezet egy új frissítési folyamatot, amely továbbítja a terméket a Configuration Manager konzolon belüli frissítéseket. Az új Configuration Manager frissítési módszerének támogatásához egy új mappa jön létre elnevezett **CD-ről. Legújabb** , amely a hely frissített verziója a Configuration Manager telepítési fájljainak másolatát tartalmazza.  

Az 1606. számú frissítés óta a CD.Latest mappa tartalmaz egy **Redist** nevű mappát, amely tartalmazza a telepítés során letöltött és használt újraterjeszthető fájlokat. Ezeket a fájlokat a rendszer egyezteti a CD.Latest mappában található Configuration Manager-fájlok verziójával. Amikor egy CD.Latest mappából futtatja a telepítőt, a telepítő adott verziójával egyeztetett fájlokat kell használnia. Ehhez utasíthatja a telepítőt, hogy töltse le az új és naprakész fájlokat a Microsofttól, vagy úgy, hogy használja a CD.Latest mappában található Redist mappa fájljait.

Azonban alapszintű verziót tartalmazó adathordozóról, például az alapkonfiguráció 1606, amely 2016. októberi kiadás dátuma, nem tartalmaz egy Redist mappában. A Redist mappa nem hozható létre, amíg nem telepíti a konzolon belüli frissítés. Addig is használja az alapszintű verziót tartalmazó adathordozó-helyek telepítésekor használt Redist mappát.  

> [!TIP]
> Ha még nem telepítette az 1606-os verziót, ügyelnie kell arra, hogy a használt redist-fájlok naprakészek legyenek. Ha az utóbbi időben nem töltött le redist-fájlokat, engedélyezze a telepítőnek, hogy letöltse ezeket a Microsofttól.   

 A következő forgatókönyvek alapján lehet létrehozni vagy frissíteni a CD.Latest mappát egy központi adminisztrációs helyen vagy egy elsődleges helykiszolgálón:  

-   Frissítés vagy gyorsjavítás regisztrációját a Configuration Manager konzol telepítése: A mappa létrehozásakor vagy frissítésekor a Configuration Manager telepítési mappájában.  

-   A Configuration Manager beépített biztonsági mentési feladat futtatása: A mappa létrehozásakor vagy frissítésekor a a kijelölt biztonsági másolat helye.  

-  Verzió 1606, a CD-tól kezdődően. Legújabb mappa jön létre, ha telepít egy új helyet alapszintű verziót tartalmazó adathordozó (például 1606 vagy 1702 verzió) használatával.

A CD.Latest mappában található forrásfájlok a következő műveletekhez támogatottak:  

1.  **Biztonsági másolat és helyreállítás:** Helyreállít egy helyet, a CD-ről forrásfájlokat kell használnia. Legfrissebb mappát, amely megfelel a helyen. Ha futtatja a hely biztonsági mentése a hely beépített biztonsági mentési feladat, a CD-t használ. Legújabb mappa a biztonsági másolat része.

    -   **A hely helyreállításának részeként végzett hely-újratelepítést** a biztonsági másolatba foglalt CD.Latest mappából végezheti el. Ezáltal a rendszer a hely biztonsági másolatának és helyadatbázisának megfelelő fájlverziókat használva telepíti a helyet.  Ha nincs hozzáférése a megfelelő CD-t. Legfrissebb mappát szerezhet be CD-ről. A megfelelő fájlverziókat telepíti a helyet egy laborkörnyezetben, és ezután a verziójával, hogy a hely frissítése a legújabb mappa végre kívánja hajtani.

        > [!IMPORTANT]  
        >  Ha nem rendelkezik a megfelelő CD.Latest mappával, és nem áll rendelkezésre annak tartalma, akkor nem lehet helyreállítani a helyet, hanem újra kell telepíteni.  

    -   Ha nem rendelkezik CD.Latest mappával, de van egy működő elsődleges gyermekhelye vagy központi adminisztrációs helye, akkor ezt a helyet használhatja referenciahelyként a hely helyreállításához.  

2.  **A gyermek elsődleges helyek telepítéséhez:** Ha szeretné, hogy telepítve van egy vagy több konzolon belüli frissítések egy központi adminisztrációs hely alá új gyermek elsődleges hely telepítése, a telepítő és a CD-ről forrásfájlokat kell használnia. A központi adminisztrációs hely legfrissebb mappát. Ha a telepítő a központi adminisztrációs hely CD.Latest mappájának másolatából fut, akkor a központi adminisztrációs hely verziójának megfelelő telepítési forrásfájlokat használja. További információk: [A telepítővarázsló használata helyek telepítéséhez](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  

3.  **Önálló elsődleges hely kibővítéséhez:** Amikor egy új központi adminisztrációs hely telepítésével bővíti az önálló elsődleges helyet, a telepítő és a CD-ről forrásfájlokat kell használnia. Az új központi adminisztrációs hely telepítéséhez az elsődleges helyről legfrissebb mappát. Ha a telepítő az elsődleges hely CD.Latest mappájának másolatából fut, akkor az elsődleges hely verziójának megfelelő telepítési forrásfájlokat használja. További információk: [Önálló elsődleges hely bővítése](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) [A telepítővarázsló használata helyek telepítéséhez](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) témakörben

> [!IMPORTANT]  
>  A CD.Latest mappa frissített forrásfájljai nem támogatottak a következő esetekben:  
>   
>  -   Új hely telepítése egy új hierarchiához  
>  -   A Microsoft System Center 2012 Configuration Manager hely frissítése a System Center Configuration Managerben

