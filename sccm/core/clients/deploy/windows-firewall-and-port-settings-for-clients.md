---
title: "A Windows tűzfal- és portbeállítások ügyfélbeállítások |} Microsoft Docs"
description: "Válassza ki a Windows tűzfal és az ügyfelek a port beállítása a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dce4b640-c92f-401a-9873-ce9aa9262014
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 79686514efcba344c4babc3d3be03b48adca7132
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="windows-firewall-and-port-settings-for-clients-in-system-center-configuration-manager"></a>A Windows tűzfal- és portbeállítások beállításait a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Gyakran a Windows tűzfalat futtató ügyfélszámítógépek a System Center Configuration Managerben kell beállítani a kivételeket úgy, hogy a hellyel való kommunikációt. A beállítandó kivételek a felügyeleti szolgáltatásokat, amelyet a Configuration Manager-ügyfél függ.  

 Az alábbi részekből megismerheti ezeket a felügyeleti funkciókat, illetve további információt kaphat a Windows tűzfalnak a leírt kivételekhez történő beállításáról.  

##  <a name="BKMK_ModifyingWindowsFirewall"></a> A Windows tűzfal által engedélyezett portok és programok módosítása  
 A következő eljárással módosíthatja a portokat és programokat a Windows tűzfalat a Configuration Manager-ügyfél.  

#### <a name="to-modify-the-ports-and-programs-permitted-by-windows-firewall"></a>A Windows tűzfal által engedélyezett portok és programok módosítása  

1.  Nyissa meg a Vezérlőpultot a Windows tűzfalat futtató számítógépen.  

2.  Kattintson a jobb gombbal a **Windows tűzfal**elemre, majd kattintson a **Megnyitás**parancsra.  

3.  Állítsa be a szükséges kivételeket, illetve az egyéni programokat és portokat kívánság szerint.  

## <a name="programs-and-ports-that-configuration-manager-requires"></a>A Configuration Managerhez szükséges programok és portok  
 A következő Configuration Manager-szolgáltatásokat kivételek meglétét kívánják meg a Windows tűzfalhoz:  

### <a name="queries"></a>Lekérdezések  
 Ha a Windows tűzfalat futtató számítógépen futtatja a Configuration Manager konzolon, futnak az első alkalommal sikertelen, és az operációs rendszer statview.exe feloldására rákérdező párbeszédpanelt jelenít meg. A statview.exe letiltásának feloldása után a rendszer hibák nélkül hajtja végre a lekérdezéseket. A statview.exe fájlt lekérdezés indítása előtt kézzel is hozzáadhatja a Windows tűzfal program- és szolgáltatáslistájához a **Kivételek** lapon.  

### <a name="client-push-installation"></a>Ügyfélleküldéses telepítés  
 Leküldéses ügyféltelepítés használatához a Configuration Manager-ügyfél telepítéséhez, adja hozzá a felsorolt kivételeket a Windows tűzfalhoz:  

-   Kimenő és bejövő: **Fájl- és nyomtatómegosztás**  

-   Bejövő: **A Windows Management Instrumentation (WMI)**  

### <a name="client-installation-by-using-group-policy"></a>Ügyfélszoftver-telepítés csoportházirenddel  
 A Configuration Manager-ügyfél telepítése a csoportházirend segítségével, vegye fel a **fájl- és nyomtatómegosztás** kivételként a Windows tűzfalon.  

### <a name="client-requests"></a>Ügyfélkérések  
 Az ügyfélszámítógépek számára, hogy a Configuration Manager-helyrendszerekkel kommunikálnak adja hozzá a felsorolt kivételeket a Windows tűzfalhoz:  

 Kimenő: TCP-Port **80** (a HTTP-kommunikációt)  

 Kimenő: TCP-Port **443-as** (HTTPS-kommunikációhoz)  

> [!IMPORTANT]  
>  Ezek a alapértelmezett portszámok, amelyek módosíthatók a Configuration Manager alkalmazásban. További információkért lásd: hogyan [ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-communication-ports.md). Ha a portok száma módosult az alapértékükhöz képest, a számukkal megegyező kivételeket szintén konfigurálni kell a Windows tűzfalon.  

### <a name="client-notification"></a>Ügyfélértesítés  
 A felügyeleti pont értesítse az ügyfélszámítógépeket azokról a műveletekről, amelyek olyankor kell végrehajtaniuk, amikor egy rendszergazda felhasználó kiválaszt egy ügyfélműveletet a Configuration Manager konzolon, többek között a számítógép-házirend letöltése vagy egy kártevő-ellenőrzés indítása adja hozzá a következő elemet kivételként a Windows tűzfalhoz:  

 Kimenő: TCP-Port **10123**  

 Ha ez a kommunikáció nem sikerül, a Configuration Manager automatikusan visszaáll a meglévő ügyfél-felügyeleti pont kommunikációs port HTTP vagy HTTPS PROTOKOLLT használ:  

 Kimenő: TCP-Port **80** (a HTTP-kommunikációt)  

 Kimenő: TCP-Port **443-as** (HTTPS-kommunikációhoz)  

> [!IMPORTANT]  
>  Ezek a alapértelmezett portszámok, amelyek módosíthatók a Configuration Manager alkalmazásban. További információkért lásd: [ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-communication-ports.md). Ha a portok száma módosult az alapértékükhöz képest, a számukkal megegyező kivételeket szintén konfigurálni kell a Windows tűzfalon.  

### <a name="remote-control"></a>Távvezérlés  
 A Configuration Manager Távvezérlés használatához engedélyezze a következő portot:  

-   Bejövő: TCP-Port**2701**  

### <a name="remote-assistance-and-remote-desktop"></a>Távsegítség és távoli asztal  
 Távsegítséget szeretne kezdeményezni a Configuration Manager konzolról, adja hozzá az egyéni program **Helpsvc.exe** és a bejövő egyéni TCP-portot **135-ös** az engedélyezett programok és szolgáltatások a Windows tűzfal az ügyfélszámítógépen listájához. A **Távsegítség** és a **Távoli asztal**funkciókat is engedélyeznie kell. Ha távsegítséget kezdeményez az ügyfélszámítógépről, a Windows tűzfal automatikusan beállítja és engedélyezi a **Távsegítség** és a **Távoli asztal**funkciókat.  

### <a name="wake-up-proxy"></a>Ébresztési proxy  
 Ha engedélyezi az ébresztési proxy ügyfélbeállítást, egy új, ConfigMgr ébresztési proxy nevű szolgáltatás társ-társ (peer-to-peer) protokollt használ annak ellenőrzésére, hogy az alhálózat más számítógépei ébren vannak-e, illetve szükség esetén a felébresztésükre. Ez a kommunikációtípus a következő portokat használja:  

 Kimenő: UDP-Port **25536**  

 Kimenő: UDP-Port **9**  

 Ezek azok az alapértelmezett portszámok, amelyek módosíthatók a Configuration Manager használatával a **energiagazdálkodás** ügyfelek beállításait **az ébresztési proxy portszáma (UDP)** és **hálózati ébresztés portszáma (UDP)**. Ha megadja a **energiagazdálkodás**: **A Windows tűzfal-kivétel az ébresztési proxy** ügyfél beállítása, ezeket a portokat automatikusan konfigurálja a Windows tűzfal ügyfelek. Ha azonban az ügyfélszoftverekhez másik tűzfal tartozik, a felsorolt portszámokhoz tartozó kivételeket kézzel kell megadni.  

 A felsorolt portokon kívül az ébresztési proxy ICMP (Internet Control Message Protocol) echo kérési üzeneteket is küld az egyik ügyfélszámítógépről egy másikra. Ezzel a kommunikációval ellenőrizhető, hogy a másik ügyfélszámítógép ébrenléti állapotban van-e a hálózatban. Az ICMP-t néha TCP/IP ping parancsnak is nevezik.  

 Az ébresztési proxyval kapcsolatos további információkért lásd: [tervezése a System Center Configuration Manager ügyfelek felébresztése](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

### <a name="windows-event-viewer-windows-performance-monitor-and-windows-diagnostics"></a>A Windows eseménynapló, a Windows teljesítményfigyelő és a Windows diagnosztika  
 Fér hozzá a Windows Eseménynapló, a Windows Teljesítményfigyelőt és a Windows diagnosztika a Configuration Manager konzolról, engedélyezze a **fájl- és nyomtatómegosztás** elemet kivételként a Windows tűzfalon.  

## <a name="ports-used-during-configuration-manager-client-deployment"></a>A Configuration Manager-ügyfelek központi telepítése során használt portok  
 Az alábbi táblázatok felsorolják az ügyféltelepítés során használt portokat.  

> [!IMPORTANT]  
>  Ha a helyrendszer-kiszolgálók és az ügyfélszámítógép között tűzfal található, ellenőrizze, hogy a tűzfal engedélyezi-e a forgalmat a kiválasztott ügyfél-telepítési módszerhez szükséges portokon. A tűzfalak miatt például gyakran sikertelen az ügyfélleküldéses telepítés, mivel letiltják a kiszolgálói üzenetblokkot (SMB) és a távoli eljáráshívásokat (RPC). Ebben az esetben válasszon másik ügyfél-telepítési módszert, például kézi telepítést (a CCMSetup.exe futtatásával), illetve csoportházirend-alapú ügyféltelepítést. Ezekhez az alternatív ügyfél-telepítési eljárásokhoz nem szükséges SMB vagy RPC.  

 További információ a Windows tűzfal konfigurálásáról az ügyfélszámítógépen: [A Windows tűzfal által engedélyezett portok és programok módosítása](#BKMK_ModifyingWindowsFirewall).  

### <a name="ports-that-are-used-for-all-installation-methods"></a>Az összes telepítési módszer során használt portok  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről a tartalék állapotkezelő pontba, amennyiben a tartalék állapotkezelő pont az ügyfélhez van rendelve.|--|80 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  

### <a name="ports-that-are-used-with-client-push-installation"></a>Az ügyfélleküldéses telepítés során használt portok  
 A következő táblázatban felsorolt portokon kívül az ügyfélleküldéses telepítés ICMP (Internet Control Message Protocol) echo kérési üzeneteket is küld a helykiszolgálóról az ügyfélszámítógépre, hogy ellenőrizze az ügyfélszámítógép elérhetőségét a hálózaton. Az ICMP-t néha TCP/IP ping parancsnak is nevezik. Az ICMP-hez nem tartozik UDP- vagy TCP-protokollszám, és ezért nincs felsorolva a következő táblázatban. A beavatkozó hálózati eszközöknek, például a tűzfalaknak azonban engedélyezniük kell az ICMP-forgalmat az ügyfélleküldéses telepítés sikeressége érdekében.  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Kiszolgálói üzenetblokk (SMB) a helykiszolgáló és az ügyfélszámítógép között.|--|445|  
|RPC végpontleképező a helykiszolgáló és az ügyfélszámítógép között.|135|135|  
|RPC dinamikus portok a helykiszolgáló és az ügyfélszámítógép között.|--|DINAMIKUS|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről egy felügyeleti pontba, amennyiben a kapcsolat HTTP-alapú.|--|80 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Secure Hypertext Transfer Protocol (HTTPS) az ügyfélszámítógépről a felügyeleti pontba, amennyiben a kapcsolat HTTPS-alapú.|--|443 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  

### <a name="ports-that-are-used-with-software-update-point-based-installation"></a>Szoftverfrissítésipont-alapú telepítéshez használt portok  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről a szoftverfrissítési pontba.|--|80 vagy 8530 (Lásd a 2. megjegyzést: **Windows Server Update Services**)|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről a szoftverfrissítési pontba.|--|443 vagy 8531 (Lásd a 2. megjegyzést: **Windows Server Update Services**)|  
|Server Message Block (SMB) a forráskiszolgáló és a CCMSetup parancssori tulajdonság megadása esetén az ügyfélszámítógép között **/source:&lt;elérési\>**.|--|445|  

### <a name="ports-that-are-used-with-group-policy-based-installation"></a>Csoportházirend-alapú telepítéshez használt portok  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről egy felügyeleti pontba, amennyiben a kapcsolat HTTP-alapú.|--|80 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Secure Hypertext Transfer Protocol (HTTPS) az ügyfélszámítógépről a felügyeleti pontba, amennyiben a kapcsolat HTTPS-alapú.|--|443 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Server Message Block (SMB) a forráskiszolgáló és a CCMSetup parancssori tulajdonság megadása esetén az ügyfélszámítógép között **/source:&lt;elérési\>**.|--|445|  

### <a name="ports-that-are-used-with-manual-installation-and-logon-script-based-installation"></a>Kézi és bejelentkezési parancsprogramfájlokon alapuló telepítéshez használt portok  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Kiszolgálói üzenetblokk (SMB) az ügyfélszámítógép és azon hálózati megosztás között, amelyen a CCMSetup.exe fájl fut.<br /><br /> Amikor telepíti a Configuration Manager, az ügyfél-telepítési forrásfájlok másolta, és automatikusan a  *&lt;Telepítésiútvonal\>*\Client mappából a felügyeleti pontokon. Ezek a fájlok azonban lemásolhatók és újonnan megoszthatók a hálózatban lévő számítógépeken. Másik lehetőségként a CCMSetup.exe fájl helyi, például cserélhető adathordozón történő futtatásával meg is szüntethető ez a hálózati forgalom.|--|445|  
|Hypertext Transfer Protocol (HTTP) az ügyfélszámítógépről egy felügyeleti pontba, amennyiben a kapcsolat HTTP Protokollon keresztül, és nincs megadva a CCMSetup parancssori tulajdonság **/source:&lt;elérési\>**.|--|80 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Secure Hypertext Transfer Protocol (HTTPS) az ügyfélszámítógépről egy felügyeleti ponthoz, amikor a kapcsolat HTTPS-en keresztül, és nincs megadva a CCMSetup parancssori tulajdonság **/source:&lt;elérési\>**.|--|443 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Server Message Block (SMB) a forráskiszolgáló és a CCMSetup parancssori tulajdonság megadása esetén az ügyfélszámítógép között **/source:&lt;elérési\>**.|--|445|  

### <a name="ports-that-are-used-with-software-distribution-based-installation"></a>Szoftverterjesztés-alapú telepítéshez használt portok  

|Leírás|UDP|TCP|  
|-----------------|---------|---------|  
|Kiszolgálói üzenetblokk (SMB) a terjesztési pont és az ügyfélszámítógép között.|--|445|  
|Hypertext Transfer Protocol (HTTP) az ügyfélről egy terjesztési pontba, amennyiben a kapcsolat HTTP-alapú.|--|80 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  
|Secure Hypertext Transfer Protocol (HTTPS) az ügyfélről egy terjesztési pontba, amennyiben a kapcsolat HTTPS-alapú.|--|443 (Lásd az 1. megjegyzést: **Elérhető alternatív port**)|  

## <a name="notes"></a>Megjegyzések  
 **1 elérhető alternatív Port** a Configuration Managerben, megadhatja ezt az értéket az alternatív port. Egyéni port definiálása esetén helyettesítse be ezt az egyéni portot az IPsec-házirendek IP-szűrési adatainak definiálásakor vagy a tűzfalak konfigurálásakor.  

 **2 Windows Server Update Services** A Windows Server Update Services (WSUS) az alapértelmezett webhelyre (80-as port) vagy egyéni webhelyre (8530-as port) telepíthető.  

 Telepítés után a port módosítható. Nem kell ugyanazt a portszámot használni a teljes helyhierarchiában.  

 Ha a HTTP-port a 80-as, akkor a HTTPS-portnak a 443-asnak kell lennie.  

 Ha a HTTP-port bármi más, a HTTPS-portnak 1-gyel nagyobbnak kell lennie. Például 8530-as és 8531-es.

