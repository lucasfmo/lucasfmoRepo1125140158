---
title: "A telepítő letöltési segédprogramja |} Microsoft Docs"
description: "Olvassa el a különálló alkalmazás, amelynek célja annak érdekében, hogy a hely telepítéséhez a legfontosabb telepítőfájlok naprakész verzióját használja."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bda87fc5-2e4c-4992-98a4-01770365038c
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34e24deb90a39bf655a2e24d16cdbe07528e6193
ms.openlocfilehash: b72148ecc16141843178cbd220fe021fab8be992
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="setup-downloader-for-system-center-configuration-manager"></a>A telepítő letöltési segédprogramja a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt a telepítővel telepítené vagy frissítené a System Center Configuration Manager-hely, a Configuration Manager verziója, amelyet a telepítés gombra a frissített telepítési fájlok letöltéséhez a telepítő letöltési segédprogramja önálló alkalmazást is használhatja.  

Frissített telepítőfájlok használatával biztosíthatja, hogy a hely telepítéséhez a legfontosabb telepítőfájlok naprakész verzióját használja-e. A oveview:   
-   Segédprogram használatával töltse le a fájlokat a telepítő indítása előtt, ha a fájlok tárolására szolgáló mappát adja meg.  
-   A telepítő letöltési segédprogramjának futtatásához használt fióknak rendelkeznie kell **teljes hozzáférés** a letöltési mappa engedélyeit.  
-   Amikor a telepítővel telepítené vagy frissítené a helyet, közvetlen úgy, hogy a fájlok korábban letöltött helyi példányát használja. Ez megakadályozza, hogy a telepítő kiszolgálóihoz csatlakozni a Microsoft, a hely telepítésének vagy frissítésének indításakor.  
-   Használhatja a telepítőfájlok helyi példányait későbbi helytelepítésekhez és frissítéseket.  

A következő típusú fájlokat tölti le a telepítő letöltési segédprogramja:  
-   Szükséges, előfeltételként szükséges újraterjeszthető fájlokat  
-   Nyelvi csomagok  
-   A legújabb frissítéseket a telepítő  

A telepítő letöltési segédprogramjának futtatásához két lehetőség közül választhat:
- Az alkalmazás futtatásához a felhasználói felületen
- A parancssori kapcsolókat az alkalmazás futtatásához a parancssorba


## <a name="run-setup-downloader-with-the-user-interface"></a>Futtassa a telepítő letöltési segédprogramját a felhasználói felület  

1.  Internetkapcsolattal rendelkező számítógépen nyissa meg a Windows Intézőt, és navigáljon a  **&lt;Configmgrtelepítésiadathordozó\>\SMSSETUP\BIN\X64**.  

2.  A telepítő letöltési segédprogramjának megnyitásához kattintson duplán **Setupdl.exe**.   

3. Adja meg a frissített telepítőfájlok tárolására, és kattintson a mappa elérési útját **letöltése**. A telepítő letöltési segédprogramja ellenőrzi a letöltési mappában jelenleg található fájlokat. Csak a hiányzó vagy, amelyek a meglévő fájloknál frissebb fájlokat tölti le azt. A telepítő letöltési segédprogramja a letöltött nyelvek számára almappákat, és más szükséges almappák hoz létre.  

4.  Tekintse át a letöltés eredményeit, nyissa meg a **ConfigMgrSetup.log** fájlt a c meghajtó gyökérkönyvtárában  .  

## <a name="run-setup-downloader-from-a-command-prompt"></a>A telepítő letöltési segédprogramja futtassa a parancssorból  

1.  Egy parancssori ablakot, keresse meg  **&lt;* Configuration Manager telepítési adathordozójáról*\>\SMSSETUP\BIN\X64**.   

2.  A telepítő letöltési segédprogramjának megnyitásához futtassa **Setupdl.exe**.

    Használhatja az alábbi parancssori kapcsolók a **Setupdl.exe**:   

    -   **/ ELLENŐRZÉS**: Ezt a beállítást a letöltési mappában található a fájlokat, köztük a nyelvi fájlok ellenőrzésére használhatja. Tekintse át az elavult fájlok listáját a C meghajtó gyökérkönyvtárában található ConfigMgrSetup.log fájlban. Nincsenek fájlok lesznek letöltve, ha ezt a beállítást használja.  

    -   **/ VERIFYLANG**: Ez a beállítás segítségével ellenőrizheti a letöltési mappában található nyelvi fájlokat. Tekintse át az elavult nyelvi fájlok listáját a C meghajtó gyökérkönyvtárában található ConfigMgrSetup.log fájlban.

    -   **/LANG**: Használja ezt a beállítást csak a nyelvi fájlok letöltéséhez a letöltési mappához.  

    -   **/NOUI**: Ezt a beállítást használja a telepítő letöltési segédprogramjának indítása a felhasználói felület megjelenítése nélkül. Ha ezt a beállítást használja, meg kell adnia a **letöltés elérési útját** a parancsot a parancssorba részeként.  

    -   **&lt;Letöltésiútvonal\>**: Megadhatja, hogy az ellenőrzés elindításához vagy letöltési folyamat automatikus a letöltési mappa elérési útja. A letöltési mappa elérési útját meg kell adnia, ha használja a **/noui** lehetőséget. Ha nem adja meg a letöltési mappa elérési útját, meg kell adnia az elérési út, amikor a telepítő letöltési segédprogramja elindult. A telepítő letöltési segédprogramja hoz létre a mappát, ha még nem létezik.  

    Példa parancsokat:

    -   **setupd &lt;Letöltésiútvonal\>**  

        -   A telepítő letöltési segédprogramja elindul, ellenőrzi a megadott letöltési mappában található fájlokat, és letölti a csak a hiányzó vagy fájlokat, amelyek újabb verziók, mint a meglévő fájlok.     

    -   **setupdl/verify &lt;Letöltésiútvonal\>**  

        -   A telepítő letöltési segédprogramja elindul, és ellenőrzi a megadott letöltési mappában található fájlokat.  

    -   **setupdl/noui &lt;Letöltésiútvonal\>**  

        -   A telepítő letöltési segédprogramja elindul, ellenőrzi a megadott letöltési mappában található fájlokat, és letölti a csak a hiányzó vagy fájlokat, amelyek a meglévő fájloknál frissebb.  

    -   **setupdl/Lang &lt;Letöltésiútvonal\>**  

        -   A telepítő letöltési segédprogramja elindul, ellenőrzi a megadott letöltési mappában található nyelvi fájlokat, és letölti a kizárólag a nyelvi fájlokat, amelyek hiányoznak, vagy a meglévő fájloknál frissebb.  

    -   **setupdl/verify**  

        -   A telepítő letöltési segédprogramja elindul, és majd meg kell adnia a letöltési mappa elérési útját. A Tovább gombra kattintás után **ellenőrizze**, a telepítő letöltési segédprogramja ellenőrzi a letöltési mappában található fájlokat.  

3.  Tekintse át a letöltés eredményeit, nyissa meg a **ConfigMgrSetup.log** fájlt a c meghajtó gyökérkönyvtárában

