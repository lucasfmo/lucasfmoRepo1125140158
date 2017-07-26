---
title: "Indítás előtti parancsok feladatütemezési médiához |} Microsoft Docs"
description: "Hozzon létre egy parancsfájlt az indítás előtti parancshoz használható, az indítás előtti parancshoz kapcsolódó tartalmat terjeszteni, és konfigurálja az indítás előtti parancs adathordozón."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccc9f652-2953-4c38-8a90-c799484105ca
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 1c396534425179c6828d48acc578295167c566be
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prestart-commands-for-task-sequence-media-in-system-center-configuration-manager"></a>Indítás előtti parancsok feladatütemezési médiához a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager rendszerindító adathordozó, különálló adathordozókhoz és előkészített adathordozókhoz használandó indítás előtti parancsot hozhat létre. Az indítás előtti parancs olyan parancsfájl vagy végrehajtható fájl, amely még a feladatütemezés kiválasztása előtt fut, és képes a Windows PE környezetben a felhasználóval kommunikálni. Az indítás előtti parancs adatokat kérhet be a felhasználótól, és azokat a feladatütemezés környezetében mentheti, vagy feladatütemezés változójából tud adatokat lekérdezni. Amikor a célszámítógépen elindul a rendszer, a parancssor még az előtt fut, hogy a házirend letöltődne a felügyeleti pontról. Az alábbi eljárásokkal hozhat létre olyan parancsfájlt, amelyet az indítás előtti parancshoz használhat, terjesztheti vele az indítás előtti parancshoz kapcsolódó tartalmat, és konfigurálhatja az indítás előtti parancsot az adathordozón.  

## <a name="create-a-script-file-to-use-for-the-prestart-command"></a>Az indítás előtti parancshoz használható parancsfájl létrehozása  
 Feladatütemezési változók a Microsoft.SMS.TSEnvironment COM-objektummal olvashatók és írhatók a feladatütemezés futása közben. A következő példa egy olyan Visual Basic-parancsfájlt mutat be, amely az _SMSTSLogPath feladatütemezés-változó lekérdezésével határozza meg az aktuális napló helyét. A parancsfájl emellett egy egyéni változót is beállít.  

```  
dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")  
dim logPath  
' You can query the environment to get an existing variable.  
logPath = env("_SMSTSLogPath")  
' You can also set a variable in the OSD environment.  
env("MyCustomVariable") = "varname"  
```  

## <a name="create-a-package-for-the-script-file-and-distribute-the-content"></a>Csomag létrehozása a parancsfájlhoz és a tartalom terjesztéséhez  
 Miután létrehozta az indítás előtti parancshoz a parancsfájlt vagy végrehajtható fájlt, létre kell hoznia egy csomagforrást, amely a parancsfájlhoz vagy végrehajtható fájlhoz tartozó fájlokat tárolja, létre kell hoznia a fájlokhoz egy csomagot (program nem szükséges), majd a tartalmat továbbítania kell egy terjesztési pontra.  

 Egy csomag létrehozásával kapcsolatos további információkért lásd: [csomagok és programok](../../apps/deploy-use/packages-and-programs.md).  

 Tartalomterjesztési funkcióival kapcsolatos további információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

## <a name="configure-the-prestart-command-in-media"></a>Az indítás előtti parancs beállítása adathordozón  
 A Feladatütemezési média létrehozása varázslóval konfigurálhat indítás előtti parancsot különálló adathordozóhoz, rendszerindító adathordozóhoz vagy előkészített adathordozóhoz. További információ a az adathordozók típusairól: [feladatütemezési média létrehozása](../deploy-use/create-task-sequence-media.md). Az indítás előtti parancs adathordozón történő létrehozásához a következő eljárást használhatja.  

#### <a name="to-create-a-prestart-command-in-media"></a>Indítás előtti parancs létrehozása adathordozón  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezési média létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezési média létrehozása** elemre.  

4.  A **Válassza ki az adathordozó típusát** lapon adja meg a **Különálló adathordozó**, a **Rendszerindító adathordozó**vagy a **Manuálisan előkészített média**beállítást, majd kattintson a **Tovább**gombra.  

5.  Nyissa meg a varázsló **Testreszabás** lapját. A varázsló többi lapján megadandó konfigurálásával kapcsolatos további információkért lásd: [feladatütemezési média létrehozása](../deploy-use/create-task-sequence-media.md).  

6.  A **Testreszabás** lapon adja meg a következő adatokat, majd kattintson a **Tovább**gombra.  

    -   Adja meg az **Indítás előtti parancs engedélyezése**beállítást.  

    -   A **Parancssor** mezőbe írja be a parancsfájlt vagy végrehajtható fájlt, amelyet az indítás előtti parancshoz létrehozott.  

        > [!IMPORTANT]  
        >  Használjon **cmd /C < indítás előtti parancs\>**  az indítás előtti parancs megadásához. Ha például az indítás előtti parancshoz készített parancsfájl neve TSScript.vb, a **cmd /C TSScript.vbs** parancsot kell beírnia a parancssorba. A **cmd /C** előtag új parancsértelmező ablakot nyit a Windowsban, és a Path környezeti változó használatával keresi meg az indítás előtti parancs parancsfájlját vagy végrehajtható fájlját. Megadhatja az indítás előtti parancs teljes elérési útját is, de a meghajtó betűjele eltérő lehet a más meghajtókonfigurációval rendelkező számítógépeken.  

    -   Adja meg a **Tartalmazza az indítás előtti parancshoz szükséges fájlokat**beállítást.  

    -   A **Beállítás** elemre kattintva válassza ki az indítás előtti parancs fájljaihoz társított csomagot.  

    -   A **Tallózás** gombra kattintva kiválaszthatja az indítás előtti parancshoz tartozó tartalmat tároló terjesztési pontot.  

7.  Fejezze be a varázslót.  

