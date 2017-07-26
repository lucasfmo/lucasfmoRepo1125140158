---
title: "A Technical Preview-ban 1610 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1610 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 59633ce68e2bb2d722900215751f345d6d098721
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>A rendszer 1610 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*



Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1610 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>A szűrőt az automatikus központi telepítési szabályokat a tartalom mérete alapján
Most már a szoftverfrissítések automatikus központi telepítési szabályokat a tartalom mérete alapján szűrhet. Például beállíthatja a **tartalom mérete (KB)** kiszűrik **< 2048** csak letölteni a szoftverfrissítéseket, amelyek 2 MB-nál kisebb. Szűrővel megakadályozza, hogy a nagy szoftverfrissítések automatikusan letöltse a jobb egyszerűsített támogatási Windows alacsonyabb szintű karbantartását, ha hálózati sávszélessége korlátozott. További információkért lásd: [Configuration Manager és a Windows karbantartási egyszerűsített le szint operációs rendszerre](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

#### <a name="to-configure-the-content-size-field"></a>A tartalom mérete mező konfigurálása
Konfigurálhatja a **tartalom mérete (KB)** mező, keresse fel a **szoftverfrissítések** automatikus központi telepítési szabály létrehozása varázsló egy automatikus központi telepítési szabály létrehozásakor, vagy lépjen a lap a **szoftverfrissítések** lapján egy meglévő automatikus központi telepítési szabály.

![Tartalom mérete mező](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>Szükséges szoftverek párbeszédpanelek továbbfejlesztett funkciók
Amikor a felhasználó kap a kötelező szoftverek, a **emlékeztet és Emlékeztessen:** beállítást, és kiválaszthatja, melyik értékeket az alábbi legördülő listából:
- Később: meghatározza, hogy értesítések beütemezve az Ügyfélügynök az értesítési beállítások alapján.
- Rögzített ideje: meghatározza, hogy az értesítés megjelenítése a kijelölt időszak után ütemezi. Például ha a felhasználó megadja 30 perc, az értesítés jelenik meg ismét 30 perc múlva.

![Az Ügyfélügynök számítógép lap](media/computeragentsettings.png)

A maximális időtartamot mindig alapján minden időpontban a központi telepítés ütemterv mentén a ügyfélügynökében beállított értesítési értékek. Például ha a **központi telepítés határideje 24 óránál közelebbi, emlékeztesse a felhasználók (óránként)** a Számítógépügynök beállítása lapon beállított 10 óra, és a határidő előtt több mint 24 órája párbeszédpanel indításakor, a felhasználó akkor jelenik meg emlékeztető lehetőségekkel legfeljebb de soha nem több mint 10 óra. Megközelíti a határidő lejártakor, mivel a párbeszédpanel kevesebb lehetőséget, a megfelelő az egyes összetevők a központi telepítés ütemterv ügyfélügynökében konzisztens jelennek meg.

Magas kockázatú központi telepítésnek, például egy feladatütemezés egy operációs rendszert központilag telepítő értesítési végfelhasználói élményt pedig most a leginkább zavaró beavatkozás. Helyett egy átmeneti értesítési, minden alkalommal, amikor a felhasználó értesítést kap, hogy a kritikus szoftverkarbantartást kell megadni egy párbeszédpanel a következő jelennek meg a felhasználó például:

![Szükséges szoftverek párbeszédpanel](media/requiredsoftwaredialog.png)


További információ:
- [Magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Ügyfélbeállítások konfigurálása](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>Korábban már jóváhagyott alkalmazáskérelmeinek megtagadása

Rendszergazdaként egy korábban már jóváhagyott alkalmazásigénylés most megtagadja. Egyszer tagadva, az alkalmazás telepítéséhez újabb felhasználók kell küldje el újra a kérelmet. Megtagadás nem távolítja el az alkalmazást; Ahelyett, hogy az adott alkalmazáshoz, hogy a felhasználó az összes új kérelem reapproval kényszerül. Alkalmazás igénylés megtagadásának korábban csak nem jóváhagyott alkalmazások kérésekhez áll rendelkezésre.

#### <a name="try-it-out"></a>Próbálja ki
Visszautasítja a kérelmet jóváhagyta a kérést:

1.    A Configuration Manager konzolon [hozzon létre és telepítsen egy alkalmazást](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications) , jóváhagyást igényel.
2.    Egy ügyfélszámítógépen nyissa meg a Szoftverközpontban, és az alkalmazás igénylésének küldése.
3.    A Configuration Manager konzolon az alkalmazás kérelem jóváhagyása.
4.    A jóváhagyott alkalmazásigénylés megtagadása: A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **jóváhagyási kérelmek** válassza ki az alkalmazás-kérelmekre, ha szeretné letiltani.  Kattintson a menüszalagon található **Megtagadás**.

## <a name="exclude-clients-from-automatic-upgrade"></a>Ügyfelek kizárása az automatikus frissítés
Technical Preview 1610 vezet be egy új beállítás segítségével-gyűjtemény kizárása az ügyfelek automatikusan a frissített ügyfél-verziónkénti telepítését.  Automatikus frissítés, valamint az egyéb módszerek, például a szoftverfrissítés-alapú, a parancsfájlok és a csoportházirend vonatkozik. Ez az ügyfél frissítésekor nagyobb figyelmet igénylő számítógépek gyűjteményét is használható. Egy ügyfél, amely egy kizárt gyűjtemény figyelmen kívül hagyja a kérelmek frissített ügyfélszoftver telepítéséhez.

### <a name="configure-exclusion-from-automatic-upgrade"></a>Kizárás az automatikus frissítés konfigurálása
Az automatikus frissítési kizárások konfigurálása:
1.    Nyissa meg a Configuration Manager konzolon **Hierarchiabeállítások** alatt **felügyeleti > Helykonfiguráció > helyek**, majd válassza ki a **ügyfélfrissítési** fülre.
2.    Jelölje be a **kizárási megadott frissítésből ügyfelek**, és majd a **kizárási gyűjtemény**, válassza ki a kizárni kívánt gyűjteményt. Egyetlen gyűjtemény kizárásra jelölhet ki.
3.    Kattintson a **OK** bezárásához és a konfiguráció mentéséhez. Ezt követően ügyfelek frissítési házirendet, miután a kizárt gyűjteményben lévő ügyfelek már nem automatikusan telepíti a frissítéseket a kliens szoftver.

  ![Az automatikus frissítési kizárási beállításai](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> Bár a felhasználói felület, hogy az ügyfelek nem frissülnek a a módszerrel, kétféleképpen felülírja ezeket a beállításokat is használhatja. Az ügyfélleküldéses telepítés és a kézi ügyféltelepítés segítségével bírálja felül ezt a konfigurációt. További részletekért tekintse meg a következő szakaszban.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Egy ügyfél, amely egy kizárt gyűjtemény frissítése
Mindaddig, amíg egy gyűjteményt ki lesznek zárva van konfigurálva, a gyűjtemény tagjai csak az ügyfélszoftvert frissíteni a két módszer, amelyek felülírják a kizárási veheti fel:
 - **Az Ügyfélleküldéses telepítés** – ügyfélleküldéses telepítés segítségével olyan ügyfél, amely egy kizárt gyűjtemény frissítése. Ez akkor tekinthető kell a rendszergazda szándéka szerint engedélyezett, és lehetővé teszi, hogy frissítse az ügyfeleket a teljes gyűjteményt a kizárási eltávolítása nélkül.       
 - **Kézi ügyféltelepítés** – manuálisan frissítheti a lévő ügyfelek egy kizárt gyűjtemény a ccmsetup a következő parancssori kapcsoló használata esetén: ***/ignoreskipupgrade***

  Ha egy ügyfél, amely tagja a kizárt gyűjtemény manuális frissítésére tett kísérlet, és ne használja ezt a kapcsolót, az ügyfél nem telepíti az új ügyfélszoftvert. További információ: [telepítése a Configuration Manager ügyfelek manuális](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually).

Az ügyfél-telepítési módszerekről további információkért lásd: [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

## <a name="windows-defender-configuration-settings"></a>A Windows Defender konfigurációs beállításai

Most már konfigurálhatja a Windows Defender-ügyfél beállításainak a Intune-ban regisztrált Windows 10 számítógépeknél konfigurációs elemek a Configuration Manager konzolon.

Pontosabban a következő Windows Defender beállításokat konfigurálhatja:
- Valós idejű figyelés engedélyezése
- Viselkedésfigyelés engedélyezése
- Hálózatfelügyeleti rendszer engedélyezése
- Minden letöltött fájl vizsgálata
- Szkriptek ellenőrzésének engedélyezése
- Fájl- és programtevékenység figyelése
  - Figyelt fájlok
- Ártalmatlanított kártevő szoftverek követése (nap)
- Ügyfél-Kezelőfelület elérésének engedélyezése
- Rendszervizsgálat ütemezése
  - Ütemezett nap
  - Ütemezett időpont
- Napi gyors vizsgálat ütemezése
  - Ütemezett időpont
- A vizsgálat vizsgálat során korlát CPU-használat % fájlok archiválása
- E-mail üzenetek vizsgálata
- Cserélhető adathordozók vizsgálata
- Csatlakoztatott meghajtók ellenőrzése
- A hálózati megosztások megnyitott fájlok vizsgálata
- Aláírás-frissítési időköz
- Felhővédelem engedélyezése
- Kérése minták a felhasználóktól
- Vélhetően nem kívánatos alkalmazások észlelése
- A kizárt fájlok és mappák
- A kizárt fájltípusok
- A kizárt folyamatok

> [!NOTE]
> Ezek a beállítások csak konfigurálható az ügyfélszámítógépeken a Windows 10 November Update futtatása (1511-es) vagy újabb verzió.

### <a name="try-it-out"></a>Próbálja ki!

1.    Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **megfelelőségi beállítások** > **Konfigurációelemek**, és hozzon létre egy új **Konfigurációelem**.
2.    Adjon meg egy nevet, majd válasszon **Windows 8.1 és Windows 10** alatt **a Configuration Manager-ügyfél nélkül kezelt eszközök beállításai** kattintson **következő**.
3.    Győződjön meg arról **minden Windows 10 (64 bites)** és **minden Windows 10 (32 bites)** ki a **által támogatott platformok** lapon, majd kattintson az **következő**.
4.    Válassza ki a **Windows Defender** csoport beállítást, majd kattintson a **következő**.
5.    Ezen a lapon adja meg a kívánt beállításokat, majd kattintson az **következő**.
6.    Fejezze be a varázslót.
7.    A konfigurációs elem hozzáadása a referenciakonfigurációhoz, majd központilag telepítenie tanulást Windows 10 November frissítés rendszerű számítógépekre (1511-es) vagy újabb.

> [!NOTE]
> Ne felejtse el, ellenőrizze a **nem megfelelő beállítások szervizelése** jelölőnégyzetet, ha az alapkonfigurációt telepíti.

## <a name="request-policy-sync-from-administrator-console"></a>Kérelem házirend szinkronizálás a felügyeleti konzol

Egy házirend-szinkronizálást a mobil eszköz a Configuration Manager konzoljáról kell szinkronizálási kérelem maga az eszköz helyett most kérhet. Szinkronizálási kérelem állapotadatokat érhető el az eszköz nézetek nevű új oszlopként **távoli szinkronizálási állapotának**. Állapota is megjelenik a **felderítési adatok** szakasza a **tulajdonságok** párbeszédpanel minden mobileszköz számára.

### <a name="try-it-out"></a>Próbálja ki!

1.    Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > eszközök.
2.    Az a **távoli eszközök műveletei** menü **szinkronizálási kérés küldése**.

Szinkronizálási öt-tíz percet is igénybe vehet. Az eszköz szinkronizált házirend módosításai. A szinkronizálási kérelmet állapotának nyomon követheti a **távoli szinkronizálási állapotának** oszlopa a **eszközök** nézetet, vagy a Device **tulajdonságok** párbeszédpanel.

## <a name="additional-security-role-support"></a>További biztonsági szerepkör támogatás

Teljes körű rendszergazda mellett a következő beépített biztonsági szerepkörök teljes hozzáféréssel rendelkezik elemekre a **minden céges eszköz** csomópont, beleértve a **Predeclared eszközök**, **iOS beléptetési profilok**, és **Windows regisztrációs csomagok**: • **Eszközkezelő** • **Company Resource Access Manager**

Ezek a területek a Configuration Manager konzol csak olvasható hozzáférést továbbra biztosítva a **írásvédett elemző** szerepkör.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Feltételes hozzáférés a Windows 10 VPN-profilok

Most előírhatja a Windows 10-es eszközöket regisztrálni kell a megfelelő Windows 10 VPN-profilok létrehozása a Configuration Manager konzolon keresztül VPN-hozzáférést Azure Active Directoryban. Ez az új révén lehetséges **engedélyezze a feltételes hozzáférést a VPN-kapcsolat** jelölőnégyzetet a **hitelesítési módszer** a VPN-profil varázsló és a Windows 10 VPN-profilok esetében a VPN-profil tulajdonságai lap. Ha engedélyezi a feltételes hozzáférés a profil egy külön egyszeri bejelentkezés hitelesítési tanúsítvány is megadható.

## <a name="see-also"></a>Lásd még:
[A System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md)

