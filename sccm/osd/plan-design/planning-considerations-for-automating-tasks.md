---
title: "Tervezési megfontolások a feladatok automatizálásához |} Microsoft Docs"
description: "Megtervezéséről, mielőtt a System Center Configuration Managerben feladatok automatizálása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc497a8a-3c54-4529-8403-6f6171a21c64
caps.latest.revision: 13
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 830f715b688cc9929a179da94eba9c81de8db11a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-considerations-for-automating-tasks-in-system-center-configuration-manager"></a>Tervezési megfontolások a feladatok automatizálásához a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager környezetben feladatok automatizálására feladatütemezéseket hozhat létre. Ilyen feladat például az operációs rendszerek rögzítése referencia-számítógépre, vagy az operációs rendszer központi telepítése egy vagy több célszámítógépre. A feladatütemezés által végrehajtott műveletek az ütemezés lépései között definiálhatók. A feladatütemezés futtatásakor a rendszer minden egyes lépést végrehajt parancssori szinten a helyi rendszer környezetében, felhasználói beavatkozás nélkül. Az alábbi szakaszok a segítségével megtervezheti a feladatok a Configuration Manager automatizálását.

##  <a name="BKMK_TSStepsActions"></a>Feladatütemezési lépések és műveletek  
 Lépésekre feladatütemezés alapeleme. Tartalmazhat olyan parancsokat, amelyek konfigurálására, és rögzítheti az operációs rendszer egy referencia-számítógép, vagy tartalmazhat olyan parancsokat, amelyek az operációs rendszer, illesztőprogramokat, a Configuration Manager-ügyfél és a szoftver telepítése a célszámítógépen. A feladatütemezési lépésekhez szükséges parancsokat a lépésben szereplő műveletek határozzák meg. Kétféle művelet van. A parancssori karakterlánccal definiált műveletek az egyéni műveletek. A Configuration Manager által előre definiált műveletek a beépített műveletek nevezzük. Egy feladatütemezés egyéni és beépített műveletek tetszőleges kombinációját hajthat végre.  

 Feladatütemezési lépések is hozzáadhat feltételeket, amelyek szabályozzák a lépés működését, például a feladatütemezés leálljon vagy a feladatütemezés Folytatás hiba esetén. Feltétel hozzáadásához feladatütemezési változót kell szerepeltetni a lépésben. Az **SMSTSLastActionRetCode** változóval például az előző lépés feltétele tesztelhető. Változók egyetlen lépésben vagy lépéseket a csoporthoz lehet hozzáadni.  

 Feladatütemezési lépések feldolgozása sorrendben történik, mely tartalmazza a műveletet, és azokat a feltételeket, a lépés rendelt. Indításakor a Configuration Manager egy feladatütemezési lépés feldolgozását, a következő lépéssel nem indult el, amíg a korábbi műveletet végre nem. A feladatütemezés akkor tekinthető befejezettnek, ha az összes lépését végrehajtotta, vagy ha egy hibás lépés miatt a Configuration Manager leállítja a feladatütemezés futtatása előtt az összes lépést elvégezte volna. Például ha egy feladatütemezés lépés nem talál egy hivatkozott rendszerképet vagy csomagot egy terjesztési ponton, a feladatütemezésben szerepel egy hibás hivatkozás, és a Configuration Manager leállítja a feladatütemezés ezen a ponton futtatását, kivéve ha a sikertelen lépés olyan feltételt továbbra is, ha hiba lép.  

> [!IMPORTANT]  
>  Alapértelmezés szerint ha egy lépés vagy művelet meghiúsul, a feladatütemezés is sikertelen lesz. Ha szeretné, hogy a feladatütemezés sikertelen lépés esetén is folytatódjon, szerkesztheti a feladatütemezést: kattintson a **Beállítások** lapfülre, majd válassza a **Folytatás hiba esetén**.  

 A lépéseket a feladatütemezésbe felvehető kapcsolatos további információkért lásd: [feladatütemezési lépéseket](../understand/task-sequence-steps.md).  

##  <a name="BKMK_TSGroups"></a> Feladatütemezési csoportok  
 **Csoportok** több lépést jelentenek egy adott feladatütemezésben. Egy feladatütemezési csoport egy névből, egy opcionális leírásból, illetve olyan opcionális feltételekből áll, amelyet a rendszer egyetlen egységként értékel, mielőtt folytatná a következő feladatütemezési lépéssel. A csoportok beágyazhatók egymásba, és vegyesen tartalmazhatnak lépéseket és alcsoportokat is. A csoportok több, közös feltétellel rendelkező lépés kombinálására kínálnak hasznos eszközt.  

> [!IMPORTANT]  
>  Ha egy csoport bármely lépése vagy beágyazott csoportja meghiúsul, alapértelmezés szerint a feladatütemezési csoport is sikertelen lesz. Ha szeretné, hogy a feladatütemezés sikertelen lépés vagy sikertelenül beágyazott csoport esetén is folytatódjon, szerkesztheti a feladatütemezést: kattintson a **Beállítások** lapfülre, majd válassza a **Folytatás hiba esetén**.  

 Az alábbi táblázat bemutatja a **Folytatás hiba** beállítás működését lépések csoportosítása esetén.  

 Ebben a példában a rendszer két feladatütemezési csoport, amely három feladatütemezési lépést tartalmazhat.  

|Feladatütemezési csoport vagy lépés|Folytatás hiba esetén beállítás értéke|  
|---------------------------------|-------------------------------|  
|**1. feladatütemezési csoport**|**A Folytatás hiba esetén** beállítás aktív.|  
|Feladatsor 1. lépése|**A Folytatás hiba esetén** beállítás aktív.|  
|2. feladatütemezési lépés|Nincs beállítva.|  
|3. feladatütemezési lépés|Nincs beállítva.|  
|**2. feladatütemezési csoport**|Nincs beállítva.|  
|4. feladatütemezési lépés|Nincs beállítva.|  
|5. feladatütemezési lépés|Nincs beállítva.|  
|6. feladatütemezési lépés|Nincs beállítva.|  

-   Ha a feladatütemezési lépés 1 sikertelen, a feladatütemezés végrehajtása folytatódik, a feladatütemezési lépés 2.  

-   2 feladatütemezési lépés sikertelen lesz, ha a feladatütemezés nem fut a 3. feladatütemezési lépés, de továbbra is fut a feladatütemezési lépések 4. és 5, amely egy másik feladatütemezési csoportban találhatók.  

-   Ha a 4. feladatütemezési lépés sikertelen lesz, hajt végre semmilyen további lépéseket, és a feladatütemezés sikertelen lesz, mivel a **Folytatás hiba** beállítás 2 feladatütemezési csoport esetén nem volt beállítva.  

 A feladatütemezési csoportokhoz, nevet kell rendelnie, bár a csoport neve nem kell egyedinek lennie. A feladatütemezési csoporthoz emellett igény szerint leírást is megadhat.  

##  <a name="BKMK_TSVariables"></a> Feladatütemezési változók  
 Feladatütemezési változók olyan számítógép, az operációs rendszer és a felhasználó konfigurációs feladatok számára egy Configuration Manager ügyfélszámítógépeken a konfigurációs és operációs rendszer központi telepítési beállításokat szolgáltatnak név-érték párokat. A feladatütemezési változók a feladatütemezési lépések konfigurálására és testreszabására nyújtanak lehetőséget.  

 Amikor futtat egy feladatütemezést, a rendszer számos feladatütemezési beállítást környezeti változóként tárol el. Eléréséhez, vagy módosítsa a beépített feladatütemezési változók értékét, és hozhat létre új feladat feladatütemezési változók segítségével testre szabhatja a feladatütemezés futtatását a célszámítógépen.  

 Feladatütemezési változók a feladatütemezési környezetben segítségével hajtsa végre a következő műveleteket:  

-   Feladatütemezési műveletek beállításainak konfigurálása  

-   Parancssori argumentumok biztosítása feladatütemezési lépés  

-   Olyan feltétel, amely meghatározza, hogy a feladatütemezési lépés vagy csoport fusson-e értékelése  

-   Adjon meg értékeket a feladatütemezésben használt egyéni parancsfájlokhoz  

 Például lehetséges, hogy a feladatütemezés tartalmazza a **csatlakozás tartományhoz vagy munkacsoporthoz** feladatütemezési lépést. A feladatütemezést különböző gyűjteményekre alkalmazhatja, a gyűjtemények tagságát pedig a tartományi tagság határozza meg. Ebben az esetben adja meg az egyes gyűjtemények tartománynevéhez gyűjteményi feladatütemezési változót, és, hogy a feladatütemezési változó segítségével adja meg a feladatütemezést a megfelelő tartománynévvel.  

###  <a name="BKMK_TSCreateVariables"></a> Feladatütemezési változók létrehozása  
 Új feladatütemezési változók testre szabhatja és szabályozhatja a feladatütemezési lépéseket adhat hozzá. Létrehozhat például olyan feladatütemezési változót, amellyel felülbírálhatja egy beépített feladatütemezési lépés egyik beállítását. Emellett egyéni feladatütemezési változók is létrehozhatók a feladatütemezés egyes feltételeihez, parancssoraihoz és egyéni lépéseihez. Amikor létrehoz egy feladatütemezési változót, a rendszer akkor is megőrzi a változót és a hozzá kapcsolódó értéket a feladatütemezési környezetben, ha a feladatütemezés újraindul a célszámítógépen. A változó és értéke a feladatütemezés keretében különböző operációs rendszerkörnyezetekben is használható – Például használható egy teljes Windows operációs rendszer és a Windows PE környezetben.  

 A következő táblázat ismerteti a feladatütemezés változó, és további használati adatai létrehozásának.  

|Létrehozási módszer|Használat|  
|-------------------|-----------|  
|Mezők beállítása a feladatütemezési lépésekben a Feladatütemezés-szerkesztő segítségével|A feladatütemezési lépés alapértelmezett értékeinek meghatározása. A változó és az érték csak akkor érhető el, amikor a feladatütemezés az adott lépést futtatja. Az általános feladatütemezési környezetnek nem szerepelnek, és nincsenek elérhető-e más feladatütemezési lépések a feladatütemezésben.<br /><br /> A beépített változók és a kapcsolódó lépések listája, [feladat feladatütemezési művelet változói](../understand/task-sequence-action-variables.md).|  
|Rögzített feladatütemezési változós lépés hozzáadása egy feladatütemezéshez|A feladatütemezési változó és a hozzá tartozó érték meghatározása a feladatütemezési környezetben, amikor a lépést a feladatütemezés keretében futtatják. A környezeti változóhoz és értékéhez az összes későbbi feladatütemezési lépés hozzáférhet.|  
|Gyűjteményre vonatkozó változó definiálása|Feladatütemezési változók és értékek meghatározása számítógép-gyűjteményhez. A gyűjteménynek szánt feladatütemezések mind hozzáférhetnek a feladatütemezési változókhoz és értékeikhez.|  
|Számítógépre vonatkozó változó definiálása|Feladatütemezési változók és értékek meghatározása egy adott számítógéphez. A számítógépre szánt feladatütemezések mind hozzáférhetnek a feladatütemezési változókhoz és értékeikhez.|  
|Feladatütemezési változó hozzáadása a Feladatütemezési média létrehozása varázsló **Testreszabás** lapján|Feladatütemezési változók és értékek meghatározása az arról a hordozóról futtatott feladatütemezéshez, amely hozzáférhet a változóhoz és értékéhez.|  

 A beépített feladatütemezési változó alapértelmezett értékének felülbírálásához a beépített változóval azonos nevű feladatütemezési változót kell definiálnia. A beépített feladatütemezési változókról, a hozzájuk kapcsolódó műveletekről és használatukról listájáért lásd: [beépített feladatütemezési változókat](../understand/task-sequence-built-in-variables.md).  

 Is töröl egy feladatütemezési változót a feladatütemezési környezet segítségével ugyanazokat a módszereket a feladatütemezési változó létrehozása. Ebben az esetben a törléshez a változó a feladatütemezési környezetben, beállíthatja a feladatütemezési változó értéke üres karakterláncot kell megadni.  

 Egy feladatütemezési környezeti változó különböző értékekre ugyanabban a sorrendben módszerek kombinálásával. Ebben a speciális esetben egyes feladatütemezési lépésekhez alapértelmezett értékeket állít be a Feladatütemezés-szerkesztőben, majd más módszerekkel egyéni értékeket határoz meg a változókhoz. Az alábbi lista ismerteti azokat a szabályokat, amelyekkel meghatározhatja, hogy melyik értéket vegye figyelembe, ha egy feladatütemezési változót több különböző módszer használatával hozták létre.  

1.  A **feladatütemezési változó beállítása** lépés az összes többi létrehozási módszert felülbírálja.  

2.  Számítógépes változók elsőbbséget élveznek gyűjteményre vonatkozó változókkal szemben. Az azonos feladatütemezési változó nevét egy számítógépre vonatkozó változó és egy gyűjteményre vonatkozó változó adja meg, ha a számítógép változó értékét fogja használni, a feladatütemezés a célszámítógépen történő futtatásakor.  

3.  Feladatütemezések adathordozóról futtatható. Az adathordozóról futtatott változók gyűjteményre vagy számítógépre vonatkozó változók helyett használhatók. Ha a feladatütemezés adathordozóról fut, a rendszer a számítógépre és gyűjteményre vonatkozó változókat nem használja, Ehelyett feladat definiált feladatütemezési változókat a **testreszabási** a feladatütemezési média varázsló értékeinek beállításához az adathordozóról futtatott feladatütemezés használatával  

4.  Ha egy feladatütemezési változó értéke nincs beállítva a feladatütemezési környezetben, beépített műveletek használja az alapértelmezett értéket a lépést, amely a feladatütemezés-szerkesztőben.  

 Beépített feladatütemezési lépések beállításainak felülbírálása, mellett is létrehozhat egy új környezeti változókat használja a egy feladatütemezési lépés, a parancsfájl, a parancssor vagy a feltétel. Amikor megad egy új feladatütemezési változó nevét, kövesse az alábbi irányelveket:  

-   A feladatütemezési változó nevét, melyet tartalmazhat betűket, számokat, aláhúzásjel (_) és kötőjelet (-).  

-   Feladatütemezési változó neve legalább 1 karakter és egy legfeljebb 256 karakter hosszúságú rendelkeznek.  

-   Felhasználó által definiált változóknak betűvel (A – Z vagy a – z) kell kezdődnie.  

-   Felhasználó által definiált váltók neve nem kezdődhet aláhúzás karaktert. Csak írásvédett feladatütemezési változók a aláhúzás karakterrel kell megelőznie.  

    > [!NOTE]  
    >  Írásvédett feladatütemezési változók is olvashatják a feladatütemezési lépéssel egy feladatütemezésben, de nem állítható be. Például használhatja az írásvédett feladatütemezési változót a parancssor részeként egy **parancssor futtatása** feladatütemezési művelet változó, de nem állítható be egy írásvédett változó segítségével a **feladatütemezési változó beállítása** művelet.  

-   A feladatütemezési változók nevében nincsenek kis-és nagybetűket. Például az "osdvar" és "osdvar" az az azonos feladatütemezési változót jelöli.  

-   Feladatütemezési változó neve nem kezdődik vagy végződik szóközzel vagy beágyazott szóközöket tartalmazhat. A kezdő vagy egy feladatütemezési változó nevét a végén hagyott szóközöket a rendszer figyelmen kívül hagyja.  

 Az alábbi táblázat néhány példát láthat érvényes és érvénytelen felhasználó által megadott feladatütemezési változók.  

|Példák felhasználó által megadott érvényes változónevekre|Példák felhasználó által megadott érvénytelen változónevekre|  
|-------------------------------------------------------|----------------------------------------------------------|  
|SajatValtozo|1Variable<br /><br /> Felhasználó által megadott feladatütemezési változók neve nem kezdődhet számmal.|  
|Sajat_valtozo|MyV@riable<br /><br /> Felhasználó által megadott feladatütemezési változók neve nem tartalmazhatja a @ karakter.|  
|Sajat_valtozo_2|_MyVariable<br /><br /> A felhasználó által megadott feladatütemezési változók nem kezdődhet aláhúzás karakterrel kezdődik.|  

 Általános korlátozások a feladatütemezési változók:  

-   A feladatütemezési változók értékei nem lehetnek hosszabbak 4000 karakternél.  

-   Nem hozható létre, vagy bírálja felül az írásvédett feladatütemezési változót. Az írásvédett változók neve aláhúzással (_) kezdődik. Az írásvédett feladatütemezési változók értéke elérhető a feladatütemezésben, a társított értékek azonban nem módosíthatók.  

-   A feladatütemezési változók értékeiben a használati módjuktól függően a kis- és nagybetűk különbözőnek számíthatnak. A legtöbb esetben azonban a változók értékeiben a rendszer nem tesz különbséget a kis- és nagybetűk között – Azonban néhány érték kis-és nagybetűket például jelszót tartalmazó változó lehet.  

-   Hány feladatütemezési változókat is létrehozható nincs korlátozva van. a változók számát azonban a feladatütemezési környezet mérete korlátozza. A feladatütemezési környezet teljes mérete legfeljebb 32 MB lehet.  

###  <a name="BKMK_TSEnvironmentVariables"></a> Hozzáférés a környezeti változókhoz  
 Miután megadta a feladatütemezési változó és értéke a fenti szakaszban leírt módszerek egyikével, a környezeti változó értékét használhatja a feladatütemezésekben. Elérhetők a beépített feladatütemezési változókról tartozó alapértelmezett értékeket, adjon meg egy új értéket a beépített változókhoz, és parancssori vagy parancsfájl egyéni feladatütemezési változót használja.  

 A következő táblázat a feladatütemezési környezet változóinak elérésével végrehajtható feladatütemezési műveleteket ismerteti.  

|Feladatütemezési művelet|Használat|  
|-----------------------------|-----------|  
|Műveleti beállítások konfigurálása|Megadhatja, hogy a feladatütemezési lépés beállítását biztosítja a változó értéke az ütemezés futtatásakor.<br /><br /> Adja meg a feladatütemezési lépés beállítását egy feladatütemezési környezeti változó használatával, segítségével a feladatütemezés-szerkesztő szerkessze a lépést, és adja meg a változó nevét a mező értékét. A változó nevét százalékjelek (%) közé kell foglalni – ez jelzi, hogy az érték környezeti változó.|  
|Parancssori argumentumok megadása|Megadhat egy részét vagy egészét egy egyéni parancssort használva egy környezeti változó értékét.<br /><br /> Szeretne megadni egy parancssori beállítást környezeti változóval, használja a változó nevét részeként a **parancssori** mezőjét a **parancssor futtatása** feladatütemezési lépést. A változó nevét százalékjelek (%) közé kell zárni.<br /><br /> Például a következő parancsot használja egy beépített környezeti változó C:\File.txt írni a számítógép nevét.<br /><br /> <br /><br /> **Cmd /C % _SMSTSMachineName % > C:\File.txt**|  
|Lépés feltételének értékelése|A feladatütemezési lépések vagy csoportok feltételeinek keretében beépített és egyéni feladatütemezési környezeti változókat is használhat. A környezeti változó értékét lesz kiértékelve az összesítés előtt a feladatütemezési lépés vagy csoport futtatása.<br /><br /> Egy változó értékének kiértékelésére szolgáló feltétel hozzáadásához tegye a következőket:<br /><br /> 1.  Válassza ki azt a lépést vagy csoportot, amely hozzá szeretné adni a feltételt.<br />2.  Az a **beállítások** a lépést vagy csoportot, válassza a lap **feladatütemezési változó** a a **feltétel hozzáadása** legördülő listán.<br />3.  Az a **feladatütemezési változó** párbeszédpanelen adja meg a nevét, a változó, a tesztelni kívánt feltételt, és a változó értékét.|  
|Információ biztosítása egyéni parancsfájlról|Feladatütemezési változók olvashatók és írhatók a Microsoft.SMS.TSEnvironment COM-objektumot a feladatütemezés futása közben.<br /><br /> Az alábbi példában egy Visual Basic-parancsfájlt, amely bemutatja a **_SMSTSLogPath** feladatütemezési változót is az aktuális napló helyét. A parancsfájl emellett egy egyéni változót is beállít.<br /><br /> <br /><br /> **dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")**<br /><br /> <br /><br /> **dim logPath**<br /><br /> <br /><br /> **' A környezet lekérdezésével megismerheti a meglévő változókat.**<br /><br /> **logPath = env("_SMSTSLogPath")**<br /><br /> <br /><br /> **' A változókat az OSD-környezetben is beállíthatja.**<br /><br /> **env("MyCustomVariable") = "varname"**<br /><br /> <br /><br /> A feladatütemezési változók parancsfájlokban történő használatáról további információért olvassa el az SDK dokumentációját.|  

###  <a name="BKMK_ComputerCollectionVariables"></a> Számítógép- és gyűjteményváltozók  
 Feladatütemezések párhuzamosan futhat egymás mellett több számítógépen vagy gyűjtemények konfigurálása Megadhat egyedi számítógépre vagy gyűjteményre adatokat, például adja meg egy egyedi operációs rendszer termékkulcsát vagy egy gyűjtemény összes tagjához megadott tartományhoz való csatlakozásra.  

 Feladatütemezési változók rendelhet egy egyetlen számítógéphez vagy gyűjteményhez. Amikor a feladatütemezés a célszámítógépen vagy-gyűjteményben futni kezd, megadott értékek érvényesek a célszámítógépen vagy -gyűjteményben.  

 Megadhatja, hogy a feladatütemezési változók egyetlen számítógépre vagy egy gyűjtemény. Amikor a feladatütemezés a célszámítógépen vagy-gyűjteményben futni kezd, a környezeti változókat kerülnek, és értékei elérhetők az összes lépése a feladatütemezés.  

> [!WARNING]  
>  Ha ugyanaz a változónév egy gyűjteményre és a számítógép változó használja, a számítógépre vonatkozó változó értékét elsőbbséget élvez a gyűjteményváltozóval. Gyűjteményekhez rendelt feladatütemezési változók elsőbbséget élveznek a beépített feladatütemezési változókról keresztül.  

 A számítógépek és gyűjtemények feladatütemezési változóinak létrehozásáról a további információkért lásd: [a számítógépek és gyűjtemények feladatütemezési változók létrehozása](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTSVariables).  

###  <a name="BKMK_TSMediaVariables"></a> Feladatütemezési adathordozóhoz kapcsolódó változók  
 Az adathordozóról futtatott feladatütemezés feladatütemezési változókat is megadhat. Ha adathordozó használatával az operációs rendszer központi telepítését a feladatütemezési változók hozzáadását és értékeik megadását a média; létrehozásakor a változók és azok értékeit tárolják az adathordozón.  

> [!NOTE]  
>  A feladatütemezések tárolása különálló adathordozón. Azonban minden más típusú telepítőlemezeké, manuálisan előkészített adathordozó, például a felügyeleti pontról képes lekérni a feladatütemezést.  

 A adhatja meg a feladatütemezési változók a **testreszabási** a feladatütemezési média varázsló oldalán. További információ az adathordozók létrehozásáról: [Feladatütemezési adathordozó létrehozása](../deploy-use/create-task-sequence-media.md).  

> [!TIP]  
>  A feladatütemezés írja a Csomagazonosítót és az előindítási parancssort, beleértve a feladatütemezési változók, a Configuration Manager konzolt futtató számítógépen a CreateTSMedia.log naplófájlba értékét. Ebben a naplófájlban ellenőrizheti a feladatütemezési változók értékét.  

##  <a name="BKMK_TSCreate"></a> Feladatütemezés létrehozása  
 A feladatütemezés létrehozása varázsló segítségével készíthet feladatütemezéseket. A varázsló adott feladatok elvégzésére szolgáló beépített feladatütemezések vagy számos különböző feladat elvégzésére szolgáló egyéni feladatütemezések készítésére szolgál.  

 Létrehozhat például olyan feladatütemezéseket, amelyek összeállítják és rögzítik egy referencia-számítógép operációsrendszer-képét, vagy már létező operációsrendszer-képet telepítenek a kívánt célszámítógépre; vagy egyéni feladatütemezéseket is létrehozhat egy egyedi feladat ellátására. Egyéni feladatütemezés segítségével speciális operációs rendszer központi telepítéseket.  

 Feladatütemezések létrehozásával kapcsolatos további információkért lásd: [feladatütemezések](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTaskSequence).  

##  <a name="BKMK_TSEdit"></a> Feladatütemezés szerkesztése  
 A feladatütemezés szerkesztésével használatával a **feladatütemezés-szerkesztő**. A szerkesztő a következő módosításokat végezheti a feladatütemezésbe:  

-   Adja hozzá, vagy távolítsa el a feladatütemezés lépéseit.  

-   Módosíthatja a feladatütemezési művelet a lépések sorrendjét.  

-   Adja hozzá, vagy távolítsa el a lépések csoportokat.  

-   Megadhatja, hogy a feladatütemezés végrehajtása folytatódik, ha hiba történik.  

-   Feltételeket adhat a feladatütemezés lépéseihez és csoportjaihoz.  

> [!IMPORTANT]  
>  Ha a feladatütemezés egy csomagot vagy a Szerkesztés programra mutató társítatlan hivatkozás marad, javítsa ki a hivatkozást, törli a helytelenül hivatkozott programot a feladatütemezésből, vagy átmenetileg tiltsa le a hibás feladatütemezési lépést, amíg a hibás hivatkozás korrigálásáig vagy eltávolításáig.  

 Feladatütemezések szerkesztésével kapcsolatos további információkért lásd: [a feladatütemezések szerkesztésével](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

##  <a name="BKMK_TSDeploy"></a> Feladatütemezés központi telepítése  
 A feladatütemezés telepítene a célszámítógépeken, amelyek a Configuration Manager-gyűjteményhez. beleértve a **Minden ismeretlen számítógép** gyűjteményt is, amely az operációs rendszerek ismeretlen számítógépekre történő telepítésére szolgál. A feladatütemezések ugyanakkor felhasználógyűjteményekre nem telepíthetők.  

> [!IMPORTANT]  
>  Kerülje az olyan feladatütemezések központi telepítését, amelyek nem megfelelő gyűjteményekbe telepítenek operációs rendszereket, például a **Minden rendszer** gyűjteménybe. Ügyeljen arra, hogy a gyűjtemény, amelyre a feladatütemezést központilag telepíti, csak olyan számítógépeket tartalmazzon, amelyeken valóban telepíteni szeretné az operációs rendszert. A központi telepítési beállítások kezelésével elkerülheti az operációs rendszer nem kívánt központi telepítését. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

 Minden célszámítógép, amely megkapja a feladatütemezést futtatja a feladatütemezést, a központi telepítés megadott beállításoknak megfelelően. Maga a feladatütemezés nem tartalmaz társított fájlokat vagy programokat. A feladatütemezés által hivatkozott fájloknak már eleve elérhetőnek kell lenniük a célszámítógépen vagy az ügyfelek számára hozzáférhető terjesztési ponton. Emellett a feladatütemezés telepítése a csomagok, programok által hivatkozott, még akkor is, ha a program vagy csomag már telepítve van a célszámítógépen.  

> [!NOTE]  
>  Csomagokkal és programokkal ellentétben a feladatütemezés telepít egy alkalmazást, ha az alkalmazás telepítése csak akkor, ha az alkalmazás a követelményszabályok teljesülnek, és az alkalmazás nincs telepítve, az alkalmazáshoz megadott észlelési módszer alapján.  

 A Configuration Manager-ügyfél ügyfélházirend letöltésekor futtatja a feladatütemezéseket. Ha nem szeretné megvárni a következő lekérdezési ciklust, hanem manuálisan szeretné elindítani a műveletet, olvassa el a [Házirend lekérésének kezdeményezése Configuration Manager-ügyfélhez](../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) című szakaszt.  

 Ha írási szűrőket használó Windows Embedded-eszközökre telepít feladatütemezést, megadhatja, hogy az írási szűrő le legyen-e tiltva az eszközön a telepítés során, majd a telepítést követően újraindítható az eszköz. Ha az írási szűrő nincs letiltva, a feladatütemezés központi telepítése átmeneti területre történik, és nem lesz elérhető az eszköz újraindításakor.  

> [!NOTE]  
>  Ha a feladatütemezés központi telepítése egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz tagja-e egy gyűjteményt, amely rendelkezik beállított karbantartási időszakkal. Ez lehetővé teszi, hogy amikor az írási szűrő le van tiltva, engedélyezve van, és az eszköz újraindításakor kezelése.  
>   
>  Ha az ügyfelek letöltik a feladatütemezések a karbantartási időszakon kívül, a feladatütemezés kétszer lesznek letöltve. Ebben a forgatókönyvben ügyfelek letölthesse a feladatütemezés, letiltja az írási szűrőket, indítsa újra a számítógépet, és ezután töltse le a feladatütemezést ismét, mert a feladatütemezés le vannak töltve az átmeneti területre történjen, amely az eszköz újraindításakor törlődik.  

 Feladatütemezések telepítésével kapcsolatos további információkért tekintse meg a [feladatütemezés központi telepítése](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_TSExportImport"></a> Feladatütemezések exportálása és importálása  
 A Configuration Manager lehetővé teszi az exportálási és importálási feladatütemezések. Feladatütemezés exportálásakor a hivatkozott objektumokat is elhelyezheti az exportált csomagban – Ezek közé tartozik, az operációs rendszer lemezképét, a rendszerindító lemezkép, ügyfélügynökcsomagról, illesztőprogram-csomagot és függőségekkel rendelkező alkalmazások.  

> [!NOTE]  
>  A feladatütemezések exportálási és importálási folyamat nagyon hasonlít a Configuration Manager-alkalmazások exportálási-importálási folyamatához.  

 További információ a feladatütemezések importálása és exportálása: [az exportálás és importálás operációsrendszer-lemezképek](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ExportImport).  

##  <a name="BKMK_TSRun"></a> Feladatütemezés futtatása  
 Alapértelmezés szerint mindig futtathatók a helyi rendszer fiók használatával. A parancssori lépés azonban lehetőséget nyújt a feladatütemezés másik fiókkal való futtatására. A feladatütemezés futtatásakor a Configuration Manager-ügyfél először ellenőrzi az esetleges hivatkozott csomagokat, a feladatütemezés lépéseit megkezdése előtt. Ha a hivatkozott csomag nincs ellenőrizve, vagy nem érhető el terjesztési ponton, a feladatütemezés hibát ad vissza a kapcsolódó feladatütemezési lépéshez.  

 Ha egy terjesztett feladatütemezés letöltése és futtatása van konfigurálva, az összes függő csomagot és alkalmazást letöltődnek a Configuration Manager-ügyfél gyorsítótárába. A szükséges csomagokat és alkalmazásokat akkor kapja meg a terjesztési pontokról, és ha a Configuration Manager-ügyfél gyorsítótára túl kicsi, vagy a csomag vagy alkalmazás nem található, a feladatütemezés sikertelen lesz, és egy állapotüzenetet generál. A **Tartalom helyi letöltése, ha a futó feladatütemezés igényli**beállítással azt is megadhatja, hogy az ügyfél csak szükség esetén töltse le a tartalmat, illetve a **Program futtatása a terjesztési pontról** beállítással azt, hogy az ügyfél közvetlenül a terjesztési pontról telepítse a fájlokat, anélkül, hogy letöltené azokat a gyorsítótárba. A **program futtatása terjesztési pontból** lehetőség áll rendelkezésre, csak akkor, ha a hivatkozott csomagoknál beállítása lehet **a csomag tartalmának másolása a terjesztési pontok egy csomagmegosztásába** engedélyezve a **adatelérési** lapján a **csomag** tulajdonságait.  

 Ha egy függő csomagot vagy alkalmazást a feladatütemezést futtató kliensgép nem talál, az ügyfél azonnal hibaüzenetet küld, amikor a függőség állapota **elérhető**. Azonban ha a függőség állapota **szükséges**, megvárja-e a Configuration Manager-ügyfél és a próbálkozások letölteni a tartalmat a határidő lejártakor, abban az esetben, ha a tartalom még nem replikálódik terjesztési ponton, amelyet az ügyfél által hozzáférhető.  

 Egy feladatütemezés sikeres vagy sikertelen teljesítése után, a Configuration Manager rögzíti ezt a Configuration Manager ügyfél az előzményekben. Nem vonhatja vissza, vagy állítsa le a feladatütemezést, Miután elindította azt egy számítógépen.  

> [!IMPORTANT]  
>  Ha egy feladatütemezési lépés a kliensgép újraindítására van szükség, az ügyfél képes rendszerindítást, egy formázott lemezpartíción kell lennie. Ellenkező esetben a feladatütemezés sikertelen lesz, függetlenül a feladatütemezésben megadott hibakezeléstől.  

 Ha egy feladatütemezés egy függő objektumát, például egy szoftverterjesztési csomagot újabb verzióra frissít, a rendszer automatikusan frissíti és a legújabb verzióhoz hivatkoztatja a csomagra hivatkozó összes feladatütemezést.  

> [!NOTE]  
>  Mielőtt a Configuration Manager-ügyfél futtatja a feladatütemezést, az ügyfél ellenőrzi a lehetséges függőségeket és az azok elérhetőségét egy terjesztési ponton az összes feladatütemezés. Ha a kliensgép egy törölt objektumot talál, amelytől a feladatütemezés függ, a kliensgép hibaüzenetet küld, és nem futtatja le a feladatütemezést.  

###  <a name="BKMK_RunProgram"></a> Program futtatása a feladatütemezés előtt  
 Kiválaszthatja a program, amely futtatja a feladatütemezés futtatása előtt. Adjon meg egy programot, melyet futtatni kíván, nyissa meg a **tulajdonságok** párbeszédpanelt, amely a feladatütemezés, és válassza ki a **speciális** lapot a következő beállítások megadásához:  

> [!IMPORTANT]  
>  Program futtatása előtt a feladatütemezés futtatása, a feladat összes tartalom és a program elérhetőnek kell lennie egy csomagmegosztásban, a csomag. A csomagmegosztást a csomag tulajdonságai között, az **Adatelérés** lapon állíthatja be.  

-   **Egy másik programot futtasson először**: Adja meg, hogy egy másik program futtatása a feladatütemezés futtatása előtt.  

    > [!IMPORTANT]  
    >  Ez a beállítás csak a teljes operációs rendszerben futó feladatütemezésekre vonatkozik. A Configuration Manager figyelmen kívül hagyja ezt a beállítást, ha a feladatütemezést PXE vagy rendszerindító adathordozó használatával indította.  

-   **Csomag**: Adja meg a programot tartalmazó csomagot.  

-   **Program**: Adja meg a program futtatásához.  

-   **A program először mindig futtassa**: Adja meg, hogy a program futtatására, minden alkalommal, amikor futtatja a feladatütemezést az adott ügyfélen a Configuration Manager. Alapértelmezés szerint a program sikeres futtatása után a rendszer nem futtatja le újra, ha a feladatütemezést ismét lefuttatják ugyanazon a kliensgépen.  

 Ha nem sikerül futtatni a kijelölt programot egy kliensgépen, a feladatütemezés sem indul.  

##  <a name="BKMK_TSMaintenanceWindow"></a> Feladatütemezés futtatási idejének meghatározása karbantartási időszak megadásával  
 Megadhatja, ha a feladatütemezés futtatásának meghatározhat egy karbantartási időszakot a célszámítógépeket tartalmazó gyűjtemény. A karbantartási időszakok a kezdés és a befejezés dátumával és időpontjával, valamint az ismétlődésük beállításával vannak konfigurálva. Ezenkívül a karbantartási időszak ütemezésének beállításakor azt is megadhatja, hogy a karbantartási időszak csak feladatütemezésekre legyen érvényes. További információkért lásd: [karbantartási időszakok használata](../../core/clients/manage/collections/use-maintenance-windows.md).  

> [!IMPORTANT]  
>  Ha karbantartási időszakot állít be egy feladatütemezéshez, az akkor is fut tovább, ha a karbantartási időszak véget ér. A feladatütemezés futtatása lehet sikeres és sikertelen.  

##  <a name="BKMK_TSNetworkAccessAccount"></a> Feladatütemezések és a hálózatelérési fiók  
 Habár a Feladatütemezések futtatása csak a helyi rendszerfiók környezetében, szükség lehet a hálózatelérési fiók konfigurálásáról a következő esetekben:  

-   Megfelelően konfigurálni kell a hálózatelérési fiókot, vagy a feladatütemezés sikertelen lesz, ha próbál meg hozzáférni a Configuration Manager-csomagokat a terjesztési pontokon a feladat végrehajtásához. A hálózati elérésre szolgáló fiókot kapcsolatos további információkért lásd: [hálózatelérési fiók](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#a-namebkmknaaa-network-access-account).  

    > [!NOTE]  
    >  A hálózatelérési fiókot soha nem lesz a biztonsági környezetben futó programok, az alkalmazás telepítését, a frissítések telepítése vagy a feladatütemezések futtatására azonban a hálózati elérésre szolgáló fiókot a hálózaton a kapcsolódó erőforrások elérésére szolgál.  

-   Ha rendszerindító lemezképet használ egy operációs rendszer központi telepítésének indítására, a Configuration Manager használ a Windows PE környezetben, ami nem minősül teljes operációs rendszernek. A Windows PE környezet automatikusan generált, véletlenszerű nevet használ, amely nem tagja egyetlen tartománynak sem. Ha nem megfelelően állítja be a hálózatelérési fiókot, a számítógép nincs a feladatütemezés befejezéséhez szükséges Configuration Manager-csomagokban eléréséhez szükséges engedélyekkel.  

##  <a name="BKMK_TSCreateMedia"></a> Adathordozó létrehozása feladatütemezésekhez  
 Feladatütemezések és a kapcsolódó fájlokat és függőségeket számos különböző típusú adathordozók írhat. Használhat például DVD- vagy CD-készletet, USB flash meghajtót médiarögzítésű, különálló vagy rendszerindító adathordozóként, vagy kiírhat egy Windows Imaging Format (WIM) fájlt egy előkészített adathordozóra.  

 A következő típusú adathordozókat hozhat létre:  

-   **Média rögzítése**. Adathordozó rögzíti az operációs rendszer lemezképének, amely a Configuration Manager infrastruktúrájának alkalmazáson kívül létrehozott és konfigurált. A médiarögzítésű adathordozó testre szabott programokat tartalmazhat, melyek egy feladatütemezés futtatása előtt futtathatók. A testre szabott program együttműködik az asztallal, kérni a felhasználótól a szükséges értékeket, vagy hozzon létre a feladatütemezésben használt változókat.  

     További információkért lásd: [médiarögzítésű adathordozó létrehozása](../deploy-use/create-capture-media.md).  

-   **Különálló adathordozó**. A különálló adathordozók egyaránt tartalmazzák a feladatütemezést és az összes kapcsolódó objektumot, melyek szükségesek a feladatütemezés futtatásához. Különálló adathordozó feladat sorozatok futtathatja, ha a Configuration Manager korlátozott vagy nem csatlakozik a hálózathoz. Különálló adathordozó is futtatható a következő módon:  

    -   Ha a célszámítógép nem indult, a Windows PE-lemezképhez társított a feladatütemezés különálló adathordozóról szolgál, és indítja a feladatütemezést.  

    -   A különálló adathordozók manuálisan is indíthatók, ha a felhasználó bejelentkezik a a hálózaton, és elindítja a telepítést.  

    > [!IMPORTANT]  
    >  A lépéseket a feladatütemezés különálló adathordozóról futtatható anélkül, hogy minden minden az adatok lekérdezése a hálózati; képesnek kell lennie. Ellenkező esetben a feladatütemezési lépés, amely megkísérli az adatok beolvasása sikertelen. Például egy feladatütemezési lépés csomagot egy terjesztési pontot igénylő sikertelen; azonban ha a szükséges csomag megtalálható a különálló adathordozót, a feladatütemezési lépés sikeres lesz.  

     További információkért lásd: [különálló adathordozó létrehozása](../deploy-use/create-stand-alone-media.md).  

-   **Rendszerindító adathordozó**. Rendszerindító adathordozók tartalmazzák a szükséges fájlokat, és a célszámítógép indításához, hogy a Configuration Manager infrastruktúrához csatlakozva meghatározhatják, mely Feladatütemezések futtatása alapján tagság gyűjteményhez csatlakozhat. A feladatütemezés és a függőségi viszonyban lévő objektumok nem találhatók meg az adathordozón; Ehelyett azok kapott a hálózaton keresztül a Configuration Manager-ügyfél. Ez a módszer új számítógép-vagy operációs rendszer nélküli telepítések, vagy ha nem a Configuration Manager-ügyfél vagy operációs rendszer a célszámítógépen.  

     További információkért lásd: [létrehozásának folyamatáról](../deploy-use/create-bootable-media.md).  

-   **A manuálisan előkészített adathordozó**. Az előkészített adathordozókkal olyan célszámítógépekre telepíthetők operációs rendszeri lemezképek, melyek nem lettek előkészítve. Az előkészített adathordozók olyan Windows Imaging Format (WIM) fájl, amely egy operációs rendszer nélküli számítógépre is telepíthető, amelyiket a gyártó, illetve a Configuration Manager környezethez nem csatlakoztatott vállalati előkészítő központ tárolja.  

     További információkért lásd: [hozza létre a manuálisan előkészített adathordozó](../deploy-use/create-prestaged-media.md).  

 Adathordozó létrehozásakor adjon meg egy jelszót az adathordozó a az adathordozón található fájlokhoz való hozzáférés vezérlése érdekében. Ha jelszót ad meg, a felhasználó kell írnia a jelszót a célszámítógépen, a feladatütemezés futtatásakor.  

 Ha egy feladatütemezés adathordozó használatával futtatja, a megadott számítógépen található chiparchitektúra az adathordozó nem ismerhető fel, és a feladatütemezés megkísérli futtatni az akkor is, ha a megadott architektúra nem egyezik meg a célszámítógépen ténylegesen telepített. Ha az adathordozón található chiparchitektúra nem egyezik meg a célszámítógépen telepített acrhitektúrával, a telepítés sikertelen lesz.  

 Operációs rendszerek központi telepítése adathordozó használatával kapcsolatos további információkért lásd: [feladatütemezési média létrehozása](../deploy-use/create-task-sequence-media.md).  

