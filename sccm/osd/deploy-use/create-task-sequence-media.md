---
title: "Feladatütemezési adathordozó létrehozása a System Center Configuration Managerrel |} Microsoft Docs"
description: "Feladatütemezési adathordozó, például CD-ről, az operációs rendszer központi telepítéséhez a Configuration Manager környezetben célszámítógépre létrehozása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
caps.latest.revision: 8
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: bd5448d70c2d465347de840cb197d4c33075c90a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-task-sequence-media-with-system-center-configuration-manager"></a>Feladatütemezési adathordozó létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Media rögzítheti az operációs rendszer lemezképét a referencia-számítógépről, vagy a System Center Configuration Manager környezetben célszámítógépre az operációs rendszer központi telepítéséhez használható. A létrehozandó adathordozó lehet egy vagy több CD, DVD vagy USB flash meghajtó.  

 Adathordozó legtöbbször az operációs rendszer olyan célszámítógépre, amelyik nincs hálózati kapcsolat vagy egy kis sávszélességű kapcsolaton keresztül kell, hogy a Configuration Manager-hely telepítéséhez használatos. Létező Windows operációs rendszer hiányában azonban a telepítő adathordozó is használható az operációs rendszer elindításához. A telepítő adathordozó ilyen használata olyankor fontos, ha nincs a célszámítógépen operációs rendszer, illetve az operációs rendszer sérült vagy nem működik, továbbá akkor, ha a rendszergazda felhasználó újra akarja particionálni a célszámítógép merevlemezét.  

 A telepítő adathordozó lehet rendszerindító adathordozó, különálló adathordozó és előkészített adathordozó. A telepítő adathordozó tartalma a használt adathordozó típusától függően eltérő lehet. A különálló adathordozó például az operációs rendszert telepítő feladatütemezést tartalmaz, míg a más típusúak a feladatütemezést a felügyeleti pontról kérik le.  

> [!IMPORTANT]  
>  Feladatütemezési média létrehozása, hogy rendszergazdai jogokkal kell rendelkeznie a Configuration Manager konzolt futtató számítógépen. Ha nem rendszergazda, a Feladatütemezési média létrehozása varázsló elindításakor a rendszer felszólítja a rendszergazdai hitelesítő adatok megadására.  

##  <a name="BKMK_PlanCaptureMedia"></a>Média rögzítése az operációsrendszer-lemezképek  
 A Média rögzítése funkció lehetővé teszi, hogy az adathordozó referencia-számítógépről rögzítse az operációs rendszer lemezképét. Ez az adathordozó tartalmazza a referencia-számítógép rendszerindító lemezképét és az operációs rendszer lemezképét rögzítő feladatütemezést. További információk médiarögzítés létrehozásáról: [Médiarögzítés létrehozása System Center Configuration Managerrel](create-capture-media.md).  

##  <a name="BKMK_PlanBootableMedia"></a>Operációs rendszert telepítő rendszerindító adathordozó  
 Rendszerindító adathordozók tartalmazzák a csak a rendszerindító lemezképet, esetleg [indítás előtti parancsok](../understand/prestart-commands-for-task-sequence-media.md) és azokhoz szükséges fájlokat, és a Configuration Manager bináris fájljait. A célszámítógép elindításakor csatlakozik a hálózatra, és lekéri onnan a feladatütemezést, az operációs rendszer lemezképét és a szükséges egyéb tartalmat. Mivel a feladatütemezés nincs az adathordozón, a feladatütemezés és/vagy a tartalom megváltoztatható anélkül, hogy újabb adathordozót kellene létrehozni.  

> [!IMPORTANT]  
>  A rendszerindító adathordozón a csomagok nem titkosítottak. A rendszergazda felhasználónak kell gondoskodni az olyan biztonsági eszközökről, mint az adathordozó védelme jelszóval, hogy a csomag tartalma védve legyen a jogosulatlan felhasználóktól.  

 További információ a rendszerindító adathordozó létrehozása [létrehozásának folyamatáról](create-bootable-media.md).  

##  <a name="BKMK_PlanPrestagedMedia"></a>Operációs rendszert telepítő manuálisan előkészített adathordozó  
 A manuálisan előkészített adathordozó lehetővé teszi a rendszerindítás és az operációs rendszer lemezképének a merevlemezre előkészítését a szabályos használatba vétel előtt. A manuálisan előkészített adathordozó egy olyan Windows Imaging Format (WIM) fájl, amelyiket a gyártó, illetve a Configuration Manager környezethez nem csatlakoztatott vállalati előkészítő központ egy operációs rendszer nélküli számítógépre telepítve.  

 A manuálisan előkészített adathordozó tartalmazza a célszámítógép elindításához használt rendszerindító lemezképet és a célszámítógépre alkalmazható operációsrendszer-képet. Megadhatja a manuálisan előkészített adathordozó részét képező alkalmazásokat, csomagokat és illesztőprogram-csomagokat is. Az operációs rendszert telepítő feladatütemezést az adathordozó nem tartalmazza. Olyan feladatütemezés telepítésekor, amelyik manuálisan előkészített adathordozót használ, az ügyfél először a feladatütemezés gyorsítótárában keresi az érvényes tartalmat, és ha az nem található vagy megváltozott, letölti a tartalmat a terjesztési pontról.  

 A manuálisan előkészített adathordozót az új számítógép merevlemezére teszik mielőtt a számítógépet elküldenék a végfelhasználónak. A manuálisan előkészített adathordozó alkalmazása utáni első indításkor a Windows PE indul el a számítógépen, amely csatlakozik a felügyeleti ponthoz, hogy megkeresse az operációs rendszer telepítési folyamatát befejező feladatütemezést.  

> [!IMPORTANT]  
>  A manuálisan előkészített adathordozón a csomagok nem titkosítottak. A rendszergazda felhasználónak kell gondoskodni az olyan biztonsági eszközökről, mint az adathordozó védelme jelszóval, hogy a csomag tartalma védve legyen a jogosulatlan felhasználóktól.  

 A manuálisan előkészített adathordozó létrehozásával kapcsolatos további információkért lásd: [hozza létre a manuálisan előkészített adathordozó](create-prestaged-media.md).  

##  <a name="BKMK_PlanStandaloneMedia"></a>Operációs rendszert telepítő különálló adathordozó  
 A különálló adathordozó mindent tartalmaz, ami szükséges az operációs rendszer telepítéséhez. Ebbe beletartozik a feladatütemezés és az egyéb szükséges tartalom. Mivel minden, ami szükséges az operációs rendszer telepítéséhez az önálló adathordozón tárolódik, az önálló adathordozó lemezterület-igénye jelentősen nagyobb, mint a más típusú telepítőlemezeké.  

 Különálló adathordozó létrehozásával kapcsolatos további információkért lásd: [különálló adathordozó létrehozása](create-stand-alone-media.md).  

## <a name="media-considerations-when-using-site-systems-configured-for-https"></a>Adathordozó vonatkozású megfontolások a HTTPS használatára konfigurált helyrendszerek használatakor  
 Ha a felügyeleti pont és a terjesztési pontok a HTTPS kommunikáció használatára vannak konfigurálva, a rendszerindító adathordozót és a manuálisan előkészített adathordozót az elsődleges helyen kell létrehozni, nem a központi felügyeleti helyen. Annak eldöntéséhez, hogy az adathordozót dinamikusnak vagy hely alapúnak konfigurálja, fontolja meg a következőket is:  

-   Az adathordozó dinamikusnak konfigurálásához minden elsődleges helynek annak a helynek a legfelső szintű hitelesítésszolgáltatójával kell rendelkezni, amelyikről az adathordozót létrehozta. A legfelső szintű hitelesítésszolgáltatót a hierarchiában összes elsődleges helyre importálhatja.  

-   Használatakor a Configuration Manager-hierarchiában lévő elsődleges helyek más legfelső szintű hitelesítésszolgáltatókat, mindegyik helyen hely alapú adathordozót kell használnia.  

