---
title: "Konfigurációs adatok importálása |} Microsoft Docs"
description: "Konfigurációs adatok importálása, ha kabinetfájlban formátumban van tartalmazott, és a támogatott szolgáltatás modellezési nyelvi séma megfelelő."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 60d0642618a3074fc50a848f1189f4d6559ca916
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>Konfigurációs adatok importálása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mellett alapkonfigurációk és konfigurációelemek létrehozása a System Center Configuration Manager-konzolon, importálhatja a konfigurációs adatokat, ha kabinetfájlban (.cab) formátumú fájlt, és a támogatott Service Modeling Language (SML) sémának megfelelő. A konfigurációs adatok importálása  

-   A Microsoft vagy más szoftvergyártó webhelyéről letöltött, bevált konfigurációkat tartalmazó adatok (konfigurációs csomagok).  

-   A System Center 2012 Configuration Manager és újabb verziók exportált konfigurációs adatokat.  

-   Konfigurációs adatok külsőleg létrehozott és, amely megfelel a SML sémának.  

 A System Center 2012 Configuration Manager helykiszolgálói szerepkör megfelelőségének kezelését segítő konfigurációs csomag példája itt található: [System Center 2012 Configuration Manager Configuration Pack](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all).  

Referenciakonfiguráció importálásakor a referenciakonfigurációban hivatkozott néhány vagy összes konfigurációelem is szerepelhet a kabinetfájlban. Az importálási folyamat során a Configuration Manager ellenőrzi, hogy a konfigurációelemeket, amelyeket a referenciakonfigurációban hivatkozott összes vagy is szerepelnek a következő kabinetfájl, vagy már létezik a Configuration Manager-hely. Az importálási folyamat sikertelen lesz, ha a Configuration Manager nem találja a konfigurációs adatok hivatkozó referenciakonfigurációt importál.  

Sikertelen lehet az importálási folyamat az alábbi esetekben is:  

-   A konfigurációs adatokat a konfigurációs adatokat, amelyek a Configuration Manager nem találja, vagy az adatbázisában, vagy maga a kabinetfájlban hivatkozik.  

-   A konfigurációs adatok már létezik azonos nevű és a konfigurációs adatok verziója a Configuration Manager adatbázisában, de a tartalom verziója eltérő.  

-   A konfigurációs adatok már megtalálható a tartalom verziója azonos a Configuration Manager adatbázis, de a kivonatoló számítás azonosítja, hogy különbözik.  

-   A konfigurációs adatok azonos nevű újabb verziója már létezik, vagy nemrég törölték a Configuration Manager adatbázisába.  

-   Többhelyes Configuration Manager-hierarchiában a konfigurációs adatok eredetileg egy szülőhelyről importálása. Az adatokat ugyanarról a helyről (és nem gyerekhelyről) kell frissíteni.  

### <a name="import-configuration-data"></a>Konfigurációs adatok importálása  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **Konfigurációelemek** vagy **Referenciakonfigurációk**
2.  Az a **Home** lap a **létrehozása** csoportjában kattintson a **konfigurációs adatok importálása**.  
3.  A **Konfigurációs adatok importálása varázsló** **Fájlok kiválasztása**lapján kattintson a **Hozzáadás**gombra, majd a **Megnyitás** párbeszédpanelen jelölje ki az importálni kívánt .cab fájlokat.  
4.  Válassza ki a **az importált alapkonfigurációk és konfigurációelemek új példányának létrehozása** jelölőnégyzetet, ha azt szeretné, hogy az importált konfigurációs adatok szerkeszthetők legyenek a, a Configuration Manager konzolon.  
5.  Az a **összegzés** lapján tekintse át a végrehajtandó műveleteket megnyílik, és fejezze be a varázslót.  

Az importált konfigurációs adatok megjelennek a **megfelelőségi beállítások** csomópontjának a **eszközök és megfelelőség** munkaterületen.  

