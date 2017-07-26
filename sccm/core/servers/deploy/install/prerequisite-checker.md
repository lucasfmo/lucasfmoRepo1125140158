---
title: "Az előfeltétel-ellenőrző |} Microsoft Docs"
description: "Ismerje meg, hogyan használható az előfeltétel-ellenőrző, amelyek blokkolhatják a hely vagy helyrendszer szerepkör telepítési problémák azonosítása és megoldása."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5cc318eaf097cb3cfbfde730f7573d27af25648
ms.openlocfilehash: f0d44f82a0b6068f8cecc5808774677eccb0f8d9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>Az előfeltétel-ellenőrző a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Mielőtt a telepítővel telepítené vagy frissítené a System Center Configuration Manager-hely, illetve előtt helyrendszerszerepkört egy új kiszolgálóra telepítette, használhatja az ennek az önálló alkalmazásnak (**Prereqchk.exe**) használja a Configuration Manager verziója, amelyet a kiszolgáló felkészültségének ellenőrzése. Az előfeltétel-ellenőrző segítségével egy helyen vagy a helyrendszer-szerepkör telepítéshez megakadályozó problémák azonosítása és megoldása.  

> [!NOTE]  
>  Az előfeltétel-ellenőrző mindig fut a telepítés részeként.  

Alapértelmezés szerint az előfeltétel-ellenőrző futtatásakor:  

-   Ellenőrzi azt a kiszolgálót, amelyen futtatják.  
-   A helyi számítógép üzemeltet-e helykiszolgálót, és csak a helyre vonatkozó ellenőrzéseket futtatja.  
-   Ha egyetlen meglévő helyet észlel, az összes előfeltételként szereplő szabály futnak.  
-   Ellenőrzi a szabályokat, győződjön meg arról, hogy a szoftver, és telepítve vannak a telepítéshez szükséges beállításokat. Akkor lehet, hogy szükséges szoftverek szükséges további konfigurációs vagy szoftverfrissítéseket, az előfeltétel-ellenőrző nem ellenőrzi.  
-   Azt naplózza az eredményeket a **ConfigMgrPrereq.log** fájl a számítógép rendszermeghajtóján. A naplófájlt, amely nem jelenik meg az felületen további adatokat tartalmazhatnak.  

Ha az előfeltétel-ellenőrző futtassa a parancsot a parancssorba, és parancssori kapcsolókat:  

-   Az előfeltétel-ellenőrző csak a helykiszolgáló vagy a parancssorban megadott helyrendszerek társított ellenőrzéseket hajtja végre.  
-   Ellenőrizze a távoli számítógépet, a felhasználói fiók a távoli számítógépre rendszergazdai jogosultságokkal kell rendelkeznie.  

Az előfeltétel-ellenőrző által végrehajtott ellenőrzések kapcsolatos további információkért lásd: [előfeltétel listája ellenőrzi a System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

## <a name="copy-prerequisite-checker-files-to-another-computer"></a>Előfeltétel-ellenőrző fájljainak másolása másik számítógépre  

1.  A Windows Intézőben nyissa meg az alábbi helyek egyikét:  

    -   **&lt;*Configuration Manager telepítési adathordozójáról*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*A Configuration Manager telepítési útvonala*\>\BIN\X64**  

2.  A következő fájlokat másolja a másik számítógépen található célmappába:  

    -   Prereqchk.exe  
    -   Prereqcore.dll  
    -   Basesql.dll  
    -   Basesvr.dll  
    -   Baseutil.dll  

##  <a name="run-prerequisite-checker-with-default-checks"></a>Előfeltétel-ellenőrzés futtatása az alapértelmezett ellenőrzésekkel  

1.  A Windows Intézőben nyissa meg az alábbi helyek egyikét:  

    -   **&lt;*Configuration Manager telepítési adathordozójáról*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*A Configuration Manager telepítési útvonala*\>\BIN\X64**  

2.  Futtatás **prereqchk.exe** előfeltétel-ellenőrző indításához.   
    Az előfeltétel-ellenőrző észlel helyet, és ha található, a frissítési készültségének ellenőrzi. Ha nincs hely található, az összes ellenőrzést végrehajtja. A **helytípus** oszlop információkat nyújt azokról a helykiszolgálóról vagy helyrendszerről, amelyhez a szabály tartozik.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>Futtatja az előfeltétel-ellenőrzőt a parancssorból az összes alapértelmezett ellenőrzéssel  

1.  Nyisson meg egy parancssori ablakot, és váltson át az alábbi helyek egyikét:  

    -   **&lt;*Configuration Manager telepítési adathordozójáról*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*A Configuration Manager telepítési útvonala*\>\BIN\X64**  

2.  Adja meg **prereqchk.exe Local** előfeltétel-ellenőrző elindításához és az összes előfeltétel-ellenőrzés a kiszolgálón.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>Futtatja az előfeltétel-ellenőrzőt a parancssorból a lehetőségek  

1.  Nyisson meg egy parancssori ablakot, és váltson át az alábbi helyek egyikét:  

    -   **&lt;*Configuration Manager telepítési adathordozójáról*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*A Configuration Manager telepítési útvonala*\>\BIN\X64**  

2.  Adja meg **prereqchk.exe** egy vagy több, az alábbi parancssori kapcsolók igény szerinti hozzáadásával.  

    Például egy elsődleges hely ellenőrzéséhez használhatja a következő:  

       **prereqchk.exe [/ noui] / PRI SQL &lt;SQL Server teljes Tartományneve\> /SDK &lt;az SMS-szolgáltató teljes Tartományneve\> [/ JOIN &lt;központi adminisztrációs hely teljes Tartományneve\>] [/MP &lt;felügyeleti pont teljes Tartományneve\>] [/DP &lt;terjesztési pont teljes Tartományneve\>]**  

    **Központi adminisztrációs hely kiszolgálóján:**  

    -   **/ NOUI**  

         Nem szükséges. A felhasználói felület megjelenítése nélkül indítja el az előfeltétel-ellenőrző. A parancssorban meg kell adnia ezt a beállítást, semmilyen egyéb kapcsoló előtt.  

    -   **/ CAS**  

         Kötelező. Ellenőrzi, hogy a helyi számítógép megfelel-e a követelményeknek, a központi adminisztrációs hely.  

    -   **/ SQL &lt;* SQL Server teljes Tartományneve*>**  

         Kötelező. A teljesen minősített tartománynevét (FQDN) használatával ellenőrzi, hogy a megadott számítógép megfelel-e a Configuration Manager Helyadatbázis futtatására SQL Serverrel szemben támasztott követelményeknek.  

    -   **/ SDK &lt;* SMS-szolgáltató teljes Tartományneve*>**  

         Kötelező. Ellenőrzi, hogy a megadott számítógép megfelel-e a követelmények az SMS-szolgáltatót.  

    -   **/ Ssbport**  

         Nem szükséges. Ellenőrzi, hogy olyan érvényes tűzfalkivétel érvényben engedélyezi a kommunikációt az SQL Server Service Broker (SSB) porton. Az alapértelmezett SSB-port a 4022-es.  

    -   **InstallDir &lt;* Configuration Manager telepítési útvonala*>**  

         Nem szükséges. A minimális lemezterület a hely telepítési követelményeinek ellenőrzése.  

    **Elsődleges hely kiszolgálója:**  

    -   **/ NOUI**  

        Nem szükséges. A felhasználói felület megjelenítése nélkül indítja el az előfeltétel-ellenőrző. A parancssorban meg kell adnia ezt a beállítást, semmilyen egyéb kapcsoló előtt.  

    -   **/ PRI**  

         Kötelező. Ellenőrzi, hogy a helyi számítógép megfelel-e az elsődleges helyre vonatkozó követelmények.  

    -   **/ SQL &lt;* SQL Server teljes Tartományneve*>**  

         Kötelező. Ellenőrzi, hogy a megadott számítógép megfelel-e a Configuration Manager Helyadatbázis futtatására SQL Serverrel szemben támasztott követelményeknek.  

    -   **/ SDK &lt;* SMS-szolgáltató teljes Tartományneve*>**  

         Kötelező. Ellenőrzi, hogy a megadott számítógép megfelel-e a követelmények az SMS-szolgáltatót.  

    -   **/ JOIN &lt;* központi adminisztrációs hely teljes Tartományneve*>**  

         Nem szükséges. Ellenőrzi, hogy a helyi számítógép megfelel-e a központi adminisztrációs hely kiszolgálójához való kapcsolódás követelményeinek.  

    -   **/MP &lt;* felügyeleti pont teljes Tartományneve*>**  

         Nem szükséges. Ellenőrzi, hogy a megadott számítógép megfelel a felügyeleti pont helyrendszerszerepkörét futtatja. Ez a beállítás csak akkor támogatott, használja a **/PRI** lehetőséget.  

    -   **/DP &lt;* terjesztési pont teljes Tartományneve*>**  

         Nem szükséges. Ellenőrzi, hogy a megadott számítógép megfelel-e a terjesztési pont helyrendszer-szerepkör követelményei. Ez a beállítás csak akkor támogatott, használja a **/PRI** lehetőséget.  

    -   **/ Ssbport**  

         Nem szükséges. Ellenőrzi, hogy olyan érvényes tűzfalkivétel érvényben engedélyezi a kommunikációt az SSB-porton. Az alapértelmezett SSB-port a 4022-es.  

    -   **InstallDir &lt;* Configuration Manager telepítési útvonala*>**  

         Nem szükséges. A minimális lemezterület a hely telepítési követelményeinek ellenőrzése.  

    **Másodlagos hely kiszolgálóján:**  

    -   **/ NOUI**  

         Nem szükséges. A felhasználói felület megjelenítése nélkül indítja el az előfeltétel-ellenőrző. A parancssorban meg kell adnia ezt a beállítást, semmilyen egyéb kapcsoló előtt.  

    -   **/ SEC &lt;* másodlagos hely kiszolgálójának teljes Tartománynevét*>**  

         Kötelező. Ellenőrzi, hogy a megadott számítógép megfelel a másodlagos hely.  

    -   **/ INSTALLSQLEXPRESS**  

         Nem szükséges. Ellenőrzi, hogy az SQL Server Express telepíthető a megadott számítógépen.  

    -   **/ Ssbport**  

         Nem szükséges. Ellenőrzi, hogy olyan érvényes tűzfalkivétel érvényben engedélyezi a kommunikációt az SSB porton. Az alapértelmezett SSB-port a 4022-es.  

    -   **/ Sqlport**  

         Nem szükséges. Ellenőrzi, hogy olyan érvényes tűzfalkivétel érvényben engedélyezi a kommunikációt az SQL Server portja, és hogy a port nincs használatban, az SQL Server másik nevesített példánya. Az alapértelmezett port a 1433-as számú.  

    -   **InstallDir &lt;* Configuration Manager telepítési útvonala*>**  

         Nem szükséges. A minimális lemezterület a hely telepítési követelményeinek ellenőrzése.  

    -   **/ Szükséges SOURCEDIR könyvtárat**  

         Nem szükséges. Ellenőrzi, hogy a másodlagos hely számítógépfiókjának hozzáférhet-e a mappát, amelyet a telepítő forrásfájljait.  

   **A Configuration Manager konzol:**  

    -   **/ Adminui**  

         Kötelező. Ellenőrzi, hogy a helyi számítógép megfelel-e a Configuration Manager telepítésének követelményeit.  

3.  Az előfeltétel-ellenőrző felhasználói felületén, az előfeltétel-ellenőrző létrehoz egy listát, az észlelt problémákat a **az előfeltétel-ellenőrzés** szakasz.  

    -   Kattintson a megfelelő elemre a listában a probléma megoldásával kapcsolatos részletekért.  
    -   Fel kell oldania a lista összes elemének, amelyek rendelkeznek egy **hiba** állapota a helykiszolgáló, helyrendszer vagy Configuration Manager konzol telepítése előtt.  
    -   Is megnyithatja a **ConfigMgrPrereq.log** tekintse át az előfeltétel-ellenőrző eredményeit a rendszermeghajtó gyökérmappájában található fájl. A naplófájl az előfeltétel-ellenőrző felhasználói felületen meg nem jelenített további adatokat tartalmazhatnak.  

