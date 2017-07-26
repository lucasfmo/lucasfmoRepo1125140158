---
title: "Konzol telepítése |} Microsoft Docs"
description: "Olvassa el a központi adminisztrációs hely vagy elsődleges hely kapcsolódni a Configuration Manager konzol telepítése."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b6b47fd1f56780a40c96b5e228046b41fe3a9a47
ms.openlocfilehash: 88ecbc48fd03ce988f04408d0378844cbed1de2b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="install-the-system-center-configuration-manager-console"></a>A System Center Configuration Manager konzol telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A rendszergazdák a System Center Configuration Manager konzol segítségével kezelése a Configuration Manager környezethez. Minden egyes Configuration Manager konzol egy központi adminisztrációs hely vagy elsődleges helyhez kapcsolódhatnak. A Configuration Manager konzol nem tud kapcsolódni egy másodlagos helyen.

> [!NOTE]  
>  Milyen objektumokat, a konzolt futtató rendszergazda számára megjelenített attól függ, hogy az a felhasználói fiókjukhoz rendelt engedélyek. Szerepkör alapú felügyelet kapcsolatos további információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 A Configuration Manager konzolt telepítheti a telepítővarázslót a helykiszolgáló telepítése során, vagy egy önálló telepítés alkalmazás, amely használja a telepítő varázsló futtatása.  

 A következő eljárás segítségével a Configuration Manager konzol telepítése a különálló alkalmazás használatával.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>A telepítővarázsló segítségével a Configuration Manager konzol telepítése  

1.  Győződjön meg arról, hogy megfelel a fenti követelményeknek:  

    -  Rendelkezik **helyi rendszergazdai** jogosultságokkal azon a számítógépen, amelyen a konzol futni fog.  

    -   Rendelkezik **olvasási** engedéllyel a hely a Configuration Manager-konzol telepítési fájljainak.  

2.  Nyissa meg a helyek egyikét:  

    -   A helykiszolgálón, Ugrás  **<* Configuration Manager helykiszolgáló telepítési elérési utat*> \Tools\ConsoleSetup**.  

    -   A Configuration Manager forrás-adathordozóján Ugrás  **<* Configuration Manager forrásfájljait*> \Smssetup\Bin\I386**.  

    > [!TIP]  
    >  Az ajánlott eljárás szerint kezdeményezni a Configuration Manager konzol telepítésének helykiszolgálóról, nem pedig a System Center Configuration Manager telepítési adathordozójáról. A hely kiszolgáló telepítési módszer másolja át a Configuration Manager konzoljának telepítési fájljait és a helyhez támogatott nyelvi csomagok a **tools\consolesetup mappába** almappájában. A Configuration Manager konzol telepítése a telepítési adathordozóról mindig az angol verziót, a támogatott nyelvektől a helykiszolgáló vagy az a számítógépen futó operációs rendszer nyelvi beállításaitól függetlenül telepíti. Másik lehetőségként másolhatja a **ConsoleSetup** mappát másik helyre a telepítés elindításához.

3.  A Configuration Manager konzol telepítő varázsló megnyitásához kattintson duplán **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Mindig telepítse a Configuration Manager konzol consolesetup.exe fájllal. A Configuration Manager konzol adminconsole.msi futtatásával telepíthető, bár ez a módszer nem futtatható az előfeltételeknek, vagy függőségi ellenőrzéseket, és a telepítés esetleg nem megfelelően telepített.  

4.  A varázslóban válassza **következő**.  

5.  Az a **helykiszolgáló** lapján adja meg a teljesen minősített tartománynevét (FQDN) a helyrendszer-kiszolgáló, amelyhez a Configuration Manager konzol kapcsolódni fog.  

6.  Az a **telepítési mappa** lapon, a telepítési mappa megadása a Configuration Manager konzolon. A mappa elérési útja nem végződhet szóközzel, és a Unicode-karaktereket tartalmazhat.  

7.  Az a **felhasználói élmény fokozása Program** lapján megadhatja, hogy csatlakozzon a felhasználói élmény fokozása Program (CEIP).  

8.  Az a **telepítésre kész** lapon jelölje be **telepítése** a Configuration Manager konzol telepítéséhez.  

## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>A Configuration Manager konzol telepítése a parancssorból  

1.  A kiszolgálón, amelyen a Configuration Manager konzol telepítéséhez nyisson meg egy parancssori ablakot, és nyissa meg az alábbi helyek egyikét:  

    -   **<*A Configuration Manager helykiszolgáló telepítési elérési utat*> \Tools\ConsoleSetup**  

    -   **<*Configuration Manager telepítési adathordozójáról*> \SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  Ha a Configuration Manager konzol telepítése a parancssorból, angol nyelvű mindig telepítve van, az a számítógépen futó operációs rendszer nyelvi beállításaitól függetlenül. A Configuration Manager konzol telepítése nem angol nyelvű, kell [a Configuration Manager konzol telepítése a telepítővarázsló segítségével](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  Írja be a parancssorba **consolesetup.exe**. Az alábbi parancssori kapcsolók közül választhat.  

|  Parancssori kapcsoló     | Leírás     |
  | :------------- | :------------- |
  |/q|A Configuration Manager konzol felügyelet nélküli telepítése. A **EnableSQM**, **TargetDir**, és **DefaultSiteServerName** beállítások szükségesek, ha ezt a beállítást használja.|  
  |/uninstall|Eltávolítja a Configuration Manager konzolon. Ez a beállítás először kell megadnia, amikor együtt használja a **/q** lehetőséget.|  
  |LangPackDir|Meghatározza a nyelvi fájlokat tartalmazó mappa elérési útját. Használhat **a telepítő letöltési segédprogramja** a nyelvi fájlok letöltéséhez. Ha nem használja ezt a beállítást, a telepítő a nyelvi csomagot az aktuális mappában keresi. Ha a mappa nem található, a telepítő angol nyelvet telepíti csak. További információkért lásd: [a telepítő letöltési segédprogramja](setup-downloader.md).|  
  |TargetDir|A Configuration Manager konzol telepítése a telepítési mappájának meghatározására szolgál. Ez a beállítás akkor szükséges, ha használja a **/q** lehetőséget.|  
  |EnableSQM|Való csatlakozást adja meg a felhasználói élmény fokozása Program (CEIP). Az érték **1** csatlakozni a felhasználói élmény fokozása program és érték **0** nem csatlakozni a programhoz. Ez a beállítás akkor szükséges, ha használja a **/q** lehetőséget.|  
  |DefaultSiteServerName|Adja meg az FQDN a helyrendszer-kiszolgáló, amelyhez a konzol csatlakozik a megnyitásakor. Ez a beállítás akkor szükséges, ha használja a **/q** lehetőséget.|  


  **Példák:**

  -  **consolesetup.exe /q TargetDir = "D:\Program Files\ConfigMgr" EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /q LangPackDir C:\Downloads\ConfigMgr TargetDir = "D:\Program Files\ConfigMgr" konzol EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com =**  

  -  **consolesetup.exe / uninstall /q**  

