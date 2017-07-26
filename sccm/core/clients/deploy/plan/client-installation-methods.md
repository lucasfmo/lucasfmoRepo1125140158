---
title: "Ügyféltelepítési módszerek |} Microsoft Docs"
description: "Ismerje meg, a System Center Configuration Manager ügyfél-telepítési módszert."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: edca31249cc2bb3e0c67265962815c82e3f4711e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>Ügyféltelepítési módszerek a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager ügyfélszoftver telepítéséhez a különböző módszereket használhat. Egy módszer vagy módszerek kombinációját használhatja. Ebben a témakörben áttekintheti az egyes módszerek, megtudhatja, melyik működhet a legjobban a szervezetében.  

## <a name="client-push-installation"></a>Ügyfél leküldéses telepítése  

 **Támogatott ügyfélplatform:** Windows  

 **Előnyök**  

-   Egyetlen számítógép, egy számítógép-gyűjtemény vagy egy lekérdezés eredményeként előálló számítógépcsoport ügyfélprogramjának telepítésére használható.  

-   Az összes felderített számítógépre automatikusan telepíthető vele az ügyfélprogram.  

-   Automatikusan használja az **Ügyfél** lapon az **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanelben meghatározott ügyféltelepítési tulajdonságokat.  

 **Hátrányok**  

-   Nagy hálózati forgalmat okozhat, ha nagy gyűjteményekre végez leküldést.  

-   Csak használható a Configuration Manager által felderített számítógépeken.  

-   Nem használható munkacsoportban lévő ügyfelek telepítésére.  

-   Meg kell adnia egy ügyfélleküldéses telepítési fiókot, mely rendszergazdai jogosultságokkal rendelkezik az adott ügyfélszámítógépen.  

-   Úgy kell beállítani a kivételeket a Windows tűzfalban az ügyfélszámítógépeken, hogy elvégezhető legyen az ügyfélleküldéses telepítés.  

-   Az ügyfélleküldéses telepítést nem lehet megszakítani. Amikor egy helyre ezt az ügyféltelepítést használja, a Configuration Manager ügyfél telepítése az összes felderített erőforrásra megpróbálja, és hiba esetén legfeljebb 7 napig újrapróbálja.  

 A telepítési módszerrel kapcsolatos további információ: [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="software-update-point-based-installation"></a>Szoftverfrissítési ponton alapuló telepítés  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök:**  

-   A szoftverfrissítések meglévő infrastruktúráját használhatja az ügyfélszoftver kezelésére.  

-   Automatikusan telepítheti az ügyfélszoftvert az új számítógépekre, ha megfelelően vannak konfigurálva a Windows Server Update Services (WSUS) és a csoportházirend-beállítások az Active Directory tartományszolgáltatásokban.  

-   Nincs szükség a számítógépek felfedezésére az ügyfél telepítéséhez.  

-   A számítógépek kiolvashatják az Active Directory tartományszolgáltatásokban közzétett ügyféltelepítési tulajdonságokat.  

-   Újratelepíti az ügyfélszoftvert, ha eltávolítják azt.  

-   Nem kell konfigurálnia és karbantartania egy telepítési fiókot az adott ügyfélszámítógéphez.  

 **Hátrányok:**  

-   Előfeltételként szükséges hozzá egy működőképes szoftverfrissítési infrastruktúra.  

-   Ugyanazt a kiszolgálót kell használnia az ügyfél telepítéséhez és a szoftverfrissítéshez, és ennek a kiszolgálónak egy elsődleges helyen kell lennie.  

-   Új ügyfelek telepítéséhez konfigurálnia kell egy csoportházirend-objektumot (GPO) az Active Directory Domain Servicesben az ügyfél aktív szoftverfrissítési pontjával és portjával.  

-   Ha az Active Directory-séma nincs kibővítve a Configuration Manager, a csoportházirend-beállítások a számítógépeket ügyféltelepítési tulajdonságokkal kell használnia.  

 A telepítési módszerrel kapcsolatos további információ: [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="group-policy-installation"></a>Csoportházirend telepítése  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök:**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél telepítéséhez.  

-   Új ügyfelek telepítésére és frissítésre is használható.  

-   A számítógépek kiolvashatják az Active Directory tartományszolgáltatásokban közzétett ügyféltelepítési tulajdonságokat.  

-   Nem kell konfigurálnia és karbantartania egy telepítési fiókot az adott ügyfélszámítógéphez.  

 **Hátrányok:**  

-   Nagy hálózati forgalmat okozhat, ha sok ügyfelet telepít.  

-   Ha az Active Directory-séma nincs kibővítve a Configuration Manager, a csoportházirend-beállítások számítógépek a webhely ügyfél-telepítési tulajdonságok hozzáadása kell használnia.  

 A telepítési módszerrel kapcsolatos további információ: [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="logon-script-installation"></a>Bejelentkezési parancsprogramfájl telepítése  
 **Támogatott ügyfélplatform:** Windows  

 **Előnyök:**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél telepítéséhez.  

-   Támogatja a parancssori tulajdonságok használatát a CCMSetup eszközhöz.  

 **Hátrányok:**  

-   Nagy hálózati forgalmat okozhat, ha sok ügyfelet telepít rövid idő alatt.  

-   Hosszú időt vehet igénybe az ügyfél telepítése az összes számítógépre, ha a felhasználók nem jelentkeznek be gyakran a hálózatba.  

 A telepítési módszerrel kapcsolatos további információ: [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="manual-installation"></a>Manuális telepítés  
 **Támogatott ügyfélplatform:** Windows, UNIX/Linux, Mac OS X  

 **Előnyök:**  

-   Nincs szükség a számítógépek felfedezésére az ügyfél telepítéséhez.  

-   Tesztelési célokra hasznos lehet.  

-   Támogatja a parancssori tulajdonságok használatát a CCMSetup eszközhöz.  

 **Hátrányok:**  

-   Nincs automatizálva, ezért időigényes.  

 Az ügyfél egyes platformokon való manuális telepítésével kapcsolatos további tudnivalókért lásd:  

-   [Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

-   [Ügyfelek üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)  

-   [Ügyfélszoftverek központi telepítése Mac-számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

