---
title: "Eszközök kezelése – alapok |} Microsoft Docs"
description: "Útmutató eszközök kezelése a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: 6
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 45d84122a86da880268c93ecd994250df6b76c8a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>A System Center Configuration Managerrel végzett eszközfelügyelet alapjai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager kezelhető eszközök széles két kategóriába sorolhatók:

-   *Ügyfelek* különböző eszközök, például munkaállomások, laptopok, kiszolgálók és mobileszközök, amelyre telepíti a Configuration Manager ügyfélszoftver. Bizonyos kezelési funkciók, például a hardverleltárhoz igényel az ügyfélszoftvert.  

-   *Felügyelt eszközök* tartalmazhatnak *ügyfelek*, de általában a mobileszköz, amelyen nincs telepítve a Configuration Manager ügyfélszoftver. Az ilyen típusú eszközök kezelheti az Intune-ban, vagy a beépített helyszíni mobileszköz-kezelés a Configuration Manager használatával.

Csoport is, és azonosíthatja azokat az eszközöket, a felhasználó, nem csak az ügyfél típusa alapján.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Eszközök felügyelete a Configuration Manager-ügyféllel

Egy eszköz felügyelete a Configuration Manager ügyfélszoftver használatára két módja van. Az első módja, ha az eszköz a hálózat felderítése, és eszközre telepíteni az ügyfélszoftvert. A más módja, ha az ügyfél szoftverek manuális telepítése egy új számítógépre, és csatlakozzon a kívánt helyhez, amikor bekerül a hálózat számítógép már rendelkezik. Az ügyfélszoftver nem futtató eszközök felderítésére, futtassa a beépített felderítési módszerek közül legalább egyet. Egy eszköz felderítését követően többféle módszer segítségével telepítse az ügyfélszoftvert. További információ a felderítés használatáról: [A felderítés futtatása a System Center Configuration Managerből](../../core/servers/deploy/configure/run-discovery.md).  

 Miután értesült az eszközöket, amelyek a Configuration Manager ügyfélszoftver futtatására, a szoftver telepítéséhez használhatja többféle módszer. A szoftver telepítését, valamint az ügyfél elsődleges helyhez való rendelését követően megkezdheti az eszköz felügyeletét.  Gyakori telepítési módszerek a következők:

 - Az ügyfélleküldéses telepítés.

 - Szoftver-alapú telepítés.

 - Csoport házirend.

 - Manuális telepítés a számítógépre.
 - A ügyfeleket telepít egy operációsrendszer-lemezkép részeként is beleértve.  


 Az ügyfél telepítését követően az eszközök felügyelete a gyűjtemények funkció használatával tovább egyszerűsíthető. Gyűjtemények olyan eszközöket vagy felhasználókat, amelyek lehetővé teszik, csoportként kezelheti azokat. Például előfordulhat, hogy szeretne egy alkalmazást minden mobileszközre, amely a Configuration Manager telepítéséhez. Ha ez a helyzet, használhatja a minden mobileszköz gyűjteményben.  

 További információ az alábbi témakörökben talál:  

-   [A System Center Configuration Manager eszköz felügyeleti megoldás kiválasztása](../../core/plan-design/choose-a-device-management-solution.md)  

-   [Ügyféltelepítési módszerek a System Center Configuration Managerben](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [A System Center Configuration Manager gyűjteményeinek bemutatása](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>Ügyfélbeállítások  
 A Configuration Manager első telepítésekor a hierarchiában lévő összes ügyfél alapértelmezett ügyfélbeállításait, amelyek megváltoztathatók használatával vannak konfigurálva. A beállítások lehetnek a konfigurációs beállításokról:

 -  Milyen gyakran az eszközök a hellyel való kommunikációhoz.

 -  Hogy az ügyfél be van állítva a szoftverfrissítések és az egyéb felügyeleti műveleteket.

 -  E felhasználók beléptethetik a mobileszközeiket, így azok még a Configuration Manager által felügyelt.  

Egyéni ügyfélbeállítások létrehozásával, és hozzárendelheti azokat gyűjteményekhez.  A gyűjtemény tagjai egyéni beállításokhoz vannak konfigurálva, és létrehozhat több egyéni ügyfél-beállításokat (szám szerinti) megadott sorrendben.  A beállítások ütközése esetén a kisebb sorszámú beállítás felülbírálja a többi konfigurációt.  

Az alábbi ábrán látható példát létrehozását és egyedi ügyfélfelhasználó-beállítások alkalmazásához.  

 ![Ügyfélbeállítások](media/ClientSettings.gif)  

 Az ügyfél-beállításokkal kapcsolatos további információkért lásd:  
                [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md) és [Tudnivalók a System Center Configuration Manager ügyfélbeállításairól](../../core/clients/deploy/about-client-settings.md).

## <a name="managing-devices-without-the-configuration-manager-client"></a>Eszközök felügyelete a Configuration Manager-ügyfél nélkül  
 A Configuration Manager nem telepítette az ügyfélszoftvert, és nem az Intune által kezelt eszközök kezelését támogatja. További információkért lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) és [mobileszközök kezelése a System Center Configuration Manager és az Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

## <a name="user-based-management"></a>Felhasználó-alapú felügyelet  
 A Configuration Manager támogatja az Active Directory tartományi szolgáltatások felhasználók gyűjteményei. Felhasználógyűjtemény használata esetén telepítheti szoftvert minden olyan számítógépre, hogy a gyűjtemény használatát tagjai. Győződjön meg arról, hogy a szoftver központi telepítése az eszközökön, hogy a felhasználó elsődleges eszközén csak telepíti, állítsa be a felhasználó-eszköz kapcsolatot. Egy felhasználó több elsődleges eszközzel is rendelkezhet.  

 A módon, hogy a felhasználók szabályozhatják a szoftver központi telepítési élmény egyik használja a **Szoftverközpont** ügyféloldali felületen. A **Szoftverközpont** ügyfélszámítógépek automatikusan telepítve van és fut a **Start** menü. A **Szoftverközpont** lehetővé teszi, hogy a felhasználók kezelése a saját szoftvereiket, és hajtsa végre a következő feladatokat:  

-   Szoftver telepítése.  

-   Ütemezze a szoftverek automatikusan telepíthetők a munkaidőn kívül.  

-   Konfigurálja, ha a Configuration Manager mikor telepíthet szoftvereket az eszközön.  

-   A távvezérlés hozzáférési beállításainak konfigurálása, ha a távvezérlés be van állítva a Configuration Manager.  

-   Ha egy rendszergazda állít be ezt a beállítást, energiagazdálkodási beállítások konfigurálása  


 Tartalmaz egy hivatkozást a **Szoftverközpont** lehetővé teszi, hogy a felhasználók csatlakozni a **Alkalmazáskatalógus**, ahonnan tallózással keresse meg, telepítse, és igényelhetnek szoftvereket. A **Alkalmazáskatalógus** egyéni beállításokat is konfigurálhatnak, mobileszközökről, ha ezt a beállítást, adja meg a felhasználó-eszköz kapcsolat elsődleges eszköz is használható.   

 Felhasználók is elérhetik a **Alkalmazáskatalógus** böngésző intranetes vagy internetes munkamenet keresztül.  

