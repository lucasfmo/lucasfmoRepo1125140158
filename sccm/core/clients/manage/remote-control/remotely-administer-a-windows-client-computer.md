---
title: "Windows-számítógép távoli felügyelete |} Microsoft Docs"
description: "Windows rendszerű ügyfélszámítógépek távoli felügyelete a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 63113a2928c0aca292e6ca07ffe1187324801b7b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>Windows rendszerű ügyfélszámítógépek távoli felügyelete az System Center Configuration Manager használatával

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A távvezérlés használatának megkezdése előtt tanulmányozza át az alábbi témakörökben található tudnivalókat:  

-   [A System Center Configuration Manager Távvezérlés előfeltételei](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [A Távvezérlés konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

Itt három módon a távvezérlés megjelenítőjének elindítása:  

-   A Configuration Manager konzolon.  

-   A Windows parancssorába.  

-   A Windows **Start** menü a Configuration Manager konzolt futtató számítógépen a **a Microsoft System Center** program csoport.  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Ügyfélszámítógépek távoli felügyelete a Configuration Manager konzolról  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **eszközök** vagy **Eszközgyűjtemények**.  

3.  Válassza ki a távolról felügyelni kívánt számítógépet, majd a a **Home** lap a **eszköz** csoportjában válassza **Start** > **távvezérlési**.  

    > [!IMPORTANT]  
    >  Ha az **Adatkérés a felhasználónak a távvezérlés engedélyezéséhez** ügyfélbeállítás értéke **Igaz**, a kapcsolat addig nem indul el, amíg a felhasználó a távoli számítógépnél nem hagyja jóvá a távvezérlést. További információkért lásd: [a Távvezérlés konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/remote-control/configuring-remote-control.md).  

4.  A **Configuration Manager Távvezérlés** ablak megnyitását követően távolból felügyelheti az ügyfélszámítógépet. A kapcsolatot az alábbi beállításokkal konfigurálhatja.  

    > [!NOTE]  
    >  Ha csatlakoztatott a számítógéphez több monitor tartozik, a figyelők által megjelenített a távvezérlés ablakában jelenik meg.  

    -   **Fájl – kapcsolódás** -Csatlakozás másik számítógéphez. Ez a beállítás nem érhető el távvezérlési munkamenet során.  

    -   **Fájl – kapcsolat bontása** – leválasztja az aktív távvezérlési munkamenetet, de nem zárja be a **Configuration Manager Távvezérlés** ablak.  

    -   **Fájl – Kilépés** – leválasztja az aktív távvezérlési munkamenetet, és bezárja a **Configuration Manager Távvezérlés** ablak.  

        > [!NOTE]  
        >  Amikor leválasztja az aktív távvezérlési munkamenetet, a rendszer törli a megtekintett számítógépen a Windows vágólapon lévő tartalmat.  

    -   **Nézet – teljes képernyő** -a lehető legnagyobbra növeli a **Configuration Manager Távvezérlés** ablak.  

        > [!NOTE]  
        >  Ha ki szeretne lépni a teljes képernyős módból, nyomja le a Ctrl+Alt+Break billentyűkombinációt.  

    -   **Nézet – méret beállítása** -méretéhez a távoli számítógép megjelenítését méretezi a **Configuration Manager Távvezérlés** ablak.  

    -   **Nézet – állapotsor** -megjelenítését váltja a **Configuration Manager Távvezérlés** ablak állapotsorának.  

    -   **Művelet – Ctrl + Alt + Del kulcs küldése** -Ctrl + Alt + Del billentyűkombináció küldése a távoli számítógépen.  

    -   **Művelet – vágólapmegosztás engedélyezése** -lehetővé teszi, hogy másolja és illessze be a és a távoli számítógépről. Ha megváltoztatja ezt az értéket, a módosítás érvénybelépéséhez újra kell indítania a távvezérlési munkamenetet.  

        > [!NOTE]  
        >  Ha nem szeretné a vágólap megosztását engedélyezni a Configuration Manager konzolon, a konzolt futtató számítógépen állítsa a beállításkulcs **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing** való **0**.  

    -   **Művelet – Lock távoli billentyűzet és egér** -zárolja a távoli billentyűzetet és egeret zárolva megakadályozza a felhasználó működtesse a távoli számítógépet.  

    -   **Súgó - távvezérlés** -megjeleníti ithe jelenlegi verziójával a megjelenítőben.  

5.  A távoli számítógépen felhasználók megtekinthetik a távvezérlési munkamenetet, ha a Configuration Manager kattintva további információt**távvezérlési** a Windows tálca értesítési területén, illetve a távvezérlési munkamenet sávján látható ikonra.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>A Távvezérlés megjelenítőjének elindítása a a Windows parancssorából  

-   A Windows parancssorba írja be a *< Configuration Manager telepítési mappa\>***\AdminConsole\Bin\x64\CmRcViewer.exe**  

    > [!NOTE]  
    >  A CmRcViewer.exe az alábbi parancssori kapcsolókat támogatja:  
    >   
    >  -   *< cím\>*  -adja meg a NetBIOS-nevet, a teljesen minősített tartománynevét (FQDN) vagy az IP-cím, az ügyfélszámítógép, amelyhez csatlakozni kíván.  
    > -   *< helykiszolgáló neve\>*  -kívánt a távvezérlési munkamenet kapcsolódó állapotüzeneteket küldhet a System Center Configuration Manager-helykiszolgáló nevét adja meg.  
    > -   **/?** – A távvezérlés megjelenítőjének parancssori kapcsolóit jeleníti meg.  
    >   
    >  **Example:CmRcViewer.exe** *< cím\>*   *< \\\Site kiszolgáló neve >*  

