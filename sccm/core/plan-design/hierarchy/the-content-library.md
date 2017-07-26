---
title: "A tartalomtár |} Microsoft Docs"
description: "Ismerje meg a tartalomtár, amely a System Center Configuration Manager a terjesztett tartalom teljes méretének csökkentésére használ."
ms.custom: na
ms.date: 2/14/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d31fecdb71b498864df2bce7403a4290ea9700ae
ms.openlocfilehash: 0fa9f431c00476d71b2b08f92f914d76636d1a27
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-in-system-center-configuration-manager"></a>A tartalomtár a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A tartalomtár egy egypéldányos tár a System Center Configuration Manager használ a kombinált törzse terjesztett tartalom teljes méretének csökkentésére tartalom. A tartalomtár tárolja a szoftverfrissítések, alkalmazások, operációs rendszerek központi telepítését, és így tovább tartozó összes tartalomfájlt.

 - A tartalomtár egy példányát az automatikusan létrehozott és megőrzi minden egyes **helykiszolgáló** és minden egyes **terjesztési pont**.

 - Mielőtt a Configuration Manager letölti a helykiszolgálóra, vagy a terjesztési pontokra másolja a fájlokat, a Configuration Manager ellenőrzi, hogy egyes tartalomfájlok már eleve a tartalomtárban.
 - Ha a tartalomfájl elérhető, a Configuration Manager nem másolja a fájlt, és hozzárendeli a meglévő tartalomfájlt az alkalmazáshoz vagy csomaghoz.

Azokon a számítógépeken, ahol terjesztési pontot telepít konfigurálhatja:

- Egy vagy több lemezmeghajtót amelyen szeretné létrehozni a tartalomtárat.
- Minden egyes használt meghajtó prioritását.

Ha a Configuration Manager a tartalomfájljait másolja, másolja át azokat az a legnagyobb prioritású meghajtóra amíg kevesebb, mint a minimális szabad területnél.
- A meghajtóbeállítások a terjesztési pont telepítése közben konfigurálhatók.
- A meghajtóbeállítások a terjesztési pont tulajdonságainak nem konfigurálhatók, a telepítés befejezése után.


A meghajtóbeállítások a terjesztési pont konfigurálásával kapcsolatos további információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


>  [!IMPORTANT]  
>  Helyezze át a tartalomtár egy másik helyre a terjesztési pont telepítése után, használja a **Content Library Transfer eszközt** a System Center 2012 R2 Configuration Manager eszközkészletben található. Letöltheti az eszközkészletet a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

## <a name="about-the-content-library-on-the-central-administration-site"></a>A központi adminisztrációs helyen a tartalomtár ismertetése  
 Alapértelmezés szerint a Configuration Manager létrehoz egy tartalomtárat a központi adminisztrációs helyen a hely telepítésekor. A tartalomtár a helykiszolgálón, a legtöbb szabad lemezterülettel rendelkező meghajtójára kerül. A központi adminisztrációs helyen lévő terjesztési pont nem tudja telepíteni, mert a tartalomtár által használható meghajtók nem rangsorolhatók. Hasonlóan a tartalomtár más helykiszolgálókon és terjesztési pontokon, amikor a a tartalomtárat magában foglaló meghajtón elfogy a szabad lemezterület, a tartalomtár automatikusan átterjed a következő rendelkezésre álló meghajtóra.  

 A Configuration Manager a tartalomtár a központi adminisztrációs helyen a következő esetekben használja:  

-   Amikor tartalmat hoz létre a központi adminisztrációs helyen.  

-   Ha tartalmat át egy másik Configuration Manager-helyről, és rendelje hozzá a központi adminisztrációs hely, amely felügyeli a tartalom helyeként.  

> [!NOTE]  
>  Ha egy elsődleges helyen hozza létre a tartalmat, és majd továbbítja azt egy másik elsődleges hely vagy egy másik elsődleges hely alatti másodlagos helyre, a központi adminisztrációs hely átmenetileg a központi adminisztrációs hely az ütemező várólistájában tárolja tartalmat, de nem adja hozzá ezt a tartalmat a tartalomtárba.  

 A következő beállítások segítségével a központi adminisztrációs helyen lévő tartalomtár kezeléséhez:  

-   A tartalomtár egy adott meghajtón telepítését, hozzon létre egy üres fájlt **no_sms_on_drive.sms**, majd másolja azt a meghajtó gyökérmappájába a tartalomtár létrehozása előtt.  

-   A tartalomtár létrehozása után a **Content Library Transfer eszközt** a a System Center 2012 R2 Configuration Manager eszközkészletben a tartalomtár helyének kezeléséhez. Letöltheti az eszközkészletet a [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

