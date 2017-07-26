---
title: "App-V virtuális alkalmazások központi telepítése |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozása és központi telepítésekor a virtuális alkalmazások."
ms.custom: na
ms.date: 02/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c73373e6f2f28f8ddc197695e4b4e3488c9c1f5b
ms.openlocfilehash: 0808edbb9a0433dd658d37e8d005c89a4778735c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-app-v-virtual-applications-with-system-center-configuration-manager"></a>App-V virtuális alkalmazások a System Center Configuration Manager telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha a Configuration Manager használatával kezeli a virtuális alkalmazásokat, a következő előnyöket:  

-   Egyetlen felügyeleti infrastruktúra  

-   Méretezhetőség, központi telepítési és tartalomterjesztési funkciók, például gyűjtemények és felhasználó-eszköz kapcsolat  

-   Speciális alkalmazásfelügyeleti szolgáltatásainak  

-   Operációs rendszer központi telepítéséhez, a szoftver- és Hardverleltár, a szoftverhasználat-mérés és a virtuális alkalmazások támogatását az eszközintelligencia-katalógus  

Létrehozásáról és sorrendvezérléséről alkalmazások a Microsoft Application Virtualization (App-V) használatával kapcsolatos további információkért lásd: [Application Virtualization](https://technet.microsoft.com/library/cc843848.aspx) a TechNet könyvtárban.  

Az egyéb System Center Configuration Manager követelményei és eljárásai alkalmazások létrehozására vonatkozó, mellett az alábbiakat is figyelembe kell végrehajtania, amikor hozzon létre és telepíthet központilag virtuális alkalmazásokat:

-   Virtuális alkalmazásokat telepíthessen a Configuration Manager-ügyfél és az App-V-ügyfelet a számítógépekre telepített kell rendelkeznie. Az ügyféleszközök lehetnek asztali és hordozható számítógépek, valamint a virtuális asztali infrastruktúrát (VDI) használó ügyfelek. A Configuration Manager és az App-V-ügyfél szoftver együttműködve kézbesíti, keresse meg és indítja el a virtuális alkalmazáscsomagokat. A Configuration Manager-ügyfél felügyeli a virtuális alkalmazáscsomagok kézbesítését az App-V-ügyfél. Az App-V-ügyfél futtatja a virtuális alkalmazást az ügyfélen.  

-   Virtuális alkalmazás központi telepítéséhez először létre kell hozni a virtuális alkalmazást az App-V Application Virtualization Sequencer használatával. A Sequencer figyeli az alkalmazás telepítési és beállítási folyamatát, valamint megjegyzi az alkalmazás virtuális környezetben való futtatásához szükséges adatokat. A sequencer segítségével állítsa be, amely fájlok és konfigurációk érvényesek az összes felhasználóra, és amely konfigurációk felhasználók testre.  

-   Ha egy alkalmazás sorrendvezérlése, mentenie kell a csomagot olyan helyre, amely a Configuration Manager hozzáférhet. Ezután olyan alkalmazás-központitelepítést hozhat létre, amely tartalmazza ezt a virtuális alkalmazást.  

-   A Configuration Manager nem támogatja az App-v megosztott csak olvasható gyorsítótárának funkciójának használatát.  

-   A Configuration Manager támogatja a megosztott tartalmat tároló szolgáltatást az App-V 5.  

-   Amikor létrehoz egy virtuális alkalmazás központi telepítési típust, a Configuration Manager az Alkalmazásjegyzék-fájl tartalmának használatával hozza létre a központi telepítési típus. Ez az XML-fájl, amely rendelkezik a virtuális alkalmazással kapcsolatos információkat. Emellett a Configuration Manager létrehoz a központi telepítési típus az App-V .osd fájlja, amelyen tájékoztatást olvashat a támogatott operációs rendszerek a virtuális alkalmazás tartalma alapján követelményeit.  

-   A Configuration Manager a virtuális alkalmazások központi telepítéséhez ügyfélszámítógépek minimális rendelkeznie kell az App-V 4.6 SP1 vagy az ügyfél telepítve van egy újabb verziója.  

-   Virtuális alkalmazások sikeres központi telepítése érdekében előbb frissíteni kell az App-V-ügyfél a Tudásbázis-cikkben leírt gyorsjavítást [2645225 sz. cikkében](https://support.microsoft.com/kb/2645225).  

-   Amikor App-V 5.0 kapcsolatcsoportokat használ, a központilag telepített virtuális alkalmazások megoszthatja a ugyanazt a fájlrendszert és beállításjegyzéket az ügyfélszámítógépeken. A szokásos virtuális alkalmazásoktól eltérően ezek a virtuális alkalmazások így egymás között is megoszthatják az adatokat. A kapcsolatcsoportok emellett megőrzik a bennük szereplő alkalmazások felhasználói beállításait is. App-V virtuális környezetei a Configuration Managerben használt kapcsolati csoportokat az ügyfélszámítógépeken. A virtuális környezetek létrehozása vagy módosítása az ügyfélgépeken az alkalmazás telepítésekor, illetve a telepített alkalmazásoknak az ügyfelek általi következő kiértékelésekor történik. Ezeket az alkalmazásokat fontossági sorrendbe állíthatja, hogy amikor több alkalmazás próbálkozik a fájlrendszer vagy egy beállításazonosító módosításával, a magasabb prioritásúnak legyen elsőbbsége. További információkért lásd: [létrehozása az App-V virtuális környezetek](../../apps/deploy-use/create-app-v-virtual-environments.md).  

##  <a name="supported-app-v-versions"></a>App-V támogatott verziói  
 A Configuration Manager az App-v következő verzióit támogatja.  

-   **App-V 4.6**: A virtuális alkalmazások a Configuration Manager használatához az ügyfélszámítógépeken kell az App-V 4.6 SP1, App-V 4.6 SP2 vagy az App-V 4.6 SP3 ügyfelet.  

     Virtuális alkalmazások sikeres központi telepítése érdekében előbb is frissíteni kell az App-V 4.6 SP1 ügyfelet a Tudásbázis-cikkben leírt gyorsjavítást [2645225 sz. cikkében](http://go.microsoft.com/fwlink/p/?LinkId=237322).  

-   **Az App-V 5, App-V 5.0 SP1, App-V 5.0 SP2, App-V 5.0 SP3 és App-V 5.1**: Az App-V 5.0 SP2 esetén telepítenie kell [5. gyorsjavítási csomagot](https://support.microsoft.com/en-us/kb/2963211) , vagy használja az App-V 5.0 SP3.  
-   **App-V 5.2**: Ez be van építve a Windows 10 Enterprise (évforduló frissítése és újabb).

App-V a Windows 10-es kapcsolatos további információkért lásd a következő témaköröket:

- [App-V újdonságai](https://technet.microsoft.com/itpro/windows/manage/appv-about-appv)
- [Ismerkedés az App-V a Windows 10](https://technet.microsoft.com/itpro/windows/manage/appv-getting-started)
- [Rendszerre történő App-V a Windows 10-re meglévő telepítés](https://technet.microsoft.com/itpro/windows/manage/appv-upgrading-to-app-v-for-windows-10-from-an-existing-installation)

##  <a name="steps-to-manage-app-v-virtual-applications"></a>App-V virtuális alkalmazások felügyeletének lépései  
 Az App-V virtuális alkalmazások kezeléséhez kövesse az alábbi lépéseket:  

1.   **Feladatütemezési**: Alkalmazás-előkészítés az a folyamat egy alkalmazás átalakítása virtuális alkalmazást az App-V sequencer használatával.

2.   **Hozzon létre**: A központi telepítési típus varázsló segítségével importálja a szekvenciális alkalmazást a Configuration Manager központi telepítési típust, amelyet ezután felvehet egy alkalmazásba történő. Ezenkívül létrehozhat virtuális környezeteket is, amelyekben több virtuális alkalmazás közösen használhatja a beállításokat.

3.   **Terjesztése**: Terjesztés az a folyamat, amellyel App-V alkalmazások elérhetővé tehetők a Configuration Manager terjesztési pontokon.

4.   **Telepítése**: Központi telepítés elérhetővé az alkalmazások az ügyfélszámítógépeken során a rendszer. Ennek meghívása az adatfolyam-az App-V teljes infrastruktúrájában.  

##  <a name="configuration-manager-virtual-application-delivery-methods"></a>A Configuration Manager virtuális alkalmazások kézbesítéséhez használt módszerek  
A Configuration Manager két módszert támogatja az ügyfelek számára a virtuális alkalmazások kézbesítésre: adatfolyamként történő kézbesítés és helyi kézbesítés (Letöltés és végrehajtás).

Amikor eldönti, hogy melyik kézbesítési módszert használja, hasonlítsa össze a csökkentett szabad területére vonatkozó követelmény adatfolyamként történő továbbítását elleni garantált elérhetőségét a helyi kézbesítés App-V alkalmazások. A helyi kézbesítés nagyobb lemezterület-igénye ellenére is megfelelőbb választás lehet az adatfolyamként történő továbbítás helyett, ha fontos, hogy a felhasználók bármikor, bárhonnan elérhessék az alkalmazást.  

###  <a name="streaming-delivery"></a>Adatfolyamként történő kézbesítéshez
A Configuration Manager használatával kezelheti az App-V-ügyfél, támogatja a adatfolyamként való küldése a terjesztési pontokról HTTP vagy HTTPS használatával a virtuális alkalmazások. HTTP vagy HTTPS keresztüli adatfolyamküldés alapértelmezés szerint engedélyezve van, és a terjesztésipont-Tulajdonságok párbeszédpaneljén be van állítva. Amikor az ügyfélszámítógépek számára virtuális alkalmazást telepít központilag, és egy felhasználó futtatja a virtuális alkalmazást, a Configuration Manager-ügyfél kapcsolódik egy felügyeleti ponthoz, hogy megállapítsa, melyik terjesztési pontot használni. Ezt követően az alkalmazás a terjesztési pontról továbbítja adatfolyamként.  

Olvassa el a táblázat segítségével eldöntheti, hogy adatfolyamként történő küldés esetén a megfelelő kézbesítési módszert meg:

|Előnyök|Hátrányok|  
|----------------|-------------------|  
|Ez a módszer szabványos hálózati protokollok használatával küldi adatfolyamként a csomag tartalmát a terjesztési pontokról.<br /><br /> A virtuális alkalmazások parancsikonjai kapcsolatot hoznak létre a terjesztési ponttal, hogy a virtuális alkalmazás kézbesítése igény esetén megtörténhessen.<br /><br /> Ez a módszer jól működik az olyan ügyfelek esetében, amelyek nagy sávszélességű kapcsolattal csatlakoznak a terjesztési pontokhoz.<br /><br /> A vállalaton belül terjesztett frissített virtuális alkalmazások akkor válnak elérhetővé, amikor az ügyfelek megkapják azt a házirendet, amely közli, hogy az aktuális verzió felül lett írva, és az ügyfelek ekkor csak az előző verzió óta bekövetkezett változásokat töltik le.<br /><br /> A hozzáférési ponton definiálható hozzáférési engedélyekkel akadályozható meg, hogy a felhasználók nem hitelesített alkalmazásokhoz vagy csomagokhoz férjenek hozzá.|A virtuális alkalmazások adatfolyamként történő küldése csak akkor kezdődik el, amikor a felhasználó első alkalommal futtatja az alkalmazást. Ebben a helyzetben előfordulhat, hogy a felhasználók megkaphatják a virtuális alkalmazások parancsikonjait, és a virtuális alkalmazás első futtatása előtt lecsatlakoznak a hálózatról. Ha a felhasználó megpróbálja futtatni az virtuális alkalmazást, amikor az ügyfél offline állapotban, a felhasználó hibaüzenetet, és nem tudja futtatni az virtuális alkalmazást, mert a Configuration Manager terjesztési pont nem érhető el az alkalmazás adatfolyamként történő. Az alkalmazás nem lesz elérhető, amíg a felhasználó nem csatlakozik újra a hálózathoz, és nem indítja el az alkalmazást.<br /><br /> Ha el szeretné kerülni ezt, használhatja a helyi kézbesítési módszert a virtuális alkalmazások kézbesítéséhez az ügyfelekre, vagy engedélyezheti az internetes ügyfélfelügyeletet az adatfolyamként történő kézbesítéshez.|  

###  <a name="local-delivery-download-and-execute"></a>Helyi kézbesítés (Letöltés és végrehajtás)  
Ha a helyi kézbesítési módszert használja, a Configuration Manager-ügyfél először letölti a virtuális alkalmazás teljes csomagját a Configuration Manager ügyfél gyorsítótárába. A Configuration Manager majd arra utasítja az App-V-ügyfél a Configuration Manager-gyorsítótára az App-V gyorsítótárba az alkalmazás adatfolyamként történő küldéséhez. Ha az ügyfélszámítógépek számára virtuális alkalmazást telepít központilag, és annak tartalma nincs az App-V gyorsítótárában, az App-V-ügyfél adatfolyamként elküldi az alkalmazás tartalmát a Configuration Manager-ügyfél gyorsítótára az App-V gyorsítótárába, és majd futtatja az alkalmazást. Az alkalmazás sikeres futtatása után a Configuration Manager-ügyfél minden régebbi verzióját a csomag a következő törlési ciklusban, vagy a Configuration Manager-ügyfél gyorsítótárában megőrzésére állíthatja be.  

Olvassa el a táblázat segítségével eldöntheti, hogy a helyi kézbesítés-e meg a megfelelő kézbesítési módszert:   

|Előnyök|Hátrányok|  
|----------------|-------------------|  
|A terjesztési pont szabványos funkciójával tölthető le a csomag a BITS (Background Intelligent Transfer Service) szolgáltatás használatával.<br /><br /> Virtuális alkalmazáscsomag tartalmának helyileg kézbesítve lenne az ügyfél. Ez azt jelenti, hogy felhasználók futtathassa őket, amikor a számítógép nem kapcsolódik a hálózathoz.<br /><br /> Ez a módszer lassú vagy nem megbízható hálózati kapcsolatokhoz, illetve olyan számítógépekhez alkalmas, amelyek csak esetenként csatlakoznak a hálózathoz.<br /><br /> A Configuration Manager távoli különbözeti tömörítés (RDC) használatával küldi el az ügyfeleknek csak azokat a bájtokat a fájlból, amelyek megváltoztak a virtuális alkalmazáscsomag frissítésekor. A Configuration Manager-ügyfél Különbözeti tömörítés funkció használatával létrehozza a csomag aktuális verziója alapján virtuálisalkalmazás-csomagok és az ügyfélnek küldött módosítások új verzióját.<br /><br /> Ez a módszer lehetővé teszi az alkalmazás rugalmas használatát a mobilfelhasználóknak és a nem csatlakozó felhasználóknak. Az választhatják a csomag megőrzését a Configuration Manager gyorsítótárában kézbesítési után, ha a virtuális alkalmazás lett telepítve, a telepítés művelet a rendszergazdák választhatják. A csomagot a Configuration Manager-ügyfél gyorsítótárában tárolt adatfolyamforrásként egy helyi, megbízható az App-V-ügyfél való lekérésére a csomagot a saját gyorsítótárába.|Szabad lemezterület, akár a virtuális alkalmazáscsomag méretének kétszeresével egyenlő az ügyfélen szükséges, amikor a virtuális alkalmazás a Configuration Manager-gyorsítótárban.|  

###  <a name="deployment-from-an-image"></a>A lemezkép központi telepítés

A virtuális alkalmazásokat ezenkívül telepítheti egy számítógépre, majd az adott számítógépről készített lemezképet használhatja a többi számítógépen végrehajtott központi telepítéshez. De ha a virtuális alkalmazáscsomag más helyen lett létrehozva, a bináris változásreplikálás nem használható az alkalmazás frissítéseinek letöltéséhez. Ez a lehetőség virtuális asztali infrastruktúra esetén lehet hasznos, amikor azt szeretné, hogy az alkalmazások azonnal elérhetők legyenek, és ne a felhasználó bejelentkezése után legyenek letöltve.    

##  <a name="migrating-from-an-app-v-infrastructure-to-a-configuration-manager-and-app-v-infrastructure"></a>Az App-V infrastruktúra telepít át egy Configuration Manager és az App-V infrastruktúra  
A következő táblázat segítségével tervezheti meg a virtuális alkalmazások kezelése a Configuration Manager meglévő App-V infrastruktúra áttelepítését.  

|Lépés|További információ|  
|----------|----------------------|  
|Vizsgálja meg az aktuális virtuális alkalmazásait, és válassza ki azokat, amelyet szeretne áttelepíteni a Configuration Manager-infrastruktúrában.|Nem áll rendelkezésre további információ.|  
|Határozza meg azokat a felhasználókat és eszközöket, akiknek és amelyekre a virtuális alkalmazásokat telepíteni fogja.|A felhasználók és eszközök csoportba foglalásához, amelyhez a virtuális alkalmazásokat telepíteni szeretné a Configuration Manager-gyűjtemények létrehozása. Lásd: [gyűjteményeinek bemutatása](/sccm/core/clients/manage/collections/introduction-to-collections).|  
|Telepítse át az App-V 5 kapcsolati csoportokat a Configuration Manager virtuális környezeteibe.|Tekintse meg a [át App-V 5 kapcsolati csoportokat a Configuration Manager virtuális környezeteibe](/sccm/apps/get-started/deploying-app-v-virtual-applications#migrate-app-v-5-connection-groups-to-configuration-manager-virtual-environments) szakaszában talál.|  
|Ellenőrizze, hogy a virtuális alkalmazások valamelyike nem létezik-e teljes alkalmazásként a Configuration Manager-infrastruktúrában.|Az egyszerűbb felügyelet érdekében a virtuális alkalmazást új központi telepítési típusként veheti fel a meglévő teljes alkalmazásba. Lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|Hozzon létre alkalmazásokat a meglévő App-V-csomagok lecseréléséhez.|Lásd: [Alkalmazáskezelés bemutatása](/sccm/apps/understand/introduction-to-application-management) és [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|A Configuration Manager veszi át a virtuális alkalmazások felügyeletét az ügyfelet a virtuális alkalmazások első központi telepítése után. Ezt követően a Configuration Manager összes App-V alkalmazás a számítógépen kell kezelni.|Nem áll rendelkezésre további információ.|  
|Terjessze a tartalmat a megfelelő terjesztési pontokra az alkalmazások helyi kézbesítésének lehetővé tételéhez.|Lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|A Configuration Manager-ügyfelek számára az alkalmazás telepítéséhez.<br /><br /> Ha az App-V alkalmazás a sequencer eszköz, amely nem készít XML-jegyzékfájlt korábbi verziójával lett létrehozva, nyissa meg, majd mentse a fájl létrehozásához a sequencer újabb verziója. Ezt a fájlt a virtuális alkalmazások a Configuration Manager telepítéséhez szükséges.<br /><br /> App-V támogatja a virtuálisalkalmazás-csomagok, a SoftGrid 4.1 SP1 vagy 4.2 verziójával a sequencer használatával létrehozott.<br /><br /> Ha az alkalmazások korábban helyben voltak telepítve, a virtuális verziójuk központi telepítése előtt el kell távolítania azokat.|Lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).|  
|A System Center Configuration Manager többé nem támogatja a csomagok és programok, virtuális alkalmazásokat tartalmazó használatát. Áttelepítésekor a Configuration Manager 2007 System Center Configuration Manager, a Configuration Manager alkalmazásokra alakítja át ezeket a csomagokat.<br /><br /> A Configuration Manager 2007 hirdetményei a következő központi telepítési típusokra lesznek konvertálva:<br /><br /> -App-V-csomagok áttelepítése hirdetmény nélkül:  Egy központi telepítési típus, amely az alapértelmezett központi telepítési típus beállításait használja.<br /><br /> -App-V-csomagok áttelepítése egy hirdetménnyel: Egy központi telepítési típus, amely megegyező beállításokat használja a <br />                A Configuration Manager 2007 hirdetménye.<br /><br /> -App-V-csomagok áttelepítése több hirdetménnyel: A központi telepítési típus minden <br />                A Configuration Manager 2007 hirdetményéhez, amely az adott hirdetmény beállításait használja.|Lásd: [tervezése a Configuration Manager-objektumok a System Center Configuration Manager az áttelepítés](../../core/migration/planning-for-the-migration-of-objects.md).|  

##  <a name="migrating-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>Áttelepítése az App-V 5 kapcsolati csoportokat a Configuration Manager virtuális környezeteibe  
App-V virtuális környezetei a Configuration Manager lehetővé teszi, hogy ugyanazt a fájlrendszert és beállításjegyzéket az ügyfélszámítógépeken telepített virtuális alkalmazások. Ez azt jelenti, hogy a szokásos virtuális alkalmazásoktól eltérően ezek a virtuális alkalmazások egymás között megoszthatják az adatokat. A virtuális környezetek létrehozása vagy módosítása az ügyfélgépeken az alkalmazás telepítésekor, illetve a telepített alkalmazásoknak az ügyfelek általi következő kiértékelésekor történik. Virtuális környezetek az önálló App-V 5 kapcsolati csoportjaihoz hasonlítanak.  

Amikor kapcsolati csoportokat telepít át az önálló App-V 5 Configuration Manager virtuális környezeteibe, gondoskodnia kell arról, hogy a Configuration Manager megfelelően kezeli-e az ügyfélszámítógépeken már meglévő kapcsolati csoportokat, és hogy adott kapcsolati csoportokban a felhasználó környezete megmaradjon.  

Konvertálása App-V 5 kapcsolati csoportokat a Configuration Manager virtuális környezeteibe:  

1.  Hozzon létre Configuration Manager-alkalmazásokat minden olyan alkalmazásnál, amely létezett az App-V.  

2.  Telepítse az alkalmazásokat a felhasználóknak vagy az eszközökre a **Szükséges**központi telepítési céllal. Központi telepítésére a felhasználók, akik az App-V környezetben használták az alkalmazást telepíteni kell. Számítógépek központitelepítése ugyanazokra a számítógépekre, amelyek az App-V környezetben tartalmazták az alkalmazást kell telepíteni.  

3.  A telepítés befejezése után hozzon létre virtuális környezeteket, melyek megfelelnek az egyedülálló App-V közzétett. A virtuális környezet az azonos csomagokat (pontosabban az App-V 5 központi telepítéstípusokat) kell rendelkeznie ugyanabban a sorrendben.  

App-V virtuális környezet létrehozásával kapcsolatos további információkért lásd: [App-V virtuális környezetek létrehozása](../../apps/deploy-use/create-app-v-virtual-environments.md).  

Azt is megteheti, akkor összes kapcsolatcsoportot törli az App-V-ügyfél alkalmazások a Configuration Managerrel való központi telepítése előtt. De a beállításait, a felhasználók az App-V kapcsolatcsoportokban lementettek előfordulhat, hogy mentette el fog veszni.  

##  <a name="dynamic-suite-composition-in-app-v-46"></a>Dinamikus csomag létrehozása az App-V 4.6.  
Dinamikus csomag létrehozása szolgáltatással olyan szolgáltatás, amely lehetővé teszi, hogy egy másik virtuális alkalmazási csomagot a függőség rendelkezőként egy virtuálisalkalmazás-csomag megadása. Az alkalmazás futtatásakor az elsődleges csomag az App-V-ügyfélen, míg a függő csomag az alkalmazással megegyező virtuális környezetben kap helyet.  

Használja ezt a szolgáltatást a Configuration Manager meg mindkét csomagot kell telepítése és az App-V-ügyfél regisztrálva. Győződjön meg arról, hogy a függő csomag tartalmát egy helyi gazdagépen az ügyfélszámítógépen, állítsa be az alkalmazás központi telepítését helyi kézbesítésre (Letöltés és végrehajtás).  

Ha bővebb információkat szeretne az App-V Dinamikus csomag létrehozása szolgáltatásról, tanulmányozza az App-V dokumentációját.  

##  <a name="converting-app-v-46-applications-to-app-v-5-applications"></a>App-V 5 alkalmazásokat az App-V 4.6 verziójú alkalmazások konvertálása  
Az alkalmazáscsomag formátuma az App-V 4.6 és az App-V 5 között megváltozott. Az App-V 4.6-tal előkészített alkalmazások többé nem támogatottak. De az App-V 5 csomagátalakító eszközével átalakíthatja az alkalmazásokat használó. További információt [az App-V 5 dokumentációjában](http://technet.microsoft.com/library/jj713472.aspx)talál.  

Az App-V 4.6 alkalmazásokat az alábbi lépések végrehajtásával alakíthatja át App-V 5 alkalmazásokká:  

1.  Átalakítás szülővé és resequence az App-V 4.6 csomagokat App-V 5 formátumba.  

2.  Központilag telepítse az App-V 5 ügyfelet a hierarchiában található számítógépekre.  

3.  Hozzon létre új alkalmazásokat, melyek App-V 5 központi telepítéstípussal rendelkeznek, és helyettesítési szabályok létrehozásával helyettesítse az App-V 4.6 alkalmazásokat.  

4.  Hozza létre a szükséges virtuális környezeteket.  

5.  Központilag telepítse az új App-V 5 alkalmazásokat a számítógépekre.  

##  <a name="user-and-deployment-configuration-files"></a>Felhasználó és a telepítési konfigurációs fájlok  
Felhasználó és a központi telepítés konfigurációs fájljaira rendelkezik az alkalmazás viselkedését vezérlő beállításokat. Ezek a fájlok segítségével beállításainak módosítása nélkül az alkalmazás resequencing.  

Egy átlagos App-V 5 alkalmazás általában a következő fájlokat tartalmazza:  

-   Egy alkalmazás-alkalmazáscsomag (.appv) fájl  

-   A felhasználó-konfigurációs fájl  

-   Telepítési konfigurációs fájllal  

A felhasználó-konfigurációs fájl csak a bejelentkezett felhasználó vonatkozó beállításokat tartalmaz. Például a konfigurációs fájlok szerkesztésével módosítani szeretné a felhasználók számára központilag telepített alkalmazás-parancsikonokkal kapcsolatos információkat. Configuration Manager-alkalmazás több központi telepítési típusok is létrehozhat. Minden központi telepítési típus egy másik felhasználó-konfigurációs fájl tartalmazhat, és követelményszabályok megadásával győződjön meg arról, hogy van telepítve a megfelelő felhasználóhoz.  

A telepítési konfigurációs fájl beállításait, amelyek érvényesek a számítógépen, például a beállításjegyzék-beállítások rendelkezik. A fájl is a felhasználói beállítások, amelyek minden felhasználójára érvényesek.  

Ha szeretné telepíteni az App-V 5 virtuális alkalmazásokat a Configuration Managerrel, mindhárom fájlt szerepelnie kell abban a mappában, az App-V 5 KözpontiTelepítés-típus létrehozásakor. Ha több fájl a mappában, a Configuration Manager legújabb fog használni.  

További információt [az App-V 5 dokumentációjában](http://technet.microsoft.com/library/jj713466.aspx)talál.  

##  <a name="app-v-local-interaction"></a>Az App-V helyi kezelése  
Bizonyos alkalmazástelepítési esetekben az alkalmazások telepítése helyileg történik az ügyfélszámítógépeken, és más alkalmazások virtuális alkalmazásokként ugyanarra az ügyfélszámítógépre vannak telepítve. Alapértelmezés szerint a helyileg telepített alkalmazások nem láthatják a virtualizált alkalmazásokat, és nem kommunikálhatnak azokkal közvetlenül. Ez az App-V szolgáltatásban olyan alkalmazáselszigetelés várt működése. Helyi kezelés egy olyan szolgáltatás, amelyet engedélyezhet az egyes alkalmazások megtekintéséhez és kommunikálni a virtualizált alkalmazások ügyfélszámítógépen futtassa helyileg telepített alkalmazások App-V-ügyfél. Configuration Manager és az App-V teljes mértékben támogatja a helyi kezelést.  

További információt az App-V helyi kezelés szolgáltatásáról tanulmányozza az App-V dokumentációját.  

##  <a name="app-v-5-shared-content-store"></a>Az App-V 5 megosztott Tartalomtárolója  
A Configuration Manager támogatja az App-V 5 megosztott tartalomtárolóját. További tudnivalók: [Az App-V App-V 5.0 megosztott tartalomtárolójának (SCS) használatára való felkészülést ismertető cikk](http://technet.microsoft.com/library/jj713431.aspx).  

##  <a name="monitoring-virtual-applications"></a>A virtuális alkalmazások figyelése  

### <a name="virtual-application-reports"></a>Jelentések virtuális alkalmazásokról  
Az alábbi jelentések használatával figyelheti az App-V a Configuration Manager-környezetben:  

|Jelentés neve|Leírás|  
|-----------------|-----------------|  
|Az App-V virtuális környezetének eredményei|Van (csak App-V 5 esetében) kiválasztott gyűjtemény egyedi állapotában levő választott virtuális környezet információkat jeleníti meg.|  
|Az App-V virtuális környezetének eredményei egy eszközhöz|Egy kijelölt virtuális környezetről egy meghatározott eszközhöz és bármely központi telepítéstípushoz a kijelölt virtuális környezethez (csak App-V 5 esetében) információkat jeleníti meg.|  
|Az App-V virtuális környezetének állapota|A kiválasztott virtuális környezet egy kijelölt gyűjtemény megfelelőségi információit jeleníti meg. A **megőrzött** ebben a jelentésben az oszlop mutatja az eszközök, amelyeken egy korábban beállított virtuális környezet már nem alkalmazható, de megőrzésre került a felhasználói beállítások megtartására az adott (csak App-V 5 esetében) a virtuális környezetben futó alkalmazásokhoz.|  
|Számítógépek egy adott virtuális alkalmazással|A megadott App-V helyi rendelkező számítógépek összegzését jeleníti meg, hogy az Application Virtualization Management Sequencer létrehozása (csak App-V 4.6 esetében).|  
|Számítógépek egy adott virtuális alkalmazáscsomaggal|Az adott App-V alkalmazáscsomaggal telepítve (csak App-V 4.6 esetében) rendelkező számítógépek listáját tartalmazza.|  
|Virtuális alkalmazáscsomagok teljes száma|A rendszer észlelt App-V alkalmazáscsomagok (csak App-V 4.6 esetében) teljes számát jeleníti meg.|  
|Virtuális alkalmazások teljes száma|A rendszer észlelt App-V alkalmazások (csak App-V 4.6 esetében) teljes számát jeleníti meg.|  

### <a name="log-files"></a>Naplófájlok  
A Configuration Manager virtuális alkalmazástelepítéssel kapcsolatos információkat a naplófájlokban rögzíti. A napló információ fájlok, amelyek virtuális alkalmazások és a Configuration Manager alkalmazás felügyeleti használja, a következő témakörben: [naplófájlok a System Center Configuration Managerben](../../core/plan-design/hierarchy/log-files.md).  

A Windows Vista, Windows 7 és Windows 8 találhatók naplók az App-V-ügyfél C:\ProgramData\Microsoft\Application virtualizálási ügyfél.  

