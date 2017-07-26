---
title: "Elavult funkciók |} Microsoft Docs"
description: "További tudnivalók a funkciókat, termékeket és operációs rendszereket, a System Center Configuration Manager többé nem támogatja."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 57b9ab13bda0bb5fa5139e52a4c55ef9524e4097
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>A System Center Configuration Manager megszűnt és elavult funkciói

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ismerteti a funkciókat, termékeket és operációs rendszerek a System Center Configuration Manager támogatási el lesznek távolítva, vagy eltávolítja az egy későbbi kiadásban (elavult). Ez lehetővé teszi a korai értesítés kapcsolatos változásokról, amelyek hatással lehetnek a Configuration Manager használatára.  

Ezek az adatok a jövőbeni kiadásokban változhat, és nem feltétlenül tartalmaznak minden elavult funkció, a termék vagy az operációs rendszer.  

## <a name="how-to-use-this-information"></a>Ezek az információk használata  
Ha egy szolgáltatás vagy az operációs rendszer először történő használata elavult, a Configuration Managerrel használná támogatása el kell távolítani egy jövőbeli verziójában a Configuration Manager van ütemezve. Ezen információ segítségével tervezheti meg az adott szolgáltatás vagy az operációs rendszer más. Az első a Configuration Manager verziókban a, amelyhez az adott támogatottak, ha ez a témakör azt jelzi, hogy bizonyos verzióra frissül.  

Egy szolgáltatás vagy az operációs rendszer támogatási eltávolítása után a szolgáltatás vagy az operációs rendszer továbbra is támogatja a Configuration Manager korábbi verziója használatakor mindaddig, amíg a Configuration Manager verzió támogatására. Azonban a Configuration Manager verziója, amely a dátum után mező vagy a megjelölt verzió használata esetén, hogy a Configuration Manager verziója nem támogatja.

Például ha egy funkció eltávolítása, annak támogatásához lett ütemezve 2016 szeptemberétől, az adott funkcióhoz tartozó támogatási. után kiadott első frissítés volna már nem szerepelnek, amely a 2016. októberi 1610, frissítés.
-  A frissítés 1610 a szolgáltatás akkor többé nem támogatjuk az.
-  Ez a témakör frissítése történne támogatása el lett távolítva, 1610 verziójával jelzi.
Azonban ha továbbra is használhatja, amely támogatja a szolgáltatást, például az 1602-es vagy 1606, verziója régebbi, továbbra is használhatja, hogy a szolgáltatás Ön által használt verzióhoz elutasítja azokat a nem támogatott.

További információkért lásd:
 - A [Microsoft terméktámogatási ciklus](https://support.microsoft.com/lifecycle) webhelyet.
 - [A Configuration Manager aktuális ág verziói támogatása](/sccm/core/servers/manage/current-branch-versions-supported).




## <a name="deprecated-operating-systems"></a>Elavult operációs rendszerek
### <a name="server-operating-systems"></a>Kiszolgálói operációs rendszerek  

|**Operációs rendszerek**|**Támogatás megszüntetésének bejelentése**|**Támogatás megszüntetve** |  
|-|-|-|  
|Windows Server 2008|2015. július 10.|1511-es verzió </br></br>Egy helyrendszer eltávolítása is támogatják. (Lásd az 1. megjegyzés).|  
|Windows Server 2008 R2|2015. július 10.| Verzió 1702 (lásd a 2. megjegyzést)|  

-   1. Megjegyzés: Ez az operációs rendszer nem támogatott a helykiszolgálókon vagy helyrendszer-szerepkörök a terjesztési pont és a lekéréses terjesztési pontok kivételével. Továbbra is használható az operációs rendszer terjesztési pontként, amíg ez a támogatás elavulásának bejelentéséig, illetve az operációs rendszer kiterjesztett támogatási időszakának lejártáig. További információkért lásd: [a System Center Configuration Manager CB telepítési és LTSB nem sikerül, a Windows Server 2008](https://support.microsoft.com/help/4015095).

-   2. Megjegyzés:    1702 verziójával kezdve ez az operációs rendszer nem támogatott a Helykiszolgálók, sem a legtöbb helyrendszerszerepkör, azonban 1702 korábbi verziók továbbra is használható. Ez az operációs rendszer támogatott maradnak, az állapotáttelepítési pont és terjesztési pont helyrendszer-szerepkör (beleértve a lekéréses terjesztési pontok, és a PXE és csoportos küldés) Ez a támogatás elavulásának bejelentéséig, illetve az operációs rendszer kiterjesztett támogatási időszakának lejártáig. 1602-es verziójától kezdve, frissítheti az operációs rendszer Windows Server 2012 R2 a Windows Server 2008 R2 a helykiszolgáló helyi.  

     A helykiszolgáló operációs rendszerének helyszíni frissítését kapcsolatos további információkért tekintse meg a [az operációs rendszer Windows Server 2008 R2 rendszerű Helykiszolgálók helyben végzett verzióváltása](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) szakasz [a System Center Configuration Managerben történt változások](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).



### <a name="client-operating-systems"></a>Ügyféloldali operációs rendszerek  

 Hacsak másként nem jelezzük, minden egyes Configuration Manager-ügyfélként támogatott operációs rendszer csak a kiterjesztett támogatás záró dátuma adott operációs rendszeren támogatott. Kibővített támogatás záró dátumát, lásd: a [Microsoft terméktámogatási ciklus](https://support.microsoft.com/lifecycle). Ha egy operációs rendszer a Configuration Manager támogatása véget ér a kiterjesztett támogatás lejárati dátuma előtt, egy megszűnésének dátumát, illetve támogatása az operációs rendszer megjelenik itt.  

|**Operációs rendszerek**|**Támogatás megszüntetésének bejelentése**|**Támogatás megszüntetve**|  
|-|-|-|  
|Windows XP|2015. július 10.|1511-es verzió|  
|Windows XP Embedded|2015. július 10.|1702 verziója|  
|Windows Server 2003|2015. július 10.|1511-es verzió|  
|Windows Server 2003 R2|2015. július 10.|1511-es verzió|  
|Windows Vista|2015. július 10.|1511-es verzió|  
|Mac OS X 10.6-10.8|2015. július 10.|1511-es verzió|  
|Windows Mobile 6.0-6.5|2015. július 10.|1511-es verzió|  
|Nokia Symbian Belle|2015. július 10.|1511-es verzió|  
|Windows CE 5.0-6.0|2015. július 10.|1511-es verzió|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Helyadatbázis az SQL Server-verziók elavult támogatása  

|**SQL Server-verziók**|**Támogatás megszüntetésének bejelentése**|**Támogatás megszüntetve**|   
|-|-|-|  
|SQL Server 2008|2015. július 10.|1511-es verzió|  
|SQL Server 2008 R2|2015. július 10.|1702 verziója|  

Ha frissítenie kell az SQL Server verziója, az alábbi módszerek, az összetett könnyen ajánlott.
1. [Frissítse az SQL Server helyi](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (ajánlott).
2. SQL Server új verziójának telepítése egy új számítógépre, majd [használja a datbase move beállítást](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) a Configuration Manager telepítőjét a helykiszolgáló mutasson az új SQL Server.
3. Használjon [biztonsági mentési és helyreállítási](/sccm/protect/understand/backup-and-recovery).


## <a name="deprecated-features"></a>Elavult funkciók  

|**Szolgáltatás**|**Támogatás megszüntetésének bejelentése**|**Támogatás megszüntetve**|  
|-|-|-|  
|Hálózatvédelem (NAP) - nek System Center 2012 Configuration Manager|2015. július 10.|1511-es verzió|  
|Sávon kívüli felügyelet - nek System Center 2012 Configuration Managerben|2015. október 16.|1511-es verzió|
|Feladatütemezések: <br /> -OSDPreserveDriveLetter  <br /><br /> Az operációs rendszer központi telepítése során alapértelmezés szerint a Windows telepítő most meghatározza, hogy a legjobb meghajtóbetűjel (általában a C:) használatára. Adjon meg egy másik meghajtót használni szeretne, ha a hely az operációs rendszer alkalmazása feladatütemezési lépés a módosíthatja. Lépjen a **válassza ki a helyet, ahová szeretné alkalmazni az operációs rendszer** beállításnál válassza **adott logikai meghajtó betűjelét**, és válassza ki a használni kívánt meghajtót. |2016. június 20. |1606 verziója |
|Feladatütemezések: <br /> -Lemez konvertálása dinamikus lemezzé <br /> -A központi telepítés eszközeinek telepítése |2016. november 18.|A feladat támogatása végpontok 2017. június 1. után kiadott első frissítés megjelenésével feladatütemezések.|
|A Szoftverközpont új, modern megjelenéssel rendelkezik. Megjelentek a Silverlight-függő Alkalmazáskatalógusban (a felhasználók számára elérhető alkalmazások) csak a most alkalmazások megjelenjenek a Szoftverközpontban, a a **alkalmazások** fülre. Az Alkalmazáskatalógus továbbra is elérhető a hivatkozásra kattint a **telepítési állapotát** szoftverközpont fülre.<br><br>Az elkövetkező hónapokban az előző verziójú Szoftverközponthoz már nem lesz elérhető.<br><br>Az új Szoftverközpont használata az ügyfélbeállítás engedélyezésével ügyfelek állíthat be **Számítógépügynök** > **új Szoftverközpont használata**.<br><br>További információ a Szoftverközpont: [tervezése és az Alkalmazáskezelés konfigurálása a System Center Configuration Managerben](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|2016. december 13.|A bejelentések|
|Virtuális merevlemezek (VHD-k) a Configuration Manager kezelése. </br></br>Ez magában foglalja az új virtuális merevlemez létrehozása vagy kezelése feladatütemezés használatával virtuális merevlemez beállítások eltávolítása, és a virtuális merevlemezek csomópontot a Configuration Manager konzol eltávolítását. </br></br>Ez a támogatás eltávolítása után a meglévő VHD-k nem törlődik, de már nem lesz a Configuration Manager-konzolon belülről érhetők el.  |2017. január 6. |Virtuális merevlemezek végpontok 2017. június 1. után kiadott első frissítés megjelenésével támogatása.|
|A System Center Configuration Manager Frissítésfelmérő eszköz. </br></br>A Frissítésfelmérő eszközt a System Center Configuration Manager és az alkalmazáskompatibilitási eszközkészlet (ACT) függ 6.x. A Windows 10 v1511 ADK teljesített ACT végleges verziójú. Mert lesz nincsenek további frissítések el, a Frissítésfelmérő eszközt támogatása megszűnik. </br></br>A Frissítésfelmérő eszközt helyébe a [frissítési készültségének](/sccm/core/clients/manage/upgrade/upgrade-analytics) szolgáltatás. A érvénytelenítése figyelje meg lett adva a [letöltési oldalának UAT](https://www.microsoft.com/download/details.aspx?id=37145) 9/12/2016. |9/12/2016  | 2017. július 11. |  


<br></br>
További részletek a szolgáltatások eltávolítása, System Center Configuration Manager-kiadás 1511-es verziója:

###  <a name="bkmk_amt"></a>Sávon kívüli felügyelet  
 A Configuration Managerrel, a natív támogatást az AMT-alapú számítógépeknek a Configuration Manager konzolon belül el lett távolítva.  

-   AMT-alapú számítógépek továbbra is teljes körűen felügyelt, használatakor a [Intel SCS-bővítmény a Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). A bővítmény elérhetővé teszi a legújabb funkciókat az AMT felügyelete során a Configuration Manager áthidalja ezeket a módosításokat bevezetéséig érvényben.  

-   Sávon kívüli felügyeletre a System Center 2012 Configuration Manager nem érinti ez a változás.  

###  <a name="bkmk_nap"></a>Hálózati hozzáférés-védelem  
 A System Center Configuration Manager többé nem támogatja a hálózati hozzáférés-védelem. A funkció a Windows Server 2012 R2 elavult, és a rendszer eltávolítja a Windows 10-es.  

 A hálózati hozzáférés-védelem egyéb alternatíváiról [a hálózati házirend- és elérési szolgáltatások áttekintésének](https://technet.microsoft.com/library/hh831683.aspx) *az elavult funkciókkal foglalkozó szakaszában* tájékozódhat.

