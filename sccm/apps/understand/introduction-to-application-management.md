---
title: "Az Alkalmazáskezelés bemutatása |} Microsoft Docs"
description: "Fedezze fel az alapvető adatok kezelését és telepítését a System Center Configuration Manager alkalmazások lesz szüksége."
ms.custom: na
ms.date: 12/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: robstackmsft
ms.author: robstack
manager: angrobe
experimental: true
experiment_id: rob-table-161101
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5aef08865b232ff2dacec6906098bebf4e42e6b1
ms.openlocfilehash: 699adb5fac0c625c321db011af6989cc4c0778ec
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>Alkalmazások kezelése a System Center Configuration Manager bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben megismerheti a System Center Configuration Manager alkalmazások használatának megkezdése előtt tudnia kell alapjai.  

> [!TIP]  
>  Ha már tudja, hogyan kezelheti az alkalmazásokat a Configuration Manager alkalmazásban, ez a témakör kihagyhatja, és lépjen tovább a mintaalkalmazás létrehozásával. Lásd: [Alkalmazás létrehozása és központi telepítése a System Center Configuration Managerrel](../../apps/get-started/create-and-deploy-an-application.md).  

## <a name="what-is-an-application"></a>Mi az az alkalmazás?  
 Bár a *alkalmazás* kifejezést gyakran használják az informatika világában, a Configuration Manager, az azt jelenti, valami eltér. Az alkalmazásra célszerű úgy gondolni, mint egy dobozra, Ebben a csoportban található egy vagy több készletet a szoftvercsomag telepítési fájlok (néven egy **központi telepítési típus**), valamint útmutatást nyújt a szoftverek telepítésére.  

 Amikor az alkalmazást központilag telepíti az eszközökre, a **követelmények** határozzák meg, hogy az alkalmazás melyik központi telepítési típussal települjön az eszközre.  

 Az alkalmazásokkal természetesen ezen kívül sok más művelet is végezhető – ebben az útmutatóban többek között ezekről is olvashat. Az alábbi táblázatban bemutat néhány olyan fogalmat, amelyet ismernie kell, mielőtt mélyebben elmerülne a rendszer használatában. Ezekre ugyanakkor nem lesz szükség minden létrehozott alkalmazásban:  

|Fogalom|Leírás|    
|-|-|  
|**Requirements**|A Configuration Manager korábbi verzióiban gyakran létre kellett hozni egy gyűjteményt azoknak az eszközöknek, az alkalmazást központilag telepíteni szeretne. Bár ez továbbra is lehetséges, a követelmények azzal enyhítik ennek az igényét, hogy sokkal részletesebb feltételek meghatározását is lehetővé teszik az alkalmazások telepítéséhez.<br /><br /> Meghatározhatja például, hogy egy alkalmazás csak a Windows 10 rendszert futtató eszközökre legyen telepíthető. Ezután telepítheti az alkalmazást az összes eszközön, de csak azokra fog települni, amelyeken Windows 10 fut.<br /><br /> A Configuration Manager annak megállapításához, hogy egy alkalmazás követelmények kiértékelésével, és annak valamelyik telepítési típusát lesz telepítve. Azután meghatározza, hogy melyik telepítési típus segítségével telepítse az alkalmazást. Az ügyfél alapértelmezés szerint hétnaponta újraértékeli a követelményszabályokat a megfelelőség érdekében. Az újraértékelés gyakoriságát a **Központi telepítése újraértékelésének ütemezése**ügyfélbeállítás határozza meg.<br /><br /> További információkért lásd: [hozzon létre és telepítsen egy alkalmazást](../../apps/get-started/create-and-deploy-an-application.md).|  
|**Globális feltételek**|Követelmények egy adott alkalmazásban adott központi telepítési típussal használhatók, amíg a globális feltételek is létrehozhat. Ezek a bármely alkalmazással és a központi telepítési típus használható előre definiált követelményekből álló tárak.<br /><br /> A Configuration Manager olyan beépített globális feltételeket tartalmaz, és létrehozhat saját.<br /><br /> További információkért lásd: [globális feltételek létrehozása](../../apps/deploy-use/create-global-conditions.md).|  
|**Szimulált központi telepítés**|Kiértékeli a követelményeket, észlelési módszer és egy alkalmazás függőségeit. A jelentés az eredményeket az alkalmazás tényleges telepítése nélkül.<br /><br /> További információkért lásd: [alkalmazások központi telepítésének szimulálása](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Központi telepítési művelet**|Megadja, hogy meg szeretné telepíteni, vagy eltávolítani (ha támogatott), az alkalmazást telepíti.<br /><br /> További információkért lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).|  
|**Központi telepítés oka**|Meghatározza, hogy a telepítésre kijelölt alkalmazás **Kötelező**vagy **Elérhető**.<br /><br /> **Szükséges** azt jelenti, hogy az alkalmazás központi telepítése automatikusan megtörténik a beállított ütemezés szerint. A felhasználó azonban nyomon követheti az alkalmazás központi telepítésének állapotát (amennyiben az állapot nem rejtett), és a Szoftverközpont használatával a határidő előtt telepítheti az alkalmazást.<br /><br /> Az**Elérhető** beállítás azt jelzi, hogy ha egy felhasználó számára telepítik az alkalmazást, akkor a felhasználó megkeresheti a közzétett alkalmazást a Szoftverközpontban, és szükség esetén telepítheti.<br /><br /> További információkért lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).|  
|**Változatok**|Amikor egy alkalmazáson vagy egy alkalmazásban található központi telepítési típuson, a Configuration Manager létrehoz egy alkalmazás új verziója. Mindegyik alkalmazásváltozatnál előzményeit, a tulajdonságai megtekintéséhez, állítsa vissza egy alkalmazás egy korábbi verzióját, vagy törölje a régi verziójú.<br /><br /> További információkért lásd: [frissítése és kivonása alkalmazások](../../apps/deploy-use/update-and-retire-applications.md).|  
|**Észlelési módszer**|Az észlelési módszerekkel azonosítható, hogy a központilag telepített alkalmazás telepítve van-e már. Ha az észlelési módszer azt jelzi, hogy az alkalmazás telepítve van, a Configuration Manager nem próbálja meg újra telepíteni azt.<br /><br /> További információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|**Függőségek**|A függőségek egy vagy több olyan, más alkalmazásból származó központi telepítési típust határoznak meg, amelyeket telepíteni kell a központi telepítési típus telepítése előtt. Állíthatja be a függőséget okozó központi telepítési típusok telepítése automatikusan egy központi telepítési típus telepítése előtt.<br /><br /> További információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|**Helyettesítés**|A Configuration Manager lehetővé teszi, hogy frissítheti vagy lecserélheti a meglévő alkalmazások helyettesítési kapcsolat használatával. Amikor egy alkalmazást felülír, megadhatja a felülírt alkalmazás központi telepítési típusát lecseréli egy új központi telepítési típus. Azt is eldöntheti, hogy frissíteni vagy eltávolítani a felülírt alkalmazás előtt a felülírt alkalmazás telepítve van.<br /><br /> További információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|**Felhasználó központú felügyelet**|A Configuration Manager támogatják a különböző alkalmazások felhasználó-központú kezelését, és így rendelje hozzá a meghatározott felhasználókat hozzárendeljék az eszközökhöz. Így ahelyett hogy meg kellene jegyezni a felhasználó eszközének a nevét, az alkalmazások a felhasználó és az eszköz számára is telepíthetők. Ez a funkció elősegíti, hogy a legfontosabb alkalmazások mindig rendelkezésre álljanak minden eszközön, amelyhez az adott felhasználó hozzáfér. Ha egy felhasználó egy új számítógépet kap, automatikusan telepíteni lehet az alkalmazásokat az eszközön ahhoz, hogy jelentkezzen be.<br /><br /> További információkért lásd: [felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).|  

## <a name="what-application-types-can-you-deploy"></a>Milyen típusú alkalmazásokat telepíthet?  
 A Configuration Manager lehetővé teszik a következő alkalmazástípusok telepítését:  

- Windows Installer (*.msi fájl)
- Windows-alkalmazáscsomag (*.appx, *.appxbundle)
- Windows-alkalmazáscsomag (a Windows Áruházban)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Windows Mobile kabinet
- macOS  


Emellett kezelheti az eszközöket a Microsoft Intune-nal vagy a Configuration Manager a helyi kezelés, a további alkalmazástípusok kezelheti:

- Windows Phone-alkalmazáscsomag (*.xap fájl)
- Csomag hozzáadása iOS-hez (*.ipa fájl)
- Alkalmazáscsomag az Androidhoz (*.apk fájl)
- Alkalmazáscsomag Androidhoz a Google Playről
- Windows Phone-alkalmazáscsomag (a Windows Phone Áruházban)
- Windows Installer mobileszköz-felügyelettel
- Webalkalmazás



## <a name="state-based-applications"></a>Állapotalapú alkalmazások  
 A Configuration Manager alkalmazás használja állapot szerinti figyelést, amellyel nyomon követheti a felhasználók és eszközök utolsó központi telepítési állapota. Az állapotüzenetek információkat jelenítenek meg az egyes eszközökről. Például ha egy alkalmazás egy felhasználógyűjtemény számára lett telepítve, megtekintheti a megfelelőségi állapotát a központi telepítés és a központi telepítés célja a Configuration Manager konzolon. A figyelheti minden szoftver központi telepítése a **figyelés** munkaterület a Configuration Manager konzolon. A szoftverek központi telepítése tartalmazza a szoftvercsomagokat, a megfelelőségi beállításokat, az alkalmazásokat. a feladatütemezéseket, a csomagokat és a programokat. További információkért lásd: [alkalmazások figyeléséhez](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Alkalmazások központi telepítésének rendszeresen újra értékeli ki a rendszer a Configuration Manager által. Példa:  

-   A végfelhasználó eltávolít egy telepített alkalmazást. A következő értékelési ciklus során a Configuration Manager észleli, hogy az alkalmazás nincs jelen, és újratelepíti.  

-   Egy eszköz nem felelt meg a követelményeknek, ezért elmaradt az egyik alkalmazás telepítése. Később az eszköz módosul, és most megfelel a követelményeknek. A Configuration Manager észleli a változást, és az alkalmazás települ.  


 Az alkalmazástelepítések újraértékelési időközét használatával állíthatja be a **ütemezés újraértékelése a központi telepítések** ügyfélbeállítást. További információkért lásd: [kapcsolatos](../../core/clients/deploy/about-client-settings.md).  

## <a name="get-started-creating-an-application"></a>Bevezetés az alkalmazások létrehozási folyamatába  
 Hozzon létre egy alkalmazást a start, hogyan szeretné, ha egy bemutató találhat létrehozásához egy egyszerű alkalmazást: a [hozzon létre és telepítsen egy alkalmazást](../../apps/get-started/create-and-deploy-an-application.md) témakör.  

 Ha ismeri az alapvető és részletes referenciaadatait elérhető, beállítások keresése a start [alkalmazásokat](/sccm/apps/deploy-use/create-applications).  

## <a name="software-center-and-the-application-catalog"></a>Szoftverközpont és az alkalmazáskatalógus  
 A korábbi verziókban a Configuration Manager Szoftverközpont telepítéséhez és szoftvertelepítések ütemezése, a távvezérlés beállításainak konfigurálása, és állítsa be az energiagazdálkodás lett megadva. Felhasználók nem kapcsolódni az Alkalmazáskatalógushoz és igényelhetnek szoftvereket, bizonyos beállítások megadása, és a mobileszközökről.  

 Ezek a beállítások továbbra is elérhetők a System Center Configuration Managerben, amíg a Szoftverközpont új verziója mostantól lehetővé teszi az alkalmazások. Nem kell használni az Alkalmazáskatalógust, amelyhez szükséges egy Silverlight-kompatibilis webböngészővel. Az alkalmazáskatalógus weboldal-elérési pontja és az alkalmazáskatalógus webszolgáltatási pontja helyrendszerszerepkör azonban továbbra is szükséges ahhoz, hogy a felhasználók számára elérhető alkalmazások megjelenjenek a Szoftverközpontban.  

 További információkért lásd: [tervezése és az Alkalmazáskezelés konfigurálása](../../apps/plan-design/plan-for-and-configure-application-management.md).  

## <a name="configuration-manager-packages-and-programs"></a>A Configuration Manager-csomagok és programok  
 A Configuration Manager továbbra is támogatja a csomagok és programok, melyekkel a termék korábbi verzióiban. A csomagokat és programokat használó központi telepítések akkor lehetnek megfelelőbbek, mint az alkalmazást használó központi telepítések, ha a következők egyikét telepíti:  

-   Olyan parancsfájlok, amelyek nem telepítenek alkalmazást egy számítógépre, például a számítógép lemezmeghajtójának töredezettségmentesítését végző parancsfájl.  

-   „Egyszeri” használatú parancsfájlok, melyeket nem szükséges folyamatosan figyelni.  

-   Ismétlődő ütemezés szerint futtatott parancsfájlok, melyekhez nem használható globális kiértékelés.

 További információkért lásd: [csomagok és programok](../../apps/deploy-use/packages-and-programs.md).  

