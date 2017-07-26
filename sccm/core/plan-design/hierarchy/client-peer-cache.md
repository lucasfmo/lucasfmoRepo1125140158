---
title: "Ügyfél társ-gyorsítótárazás |} System Center Configuration Managerben"
description: "Társ-gyorsítótárazási ügyfél a tartalom forráshelyét vizsgáló használatára, ha a System Center Configuration Managerrel tartalom központi telepítése."
ms.custom: na
ms.date: 4/4/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: dcd05d7d120f8997562da7d92b38c8b52a512357
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="peer-cache-for-configuration-manager-clients"></a>A Configuration Manager-ügyfelek számára társ-gyorsítótárazás

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager verziója 1610 kezdve használhatja **társ-gyorsítótárazás** telepítése a tartalom távoli ügyfelek kezeléséhez. Társ-gyorsítótárazás a beépített Configuration Manager megoldással, amely lehetővé teszi az ügyfelek számára, hogy közvetlenül a helyi gyorsítótárból más ügyfelekkel tartalmat osszanak.   

> [!TIP]  
> Bevezetett 1610 verziójával, társ-gyorsítótárazás és a Ügyféladatforrások irányítópult is előzetes kiadású szolgáltatások. Engedélyezheti a őket [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/pre-release-features).

## <a name="overview"></a>Áttekintés
 -     Ügyfélbeállítások segítségével az ügyfelek számára társ-gyorsítótárazás engedélyezése.
 -     Tartalmak megosztása, társ-gyorsítótárazási ügyfeleknek kell lennie az ügyfél, amely a tartalmat kér az aktuális határcsoporthoz tagként. Található szomszédos társ-gyorsítótárazási ügyfelek nem is a rendelkezésükre áll rendelkezésre a tartalom forráshelyét vizsgáló tartalmaz, amikor egy ügyfél tartalék használ, hogy tartalmat szomszédos határcsoportban. Az aktuális és szomszédos határcsoportok kapcsolatos további információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - A társ-gyorsítótárazás nem engedélyezettek, de a jelenlegi határcsoportban a társ-gyorsítótárazási ügyfelek kezelésére képes ügyfelek számára, beszerezheti a tartalmat a társ-gyorsítótárazás engedélyezve ügyfélről.  
 - Bármilyen típusú tartalmat, amely a Configuration Manager-ügyfél gyorsítótára használatban van más ügyfelek számára társ-gyorsítótárazás használatával szolgálhatók ki.
 -    Társ-gyorsítótárazás nem helyettesíti az egyéb megoldások, például a BranchCache, de ehelyett működik mellé további lehetőségek a hagyományos tartalomterjesztési megoldások, például a terjesztési pontok kibővítésére vele. Ez az egy egyéni megoldást, a BranchCache nem igényel, ha nem engedélyezi, vagy a Windows BranchCache használata, továbbra is működik.

### <a name="operations"></a>Műveletek

Miután ügyfélbeállítások, amelyek lehetővé teszik a társ-gyorsítótárazás egy gyűjteményhez, tagjai működhet társ tartalomforrásként más ügyfelek számára az azonos határcsoportban:
 -    Társ tartalomforrásként működő ügyfél küldi el a felügyeleti pontjára érhető el a gyorsítótárazott tartalom listáját.
 -    Majd amikor az adott határcsoport a következő ügyfél ezt a tartalmat, minden társ-gyorsítótárazási forrástól, amely a tartalmat adja vissza az esetleges tartalom a terjesztési pontok és egyéb tartalom forráshelyeiről az adott határcsoport együtt.
 -    A normál működési folyamatonként az ügyfélnek, amelyik a tartalmat kér egy tartalomforrás források van megadva, és a tartalom beszerzéséhez megkísérli majd folytatódik a készletből választja ki.

> [!NOTE]
> Ha a tartalék tartalom szomszédos határcsoportban következik be, a szomszédos határcsoport a tartalom forráshelyét vizsgáló nem lettek hozzáadva a potenciális tartalom forráshelyét vizsgáló készletéhez az ügyfél társ-gyorsítótárazás.  


Bár a lehetőség minden ügyfél társ-gyorsítótárazási forrásként, az ajánlott eljárás, csak a leginkább ügyfelek válasszon olyan alkalmas alatt társközi gyorsítótár források részt venni.  Az ügyfelek megfelelősége kiértékelése ügyfél Váztípus, lemezterület, hálózati kapcsolat és több alapján. További információk, amelyek segítségével válassza ki a legjobb ügyfelek számára társ-gyorsítótárazás: [ebben a blogban által Microsoft tanácsadó](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Társ-gyorsítótárazási forrástól való korlátozott hozzáférésre**  
1702 verziójával kezdve társközi gyorsítótár forrásoldali számítógép elutasítják tartalmat kér, amikor a társközi gyorsítótár forrásoldali számítógép megfelel-e az alábbi feltételek bármelyike:  
  -  Alacsony töltöttségű telepre vonatkozó módban van.
  -  CPU-terhelés meghaladja a 80 % időpontjában a tartalmat.
  -  Lemezes i/o-rendelkezik egy *AvgDiskQueueLength* , amely meghaladja a 10.
  -  Nincs több elérhető kapcsolódást a számítógéphez van.   

Beállíthatja, hogy ezek a beállítások az ügyfél-konfigurációs kiszolgáló WMI-osztályt használja a társ forrásról (*SMS_WinPEPeerCacheConfig*) a System Center Configuration Manager SDK használatakor.

Ha a számítógép visszautasítja a kérelmet a tartalomhoz, a kérést küldő számítógép továbbra keresik a készlet elérhető a tartalom forráshelyei helyek alternatív forrásból származó tartalom.   



### <a name="monitoring"></a>Figyelés   
Megismerheti a társ-gyorsítótárazás használatát, megtekintheti az Ügyféladatforrások irányítópulton. Lásd: [Ügyféladatforrások irányítópult](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

1702 verziójával kezdve segítségével három jelentések megtekintése a társközi gyorsítótár-használata. Nyissa meg a a konzol **figyelés** > **jelentéskészítési** > **jelentések**. A jelentések összes típusa lehet **szoftver telepítési tartalom**:
1.  **Gyorsítótár-forrás tartalom elutasítási partnert**:  
Ez a jelentés segítségével azonosíthatja, milyen gyakran a társ-gyorsítótár adatforrások határcsoportban elutasította a tartalomra vonatkozó kérelmet.
 - **Ismert hiba:** Amikor a szakasz a Lehatolás példáit eredmények, például *MaxCPULoad* vagy *MaxDiskIO*, egy, a jelentés javasol hiba akkor fordulhat elő, vagy nem tartalmaz adatokat. Ez, használja az alábbi két jelentés, amely közvetlenül a eredmények megjelenítése.

2. **Gyorsítótár-forrás tartalom elutasítási partnert feltétel**:  
Ez a jelentés segítségével azonosíthatja egy megadott csoportban vagy az elutasítással kapcsolatos határtípusként elutasítási részleteit. Megadhat

  - **Ismert hiba:** Nem választható ki olyan rendelkezésre álló paraméterek közül, és inkább manuálisan kell megadnia őket. Adja meg az értékeket a *határ csoportnév* és *elutasítási típus* az első jelentés látható módon. Például *elutasítási típus* beírhatja *MaxCPULoad* vagy *MaxDiskIO*.

3. **Gyorsítótár adatforrás tartalom elutasítási részletei partnert**:   
  Ez a jelentés segítségével azonosíthatja a tartalmat, amely alatt a kért Ha vissza lett utasítva.

 - **Ismert hiba:** Nem választható ki olyan rendelkezésre álló paraméterek közül, és inkább manuálisan kell megadnia őket. Adja meg az értéket *elutasítási típus* megjelenő első jelentést (társközi gyorsítótár forrás tartalom elutasítása), és írja be a *erőforrás-azonosító* a tartalomforrás, amely további információt szeretne kapni.  Az erőforrás-azonosítója a tartalomforrás keresése:  

    1. Keresse meg a számítógép nevét, amely jelzi a *társ-gyorsítótárazási forrástól* a 2. a jelentés (társközi gyorsítótár forrás tartalom elutasítási feltétel) eredményét.  
    2. A következő Ugrás **eszközök és megfelelőség** > **eszközök** majd keresse meg a számítógép neve. Az erőforrás-azonosító oszlop értékét használja.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Követelmények és szempontok a társ-gyorsítótárazás
-   Társ-gyorsítótárazás bármely támogatott Configuration Manager-ügyfél, a Windows operációs rendszeren támogatott. Nem Windows operációs rendszerek nem támogatottak a társ-gyorsítótárazás.

-   Az ügyfelek csak akkor továbbíthatnak tartalmakat a társ-gyorsítótárazási ügyfelek számára, amely az aktuális határcsoportban vannak.

-   Minden hely, ahol az ügyfél társ-gyorsítótárazás használatára kell konfigurálni a [hálózatelérési fiók](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). A fiók társaktól letöltési kérelmek hitelesítéséhez szükséges a társ-gyorsítótárazási forrás számítógép által használt, és csak a tartományi felhasználói engedélyekkel kell rendelkeznie az erre a célra.

-     Az aktuális határ társ-gyorsítótárazás tartalomforrás, hogy az ügyfélszámítógépek utolsó hardver készlet küldésének határozza meg, mert egy ügyfelet, hogy egy hálózati helyre barangol, és azt egy másik határcsoportba továbbra is tekinthető a korábbi határcsoport tagja társ-gyorsítótárazás céljára. Ez egy ügyfél társ-gyorsítótárazás tartalomforrás, amely nincs az azonnali hálózati helyen felajánlott eredményezhet. Azt javasoljuk, kivéve az ügyfelek esetében, akik a hibalehetőség ezt a konfigurációt a társ-gyorsítótárazási forrásként való részvétellel.

## <a name="to-configure-client-peer-cache-client-settings"></a>Ügyfél társgyorsítótár beállításainak konfigurálása
1.    Nyissa meg a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások**, majd nyissa meg az eszköz egy ügyfélbeállítás-objektumot, amely a használni kívánt. Módosíthatja az alapértelmezett ügyfélbeállítások objektum is.
2.    A rendelkezésre álló beállítások listája, válassza a **Ügyfélgyorsítótár beállításait**.
3.    Állítsa be **teljes körű operációsrendszer tartalommegosztás engedélyezése a Configuration Manager-ügyfél** való **Igen**.
4.    A következő beállításokat adja meg a társ-gyorsítótárazás használni kívánt portokat:  
  -  **Kezdeti hálózati szórás portja**
  -  **A HTTPS a társközi kommunikációban való használatának engedélyezése**
  -  **Port a tartalomletöltés (HTTP/HTTPS)**

Minden számítógépen, amely a társ-gyorsítótárazás engedélyezve van a Windows tűzfal van használatban, ha a Configuration Manager konfigurálja úgy, hogy engedélyezze a konfigurált portok használatát.

