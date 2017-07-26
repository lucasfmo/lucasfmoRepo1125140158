---

title: "Telepítse és konfigurálja a szoftverfrissítési pont |} Microsoft Docs"
description: "Elsődleges helyek a központi adminisztrációs helyen lévő szoftverfrissítési pont a szoftverfrissítés megfelelőségi vizsgálata, és a központi telepítés frissítéseit az ügyfelekre."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b099a645-6434-498f-a408-1d438e394396
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 1d9911274fd76942131054231cdcc2bcebbd3fcb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---


# <a name="install-and-configure-a-software-update-point"></a>Telepítse és konfigurálja a szoftverfrissítési pont  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


> [!IMPORTANT]  
>  A szoftverfrissítési pont helyrendszerszerepkör telepítése előtt ellenőriznie kell, hogy a kiszolgáló teljesíti-e az előírt függőségeket, és meg kell határoznia a szoftverfrissítési pont infrastruktúráját. További információ a szoftverfrissítések tervezéséről és a szoftverfrissítési pont infrastruktúrájának meghatározásáról, lásd: [szoftverfrissítések tervezése](../plan-design/plan-for-software-updates.md).  

 A szoftverfrissítési pontot előírás szerint a központi felügyeleti helyen és az elsődleges helyeken kell telepíteni, hogy engedélyezhető legyen a szoftverfrissítés megfelelőségi vizsgálata, és központilag telepíthetők legyenek a szoftverfrissítések az ügyfélgépekre. Másodlagos helyeken a szoftverfrissítési pont telepítése nem kötelező. A szoftverfrissítési pont helyrendszerszerepkört olyan kiszolgálón kell létrehozni, amelyen a WSUS már telepítve van. A szoftverfrissítési pont együttműködik a WSUS szolgáltatásaival a szoftverfrissítés beállításainak konfigurálásakor és a szoftverfrissítések metaadatainak szinkronizálásakor. Ha a Configuration Manager-hierarchiában, először telepítse és konfigurálja a szoftverfrissítési pont a központi adminisztrációs helyen, majd az alárendelt elsődleges helyeken, és végül szükség esetén a másodlagos helyeken. Ha központi felügyeleti hely helyett önálló elsődleges hellyel rendelkezik, először az elsődleges helyen telepítse és konfigurálja a szoftverfrissítési pontot, majd választható módon a másodlagos helyeken. Egyes beállítások csak akkor érhetők el, ha a szoftverfrissítési pontot a legfelső szintű helyen konfigurálja. Különböző beállításokat kell megfontolnia attól függően, hogy hol telepítette a szoftverfrissítési pontot.  

> [!IMPORTANT]  
>  Egy helyen több szoftverfrissítési pontot is telepíthet. Az elsőként telepített szoftverfrissítési pont a szinkronizálás forrásaként lesz konfigurálva, és ez fogja szinkronizálni a Microsoft Update webhelyről vagy a felsőbb rétegbeli frissítési forrásból származó frissítéseket. A helyen telepített további szoftverfrissítési pontok az első szoftverfrissítési pont replikájaként lesznek konfigurálva. Ezért ezeknél bizonyos beállítások nem lesznek elérhetők a kezdeti szoftverfrissítési pont telepítése és konfigurálása után.  

 A szoftverfrissítési pont helyrendszerszerepkört hozzáadhatja meglévő helyrendszer-kiszolgálóhoz, vagy létrehozhat új kiszolgálót. Attól függően, hogy a helyrendszerszerepkört új vagy meglévő kiszolgálóra veszi-e fel, a **Helyrendszer-kiszolgáló létrehozása varázsló** vagy a **Helyrendszerszerepkörök hozzáadása varázsló** **Rendszerszerepkör kiválasztása** oldalán jelölje ki a **Szoftverfrissítési pont**elemet, majd a varázslóban adja meg a szoftverfrissítési pont beállításait. A beállítások a Configuration Manager használt verziójától függően eltérőek. Helyrendszer-szerepkörök telepítésével kapcsolatos további információkért lásd: [helyrendszerszerepkörök telepítése](../../core/servers/deploy/configure/install-site-system-roles.md).  

 A következő szakaszok a szoftverfrissítési pont beállításait ismerteti az egyes helyeken.  

## <a name="proxy-server-settings"></a>Proxykiszolgáló beállításai  
 A proxykiszolgáló beállításait konfigurálhatja a különböző oldalain a **helyrendszer-kiszolgáló létrehozása varázsló** vagy **helyrendszer-szerepkörök hozzáadása varázslóval** a Configuration Manager használt verziójától függően.  

-   Konfigurálnia kell a proxykiszolgálót, majd meg kell adnia, hogy mikor kívánja használni a proxykiszolgálót a szoftverfrissítéseknél. Adja meg a következő beállításokat:  

    -   Konfigurálja a proxykiszolgáló beállításait a varázsló **Proxy** oldalán vagy a Helyrendszer tulajdonságai párbeszédpanel **Proxy** lapján. A proxykiszolgáló beállításai a teljes helyrendszerre vonatkoznak, azaz az összes helyrendszerszerepkör az itt megadott beállításokat használja.  

    -   Adja meg, hogy használni a proxykiszolgálót, amikor a Configuration Manager szinkronizálja a szoftverfrissítési a frissítések, és amikor tartalmat tölt le automatikus központi telepítési szabály használatával. Adja meg a szoftverfrissítési pont proxykiszolgálójának beállításait a varázsló **Proxy- és fiókbeállítások** oldalán vagy a Szoftverfrissítési pont tulajdonságai párbeszédpanel **Proxy- és fiókbeállítások** lapján.  

        > [!NOTE]  
        >  A **Proxykiszolgáló használata tartalom automatikus központi telepítési szabályokkal történő letöltésekor** beállítás elérhető, de nem használatos másodlagos helyen lévő szoftverfrissítési pontnál. Csak a központi felügyeleti helyen és elsődleges helyen lévő szoftverfrissítési pont tölt le tartalmat a Microsoft Update webhelyről.  

> [!IMPORTANT]  
>  Alapértelmezés szerint az automatikus központi telepítési szabály létrehozási kiszolgálójához tartozó **Helyi rendszer** fiókot használja a rendszer az internetre való csatlakozáshoz és szoftverfrissítések letöltéséhez az automatikus központi telepítési szabály futtatásakor. Ez a fiók nem rendelkezik Internet-hozzáférést, ha szoftverfrissítések letöltése sikertelen lesz, és a következő bejegyzés kerül a ruleengine.log naplófájlba: **Nem sikerült a frissítés letöltése az internetről. Hiba = 12007**. Adja meg a proxykiszolgálóhoz tartozó hitelesítő adatokat, ha a Helyi rendszer fiók nem rendelkezik interneteléréssel.  


## <a name="wsus-settings"></a>A WSUS beállításai  
 A WSUS beállításai különböző oldalain kell konfigurálnia a **helyrendszer-kiszolgáló létrehozása varázsló** vagy **helyrendszer-szerepkörök hozzáadása varázslóval** attól függően, hogy a Configuration Manager használt, és egyes esetekben a verzió csak a szoftver tulajdonságai között található frissítése a pont, más néven a szoftverfrissítési pont összetevő tulajdonságai. A következő szakaszok a WSUS beállításainak konfigurálását ismertetik.  

### <a name="BKMK_wsusport"></a>A WSUS portbeállításait  
 A WSUS portbeállításait a varázsló Szoftverfrissítési pont oldalán vagy a szoftverfrissítési pont tulajdonságainál kell megadnia. A következő eljárással határozhatja meg a WSUS szolgáltatás által használt portbeállításokat.  

#### <a name="to-determine-the-port-settings-used-in-iis"></a>Az IIS szolgáltatásban használt portbeállítások meghatározása  

 1.  Nyissa meg a WSUS-kiszolgálón az Internet Information Services (IIS) kezelőjét.  

 2.  Bontsa ki a **Webhelyek**csomópontot, kattintson a jobb gombbal a WSUS-kiszolgálóhoz tartozó webhelyre, és kattintson a **Kötések szerkesztése**pontra. A Webhely kötései párbeszédpanelen a **Port** oszlopban jelennek meg a HTTP- és HTTPS-portok értékei.


### <a name="configure-ssl-communications-to-wsus"></a>SSL kommunikáció konfigurálása a WSUS szolgáltatásához  
 Az SSL kommunikáció konfigurálását a varázsló **Általános** oldalán vagy a szoftverfrissítési pont **Általános** lapján hajthatja végre.  

 További információ az SSL használatáról: [Be kell-e állítani az SSL használatát a WSUS szolgáltatásban?](../plan-design/plan-for-software-updates.md#BKMK_WSUSandSSL).  

### <a name="wsus-server-connection-account"></a>WSUS-kiszolgáló csatlakozási fiókja  
 Fiókot konfigurálhat, amelyet a helykiszolgáló a szoftverfrissítési ponton futó WSUS szolgáltatáshoz való csatlakozáskor használ. Ha nem konfigurálja ezt a fiókot, a Configuration Manager használ a helykiszolgáló számítógépfiókja művelethez. A WSUS kiszolgálói kapcsolat fiókját a varázsló **Proxy- és fiókbeállítások** oldalán vagy a Szoftverfrissítési pont tulajdonságai párbeszédpanel **Proxy- és fiókbeállítások** lapján konfigurálja.  A fiók konfigurálható attól függően, hogy a Configuration Manager verziója, amelyekkel a varázsló különböző helyein.  

 A Configuration Manager fiókokkal kapcsolatos további információkért lásd: [a System Center Configuration Managerben használt fiókok](../../core/plan-design/hierarchy/accounts.md).  

## <a name="synchronization-source"></a>Szinkronizálási forrás  
 A fölérendelt szinkronizálási forrás a szoftverfrissítések szinkronizálásához a varázsló **Szinkronizálási forrás** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Szinkronizálási beállítások** lapján konfigurálható. A szinkronizálási forráshoz rendelkezésre álló lehetőségek köre a helytől függ.  

 Az alábbi táblázatban láthatók a hely szoftverfrissítési pontjának konfigurálásakor elérhető beállítások.  

|Hely|A szinkronizálási forráshoz elérhető beállítások|  
|----------|----------------------------------------------|  
|-...Központi adminisztrációs hely<br />-...Önálló elsődleges hely|-...Szinkronizálás a Microsoft Update webhelyről<br />-...Szinkronizálás fölérendelt adatforrásról<br />-...Ne szinkronizáljon a Microsoft Update webhelyről vagy a fölérendelt adatforrásról|  
|-...További szoftverfrissítési pontok egy helyen<br />-...Gyermek elsődleges hely<br />-...Másodlagos hely|-...Szinkronizálás fölérendelt adatforrásról|  

 Az alábbi lista további információt nyújt a szinkronizálási forrásként használható lehetőségekről:  

-   **Szinkronizálás a Microsoft Update webhelyről**: Ez a beállítás segítségével szinkronizálhatók a szoftverfrissítések metaadatai a Microsoft Update szolgáltatásból. A központi adminisztrációs helynek kapcsolódnia kell az internethez, ellenkező esetben a szinkronizálás sikertelen lesz. Ez a beállítás csak akkor érhető el, ha a szoftverfrissítési pontot a legfelső szintű helyen konfigurálja.  

    > [!NOTE]  
    >  Ha a szoftverfrissítési pont és az internet között tűzfal található, elképzelhető, hogy a tűzfalon be kell állítani a WSUS-webhelyhez használt HTTP- és HTTPS-portok fogadását. A tűzfalon emellett a tartományokhoz való hozzáférés is korlátozható. A szoftverfrissítéseket támogató tűzfalak tervezését a [Tűzfalak konfigurálása](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls) című szakasz ismerteti részletesen.  

-   **Szinkronizálás fölérendelt adatforrásról**: Ez a beállítás segítségével szinkronizálhatók a szoftverfrissítések metaadatai a fölérendelt szinkronizálási forrásról. A gyermek elsődleges és másodlagos helyek esetén a rendszer automatikusan a szülőhely URL-jét alkalmazza ennél a beállításnál. A szoftverfrissítések meglévő WSUS-kiszolgálóról is szinkronizálhatók. ehhez adjon meg egy URL-t, például: https://WSUSServer:8531, ahol a 8531-es szám a WSUS-kiszolgálóhoz való kapcsolódáshoz használt portot jelöli.  

-   **Ne szinkronizáljon a Microsoft Update vagy a fölérendelt adatforrásról**: Ez a beállítás segítségével manuálisan szinkronizálja a szoftverfrissítéseket, ha a legfelső szintű helyen a szoftverfrissítési pont nem kapcsolódik az internethez. Erről bővebben lásd: [Szoftverfrissítések szinkronizálása leválasztott szoftverfrissítési pontról](synchronize-software-updates-disconnected.md).  

> [!NOTE]  
>  Ha a szoftverfrissítési pont és az internet között tűzfal található, elképzelhető, hogy a tűzfalon be kell állítani a WSUS-webhelyhez használt HTTP- és HTTPS-portok fogadását. A tűzfalon emellett a tartományokhoz való hozzáférés is korlátozható. A szoftverfrissítéseket támogató tűzfalak tervezését a [Tűzfalak konfigurálása](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls) című szakasz ismerteti részletesen.  

 A WSUS jelentési események létrehozása a varázsló **Szinkronizálási forrás** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Szinkronizálási beállítások** lapján konfigurálható. A Configuration Manager nem használja ezeket az eseményeket; ezért általában fogja választani az alapértelmezett beállítás **ne hozzon létre WSUS jelentési események**.  

## <a name="synchronization-schedule"></a>Szinkronizálás ütemezése  
 A szinkronizálás ütemezése a varázsló **Szinkronizálás ütemezése** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen konfigurálható. A rendszer csak a legfelső szintű helyen lévő szoftverfrissítési ponton konfigurálja ezt a beállítást.  

 Ha engedélyezi az ütemezést, egyszerű ismétlődő vagy egyéni szinkronizálási ütemezést konfigurálhat. Ha egyszerű ütemezést állít be, a kezdési időpont időpontjában, amikor az ütemezés létrehozása a Configuration Manager konzolt futtató számítógép helyi idején alapul. Egyéni ütemezések kezdő időpontja konfigurálásakor, a Configuration Manager konzolt futtató számítógép helyi idején a alapul.  

> [!TIP]  
>  A környezetének megfelelő időpontokra ütemezze a szoftverfrissítések kívánt szinkronizálását. Egy lehetséges megoldás például, ha a szoftverfrissítések szinkronizálásának időpontját röviddel a Microsoft rendszeres biztonsági frissítései után ütemezi, amelyek minden hónap második keddjén jelennek meg („Frissítő kedd”). Jellemző még például az is, hogy a szoftverfrissítések szinkronizálását napi rendszerességgel ütemezik arra az időpontra, amikor a szoftverfrissítésekkel eljuttatják az ügyfelekre az Endpoint Protection definíció- és keresőmotor-frissítéseit.  

> [!NOTE]  
>  Ha úgy dönt, hogy nem szeretné ütemezni a szoftverfrissítések szinkronizálását, a Szoftverkönyvtár munkaterület **Minden szoftverfrissítés** vagy **Szoftverfrissítési csoportok** csomópontjából manuálisan is szinkronizálhatja a szoftverfrissítéseket. További információkért lásd: [szinkronizálhatók a szoftverfrissítések](synchronize-software-updates.md).  

## <a name="supersedence-rules"></a>Helyettesítési szabályok  
 A helyettesítési beállítások a varázsló **Helyettesítési szabályok** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Helyettesítési szabályok** lapján konfigurálhatók. A helyettesítési szabályok konfigurálása csak a legfelső szintű helyen lehetséges.  

 Ezen az oldalon beállíthatja, hogy a felülírt (helyettesített) szoftverfrissítések azonnal lejárjanak – ebben az esetben a rendszer megakadályozza elhelyezésüket az új központi telepítésekben, a meglévő központi telepítéseknél pedig jelzi, hogy a felülírt szoftverfrissítések legalább egy lejárt szoftverfrissítést tartalmaznak. Ehelyett ugyanakkor beállíthatja azt is, hogy a felülírt szoftverfrissítések csak adott idő elteltével járjanak le, így továbbra is telepítheti őket központilag. További információkért lásd: [Helyettesítési szabályok](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

> [!NOTE]  
>  A varázsló **Helyettesítési szabályok** lapja csak a hely első szoftverfrissítési pontjának konfigurálásakor érhető el. Ez a lap további szoftverfrissítési pontok telepítésekor nem jelenik meg.  

## <a name="classifications"></a>Besorolások  
 A besorolási beállítások a varázsló **Besorolások** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Besorolások** lapján konfigurálhatók. További információ a szoftverfrissítések besorolásáról: [Frissítési besorolások](../plan-design/plan-for-software-updates.md#BKMK_UpdateClassifications).  

> [!NOTE]  
>  A varázsló **Besorolások** lapja csak a hely első szoftverfrissítési pontjának konfigurálásakor érhető el. Ez a lap további szoftverfrissítési pontok telepítésekor nem jelenik meg.  

> [!TIP]  
>  Ha először telepíti a szoftverfrissítési pontot a legfelső szintű helyen, törölje az összes szoftverfrissítési besorolást. A szoftverfrissítések kezdeti szinkronizálását követően egy frissített listából konfigurálja a besorolásokat, majd indítsa el újra a szinkronizálást. A rendszer csak a legfelső szintű helyen lévő szoftverfrissítési ponton konfigurálja ezt a beállítást.  

## <a name="products"></a>Termékek  
 A termékbeállítások a varázsló **Termékek** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Termékek** lapján adhatók meg.  

> [!NOTE]  
>  A varázsló **Termékek** lapja csak a hely első szoftverfrissítési pontjának konfigurálásakor érhető el. Ez a lap további szoftverfrissítési pontok telepítésekor nem jelenik meg.  

> [!TIP]  
>  Ha először telepíti a szoftverfrissítési pontot a legfelső szintű helyen, törölje az összes terméket. A szoftverfrissítések kezdeti szinkronizálását követően egy frissített listából konfigurálja a termékeket, majd indítsa el újra a szinkronizálást. A rendszer csak a legfelső szintű helyen lévő szoftverfrissítési ponton konfigurálja ezt a beállítást.  

## <a name="languages"></a>Nyelvek  
 A nyelvi beállítások a varázsló **Nyelvek** lapján vagy a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Nyelvek** lapján konfigurálhatók. Adja meg, hogy mely nyelvek esetén szeretné szinkronizálni a szoftverfrissítési fájlokat és az összefoglaló információkat. A **szoftverfrissítési fájl** beállítás konfigurálni kell a Configuration Manager-hierarchia minden szoftverfrissítési pontjánál. Az **Összefoglaló információk** beállításainak konfigurálása csak a legfelső szintű szoftverfrissítési ponton lehetséges. További információkért lásd: [Nyelvek](../plan-design/plan-for-software-updates.md#BKMK_UpdateLanguages).  

> [!NOTE]  
>  A varázsló **Nyelvek** lapja csak a szoftverfrissítési pont központi adminisztrációs helyen történő telepítése esetén érhető el. A gyermekhelyeknél a szoftverfrissítési fájlok nyelvei a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel **Nyelvek** lapján konfigurálhatók.  

## <a name="next-steps"></a>További lépések
A Configuration Manager-hierarchia legfelső szintjén kezdve a szoftverfrissítési pont telepítése. Ismételje meg a eljárások ebben a témakörben az alárendelt helyeken a szoftverfrissítési pont telepítése.

Ha elvégezte a szoftverfrissítési pontokon frissítéséhez lépjen [szinkronizálhatók a szoftverfrissítések](synchronize-software-updates.md).

