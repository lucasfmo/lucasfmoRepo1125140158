---
title: "A helyhez rendelt ügyfelek |} Microsoft Docs"
description: "A System Center Configuration Managerben helyhez rendelt ügyfelek."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ba9b623f-6e86-4006-93f2-83d563de0cd0
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: a0ccd453fbe346c239eb6e37bc3ed557487b1e27
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-assign-clients-to-a-site-in-system-center-configuration-manager"></a>Ügyfélszoftverek helyhez rendelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-ügyfél a telepítést követően csatlakozniuk kell a Configuration Manager elsődleges hely előtt kezelhető. Neve a helyet, amelyhez az ügyfél csatlakozik a *hozzárendelt helyét*. Az ügyfelek központi adminisztrációs helyhez vagy másodlagos helyhez nem rendelhetők.  

A hozzárendelési folyamat az ügyfél sikeresen telepítve van, és az ügyfélszámítógépet felügyelő hely meghatározása után történik. Közvetlenül hozzárendelhet az ügyfél egy helyhez, vagy használhatja az automatikus helyhozzárendelést ahol az ügyfél automatikusan megtalálja a megfelelő helyet az aktuális hálózati hely vagy a hierarchiához konfigurált tartalék hely alapján.

A Configuration Manager a beléptetés során a mobileszközön lévő ügyfél telepítésekor a rendszer mindig automatikusan hozzárendeli az eszközhöz egy helyhez. Ha az ügyfél telepíthető olyan számítógépre, dönthet úgy kell hozzárendelnie az ügyfelet a hely-e. A hozzárendelés nélkül telepített ügyfeleket azonban addig nem felügyeli a rendszer, amíg sikeresen hozzá nem rendel egy helyet.  
 

> [!NOTE]  
>  Mindig rendelése a Configuration Manager azonos verzióját futtató webhelyek. Ne rendelje a Configuration Manager-ügyfél újabb verziójára a régebbi kiadást futtató helyhez.   Ha szükséges, frissítse az elsődleges hely ugyanazt a Configuration Manager verziót használó ügyfelek számára.  

Miután az ügyfelet helyhez rendeli, a hozzárendelés akkor is megmarad, ha az ügyfél megváltoztatja az IP-címét, és másik helyre barangol. Csak a rendszergazda manuálisan rendeli az ügyfelet egy másik helyre vagy az ügyfél hozzárendelésének megszüntetése.  

> [!WARNING]  
>  Kivételt jelent ez alól, ha egy aktív írási szűrőt használó Windows Embedded-eszközön lévő ügyfelet rendel helyhez. Ha nem tiltja le az írási szűrőket, mielőtt az ügyfelet helyhez rendelné, az ügyfél hely-hozzárendelési állapota az eszköz következő újraindításakor visszaáll az eredeti állapotba.  
>   
>  Ha például az ügyfélen automatikus helyhozzárendelés van beállítva, indításkor a hozzárendelés újra megtörténik – elképzelhető azonban, hogy másik helyhez. Ha az ügyfél nincs beállítva automatikus helyhozzárendelés, de manuális helyhozzárendelést ír elő, akkor manuálisan kell újra hozzárendelnie az ügyfél indítási kezeléséhez az ügyfelet újra Configuration Manager használatával.  
>   
>  A probléma elhárításához tiltsa le az írási szűrőket, mielőtt hozzárendelné az ügyfelet az Embedded-eszközökhöz, majd engedélyezze azokat, miután meggyőződött a helyhozzárendelés sikeréről.  

Ügyfél-hozzárendelés nem sikerül, ha az ügyfélszoftver telepítve marad, de nem lesznek kezelhetők. Az ügyfél akkor tekinthető felügyelet nélkülinek, ha telepítve van, de nincs helyhez rendelve, vagy helyhez van rendelve, de nem képes felügyeleti ponttal kommunikálni.  

##  <a name="using-manual-site-assignment-for-computers"></a>Manuális helyhozzárendelés használata számítógépekhez  
 Kétféle manuális módszerrel rendelhet ügyfélszámítógépet helyhez:  

-   A helykódot meghatározó ügyfél-telepítési tulajdonsággal.  

-   A Vezérlőpulton a **Configuration Manager**elemnél adja meg a hely kódját.  

> [!NOTE]  
>  Ha manuálisan rendel ügyfélszámítógépet nem létező Configuration Manager helykódot, a helyhozzárendelés sikertelen lesz.   

##  <a name="BKMK_AutomaticAssignment"></a> Automatikus helyhozzárendelés használata számítógépekhez  
 Az automatikus helyhozzárendelés történhet az ügyfél telepítésekor, vagy ha a Vezérlőpult **Configuration Manager – Tulajdonságok** elemnél a **Speciális** lapon a **Hely keresése** parancsra kattint. A Configuration Manager-ügyfél összehasonlítja saját hálózati helyét a Configuration Manager-hierarchiában konfigurált határokkal. Ha az ügyfél hálózati helye olyan határcsoporton belül van, amelyen a helyhozzárendelés engedélyezett, vagy a hierarchiához tartalék hely van beállítva, a rendszer automatikusan az adott helyhez rendeli az ügyfelet, anélkül, hogy ehhez helykódot kellene megadnia.  

 Határokat az alábbi elemekkel konfigurálhat:  

-   IP-alhálózat  

-   Active Directory-hellyel  

-   IPv6-előtaggal  

-   IP-címtartománnyal  

> [!NOTE]  
>  Ha a Configuration Manager-ügyfél több hálózati adapterrel rendelkezik, és következésképpen több IP-címmel rendelkezik, az ügyfél helyhozzárendelésének egy értékeléséhez használt IP-cím hozzá van rendelve véletlenszerűen.  

 A határcsoportok helyhozzárendeléshez való konfigurálására és a tartalék hely automatikus helyhozzárendeléshez való konfigurálására vonatkozó információért lásd: [Helyhatárok és határcsoportok megadása a System Center Configuration Managerben](../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

 Automatikus helyhozzárendelést használó Configuration Manager-ügyfelek megpróbálnak helyre a rendszer közzéteszi az Active Directory tartományi szolgáltatások határcsoportokat találni. Ha ez nem sikerül (például az Active Directory-séma nincs kibővítve a Configuration Manager vagy az ügyfél a következők munkacsoport-számítógépek), az ügyfelek érheti el a felügyeleti pont határcsoportra vonatkozó információkat.  

 Az ügyfélszámítógépek számára a telepítéskor is megadhatja a felügyeleti pontot, vagy az ügyfelek DNS-közzététel vagy WINS segítségével maguk is találhatnak egyet.  

 Ha az ügyfél nem talál olyan helyet, amely a saját hálózati helyét tartalmazó határcsoporthoz tartozik, és a hierarchiában nincs tartalék hely, az ügyfél 10 percenként újra próbálkozik, amíg a helyhozzárendelés sikerrel nem jár.  

 Configuration Manager ügyfélszámítógépeinek nem rendelhetők automatikusan helyhez, ha van ilyen a következő apply, és azok kell manuálisan rendelhetők:  

-   Ha már hozzá vannak rendelve egy helyhez.  

-   Az interneten keresztül csatlakoznak, vagy csak internetes ügyfélként vannak konfigurálva.  

-   Ha hálózati helyük nem tartozik bele a Configuration Manager-hierarchia egyik konfigurált határcsoportjába sem, és a hierarchiában nincs tartalék hely beállítva.  

##  <a name="completing-site-assignment-by-checking-site-compatibility"></a>Helyhozzárendelés végrehajtása a hely kompatibilitásának ellenőrzésével  
 Miután az ügyfél megtalálta a hozzárendelt helyről, a verzióra, és az ügyfél operációs rendszerének ellenőrzésével győződjön meg arról, hogy a Configuration Manager-hely felügyelheti. Például a Configuration Manager nem tudja kezelni a Configuration Manager 2007-ügyfelek, a System Center 2012 Configuration Manager-ügyfelek vagy a Windows 2000 rendszert futtató ügyfeleken.  

 Helyhozzárendelés sikertelen lesz, ha a Configuration Manager-hely Windows 2000 rendszert futtató ügyfelet. Ha a Configuration Manager 2007 vagy System Center 2012 Configuration Manager ügyfélszámítógépekhez rendel (aktuális ág) Configuration Manager-hely, a helyhozzárendelés sikeres, az automatikus ügyfélfrissítés támogatására. Azonban a régebbi generációs ügyfeleket nem frissíti (aktuális ág) a Configuration Manager-ügyfél, amíg a Configuration Manager nem képes felügyelni az ügyfelet ügyfélbeállításokkal, alkalmazások és szoftverfrissítések.  

> [!NOTE]  
>  A Configuration Manager 2007 vagy a System Center 2012 Configuration Manager ügyfelet (aktuális ág) Configuration Manager-hely hozzárendelésének támogatásához automatikus ügyfélfrissítést a hierarchia kell konfigurálnia. További információ: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

A Configuration Manager is ellenőrzi, hogy olyan helyhez, amely támogatja a Configuration Manager (aktuális ág) ügyfél hozzárendelve. A Configuration Manager korábbi verzióiról az áttelepítés során a következő esetekben fordulhat elő.  

-   Forgatókönyv: Az automatikus helyhozzárendelést használt, és a határai átfedésben vannak a megadott Configuration Manager korábbi verziójában.  

     Ebben az esetben az ügyfél automatikusan megpróbál (aktuális ág) Configuration Manager-hely található.  

     Az ügyfél először ellenőrzi az Active Directory tartományi szolgáltatásokban, és ha közzétett (aktuális ág) Configuration Manager-hely talál, a helyhozzárendelés sikeres lesz. Ha ez nem sikerül (például a Configuration Manager helye nincs közzétéve vagy a számítógép a munkacsoportba tartozó ügyfél), az ügyfél próbál helyre vonatkozó információkat a hozzárendelt felügyeleti pontról.  

    > [!NOTE]  
    >  Rendelhet felügyeleti pontot az ügyfélhez ügyfél telepítése során a Client.msi-tulajdonsággal **SMSMP =&lt;kiszolgáló_neve >**.  

     Ha egyik módszer sem jár sikerrel, a helyhozzárendelés meghiúsul, és manuálisan kell helyhez rendelnie az ügyfelet.  

-   Forgatókönyv: A Configuration Manager (aktuális ág) ügyfél hozzárendelt automatikus helyhozzárendelés helyett egy adott Helykód használatával, és véletlenül egy Configuration Manager verziója korábbi, mint a System Center 2012 R2 Configuration Manager hely kódját.  

     Ebben az esetben a helyhozzárendelés sikertelen lesz, és manuálisan újra hozzárendelnie az ügyfelet (aktuális ág) Configuration Manager-hely.  

 A hely kompatibilitási ellenőrzéséhez teljesülnie kell az alábbi feltételek egyikének:  

-   Az ügyfél hozzáférhet az Active Directory tartományi szolgáltatásokban közzétett helyadatokhoz.  

-   Az ügyfél képes kommunikálni egy felügyeleti ponttal a helyen.  

 Ha a hely kompatibilitási ellenőrzése sikertelen befejezése sikertelen volt, a helyhozzárendelés sikertelen lesz, és az ügyfél nem felügyelt marad, amíg a hely kompatibilitási ellenőrzése ismét elindul, és sikeres.  

 Ha az ügyfél internetes felügyeleti ponthoz van rendelve, Ebben az esetben nem helykompatibilitási ellenőrzés történik. Ha olyan helyhez társítja az ügyfeleket, amely internetes helyrendszereket tartalmaz, és internetes felügyeleti pontot ad meg, győződjön meg arról, hogy a megfelelő helyhez rendeli az ügyfelet. Ha véletlenül hozzárendelnie az ügyfelet a Configuration Manager 2007 helyen, a System Center 2012 Configuration Manager hely, vagy a Configuration Manager-hely, amely nem rendelkezik Internet alapú helyrendszer-szerepköröket, az ügyfél marad.  

##  <a name="locating-management-points"></a>Felügyeleti pontok megtalálása  
 A sikeres helyhozzárendelést követően az ügyfél felügyeleti pontot keres a helyen.  

 Az ügyfélszámítógépek töltik le, hogy csatlakozhassanak a hely felügyeleti pontok listáját. Ez akkor fordul elő, amikor az ügyfél valamennyi újraindulásakor, 25 óránként vagy, vagy ha az ügyfél, hálózatváltást észlel, mint például a számítógép bontja a kapcsolatot, és újra csatlakozik a hálózathoz, vagy egy új IP-címet kap. A lista az intranetes felügyeleti pontokat is tartalmazza, és arról is információval szolgál, hogy a felügyeleti pontok HTTP- vagy HTTPS-ügyfélkapcsolatokat fogadnak-e. Ha az ügyfélszámítógép az internethez csatlakozik, és az ügyfél még nem kapott listát a felügyeleti pontokról, abban az esetben a megadott internetes felügyeleti pontról kéri le a felügyeleti pontok listáját. Ha az ügyfél megkapta a hozzárendelt helyhez tartozó felügyeleti pontok listáját, kiválasztja, hogy melyikhez csatlakozzon:  

-   Ha az ügyfél az intraneten található, és érvényes, általa is használható PKI-tanúsítvánnyal rendelkezik, akkor a HTTPS-alapú felügyeleti pontokat részesíti előnyben a HTTP-alapú felügyeleti pontokkal szemben. Ezt követően erdőtagság alapján megkeresi a legközelebbi felügyeleti pontot.  

-   Ha az ügyfél csatlakozik az internethez, akkor véletlenszerűen kiválasztja az egyik az Internet alapú felügyeleti pontokat.  

Mobileszköz-ügyfelek, a Configuration Manager által beléptetett csak csatlakozik egy felügyeleti pont a hozzájuk rendelt helyen, és soha nem csatlakoznak másodlagos helyen található felügyeleti pontokhoz. Ezek az ügyfelek mindig HTTPS-kapcsolaton keresztül csatlakoznak, a felügyeleti pontnak pedig fogadnia kell az internetes ügyfélkapcsolatokat. Ha egynél több felügyeleti pontot az elsődleges hely a mobileszközre telepített ügyfelekre vonatkozó, a Configuration Manager véletlenszerűen úgy dönt, egyet a hozzárendelési és a mobileszközön lévő ügyfél során továbbra is használja ugyanezt a felügyeleti pontot.  

Ha az ügyfél letöltött egy ügyfélházirendet a hely valamelyik felügyeleti pontjáról, akkor az ügyfél felügyelet alatt áll.  

##  <a name="downloading-site-settings"></a>Helybeállítások letöltése  
 A sikeres helyhozzárendelést és a felügyeleti pont megtalálását követően a helykompatibilitási ellenőrzéshez Active Directory tartományi szolgáltatásokat használó ügyfélszámítógép letölti az ügyfélhez kapcsolódó helybeállításokat a hozzárendelt helyhez. E beállítások közé tartoznak az ügyféltanúsítvány kiválasztási feltételei, a visszavont tanúsítványok listájának használata, illetve az ügyfélkérelmekhez használt portszámok. Az ügyfél rendszeresen ellenőrzi ezeket a beállításokat.  

 Ha az ügyfélszámítógép nem tud helybeállításokat lekérni az Active Directory tartományi szolgáltatásokból, a felügyeleti pontról fogja letölteni azokat. Ügyfélszámítógépek ügyfélleküldéses telepítéskor, vagy megadhatja őket manuálisan a CCMSetup.exe és ügyfél-telepítési tulajdonságokkal is beszerezhető a hely beállításait. További információ az ügyfél telepítési tulajdonságairól: [Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md).  

##  <a name="downloading-client-settings"></a>Ügyfélbeállítások letöltése  
 Minden ügyfél letölti az alapértelmezett ügyfél-beállítási házirendet, valamint az esetlegesen rá vonatkozó egyéni ügyfél-beállítási házirendeket is. A Szoftverközpont Windows rendszerű számítógépek esetén ezeket az ügyfél-konfigurációs házirendeket alkalmazza, és értesíti a felhasználót arról, hogy a Szoftverközpont sikeres működésének feltétele e konfigurációs információk letöltése. Az ügyfél konfigurált beállításaitól függően az ügyfélbeállítások első letöltése hosszabb időt is igénybe vehet, és egyes ügyfél-felügyeleti feladatok nem futnak addig, amíg a folyamat be nem fejeződik.  

##  <a name="verifying-site-assignment"></a>Helyhozzárendelés ellenőrzése  
 Hely hozzárendelés sikerült a következő módszerek bármelyikével ellenőrizheti:  

-   Az ügyfelek Windows rendszerrel működő számítógépeken, a Configuration Manager használja a Vezérlőpult, és ellenőrizze, hogy a hely kódja helyesen jelenik meg a **hely** fülre.  

-   Az ügyfélszámítógépek a a **eszközök és megfelelőség** munkaterület > **eszközök** csomópont, győződjön meg arról, hogy megjelenik-e a számítógép **Igen** a a **ügyfél** oszlopban pedig az elsődleges hely helyes helykódja a **Helykód** oszlop.  

-   Mobileszközök esetén az **Eszközök és megfelelőség** munkaterületen használja a **Minden mobileszköz** gyűjteményt annak ellenőrzésére, hogy az **Igen** jelenik-e meg az **Ügyfél** oszlopban, a **Helykód** oszlopban pedig az elsődleges hely helyes helykódja látható-e.  

-   Használja az ügyfélhozzárendelések és a mobileszközök beléptetési jelentéseit.  

-   Ügyfélszámítógépek esetén használja az ügyfél LocationServices.log fájlját.  

##  <a name="roaming-to-other-sites"></a>Barangolás másik helyre  
 Ha az ügyfélszámítógépek az intraneten az elsődleges helyhez vannak hozzárendelve, de a hálózati helyük úgy változik meg, hogy másik helyhez konfigurált határcsoportba kerülnek, akkor azok másik helyre barangoltak. Ha ez a hely az elsődleges helyük másodlagos helye, az ügyfelek használhatják a felügyeleti pontot a másodlagosban, hogy letöltsék az ügyfélházirendet, és feltöltsék az ügyféladatokat, elkerülve ezzel, hogy ezek az adatok egy esetleg lassú hálózaton legyenek elküldve. Ha azonban ezek az ügyfelek egy másik elsődleges helynek vagy olyan másodlagos helynek a határai közé esnek, amelyik nem a hozzárendelt elsődleges helyük alárendelt helye, akkor ezek az ügyfelek mindig a hozzárendelt helyükön lévő felügyeleti pontot használják, hogy letöltsék az ügyfélházirendet, és feltöltsék az ügyféladatokat a helyükre.  

 Ezek az ügyfélszámítógépek, amelyek másik helyre barangolnak (az összes elsődleges és másodlagos helyet is beleértve) a tartalom helylekéréséhez mindig használhatják a másik helyen lévő felügyeleti pontokat. Az aktuális helyen lévő felügyeleti pontok elláthatják az ügyfeleket azon terjesztési pontok listájával, amelyeknél az ügyfél által lekért tartalom megtalálható.  

 Kizárólag internetes ügyfélfelügyeletre, és a mobileszközök konfigurált ügyfélszámítógépek és a Configuration Manager által beléptetett Mac számítógépek esetén az ügyfelek csak kommunikálnak a hozzájuk rendelt hely felügyeleti pontokat. Ezek az ügyfelek sosem kommunikálnak a másodlagos helyeken lévő, vagy más elsődleges helyeken lévő felügyeleti ponttal.  

