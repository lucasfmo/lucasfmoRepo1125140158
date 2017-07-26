---
title: "Távoli kapcsolati profilok létrehozása |} Microsoft Docs"
description: "System Center Configuration Manager távoli kapcsolati profilok használata lehetővé teszi a felhasználók távolról érjék el a munkahelyi számítógépekhez."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c6eabc4-5dda-4682-b03e-3a450e6ef65a
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 72fc94c6449649656a7e8b81659c2b5cc2551107
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="remote-connection-profiles-in-system-center-configuration-manager"></a>Távoli kapcsolati profilok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a System Center Configuration Manager távoli kapcsolati profiljaival lehetővé teszi a felhasználók távolról érjék el a munkahelyi számítógépeket, amikor nem csatlakoznak a tartományhoz, vagy ha a személyi számítógépükkel az interneten keresztül csatlakoznak.  

 A felhasználók a következő eszköztípusokról kapcsolódhatnak munkahelyi számítógépükhöz:  

-   Microsoft Windows rendszerű számítógépek  

-   IOS rendszerű eszközök  

-   Android rendszerű eszközök  

Távoli kapcsolati profilokkal távoli asztali kapcsolat-beállításokat telepíthet a Configuration Manager-hierarchiában található felhasználóknál. A felhasználók ezt követően a vállalati portál segítségével bármelyik elsődleges munkahelyi számítógépükhöz hozzáférhetnek a távoli asztalon keresztül, a vállalati portál által szolgáltatott távoli asztali beállítások használatával.  

A Microsoft Intune használata szükséges, ha azt szeretné, hogy a felhasználók a vállalati portál használatával csatlakozzanak munkahelyi számítógépükhöz. Az Intune nélkül a felhasználók a Távoli asztal szolgáltatást VPN-kapcsolaton keresztül használva érhetik el a távoli kapcsolati profil adatait a munkahelyi számítógépükhöz való csatlakozáshoz.  

> [!IMPORTANT]  
>  Ha távoli kapcsolati profil beállításainak megadása a Configuration Manager konzol használatával, a beállításokat az ügyfélszámítógép helyi házirendje tárolja. Ezek a beállítások esetleg felülbírálhatják a Távoli asztal más alkalmazással konfigurált beállításait. Emellett ha a Windows csoportházirendjének használatával konfigurálja a távoli asztal beállításait, a csoportházirendben megadott beállítások felülírják a Configuration Manager használatával konfiguráltakat.  

 Ha telepíti a Configuration Manager, egy új biztonsági csoportot, **távoli számítógép-kapcsolat**, jön létre. Ez a csoport akkor töltődik fel tagokkal, amikor olyan távoli kapcsolati profilt telepít, amelyben szerepelnek annak a számítógépnek az elsődleges felhasználói, amelyen telepíti a profilt. Bár a helyi rendszergazdának lehetősége van arra, hogy a csoportba felhasználóneveket vegyen fel, ezek a felhasználók a központilag telepített távoli kapcsolati profilok következő megfelelőségi kiértékelésekor eltávolítódnak a csoportból.  

 Ha a csoportba manuálisan vesz fel felhasználót, a felhasználó kezdeményezhet távoli kapcsolatokat, de a vállalati portálon nem lesznek közzétéve a kapcsolat adatai.  

 Ha egy olyan felhasználó hozzá lett adva a Configuration Manager által, a Configuration Manager ezt a változtatást automatikusan kijavítja a felhasználót, ha a távoli kapcsolati profil következő biztonsági csoportból manuálisan eltávolít kompatibilitásának kiértékelése.  

> [!IMPORTANT]  
>  Ha a felhasználói eszköz egy felhasználó és eszköz közötti kapcsolat változik (például a számítógép a felhasználó kapcsolódik, már nem lesz a Configuration Manager letiltja a felhasználó elsődleges eszköze, a távoli kapcsolati profilt és a Windows tűzfal beállításait, hogy megakadályozza a kapcsolódást a számítógéphez.  

## <a name="prerequisites"></a>Előfeltételek  

### <a name="external-dependencies"></a>Külső függőségek  

|Függőség|További információ|  
|----------------|----------------------|  
|Távoli asztali átjárókiszolgáló.|Ha szeretné, hogy a felhasználók a vállalati tartományon kívülről is tudjanak csatlakozni az internethez, távoli asztali átjárókiszolgálót kell telepítenie és konfigurálnia.<br /><br /> Ha a távoli asztal vagy a terminálszolgáltatások beállításait egy másik alkalmazás vagy csoportházirend-beállítások kezelik, lehetséges, hogy a távoli kapcsolati profilok nem működnek majd megfelelően. Amikor telepíti a távoli kapcsolati profilok a Configuration Manager konzolról, annak beállításait az ügyfélszámítógép helyi házirendjében tárolódnak. Ezek a beállítások felülírhatják a távoli asztal más alkalmazás által konfigurált beállításait. Ha a csoportházirend-beállítások segítségével konfigurálja a távoli asztal beállításait, a csoportházirend-beállítással a megadott beállítások felülírják a Configuration Manager által konfigurált beállításokat.<br /><br /> A távoli asztali átjárókiszolgáló telepítéséről és beállításáról a Windows Server dokumentációjában olvasható további információ.|  
|Ha az ügyfélszámítógépeken állomásalapú tűzfal fut, engedélyezni kell rajta az Mstsc.exe programot.|Távoli kapcsolati profil beállításakor engedélyeznie kell a **Windows tűzfal kivétel engedélyezése a kapcsolatok számára Windows-tartományokban és magánhálózatokon** beállítást. Ha ez a beállítás engedélyezve van, a Configuration Manager automatikusan beállítja az Mstsc.exe program engedélyezését a Windows tűzfal. Ha azonban az ügyfélszámítógépeken másik állomásalapú tűzfal fut, ezt a tűzfalfüggőséget kézzel kell megadni.<br /><br /> A Windows tűzfal konfigurálását biztosító csoportházirend-beállítások felülírhatják a Configuration Managerben megadott beállítást. Ha a Windows tűzfalat csoportházirend segítségével konfigurálja, ellenőrizze, hogy a csoportházirend-beállítások ne tiltsák le az Mstsc.exe programot.|  

### <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  

|Függőség|További információ|  
|----------------|----------------------|  
|A Configuration Manager kapcsolódnia kell a Microsoft Intune (más néven a hibrid konfiguráció).|A Configuration Manager kapcsolódik a Microsoft Intune kapcsolatos további információkért tekintse meg a mobileszközök kezelése a Configuration Manager és a Microsoft Intune.|  
|Annak érdekében, hogy egy felhasználó a vállalati hálózaton található munkahelyi számítógéphez tudjon csatlakoznia, az adott számítógépnek a felhasználó elsődleges eszközének kell lennie.|Felhasználó-eszköz kapcsolatra vonatkozó további információkért lásd: [felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity).|  
|Távoli kapcsolati profilok kezeléséhez előbb meg kell adni bizonyos biztonsági engedélyeket.|A **megfelelőségibeállítás-kezelő** biztonsági szerepkör tartalmazza azokat az engedélyeket, amelyekre a távoli kapcsolati profilok kezeléséhez szükség van. További információk a következő helyen találhatók: <br />[Szerepköralapú Adminisztráció konfigurálása](/sccm/core/servers/deploy/configure/configure-role-based-administration).|  

## <a name="security-and-privacy-considerations-for-remote-connection-profiles"></a>A távoli kapcsolati profilok biztonságával és adatvédelmével kapcsolatos megfontolások  

### <a name="security-considerations"></a>Biztonsági megfontolások  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|A felhasználó-eszköz kapcsolatot manuálisan adja meg, ne hagyja a felhasználóknak, hogy azonosítsák az elsődleges eszközüket. Ezen kívül ne engedélyezze a használat alapú konfigurálást.|Mivel engedélyeznie kell a **Távoli kapcsolatok engedélyezése a munkahelyi számítógépek valamennyi felhasználója számára** beállítást a távoli kapcsolati profil központi telepítése előtt, mindig manuálisan adja meg a felhasználó-eszköz kapcsolatot. Ne tekintse mérvadónak a felhasználóktól vagy az eszköztől begyűjtött adatokat. Ha központilag telepíti a távoli kapcsolati profilokat, és a megbízható rendszergazda nem határozza meg a felhasználó-eszköz kapcsolatot, akkor a jogosulatlan felhasználók emelt szintű jogosultságot kaphatnak, és távolról kapcsolódhatnak a számítógépekhez.<br /><br /> Ha engedélyezi a használat alapú konfigurálást, az információk gyűjtése, amelynek az a Configuration Manager nem védett állapotüzeneteken keresztül. A biztonsági kockázat enyhítése érdekében az ügyfélszámítógépek és a felügyeleti pont között használjon Server Message Block-aláírást (SMB) vagy IP-biztonságot (IPsec-et).|  
|Korlátozza a helyi rendszergazdai engedélyeket a helykiszolgáló számítógépén.|A helykiszolgálón helyi rendszergazdai jogosultságokkal rendelkező felhasználó manuálisan adhat hozzá tagokat a távoli számítógép-kapcsolat biztonsági csoporthoz, amely a Configuration Manager automatikusan hozza létre és kezeli. Ez a jogosultsági szintek megemelkedését okozhatja, mert az ehhez a csoporthoz hozzáadott tagok Távoli asztal engedélyt kaphatnak.|  

### <a name="privacy-considerations"></a>Adatvédelmi megfontolások  

-   Ha egy felhasználó kapcsolatot kezdeményez egy munkahelyi számítógéphez a vállalati portálról, egy .rdp vagy .wsrdp kiterjesztésű fájlt tölt le, mely tartalmazza az eszköz nevét és a Távoli asztali átjáró kiszolgálójának nevét, mely a távoli asztali munkamenet kezdeményezéséhez szükséges. A fájl kiterjesztése az eszköz operációs rendszerétől függ. Például a Windows 7 és a Windows 8 operációs rendszer egy .rdp fájlt, míg a Windows 8.1 egy .wsrdp fájlt használ.  

-   A felhasználó választhat az .rdp fájl megnyitása vagy mentése között. Ha a felhasználó az .rdp fájl megnyitását választja, a fájl a böngésző gyorsítótárában tárolódhat, a böngésző megőrzési beállításaitól függően. Ha a felhasználó a fájl mentését választja, akkor az nem lesz eltárolva a gyorsítótárban. A fájlt addig tárolja az eszköz, míg a felhasználó nem törli.  

-   A .wsrdp fájlt automatikusan letölti és helyben elmenti az eszköz. Ezt a fájlt akkor írja felül az eszköz, amikor a felhasználó legközelebb futtatja a távoli asztali munkamenetet.  

-   A távoli kapcsolati profilok konfigurálása előtt gondolja át az adatvédelmi követelményeit.  


## <a name="create-a-remote-connection-profile"></a>Távoli kapcsolati profil létrehozása

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **távoli kapcsolati profilok**.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Távoli kapcsolatprofil létrehozása**elemre.  

4.  A **Távoli kapcsolati profil létrehozása varázsló** **Általános**lapján adja meg a profil nevét és opcionálisan a leírását. Mindkettő legfeljebb 256 karakterből állhat.  

5.  Az a **profil** beállítások lapon adja meg a távoli kapcsolati profil következő beállításait:  

    -   **A Távoli asztali átjárókiszolgáló teljes neve és portszáma (nem kötelező)** : adja meg a kapcsolatokhoz használandó távoli asztali átjárókiszolgáló nevét.  

        > [!NOTE]  
        >  A Configuration Manager nem támogatja az IDN-formátumú tartománynév használható ebben a mezőben adja meg a kiszolgálót.  
        >   
        >  A kiszolgáló neve nem lehet hosszabb, mint 256 karakter, csak nagybetűket, kisbetűket, számokat, valamint a **–** és az **_** karaktert tartalmazhatja, az elemek elválasztására pedig a pont karakter használható.  

    -   **Kapcsolatok engedélyezése csak a Távoli asztalt hálózati szintű hitelesítéssel futtató számítógépek számára**  

6.  Az egyes csatlakozási beállításoknál válassza vagy az **Engedélyezett** , vagy a **Letiltott** lehetőséget:  

    -   **Távoli kapcsolat lehetővé tétele munkahelyi számítógépekhez**  

    -   **Távoli kapcsolatok engedélyezése a munkahelyi számítógépekhez**  

    -   **A Windows tűzfal kivételeinek engedélyezése a kapcsolatok számára Windows-tartományokban és magánhálózatokon**  

    > [!IMPORTANT]  
    >  A varázsló jelen oldaláról továbblépni csak akkor lehet, ha mindhárom beállítás azonos.  

7.  Az a **összegzés** lapon tekintse át a végrehajtandó műveleteket, és fejezze be a varázslót.  

 Az új távoli kapcsolatprofil az **Eszközök és megfelelőség** munkaterületen a **Távoli kapcsolati profilok** csomópontban jelenik meg.  

Távoli kapcsolati profil központi telepítése  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **távoli kapcsolati profilok**.  

3.  Válassza ki a **Távkapcsolati profilok** listában azt a távkapcsolati profilt, amelyiket központilag telepíteni akarja, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Telepítés**elemre.  

4.  A **Távoli kapcsolat profiljának központi telepítése** párbeszédpanelen adja meg a következő információkat:  

    -   **Gyűjtemény** – A **Tallózás** gombra kattintva kiválaszthatja az eszközök azon gyűjteményét, amelyikbe a távkapcsolati profilt telepíteni kívánja.  

    -   **Nem megfelelő szabályok szervizelése** – ezzel a beállítással automatikusan szervizeli a távoli kapcsolati profil nincs jelen az eszközön, például bizonyul talált.  

    -   **Szervizelés engedélyezése a karbantartási időszakon kívül** - Ha lett konfigurálva karbantartási időszak ahhoz a gyűjteményhez, amelyikbe a távkapcsolati profilt telepíti, engedélyezze ezt a beállítást, hogy a Configuration Manager a távoli kapcsolat profilt a karbantartási időszakon kívül is szervizelje. További információ a karbantartási időszakok: [karbantartási időszakok használata](/sccm/core/clients/manage/collections/use-maintenance-windows).  

    -   **Riasztás generálása** - Ha engedélyezi ezt a beállítást, konfigurálhat egy olyan riasztást, amelyik akkor jön létre, amikor a távkapcsolati profil megfelelősége kisebb, mint a megadott dátummal és idővel megadott százalék. Azt is megadhatja, hogy kíván-e riasztást küldeni a System Center Operations Manager alkalmazásnak.  

    -   **Adja meg a megfelelőség értékelésének ütemezését az alapkonfigurációhoz** : adja meg azt az ütemezést, mely szerint a telepített távoli kapcsolati profil kiértékelése történik az eszközökön. Megadhat egyszerű vagy egyéni ütemezést.  

    > [!TIP]  
    >  Ha az eszköz kikerül abból a gyűjteményből, amelyikbe a távkapcsolati profil telepítve lett, az eszközre a távkapcsolati profil beállításai le lesznek tiltva. Ahhoz azonban, hogy ez a folyamat helyesen történjen, már telepítve kell lenni legalább egy konfigurálási elemnek vagy olyan alapkonfigurációnak, amelyik tartalmaz konfigurálási elemet az Ön webhelyéről.  
    >   
    >  A profilt az eszközök értékelik ki, amikor a felhasználó bejelentkezik.  
    >   
    >  Ha két távoli kapcsolati profil van telepítve ugyanarra az eszközgyűjteményre, és az egyik profilban be van jelölve a **Nem megfelelő szabályok szervizelése (ha támogatott)** beállítás, a másik profilban viszont ugyanez a beállítás nincs bejelölve, és a két távoli kapcsolati profil eltérő kapcsolati beállításokat tartalmaz, akkor az a profil, amelyben a beállítás nincs bejelölve, felülírhatja a másik profil beállításait. Ilyen típusú távoli kapcsolati profil központi telepítése a Configuration Manager által nem támogatott.  

5.  Kattintson az **OK** gombra, hogy bezárja a **Távoli kapcsolat profiljának központi telepítése** párbeszédpanelt és létrehozza a központi telepítést.  

## <a name="monitor-a-remote-connection-profile"></a>Távoli kapcsolati profil figyelése  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Megfelelési eredmények megtekintése a Configuration Manager konzolon  

1.  Kattintson a Configuration Manager konzolon **figyelés** > **központi telepítések**.  

3.  Válassza ki a **Központi telepítések** listában a távkapcsolati profilok azon központi telepítését, amelyre vonatkozóan szeretné ellenőrizni a megfelelőségi információkat.  

4.  A távkapcsolati profilok központi telepítésének megfelelőségére vonatkozó összefoglaló információkat a főoldalon tudja ellenőrizni. Részletesebb adatok megtekintéséhez válassza ki a távkapcsolati profilok központi telepítését, majd a **Kezdőlap** **Központi telepítés** csoportjában kattintson az **Állapot megtekintése** elemre a **Telepítés állapota** lap megnyitásához.  

     A **Telepítés állapota** lapon a következő fülek találhatók:  

    -   **Megfelelő:** Az érintett eszközök száma alapján távoli kapcsolati profil megfelelőségét jeleníti meg. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont minden olyan eszközt tartalmaz, amelyik megfelel a távkapcsolati profilnak. Az **Eszköz adatai** ablaktáblán jelennek meg azok az eszközök, amelyek megfelelnek ennek a profilnak. További információk megjelenítéséhez a listában kattintson duplán az eszközre.  

        > [!IMPORTANT]  
        >  A távkapcsolati profil nem kerül kiértékelésre, ha nem alkalmazható az ügyféleszközre, hanem a rendszer megfelelőként jelzi azt.  

    -   **Hiba:** Megjeleníti az érintett eszközök száma alapján kiválasztott távoli kapcsolati profil központi telepítésére vonatkozó hibákat. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont tartalmazza az összes olyan eszközt, amelyik ezzel a profillal hibát jelzett. Amikor kijelöl egy eszközt, az **Eszköz adatai** ablaktáblán megjelennek azok az eszközök, amelyeket a kijelölt probléma érint. A problémáról további információk megjelenítéséhez kattintson duplán a kívánt eszközre a listában.  

    -   **Nem megfelelő:** A távoli kapcsolati profil az érintett eszközök száma alapján nem megfelelő szabályok teljes listáját jeleníti meg. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont tartalmazza az összes olyan eszközt, amelyik nem megfelelő ezzel a profillal. Amikor kijelöl egy eszközt, az **Eszköz adatai** ablaktáblán megjelennek azok az eszközök, amelyeket a kijelölt probléma érint. A problémáról további információk megjelenítéséhez kattintson duplán a kívánt eszközre a listában.  

    -   **Ismeretlen:** Megjeleníti az összes eszközről nem jelentett megfelelőséget, a kijelölt távoli kapcsolati profilok központi telepítésére vonatkozó, eszközeik aktuális ügyfélállapotával együtt.  

5.  A **Telepítés állapota** lapon tekinthetők meg a központilag telepített távkapcsolati profil megfelelőségével kapcsolatos részletes információk. A **Központi telepítések** csomópont alatt létrejön egy ideiglenes csomópont, amellyel később gyorsan előkeresheti ezt az információt.  

### <a name="view-compliance-results-with-reports"></a>Megfelelési eredmények megtekintése jelentésekkel  
 A Configuration Manager beépített jelentéseket tartalmazza, a távoli kapcsolati profilok vonatkozó információk megfigyelésére használhatja. Ezek a jelentések a **Megfelelőség és beállítások kezelése**jelentési kategóriába tartoznak.  

> [!IMPORTANT]  
>  Ha a megfelelőségi beállítások jelentéseiben az **Eszközszűrő** és a **Felhasználószűrő** paraméter szerepel, helyettesítő (%) karaktert kell használni.  

 Jelentéskészítés a Configuration Managerben konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](/sccm/core/servers/manage/reporting).  

