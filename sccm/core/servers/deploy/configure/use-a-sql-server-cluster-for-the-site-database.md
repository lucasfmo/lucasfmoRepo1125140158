---
title: "SQL Server-fürt |} Microsoft Docs"
description: "SQL Server-fürtöt használ a System Center Configuration Manager Helyadatbázis futtatására. Támogatott beállítások kapcsolatos adatokat tartalmaz."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ce0d7fc5f3d1812c4d62e551661c0ef89707567b
ms.openlocfilehash: 53f119bbb1f8827a9c23c8b747840350bbb92790
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>A System Center Configuration Manager helyadatbázishoz SQL Server-fürt használatára

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 SQL Server-fürtöt a System Center Configuration Manager Helyadatbázis futtatására használhatja. A helyadatbázis az SQL Server-fürtökön támogatott egyetlen helyrendszerszerepkör.  

> [!IMPORTANT]  
>  Az SQL Server-fürtök beállítása sikeres támaszkodik dokumentáció és eljárások nyújtanak az SQL Server dokumentációs könyvtárában.  

 A fürtök támogathatja a feladatátvételt és a Helyadatbázis megbízhatóságát. Azonban ez nem nyújt további feldolgozási vagy terheléselosztási teljesítménynövekedést. Valójában akár teljesítménycsökkenés akkor fordulhat elő, mert a helykiszolgáló kell találnia az SQL Server-fürt aktív csomópontja, mielőtt csatlakozna a helyadatbázishoz.  

 A Configuration Manager telepítése előtt elő kell készítenie az SQL Server-fürt Configuration Manager támogatására. (Lásd a szakasz későbbi részében olvashat.)  

 A Configuration Manager a telepítés során a Windows a kötet árnyékmásolata szolgáltatás írója is telepítve a Microsoft Windows Server-fürt mindegyik fizikai számítógép-csomópontján. Ez a funkció támogatja a **helykiszolgáló biztonsági mentése** karbantartási feladatot.  

 A hely telepítése után a Configuration Manager ellenőrzi a fürt csomópontjának változásait minden órában. A Configuration Manager automatikusan kezeli a találhatók (például a csomópontok feladatátvételét hiba, vagy az SQL Server-fürt új csomópontjának hozzáadása) a Configuration Manager összetevő telepítését befolyásoló módosításokat.  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>Támogatott beállítások SQL Server feladatátvevő fürt segítségével

Az alábbi lehetőségek a helyadatbázishoz használt SQL Server feladatátvevő fürtök támogatottak:

-   Egypéldányos fürt  

-   Többpéldányos konfiguráció  

-   Több aktív csomópont  

-   Elnevezett vagy egy alapértelmezett példány  

Vegye figyelembe a következő előfeltételek teljesülését:  

-   A helyadatbázisnak a helykiszolgálóhoz képest távol kell lennie. (A fürt nem tartalmazhatja a helyrendszer-kiszolgálót.)  

-   Hozzá kell adnia a helykiszolgáló számítógépfiókját a fürt összes kiszolgálójának a helyi rendszergazdák csoportjának.  

-   Kerberos-hitelesítés támogatásához a **TCP/IP** hálózati kommunikációs protokollt engedélyezni kell mindegyik SQL Server-fürt csomópontjának hálózati kapcsolathoz. A**nevesített csövek** nem szükségesek, de használhatók a Kerberos-hitelesítés problémainak megoldásához. A hálózati protokoll beállításai a **SQL Server Configuration Manager**a **SQL Server hálózati konfigurációja**.  

-   Ha PKI használata esetén lásd: PKI-tanúsítványkövetelmények a Configuration Manager számára az adott tanúsítványkövetelményeket SQL Server-fürtöt a Helyadatbázis használatakor.  

Vegye figyelembe a következő korlátozások vonatkoznak:  

-   **Telepítés és konfiguráció:**  

    -   A másodlagos helyek nem használhatnak SQL Server-fürtöt.  

    -   Ha SQL Server-fürtöt ad meg, a helyadatbázisokhoz nincs lehetőség nem alapértelmezett fájlhelyek választására.  

-   **SMS-szolgáltató**  

    -   Az SMS-szolgáltató példányát telepíti, az SQL Server-fürtöt, vagy egy fürtözött SQL Server-csomópontként futtató számítógépen nem támogatott.  

-   **Adatreplikációs beállítások:**  

    -   Ha használja, akkor **elosztott nézetek**, a helyadatbázist tároló SQL Server-fürt nem használhatja.  

-   **Biztonsági másolat és helyreállítás:**  

    -   A Configuration Manager nem támogatja a Data Protection Manager (DPM) biztonsági mentés az SQL Server-fürtöt, amely megnevezett példányt használ. Azt, a DPM biztonsági mentése azonban támogatja az SQL Server alapértelmezett példányát használó SQL Server fürtön.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>Fürtözött SQL Server-példány előkészítése a helyadatbázishoz  

Az alábbiakban a Helyadatbázis elkészítése érdekében végezze el a fő feladatokat:

-   Hozza létre a virtuális SQL Server-fürtöt, amely a helyadatbázist fogja tárolni egy meglévő Windows Server-fürt környezetében. Telepítse és állítsa be az SQL Server-fürtöt, az adott SQL Server verziójának dokumentációjában talál lépéseit. Például ha az SQL Server 2008 R2 használ, tekintse meg [egy SQL Server 2008 R2 feladatátvevő fürt telepítése](http://go.microsoft.com/fwlink/p/?LinkId=240231).  

-   Az SQL Server-fürt minden egyes számítógépen elhelyezhet egy fájlt minden olyan meghajtó, amelyen nincs szükség hely összetevőinek telepítése a Configuration Manager gyökérmappájában. A fájl neve kell **NO_SMS_ON_DRIVE.SMS**. Alapértelmezés szerint a Configuration Manager telepít néhány összetevőt minden fizikai csomópontra, mint a biztonsági mentés műveletek támogatásához.  

-   Vegye fel a helykiszolgáló számítógépfiókját a **Helyi rendszergazdák** csoportba a Windows Server-fürt minden csomópont-számítógépén.  

-   A virtuális SQL Server-példányban rendelje hozzá a **sysadmin** SQL Server-szerepkört ahhoz a felhasználói fiókhoz, a Configuration Manager telepítő fog futni.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>Új hely telepítése fürtözött SQL Server-kiszolgálóval  
 Egy fürtözött helyadatbázist használó hely telepítéséhez futtassa a Configuration Manager telepítő a következő normál folyamatát követően telepíti a helyet, és vegye figyelembe a következő módosítást:  

-   Az **Adatbázis-információ** lapon adja meg a helyadatbázist tároló virtuális SQL Server-példány nevét. A virtuális példány felülírja az SQL Servert futtató számítógép nevét.  

    > [!IMPORTANT]  
    >  Amikor megadja a virtuális SQL Server-fürt példányának nevét, ne a Windows Server-fürt által létrehozott virtuális Windows Server nevét adja meg. Ha a virtuális Windows Server nevet használja, a Helyadatbázis az aktív Windows Server-fürt csomópontjának helyi merevlemezére telepíti. Ez megakadályozza a sikeres feladatátvételt, ha az adott csomóponton hiba történik.  

