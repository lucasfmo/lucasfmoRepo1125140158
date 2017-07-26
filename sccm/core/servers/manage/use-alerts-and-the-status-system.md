---
title: "Riasztások és az állapotrendszer |} Microsoft Docs"
description: "Riasztások konfigurálása, és az állapotrendszer használatával tájékozódhat a Configuration Manager központi telepítésének állapotát."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7341cc6e-9e08-41e4-bcc6-6c1ff12e85ca
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: ed692bdea055775890535d2666f09ba5f5c7c4e1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-alerts-and-the-status-system-for-system-center-configuration-manager"></a>A riasztások és az állapotrendszer használata a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Riasztások konfigurálása, és a beépített Állapotrendszer használatával tájékozódhat a System Center Configuration Manager központi telepítésének állapotát.  


##  <a name="bkmk_Status"></a> Állapotrendszer  
 A fő helyösszetevők használata során a rendszer állapotüzeneteket hoz létre, amelyek tájékoztatnak a hely és a hierarchia műveleteiről.    Az üzenetek értesítik a különböző helyeken végbemenő folyamatok állapotáról. A riasztási rendszer beállításával figyelmen kívül hagyja az ismert problémákból fakadó értesítéseket, és könnyebben észlelheti a fontos problémákat.  

 Alapértelmezés szerint a Configuration Manager állapotrendszer konfigurálás nélkül, amelyek a legtöbb környezetben megfelelő beállításokkal. Ugyanakkor lehetőség van a következő beállítások konfigurálására:  

-   **Állapotösszegzők:** Módosíthatja az állapotjelző állapotüzenetek gyakoriságát az egyes helyeken összefoglalóknak módosítása a következő négyféle összegző állapotát:  

    -   Alkalmazás-központitelepítés összegző  

    -   Alkalmazásstatisztika-összegző  

    -   Összetevőállapot-összegző  

    -   Helyrendszer-állapotösszegző  

-   **Állapotszűrő szabályok:** Akkor is új Állapotszűrő szabályok létrehozására, a szabályok prioritásának módosítására, tiltsa le a szabályok engedélyezése, illetve az egyes helyeken nem használt szabályok törlésére.  

    > [!NOTE]  
    >  Az állapotszűrő-szabályok nem támogatják a környezeti változók használatát a külső parancsok futtatásához.  

-   **Állapotjelentés:** Beállíthatja a kiszolgáló- és ügyfélösszetevőkre vonatkozó jelentések beállításával módosíthatja, miként állapotüzenetek jelentik a rendszer a Configuration Manager állapotát, és adja meg, ahol állapotüzeneteket küldeni.  

    > [!WARNING]  
    >  Mivel az alapértelmezett jelentéskészítési beállítások a legtöbb környezet esetében megfelelőek, legyen körültekintő, ha módosítja őket. Növelésével feldolgozása az összes részletes állapot növelheti a kell állapotüzenetek mennyiségét jelentés megadásával állapotjelentések szintjét, amely a Configuration Manager-hely feldolgozási terhelését növeli. Ha csökkenti az állapotjelnetések szintjét, azzal az állapotösszegzők hasznosságát korlátozhatja.  

Mivel az állapotrendszer minden hely esetében külön konfigurációt készít, a helyeket csak egyenként szerkesztheti.  

###  <a name="bkmk_configstatus"></a> Az állapotrendszer konfigurálásának eljárásai  

##### <a name="to-configure-status-summarizers"></a>Az állapotösszegzők konfigurálása  

1.  A Configuration Manager konzolon lépjen a **felügyeleti** > **Helykonfiguráció** >**helyek**, majd válassza ki a helyet, amelynek szeretné az állapotrendszert konfigurálná.  

2.  A **Kezdőlap** **Beállítások** csoportjában kattintson az **Állapotösszefoglalók**elemre.  

3.  Az **Állapotösszefoglalók** párbeszédpanelen jelölje ki a konfigurálni kívánt állapotösszegzőt, majd az állapotösszegző tulajdonságainak megnyitásához kattintson a **Szerkesztés** elemre. Ha az Alkalmazástelepítést vagy az Alkalmazásstatisztika-összegzőt kívánja szerkeszteni, folytassa az 5. lépéssel. Ha az Összetevő állapotát kívánja szerkeszteni, folytassa a 6. lépéssel. Ha a Helyrendszer-állapotösszegzőt kívánja szerkeszteni, folytassa a 7. lépéssel.  

4.  Az alkalmazás-központitelepítés összegző vagy alkalmazásstatisztika-összegző tulajdonságlapjának megnyitása után hajtsa végre a következő lépéseket:  

    1.  Az összegzők tulajdonságlapjának **Általános** lapfülén konfigurálja az összegzési időközöket, majd a tulajdonságlap bezáráshoz kattintson az **OK** gombra.  

    2.  Az **Állapot-összefoglalók** párbeszédpanel bezárásához és az eljárás befejezéséhez kattintson az **OK** gombra.  

5.  Az összetevőállapot-összegző tulajdonságlapjának megnyitása után hajtsa végre a következő lépéseket:  

    1.  Az a **általános** az összegzők tulajdonságlapjának lapfülén konfigurálja a replikáció és küszöbidőszakok értékeit.  

    2.  A **Küszöbértékek** lapon válassza ki a konfigurálni kívánt **Üzenettípus** értékét, majd kattintson egy összetevő nevére a **Küszöbértékek** listában.  

    3.  Az **Állapot küszöbértékének tulajdonságai** párbeszédpanelen szerkessze a figyelmeztetési és a kritikus küszöbértékeket, majd kattintson az **OK**gombra.  

    4.  Igény szerint ismételje meg a 6.b és a 6.c lépést, és amikor elkészült, az összegző tulajdonságainak bezárásához kattintson az **OK** gombra.  

    5.  Az **Állapot-összefoglalók** párbeszédpanel bezárásához és az eljárás befejezéséhez kattintson az **OK** gombra.  

6.  A helyrendszer-állapotösszegző tulajdonságlapjának megnyitása után hajtsa végre a következő lépéseket:  

    1.  Az a **általános** az összegzők tulajdonságlapjának lapfülén konfigurálja a replikáció és az ütemezés értékeit.  

    2.  A **Küszöbértékek** lapon az **Alapértelmezett küszöbértékek** megadásával konfigurálja a kritikus és a figyelmeztető állapot megjelenítésére vonatkozó alapértelmezett küszöbértékeket.  

    3.  A konkrét **Tárolóobjektum**elemek értékeinek szerkesztéséhez jelölje ki az objektumot a **Megadott küszöbértékek:** listában, majd kattintson a **Tulajdonságok** gombra a tárolóobjektumokra vonatkozó figyelmeztetési és a kritikus küszöbértékek eléréséhez és szerkesztéséhez. A tárolóobjektum tulajdonságlapjának bezárásához kattintson az **OK** gombra.  

    4.  Új tárolóobjektum létrehozásához kattintson az **Objektum létrehozása** gombra, és adja meg a tárolóobjektumra vonatkozó értékeket. Az objektum tulajdonságlapjának bezárásához kattintson az **OK** gombra.  

    5.  Tárolóobjektum törléséhez jelölje ki az objektumot, majd kattintson a **Törlés** gombra.  

    6.  Ismételje meg igény szerint a 7.b–7.e lépéseket szükség esetén. Amikor elkészült, kattintson az **OK** gombra az összegző tulajdonságainak bezárásához.  

    7.  Az **Állapot-összefoglalók** párbeszédpanel bezárásához és az eljárás befejezéséhez kattintson az **OK** gombra.  

##### <a name="to-create-a-status-filter-rule"></a>Állapotszűrő szabály létrehozása  

1.  A Configuration Manager konzolon lépjen a **felügyeleti** > **Helykonfiguráció** >**helyek**, majd válassza ki a helyet, ahol az állapotrendszert konfigurálásához.  

2.  A **Kezdőlap** **Beállítások** csoportjában kattintson az **Állapotszűrő szabályok**elemre. Megnyílik az **Állapotszűrő szabályok** párbeszédpanel.  

3.  Kattintson a **Létrehozás**gombra.  

4.  Az **Állapotszűrési szabály létrehozása varázsló** **Általános** lapján adjon meg nevet az új állapotszűrő szabályhoz, adja meg a szabályhoz tartozó üzenetegyezési feltételeket, majd kattintson a **Tovább**gombra.  

5.  A **Műveletek** lapon adja meg azokat a műveleteket, amelyeket olyankor kell végrehajtani, amikor egy állapotüzenet megfelel a szűrőszabálynak, majd kattintson a **Tovább**gombra.  

6.  Az **Összefoglalás** lapon ellenőrizze az új szabály részleteit, majd fejezze be a varázslót.  

    > [!NOTE]  
    >  A Configuration Manager csak szükséges, hogy az új Állapotszűrő szabálynak a nevét. Ha a szabályt létrehozza, de nem ad meg semmilyen feltételt az állapotüzenetek feldolgozásához, az állapotszűrő szabály hatástalan lesz. Ez a viselkedés lehetővé teszi, hogy a szabályokat még az előtt létrehozza és rendszerezze, hogy az egyes szabályokhoz megadná a feltételeket.  

##### <a name="to-modify-or-delete-a-status-filter-rule"></a>Állapotszűrő szabály módosítása vagy törlése  

1.  A Configuration Manager konzolon lépjen a **felügyeleti** > **Helykonfiguráció** >**helyek**, majd válassza ki a helyet, ahol az állapotrendszert konfigurálásához.  

2.  A **Kezdőlap** **Beállítások** csoportjában kattintson az **Állapotszűrő szabályok**elemre.  

3.  Az **Állapotszűrő szabályok** párbeszédpanelen jelölje ki a módosítandó szabályt, majd hajtsa végre a megfelelő műveletet a következők közül:  

    -   A **Prioritás növelése** vagy a **Prioritás csökkentése** elemre kattintva módosíthatja az állapotszűrő szabály helyét a feldolgozási sorrendben. Ezt követően kiválaszthat egy újabb műveletet, vagy az eljárás 8. lépésével folytatva befejezheti a feladatot.  

    -   A szabály állapotának megváltoztatásához kattintson a **Letiltás** vagy az **Engedélyezés** elemre. A szabály állapotának módosítása után kiválaszthat egy újabb műveletet, vagy az eljárás 8. lépésével folytatva befejezheti a feladatot.  

    -   Kattintson a **Törlés** gombra, ha törölni szeretné a helyről az állapotszűrő szabályt, majd a művelet megerősítéséhez kattintson az **Igen** gombra. Szabály törlése után kiválaszthat egy újabb műveletet, vagy az eljárás 8. lépésével folytatva befejezheti a feladatot.  

    -   Kattintson a **Szerkesztés** gombra, ha módosítani szeretné az állapotüzenet-szabály feltételeit, és folytassa az eljárás 5. lépésével.  

4.  Az állapotszűrő szabály tulajdonságait tartalmazó párbeszédpanel **Általános** lapján módosíthatja a szabályt és az üzenetegyezési feltételeket.  

5.  A **Műveletek** lapon módosíthatja azokat a műveleteket, amelyeket olyankor kell végrehajtani, amikor egy állapotüzenet megfelel a szűrőszabálynak.  

6.  A változtatások mentéséhez kattintson az **OK** gombra.  

7.  Kattintson az **OK** gombra az **Állapotszűrő szabályok** párbeszédpanel bezárásához.  

##### <a name="to-configure-status-reporting"></a>Az állapotjelentések konfigurálása  

1.  A Configuration Manager konzolon lépjen a **felügyeleti** > **Helykonfiguráció** > **helyek**, majd válassza ki a helyet, ahol az állapotrendszert konfigurálásához.  

2.  A **Kezdőlap** **Beállítások** csoportjában kattintson a **Helyösszetevők konfigurálása**, majd az **Állapotjelentés**elemre.  

3.  Az **Összetevők tulajdonságának állapotjelentése** párbeszédpanelen adja meg azokat a kiszolgálói és ügyféloldali összetevőkre vonatkozó állapotüzeneteket, amelyeket szeretne a jelentésben vagy naplóban szerepeltetni:  

    1.  Konfigurálása **jelentés** állapotüzeneteket küldeni a Configuration Manager állapotüzenet-rendszerének.  

    2.  A **Napló** konfigurálásával az állapotüzenetek típusát és súlyosságát a Windows eseménynaplójába írhatja.  

4.  Kattintson az **OK**gombra.  

###  <a name="BKMK_MonitorSystemStatus"></a> Az állapotrendszer figyelése a Configuration Managerben  
 **A rendszerállapot** a Configuration Manager-helyek és a hely általános műveleteiről áttekintést nyújt a hierarchia helykiszolgálóinak műveleteiről. Feltárhatja a helyrendszer-kiszolgálók vagy az összetevők működési problémáit, és használhatja a rendszerállapot különböző Configuration Manager műveleteihez kívánt részletes adatok áttekintésére. Figyelheti a a **rendszerállapot** csomópontjának a **figyelés** munkaterület a Configuration Manager konzolon.  

 A legtöbb Configuration Manager helyrendszer-szerepkörök és összetevők előállít állapotüzeneteket. Az állapotüzenetek részletes adatai az egyes összetevők műveleti naplóiba kerülnek, de a rendszer elküldi ezeket a helyadatbázisba is, ahol összegzés után megjelennek az egyes összetevők vagy helyrendszerek általános állapotánál. Az állapotüzenetek ezen összesítései részletes adatokkal szolgálnak a szabályos műveletekről, a figyelmeztetésekről és a hibákról. Beállíthatja a figyelmeztetések és a hibák eseményindításának küszöbértékeit, és a rendszer finomhangolásával elérheti, hogy az összesített adatok figyelmen kívül hagyják az érdektelen, ismert problémákat, de jelezzék a további vizsgálatra érdemes tényleges problémákat a kiszolgálók vagy az összetevők működésében.  

 A rendszeradatok replikálása a hierarchia más helyeire helyadatként történik, nem globális adatként. Ez azt jelenti, hogy a hely, amelyhez a Configuration Manager konzol csatlakozik, és az alárendelt helyeknek hely alatti állapotát. Emiatt érdemes lehet a Configuration Manager konzol csatlakozik a hierarchia legfelső szintű helyén, a rendszerállapot megtekintésekor.  

 A következő táblázat a rendszerállapot különböző nézeteit ismerteti, és bemutatja, hogy mikor érdemes használni ezeket.  

|Csomópont|További információ|  
|----------|----------------------|  
|Hely állapota|Ezt a csomópontot használva megtekintheti az egyes helyrendszerek állapotának összesítését, és áttekintheti az egyes helyrendszer-kiszolgálók állapotát. A helyrendszer állapotát az egyes helyeknél a **helyrendszer állapotösszegzőjében**beállított küszöbértékek határozzák meg.<br /><br /> Megtekintheti az egyes helyrendszerekhez tartozó állapotüzeneteket, beállíthatja az állapotüzenetek küszöbértékeit, és a **Configuration Manager Service Manager**használatával kezelheti a helyrendszereken lévő összetevők műveleteit.|  
|Összetevő állapota|Ezt a csomópontot használva megtekintheti egy összegző és áttekintheti az összetevők működési állapotát minden egyes Configuration Manager összetevő állapota. Az összetevő állapotát az egyes helyeknél az **összetevőállapot-összegzőben**beállított küszöbértékek határozzák meg.<br /><br /> Megtekintheti az egyes összetevőkhöz tartozó állapotüzeneteket, beállíthatja az állapotüzenetek küszöbértékeit, és a **Configuration Manager Service Manager**használatával kezelheti az összetevők műveleteit.|  
|Ütköző rekordok|Ezt a csomópontot használva megtekintheti a vélhetőleg ütköző rekordokat tartalmazó ügyfelekre vonatkozó állapotüzeneteket.<br /><br /> A Configuration Manager a hardverazonosítók alapján megpróbálja azonosítani az ügyfeleket, előfordulhat, hogy ismétlődő, és figyelmeztet az ütköző rekordokra. Például ha újratelepít egy számítógépet, a Hardverazonosító változatlan marad, de a Configuration Manager által használt GUID megváltozhat.|  
|Állapotüzenet-lekérdezések|Ez a csomópontot használva lekérdezheti az adott eseményekhez tartozó állapotüzeneteket és a kapcsolódó részletes adatokat. Az állapotüzenet-lekérdezések segítségével megkeresheti az adott eseményekhez kapcsolódó állapotüzeneteket<br /><br /> Gyakran használhatja adott összetevő, művelet vagy Configuration Manager-objektum módosult azonosításához állapotüzenet-lekérdezések és a módosítás végrehajtásához használt fiók. Például futtathatja a **Létrehozott, módosított vagy törölt gyűjtemények** beépített lekérdezést adott gyűjtemény létrehozási időpontjának megállapításához, és a művelethez használt felhasználói fiók azonosításához.|  

####  <a name="bkmk_managestatus"></a> A hely állapotának és az összetevő állapotának felügyelete  
 Az alábbi ismertetés a hely állapotának és az összetevő állapotának kezeléséhez nyújt segítséget:  

-   Az állapotrendszerhez küszöbértékek konfigurálásáról lásd: [Az állapotrendszer konfigurálásának eljárásai](#bkmk_configstatus).  

-   A Configuration Manager alkalmazásban egyedi összetevők kezeléséhez használja a **Configuration Manager Service Manager**.  

####  <a name="bkmk_view"></a> Állapotüzenetek megtekintése  
 Megtekintheti egyedi helyrendszer-kiszolgálók és összetevők állapotüzeneteit.  

 A Configuration Manager konzol állapotüzenetek megtekintéséhez válassza ki a kívánt helyrendszer-kiszolgálót vagy összetevőt, és kattintson **üzenetek megjelenítése**. Az üzenetek megtekintésekor választhatja adott üzenettípusok vagy adott időtartamhoz tartozó üzenetek megjelenítését, valamint az eredményeket szűrheti az állapotüzenetek részletei alapján.  

##  <a name="bkmk_Alerts"></a> Riasztások  
 A Configuration Manager riasztást egyes műveletei által egy adott állapot akkor fordul elő.  

-   Erre legtöbbször a feltétlenül javítást igénylő hibák esetében kerül sor.  

-   A riasztások felhívhatják a figyelmet egy adott állapotra is, amelyet célszerű tovább figyelni.  

-   Néhány riasztást a rendszer automatikusan konfigurál, de az Endpoint Protection és az ügyfélállapot riasztásait például a felhasználónak kell beállítania.  

-   Az előfizetések esetében is állíthat be riasztásokat, amelyek e-mailben hívhatják fel a figyelmet a problémák fontos részleteire.  

 Használja a következő táblázatban található információ a riasztások és a riasztási előfizetések konfigurálása a Configuration Manager alkalmazásban:  


|Művelet|További információ|  
|------------|----------------------|  
|Az Endpoint Protection riasztásainak gyűjteményhez való beállítása|Lásd: **riasztások konfigurálása az Endpoint Protection a Configuration Manager** a [az Endpoint Protection konfigurálása a System Center Configuration Managerben](../../../protect/deploy-use/configure-endpoint-protection.md)|  
|Az ügyfélállapot riasztásainak gyűjteményhez való beállítása|Lásd: [ügyfélállapot konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-status.md).|  
|A Configuration Manager-riasztások kezelése|Lásd: e témakör [Management tasks for alerts](#BKMK_Manage) című szakasza.|  
|E-mail előfizetések konfigurálása riasztásokhoz|Lásd: e témakör [Management tasks for alerts](#BKMK_Manage) című szakasza.|  
|Riasztások figyelése|Lásd: e témakör [Riasztások figyelése](#BKMK_MonitorAlerts)|  

###  <a name="BKMK_Manage"></a> Management tasks for alerts  

##### <a name="to-manage-general-alerts"></a>Általános riasztások kezelése  

1.  A Configuration Manager konzolon lépjen a **figyelés** > **riasztások**, majd válassza ki a kezelési feladatot.  

  A következő táblázat használatával további információt kaphat azokról a kezelési feladatokról, amelyek kiválasztása előtt még tájékozódni szeretne.  

|Kezelési feladat|Részletek|  
    |---------------------|-------------|  
    |**A**|Megnyitja a  *&lt;riasztás neve*\>**tulajdonságok** párbeszédpanelt, ahol módosíthatja a nevét, súlyossági és a kijelölt riasztás vonatkozó küszöbértékeket. Ha módosítja a riasztás súlyossága, ez a konfiguráció hatással van a riasztások megjelenítésének a Configuration Manager konzolon.|  
    |**Megjegyzés szerkesztése**|Írjon be egy megjegyzést a kiválasztott riasztásokhoz. Ezek a Megjegyzések a Configuration Manager konzolon a riasztással együtt jelennek meg.|  
    |**Elhalasztás**|A megadott időpontig felfüggeszti a riasztás figyelését. A dátum lejártakor a riasztás állapota frissül.<br /><br /> Csak aktív állapotú riasztást halaszthat el.|  
    |**Előfizetés létrehozása**|Megnyitja az **Új előfizetés** párbeszédpanelt, ahol e-mail előfizetést hozhat létre a kiválasztott riasztáshoz.|  

##### <a name="to-configure-endpoint-protection-alerts-for-a-collection"></a>Endpoint Protection-riasztások konfigurálása gyűjteményhez  

1.  Függőben  

##### <a name="to-configure-client-status-alerts-for-a-collection"></a>Az ügyfélállapot riasztásainak gyűjteményhez való beállítása  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** >   **Eszközgyűjtemények**.  

2.  Válassza ki az **Eszközgyűjtemények** listában azt a gyűjteményt, amelyre vonatkozóan a riasztásokat konfigurálni szeretné, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

    > [!NOTE]  
    >  Felhasználógyűjteményekre vonatkozóan nem lehet riasztásokat konfigurálni.  

3.  A a **riasztások** lapján a  *&lt;gyűjteménynév*\>**tulajdonságok** párbeszédpanel, kattintson a **Hozzáadás**.  

    > [!NOTE]  
    >  A **Riasztások** lap csak akkor látható, ha a felhasználóhoz társított biztonsági szerepkör rendelkezik a riasztásokra vonatkozó engedélyekkel.  

4.  Az **Új gyűjteménnyel kapcsolatos riasztások hozzáadása** párbeszédpanelen válassza ki azokat a riasztásokat, amelyeket szeretne létrehozni, amennyiben az ügyfél állapot-küszöbértékei adott érték alá esnek, majd kattintson az **OK**gombra.  

5.  A **Riasztások** lap **Feltételek** listájában válassza ki egyenként az ügyfél állapotriasztásait, majd adja meg a következő információkat.  

    -   **Riasztás neve** – elfogadhatja az alapértelmezett nevet, vagy adjon meg egy új nevet a riasztáshoz.  

    -   **Riasztás súlyossága** – a legördülő listából válassza ki a riasztási szintet fog megjelenni a Configuration Manager konzolon.  

    -   **Riasztás** -adja meg a riasztásra vonatkozó százalékos küszöbérték.  

6.  Kattintson a **OK** bezárásához a  *&lt;gyűjteménynév*\>**tulajdonságok** párbeszédpanel megnyitásához.  

##### <a name="to-configure-email-notification-for-alerts"></a>A riasztásokhoz kapcsolódó e-mail értesítések beállítása  

1.  A Configuration Manager konzolon lépjen a **figyelés** > **riasztások** > **előfizetések**.  

2.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **E-mail értesítések konfigurálása**lehetőségre.  

3.  **Az e-mailes értesítő összetevő tulajdonságai** párbeszédpanelen adja meg a következő információkat:  

    -   **Riasztásokhoz kapcsolódó e-mail értesítések engedélyezése**: Válassza ezt a jelölőnégyzetet ahhoz, hogy a Configuration Manager SMTP-kiszolgáló segítségével küld e-mail riasztást.  

    -   **Teljesen minősített tartománynév vagy IP-címet az SMTP-kiszolgáló e-mailes riasztások küldéséhez**: A teljesen minősített tartománynevét (FQDN) vagy IP-cím és az SMTP-port megadása a riasztásokhoz használni kívánt e-mail kiszolgáló.  

    -   **SMTP-kiszolgáló csatlakozási fiókja**: Adja meg a hitelesítési módszert a Configuration Manager segítségével az e-mail kiszolgálóhoz csatlakozzon.  

    -   **Feladó címe az e-mailes riasztásokhoz**: Adja meg az e-mail cím, amely az értesítő e-mailek küldése történik.  

    -   **SMTP-kiszolgáló tesztelése**: Tesztelő e-mailt küld a megadott e-mail címre **feladó címe az e-mailes riasztásokhoz**.  

4.  Kattintson az **OK** gombra a beállítások mentéséhez és **Az e-mailes beállítások összetevő tulajdonságai** párbeszédpanel bezárásához.  

##### <a name="to-subscribe-to-email-alerts"></a>Az e-mailes riasztásokra való előfizetés  

1.  A Configuration Manager konzolon lépjen a **figyelés** > **riasztások**.  

2.  Válasszon egy riasztást, majd a **Kezdőlap** **Előfizetés** csoportjában kattintson az **Előfizetés létrehozása**lehetőségre.  

3.  Az **Új előfizetés** párbeszédpanelen adja meg a következő információkat:  

    -   **Nevét**: Adja meg az e-mail előfizetést azonosító nevet. Legfeljebb 255 karaktert használhat.  

    -   **E-mail cím**: Adja meg e-mail címét, amelyet a rendszer a riasztást küldje. Az e-mail címeket pontosvesszővel (;) választhatja el.  

    -   **E-mail nyelve**: A listában adja meg az e-mailek nyelvét.  

4.  Az **OK** gombra kattintva bezárja az **Új előfizetés** párbeszédpanelt, és létrehozza az e-mail előfizetést.  

    > [!NOTE]  
    >  Az előfizetések törléséhez és szerkesztéséhez a **Figyelés** munkaterületen bontsa ki a **Riasztások** csomópontot, majd kattintson az **Előfizetések** lehetőségre.  

###  <a name="BKMK_MonitorAlerts"></a> Riasztások figyelése  
 A riasztásokat a **Figyelés** munkaterület **Riasztások** csomópontján tekintheti meg. A riasztások a következő riasztási állapotok valamelyikével rendelkeznek:  

-   **Soha nem aktiválódott**: A riasztás feltétele nem teljesült.  

-   **Aktív**: A riasztás feltétele teljesült.  

-   **Visszavont**: Az aktív riasztás feltétele nem teljesül. Ez az állapot azt jelzi, hogy a riasztást kiváltó probléma megoldódott.  

-   **Elhalasztva**: Egy rendszergazda úgy konfigurálta a riasztás állapotának kiértékelésére később a Configuration Manager.  

-   **Letiltott**: A riasztás le van tiltva, egy rendszergazda felhasználónak. Ha a riasztás ebben az állapotban van, a Configuration Manager frissíti, még akkor is, ha megváltozik a riasztás állapota.  

 Az alábbi műveletek valamelyikét hajthatja végre, a Configuration Manager riasztást küld, ha:  

-   Megoldja a riasztást kiváltó problémát, ez például hálózati vagy konfigurálási probléma lehet. Miután a Configuration Manager azt észleli, hogy a probléma már nem létezik, a riasztás állapota változik **Mégse**.  

-   Ha a riasztás ismert probléma, adott időtartamra elhalaszthatja a riasztást. Idő lejárta után a Configuration Manager aktuális állapotára frissíti a riasztást.  

     Csak aktív állapotú riasztást halaszthat el.  

-   Szerkesztheti a riasztáshoz tartozó **Megjegyzés** mezőt, így a többi rendszergazda értesülhet arról, hogy észrevette a riasztást. Például megjegyzésként közölheti a probléma megoldásának módját, tájékoztatást adhat a feltétel aktuális állapotáról, vagy ismertetheti a riasztás elhalasztásának okát.  

