---
title: "Ajánlott hardver |} Microsoft Docs"
description: "Hardver-ajánlásokat segítséget túl az alapszintű üzembe helyezéséhez a System Center Configuration Manager környezet skálázása beolvasása."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5267f0af-34d3-47a0-9ab8-986c41276e6c
caps.latest.revision: 26
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8dac6df60b07461d6410d305723b3f03fb09fa16
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="recommended-hardware-for-system-center-configuration-manager"></a>A System Center Configuration Manager használatához ajánlott hardver

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbi javaslatokat iránymutatásként használva úgy méretezheti a System Center Configuration Manager-környezetet, több, mint a helyek, helyrendszerek és ügyfelek nagyon alapszintű központi telepítést. A javaslatok nem feltétlenül fedik le a helyek és hierarchiák minden lehetséges konfigurációját.  

 Olvassa el a következő szakaszok útmutatóként hardver, amely megfelel a terhelése ügyfelek és az alapértelmezett konfigurációjú a rendelkezésre álló Configuration Manager-szolgáltatásokat használó helyek tervezéséhez nyújtanak segítséget.  


##  <a name="bkmk_ScaleSieSystems"></a>Beléptetésihely-rendszerek  
 Ez a témakör javasolt hardverkonfigurációkat a Configuration Manager helyrendszerei a maximális számú ügyfél támogatására, és a legtöbb vagy az összes Configuration Manager-szolgáltatásokat használó telepítések. Központi telepítések, amelyek támogatják a kisebb, mint az ügyfelek maximális száma, és ne használja az összes rendelkezésre álló funkciót kevesebb számítógép-erőforrásokat lehet szükség. A teljes rendszer teljesítményét korlátozó tényezők közé általában a következők tartoznak, sorrendben:  

1.  Lemezek bemeneti/kimeneti teljesítménye  

2.  Igénybe vehető memória  

3.  CPU  

A legjobb teljesítmény érdekében használjon RAID 10 konfigurációt minden adatmeghajtóhoz, illetve 1-Gbps Ethernet-hálózaton.  

###  <a name="bkmk_ScaleSiteServer"></a>Helykiszolgálók  

|Önálló elsődleges hely|Processzor (magok)|Memória (GB)|A memóriafoglalás a SQL Server (%)|  
|-------------------------------|---------------|---------------|----------------------------------------|  
|Önálló elsődleges helykiszolgáló egy adatbázis helyszerepkörrel ugyanazon a kiszolgálón<sup>1</sup>|16|96|80|  
|Önálló elsődleges helykiszolgáló távoli helyadatbázissal|8|16|-|  
|Távoli adatbázis-kiszolgáló önálló elsődleges helyhez|16|72|90|  
|Egy adatbázis helyszerepkörrel ugyanazon a kiszolgálón a központi adminisztrációs hely kiszolgálóján<sup>1</sup>|20|128|80|  
|Központi adminisztrációs helykiszolgáló távoli helyadatbázissal|8|16|-|  
|Távoli adatbázis-kiszolgáló egy központi adminisztrációs helyhez|16|96|90|  
|Gyermek elsődleges helyek egy adatbázis helyszerepkörrel ugyanazon a kiszolgálón|16|96|80|  
|Gyermek elsődleges helykiszolgáló távoli helyadatbázissal|8|16|-|  
|Távoli adatbázis-kiszolgáló gyermek elsődleges helyhez|16|72|90|  
|Másodlagos hely kiszolgálója|8|16|-|  

 <sup>1</sup> a helykiszolgáló és az SQL Server ugyanazon a számítógépen van telepítve, ha a környezet támogatja-e a maximális [méretezés és skálázási számok](/sccm/core/plan-design/configs/size-and-scale-numbers) helyeken és ügyfeleken. Azonban ez a konfiguráció korlátozhatja [magas rendelkezésre állású lehetőség a System Center Configuration Manager](/sccm/protect/understand/high-availability-options), például egy SQL Server-fürtöt használ. A magasabb i/o-követelményeinek, amelyek szükségesek ahhoz, hogy támogatja az SQL Server és a Configuration Manager helykiszolgálón, ha mindkét szolgáltatás ugyanazon a számítógépen futtatja, mert azt is érdemes figyelembe venni, a konfiguráció használata egy távoli SQL Server-számítógépen, ha nagyobb telepítést.  

###  <a name="bkmk_RemoteSiteSystem"></a>Távoli helyrendszer-kiszolgálók  
 Az alábbi útmutatót az egyetlen helyrendszerszerepkörrel rendelkező számítógépek. Ha ugyanarra a számítógépre több helyrendszerszerepkört telepít, módosításokra lesz szükség.  

|Helyrendszerszerepkör|Processzor (magok)|Memória (GB)|Lemezterület (GB)|  
|----------------------|---------------|---------------|--------------------|  
|Felügyeleti pont|4|8|50|  
|Terjesztési pont|2|8|Szükség szerint, az operációs rendszer, és tárolja a központilag telepített tartalomhoz.|  
|Alkalmazáskatalógus webszolgáltatással és webhellyel a helyrendszer-kiszolgáló számítógépen|4|16|50|  
|Szoftverfrissítési pont<sup>1</sup>|8|16|Szükség szerint, az operációs rendszer, és központilag telepített frissítések tárolásához|  
|Minden egyéb helyrendszerszerepkör|4|8|50|  

 <sup>1</sup> szoftverfrissítési pontot futtató számítógépen az IIS-alkalmazáskészletek van szükség a következő beállításokat:  

-   Növelje a **WsusPool várólista hosszának** való **2000**.  

-   Növelje a **WsusPool privát memóriakorlátját** 4 időpontok, vagy állítsa az értékét **0** (korlátlan).  

###  <a name="bkmk_DiskSpace"></a>Szabad lemezterület a helyrendszerekhez  
 A lemezfoglalás és -konfiguráció fokozza a teljesítmény a Configuration Manager. Mivel minden egyes Configuration Manager-környezetben különböző, az értékek, amelyek megvalósítása eltérőek lehetnek a következőknek megfelelően.  

 A legjobb teljesítményhez mindegyik objektumot egy különálló, dedikált RAID kötetre helyezze el. Minden adatkötetnél (Configuration Manager és az adatbázisának fájljai) RAID 10 használata biztosítja a legjobb teljesítmény érdekében.  

|Adathasználat|Minimális lemezterület|25 000 ügyfél|50 000 ügyfél|100 000 ügyfél|150 000 ügyfél|700 000 ügyfél (központi adminisztrációs hely)|  
|----------------|------------------------|--------------------|--------------------|---------------------|---------------------|-----------------------------------------------------|  
|Operációs rendszer|Tekintse át az operációs rendszer útmutatóját.|Tekintse át az operációs rendszer útmutatóját.|Tekintse át az operációs rendszer útmutatóját.|Tekintse át az operációs rendszer útmutatóját.|Tekintse át az operációs rendszer útmutatóját.|Tekintse át az operációs rendszer útmutatóját.|  
|A Configuration Manager alkalmazás és a naplófájlok fájlok|25 GB|50 GB|100 GB|200 GB|300 GB|200 GB|  
|A helyadatbázis .mdf fájlja|25 000 ügyfelenként 75 GB|75 GB|150 GB|300 GB|500 GB|2 TB|  
|A helyadatbázis .ldf fájlja|25 000 ügyfelenként 25 GB|25 GB|50 GB|100 GB|150 GB|100 GB|  
|Átmeneti adatbázisfájlok (.mdf és .ldf)|Igény szerint|Igény szerint|Igény szerint|Igény szerint|Igény szerint|Igény szerint|  
|Tartalom (a terjesztési pontok megosztása)|Igény szerint<sup>1</sup>|Igény szerint<sup>1</sup>|Igény szerint<sup>1</sup>|Igény szerint<sup>1</sup>|Igény szerint<sup>1</sup>|Igény szerint<sup>1</sup>|  

 <sup>1</sup> a lemezterületre vonatkozó útmutatás nem tartalmazza a helykiszolgáló vagy terjesztési pontok tartalomtárában elhelyezett tartalomhoz szükséges helyet. További információ a tartalomtár tervezéséről: [A tartalomtár](../../../core/plan-design/hierarchy/the-content-library.md).  

 Az előző útmutatás kiegészítéseként a szükséges lemezterület tervezésekor vegye figyelembe a következő irányelveket:  

-   Minden ügyfél körülbelül 5 MB helyet igényel.  

-   Ha tervezi az kombinált méretének 25 – 30 százalékával a Helyadatbázis .mdf fájlja tervezése elsődleges hely átmeneti adatbázisa méretének. A tényleges méret lehet lényegesen kisebb vagy nagyobb – függ a helykiszolgáló teljesítményét, és a bejövő adatok mennyiségét rövid és a hosszú idő alatt.  

    > [!NOTE]  
    >  Ha egy helyen 50 000 vagy több ügyfelet, tervezi a négy vagy több ideiglenes adatbázis .mdf fájl használatát.  

-   A központi felügyeleti hely átmeneti adatbázisának mérete jellemzően sokkal kisebb, mint az elsődleges hely adatbázisának mérete.  

-   A másodlagos hely adatbázisának mérete a következők szerint korlátozódik:  

    -   Az SQL Server 2012 Express: 10 GB  

    -   Az SQL Server 2014 Express: 10 GB  

##  <a name="bkmk_ScaleClient"></a>Ügyfelek  
 Ez a témakör a javasolt hardverkonfigurációkat a számítógépek, amelyek a Configuration Manager ügyfélszoftver használatával felügyeli.  

### <a name="client-for-windows-computers"></a>Ügyfélprogram Windows rendszerű számítógépekhez  
 Windows rendszerű számítógépeken, amelyeket Ön kezel, a Configuration Managerrel, beleértve az embedded operációs rendszerek minimális követelményei a következők:  

-   **Processzor és memória:** A processzorra és a RAM vonatkozó követelményeket a számítógép operációs rendszere meg.  

-   **Lemezterület:** 500 MB szabad lemezterület, továbbá 5 GB ajánlott a Configuration Manager-ügyfél gyorsítótárában. Kisebb lemezterületre szükség, ha a Configuration Manager-ügyfél telepítéséhez testreszabott beállításokat használja:  

    -   Használja a CCMSetup parancssori tulajdonság/skipprereq elkerülése érdekében, hogy az ügyfél nem igényel fájlok telepítése. Futtasson például **CCMSetup.exe /skipprereq:silverlight.exe** Ha az ügyfél nem használni az Alkalmazáskatalógust.  

    -   A Client.msi SMSCACHESIZE tulajdonság használatával az alapértelmezett 5120 MB-nál kisebb méretű gyorsítótárfájl állítható be. A minimális méret 1 MB. Például a **CCMSetup.exe SMSCachesize=2** parancs egy 2 MB méretű gyorsítótárfájlt hoz létre.  

    További információk az ügyfél telepítési tulajdonságairól: [Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md).  

    > [!TIP]  
    >  Az ügyfélszoftver telepítése minimális lemezterülettel az olyan Windows Embedded-eszközök esetén hasznos, amelyek lemezterülete általában kisebb, mint a szokásos Windows-számítógépeké.  



 Az alábbiakban a minimális hardverkövetelmények választható funkcióihoz szükségesek a Configuration Manager alkalmazásban.  

-   **Operációs rendszer központi telepítéséhez:** 384 MB RAM  

-   **Szoftverközpont:** 500 MHz-es processzor  

-   **Távvezérlés:** Pentium 4 Hyper-threaded 3 GHz (egymagos) vagy hasonló Processzor legalább 1 GB RAM memóriával az optimális működés érdekében  

### <a name="client-for-linux-and-unix"></a>Ügyfél Linux és UNIX rendszeren  
 A Configuration Managerrel felügyelt Linux és UNIX rendszerű kiszolgálók minimális követelményei a következők.  

|Követelmény|Részletek|  
|-----------------|-------------|  
|Processzor és memória|A processzorra és a RAM vonatkozó követelményeket a számítógép operációs rendszere meg.|  
|Lemezterület|500 MB szabad lemezterület, továbbá 5 GB ajánlott a Configuration Manager-ügyfél gyorsítótárában.|  
|Hálózati kapcsolat|A Configuration Manager-ügyfél számítógépeinek felügyeletének engedélyezése a Configuration Manager helyrendszerei hálózati kapcsolattal kell rendelkeznie.|  

##  <a name="bkmk_ScaleConsole"></a>A Configuration Manager konzol  
 Az alábbi táblázatban követelményeit, minden a Configuration Manager konzolt futtató számítógépre.  

 **Minimális hardverkonfiguráció:**  

-   Intel i3 vagy hasonló processzor  

-   2 GB RAM  

-   2 GB szabad lemezterület  

|DPI-beállítás|Minimális felbontás|  
|-----------------|------------------------|  
|96 / 100%|1024 x 768|  
|120 /125%|1280 x 960|  
|144 / 150%|1600 x 1200-as|  
|196 / 200%|2500 x 1600|  

 **A PowerShell-támogatást:**  

 PowerShell-támogatás a Configuration Manager konzolt futtató számítógépen való telepítésekor a számítógépen kezelheti a Configuration Manager PowerShell-parancsmagok is futtathatja.

 - A PowerShell 3.0-s vagy újabb verzió esetén támogatott.

A PowerShell mellett támogatja a Windows Management Framework (WMF) 3.0-s vagy újabb verziója.   


##  <a name="bkmk_ScaleLab"></a>Laboratóriumi központi telepítések  
 Használja a következő minimális hardverkövetelményeket labor és tesztelési központi telepítések a Configuration Manager. Ezek az ajánlások összes helytípusra, legfeljebb 100 ügyféllel vonatkoznak:  

|Szerepkör|Processzor (magok)|Memória (GB)|Lemezterület (GB)|  
|----------|---------------|-------------------|-----------------------|  
|Hely- és adatbázis-kiszolgáló|2 - 4|7 - 12|100|  
|Helyrendszer kiszolgálója|1 - 4|2 - 4|50|  
|Ügyfél|1 - 2|1 - 3|30|  

