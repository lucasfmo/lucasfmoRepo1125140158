---
title: "Az Endpoint Protection-ügyfél súgója |} Microsoft Docs"
description: "Ismerje meg és az Endpoint Protection funkciókkal továbbfejlesztett szolgáltatásokat, a számítógép fenyegetésekkel szembeni hatékony védelmét."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: 6
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 212c73fcb947c3b56da6055bf47fe078301ad90d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection-client-help"></a>Az Endpoint Protection-ügyfél súgója

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Ebben a Windows Defender vagy az Endpoint Protection a számítógép fenyegetésekkel szembeni hatékony védelme érdekében az alábbi szolgáltatásokat tartalmazza:  

-   **Integráció a Windows tűzfallal.** Az Endpoint Protection telepítőprogramja lehetővé teszi a Windows tűzfal be- vagy kikapcsolását.  
-   **Hálózatvizsgáló rendszer.** Ez a funkció azáltal fokozza a valós idejű védelmet, hogy a hálózati forgalom folyamatos vizsgálatával megkönnyíti az ismert hálózati biztonsági rések kihasználásának proaktív módon való megakadályozását.  
-   **Kártevőirtó motor.** A valós idejű védelem talál, és leállítja a kártevő szoftverek telepítését és futtatását a számítógépen. A frissített, nagyobb teljesítményű motor hatékonyabb észlelési és kártevő-eltávolítási funkciókat kínál.  

A Windows Defender a Windows 10 operációs rendszer részeként elérhető lesz.  A Windows korábbi verzióiban a rendszergazda biztosíthat a Windows Defender vagy az Endpoint Protection felügyeleti szoftver használatával.

Megtalálhat listája [gyakori kérdések a Windows Defender és az Endpoint Protection](endpoint-protection-client-faq.md). Súgó, tekintse meg [hibaelhárítása a Windows Defender vagy az Endpoint Protection ügyfél](troubleshoot-endpoint-client.md). Új szolgáltatások listáját lásd: [Újdonságok a Windows Defender-ügyfél új](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## <a name="windows-firewall-integration"></a>Integráció a Windows tűzfallal  
 A Windows tűzfal megakadályozhatja, hogy támadók vagy kártevő szoftverek az interneten vagy a hálózaton keresztül hozzáférjenek a számítógéphez. Az Endpoint Protection telepítésekor a telepítővarázsló már ellenőrzi, hogy a Windows tűzfal be van-e kapcsolva. Ha szándékosan kapcsolta a Windows tűzfalat, elkerülheti a bekapcsolását, ha törli a jelet a megfelelő jelölőnégyzetből. A Windows tűzfal beállításait a Vezérlőpult rendszer- és biztonsági beállításainál bármikor módosíthatja.  

## <a name="network-inspection-system"></a>Hálózatvizsgáló rendszer  
 Egyre gyakrabban éri hálózati támadás a biztonsági réseket még azelőtt, hogy a szoftvergyártók a biztonsági frissítéseket elkészíthetnék és eljuttathatnák a felhasználókhoz. A biztonsági résekkel kapcsolatos tanulmányok szerint egy új típusú támadást követően egy hónapig vagy még több ideig is eltarthat a megfelelő biztonsági frissítés létrehozása, tesztelése és kibocsátása. Emiatt sok számítógép hosszú időre védtelenné válik a támadásokkal szemben. A hálózatvizsgáló rendszer valós idejű védelmi funkciója azáltal tesz lehetővé hatékonyabb védekezést a hálózati támadásokkal szemben, hogy nagymértékben, több hétről néhány órára csökkenti a biztonsági rések felfedése és a megfelelő frissítések telepítése közötti időt.  

## <a name="award-winning-protection-engine"></a>Díjnyertes kártevőirtó motor  
 A Windows Defender vagy az Endpoint Protection technikai van a díjnyertes kártevőírtó motor, amely rendszeresen frissül. A motort a Microsoft kártevőkezelési központ kutatói gondozzák, folyamatos védelmet biztosítva a legújabb kártevőkkel szemben.  

## <a name="windows-defender-settings"></a>A Windows Defender beállításait
A Windows Defender beállításokat, amelyek segítenek megvédeni a Számítógépet olyan rosszindulatú szoftverektől-beállítások engedélyezése. A rendszergazda előfordulhat, hogy bizonyos Windows Defender beállításainak kezelése. A Windows Defender beállításokat használják, mások is kezelheti. Javasoljuk, hogy engedélyezze, hogy a Windows Defender beállításait a Számítógépről, majd az adatok védelme érdekében.

A Windows Defender beállításainak megtekintéséhez keresse meg `Windows Defender` a számítógépen. Nyissa meg **Windows Defender** válassza **beállítások**. A Windows Defender beállítások a következők:
- **A valós idejű védelem** - található, és állítsa le a kártevő szoftverek telepítését és futtatását a számítógépen.
- **Felhő alapú védelem** -a Windows Defender küld adatokat a Microsoft kapcsolatos esetleges biztonsági fenyegetéseket jelezhetnek.
- **Automatikus mintaküldési jelentés** -engedélyezése a Windows Defender gyanús fájlok minták küldeni a Microsoft kártevő-észlelési javítása érdekében.
- **Kizárások** -normálérték megadott fájlok, mappák, fájltípusok vagy a Windows Defender ellenőrzését folyamatok is.
- **Értesítési fokozott** -lehetővé teszi, hogy tájékoztatja a számítógép állapotával kapcsolatos értesítések. Akkor is **ki** kritikus fontosságú értesítéseket kap.
- **A Windows Defender Offline** -Windows Defender Offline található, és távolítsa el a kártevő szoftverek segítségével is futtathatja. Ez a vizsgálat a számítógép újraindul, és körülbelül 15 percet vesz igénybe.

### <a name="see-also"></a>További információ  
 [Endpoint Protection-ügyfél gyakran ismételt kérdések](endpoint-protection-client-faq.md)   
 [A Windows Defender vagy az Endpoint Protection ügyfél elhárítása](troubleshoot-endpoint-client.md)

