---
title: Az Azure Configuration Manager |} Microsoft Docs
description: "A Configuration Manager környezetet az Azure használatával kapcsolatos információkat."
ms.custom: na
ms.date: 03/27/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5276ad999fc871496d79e6efff34d5edc6335380
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>A Configuration Manager az Azure - gyakran ismételt kérdések
*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbi kérdések és válaszok segítségével megtudhatja, hogy mikor érdemes használni, és a Microsoft Azure Configuration Manager konfigurálása.

## <a name="general-questions"></a>Általános kérdések
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>A vállalat próbál áthelyezi a Microsoft Azure, a lehető sok fizikai kiszolgálón is I Configuration Manager-kiszolgálók áthelyezése az Azure-bA?
Biztosan Ez egy webfarmos támogatott.  Lásd: [virtualizálási környezetek támogatása a System Center Configuration Manager](/sccm/core/plan-design/configs/support-for-virtualization-environments).

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>nagyszerű! A környezet több helyre van szükség. Minden elsődleges gyerekhelyén kell az Azure-ban a központi adminisztrációs hely vagy a helyszínen? Mi a helyzet a másodlagos helyek?
Pont-pont kommunikáció (fájlalapú és adatbázis-replikálás) az Azure-ban üzemeltetett közelében előnyeivel. Azonban az összes ügyfél kapcsolódó forgalom távoli Helykiszolgálók és helyrendszerek lenne. Ha egy adatforgalmi Azure és az intranet között gyors és megbízható hálózati kapcsolatot használ, az Azure-ban a infrastruktúrát szolgáltató lehetőség.

Azonban ha használnia, mért adatforgalmi és rendelkezésre álló sávszélesség vagy költség problémát jelent, vagy a hálózati kapcsolatot az Azure és az intranet nincs gyors, vagy nem megbízható, fontolja meg adott helyek (és a helyrendszerek) helyezi el a helyszíni és a Configuration Manager beépített sávszélesség vezérlők.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Nehézségekkel Configuration Manager az Azure-ban egy SaaS-forgatókönyv (szolgáltatott szoftver)?
Nem, akkor az IaaS (szolgáltatott infrastruktúra) mert működteti a Configuration Manager infrastruktúra-kiszolgálók az Azure virtuális gépeken.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Milyen területeken I ügyelnie kell annak eldöntéséhez, hogy az Azure-bA a Configuration Manager infrastruktúra áthelyezésre?
Nagyszerű kérdést, itt a területeit legfontosabb ehhez a döntéshez meghozásakor, hogy az egyes van írja le egy külön című szakaszát:
1.    Hálózat
2.    Elérhetőség
3.    Performance (Teljesítmény)
4.    Költség
5.    Felhasználói élmény

## <a name="networking"></a>Hálózat
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>Mi a helyzet hálózati követelményei, a használandó expressroute-on vagy egy Azure VPN Gateway?
Hálózatkezelés-e egy nagyon fontos döntés. Hálózati sebességek mellett és a késleltetés hatással lehet a helykiszolgáló és a távoli helyrendszerek és bármely ügyfél-kommunikáció a helyrendszerekkel között funkcióval. Azt javasoljuk, hogy az ExpressRoute használja. Azonban a Configuration Manager korlátozás arra vonatkozóan, megakadályozza az Azure VPN Gateway használatával. Gondosan tekintse át a követelmények (teljesítmény, javítását, a szoftverek terjesztéséhez, operációs rendszerek központi telepítésének) az infrastruktúra kell, és végezze el a döntés. Szempontokat kell figyelembe venni az egyes megoldások a következők:

 - **ExpressRoute** (ajánlott)
  - Az Adatközpont (lehet összekötni több adatközpontot) természetes bővítménye
  - Azure adatközpontjaiban és az infrastruktúra közötti magánhálózati kapcsolatok
  - A nyilvános interneten keresztül nem használható
  - Megbízhatóság, adatátviteli sebesség, kisebb késést biztosít, a fokozott biztonságot nyújt
  - Legfeljebb 10 GB/s sebességű és korlátlan Data ajánlatokat beállítások megtervezése
 - **VPN-átjáró**
  - Hely-a-site/pont-hely VPN
  - Forgalom a nyilvános interneten keresztül halad
  - Használja az IP-biztonság (IPsec) és az internetes kulcscsere (IKE)

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute van például sok különböző beállításokról és a forgalmi díjas, különböző sebességű beállításokat és a prémium szintű bővítmény korlátlan. Amely válasszam?
A kiválasztott beállítások a forgatókönyv webkiszolgálókból függ, és mennyi adat kívánja terjeszteni. Helykiszolgálókon és terjesztési pontjai között szabályozhatja a Configuration Manager adatátvitelt, de nem vezérelhető a helyek kiszolgáló helyrendszer kiszolgáló közötti kommunikációra.   Használata esetén a díjköteles adatforgalom terv helyezi el a megadott helyek (és a helyrendszerek) a helyszíni és a segítségével [Configuration Manager beépített sávszélesség-vezérlés](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) Azure költségeinek szabályozni.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>Mi a helyzet a telepítési követelményeknek, például az Active Directory-tartományok? Meg kell-e a helyrendszer-kiszolgálók csatlakoztatása egy Active Directory-tartományhoz?
igen. Amikor helyezi át az Azure-ba, a [által támogatott konfigurációk](/sccm/core/plan-design/configs/supported-configurations) változatlan marad, beleértve a Configuration Manager telepítésének Active Directory követelményeit.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>Tudomásul veszem, hogy a helyrendszer-kiszolgálók csatlakoztatása egy Active Directory-tartományhoz kell, de használható Azure Active Directory?
Azure Active Directory jelenleg nem, nem támogatott. A helykiszolgálóknak továbbra is tagjának kell lennie egy [Windows Active Directory-tartomány](/sccm/core/plan-design/configs/support-for-active-directory-domains).



## <a name="availability"></a>Elérhetőség
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>A magas rendelkezésre állás ígéret a okai vagyok áthelyezése infrastruktúra az Outlook az Azure-bA. Lehet például az Azure virtuális gép rendelkezésre állási készletek virtuális gépekhez, amelyek használom a Configuration Manager magas rendelkezésre állású lehetőség előnyeinek kihasználása?
igen! Az Azure virtuális gép rendelkezésre állási készletek redundáns helyrendszerszerepkörök például terjesztési vagy felügyeleti pontokat is használható.

Is használhatja őket a Configuration Manager helyrendszer-kiszolgálók. Például a központi adminisztrációs helyek és elsődleges helyek lehetnek a a azonos rendelkezésre állási csoportot, amely segítségével győződjön meg arról, hogy azok nem újraindítása van egy időben.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>Hogyan lehet az adatbázis magas rendelkezésre állású? Használható az Azure SQL Database? Vagy konfigurálnom kell a Microsoft SQL Servert használja a virtuális gépen?
Szeretné használni a Microsoft SQL Server virtuális gépen. A Configuration Manager nem támogatja az Azure SQL Server jelenleg. De az SQL server AlwaysOn rendelkezésre állási csoportok például funkciók is használhatja. [AlwaysOn rendelkezésre állási csoportok](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database) használata ajánlott, és a Configuration Manager 1602-es verziójától kezdve hivatalosan támogatott.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Használható Azure load Balancer terheléselosztók helyrendszer-szerepköröket, például a felügyeleti pontokat vagy a szoftverfrissítési pontokat?
A Configuration Manager átlátható az alkalmazás működésének esetén nem lett tesztelve az Azure load Balancer terheléselosztók, amíg nem rendelkezhet normál működésre állapotot okoz.


## <a name="performance"></a>Performance (Teljesítmény)
### <a name="what-factors-affect-performance-in-this-scenario"></a>Ható tényezők hatása a teljesítményre ebben a forgatókönyvben?
[Az Azure virtuális gép méretét és típusát](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), Azure virtuális lemezek (prémium szintű storage ajánlott, különösen az SQL Server), hálózati késés, és sebességét, a legfontosabb területek.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>Igen további tudnivalók az Azure virtuális gépek; milyen méretű virtuális gépek érdemes használni?
Általában a számítási teljesítmény (Processzor és memória) meg kell felelniük a [ajánlott hardver a System Center Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware). De vannak rendszeres számítógép hardvereszközeiről, illetve az Azure virtuális gépek közötti eltérések, különösen akkor, ha ismét a lemezeket a a virtuális gépek használatát.  Milyen méretű virtuális gépek használata a környezet méretétől függ, de az alábbiakban néhány javaslatot:
- Az üzemi környezetek bármilyen jelentős méretű ajánlott "**S**" osztályban Azure virtuális gépeken. Ennek oka az, prémium szintű Storage lemezeket is kihasználja.  Virtuális gépek használata nem "S" osztály blob-tároló, és általában nem teljesítmény követelményeknek megfelelő elfogadható termelési élményt szükséges.
- Több Premium tárolólemezek legyen nagyobb méretezéshez használt, és a maximális IOPS a Windows Lemezkezelés segédprogramban csíkozott.  
- Javasoljuk, hogy jobban használatával, vagy több premium lemezek során a kezdeti helyen történő központi telepítés (például P30 P20, és a 1xP30 helyett a csíkozott kötetek 2xP30 helyett). Majd ha a webhely később kell a Virtuálisgép-méretet további terhelés miatt hatékonyságának növeléséhez, kihasználhatja a további CPU és memória, amely nagyobb Virtuálisgép-méretet biztosít. Akkor is lemezek már, amely kihasználhatja a további IOPS-teljesítmény, amely lehetővé teszi, hogy a nagyobb Virtuálisgép-méretet.



Az alábbi táblázatok a kezdeti javasolt lemez számát az elsődleges és a központi adminisztrációs helyeken különböző méretű telepítések használatára:

**A Helyadatbázis ugyanott** -elsődleges vagy központi felügyeleti hely a Helyadatbázis, a helykiszolgálón:

| Asztali ügyfelek    |Ajánlott Virtuálisgép-mérettel|Ajánlott lemezek|
|--------------------|-------------------|-----------------|
|**Legfeljebb 25-k**       |   DS4_V2          |2xP30 (csíkozott)  |
|**25-k – 50-k**      |   DS13_V2         |2xP30 (csíkozott)  |
|**50-k a 100-k**     |   DS14_V2         |3xP30 (csíkozott)  |


**Távoli helyadatbázissal** -elsődleges vagy központi felügyeleti hely a Helyadatbázis egy távoli kiszolgálón:

| Asztali ügyfelek    |Ajánlott Virtuálisgép-mérettel|Ajánlott lemezek |
|--------------------|-------------------|------------------|
|**Legfeljebb 25-k**       | Helykiszolgáló: F4S </br>Adatbázis-kiszolgáló: DS12_V2 | Helykiszolgáló: 1xP30 </br>Adatbázis-kiszolgáló: 2xP30 (csíkozott)  |
|**25-k – 50-k**      | Helykiszolgáló: F4S </br>Adatbázis-kiszolgáló: DS13_V2 | Helykiszolgáló: 1xP30 </br>Adatbázis-kiszolgáló: 2xP30 (csíkozott)   |
|**50-k a 100-k**     | Helykiszolgáló: F8S </br>Adatbázis-kiszolgáló: DS14_V2 | Helykiszolgáló: 2xP30 (csíkozott)   </br>Adatbázis-kiszolgáló: 3xP30 (csíkozott)   |

Az alábbiakban látható egy példa konfiguráció 50-k – 100k ügyfelek DS14_V2 3xP30 lemezzel rendelkező önálló csíkozott köteteken lévő logikai kötetek a Configuration Manager telepítése és az adatbázis-fájlok:  ![Virtuális gép) lemezek](media/vm_disks.png)  



## <a name="user-experience"></a>Felhasználói élmény
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>Említse meg, hogy a felhasználói élmény egyike a fő területet, fontos, miért van, amely?
A döntéseit hálózatkezelés, a rendelkezésre állási, a teljesítmény, és ha helyezi-e a Configuration Manager-Helykiszolgálók hatással lehet a felhasználók közvetlenül. Úgy véljük, Azure az áthelyezési kell lennie a felhasználók számára átlátható, hogy a napi kapcsolati a Configuration Manager változás nem az ügyfeleken.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>Az OK gombra jelenik meg azt. I szeretne egyetlen önálló elsődleges hely telepítése Azure virtuális géphez, és győződjön meg arról, hogy a költségek pedig alacsonyak legyenek szeretnék. Kell (távoli) helyrendszer rendszerek (például a felügyeleti pontok, a terjesztési pontok és a szoftverfrissítési pontok frissítése) is helyezze az Azure virtuális gépek és vagy a helyszínen?
A terjesztési pontok és a helyrendszer-kiszolgáló közötti kommunikáció, kivéve a kiszolgáló és a kiszolgáló közötti kommunikáció, egy helyen akkor fordulhat elő, tetszőleges időpontban, és ne használja mechanizmusok a hálózati sávszélesség használatának szabályozására. Mivel a helyrendszerek közötti kommunikációt nem szabályozhatja, ezek a kommunikációk társított költségekre figyelembe kell venni.

Hálózati sebességek mellett és a késés is is figyelembe veendő tényezőket ismertetjük. Lassú vagy megbízhatatlan hálózat jelentős hatással lehet a helykiszolgáló és a távoli helyrendszerek között funkciókat is bármely ügyfél-kommunikáció a helyrendszerekkel. A felügyelt ügyfelek, amelyek egy adott helyrendszer, valamint a funkcióra aktívan számát figyelembe kell venni.
Általánosságban elmondható használhatja a szokásos útmutató vonatkozik WAN-kapcsolatok és a helyrendszerek kiindulási pontként. Ideális esetben a hálózati teljesítményt, az adott Azure és az intranet között kap, amely jó kapcsolat gyors hálózat WAN konzisztens lesz.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>Mi a helyzet a tartalom terjesztése és a tartalomkezelésről? Normál terjesztési pontokat kell Azure vagy a helyszínen, és érdemes használni a BranchCache vagy lekéréses terjesztési pontok a helyszíni? Vagy kell-e még a felhőalapú terjesztési pontok kizárólagos használata?
A megoldás a Tartalomkezelés, sokkal ugyanaz, mint a Helykiszolgálók és helyrendszerek.
- Ha egy adatforgalmi Azure és az intranet között gyors és megbízható hálózati kapcsolatot használ, az Azure-ban a normál terjesztési pontokat üzemeltető lehet beállítást.
-  Ha díjköteles adatforgalom terv és a sávszélesség költségekkel fontos, vagy a hálózati kapcsolatot az Azure és az intranet nincs gyors, vagy nem megbízható, akkor érdemes valamilyen más megoldások. Ezek közé tartozik a standard megkeresése, vagy a lekéréses terjesztési pontok, a helyszíni, valamint a BranchCache szolgáltatás használatával. A felhő alapú terjesztési pontok használata is egy beállítást, de vannak bizonyos korlátai tartalomtípusokat támogatott (például szoftvercsomagok frissítések nem támogatottak).

> [!NOTE]
>  PXE-támogatás szükség, ha a helyszíni terjesztési pontokra (standard vagy lekéréses) rendszerindítási kérésekre való válaszolás kell használnia. [A WDS jelenleg nem támogatott az Azure virtuális gépeken futó futtatásához](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>A felhő alapú terjesztési pontok korlátozásokkal vagyok OK gombra, amíg nem szeretnék a felügyeleti pont üzembe DMZ, annak ellenére, hogy az internetes ügyfelek támogatásához van szükség. A további beállításokat kell?
igen! A Configuration Manager verziója 1610, az azt bevezetni a [felhő adatkezelési átjáró](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) kiadás előtti szolgáltatásként. (Ez a szolgáltatás jelent meg először a technikai előzetes verzióra 1606 a [Felhőbeli proxyszolgáltatás](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)).

A **felhő adatkezelési átjáró** kezelése a Configuration Manager-ügyfelek az interneten lévő egyszerű módszert kínál. A szolgáltatást, amely a Microsoft Azure telepít, és az Azure-előfizetés szükséges, a helyi Configuration Manager-infrastruktúrát, a felhő felügyeleti átjáró összekötőpontja nevű új szerepkör alapján csatlakozik. Miután telepítve van, és konfigurálva, az ügyfelek hozzáférhetnek a helyi Configuration Manager helyrendszer-szerepkörök függetlenül attól, hogy van csatlakoztatva a belső magánhálózaton vagy az interneten.

Indítsa el a felhő adatkezelési átjáró használata a környezetben, és küldjön visszajelzést élvezetesebbé tegyük ezt. Előzetes kiadású szolgáltatások kapcsolatos információkért lásd: [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates).

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>Hallottam is, hogy rendelkezik-e egy másik új szolgáltatás társ-gyorsítótárazás kiadás előtti szolgáltatásként 1610 verzióban bevezetett nevezik. Eltér, hogy a BranchCache? Azt, amelyiket válasszam?
Igen, illeszkedő. [Gyorsítótár partnert](/sccm/core/plan-design/hierarchy/client-peer-cache) van 100 %-os natív Configuration Manager-technológia, amelyben a BranchCache csak a Windows. Mindkét lehet hasznos. A BranchCache által a szükséges tartalom található, mivel a társ-gyorsítótárazás konfigurációs kezelők normál terjesztési munkafolyamat és a határ csoport-beállításokat használja.

Beállíthatja, hogy minden ügyfél a társ-gyorsítótárazási forrásként. Majd, amikor a felügyeleti pontok az ügyfelek a tartalom forráshelyét vizsgáló kapcsolatos adatok megadása, biztosítanak mind a terjesztési pontokat, és egyetlen társ-gyorsítótárazási forrás, amely megtalálható a tartalom részleteit, hogy az ügyfél igényel.


## <a name="cost"></a>Költség
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>OK arról, hogy egy kicsit kapcsolatos költségek. Ez lesz a költséghatékony megoldást jelent a számomra?
Tegyük fel például, mivel minden környezet nehezen nem egyezik. A legjobb hozzá kell, hogy a környezet használatával a Microsoft Azure díjkalkulátor költség: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>További források
**– Alapok:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Az Azure virtuális gépek típusainak:**
 - Az Azure méreteket: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - Virtuális gépek díjszabása: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - Storage szolgáltatás díjszabása: http://azure.microsoft.com/pricing/details/storage/

**Lemez teljesítménnyel kapcsolatos szempontok:**    
 - Prémium szintű lemez Bevezetés: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - Prémium szintű lemez mélyebb információ: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - A maximális méretek és a Teljesítményfigyelő diagramok praktikus gyűjteményét célozza tárolás: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Egy másik bevezetés + néhány cool uber-geek adatok prémium szintű Storage működéséről a magában foglalja az mögött: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**Rendelkezésre állás:**
 - Az Azure infrastruktúra-szolgáltatási hasznos üzemidő SLA tartozó: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - Rendelkezésre állási csoportok ismertetése: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**Kapcsolat:**
 - Útvonal Visual Studio Express. Az Azure VPN: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Express Route árképzési: http://azure.microsoft.com/pricing/details/expressroute/
 - További információk az Express Route: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 

