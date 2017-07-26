---
title: "A Technical Preview-ban 1702 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1702 verzió."
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 3bdbcd1a3c64a1d50f2f6219b2a5e17d60979864
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>A rendszer 1702 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1702 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Visszajelzés küldése a Configuration Manager konzolról

Ez az előzetes új visszajelzési lehetőségek a Configuration Manager konzolon. A visszajelzési lehetőségek lehetővé teszi a visszajelzés küldése közvetlenül a fejlesztői csapat vállalja a Configuration Manager UserVoice visszajelzési webhelyet.  

>Megtalálhatja az **visszajelzés** lehetőséget:
-  A menüszalagon látható, minden egyes csomópont kezdőlap lapján bal.  
   ![Szalagon](./media/feedback-home.png)

-  Amikor a jobb gombbal a konzolon bármely objektumon.   
    ![Jogosultságot kattintást](./media/feedback-option.png)   

Kiválasztása **visszajelzés** megnyitja a böngészőt, hogy a Configuration Manager UserVoice visszajelzés webhellyel, https://configurationmanager.uservoice.com/forums/300492-ideas.
##  <a name="changes-for-updates-and-servicing"></a>Módosítások történtek a frissítések és karbantartás
A következő új, a jelen előzetes kiadással.

**Egyszerűbb frissítési lehetőségek**  
Amikor legközelebb az infrastruktúra címtársémának megfelelően két vagy több frissítéshez, csak a legfrissebb lesznek letöltve. Például, ha az aktuális hely verziója két vagy több verziója régebbi, mint a legutóbbi elérhető, csak a legfrissebb verzió automatikusan letölti.  

Lehetősége van a frissítések letöltése és telepítése a más elérhető, akkor is, ha azok nem a legújabb verzióját. Azonban, hogy a frissítés felváltotta újabb egy figyelmeztetést fog kapni. A frissítés letöltése *elérhető letöltésre*, válassza ki a frissítést a konzolon, és kattintson a **letöltése**.

**A régebbi frissítések továbbfejlesztett karbantartása**   
Hozzáadott egy automatikus karbantartás függvény, amely a szükségtelen letöltéseket törlése a "EasySetupPayload" mappában található a helykiszolgálón.  


## <a name="peer-cache-improvements"></a>Társközi gyorsítótár fejlesztései
Jelen kiadásával kezdődően társközi gyorsítótár forrásoldali számítógép elutasítják tartalmat kér, amikor a társközi gyorsítótár forrásoldali számítógép megfelel-e az alábbi feltételek bármelyike:  
 -     Alacsony töltöttségű telepre vonatkozó módban van.
 -  CPU-terhelés meghaladja a 80 % időpontjában a tartalmat.
 -  Lemezes i/o-rendelkezik egy *AvgDiskQueueLength* , amely meghaladja a 10.
 -  Nincs több elérhető kapcsolódást a számítógéphez van.   

Beállíthatja, hogy ezeket a beállításokat az ügynök konfigurációs ügyfélosztályt a társ forrás funkció (*SMS_WinPEPeerCacheConfig*) a System Center Configuration Manager SDK használatakor.

Ha a számítógép visszautasítja a kérelmet a tartalomhoz, a kérést küldő számítógép továbbra pozícionálni tartalom űrlap az alternatív források az elérhető tartalom forráshelyeiről készletében.   

## <a name="azurediscovery"></a>Eszközök, felhasználók és csoportok kezelése az Azure Active Directory tartományi szolgáltatások segítségével

A jelen technikai előzetes verziójával egy Azure Active Directory (AD) tartományi szolgáltatásokban tartományhoz csatlakoztatott eszközök kezeléséhez felügyelt tartomány. A Configuration Manager felderítési módszerek eszközök, felhasználók és csoportok az adott tartományban is kap.

A technical preview-hely infrastruktúra, ügyfelek és az Azure AD tartományi szolgáltatások tartomány összes futtatásához az Azure-ban.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>A Configuration Manager beállítása az Azure AD használatára
Az Azure AD a Configuration Manager használatához a következőkre lesz szüksége:
-    Azure-előfizetés.
-    Az Azure AD tartományi szolgáltatásokkal (DS).
-    Egy Azure virtuális gépen, amely az Azure AD csatlakozik futó Configuration Manager-hely.
-    A Configuration Manager ügyfelek, amelyek ugyanabban az Azure AD-környezetben futnak.

Azure AD tartományi szolgáltatások konfigurálásához lásd: [Ismerkedés az Azure AD tartományi szolgáltatások](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started).

### <a name="discover-resources"></a>Erőforrások felderítéséhez
Az Azure ad-ben futtassa a Configuration Manager beállítása, használhatja a következő Active Directory felderítési módszerei Azure ad-val erőforrások kereséséhez:  
- Active Directory-rendszerfelderítés
- Active Directory-felhasználófelderítés
- Active Directory-csoportfelderítés  

Az egyes módszerek használ szerkessze az LDAP-lekérdezést az Azure AD OU struktúrákat helyett a jellemző a helyszíni Active Directory-tárolókban kereséséhez. Ehhez telepítenie kell az Azure-előfizetéshez az Active Directory keresési lekérdezés közvetlen.  

Az alábbi példák használja az Azure AD *contoso.onmicrosoft.com*:
 - **Rendszer-felderítési**   
Az Azure AD tárolja az eszközök a **AADDC számítógépek** szervezeti Egységet.  Konfigurálja a következőket:  
  -    *LDAP://OU=AADDC számítógépek, DC = contoso, DC = onmicrosoft, DC = com*  


- **Felhasználófelderítés** AAD tárolja a felhasználók a **AADDC felhasználók** szervezeti Egységet.  Konfigurálja a következőket:
  - *LDAP://OU=AADDC felhasználók, DC = contoso, DC = onmicrosoft, DC = com*


- **Csoport felderítése**  
Az Azure AD nem rendelkezik egy szervezeti Egységhez, amely tárolja a csoportok. Az azonos általános struktúra használja a rendszer vagy felhasználói lekérdezések és konfigurálásához ehelyett az LDAP-lekérdezés számára a szervezeti Egységhez, amely tartalmazza a csoportok ponthoz felderítéséhez.

Tekintse meg az Azure AD további információt a következő:  
 - [Az Azure Active Directory tartományi szolgáltatások](https://azure.microsoft.com/en-us/services/active-directory-ds) az Azure.microsoft.com webhelyen.
 - [Active Directory tartományi szolgáltatások dokumentációja](https://docs.microsoft.com/azure/active-directory-domain-services) docs.microsoft.com.

## <a name="conditional-access-device-compliance-policy-improvements"></a>Feltételes hozzáférés eszköz megfelelőségi házirend fejlesztései

Eszköz megfelelőségi új házirendszabály segítségével érhető el, blokkolni a hozzáférést a vállalati erőforrásokhoz, amelyek támogatják a feltételes hozzáférést, ha a felhasználók a nem megfelelő alkalmazások listája részét képező alkalmazásokat használnak. A nem megfelelő alkalmazások listája a rendszergazda által adható meg az új kompatibilis szabály hozzáadásakor **, amely nem telepíthető alkalmazások**. Ez a szabály van szükség a rendszergazdát, hogy adja meg a **alkalmazásnév**, a **Alkalmazásazonosító**, és a **alkalmazás kiadóját** (választható), amikor egy alkalmazás hozzáadását a nem megfelelő listájához. Ez a beállítás csak iOS és Android-eszközökre vonatkozik.

Ezenkívül ez segít a szervezeteknek csökkenthető az adatszivárgás keresztül nem biztonságos alkalmazásokat, és meg kell akadályozni az egyes alkalmazásokkal túl sok adatot fogyasztás.

- További [eszközmegfelelőségi szabályzatok működése](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies).
- További [eszköz megfelelőségi házirendek létrehozásáról](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy).

### <a name="try-it-out"></a>Próbálja ki

**Forgatókönyv:** Az alkalmazások, amelyek okozta adatszivárgás úgy, hogy a vállalaton kívül biztosítható a vállalati adatokat küld, vagy túl sok adatot fogyasztás, majd okozza, hogy azonosítsa [feltételes hozzáférési megfelelőségi szabályzat létrehozása](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy) ezeket az alkalmazásokat, hogy hozzáadja a nem megfelelő alkalmazások listája. Ez letiltja a vállalati erőforrásokhoz, amíg a felhasználó a letiltott alkalmazást eltávolíthatja a feltételes hozzáférést támogató való hozzáférést.

## <a name="antimalware-client-version-alert"></a>Kártevőirtó ügyfélaktivitási verziója
Az előzetes verzióval kezdődően, a Configuration Manager az Endpoint Protection biztosít riasztást Ha több mint 20 % (alapértelmezett) felügyelt ügyfelek a kártevőirtó-ügyfél (azaz a Windows Defender vagy az Endpoint Protection ügyfél) egy lejárt verzióját használja.

### <a name="try-it-out"></a>Próbálja ki
Győződjön meg arról, Endpoint Protectiont engedélyezte az összes asztali és kiszolgáló ügyfél ügyfél-beállítási házirendet. Most már megtekintheti **kártevőirtó ügyfélverzió** és **Endpoint Protection központi telepítési állapota** címen **eszközök és megfelelőség** > **áttekintése** > **eszközök** > **összes asztali számítógép és az ügyfelek kiszolgálásához**. Riasztás ellenőrzéséhez tekintse meg **riasztások** a a **figyelés** munkaterületen. Ha több mint 20 %-ban felügyelt ügyfelek egy kártevőirtó szoftver lejárt verzióját futtatja, a kártevőirtó-ügyfél verziója elavult riasztás jelenik meg. Ez a riasztás nem jelenik meg a **figyelés** > **áttekintése** fülre. Lejárt kártevőirtó ügyfelek frissítéséhez engedélyezése a szoftverfrissítések kártevőirtó-ügyfelek számára.

Konfigurálja a százalékos arányát, amelyen a riasztás akkor jön létre, bontsa ki **figyelés** > **riasztásokat** > **minden riasztás**, kattintson duplán a **kártevőirtó ügyfelek elavult** , és módosítsa a **riasztás, ha a felügyelt ügyfelek százalékos aránya a kártevőirtó ügyfélprogram elavult verzióját futtató több mint** lehetőséget.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Az üzleti frissítések a Windows Update megfelelőségi vizsgálata
Most már konfigurálhatja a megfelelőségi házirend frissítés bevonó szabályt a Windows Update üzleti assessment eredmény a feltételes hozzáférési kiértékelésnek részeként.
> [!IMPORTANT]
> Windows 10 Insider Preview Build 15019 vagy újabb verzió megfelelőségének assessment használata a Windows Update üzleti frissítésekhez kell rendelkeznie.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>A Windows Update for Business kezelése Windows 10-es frissítések engedélyezése
Üzleti frissítések a Windows Update megfelelőségének assessment adatainak összegyűjtése, a következő eljárással konfigurálhatja az ügyfélügynök-beállítást explicit módon engedélyezi a Windows Update for Business kezelheti a Windows 10-frissítéseket.
1. A Configuration Manager konzolon kattintson az **Adminisztráció** > **Ügyfélbeállítások**elemre.
2. Az ügyfél beállításainak tulajdonságaiban, Ugrás **szoftverfrissítések**, és válassza ki **Igen** a a **kezelése Windows 10 frissítései a Windows Update for Business** beállítás.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Megfelelőségi szabályzat létrehozása a Windows Update üzleti értékeléshez
1. Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **megfelelőségi beállítások** > **megfelelőségi szabályzatok**.
2. Kattintson a **megfelelőségi szabályzat létrehozása** , vagy válasszon egy meglévő megfelelőségi szabályzat módosításához.
3. Az Általános lapon adja meg a nevét és leírását, válassza ki a **a Configuration Manager-ügyféllel felügyelt eszközök megfelelőségi szabályai**, állítsa be a meg nem felelés súlyossága reporting, és kattintson **következő**.
4. A támogatott platformok lapon válassza az **Windows 10**, és kattintson a **következő**.
5. A szabályok lapján kattintson a **új...** , és majd a **feltétel** válasszon **szükséges Windows Update üzleti megfelelőségi**. A **érték** automatikusan beállítása **igaz**.

Az új szabályzat az **Eszközök és megfelelőség** munkaterület **Megfelelőségi szabályzatok** csomópontjában jelenik meg.

### <a name="deploy-a-compliance-policy"></a>Megfelelőségi házirend telepítése
1. Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **megfelelőségi beállítások**, és kattintson a **megfelelőségi szabályzatok**.
2. A **Kezdőlap** **Telepítés** csoportjában kattintson a **Telepítés**elemre.
3. A **Megfelelőségi szabályzat telepítése** párbeszédpanelen a **Tallózás** gombra kattintva jelölje ki a felhasználógyűjteményt, amelyre a szabályzatot telepíteni szeretné.
   Emellett kijelölhet beállításokat riasztások létrehozásához arra az esetre, ha a házirend nem megfelelő, valamint az ütemterv konfigurálásához, amely szerint ezt a szabályzatot a megfelelőség szempontjából értékelik.
4. Amikor elkészült, kattintson az **OK**gombra.

### <a name="monitor-the-compliance-policy"></a>A megfelelőségi házirend megfigyelése
Miután létrehozta a megfelelőségi szabályzatot, a megfelelőségi eredmények a Configuration Manager konzolon figyelheti meg. További információkért lásd: [a megfelelőségi házirend megfigyelése](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>A Szoftverközpont beállítások és az értesítési üzenetek nagy jelentőségű feladatütemezésekhez fejlesztései
Ebben a kiadásban a Szoftverközpont beállítások és az értesítési üzenetek nagy jelentőségű központi telepítésére vonatkozó feladatütemezés a következő fejlesztéseket tartalmazza:

- A feladatütemezés tulajdonságai konfigurálhat feladatütemezési, többek között operációs rendszert nem tartalmazó feladatütemezések, mint a magas kockázatú telepítés. Bizonyos feltételeknek megfelelő feladatütemezési automatikusan nagy jelentőségű típusúként van definiálva. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- A feladatütemezés tulajdonságai Ha szeretné, használja az alapértelmezett értesítési üzenetet, vagy hozzon létre saját egyéni értesítési üzenet nagy jelentőségű telepítésekhez.
- A feladatütemezés tulajdonságai a Szoftverközpont tulajdonságai, például egy újraindítás szükséges, ügyeljen a letöltési mérete, a feladatütemezés és konfigurálható a becsült futási időt.
- Az alapértelmezett nagy jelentőségű telepítési üzenet helyben most, hogy az alkalmazások, adatok és beállítások települnek át automatikusan állapotok frissíti. Korábban, az alapértelmezett üzenetet az egyetlen operációs rendszer telepítése azt mutatták ki, hogy az összes, adatok, beállítások és alkalmazások elveszhetnek, amelyet a rendszer nem igaz a helyben frissítés.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>A feladatütemezés állítja be a nagy jelentőségű feladatütemezés
A következő eljárással feladatütemezés állítja be nagy jelentőségű.
> [!NOTE]
> Bizonyos feltételeknek megfelelő feladatütemezési automatikusan nagy jelentőségű típusúként van definiálva. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **felhasználói értesítés** lapon jelölje be **Ez a nagy jelentőségű feladatütemezés**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Magas kockázatú telepítések az egyéni értesítés létrehozása
1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **felhasználói értesítés** lapon jelölje be **használja az egyéni szöveg**.
>  [!NOTE]
>  Felhasználói értesítés szövegéhez csak állítható amikor a **Ez a nagy jelentőségű feladatütemezés** van kiválasztva.

4. A következő beállításokat (a 255 karakteres minden szövegmező maximális):

   **Felhasználói értesítés főcím szövegét**: Itt adhatja meg, amely megjeleníti a Szoftverközpont felhasználói értesítés kék színű szövegre. Például az alapértelmezett felhasználói értesítés, ez a szakasz hasonlót "Megerősítése frissíti az operációs rendszer ezen a számítógépen".

   **Felhasználói értesítő üzenet szövege**: Adja meg az egyéni értesítés a szervezet három szövegmezőt van.
   - 1. szövegmező: Megadja a szöveg, amelyet általában az a felhasználó kapcsolatos utasításokat tartalmazó fő törzsét. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található valami például "az operációs rendszer frissítése időt vesz igénybe, és a számítógép többször is újraindulhat."
   - 2. szövegmező: Megadja a szöveg a fő törzs félkövér szövegét. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található valami például "a frissítés az új operációs rendszert telepít, és automatikusan áttelepíti az alkalmazásokat, adatokat és beállításokat."
   - 3. szövegmező: Megadja a félkövérrel a szöveg utolsó sort. Például az alapértelmezett felhasználói értesítés, ebben a szakaszban található hasonlót "gombra kattintva megkezdheti. Ellenkező esetben kattintson a Mégse gombra."   

   Tegyük fel, konfigurálja a következő egyéni értesítés tulajdonságai.

   ![Egy feladatütemezés egyéni értesítés](.\media\user-notification.png)

   A következő értesítést fog megjelenni, ha a végfelhasználó nyit meg a telepítést a Szoftverközpontból.

   ![Egy feladatütemezés egyéni értesítés](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>A Szoftverközpont tulajdonságainak konfigurálása
A következő eljárással konfigurálhatja a feladatütemezés a szoftverközpontban megjelenített adatokat. Ezek az adatok csak tájékoztatásra szolgálnak.  
1. Nyissa meg a Configuration Manager konzol **szoftverkönyvtár** > **operációs rendszerek** > **feladatütemezések**.
2. Válassza ki a feladatütemezést, szerkesztése, és kattintson a **tulajdonságok**.
3. Az a **általános** lapon, a Szoftverközpont a következő beállítások érhetők el:
  - **Újraindítás szükséges**: Lehetővé teszi, hogy a felhasználó tudja, hogy újraindítás szükséges a telepítés során.
  - **Méret (MB) letöltése**: Itt adható meg, hány mérete (MB) a Szoftverközpontban a feladatütemezéshez.  
  - **Futási idő (percekben) becsült**: Megadja a becsült futási idő percben megadva, ameddig a feladatütemezést a Szoftverközpontban jelenik meg.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>Ellenőrizze a végrehajtható fájlok futtatásának egy alkalmazás telepítése előtt

A a  *<deployment type name>*  **tulajdonságok** párbeszédpanelt a központi telepítési típus telepítése viselkedés lapján, megadhat további végrehajtható fájlok, fut, ha letiltja a telepítés, a központi telepítési típus közül. A felhasználónak be kell zárnia a működő végrehajtható fájl (vagy lezárása automatikusan céllal megadott központi telepítéseknél kötelező) előtt a központi telepítési típus telepíthetővé válna.

### <a name="try-it-out"></a>Próbálja ki.

1.    A Configuration Manager központi telepítési típus tulajdonságait, válassza ki a **telepítése viselkedés** fülre.
2.    Válasszon **Hozzáadás** hozzáadása egy vagy több, az ellenőrizni kívánt végrehajtható fájl neve. Azt is megteheti, ezzel segítve a listában lévő alkalmazások felderítésének megjelenítendő nevét.
3.    Ha a központi telepítési céllal szükséges, a szoftver központi telepítése varázsló akkor is lehetősége **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott**.

Ha az alkalmazás lett telepítve, mint a **elérhető**, és a felhasználó megpróbál telepíteni egy alkalmazást, zárjon be minden futó végrehajtható fájlok, a telepítés folytatásához, akkor a megadott kéri.

Ha az alkalmazás lett telepítve, mint a **szükséges**, és a beállítás **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** van kiválasztva, akkor fog látni egy párbeszédpanelt, amely közli, hogy a megadott végrehajtható fájlok automatikusan bezáródik az alkalmazás telepítési határidő elérésekor. A párbeszédpanelek a ütemezhet **ügyfélbeállítások** > **Számítógépügynök**. Ha nem a felhasználó a ezeket az üzeneteket, jelölje be **Elrejtés a Szoftverközpontban és az összes értesítésben** a a **felhasználói élmény** a központi telepítési tulajdonságok lapján.

Ha az alkalmazás lett telepítve, mint a **szükséges** beállítást pedig **automatikusan zárjon be minden futó végrehajtható fájlok, a központi telepítési típus tulajdonságai párbeszédpanel telepítés viselkedés lapján megadott** nincs kiválasztva, akkor az alkalmazás telepítése sikertelen lesz, ha egy vagy több megadott alkalmazás futnak.

## <a name="create-pfx-certificates-with-s-mime-support"></a>S MIME-támogatással rendelkező PFX-tanúsítványok létrehozása

Mostantól, amely támogatja az S/MIME PFX-tanúsítványprofil létrehozása és telepítése a felhasználók számára.  Ez a tanúsítvány majd alkalmas S/MIME titkosítási és visszafejtési, hogy a felhasználók által regisztrált eszközök között.

Emellett mostantól több hitelesítésszolgáltatók (CA) adjon meg több Tanúsítványregisztrációs pont helyrendszer-szerepkörök és hozzárendelheti a CAs folyamat kérések a profil részeként.

Az iOS-eszközök társítson egy PFX-tanúsítványprofilhoz egy e-mail profilt, és engedélyezze az S/MIME titkosítással.  Ez lehetővé teszi, hogy az S/MIME IOS a natív e-mail ügyfélprogramban és társítja azt a megfelelő S/MIME titkosítási tanúsítvány.

A Configuration Manager-tanúsítványokkal kapcsolatos további információkért lásd: [a System Center Configuration Managerben tanúsítványprofilok ismertetése]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles).


## <a name="new-compliance-settings-for-ios-devices"></a>Új megfelelőségi beállítások az iOS-eszközök

A következőkkel egészült ki új beállítások az iOS-eszközök a konfigurációs elemek használható. Ezek a beállítások, amelyek korábban már létezett a Microsoft Intune önálló konfigurációban, és most már elérhető a Configuration Manager Intune használatakor. Ha segítségre van szüksége a beállítások, lásd: [iOS-szabályzatbeállítások a Microsoft Intune-ban](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).

- **Icloudba történő szinkronizálásának engedélyezése felügyelt alkalmazásokból való szinkronizálja az adatokat**
- **Tevékenységek más eszközön való folytatáshoz handoff számára**
- **Fénykép megosztása icloudba szinkronizálásának engedélyezése**
- **icloud szolgáltatásba fényképe oszlopot könyvtár**
- **Új vállalati alkalmazás szerzők megbízhatóság**
- **A felhasználó számára az iBook áruházban "Erotika" ellátott tartalom letöltésének engedélyezése** (csak felügyelt módban)
- **Körkörös észlelési használandó párosított Apple órák kényszerítése**
- **Kérelmek kimenő AirPlay jelszavát**
- **Módosítsa a fiókbeállításokat** (csak felügyelt módban)
- **Alkalmazás mobiladatátvitel-használati beállításai vált** (csak felügyelt módban)
- **Összes tartalom és beállítás törlésére** (csak felügyelt módban)
- **Állítson be korlátozásokat, eszközön** (csak felügyelt módban)
- **Az egy iOS-eszközzel párosítható eszközök szabályozásának való használatát a gazdapárosítási** (csak felügyelt módban)
- **Konfigurációs profilok és tanúsítványok telepítésének** (csak felügyelt módban)
- **Eszköz neve módosítása** (csak felügyelt módban)
- **PIN-kód módosítása** (csak felügyelt módban)
- **Apple Watch párosítás** (csak felügyelt módban)
- **Értesítési beállításainak módosítása** (csak felügyelt módban)
- **Módosítás tapéta** (csak felügyelt módban)
- **Diagnosztika küldésének beállításainak módosítása** (csak felügyelt módban)
- **Bluetooth-módosítás** (csak felügyelt módban)
- **AirDrop** (csak felügyelt módban)
- **Használja az internetről lekérdezés felhasználó által létrehozott tartalom Siri** (csak felügyelt módban)
- **A Siri Profanitás szűrő** (csak felügyelt módban)
- **A Spotlight kereső internetes eredmények visszaadásának** (csak felügyelt módban)
- **Word definition keresési** (csak felügyelt módban)
- **A prediktív billentyűzetek** (csak felügyelt módban)
- **Automatikus javítási** (csak felügyelt módban)
- **Azok a helyesírás-ellenőrzési** (csak felügyelt módban)
- **Azok a billentyűparancsok** (csak felügyelt módban)
<!--- - **Enterprise app trust settings modification** --->
- **Apple Configuratort és iTunes csak alkalmazások telepítése** (csak felügyelt módban)
- **Automatikus app letöltések** (csak felügyelt módban)
- **A barátok alkalmazás beállításai módosításokat** (csak felügyelt módban)
- **Az iBooks áruház elérésének** (csak felügyelt módban)
- **Üzenetek alkalmazás** (csak felügyelt módban)
- **Podcastok** (csak felügyelt módban)
- **Apple zene** (csak felügyelt módban)
- **iTunes rádió** (csak felügyelt módban)
- **Apple hírek** (csak felügyelt módban)
- **Game Centerbeli** (csak felügyelt módban)
- **AirDrop tekinti egy nem felügyelt cél**

## <a name="android-for-work-support"></a>Android munkahelyi támogatásához

Technikai előzetes verziójában 1702 verziótól kezdődően köthető egy Google-fiók a hibrid MDM-bérlő. Ez lehetővé teszi, hogy tegye a következőket:

- Regisztrálása [Android-eszközök támogatott](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) Android for Work, mint a regisztrált eszközök közül munkahelyi profilok létrehozása
- A Play Store munkahelyi alkalmazások jóváhagyása, a Configuration Manager-konzol szinkronizálása őket és majd telepítheti őket az eszközök munkahelyi profilok
- Létrehozhat és telepíthet a konfigurálási elemeket, hogy az eszközök munkahelyi profil és a jelszó beállítása
- Létrehozhat és telepíthet megfelelőségi házirend elemek és erőforrás-hozzáférési profilok Android munkahelyi eszközök módon már az Android-eszközök
- Szelektív törlés végrehajtását az Android munkahelyi eszközök

Android for Work létrehoz egy munkahelyi profilt az eszközön mely Intune-ban, amikor beléptet egy eszközt kezelhet. A munkahelyi profil létezik mellé a személyes profillal az Android készülékén. Felhasználók egyszerűen átválthatja munkahelyi profil alkalmazásokat és a személyes profil alkalmazások között. A személyes profil elemeinek nem tudja kezelni. Személyes alkalmazások és adatok megmaradnak a nem felügyelt. A Configuration Manager tartalmával együtt a munkahelyi profil teljes hozzáféréssel rendelkezik, és eltávolíthatja az eszközről.

Android for Work egy külön platform az Android, és döntse el, hogy mely űrlap a felügyelet az Android-eszközök, amelyek támogatják a munkahelyi profilok használatához szüksége lesz.

### <a name="try-it-out"></a>Próbálja ki!
A következő szakaszok ismertetik a Android for Work felügyeletének.

#### <a name="enable-android-for-work-management"></a>Android for Work felügyeletének engedélyezése
1. Google-fiók létrehozása a munkahelyi rendszergazdai fiók, amely az összes Android munkahelyi felügyeleti feladatok az adott Intune-bérlőt lesz társítva a Android használandó https://accounts.google.com/SignUp. Ennek oka lehet egy Google-fiókja a rendszergazdák, akik Android-eszközök kezeléséhez között meg van osztva. Ez az a szervezet által használt kezelésére és alkalmazások közzététele a Play munkahelyi konzol a Google-fiók. Ehhez a fiókhoz használandó hagyja jóvá a Play Store munkahelyi alkalmazásokat, így nyomon követjük, hogy a fiók nevét és jelszavát.
2. Android-eszközök regisztrációjának engedélyezéséhez a Google-fiók kötése az Intune-bérlőjéhez tartozik, a Configuration Manager kezeli:
  1. Keresse fel **felügyeleti** > **áttekintése** > **Cloud Services** > **Microsoft Intune-előfizetések** válassza ki az Intune-előfizetés.
  2. Kattintson a menüszalagon található **platformok konfigurálása** > **Android** , és győződjön meg arról, hogy **Android-igénylés engedélyezése** be van jelölve.
  3. Kattintson a menüszalagon található **platformok konfigurálása** > **Android for Work**.
  4. Kattintson a párbeszédpanelen **Android konfigurálása az Intune-konzolon munka**. Az Intune-konzolon megnyitása a böngészőben.
  5. Az Intune rendszergazdai hitelesítő adatok segítségével jelentkezzen be az Intune-portál.
  6. Kattintson a **konfigurálása** Google Play áruházból Android munkahelyi webhely megnyitásához.
  7. A Google bejelentkezési lapon adja meg a Google-fiók hitelesítő adatait az 1. lépés, és adja meg a vállalati adatok.
3. Amikor visszatér az Intune-portál, Android for Work engedélyezve van, és három regisztrációs beállítások érhetők el Android munkahelyi eszközök:
  - **Az összes eszköz kezelését, Android** (letiltott) – az összes Android-eszközök, beleértve az eszközök, amelyek támogatják az Android for Work fogja regisztrálni, mint a hagyományos Android-eszközök
  - **Támogatott eszközök munkára Android rendszer kezelése** – (engedélyezve), amely támogatja az Android for Work minden eszköz munkahelyi eszközök, Android regisztrált. Bármely Android-eszköz nem támogatja az Android for Work mint egy hagyományos Android-eszköz regisztrálva van.
  - **Csak ebben a csoportokban lévő felhasználók által támogatott eszközök munkára Android rendszer kezelése** -(teszteli) segítségével célozhat meg Android for Work felügyeletének csak bizonyos felhasználók számára. A kiválasztott csoportok számára, amely támogatja az Android for Work egy eszközt regisztráló csak tagjai munkahelyi eszközök regisztrálása, Android. Minden más, Android-eszközök regisztrálása.
  
> [!NOTE]
> Egy ismert probléma megakadályozza, hogy a **kezelése támogatott eszközök csak ebben a csoportokban lévő felhasználók Android for Work** várt módon működik parancsát. A felhasználói eszközök az Azure ad-ben megadott helyett Android for Work Android, csoportok fognak beléptetni. Android for Work teszteléséhez kell használnia a **munka Android rendszer összes támogatott eszközök kezelése**.


  Ahhoz, hogy Android munkahelyi regisztrálásra, ki kell választania, az alsó két lehetőségek közül. A **kezelése támogatott eszközök csak ebben a csoportokban lévő felhasználók Android for Work** beállítás megköveteli, hogy Azure Active Directory biztonsági csoportok beállítása az első.

Látni fogja, a fiók nevét és a szervezet neve, az Intune portál befejezésekor a kötés; Ezen a ponton zárja be mindkét böngészőkben.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Jóváhagyhatja és telepítheti az Android munkahelyi alkalmazások
Kövesse az alábbi lépéseket a Play Store munkahelyi alkalmazások, a Configuration Manager konzol szinkronizálása őket, és telepítheti őket az eszközök munkahelyi felügyelt Android. Alkalmazások telepítése a felhasználók munkahelyi profilok, lesz szüksége a Play áruházban a munkahelyi alkalmazások jóváhagyásához, és majd a az alkalmazásokat a Configuration Manager konzol szinkronizálása.

1. Nyisson meg egy böngészőt, és navigáljon: https://play.google.com/work.
2. Jelentkezzen be van kötve, az Intune-bérlőjéhez tartozik Google-rendszergazdai fiók használatával.
3. Alkalmazásokat szeretne telepíteni a környezetben, és kattintson a Tallózás **jóváhagyás** esetében.
4. Nyissa meg a Configuration Manager konzol **rendszergazda** > **áttekintése** > **Felhőszolgáltatások** > **Android for Work** kattintson **szinkronizálási**.
5. Várjon, amíg az alkalmazások akár 10 percet, és folytassa **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **Áruházbeli alkalmazások Licencadatai**.
6. Kattintson a egy alkalmazást a Play áruházból munka szinkronizálva, és kattintson a **alkalmazás létrehozása**.
7. Fejezze be a varázslót, és kattintson a **Bezárás**.
8. Ugrás a **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **alkalmazások**, válassza ki az Android munkahelyi alkalmazások és központi telepítése a szokásos módon.

Play szinkronizálva munkahelyi alkalmazásokat a Configuration Managerrel, jóvá kell hagynia a legalább egy alkalmazást a munkahelyi webhely a Play áruházból.

#### <a name="enroll-an-android-for-work-device"></a>Az Android munkahelyi eszköz regisztrálása
Hogyan regisztrál az Android eszközök munkahelyi hasonlít a regisztrációt az Android. Alkalmazás letöltése és futtatása a vállalati portál Android-verziójában a mobileszközön. Kérni fogja a beléptetési folyamat részeként munkahelyi profil létrehozásához.  A munkahelyi profil létrehozása után át kell váltania a vállalati portál felügyelt verzió. A felügyelt vállalati portál jobb alsó sarokban kis narancssárga táskát címkéje.

#### <a name="create-and-deploy-a-configuration-item"></a>Létrehozhat és telepíthet egy konfigurációs elem
Android for Work van két beállítás a konfigurációelemhez:
- Jelszó
- A munkahelyi profil

Konfigurálhatja a tartalom munkahelyi profilok, valamint Android 6-es eszközökön a következő konfigurációs elemek közötti megosztása vagy magasabb:
- A viselkedés alkalmazásokat engedélyekről kérése
- Hogy az alkalmazások a munkahelyi profilon belüli értesítések jelennek meg a zárolási képernyőn

Próbálkozzon a következővel, a standard munkafolyamaton keresztül egy konfigurációs elem létrehozása, válassza a **Android for Work** a a **általános** lapon, és konfigurálja a beállításokat az egyes a beállításcsoportok, a konfigurációs elem hozzáadása egy alapkonfigurációt, és központi telepítése a szokásos módon. Ezek a beállítások csak Beléptetve az munka, és nem a regisztrált Android-, Android-eszközökre vonatkoznak.

#### <a name="perform-selective-wipe"></a>Hajtsa végre a szelektív törlés
Eszközök, Android for Work csak lehet szelektív törlése lehetséges, mert a munkahelyi profil csak felügyelt regisztrálva. Ez megakadályozza, a személyes profil adatainak törlése. A szelektív Törlés az eszköz munkahelyi egy Android minden alkalmazást és adatot, beleértve a munkahelyi-profil eltávolítása és az eszköz unenrolls.

Az Android munkahelyi eszköz szelektív törlése, használja a normál [szelektív törlési folyamat](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe) a Configuration Manager konzolon.

#### <a name="known-issues-for-android-for-work"></a>Android for Work kapcsolatos ismert problémák
**Szinkronizálás konfigurálása ütemezni Android a munkahelyi e-mail profilok okokért központi telepítése sikertelen** "Ütemezés" a beállítások a ConfigMgr felhasználói felületének Android munkahelyi e-mail-profilok egyikét. Más platformokon így a rendszergazdát, hogy konfiguráljon egy ütemezést az e-mailek és más e-mail fiók adatait le azt a rendszer a mobil eszközök szinkronizálása. Azonban nem működik az Androidos munkahelyi e-mail-profilok, és bármely beállítás csak "Nincs konfigurálva", akkor a profil szolgáltatás nem telepíthető az egyik eszközön sem.

