---
title: "Helyrendszer-szerepkörök ügyfelek |} Microsoft Docs"
description: "Helyrendszerszerepkörök meghatározása ügyfelek a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9f2dda834f23b2ee85c4c301c7e1b6a3a54ebc97
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>A helyrendszerszerepkörök meghatározása a System Center Configuration Manager-ügyfelek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör segítségével meghatározhatja, hogy a helyrendszer-szerepkörök, amelyekre szüksége van a Configuration Manager-ügyfelek központi telepítése:  

 Telepíteni a szükséges helyrendszerszerepköröket a hierarchia kapcsolatos további információkért lásd: [helyek hierarchiájának tervezése a System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

 Telepítse és konfigurálja a szükséges helyrendszerszerepköröket kapcsolatos további információkért lásd: [helyrendszerszerepkörök telepítése](../../../../core/servers/deploy/configure/install-site-system-roles.md).  

##  <a name="determine-if-you-need-a-management-point"></a>Meghatározza, hogy szükséges-e a felügyeleti pont  
 Alapértelmezés szerint az összes Windows rendszerrel működő ügyfélszámítógép terjesztési pont használata a Configuration Manager-ügyfél telepítéséhez, és képes tartalékként felügyeleti pontot Ha terjesztési pont nem érhető el. Azonban telepítheti Windows ügyfelek alternatív forrásból származó számítógépeken a CCMSetup parancssori tulajdonság használatakor **/source: < elérési út\>**. Például előfordulhat, hogy ehhez az interneten lévő ügyfelek telepítésekor. Egy másik helyzet lehet, amikor szeretné elkerülni a hálózati csomagok küldését a számítógép és a felügyeleti pont az ügyfél telepítésekor lehet, hogy mivel tűzfal blokkolja a szükséges portok, vagy mert alacsony sávszélességű kapcsolattal rendelkezik. Azonban az összes ügyfélnek kommunikálnia kell egy felügyeleti ponttal a helyhez való hozzárendelés, és a Configuration Manager által kezelendő.  

 További információ a CCMSetup parancssori tulajdonság **/source: < elérési út\>**, lásd: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../../core/clients/deploy/about-client-installation-properties.md).  

 Ha egynél több felügyeleti pontot telepít a hierarchiában, az ügyfelek automatikusan csatlakoznak egy olyan pont, az erdő tagság és a hálózati hely alapján. Nem telepíthet több felügyeleti pont egy másodlagos helyen.  

 Mac számítógépek és mobileszközök mindig regisztrálni a Configuration Manager szükséges felügyeleti pont az ügyfél telepítéséhez. A felügyeleti pont egy elsődleges helyen kell lennie, meg kell adni a mobileszközök támogatásához, és el kell fogadnia az internetről érkező ügyfélkapcsolatokat. Ezek az ügyfelek nem a másodlagos helyeken lévő felügyeleti pontok használatát, vagy más elsődleges helyeken lévő felügyeleti pontokhoz csatlakozó.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>Meghatározza, hogy szükséges-e a tartalék állapotkezelő pont  
 A tartalék állapotkezelő pont használatával figyelheti az ügyfél központi telepítését a Windows rendszerű számítógépeken. Azt is megállapíthatja, hogy a Windows számítógép-ügyfeleket, amelyek nem felügyelt, mert nem tudnak kommunikálni egy felügyeleti ponttal. Mac számítógépek, a Configuration Manager által beléptetett mobileszközök és az Exchange Server-összekötő segítségével kezelt mobileszközök ne használja a tartalék állapotkezelő pontot.  

 A tartalék állapotkezelő pont nincs szükség ügyféltevékenységet és -ügyfél rendszerállapot-figyelése.  

 A tartalék állapotkezelő pont mindig kommunikál az ügyfelek HTTP, amelyek nem hitelesített kapcsolatokat használ, és adatot küld egyszerű szöveges. Így a tartalék állapotkezelő pont ki van téve a támadásoknak, különösen ha a használható Internet alapú ügyfélfelügyelethez. A támadási felület csökkentése érdekében minden esetben dedikáljon külön kiszolgálót a tartalék állapotkezelő pont fut, és nem telepíthető ugyanarra a kiszolgálóra, éles környezetben más helyrendszerszerepköröket.  

 Telepítse a tartalék állapotkezelő pont a következő esetekben:  

-   Ügyfél-kommunikációs hibái továbbítva legyenek a hely Windows rendszerű számítógépekről azt szeretné, akkor is, ha ezek az ügyfélszámítógépek nem tud kommunikálni egy felügyeleti ponttal.  

-   A Configuration Manager-ügyfél telepítési jelentéseit, amelyek megjelenítik a tartalék állapotkezelő pont által küldött adatokat használni kívánt.  

-   A helyrendszerszerepkörhöz dedikált kiszolgálóval rendelkezik, és a kiszolgáló támadások elleni védelme érdekében további biztonsági intézkedésekkel rendelkezik.  

-   A tartalék állapotkezelő pont használatának előnyei nem hitelesített kapcsolatokkal kapcsolódó biztonsági kockázatoknál járó, és törölje a szöveget HTTP Protokollon keresztül.  

 Ne telepítse a tartalék állapotkezelő pont, ha a biztonsági kockázatok rendelkező webhely, nem hitelesített kapcsolatokhoz és a tiszta szöveges nyomósabbak az ügyfél-kommunikációs problémák azonosításának előnyeinél.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>Határozza meg, hogy szükséges-e a jelentéskészítési szolgáltatási pont  
 A Configuration Manager több jelentést is nyújt segítséget a telepítése, hozzárendelése és -ügyfelek a Configuration Manager konzolon figyelheti. Egyes ügyfél-telepítési jelentésekben szükséges, hogy az ügyfelek tartalék állapotkezelő ponthoz legyenek rendelve.  

 Bár a jelentések központi telepítése esetén nem szükséges, és tekintse meg az egyes központi telepítési információk a Configuration Manager konzolon, vagy használja az ügyfelek naplófájljai részletes információkat, az ügyfél ügyféljelentések hasznos információkkal szolgálnak figyelése és hibáinak elhárítása az ügyfelek központi telepítése.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>Meghatározza, hogy szükséges-e a beléptetési pont és beléptetési proxypont  
 A Configuration Manager megköveteli, hogy a beléptetési pont és a beléptetési proxypontra a mobileszközök beléptetéséhez és a Mac számítógépek tanúsítványainak beléptetéséhez mutasson. Ezen helyrendszerszerepkörök nem szükségesek, ha a mobileszközöket az Exchange Server-összekötő segítségével kezeli, vagy ha telepíti a mobileszközön lévő korábbi ügyfél (például Windows CE rendszerhez), vagy ha igényli és telepíti az ügyféltanúsítványt a Mac számítógépek egymástól függetlenül a Configuration Manager.  

##  <a name="determine-if-you-need-a-distribution-point"></a>Meghatározza, hogy szükséges-e a terjesztési pont  
 A terjesztési pontot a Configuration Manager-ügyfelek telepítése Windows rendszerű számítógépeken nincs szükség. Alapértelmezés szerint a Configuration Manager terjesztési pont használatával telepíti az ügyfél forrásfájljait a Windows rendszerű számítógépeken azonban visszatérhet ezeket a fájlokat felügyeleti pontról töltse le. Terjesztési pontok nem használják a Configuration Manager által beléptetett mobileszközök ügyfeleinek telepítése, de a mobileszközön lévő korábbi ügyfél telepítésekor használt. Ha az operációs rendszer központi telepítésének részeként telepíti a Configuration Manager-ügyfél, az operációs rendszer lemezképének tárolja, és egy terjesztési pontról történő lekérése.  

 Bár előfordulhat, hogy nem kell terjesztési pontok a legtöbb Configuration Manager-ügyfelek telepítése, kell őket telepíteni a szoftvert, például alkalmazások és szoftverfrissítések az ügyfelek számára.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>Meghatározza, hogy szükséges-e az alkalmazáskatalógus weboldal-elérési pontja és az alkalmazáskatalógus webszolgáltatási pontja  
 Az alkalmazáskatalógus weboldal-elérési pontja és az alkalmazáskatalógus webszolgáltatási pontja nem szükséges az ügyfelek központi telepítéséhez. Azonban érdemes telepíteni ezeket az összetevőket az ügyfél központi telepítési folyamata során, így a felhasználók a következő műveleteket tudják végrehajtani, amint a Configuration Manager-ügyfél telepítve van a Windows rendszerű számítógépeken:  

-   A mobileszközök törlési.  

-   Keresse meg, és telepítse az alkalmazásokat az alkalmazáskatalógusból.  

-   Telepítsen alkalmazásokat olyan felhasználók és eszközök központi telepítési céllal **elérhető**.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>Határozza meg, hogy szükség van-e egy felhőalapú felügyeleti átjáró összekötőpontja 

Ha hoz létre egy felhőalapú felügyeleti átjáró összekötőpontja kell egy [felhő adatkezelési átjáró](/sccm/core/clients/manage/setup-cloud-management-gateway) való [az interneten lévő ügyfelek kezelése](/sccm/core/clients/manage/manage-clients-internet).


 
