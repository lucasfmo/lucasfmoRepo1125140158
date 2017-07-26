---
title: "Mobileszközök kezelése a Windows Eszközvédelem |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager segítségével kezelheti a Windows Eszközvédelem."
ms.custom: na
ms.date: 04/14/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 49599f529bb409f40caf9057989762e759f1c0ac
ms.openlocfilehash: 113dddb2939fedf24e8d489ff4443bd5e3e72c65
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---


# <a name="device-guard-management-with-configuration-manager"></a>Őr eszközkezelés a Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

## <a name="introduction"></a>Bevezetés
Windows Eszközvédelem olyan Windows 10 szolgáltatásainak, melyet úgy terveztek, kártevő szoftverek és más, nem megbízható szoftverek elleni védelem érdekében a számítógépek csoportja. Megakadályozza, hogy kártékony kódot futó biztosításával, hogy csak engedélyezett kódot, tudja, hogy futtatható-e.

Eszközvédelem magában foglalja a szoftver- és hardverkötet-alapú biztonsági funkcióit. A kódintegritás konfigurálható a szoftver alapú biztonsági rétege, amely képes kikényszeríteni a szoftver futtatásához a számítógépen engedélyezett explicit listáját. A saját, konfigurálható kód sértetlenségének nem áll a hardver- vagy belső vezérlőprogram előfeltételeket. A Configuration Manager telepített őr eszközházirendek egy konfigurálható kódintegritási szabályzat számítógépeken a minimális Windows-verzió és az alábbiakban leírt SKU-követelményeknek megfelelő célgyűjtemények engedélyezése. Másik lehetőségként hipervizor-alapú kódintegritási házirendek a Configuration Manager használatával telepített csoportházirenden keresztül engedélyezhető az erre alkalmas hardvereszközökön védelméről.

Eszközvédelem kapcsolatos további tudnivalókért olvassa el [Eszközvédelem telepítési útmutató](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

A Configuration Manager használatával, amely lehetővé teszi, amelyben Eszközvédelem fog futni a számítógépeken egy gyűjtemény módnál Eszközvédelem házirend telepítése. 

Konfigurálja a következő módok egyikét:

1.    **Engedélyezett kényszerítési** – csak a megbízható végrehajtható fájlok futtatásának engedélyezése.
2.    **Csak naplózási** - engedélyezése az összes ilyen programok futtatását, de a napló nem megbízható végrehajtható fájlok, amelyek az ügyfél helyi eseménynaplóban futnak.

>[!TIP]
>A Configuration Manager jelen verziójának Eszközvédelem egy előzetes verziójú funkció. Az engedélyezéshez, lásd: [előzetes funkciók a System Center Configuration Managerben](/sccm/core/servers/manage/pre-release-features).

### <a name="what-can-run-when-you-deploy-a-device-guard-policy"></a>Mi futtathatja egy Eszközvédelem házirend telepítésekor?

Windows Eszközvédelem segítségével szabályozhatja erősen mi futtatható felügyelt számítógépeken. Ez különösen hasznos a számítógépekhez, a magas biztonsági szintű szervezeti egységek, ahol elengedhetetlen, hogy a nemkívánatos szoftverek nem engedélyezett a futtatandó lehet.

A házirend telepítésekor általában a következő végrehajtható fájlok megengedett futtatásához:

- A Windows operációs rendszeri összetevők
- Hardver-fejlesztői központhoz illesztőprogramok (Windows Hardware Quality Labs aláírással rendelkeznek-e)
- A Windows Áruházbeli alkalmazások
- A Configuration Manager-ügyfél 
- Összes szoftvert, hogy a számítógépek telepítése a Eszközvédelem házirend feldolgozása után Configuration Manager használatával telepített. 
- A windows-összetevők frissítéseit:
    - A Windows Update
    - A Windows Update for Business
    - A Windows Server Update Services
    - Configuration Manager

>[!IMPORTANT]
>Ezek nem tartalmaznak szoftvereket **nem** beépített Windows, amely automatikusan frissíti az interneten vagy harmadik féltől származó szoftvereket frissíti, hogy telepítve vannak a frissítési mechanizmusok, fent említett, az interneten keresztül. Csak olyan szoftver változásainak üzembe helyezett, ha a Configuration Manager-ügyfél itt megadotton kívül futtatásához.

## <a name="before-you-start"></a>Előkészületek

Konfigurálása előtt, vagy telepítheti Eszközvédelem házirendeket, olvassa el a következő információkat:

- Őr eszközkezelés a Configuration Manager előzetes verziójú funkció, és változhat.
- Eszközvédelem használatához felügyelt számítógépekhez futnia kell a Windows 10 Enterprise Creators frissítéssel vagy újabb.
- Egy házirend feldolgozása sikeresen rendszerű ügyfélszámítógépen, a felügyelt telepítőjét, hogy az ügyfél a Configuration Manager van beállítva, és szoftverek központilag telepítve az SCCM használatával, a házirend feldolgozása után automatikusan megbízható. Nincs automatikusan megbízható által kezelt konfigurációs szoftvereket, a Eszközvédelem házirend feldolgozása előtt.
- Jelen kiadás előtti verziójában Miután egy ügyfél PC megkapja a központi telepítés Eszközvédelem házirend, azt fogja ügyfélfuttatási kétórás időszakon át ezzel a házirend-feldolgozási ideje. 
- Ügyfélszámítógépek rendelkeznie kell ahhoz, hogy sikeresen feldolgozandó Eszközvédelem házirend a tartományvezérlővel létesített kapcsolatot.
- A megfelelőség értékelésének alapértelmezett ütemezését Eszközvédelem házirendek, a telepítés során konfigurálható minden nap. A házirend feldolgozása problémákat figyelnek, ha a megfelelőség értékelésének ütemezését, hogy rövidebb, például 1 óránként konfigurálása előnyös lehet. Az ütemezés határozzák meg, hogy milyen gyakran ügyfelek újból megpróbálja feldolgozni egy Eszközvédelem házirend hiba esetén.
- Függetlenül a kényszerítési mód, akkor válassza, ha Eszközvédelem házirendet telepít, ügyfélszámítógépek nem tudnak a bővítmény .hta HTML-alkalmazások futtatásához.

## <a name="how-to-create-a-device-guard-policy"></a>Egy Eszközvédelem házirend létrehozása
1.    Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.
2.    Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **Endpoint Protection**, és kattintson a **őr Eszközházirendek**.
3.    A a **Home** lap a **létrehozása** csoportjában kattintson a **eszköz őr házirend létrehozása**.
4.    Az a **általános** oldalán a **eszköz őr házirend létrehozása varázsló**, adja meg a következőket:
    - **Név** -adjon meg egy egyedi nevet a Eszközvédelem házirend. 
    - **Leírás** : nem kötelezően, adjon meg egy leírást a házirendet, amely segít azonosítani a Configuration Manager-konzolon.
    - **Érvényesítési mód** -válassza a következő érvényesítési módszer Eszközvédelem PC az ügyfélen.
        - **Érvényesítési engedélyezve** – csak engedélyezése a megbízható végrehajtható fájlok futtatásának engedélyezése.
        - **Csak naplózási** - engedélyezése az összes ilyen programok futtatását, de a napló nem megbízható végrehajtható fájlok, amelyek az ügyfél helyi eseménynaplóban futnak.
5.    Kattintson a **következő**, majd fejezze be a varázslót.

## <a name="how-to-deploy-a-device-guard-policy"></a>Eszközvédelem házirend központi telepítése
1.    Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.
2.    Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **Endpoint Protection**, és kattintson a **őr Eszközházirendek**.
3.    Házirendek, válassza ki az egyik szeretné telepíteni, majd válassza a listából a **Home** lap a **telepítési** csoportjában kattintson **telepítés**.
4.    Az a **eszköz őr házirend telepítése** párbeszédpanelen válassza ki azt a gyűjteményt, amelyhez a szabályzatot telepíteni szeretné az ügyfelek fogja kiértékelni a házirend, és végül válassza ki, hogy az ügyfél meg tudja határozni a beállított karbantartási időszakokon kívül történjen a házirend ütemezésének beállítása.
5.    Ha elkészült, kattintson a **OK** a szabályzatot telepíteni szeretné. 

Rendszerű ügyfélszámítógépen a csoportházirend feldolgozása után a számítógép újraindítását, hogy az ügyfélszámítógépek megfelelően a ütemezi a **ügyfélbeállítások** a **indítsa újra a számítógépet**.
**Amíg újra nem indítja az ügyfélszámítógépen, a házirend nem lépnek érvénybe.**

## <a name="how-to-monitor-a-device-guard-policy"></a>Eszközvédelem házirend figyelése

Az információk a [megfelelőségi beállítások figyelése](/sccm/compliance/deploy-use/monitor-compliance-settings) témakör segítséget nyújt a figyelheti a telepített szabályzatok azt telepítve van minden számítógépre megfelelően.

A következő naplófájl ügyfél számítógépek használatával figyelheti egy Eszközvédelem házirend feldolgozása:

**%Windir%\CCM\Logs\DeviceGuardHandler.log**

Az adott szoftver folyamatban, vagy az ellenőrzött ellenőrzéséhez tekintse meg a következő helyi ügyfelek eseménynaplóinak. Az eseménynaplóban a megfelelő naplókat a következők:

1.    Blokkolja-e, és végrehajtható fájlok naplózását, használja **alkalmazási és Szolgáltatásnaplójában** > **Microsoft** > **Windows** > **Kódintegritási** > **Operational**.
2.    Blokkolását, és a Windows Installer és a parancsfájlok naplózását, használja a **alkalmazási és Szolgáltatásnaplójában** > **Microsoft** > **Windows** > **AppLocker** > **MSI és parancsfájl**.

## <a name="security-and-privacy-information-for-device-guard"></a>Eszközvédelem kapcsolatos biztonsági és adatvédelmi tudnivalókat

- A kiadás előtti verziójában nem kell telepítenie a kényszerítési mód Eszközvédelem szabályzatok **csak naplózási** éles környezetben. Ebben a módban készült segítséget nyújtanak a funkció csak laboratóriumi tesztelése.
- A szabályzatot az eszközök **csak naplózási** módban, vagy eszközökre, amelyeken a szabályzatot a **kényszerítési engedélyezett** mód, amely rendelkezik még nem indították újra a házirend kikényszerítésére ki téve a nem megbízható szoftver telepítése folyamatban.
Ebben a helyzetben az továbbra is engedélyezni szeretné a futtatását, még akkor is, ha az eszköz újraindul, előfordulhat, hogy a szoftver vagy megkapja a házirendet a **kényszerítési engedélyezett** mód.
- Győződjön meg arról, hogy a Eszközvédelem házirend érvényben, az eszköz laborkörnyezetben előkészítése, üzembe helyezés a **kényszerítési engedélyezett** házirendet, majd indítsa újra az eszközt, az eszköz végfelhasználóknak átadása előtt.
- Ne telepítsen egy házirend **kényszerítési engedélyezett**, és később központilag telepítheti egy házirend **csak naplózási** ugyanarra az eszközre. Emiatt előfordulhat, hogy a nem megbízható szoftver futtathat.
- A Configuration Manager ügyfél számítógépek Eszközvédelem házirendekkel konfigurálható kódintegritás engedélyezéséhez használatakor vegye figyelembe, hogy a házirend **nem** játsszák ki a Eszközvédelem házirend, vagy ellenkező esetben a nem megbízható szoftver végrehajtása helyi rendszergazdai jogosultságokkal rendelkező felhasználók. 
- A csak konfigurálható a kódintegritás letiltása a helyi rendszergazdai jogosultságokkal rendelkező felhasználók számára, egy aláírt bináris házirendet, amely a csoportházirenden keresztül lehetséges, de jelenleg nem támogatott a Configuration Manager telepítéséhez.
- Az AppLocker-házirendek a Configuration Manager beállítása, egy felügyelt telepítő ügyfél-számítógépeken használja. Az AppLocker csak felügyelt telepítők azonosításához, és minden kényszerítési fordul elő, ha a kódintegritás konfigurálható. 





