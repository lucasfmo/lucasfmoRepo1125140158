---
title: "Szerepkör alapú felügyelet – alapok |} Microsoft Docs"
description: "Szerepköralapú felügyelet segítségével szabályozhatja a Configuration Manager és a felügyelt objektumokhoz, rendszergazdai hozzáféréssel."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a2d6c3f-a4e4-4c19-b087-3caada480de9
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: ddf2ad1cae51c1e36df5a6d86822e2b9abe604e2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-role-based-administration-for-system-center-configuration-manager"></a>Szerepkör alapú felügyelet a System Center Configuration Manager – alapok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerrel, használjon szerepkör alapú felügyelet a Configuration Manager felügyeletéhez szükséges hozzáférést. Továbbá biztonságos hozzáféréssel az objektumokhoz, amelyeket Ön kezel, például gyűjtemények, központi telepítések és helyek. Miután megismerte az ebben a témakörben bemutatott fogalmakkal, [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md).  

 A szerepköralapú adminisztrációs modell központilag határozza meg, és kezeli a hierarchiára kiterjedő biztonsági hozzáférési beállításokat minden hely és helybeállítás használatával a következő:  

-   *Biztonsági szerepkörök* rendelt rendszergazdai felhasználók jogosultság ezeknek a felhasználóknak (vagy felhasználói csoportok) más Configuration Manager-objektumok. Például a létrehozására és megváltoztatására ügyfélbeállítások engedély.  

-   *Biztonsági hatókörök* csoportja, amely egy rendszergazda felhasználó felelős, például egy alkalmazás, amely telepíti a Microsoft Office 2010-objektumok olyan specifikus példányai szolgálnak.  

-   *Gyűjtemények* adja meg a rendszergazda kezelheti a felhasználó-eszköz erőforrások csoportjai segítségével.  

 A biztonsági szerepkörök, biztonsági hatókörök és gyűjtemények kombinációja elkülönítse a szervezet szükségleteit rendszergazdai hozzárendeléseket. Együtt használja, azok a felügyeleti hatókör definiálásához egy olyan felhasználó, amely mi, hogy a felhasználó tekintheti meg és kezelheti a Configuration Manager környezetben.  

## <a name="benefits-of-role-based-administration"></a>Szerepkör alapú felügyelet előnyei  

-   Helyek nem használja a felügyeleti határként.  

-   A rendszergazda felhasználók létrehozása az olyan hierarchia esetében, és csak hozzá kell rendelni biztonsági őket egy alkalommal.  

-   Biztonsági hozzárendeléseket a rendszer replikálja, és a teljes hierarchiában elérhetőek.  

-   Amely segítségével a jellemzően előforduló rendszergazdai feladatok hozzárendeléséhez beépített biztonsági szerepkör is létezik. Hozzon létre egy saját egyéni biztonsági szerepkörök saját speciális üzleti igényeinek támogatására.  

-   A rendszergazda felhasználók csak az objektumokat látják, amelyek kezeléséhez engedélyekkel rendelkeznek.  

-   A biztonsággal kapcsolatos rendszergazdai műveletek naplózhatók.  

Amikor tervezése és implementálása felügyeleti biztonsági a Configuration Manager, a következő használatával hozzon létre egy *felügyeleti hatókört* rendszergazda felhasználónak:  

-   [Biztonsági szerepkörök](#bkmk_Planroles)  

-   [Gyűjtemények](#bkmk_planCol)  

-   [Biztonsági hatókörök](#bkmk_PlanScope)  


 A felügyeleti hatókört az objektumokat vezérli, amelyeket egy rendszergazda felhasználó nézetek, a Configuration Manager konzolon, és szabályozza a felhasználó ezen objektumokra jogosultságai. A szerepköralapú adminisztrációs konfigurációkat globális adatokként a hierarchia összes helyére replikálja a rendszer, majd az összes felügyeleti kapcsolatra alkalmazza azokat.  

> [!IMPORTANT]  
>  A helyek közötti replikáció késései akadályozhatják a szerepköralapú adminisztráció változásainak fogadását az egyes helyeken. További információ a helyek közötti adatbázis-replikáció figyeléséről: a [a System Center Configuration Manager helyek közötti adatátvitel](../../core/servers/manage/data-transfers-between-sites.md) témakör.  

##  <a name="bkmk_Planroles"></a> Biztonsági szerepkörök  
 Használjon biztonsági szerepköröket a biztonsági engedélyek megadására a rendszergazda felhasználóknak. A biztonsági szerepkörök olyan biztonsági engedélyek csoportjai, amelyeket a rendszergazda a felhasználókhoz rendelhet, hogy azok elláthassák felügyeleti feladataikat. Ezek a biztonsági engedélyek megadják a rendszergazda felhasználók által végrehajtható felügyeleti műveleteket, valamint az egyes objektumtípusokra vonatkozóan biztosított engedélyeket. A megfelelő biztonság érdekében célszerű a lehető legkevesebb engedélyt biztosító biztonsági szerepköröket hozzárendelni.  

 A Configuration Manager támogatására a felügyeleti feladatok szokásos csoportosításait. emellett számos beépített biztonsági szerepkörrel rendelkezik, és saját speciális üzleti igényeinek támogatására saját egyéni biztonsági szerepköröket is létrehozhat. Beépített biztonsági szerepkörök többek között az alábbiak:  

-   *Teljes körű rendszergazda* a Configuration Manager összes engedélyt.  

-   *Eszközkezelő* az Eszközintelligencia-szinkronizációs pont, az Eszközintelligencia jelentéskészítési osztályai, a szoftverleltár, Hardverleltár, és a mérési szabályok kezelésére ad engedélyt.  

-   *Szoftverfrissítés-kezelő* engedélyt definiálása, valamint a szoftverfrissítések központi telepítését. Ehhez a szerepkörhöz társított rendszergazda felhasználók gyűjteményeket, szoftverfrissítési csoportok, központi telepítések és sablonok hozhat létre.  

> [!TIP]  
>  Megtekintheti a beépített biztonsági szerepkörök listáját és egyéni biztonsági szerepkörök létrehozása, beleértve azok leírásait tartalmazza, a Configuration Manager konzolon. Megtekintéséhez a szerepkörök a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, majd válassza ki **biztonsági szerepkörök**.  

 Mindegyik biztonsági szerepkör a különböző objektumtípusokra vonatkozó konkrét engedélyeket tartalmaz. Például a *alkalmazás szerzője* biztonsági szerepkör az alkalmazások a következő engedélyekkel rendelkezik: Hagyja jóvá, létrehozása, törlése, módosítása, mappa, módosítása, objektum áthelyezése olvasási, futtassa a jelentést, és biztonsági hatókör megadása.

 Egy beépített biztonsági szerepkör engedélyeit nem módosíthatja, de másolatot készíthet róla, hogy módosítsa azt, majd egy új egyéni biztonsági szerepkörként mentse ezekkel a módosításokkal. Biztonsági szerepkörök, amelyek exportálása egy másik hierarchiából, például egy teszthálózatból is importálhat. Tekintse át a biztonsági szerepköröket és engedélyeiket annak eldöntéséhez, hogy a beépített biztonsági szerepkörök fogja használni, vagy kell-e a saját egyéni biztonsági szerepkörök létrehozása.  

 ### <a name="to-help-you-plan-for-security-roles"></a>A biztonsági szerepkörök tervezéséhez nyújtanak segítséget  

1.  Azonosítsa, hogy a rendszergazda felhasználók, hajtsa végre a Configuration Manager alkalmazásban. Ezek a feladatok a felügyeleti feladatok egy vagy több csoportjához, mint például az alkalmazások és csomagok központi telepítéséhez, az operációs rendszerek és a beállítások a megfelelőség érdekében történő központi telepítéséhez, a helyek és a biztonság konfigurálásához, a naplózáshoz, a számítógépek távvezérléséhez és a leltáradatok gyűjtéséhez kapcsolódhatnak.  

2.  Rendelje hozzá ezeket a felügyeleti feladatokat egy vagy több beépített biztonsági szerepkörhöz.  

3.  Amennyiben egyes rendszergazda felhasználók több biztonsági szerepkör feladatait végzik, az ezen feladatokat tartalmazó egyetlen új biztonsági szerepkör létrehozása helyett rendeljen hozzá több biztonsági szerepkört ezen felhasználókhoz.  

4.  Ha az azonosított feladatok nem felelnek meg a beépített biztonsági szerepköröknek, hozzon létre és teszteljen új biztonsági szerepköröket.  

A szerepkör alapú felügyelet biztonsági szerepköreinek létrehozásáról és konfigurálásáról kapcsolatos információkért lásd: [létrehozhat egyéni biztonsági szerepköröket](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole) és [biztonsági szerepkörök konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole) a a [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md) témakör.  

##  <a name="bkmk_planCol"></a> Gyűjtemények  
 A gyűjtemények a rendszergazda felhasználó által megtekinthető, illetve felügyelhető felhasználói és számítógép-erőforrásokat adják meg. Ahhoz például, hogy a rendszergazda felhasználók alkalmazásokat telepíthessenek vagy használhassák a távvezérlést, olyan biztonsági szerepkörhöz kell őket hozzárendelni, amely engedélyezi a hozzáférést egy ezen erőforrásokat tartalmazó gyűjteményhez. Ehhez felhasználókat vagy eszközöket tartalmazó gyűjteményeket jelölhet ki.  

 További információ a gyűjtemények: [a System Center Configuration Manager gyűjteményeinek bemutatása](../../core/clients/manage/collections/introduction-to-collections.md).  

 A szerepköralapú adminisztráció konfigurálása előtt ellenőrizze, hogy valamely alábbi okból szükség van-e új gyűjtemények létrehozására:  

-   Funkcionális szervezés, például külön gyűjtemények kialakítása a kiszolgálók és a munkaállomások számára.  

-   Földrajzi elkülönítés, például külön gyűjtemények az észak-amerikai és az európai telephelyek számára.  

-   Biztonsági követelmények és üzleti folyamatok, például külön gyűjtemények az üzemi környezet és a tesztgépek számára.  

-   Szervezeti elkülönítés, például külön gyűjtemények mindegyik üzleti egység számára.  

További információ a szerepköralapú Adminisztráció gyűjteményeinek konfigurálásáról: [gyűjtemények konfigurálása kezeléséhez biztonsági](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl) a a [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md) témakör.  

##  <a name="bkmk_PlanScope"></a> Biztonsági hatókörök  
 Biztonsági hatókörök használatával hozzáférést biztosíthat a rendszergazda felhasználóknak a biztonságos objektumokhoz. A biztonsági hatókörhöz rendelt rendszergazdai felhasználók csoportként biztonságos objektumok elnevezett készleten. Minden biztonságos objektumot hozzá kell rendelni egy vagy több biztonsági hatókörhöz. Configuration Manager rendelkezzen a két beépített biztonsági hatókört tartalmazza:  

-   A *összes* beépített biztonsági hatókörhöz engedélyezi a hozzáférést minden hatókör számára. nem rendelhet hozzá objektumokat.  

-   A *alapértelmezett* beépített biztonsági hatókört használja a rendszer minden objektum alapértelmezés szerint. A Configuration Manager első telepítésekor az összes objektum ehhez a biztonsági hatókörhöz van rendelve.  

Ha korlátozni szeretné a rendszergazda felhasználók számára látható és felügyelhető objektumok körét, egyéni biztonsági hatóköröket kell létrehoznia és használnia. A biztonsági hatókörök nem támogatják a hierarchikus elrendezést, és nem ágyazhatók egymásba. Egy biztonsági hatókörben egy vagy több objektumtípus szerepelhet, többek között az alábbiak:  

-   Riasztási előfizetések  

-   Alkalmazások  

-   Rendszerindító lemezképek  

-   Határcsoportok  

-   Konfigurációelemek  

-   Egyedi ügyfélbeállítások  

-   Terjesztési pontok vagy terjesztésipont-csoportok  

-   Illesztőprogram-csomagok  

-   Globális feltételek  

-   Áttelepítési feladatok  

-   Operációsrendszer-lemezképek  

-   Operációs rendszer telepítőcsomagjai  

-   Csomagok  

-   Lekérdezések  

-   Helyek  

-   Szoftverhasználat-mérési szabályok  

-   Szoftverfrissítési csoportok  

-   Szoftverfrissítési csomagok  

-   Feladatütemező csomagok  

-   Windows CE eszközbeállítás elemek és csomagok  

Van még néhány olyan objektum, amelyet nem tartalmazhatnak a biztonsági hatókörök, mert csak biztonsági szerepkörökkel vannak biztosítva. Ezek az objektumok való rendszergazdai hozzáférés nem korlátozható a rendelkezésre álló objektumok egy részhalmazára. Például előfordulhat, hogy egy rendszergazda felhasználó egy adott helyhez használatos határcsoportokat hoz létre. Mivel a határobjektum nem támogatja a biztonsági hatóköröket, ezt a felhasználót nem rendelheti hozzá olyan biztonsági hatókörhöz, amely csak az adott hellyel társított határokhoz biztosítja a hozzáférést. Az, hogy a határobjektumok nem társíthatók biztonsági hatókörökhöz, azt jelenti, hogy amikor határobjektumokhoz való hozzáférést tartalmazó biztonsági szerepkört rendel egy felhasználóhoz, az a hierarchiában szereplő összes határhoz hozzáférést kap.  

Többek között az alábbi objektumok nincsenek biztonsági hatókörök által korlátozva:  

-   Active Directory-erdők  

-   Rendszergazda felhasználók  

-   Riasztások  

-   Kártevőirtó-házirendek  

-   Határok  

-   Számítógép-társítások  

-   Alapértelmezett ügyfélbeállítások  

-   Központi telepítési sablonok  

-   Eszközillesztők  

-   Exchange Server-összekötő  

-   Helyek közti megfeleltetések áttelepítése  

-   Mobileszköz-beléptetési profilok  

-   Biztonsági szerepkörök  

-   Biztonsági hatókörök  

-   Helycímek  

-   Helyrendszerszerepkörök  

-   Szoftvercímek  

-   Szoftverfrissítések  

-   Állapotüzenetek  

-   Felhasználó-eszköz kapcsolatok  

Ha különálló objektumpéldányokhoz való hozzáférés korlátozására van szükség, készítsen biztonsági hatóköröket. Példa:  

-   A rendszergazda felhasználók egy csoportjának az üzemi környezetben működő alkalmazásokat kell látnia, és nem a tesztalkalmazásokat. Létrehozhat egy biztonsági hatókört az üzemi környezetben működő alkalmazásokhoz, valamint egy másikat a tesztalkalmazásokhoz.  

-   Különböző rendszergazda felhasználók eltérő hozzáférést igényelnek egy objektumtípus különböző példányaihoz, Például az egyik csoportjuknak adott szoftverfrissítési csoportokhoz olvasási engedélyre van szüksége, és egy másik csoportjuknak módosítása és törlése engedélyekkel kell rendelkeznie a többi szoftverfrissítési csoportok. Ekkor létrehozhat az ezekhez a szoftverfrissítési csoportokhoz tartozó különböző biztonsági hatóköröket.  

Szerepköralapú Adminisztráció biztonsági hatóköreinek konfigurálásáról további információkért lásd: a [objektum biztonsági hatókörök konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope) a a [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md) témakör.  

