---
title: "Helyek konfigurálása |} Microsoft Docs"
description: "Tekintse át ezt az ellenőrző listát győződjön meg arról, hogy fontolja meg a helyeket és hierarchiákat egyaránt befolyásoló leggyakoribb beállításokat."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5f1efaa776079b21d52b9936273380e9bb8963e9
ms.openlocfilehash: 862f420c063cb44c419d4904fbb4696efb739758
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-sites-and-hierarchies-for-system-center-configuration-manager"></a>Helyek és hierarchiák konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután az első System Center Configuration Manager-hely, vagy adja hozzá a további helyeket adott a hierarchiához, a következő ellenőrzőlista segítségével győződjön meg arról, hogy érdemes-e a helyeket és hierarchiákat egyaránt befolyásoló leggyakoribb beállításokat.  

## <a name="checklist-of-common-configurations-for-new-and-additional-sites"></a>Új és további helyek gyakori konfigurációinak ellenőrzőlistája  
Vegye figyelembe az alábbi megjegyzések konfigurációjáról, amelyek a legtöbb telepítés vonatkoznak:

-   Néhány beállítás egymásra épül, például az Active Directory-Erdőfelderítés, a határokat és a határ csoportok.  

-   Több beállításnak van olyan alapértelmezett értéke, amelyet nem szükséges megváltoztatni, legalább is nem rögtön.  

-   Más beállításokat, például a határcsoportokat és a terjesztésipont-csoportokat a használatba vétel előtt konfigurálni kell.  

|Művelet|Részletek|  
|------------|-------------|  
|Szerepköralapú adminisztráció konfigurálása|A rendszergazda felhasználók elkülönített rendszergazdai hozzárendelések tekintheti meg és kezelheti a különböző objektumokat és adatokat a Configuration Manager környezetben.<br /><br /> A szerepköralapú adminisztráció konfigurációi a hierarchiában található összes hellyel meg vannak osztva.   <br/><br/>További információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../../../core/servers/deploy/configure/configure-role-based-administration.md).|  
|Helyadatok közzététele az Active Directory tartományi szolgáltatásokban (AD DS)|Könnyebben az ügyfelek számára a szolgáltatások keresését, és a webhely-erőforrások hatékony használatát.<br /><br /> Először [az Active Directory-séma kiterjesztése a System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md), majd minden helyen kell konfigurálni a külön-külön és [helyadatok közzététele a System Center Configuration Managerhez](../../../../core/servers/deploy/configure/publish-site-data.md)|  
|Szolgáltatáskapcsolódási pont konfigurálása|Tervezze meg telepítése és a szolgáltatáskapcsolódási pont konfigurálása a hierarchia legfelső szintű helyén. További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése](../../../../core/servers/deploy/configure/about-the-service-connection-point.md).|  
|Helyrendszerszerepkörök hozzáadása|Egy vagy több további helyrendszerszerepkört telepíthet az egyes helyek.  További információkért lásd: [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](../../../../core/servers/deploy/configure/add-site-system-roles.md).|  
|Helyhatárok és határcsoportok konfigurálása|Adja meg a kezelni kívánt eszközöket tartalmazó intranetes hálózati helyeket meghatározó határokat. A határcsoportok konfigurálja, hogy az ügyfelek adott hálózati helyeken található Configuration Manager-erőforrások. További információkért lásd: [helyhatárok és határcsoportok megadása a System Center Configuration Manager](../../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).|  
|Terjesztésipont-csoportok konfigurálása|A telepítések kezelésének megkönnyítése érdekében konfigurálja a terjesztési pontok logikai csoportjait. További információkért lásd: [terjesztésipont-csoportok kezelése](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) a [telepíteni és konfigurálni a terjesztési pontokat a System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md).|  
|Felderítés futtatása|Futtassa a felderítést erőforrást a hálózaton, beleértve a hálózati infrastruktúra, eszközök és felhasználók kereséséhez.<br /><br /> További információkért lásd: [A felderítés futtatása a System Center Configuration Managerből](../../../../core/servers/deploy/configure/run-discovery.md).|  
|Adjon hozzá redundanciát és kapacitást az infrastruktúrát kezelő rendszergazdák számára|A rendszergazdák számára az infrastruktúra kezelését kapacitás bővítése céljából további SMS-szolgáltatók és a Configuration Manager konzolok telepítése:<br /><br /> **További SMS-szolgáltatók telepítéséhez** a hely és a hierarchia felügyeletére kapcsolódási pontok redundanciájának biztosítása érdekében. További információkért lásd: [az SMS-szolgáltató kezeléséről](../../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) a [a System Center Configuration Manager infrastruktúra](../../../../core/servers/manage/modify-your-infrastructure.md).<br /><br /> **További Configuration Manager konzolok telepítése** további rendszergazda felhasználóknak hozzáférést biztosítani. További információkért lásd: [telepítése a Configuration Manager konzolok](../../../../core/servers/deploy/install/install-consoles.md).|  
|Helyösszetevők konfigurálása|Helyösszetevőinek konfigurálásával módosíthatja a helyrendszerszerepkörök és a hely állapotjelentéseinek viselkedését az egyes helyeken. További információkért lásd: [A System Center Configuration Manager helyösszetevői](../../../../core/servers/deploy/configure/site-components.md).|  
|Egyéni gyűjtemények létrehozása|Információ a felderített eszközök és felhasználók segítségével hozzon létre egyéni gyűjtemények jövőbeli felügyeleti feladatok megkönnyítése érdekében. További információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md).|  
|A magas kockázatú központi telepítések felügyeletéhez szükséges beállítások konfigurálása|A beállítások, amelyek figyelmeztetik a rendszergazda felhasználóknak a magas kockázatú feladatütemezési központi telepítés létrehozásakor egy helyen.  További információkért lásd: [beállításait a System Center Configuration Manager magas kockázatú telepítések kezelését](../../../../protect/understand/settings-to-manage-high-risk-deployments.md).|  
|Adatbázis-replikák beállítása felügyeleti pontokhoz|Csökkentik a CPU-terhelést, hogy el van helyezve a Helyadatbázis-kiszolgáló által a felügyeleti pontokat, az ügyfelektől érkező kérelmek kiszolgálása során az adatbázis-replika konfigurálásához. További információk: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md).|  
|A Helyadatbázis tárolásához az SQL Server AlwaysOn rendelkezésre állási csoport konfigurálásához|Rendelkezésre állási csoportok 1602-es verziójától kezdve beállítása a magas rendelkezésre állású és vész-helyreállítási megoldások elsődleges helyek és a központi adminisztrációs helyen a Helyadatbázis üzemeltetéséhez. További információkért lásd: [SQL Server AlwaysOn magas rendelkezésre állású Helyadatbázis a System Center Configuration Manager](../../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).|  
|A helyek közötti replikálás módosítása|Az alábbi témakörök alaposabb ismertetéséhez lásd: [Adatátvitel a System Center Configuration Manager helyei között](../../../../core/servers/manage/data-transfers-between-sites.md)<br /><br /> Konfigurálása [fájl alapú replikációként](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_fileroute) másodlagos hely között<br /><br /> Konfigurálása [adatbázis-replikációs hivatkozások](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_Dblinks)<br /><br /> Konfigurálása [elosztott nézetek](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_distviews)|  

