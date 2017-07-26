---
title: "Parancssori telepítés |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager telepítő futtassa a hely telepítésekor számos parancsot a parancssorba."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7cdb1a9-140a-436e-ac71-72d083110223
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fefa5f3aa12d82b66a251cf0525475496e1e35cf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>A parancssori telepítéséhez használja a System Center Configuration Manager-helyek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A System Center Configuration Manager telepítő különböző helytípusok telepítése parancssorból futtathatja.

## <a name="supported-tasks-for-command-line-installations"></a>Támogatott feladatok nélküli parancssori telepítés
 A telepítő ezt a módszert támogatja a következő hely telepítése és a helykarbantartási feladatokról:

-   **A központi adminisztrációs hely vagy elsődleges hely telepítése a parancssorból**  
  Nézet [telepítéshez használható parancssori kapcsolók](../../../../core/servers/deploy/install/command-line-options-for-setup.md)

-  **A központi adminisztrációs hely vagy elsődleges helyen használt nyelvek módosítása**  
    Módosítja egy hely egy parancssort (beleértve a mobileszközök nyelveit) telepített nyelvek, a következőket kell tennie:  

     -   Futtassa a telepítőt  **&lt;Configmgrtelepítésiútvonal\>\Bin\X64** a helykiszolgálón
     -   Használja a **/managelangs** parancssori kapcsoló
     -   Adjon meg egy nyelvi parancsfájlt, amely meghatározza a nyelveket a hozzáadása vagy eltávolítása,  

    Például használhatja a következő parancsszintaxist: **setupwpf.exe/managelangs &lt;nyelvi parancsfájl\>**  

    A nyelvi parancsfájl létrehozásához használja az információk [nyelvek kezelése parancssori kapcsolókkal](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)  

-  **Nélküli telepítési parancsfájlban használandó felügyelet nélküli telepítéséhez vagy a helyreállítás**  
    Futtathatja a telepítő parancssori nélküli telepítési parancsfájllal, és a helyek felügyelet nélküli telepítés futtatásakor. Ez a beállítás segítségével a hely helyreállítása.    

    Parancsfájl használata a telepítővel:  

    -   Futtassa a telepítőt a parancssori kapcsolóval **/SCRIPT** és adjon meg egy parancsfájlt.  

    -   A parancsfájlt a szükséges kulcsokkal és értékekkel kell konfigurálni.  

    Egy központi adminisztrációs hely vagy elsődleges hely felügyelet nélküli telepítés esetén a parancsfájlt a következő szakaszok kell rendelkeznie:  

    -   Azonosító    
    -   Paraméterek    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    A hely helyreállítása is szerepelnie kell a parancsfájl alábbi szakaszait:  

    -   Azonosító  
    -   Helyreállítás

A biztonsági mentési és helyreállítási kapcsolatos további információkért tekintse meg a [a helyek felügyelet nélküli helyreállításához használható parancsfájl kulcsai](../../../../protect/understand/backup-and-recovery.md#BKMK_UnattendedSiteRecoveryKeys) a a [biztonsági mentés és helyreállítás a Configuration Manager](../../../../protect/understand/backup-and-recovery.md) témakör.  

Kulcsok és értékek egy felügyelet nélküli telepítési parancsfájlban használandó listájáért lásd: [felügyelet nélküli telepítési parancsfájl kulcsai](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended).  

## <a name="about-the-command-line-script-file"></a>A parancssori parancsfájl fájlról  
 A Configuration Manager felügyelet nélküli telepítés esetén a telepítő futtatásával a parancssori kapcsolóval **/SCRIPT**, és adjon meg egy parancsfájlt, amely tartalmazza a telepítési beállítások. Ezzel a módszerrel az alábbi feladatokat támogatja:  

-   Központi adminisztrációs hely telepítése  
-   Elsődleges hely telepítése  
-   A configuration Manager konzol telepítése  
-   A hely helyreállítása  

> [!NOTE]  
>  A felügyelet nélküli telepítés parancsfájljában próbaverziójának frissítése licencelt verzióra a Configuration Manager nem tudja használni.  

### <a name="the-cdlatest-key-name"></a>A CDLatest kulcs neve
A CD-ről adathordozó használatakor. Legfrissebb mappát egy parancsfájl futtatásához telepítse a következő négy telepítési beállításokat, a parancsfájl tartalmaznia kell a **CDLatest** értékkel rendelkező kulcs **1**:
- Új központi adminisztrációs hely telepítése
- Új elsődleges hely telepítése
- Központi adminisztrációs hely helyreállítása
- Elsődleges hely helyreállítása 

Ez az érték nem támogatott telepítési adathordozóján való használatra, hogy a Microsoft mennyiségi licenc helyről kapott.
Lásd: [parancssori kapcsolók](/sccm/core/servers/deploy/install/command-line-options-for-setup) információk használata a kulcs neve a parancsfájlban.



### <a name="create-the-script"></a>A parancsfájl létrehozása
A telepítési parancsfájl automatikus létrehozása esetén, [futtassa a telepítőt egy hely, a felhasználói felület használatával](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  Ha a beállításokat jóváhagyja a **összegzés** a varázsló a következő történik:  

-   A telepítő létrehozza a parancsfájlt **%TEMP%\ConfigMgrAutoSave.ini**.  Átnevezheti ezt a fájlt, mielőtt használja, de meg kell őrizni az .ini fájlkiterjesztést.  
-   A felügyelet nélküli telepítési parancsfájl a varázslóban kiválasztott beállításokat tartalmazza.  
-   A parancsfájl létrehozása után módosíthatja a parancsfájl más helyeket is telepíthet a hierarchiában.  
-   Ezt a parancsfájlt használhatja egy Configuration Manager felügyelet nélküli telepítés végrehajtásához.  

A parancsfájl ugyanolyan információkat tartalmaz, amely a telepítővarázsló kér, azzal a különbséggel, hogy nincsenek alapértelmezett beállítások.   
A telepítési kulcsokhoz az Ön által használt telepítési típusra vonatkozó minden értéket meg kell adni.   

Amikor a telepítő létrehozza a felügyelet nélküli telepítési parancsfájlt, a telepítéskor megadott termékkulcsot állítja, a telepítés során kell beírni. Ez lehet érvényes termékkulcs, vagy **EVAL** a Configuration Manager próbaverziójának telepítésekor. A parancsfájl a termékkulcs értékét úgy, hogy az előfeltétel-ellenőrzés be tudja fejezni van feltöltve.   

Amikor a telepítő megkezdi a hely tényleges telepítését, az automatikusan létrehozott parancsfájlt rendszer újraírja, hogy törli a parancsfájlt, amely létrehozza a termékkulcs értékét. Mielőtt a parancsfájlt új hely felügyelet nélküli telepítéséhez, szerkesztheti a parancsprogramot, adjon meg egy érvényes termékkulcsot, vagy adja meg a Configuration Manager próbaverziójáról van szó.  

### <a name="section-names-key-names-and-values"></a>Szakaszneveket, a kulcsneveket és az értékeket
A parancsfájl tartalmazza a szakaszneveket, a kulcsneveket és az értékeket. Vegye figyelembe a következőket:
-   Szükséges szakaszkulcsnevek attól függően, hogy a telepítési típus, amely készít parancsfájlt.
-   A kulcsok szakaszokon belüli sorrendje, illetve a szakaszok fájlon belül sorrendje nem számít.     
-   A kulcsokban nincs kis-és nagybetűket.  
-   Ha értékeket ad meg a kulcsokhoz, a kulcs nevét kell követi egyenlőségjel (=) és a kulcs értékét.    

> [!TIP]  
>  A beállítások teljes készletének megtekintése: [üzembe helyezési és parancsfájlok parancssori kapcsolók](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  

## <a name="use-the-script-setup-command-line-option"></a>A setup parancs/Script telepítési parancssori kapcsoló használata

-   Kell egy telepítési parancsfájlt használ, és adja meg a fájlnevet, miután a **/SCRIPT** telepítési parancssori kapcsoló. Vegye figyelembe a következőket:   
    -   A fájl nevének kell lennie a **.ini** fájlnév-kiterjesztésű.  
    -   Ha hivatkozik a telepítési parancsfájl a parancssorban, meg kell adnia a fájl teljes elérési útja. Például, ha a telepítési inicializációs fájl neve Setup.ini, és tárolja a C:\Setup mappában található, a parancssorba írja be: **telepítő/script c:\setup\setup.ini**.  

-   A telepítő futtatásához használt fióknak rendelkeznie kell **rendszergazda** jogosultságokkal azon a számítógépen. Amikor a telepítő felügyelet nélküli parancsfájllal futtatja, nyissa meg a parancsablakot használatával a **Futtatás rendszergazdaként** lehetőséget.   

