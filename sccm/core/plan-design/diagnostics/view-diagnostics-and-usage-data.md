---
title: "Diagnosztikai adatok megtekintése |} Microsoft Docs"
description: "Győződjön meg arról, hogy a System Center Configuration Manager hierarchia nem bizalmas információkat tartalmaznak a diagnosztikai és használati adatok megtekintéséhez."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 0932e2b2a4f3e13c35d6b7b0446083f1c233ce03
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>A System Center Configuration Manager diagnosztikai és használati adatainak megtekintése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Diagnosztikai és használati adatokat megtekintheti annak ellenőrzéséhez, hogy megtalálható-e a bizalmas vagy azonosításra alkalmas adatokat a System Center Configuration Manager hierarchiából. Telemetriai adatok összegzi és tárolja a **TEL_TelemetryResults** tábla a Helyadatbázis és használhatóságot és hatékonyságot kell formátumú. Bár a következő beállításokat, egy betekintést nyújt a pontos adatok küldése a Microsoftnak, azok nem feltétlenül más célra, például az adatok elemzésére szolgáló.  

A következő SQL-parancs használatával tekintheti meg a tábla tartalmát, és a pontos küldött adatok megjelenítése. (Emellett exportálhatja ezeket az adatokat egy szövegfájlba.):  

-   **Válassza ki \* a TEL_TelemetryResults**  

> [!NOTE]  
>  Az 1602-es verzió telepítése előtt van-e a tábla tárolja a telemetriai adatok **TelemetryResults**.  

Ha a szolgáltatáskapcsolódási pont offline módban van, a szolgáltatáskapcsolati eszköz segítségével exportálhatja az aktuális diagnosztikai és használati adatokat egy vesszővel tagolt (CSV) fájl. Futtassa a szolgáltatáskapcsolódási eszközt a szolgáltatáskapcsolódási pont a használatával a **-exportálása** paraméter.  

##  <a name="bkmk_hashes"></a>Egyirányú kivonatok  
Egyes adatokat véletlenszerű alfanumerikus karakterekből álló karakterláncok áll. Configuration Manager használ az SHA-256 algoritmus, amely egyirányú kivonatokat használ az győződjön meg arról, hogy nem gyűjtünk potenciálisan bizalmas adatokat. Az algoritmus ahol továbbra is használható a összefüggések keresésére és összehasonlításra állapotban hagyja az adatokat. Például a helyadatbázisban lévő táblák nevének gyűjtése, helyett egy egyirányú kivonatot rögzített minden tábla neve. Ez biztosítja, hogy bármilyen egyéni táblaneveket, hogy a létrehozott vagy a termék bővítmények lévő többi nem láthatók. Azt, hogy küldje el a termékben alapértelmezés szerint, és hasonlítsa össze a termék alapértelmezett az adatbázisséma eltérése megállapításához két lekérdezések eredményeit SQL-táblanevek ugyanilyen egyirányú kivonatai majd végezhet. Ezt később az SQL-séma módosításait igénylő frissítések fejlesztéséhez használjuk fel.  

A nyers adatok megtekintésekor egy közös kivonatolt érték jelenik meg az egyes adatsorokban. Ez az a hierarchia azonosítója. Ezzel a kivonatolt értékkel annak biztosítására szolgál, hogy adatok visszamenőleges korrelációban állnak ugyanahhoz a hierarchiához az ügyfél vagy a forrás azonosítása nélkül.  

#### <a name="to-see-how-the-one-way-hash-works"></a>Az egyirányú kivonat működésének megjelenítéséhez  

1.  A hierarchia azonosítója lekéréséhez futtassa a következő SQL-utasítást az SQL Management Studio, a Configuration Manager adatbázisban: **válassza ki a [dbo]. [ fnGetHierarchyID]\(\)**  

2.  Használja a következő Windows PowerShell-parancsfájlt az adatbázistól kapott GUID egyirányú kivonatát. A kivonatot összehasonlíthatja a nyers adatok között található hierarchiaazonosítóval, és megállapíthatja, hogyan lettek elrejtve ezek az adatok.  

    ```  
    Param( [Parameter(Mandatory=$True)] [string]$value )  
      $guid = [System.Guid]::NewGuid()  
      if( [System.Guid]::TryParse($value,[ref] $guid) -eq $true ) {  
      #many of the values we hash are Guids  
      $bytesToHash = $guid.ToByteArray()  
    } else {  
      #otherwise hash as string (unicode)  
      $ue = New-Object System.Text.UnicodeEncoding  
      $bytesToHash = $ue.GetBytes($value)   
    }  
      # Load Hash Provider (https://en.wikipedia.org/wiki/SHA-2)   
    $hashAlgorithm = [System.Security.Cryptography.SHA256Cng]::Create()    
    # Hash the input   
    $hashedBytes = $hashAlgorithm.ComputeHash($bytesToHash)              
    # Base64 encode the result for transport   
    $result = [Convert]::ToBase64String($hashedBytes)    
    return $result   
    ```  

