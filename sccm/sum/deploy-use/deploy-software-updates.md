---
title: "Szoftverfrissítések központi telepítése |} Microsoft Docs"
description: "Szoftverfrissítések adja meg manuálisan elindítani a telepítési folyamat, és automatikusan telepítheti a frissítéseket a Configuration Manager konzolon."
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
ms.assetid: 04536d51-3bf7-45e5-b4af-36ceed10583d
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 70a0ad1da03a7ca88df206fec683ab1df2b531e1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

#  <a name="BKMK_SUMDeploy"></a> Szoftverfrissítések központi telepítése  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A szoftverfrissítések központi telepítése fázisban megtörténik a szoftverfrissítések központi telepítése. Függetlenül attól, hogy központilag telepíti a szoftverfrissítéseket a frissítések általában kerülnek egy szoftverfrissítési csoportba, a szoftverfrissítések letöltődnek a terjesztési pontokra, majd a frissítési csoport központi telepítése az ügyfelek. A központi telepítés létrehozásakor egy társított szoftverfrissítési házirend zajlik az ügyfélszámítógépek számára, a szoftverfrissítést tartalmazó fájlok letöltése a terjesztési pontokról a helyi gyorsítótárba az ügyfélszámítógépeken, és ezután a szoftverfrissítések érhetők el az ügyfél telepítéséhez. Az interneten levő ügyfelek a Microsoft Update segítségével töltik le a tartalmat.  

> [!NOTE]  
>  Az intraneten lévő ügyfelek beállíthatók úgy, hogy a Microsoft Update webhelyről töltsék le a szoftverfrissítéseket, ha nem érhető el egy terjesztési pont.  

> [!NOTE]  
>  A más jellegű központi telepítésekkel ellentétben a rendszer az összes szoftverfrissítést letölti az ügyfél gyorsítótárába, bármekkora felső korlát vonatkozik rá az ügyfélen. További információk az ügyfél gyorsítótárának beállításairól: [A Configuration Manager-ügyfelekhez tartozó ügyfélgyorsítótár konfigurálása](../../core/clients/manage/manage-clients.md#BKMK_ClientCache).  

Ha egy szükséges szoftverfrissítéshez állít be központi telepítést, a szoftverfrissítések automatikus telepítésére a határidőként megadott időpontban kerül sor. Másik lehetőségként az ügyfélszámítógép felhasználója a határidő letelte előtt beütemezheti vagy kezdeményezheti a szoftverfrissítés telepítését. A telepítési kísérlet után az ügyfélszámítógép állapotüzeneteket küld a helykiszolgálónak, jelentve, hogy sikerült-e a szoftverfrissítés telepítése. További információk a szoftverfrissítések központi telepítéséről: [Szoftverfrissítések központi telepítési munkafolyamatai](../understand/software-updates-introduction.md#BKMK_DeploymentWorkflows).  

A szoftverfrissítések központi telepítése alapvetően kétféle módon történhet: manuális, illetve automatikus telepítéssel. Általában alapterv létrehozása a ügyfél számítógépek szoftverfrissítések manuális központi telepítésének megkezdéséhez fog, és majd kezeli az ügyfeleken a szoftverfrissítések automatikus központi telepítés segítségével.  

## <a name="BKMK_ManualDeployment"></a>Szoftverfrissítések manuális központi telepítése
Válassza ki azokat a szoftverfrissítéseket a Configuration Manager konzolon, és manuálisan indítsa el a telepítési folyamat. Ez a telepítési módszer jellemzően az ügyfélszámítógépek kötelező szoftverfrissítésekkel való ellátására szolgál a naprakész működés érdekében, mielőtt automatikus központi telepítési szabályokat hozna létre a rendszeres havi szoftverfrissítések telepítéséhez, illetve a „sávon kívüli” szoftverfrissítési követelmények teljesítéséhez. Az alábbi lista ismerteti a szoftverfrissítések manuális központi telepítésének általános folyamatát:  

1. Konkrét követelmények szerint szűrje a szoftverfrissítéseket. A megfelelő feltételek megadásával lekérheti például az összes olyan biztonsági és kritikus szoftverfrissítést, amelyre több mint 50 ügyfélszámítógépen szükség van.  
2. Hozzon létre egy szoftverfrissítési csoportot, amely a kívánt szoftverfrissítéseket tartalmazza.  
3. Töltse le a szoftverfrissítésekhez kapcsolódó tartalmat a szoftverfrissítési csoportba.  
4. Manuális módszerrel végezze el a szoftverfrissítési csoport központi telepítését.

Részletes útmutató: [szoftverfrissítések manuális központi telepítése](manually-deploy-software-updates.md).

## <a name="automatically-deploy-software-updates"></a>Szoftverfrissítések automatikus központi telepítése
A szoftverfrissítések automatikus központi telepítése automatikus központi telepítési szabályokkal konfigurálható. Ez az telepítési gyakran használják havi (általában más néven "Frissítő kedd") szoftver frissítések és definíciófrissítések kezeléséhez. A szabály futásakor frissítések törlődnek a szoftverfrissítési csoport (Ha egy meglévő használatával frissítse a csoport) szoftver, a szoftverfrissítéseket, amelyek megfelelnek a megadott feltételeknek megfelelő (például az utolsó hónapban kiadott összes biztonsági szoftverfrissítéseket) hozzáadódnak egy szoftverfrissítési csoportot, a szoftverfrissítések a tartalomfájlok letöltődnek és a terjesztési pontokra másolja, és a szoftverfrissítések központi telepítése a célgyűjteményben lévő ügyfelekre. Az alábbi lista ismerteti az általános munkafolyamat automatikusan a szoftverfrissítések központi telepítését:  

1.  Hozzon létre egy automatikus központi telepítési szabály adja meg a központi telepítés beállításait.
2.  A rendszer felveszi a szoftverfrissítéseket egy szoftverfrissítési csoportba.  
3.  A rendszer a célgyűjtemény ügyfélszámítógépein telepíti a szoftverfrissítési csoportot, ha a célgyűjtemény meg van adva.  

Meg kell határoznia, hogy milyen központi telepítési stratégiát kíván használni a környezetében. Az automatikus központi telepítési szabály létrehozását követően például tesztelési célú gyűjteményt is kijelölhet ügyfélszámítógépekből. Miután meggyőződött arról, hogy a szoftverfrissítéseket sikerült telepíteni a tesztcsoport tagjain, új központi telepítést adhat a szabályhoz, vagy bővebb ügyfélkört határozhat meg célgyűjteményként az a meglévő központi telepítésben. Az automatikus központi telepítési szabályok interaktív szoftverfrissítési objektumokat hoznak létre.  

-   Az automatikus központi telepítési szabállyal telepített szoftverfrissítéseket a rendszer automatikusan telepíti a célgyűjteménybe felvett új ügyfelekre is.  
-   A szoftverfrissítési csoportba felvett új szoftverfrissítéseket a rendszer automatikusan telepíti a célgyűjtemény ügyfélszámítógépein.  
-   Az automatikus központi telepítési szabályhoz kapcsolódó központi telepítések bármikor engedélyezhetők és letilthatók.  

Az automatikus központi telepítési szabály létrehozása után további központi telepítéseket is hozzáadhat a szabályhoz. Ennek segítségével egyszerűbben felügyelheti a különböző frissítések különböző gyűjteményekbe történő központi telepítését. Minden egyes új központi telepítés rendelkezik az összes funkcióval, és a központi telepítés figyelésének lehetőségével. A hozzáadott új központi telepítések:  

-   Ugyanazt a frissítési csoportot és csomagot használják, amelyet a rendszer az ADR első futásakor létrehoz.  
-   Különböző gyűjteményeket adhatnak meg.  
-   Egyedi központi telepítési tulajdonságokat támogatnak, beleértve:  
   -   aktiválás ideje,  
   -   határidő,  
   -   végfelhasználói felület megjelenítése vagy elrejtése,  
   -   a központi telepítéshez tartozó külön riasztások.  

Részletes útmutató: [szoftverfrissítések automatikus központi telepítése](automatically-deploy-software-updates.md)

<!-- ###  <a name="BKMK_ClientCache"></a> Client cache setting  
The Configuration Manager client downloads the content for required software updates to the local client cache soon after it receives the deployment. However, the client waits to download the content until after the **Software available time** setting for the deployment. The client does not download software updates in optional deployments (deployments that do not have a scheduled installation deadline) until the user manually starts the installation. When the configured deadline passes, the software updates client agent performs a scan to verify that the software update is still required, then the software updates client agent checks the local cache on the client computer to verify that the software update source file is still available, and then installs the software update. If the content was deleted from the client cache to make room for another deployment, the client downloads the software updates to the cache. Software updates are always downloaded to the client cache regardless of the configured maximum client cache size. For other deployments, such as applications or packages, the client only downloads content that is within the maximum cache size that you configure for the client. Cached content is not automatically deleted, but it remains in the cache for at least one day after the client used that content.  -->


 <!-- For more information about the deployment process, see [Software update deployment process](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).  -->

