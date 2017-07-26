---
title: "Windows központi telepítése a hálózaton keresztül nélkül a különálló adathordozó használatával |} Microsoft Docs"
description: "Különálló adathordozó használata a Configuration Manager ahol sávszélessége korlátozott operációs rendszerek központi telepítéséhez vagy egy lehetőség, hogy a frissítés, telepítse vagy számítógépek frissítéséhez."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58a0d2ae-de76-401f-b854-7a5243949033
caps.latest.revision: 16
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 30ae794381c6894e11b21a8167d0af60463c5279
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-stand-alone-media-to-deploy-windows-without-using-the-network-in-system-center-configuration-manager"></a>Windows központi telepítése a System Center Configuration Managerben a hálózat használata nélkül a különálló adathordozó használatával

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Különálló adathordozó a System Center Configuration Manager tartalmaz mindent, ami egy számítógépen operációs rendszer központi telepítése szükséges. Az adathordozónak így tartalmaznia kell a rendszerindító lemezképet, az operációsrendszer-lemezképet és a feladatütemezést az operációs rendszer telepítéséhez, beleértve az alkalmazásokat, az illesztőprogramokat, és így tovább. Az operációs rendszer különálló adathordozó használatával indított központi telepítéseit a következő feltételek esetében alkalmazhatja:  

-   Olyan környezetekben, ahol nem célszerű a hálózaton keresztül átmásolni az operációs rendszer lemezképét vagy egyéb nagyméretű csomagokat.  

-   Olyan környezetekben, ahol nincs hálózati kapcsolat vagy kicsi a hálózati kapcsolat sávszélessége.  

Az operációs rendszerek alábbi központi telepítési forgatókönyveiben használhatók különálló adathordozók:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [A Windows frissítése a legújabb verzióra](upgrade-windows-to-the-latest-version.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján készítheti elő és hozhatja létre a különálló adathordozót.  

## <a name="task-sequence-actions-not-supported-when-using-stand-alone-media"></a>Különálló adathordozó használatakor nem támogatott feladatütemezési műveletek  
 Ha végrehajtotta egy támogatott operációsrendszer-telepítési forgatókönyv lépéseit, az azt jelenti, hogy létrejött az operációs rendszer központi telepítését vagy frissítését végző feladatütemezés, és minden ahhoz kapcsolódó tartalom továbbítva lett egy terjesztési pontra. Különálló adathordozó használatakor a következő műveletek használata nem támogatott a feladatütemezésben:  

-   Az Illesztőprogramok automatikus alkalmazása lépés használata a feladatütemezésben. Az eszközillesztők illesztőprogram-katalógusból való automatikus alkalmazása nem támogatott, de az Illesztőprogram-csomag alkalmazása lépésben elérhetővé tehet egy adott illesztőprogram-készletet a Windows telepítő számára.  

-   A szoftverfrissítések telepítése.  

-   Szoftver telepítése az operációs rendszer telepítése előtt.  

-   Felhasználók társítása a célszámítógéphez a felhasználó-eszköz kapcsolat támogatásához.  

-   Dinamikus csomag telepítése az Install Packages (Csomagok telepítése) feladattal.  

-   Dinamikus alkalmazás telepítése az Install Application (Alkalmazás telepítése) feladattal.  

> [!NOTE]  
>  Ha az operációs rendszerek központi telepítéséhez használt feladatütemezés tartalmazza a [csomagtelepítés](../understand/task-sequence-steps.md#BKMK_InstallPackage) lépés és hozza létre a különálló adathordozót egy központi adminisztrációs helyen, hiba történhet. A központi felügyeleti hely nem rendelkezik azon ügyfélkonfigurálási házirendekkel, amelyek a feladatütemezés végrehajtása közben a szoftverterjesztési ügynök engedélyezéséhez szükségesek. A CreateTSMedia.log fájlban a következő hiba jelenhet meg:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`
>   
>  A különálló adathordozót egy **csomag telepítése** lépés, kell létrehoznia a különálló adathordozót azon az elsődleges helyen, amelynek engedélyezett szoftverterjesztési ügynöke, vagy adja hozzá egy [parancssor futtatása](../understand/task-sequence-steps.md#BKMK_RunCommandLine) lépés után a [Windows és ConfigMgr beállítása](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) lépés és első **csomag telepítése** lépést a feladatütemezéshez. A **Parancssor futtatása** lépés a WMIC parancsot futtatja, hogy engedélyezze a szoftverterjesztési ügynököt, mielőtt az első Telepítőcsomag lépés futna. A feladatütemezés **Parancssor futtatása** lépésében a következő használható:  
>   
>  **Parancssori**: **WMIC/Namespace:\\\root\ccm\policy\machine\requestedconfig elérési ccm_SoftwareDistributionClientConfig most letölthető a KomponensNév létrehozása = "SWDist engedélyezése", engedélyezve = "true", LockSettings = "TRUE", PolicySource = "local", az PolicyVersion = "1.0" SiteSettingsKey = "1" / NOINTERACTIVE**  

## <a name="configure-deployment-settings"></a>Központi telepítési beállítások konfigurálása  
 Ha különálló adathordozóval indítja el az operációs rendszer központi telepítésének folyamatát, úgy kell konfigurálnia a központi telepítést, hogy elérhetővé tegye az operációs rendszert adathordozók számára. Ezt a Szoftver központi telepítése varázsló **Központi telepítési beállítások** lapján, vagy a központi telepítés tulajdonságainak **Központi telepítési beállítások** lapján konfigurálhatja.  Az **Elérhetővé tétel a következők számára** beállításnál konfigurálja a következők egyikét:  

-   **Configuration Manager ügyfelek, média és PXE**  

-   **Csak média és PXE**  

-   **Csak média és PXE (rejtett)**  

## <a name="create-the-stand-alone-media"></a>Különálló adathordozó létrehozása  
 Megadhatja, hogy a különálló adathordozó USB flash meghajtó vagy CD/DVD-készlet legyen. Az adathordozót elindító számítógépnek támogatnia kell a rendszerindító meghajtóként kiválasztott lehetőséget. További információkért lásd: [különálló adathordozó létrehozása](create-stand-alone-media.md).  

## <a name="install-the-operating-system-from-stand-alone-media"></a>Az operációs rendszer telepítése különálló adathordozóról  
 Az operációs rendszer telepítéséhez helyezze be a különálló adathordozót a számítógép egy rendszerindító meghajtójába, majd kapcsolja be a számítógépet.  

