---
title: "A Technical Preview-ban 1609 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1609 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 89a41c8a3137d0e54011ddf9a1d9b4894ecb7df8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>A rendszer 1609 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*



Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1609 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    

**A Technical Preview kiadással kapcsolatos ismert problémák:**  
*  Való frissítéskor a Configuration Manager 1609 Technical Preview-ban, az összes telepített edition frissítési házirend törlődni fog. Ezek a házirendek továbbra is, hozza létre újra, és telepítheti őket.


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="improvements-to-endpoint-protection"></a>Az Endpoint Protection fejlesztései
Az Endpoint Protection kártevőirtó-házirend beállításainak - fokozása mostantól megadhatja a szintjét, amellyel a szolgáltatás az Endpoint Protection felhő blokkolja a gyanús fájlok. Új beállítás lehetővé teszi, hogy a rendszergazdák számára a "kockázatos" számítógépek kártevő szoftverek szembesülnek nagy mennyiségű alapján.

## <a name="increased-number-of-enrolled-devices"></a>A regisztrált eszközök megnövekedett számát
A rendszergazdák mostantól lehetővé teheti a felhasználók regisztrálhatják legfeljebb 15 eszközt a hibrid mobileszköz-kezelés az Intune-nal. A korlátját felhasználónként 5 eszköz korábban volt.

## <a name="additional-apple-dep-settings"></a>További Apple DEP-beállítások

A rendszergazdák most már konfigurálhatja a következő Apple eszköz beléptetési Program (DEP) beállításai a DEP-profilt, az iOS és Mac-eszközök:
- **Touch ID**
- **Nagyítás**
- **Siri**

Ha engedélyezve van, az Apple beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja eszköz.

## <a name="integration-with-upgrade-analytics"></a>Integráció a frissítési elemzés

Frissítési analytics segítségével mérheti fel, és elemezze eszköz készültsége és a Windows 10-es kompatibilitási egyszerűbbé és gördülékenyebb frissítések engedélyezéséhez teszi lehetővé. És az elemzés frissítse a Configuration Manager integrációja a Configuration Manager felügyeleti konzol a frissítés kompatibilitásának adatait, és majd, az eszköz listából a frissítéshez vagy javítási eszközök célként.

További elemzés frissítse a kapcsolatos [frissítése Analytics használatába](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started).

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>A Windows 10 VPN hibrid profilok natív kapcsolat típusai

A Configuration Manager használata az Intune-ban, most létrehozhat a Windows 10 VPN-profilok Microsoft Automatic, IKEv2, PPTP vagy L2TP kapcsolattípusok közül a Configuration Manager konzolon OMA-URI használata nélkül.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Windows áruház Továbbfejlesztett integráció a vállalati és a Configuration Managerben

Ebben a kiadásban frissítettük [integráció a vállalati Windows áruház](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) az említett új szolgáltatásokat:

**Frissítés:** A jelenlegi technikai előzetes kiadásban az azonnali szinkronizálás szolgáltatás nem működőképességét.

- Csak telepíthet korábban, a vállalati Windows áruházból származó ingyenes alkalmazások. A Configuration Manager most emellett támogatja a telepítését online fizetett licenccel rendelkező alkalmazásokat (csak Intune-ban regisztrált eszközök esetén).
- Most kezdeményezheti az azonnali szinkronizálás a vállalati Windows áruház és a Configuration Manager között.
- Mostantól módosíthatja a titkos ügyfélkulcsot az Azure Active Directory beszerzett

### <a name="try-it-out"></a>Próbálja ki!

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>Vásároljon, és a fizetett online licencelt alkalmazások szinkronizálása

1. Vásároljon egy fizetős, online licenccel rendelkező alkalmazást a vállalati Windows áruházban.
2. Az a **felügyeleti** a Configuration Manager konzol munkaterületén kattintson **Felhőszolgáltatások** > **frissítés és karbantartás** > **vállalati Windows áruház**.
3. Az a **Home** lap a **szinkronizálási** csoportjában kattintson a **szinkronizálás most**.
4. Sokkal utána vásárolt alkalmazás fog megjelenni a **Áruházbeli alkalmazások Licencadatai** csomópontjának a **Alkalmazáskezelés** munkaterületen.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>Létrehozhat és telepíthet a szinkronizált alkalmazások adatainak a Configuration Manager-alkalmazás

Egy létrehozása és telepítése a Configuration Manager-alkalmazás egy fizetős áruházbeli alkalmazásból eljárás ugyanaz, mint az alkalmazás létrehozása egy szabad alkalmazásból. Című témakör **létrehozása és telepítése a Configuration Manager-alkalmazás Windows áruházbeli alkalmazás** a [alkalmazások kezelése a System Center Configuration Managerrel a vállalati Windows áruházból](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>Az Azure Active Directory titkos ügyfélkulcsot módosítása

1. Az a **felügyeleti** a Configuration Manager konzol munkaterületén kattintson **Felhőszolgáltatások** > **frissítés és karbantartás** > **vállalati Windows áruház**.
2. Válassza ki a Windows áruház-fiókjában, és kattintson **tulajdonságok**.
3. A a **üzleti fióktulajdonságok Windows áruház** párbeszédpanelen adja meg az új kulcs a **titkos ügyfélkulcsot** mezőben, majd kattintson a **győződjön meg arról**. Miután ellenőrizte, kattintson a **alkalmaz**, majd zárja be a párbeszédpanelt.


## <a name="new-compliance-settings-for-configuration-items"></a>Új megfelelőségi beállítások a konfigurációs elemek

A következőkkel egészült ki a konfigurációelemek használható különböző eszközplatformok számos új beállítások.
Ezek a beállítások, amelyek korábban már létezett a Microsoft Intune önálló konfigurációban, és most már elérhető a Configuration Manager Intune használatakor.
Ha segítségre van szüksége az összes ezeket a beállításokat, nyissa meg a [beállításainak és funkcióinak az eszközök a Microsoft Intune-házirendek kezelése](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) , és válassza a beállítások altémakör a kívánt platform.


### <a name="new-settings-for-android-devices"></a>Új beállítások az Android-eszközök

#### <a name="password-settings"></a>Jelszóbeállítások

- **Korábbi jelszavak megjegyzése**
- **Ujjlenyomat használatának engedélyezése zárolásának feloldásához**

#### <a name="security-settings"></a>Biztonsági beállítások

- **Tárolókártyák titkosításának kötelezővé tétele**
- **Képernyőfelvétel-készítés engedélyezése**
- **Diagnosztikai adatok küldésének engedélyezése**

#### <a name="browser-settings"></a>Webböngésző beállításai

- **Webböngésző engedélyezése**
- **Automatikus kitöltés engedélyezése**
- **Előugróablak-blokkoló engedélyezése**
- **Cookie-k engedélyezése**
- **Active scripting engedélyezése**

#### <a name="app-settings"></a>Alkalmazásbeállítások

- **Google Play áruház engedélyezése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai

- **Cserélhető tároló engedélyezése**
- **Wi-Fi alapú internetmegosztás használatának engedélyezése**
- **Földrajzi hely meghatározásának engedélyezése**
- **NFC használatának engedélyezése**
- **Bluetooth használatának engedélyezése**
- **Hangroaming engedélyezése**
- **Adatroaming használatának engedélyezése**
- **SMS-és MMS engedélyezése**
- **Beszédfelismerés használatának engedélyezése**
- **Hangtárcsázás engedélyezése**
- **Másolás és Beillesztés engedélyezése**


### <a name="new-settings-for-ios-devices"></a>Új beállítások az iOS-eszközök

#### <a name="password-settings"></a>Jelszóbeállítások

- **A jelszóban megkövetelt speciális karaktereinek száma**
- **Egyszerű jelszavak engedélyezése**
- **Ennyi perc inaktivitás után kell jelszót beírni**
- **Korábbi jelszavak megjegyzése**

### <a name="new-settings-for-mac-os-x-devices"></a>Új beállítások Mac OS X rendszerű eszközökhöz

#### <a name="password-settings"></a>Jelszóbeállítások

- **A jelszóban megkövetelt speciális karaktereinek száma**
- **Egyszerű jelszavak engedélyezése**
- **Korábbi jelszavak megjegyzése**
- **Tétlenség után képernyőkímélő bekapcsolása ennyi perc**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Windows 10 asztali és mobil eszközök új beállításai

#### <a name="password-settings"></a>Jelszóbeállítások

- **Karakterkészletek minimális száma**
- **Korábbi jelszavak megjegyzése**
- **Jelszó kérése, amikor az eszköz visszatér inaktív állapotból**

#### <a name="security-settings"></a>Biztonsági beállítások

- **Mobileszköz titkosításának kötelezővé tétele**
- **Regisztráció manuális törlésének engedélyezése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai

- **VPN engedélyezése mobilhálózaton**
- **Engedélyezése mobilhálózati roaming VPN**
- **Telefon alaphelyzetbe állításának engedélyezése**
- **USB-kapcsolat engedélyezése**
- **A Cortana engedélyezése**
- **Műveletközponti értesítések engedélyezése**

### <a name="new-settings-for-windows-10-team-devices"></a>Új beállítások a Windows 10 Team rendszerű eszközökhöz

#### <a name="device-settings"></a>Eszközbeállítások

- **Azure Operational Insights engedélyezése**
- **Miracast vezeték nélküli vetítés**
- **Az üdvözlőképernyőn megjelenő értekezletadatok kiválasztása**
- **Zárolási képernyő háttérképének URL-címe**


### <a name="new-settings-for-windows-81-devices"></a>Windows 8.1-eszközök új beállításai

#### <a name="applicability-settings"></a>Alkalmazhatósági beállítások

- **Az összes konfiguráció alkalmazása a Windows 10**

#### <a name="password-settings"></a>Jelszóbeállítások

- **Jelszó kötelező típusa**
- **Karakterkészletek minimális száma**
- **Jelszó minimális hossza**
- **Ismétlődő sikertelen bejelentkezés az eszközön tárolt adatok törléséig való száma**
- **Ennyi perc tétlenség képernyő kikapcsolása**
- **Jelszó lejárata (nap)**
- **Korábbi jelszavak megjegyzése**
- **Korábbi jelszavak újbóli használatának tiltása**
- **Képjelszó és PIN-kód engedélyezése**

#### <a name="browser-settings"></a>Webböngésző beállításai

- **Intranetes hálózatok automatikus felderítésének engedélyezése**


### <a name="new-settings-for-windows-phone-81-devices"></a>Új beállítások a Windows Phone 8.1 rendszerű eszközökhöz

#### <a name="applicability-settings"></a>Alkalmazhatósági beállítások

- **Az összes konfiguráció alkalmazása a Windows 10**

#### <a name="password-settings"></a>Jelszóbeállítások

- **Karakterkészletek minimális száma**
- **Egyszerű jelszavak engedélyezése**
- **Korábbi jelszavak megjegyzése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai

- **Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése**


## <a name="improvements-for-boundary-groups"></a>A határcsoportok fejlesztései
Ebben az előzetes verzióban a határcsoportokat és a leírás és a terjesztési pontok olyan fontos módosításait. Ezek a változások megkönnyíti a a tartalmi infrastruktúra tervezési miközben Ön jobban vezérelheti, hogyan és mikor további terjesztési kereséséhez ügyfelek tartalék tartalomforrás helyként mutat. Ez magában foglalja, mind a helyszíni és felhőalapú terjesztési pontok.

Ezek a fejlesztések cserélje le a fogalmakat és viselkedéshez, előfordulhat, hogy ismeri a ma (például a gyors vagy lassú terjesztési pontok konfigurálása), és lecseréli azokat, amelyeket egyszerűbb beállítása és karbantartása új modell. Ezek a változások egyaránt áttelepítés jövőbeli változásokról, melyek más helyrendszerszerepköröket, határcsoporthoz hozzárendel javítja.  

1609 való frissítés során a frissítés alakítja át a jelenlegi határcsoportok konfigurációiról megfelelően az új modell, így ezek a változások ne zavarja meg a tartalom terjesztése konfigurációk (lásd: [meglevő határcsoportokhoz frissítsen az új modell](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update)).

A következő részek a jelen villámnézet, az új modell működése és várhatók egy helyet, amely már konfigurált határcsoportok frissítésekor bevezetett változások.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>Felhasználói felület és a határcsoportokat és a tartalomhelyek viselkedése változásai
A következő kulcs határcsoportok és módosulnak hogyan ügyfelek található tartalmat. Ezeket a módosításokat és fogalmak számos működnek együtt.
-    **Gyors vagy lassú konfigurációi törlődnek:** Már nem konfigurálhatja az egyes terjesztési pontok gyors vagy lassú.  Ehelyett a rendszer minden határcsoporthoz hozzárendelt helyrendszer azonos. Ez a változás miatt a **hivatkozások** a határcsoport tulajdonságainak lapján már nem támogatja a gyors vagy lassú konfigurációja.
-     **Új alapértelmezett határcsoport az egyes helyeken:**  Minden elsődleges hely rendelkezik nevű új alapértelmezett határcsoportba ***alapértelmezett –--Helyhatárcsoportba\<sitecode >***.  Ha egy ügyfél nem egy hálózati helyet, amelyhez tartozik egy határcsoporthoz, hogy az ügyfél a hozzárendelt helyről származó alapértelmezett csoporthoz rendelt helyrendszerek fogja használni. Ehhez a határcsoporthoz tartalék tartalmi helyet, amelynek helyettesítésére használni szeretne.      
 -    **"A tartalék tartalomhelyekről engedélyezése"** eltávolítása: Explicit módon már nem konfigurálja a terjesztési pont használható tartalék tartalomhelyként, és ez beállítások el lesznek távolítva a felhasználói felületen.

    Emellett az eredmény beállítás **ügyfelek használhatnak tartalék forráshely a tartalomhoz** üzemelő példányon az alkalmazások megváltozott. Ezt a beállítást a központi telepítési típus mostantól lehetővé teszi az ügyfél az alapértelmezett helyhatárcsoportba használják a tartalom forráshelyeként.

 -    **Határ csoportok kapcsolatokat:** Mindegyik határcsoporthoz egy vagy több további határcsoportok lehet társítani. Ezek a hivatkozások alkotnak az új határ csoport tulajdonságai lap nevű konfigurált kapcsolatok **kapcsolatok**:
     -    Minden ügyfél közvetlenül társított határcsoportban nevezik egy **aktuális** határcsoporthoz.  
    -     Egyetlen határcsoporthoz sem az ügyfél használhatja, hogy az ügyfélszámítógépek közötti társítás miatt *aktuális* határcsoport és egy másik csoport neve egy **szomszédos** határcsoporthoz.
    -  Szolgáltatás be van kapcsolva a **kapcsolatok** lap, amely akkor adja meg, amelyek változtatás nélkül használhatók határcsoportokat egy *szomszédos* határcsoporthoz. Beállíthatja úgy is egy időt percben, amely meghatározza, hogy amikor egy ügyfelet, amelyben a sikertelen lesz a tartalmat a terjesztési pontról a *aktuális* csoport megkezdődik a tartalom helyét a Keresés *szomszédos* határcsoportokat.

        Adja hozzá, vagy a határcsoport konfigurációjának módosításához, a beállítást kell blokk tartalék adott határcsoportra konfigurál, az adott csoportból.

    Az új konfiguráció használatához explicit társítások (hivatkozások) megadása az egy határcsoportban a másikra, valamint percben egyszerre társított csoport összes terjesztési pont konfigurálása. Konfigurálja az idő határozza meg, amikor egy ügyfél nem talál a tartalomforrás a *aktuális* határcsoport keresse meg az adott szomszédos határcsoport tartalomforrások kezdődhet.

    Explicit módon konfigurálnia a határcsoportokat, mellett határcsoporthoz van egy implicit hivatkozás az alapértelmezett hely határcsoporthoz. Ez a hivatkozás 120 perc után ekkor az alapértelmezett hely határcsoporthoz egy szomszédos határcsoporthoz, amely lehetővé teszi az ügyfelek számára a tartalom forrásához helyként adott határcsoport társított terjesztési pontok válik aktívvá válik.

    Ez a viselkedés váltja fel, milyen volt korábban említett a tartalom tartalék módszerként.  Ez az alapértelmezett viselkedés 120 perc felülbírálhatja az alapértelmezett helyhatárcsoportba explicit módon társításával egy *aktuális* csoport, és beállításakor egy megadott idő percben, vagy blokkolja a tartalék teljesen a használat megelőzése érdekében.


-     **Ügyfelek próbálják beszerezni a tartalmat minden terjesztési pont legfeljebb 2 percig:** Amikor egy ügyfelet keres a tartalom forráshelyeként, megkísérli minden terjesztési pont el a 2 percet, majd próbálkozzon egy másik terjesztési pontot. Ez az egyik változás korábbi verzióiról ahol ügyfelek próbált kapcsolódni, hogy a terjesztési pont legfeljebb 2 órán át.

    - Első terjesztési pontról, amely az ügyfél megkísérel használni véletlenszerűen kiválasztott elérhető terjesztési pontok az ügyfél a készletből *aktuális* határcsoport (vagy csoportokat).

    - Két perc elteltével az ügyfél nem találja a tartalmat, ha azt vált egy új terjesztési pontra, és megkísérli beszerezni a tartalmat, hogy a kiszolgáló. Ez a folyamat addig, amíg az ügyfél megtalálja a tartalmat, vagy elérte a készlet legutóbbi kiszolgálót két percenként ismétlődik.

    - Ha egy ügyfél nem találja a egy érvényes tartalomforrás helye a *aktuális* készlet tartalékként történő időszak előtt egy *szomszédos* határcsoport éri el, az ügyfél hozzáadja a terjesztési pontokat, amelyek a *szomszédos* csoport számára, az aktuális lista végére, és majd megkeresi az adatforrás helyének kibontott csoport mindkét határcsoportok terjesztési pontjait tartalmazó.

        > [!TIP]  
        > Ha egy explicit hivatkozás az aktuális határcsoport létrehozása az alapértelmezett hely határcsoporthoz, és adja meg a tartalék időt, amely kisebb, mint a tartalék időt, hogy a szomszédos határcsoport mutató hivatkozást, ügyfelei megkezdik az alapértelmezett helyhatárcsoportba az adatforrás helyének keresése előtt, beleértve a szomszédos csoport.

    - Ha az ügyfél nem sikerült beszerezni a tartalmat a kiszolgáló a készletben, újra megkezdi a folyamatot.


### <a name="how-the-new-model-works"></a>Az új modell működése
A határcsoportok konfigurálásakor rendeli határok (hálózati helyek) és a helyrendszer-kiszolgálókat, például a terjesztési pontok, a határcsoporthoz. Ez segít ügyfelek helyrendszer-kiszolgálókat hasonlóan található terjesztési pontok a hálózaton lévő ügyfelek közelében.   
-    Ugyanazt a határt több határcsoporthoz rendelhet
-    Lehet, hogy a helyrendszer-kiszolgálók, például a terjesztési pontok társítva a következőhöz: több határcsoporthoz, így azok elérhetővé válnak a hálózati helyek szélesebb köre
-    Ha a terjesztési pont nincs társítva egy határcsoporthoz, ügyfelek nem tudnak az adott terjesztési pontokat használják a tartalom forráshelyeként.

Verziótól kezdődően ez a technical preview konfigurálhatja a tartalom forráshelyét vizsgáló tartalék viselkedését határ csoportok közötti kapcsolatok meghatározása. Ez a viselkedés úgy van konfigurálva, az új **kapcsolatok** a határcsoport tulajdonságainak és gyors vagy lassú helyrendszerek konfigurálásáról és tartalék forráshely engedélyezése a tartalom határcsoport konfigurálásával cserél lapján.

A kapcsolatok lapon vegye fel más határcsoportok ezekhez a csoportokhoz kapcsolat konfigurálása. Egy egyirányú kapcsolatot minden kapcsolat a **aktuális** határcsoport a határcsoporthoz ad hozzá, melynek neve egy **szomszédos**. Minden hivatkozás hoz létre konfigurálhatja terjesztési pontok és a tartalék idő percben. Most azt határozza meg, mennyi ideig ügyfelek után a *aktuális* határcsoporthoz is a terjesztési pontok használatának megkezdéséhez a *szomszédos* határcsoporthoz, ha azok nem egy érvényes tartalomforrás helye található az aktuális határcsoport a.

Ha az ügyfél nem találja a tartalmat, és kizár a szomszédos határcsoportok kereséséhez kezdődik, növeli a elérhető terjesztési pontok számára, hogy az ügyfél szabályozott módon.  

-    A határcsoport rendelkezhet egynél több kapcsolattal. Ez lehetővé teszi a különböző időszakokra, után más szomszédoknak tartalék konfigurálása.
-    Az ügyfelek csak tartalék lesz, amely egy közvetlen az aktuális határcsoportot szomszéd határcsoportba.
-    Amikor egy ügyfél több határcsoporthoz is tagja, az aktuális határcsoporthoz, hogy az ügyfél határcsoportjaihoz Uniója típusúként van definiálva.  Hogy az ügyfél az eredeti határcsoportokhoz bármelyikének a szomszédos majd tartalék is.

Mellett a hivatkozásokat adhat meg egy implicit kapcsolat, amely automatikusan jön létre a határcsoportokat hoz létre, és minden helyen automatikusan létrehozott alapértelmezett határcsoportba között van. Automatikus ide:
-    Ügyfelek által vannak a hierarchiában egyetlen határcsoporthoz társított automatikusan a határ a nem az alapértelmezett határcsoport a hozzájuk rendelt hely érvényes tartalomforrás-helyek azonosítására szolgál.   
-     A beállítás alapértelmezett tartalék az aktuális határcsoport az a hely alapértelmezett határcsoportba használt 120 perc múlva.

**Példa: az új modell használatával:**     
Három határcsoportok határok vagy helyrendszer-kiszolgálók nem használó létrehozásával:
-    Terjesztési pontok DP_A1 és a csoporthoz tartozó DP_A2 BG_A csoport
-    Terjesztési pontok DP_B1 és a csoporthoz tartozó DP_B2 BG_B csoport
-    Terjesztési pontok DP_C1 és a csoporthoz tartozó DP_C2 BG_C csoport

Ügyfelek a hálózati helyeket felveheti határként csak a BG_A határcsoportot, és azt, majd a másik két határcsoportokhoz az adott határcsoport kapcsolatok konfigurálása:
-    Konfigurálja a terjesztési pontok az első *szomszédos* csoport (BG_B) használható 10 perc múlva. Ez a csoport tartalmazza a terjesztési pontok DP_B1 és DP_B2. Mindkettő jó csatlakozású, az első csoportok határ helyekre.
-    Konfigurálja a második *szomszédos* csoport (BG_C) 20 perc után használni. Ez a csoport tartalmazza a terjesztési pontok DP_C1 és DP_C2. A többi két határcsoport a WAN-KAPCSOLATON keresztüli mindkettő.
-    Is hozzáadhat egy további terjesztési ponton található a helykiszolgálón a hely alapértelmezett helyhatárcsoportba. Ez a legkevésbé preferált tartalom forráshelyeként, de központilag található, a határcsoporthoz.

    Példa a határcsoportokat és a tartalék alkalommal:

     ![BG_Fallack](media/BG_Fallback.png)


Ez a konfiguráció:
-    Az ügyfél megkezdi a tartalom a terjesztési pontokról a Keresés a *aktuális* határcsoport (BG_A), a keresés minden egyes terjesztési pontok a Váltás a következő terjesztési ponthoz a határcsoport két percet. Az ügyfelek készlete érvényes tartalomforrás helyek DP_A1 és DP_A2 tartalmaz.
-    Ha az ügyfél nem találja a tartalmat a *aktuális* határcsoport keresés 10 percig, után, majd hozzáadja a terjesztési pontokat a BG_B határcsoport a keresést. Majd továbbra is a terjesztési pontról a terjesztési pontok saját kombinált készletét, amely már tartalmazza a BG_A és a BG_B határcsoportok származó tartalom keresése. Az ügyfél továbbra is csatlakozni az egyes terjesztési pontok két percet, mielőtt Váltás a következő terjesztési pontra a készletből. Az ügyfelek készlete érvényes tartalomforrás helyek DP_A1, DP_A2, DP_B1 és DP_B2 tartalmazza.
-    Egy további 10 perc (összesen 20 perc) után az ügyfél még mindig rendelkezik nem található egy terjesztési pontot tartalommal, ha bővíti az elérhető terjesztési pontok közé tartoznak a második készlete *szomszédos* csoportban, BG_C határcsoporthoz. Az ügyfél most keresés (DP_A1, DP_A2, DP_B2, DP_B2, DP_C1 és DP_C2) 6 terjesztési pont van, és továbbra is fennáll, egy új terjesztési pont módosítása a kétpercenként, amíg a tartalom található.
-    Ha az ügyfél nem rendelkezik található tartalom összesen 120 perc után, akkor visszaáll közé tartozik a *alapértelmezett helyhatárcsoportba* folyamatos keresését részeként. A készlet a terjesztési pontok mostantól tartalmazza a három konfigurált határcsoportok terjesztési pontok és a végső terjesztési pont a helykiszolgáló számítógépen található.  Az ügyfél majd továbbra is használja a tartalomhoz, a keresési módosítása a terjesztési pontok kétpercenként, amíg a tartalom található.

A különböző szomszédos csoportok különböző időpontokban elérhető legyen konfigurálásával szabályozhatja a adott terjesztési pontot hozzá szeretné adni a tartalom forráshelyeként, és ha, vagy ha, az ügyfél használja az alapértelmezett hely határcsoporthoz tartalék biztonsági hálóként nem elérhető tartalom más helyről.


### <a name="bkmk_update"></a>Frissítse az új modell meglevő határcsoportokhoz
Amikor 1609 verzióját telepíti, és frissítse a helyet, az alábbi konfigurációk automatikusan történik. Ezek célja, hogy ellenőrizze, hogy az aktuális tartalék módot továbbra is elérhető marad, amíg nem konfigurál az új határcsoportokhoz és a kapcsolatokat.  
-    Nem védett terjesztési pontok egy helyen hozzáadódnak a *alapértelmezett –--Helyhatárcsoportba\<Helykód >* az adott hely határcsoporthoz.
-    Másolatot minden meglévő határcsoporthoz, amely tartalmazza a helykiszolgáló konfigurálva lassú kapcsolaton keresztül történik. Az új csoport neve *** \<határ csoport neve > - lassú - Tmp***:  
    -    Gyors kapcsolattal rendelkező helyrendszerek maradnak az eredeti határcsoporthoz.
    -    Olyan helyrendszeren, amely lassú kapcsolattal rendelkezik másolatot hozzáadódnak a határcsoport példányát. Az eredeti helyrendszerek lassú konfigurálva maradnak az eredeti határcsoportban a visszamenőleges kompatibilitás érdekében szerepel, de nem használják az adott határcsoport.
    -     A határ másolat nincs társítva határokat. Azonban tartalék kapcsolat jön létre az eredeti csoport és az új határ másolat, a tartalék ideje nulla között.

 A következő táblázat ismerteti az új tartalék viselkedés várható kombinációja az eredeti központi telepítési beállítások és a terjesztési pontok konfigurációi:

"Nem futtatja a programot" lassú hálózati az eredeti telepítési konfigurációja  |Eredeti terjesztési pont "Engedélyezése az ügyfél számára a tartalék forráshely használatát a tartalomhoz" konfigurációja  |Új tartalék viselkedése  
---------|---------|---------
Kijelölt     |  Kijelölt    |  **Nincs tartalék** -csak használják a terjesztési pontokat aktuális határcsoportban       
Kijelölt     |  Nincs kiválasztva|  **Nincs tartalék** -csak használják a terjesztési pontokat aktuális határcsoportban       
Nincs kiválasztva |  Nincs kiválasztva|  **A szomszédos tartalék** – a terjesztési pontok aktuális határcsoportban, majd a terjesztési pontok a szomszédos határ csoportból. Kivéve, ha az explicit kapcsolat az alapértelmezett hely határcsoporthoz van konfigurálva, az ügyfelek nem lesznek tartalék ehhez a csoporthoz.    
Nincs kiválasztva | Kijelölt        |   **Normál tartalék** -aktuális határcsoportban terjesztési pontokat használ, akkor azokat a szomszédos és a hely alapértelmezett határcsoportok

 Más szolgáltatástelepítési konfigurációk eredményez **normál tartalék**.  



## <a name="office-365-client-management-dashboard"></a>Az Office 365-ügyfél kezelési irányítópult  
A Configuration Manager 1609 Technical Preview új irányítópult vezet be. Az irányítópult megtekintéséhez a Configuration Manager konzolon lépjen **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése**.
>[!NOTE]
>Az a **Újdonságok** munkaterület a Configuration Manager konzolon, az új irányítópult helytelenül nevű **Office 365-karbantartási irányítópulton**.

Az irányítópult a következő diagramot jelenít meg:

- Office 365-ügyfelek száma
- Az Office 365-ügyfél verziója
- Az Office 365 ügyfélnyelveket
- Az Office 365-ügyfél csatornák     
További információkért lásd: [frissítés áttekintése az Office 365 ProPlus csatornák](https://technet.microsoft.com/library/mt455210.aspx).
- Automatikus központi telepítési szabályok, amelyek rendelkeznek Office 365-ügyfél a választható termékek készletében kiválasztva.

Az irányítópult a következő műveletek hajthatók végre:
- Az irányítópult tetején, használja a **gyűjtemény** legördülő a beállítást, ha az irányítópult adatokat egy adott gyűjtemény tagjai.
- Kattintson a jobb felső oldalon az irányítópultot, **Office 365 telepítő** elindítani az Office 365 telepítés varázsló az ügyfelek számára az Office 365-alkalmazások telepítéséhez. További információkért lásd: [ügyfelek központi telepítése az Office 365-alkalmazások](#deploy-office-365-apps-to-clients).
- Az irányítópult közel jobb oldalán kattintson **egy automatikus központi telepítési szabály létrehozása** megnyitásához az automatikus központi telepítési szabály létrehozása varázslóban egy új automatikus központi telepítési szabály (ADR) létrehozása. Egy ADR-t az Office 365-alkalmazások létrehozásához válassza **Office 365-ügyfél** Ha úgy dönt, hogy a termék. További információkért lásd: [szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- Az irányítópult alsó jobb oldalán kattintson **Ügyfélügynök-beállítások létrehozása** Ügyfélügynök beállításainak megnyitásához. További információkért lásd: [kapcsolatos](/sccm/core/clients/deploy/about-client-settings).



Office 365 ProPlus-frissítések kapcsolatos további információkért lásd: [Office 365 ProPlus kezelése frissíti a Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="deploy-office-365-apps-to-clients"></a>Office 365-alkalmazásokat telepíteni az ügyfelek számára
Ebben a kiadásban az Office 365-ügyfél kezelése irányítópultról az Office 365-telepítő, amely lehetővé teszi az Office 365-telepítési beállítások konfigurálása, fájlokat tartalom kézbesítési hálózatokon (tartalomtovábbító) töltse le és telepíti a fájlokat a Configuration Manager alkalmazásként is elindítható.

### <a name="limitations-of-office-365-deployment"></a>Office 365 telepítési korlátozásai
- Lehetséges, hogy problémák meglévő ügyfél-beállítások importálása (XML) az Office 365-alkalmazás telepítése varázslóban meg. Manuálisan konfigurálhatja az ügyfélbeállítások probléma nélkül.

#### <a name="to-deploy-office-365-apps-to-clients"></a>Office 365-alkalmazásokat telepíteni az ügyfelek számára
1. A Configuration Manager-konzolon lépjen a **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése**.
2. Kattintson a **Office 365 telepítő** a jobb felső ablaktáblán. Az Office 365 Ügyféltelepítő varázsló megnyílik.
3. Az a **Alkalmazásbeállítások** lapon adjon nevet és leírást az alkalmazás, adja meg a fájlok letöltési helyét, és kattintson a **következő**. Vegye figyelembe, hogy a hely kell adni az űrlap &#92; &#92; *server*&#92; *megosztás*.
4. Az a **ügyfélbeállítások importálása** lapon, válassza ki, hogy az Office 365-ügyfél beállítások importálása egy meglévő konfigurációs XML-fájl, vagy manuálisan adja meg a beállításokat, és kattintson **következő**.
Ha a konfigurációs fájlt, adja meg a fájl helyét, és ugorjon a 7. Vegye figyelembe, hogy a helyen kell megadni az űrlap &#92; &#92; *server*&#92; *megosztás*&#92;* Fájlnév*. XML-KÓD.

    > [!IMPORTANT]
    >Lehetséges, hogy problémák meglévő ügyfél-beállítások importálása (XML) a technical Preview megkísérlésekor.

5. Az a **ügyfél termékek** lapon válassza ki az Office 365 csomag Ön által használt, válassza ki az alkalmazásokat tartalmazza, válassza ki a további Office termékeket kell meg lehet adni, és kattintson a kívánt **következő**.
6. Az a **ügyfélbeállítások** lapon, válassza ki a beállítások közé tartoznak, és kattintson a **következő**.
7. Az a **telepítési** lapon, válassza ki, hogy az alkalmazás központi telepítése, és kattintson a **következő**.
Ha nem kíván a varázslóban a csomag központi telepítéséhez, folytassa a 9.
8. A varázsló lapjai részében konfigurálhatók, mint a szokásos alkalmazások telepítése. További információkért lásd: [hozzon létre és telepítsen egy alkalmazást](/sccm/apps/get-started/create-and-deploy-an-application).
9. Fejezze be a varázslót.
10. Telepítése, illetve az alkalmazás szerkesztése, ugyanúgy, mint bármely más alkalmazás a Configuration Manager a **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **alkalmazások**.

>[!NOTE]
>Office 365-alkalmazások telepítése után az alkalmazások karbantartásához automatikus központi telepítési szabályokat is létrehozhat. Az Office 365-alkalmazások automatikus központi telepítési szabály létrehozásához kattintson a **egy automatikus központi telepítési szabály létrehozása**, és válassza ki **Office 365-ügyfél** Ha úgy dönt, hogy a termék. További információkért lásd: [szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="BKMK_UEFIConversion"></a>UEFI-átalakítás BIOS fejlesztései
Most testre egy operációs rendszer központi telepítésének feladatütemezése TSUEFIDrive, új változó, hogy a számítógép újraindítása lépés való áttérés UEFI a merevlemez-meghajtón FAT32 partíció készítse elő. A következő eljárás azt mutatja, hogyan hozhat létre feladatütemezési lépések a merevlemez-meghajtó előkészítése a BIOS UEFI alakításához.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>A FAT32 partíció előkészítése UEFI átalakítása:
Egy meglévő feladatütemezés egy operációs rendszer telepítéséhez a ehhez a BIOS UEFI alakításához lépéseket egy új csoportot adja hozzá.

1. Hozzon létre egy új feladatütemezési csoport, a lépéseket a fájlok és beállítások rögzítése után, és a lépéseket az operációs rendszer telepítése előtt. Hozzon létre például egy csoport után a **rögzítése fájlok és beállítások** nevű csoport **BIOS-UEFI**.
2. Az a **beállítások** lap az új csoport hozzáadása egy új feladatütemezési változó feltételként ahol **_SMSTSBootUEFI** van **nem egyenlő** való **igaz**. Ez megakadályozza, hogy a csoport lépéseit futtatását, ha a számítógép már UEFI módban van.
![BIOS UEFI-csoporthoz](media/BIOS-to-UEFI-group.png)
3. Az új csoporthoz, adja hozzá a **számítógép újraindítása** feladatütemezési lépést. A **adja meg, mi legyen futtatva az újraindítás után**, jelölje be **a feladatütemezéshez hozzárendelt rendszerindító lemezkép kijelölt** a számítógép indítása a Windows PE környezetben.  
4. Az a **beállítások** lapon maradva adja hozzá a feladatütemezési változó feltételként ahol **_SMSTSInWinPE értéke hamis**. Ez megakadályozza, hogy ez a lépés futtatása, ha a számítógép már a Windows PE környezetben.

    ![Indítsa újra a számítógépet. lépés](media/Restart-in-Windows-PE.png)
5. Adjon hozzá egy lépést, az OEM eszköz, amelyek a rendszer a belső vezérlőprogram BIOS UEFI indításához. Ez általában lesz egy **parancssor futtatása** feladatütemezési lépés a parancssorral, az OEM eszköz elindításához.
5.    A lemez formázása és particionálása feladatütemezési lépés a merevlemez formázása és particionálása hozzáadása. A lépés tegye a következőket:
    1.    Hozzon létre a FAT32-partíció, konvertálja UEFI az operációs rendszer telepítése előtt. Válasszon **GPT** a **lemez típusa**.
    ![Lemez lépés formázása és particionálása](media/Format-and-partition-disk.png)
    2.    Ugrás a FAT32 partíció tulajdonságainak. Adja meg **TSUEFIDrive** a a **változó** mező. Amikor a feladatütemezés azt észleli, hogy ezt a változót, akkor készítse elő az UEFI áttérés a számítógép újraindítása előtt.
    ![Partíció tulajdonságai](media/Partition-properties.png)
    3. Hozzon létre egy NTFS-partíciót, amelyek a Feladatütemező motor menteni az állapotot, és a naplófájlok tárolására használ.
6.    Adja hozzá a **számítógép újraindítása** feladatütemezési lépést. A **adja meg, mi legyen futtatva az újraindítás után**, jelölje be **a feladatütemezéshez hozzárendelt rendszerindító lemezkép kijelölt** a számítógép indítása a Windows PE környezetben.  




## <a name="intune-compliance-charts"></a>Intune megfelelőségi diagramok
Ebben a kiadásban kaphat átfogó megfelelőségének áttekintő képet az eszközök és a felső okok miatt meg nem felelés az új diagramok **munkaterület figyelési** a Configuration Manager konzolon.

#### <a name="to-view-the-intune-compliance-charts"></a>Az Intune megfelelőségi diagramok megtekintése
1. Nyissa meg a Configuration Manager konzol **figyelés** > **áttekintése** > **megfelelőségi beállítások**.
2. A **eszköz teljes mértékben** diagram jelenik meg.
3. Kattintson a **megfelelőségi szabályzatok** csomópont megtekintéséhez a **eszköz teljes mértékben** és **felső meg nem felelési okok** diagramokat.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>Intune megfelelőségi diagramok TP 1609 korlátozásai
- A részletezés az a **eszköz teljes mértékben** diagram jelenleg hibát eredményez.
- A **felső meg nem felelési okok** diagram megjeleníti a házirend nevét és a nem az egyes meg nem felelés oka. Részletezés és az eszközök, amelyek nem megfelelő házirendhez tartozó csoportházirend gombra.

### <a name="try-it-out"></a>Próbálja ki
Hajtsa végre az alábbi szakaszok sorrendben:

#### <a name="check-overall-compliance-chart"></a>Diagram átfogó megfelelőségének ellenőrzése
1. Adja hozzá két iOS megfelelőségi házirendek a Configuration Manager alkalmazásban. Egy házirend egy beállításokkal eszközök (például beállított PIN-kód hosszának 6) rendelkeznie kell. A többi házirend egy másik beállításokkal (például a PIN kód összetettségét) rendelkeznie kell. A házirend-beállítások nem lehetnek átfedésben vagy ütközést jelez.
2. A két házirendeket telepíthet a felhasználók egy csoportja.
3. Az Intune-ban ugyanazzal a fiókkal, és egy fiókot, amelyet a házirendek az előző lépésben kapott két iOS-eszközök regisztrálása. Az eszközök nem meg kell felelnie a megfelelőségi házirend feltételeinek.
4. A Configuration Manager ellenőrizze a **eszköz teljes mértékben** diagram. Mindkét eszköz nem megfelelő jelentse.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>A felső meg nem felelési okok diagram ellenőrzése
5. Ellenőrizze a **felső meg nem felelési okok** diagram. Ez a diagram a felső 5 okairól nem sorolja fel, de csak két megfelelőségi beállítások meghatározott házirendek között csak az első 2 meg nem felelés oka jelenik meg.
6. Kattintson a diagram a részeket. Mindkét eszköz meg kell jelennie a szűrt nézet **eszközök és megfelelőség** > **áttekintése** > **eszköz**.

#### <a name="make-devices-compliant-and-check-the-charts"></a>Megfelelő tehetik az eszközöket, és ellenőrizze, a diagramok
7. Ellenőrizze az eszközök megfelelnek a házirendek egyikét. Ellenőrizze a **eszköz teljes mértékben** diagram újra. A diagram megjelenjen-e egy kompatibilis eszköz és egy nem megfelelő eszköz.
8. Ellenőrizze a másik eszköz a szabályzatnak megfelelő azonos. Ezzel biztosítható egy eszköz megfelel házirendek és egy eszköz egyszerre csak egy házirendnek megfelelő.
9. Ellenőrizze a **felső meg nem felelési okok** diagram. Csak egy meg nem felelés oka felsorolt kell.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>Lásd még:
[A System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md)

