---
title: "Szolgáltatáskeresést helyerőforrások keresésére |} Microsoft Docs"
description: "Ismerje meg, hogyan és mikor System Center Configuration Manager használják az ügyfelek a szolgáltatáskeresést helyerőforrások keresésére."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae72df4b-5f5d-4e19-9052-bda28edfbace
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a181171cc1a92ec4519f4e4b34ca3274a0aa0440
ms.openlocfilehash: 1c9e7ada6a8aa228b30e58865baae0f6e529e6af
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="learn-how-clients-find-site-resources-and-services-for-system-center-configuration-manager"></a>Ismerje meg, hogyan ügyfelek keresése és a System Center Configuration Manager szolgáltatáskeresés

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-ügyfelek nevezett folyamat használata *hely szolgáltatás* található a helyrendszer-kiszolgáló, amely képes kommunikálni, és amelyek biztosítják a szolgáltatásokat, amellyel az ügyfelek irányítja a rendszer használni. Az ismertetése, hogyan és mikor használják az ügyfelek a szolgáltatáskeresést helyerőforrások keresésére segíthet konfigurálni a helyeket, hogy azok sikeresen támogassák az ügyfél-feladatok. Ezek a beállítások megkövetelhetik a webhely kommunikál a tartományi és hálózati konfigurációkkal, például az Active Directory tartományi szolgáltatások (AD DS) és a DNS Szolgáltatásban. Vagy összetettebb alternatív megoldások konfigurálását is szükséges.  

 Szolgáltatást biztosító helyrendszer-szerepkörök közé:

 - A core helyrendszer-kiszolgálót az ügyfelek számára.
 - A felügyeleti pont.
 - További helyrendszer-kiszolgálókat, az ügyfél kommunikálni képes, mint például a terjesztési pontok és a szoftverfrissítési pontok frissítése.  



##  <a name="bkmk_fund"></a> Fundamentals of service location  
 Ügyfél értékeli az aktuális hálózati helyét, a kommunikáció protokollsorrend és a hozzárendelt hely található, amely képes kommunikálni egy felügyeleti pont szolgáltatáskeresésre használata esetén.  

 **Ügyfél kommunikációt folytat egy felügyeleti ponttal:**  
-   Töltse le a hely más felügyeleti pontok adatait, akkor hozhat létre az ismert felügyeleti pontok listáját (néven a *Felügyeletipont-listát*) jövőbeli szolgáltatási hely cikluson.  
-   Töltse fel a konfigurációs részletek, például a leltározási és állapotát.  
-   Töltse le a házirendet, amely az ügyfél konfigurációk be, és tájékoztathatja az ügyfél szoftver, amely akkor is, vagy telepíteni kell, és egyéb kapcsolódó feladatokat.  
-   További információ helyrendszerszerepköröket, amelyek szolgáltatásokat nyújtanak az ügyfél kérelmet használatára van konfigurálva. Ilyen például a szoftver, amely az ügyfél telepítése a terjesztési pontokon, vagy a szoftverfrissítési pont frissítések beszerzéséhez.  

**A Configuration Manager-ügyfél a szolgáltatás helyére vonatkozó kérelmet teszi:**  
-   25 óránként, a folyamatos működéshez.  
-   Ha az ügyfél észleli a változást a hálózati konfiguráció vagy a hely.  
-   Ha a **ccmexec.exe** szolgáltatás a számítógépen (az alapvető ügyfélszolgáltatás) elindul.  
-   Ha az ügyfél elő kell készítenie a helyrendszerszerepkör, amely biztosítja a szükséges szolgáltatások.  

**Amikor egy ügyfél megpróbálja található helyrendszer-szerepköröket működtető**, szolgáltatáskeresés található olyan helyrendszerszerepkör, amely támogatja az ügyfél protokollt (HTTP vagy HTTPS) használja. Az ügyfelek alapértelmezés szerint a rendelkezésükre álló legbiztonságosabb módszert használják. Ügyeljen a következőkre:  

-   A HTTPS protokoll használatához rendelkeznie kell nyilvános kulcsokra épülő infrastruktúrával (PKI), és telepítenie kell a PKI-tanúsítványokat az ügyfelekre és a kiszolgálókra. További információk a tanúsítványok használatáról: [A System Center Configuration Manager PKI-tanúsítványának követelményei](../../../core/plan-design/network/pki-certificate-requirements.md).  

-   Amikor az IIS-t (Internet Information Services) használó helyrendszerszerepkört telepít, amely támogatja az ügyfelekről érkező kommunikációt, meg kell adnia, hogy az ügyfelek a HTTP vagy a HTTPS protokoll használatával csatlakoznak-e a helyrendszerhez. A HTTP használata esetén meg kell fontolnia az aláírás és a titkosítás alkalmazását is. További információkért lásd: [aláírás és titkosítás tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) a a [tervezése a System Center Configuration Manager security](../../../core/plan-design/security/plan-for-security.md).  

##  <a name="BKMK_Plan_Service_Location"></a>Szolgáltatáskeresés és hogyan meg az ügyfelek a hozzájuk rendelt felügyeleti pontról  
Amikor egy ügyfél először egy elsődleges helyhez van rendelve, az adott hely alapértelmezett felügyeleti pont választja ki. Elsődleges helyek támogatják a több felügyeleti pontot, és minden egyes ügyfél önállóan határoz meg a felügyeleti pont az alapértelmezett felügyeleti pontnak. Az alapértelmezett felügyeleti pont lesz, hogy az ügyfélszámítógépek hozzárendelt felügyeleti ponttal. (Akkor is ügyfél-telepítési parancsokat beállításához használja a hozzárendelt felügyeleti pont az ügyfél a telepítés.)  

Egy ügyfél kommunikálni felügyeleti pontot választ, az ügyfél aktuális hálózati helyük és határcsoportjuk csoport konfigurációk alapján. Annak ellenére, hogy a hozzárendelt felügyeleti ponttal rendelkezik, az nem lehet a felügyeleti ponthoz, az ügyfél használ.  

    > [!NOTE]  
    >  A client always uses the assigned management point for registration messages and certain policy messages, even when other communications are sent to a proxy or local management point.  

Előnyben részesített felügyeleti pontokat is használhat. Előnyben részesített felügyeleti pontok olyan felügyeleti pontok egy ügyfél hozzárendelt helye az ügyfél által helyrendszer-kiszolgálók keresésére használt határcsoporthoz társított. A határ egy előnyben részesített felügyeleti pontot társítást csoportban, a helyrendszer-kiszolgáló hasonlít hogyan terjesztési pontokat vagy állapotáttelepítési pontok társítva egy határcsoporthoz. Ha engedélyezi az előnyben részesített felügyeleti pontokat a hierarchiához, és egy ügyfél felügyeleti pontot használ a hozzárendelt helyéről, akkor az ügyfél először előnyben részesített felügyeleti pontot meg használni, mielőtt más felügyeleti pontokat használna a hozzárendelt helyéről.  

Használhatja az információk a [felügyeletipont-affinitás](http://blogs.technet.com/b/jchalfant/archive/2014/09/22/management-point-affinity-added-in-configmgr-2012-r2-cu3.aspx) blogja a TechNet.com felügyeletipont-affinitás konfigurálásához. Felügyeleti pont affinitás felülbírálások az alapértelmezett működést hozzárendelt felügyeleti pontok, és lehetővé teszi, hogy az ügyfél egy vagy több konkrét felügyeleti pontok használatát.  

Minden alkalommal, amikor egy ügyfélnek kapcsolódnia felügyeleti pontot, ellenőrzi a Felügyeletipont-listát, amelyet helyben tárol a Windows Management Instrumentation (WMI). Az ügyfél egy kezdeti Felügyeletipont-listát hoz létre, ha telepítve van. Az ügyfél majd rendszeres időközönként frissíti a hierarchia minden olyan felügyeleti pont adatait.  

Ha az ügyfél nem talál érvényes felügyeleti pontot a listán, azt a következő szolgáltatáskeresési forrásokon, sorrendben keres, amíg nem talál használható felügyeleti pontot:  

1.  Felügyeleti pont  
2.  ACTIVE DIRECTORY TARTOMÁNYI SZOLGÁLTATÁSOK  
3.  DNS  
4.  WINS  

Ha egy ügyfél talál, és kapcsolatba lép egy felügyeleti ponttal, akkor letölti a hierarchiában elérhető felügyeleti pontok aktuális listáját, és frissíti a helyi Felügyeletipont-listát. Ez a tartományhoz csatlakoztatott és nem csatlakoztatott ügyfelekre egyaránt érvényes.  

Például amikor a Configuration Manager-ügyfél, amely az interneten egy internetalapú felügyeleti pont csatlakozik, a felügyeleti pont elküldi az ügyfélnek a rendelkezésre álló Internet alapú felügyeleti pontok listáját a helyen. Ugyanígy, a tartományhoz csatlakoztatott vagy munkacsoporthoz tartozó ügyfelek is megkapják az általuk használható felügyeleti pontok listáját.  

Nincs beállítva az internetes ügyfél nem szerepel a irányuló-csak internetes felügyeleti pontok. Az internethasználatra konfigurált munkacsoportba tartozó ügyfelek csak internetes felügyeleti ponttal kommunikálnak.  

##  <a name="BKMK_MPList"></a> A felügyeleti pontok listája  
A Felügyeletipont-listát, mert a prioritási sorrend listájáról az ügyfél által korábban azonosított felügyeleti pontok egy ügyfél az előnyben részesített szolgáltatáskeresési forrásokról. A lista elemeit az ügyfél a lista frissítésekor hálózati hely szerint rendezi, és a helyi WMI szolgáltatásban tárolja.  

### <a name="building-the-initial-mp-list"></a>A kezdeti Felügyeletipont-listát felépítése  
Az ügyfél telepítése során a következő szabályok segítségével build az ügyfél kiindulási listáját:  

-   A kiindulási lista az ügyfél telepítése során megadott felügyeleti pontokat tartalmazza (Ha használja a **SMSMP**= vagy **/MP** lehetőséget).  
-   Az ügyfél lekérdez az Active Directory tartományi Szolgáltatásokban közzétett felügyeleti pontokat. Azonosítsa az AD DS-ből, a felügyeleti pont az ügyfél hozzárendelt helyéről kell lennie, és az ügyféllel azonos termékverziójú kell lennie.  
-   Ha nincs olyan felügyeleti pont ügyfél telepítése során lett megadva, és az Active Directory-séma nincs kiterjesztve, az ügyfél ellenőrzi, DNS és WINS keres közzétett felügyeleti pontokat.  
-   Ha az ügyfél összeállította a kiindulási lista, a hierarchia egyes felügyeleti pontok adatait nem lehet, hogy ismert.  

### <a name="organizing-the-mp-list"></a>A felügyeleti csomag lista rendszerezése  
Ügyfelek a felügyeleti pontok listájának rendezése a következő besorolásokkal használatával:  

-   **Proxy**: A felügyeleti pont egy másodlagos helyen.  
-   **Helyi**: Minden olyan felügyeleti pont, amely a helyhatárok alapján az ügyfél aktuális hálózati helye társítva van. Vegye figyelembe a határok a következő információkat:
    -   Ha az ügyfél több határcsoporthoz tartozik, a rendszer az ügyfél aktuális hálózati helyét tartalmazó összes határ uniója alapján határozza meg a helyi felügyeleti pontok listáját.  
    -   Helyi felügyeleti pontok jellemzően egy részét az ügyfél által hozzárendelt felügyeleti pontok, kivéve, ha az ügyfél határcsoportjait kiszolgáló felügyeleti pontokkal való van egy másik helyhez társított hálózati helyen belül van.   


-   **Hozzárendelt**: Minden olyan felügyeleti pont, amely az ügyfél hozzárendelt helyének helyrendszere.  

Előnyben részesített felügyeleti pontokat is használhat. Felügyeleti pontok egy helyen, amelyek nincsenek társítva egy határcsoporthoz, és amelyek nincsenek egy ügyfél aktuális hálózati helyüket, társított határcsoportban nem tekinthetők előnyben részesített. Ha az ügyfél nem talál elérhető előnyben részesített felügyeleti pontként használandó.  

### <a name="selecting-a-management-point-to-use"></a>A használandó felügyeleti pont kiválasztása  
A tipikus kommunikációhoz az ügyfél megkísérel használni egy felügyeleti pontot használja a besorolásokat, az ügyfél hálózati helye alapján, az alábbi sorrendben:  

1.  Proxy:  
2.  Helyi:  
3.  hozzárendelt  

Az ügyfél ugyanakkor mindig a hozzárendelt felügyeleti pontot használja a regisztrációs üzenetekhez és egyes házirendüzenetekhez, még akkor is, ha más üzeneteket proxy típusú vagy helyi felügyeleti pontra küld.  

Az egyes kategóriákban (proxy, helyi és hozzárendelt) a választ egy felügyeleti ponthoz, beállítások, a következő sorrendben:  

1.  HTTPS-kommunikációra alkalmas felügyeleti pont megbízható vagy helyi erdőben (ha az ügyfél HTTPS-kommunikációra van konfigurálva)  
2.  HTTPS-kompatibilis nem megbízható vagy helyi erdőben (ha az ügyfél HTTPS-kommunikációra van konfigurálva)  
3.  A HTTP-kompatibilis megbízható vagy helyi erdőben  
4.  Képes a HTTP nem megbízható vagy helyi erdőben található  

Az ügyfél a felügyeleti pontok preferencia szerint rendezett készletből megpróbálja az első felügyeleti pontot használják, a listában. Ez a felügyeleti pontok rendezett lista véletlenszerű, és nem lehetnek rendezve. A lista sorrendje minden alkalommal, amikor az ügyfél frissíti a felügyeleti csomag listáját módosíthatja.  

Amikor egy ügyfél nem képes csatlakozni az első felügyeleti pontot, megkísérli minden egymást követő felügyeleti pontot a listán. A nem előnyben részesített felügyeleti pontok előtt megkísérli minden előnyben részesített felügyeleti pontot az adott kategóriában. Ha egy ügyfél nem képes kommunikálni valamelyik felügyeleti ponttal az osztályozási, megpróbál kapcsolódni egy előnyben részesített felügyeleti pontot a következő besorolási, és így tovább, amíg nem talál egy felügyeleti pontot.  

Miután egy ügyfél egy felügyeleti ponttal való kommunikációt létesít, akkor továbbra is használja, hogy azonos felügyeleti pontot, amíg:  

-   25 óra elteltével.  
-   Az ügyfél nem tud kommunikálni a felügyeleti pont öt megkísérelnek-e egy adott időszakban 10 perc.

Az ügyfél ezután véletlenszerűen választ egy új felügyeleti pontot.  

##  <a name="bkmk_ad"></a> Active Directory  
A tartományhoz csatlakoztatott ügyfelek az AD DS-t használhatják szolgáltatáskeresésre. Ennek feltétele, hogy a helyek [közzétegyék adataikat az Active Directoryban](http://technet.microsoft.com/library/hh696543.aspx).  

Egy ügyfél Active Directory tartományi szolgáltatások használhatja a szolgáltatáskereséshez, a következő feltételek teljesülése esetén:  

-   Az Active Directory [kiterjesztése megtörtént-e](https://technet.microsoft.com/library/mt345589.aspx) vagy a System Center 2012 Configuration Manager rendszerre.  
-   A [Active Directory-erdő van konfigurálva a közzétételt](http://technet.microsoft.com/library/hh696542.aspx), és a Configuration Manager-helyeknek egyaránt engedélyezve közzététele.  
-   Az ügyfélszámítógép Active Directory-tartományhoz tartozik, és van számára elérhető globáliskatalógus-kiszolgáló.  

Ha az ügyfél nem talál az Active Directory tartományi szolgáltatásokat szolgáltatáskeresésre használható felügyeleti pontot, megpróbálja használhatják a DNS.  

##  <a name="bkmk_dns"></a> DNS  
Az intranethez kapcsolódó ügyfelek a DNS szolgáltatást használhatják szolgáltatáskeresésre. Ennek feltétele, hogy a hierarchiában legalább egy hely közzétegyen információkat a felügyeleti pontokról a DNS-ben.  

Akkor célszerű megfontolni a DNS használatát szolgáltatáskeresésre, ha az alábbi feltételek közül valamelyik teljesül:
-   Az AD DS-séma nincs kibővítve a Configuration Manager támogatására.
-   Az intranethez kapcsolódó ügyfelek olyan erdőben, amely nincs engedélyezve a találhatók a Configuration Manager-közzétételt.  
-   Egyes ügyfelek munkacsoportba tartozó számítógépeken futnak, és nincsenek beállítva kizárólag internetes ügyfélfelügyeletre. (Az internethasználatra konfigurált munkacsoportba tartozó ügyfél fog csak internetes felügyeleti ponttal kommunikálnak, és ne használja a DNS szolgáltatás helyét.)  
-   [Az ügyfelek beállíthatók a felügyeleti pontok keresésére a DNS szolgáltatásból](http://technet.microsoft.com/library/gg682055).  

Ha egy hely szolgáltatáskeresési rekordokat tesz közzé a felügyeleti pontokról a DNS-ben:  

-   A közzététel csak olyan felügyeleti pontok esetében alkalmazható, amelyek fogadják az intranetről érkező ügyfélkapcsolatokat.  
-   A hely szolgáltatáskeresési erőforrásrekordot (SRV RR) helyez el a felügyeleti pontot üzemeltető számítógép DNS-zónájában. Az adott számítógépnek rendelkeznie kell egy gazdagépbejegyzéssel a DNS-ben.  

Alapértelmezés szerint a tartományhoz csatlakoztatott ügyfelek keresnek a saját tartományukhoz felügyeletipont-rekordokat. Beállíthatja, hogy egy ügyfél a tartománynak az utótagját, amely rendelkezik felügyeleti ponttal kapcsolatos információkat a DNS-ben közzétett megadó tulajdonság.  

A DNS-utótag ügyféltulajdonság konfigurálásával kapcsolatos további információkért lásd: [konfigurálása az ügyfélszámítógépek számára, hogy a felügyeleti pont keresésére DNS-közzététel segítségével a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md).  

Ha az ügyfél nem talál a DNS-ből szolgáltatáskeresésre használható felügyeleti pontot, megpróbálja a WINS használatával.  

### <a name="publish-management-points-to-dns"></a>Felügyeleti pontok közzététele a DNS szolgáltatásban  
A felügyeleti pontok DNS szolgáltatásban való közzétételéhez teljesülnie kell az alábbi két feltételnek:  

-   A DNS-kiszolgálóknak támogatniuk kell a szolgáltatáskeresési erőforrásrekordokat, 8.1.2-es vagy újabb BIND használatával.  
-   A felügyeleti pontok a Configuration Manager a megadott intranetes teljes tartományneveknek Állomásbejegyzéssel (például A rekorddal) kell a DNS-ben.  

> [!IMPORTANT]  
>  A Configuration Manager DNS-közzététele nem támogatja az elkülönülő névtereket. Ha elkülönülő névteret, manuálisan felügyeleti pontok közzététele a DNS-ben vagy ebben a szakaszban a többi szolgáltatáskeresési módszerek ismertetett valamelyikével.  

**Ha a DNS-kiszolgálók támogatják az automatikus frissítéseket**, beállíthatja a Configuration Manager automatikus közzétételét az intraneten lévő felügyeleti pontokat a DNS-ben vagy a DNS-ben manuálisan is közzéteheti ezeket a rekordokat. A felügyeleti pontok DNS szolgáltatásban való közzétételekor a rendszer a felügyeleti pontok intranetes teljes tartománynevét és portszámát közzéteszi a szolgáltatáskeresési (SRV) rekordban. A DNS-közzététel konfigurál egy helyen a hely felügyeleti pont összetevő tulajdonságai. További információkért lásd: [összetevő a System Center Configuration Manager hely](../../../core/servers/deploy/configure/site-components.md).  

**Ha a DNS-zónát a dinamikus frissítéseket beállítása "Csak biztonságos"**, csak az első felügyeleti pontot a DNS-közzététele sikeresen úgy teheti az alapértelmezett engedélyek.

Ha csak egy felügyeleti pont sikeresen közzététele és módosítsa a DNS-rekordot, és a felügyeletipont-kiszolgáló állapota kifogástalan, ügyfelek kaphat a teljes Felügyeletipont-listát, hogy a felügyeleti pont, és keresse meg az előnyben részesített felügyeleti pontot.


**Ha a DNS-kiszolgálók nem támogatják az automatikus frissítéseket, a szolgáltatáskeresési rekordokat azonban igen**, manuális módszerrel közzéteheti a felügyeleti pontokat a DNS-ben. Ehhez manuálisan kell meghatároznia a szolgáltatáskeresési erőforrásrekordot (SRV RR) a DNS szolgáltatásban.  

A Configuration Manager támogatja az RFC 2782 szabványnak megfelelő szolgáltatáskeresési rekordok. Ezek a rekordok formátuma a következő: *_Service._Proto.Name élettartam osztály SRV Prioritás Súly Port cél*  

A Configuration Manager felügyeleti pont közzétételéhez a következő értékeket határozza meg:  

-   **_Szolgáltatás**: Adja meg **_mssms_mp**_&lt;Helykód\>, ahol &lt;Helykód\> a felügyeleti pont helykódja.  
-   **._Protokoll**: Adja meg **._tcp**.  
-   **. Név**: Adja meg például a felügyeleti pont DNS-utótagját **contoso.com**.  
-   **TTL**: Adja meg **14400**, ami négy órát.  
-   **Osztály**: Adja meg **IN** (az RFC 1035 szabványnak megfelelően).  
-   **Prioritás**: A Configuration Manager nem használja ezt a mezőt.
-   **Súly**: A Configuration Manager nem használja ezt a mezőt.  
-   **Port**: Adja meg a portszámot, a felügyeleti pont által használt, például **80** a HTTP és **443-as** HTTPS-hez.  

    > [!NOTE]  
    >  A SRV rekord portjának meg kell felelnie a felügyeleti pont által használt kommunikációs portot. Alapértelmezés szerint ez a **80** HTTP-kommunikációhoz és **443-as** HTTPS-kommunikációhoz.  

-   **Cél**: Adja meg az intranetes teljes Tartománynevet, a felügyeleti pont helyszerepkörhöz konfigurált helyrendszerhez megadott.  

Windows Server DNS használata esetén az alábbi módszerrel adhatja meg a DNS-rekordot az intranetes felügyeleti pontokhoz. Ha más DNS-implementációt használ, a jelen szakaszban ismertetett mezőértékek és a DNS szolgáltatás dokumentációja alapján ültesse át az eljárást saját környezetére.  

##### <a name="to-configure-automatic-publishing"></a>Az automatikus közzététel konfigurálása:  

1.  A Configuration Manager-konzolon bontsa ki **felügyeleti** > **Helykonfiguráció** > **helyek**.  

2.  Válassza ki azt a helyet, és válassza a **Helyösszetevők**.  

3.  Válasszon **felügyeleti pont**.  

4.  Válassza ki a közzétenni kívánt felügyeleti pontokat. (Ez a beállítás az AD DS és a DNS-közzététel vonatkozik.)  

5.  Jelölje be a jelölőnégyzetet annak közzététele a DNS Szolgáltatásban. Ebben a mezőben:  

    -   Lehetővé teszi, hogy mely felügyeleti pontok közzététele a DNS Szolgáltatásban kiválasztását.  

    -   Közzététel az Active Directory tartományi szolgáltatások nem konfigurálja.  

##### <a name="to-manually-publish-management-points-to-dns-on-windows-server"></a>Felügyeleti pontok manuális közzététele a Windows Server DNS szolgáltatásában  

1.  A Configuration Manager konzolon adja meg a helyrendszerek helyrendszerek teljes tartománynevét.  

2.  A DNS-kezelőkonzolon jelölje ki a felügyeleti pont számítógépének DNS-zónáját.  

3.  Győződjön meg arról, hogy a helyrendszer intranetes teljes tartománynevéhez tartozik állomásrekord (A vagy AAAA). Ha nincs, hozzon létre egyet.  

4.  Használatával a **egyéb új rekordok** lehetőségre, válassza a **szolgáltatáshely (SRV)** a a **erőforrásrekord típusa** párbeszédpanelen válassza ki **rekord létrehozása**, adja meg a következő adatokat, és válassza **végzett**:  

    -   **Tartomány**: Szükség esetén adja meg a felügyeleti pont DNS-utótagját például **contoso.com**.  
    -   **Szolgáltatás**: Típus **_mssms_mp**_&lt;Helykód\>, ahol &lt;Helykód\> a felügyeleti pont helykódja.  
    -   **Protokoll**: Type **_tcp**.  
    -   **Prioritás**: A Configuration Manager nem használja ezt a mezőt.  
    -   **Súly**: A Configuration Manager nem használja ezt a mezőt.  
    -   **Port**: Adja meg a portszámot, a felügyeleti pont által használt, például **80** a HTTP és **443-as** HTTPS-hez.  

        > [!NOTE]  
        >  A SRV rekord portjának meg kell felelnie a felügyeleti pont által használt kommunikációs portot. Alapértelmezés szerint ez a **80** HTTP-kommunikációhoz és **443-as** HTTPS-kommunikációhoz.  

    -   **A szolgáltatást nyújtó állomás**: Adja meg az intranetes teljes Tartománynevet, a felügyeleti pont helyszerepkörhöz konfigurált helyrendszerhez megadott.  

Ismételje meg ezeket a lépéseket a DNS-ben közzétenni kívánt valamennyi felügyeleti ponthoz az intraneten.  

##  <a name="bkmk_wins"></a> WINS  
Ha a többi szolgáltatáskeresési módszer nem jár eredménnyel, az ügyfelek a WINS szolgáltatásban is kereshetnek kezdeti felügyeleti pontot.  

Alapértelmezés szerint elsődleges hely közzéteszi a WINS SZOLGÁLTATÁSBAN az első felügyeleti pontot a helyen konfigurált HTTP- és az első felügyeleti pontot, amely a HTTPS használatára konfigurált.  

Ha nem szeretné, hogy az ügyfelek a WINS-ben HTTP-kommunikációra konfigurált felügyeleti pontot találjanak, az ügyfelek konfigurálásához használja a CCMSetup.exe **SMSDIRECTORYLOOKUP=NOWINS**Client.msi-tulajdonságát.  

