---
title: "Ügyfelek frissítése |} Microsoft Docs"
description: "A System Center Configuration Manager ügyfelek frissítése adatainak beolvasása."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 4b80e0e688dd6482bc9a7fe111607e258071f45a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-clients-in-system-center-configuration-manager"></a>Ügyfélszoftverek verziófrissítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Különböző módszereket használhat a Windows rendszerű számítógépek, UNIX és Linux-kiszolgálókon és Mac számítógépekre a System Center Configuration Manager ügyfélszoftver frissítéséhez. Az alábbiakban előnyeit és hátrányait az egyes módszerek.  

> [!TIP]  
>  Amennyiben a Configuration Manager egy előző verziójáról frissíti a kiszolgáló infrastruktúráját \(például Configuration Manager 2007-ről, vagy System Center 2012 Configuration Managerről\), a Configuration Manager-ügyfelek frissítése előtt ajánlott a kiszolgálófrissítések elvégzése, beleértve az összes aktuális ág frissítését is. Ezzel a módszerrel is összekapcsolta az ügyfélszoftver legújabb verziójának.  

## <a name="group-policy-installation"></a>Csoportházirend telepítése  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél frissítéséhez.  

-   Új ügyfelek telepítésére és frissítésre is használható.  

-   A számítógépek kiolvashatják az Active Directory tartományszolgáltatásokban közzétett ügyféltelepítési tulajdonságokat.  

-   Nem kell konfigurálnia és karbantartania egy telepítési fiókot az adott ügyfélszámítógéphez.  

 **Hátrányok**  

-   Nagy hálózati forgalmat okozhat nagy mennyiségű ügyfél frissítés.  

-   Ha az Active Directory-séma nincs kibővítve a Configuration Manager, kell használnia [csoportházirend-beállítások](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP) ügyfél-telepítési tulajdonságok hozzáadása a hely számítógépein.  


## <a name="logon-script-installation"></a>Bejelentkezési parancsprogramfájl telepítése  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél telepítéséhez.  

-   Új ügyfelek telepítésére és frissítésre is használható.  

-   Támogatja a parancssori tulajdonságok használatát a CCMSetup eszközhöz.  

 **Hátrányok**  

-   Nagy hálózati forgalmat okozhat az ügyfelek rövid időn belül számos frissítés.  

-   A számítógépek frissítéséhez, ha a felhasználók nem jelentkeznek be gyakran a hálózatba hosszú időt vehet igénybe.  

 További információk: [A Configuration Manager-ügyfelek telepítése bejelentkezési parancsfájlok használatával](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript).  

## <a name="manual-installation"></a>Manuális telepítés  
 **Támogatott ügyfélplatform:** Windows, UNIX/Linus, Mac OS X  

 **Előnyök**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél frissítéséhez.  

-   Tesztelési célokra hasznos lehet.  

-   Támogatja a parancssori tulajdonságok használatát a CCMSetup eszközhöz.  

 **Hátrányok**  

-   Nincs automatizálva, ezért időigényes.  

 További információ a következő témakörökben:  

-   [A Configuration Manager ügyfelek manuális telepítése](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Manual)  

-   [A Linux és UNIX rendszerű kiszolgálók a System Center Configuration Manager ügyfelek frissítése](../../../../core/clients/manage/upgrade/upgrade-clients-for-linux-and-unix-servers.md)  

-   [A System Center Configuration Manager Mac számítógépeken lévő ügyfelek frissítése](../../../../core/clients/manage/upgrade/upgrade-clients-on-mac-computers.md)  

## <a name="upgrade-installation-application-management"></a>Frissítéstelepítés (alkalmazáskezelés)  
 **Támogatott ügyfélplatform:** Windows  

> [!NOTE]  
>  Ezzel a módszerrel a Configuration Manager 2007-ügyfelek nem frissíthető. Ebben a forgatókönyvben egy csomagot a Configuration Manager 2007 helyről a Configuration Manager-ügyfelet telepítheti, vagy használhatja az automatikus ügyfélfrissítést, mely automatikusan létrehozza és telepíti az ügyfél legújabb verzióját tartalmazó csomagot.  

 **Előnyök**  

-   Támogatja a parancssori tulajdonságok használatát a CCMSetup eszközhöz.  

 **Hátrányok**  

-   Nagy hálózati forgalmat is okozhat, ha nagy gyűjteményekre ügyfél.  

-   Csak olyan felderített számítógépek ügyfélszoftverének frissítésére használható, melyeket hozzárendeltek a helyhez.  

 További információk: [A Configuration Manager-ügyfelek telepítése csomag és program használatával](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientApp).  

## <a name="automatic-client-upgrade"></a>Automatikus ügyfélfrissítés  

> [!NOTE]  
>  A Configuration Manager 2007-ügyfelek frissítése a System Center Configuration Manager ügyfelek használható. A Configuration Manager 2007-ügyfél a Configuration Manager-hely rendelhet, de automatikus ügyfélfrissítésen műveletet nem lehet végrehajtani.  

 **Támogatott ügyfélplatform:** Windows  

 **Előnyök**  

-   A hely ügyfeleinek automatikus legújabb verzión tartására használható.  

-   Minimális adminisztrációt.  

 **Hátrányok**  

-   Csak az ügyfélszoftver frissítésére használható, nem lehet vele új ügyfélszoftvert telepíteni.  

-   Nem alkalmas egyszerre sok ügyfél frissítésére.  

-   A hierarchia minden olyan ügyfelére érvényes, amely hozzá van rendelve a helyhez. Gyűjteményenkénti hatókörrel nem használható.  

-   Korlátozott ütemezési lehetőségei vannak.  

 További információk: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

## <a name="client-testing"></a>Ügyfél tesztelése  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök**  

-   Új ügyfél-verziók ellenőrzéséhez egy kisebb üzem előtti gyűjtemény használható.  

-   A tesztelés során az éles üzem előtti ügyfelek üzemi előléptetve, és a Configuration Manager-hely automatikusan frissülnek.  

 **Hátrányok**  

-   Csak az ügyfélszoftver frissítésére használható, nem lehet vele új ügyfélszoftvert telepíteni.  

 [Ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  

