---
title: "Az alkalmazhatósági szabályok |} Microsoft Docs"
description: "Az alkalmazhatósági szabályok kezelése a System Center frissítés-közzétevő"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 2925abda07abaa46ad56b9b433ce003c22aede5e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="manage-applicability-rules-in-updates-publisher"></a>Az Updates Publisher alkalmazhatósági szabályok kezelése

*Vonatkozik: A System Center frissítés-közzétevő*

A frissítés-közzétevője alkalmazhatósági szabályok eszköz frissítés telepítése előtt teljesítendő követelmények meghatározása. A szabályok alapján határozza meg, ha a számítógép rendelkezik-e a telepített frissítés is állítja. Egy alkalmazhatósági szabályt, amely több alkotórészek összetett hivatkozik, amely szabály beállítása.

Frissítési csomagok ne használja az alkalmazhatósági szabályok.

## <a name="overview-of-applicability-rules"></a>Az alkalmazhatósági szabályok áttekintése
Az alkalmazhatósági szabályok kezelheti a **szabályok munkaterület**. A szabály létrehozásakor meg egy vagy több feltételt. Több feltétel van megadva, konfigurálhatók, azok egymás után kiértékelése vagy logikai egyesítve a feltételek közötti kapcsolatok **és** vagy **vagy** utasításokat.

Például a következő olyan szabály, amely három szabályokat tartalmazza. Az első szabály ellenőrzi, hogy a *Saját_fájl* fájl létezik-e, és a második és harmadik szabályok győződjön meg arról, hogy a a Windows operációs rendszer nyelve nem angol és a japán.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

Minden frissítés szükséges legalább egy alkalmazhatósági szabályt. Már importált frissítések alkalmazása az alkalmazhatósági szabályok rendelkezik, és a saját frissítések létrehozásakor hozzá kell adnia egy vagy több szabály azokat. Módosíthatja, és bontsa ki az Updates Publisher található bármelyik frissítés a szabályok.

A létrehozott, a szabályok megtekintése a **szabályok munkaterület**, jelöljön ki egy szabályt a a **mentett szabály** listája. Az egyedi feltételeket és a szabályhoz tartozó logikai műveletek megjelennek a **alkalmazhatósági szabályok** a konzol ablaktáblájában. Az importált frissítések szabályok is csak tekinthetők meg és módosíthatók, ez a frissítés szerkesztésekor.

Az Updates Publisher két helyen szabályokat hozhat létre:

-   Az a **szabályok munkaterület** hoz létre és **mentése** beállítására, majd később használhatja. Ha egy frissítés létrehozása vagy szerkesztése hajthatók végre **mentett szabály** , a **szabály típusa**, majd válassza ki az előre létrehozott készletekkel listáját.

-   Is létrehozhat új szabályokat időpontjában, amely készít vagy szerkeszt a frissítést. Ezzel a módszerrel hoz létre szabályok mentése nem történik meg későbbi felhasználás céljából.

## <a name="create-applicability-rule"></a>Az alkalmazhatósági szabály létrehozása
Az alábbi információk hasonlít szabályok létrehozásában belül a [létrehozása frissítése varázsló](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard). De eltérően a varázslóban lehetősége van a szabálykészletek későbbi használatra menti.

1.  Az a **szabályok munkaterület**, válassza a **létrehozása** megnyitásához a **szabály létrehozása** varázsló.

2.  Adja meg a szabály nevét, és kattintson ![új szabály](media/newrule.png). Ekkor megnyílik a **alkalmazhatósági szabályt** szabályok konfigurálására szolgáló oldalon.

3.  A **szabály típusa,** válassza ki a következők egyikét. A beállítások, konfigurálnia kell az egyes változhatnak:

    -   **Fájl** – Ez a szabály segítségével szükségük van egy eszköz tulajdonságait, amelyek megfelelnek egy fájlt, vagy adja meg, ha a frissítés előtt további feltételeket is lehet alkalmazni.

    -   **Beállításjegyzék –** ennek használatával adja meg a beállításjegyzék adatait, amely szerepelnie kell egy eszköz akkor minősül a frissítés telepítése előtt.

    -   **Rendszer –** Ez a szabály alkalmazhatósági meghatározására: rendszeradatok használja. Itt választhat egy Windows-verzió, a Windows nyelv, a processzor architektúrájától meghatározása, vagy adja meg a WMI-lekérdezés azonosításához az eszközök operációs rendszer.

    -   **A Windows Installer –** használja ezt a szabálytípust alkalmazhatósági egy telepített alapján határozza meg. MSI-fájl vagy a Windows Installer javítási (. AZ MSP). Ha a meghatározott összetevők vagy a szolgáltatások telepítését a követelmény részeként is ellenőrizheti.

       > [!IMPORTANT]   
       > A felügyelt deices, a Windows Update Agent nem észleli a Windows telepítése csomagok, amelyek felhasználói telepítve. Ezt a szabálytípust használatakor konfigurálása további alkalmazhatósági szabályok fájlverzió vagy beállításkulcs-értékeket, például, hogy a Windows Installer-csomag megfelelően észlelt függetlenül felhasználónként vagy rendszerenként alapul.

    -   **Szabály – mentett** Ez a beállítás lehetővé teszi megkeresheti, szabályok, amelyek korábban konfigurált és mentve.

4.  Továbbra is hozzá, és konfigurálja a további szabályok tetszés szerint.

5.  A logikai művelet gombokkal rendezéshez és a különböző szabály létrehozása összetettebb előfeltétel-ellenőrzések.

6.  A szabálykészlet befejeztével kattintson **OK** menti. A szabálykészlet már szerepel a **a mentett szabályok** listája.

## <a name="edit-applicability-rule-sets"></a>Az alkalmazhatósági szabálykészletek szerkesztése
Egy alkalmazhatósági szabályt szerkesztéséhez a **szabályok munkaterület** jelöljön ki egyetlen szabályt mentett a **a mentett szabályok** listában, és válassza a **szerkesztése** a szalagról. Ekkor megnyílik a **szabály szerkesztése** varázsló.

A **szabály szerkesztése** varázsló megjeleníti az aktuális szabályok a szabálykészletet. Szabályok ugyanúgy szerkeszteni, használja a **szabály létrehozása** új szabályok létrehozása varázsló. Ez a varázsló segítségével nevezze át a szabálykészletet, törölje a szabályokat, a szabályok sorrendjének és a kapcsolatokat, vagy új szabályokat hozzáadni.

Miután változtatásokat, válassza ki azt **OK** a módosítások mentéséhez és a varázsló bezárásához.

A szabály varázsló használatával kapcsolatos további részletekért lásd: **7. lépés**, alkalmazhatósági lap, a [létrehozása frissítése varázsló](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard).

## <a name="delete-applicability-rules"></a>Az alkalmazhatósági szabályok törlése
A törlendő egy mentett alkalmazhatósági szabályt, a **szabályok munkaterület** válassza ki a szabály vagy állítson be úgy a szabály a **a mentett szabályok** listában, és válassza a **törlése** a menüszalagról. Ezzel eltávolítja a mentett szabály vagy a szabálykészletet, a frissítés-közzétevő.

Egy adott frissítés a szabály törléséhez kell [a frissítés szerkesztése](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles).

