---
title: "Mely fiókirodai használandó |} Microsoft Docs"
description: "Ismerje meg a rendelkezésre álló ágak a System Center Configuration Manager közötti különbségeket."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: f791278b0aa8efc734a894da7dab1704bb567ed0
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Melyik Configuration Manager fiókirodai érdemes használni?

*Vonatkozik: A System Center Configuration Manager (aktuális ág, hosszú távú karbantartási ág és Technical Preview-ban)*


2016. októberi kezdve három ágak a System Center Configuration Manager elérhető vannak. Ez a témakör a segítségével válassza ki a megfelelő fiókirodai meg.

> [!TIP]  
> A hierarchiában található összes helyen ugyanazt a fiókiroda kell futtatni. Egy hierarchia ággal rendelkezik különböző helyeken nem támogatott.

## <a name="current-branch-of-system-center-configuration-manager"></a>A System Center Configuration Manager aktuális ágának
Ez az egy licencelt ágat, ahol azt szeretné, hogy a legújabb szolgáltatások és funkciók eléréséhez a lehetőséget éles környezetben használható. Ez az ág használja, ha a következők egyikét: A System Center adatközpont, a System Center szabványos, System Center Configuration Manager vagy egyenértékű előfizetés jogok. Frissítési garancia és a licencelési lehetőségek kapcsolatban bővebben lásd: [licencelés és a System Center Configuration Manager az](learn-more-editions.md).


>  [!TIP]
> Az aktuális ág telepítheti próbaverzióként, amely nem igényel licencet. Próbaverziót 180 napig használható, és támogatja az aktuális ág egy licencelt kiadásra való frissítést.

Az aktuális ág évente többször új szolgáltatásainak frissül. Minden egyes frissítés egy év után a kiadása verziója támogatott. Az aktuális ág vagy az, hogy egy éven lejárta előtt egy újabb verzióra kell frissíteni. Újabb verzióra való frissítéseket a konzolon belüli frissítésként érhetők el.

Az aktuális ág egy új helyet, vagy a System Center 2012 Configuration Manager Service Pack 2 vagy a System Center 2012 R2 Configuration Manager Service Pack 1 frissítés telepítéséhez használhat [alapszintű verziót tartalmazó adathordozó](/sccm/core/servers/manage/updates#baseline-and-update-versions) a System Center Configuration Manager, a System Center 2016 DVD elérhető lesz, vagy elérhető egy önálló kiadásában a System Center Configuration Manager. Ehhez az adathordozóhoz hozzáférés attól függ, hogyan van szükségük a System Center Configuration Manager. Alapkonfiguráció újabb, mint 1702 nem támogatják a LTSB telepítését.

Az alapszintű verziót tartalmazó adathordozóról egy új helyet, amely az aktuális ág egy próbaverzió telepítéséhez is használható. Ha csak egy próbaverzió telepíteni kívánja, a szoftver kaphat a [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) webhelyet.

>  [!NOTE]
> Helyek telepítése egy új Configuration Manager-hierarchia alapszintű verziót tartalmazó adathordozó használatával. Ha korábban telepítette egy alapkonfigurációt, például 1511-es verzió, a konzolon belüli frissítések segítségével a helyek frissítése újabb verzióra, például a 1606.
>
> Helyek használatával frissített konzolon belüli frissítések eredmény helyeken találhatóak, amelyek megegyeznek-e az alapszintű verziót tartalmazó adathordozó használatával telepíti az új hely.
>
> További információ: [frissítések a System Center Configuration Manager](/sccm/core/servers/manage/updates).

**Az aktuális ág szolgáltatások**
- Kap [a konzolon belüli frissítések](/sccm/core/servers/manage/install-in-console-updates) , amelyek új szolgáltatások elérhetővé teszi.
- Hogy a biztonsági és a minőségét javítja a meglévő szolgáltatások a konzolon belüli frissítések kap.
- Sávon kívüli frissítések szükség esetén támogatja. Lásd: [a frissítésregisztráló eszköz használata](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) vagy [a gyorsjavítás telepítőjének használata](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- A Microsoft Intune és más felhőalapú szolgáltatásokat és az infrastruktúra képes együttműködni.
- Támogatja a [adatok áttelepítésének](/sccm/core/migration/migrate-data-between-hierarchies) irányuló és onnan más Configuration Manager telepítése.
- A Configuration Manager korábbi verzióiról változatról.
- Telepítés próbaverzióként, ahonnan később frissítheti egy teljes mértékben licencelt verzióra támogatja.

Az aktuális ága eredeti kiadásának verziója 1511-es volt. Soron következő frissítések például a 1602-es, 1606, és így tovább. Minden verzió támogatására egy évig marad, és a Microsoft azt javasolja, hogy frissítse a legújabb verziójára a kiadása után minél hamarabb. Várjon, amíg egy év újabb verzióra való frissítése előtt, és ki is hagyhatja az elérhető legújabb verzióra a telepítendő frissítést. Minden verzió is összesített, ezért ha kihagyni a frissítést, és telepítse a legújabb verziót, minden szolgáltatásait és fejlesztéseit elérésére korábbi verzióiról továbbra is elérhetővé válik.

További információkért lásd: [aktuális ág verziók támogatása](/sccm/core/servers/manage/current-branch-versions-supported).

**Frissítési beállítások**
- Aktív Szoftverbiztosítási is telepítheti a konzolon belüli frissítések aktuális ág verzióihoz.  
- Nincs lehetőség az aktuális ág átalakítása Technical Preview-ban. A Technical Preview kiadások, amelyek nem igényelnek licencet külön telepíteni.
- Nincs konvertálni az aktuális ág számára a hosszú távú karbantartási ág (LTSB) beállítás. Távolítsa el az aktuális ág kell, és telepítse a LTSB új telepítést.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>A System Center Configuration hosszú távú karbantartási ág
Ez a Configuration Manager ügyfelek, akik az aktuális ág használ, és amelyeknél az engedélyezett a Configuration Manager szoftver megbízhatósági (SA) vagy a megfelelő előfizetés jogosultság 2016. október 1. után lejár üzemi használatra licencelt ág. Frissítési garancia és a licencelési lehetőségek kapcsolatban bővebben lásd: [licencelés és a System Center Configuration Manager az](learn-more-editions.md).

A LTSB 1606 verzióján alapul. Az ág nem kapja meg a konzolon belüli frissítések, amelyek új szolgáltatások biztosításához, vagy frissítse a meglévő képességeket. Azonban kritikus biztonsági javítások vannak megadva. A LTSB telepítéséhez kell használnia a verzió 1606 [alapszintű verziót tartalmazó adathordozó](/sccm/core/servers/manage/updates#baseline-and-update-versions) , DVD-ről a System Center 2016 vagy a System Center Configuration Manager kapott.

Egy új helyet, vagy egy támogatott Configuration Manager 2012 helyre való frissítése a LTSB telepítéséhez használja a verzió 1606 [alapszintű verziót tartalmazó adathordozó](/sccm/core/servers/manage/updates#baseline-and-update-versions) , DVD-ről a System Center 2016 vagy a System Center Configuration Manager (aktuális ág és hosszú távú karbantartási ág 1606) kiadása kapott. Alapszintű verziót tartalmazó adathordozó segítségével telepítse egy új helyet, amely az aktuális ág 1606 verziója fut, vagy a hosszú távú karbantartási ág futtató új helyen.

> [!TIP]  
> System Center 2016 kapcsolatos további tudnivalókért lásd: [System Center 2016 dokumentáció](https://technet.microsoft.com/system-center-docs/system-center). Ebben a dokumentációban is azonosítja az beszerzése a Microsoft licencszerződések vagy hasonló jogosultság szükséges a System Center 2016.

> A System Center Configuration Manager verziója 1606 találja a a mennyiségi licencelés Service Center (VLSC), a **letölti és a kulcsok** lapján a [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), keressen a "system center konfigurációs", és válassza **System Center Config Mgr (aktuális ág és LTSB 1606)**.

> A System Center 2016 próbaverziójának is lehet a [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).

**A LTSB jellemzői**
-    Kritikus biztonsági javítások, hogy a konzolon belüli frissítések kap
- Az alábbi telepítési lehetőségek biztosít, ha a rendszergazdai (SA) szerződéssel vagy azzal egyenértékű jogokat a Configuration Manager lejárt
- Változatról (átalakítás) az aktuális ág az aktuális SA-szerződésben vagy ezzel egyenértékű jogosultságokkal a Configuration Manager

**Korlátozások**  
A LTSB az aktuális ág 1606 verzión alapul, és a következő korlátozások vonatkoznak:
- A LTSB esetén támogatott kritikus frissítések 10 éve után az általánosan rendelkezésre álló (2016 október), után, mely támogatja a fiókiroda lejár. A támogatási életciklusa kapcsolatban bővebben lásd: [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).
- Támogatja a kiszolgáló és az ügyféloldali operációs rendszerek és az ahhoz kapcsolódó technológiák, például az SQL Server-verziók korlátozott listáját. Mi támogatott, a fiókiroda kapcsolatban bővebben lásd: [támogatott konfigurációi a hosszú távú karbantartási ág](supported-configurations-for-ltsb.md).
- Nem kapja meg az új szolgáltatások frissítéseket.
- Nem támogatja a Microsoft Intune-előfizetés, amely megakadályozza a használatát hozzáadása:
  -    A hibrid MDM-konfiguráció az Intune-ban
 - A helyszíni MDM
-    Nem támogatja a Windows 10 karbantartási irányítópulton, karbantartási terveket, a Windows 10 aktuális ág (CB), vagy az aktuális ág üzleti (CBB).
- Nem támogatja a Windows 10 LTSB és a Windows Server későbbi kiadásaiban.
-    Az Eszközintelligencia szolgáltatás nem támogatott.
-    Nem támogatja a felhő alapú terjesztési pontok.
-    Nem támogatott az Exchange online-hoz, az Exchange-összekötő támogatására.
-    Minden előzetes kiadású szolgáltatások nem támogatja.



**Frissítési beállítások**
- Aktuális ágára átválthat az LTSB telepítse. Az aktuális ág átalakítása van támogatott előtt vagy után támogatja a LTSB lejár.

  Alakítsa át, rendelkeznie kell egy aktív Szoftverbiztosítási Microsofttal. További információkért tekintse meg a következőket:
  - [Frissítse a hosszú távú karbantartási ág az aktuális ág](convert-to-current-branch.md)
  - [Licencelés és a System Center Configuration Manager az](learn-more-editions.md)
  - [Alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#baseline-and-update-versions) a [frissíti a Configuration Manager](/sccm/core/servers/manage/updates)
- Nincs lehetőség a LTSB átalakítása Technical Preview-ban. A Technical Preview kiadások, amelyek nem igényelnek licencet külön telepíteni.
-    Az aktuális ág próbaverziójának nem tudja frissíteni a LTSB telepítéshez.


## <a name="technical-preview-for-system-center-configuration-manager"></a>A System Center Configuration Manager Technical Preview kiadása
A Technical Preview egy laboratóriumi környezetet, ahová és fejlesztik a Configuration Manager számára a legújabb funkciók kipróbálására használatban van. A Technical Preview termelési környezetben nem támogatott, és nem kell rendelkeznie a frissítési garancia licencszerződés.

Egy új helyet, a Technical Preview-ban futó telepítéséhez használja a legújabb [a System Center Configuration Manager Technical Preview az alapszintű verziót tartalmazó adathordozó](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). A Technical Preview telepítése után konzolon belüli frissítésként minden hónap új verziók érhetők el.

**A Technical Preview jellemzői**
-  Az aktuális ág legújabb alapverziói alapján
-  A telepítés frissítése a legújabb technikai előzetes verzióra a konzolon belüli frissítések kap
-  Új funkciókat, amelyek vannak fejlesztés alatt áll, és mit, amelynek a fejlesztők visszajelzését
-  Csak a Technical Preview fiókirodai vonatkozó frissítések kap

**Korlátozások**
-  [A funkció korlátozott](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), például csak egyetlen elsődleges hely, és legfeljebb 10 ügyfelet.  
-  Aktuális ág vagy LTSB nem frissíthető.
-  Nem támogatja a áttelepítésével való importálására vagy exportálására adatokat egy másik Configuration Manager telepítéshez.
-  Nem támogatja a frissítést a Configuration Manager korábbi verziójáról.
-  Telepítés próbaverzióként nem támogatja.

Először a Technical Preview funkciói gyakran kerülnek az aktuális ág egy újabb frissítés. Minden új technikai előzetes verziójában az előző technical Preview kiadások, a funkciókat is tartalmaz, ezek a szolgáltatások érhetőek el az aktuális ág után is.

További információkért lásd: [a System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview).

**Frissítési beállítások**
-    A konzolon belüli frissítés egy új technikai előzetes verzióhoz is telepítheti.
-    Nincs a Technical Preview konvertálása az aktuális ág vagy LTSB beállítás.


## <a name="identify-your-branch-and-version"></a>Azonosítsa a ágak és -verzió
Amikor a Configuration Manager-hely fájlverzió-információkat, a fiókiroda is ellenőrizheti.

**Verzió**   
Az a hely verziójának ellenőrzése a konzolon lépjen **System Center Configuration Manager** a konzol bal felső sarkában, ahol a **hely verziójának** jelenik meg. Lásd: [ ]() hely verziók listáját.

**Fiókiroda**  
Erősítse meg a fiókiroda a hely (a LTSB vagy az aktuális ág), a konzolon lépjen **felügyeleti** > **Helykonfiguráció** > **helyek**, és nyissa meg a **Hierarchiabeállítások**. Ha egy lehetőség, hogy az aktuális ág átalakítása és aktív, akkor a hely a LTSB verzióját futtatja. Ha a webhely az aktuális ág fut, ez a beállítás szürkén jelenik meg.
A Configuration Manager különböző verziói kapcsolatos információkért lásd a "alapkonfiguráció és frissítési verziók" [frissíti a Configuration Manager](/sccm/core/servers/manage/updates).

