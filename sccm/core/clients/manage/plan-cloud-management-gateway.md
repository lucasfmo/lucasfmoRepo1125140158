---
title: "A felhő adatkezelési átjáró tervezése |} Microsoft Docs"
description: 
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: b1295891a5567e64b901c79100c2971e526dc874
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Tervezze meg a felhő adatkezelési átjáró a Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1610 verziójától kezdve felhő adatkezelési átjáró kezelése a Configuration Manager-ügyfelek az interneten lévő egyszerű módszert kínál. A felhő management gateway szolgáltatás telepítve van a Microsoft Azure, és egy Azure-előfizetést igényel. Csatlakozik a helyi Configuration Manager-infrastruktúrát, a felhő felügyeleti átjáró összekötőpontja nevű új szerepkör használatával. Miután rendszerbe állította és konfigurálta, ügyfelek fognak tudni hozzáférni a helyi Configuration Manager helyrendszer-szerepkörök függetlenül attól, hogy fontosságúak a belső magánhálózati hálózati vagy az interneten.

A Configuration Manager konzol segítségével a szolgáltatás üzembe helyezése az Azure-ba, adja hozzá a felhő felügyeleti átjáró connector-pont szerepkört, és helyrendszer-szerepköröket felhő felügyeleti átjáró forgalom engedélyezésére kell konfigurálni. Felhő adatkezelési átjáró jelenleg csak támogatja a felügyeleti pont és a szoftver frissítés pont szerepkör.

Ügyféltanúsítványok és a Secure Socket Layer (SSL)-tanúsítványok szükségesek számítógépek hitelesítéséhez és a különböző rétegeket, a szolgáltatás közötti kommunikáció titkosításához. Ügyfélszámítógépek általában keresztül csoport házirend betartatása ügyfél tanúsítványt kaphasson. Az ügyfelek és a szerepköröket üzemeltető helyrendszer-kiszolgáló közötti forgalom titkosításához, hozzon létre egy egyéni SSL-tanúsítványt a CA-tól kell. Is kell állít be, amely lehetővé teszi a felhőalapú felügyeleti átjáró szolgáltatás telepítéséhez a Configuration Manager Azure felügyeleti tanúsítvánnyal.

## <a name="requirements-for-cloud-management-gateway"></a>Felügyeleti átjáró követelményei

-   Ügyfélszámítógépek és a felhő felügyeleti átjáró összekötő pontot futtató helyrendszer-kiszolgálón.

-   Egyéni SSL, a belső hitelesítésszolgáltató – az ügyfélszámítógépek számára a kommunikáció titkosítására és a felhő management gateway szolgáltatás identitásának hitelesítésére használt tanúsítványok.

-   Azure-előfizetés felhőszolgáltatásai számára.

-   Az Azure felügyeleti tanúsítvány - való hitelesítéshez szükséges a Configuration Manager az Azure-ral.

## <a name="specifications-for-cloud-management-gateway"></a>Felügyeleti átjáró specifikációk

- Felügyeleti átjáró minden példánya támogatja a 4 000 ügyféltől.
- Azt javasoljuk, hogy hozzon létre legalább két példányban kezelési átjáró a rendelkezésre állás javítása érdekében.
- Felügyeleti átjáró csak a felügyeleti pont és a szoftver frissítés pont szerepköre támogatja.
-   A következő szolgáltatások a Configuration Managerben is felhő adatkezelési átjáró jelenleg nem támogatott:

    -   Ügyfelek központi telepítése
    -   Automatikus helyhozzárendelés
    -   A felhasználói házirendek
    -   Alkalmazáskatalógus (beleértve a szoftver jóváhagyási kérelmek)
    -   Teljes operációs rendszer központi telepítési (OSD)
    -   Configuration Manager-konzol
    -   Táveszközök
    -   Jelentéskészítő webhely
    -   Hálózati ébresztés
    -   Mac, Linux és UNIX rendszerű ügyfelek
    -   Az Azure Resource Manager
    -   Társ-gyorsítótárazás
    -   Helyszíni mobileszköz-felügyelet

## <a name="cost-of-cloud-management-gateway"></a>Felügyeleti átjáró költsége

>[!IMPORTANT]
>Az alábbi Költséginformációk jelleggel becsléséhez van. Előfordulhat, hogy a környezet más változókat, amelyek hatással vannak a teljes költség szempontjából felhő adatkezelési átjáró használatával.

Felügyeleti átjáró használja, a következő Microsoft Azure, amely az Azure-előfizetés fiók költségeket terhel:

-   Virtuális gép

    -   Felhő adatkezelési átjáró jelenleg van szükség a szabványos\_A2 virtuális gépet. A szolgáltatás létrehozásakor választhat hány virtuális gépek támogatásához a szolgáltatás (egyik az alapértelmezett érték).

    -   A becsléséhez jelleggel, várt, hogy egyetlen Azure Standard\_A2 virtuális gép is körülbelül 2000 egyidejű Internet alapú ügyfél támogatására.

    -   Tekintse meg a [Azure árképzési Számológép](https://azure.microsoft.com/en-us/pricing/calculator/) annak meghatározásához, potenciális költségeket.

      >[!NOTE]
      >Virtuális gép költségek régiónként eltérőek lehetnek.

-   Kimenő adatátvitel

    -   Díjak sem merülnek fel, az adatok továbbítására kívüli a szolgáltatás... Tekintse meg a [Azure díjszabása sávszélesség](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) annak meghatározásához, potenciális költségeket.

    -   A becsléséhez jelleggel, várt körülbelül 100 MB / hónap ügyfelenként Internet alapú ügyfelek ezzel a házirend frissítése minden órában.

    >[!NOTE]
    > Egyéb műveleteket a felhő adatkezelési átjáró (például központi telepítés szoftverfrissítéseket vagy alkalmazások) keresztül lesz növelje a kimenő adatforgalom az Azure-ból.

-   Tartalomtárolás

    -   Internetalapú ügyfelek az adatkezelési átjáró cloud felügyelt kap szoftver tartalom frissítése a Windows Update díjmentesen.

    -   Egyéb szükséges tartalmat (például alkalmazások) a felhőalapú terjesztési pont elérhetőnek kell lennie. A felhő adatkezelési átjáró jelenleg csak a felhőalapú terjesztési pont támogatja az ügyfelek számára a tartalom küldése.

    - Tekintse meg a költségeinek egy [felhő alapú terjesztési](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) további részleteket.

## <a name="next-steps"></a>További lépések

[Felügyeleti átjáró beállítása](setup-cloud-management-gateway.md)


## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>A felhő felügyeleti átjáró (CMG) kapcsolatos gyakran ismételt kérdések

### <a name="why-use-the-cloud-management-gateway"></a>A felhő adatkezelési átjáró miért érdemes használni?

Ez a szerepkör használatával egyszerűsíthető Internet alapú ügyfélfelügyelethez három lépésben a Configuration Manager konzoljáról.

1. Az Azure használatával telepítse a CMG a [létrehozása kezelési átjáró a](/sccm/core/clients/manage/setup-cloud-management-gateway) varázsló.
2. Konfigurálja a [felhőcsatlakozási pont felügyeleti átjáró](/sccm/core/servers/deploy/configure/install-site-system-roles) helyrendszerszerepkör.
3. [Felügyeleti átjáró felhőforgalom szerepkörök konfigurálásához](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic), például a felügyeleti pont és a szoftverfrissítési pont frissítését.

### <a name="how-does-the-cloud-management-gateway-work"></a>Hogyan működik a felhő adatkezelési átjáró?

- A felhő felügyeleti átjáró csatlakozási pont lehetővé teszi, hogy a felhő adatkezelési átjáró következetes és magas teljesítmény kapcsolatot az internetről.
- A Configuration Manager a kapcsolat adatait és biztonsági beállításait például CMG teszi közzé a beállításokat.
- A CMG hitelesíti, és továbbítja a Configuration Manager ügyfelek kéréseit az a felhő felügyeleti átjáró csatlakozási pont. Ezeket a kéréseket a vállalati hálózat megfelelően URL-cím hozzárendelések szerepkörök továbbítja.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>Hogyan történik a felhő adatkezelési átjáró?

A cloud service manager összetevője a szolgáltatáskapcsolódási pont összes CMG telepítési feladatok kezeli. Továbbá figyeli, és jelenti a szolgáltatás állapotának és a naplózási adatokat az Azure AD.

#### <a name="certificate-requirements"></a>Tanúsítványkövetelmények

Az alábbi tanúsítványok biztonságossá tételéhez a CMG lesz szüksége:

- **Felügyeleti tanúsítvány** – Ez lehet bármely olyan tanúsítvány, beleértve az önaláírt tanúsítványokat. Használhatja az Azure AD feltöltött nyilvános tanúsítvány vagy egy [titkos kulcsot tartalmazó PFX](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) importálása a Configuration Manager az Azure AD szolgáltatással való hitelesítésre. 
- **Webszolgáltatásának olyan tanúsítvánnyal** -javasoljuk, hogy ahhoz, hogy az ügyfelek által natív megbízhatósági egy nyilvános Hitelesítésszolgáltatói tanúsítványt használjon. A CNAME rekordot kell létrehozni a nyilvános DNS-registar a. Nem támogatja a helyettesítő tanúsítványokat.
- **Legfelső szintű/SubCA tanúsítványok feltöltése CMG** -a CMG kell teljes tanúsítványlánc ellenőrzése az ügyfél PKI-tanúsítványokat. Ha egy vállalati hitelesítésszolgáltató használata kiállító PKI-ügyféltanúsítványok és a legfelső szintű vagy alárendelt hitelesítésszolgáltató nem érhető el az interneten, majd fel kell tölteni azt a CMG.

#### <a name="deployment-process"></a>A központi telepítési folyamat

Ott két fázisban történik a központi telepítéshez:

- A felhőalapú szolgáltatás telepítéséhez
    - Töltse fel a [Azure szolgáltatás definíciós séma](https://msdn.microsoft.com/library/azure/ee758711.aspx) (csdef) fájlt
    - Töltse fel a [Azure szolgáltatás konfigurációs séma](https://msdn.microsoft.com/library/azure/ee758710.aspx) (cscfg)-fájl.
- Állítsa be a CMG összetevő az Azure AD-kiszolgálón, és a végpontok, a HTTP-kezelők és a szolgáltatások beállítása az Internet Information Services (IIS)

Ha módosítja a CMG konfigurációját, egy központi telepítését a CMG való lehet kezdeményezni.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>Hogyan segít a felhőalapú adatkezelési átjáró biztonsága?

A CMG biztosíthatja biztonsági a következőképpen:

- Fogad el, és kezeli a kapcsolatok CMG csatlakozási pontok például a belső tanúsítványokkal kölcsönös SSL-hitelesítés és a kapcsolat azonosítók.
- Fogad el, és továbbítja az ügyfélkéréseket
    - Előzetesen hitelesíti kölcsönös SSL használatával a PKI-ügyféltanúsítvány a kapcsolatokat.
    - A megbízható tanúsítványok listáját a PKI-ügyféltanúsítvány gyökérmappájában ellenőrzi. Ezt a beállítást, az ügyfél kommunikációt hely tulajdonságai beállításokat adhatja meg. Is érvényesítésének a ugyanabban a felügyeleti pontként az ügyfél számára.
    - Ellenőrzi a fogadott URL-címek
    - Szűrők URL-címeket ellenőrizni, ha bármely csatlakozó CMG szolgáltatáskapcsolódási pont is szolgáltatás az URL-kérelmet kapott.  
    - Ellenőrzi a tartalom hossza ellenőrzés közzétételi végpontok.
    - Használja a "ciklikus multiplexelés" terheléselosztásához ugyanazon helyről CMG csatlakozási pont között.

- Biztonságossá teszi a CMG szolgáltatáskapcsolódási pont
    - A kapcsolódó CMG mindegyik virtuális példányának konzisztens HTTP vagy TCP-kapcsolatok alkot. Ellenőrzi, és kapcsolatok percenként fenn.
    - Kölcsönösen autheticates SSL-hitelesítés a CMG belső tanúsítványok használatával.
    - Továbbítja a HTTP-kérelmek URL-cím leképezések alapján.
    - A jelentés megjelenítése a felügyeleti szolgáltatás állapot létesített kapcsolat állapotát.
    - A jelentés végpont forgalom jelentés végpontonként 5 percenként.

- Biztonságos közzététel végpont Configuration Manager-ügyfél irányuló szerepkörök, például a felügyeleti pont és a szoftver frissítés pont állomás végpontok az IIS-ben ügyfelektől érkező kérelmeket. Minden a CMG közzétett végpont egy URL-címmegfeleltetés rendelkezik.
A külső URL-CÍMÉT, a egy, az ügyfél használ a CMG folytatott kommunikációhoz.
A belső URL-címe a CMG csatlakozási pont továbbítják a belső kiszolgálóhoz intézett kérésekben. 

#### <a name="example"></a>Például:
Ha engedélyezi a CMG forgalom a felügyeleti ponton, a Configuration Manager jönnek létre a belső a felügyeleti pont kiszolgálókon, például ccm_system, ccm_incoming és sms_mp leképezéseit URL-CÍMÉT.
A külső URL-címet a felügyeleti pont ccm_system végpont nézhet **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**. Az URL-címe: egyedi valamennyi felügyeleti pontnál. A Configuration Manager-ügyfél ezután visszahelyezi a CMG engedélyezve van a felügyeleti csomag neve például  **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>**  azokat a internetes felügyeleti pontok listáját. Az összes közzétett külső URL-címek feltöltötte-e a CMG automatikusan akkor CMG el az URL-szűrés. Az összes URL-címmegfeleltetés replikálja CMG szolgáltatáskapcsolódási pont, a belső kiszolgálókhoz külső URL-CÍMÉT kérő ügyfél szerint továbbíthatja.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>Mely portokat kell használni a felhő felügyeleti átjáró? 

- Nincs szükség a helyi hálózati bejövő portra. CMG telepítését hoz létre álló, lemezcsoport CMG automatikusan. 
- 443-as mellett néhány kimenő portok a CMG csatlakozási pont igényel.

|||||
|-|-|-|-|
|Adatfolyam|Kiszolgáló|Kiszolgáló port|Ügyfél|
|CMG központi telepítés|Azure|443|A Configuration Manager szolgáltatáskapcsolódási pont|
|CMG csatorna létrehozása|CMG|Virtuálisgép-példány: 1-port: 443<br>Virtuálisgép-példány: N (N > = 2, az N < = 16) portok: 10124 ~ N 10140 ~ N|CMG szolgáltatáskapcsolódási pont|
|CMG ügyfél|CMG|443|Ügyfél|
|CMG-összekötő helyrendszer-szerepkör (jelenleg a felügyeleti pontok és a szoftverfrissítési pontok)|Helyszerepkör|A helyrendszer-szerepkör konfigurált protokoll és portok|CMG szolgáltatáskapcsolódási pont|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>Hogyan javítható a kezelési átjáró a teljesítménye?

- Ha lehetséges, konfigurálja a CMG CMG szolgáltatáskapcsolódási pont és a Configuration Manager helykiszolgáló azonos hálózati késés csökkentése érdekében a régióban.
- A kapcsolatot a Configuration Manager-ügyfél és a CMG jelenleg nem régió-kompatibilis.
- Ahhoz, hogy a magas rendelkezésre állású, azt javasoljuk a CMG és két CMG csatlakozási pontok helyenként legalább 2 virtuális példánya 
- Több ügyfél támogatására képes több Virtuálisgép-példányok hozzáadásával CMG méretezheti. Az Azure AD terheléselosztó által elosztott terhelésű.
- Hozzon létre több CMG csatlakozási pontok közöttük a terhelés elosztása. A CMG fog "ciklikus multiplexelés" a forgalmat a kapcsolódó CMG csatlakozási pontokhoz.
- Támogatási ügyfél CMG VM példányonként értéke 6k 1702 kiadásában. A CMG csatorna nagy terhelésnek van kitéve, ha a kérelem automatikusan továbbra is elvégezhető, de a szokásosnál hosszabb ideig is tarthat.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>Hogyan figyelheti a felügyeleti átjáró?

Az üzembe helyezés hibaelhárítása használja **CloudMgr.log** és **CMGSetup.log**.
Hibaelhárítás a szolgáltatás állapotát, használja a **CMGService.log** és **SMS_CLOUD_PROXYCONNECTOR.log**.
Hibaelhárítási ügyfélforgalmat, használjon **CMGHttpHandler.log**, **CMGService.Log**, és **SMS_CLOUD_PROXYCONNECTOR.log**.

Minden CMG kapcsolódó naplófájlok listáját lásd: [naplófájlok a Configuration Managerben](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)


