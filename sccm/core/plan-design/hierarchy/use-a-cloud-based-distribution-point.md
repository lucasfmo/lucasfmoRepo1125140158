---
title: "Felhőalapú terjesztési pont |} Microsoft Docs"
description: "Ismerje meg, valamint a felhőalapú terjesztési pont a System Center Configuration Manager használatára vonatkozó korlátozások."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cd9c725-6b42-427d-9191-86e67f84e48c
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: 489f38d3f88391e42b5271c03151203d22b26d9e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-cloud-based-distribution-point-with-system-center-configuration-manager"></a>Felhőalapú terjesztési pont használata a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A felhőalapú terjesztési pont a Microsoft Azure-ban üzemeltetett System Center Configuration Manager terjesztési ponttá. Az alábbi információk segítenek megismerni a felhőalapú terjesztési pontok használatának konfigurációit és korlátozásait.

Miután telepített egy elsődleges hely és készen áll a felhő alapú terjesztési pontok telepítéséhez, [felhő alapú terjesztési pontok telepítése az Azure-ban](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md).


## <a name="plan-to-use-a-cloud-based-distribution-point"></a>Felhőalapú terjesztési pont használatának tervezése
Ha felhőalapú terjesztést használ:  

-   **Ügyfélbeállítások konfigurálása** engedélyezése a felhasználók és eszközök számára a tartalom.  

-   **Adja meg egy elsődleges helyet a tartalomátvitel kezeléséhez** a terjesztési pontra.  

-   **Adja meg a küszöbértékek** a terjesztési pont és a terjesztési pontról átvitelének engedélyezése kívánt tartalom mennyisége tárolni kívánt tartalom mennyiségére.  


Az Ön által konfigurált küszöbértékek alapján, a Configuration Manager riasztást adhat, mely figyelmezteti, ha a terjesztési ponton eltárolt tartalom összesített mennyisége mennyisége vagy az ügyfelek adatforgalma megközelíti a meghatározott küszöbértékeket.  

Felhőalapú terjesztési pontok ellenőrzésben is elérheti a helyszíni terjesztési pontok számos szolgáltatásokat támogatja:  

-   Felhőalapú terjesztési pontok kezelése vagy tagjaiként terjesztésipont-csoportokhoz.  

-   A felhőalapú terjesztési pont használható tartalék tartalomhelyként.  

-   Az intranetes és az internetes ügyfeleket is támogatják.  


Felhőalapú terjesztési pontok további előnyei a következők:  

-   Felhőalapú terjesztési pontra küldött tartalmakat a Configuration Manager által titkosított előtt a Configuration Manager elküldi az Azure-bA.  

-   Az Azure a felhőalapú szolgáltatás, az ügyfelek, anélkül hogy telepíteni és kezelni az újabb terjesztési pontokat kellene tartalomkérelmek tartalomkérései változó igényeinek kielégítéséhez manuálisan méretezhető.  

-   Azok az ügyfelek is használhatják a felhőalapú terjesztési pontot, amelyek a Windows BranchCache segítségével töltik le a tartalmat.  


A következő korlátozások vonatkoznak a felhőalapú terjesztési pontokra:  

-  A gyorsjavítás KB4010155 1610 verziót használ, mielőtt a felhőalapú terjesztési pontot a szoftverfrissítési csomagok tárolására nem használhat. Ez a probléma fennáll kezdő 1702 verziójával, és újabb verziók.  

-   A felhőalapú terjesztési pont a PXE vagy csoportos küldésre képes központi telepítések nem használható.  

-   Az ügyfelek nem használhatják tartalomhelyként a felhőalapú terjesztési pontot az olyan feladatütemezések központi telepítéséhez, amelyeknél be van kapcsolva a **Tartalom helyi letöltése, ha a futó feladatütemezés igényli**beállítás. De azok a feladatütemezések, amelyeknél a **Minden tartalom helyi letöltése a feladatütemezés elindítása előtt** beállítás van megadva, használhatják tartalomhelyként a felhőalapú terjesztési pontot.  

-   A felhőalapú terjesztési pontok nem támogatják a terjesztési pontról futtatott csomagokat. Minden tartalmat kell letöltenie az ügyfél és futtassa helyileg.  

-   A felhőalapú terjesztési pontok nem támogatják az Application Virtualization és a hasonló programok által használt adatfolyam-alkalmazásokat.  

-   A felhőalapú terjesztési pontok nem támogatják a manuálisan előkészített tartalmat. A distribution manager az elsődleges hely, amely kezeli a terjesztési pont minden tartalmat a terjesztési pontra.  

-   Felhőalapú terjesztési pont nem konfigurálható lekéréses terjesztési pontként.  

##  <a name="BKMK_PrereqsCloudDP"></a> A felhőalapú terjesztési pontok használatának előfeltételei  
 A következő előfeltételeket kell teljesíteni a felhőalapú terjesztési pontok használatához:  

-   Azure-előfizetéssel (lásd: [előfizetések és tanúsítványok](#BKMK_CloudDPCerts) ebben a témakörben).

-   Az Azure-ban a felhőszolgáltatás és a Configuration Manager elsődleges helykiszolgáló közötti kommunikáció egy önaláírt vagy a nyilvános kulcsokra épülő infrastruktúra (PKI) felügyeleti tanúsítvány (lásd: [előfizetések és tanúsítványok](#BKMK_CloudDPCerts) ebben a témakörben).

-   (Egy PKI) szolgáltatástanúsítvány, amelyek Configuration Manager-ügyfelek csatlakozhatnak a felhőalapú terjesztési pontok, tartalmat töltsenek HTTPS protokoll használatával.  

-  Egy eszköz vagy felhasználó rendelkeznie kell **hozzáférés engedélyezése a felhőalapú terjesztési pontok** beállítása **Igen** az ügyfél beállítása **Felhőszolgáltatások** egy eszközre vagy felhasználóra tartalom hozzáférhessen a felhőalapú terjesztési pontokról. Alapértelmezésben a **Nem**érték van megadva.  

-   Egy ügyfélnek el kell tudnia oldani a nevet, a felhőalapú szolgáltatás, amelyhez a tartománynévrendszer (DNS) alias és egy olyan CNAME rekordot a DNS-névtérben.  

-   Az ügyfélnek internet-hozzáféréssel kell rendelkeznie a felhőalapú terjesztési pont használatához.  

##  <a name="BKMK_CloudDPCost"></a> A felhőalapú terjesztés költségei  
 A felhő alapú terjesztési pontok használatakor vett adattárolás és letöltési átvitelek, amelyek a Configuration Manager-ügyfelek végre költségeinek tervezése.  

 A Configuration Manager tartalmaz olyan költségek korlátozására és adatelérés figyelésére:  

-   Szabályozhatja és figyelemmel kísérheti a felhőszolgáltatásban tárolt tartalom mennyiségét.  

-   Beállíthatja, hogy a Configuration Manager riasztást küld amikor **küszöbértékek** az ügyfelek letöltéseire elérik vagy túllépik a havi korlátot.  

-   Emellett társ-gyorsítótárazás (a Windows BranchCache) segítségével az ügyfelek által a felhőalapú terjesztési pontok adatátvitelek számának csökkentése érdekében. A BranchCache használatára beállított Configuration Manager-ügyfelek is tartalomátvitelt a felhőalapú terjesztési pontok használatával.  


**Paraméterek:**  

-   **Felhőre vonatkozó ügyfélbeállítások**: A hierarchiában lévő összes felhőalapú terjesztési pont elérését Ön szabályozza a **ügyfélbeállítások**.  

     Az **Ügyfél beállításai**alatt a **Felhőbeállítások** kategória támogatja a **Hozzáférés engedélyezése a felhőalapú terjesztési pontokhoz**beállítást. Alapértelmezés szerint a beállítás értéke **Nem**. Ezt a beállítást a felhasználók és eszközök is engedélyezheti.  

-   **Adatátviteli küszöbértékek**: Az adatok a terjesztési ponton tárolni kívánt és az ügyfelek a terjesztési pontról letöltött adatok küszöböket is beállíthat.  

     A felhőalapú terjesztési pontokra vonatkozó küszöbértékek az alábbiakat tartalmazzák:  

    -   **Tárolási riasztási küszöbérték**: A tárolási riasztási küszöbérték egy felső korlátot állít be adatokat vagy a felhőalapú terjesztési ponton tárolni kívánt tartalom mennyisége. A Configuration Manager is kritikus riasztás, ha fennmaradó szabad helye elér egy meghatározott szintet megadott.  

    -   **Átviteli riasztási küszöbérték**: Az átviteli riasztási küszöbérték segíti a terjesztési pontról az ügyfelek felé átvitt egy 30 napos időtartamon belül tartalom mennyiségének figyelését. Az átviteli riasztási küszöbérték figyeli az adatátvitelt az elmúlt 30 napban, és emelheti figyelmeztető riasztást és kritikus riasztás, ha az átvitel eléri az Ön által meghatározott értékeket.  

        > [!IMPORTANT]  
        >  A Configuration Manager figyeli az adatátvitelt, de nem állítja le a megadott átviteli riasztási küszöbérték felett marad az adatátvitelt.  

 Mindegyik felhőalapú terjesztési ponthoz meghatározhatja a küszöbértékeket a felhőalapú terjesztési pont telepítése során, vagy a telepítés után szerkesztheti az összes felhőalapú terjesztési pont tulajdonságait.  

-   **Riasztások**: Beállíthatja a Configuration Manager számára küldött adatok átviteléről és az egyes felhőalapú terjesztési pontok, a megadott adatátviteli küszöböknél alapuló riasztást. Ezek a riasztások adatátvitelek figyelése, és segíthetnek eldönteni, mikor leállíthatja a felhőszolgáltatást, állítsa be a tartalmat a terjesztési pont tárolja, vagy módosítsa mely ügyfelek használhatják a felhőalapú terjesztési pontok.  

     A óránként az elsődleges hely, amely figyeli a felhőalapú terjesztési pont letölti a tranzakciós adatokat az Azure-ból, és tárolja a CloudDP -&lt;szolgáltatásnév\>.log a helykiszolgálón. A Configuration Manager majd ezt az információt az egyes felhőalapú terjesztési pontok tárolási és átviteli kvótái alapján értékeli ki. Amikor az adatátvitel eléri vagy meghaladja a figyelmeztetés vagy kritikus riasztások mennyiséget, a Configuration Manager a megfelelő riasztást állít elő.  

    > [!WARNING]  
    >  Mivel az adatátvitelről szóló információkat az Azure-ból hourly, hogy adatfelhasználás meghaladhatja a figyelmeztetési vagy kritikus küszöbértéket, mielőtt a Configuration Manager, az adatokat, és riasztást tölti le.  

    > [!NOTE]  
    >  A felhő alapú terjesztési pontok riasztásokat kihasználtságának statisztikai adatai, amely elérhető legyen, akár 24 órába is telhet az Azure-ból függ. További információ az Azure-ba, hogy milyen gyakran Azure felhasználási statisztikáinak frissítési gyakoriságát, beleértve a tárolási analitika: [tárolási analitika](http://go.microsoft.com/fwlink/p/?LinkID=275111) az MSDN könyvtárában.  


-   **Az igény szerinti a felhőszolgáltatás indítása vagy leállítása**: A beállítás segítségével leállíthatja a felhőszolgáltatást, hogy megakadályozza a felhasználókat a szolgáltatás folyamatos használatában. Amikor leállítja a felhőszolgáltatást, akkor azonnal megakadályozza az ügyfeleket abban, hogy a szolgáltatásból további tartalmat töltsenek le. Ezenkívül újraindíthatja a felhőszolgáltatást, hogy helyreállítsa az ügyfelek hozzáférését. Például lehetséges, hogy le akarja állítani a felhőszolgáltatást, amikor eléri az adatok küszöbértékét.  

     Amikor leállítja a felhőszolgáltatást, akkor a felhőszolgáltatás nem törli az adatokat a terjesztési pontról, és nem akadályozza meg a helykiszolgálót sem abban, hogy további tartalmat vigyen át a felhőalapú terjesztési pontra.  

     Leállíthatja a felhőszolgáltatást, a Configuration Manager konzolon jelölje ki a terjesztési pontot a **felhőalapú terjesztési pontok** csomópontjából **Felhőszolgáltatások**, a a **felügyeleti** munkaterületen. Ezután válasszon **szolgáltatás leállítása** az Azure-ban futó felhőszolgáltatás leállításához.  

##  <a name="BKMK_CloudDPCerts"></a> A felhőalapú terjesztési pontokhoz szükséges előfizetések és tanúsítványok  
 Felhő alapú terjesztési pontok tanúsítványokat kér ahhoz, hogy engedélyezze a Configuration Manager kezelje a terjesztési pontot futtató felhőszolgáltatást, és hogy az ügyfelek a tartalom elérésére a terjesztési ponton. Az alábbi információk áttekintést nyújt ezekről a tanúsítványokról. További részletes információ: [PKI certificate requirements for System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md)(A System Center Configuration Manager PKI-tanúsítványának követelményei).  

 **Tanúsítványok**  

-   **Felügyeleti tanúsítvány a helykiszolgáló és a terjesztési pontok közötti kommunikációhoz**: A felügyeleti tanúsítvány az Azure szolgáltatásfelügyeleti API és a Configuration Manager megbízhatósági kapcsolatot hoz létre. Ez a hitelesítés lehetővé teszi, hogy a Configuration Manager az Azure API hívásokat kezdeményezzen, amire például központi telepítési tartalom vagy indítása és a felhőalapú szolgáltatás leállítása esetén. Azure használatával létrehozhat saját felügyeleti tanúsítványaikat, amely lehet önaláírt tanúsítványokat vagy a hitelesítésszolgáltató (CA) által kiállított tanúsítványokat:  

    -   Adja meg a felügyeleti tanúsítvány .cer fájlját az Azure-ba, Azure Configuration Manager konfigurálásakor. A .cer fájl tartalmazza a felügyeleti tanúsítvány nyilvános kulcsát. Az Azure-bA a tanúsítványt kell tölteni a felhőalapú terjesztési pont telepítése előtt. Ez a tanúsítvány lehetővé teszi, hogy a Configuration Manager az Azure API elérését.  

    -   Adja meg a felügyeleti tanúsítvány PFX-fájlját a Configuration Manager a felhőalapú terjesztési pont telepítésekor. A .pfx fájl tartalmazza a felügyeleti tanúsítvány titkos kulcsát. A Configuration Manager a helyadatbázisban tárolja ezt a tanúsítványt. Mivel a .pfx fájlban a titkos kulcsot, meg kell adnia a jelszót a Tanúsítványfájl importálása a Configuration Manager adatbázisába.  

    Ha hoz létre egy önaláírt tanúsítványt, akkor először exportálja a tanúsítványt egy .cer fájlba, és majd exportálni újra egy .pfx fájlba.  

    Másik lehetőségként megadhat egy verzió **.publishsettings** az Azure SDK 1.7 a fájlt. Információ a .publishsettings fájlokról tekintse meg az Azure dokumentációját.  

    További információkért lásd: [felügyeleti tanúsítvány létrehozása](http://go.microsoft.com/fwlink/p/?LinkId=220281) és [felügyeleti tanúsítvány hozzáadása az Azure-előfizetés](http://go.microsoft.com/fwlink/p/?LinkId=241722) az MSDN Library Azure platform szakaszában.  

-   **Szolgáltatástanúsítvány az ügyfél és a terjesztési pont közötti kommunikációhoz**: A Configuration Manager felhő alapú terjesztési pont szolgáltatási tanúsítványához a Configuration Manager-ügyfelek és a felhőalapú terjesztési pont között megbízhatósági kapcsolatot hoz létre, és biztosítja az adatok, Secure Socket Layer (SSL) használatával a HTTPS-KAPCSOLATON keresztül.  

    > [!IMPORTANT]  
    >  A szolgáltatástanúsítvány tárgymezőjében szereplő köznapi névnek egyedinek kell lennie a tartományon belül, és a tartományhoz csatlakozó eszközök nevével sem lehet azonos.  

   Ez a tanúsítvány telepítését bemutató példát, című **a felhő alapú terjesztési pontok a szolgáltatástanúsítvány központi telepítése** a következő témakör [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="bkmk_Tasks"></a> A felhőalapú terjesztési pontok általános felügyeleti feladatai  

-   **Helykiszolgáló és a felhő alapú terjesztési pontok közötti kommunikációhoz**: A felhőalapú terjesztési pont telepítésekor hozzá kell rendelnie egy elsődleges hely kezeléséhez a tartalom átvitelét a felhőszolgáltatásba. Ez a művelet ugyanúgy történik, mint amikor a terjesztési pont helyrendszerszerepkört telepítik egy helyre.  

-   **Ügyfél és a felhőalapú terjesztési pont közötti kommunikációhoz**: Ha egy eszköz vagy egy eszköz felhasználója van adva az az ügyfélbeállítás, amely lehetővé teszi a felhő alapú terjesztési pont használatát, az eszköz megkaphatja a felhőalapú terjesztési pontot érvényes tartalomhelyként:  

    -   A felhőalapú terjesztési pont távoli terjesztési pontot tekintendő, ha az ügyfél értékeli az elérhető tartalomhelyeket.  

    -   Az intranetes ügyfelek csak akkor használhatják felhő alapú terjesztési pontok végső esetben ha a helyszíni terjesztési pontok nem érhetők el.  

    Annak ellenére, hogy a felhő alapú terjesztési pontok Azure meghatározott régióiba telepítik, a felhőalapú terjesztési pontokat használó ügyfelek nem ismerik az Azure-régiók, és nem determinisztikusan választják ki a felhő alapú terjesztési pontok.

Ez azt jelenti, hogy ha több régióba felhő alapú terjesztési pontok telepítése, és egy ügyfél több felhőalapú terjesztési pont tartalomhelyként kap, az ügyfél nem használhatja a felhőalapú terjesztési pont az ügyféllel azonos Azure régióban.  

Felhőalapú terjesztési pontokat használó ügyfelek számára a tartalom helyére irányuló kérelmek kövesse az alábbi eljárást:  

1.  Ha egy ügyfélen engedélyezve van a felhőalapú terjesztési pontok használata, először az előnyben részesített terjesztési pontokról próbálja megszerezni a tartalmat.  

2.  Ha előnyben részesített terjesztési ponton nem érhető el, az ügyfél egy távoli terjesztési pontot használ, ha a központi telepítés támogatja ezt a lehetőséget, és ha nem érhető el egy távoli terjesztési pont.  

3.  Ha sem az előnyben részesített, sem a távoli terjesztési pontok nem érhetők el, csak akkor próbálja az ügyfél megszerezni a tartalmat egy felhőalapú terjesztési pontról.  



  Amikor egy ügyfél egy felhőalapú terjesztési pontot használ tartalomhelyként, az ügyfél hitelesíti magát a felhőalapú terjesztési pontot a Configuration Manager hozzáférési jogkivonat segítségével. Ha az ügyfél megbízhatónak találja a Configuration Manager felhő alapú terjesztési pont tanúsítványa, az ügyfél ezután letöltheti a kért tartalomhoz.  

-   **Felhőalapú terjesztési pontok figyelése**: Figyelheti az egyes felhőalapú terjesztési pontokra központilag telepített tartalmat, és figyelheti a terjesztési pontot üzemeltető felhőszolgáltatást.  

    -   **Tartalom**: Központilag telepített tartalmat egy felhőalapú terjesztési pontra, akkor hajtsa végre, ha a helyszíni terjesztési pontokra telepít tartalmat ugyanúgy figyelheti.  

    -   **A felhőalapú szolgáltatás**: A Configuration Manager rendszeresen ellenőrzi az Azure-szolgáltatás, és riasztást küld, ha a szolgáltatás nem aktív, vagy ha nincsenek az előfizetéssel vagy a tanúsítvánnyal kapcsolatos problémák. A terjesztési pont adatait is megtekintheti a **felhőalapú terjesztési pontok** csomópontjából **Felhőszolgáltatások** a a **felügyeleti** a Configuration Manager konzol munkaterületén. Erről a helyről áttekintő szintű adatokat láthat a terjesztési pontról megtekintése. Is kiválaszthat egy terjesztési pontot, és szerkesztheti a tulajdonságait.  

    A felhőalapú terjesztési pont tulajdonságainak szerkesztésekor a következőket teheti:  

    -   Állítsa be az adatok tárolási és riasztási küszöbértékeit.  

    -   Tartalom kezelése, mivel azt szeretné egy a helyszíni terjesztési pontot.  

    Végül minden felhőalapú terjesztési pontnál megtekintheti, de nem szerkesztheti az előfizetési azonosítót, a szolgáltatásnevet és minden hozzá kapcsolódó részletes adatot, melyet a felhőalapú terjesztés telepítésénél adott meg.  

-   **Biztonsági mentés és helyreállítás a felhő alapú terjesztési pontok**: Felhőalapú terjesztési pontot használ a hierarchiában, az az alábbi információk segítségével tervezheti meg a biztonsági mentési vagy helyreállítási a terjesztési pont:  

    -   Ha használja az előre meghatározott **helykiszolgáló biztonsági mentése** karbantartási feladat, a Configuration Manager automatikusan beveszi a mentésbe a felhőalapú terjesztési pont konfigurációját.  

    -   Ajánlott biztonsági másolatot, és mentse el a felügyeleti tanúsítványt és a szolgáltatástanúsítvány használt felhő alapú terjesztési ponttal is. Ha a Configuration Manager egy másik számítógépre a felhőalapú terjesztési pontot kezelő elsődleges hely, akkor újra kell importálnia a tanúsítványokat előtt továbbra is használhatja őket.  

-   **Felhőalapú terjesztési pont eltávolítása** : A felhőalapú terjesztési pont eltávolításához jelölje ki a terjesztési pontot a Configuration Manager konzolon, és válassza **törlése**.  

    Ha töröl egy felhőalapú terjesztési pontot a hierarchiából, a Configuration Manager eltávolítja a tartalmat az Azure felhőalapú szolgáltatásából.  

