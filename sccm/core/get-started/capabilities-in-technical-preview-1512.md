---
title: "A Technical Preview 1512 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1512 verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5cf8d54fbaa98a75ac2a875a23a43b1d3e5be0dd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>A Technical Preview 1512 rendszer képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat a Technical Preview a System Center Configuration Manager, a verzió 1512 elérhető. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

 Új funkciókat próbálhatja ki ebben a következők:  

##  <a name="bkmk_devicehealth"></a> Eszközállapot-igazolás  
 Technical Preview 1512 verziótól kezdődően a rendszergazdák a Windows 10 Eszközállapot-igazolási állapotát a Configuration Manager konzolon megtekintheti.  Ez a funkció érhető el a Configuration Manager és a Configuration Manager a Microsoft Intune-nal. Eszközállapot-igazolással a rendszergazdák gondoskodhatnak arról, hogy az ügyfél számítógépek megbízható a BIOS, TPM- és rendszerindítószoftver-konfigurációja. Az Eszközállapot-igazolás támogatásához ügyféleszközök futnia kell: Win10 a TPM 2-t. Eszközállapot-igazolás megjeleníti az egyes alábbi funkciók engedélyezett eszközök száma:  

-   Korai indítás kártevőirtó  

-   A BitLocker  

-   A biztonságos rendszerindítás  

-   A Kódintegritás  

A konzol megjeleníti a hiányzó állapotigazolással kapcsolatos főbb beállítások eszközök számának felső is.  

Ahhoz, hogy az Eszközállapot-igazolási nézet előnézetének megtekintéséhez a Configuration Manager konzolon lépjen a **figyelés** munkaterületét, és kattintson **biztonsági** csomópontra, majd **az Eszközállapot-igazolás**.  

##  <a name="bkmk_viewterms"></a>A konzolon belüli figyelést feltételek és kikötések  
Technical Preview 1512 kezdve Ha integrálja a Configuration Manager a Microsoft Intune-nal, használhatja a Configuration Manager-konzol mely felhasználók fogadták el a feltételeket és kikötéseket, az informatikai részleg által konfigurált, és mely felhasználók nem rendelkeznek.  

**Összefoglaló információk megtekintése:**  

-   Nyissa meg a a Configuration Manager konzol **figyelés** > **áttekintése** > **központi telepítések** , és válassza ki a használati feltételek központi telepítését, meg szeretné tekinteni.  

**Részletes információk megtekintése:**  

1.  Nyissa meg a a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **megfelelőségi beállítások** > **feltételek és kikötések**, majd válassza ki a megtekinteni kívánt feltételeket.  

2.  A konzol alján válassza ki a **központi telepítések** fülre, válassza ki a központi telepítést, majd **állapotának megtekintése.**  

##  <a name="bkmk_EPpolicy"></a>Az Endpoint Protection házirend-beállításainak fejlesztései  
A Technical Preview 1512 az Endpoint Protection kártevőirtó-házirendet a következő új beállítások jelentek meg:  

-   A valós idejű védelem: **Vélhetően nemkívánatos alkalmazások blokkolása letöltéskor és telepítés előtt**  

    -   A Vélhetően nemkívánatos alkalmazások (PUA) egy megbízhatósági besoroláson és kutatásvezérelt azonosításon alapuló fenyegetési besorolás. Ezek leggyakrabban nemkívánatos alkalmazáscsomagolók vagy azok csomagolt alkalmazásai.  

    -   A védelmi házirend-beállítás ("Yes" értékre állítva) alapértelmezés szerint engedélyezett. Ha engedélyezve van, ez a beállítás letöltéskor és telepítéskor blokkolja a vélhetően nemkívánatos alkalmazásokat. Azonban kizárhat meghatározott fájlokat vagy mappákat a környezet konkrét igényeinek.  

-   Vizsgálati beállítások: **Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat futtatásakor**  

    -   Ez a beállítás biztosítja nagyobb részletességgel anélkül, hogy mindig vizsgálja a hálózati fájlok igény szerinti vizsgálat engedélyezéséhez a csatlakoztatott hálózati meghajtókat a ütemezett teljes vizsgálat közben.  

    -   A beállítás **hálózati fájlok ellenőrzése** kell ("yes") Ez a beállítás konfigurálható legyen engedélyezve.  

    -   Alapértelmezés szerint ez a beállítás értéke "Nincs" jelentése, hogy a teljes vizsgálatok nem érik el a csatlakoztatott hálózati meghajtók.  

-   Az automatikus mintafájlküldési beállítások:  

     A kártevőirtó motor kérheti fájlminták elküldését a Microsoftnak további elemzés céljából. Az ilyen minták küldése előtt a rendszer alapértelmezés szerint mindig megkérdezi a felhasználót. A rendszergazdák mostantól a következő beállítások kezelésével konfigurálhatják ezt a viselkedést:  

    -   Speciális: **Mintafájlok automatikus küldésének hogy segítse annak meghatározásában, hogy bizonyos észlelt elemek-e az esetleg kártékony engedélyezése**:  Módosítsa ezt a beállítást, az "Igen" mintafájlok automatikus küldésének engedélyezéséhez. Alapértelmezés szerint ez a beállítás értéke "Nem", ami azt jelenti, mintafájlok automatikus küldése le van tiltva, és a felhasználók felszólítást kapnak minták küldése előtt.   (Ez a beállítás először a System Center 2012 R2 Configuration Manager SP1 verzióban jelent)  

    -   Speciális: **Felhasználók automatikus mintafájlküldési beállítások módosítása**: Ez a beállítás meghatározza, hogy egy eszközön helyi rendszergazdai jogosultságokkal rendelkező felhasználók módosíthatják-e a mintafájlok automatikus küldésének beállításait az ügyféloldali felületen. Alapértelmezés szerint ez a beállítás értéke "Nem", ami azt jelenti, hogy a beállítások csak módosítható az a Configuration Manager-konzolon, és az eszközön helyi rendszergazdák nem módosíthatják ezt a konfigurációt.  

         Például a következő látható, a Windows Defender-beállítása, a Windows 10 a rendszergazda által beállított, mivel engedélyezve van, és a felhasználó nem módosítható:  

         ![TechRef &#95; WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    Ezen felül a meglévő **fájlok és mappák kizárása** beállítása a "A kizárások beállításai" szakaszban, az endpoint protection kártevőirtó házirend tovább lett fejlesztve a lehetővé tegye az eszközök kizárását. Most már megadhatja például a következőt kizárásként: **\device\mvfs** (többverziós fájlrendszer esetén). A házirend nem ellenőrzi az eszköz elérési útját; az endpoint protection-házirend megadott a kártevőirtó motor, amely értelmezni az eszköz karakterláncát képesnek kell lennie.  

**Endpoint Protection-házirendek használatának előfeltételei:**  

Endpoint Protection-házirendek használata előtt kell telepíteni, és az Endpoint Protection ügyfél kezelése az Endpoint Protection ügyfélbeállításainak használatával. Ebben az esetben a System Center Endpoint Protection-ügyfél Windows 7, Windows 8, Windows 8.1 vagy felügyelt Windows Defender a Windows 10 használatával. Lásd: [a System Center Configuration Managerben az Endpoint Protection](../../protect/deploy-use/endpoint-protection.md).  

