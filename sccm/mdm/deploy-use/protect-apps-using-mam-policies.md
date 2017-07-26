---
title: "Mobilalkalmazás-kezelési házirendekkel alkalmazások védelme |} Microsoft Docs"
description: "Így azok felel meg a vállalat megfelelőségi és biztonsági házirendeket központilag telepített alkalmazások funkcióinak módosítását."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28115475-e563-4e16-bf30-f4c9fe704754
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 74f4dd44089d4a13526c981589e1f497f0e10290
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="protect-apps-using-mobile-application-management-policies-in-system-center-configuration-manager"></a>Alkalmazások védelme mobilalkalmazás-kezelési házirendekkel a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager alkalmazáskezelési házirendek lehetővé teszik az érdekében, hogy azok összhangban a vállalat megfelelőségi és biztonsági házirendjeivel központilag telepített alkalmazások működésének módosítását. Például korlátozhatja a kivágási, másolási és beillesztési műveleteket egy alkalmazáson belül, vagy konfigurálhat egy alkalmazást az URL-címet egy kezelt böngészőben megnyitásához. Az alkalmazáskezelési házirendek az alábbiakat támogatják:  

-   Android 4 vagy újabb rendszerű eszközök  

-   iOS 7 vagy újabb rendszerű eszközök  

Mobilalkalmazás-felügyeleti szabályzatok az Intune által nem kezelt eszközök alkalmazásoknak is védelmet is használhatja. Ezzel az új funkcióval alkalmazhat mobilalkalmazás-felügyeleti szabályzatok az Office 365-szolgáltatásokhoz alkalmazásokat. Ez nem támogatott, amelyek kapcsolódnak a helyszíni Exchange vagy SharePoint-alkalmazások.  

Ez a funkció használatához szüksége az Azure betekintő portálon. A következő témakörök segíthetnek az első lépések megtételében:  
-   [Ismerkedés a mobilalkalmazás-felügyeleti szabályzatokkal az Azure-portálon](https://technet.microsoft.com/library/mt627830.aspx)  
-   [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](https://technet.microsoft.com/library/mt627829.aspx)  

 Nem kell telepíteni az alkalmazáskezelési házirendek közvetlenül, mint a konfigurációelemeket és alapkonfigurációkat a Configuration Manager alkalmazásban. Ehelyett a házirendet társítani kell a korlátozni kívánt alkalmazástelepítési típussal. Az alkalmazás központi telepítési típus központi és telepítve azokon az eszközökön való, a beállítások érvénybe léptetéséhez.  

A korlátozások alkalmazni egy alkalmazásra, az alkalmazásnak tartalmaznia kell a Microsoft Intune App Software Development Kit (SDK). Ilyen típusú alkalmazást az alábbi két módszerrel lehet beszerezni:  

-   **Egy házirend által kezelt alkalmazás használata** (Android és iOS): Ezeket az alkalmazásokat az App SDK a beépített rendelkezik. Ilyen típusú alkalmazások hozzáadásához meg kell adnia az alkalmazás hivatkozását egy alkalmazás-áruházból, például az iTunes vagy Google Play áruházból. Az ilyen típusú alkalmazáshoz nincs szükség további feldolgozásra. Az iOS- és Android-eszközökhöz elérhető, házirend által felügyelt alkalmazások listáját a [Felügyelt alkalmazások a Microsoft Intune mobilalkalmazás-kezelési házirendjeihez](https://technet.microsoft.com/en-us/library/dn708489.aspx)című témakör tartalmazza.  

-   **Használja a "becsomagolt" alkalmazás** (Android és iOS): Ezek az alkalmazások vannak újracsomagolva, hogy tartalmazzák az App SDK a **Microsoft Intune Alkalmazásburkoló eszközével**. Ez az eszköz általában a házon belül létrehozott vállalati alkalmazások feldolgozásához használatos. Nem használható az alkalmazás-áruházból letöltött alkalmazások feldolgozásához. További információ a következő cikkekben talál:
    - [IOS-alkalmazások előkészítése mobilalkalmazás-kezeléshez a Microsoft Intune Alkalmazásburkoló eszközzel](https://technet.microsoft.com/en-us/library/dn878028.aspx)

    - [Android-alkalmazások előkészítése mobilalkalmazás-kezeléshez a Microsoft Intune Alkalmazásburkoló eszközzel](https://technet.microsoft.com/en-us/library/mt147413.aspx)  

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Alkalmazás létrehozása és telepítése mobilalkalmazás-kezelési házirenddel  

##  <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>1. lépés: Egy házirend által kezelt alkalmazás hivatkozásának beszerzése, illetve egy becsomagolt alkalmazás létrehozása  

-   **Szerezzen be egy hivatkozást egy házirend által kezelt alkalmazás**: Az app Store áruházból keresse meg és jegyezze fel a telepíteni kívánt házirend által kezelt alkalmazás URL-CÍMÉT.  

     Az iPad Microsoft Word alkalmazás URL-címe például a következő: **https://itunes.apple.com/hu/app/microsoft-word-for-ipad/id586447913?mt=8**  

-   **Becsomagolt alkalmazás létrehozása**: Olvassa el a témakörök [iOS-alkalmazások előkészítése mobilalkalmazás-kezeléshez a Microsoft Intune Alkalmazásburkoló eszközével való](https://technet.microsoft.com/en-us/library/dn878028.aspx) és [Android-alkalmazások előkészítése a mobilalkalmazás-kezeléshez a Microsoft Intune Alkalmazásburkoló eszközével](https://technet.microsoft.com/en-us/library/mt147413.aspx) becsomagolt alkalmazás létrehozása.  

     Az eszköz létrehoz egy feldolgozott alkalmazást és egy társított jegyzékfájlt. Az alkalmazást tartalmazó Configuration Manager-alkalmazás létrehozásakor használja ezeket a fájlokat.  

##  <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>2. lépés: Az alkalmazást tartalmazó Configuration Manager-alkalmazás létrehozása  
 A Configuration Manager-alkalmazás létrehozásának eltér attól függően, hogy használ-e a házirend által kezelt alkalmazások (külső hivatkozás) vagy olyan alkalmazás, amelynek az iOS számára (alkalmazáscsomag az iOS) a Microsoft Intune Alkalmazásburkoló eszközével használatával lett létrehozva. A Configuration Manager-alkalmazás létrehozásához használja az alábbi eljárások egyikét.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása** megnyitásához a **alkalmazás létrehozása** varázsló.  

4.  Az **Általános** lapon válassza **Az alkalmazás adatainak automatikus észlelése a telepítési fájlokban**lehetőséget.  

5.  A **Típus** legördülő listából válassza az **Alkalmazáscsomag az iOS számára (\*.ipa fájl)** elemet.  

6.  Válasszon **Tallózás** a importálja, és válassza a kívánt csomag kiválasztásához **következő**.  

7.  Az **Általános információ** lapon adja meg azt a leíró szöveget és kategóriainformációt, amelyet meg szeretne jeleníteni a felhasználóknak a vállalati portálon.  

8.  Fejezze be a varázslót.  

 Az új alkalmazás megjelenik a **Szoftverkönyvtár** munkaterület **Alkalmazások** csomópontjában.  

### <a name="create-an-application-that-contains-a-link-to-a-policy-managed-app"></a>Egy házirend által kezelt alkalmazás hivatkozást tartalmazó alkalmazás létrehozása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása** megnyitásához a **alkalmazás létrehozása** varázsló.  

4.  Az **Általános** lapon válassza **Az alkalmazás adatainak automatikus észlelése a telepítési fájlokban**lehetőséget.  

5.  A **Típus** legördülő listában válasszon az alábbiak közül:  

    -   IOS: **Alkalmazáscsomag az iOS App Store-ból**  

    -   Android: **Alkalmazáscsomag az Androidhoz a Google Playről**  

6.  Adja meg az URL-címet az alkalmazás (1. lépés), és válassza a **következő**.  

7.  Az **Általános információ** lapon adja meg azt a leíró szöveget és kategóriainformációt, amelyet meg szeretne jeleníteni a felhasználóknak a vállalati portálon.  

8.  Fejezze be a varázslót.  

 Az új alkalmazás megjelenik a **Szoftverkönyvtár** munkaterület **Alkalmazások** csomópontjában.  

##  <a name="step-3-create-an-application-management-policy"></a>3. lépés: Az Alkalmazáskezelési házirend létrehozása  
 Ezután hozzon létre egy Alkalmazáskezelési szabályzatot az alkalmazáshoz társítani. Létrehozhat általános vagy felügyeltböngésző-szabályzatot.  

1)  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazáskezelési házirendek**.  

2)  Az a **Home** lap a **létrehozása** csoportjában válassza **Alkalmazáskezelési házirend létrehozása**.  

3)  Az a **általános** lapon adja meg a nevét és a házirend leírását, és válassza a **következő**.  

4)  Az a **Házirendtípus** lapon válassza ki a platformot és a házirend típusát, és válassza a **következő**. A következő házirendtípusok közül választhat:  

-   **Általános**: Az általános házirendtípus lehetővé teszi, hogy azok összhangban a vállalat megfelelőségi és biztonsági házirendeket központilag telepített alkalmazások működésének módosítását. A korlátozott alkalmazásokban például korlátozhatja a vágás, a másolás és a beillesztés műveletet.  

-   **A Managed Browser**: A Managed Browser-szabályzat lehetővé teszi, hogy Ön döntse el, hogy engedélyezi vagy letiltja a managed browser nem nyithatja URL-címek listáját. A Felügyelt böngésző házirendtípus lehetővé teszi az Intune Managed Browser alkalmazás funkcióinak módosítását. Ez egy olyan webböngésző, amellyel kezelheti a felhasználók által végrehajtható műveleteket, beleértve, hogy milyen webhelyeket kereshetnek fel, és hogy miként történik a tartalmakra mutató hivatkozások megnyitása a böngészőben. További információ az  [iOS-hez készült Intune Managed Browser alkalmazásról](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) és [az Androidhoz készült Intune Managed Browser alkalmazásról](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en).

5)  Az a **iOS-házirend** vagy **Android-házirend** lapon konfigurálja a következő értékeket, és válassza a **következő**. A beállítások eltérhetnek attól függően, hogy a házirendet milyen típusú eszközhöz konfigurálja.  

|Érték|További információ|  
|-----------|----------------------|  
|**A vállalat által kezelt böngészőben megjelenő webtartalom korlátozása**|Lehetővé teszi az alkalmazásnak, hogy a kezelt böngészőben nyissa meg az összes hivatkozást. Ahhoz, hogy működjön ez a beállítás, az alkalmazásnak telepítve kell lennie az eszközökön.|  
|**Android biztonsági mentések tiltása** vagy **iTunes és iCloud biztonsági mentések tiltása**|Információk biztonsági mentésének letiltása az alkalmazásból.|  
|**Más alkalmazásokból való adatátvitel engedélyezése az alkalmazásnak**|Megadhatja azokat az alkalmazásokat, amelyekbe ez az alkalmazás adatokat küldhet. Ha szeretné, nem engedélyezi az adatátvitelt bármely alkalmazásba engedélyezése csak más korlátozott alkalmazásokba átviteli, vagy bármely alkalmazásba tiltott átvitele.<br /><br /> iOS-eszközök esetén a kezelt és nem kezelt alkalmazások közötti dokumentumátvitel letiltásához egy olyan mobileszköz-biztonsági házirendet is konfigurálnia és alkalmaznia kell, amely letiltja a **Kezelt dokumentumok engedélyezése más nem kezelt alkalmazásokban**beállítást.<br /><br /> Ha csak engedélyezi az adatátvitelt más korlátozott alkalmazásokba, az Intune PDF- és képmegtekintői (ha telepítve vannak) segítségével a megfelelő típusú tartalmak megnyitásához.|  
|**Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak**|Megadhatja azokat az alkalmazásokat, amelyekből ez az alkalmazás adatokat fogadhat. Dönthet úgy, hogy letiltja az adatátvitel minden alkalmazásból engedélyezése csak más korlátozott alkalmazásokból, illetve bármilyen alkalmazásból érkező adatátvitel engedélyezése.|  
|**A „Mentés másként” művelet letiltása**|Letiltja a a **Mentés másként** beállítást az e házirendet használó alkalmazásokban.|  
|**Kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal**|Megadhatja, hogy miként legyen használható a kivágási, a másolási és a beillesztési művelet az alkalmazással. A következő lehetőségek közül választhat:<br /><br /> **Blokkolt** – nem engedélyezi a kivágási, másolási és beillesztési műveletek letiltása az alkalmazás és más alkalmazások között.<br /><br /> **Házirend által felügyelt alkalmazások** – lehetővé teszi kivágási, másolási és beillesztési műveletek csak az alkalmazás és más korlátozott alkalmazások között.<br /><br /> **Házirend által kezelt alkalmazások beillesztéssel** – lehetővé teszi az adatok kivágása vagy másolása az alkalmazásból illeszthetők be más korlátozott alkalmazásokba. Lehetővé teszi az adatok kivágása vagy bármely alkalmazásból illeszthető be az alkalmazásba másolva.<br /><br /> **Bármely alkalmazás** – korlátozás nélkül használhatók a kivágási, másolási és beillesztési műveletek az alkalmazásból.|  
|**Egyszerű PIN-kód szükséges a hozzáféréshez**|A felhasználónak az alkalmazás használatához megadott PIN-kód. A felhasználónak kapcsolatba kell beállítaniuk ezt, az első alkalommal futtatja az alkalmazást.|  
|**Kísérletek száma a PIN-kód alaphelyzetbe állítása előtt**|Azt a hányszor tehessen kísérletet, mielőtt a felhasználó a PIN-kód alaphelyzetbe állítását.|  
|**Vállalati hitelesítő adatok szükségesek a hozzáféréshez**|Megköveteli, hogy a felhasználónak meg kell adnia a vállalati bejelentkezési adatait az alkalmazás eléréséhez.|  
|**A vállalati házirenddel való eszközkompatibilitás szükséges a hozzáféréshez**|Lehetővé teszi, hogy az alkalmazás használata csak akkor, ha az eszköz nincs függetlenítve vagy rootolva.|  
|**A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)**|Meghatározza az adott időszakban, mielőtt az alkalmazás hozzáférési követelményeinek újbóli ellenőrzéséig fennmaradó, miután az alkalmazás elindul (a a **időtúllépés** mező).<br /><br /> Az a **Offline türelmi időszak** mező, ha az eszköz offline állapotban, adja meg az adott időszakban az alkalmazás hozzáférési követelményeinek újbóli ellenőrzéséig.|  
|**Alkalmazásadatok titkosítása**|Meghatározza, hogy ezzel az alkalmazással társított összes adat titkosítva van, például SD-kártyán tárolt adatok kívülről, tárolt adatokat is beleértve.<br /><br /> **Titkosítás iOS rendszerhez**<br /><br /> A Configuration Manager mobilalkalmazás-kezelési házirendjével társított alkalmazások esetén az adatok titkosítása az operációs rendszer által biztosított eszközszintű titkosítást használ. Ez az egy eszköz a rendszergazda segítségét. be kell állítani PIN-házirendjén keresztül engedélyezhető Ha a PIN-kód szükséges, az adattitkosítás a mobilalkalmazás-felügyeleti szabályzatban megadott beállítások szerint. Az Apple dokumentációjában leírtaknak [az iOS 7 által használt modulokra érvényes a FIPS 140-2 szerinti tanúsítást alkalmaznak](http://support.apple.com/en-us/HT202739).<br /><br /> **Titkosítás Android rendszerhez**<br /><br /> A Configuration Manager mobilalkalmazás-kezelési házirendjével társított alkalmazások esetén titkosítást a Microsoft biztosítja. Az adatok titkosítása a fájl I/O műveleteivel egy időben történik a mobilalkalmazás-kezelési házirendben megadott beállításnak megfelelően. Az Androidban a kezelt alkalmazások az AES-128 titkosítást használják CBC módban, a platform kriptográfiai tárainak felhasználásával. A titkosítási módszerre nem érvényes a FIPS 140-2 típusú tanúsítvány. Az eszköz tárhelyén található tartalom mindig titkosított.|  
    |**Képernyőrögzítés letiltása** (csak Android-eszközök esetén)|Megadhatja, hogy az eszköz képernyő-rögzítési lehetőségei le legyenek tiltva az alkalmazás használatakor.|  

6)  Az a **Managed Browser** lapon adja meg, hogy a felügyelt böngésző kap, a listában csak URL-címek megnyitásához vagy a Managed browser nem nyithatja meg az URL-címeket a listában, és válassza a **következő**.  
További információkért lásd: [kezelése Internet-hozzáférés felügyelt böngészőszabályzatokkal](manage-internet-access-using-managed-browser-policies.md).  

7)  Fejezze be a varázslót.  

 Az új házirend megjelenik a **Szoftverkönyvtár** munkaterület **Alkalmazáskezelési házirendek** csomópontjában.  

##  <a name="step-4-associate-the-application-management-policy-with-a-deployment-type"></a>4. lépés: Az Alkalmazáskezelési házirend társítása egy központi telepítési típussal  

 Amikor központi telepítési típust hoz létre egy alkalmazáshoz, amelyhez alkalmazáskezelési házirendre, a Configuration Manager felismeri ezt, és megkéri, hogy társítson egy Alkalmazáskezelési házirendet. A Managed Browser szükségesek hozzá kell rendelnie egy általános és a Managed Browser-szabályzatot. További információkért lásd: [alkalmazásokat](create-applications.md).  

> [!IMPORTANT]  
>  Ha az alkalmazás már telepítve van, majd az új központi telepítési típus telepítése sikertelen amíg ezt a társítást. Ezt a társítást az alkalmazás **Tulajdonságai** között végezheti el az **Alkalmazáskezelés** lapon.  

> [!IMPORTANT]  
>  Az iOS 7.1-es verziójánál operációs rendszereket futtató eszközök esetén a társított házirendek rendszer nem távolítja el, amikor a rendszer eltávolítja az alkalmazást.  
>   
>  Ha az eszköz regisztrációját megszüntetik a Configuration Manager alkalmazásból, házirendek nem lesznek eltávolítva az alkalmazásokat. Alkalmazások, amelyekre házirendeket alkalmaztak megőrzi a házirend-beállításokat, az alkalmazás eltávolítása és újratelepítése után is.  

##  <a name="step-5-monitor-the-app-deployment"></a>5. lépés: Az alkalmazás telepítésének figyelése  
 Miután létrehozott és telepített egy mobilalkalmazás-kezelési házirenddel társított alkalmazást, figyelheti az alkalmazást, és oldja meg az esetleges házirendütközéseket.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **áttekintése** > **központi telepítések**.  

3.  Válassza ki a telepítést, amelyet létrehozott. Ezt követően a **Home** lapra, majd **tulajdonságok**.  

4.  A részleteket tartalmazó ablaktáblán a telepítés alatt **kapcsolódó objektumok**, válassza a **alkalmazáskezelési házirendek**.  

 Alkalmazások figyelésével kapcsolatos további információkért lásd: [alkalmazások figyeléséhez](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

##  <a name="learn-how-policy-conflicts-are-resolved"></a>Ismerje meg a házirend-ütközések feloldása  
 Ha a felhasználó vagy eszköz első telepített egy mobilalkalmazás felügyeleti házirend ütközik, a rendszer eltávolítja az ütközésben lévő beállításérték a házirendet, amely az alkalmazás központi telepítése. Ezt követően az alkalmazás egy beépített ütközési értéket használ.  

 Ha az alkalmazás vagy felhasználó későbbi telepített egy mobilalkalmazás felügyeleti házirend ütközik, az ütközésben lévő beállításérték nem frissül, az alkalmazásra alkalmazott mobilalkalmazás-felügyeleti házirend, és az alkalmazás beállítás meglévő értékét használja.  

 Azokban az esetekben, amikor az eszköz vagy a felhasználó két ütköző házirendet kap, a következő viselkedés tapasztalható:  

-   A házirend még telepítve van az eszközön, a meglévő házirend-beállítások nem a rendszer felülírja.  

-   Ha nincs házirend már alkalmazva van az eszközön, és két ütköző beállítás vannak telepítve, az az eszközbe épített alapértelmezett beállítás használatos.  

##  <a name="see-a-list-of-available-policy-managed-apps"></a>Tekintse meg a rendelkezésre álló, házirend által kezelt alkalmazások listája  
 A házirend listája, amelyek elérhetők az iOS és Android-eszközök felügyelt alkalmazásokban: [Microsoft Intune alkalmazási partnerektől származó](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).  

