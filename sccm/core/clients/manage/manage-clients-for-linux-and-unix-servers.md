---
title: "Linux és UNIX rendszerű ügyfelek kezelésére |} Microsoft Docs"
description: "A Linux és UNIX rendszerű kiszolgálókon a System Center Configuration Manager ügyfelek kezelésére."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 689af6998d9454d76d060b89ca1365d328c08020
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Ügyfélszoftverek kezelése a Linux és UNIX rendszerű kiszolgálók a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha Ön kezeli a Linux és UNIX rendszerű kiszolgálókon a System Center Configuration Managerrel, konfigurálhatja a gyűjteményeket, karbantartási időszakokat és ügyfélbeállításokat a kiszolgálók kezeléséhez. Emellett, ha a Configuration Manager-ügyfél Linux és UNIX rendszerű nincs felhasználói felület, kényszerítheti az ügyfél az ügyfélházirend manuális lekérdezésére.

##  <a name="BKMK_CollectionsforLnU"></a> Collections of Linux and UNIX servers  
 Gyűjtemények segítségével kezelheti a csoportok a Linux és UNIX rendszerű kiszolgálók azonos módon gyűjtemények segítségével más ügyféltípusok kezelhető. A gyűjtemények közvetlen tagságú vagy lekérdezésalapú gyűjtemények, amelyek azonosítják az ügyféloldali operációs rendszerek, hardverkonfigurációk vagy az ügyfél további adatait, a helyadatbázisban tárolt lehetnek. A Linux és UNIX rendszerű kiszolgálókat tartalmazó gyűjteményekkel például többek között az alábbiakat kezelheti:  

-   Ügyfélbeállítások  

-   Szoftverek központi telepítése  

-   Karbantartási időszakok kényszerítése  

 Mielőtt az operációs rendszer vagy a terjesztési Linux vagy UNIX rendszerű ügyfél azonosíthatja, össze kell gyűjteni [Hardverleltár](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) az ügyféltől.  

 A Hardverleltár alapértelmezett ügyfélbeállításait az ügyfél a számítógép operációs rendszere információkat tartalmaznak. Az **Operációs rendszer** osztály **Felirat** tulajdonságával azonosíthatja egy adott Linux vagy UNIX rendszerű kiszolgáló operációs rendszerét.  

 Részletek futtató számítógépekkel kapcsolatos a Configuration Manager-ügyfél Linux és UNIX rendszerű az eszköz csomópont alatt az eszközök és megfelelőség munkaterületen a Configuration Manager konzolon. A Configuration Manager konzol eszközök és megfelelőség munkaterületen megtekintheti az egyes számítógépek operációs rendszerének nevét a **operációs rendszer** oszlop.  

 Alapértelmezés szerint a Linux és UNIX rendszerű kiszolgálók a **Minden rendszer** gyűjtemény tagjai. Azt javasoljuk, hogy csak a Linux és UNIX rendszerű kiszolgálók vagy azok egy részét tartalmazó egyéni gyűjtemények létrehozása. Ez lehetővé teszi a műveletek, például a szoftverek központi telepítése és hozzárendelése ügyfél beállításait, és a csoportok, például a számítógépeket, kezelheti, hogy pontosan tudja mérni a központi telepítés sikeres.   

 Linux és UNIX rendszerű kiszolgálók egy egyéni gyűjteményének létrehozásakor használja tagsági szabályok az Operációs rendszer attribútum Feliratot attribútumát tartalmazó lekérdezéseit is. További információ a gyűjtemények létrehozásáról: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../core/clients/manage/collections/create-collections.md).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Maintenance windows for Linux and UNIX servers  
 A Configuration Manager-ügyfél Linux és UNIX rendszerű kiszolgálók használatát támogatja [karbantartási időszakok](../../../core/clients/manage/collections/use-maintenance-windows.md). Ez a támogatás nem különbözik a Windows rendszerű ügyfelekétől.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Client settings for Linux and UNIX servers  
 Is [ügyfélbeállítások konfigurálása](../../../core/clients/deploy/configure-client-settings.md) , amelyek érvényesek a Linux és UNIX rendszerű kiszolgálók a ugyanúgy konfigurálhatók, más ügyfelek beállításai.  

 Alapértelmezés szerint a Linux és UNIX rendszerű kiszolgálókra az **Ügyfélügynök alapértelmezett beállításai** érvényesek. Is létrehozhat egyéni beállításokat, majd telepítheti őket az adott ügyfélgyűjteményekből.  

 Nincsenek csak a Linux és UNIX rendszerű ügyfelekre vonatkozó további ügyfélbeállítások. Egyes alapértelmezett ügyfélbeállítások azonban nem vonatkoznak a Linux és UNIX rendszerű ügyfelekre. A Linux és UNIX rendszerekhez készült ügyfél csak funkciókra alkalmaz beállításokat, hogy az támogatja-e.  

 Például egy egyéni ügyféleszköz-beállítást, amely lehetővé teszi, hogy és távvezérlési beállításokat konfigurál volna figyelmen kívül hagyja a Linux és UNIX kiszolgálók, a Linux és UNIX rendszerű ügyfél nem támogatja a távvezérlést.  

##  <a name="BKMK_PolicyforLnU"></a> Computer policy for Linux and UNIX servers  
 Az ügyfél Linux és UNIX rendszerű kiszolgálók rendszeresen lekérdezi a számítógép-házirendet a helyéről a kért konfigurációkról és központi telepítések keresése céljából.  

 A Linux vagy UNIX rendszerű kiszolgálón lévő ügyfél emellett a számítógép-házirend azonnali lekérdezésére is kényszeríthető. Ehhez használja **legfelső szintű** hitelesítő adatokkal a kiszolgálón a következő parancsot: **/opt/microsoft/configmgr/bin/ccmexec - rs házirend**  

 A számítógép-házirend lekérdezésének adatai bekerülnek a megosztott ügyfélnaplófájlba, az **scxcm.log**fájlba.  

> [!NOTE]  
>  A Configuration Manager-ügyfél Linux és UNIX rendszerű soha nem kér le vagy dolgoz fel felhasználói házirendet.  

##  <a name="BKMK_ManageLinuxCerts"></a> How to manage certificates on the client for Linux and UNIX  
 A Linux és UNIX rendszerekhez készült ügyfél telepítése után a **certutil** eszközzel frissítheti az ügyfelet új PKI-tanúsítvánnyal, illetve importálhatja a visszavont tanúsítványok új  listáját (CRL). Ha az ügyfél telepítése Linux és UNIX rendszerekhez készült, az eszköz kerül **/opt/microsoft/configmgr/bin/certutil**. 

 A tanúsítványok kezeléséhez minden ügyfélen futtassa a certutil eszközt az alábbi kapcsolók egyikével:  

|Beállítás|További információ|  
|------------|----------------------|  
|importPFX|Ezzel a kapcsolóval adhatja meg a tanúsítványt, amelyre le szeretné cserélni az ügyfél által jelenleg használt tanúsítványt.<br /><br /> Amikor **– importPFX**, is használnia kell a **-jelszó** paramétert a PKCS #12 fájlhoz tartozó jelszót.<br /><br /> A **-rootcerts** kapcsolóval adhat meg további főtanúsítványra vonatkozó követelményeket.<br /><br /> Példa: **certutil – importPFX &lt;a PKCS #12 tanúsítvány elérési útja >-jelszó &lt;tanúsítványjelszavas\> [-rootcerts &lt;tanúsítványok vesszővel tagolt listája >]**|  
|-importsitecert|Ezzel a kapcsolóval frissítheti a helykiszolgáló a felügyeleti kiszolgálón lévő aláíró tanúsítványát.<br /><br /> Példa: **certutil - importsitecert &lt;DER tanúsítvány elérési útja\>**|  
|-importcrl|Ezzel a kapcsolóval frissítheti az ügyfél CRL-listáját egy vagy több CRL-lista fájlelérési útjával.<br /><br /> Példa: **certutil - importcrl &lt;vesszővel elválasztott CRL elérési utat\>**|  

