---
title: "A tartalom forráshelyeként |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager-beállításokat, amelyek lehetővé teszik az ügyfelek megtalálják a tartalmat a lassú hálózaton."
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70b5cbc0-64ba-49bd-8b34-fb4c09b2b95b
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7f2fd3e550c7dc1b27996dc309b53f74e8c865e9
ms.openlocfilehash: a823458dc3b891b1c32d1cb44a96e8cafd376ed5
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="content-source-location-scenarios-in-system-center-configuration-manager"></a>A tartalom forráshelyei – forgatókönyvek a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Verzió 1610, mielőtt System Center Configuration Manager támogatott kombinált meghatározni, hogyan és hol ügyfelek tartalom keresése lassú hálózaton lévő több beállításokat. A lehetséges kombinációk hatással a tartalom helyéhez használni, és hogy sikeresen használhat, amikor egy előnyben részesített forrás tartalék helyet tartalom nem érhető el.  

> [!IMPORTANT]  
> **Ha a helyek verziója 1511-es, a 1602-es vagy 1606 fut**, a jelen témakörben található információk az infrastruktúra vonatkozik. Lásd még: [1511,1602 és 1606 határcsoportjainak](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) ezeket a Configuration Manager verziói a határcsoportok vonatkozó információt.
>
> **Ha a helyek 1610 vagy újabb verzióját futtatják**, olvassa el a [helyhatárok és határcsoportok megadása a System Center Configuration Manager](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups) ismertetése az ügyfelek, amelyeken megtalálható a tartalom elérhető terjesztési pontok számára.





**A következő három beállítást viselkedését határozza meg, amikor az ügyfelek tartalmat igényelnek:**

-  **Tartalék forráshely engedélyezése a tartalom** (engedélyezve vagy nem engedélyezve): Ez a lehetőség az, hogy engedélyezhető a **Határcsoportok** a terjesztési pontok lapon. Ez lehetővé teszi, hogy az ügyfél számára, amikor a tartalom nem érhető el egy előnyben részesített terjesztési ponton tartalék helyként konfigurált terjesztési pontot használ.  

 - **Hálózati kapcsolat sebességének központi telepítés működése**: A központi telepítések a következő konfigurációk határozhatják meg, amennyiben a kapcsolat a terjesztési pontra lassú egyike:  

    -   **Tartalom letöltése a terjesztési pontról és Futtatás helyben**  

    -   **Tartalom letöltésének mellőzése**: Ez a beállítás csak akkor használható, amikor egy ügyfél tartalék helyet használ a tartalom beszerzését.  

    A kapcsolat sebességének beállítása a terjesztési pont konfigurálva van a **hivatkozások** lapon határcsoporthoz, és csak az adott határcsoport.  

 -  **Az igény szerinti csomagterjesztés** (az előnyben részesített terjesztési pontokra): Ez a lehetőséget választva engedélyezve **tartalmának terjesztése az előnyben részesített terjesztési pontokon a csomag** a a **terjesztési beállítások** egy csomag vagy alkalmazás Tulajdonságok lapján. Ha engedélyezve van, ez a beállítás arra utasítja a automatikusan átmásolni a tartalmat egy előnyben részesített terjesztési ponton, amely még nem rendelkezik a tartalom után egy ügyfél a tartalmat kéri le a terjesztési pont a Configuration Manager.  


 **Minden forgatókönyvben az alábbi követelmények vonatkoznak:**


-   A tartalom érhető el egy tartalék terjesztési ponton  

-   Terjesztési pontok online állapotúak és elérhetők  


## <a name="scenario-1"></a>1. eset  
 Érvényes, ha a konfiguráció a következő:  

-   **Tartalom áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Tartalék engedélyezése**: Nincs engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Bármely konfiguráció  


**Részletek:** (A igény szerinti csomagterjesztés konfigurációja esetében nem releváns ebben a forgatókönyvben.)  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom a felügyeleti pontra.  

3.  Az ügyfél letölti a tartalmat egy előnyben részesített terjesztési pontról a listában.  

## <a name="scenario-2"></a>2. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltésének mellőzése  


**Részletek:** (A igény szerinti csomagterjesztés konfigurációja esetében nem releváns ebben a forgatókönyvben.)  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely jelzi, hogy engedélyezve legyenek-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontról.  

3.  Az ügyfél letölti a tartalmat egy előnyben részesített terjesztési pontról a listában.  

## <a name="scenario-3"></a>3. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltése és telepítése  


**Részletek:** (A igény szerinti csomagterjesztés konfigurációja esetében nem releváns ebben a forgatókönyvben.)  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely jelzi, hogy engedélyezve legyenek-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontról.  

3.  Az ügyfél letölti a tartalmat egy előnyben részesített terjesztési pontról a listában.  

## <a name="scenario-4"></a>4. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** nincs engedélyezve  

-   **Tartalék engedélyezése**: Nincs engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Bármely konfiguráció  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek előnyben részesített terjesztési pontok a listán.  

3.  Az ügyfél nem tud üzenet **tartalom nem áll rendelkezésre** és újrapróbálkozik. Óránként küld új tartalomkérelmet.  

## <a name="scenario-5"></a>5. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** nincs engedélyezve  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltésének mellőzése  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely jelzi, hogy engedélyezve legyenek-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek előnyben részesített terjesztési pontok, amelyeken megtalálható a tartalom, de legalább egy tartalék terjesztési ponton.  

3.  A tartalom letöltése nem történik meg, mert az ügyfél egy tartalék terjesztési pontra vonatkozó a rendszerbe állítási tulajdonság értéke **tartalom letöltésének mellőzése** (amely használatos ügyfelek számára a tartalom forráshelyeként). Az ügyfél nem tud üzenet **tartalom nem áll rendelkezésre** és újrapróbálkozik. Az ügyfél óránként küld új lehetővé teszi.  

## <a name="scenario-6"></a>6. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** nincs engedélyezve  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltése és telepítése  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely azt jelzi, hogy engedélyezve vannak-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek nem előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom, de legalább egy tartalék terjesztési ponton, amelyen a tartalmat.  

3.  A tartalom letölthető a listán szereplő tartalék terjesztési pontról, mert az ügyfél egy tartalék terjesztési pontra vonatkozó a rendszerbe állítási tulajdonság értéke **a tartalom letöltése és telepítése**.  

## <a name="scenario-7"></a>A forgatókönyv 7  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** engedélyezve van  

-   **Tartalék engedélyezése**: Nincs engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Bármely konfiguráció  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek nem előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom.  

3.  Az ügyfél nem tud üzenet **tartalom nem áll rendelkezésre** és újrapróbálkozik. Óránként küld új kérés érkezett.  

4.  A felügyeleti pont eseményindítót hoz létre a Distribution Manager tartalmat kíván terjeszteni az összes előnyben részesített terjesztési pont az ügyfél a tartalom kérést.  

5.  A Distribution Manager eljuttatja a tartalmat az összes előnyben részesített terjesztési pontokra. A legtöbb esetben a tartalom terjesztése az előnyben részesített terjesztési pontokra egy órán belül.  

6.  Új tartalomkérelmet a felügyeleti pont az ügyfél által kezdeményezett.  

7.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom a felügyeleti pontra. Az ügyfél letölti a tartalmat egy előnyben részesített terjesztési pontról a listában.  

## <a name="scenario-8"></a>8. forgatókönyv  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** engedélyezve van  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltésének mellőzése  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely jelzi, hogy engedélyezve legyenek-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek előnyben részesített terjesztési pontok, amelyeken megtalálható a tartalom, de legalább egy tartalék terjesztési ponton.  

3.  A tartalom letöltése nem történik meg, mert az ügyfél egy tartalék terjesztési pontra vonatkozó a rendszerbe állítási tulajdonság értéke **ne töltse le**. Az ügyfél nem tud üzenet **tartalom nem áll rendelkezésre** és újrapróbálkozik. Az ügyfél óránként küld új lehetővé teszi.  

4.  A felügyeleti pont eseményindítót hoz létre a Distribution Manager tartalmat kíván terjeszteni az összes előnyben részesített terjesztési pont az ügyfél a tartalom kérést.  

5.  A Distribution Manager eljuttatja a tartalmat az összes előnyben részesített terjesztési pontokra. A legtöbb esetben a tartalom terjesztése az előnyben részesített terjesztési pontokra egy órán belül.  

6.  Új tartalomkérelmet a felügyeleti pont az ügyfél által kezdeményezett.  

7.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontokra, amelyeken megtalálható a tartalom a felügyeleti pontra.  

8.  Az ügyfél letölti a tartalmat egy előnyben részesített terjesztési pontról a listában.  

## <a name="scenario-9"></a>A forgatókönyv 9  
 Létezik a következő beállításokat:  

-   **Tartalom nem áll rendelkezésre előnyben részesített terjesztési ponton**  

-   **Előnyben részesített terjesztési pontokon a csomag tartalmának terjesztése az** engedélyezve van  

-   **Tartalék engedélyezése**: Engedélyezve  

-   **Központi telepítés működése lassú hálózaton**: Tartalom letöltése és telepítése  


**Részletek:**  

1.  Az ügyfél tartalomkérelmet küld a felügyeleti pont. Az ügyfél jelzőt mellékel a kérelemhez, amely jelzi, hogy engedélyezve legyenek-e a tartalék terjesztési pontok tartalmazza.  

2.  Egy tartalomhelylistát küld vissza az ügyfél az előnyben részesített terjesztési pontok és tartalék terjesztési pontok, amelyeken megtalálható a tartalom a felügyeleti pontra. Nincsenek előnyben részesített terjesztési pontok, amelyeken megtalálható a tartalom, de legalább egy tartalék terjesztési ponton.  

3.  A tartalom letölthető a listán szereplő tartalék terjesztési pontról, mert az ügyfél egy tartalék terjesztési pontra vonatkozó a rendszerbe állítási tulajdonság értéke **a tartalom letöltése és telepítése**. A központi telepítési beállítás lehetővé teszi, hogy az ügyfél, amely a tartalom beszerzését arról a helyről tartalék tartalmi helyet kell használnia.  

4.  A felügyeleti pont eseményindítót hoz létre a Distribution Manager tartalmat kíván terjeszteni az összes előnyben részesített terjesztési pont az ügyfél a tartalom kérést.  

5.  A Distribution Manager eljuttatja a tartalmat az összes előnyben részesített terjesztési pontokra, amely lehetővé teszi további ügyfelek számára a tartalom tartalék terjesztési pontra használata nélkül.  

