---
title: "Konfigurálja a felderítést |} Microsoft Docs"
description: "Futtatását, hogy a Configuration Manager-hely található erőforrások kezelheti a hálózati infrastruktúra és Active Directory felderítési eljárások konfigurálása."
ms.custom: na
ms.date: 2/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49505eb1-d44d-4121-8712-e0f3d8b15bf5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 860815010068422f2d8854ed2d574c24cc386891
ms.openlocfilehash: 63a3c2ef66c80d1da9b50e67166a2196cf1b081b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="configure-discovery-methods-for-system-center-configuration-manager"></a>Felderítési módszerek konfigurálása a System Center Configuration Manager

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Felderítési módszer futtatásához a System Center Configuration Manager hely keresi az erőforrásokat, amelyeket felügyelhet a hálózati infrastruktúra és az Active Directory konfigurálása Ehhez szükséges, hogy engedélyezi, majd konfigurálja az egyes módszerek használatával kereshet környezetében kívánt. (Letilthatja egy metódust ugyanazzal az eljárással, amelyekkel engedélyezheti a.)  Az egyetlen kivétel ez alól a Szívveréses felderítés és a kiszolgálóészlelés:  

-   Alapértelmezés szerint a Szívveréses felderítés már engedélyezve van a Configuration Manager elsődleges hely telepítésekor, és egy egyszerű ütemezés következőn történő futtatásra konfigurálva. Célszerű Szívveréses felderítést hagyja engedélyezve, mert biztosítja, hogy az eszközök felderítési adatrekordok (DDR) naprakészek legyenek. További információ a Szívveréses felderítés: [a Szívveréses felderítés](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutHeartbeat).  

-   A Kiszolgálófelderítés az automatikus felderítési módszer, amely a hely rendszerként használó számítógépek megkeresése. Nem konfigurálhatja, vagy tiltsa le azt.  

**Ahhoz, hogy az összes konfigurálható felderítési módszert:**  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válassza ki a felderítési módszert ahhoz a helyet, ahol a felderítés engedélyezéséhez.  

3.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**, majd a a **általános** lapon jelölje a **engedélyezése&lt;felderítési módszer\>**  mezőbe.  

     Ha ez a mező már be van jelölve, a jelölőnégyzet jelölésének törlése letilthatja a felderítési módszer.  

4.  Válasszon **OK** a konfiguráció mentéséhez.  


##  <a name="BKMK_ConfigADForestDisc"></a>Active Directory-Erdőfelderítés konfigurálása  
Active Directory-Erdőfelderítés konfigurációjának befejezéséhez konfigurálnia kell az beállításokat két külön helyen:  

-   Az a **felderítési módszerek** csomóponton is:

    - A felderítési módszerek engedélyezése.
    - Beállíthatja a lekérdezési ütemezést.
    - Adja meg, hogy a felderítési művelet automatikusan létrehozza az Active Directory – helyek és-alhálózatok határait.  

-   Az a **Active Directory-erdők** csomóponton is:

    - Adja hozzá a felderíteni kívánt erdőket.
    - Active Directory – helyek és alhálózatok az adott erdőben felderítés engedélyezéséhez.
    - Adja meg, amelyek lehetővé teszik a Configuration Manager-helyek számára a helyadatok közzétételéhez az erdő beállításait.
    - Rendelje hozzá az egyes erdőkhöz az Active Directory-erdő fiókjának használandó fiók.  

Az alábbi eljárásokkal az Active Directory-Erdőfelderítés engedélyezése, valamint használandó erdőket az Active Directory-Erdőfelderítés konfigurálásához.  

#### <a name="to-enable-active-directory-forest-discovery"></a>Active Directory-Erdőfelderítés engedélyezése  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válassza ki a helyet, ahol felderítés Active Directory-Erdőfelderítés módszerét.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **általános** lapra, jelölje be a jelölőnégyzetet, a felderítés engedélyezéséhez. Vagy konfigurálja a felderítést, és térjen vissza később a felderítés engedélyezéséhez.  

5.  Adja meg a beállításokat a felderített helyek határainak létrehozására.  

6.  Adja meg a felderítés futtatásának ütemezését.  

7.  Amikor befejezte az adott hely Active Directory-Erdőfelderítés a konfigurálását, válassza ki a **OK** a konfiguráció mentéséhez.  

#### <a name="to-configure-a-forest-for-active-directory-forest-discovery"></a>Erdő konfigurálása az Active Directory-Erdőfelderítés  

1.  Az a **felügyeleti** munkaterületen, válassza a **Active Directory-erdők**. Ha korábban már futott az Active Directory-erdőfelderítés, az eredmények ablaktáblájában láthatók a felderített erdők. A helyi erdők és a megbízható erdők felderíthetők az Active Directory-erdőfelderítés futtatásával. Csak nem megbízható erdőket kell kézzel felvenni.  

    -   Korábban felderített erdő konfigurálásához jelölje ki az erdőt az eredmények ablaktáblán. Végül a a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok** kattintva jelenítse meg az erdő tulajdonságait. Folytassa a 3. lépéssel.  

    -   Amely nem szerepel, az új erdő konfigurálásához a **Home** lap a **létrehozása** csoportjában válassza **erdő hozzáadása** megnyitásához a **erdők hozzáadása** párbeszédpanel megnyitásához. Folytassa a 3. lépéssel.  

2.  Az a **általános** lapra, Befejezés felderíteni, és adja meg a kívánt erdő beállításait, a **Active Directory-erdő fiókjának**.  

    > [!NOTE]  
    >  Az Active Directory-erdőfelderítés globális fiókot igényel a nem megbízható erdők felderítéséhez és az ezekben történő közzétételhez. Ha a nem a helykiszolgáló számítógépfiókját használja, csak globális fiókot is választhat.  

3.  Ha azt tervezi, hogy ebben az erdőben, az adatok közzétételét a helyek a **közzétételi** lapra, Befejezés erdőbeli közzététel beállításait.  

    > [!NOTE]  
    >  Ha engedélyezi a helyek közzétegyék az adott erdő, ki kell terjesztenie az Active Directory-sémáját a Configuration Manager számára. Az Active Directory-erdő fiókjának teljes hozzáférés engedéllyel a rendszer tárolóhoz kell rendelkeznie az adott erdőben.  

4.  Amikor befejezte az adott erdő Active Directory-Erdőfelderítés való használatra a konfigurálását, válassza ki a **OK** a konfiguráció mentéséhez.  

##  <a name="BKMK_ConfigADDiscGeneral"></a>Active Directory-felderítés konfigurálása számítógépekhez, felhasználók vagy csoportok  
 Az alábbi szakaszokban található információk segítségével konfigurálhatja a számítógépek, felhasználók vagy csoportok. Felderítési módszer bármelyikét alkalmazhatja:  

-   Active Directory-csoportfelderítés  

-   Active Directory-rendszerfelderítés  

-   Active Directory-felhasználófelderítés  

> [!NOTE]  
>  Az itt olvasható információk az Active Directory-Erdőfelderítés nem vonatkozik.  

 Bár a fenti felderítési módszerek független a többi, hasonló beállítások osztoznak. A konfigurációs beállításokról kapcsolatos további információkért lásd: [megosztott beállítások a csoport, a rendszer és a felhasználó felderítése](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_shared).  

> [!WARNING]  
>  Az Active Directory lekérdezés által az egyes felderítési módszereket jelentős hálózati forgalmat generálhat. Vegye fontolóra ütemezés minden olyan időpontra, amikor a hálózati forgalom nem zavarja a hálózat üzleti felhasználását a felderítési módszert.  

#### <a name="to-configure-active-directory-group-discovery"></a>Active Directory-Csoportfelderítés konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válassza ki a **Active Directory-Csoportfelderítés** módszert ahhoz a helyhez, ahol szeretné konfigurálja a felderítést.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **általános** lapra, jelölje be a jelölőnégyzetet, a felderítés engedélyezéséhez. Vagy konfigurálja a felderítést, és térjen vissza később a felderítés engedélyezéséhez.  

5.  Válasszon **Hozzáadás** a felderítési hatókör beállításához, válassza ki vagy **csoportok** vagy **hely**, és fejezze be a következő beállításokat a **csoportok hozzáadása** vagy **Active Directory-hely hozzáadása** párbeszédpanel:  

    1.  Adjon meg egy **neve** a felderítési hatókör.  

    2.  Adjon meg egy **Active Directory-tartomány** vagy **hely** kereséséhez:  

        -   Ha úgy döntött, hogy **csoportok**, adjon meg egy vagy több felderítendő Active Directory-csoportot.  

        -   Ha úgy döntött, hogy **hely**, felderítendő helyként adjon meg egy Active Directory-tárolót. Ezen a helyen az Active Directory-gyermektárolók rekurzív keresését is engedélyezheti.  

    3.  Adja meg a **Active Directory Csoportfelderítési fiók** Ez a felderítési hatókörhöz használandó.  

    4.  Válasszon **OK** a felderítési hatókör konfigurációjának mentéséhez.  

6.  Ismételje meg a 6. minden további felderítési hatókör, amelyet meg szeretne adni.  

7.  Az a **lekérdezés ütemezése** lapra, mind a teljes felderítés és a változásfelderítés lekérdezésütemezési beállításait konfigurálhatja.  

8.  Szükség esetén a a **beállítás** lapon konfigurálhatja a kiszűrhetik vagy kizárhatják azokat az elavult számítógéprekordok felderítésből, és a terjesztési csoportok tagságának felderítésére.  

    > [!NOTE]  
    >  Active Directory-Csoportfelderítés alapértelmezés szerint csak a biztonsági csoportok tagságát deríti fel.  

9. Amikor befejezte az adott hely Active Directory-Csoportfelderítés konfigurálása, **OK** a konfiguráció mentéséhez.  

#### <a name="to-configure-active-directory-system-discovery"></a>Active Directory-Rendszerfelderítés konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válassza ki a helyet, ahol konfigurálhatja a felderítési módszerét.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **általános** lapra, jelölje be a jelölőnégyzetet, a felderítés engedélyezéséhez. Vagy konfigurálja a felderítést, és térjen vissza később a felderítés engedélyezéséhez.  

5.  Válassza ki a **új** ikon ![új ikon](media/Disc_new_Icon.gif) egy új Active Directory-tároló megadásához. Az a **Active Directory-tároló** párbeszédpanel mezőben a következő konfigurációk Befejezés:  

    1.  Adjon meg egy vagy több helyet a kereséshez.  

    2.  Mindegyik helyen adja meg a keresési megváltozzon beállításokat.  

    3.  Mindegyik helyen adja meg a használandó fiókot az **Active Directory felderítési fiók**.  

        > [!TIP]  
        >  Minden egyes megadott helyre felderítési lehetőségek és egyedi Active Directory felderítési fiókot is beállíthat.  

    4.  Válasszon **OK** az Active Directory-tároló konfigurációjának mentéséhez.  

6.  Az a **lekérdezés ütemezése** lapra, mind a teljes felderítés és a változásfelderítés lekérdezésütemezési beállításait konfigurálhatja.  

7.  Szükség esetén a a **Active Directory-attribútumok** lapon további Active Directory-attribútumok felderíteni kívánt számítógépeken konfigurálhatja. Az alapértelmezett objektumattribútumok is szerepelnek.  

8.  Szükség esetén a a **beállítás** lapon konfigurálhatja a kiszűrhetik vagy kizárhatják azokat az elavult számítógéprekordok felderítésből.  

9. Amikor befejezte az adott hely Active Directory-Rendszerfelderítés konfigurálása, **OK** a konfiguráció mentéséhez.  

#### <a name="to-configure-active-directory-user-discovery"></a>Active Directory-Felhasználófelderítés konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válassza ki a **Active Directory-Felhasználófelderítés** módszert ahhoz a helyhez, ahol szeretné konfigurálja a felderítést.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az a **általános** lapra, jelölje be a jelölőnégyzetet, a felderítés engedélyezéséhez. Vagy konfigurálja a felderítést, és térjen vissza később a felderítés engedélyezéséhez.  

5.  Válassza ki a **új** ikon ![új ikon](media/Disc_new_Icon.gif) egy új Active Directory-tároló megadásához. Az a **Active Directory-tároló** párbeszédpanel mezőben a következő konfigurációk Befejezés:  

    1.  Adjon meg egy vagy több helyet a kereséshez.  

    2.  Mindegyik helyen adja meg a keresési megváltozzon beállításokat.  

    3.  Mindegyik helyen adja meg a használandó fiókot az **Active Directory felderítési fiók**.  

        > [!NOTE]  
        >  Minden egyes megadott helyre egyedi készletének felderítési lehetőségek és egyedi Active Directory felderítési fiókot is beállíthat.  

    4.  Válasszon **OK** az Active Directory-tároló konfigurációjának mentéséhez.  

6.  Az a **lekérdezés ütemezése** lapra, mind a teljes felderítés és a változásfelderítés lekérdezésütemezési beállításait konfigurálhatja.  

7.  Szükség esetén a a **Active Directory-attribútumok** lapon további Active Directory-attribútumok felderíteni kívánt számítógépeken konfigurálhatja. Az alapértelmezett objektumattribútumok is szerepelnek.  

8.  Amikor befejezte az adott hely Active Directory-Felhasználófelderítés konfigurálása, **OK** a konfiguráció mentéséhez.  

##  <a name="BKMK_ConfigHBDisc"></a>A Szívveréses felderítés konfigurálása  
 Alapértelmezés szerint a Szívveréses felderítés engedélyezve van a Configuration Manager elsődleges hely telepítésekor. Ennek eredményeképpen csak akkor kell gyakran a Szívveréses felderítési adatrekordot egy felügyeleti ponthoz, ha nem szeretné használni a rendszer az alapértelmezett hét naponta ügyfelek küldési hogyan az ütemezés beállítása.  

> [!NOTE]  
>  Ha ügyfélleküldéses telepítést, mind a karbantartási feladathoz tartozó **telepítési jelző törlése** vannak engedélyezve van ugyanazon a helyen, állítsa be a Szívveréses felderítés kell lennie az ütemezés kisebb, mint a **ügyfél Újrafelderítési időszak** , a **telepítési jelző törlése** helykarbantartási feladat. Helykarbantartási feladatokkal kapcsolatos további információkért lásd: [karbantartási feladatok a System Center Configuration Manager](../../../../core/servers/manage/maintenance-tasks.md).  

#### <a name="to-configure-the-heartbeat-discovery-schedule"></a>A Szívveréses felderítés ütemezésének konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válasszon **a Szívveréses felderítés** a hely, ahová konfigurálhatnak Szívveréses felderítést.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Konfigurálja a gyakoriság, amellyel az ügyfelek küldje el a Szívveréses felderítési adatrekordot, és válassza a **OK** a konfiguráció mentéséhez.  

##  <a name="BKMK_ConfigNetworkDisc"></a>A hálózatfelderítés konfigurálása  
 Az alábbi szakaszokban található információk használatával alakítsa ki a hálózatfelderítés konfigurálása.  

###  <a name="BKMK_AboutConfigNetworkDisc"></a>A hálózatfelderítés konfigurálásának áttekintése  
 A hálózatfelderítés konfigurálása előtt ismernie kell a következő:  

-   A hálózatfelderítés szintjei  

-   A hálózatfelderítés beállításai  

-   A hálózatfelderítés korlátozása a hálózaton  

További információkért lásd: [hálózati felderítés](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutNetwork).  

 Az alábbi szakaszok ismertetik a hálózatfelderítés általános konfigurációi. Beállíthatja az egyik, vagy ezeket a konfigurációkat használatra ugyanazt a felderítés során futtatási. Ha több konfigurációt használ, meg kell terveznie az olyan műveleteket, amelyek hatással lehetnek a felderítés eredményei között.  

 Például érdemes egy adott SNMP logikai csoportnév használó összes Simple Network Management Protocol (SNMP) eszközök felderítéséhez. Ezenkívül ugyanebben a felderítési munkamenetben, a le szeretné tiltani a felderítést adott alhálózaton. Felderítés futásakor a hálózatfelderítés nem deríti fel, amely le van tiltva az alhálózat a megadott logikai csoportnévvel rendelkező SNMP-eszközöket.  

####  <a name="BKMK_DetermineNetTopology"></a>A hálózati topológia meghatározása  
 A topológiára korlátozott felderítés segítségével csatlakoztassa a hálózatot. Ez a felderítési típus nem deríti fel a lehetséges ügyfeleket. A topológiára korlátozott hálózatfelderítés az SNMP protokollon alapul.  

 A hálózati topológia felderítésekor konfigurálnia kell a **útválasztók ugrásainak maximuma** a a **SNMP** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanel megnyitásához. Néhány ugrások, csökkentheti a felderítés futásakor használt hálózati sávszélességet. Felderíteni a hálózatot, mert ahhoz, hogy a hálózati topológia jobb megértése ugrások száma növelhető.  

 Miután megismerte a hálózati topológia, beállíthatja a lehetséges ügyfeleket és az operációs rendszerük felderítését, amíg elérhető konfigurációk használatával korlátozhatja a hálózatfelderítés kereső további tulajdonságait.  

####  <a name="BKMK_LimitBySubnet"></a>A keresések korlátozása alhálózatok használatával  
 Konfigurálhatja a hálózatfelderítést, hogy meghatározott alhálózatokban keressen a felderítési munkamenetben. Alapértelmezés szerint a hálózatfelderítés a felderítést futtató kiszolgáló alhálózatában keres. Bármely további alhálózatokat, konfigurálása és engedélyezése csak a SNMP és a Dynamic Host Configuration Protocol (DHCP) érvényes keresési beállítások. Amikor a hálózatfelderítés tartományokban keres, a alhálózatok konfigurációi nem korlátozza.  

 Ha megad egy vagy több alhálózatból a a **alhálózatok** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanelen, csak a megjelölt alhálózatok **engedélyezve** figyelembe veszi a keresésnél.  

 Ha letilt egy alhálózatot, az ki lesz zárva a felderítésből, és a következő feltételek érvényesek:  

-   Az SNMP alapú lekérdezések nem futnak az alhálózatban.  

-   DHCP-kiszolgálók nem válaszolnak az alhálózatban található erőforrások listájával.  

-   Tartományalapú lekérdezések fel tudják deríteni az alhálózatban található erőforrásokat.  

####  <a name="BKMK_SearchByDomain"></a>Keresés adott tartományban  
 Konfigurálhatja a hálózati felderítés során végzett kereséshez egy adott tartományban vagy tartományok a felderítés futtatásakor. Alapértelmezés szerint a hálózatfelderítés a felderítést futtató kiszolgáló helyi tartományában keres.  

 Ha megad egy vagy több tartományt a a **tartományok** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanelen, csak a megjelölt tartományok **engedélyezve** figyelembe veszi a keresésnél.  

 Ha letilt egy tartományt, az ki lesz zárva a felderítésből, és a következő feltételek érvényesek:  

-   A hálózatfelderítés nem kérdezi le a tartományvezérlőket ebben a tartományban.  

-   Az SNMP alapú lekérdezések továbbra is futhatnak a tartomány alhálózataiban.  

-   DHCP-kiszolgálók továbbra is megválaszolhatja a tartományban található erőforrások listájával.  

####  <a name="BKMK_LimitBySNMPname"></a>A keresések korlátozása SNMP logikai csoportnevek használatával  
 Úgy konfigurálja a hálózati felderítést során végzett kereséshez egy adott SNMP logikai vagy -csoportok készletében hajtsa végre a felderítés futtatásakor. Alapértelmezés szerint a logikai csoportnévvel **nyilvános** van beállítva.  

 A hálózatfelderítés logikai csoportneveket használja, amelyek SNMP-eszközök útválasztók eléréséhez. Útválasztó megadhatja a hálózati felderítés más útválasztókról és alhálózatokról az első útválasztóhoz kapcsolódó információkat.  

> [!NOTE]  
>  SNMP logikai csoportnevek a jelszavakhoz hasonlítanak. A hálózatfelderítés csak SNMP-eszközről, amelynek a logikai csoportnév megadott információkat kapni. Minden SNMP-eszköz saját logikai csoportnévvel rendelkezhet, de gyakran a közösségi névvel több eszköz osztozik. Emellett az SNMP-eszközök többsége az alapértelmezett logikai csoportnévvel rendelkezik **nyilvános**. Azonban egyes szervezetek törlik a **nyilvános** logikai csoportnevet az eszközeikről biztonsági okokból.  

 Ha több SNMP logikai csoport jelennek meg a **SNMP** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanel, a hálózatfelderítés keres ezekben, amelyben látható sorrendben. Egy eszköz csatlakozni a különböző nevű kísérletek által okozott hálózati adatforgalom csökkentése érdekében győződjön meg arról, hogy a leggyakrabban használt nevek a lista tetején.  

> [!NOTE]  
>  Az SNMP logikai csoportnév használata, mellett az IP-címét vagy feloldható nevét a megadott SNMP-eszköz is megadhat. Az ehhez a **SNMP-eszközök** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanel megnyitásához.  

####  <a name="BKMK_SearchByDHCP"></a>Keresés egy adott DHCP-kiszolgálón  
 Konfigurálhatja a hálózatfelderítést, hogy egy adott DHCP-kiszolgáló vagy több kiszolgáló segítségével DHCP-ügyfelek felderítéséhez a felderítés futtatásakor.  

 A hálózatfelderítés minden olyan DHCP-kiszolgáló a megadott keres a **DHCP** lapra a **hálózatfelderítés tulajdonságai** párbeszédpanel megnyitásához. Ha a felderítést futtató kiszolgáló az IP-címét egy DHCP-kiszolgálótól bérli, funkciójával hajthat végre keresést az adott DHCP-kiszolgáló úgy konfigurálhatja a **közé tartozik a DHCP-kiszolgáló, amely a helykiszolgáló konfigurálva van használja** mezőbe.  

> [!NOTE]  
>  A hálózatfelderítés a DHCP-kiszolgáló konfigurálásához, a környezetnek támogatnia IPv4-alapú. A DHCP-kiszolgáló használatára natív IPv6-környezetben a hálózatfelderítést nem konfigurálhatja.  

###  <a name="BKMK_HowToConfigNetDisc"></a>A hálózatfelderítés konfigurálása  
 Az alábbi eljárásokkal először csak a hálózati topológia feltérképezéséhez, majd konfigurálja a lehetséges ügyfelek felderítését használatával a rendelkezésre álló hálózatfelderítési beállítások közül legalább egyet.  

##### <a name="to-determine-your-network-topology"></a>A hálózati topológia meghatározása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válasszon **hálózatfelderítés** a hely, ahol a hálózati felderítés futtatni kívánt.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

    -   A a **általános** lapon jelölje a **engedélyezés hálózatfelderítés** mezőbe, majd válassza a **topológia** a a **felderítés típusa** beállítások.  

    -   Az a **alhálózatok** lapon ellenőrizze a **helyi alhálózatok keresése** mezőbe.  

        > [!TIP]  
        >  Ha ismeri a hálózatot alkotó adott alhálózatokat, törölje a **helyi alhálózatok keresése** mezőben, és használja a **új** ikon ![új ikon](media/Disc_new_Icon.gif) az alhálózatok, amelyet meg szeretne keresni. Nagy hálózatoknál érdemes minimalizálása érdekében a hálózati sávszélesség használatának egyszerre csak egy vagy két alhálózat kereséséhez.  

    -   Az a **tartományok** lapon ellenőrizze a **keresés helyi tartományban** mezőbe.  

    -   Az a **SNMP** lapon a **útválasztók ugrásainak maximuma** legördülő listán adja meg a hálózati felderítés útválasztók hány ugrását hajthatja végre a a topológia leképezésekor.  

        > [!TIP]  
        >  Amikor elsőként a hálózati topológia, konfigurálja a pár útválasztók ugrásainak a hálózati sávszélesség használatának csökkentése érdekében.  

4.  Az a **ütemezés** lapra, majd a **új** ikon ![új ikon](media/Disc_new_Icon.gif) a hálózatfelderítés futtatási ütemezésének beállításához.  

    > [!NOTE]  
    >  Nem rendelhet eltérő felderítési konfigurációkat az egyes hálózatfelderítési ütemezésekhez. Minden alkalommal, amikor a hálózatfelderítés fut, az aktuális felderítési konfigurációt használja.  

5.  Válasszon **OK** számára a beállítások elfogadásához. A hálózatfelderítés az ütemezett időpontban fut.  

##### <a name="to-configure-network-discovery"></a>A hálózatfelderítés konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Hierarchiakonfiguráció**, és válassza a **felderítési módszerek**.  

2.  Válasszon **hálózatfelderítés** a hely, ahol a hálózati felderítés futtatni kívánt.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  A a **általános** lapon ellenőrizze a **engedélyezése a hálózatfelderítés** mezőbe, majd válassza ki a futtatni kívánt felderítés típusa a **felderítés típusa** beállítások.  

5.  Konfigurálja a felderítést alhálózatokban való keresésre, válassza ki a **alhálózatok** lapra, és adja meg az alábbi lehetőségek közül:  

    -   Felderítés futtatása, amelyek a felderítést futtató számítógép helyi alhálózatok, ellenőrizze a **helyi alhálózatok keresése** mezőbe.  

    -   Egy adott alhálózaton való futtatáshoz győződjön meg arról, hogy az alhálózat szerepel **átvizsgálandó alhálózatok** , és egy **keresési** értékének **engedélyezve**:  

        1.  Ha az alhálózat nincs felsorolva, válassza ki azt a **új** ikon ![új ikon](media/Disc_new_Icon.gif). A a **új alhálózat-hozzárendelés** párbeszédpanelen adja meg a **alhálózati** és **maszk** információkat, és válassza a **OK**. Alapértelmezés szerint egy új alhálózatot engedélyezve van a keresés.  

        2.  Módosíthatja a **keresési** felsorolt alhálózatnál értékét, jelölje ki az alhálózatot, és válassza a **váltása** beállítás közötti váltáshoz ikon **letiltott** és **engedélyezve**.  

6.  Konfigurálja a felderítést tartományokban való keresésre, válassza ki a **tartományok** lapra, és adja meg az alábbi lehetőségek közül:  

    -   Futtassa a felderítést a felderítést futtató számítógép tartományán, ellenőrizze a **keresés helyi tartományban** mezőbe.  

    -   Keresés adott tartományban, győződjön meg arról, hogy a tartomány szerepel **tartományok** , és egy **keresési** értékének **engedélyezve**:  

        1.  Ha a tartomány nincs felsorolva, válassza ki azt a **új** ikon ![új ikon](media/Disc_new_Icon.gif). A a **tartomány tulajdonságai** párbeszédpanelen adja meg a **tartomány** információkat, és válassza a **OK**. Új tartomány alapértelmezés szerint engedélyezve van a kereséshez.  

        2.  Módosíthatja a **keresési** felsorolt tartománynál értékét, válassza ki a tartományt, és válassza a **váltása** beállítás közötti váltáshoz ikon **letiltott** és **engedélyezve**.  

7.  Konfigurálja a felderítést adott SNMP logikai csoportnevekkel rendelkező SNMP-eszközök kereséséhez, válassza ki a **SNMP** lapra, és adja meg az alábbi lehetőségek közül:  

    -   SNMP logikai csoportnév hozzáadása listájának **SNMP logikai csoportnevek**, válassza ki a **új** ikon ![új ikon](media/Disc_new_Icon.gif). A a **új SNMP logikai csoportnév** párbeszédpanelen adja meg a **neve** az SNMP-Közösség, és válassza a **OK**.  

    -   SNMP logikai csoportnév eltávolításához jelölje ki a logikai csoport nevét, és válassza a **törlése** ikon ![Törlés ikonra](media/Disc_delete_Icon.gif).  

    -   SNMP logikai csoportnevek keresési sorrendjének beállításához jelölje ki a kívánt logikai csoport nevét, és válassza a **elem áthelyezése felfelé** ikon ![ikon áthelyezése](media/Disc_moveUp_Icon.gif) vagy a **elem áthelyezése lefelé** ikon ![ikon áthelyezése](media/Disc_moveDown_Icon.gif). Felderítés futáskor logikai csoportnevekben való keresés felső sorrendben. Vegye figyelembe a következő szempontokat.

        > [!NOTE]  
        >  A hálózatfelderítés SNMP logikai csoportneveket használja, amelyek SNMP-eszközök útválasztók eléréséhez. Az útválasztók adatokat szolgáltathatnak a hálózatfelderítés más útválasztókról és az első útválasztóhoz kapcsolódó alhálózatokat.  

        -   SNMP logikai csoportnevek a jelszavakhoz hasonlítanak.  

        -   A hálózatfelderítés csak SNMP-eszközről, amelynek a logikai csoportnév megadott információkat kapni.  

        -   Minden SNMP-eszköz saját logikai csoportnévvel rendelkezhet, de gyakran a közösségi névvel több eszköz osztozik.  

        -   SNMP-eszközök többsége az alapértelmezett logikai csoportnévvel rendelkezik **nyilvános**. Is használhatja, ha nem ismer más logikai csoportneveket. Azonban egyes szervezetek törlik a **nyilvános** logikai csoportnevet az eszközeikről biztonsági okokból.  

8.  Az útválasztók ugrásai SNMP keresések maximális számának megadásához válassza ki a **SNMP** lapot, és válassza ki az ugrások számát az **útválasztók ugrásainak maximuma** legördülő listából.  

9. Az SNMP-eszközök konfigurálása, válassza ki a **SNMP-eszközök** fülre. Ha az eszköz nem szerepel ott, válassza ki azt a **új** ikon ![új ikon](media/Disc_new_Icon.gif). Az a **új SNMP-eszköz** párbeszédpanelen adja meg az SNMP-eszköz IP-címét vagy eszköznevét kiszolgálónevét, és válassza **OK**.  

    > [!NOTE]  
    >  Ha eszköznevet ad meg, a Configuration Manager kell tudnia oldani a NetBIOS-nevet egy IP-címet.  

10. Konfigurálja a felderítést adott DHCP-kiszolgálók lekérdezése DHCP-ügyfelek esetében, válassza ki a **DHCP** lapra, és adja meg az alábbi lehetőségek közül:  

    -   A felderítést futtató számítógépen lévő DHCP-kiszolgáló lekérdezéséhez jelölje a **mindig használja a helykiszolgáló DHCP-kiszolgáló** mezőbe.  

        > [!NOTE]  
        >  Használja ezt a beállítást, a kiszolgáló bérelnie kell egy DHCP-kiszolgáló IP-címét, és nem használható egy statikus IP-címet.  

    -   Egy adott DHCP-kiszolgáló lekérdezéséhez kattintson a **új** ikon ![új ikon](media/Disc_new_Icon.gif). Az a **új DHCP-kiszolgáló** párbeszédpanelen adja meg a DHCP-kiszolgáló IP cím vagy a kiszolgáló nevét, és válassza **OK**.  

        > [!NOTE]  
        >  Ha kiszolgálónevet ad meg, a Configuration Manager kell tudnia oldani a NetBIOS-nevet egy IP-címet.  

11. Felderítés futtatási idejének megadásához válassza ki a **ütemezés** lapra, és válassza a **új** ikon ![új ikon](media/Disc_new_Icon.gif) a hálózatfelderítés futtatási ütemezésének beállításához.  

     Ismétlődő ütemezéseket, és több olyan ütemezést, amelyekben nincs ismétlődés is konfigurálhatja.  

    > [!NOTE]  
    >  Ha egyszerre több ütemezés jelennek meg a **ütemezés** lapon egyszerre, az összes ütemezés eredményezi, a hálózatfelderítés futását mivel az az ütemezésben jelzett időpontra van konfigurálva. Ez akkor is igaz, az ismétlődő ütemezésekre.  

12. Válasszon **OK** a konfigurációk mentéséhez.  

###  <a name="BKMK_HowToVerifyNetDisc"></a>A hálózatfelderítés befejeződésének ellenőrzése  
 A hálózati felderítés befejezéséhez szükséges idő számos tényezőtől függően változhat. Ezek a tényezők lehetnek a következők közül:  

-   A hálózat mérete  

-   A hálózat topológiája  

-   A hálózati útválasztók kereséséhez beállított ugrások maximális száma  

-   Az elindított felderítés típusa  

A hálózatfelderítés nem hoz létre riasztást küldjön, amikor befejezte a felderítési üzenetek, mert a következő eljárással ellenőrizheti, amikor befejezte a felderítés.  

##### <a name="to-verify-that-network-discovery-has-finished"></a>A hálózatfelderítés befejeződésének ellenőrzése  

1.  Kattintson a Configuration Manager konzol **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **rendszerállapot**, és válassza a **állapotüzenet-lekérdezések**.  

3.  Válasszon **összes állapotüzenet**.  

4.  Az a **Home** lap a **állapotüzenet-lekérdezések** csoportjában válassza **üzenetek megjelenítése**.  

5.  Az a **dátum és idő kiválasztása** legördülő listában válassza ki a megfelelő értéket, amely magában foglalja, hogy mennyivel a felderítés elindult, és válassza a **OK** megnyitásához a **Configuration Manager állapotüzenet-megjelenítő**.  

    > [!TIP]  
    >  Használhatja a **dátumának és idejének megadása** futtatási dátumának és időpontjának megadásához beállítással futott felderítés. Ez a beállítás akkor hasznos, ha adott napon futtatta a hálózatfelderítést, és szeretné csak adott dátum üzeneteket beolvasni.  

6.  A hálózatfelderítés befejeződésének ellenőrzéséhez keressen a következő részleteket tartalmazó állapotüzenetet:  

    -   Üzenet azonosítója: **502**  

    -   Összetevő: **SMS_NETWORK_DISCOVERY**  

    -   Leírás: **Ez az összetevő leállt**  

    Ha ez az állapotüzenet nincs jelen, a hálózatfelderítés nem fejeződött be.  

7.  Hálózatfelderítés elindításának ellenőrzéséhez keressen a következő részleteket tartalmazó állapotüzenetet:  

    -   Üzenet azonosítója: **500**  

    -   Összetevő: **SMS_NETWORK_DISCOVERY**  

    -   Leírás: **Ez az összetevő elindult**  

    Ez azt igazolja, hogy a hálózatfelderítés elindult. Ha ez az információ nincs jelen, ütemezze újra a hálózatfelderítést.  

