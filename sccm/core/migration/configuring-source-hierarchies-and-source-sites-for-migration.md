---
title: "Az áttelepítés forráshierarchiái |} Microsoft Docs"
description: "Konfigurálja a forráshierarchiák és Forráshelyek, áttelepítheti az adatokat a System Center Configuration Manager környezethez."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c5a58d79f81ccdf19ad88dc932e3a52eac2c18ab
ms.openlocfilehash: 80c43ab93ee5a2de6bf8d7993dfd46f0005d2df8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>Forráshierarchiák és Forráshelyek System Center Configuration Manager az áttelepítés konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ahhoz, hogy az adatoknak a System Center Configuration Manager környezetben, konfigurálnia kell a Configuration Manager támogatott forráshierarchia és egy vagy több forráshely abban a hierarchiában, amely az áttelepíteni kívánt adatokat tartalmazza.  

> [!NOTE]  
>  Az áttelepítéshez a műveletek a célhierarchiában a legfelső szintű helyén futnak. Ha az áttelepítés konfigurálását elsődleges alárendelt helyhez kapcsolódó Configuration Manager-konzol használata esetén, és a konfigurációját, és a központi felügyeleti helyre replikálódjék, kezdet, amíg kell, majd replikálja az állapot vissza az elsődleges hely, amelyhez csatlakoznak a.  

 Segítségével információkat és eljárásokat az alábbi szakaszok a forráshierarchia megadásához és további Forráshelyek felvételéhez. Ezek az eljárások befejezése után hozzon létre áttelepítési feladatokat, és indítsa el az adatokat a forráshierarchiából a célhierarchiába áttelepítendő.  

-   [Az áttelepítés forráshierarchiájának megadásához](#BKBM_ConfigSrcHierarchy)  

-   [További Forráshelyek kiválasztása a forráshierarchiából](#BKBM_ConfigSrcSites)  

##  <a name="BKBM_ConfigSrcHierarchy"></a>Az áttelepítés forráshierarchiájának megadásához  
 Telepítse át az adatokat a célhierarchia, meg kell adnia a támogatott forráshierarchiát, amely az áttelepíteni kívánt adatokat tartalmaz. Alapértelmezés szerint a hierarchia legfelső szintű helye válik a forráshierarchia forráshelyévé. Ha telepít át, a Configuration Manager 2007-hierarchiából, majd állíthatja be az áttelepítéshez további forráshelyeket Miután adatokat gyűjtött a kezdeti forráshelyről. Ha a System Center 2012 Configuration Manager vagy a System Center Configuration Manager hierarchiából telepít át, Önnek nincs át adatokat a forráshierarchiában további forráshelyeket beállításához. Ez azért, mert a Configuration Manager ezen verziói olyan megosztott adatbázist, amely elérhető a forráshierarchia legfelső szintű helyén. A megosztott adatbázis tartalmaz minden olyan információt, amit áttelepíthet.  

 Az alábbi eljárásokkal áttelepítés forráshierarchiájának megadásához és a Configuration Manager 2007 hierarchia további Forráshelyek kiválasztásához.  

 Ezzel az eljárással futtassa a Configuration Manager konzolt, amely csatlakozik a célhierarchiában:  

### <a name="to-configure-a-source-hierarchy"></a>A forráshierarchia konfigurálása   

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A **Felügyelet** munkaterületen bontsa ki az **Áttelepítés**csomópontot, majd kattintson a **Forráshierarchia**lehetőségre.  

3.  Az a **Home** lap a **áttelepítési** csoportjában kattintson a **forráshierarchia megadása**.  

4.  Az a **forráshierarchia megadása** párbeszédpanelen a **forráshierarchia**, jelölje be **új forráshierarchia**.  

5.  A **legmagasabb szintű Configuration Manager helykiszolgáló**, adja meg a nevét vagy IP-címét a támogatott forráshierarchia legfelső szintű helyén.  

6.  Adja meg a forráshely hozzáférési fiókjait, amelyek rendelkeznek a következő engedélyekkel:  

    -   Forráshelyfiók: **Olvasási** engedély a forráshierarchia megadott legfelső szintű helyének SMS-szolgáltatóhoz. Terjesztési pont megosztását és a frissítések megkövetelése **módosítás** és **törlése** engedéllyel a helyhez a forráshierarchiában.

    -   Forráshelyi adatbázisfiók: **Olvasási** és **Execute** engedély a forráshierarchia megadott legfelső szintű helyének SQL Server adatbázisához.  

     Ha számítógépi fiók használatát adja meg, a Configuration Manager a célhierarchia legfelső szintű helyének számítógépi fiókját használja. Ezt a lehetőséget, győződjön meg arról, hogy ez a fiók tagja-e a biztonsági csoport **elosztott COM-felhasználók** a tartományban, ahol a forráshierarchia legfelső szintű helyén található.  

7.  Terjesztési pontoknak a forrás és cél közti megosztásához jelölje be a **engedélyezése a terjesztési pont megosztását a forráshely kiszolgálója számára** jelölőnégyzetet. Ha nem engedélyezi a terjesztési pont megosztását, végezhet, azzal hogy szerkeszti a hitelesítő adatok a forráshely után adatok gyűjtése befejeződött.  

8.  A konfiguráció mentéséhez kattintson az **OK** gombra. Ekkor megnyílik a **adatgyűjtési állapot** párbeszédpanelt, és automatikusan elindul az adatgyűjtés.  

9. Ha az adatgyűjtés befejezésekor kattintson **bezárása** bezárásához a **adatgyűjtési állapot** párbeszédpanel és a konfigurálás befejezéséhez.  

##  <a name="BKBM_ConfigSrcSites"></a>További Forráshelyek kiválasztása a forráshierarchiából  
 A támogatott forráshierarchia konfigurálásakor a hierarchia legfelső szintű helye automatikusan forráshelyként van konfigurálva, és automatikusan adatgyűjtés erről a helyről. A következő művelet, amelyet a Configuration Manager a forráshierarchia által futtatott verziójától függ:  

-   A Configuration Manager 2007 verziójú forráshierarchia kezdeni az áttelepítést a kezdeti forráshelyről, vagy állítsa be további Forráshelyek kiválasztása a forráshierarchiából a kezdeti forráshelyen az adatgyűjtés befejeződése után. Telepítse át az adatokat, amelyeket csak egy alárendelt helyről, állítsa be további Forráshelyek kiválasztásához a Configuration Manager 2007 hierarchia. Például előfordulhat, hogy állítsa be további forráshelyeket a forráshierarchiában egy alárendelt helyen jön létre és nem áll rendelkezésre a forráshierarchia legfelső helyéről áttelepíteni kívánt tartalomra vonatkozó adatgyűjtést.  

-   A System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiát nem kell további Forráshelyek konfigurálására. Ez azért, mert a Configuration Manager ezen verziói olyan megosztott adatbázist, amely elérhető a forráshierarchia legfelső szintű helyén. A megosztott adatbázis minden olyan információt, hogy telepíthet át a forráshierarchiában a hely összes rendelkezik. Így az áttelepíthető adatok elérhetők a forráshierarchia legfelső szintű helyről.  

Ha további Forráshelyek konfigurálása a Configuration Manager 2007 verziójú forráshierarchia, konfigurálnia kell a kiegészítő forráshelyeket a forráshierarchiában felülről lefelé a. Egy fölérendelt helyre kell konfigurálnia forráshelyként, bármelyik gyermekhelyét forráshelyként konfigurálása előtt.  

A következő eljárással olyan Configuration Manager 2007 forráshierarchiák kiegészítő forráshelyeinek konfigurálásához:  

### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>A forráshierarchiában további Forráshelyek kiválasztásához 

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A **Felügyelet** munkaterületen bontsa ki az **Áttelepítés**csomópontot, majd kattintson a **Forráshierarchia**lehetőségre.  

3.  Válassza ki a helyet, mint amit a forráshely konfigurálni szeretné.  

4.  A **Kezdőlap** **Forráshely** csoportjában kattintson a **Konfigurálás**elemre.  

5.  Az a **forráshely hitelesítő adatai** párbeszédpanelen a forráshely hozzáférési fiókjaiként adjon meg olyan fiókokat, amelyek rendelkeznek a következő engedélyekkel:  

    -   Forráshelyfiók: **Olvasási** engedély a forráshierarchia megadott legfelső szintű helyének SMS-szolgáltatóhoz. Terjesztési pont megosztását és a frissítések megkövetelése **módosítás** és **törlése** engedéllyel a helyhez a forráshierarchiában.  

    -   Forráshelyi adatbázisfiók: **Olvasási** és **Execute** engedély a forráshierarchia megadott legfelső szintű helyének SQL Server adatbázisához.  

    Ha számítógépi fiók használatát adja meg, a Configuration Manager a célhierarchia legfelső szintű helyének számítógépi fiókját használja. Ezt a lehetőséget, győződjön meg arról, hogy ez a fiók tagja-e a biztonsági csoport **elosztott COM-felhasználók** a tartományban, ahol a forráshierarchia legfelső szintű helyén található.  

6.  Terjesztési pontoknak a forrás és cél közti megosztásához jelölje be a **engedélyezése a terjesztési pont megosztását a forráshely kiszolgálója számára** jelölőnégyzetet. Ha nem engedélyezi a terjesztési pont megosztását, végezhet, azzal hogy szerkeszti a hitelesítő adatok a forráshely után adatok gyűjtése befejeződött.  

7. A konfiguráció mentéséhez kattintson az **OK** gombra. Ekkor megnyílik a **adatgyűjtési állapot** párbeszédpanelt, és automatikusan elindul az adatgyűjtés.  

8.  Ha az adatgyűjtés befejezésekor kattintson **Bezárás** a konfigurálás befejezéséhez.  

