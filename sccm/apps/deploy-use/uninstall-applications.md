---
title: "Alkalmazások eltávolítása |} Microsoft Docs"
description: "Az alkalmazás eltávolítása a System Center Configuration Manager használatával"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ea3edaa-27c6-4391-9896-cd97d9c5d06d
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2d0c0bc2e4e080e6061d8d3fe6cafd264d95c42a
ms.openlocfilehash: f42fee5974567f667c015a6b0bf34d9a9a7d2dab
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="uninstall-applications-with-system-center-configuration-manager"></a>A System Center Configuration Managerrel alkalmazások eltávolítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A következő műveletek egy korábban telepített alkalmazás telepítésének eltávolításához.

-   Adja meg a parancssor eltávolításához a központi telepítési típus tartalmának a **tartalom** a központi telepítési típus varázsló oldalán.  

-   Végezze el a az alkalmazás eltávolítását a központi telepítés **Eltávolítás**műveletével.  

> [!IMPORTANT]  
> Néhány alkalmazástípus nem támogatja az eltávolítást.  

 Ez a lista lehetővé teszi az alkalmazás eltávolítása működésével kapcsolatos további információk:  

-   Amikor eltávolítja a System Center Configuration Manager (a Configuration Manager) alkalmazások, a függő alkalmazások nem lesznek automatikusan eltávolítva.  

-   Ha olyan központi telepítésű alkalmazást távolít művelet **Eltávolítás** a felhasználóknak és az alkalmazás lett telepítve, a számítógép összes felhasználója számára, az eltávolítás sikertelen lehet, ha a felhasználó fiókjának nincs engedélye az alkalmazás telepítésének eltávolításához.  

-   Ha egy felhasználó vagy eszköz olyan gyűjtemény, amelyikhez hozzá központi telepítésű alkalmazás eltávolítja, az alkalmazás nem automatikusan törlődik az eszközről.  

-   Az olyan központi telepítés, amelynek a telepítési célja az **Eltávolítás** , nem ellenőriz a követelmény-szabályokkal. Ha az alkalmazás telepítve van azon a számítógépen amelyikre fut a központi telepítés, az el lesz távolítva.  

> [!IMPORTANT]  
> Egy alkalmazásnak gyűjteménybe irányuló központi telepítéseit vagy szimulált központi telepítéseit még azelőtt kell törölni, hogy az alkalmazást a központi telepítés **Eltávolítás**műveletével eltávolítaná.  

 A központi telepítési típus létrehozásával kapcsolatos további információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).  

 Az alkalmazás telepítésével kapcsolatos további információkért lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).  

## <a name="uninstall-an-application"></a>Alkalmazás telepítésének eltávolítása  

1.  Az alkalmazás központi telepítési típusának konfigurálása az Uninstall parancssorral, a következő módszerek egyikét használva:  

    -   Az a **általános** lapon a központi telepítési varázsló, válassza ki a beállítást **a telepítési fájlokban a központi telepítési típus automatikus azonosítása**. Ha az információ elérhető a telepítési fájlokban, az eltávolítási parancssor automatikusan hozzáadódik a központi telepítési típus tulajdonságaihoz.  

    -   Az a **tartalom** oldalán a központi telepítési típus varázsló, a a **eltávolítóprogram** mezőben adja meg a parancssort az alkalmazás telepítésének eltávolításához.  

        > [!NOTE]  
        >  A **tartalom** lap is megjelenik, csak akkor, ha a beállítást választja **a központi telepítési típus adatainak manuális megadása** a a **általános** a központi telepítési típus varázsló oldalán.  

    -   Az a **programok** lapján a  **<* központi telepítési típus neve*> Tulajdonságok ** párbeszédpanelen adja meg a parancssort az alkalmazás telepítésének eltávolításához a **eltávolítóprogram** mező.  

2.  Az alkalmazás központi telepítése, majd válassza ki a központi telepítési művelet **Eltávolítás** a a **központi telepítési beállítások** a szoftver központi telepítése varázsló oldalán.  

    > [!NOTE]  
    >  Ha a központi telepítés **Eltávolítás**műveletét választja, a központi telepítés céljaként automatikusan a **Kötelező**lesz konfigurálva.  

