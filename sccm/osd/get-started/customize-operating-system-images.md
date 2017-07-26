---
title: "Operációsrendszer-lemezképek – Configuration Manager testreszabása |} Microsoft Docs"
description: "Az operációs rendszer lemezképének testreszabásához rögzítési és beépített feladatütemezések, kézi konfigurálás vagy mindkettőt használja."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95033a9b-ff13-4b70-b1de-bcb25bcb6024
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 485cb3ca4988f983c1ec71b6c8daf136571bf0ea
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="customize-operating-system-images-with-system-center-configuration-manager"></a>Operációsrenszer-lemezképek testreszabása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager operációsrendszer-lemezképek WIM-fájl, és a referencia-fájlokat és mappákat, amelyek szükségesek a sikeres telepítéséhez és az operációs rendszer konfigurációjához a számítógépen a tömörített gyűjteményét tartalmazzák. Egy egyéni operációsrendszer-lemezkép összeállítása és rögzítése egy olyan referencia-számítógépről történik, amelyen konfigurálnia kell az operációs rendszer összes szükséges fájlját, a támogatási fájlokat, a szoftverfrissítéseket, az eszközöket és az egyéb szoftveralkalmazásokat. A referencia-számítógépet tetszőleges mértékben konfigurálhatja manuálisan. A referencia-számítógép konfigurálását teljesen automatizálhatja egy elkészítési feladatütemezés alkalmazásával. Emellett megadhatja a referencia-számítógép bizonyos jellemzőit manuálisan, majd feladatütemezésekkel automatizálhatja a további konfigurálást, vagy konfigurálhatja a referencia-számítógépet manuálisan, feladatütemezések alkalmazása nélkül is. A következő szakaszok segítségével az operációs rendszer testreszabását.

##  <a name="BKMK_PrepareReferenceComputer"></a>A referencia-számítógép előkészítése  
 Számos szempontot figyelembe kell vennie, mielőtt rögzíti az operációs rendszer lemezképét egy referencia-számítógépről.  

###  <a name="BKMK_RefComputerDecide"></a>Az automatikus vagy manuális konfigurációs között  
 Az alábbi táblázat a referencia-számítógép automatizált, illetve kézi konfigurálásának előnyeit és hátrányait összegzi.  

#### <a name="automated-configuration"></a>Automatizált konfigurálás  
 **Előnyök**  

-   A konfigurálás során nincs szükség személyes felügyeletre, így a rendszergazda vagy a felhasználó jelenlétére sem.  

-   A feladatütemezés ismét felhasználható további referencia-számítógépek konfigurálásának megismétléséhez, és nagymértékben megbízható.  

-   A feladatütemezés a referencia-számítógépek közötti különbségek érvényre juttatása érdekében anélkül módosítható, hogy ismét létre kelljen hozni a teljes feladatütemezést.  

 **Hátrányok**  

-   A feladatütemezések kezdeti létrehozása és ellenőrzése hosszadalmas lehet.  

-   Amennyiben a referencia-számítógép jelentős módosításokat kíván meg, a feladatütemezés újbóli létrehozása és ellenőrzése hosszadalmas lehet.  

#### <a name="manual-configuration"></a>Kézi konfigurálás  
 **Előnyök**  

-   Nem szükséges feladatütemezéseket létrehoznia, ellenőriznie, illetve elhárítania a fellépő hibákat.  

-   Telepítése CD-ről anélkül (így magát a Windowst is) az összes szoftvercsomag a Configuration Manager-csomagból.  

 **Hátrányok**  

-   A referencia-számítógép konfigurálásának pontossága a konfigurálást végző rendszergazdán vagy felhasználón múlik.  

-   Önnek mindenképpen ellenőriznie kell, hogy a referencia-számítógép konfigurálása megfelelő-e.  

-   Nem használhatja újra a konfigurációs módszert.  

-   A folyamat során valakinek mindvégig jelen kell lennie.  

###  <a name="BKMK_RefComputerConsiderations"></a>A referencia-számítógéppel kapcsolatos szempontok  
 Az alábbi táblázat a referencia-számítógépek konfigurálásához alapvetően szükséges elemeket sorolja fel.  

-   **Operációs rendszer központi telepítése**  

     A referencia-számítógépre a célszámítógépekre központilag telepíteni kívánt operációs rendszert kell telepíteni. A központilag telepíthető operációs rendszerekkel kapcsolatos további információkért lásd: [operációs rendszer központi telepítésének infrastrukturális követelményei](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Megfelelő szervizcsomag**  

     A referencia-számítógépre a célszámítógépekre központilag telepíteni kívánt operációs rendszert kell telepíteni.  

-   **Megfelelő szoftverfrissítések**  

     Telepítsen minden olyan szoftveralkalmazást, amit szerepeltetni kíván a referencia-számítógépen rögzített operációsrendszer-lemezképen. Szoftveralkalmazásokat a rögzített operációsrendszer-lemezképnek a célszámítógépekre történő központi telepítése során is telepíthet.  

-   **Munkacsoporttagság**  

     A konfigurálni kívánt referencia-számítógépnek munkacsoportba kell tartoznia.  

-   **A Sysprep**  

     A Sysprep rendszer-előkészítő eszköz egy olyan technológia, amely más telepítőeszközökkel együtt használható Windows operációs rendszerek új számítógépre telepítéséhez. A Sysprep előkészíti a számítógépet lemezkép készítésére, illetve az ügyfélnek történő szállításra. Ennek érdekében úgy konfigurálja a számítógépet, hogy újraindításkor új számítógép-biztonsági azonosítót (SID) hozzon létre. A Sysprep emellett azokat a felhasználó- és számítógép-specifikus beállításokat és adatokat is törli, amelyek nem kerülhetnek a célszámítógépre.  

     A célszámítógépen a következő parancs futtatásával kézzel is végrehajtható a Sysprep:  

     `Sysprep /quiet /generalize /reboot`  

     A /generalize kapcsoló utasítja a Sysprep eszközt a rendszerspecifikus adatok eltávolítására a Windows-telepítésből. Rendszerspecifikus adatok például az eseménynaplók, az egyedi biztonsági azonosítók (SID-k) és az egyéb egyedi adatok. Az egyedi rendszeradatok eltávolítása után a számítógép újraindul.  

     A Sysprep a feladatütemezés [Windows előkészítése a rögzítéshez](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) lépésével vagy médiarögzítéssel automatizálható.  

    > [!IMPORTANT]  
    >  A feladatütemezés [Windows előkészítése a rögzítéshez](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) lépése megkísérli a referencia-számítógép helyi rendszergazdai jelszavának üres értékre történő visszaállítását a Sysprep futtatása előtt. Ha **A jelszónak meg kell felelnie a bonyolultsági feltételeknek** Helyi biztonsági házirend engedélyezve van, a feladatütemezés e lépése nem fogja tudni visszaállítani a rendszergazdai jelszót. Ebben az esetben a feladatütemezés futtatása előtt tiltsa le a házirendet.  

     A Sysprep eszközről a [Rendszer-előkészítő eszköz (Sysprep) – technikai útmutató](http://go.microsoft.com/fwlink/?LinkId=280286) című témakörben olvashat bővebben.  

-   **Telepítésiforgatókönyv szükséges megfelelő eszközök és parancsfájlok**  

     Megfelelő, a telepítésiforgatókönyv-hibák számának csökkentéséhez szükséges eszközök és parancsfájlok  

-   **Asztal megfelelő testreszabása: például háttérkép, védjegy és alapértelmezett felhasználói profil**  

     A referencia-számítógépen beállíthatja azokat az asztaltulajdonságokat, amelyeket szerepeltetni kíván a referencia-számítógépen rögzített operációsrendszer-lemezképen. Az asztal tulajdonságai közé tartozik például a háttérkép, a vállalati védjegyek, illetve az alapértelmezett normál felhasználói profil.  

##  <a name="BKMK_ManuallyBuildReference"></a>A referencia-számítógép manuális elkészítése  
 Az alábbi eljárással készíthet el egy referencia-számítógépet manuálisan.  

> [!NOTE]  
>  Ha a referencia-számítógépet manuálisan készíti el, az operációs rendszer lemezképét médiarögzítésű adathordozó használatával rögzítheti. További információkért lásd: [médiarögzítésű adathordozó létrehozása](../deploy-use/create-capture-media.md).  

#### <a name="to-manually-build-the-reference-computer"></a>A referencia-számítógép manuális elkészítése  

1.  Azonosítsa a referencia-számítógépként használandó számítógépet.  

2.  Konfigurálja a referencia-számítógépen a megfelelő operációs rendszert és minden egyéb szoftvert, amely a központi telepítéshez használni kívánt operációsrendszer-lemezkép létrehozásához szükséges.  

    > [!WARNING]  
    >  Telepítse legalább a megfelelő operációs rendszert és szervizcsomagot, a támogatott illesztőprogramokat és a szükséges szoftverfrissítéseket.  

3.  Konfigurálja a referencia-számítógépet, hogy munkacsoport tagja legyen.  

4.  Állítsa vissza a referencia-számítógép helyi rendszergazdájának jelszavát üresre.  

5.  Sysprep futtatásához használja a következő parancsot: **sysprep /quiet /generalize /reboot**. A /generalize kapcsoló utasítja a Sysprep eszközt a rendszerspecifikus adatok eltávolítására a Windows-telepítésből. Rendszerspecifikus adatok például az eseménynaplók, az egyedi biztonsági azonosítók (SID-k) és az egyéb egyedi adatok. Az egyedi rendszeradatok eltávolítása után a számítógép újraindul.  

 Amikor a referencia-számítógép készen áll, egy feladatütemezés segítségével rögzítse az operációs rendszer lemezképét a referencia-számítógépről.  A lépések részletes leírását az [Operációs rendszer lemezképének rögzítése meglévő referencia-számítógépről](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_CaptureExistingRefComputer) című témakörben találja.  

##  <a name="BKMK_UseTSToBuildReference"></a>Referencia-számítógép elkészítése feladatütemezés használatával  
 A referencia-számítógép elkészítésének folyamatát egy feladatütemezés használatával automatizálhatja, amely telepíti az operációs rendszert, az illesztőprogramokat, az alkalmazásokat és így tovább.  Az alábbi lépések végrehajtásával készítse el a referencia-számítógépet, és rögzítse az operációs rendszer lemezképét a referencia-számítógépről.  

-   Az operációs rendszer lemezképének rögzítéséhez a referencia-számítógépről használjon feladatütemezést.  Lépésenkénti útmutató: [Referencia-számítógép előállítása feladatütemezés használatával](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_BuildCaptureTS).  

