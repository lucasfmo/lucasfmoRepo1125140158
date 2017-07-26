---
title: "Támogatott helyrendszer-kiszolgálók |} Microsoft Docs"
description: "Ismerje meg, hogy mely Windows-verziók a System Center Configuration Manager-hely vagy helyrendszer-szerepkör tárolására is használhatja."
ms.custom: na
ms.date: 3/9/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
caps.latest.revision: 44
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 86109f7186422c2b29ee933e827a7d14123e5792
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="supported-operating-systems-for-system-center-configuration-manager-site-system-servers"></a>Támogatott operációs rendszerek a System Center Configuration Manager helyrendszer-kiszolgálókhoz

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Ez a cikk részletezi, amelyek segítségével a System Center Configuration Manager-hely és helyrendszer-szerepkör a Windows-verziók.


Használja a témakörben szereplő információkat az alábbi cikkekben található információkkal:
-   [A Configuration Manager ajánlott hardver](../../../core/plan-design/configs/recommended-hardware.md)
-   [Hely és hely rendszer Előfeltételek a Configuration Manager](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)
-   [Méret és a skálázási számok a Configuration Manager](../../../core/plan-design/configs/size-and-scale-numbers.md)



## <a name="windows-server-2016-standard-and-datacenter"></a>Windows Server 2016: Standard és Datacenter
Verziójától 1606 a gyorsjavítás összesítő KB3186654 (vagy 1606, az Alapverzió 2016. októberi kiadott) az operációs rendszer támogatott a következő:

**Helykiszolgálók:**  

-   Központi adminisztrációs hely  

-   Elsődleges hely  

-   Másodlagos hely  

**Helyrendszer-kiszolgálók:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Tanúsítványregisztrációs pont  

-   Terjesztési pont  

     A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont

-   Jelentéskészítési szolgáltatási pont  

-   Szolgáltatáskapcsolódási pont  

-   Helyadatbázis-kiszolgáló  

     A helyadatbázis-kiszolgálók nem használhatók írásvédett tartományvezérlőkön (RODC). A további tudnivalók a Microsoft tudásbázis következő, angol nyelvű cikkében találhatók: [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) . Ezenkívül a másodlagos helykiszolgálók semmilyen tartományvezérlőn nem támogatottak.  

-   SMS-szolgáltató  

-   Szoftverfrissítési pont  

-   állapotáttelepítési pont

## <a name="windows-server-2012-r2-x64-standard-and-datacenter"></a>Windows Server 2012 R2 (x 64): Standard és Datacenter  
**Helykiszolgálók:**  

-   Központi adminisztrációs hely  

-   Elsődleges hely  

-   Másodlagos hely  

**Helyrendszer-kiszolgálók:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Tanúsítványregisztrációs pont  

-   Terjesztési pont  

     A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont

-   Jelentéskészítési szolgáltatási pont  

-   Szolgáltatáskapcsolódási pont  

-   Helyadatbázis-kiszolgáló  

     A helyadatbázis-kiszolgálók nem használhatók írásvédett tartományvezérlőkön (RODC). A további tudnivalók a Microsoft tudásbázis következő, angol nyelvű cikkében találhatók: [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) . Ezenkívül a másodlagos helykiszolgálók semmilyen tartományvezérlőn nem támogatottak.  

-   SMS-szolgáltató  

-   Szoftverfrissítési pont  

-   állapotáttelepítési pont  

## <a name="windows-server-2012-x64-standard-and-datacenter"></a>Windows Server 2012 (x 64): Standard és Datacenter  
**Helykiszolgálók:**  

-   Központi adminisztrációs hely  

-   Elsődleges hely  

-   Másodlagos hely  

**Helyrendszer-kiszolgálók:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Tanúsítványregisztrációs pont  

-   Terjesztési pont  

     A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont

-   Jelentéskészítési szolgáltatási pont  

-   Szolgáltatáskapcsolódási pont  

-   Helyadatbázis-kiszolgáló  

     A helyadatbázis-kiszolgálók nem használhatók írásvédett tartományvezérlőkön (RODC). A további tudnivalók a Microsoft tudásbázis következő, angol nyelvű cikkében találhatók: [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) . Ezenkívül a másodlagos helykiszolgálók semmilyen tartományvezérlőn nem támogatottak.  

-   SMS-szolgáltató  

-   Szoftverfrissítési pont  

-   állapotáttelepítési pont  

## <a name="windows-server-2008-r2-with-sp1-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 R2 SP1 (x 64): Standard, Enterprise és Datacenter  
 Windows Server 2008 R2 rendszert jelenleg már meghosszabbított támogatás és nem alapvető technikai támogatással, ahogy az az [Microsoft terméktámogatási ciklusait](https://support.microsoft.com/lifecycle). A Configuration Manager helyrendszer-kiszolgálóként a fenti operációs rendszerek jövőbeli támogatásával kapcsolatos további információkért lásd: [eltávolítva és elavult funkciók a System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 A Configuration Manager verziója 1702 kezdve, az operációs rendszer helykiszolgálókon vagy a legtöbb helyrendszerszerepkör esetében nem támogatott, de is támogatni, az állapotáttelepítési pont és terjesztési pont helyrendszer-szerepkör (beleértve a lekéréses terjesztési pontok, és a PXE és csoportos küldés).
 
 1702 korábbi verziók továbbra is használható a következő.


**Helykiszolgálók:**  

-   Központi adminisztrációs hely  

-   Elsődleges hely  

-   Másodlagos hely  

**Helyrendszer-kiszolgálók:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Eszközintelligencia-katalógus szinkronizálási pontja  

-   Tanúsítványregisztrációs pont  

-   Terjesztési pont  

     A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont

-   Jelentéskészítési szolgáltatási pont  

-   Szolgáltatáskapcsolódási pont  

-   Helyadatbázis-kiszolgáló  

     A helyadatbázis-kiszolgálók nem használhatók írásvédett tartományvezérlőkön (RODC). A további tudnivalók a Microsoft tudásbázis következő, angol nyelvű cikkében találhatók: [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) . Ezenkívül a másodlagos helykiszolgálók semmilyen tartományvezérlőn nem támogatottak.  

-   SMS-szolgáltató  

-   Szoftverfrissítési pont  

-   állapotáttelepítési pont  

## <a name="windows-server-2008-with-sp2-x86-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 SP2 (x 86, x 64): Standard, Enterprise és Datacenter  
 Windows Server 2008 rendszert jelenleg már meghosszabbított támogatás és nem alapvető technikai támogatással, ahogy az az [Microsoft terméktámogatási ciklusait](https://support.microsoft.com/lifecycle). A Configuration Manager helyrendszer-kiszolgálóként a fenti operációs rendszerek jövőbeli támogatásával kapcsolatos további információkért lásd: [eltávolítva és elavult funkciók a System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

Ez az operációs rendszer nem támogatott a helykiszolgálókon vagy helyrendszer-szerepkörök a terjesztési pont és a lekéréses terjesztési pontok kivételével. Továbbra is használható az operációs rendszer terjesztési pontként, amíg ez a támogatás elavulásának bejelentéséig, illetve az operációs rendszer kiterjesztett támogatási időszakának lejártáig. További információkért lásd: [a System Center Configuration Manager CB telepítési és LTSB nem sikerül, a Windows Server 2008](https://support.microsoft.com/help/4015095).

**Helyrendszer-kiszolgálók:**  
-   Terjesztési pont  

    -   Ezen az operációs rendszeren a terjesztési pontok nem támogatják a csoportos küldést.  

    -   Az operációs rendszer támogatja a terjesztési pontokat a PXE használatához, de az ügyfélszámítógépek EFI üzemmódban történő hálózati rendszerindítását nem. A BIOS vagy örökölt módú EFI rendszerindítású ügyfélszámítógépek támogatottak.  

    -   A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-10-x86-x64-pro-and-enterprise"></a>Windows 10 (x86, x64): Pro és Enterprise  
**Helyrendszer-kiszolgálók:**  

-   Terjesztési pont  

    -   Ez az operációs rendszer nem támogatja a terjesztési pontokat a PXE használatához.  

    -   Ezen az operációs rendszeren a terjesztési pontok nem támogatják a csoportos küldést.  

    -   A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-81-x86-x64-professional-and-enterprise"></a>Windows 8.1 (x86, x64): Professional és Enterprise  
**Helyrendszer-kiszolgálók:**  

-   Terjesztési pont  

    -   Ez az operációs rendszer nem támogatja a terjesztési pontokat a PXE használatához.  

    -   Ezen az operációs rendszeren a terjesztési pontok nem támogatják a csoportos küldést.  

    -   A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Bizonyos esetekben a konfigurációs támogatásának telepítése nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-8-x86-x64-professional-and-enterprise"></a>Windows 8 (x86, x64): Professional és Enterprise
**Helyrendszer-kiszolgálók:**  

-   Terjesztési pont  

    -   Ez az operációs rendszer nem támogatja a terjesztési pontokat a PXE használatához.  

    -   Ezen az operációs rendszeren a terjesztési pontok nem támogatják a csoportos küldést.  

    -   A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-7-with-sp1-x86-x64-professional-enterprise-and-ultimate"></a>Windows 7 SP1 (x 86, x 64): Professional, Enterprise és Ultimate  
**Helyrendszer-kiszolgálók:**  

-   Terjesztési pont  

    -   Ez az operációs rendszer nem támogatja a terjesztési pontokat a PXE használatához.  

    -   Ezen az operációs rendszeren a terjesztési pontok nem támogatják a csoportos küldést.  

    -   A terjesztési pontok, eltérő követelményekkel rendelkező számos különböző konfigurációt támogatnak. Néhány esetben ezeket a konfigurációkat támogatják a telepítést nem csak a kiszolgálókon, hanem az ügyfél operációs rendszereken. A terjesztési pontok rendelkezésre álló beállításokkal kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


## <a name="the-server-core-installation-of-windows-server-2016"></a>A server core telepítési lehetőség Windows Server 2016
A gyorsjavítás összesítő KB3186654 (vagy 1606, az Alapverzió 2016. októberi kiadott) 1606 verziójától ebben az operációs rendszerben való használata is támogatott jelenítik meg terjesztési pont a következő korlátozásokkal:  
  -   Csak a x64 bites verziója támogatott.
  -   Az operációs rendszer terjesztési pontok nem támogatják a PXE vagy csoportos küldést.  


## <a name="the-server-core-installation-of-windows-server-2012-r2"></a>Windows Server 2012 R2 Server Core telepítése  
 A korábbi operációs rendszerek mellett felsorolt a server core telepítési lehetőség Windows Server 2012 R2 van támogatott használatra szolgáló terjesztési pontként a következő korlátozásokkal:  

-   Csak a x64 bites verziója támogatott.

-   Az operációs rendszer terjesztési pontok nem támogatják a PXE vagy csoportos küldést.  

## <a name="the-server-core-installation-of-windows-server-2012"></a>Windows Server 2012 Server Core telepítése  
 Mellett a korábbi operációs rendszereket a listáról, a server core telepítési lehetőség Windows Server 2012 rendszer is való használata támogatott jelenítik meg terjesztési pont a következő korlátozásokkal:  

-   Csak a 64 bites verziója támogatott.  

-   Az operációs rendszer terjesztési pontok nem támogatják a PXE vagy csoportos küldést.

