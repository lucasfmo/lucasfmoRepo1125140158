---
title: "Biztonsági alapok |} Microsoft Docs"
description: "Ismerje meg a biztonsági réteg alkalmazása a System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d56c8a76e4770336d4a2ab519e776e48fec8ebcd
ms.openlocfilehash: df3198885259b1db4a1aadee0db6512a1a2d4911
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>A System Center Configuration Manager biztonsági elemei – Alapok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager Security több rétegből tevődik. Az első réteg Windows biztonsági funkciókat biztosítja az operációs rendszer és a hálózathoz, és tartalmazza:  

-   A Configuration Manager összetevői közötti átvitelhez fájlmegosztás.  

-   Hozzáférés-vezérlési listái (ACL) segítségével biztonságos fájlokhoz és beállításokhoz.  

-   Az Internet Protocol Security (IPsec) biztonságos kommunikáció érdekében.  

-   Csoportházirend a biztonsági házirend beállítása.  

-   Elosztott Component Object Model (DCOM) engedélyek elosztott alkalmazásokhoz, például a Configuration Manager konzolon.  

-   Active Directory tartományszolgáltatások a rendszerbiztonsági tagok tárolásához.  

-   A Windows fiókvédelme, beleértve néhány olyan csoportot, a Configuration Manager telepítő futásakor lettek létrehozva.  

Ezt követően további biztonsági összetevők, például a tűzfalak és a behatolás-észlelés biztosítható szolgálhat a teljes működési környezetére. Iparági által kiadott tanúsítványok szabványos nyilvános kulcsú infrastruktúra (PKI) megvalósítások segítségével adja meg a hitelesítési, aláírási és titkosítási.  

A Windows server és a hálózati infrastruktúra által nyújtott biztonsági elemek, mellett a Configuration Manager szabályozza a hozzáférést a Configuration Manager konzoljához és erőforrásaihoz többféle módon. Alapértelmezés szerint csak a helyi rendszergazdák jogosult a fájlokat és beállításkulcsokat, amelyen telepítve van a számítógépeken a Configuration Manager konzol futtatásához szükséges.  

A biztonság következő rétege a Windows Management Instrumentation (WMI) általi, konkrétan az SMS Provider általi hozzáférésen alapszik. Az SMS-szolgáltató a Configuration Manager összetevő egy felhasználó hozzáférést biztosít a információ a Helyadatbázis lekérdezéséhez. Alapértelmezés szerint a szolgáltató elérése történik a helyi SMS rendszergazdák csoport tagjai számára. Ez a csoport elsőként csak a felhasználó, aki telepítette a Configuration Manager tartalmazza. Az SMS rendszergazdák csoportjába más fiókokat is fel kell venni, hogy fiókengedélyeket lehessen adni az általános információmodell (CIM) adattárára és az SMS Provider szolgáltatásaira.  

A biztonság utolsó rétege a helyadatbázisban lévő objektumokra vonatkozó engedélyeken alapszik. Alapértelmezés szerint a helyi rendszerfiók és a Configuration Manager telepítéséhez használt felhasználói fiókot felügyelhető minden objektumot a helyadatbázisban. Adja meg, és a Configuration Manager konzolon a további rendszergazda felhasználóknak engedélyeket korlátozhatja a szerepköralapú felügyelet használatával.  



## <a name="role-based-administration"></a>Szerepköralapú adminisztráció  
 A Configuration Manager szerepkör alapú felügyelet használatával például gyűjtemények, központi telepítések és helyek biztonsági objektumok védelméhez. Ez a felügyeleti modell központilag határozza meg, és a teljes hierarchiára kiterjedően kezeli a biztonsági hozzáférési beállításokat minden hely és helybeállítás részére. Biztonsági szerepkörök rendszergazda felhasználók és a csoporthoz rendelt. Az engedélyek másik Configuration Manager típusú objektumokat, például az engedélyeket, létrehozására és megváltoztatására ügyfélbeállítások segítségével csatlakoznak. Biztonsági a meghatározott objektumpéldányokat tartalmazó csoportok objektumok, amelyek egy rendszergazda felhasználó felelős, például egy alkalmazás, amely telepíti a Microsoft Office. Biztonsági szerepkörök, biztonsági hatókörök és gyűjtemények kombinációja határozza meg az objektumok egy rendszergazda felhasználó tekintheti meg és kezelheti. A Configuration Manager telepít néhány alapértelmezett biztonsági szerepkört a tipikus felügyeleti feladatokhoz. Azonban létrehozhat saját biztonsági szerepköröket, meghatározott üzleti igényei támogatásához.  

 További információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="securing-client-endpoints"></a>Ügyfél-végpontok védelme  
 Ügyfél-kommunikációt a helyrendszer-szerepkörök vagy önaláírt tanúsítványokat használ, vagy PKI-tanúsítványok használatával védett. PKI-ügyféltanúsítványt használjanak, hogy a Configuration Manager az interneten észlelt számítógépes ügyfeleknek és a mobileszközök ügyfelei lesz szüksége. A PKI-tanúsítványt az ügyfél-végpontok biztonságos HTTPS PROTOKOLLT használ. Azok a helyrendszerszerepkörök, amelyekhez az ügyfelek csatlakoznak konfigurálhatók vagy a HTTPS vagy a HTTP protokollos ügyfélkommunikációra. Ügyfélszámítógépek mindig a rendelkezésre álló legbiztonságosabb mód használatával kommunikálnak. Ügyfélszámítógépek csak akkor térnek át a kevésbé biztonságos kommunikációs módszer http használatával az intraneten, ha helyrendszerszerepkör, amely engedélyezi a HTTP-kommunikációt.  

 További információkért lásd: [a kriptográfiai szolgáltató szabályozza technikai útmutató a System Center Configuration Manager](../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

## <a name="configuration-manager-accounts-and-groups"></a>A Configuration Manager fiókjai és csoportjai  
 Configuration Manager a legtöbb helyművelethez a helyi rendszerfiókot használja. Egyes felügyeleti feladatok szükség lehet további fiókok karbantartását. Több alapértelmezett csoport és SQL Server szerepkörök telepítés során jön létre. Lehetséges, hogy manuálisan számítógépi vagy felhasználói fiókok hozzáadása az alapértelmezett csoportokat és az SQL-kiszolgálói szerepeknek.  

 További információk: [A System Center Configuration Managerben használt fiókok](../../core/plan-design/hierarchy/accounts.md).  

## <a name="privacy"></a>Személyes adatok védelme  
 Bár a vállalatfelügyeleti termékek sok előnyt kínálnak, mivel a felhasználók tömegeit kezelhetik hatékonyan, arra is kell vigyázni, hogy ennek a szoftvernek milyen hatása lehet a szervezeten belüli felhasználók személyes adatainak biztonságára. A System Center Configuration Manager az adatok gyűjtéséhez és az eszközök figyeléséhez több segédprogramot is tartalmaz. Egyes eszközök előfordulhat, hogy előléptetése adatvédelmi aggályokat.  

 Például a Configuration Manager-ügyfél telepítésekor számos felügyeleti beállítás alapértelmezetten engedélyezett. Ez azt eredményezi, hogy az ügyfélszoftver adatokat küld a Configuration Manager-hely. A Configuration Manager adatbázisában tárolja az ügyféladatokat, és az adatokat a Microsoftnak nem küldi el. System Center Configuration Manager megvalósítása előtt gondolja át az adatvédelmi követelményeit.  

