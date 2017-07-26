---
title: "Előzetes deklarálása IMEI- vagy iOS-sorozatszámokat eszközök |} Microsoft Docs"
description: "Az IMEI- vagy iOS sorozatszámmal rendelkező vállalati tulajdonú eszközök előzetes deklarálása."
ms.custom: na
ms.date: 03/24/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: 3
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6833951db27b227a3ca22925e9d9f4c3fc443fc
ms.openlocfilehash: e8606b8a9268a0a0668b75070cf35894f4794123
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Előzetes deklarálása IMEI- vagy iOS-sorozatszámokat rendelkező eszközök

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Vállalat által birtokolt eszközök azonosíthatja az állomás nemzetközi mobilkészülék-azonosító (IMEI) számokat vagy iOS-sorozatszámokat importálásával. Feltöltheti az eszközök IMEI-számának tartalmazó vesszővel tagolt (.csv) fájlt, vagy meg manuálisan is beírhatja az eszközadatokat.  Importált adatok állítja **tulajdonjogának** az eszközöket a **vállalati** elemnél. Intune-licencet a szolgáltatáshoz hozzáférő mindegyik felhasználóhoz továbbra is szükség.  

Vállalat által birtokolt iOS-eszközök sorozatszámokat feltöltésekor azokat egy vállalati regisztrációs profil kell megfeleltetni. Eszközök majd kell léptetni, vagy az Apple eszközregisztrációs program (DEP) vagy az Apple Configurator használatával ezek jelennek meg a vállalati tulajdonú.

## <a name="how-to-predeclare-corporate-owned-devices"></a>A vállalat által birtokolt eszközök előzetes deklarálása hogyan

1.    Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **minden céges eszköz** > **eszközök Predeclared**.

2.  Kattintson a **Predeclared eszközök létrehozása**. Megnyílik a Predeclared eszközök létrehozása varázsló.

3.    Válassza ki, hogyan szeretné eszközadatokat hozzáadása:

     -    **IMEI vagy sorozatszámokat és eszközadatokat tartalmazó CSV-fájl feltöltése**

        Ezt a lehetőséget, kattintson a **Tallózás** adhatja meg a vállalat által birtokolt eszközök előzetes deklarálása információt tartalmazó .csv fájlt. A .csv fájl megfelelően kell formázni. További információkért lásd: [.csv fájlok feltöltése formátum](#format-for-uploading-csv-files).

     -    **IMEI vagy sorozatszámok és eszközadatok manuális felvétele**

        Manuálisan adja meg az adatokat, írja be az IMEI-szám vagy iOS sorozatszám, valamint az eszközök adatait. A folytatás előtt javítsa ki a semmilyen hiba vagy figyelmeztetés.

    Kattintson a **Tovább** gombra.

4. Ha egy CSV-fájlt töltött fel, tekintse át a fájl importálása eredményét. Ha egy eszköz száma korábban importált, Configuration Manager megjelenít-e az eszközöket és a helyettesítő **részletek**. Válassza ki a eszközöket, amelynek részleteit szeretné felülírni. Eszközadatok csak módosíthatják az eszköz azonosítása vagy sorozatszámot importintézkedésekkel.

  Ha úgy döntött, hogy manuálisan adja meg, töltse ki az eszközök előzetes deklarálása kívánt űrlapot.

  A folytatáshoz kattintson a **Tovább** gombra.

4. Ha a lista tartalmazza iOS-sorozatszámokat, jelölje be a **hozzárendelendő regisztrációs profil** rendelkezésre álló profilok, és kattintson a listájáról **következő**.

5. Kattintson a **következő** tekintse át a részletes adatait, majd **következő** be újra az adatok feltöltésére.

6. Kattintson a **Bezárás** befejezéséhez.

## <a name="format-for-uploading-csv-files"></a>Formátum .csv fájlok feltöltése

Az eszközök imei-Azonosítót vagy sorozatszámot azonosítására használt csv-fájlt kell rendelkeznie a következő formátumban, amely útmutatást csak a megadott felső sorában kivéve. Minden egyes sorának tartalmaznia kell egy azonosítószámát, vagy egy IMEI számának vagy iOS sorozatszámát. Is megadhat. IMEI-számokkal Android, iOS és Windows eszközökhöz használható. iOS-sorozatszámokat is támogatottak.  Ez a tábla a mintaadatok tartalmazza:

| IMEI #  | iOS soros #  | AZ OPERÁCIÓS RENDSZER | Részletek |
|------------ |---------------|-----|-----|
| 123456789012345    |   | WINDOWS | Vállalati tulajdonban lévő Windows-eszköz|
|   | A1B2C3D4E5C6 | IOS |     Vállalat által birtokolt iOS-eszközön|
| 223456789012345 | E6D5C4B3A210 |   IOS |     Egy másik iOS-eszközön|
| 323456789012345 |        |   IOS |     Egy harmadik iOS-eszközön|
| 123456789012346 |         |   ANDROID |     Android-eszköz vállalati által birtokolt|

A .csv fájl nem tartalmaz a fejlécsor. A következő példa bemutatja a azonos mintaadatok CSV formátumban:

```
123456789012345,,WINDOWS,Company-owned Windows device
,A1B2C3D4E5C6,IOS,Company-owned iOS device
223456789012345,E6D5C4B3A210,IOS,Another iOS device
323456789012345,,IOS,A third iOS device
123456789012346,,ANDROID,Company-owned Android device
```

A .csv fájl oszlopai fogadja el az alábbi értékeket:

| 1. oszlop | 2. oszlop | 3. oszlop | 4. oszlop |
|---|---|---|---|
|IMEI-számmal, szóközök nélkül | iOS-sorozatszám | IOS, WINDOWS és ANDROID | Nem kötelező eszközadatok (1024 karakter lehet) |

