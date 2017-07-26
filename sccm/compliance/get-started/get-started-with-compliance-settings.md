---
title: "A megfelelőségi beállítások beolvasása használatába |} Microsoft Docs"
description: "Tudnivalók a System Center Configuration Manager megfelelőségi beállítások működését. Emellett ismerje meg alapvető fogalmait, ismernie kell."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: f16c87dfd0c4f80d96aedf7f5f7497f2bbd4752a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>Bevezetés a System Center Configuration Manager megfelelőségi beállításainak használatába

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager-konfigurációelemek létrehozása előtt tekintse át a témakör megérteni a megfelelőségi beállítások működését, illetve az alapfogalmakat tudnia kell.  

## <a name="how-compliance-settings-works"></a>A megfelelőségi beállítások működése  
 Megfelelőségi beállítások segítségével konfigurációját és megfelelőségét a kiszolgálók, laptopok, asztali számítógépek és a szervezet mobileszközeinek kezelését.  

 A konfigurációelemek két fő kategóriába sorolhatók:  

-   **A Configuration Manager-ügyféllel kezelt eszközök beállításai** – általában eszközök, amelyeken telepítette a Configuration Manager ügyfélszoftver lehetővé teszi, hogy az eszköz felügyeletére.  

-   **A Configuration Manager-ügyfél nélkül kezelt eszközök beállításai** – általában a Microsoft Intune-nal vagy a Configuration Manager helyszíni felügyeleti (MDM) kezelt eszközökre.  

## <a name="what-devices-are-supported"></a>Támogatott eszközök  


|Eszköz típusa|További információ|  
|------------|----------------------|  
|Windows rendszerű számítógépek (a Configuration Manager-ügyfél)|Egyéni konfigurációs elemek létrehozását teszik lehetővé, melyekkel elemek, például beállításkulcsok, fájlok és Active Directory-attribútumok értékelhetők.<br /><br /> A Windows 10 konfigurációelem-típus használatakor egy előre megadott listából választhatja ki a kívánt beállításokat.|  
|Windows rendszerű számítógépek (regisztrálva a Microsoft Intune)|Egy előre megadott listából választhatja ki a kívánt beállításokat.|  
|iOS-eszközök (regisztrálva a Microsoft Intune)|Egy előre megadott listából választhatja ki a kívánt beállításokat.|  
|Android-eszközök (regisztrálva a Microsoft Intune)|Egy előre megadott listából választhatja ki a kívánt beállításokat.|  
|Windows Phone-eszközök (regisztrálva a Microsoft Intune)|Egy előre megadott listából választhatja ki a kívánt beállításokat.|  
|Mac számítógépek (a Configuration Manager-ügyfél)|Egyéni konfigurációs elemek létrehozását teszik lehetővé, melyekkel elemek, például a Mac OS X beállítások (tulajdonságlista) értékei értékelhetők, az eredményeket pedig egy parancsfájl adja vissza.|  
|Mac számítógépek (regisztrálva a Microsoft Intune)|Egy előre megadott listából választhatja ki a kívánt beállításokat.|  

## <a name="what-is-a-configuration-item"></a>Mi az a konfigurációs elemet?  
 A konfigurációelemek olyan tárolónak tekinthetők, amely a következő adatokat tárolja (a konfigurált adatok a konfigurációelem típusától függenek):  

-   **Észlelési módszerre vonatkozó adatok** (csak alkalmazásbeállításokat tartalmazó Windows-konfigurációelemek esetén) – egy adott alkalmazás Windows Installer-fájljának észlelésével vagy egy egyéni parancsfájl használatával lehetővé teszi annak észlelését, hogy az alkalmazás telepítve van-e.  

-   **Beállítások** – a beállítások azon üzleti vagy technikai feltételeket jelentik, melyeket a rendszer a megfelelőség az ügyféleszközökön való értékeléséhez használ. Megadhat új beállításokat, vagy kereshet a meglévő beállítások között egy referencia-számítógépen.  

-   **Megfelelőségi szabályok** – a megfelelőségi szabályok a konfigurációelemek megfelelőségét meghatározó feltételeket adják meg. Egy adott beállítás megfelelőségének értékeléséhez ahhoz legalább egy megfelelőségi szabálynak kell tartoznia. Egyes beállítások lehetővé teszik a nem megfelelőnek bizonyult értékek javítását. Létrehozhat új szabályokat, vagy tallózással megkereshet meglévő beállításokat bármelyik konfigurációelemben a benne található szabályok kijelöléséhez.  

-   **Támogatott platformok** – ezek a megadott eszközplatformok, melyeken a rendszer értékeli a konfigurációelem megfelelőségét. Ha egy olyan eszközre telepít egy konfigurációelemet, amely nem szerepel a támogatott platformok listáján, a rendszer nem értékeli annak megfelelőségét.  

## <a name="what-is-a-configuration-baseline"></a>Mi az a referenciakonfiguráció?  
 A rendszer egy referenciakonfiguráció meghatározásával értékeli a megfelelőséget, amely az értékelni kívánt konfigurációelemeket, illetve a szükséges megfelelőségi szintet leíró beállításokat és szabályokat tartalmazza. Ezeket a konfigurációs adatokat importálhat a Microsoft System Center Configuration Manager konfigurációs csomagokat, ajánlott eljárások a Microsoft és más gyártók, a Configuration Managerben, és hogy által meghatározott, majd importálása a Configuration Managerbe a weben. Emellett új konfigurációelemeket és referenciakonfigurációkat is létrehozhat.  

 Egy referenciakonfiguráció meghatározása után gyűjtemények segítségével telepítheti azt felhasználók számára és eszközökre, és egy ütemezés szerint értékelheti ki a megfelelőségi beállításait. Az eszközökre több referenciakonfiguráció is telepíthető. Ez magas szintű szabályozást tesz lehetővé.  

 Az ügyféleszközök minden telepített referenciakonfiguráció alapján értékelik a megfelelőségüket, és azonnal jelentik az eredményeket a helynek állapotjelző üzenetek és állapotüzenetek formájában. Ha egy ügyféleszköz az adott időpontban nem kapcsolódik a hálózathoz, de már letöltötte az adott telepített referenciakonfigurációkban hivatkozott konfigurációelemeket, értékeli a referenciakonfiguráció megfelelőségét. A megfelelőségi adatok az újbóli kapcsolódáskor lesznek elküldve.  

 Figyelheti, hogy az a referenciakonfiguráció megfelelőségértékelésének eredményeit a **központi telepítések** csomópontja a **figyelés** munkaterület nem felel meg, a hibák és a felhasználók és az érintett eszközök száma a leggyakoribb okok megtekintése a Configuration Manager konzolon. A megfelelőségi beállítások jelentéseinek futtatásával további részleteket is megismerhet, például hogy mely eszközök megfelelőek illetve nem megfelelőek, vagy hogy az adott számítógép a referenciakonfiguráció mely eleme miatt bizonyul nem megfelelőnek. Is nézet megfelelőségértékelési eredményeit a használatával a Configuration Manager ügyfélszoftvert futtató Windows rendszerű számítógépek a **konfigurációk** lapján **Configuration Manager** a Vezérlőpulton.  

## <a name="user-data-and-profiles-configuration-items"></a>Felhasználói adatokat és profilokat tartalmazó konfigurációelemek  
 Felhasználói adatokat és profilokat tartalmazó konfigurációelemek olyan beállításokat tartalmaznak, meghatározzák, hogy az a hierarchiában lévő felhasználók hogyan kezelhetik a mappa átirányítása, offline fájlokhoz és barangoló profilok a Windows 8 és újabb rendszerű számítógépeken. Felhasználói gyűjteményekben, és figyelheti a megfelelőségüket a **figyelés** csomópont a Configuration Manager konzol. Más konfigurációelemektől eltérően ezeket nem kell hozzáadni referenciakonfigurációkhoz a központi telepítésük előtt. Közvetlenül telepíthetők a **Felhasználói adatok és profilok konfigurációs elemének központi telepítése** párbeszédpanel használatával.  

 További információkért lásd: [felhasználói adatokat és profilokat tartalmazó konfigurációelemek létrehozása](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

## <a name="remote-connection-profiles"></a>Távoli kapcsolati profilok  
 A távoli kapcsolati profilok olyan eszközöket és erőforrásokat biztosítanak, melyek elősegítik a távoli kapcsolati beállítások létrehozását, központi telepítését és figyelését a szervezetben lévő eszközökön. Ezeknek a beállításoknak a központi telepítésével minimálisra csökkenthető a végfelhasználók részéről az erőfeszítés, amely a vállalati hálózaton működő számítógépeikhez való kapcsolódáshoz szükséges.  

További információkért lásd: [távoli kapcsolati profilok létrehozása](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

## <a name="windows-edition-upgrade"></a>Windows-kiadás frissítésének
A Kiadásfrissítési házirend lehetővé teszi bizonyos verzióit futtató Windows 10 újabb verzióra történő úgy, hogy megadja az új termékkulcs vagy licencelési fájl eszközök automatikus frissítését.

További információkért lásd: [frissítése Windows-eszközök a Kiadásfrissítési házirend frissítése](/sccm/compliance/deploy-use/upgrade-windows-version)

