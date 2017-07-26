---
title: "Alkalmazások telepítése |} Microsoft Docs"
description: "A központi telepítési típus, vagy egy alkalmazás központi telepítésének szimulálása a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 0eaa1d13e9c273a6649f50d73fb357f04464d94c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>A System Center Configuration Managerrel alkalmazások központi telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 System Center Configuration Manager-alkalmazás telepítése előtt létre kell hoznia legalább egy központi telepítési típus az alkalmazáshoz. Alkalmazások és központi telepítési típusok létrehozásával kapcsolatos további információkért lásd: [alkalmazásokat ](../../apps/deploy-use/create-applications.md).

 Emellett szimulálhatja is alkalmazások központi telepítését Használja ezt a központi telepítési típust, ha szeretné számítógépeken tesztelni egy alkalmazás központi telepítésének működőképességét anélkül, hogy az alkalmazást telepítené vagy eltávolítaná. A szimulált központi telepítés kiértékeli az észlelési módszert, követelményeket és a központi telepítési típus függőségeit, és jelentést az eredményekről a a **központi telepítések** csomópontjának a **figyelés** munkaterületen. További információkért lásd: [alkalmazások központi telepítésének szimulálása ](../../apps/deploy-use/simulate-application-deployments.md).

> [!IMPORTANT]
>  Központilag telepíthető (telepítéséhez vagy eltávolításához) alkalmazások, de nem csomagokét vagy szoftverfrissítésekét szükséges. MDM által regisztrált eszközökhöz is nem támogatja a szimulált központi telepítés, a felhasználói élmény vagy az ütemezéssel kapcsolatos beállításait.

## <a name="deploy-an-application"></a>Alkalmazás üzembe helyezése

1.  Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.

2.  Válassza ki az **Alkalmazások** listában az alkalmazást, amelyet központilag telepíteni szeretne. A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.

### <a name="specify-general-information-about-the-deployment"></a>A telepítéssel kapcsolatos általános információk megadása

Az a **általános** lap a szoftver központi telepítése varázslót, adja meg a következő adatokat:

- **Szoftver**– ekkor megjelenik az alkalmazás központi telepítéséhez. A **Tallózás** gombra kattintva másik alkalmazást választhat ki.
- **Gyűjtemény**--kattintson **Tallózás** kattintva kiválaszthatja a gyűjteményt, hogy az alkalmazás telepítéséhez.
- **A gyűjteményhez társított alapértelmezett terjesztésipont-csoportok használata**– válassza ezt a lehetőséget, ha az alkalmazás tartalmát a gyűjtemény alapértelmezett terjesztésipont-csoport tárolni szeretné. Ha a kiválasztott gyűjteményhez társított alapértelmezett terjesztésipont-csoport nem, ez a beállítás nem érhető el.
- **Tartalom automatikus terjesztése a függőségek**– Ha ez engedélyezve van, és ha bármelyik, az alkalmazás központi telepítési típusa függőséget tartalmaz, majd a függő alkalmazástartalom is továbbítódik a terjesztési pontokra.

    >[!IMPORTANT]
    > Ha a függő alkalmazást az után frissíti, hogy az elsődleges alkalmazás központi telepítése megtörtént, nem történik meg automatikusan a függő viszonyhoz tartozó új tartalmak terjesztése.

- **Megjegyzések (nem kötelező)** – Itt a központi telepítés leírását lehet megadni.

### <a name="specify-content-options-for-the-deployment"></a>Tartalombeállítások megadása a központi telepítés

A a **tartalom** kattintson **Hozzáadás** hozzáadása ehhez a terjesztési pontokra vagy terjesztésipont-csoportok központi telepítéshez kapcsolódó tartalmat. Ha be van jelölve **a gyűjteményhez társított alapértelmezett terjesztési pontok használata** a a **általános** lapon, majd ezt a beállítást az adatok automatikusan kitöltődnek, és csak az alkalmazás-rendszergazda biztonsági szerepkör tagjai módosíthatják.

### <a name="specify-deployment-settings"></a>Adja meg a központi telepítési beállítások

Az a **központi telepítési beállítások** lap a szoftver központi telepítése varázslót, adja meg a következő adatokat:

- **A művelet**– a legördülő listából válassza ki, hogy a központi telepítés célja, hogy **telepítése** vagy **Eltávolítás** az alkalmazást.

    > [!NOTE]
    >  Ha egy alkalmazás központi telepítése egy eszközön kétszer is meg van adva, egyszer **Telepítés** , egyszer pedig **Eltávolítás**művelettel, az alkalmazás esetében a **Telepítés** művelettel megadott központi telepítés kap elsőbbséget.

A központi telepítéshez tartozó műveletet a létrehozás után nem lehet megváltoztatni.

- **Cél**– a legördülő listából válassza ki a következő lehetőségek közül:
    - **Rendelkezésre álló**– Ha egy felhasználó számára telepítik az alkalmazást, a felhasználó megkeresheti a közzétett alkalmazást a Szoftverközpontban, és igény szerint telepítheti.
    - **Szükséges**– az alkalmazás központi telepítése automatikusan megtörténik az ütemezés szerint. Ha az alkalmazás központi telepítési állapot nem rejtett, az alkalmazás felhasználója nyomon követheti a telepítési állapotát, és telepítheti az alkalmazást a Szoftverközpontból a határidő lejárta előtt.

    > [!NOTE]   
    >  Ha a központi telepítéshez beállított művelet az **Eltávolítás**, a központi telepítés célja automatikusan **Kötelező** lesz, és ezt nem lehet megváltoztatni.  

- **Automatikus központi telepítés ütemezése a felhasználói bejelentkezéssel vagy anélkül**– Ha a központi telepítés a felhasználó, válassza ezt a beállítást, a felhasználó elsődleges eszközein az alkalmazás telepítéséhez. Ez a beállítás nem követeli meg, hogy a felhasználó bejelentkezzen a központi telepítés futtatása előtt. Ne válassza ezt a beállítást, ha a felhasználónak meg kell adnia valamit a telepítés befejezéséhez. Ez a beállítás csak **Kötelező**célú központi telepítés esetén használható.


- **Az ébresztési csomagok küldése**– Ha a központi telepítési céllal van megadva **szükséges** és ezt a lehetőséget választja, a ébresztési csomagot küld a rendszer a számítógépekre a központi telepítés előtt. A csomaghoz a telepítési határidő lejártakor alvó állapotból a számítógépeket. E lehetőség használatához a számítógépeken és a hálózatokban be kell állítani a hálózati ébresztést.
- **Annak engedélyezése, hogy az ügyfelek mért internetkapcsolatot használjanak a tartalom letöltésére, miután elérkezett a telepítés határideje költségnövekedéssel járhat**– ezt a beállítást csak akkor céllal megadott központi telepítéseknél használható **szükséges**.
- **Automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** – is megakadályozhatja, hogy egy alkalmazás telepítését, lásd: végrehajtható fájlok listájának konfigurálásával kapcsolatos további információk **hogyan ellenőrizhető az alkalmazás telepítése előtt végrehajtható fájlok futtatásának** a témakör későbbi részében.
- **Rendszergazdai jóváhagyás megkövetelése, ha a felhasználók ezt az alkalmazást kérik**– Ha ezt a lehetőséget választja, a rendszergazdának jóvá kell hagynia a felhasználók kéréseit az alkalmazás telepítése előtt. Ez a beállítás nem érhető el, ha a központi telepítés célja **szükséges** és mikor telepítik az alkalmazást egy eszközgyűjteménybe.

    > [!NOTE]
    >  Az alkalmazásokra vonatkozó jóváhagyási kérelmek a **Jóváhagyási kérelmek** csomópontban jelennek meg, a **Szoftverkönyvtár** munkaterület **Alkalmazáskezelés** pontja alatt. Ha 45 napon belül nem engedélyezik a kérést, az el lesz távolítva. Emellett a Configuration Manager-ügyfél újratelepítése előfordulhat, hogy megszakítja a függőben lévő jóváhagyási kérelmek.
    >  Telepítési iránti kérelem jóváhagyását követően dönthet úgy, ezt követően visszautasítja a kérelmet kattintva **Megtagadás** a Configuration Manager konzolon (korábban erre a gombra kattintva lett szürkén jelenik meg jóváhagyást követően).
    >  Ez a művelet nem okoz azokat az eszközöket, a rendszer eltávolítja az alkalmazást, de akkor állítsa le a felhasználókat az alkalmazás új példánya a Szoftverközpontból.



- **Ez az alkalmazás minden felülírt verziójának automatikus frissítése**– ezt a beállítást, ha az alkalmazás minden felülírt verziójának frissítve lesz a felülírt alkalmazás.

### <a name="specify-scheduling-settings-for-the-deployment"></a>Ütemezési beállítások megadása a központi telepítés

Az a **ütemezés** lap a szoftver központi telepítése varázslóban adja meg, ha ezt az alkalmazást kell telepíteni vagy elérhetővé tenni az ügyféleszközök.
Az ezen a lapon elérhető beállítások attól függően eltérőek, hogy a központi telepítés céljának beállítása **Elérhető** vagy **Kötelező**.

Bizonyos esetekben előfordulhat, hogy szeretné telepíteni a szükséges alkalmazások központi telepítéseit vagy szoftverfrissítések bármely beállítása határidők túl további időt hagy a felhasználók. A rendszer általában szükség lehet, amikor a számítógép ki van kapcsolva hosszabb ideig, és ha telepíti a frissítések és alkalmazások központi telepítésének nagy számú. Például ha a felhasználó csak a szabadsága adott vissza, előfordulhat, hogy rendelkeznek hosszú ideig várjon a lejárt alkalmazástelepítések vannak. Ez a probléma megoldásához most definiálhat egy kényszerítési türelmi időszak gyűjteményhez a Configuration Manager ügyfél beállítások telepítésével.

A türelmi időszak konfigurálásához hajtsa végre a következő műveleteket:

- Az a **Számítógépügynök** lap, az ügyfélbeállítások konfigurálása az új tulajdonság **türelmi idő a kényszerítésre a telepítés utáni határidő (óra)** közötti értékű **1** és **120** óra.
- Az a **ütemezés** egy új kötelező alkalmazások központi telepítése, vagy egy meglévő központi telepítési tulajdonságok lapján jelölje be **felhasználói beállítások szerint, legfeljebb az ügyfélbeállításokban megadott türelmi idő a telepítés kényszerítésének késleltetés**. A kényszerítési türelmi időszak használja minden telepítés esetén, amelyek a be van jelölve, és az eszközök számára is telepítve az ügyfél-eszközbeállítást célozzák meg.

Az alkalmazás telepítése után határidejének, az alkalmazás első nem üzleti ablakában a felhasználó konfigurált és a türelmi időszak lesz telepítve. A felhasználó azonban továbbra is nyissa meg a Szoftverközpont és telepítheti az alkalmazást szeretnék bármikor. A türelmi időszak lejárta után a kényszerítési visszatér a lejárt központi telepítések elvégzéséhez ezek normál viselkedése.

Ha az alkalmazás elérhetővé tett egy másik alkalmazás felülír, a telepítési határidő felhasználók megkapják az új alkalmazás állíthatja be. Ezzel a beállítással **telepítési határidő** frissítése a felhasználók a a felülírt alkalmazást telepítették.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Felhasználói élmény beállításainak megadása a központi telepítés


Az a **felhasználói élmény** lap a szoftver központi telepítése varázsló adja meg a felhasználók hogyan használhatják az alkalmazás telepítésével kapcsolatos információkat.

Amikor engedélyezett írási szűrőkkel rendelkező Windows Embedded-eszközökre végez központi telepítést, megadhatja, hogy az alkalmazás telepítése az átmeneti területre történjen, és aztán később, illetve a telepítés határidő lejártakor vagy karbantartási időszak alatt véglegesítheti a változtatásokat. Ha a változtatásokat a telepítési határidő lejártakor vagy karbantartási időszakban véglegesíti, újra kell indítania az eszközt. A változtatások megmaradnak az eszközön.

>[!NOTE]
    >  Amikor alkalmazást telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal. További információ a karbantartási időszakok használata alkalmazások Windows Embedded-számítógépekre történő központi telepítésekor: [létrehozása a Windows Embedded-alkalmazások](../../apps/get-started/creating-windows-embedded-applications.md).
    > A **Szoftver telepítése** és a **Rendszer újraindítása (ha szükséges a telepítés befejezéséhez)** beállításokat nem használja a folyamat, ha a központi telepítéshez az **Elérhető**cél van beállítva. Emellett konfigurálhatja azt is, hogy a felhasználó milyen szintű értesítést lásson az alkalmazás telepítésekor.

### <a name="specify-alert-options-for-the-deployment"></a>Riasztási beállítások megadása a központi telepítéshez

Az a **riasztások** a szoftver központi telepítése varázsló, állítsa be, hogyan Configuration Manager és a System Center Operations Manager riasztásokat generál a központi telepítés. Konfigurálhatja a riasztások megjelenítésére vonatkozó küszöbértékeket, illetve kikapcsolhatja a jelentéskészítést a központi telepítés tartamára.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>Rendelje hozzá a központi telepítés iOS alkalmazás-konfigurációs házirend

Az a **alkalmazáskonfigurációs szabályzatok** kattintson **új** társítja a központi telepítés iOS alkalmazás-konfigurációs házirend (Ha hozott létre). Ezt a szabályzattípust kapcsolatos további információkért lásd: [iOS-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="finish-up"></a>Végül

A a **összegzés** lapon ellenőrizze a végrehajtandó műveleteket, megnyílik a központi telepítési, és kattintson a szoftver központi telepítése varázsló **tovább** a varázsló befejezéséhez.

Az új központi telepítés a **Figyelés** munkaterület **Központi telepítések** csomópontjának **Központi telepítések** listájában jelenik meg. A központi telepítés tulajdonságait szerkesztheti, illetve az alkalmazás Részletek ablaktáblájának **Központi telepítések** lapján törölheti a központi telepítést.

## <a name="delete-an-application-deployment"></a>Egy alkalmazás központi telepítésének törlése

1.  Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.

3.  Az a **alkalmazások** listára, válassza ki az alkalmazást, amely tartalmazza a központi telepítés törlésével.

4.  Válassza ki az *<alkalmazás neve\>* lista **Központi telepítések** lapján a törlendő központi telepítést. Végül a a **telepítési** lap a **telepítési** csoportjában kattintson a **törlése**.

 Alkalmazás központi telepítésének törlésekor az alkalmazás már telepített példányai nem távolítódnak el. Távolítsa el ezeket az alkalmazásokat, telepítenie kell a számítógépeken az alkalmazás **Eltávolítás**. Ha törli egy alkalmazás központi telepítését, illetve eltávolít egy erőforrást abból a gyűjteményből, amelyen a központi telepítést végzi, az alkalmazás ettől kezdve nem lesz látható a Szoftverközpontban.

## <a name="user-notifications-for-required-deployments"></a>Felhasználó értesítései a szükséges központi telepítések elvégzéséhez
Amikor megjelenik a szükséges szoftverek a **emlékeztet és Emlékeztessen** beállítás közül választhat az alábbi legördülő listán szereplő értékek:
- **Később**– Megadja, hogy értesítések beütemezve az Ügyfélügynök az értesítési beállítások alapján.
- **Rögzített ideje**– Megadja, hogy az értesítés megjelenítése a kijelölt időszak után ütemezi. Például ha 30 perc választja, az értesítés jelenik meg 30 perc múlva.

![Az Ügyfélügynök számítógép lap](media/ComputerAgentSettings.png)

A maximális időtartamot mindig alapján minden időpontban a központi telepítési ütemterv mentén a ügyfélügynökében beállított értesítési értékek. Például ha a **központi telepítés határideje 24 óránál közelebbi, emlékeztesse a felhasználók (óránként)** beállítása a **Számítógépügynök** lap 10 óra van konfigurálva és a határidő előtt több mint 24 órája párbeszédpanel indításakor, akkor akkor jelenik meg a emlékeztető lehetőségekkel legfeljebb de soha nem több mint 10 óra. Megközelíti a határidő lejártakor, mivel a párbeszédpanel kevesebb lehetőséget, a megfelelő az egyes összetevők a központi telepítés ütemterv ügyfélügynökében konzisztens jelennek meg.

Magas kockázatú telepítés például az operációs rendszert központilag telepítő feladatütemezés a felhasználói értesítés élmény pedig most a leginkább zavaró beavatkozás. Átmeneti értesítési helyett egy párbeszédpanel, például a következő jeleníti meg a számítógép minden alkalommal, amikor Ön értesítést kap, hogy a kritikus szoftverkarbantartást kell:

![Szükséges szoftverek párbeszédpanel](media/client-toast-notification.png)

## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Útmutató: a végrehajtható fájlok futtatásának egy alkalmazás telepítése előtt

>[!Tip]
>Bevezetett 1702 verziójával, ez az előzetes verziójú szolgáltatás. Az engedélyezéshez, lásd: [előzetes funkciók a System Center Configuration Managerben](https://docs.microsoft.com/sccm/core/servers/manage/pre-release-features).

Az a **tulajdonságok** központi telepítés párbeszédpanelen írja be, a a **telepítése viselkedés** lapon, az egyik adható meg több végrehajtható fájlok, fut, ha letiltja a telepítés, a központi telepítési típus. A felhasználónak be kell zárnia a működő végrehajtható fájl (vagy céllal megadott központi telepítéseknél automatikusan lezárható szükséges) előtt a központi telepítési típus telepíthetővé válna. Ennek beállításához:

1. Nyissa meg a **tulajdonságok** párbeszédpanelt, amely a központi telepítési típus.
2. A a **telepítése viselkedés** lapján a  *<deployment type name>*  **tulajdonságok** párbeszédpanel, kattintson a **Hozzáadás**.
3. Az a **hozzáadása vagy szerkesztése végrehajtható fájl** párbeszédpanelen adja meg a végrehajtható fájl, ha fut, az az alkalmazás telepítését letiltja a neve. Másik lehetőségként megadhat egy rövid nevet, amellyel az egyszerűen azonosítható a listában az alkalmazásra vonatkozóan.
4. Kattintson a **OK**, majd zárja be a  *<deployment type name>*  **tulajdonságok** párbeszédpanel megnyitásához.
5. Mellett, ha egy alkalmazás telepít a **központi telepítési beállítások** a szoftver központi telepítése varázsló, válassza a lap **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott**, majd folytassa az alkalmazás telepítéséhez.

Miután az alkalmazás eléri az ügyfélszámítógépeken, a következők történnek:

- Ha az alkalmazás lett telepítve, mint a **elérhető**, és a felhasználó megpróbál telepíteni, zárjon be minden futó végrehajtható fájlok, a telepítés folytatásához, akkor a megadott kéri.

- Ha az alkalmazás lett telepítve, mint a **szükséges**, és a beállítás **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** van kiválasztva, akkor fog látni egy párbeszédpanelt, amely közli, hogy a megadott végrehajtható fájlok automatikusan bezáródik az alkalmazás telepítési határidő elérésekor. A párbeszédpanelek a ütemezhet **ügyfélbeállítások** > **Számítógépügynök**. Ha nem a felhasználó a ezeket az üzeneteket, jelölje be **Elrejtés a Szoftverközpontban és az összes értesítésben** a a **felhasználói élmény** a központi telepítési tulajdonságok lapján.

- Ha az alkalmazás lett telepítve, mint a **szükséges** beállítást pedig **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** nincs kiválasztva, akkor az alkalmazás telepítése sikertelen lesz, ha egy vagy több megadott alkalmazás futnak.

## <a name="for-more-information"></a>További információ:
- [Magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md)

