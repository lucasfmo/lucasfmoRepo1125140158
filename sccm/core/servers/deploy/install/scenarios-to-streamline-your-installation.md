---
title: "Telepítési forgatókönyvek |} Microsoft Docs"
description: "Ismerje meg, hogy egy új Configuration Manager-hierarchia telepítése, frissítése vagy a hely frissítése technikákat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9dac6b3fa92c193e3c1a75dd804e0b72fb5394b9
ms.openlocfilehash: dbc303ea9df5a429cb2ef8bd89f372639a4ae2b2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>A System Center Configuration Manager telepítésének egyszerűsítésére használható forgatókönyvek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager aktuális ágának frissítési verziók megjelenésével nincsenek egyszerűsítésére frissített verziójára (például 1610 frissítéssel) egy új hierarchia telepítése, és a frissítésre a Microsoft System Center 2012 Configuration Manager új forgatókönyvek használhatók.

A támogatott helyzetek a következők:  

**Új System Center Configuration Manager aktuális ág hierarchia telepítése** , amelyen fut a frissített verzióra.  

-   Csak a legfelső szintű helyet telepíti, és telepítse azonnal érdekében, hogy a hely aktuális használni kívánt frissített verzióra való frissítést. Ezt követően közvetlenül a frissített verzióra további helyeket is telepíthet.  
-   Ebben a forgatókönyvben hagyja ki további helyek telepítése alapterv szintjét, illetve létrehoztak használni kívánt frissített verzióra folyamatán.  
-   Ebben a forgatókönyvben hagyja ki az ügyfelek telepítése egy alapkonfigurációt, és majd újratelepíteni őket egy újabb verzióra való frissítéskor a folyamatot.  

**A Microsoft System Center 2012 Configuration Manager frissítési** frissített verziójára a System Center Configuration Manager infrastruktúra.  

-   Kézi frissítés a központi adminisztrációs hely és egy alapszintű verzióra (például verzió 1606) előtt minden elsődleges hely telepítése frissített verziójára (például 1610. verzió).  
-   A Microsoft System Center 2012 Configuration Manager nem másodlagos helyek frissítésére, amíg nem fut a frissített verziót fogja használni, az elsődleges helyen.  
-   A Microsoft System Center 2012 Configuration Manager nem ügyfelek frissítése, amíg nem fut a frissített verziót fogja használni, az elsődleges helyen.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>Forgatókönyv: Új hierarchia telepítése frissített verzióra  
Ebben a példaforgatókönyvben telepíteni a hierarchia első helyének hasonlóan 1610 Alapverzió a System Center Configuration Manager használatával. Ezt követően a frissítés a 1610 további helyek vagy ügyfelek telepítése előtt.  

-   Tervezi (például 1610. verzió) frissítési verzióval használja, és nem marad meg az alapszintű verziónál (például verzió 1606), mert nem kell további helyek telepítése és majd frissíti őket. Ez vonatkozik az ügyfelek is.  
-   Nem telepíti a másodlagos helyeket 1606 verziójával, és majd 1610 verzióra frissíteni. Ehelyett telepíti a másodlagos helyeket, miután az elsődleges helyeken 1610 verzióját futtatják.  

Kövesse az ebben a sorozatban:  

1.  **Az új hierarchia legfelső szintű hely telepítése** az alapszintű verziót tartalmazó adathordozó használatával.  

    -   Segítségével alapszintű verziót tartalmazó adathordozó csak egy új hierarchia első helyének telepítése.  
    -   Például egy legfelső szintű helyet telepíthet 1606 alapszintű verziójára. További információkért lásd: [helyek telepítése a telepítővarázsló segítségével](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Ez a lépés után a a legfelső szintű hely verzióját 1606 futtatja.  

2.  **A konzolon belüli frissítések segítségével frissítse a legfelső szintű helyet újabb verzióra.**  

    -   Gyermek helyek vagy ügyfelek telepítése előtt frissítse a legfelső szintű helyet a használni kívánt frissített verzióra.  
    -   Például a legfelső szintű hely verziójára 1610 1606 verziót futtató segítségével frissítheti. További információ: [A System Center Configuration Manager frissítései](../../../../core/servers/manage/updates.md).  

    Ez a lépés után a a legfelső szintű hely verzióját 1610 futtatja.  

3.  **Telepítse az új gyermek elsődleges helyeket a központi adminisztrációs hely alá.**  

    -   A gyermek elsődleges helyek telepítéséhez használja a központi adminisztrációs helykiszolgáló CD.Latest mappájában található telepítési adatokat. További információért lásd: [A System Center Configuration Manager CD.Latest mappája](../../../../core/servers/manage/the-cd.latest-folder.md).  

      Mindenképpen ezt a forrást használja, mivel így az új gyermek elsődleges helyek verziója biztosan egyezni fog a központi adminisztrációs hely verziójával.  

    Elvégezte a lépést az új gyermek elsődleges helyeken 1610 verzióját futtassa.  

4.  **Minden elsődleges helyen a konzolon belüli lehetőség használatával telepítse a másodlagos helyeket.**  

    -   Másodlagos helyeket nem telepítette, amikor az elsődleges helyek még az verzió 1606, mert nem kell a másodlagos helyek frissítésére.  
    -   Ehelyett telepítsen 1610 verzióját futtató másodlagos helyeket. További információ: [A telepítővarázsló használata helyek telepítéséhez](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites) című témakör [Másodlagos hely telepítése](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary) című szakasza.  

    Ez a lépés után új másodlagos helyek telepítse és 1610 verzióját futtatják.  

5.  **Telepítse az új ügyfeleket az elsődleges helyen.**  

    -   Az ügyfelek nem telepítette, amikor az elsődleges helyek még az verzió 1606, mert nem kell ügyfelek verzió 1606 1610 verzióra frissítésével.  
    -   Ehelyett telepítsen új 1610 verzióját futtató ügyfelek. További információkért lásd: [a System Center Configuration Manager-ügyfelek központi telepítése](../../../clients/deploy/deploy-clients-to-windows-computers.md).  

    Ha elvégezte a lépést az újonnan telepített ügyfeleken 1610 verzióját futtató.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>Forgatókönyv: Frissítés a System Center 2012 Configuration Manager a System Center Configuration Manager, aktuális ágának frissített verziójára  
Ebben a példaforgatókönyvben hasonlóan 1610 frissített verziójára a System Center Configuration Manager, a Microsoft System Center 2012 Configuration Manager infrastruktúra frissíti.  

-   A központi adminisztrációs helyen és az összes elsődleges hely az alapkonfiguráció 1606 1610 verziójához a frissítés telepítése előtt frissíteni kell.  
-   A másodlagos helyek és ügyfelek ne frissítse és 1606 verzió telepítése. Ehelyett mozognak közvetlenül a Microsoft System Center 2012 Configuration Manager a System Center Configuration Manager verziója 1610.  

Kövesse az ebben a sorozatban:  

1.  **A Microsoft System Center 2012 Configuration Manager legfelső szintű helyet** a forrás-adathordozóján a System Center Configuration Manager használatával (hasonlóan 1606) az aktuális ág alapszintű verziójára. További információkért lásd: [frissítése a System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md).  

    -   Frissítési forgatókönyvek esetében megszokott, például először frissíti egy hierarchia legfelső szintű helyen, és frissítse a gyermekhelyekre.  

    Ez a lépés után a a legfelső szintű hely verzióját 1606 futtatja.  

2.  **Frissítse a hierarchiához tartozó összes gyermek elsődleges helyet** ugyanerre az alapszintű verzióra.  

    -   Amikor frissíti a Microsoft System Center 2012 Configuration Manager, kézzel kell frissítenie minden elsődleges helyen az aktuális ág alapszintű verziójára.  
    -   A másodlagos helyek ezen a ponton nem frissíti.  

    Ez a lépés után az elsődleges helyekhez futtat a 1606.  

3.  **Karbantartási időszakok beállítása a gyermek elsődleges helyeken.** Miután az elsődleges helyeken az alapszintű verzióra frissít, tervezze meg karbantartási időszakokkal szabályozhatja a helyek mikor telepítsék az infrastruktúrát érintő frissítéseket konfigurálása. További információkért lásd: [a System Center Configuration Manager karbantartási időszakok használata](../../../../core/clients/manage/collections/use-maintenance-windows.md).  (A karbantartási időszakok nevezzük *windows szolgáltatás* verziójában 1606.)  

    -   A gyermek elsődleges helyek automatikusan telepítik a központi adminisztrációs helyre telepített frissítéseket.  
    -   Másodlagos helyek nem telepítik automatikusan az új verziók. Frissítenie kell őket manuálisan a konzolon.  

  Ha elvégezte ezt a lépést, és a továbbiakban frissítéseket telepít a központi adminisztrációs helyen, a gyermek elsődleges helyek csak akkor fogják telepíteni a frissítést, amikor ezt a karbantartási időszak beállítása lehetővé teszi.  

4.  **Telepítse a frissített verziót a legfelső szintű helyén.** Ekkor frissül, a legfelső szintű helyen. Miután egy központi adminisztrációs hely telepítése a frissített verzióra, a összes alárendelt elsődleges hely automatikusan telepíti a frissítést, kivéve, ha a telepítés le van tiltva, a karbantartási időszak beállítása.  

    -   Például verzióra 1610 1606 verziójáról a legfelső szintű hely frissíthető. További információ: [A System Center Configuration Manager frissítései](../../../../core/servers/manage/updates.md).  

    Ez a lépés után a a központi adminisztrációs helyen és az összes elsődleges hely 1610 verzióját futtatja.  

5.  **Frissítse a másodlagos helyeket.** Miután egy elsődleges helyet telepíti a frissítést, és 1610 verzióját futtatja, a konzolon belüli lehetőség használatával másodlagos helyek frissítésére.  

    -   Ez az elsődleges helyen telepített frissített verzióra közvetlenül a Microsoft System Center 2012 Configuration Manager frissíti a másodlagos helyek.  
    -   A másodlagos helyek frissítésével kapcsolatos információkért lásd: [helyek frissítésére](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade) a a [frissítése a System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) témakör.  

6.  **Frissítse az ügyfeleket.** Ügyfelek frissítése, olvassa el a [frissítése a Windows rendszerű számítógépekre a System Center Configuration Manager-ügyfelek](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

    -   Ez ügyfelek frissítése a Microsoft System Center 2012 Configuration Manager-ről az elsődleges helyen telepített frissített verzióra.  

    Ez a lépés után az ügyfelek verzióra, hogy 1610 1606 verzióra történő frissítés első nélkül.

