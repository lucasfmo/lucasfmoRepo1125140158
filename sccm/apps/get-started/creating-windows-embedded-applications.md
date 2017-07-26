---
title: "Windows Embedded-alkalmazások létrehozása |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozásakor és központi telepítése a Windows Embedded-eszközökhöz készült alkalmazások."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16acfd63-0c40-424c-82f4-8c63f7f1c30b
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: cb0c22f3060ba654778dca958d620f1e1725b93c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-embedded-applications-with-system-center-configuration-manager"></a>Windows Embedded-alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az egyéb System Center Configuration Manager követelményei és eljárásai alkalmazások létrehozására vonatkozó, felül kell vennie az alábbiakat is figyelembe létrehozása és központi telepítésekor a Windows Embedded-eszközökhöz készült alkalmazások.  

## <a name="general-considerations"></a>Általános megfontolások  

-   Amikor telepíti a Windows Embedded-eszközökön, amelyek engedélyezve vannak írási szűréshez, azt megadhatja, hogy letiltja az írási szűrő, az eszközön az alkalmazás központi telepítése során. Ezután kiválaszthatja az alkalmazás telepítését követő újraindítása előtti az írási szűrő. Ha az írási szűrő nincs letiltva, a szoftver központi telepítése átmeneti területre történik. Ez azt jelenti, hogy másik központi telepítésnek kényszeríti megőrizni a módosításokat, ha a szoftver már nem telepíti az eszköz újraindításakor.  

-   Amikor alkalmazást telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal. Ilyen módon felügyelheti, hogy az írási szűrő mikor van letiltva és engedélyezve, és az eszköz mikor indul újra.  

-   Az írási szűrő viselkedését vezérlő beállítás nevű jelölőnégyzet **változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)**.  

## <a name="tips-for-deploying-applications"></a>Tippek alkalmazások központi telepítéséhez  

**Használja a szükséges alkalmazásokat, nem pedig a rendelkezésre álló alkalmazások Windows Embedded-eszközök, amelyeken írási szűrők engedélyezve van.** Mivel a felhasználók nem tudják telepíteni alkalmazásokat a Szoftverközpont egy Windows Embedded eszközön, amelyhez az írási szűrőket, a központi telepítésbe mindig a központi telepítési céllal **szükséges** helyett **elérhető** ezekre az eszközökre. Általában ezt nem meg probléma, mivel a Windows Embedded operációs rendszer gyakran futtatják az egyetlen alkalmazást, amely több felhasználóval ugyanúgy kell futnia. Ezért ezeket az eszközöket erősen figyeli és lezárja az informatikusi részleg. A kötelező alkalmazások az ilyen forgatókönyvhöz jól használhatók.

 Ha azonban a felhasználók több alkalmazást futtatnak az írási szűrőket tartalmazó beágyazott készülékeken, ezeket a felhasználókat ki kell oktatni a következő megszorításokra.  

-   A felhasználók nem telepíthetnek kötelező szoftvert a Szoftverközpontból.  

-   A felhasználók nem változtathatják meg a Szoftverközpont Beállítások lapján a munkaóráikat.  

-   A felhasználók nem halaszthatják el a kötelező alkalmazás telepítését.  

Ezenkívül alacsony szintű jogosultsággal rendelkező felhasználók nem jelentkezhetnek be a karbantartási időszak alatt, ha a Configuration Manager változtatásokat végez a szoftver telepítésein és frissítésein. Ezen időszak alatt a felhasználók olyan üzenetet láthatnak, hogy a készülék szervizelés miatt nem használható.  

**Ne telepítsen alkalmazásokat a Windows Embedded-eszközökre, amelyeken írási szűrők engedélyezve van, ha az alkalmazások a felhasználónak kell fogadnia a licencfeltételeket.** Ha az írási szűrők le vannak tiltva, hogy a Configuration Manager mikor telepíthet szoftvereket az embedded-eszközök esetén alacsony szintű jogosultsággal rendelkező felhasználók nem jelentkezhetnek be az eszközre. Ha a telepítés azt igényli, hogy a felhasználó fogadja el a licencfeltételeket, ezt nem lehet megtenni, és a telepítés sikertelen lesz. Legyen biztos benne, hogy nem végzi szoftver központi telepítését Windows Embedded-eszközökre, ha a telepítés felhasználói beavatkozást igényel. Az ilyen operációs rendszerek szűréséhez használja a megfelelő platformok listáját.  

