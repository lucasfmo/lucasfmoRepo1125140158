---
title: "Biztonság és adatvédelem az Alkalmazáskezelés |} Microsoft Docs"
description: "Biztonsági és adatvédelmi gyakorlati tanácsokat az alkalmazások kezelése a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 521b90b9d497818a4c1e546fca38cd15d4cab487
ms.openlocfilehash: 6ee99fa0c07676f004e41a50bf16d0d17604e790
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Alkalmazáskezeléssel kapcsolatos biztonság és adatvédelem a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


##  <a name="security-best-practices-for-application-management"></a>Ajánlott biztonsági eljárások az alkalmazáskezeléshez  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Az alkalmazáskatalógus pontjait állítsa be HTTPS-kapcsolatok használatára, és tájékoztassa a felhasználókat a rosszindulatú webhelyekkel kapcsolatos veszélyekről.|Az alkalmazáskatalógus weboldal-elérési pontját és az alkalmazáskatalógus webszolgáltatási pontját állítsa be a HTTPS-kapcsolatok fogadására, hogy a kiszolgáló hitelesíthető legyen a felhasználók számára, és hogy az adatok átvitele az illetéktelen hozzáférés és megtekintés ellen védett módon történjen. A pszichológiai manipuláció módszerével végrehajtott támadások megakadályozásához tájékoztassa a felhasználókat arról, hogy csak megbízható webhelyekhez csatlakozzanak.<br /><br /> Ne használja a márkajelzési beállítások, amelyek megjelenítik a szervezet nevét az alkalmazáskatalógusban azonosítóként, identitás használatakor nem HTTPS.|  
|Különítse el a szerepköröket, és külön kiszolgálókra telepítse az alkalmazáskatalógus weboldal-elérési pontját és az alkalmazáskatalógus webszolgáltatási pontját.|Ha az Alkalmazáskatalógus weboldal-elérési pontjának biztonsága sérül, telepítse az Alkalmazáskatalógus webszolgáltatási pontja az külön kiszolgálón. Ez segít a Configuration Manager-ügyfelek és a Configuration Manager infrastruktúrájának védelme érdekében. Ez különösen fontos akkor, ha az alkalmazáskatalógus weboldal-elérési pontja az internetről érkező ügyfélkapcsolatokat fogad, mert ez a konfiguráció védtelenné teszi a kiszolgálót a támadásokkal szemben.|  
|Tájékoztassa a felhasználókat arról, hogy az alkalmazáskatalógus használatának befejezése után be kell zárniuk a böngészőablakot.|Ha a felhasználók az alkalmazáskatalógushoz használt böngészőablakban keresnek fel külső webhelyeket, a böngésző továbbra is az intraneten lévő megbízható helyekhez megfelelő biztonsági beállításokat fogja használni.|  
|Manuálisan adja meg a felhasználó-eszköz kapcsolat ahelyett, hogy a felhasználók azonosíthatják azokat az elsődleges eszközüket. Ne engedélyezze a használat alapú konfigurálást.|Ne vegye figyelembe a felhasználóktól vagy az eszköz mérvadónak az összegyűjtött adatokat. Ha a központi szoftvertelepítéshez olyan felhasználó-eszköz kapcsolatot használ, amelyet nem megbízható rendszergazda adott meg, előfordulhat, hogy olyan számítógépre vagy olyan felhasználók számára is telepíti a szoftvert, amelyek vagy akik nem jogosultak az adott szoftver használatára.|  
|A központi telepítéseket mindig úgy állítsa be, hogy letöltsék a tartalmat a terjesztési pontokról, és ne futtassák azt a terjesztési pontokról.|Ha a tartalom letöltését a terjesztési pont központi telepítéseket úgy állítja, és futtassa helyileg, a Configuration Manager ügyfél a után ellenőrzi a tartalmat tölt le. Az ügyfél elveti a csomagot, ha a kivonat nem egyezik meg a kivonat, a házirendben. Szemben ha közvetlenül a terjesztési pont futtatásához központi telepítésének konfigurálásához a Configuration Manager-ügyfél nem ellenőrzi a csomagkivonatot, ami azt jelenti, hogy a Configuration Manager ügyfél illetéktelenül szoftvert is telepíthet.<br /><br /> Ha a központi telepítéseket közvetlenül a terjesztési pontokról kell futtatnia, használjon NTFS a csomagokat a terjesztési pontok, és használja az Internet protocol biztonság (IPsec) az ügyfél és a terjesztési pont között, és a terjesztési pontok és a helykiszolgáló közötti csatorna biztonságossá tételéhez legalább engedélyeit.|  
|Interaktív programok használata, ha nem teszik lehetővé a **Futtatás rendszergazdai jogosultságokkal** lehetőség szükség.|A programok konfigurálásakor állíthatja be a **engedélyezése a felhasználók számára a következő program interaktív használatának** kapcsolót, hogy a felhasználók válaszolhassanak a felhasználói felületen szükséges figyelmeztetéseket. Ha a programhoz a **Futtatás rendszergazdai jogosultságokkal**beállítás is meg van adva, a programot futtató számítógépre bejutó támadó a felhasználói felületen továbbíthatja az ügyfélszámítógépen érvényes jogosultságokat.<br /><br /> A telepítő és a felhasználónkénti emelt szintű jogosultságokkal a felügyeleti hitelesítő adatokat igénylő szoftverek központi telepítése a Windows Installer használó programok használja. A telepítő egy rendszergazdai hitelesítő adatokkal nem rendelkező felhasználó környezetében kell futtatni. A Windows Installer felhasználónkénti emelt szintű jogosultságokkal lehetőséget nyújtanak a legbiztonságosabb telepíteni az alkalmazásokat, amelyek ennek a követelménynek.|  
|Határozza meg, hogy a felhasználók telepíthetnek-e szoftvert interaktív módon a **Telepítési engedélyek** ügyfélbeállítás használatával.|Konfigurálja a **Számítógépügynök** ügyféleszköz **telepítési engedélyek** beállítást, ha a felhasználók, akik telepíthetik a szoftvert az Alkalmazáskatalógus vagy a Szoftverközpont használatával korlátozásához. Például hozzon létre egy egyéni ügyfélbeállítást, amelynek **Telepítési engedélyek** lehetőségénél a **Csak rendszergazdák**értéket adja meg. Ezután alkalmazza ezt az ügyfélbeállítást a kiszolgálók gyűjteményére, hogy a felhasználók szoftvert telepítsenek az adott számítógépen rendszergazdai jogosultságok nélkül.|  
|Mobileszközök esetén csak aláírt alkalmazásokat telepíteni.|Mobileszköz-alkalmazások központi telepítése, csak akkor, ha a mobil eszközök által megbízhatónak minősített hitelesítésszolgáltató (CA) által kódaláíró tanúsítványával aláírt. Példa:<br /><br /><ul><li>Olyan szállítótól, amely egy ismert hitelesítésszolgáltató, például a VeriSign által aláírt alkalmazás.</li><li>Belső alkalmazás aláírása független a Configuration Manager a belső hitelesítésszolgáltató használatával.</li><li>Az alkalmazástípus létrehozásakor, és amely aláírási tanúsítványt használ a Configuration Manager használatával írja alá belső alkalmazás.</li></ul>|  
|Ha a mobileszköz-alkalmazások használatával írja alá a **alkalmazás létrehozása varázsló** a Configuration Managerben, tegye biztonságossá a helyet a fájlt, és a kommunikációs csatorna biztonságáról.|Jogok kiterjesztése és -átjárójának elleni védelme érdekében a fájlt tárolja védett mappában, és használja az IPsec vagy Server Message Block (SMB) a következő számítógépek között:<br /><br /><ul><li>A Configuration Manager konzolt futtató számítógép</li><li>Az aláírási tanúsítvány fájlját tároló számítógép</li><li>Az alkalmazás forrásfájljait tároló számítógép</li></ul> Alternatív megoldásként írja alá az alkalmazást független a Configuration Manager és a futtatása előtt a **alkalmazás létrehozása varázsló**.|  
|Alkalmazzon hozzáférés-vezérlést a referencia-számítógépek védelméhez.|Amikor egy rendszergazda felhasználó a referencia-számítógépet tallózással megkeresve konfigurálja a felderítési módszert egy központi telepítési típusban, győződjön meg arról, hogy nem sérült a számítógép biztonsága.|  
|Korlátozza és figyelje azokat a rendszergazdákat, akik az alkalmazáskezeléssel kapcsolatos következő szerepköralapú biztonsági szerepkörökkel rendelkeznek:<br /><br /><ul><li>**Alkalmazás-rendszergazda**</li><li>**Alkalmazás szerzője**</li><li> **Alkalmazás-KözpontiTelepítés kezelő**</li></ul>|Amikor szerepköralapú felügyeletet konfigurál, előfordulhat, hogy az alkalmazásokat létrehozó és telepítő rendszergazdák több engedéllyel rendelkeznek, mint azt feltételezné. Válassza például az rendszergazdákat, akik létrehozása vagy módosítása egy alkalmazás függő alkalmazások, amelyek nem szerepelnek a saját biztonsági hatókörükbe tartoznak.|  
|Microsoft Application Virtualization (App-V) virtuális környezetei konfigurálásakor válassza ki a virtuális környezetben azonos megbízhatósági szintű alkalmazásokat.|Az App-V virtuális környezetben futó alkalmazások megoszthatók az erőforrások, mert például a vágólapot, konfigurálja a virtuális környezet, hogy a választott alkalmazások azonos megbízhatósági szintűek.<br /><br /> További információkért lásd: [létrehozása az App-V virtuális környezetek](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Ha Mac számítógépekhez telepít központilag alkalmazásokat, ellenőrizze, hogy a forrásfájlok megbízható forrásból származnak-e.|A CMAppUtil eszköz nem érvényesíti a forráscsomagok aláírását, ezért bizonyosodjon meg arról, hogy a fájlok megbízható forrásból származnak. A CMAppUtil eszköz nem észleli, hogy a fájlok módosították.|  
|Ha alkalmazások Mac számítógépeken, tegye biztonságossá a helyet, a **.cmmac** fájlt, és a kommunikációs csatorna biztonságáról, amikor importálja ezt a fájlt a Configuration Manager.|A **.cmmac** a CMAppUtil eszközzel előállított és a Configuration Manager importált fájl nincs aláírva vagy érvényesítve. Ez a fájl illetéktelen módosításának megelőzése érdekében tárolja védett mappában, és IPsec vagy az SMB Protokollt használja a következő számítógépek között:<br /><br /><ul><li>A Configuration Manager konzolt futtató számítógép</li><li>A számítógép, amely tárolja a **.cmmac** fájl</li></ul>.|  
|Ha a webes alkalmazás központi telepítési típus konfigurál, használja HTTP helyett HTTPS a kapcsolat biztonságossá tétele érdekében.|Ha webes alkalmazást telepít központilag az HTTP-kapcsolat helyett HTTPS-kapcsolat használatával, az eszköz támadó kiszolgálóra lesz átirányítva, és az eszköz és a kiszolgáló között továbbított adatokat illetéktelenül sikerült.|  

##  <a name="security-issues-for-application-management"></a>Az Alkalmazáskezelés biztonsági problémái  

-   Az alacsony szintű jogosultsággal rendelkező felhasználók fájlokat másolhatnak az ügyfélszámítógépen lévő gyorsítótárból.  

     A felhasználók olvashatják az ügyfél gyorsítótárába, de nem lehet írni. Olvasási engedély birtokában a felhasználók átmásolhatják egyik számítógépről a másikra az alkalmazások telepítőfájljait.  

-   Alacsony szintű jogosultsággal rendelkező felhasználók módosíthatja a fájlokat, amelyek a központi Szoftvertelepítés előzményadatait az ügyfélszámítógépen.  

     Az alkalmazások előzményadatai nem védettek, mert a felhasználó módosíthatja a fájlokat, hogy az alkalmazás telepítve van.  

-   Az App-V csomagok nincsenek aláírva.  

     App-V csomagok a Configuration Manager alkalmazásban nem támogatják az aláírást annak ellenőrzéséhez, hogy a tartalom megbízható forrásból származik-e, és, hogy nem módosították-e az átvitel során. Nincs a biztonsági problémára nincs megoldás. Győződjön meg arról, hogy kövesse a biztonsági szempontból ajánlott letölteni a tartalmat megbízható forrásból és biztonságos helyről.  

-   A közzétett App-V alkalmazásokat az összes felhasználó telepítheti a számítógépre.  

     Az App-V alkalmazás közzé van téve egy számítógépen, ha minden felhasználó, aki jelentkezzen be arra a számítógépre telepítheti az alkalmazást. Ez azt jelenti, hogy nem korlátozhatja a felhasználókat, akik telepíthetik az alkalmazást, hogy közzététele után.  

-   A vállalati portál telepítési engedélyei nem korlátozhatók.  

     Jóllehet konfigurálhat korlátozására ügyfél telepítési engedélyek, például egy eszköz felhasználója vagy csak a helyi rendszergazdák, ez a beállítás nem működik a vállalati portál. Emiatt a jogok kiterjesztésével járhat mivel a felhasználók olyan alkalmazás, amelynek nem szabadna telepítése sikerült telepíteni.  

##  <a name="BKMK_CertificatesSilverlight5"></a>A Microsoft Silverlight 5 és az alkalmazáskatalógushoz szükséges emelt szintű megbízhatósági módban tanúsítványok  
 Configuration Manager-ügyfelek a felhasználók szoftvert tudjanak telepíteni az alkalmazáskatalógusból emelt szintű megbízhatósági módban kell futtatni a Microsoft Silverlight 5 szükséges. Alapértelmezés szerint a Silverlight alkalmazások részleges megbízhatósági módban futnak, hogy az alkalmazások ne férhessenek hozzá a felhasználói adatokhoz. Ha még nincs telepítve a Configuration Manager automatikusan telepíti a Microsoft Silverlight 5 ügyfelek. Alapértelmezés szerint a Configuration Manager állítja a Számítógépügynök **engedélyezése a Silverlight alkalmazások emelt szintű megbízhatóság módban való futásra** ügyfélbeállítást **Igen**. Ez a beállítás lehetővé teszi, hogy az aláírt és megbízható Silverlight alkalmazások kérelem emelt szintű megbízhatósági módban.  

 Az Alkalmazáskatalógus weboldal-elérési pont helyrendszerszerepkör telepítése, az ügyfél is telepíti a Microsoft aláírási tanúsítványt a megbízható közzétevők tanúsítványtárolóba minden egyes Configuration Manager ügyfélszámítógépeken. Ez a tanúsítvány lehetővé teszi, hogy a szoftver telepítése az alkalmazáskatalógusból igénylő számítógépek emelt szintű megbízhatósági módban fussanak használatával aláírt Silverlight alkalmazások. A Configuration Manager automatikusan kezeli ezt az aláírási tanúsítványt. A szolgáltatás folytonosságának biztosításához ne törölje és ne helyezze át kézzel ezt a Microsoft aláírási tanúsítványt.  

> [!WARNING]  
>  Ha engedélyezve van, a **engedélyezése a Silverlight alkalmazások emelt szintű megbízhatóság módban való futásra** ügyfél beállítással megadható, hogy a számítógép vagy a felhasználókhoz tartozó tárolóban tárolni minden olyan Silverlight alkalmazás, amely alá van írva a megbízható közzétevők tanúsítvány tanúsítványokkal emelt szintű megbízhatósági módban fusson. Az ügyfélbeállítás nem tudja engedélyezni az emelt szintű megbízhatósági módban, kifejezetten a Configuration Manager Alkalmazáskatalógus vagy a megbízható közzétevők tanúsítványtároló, a számítógép tárolja. Ha egy rosszindulatú program érvénytelen tanúsítványt helyez el a Megbízható közzétevők tanúsítványtárolóban, például a felhasználókhoz tartozó tárolóban, a saját Silverlight alkalmazását használó rosszindulatú program szintén emelt szintű megbízhatósági módban futhat.  

 Ha a **engedélyezése a Silverlight alkalmazások emelt szintű megbízhatóság módban való futásra** ügyfélbeállítást **nem**, ez nem távolítja el a Microsoft aláírási tanúsítványt az ügyfelekről.  

 További információ a Silverlight megbízható alkalmazásairól [megbízható alkalmazások](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Adatvédelmi információ az alkalmazáskezeléshez  
 Alkalmazáskezelés lehetővé teszi bármilyen alkalmazás, program vagy parancsfájl futtatását bármelyik ügyfélszámítógépen vagy mobileszköz típusú ügyfélen a hierarchiában. A Configuration Manager nem szabályozza, milyen típusú alkalmazásokat, programok vagy parancsfájlok futtatott vagy általuk közvetített információk típusa van. Az alkalmazások központi telepítése során a Configuration Manager továbbíthat az eszköz és az ügyfelek és kiszolgálók közötti bejelentkezési fiókok azonosító információkat.  

 A Configuration Manager a szoftver központi telepítésére vonatkozó állapotadatokat megőrzi. A rendszer nem titkosítja a szoftvertelepítési állapotadatokat az átvitel során, kivéve, ha a kliensgép HTTPS protokoll használatával kommunikál. Az adatbázis titkosítás nélkül tárolja az állapotadatokat.  

 A Configuration Manager alkalmazás telepítéséhez a távoli, interaktív vagy csendes szoftvertelepítéshez az ügyfeleken használatát, a szoftver szoftverlicenc-szerződés célpontjává válhat. Ehhez a szoftverlicenc-feltételek a System Center Configuration Manager elkülönül. Mindig tekintse át és fogadja el a szoftverlicenc-szerződést, mielőtt a Configuration Manager használatával központilag telepít szoftvert.  

 Alkalmazás központi telepítése alapértelmezés szerint történik, és több konfigurációs lépésre van szükség.  

 A felhasználó-eszköz kapcsolat és az alkalmazáskatalógus a szoftvertelepítést elősegítő opcionális szolgáltatások.  

-   Felhasználó-eszköz kapcsolatot, hogy a Configuration Manager felügyeleti használatával szoftverek telepíthetők központilag egy felhasználó, és a szoftver automatikusan számítógépre telepítve van egy vagy több által leggyakrabban használt a felhasználói eszközökre hozzárendeli a felhasználót.  

-   Az Alkalmazáskatalógus egy olyan webhely, lehetővé teszi, hogy a felhasználók kérelem szoftvert kell telepíteni.  

 Az alábbi szakaszok a felhasználó-eszköz kapcsolat és az alkalmazáskatalógus használatához tartozó adatvédelmi információkat tartalmazzák.  

 Az alkalmazáskezelés konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

##  <a name="user-device-affinity"></a>Felhasználó-eszköz kapcsolat  
-  A Configuration Manager továbbíthat az ügyfelek és a felügyeletipont-rendszerek között. A információ előfordulhat, hogy azonosítsa a számítógép és a bejelentkezési fiók és bejelentkezési fiókok röviden bemutatják azok használatát.  
-  Az ügyfél és kiszolgáló között továbbított adatok nem titkosítottak, kivéve, ha a felügyeleti pont HTTPS segítségével kommunikáló ügyfelek úgy van beállítva.  
-  A számítógép és bejelentkezési fiókok használati adatait, amely a felhasználó hozzárendelése egy eszköz szolgál az ügyfélszámítógépeken tárolt, felügyeleti pontoknak küldött, és majd tárolja a Configuration Manager adatbázisába. A régi információk alapértelmezés szerint 90 nap után törlődnek az adatbázisból. A törlési beállítás testre szabható a **Felhasználó-eszköz kapcsolatra vonatkozó régi adatok törlése** helykarbantartási feladat beállításával.
-  A Configuration Manager felhasználó-eszköz kapcsolatra vonatkozó állapotadatokat megőrzi. Az állapotadatok nincsenek titkosítva az átvitel során, kivéve, ha a kliensgépek úgy vannak beállítva, hogy HTTPS használatával kommunikáljanak a felügyeleti pontokkal. Az adatbázis titkosítás nélkül tárolja az állapotadatokat.  
-  Számítógép, a bejelentkezési fiókok használati adatait és a állapotára vonatkozó információkat nem küldése a Microsoftnak.  
-  Számítógép, és jelentkezzen be, hogy a felhasználó-eszköz kapcsolat létrehozására szolgál használati adatai mindig engedélyezve van. Ezenkívül a felhasználók és rendszergazda felhasználók is megadhatnak a felhasználó-eszköz kapcsolatra vonatkozó információkat.  

##  <a name="application-catalog"></a>Alkalmazáskatalógus  
-  Az Alkalmazáskatalógus lehetővé teszi, hogy a Configuration Manager felügyeleti bármilyen alkalmazás vagy a program vagy parancsfájl futtatását a közzététele. A Configuration Manager nem szabályozza, programokat vagy parancsfájlokat a katalógusban közzétett típusú vagy az általuk közvetített információk típusa van.    
-  A Configuration Manager ügyfelek és az Alkalmazáskatalógus helyrendszerszerepkörök között információt továbbíthat az. Az információk előfordulhat, hogy azonosítsa a számítógépet és annak bejelentkezési fiókjait. A kliensgép és a kiszolgálók között továbbított adatok nincsenek titkosítva, kivéve, ha a helyrendszerszerepkörök úgy vannak beállítva, hogy HTTPS használatát követeljék meg csatlakozáskor a kliensgépektől.  
-  A az alkalmazás-jóváhagyási kérelmekre vonatkozó adatok tárolása a Configuration Manager adatbázisába. A törölt vagy visszautasított kérelmek és a megfelelő kérelemelőzmény-bejegyzésekkel törlődik alapértelmezés szerint 30 nap múlva. A törlési beállítás testre szabható az **Alkalmazásigénylésekre vonatkozó régi adatok törlése** helykarbantartási feladat beállításával. Alkalmazás-jóváhagyási kérelmek a jóváhagyott és függőben lévő állapotok soha nem kerülnek törlésre.  
-  Az alkalmazáskatalógusba érkező és onnan küldött adatokat a rendszer nem küldi el a Microsoftnak.  
-  A rendszer alapértelmezés szerint nem telepíti az alkalmazáskatalógust. Ez a telepítés több konfigurációs lépést igényel.  

