---
title: "Endpoint Protection-ügyfél konfigurálása |} Microsoft Docs"
description: "Útmutató egyéni ügyfélbeállításokat az Endpoint Protection telepítését követően a hierarchiában lévő számítógép-gyűjteményekhez."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 1488aaa465fb9810bc1b641d41dad95189d37418
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="configure-custom-client-settings-for-endpoint-protection"></a>Az Endpoint Protection egyedi ügyfélbeállítások konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ezzel az eljárással egyéni ügyfélbeállításokat az Endpoint Protectiont, amely a hierarchiában lévő számítógépcsoportokon telepíthetők.

> [!IMPORTANT]
>  Csak konfigurálása az Endpoint Protection-ügyfél alapértelmezett beállításait, ha biztos abban, hogy azokat a hierarchiában lévő összes számítógépre alkalmazni szeretné.

## <a name="to-enable-endpoint-protection-and-configure-custom-client-settings"></a>Az Endpoint Protection engedélyezése és az egyéni ügyfélbeállítások konfigurálása

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

2.  Kattintson az **Adminisztráció** munkaterületen az **Ügyfél beállításai**elemre.

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson az **Egyedi ügyfél-eszközbeállítás létrehozása**elemre.

4.  Az **Egyedi ügyfél-eszközbeállítás létrehozása** párbeszédpanelen adja meg a beállításcsoport nevét és leírását, majd válassza az **Endpoint Protection**lehetőséget.

5.  A szükséges Endpoint Protection-ügyfél beállításainak konfigurálása. Konfigurálható Endpoint Protection ügyfélbeállításainak teljes listáját lásd: az Endpoint Protection szakasz [információ a System Center Configuration Manager ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md).

   > [!IMPORTANT]
   >  Az Endpoint Protection ügyfél beállításainak konfigurálása előtt telepítenie kell az Endpoint Protection helyrendszerszerepkör.

6.  Kattintson az **OK** gombra az **Egyedi ügyfél-eszközbeállítás létrehozása** párbeszédpanel bezárásához. Az új ügyfélbeállítások az **Adminisztráció** munkaterület **Ügyfélbeállítások** csomópontjában jelennek meg.

7.  Az egyéni ügyfélbeállításokat telepíteni kell egy gyűjteményre, hogy a rendszer használhassa őket. Válassza ki a telepíteni kívánt egyéni ügyfélbeállításokat, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Telepítés**elemre.

8.  Válassza ki azt a gyűjteményt a **Gyűjtemény választása** párbeszédpanelen, amelyre telepíteni szeretné az ügyfélbeállításokat, majd kattintson az **OK**gombra. Az új központi telepítés a Részletek ablaktábla **Központi telepítések** lapján lesz látható.

Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egy ügyfél házirend lekérésének kezdeményezése, lásd: a Configuration Manager-ügyfél szakaszt kezdeményezése Házirendlekérésről [ügyfélszoftverek kezelése a System Center Configuration Managerben](../../core/clients/manage/manage-clients.md).

## <a name="how-to-provision-the-endpoint-protection-client-in-a-disk-image-in-configuration-manager"></a>Az Endpoint Protection-ügyfél kiépítése lemezképben a Configuration Managerben
Az Endpoint Protection-ügyfél telepíthető olyan számítógépre, amely a Configuration Manager operációs rendszer központi telepítésének lemez kép forrásként használni kívánja. Ezt a számítógépet általában referencia-számítógépnek nevezik. Miután létrehozta az operációs rendszer képfájlját, majd segítségével a Configuration Manager operációs rendszerek központi telepítéséhez a lemezképet, amely tartalmazhat szoftvercsomagokat, például az Endpoint Protection az ügyfélszámítógépeken.

Ez a témakör az eljárások segítségével segítségével telepítheti és konfigurálhatja az Endpoint Protection-ügyfél egy referencia-számítógépen

### <a name="prerequisites-for-installing-the-endpoint-protection-client-on-the-reference-computer"></a>Az Endpoint Protection-ügyfélszoftver referencia-számítógépekre történő telepítésének előfeltételei
Az alábbi lista tartalmazza a referencia-számítógépen az Endpoint Protection-ügyfélszoftver telepítéséhez szükséges előfeltételeket.

-   Az Endpoint Protection ügyfél-telepítési csomaggal, hozzáféréssel kell rendelkeznie **scepinstall.exe**. Ez a csomag megtalálható a **ügyfél** mappában található a Microsoft System Center Configuration Manager telepítési mappájában a helykiszolgálón.

-   Győződjön meg arról, hogy az Endpoint Protection ügyfél központi telepítése konfiguráció szerint a vállalata által előírt, hozzon létre kártevőirtó-házirendet, és majd exportálja. Megadhatja, hogy az Endpoint Protection-ügyfél manuális telepítésekor alkalmazandó kártevőirtó-házirendet. További információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).

   > [!NOTE]
   >  Az **Alapértelmezett kártevőirtó ügyfélházirend** nem exportálható.

-   Ha az Endpoint Protection-ügyfelet a legfrissebb definíciókkal rendelkező telepíteni kívánja, akkor le kell töltenie ezeket a a [Microsoft Malware Protection Center](http://go.microsoft.com/fwlink/?LinkID=200965).

### <a name="how-to-install-the-endpoint-protection-client-software-on-the-reference-computer"></a>Az Endpoint Protection-ügyfélszoftver telepítése a referencia-számítógépre
Telepítheti az Endpoint Protection-ügyfélszoftver helyileg egy parancs parancssori futtatásával referencia-számítógépen. Ehhez előbb rendelkeznie kell a **scepinstall.exe**telepítőfájllal. Az ügyfélszoftvert egy előre beállított vagy egy korábban exportált kártevőirtó-házirend segítségével is telepítheti.

## <a name="to-install-the-endpoint-protection-client-from-a-command-prompt"></a>Az Endpoint Protection-ügyfélszoftver parancssori telepítése

1.  Másolás **scepinstall.exe** a a **ügyfél** mappába a számítógépen, amelyen szeretné az Endpoint Protection-ügyfélszoftver telepítéséhez a System Center Configuration Manager telepítési adathordozón.

2.  Nyisson parancssort rendszergazdai jogokkal, keresse meg a **scepinstall.exe** fájlt tartalmazó mappát, majd futtassa a következő parancsot – kívánság szerint további parancssori tulajdonságokat is hozzáadhat:

   ```
   scepinstall.exe
   ```

    Az alábbi parancssori tulajdonságok valamelyikét határozhatja meg:

   |Tulajdonság|Leírás|
   |--------------|-----------------|
   |/s|A megadása után csendes telepítésre kerül sor.|
   |/q|A megadása után csendes telepítőfájl-kibontásra kerül sor.|
   |/i|A megadása után normál telepítésre kerül sor.|
   |/noreplace|A megadása után a külső felektől származó kártevőirtó szoftverek nem törlődnek a telepítés során.|
   |/policy|Kártevőirtó házirendfájlt ad meg, amelyet a telepítés során az ügyfélszoftver beállításához kell használni.|
   |/sqmoptin|Megadja, hogy ez az ügyfélszoftver be legyen léptetve a Microsoft Felhasználói élmény fokozása programba.|

3.  Az ügyfélszoftver telepítésének befejezéséhez kövesse a képernyőn megjelenő utasításokat.

4.  Ha letöltötte a legfrissebb definíciófrissítési csomagot, másolja az ügyfélszámítógépre, majd kattintson rá duplán a telepítéshez.

   > [!NOTE]
   >  Az Endpoint Protection-ügyfél telepítésének befejezése után az ügyfél automatikusan ellenőrzi a definíciófrissítéseket. Ha az ellenőrzés sikeres, nem szükséges kézzel telepíteni a legfrissebb definíciófrissítési csomagot.

## <a name="to-install-the-client-software-with-an-antimalware-policy-from-the-command-prompt"></a>Az ügyfélszoftver telepítése parancssori kártevőirtó-házirend segítségével

1.  Másolás **scepinstall.exe** és az exportált vagy előre beállított kártevőirtó-házirendet arra a számítógépre, amelyen szeretné az Endpoint Protection-ügyfélszoftver telepítéséhez.

2.  Nyisson parancssort rendszergazdai jogokkal, keresse meg a **scepinstall.exe** fájlt és a kártevőirtó-házirendet tartalmazó mappát, majd futtassa a következő parancsot:

   ```
   scepinstall.exe /policy <full path>\<policy file>
   ```

3.  Az ügyfélszoftver telepítésének befejezéséhez kövesse a képernyőn megjelenő utasításokat.

4.  Ha letöltötte a legfrissebb definíciócsomagot, másolja az ügyfélszámítógépre, majd kattintson rá duplán a telepítéshez.

   > [!NOTE]
   >  Az Endpoint Protection-ügyfél telepítésének befejezése után az ügyfél automatikusan ellenőrzi a definíciófrissítéseket. Ha az ellenőrzés sikeres, nem szükséges kézzel telepíteni a legfrissebb definíciófrissítési csomagot.

## <a name="verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Az Endpoint Protection-ügyfélszoftver megfelelő telepítésének ellenőrzése
Telepítése után az Endpoint Protection-ügyfél a referencia-számítógépen, győződjön meg arról, hogy az ügyfélszoftver megfelelően működik-e.

### <a name="to-verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Az Endpoint Protection-ügyfélszoftver megfelelő telepítésének ellenőrzése

1.  A referencia-számítógépen nyissa meg a **System Center Endpoint Protection** a Windows értesítési területen.

2.  Az a **Home** lapján a **System Center Endpoint Protection** párbeszédpanelen ellenőrizze, hogy **valós idejű védelem** értéke **a**.

3.  Ellenőrizze, hogy a **Vírus- és kémprogram-definíciók** állapota **Naprakész**-e.

4.  Annak érdekében, hogy a referencia-számítógép készen álljon a lemezképkészítésre, válassza a **Teljes**lehetőséget az **Ellenőrzési beállítások**pontban, majd kattintson a **Vizsgálat**parancsra.

### <a name="how-to-prepare-the-endpoint-protection-client-for-imaging"></a>Az Endpoint Protection-ügyfélszoftver előkészítése a lemezképkészítésre
Miután ellenőrizte, hogy az Endpoint Protection ügyfél telepítve van megfelelően a referencia-számítógépen, előkészítheti a számítógépet, a lemezképpel végrehajtott telepítéshez. A következő lépésekkel az Endpoint Protection-ügyfél előkészítése a lemezképkészítésre.


Operációs rendszer központi telepítése a Configuration Manager kapcsolatos további információkért lásd: [a System Center Configuration Manager operációsrendszer-lemezképek kezelése](/sccm/osd/get-started/manage-operating-system-images).

### <a name="to-prepare-the-endpoint-protection-client-for-imaging"></a>Az Endpoint Protection-ügyfélszoftver előkészítése a lemezképkészítésre

1.  Jelentkezzen be rendszergazdai jogokkal rendelkező felhasználóként a referencia-számítógépen.

2.  Töltse le és telepítse a **PsTools** eszközt a [Windows SysInternals webhelyéről](http://go.microsoft.com/fwlink/?LinkId=215263) a TechNet oldalon.

3.  Nyisson meg egy rendszergazda jogú parancssort, keresse meg azt a mappát, amelybe a PsTools eszközt telepítette, majd írja be a következő parancsot:

   ```
   Psexec.exe -s -i regedit.exe
   ```

   > [!IMPORTANT]
   >  Körültekintően járjon el, ilyen módon; a beállításjegyzék-szerkesztővel futtatása során a PsExec.exe -s beállítás a beállításjegyzék-szerkesztő LocalSystem-jogokkal fut.

4.  Keresse meg és törölje a következő beállításkulcsokat a beállításjegyzék-szerkesztőben.

   > [!IMPORTANT]
   >  A beállításkulcsokat a referencia-számítógép lemezképkészítés előtti utolsó lépéseként kell törölnie. A beállításkulcsok jönnek létre újból, amikor az Endpoint Protection-ügyfél elindul. Ha újraindítja a referencia-számítógépet, ismét törölnie kell a beállításkulcsokat.

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID**

Miután végzett a fent leírt lépésekkel, előkészítheti a referencia-számítógépet a lemezképkészítésre. Operációs rendszer központi telepítése a Configuration Manager kapcsolatos további információkért lásd: [a System Center Configuration Manager operációsrendszer-lemezképek kezelése](/sccm/osd/get-started/manage-operating-system-images).

Az Endpoint Protection-ügyfélszoftvert tartalmazó képfájl központi telepítése, amikor az Endpoint Protection-ügyfélszoftver automatikusan jelenti ezt információkat a Configuration Manager-hely, amelyhez a számítógépet rendelték, majd sor kerül az ügyfélszámítógépre vonatkozó házirend letöltésére és alkalmazására.

