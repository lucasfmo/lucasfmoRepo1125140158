---
title: "Az SMS-szolgáltató tervezése |} Microsoft Docs"
description: "További információk a hogyan az SMS-szolgáltató segítségével felügyelheti a System Center Configuration Manager."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 11ac851696ce52642412ca29e4873679d50cf398
ms.openlocfilehash: 547dc39d5659c7c2e6f1ca670caddc127dbf22c4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-sms-provider-for-system-center-configuration-manager"></a>A System Center Configuration Manager SMS-szolgáltatójának tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Kezelheti a System Center Configuration Manager, a Configuration Manager konzol egy példánya csatlakozó használja a **SMS-szolgáltató**. Alapértelmezés szerint az SMS-szolgáltatót telepíti a helykiszolgálón a központi adminisztrációs hely vagy elsődleges hely telepítésekor. 


##  <a name="BKMK_PlanSMSProv"></a> Az SMS-szolgáltató áttekintése  
 Az SMS-szolgáltató a Windows Management Instrumentation (WMI) szolgáltatót, amelyet hozzárendel **olvasási** és **írási** a Configuration Manager adatbázishoz a helyen a hozzáférést:  

-   Minden központi adminisztrációs helyen és elsődleges helyen legalább egy SMS-szolgáltatóra van szükség. Szükség szerint további szolgáltatók is telepíthetők.  
-   A **SMS rendszergazdák** biztonsági csoport biztosít hozzáférést az SMS-szolgáltatót. A Configuration Manager automatikusan létrehozza ezt a csoportot, a helykiszolgálón és minden számítógépen, amelyre telepíti az SMS-szolgáltató példánya.  

-   A másodlagos helyek nem támogatják az SMS-szolgáltatót.  


Configuration Manager rendszergazda felhasználóhoz használni egy SMS-szolgáltatót az adatbázisban tárolt adatok eléréséhez. Ehhez az szükséges, a rendszergazdák a Configuration Manager konzol, erőforrás-kezelő, eszközöket és egyéni parancsfájlok használhatja. Az SMS-szolgáltató nem kommunikál a Configuration Manager-ügyfelek. A Configuration Manager konzol csatlakozik egy helyhez, amikor a Configuration Manager konzol lekérdezi a WMI keresse meg a használni kívánt SMS-szolgáltató példánya a helykiszolgálón.  

 Az SMS-szolgáltató segít a Configuration Manager biztonság kényszerítése. Csak az információkat a Configuration Manager konzolt futtató rendszergazda felhasználó jogosult megtekinteni adja vissza.  

> [!IMPORTANT]  
>  Ha minden olyan számítógép, egy hely SMS-szolgáltató rendelkezik offline állapotban, a Configuration Manager konzolok, hogy a Helyadatbázis nem tud kapcsolódni.  

 További információkat az SMS-szolgáltató kezeléséről [A System Center Configuration Manager infrastruktúrájának módosítása](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) témakör [Az SMS-szolgáltató kezelése](../../../core/servers/manage/modify-your-infrastructure.md) szakaszában találhat.  

## <a name="prerequisites-to-install-the-sms-provider"></a>Az SMS-szolgáltató telepítésének előfeltételei  

 Az SMS-szolgáltató támogatása:  

-   A számítógép, amely kétirányú megbízhatósági kapcsolatban áll a helykiszolgáló és a Helyadatbázis helyrendszereivel tartományban kell lennie.  

-   A számítógép nem rendelkezhet más helyről származó helyrendszerszerepkörrel.  

-   A számítógép nem rendelkezhet SMS-szolgáltatóval (egyetlen helyről sem).  

-   A számítógépnek olyan operációs rendszert kell futtatnia, amelynek helykiszolgálóhoz való használata támogatott.  

-   A számítógép rendelkeznie kell legalább 650 MB szabad lemezterület a Windows Assessment and Deployment Kit (Windows ADK) SMS-szolgáltatóval telepített összetevőinek támogatásához. További információt a Windows ADK-ról és az SMS-szolgáltatóról jelen témakör [Operációs rendszer központi telepítésére vonatkozó követelmények az SMS-szolgáltatóhoz](#BKMK_WAIKforSMSProv) szakaszában találhat.  

##  <a name="bkmk_location"></a> Az SMS-szolgáltató helyei  
 A hely telepítésekor automatikusan telepítése az első SMS-szolgáltatót a helyhez. Az SMS-szolgáltatóhoz a következő támogatott helyek bármelyikét megadhatja:  

-   A helykiszolgáló számítógép  

-   A helyadatbázist futtató számítógép  

-   Egy kiszolgálói számítógép, amely azonban nem tartalmaz egy SMS-szolgáltatót, vagy a helyrendszer-szerepkör más helyről származó  


Egy helyen telepített egyes SMS-szolgáltatók helyeinek megtekintéséhez jelölje ki a **általános** lapot a hely **tulajdonságok** párbeszédpanel megnyitásához.  

 Minden SMS-szolgáltató támogatja a többszörös kérésekből származó egyidejű kapcsolatokat. Ezeket a kapcsolatokat csak az SMS-szolgáltató számítógépén elérhető kiszolgálókapcsolatok száma, valamint az SMS-szolgáltató számítógépén a kapcsolati kérelmek kiszolgálására elérhető erőforrások mennyisége korlátozza.  

 Hely telepítését követően ismét futtathatja a telepítőt a helykiszolgálón, hogy módosítsa egy meglévő SMS-szolgáltató helyét, vagy további SMS-szolgáltatókat telepítsen a helyre. Egy számítógépre csak egy SMS-szolgáltató telepíthető, és egy számítógép csak egyetlen helyhez rendelkezhet SMS-szolgáltatóval.  

 A következő lista az SMS-szolgáltatók támogatott helyekre történő telepítésének előnyeit és hátrányait foglalja össze.  

 **A Configuration Manager-helykiszolgáló**  

-   **Előnyök:**  

    -   Az SMS-szolgáltató nem használja a helyadatbázis számítógépének rendszererőforrásait.  

    -   Ez a hely jobb teljesítményt nyújthat, mint a nem helykiszolgálóra vagy helyadatbázist futtató számítógépre telepített SMS-szolgáltatók.  

-   **Hátrányok:**  

    -   Az SMS-szolgáltató olyan rendszererőforrásokat és hálózati erőforrásokat használ, amelyeket a helykiszolgálói műveletekhez is fel lehetne használni.  


**A helyadatbázist futtató SQL Server**  

-   **Előnyök:**  

    -   Az SMS-szolgáltató nem használja a helykiszolgáló rendszererőforrásait.  

    -   A három hely közül ez nyújthatja a legjobb teljesítményt, ha elegendő rendszererőforrás áll rendelkezésre.  

-   **Hátrányok:**  

    -   Az SMS-szolgáltató olyan rendszererőforrásokat és hálózati erőforrásokat használ, amelyeket a helyadatbázis-műveletekhez is fel lehetne használni.  

    -   Ha a helyadatbázist tároló SQL Server fürtözött példánya üzemelteti, ezen a helyen nem használhatja.  


**A helykiszolgálótól és a helyadatbázis számítógépétől eltérő számítógép**  

-   **Előnyök:**  

    -   Az SMS-szolgáltató nem használja a helykiszolgáló vagy a helyadatbázist futtató számítógép rendszererőforrásait.  

    -   Ilyen típusú hely esetében további SMS-szolgáltatók is telepíthetők, hogy biztosítható legyen a magas rendelkezésre állás a kapcsolatok számára.  

-   **Hátrányok:**  

    -   Az SMS-szolgáltató teljesítménye csökkenhet miatt a szükséges ahhoz, hogy a helykiszolgáló és a Helyadatbázis számítógépe egyeztessen további hálózati tevékenységet.  

    -   Ez a kiszolgáló mindig elérhetőnek kell lennie a Helyadatbázis számítógépéhez, és az összes számítógépre telepített Configuration Manager-konzol.  

    -   Ez a hely olyan rendszererőforrásokat használhat, amelyeket egyébként más szolgáltatásokhoz lehetne rendelni.  

##  <a name="BKMK_SMSProvLanguages"></a>SMS-szolgáltató nyelvek  
 Az SMS-szolgáltató működése független annak a számítógépnek a megjelenítési nyelvétől, amelyre telepítve van.  

 Ha egy rendszergazda felhasználó vagy a Configuration Manager folyamat kérelmek data az SMS-szolgáltató használatával, az SMS-szolgáltató próbálja elküldeni a formátuma, amely megfelel a kérést küldő számítógép operációs rendszerének nyelvével.

A egyezik megkísérli módja némileg közvetett. Az SMS-szolgáltató nem fordítja le az adatokat egyik nyelvről a másikra. Ehelyett adatok visszaküldött a Configuration Manager konzolon, ha az adatok megjelenítési nyelvét a forrástól függ az objektumforrás és a tároló típusa szerinti.  

 Ha egy objektum adatai az adatbázisban vannak tárolva, az elérhető nyelvek a következőktől függenek:  

-   A Configuration Manager által létrehozott objektumok több nyelv támogatása használatával tárolja az adatbázisban. Az objektum tárolása azoknak a nyelveknek a használatával történik, amelyek azon a helyen vannak beállítva, ahol a telepítő futtatásakor az objektum létrejön. Ha az adott nyelv elérhető az objektumhoz ezeket az objektumokat a Configuration Manager konzolon a kérést küldő számítógép megjelenítési nyelvén jelennek meg. Ha az objektum nem jeleníthető meg a kérést küldő számítógép megjelenítési nyelvén, akkor az alapértelmezett nyelven, azaz angolul jelenik meg.  

-   A rendszergazda felhasználó által létrehozott objektumok az objektum létrehozásához használt nyelven tárolódnak az adatbázisban. Ezeket az objektumokat a Configuration Manager konzol ugyanezen a nyelven jelennek meg. Nem fordíthatók le az SMS-szolgáltatót, és nem tartozik hozzájuk többnyelvű támogatás.  

##  <a name="BKMK_MultiSMSProv"></a> Több SMS-szolgáltató használata  
 A hely telepítését követően további SMS-szolgáltatók is telepíthetők a helyhez. További SMS-szolgáltatók telepítéséhez futtassa a Configuration Manager telepítőjét a helykiszolgálón. Akkor lehet érdemes további SMS-szolgáltatókat telepíteni, ha a következők bármelyike igaz:  

-   Sok rendszergazda felhasználók a Configuration Manager konzol futtatásához, és csatlakozik egy helyhez egy időben lesz.  

-   A Configuration Manager SDK vagy más olyan termékek, amelyek lehet, hogy a gyakori hívásokat az SMS-szolgáltatót fogja használni.  

-   Magas rendelkezésre állást szeretne biztosítani az SMS-szolgáltatóhoz.  


Ha egy helyen több SMS-szolgáltató telepített, és a kapcsolódási kérelem, a hely véletlenszerűen rendeli minden új kapcsolódási kérelemhez egy telepített SMS-szolgáltatót. Egy adott kapcsolat-munkamenethez nem adható meg az általa használt SMS-szolgáltató helye.  

> [!NOTE]  
>  Vegye figyelembe a előnyeit és hátrányait minden egyes SMS-szolgáltató helyét. Ezeket a szempontokat, hogy nem szabályozhatja, hogy melyik SMS-szolgáltató információkkal szolgál minden új kapcsolódási egyensúlyára.  

Például ha először a Configuration Manager konzol csatlakozik egy helyhez, a kapcsolat lekérdezi WMI a helykiszolgálón az SMS-szolgáltató a konzol egyik példányát azonosító. Ez az SMS-szolgáltató példányát marad használatban a Configuration Manager konzol mindaddig, amíg a Configuration Manager konzol munkamenet azért ér véget. Ha a munkamenet azért ér véget, mert az SMS-szolgáltató számítógépe elérhetetlenné válik a a hálózaton, a Configuration Manager-konzol újrakapcsolódásakor, a hely egyszerűen ismétlődik azonosítására kapcsolódni az SMS-szolgáltató példánya. Előfordulhat az is, hogy ismét ugyanazt a nem elérhető SMS-szolgáltatót rendeli hozzá. Ilyen esetben megpróbálhat csatlakozzon újra a Configuration Manager konzolon, amíg elérhető, SMS-szolgáltatót futtató számítógép hozzá van rendelve.  

##  <a name="BKMK_AboutSMSAdmins"></a> Az SMS rendszergazdák csoport  
 Az SMS rendszergazdák csoport használatával hozzáférést biztosíthat a rendszergazda felhasználók számára az SMS-szolgáltatóhoz. Ez a csoport a hely telepítésekor automatikusan létrejön a helykiszolgálón, valamint minden olyan számítógépen, amelyre SMS-szolgáltatót telepítenek. További információ az SMS rendszergazdák csoport a következő:  

-   Ha a számítógép tagkiszolgáló, az SMS rendszergazdák csoport helyi csoportként jön létre.  

-   Ha a számítógép tartományvezérlő, az SMS rendszergazdák csoport tartományi helyi csoportként jön létre.  

-   Ha egy számítógépről eltávolítják az SMS-szolgáltatót, az SMS rendszergazdák csoport nem lesz eltávolítva róla.  


Ahhoz, hogy egy felhasználó sikeresen kapcsolódhasson egy adott SMS-szolgáltatóhoz, a felhasználói fiókjának az SMS rendszergazdák csoportban kell lennie. A Configuration Manager-konzolon konfigurált minden egyes felügyeleti felhasználó automatikusan kerül, az SMS rendszergazdák csoport minden egyes helykiszolgálóján és minden SMS-szolgáltató számítógép a hierarchiában. Ha töröl egy rendszergazda felhasználó a Configuration Manager konzolról, hogy a felhasználó törlődik az SMS rendszergazdák csoport minden egyes helykiszolgálóján és minden SMS-szolgáltató számítógép a hierarchiában.  

Miután a felhasználó sikeresen kapcsolódott az SMS-szolgáltatóhoz, szerepkör alapú felügyelet meghatározza, hogy milyen Configuration Manager erőforrásokat, hogy a felhasználó érheti el és kezelheti.  

Megtekintheti és konfigurálhatja az SMS rendszergazdák csoport jogosultságai és engedélyei a WMI-vezérlő MMC beépülő modul használatával. Alapértelmezés szerint a **Mindenki** csoport a **Metódusok végrehajtása**, a **Szolgáltató írása**és a **Fiók engedélyezése** jogosultságokkal rendelkezik. Miután egy felhasználó kapcsolódott az SMS-szolgáltatóhoz, kap hozzáférést szerepköralapú rendszergazdai biztonsági jogosultságai alapján a Configuration Manager-konzolon meghatározott, a helyadatbázisban lévő adatokhoz. Az SMS rendszergazdák csoport explicit módon kapnak **fiók engedélyezése** és **távoli engedélyezés** engedélyeit a **gyökér\sms** névtér.  

> [!NOTE]  
>  Minden egyes rendszergazda felhasználó, aki használja a távoli Configuration Manager konzol a helykiszolgáló számítógépen és az SMS-szolgáltató számítógép a Távoli aktiválás DCOM engedélyekkel kell rendelkeznie. Bár ezek a jogosultságok bármely felhasználónak vagy csoportnak megadhatók, célszerű a hozzáférést az SMS rendszergazdák csoport egyszerűbb felügyelet érdekében. További információt [A System Center Configuration Manager infrastruktúrájának módosítása](../../../core/servers/manage/modify-your-infrastructure.md) témakör [DCOM-engedélyek konfigurálása a távoli Configuration Manager konzolhoz](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) című szakaszában talál.  


##  <a name="BKMK_SMSProvNamespace"></a>Információ az SMS-szolgáltató névtere  
Az SMS-szolgáltató felépítését a WMI-séma határozza meg. Séma névterei az SMS-szolgáltató sémáján belül a Configuration Manager adatainak helyét írják le. A következő táblázatban az SMS-szolgáltató által használt néhány gyakori névtér látható.  

|Névtér|Leírás|  
|---------------|-----------------|  
|Root\SMS\site_*&lt;Helykód\>*|Az SMS-szolgáltató, a Configuration Manager konzol, erőforrás-kezelő, a Configuration Manager eszközök és parancsfájlok által nagymértékben használt.|  
|Root\SMS\SMS_ProviderLocation|Egy hely SMS Provider-számítógépei helyét.|  
|Root\CIMv2|A WMI-névtér információ hardver- és szoftverleltár során a leltárba helyét.|  
|Root\CCM|A Configuration Manager ügyfél-konfigurációs házirendjei és ügyféladatai.|  
|root\CIMv2\SMS|Hardverleltár-jelentési osztályai, a leltár ügyfélügynöke által összegyűjtött helyét. Ezek a beállítások vannak ügyfelek állítják össze számítógép-házirend értékelésekor, és a számítógép ügyfélbeállításai alapulnak.|  

##  <a name="BKMK_WAIKforSMSProv"></a>Operációs rendszer központi telepítésére vonatkozó követelmények az SMS-szolgáltató  
A számítógépen, ahová az SMS-szolgáltató példányát telepíti, amely a Configuration Manager verziója használata szükséges a Windows ADK szükséges verziójának kell rendelkeznie.  

 -   Például a Configuration Manager 1511-es verziója szükséges a Windows 10 RTM (10.0.10240) a Windows ADK-verziót.  

 -   Ez a követelmény kapcsolatos további információkért lásd: [operációs rendszer központi telepítésének infrastrukturális követelményei](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

Operációs rendszer központi telepítésének kezelésekor a Windows ADK lehetővé teszi, hogy az SMS-szolgáltató elvégezzen különböző feladatokat, például:  

-   WIM fájlok részleteinek megtekintése.  

-   Illesztőprogram-fájlok hozzáadása meglévő rendszerindító lemezképekhez.  

-   Hozzon létre rendszerindító. ISO-fájl.  


A Windows ADK telepítése legfeljebb 650 MB szabad lemezterületet igényel minden olyan számítógépen, amelyikre az SMS-szolgáltató telepítve lesz. Ez méretű lemezterület azért szükséges a Configuration Manager telepítéséhez a Windows PE rendszerindító lemezképeit.  

