---
title: "Lemezkép létrehozása OEM gyára vagy helyi raktár számára |} Microsoft Docs"
description: "A manuálisan előkészített adathordozóval végrehajtott központi telepítés segítségével csökkenthető a hálózati forgalom, miközben telepíti az operációs rendszer olyan számítógépre, amelyen nincsenek teljesen kiépítve."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7d3df90-062d-4d57-9e9d-e137d3e7cd7f
caps.latest.revision: 8
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 07aba04fb1b845e389a5f75b115d536136c1569c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-an-image-for-an-oem-in-factory-or-a-local-depot-with-system-center-configuration-manager"></a>Lemezkép létrehozása OEM gyára vagy helyi raktár számára a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A manuálisan előkészített adathordozóval végrehajtott központi telepítés a System Center Configuration Managerben lehetővé teszik, hogy az operációs rendszer telepítése olyan számítógépre, amelyen nincsenek teljesen kiépítve. A manuálisan előkészített adathordozó egy olyan Windows Imaging Format (WIM) fájl, amelyiket a gyártó (OEM), illetve a Configuration Manager környezethez nem csatlakoztatott vállalati előkészítő központ egy operációs rendszer nélküli számítógépre telepítve. A Configuration Manager környezethez, a számítógép elindul a rendszerindító lemezképet használja az adathordozón, a kivonatoló a rendszer ellenőrzi a manuálisan előkészített adathordozó, ellenőrizze, hogy érvényes, és majd a számítógép csatlakozik a helyfelügyeleti ponthoz az elérhető feladatütemezéseket, amelyek befejezik a letöltési folyamatot.


Ezzel a módszerrel csökkenthető a hálózati forgalom, mivel a rendszerindító lemezkép és az operációs rendszer lemezképe már a célszámítógépen van. Megadhatók a manuálisan előkészített adathordozóhoz hozzáadni kívánt alkalmazások, csomagok és illesztőprogram-csomagok. Miután az operációs rendszer már települt a számítógépre, a rendszer először ellenőrzi, hogy vannak-e alkalmazások, csomagok vagy illesztőprogram-csomagok a helyi feladatütemezési gyorsítótárban, és ha a tartalom nem található vagy módosítva lett, a rendszer letölti a tartalmat az előkészített médián konfigurált terjesztési pontról, majd telepíti azt.  

 A manuálisan előkészített adathordozó a következő operációsrendszer-telepítési helyzetekben használhatja:  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [Meglévő számítógép cseréje és a beállítások átvitele](replace-an-existing-computer-and-transfer-settings.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján készítheti elő és hozhatja létre a manuálisan előkészített adathordozót.  

## <a name="configure-deployment-settings"></a>Központi telepítési beállítások konfigurálása  
 Ha manuálisan előkészített adathordozót szeretne használni az operációs rendszer központi telepítésének folyamata során, úgy kell konfigurálnia a központi telepítést, hogy elérhetővé tegye az operációs rendszert adathordozók számára. Ezt a Szoftver központi telepítése varázsló **Központi telepítési beállítások** lapján, vagy a központi telepítés tulajdonságainak **Központi telepítési beállítások** lapján konfigurálhatja.  Az **Elérhetővé tétel a következők számára** beállításnál konfigurálja a következők egyikét:  

-   **Configuration Manager ügyfelek, média és PXE**  

-   **Csak média és PXE**  

-   **Csak média és PXE (rejtett)**  

## <a name="create-the-prestaged-media"></a>A manuálisan előkészített adathordozó létrehozása  
 A számítógépgyártó vagy a helyi raktár számára elküldeni kívánt manuálisan előkészített adathordozófájl létrehozása További információ: [Manuálisan előkészített adathordozó létrehozása a System Center Configuration Managerrel](create-prestaged-media.md).  

## <a name="send-the-prestaged-media-file-to-the-oem-or-local-depot"></a>A manuálisan előkészített adathordozófájl elküldése a számítógépgyártó vagy a helyi raktár számára  
 Küldje el az adathordozót a számítógépgyártó vagy a helyi raktár számára a számítógépek előkészítéséhez. A manuálisan előkészített adathordozófájl a számítógép egy formázott merevlemezén alkalmazható.  

## <a name="start-the-computer-to-install-the-operating-system"></a>A számítógép elindítása az operációs rendszer telepítéséhez  
 A rendszer alkalmazza a manuálisan előkészített adathordozófájlt a számítógépekre. A számítógép első elindításakor megkezdődik az operációs rendszer telepítési folyamata.  

