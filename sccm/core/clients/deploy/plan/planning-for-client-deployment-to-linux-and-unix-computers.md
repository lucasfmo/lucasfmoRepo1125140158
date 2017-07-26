---
title: "Ügyfelek Linux és UNIX rendszerű számítógépekre való központi telepítésének megtervezése |} Microsoft Docs"
description: "Tervezze meg a Linux és UNIX rendszerű számítógépekre a System Center Configuration Managerben történő központi ügyféltelepítésre."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 367ffb919a1adb9a0530f7357a0fcf1e6636af08
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-linux-and-unix-computers-in-system-center-configuration-manager"></a>Az ügyfelek Linux vagy UNIX rendszerű számítógépekre való központi telepítésének megtervezése System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-ügyfél Linux vagy UNIX rendszert futtató számítógépeken is telepíthető. Ez az ügyfél munkacsoportbeli számítógépként működő kiszolgálókhoz készült, és nem támogatja a bejelentkezett felhasználókkal való kommunikációt. Miután telepítette az ügyfélszoftvert, és az ügyfél a Configuration Manager-hely kommunikációt létesít, az ügyfél segítségével kezeli a Configuration Manager konzoljáról és jelentéseiből.  

> [!NOTE]  
>  A Configuration Manager-ügyfél Linux és UNIX rendszerű számítógépeken nem támogatja a következő felügyeleti lehetőségei:  
>   
>  -   Ügyfél leküldéses telepítése  
> -   Operációs rendszer központi telepítése  
> -   Alkalmazások központi telepítése; helyette a szoftvereket csomagokkal és programokkal telepítheti.  
> -   Szoftverleltár  
> -   Szoftverfrissítések  
> -   Megfelelőségi beállítások  
> -   Távvezérlés  
> -   Energiagazdálkodás  
> -   Ügyfélállapot ellenőrzése és hibák elhárítása  
> -   Internetalapú ügyfélkezelés  

 További információk a Linux és a UNIX támogatott disztribúcióiról, valamint az ügyfél Linux és UNIX rendszerben történő támogatásához szükséges hardverről: [A System Center Configuration Manager használatához ajánlott hardver](../../../../core/plan-design/configs/recommended-hardware.md).  

 Olvassa el ebben a cikkben a Configuration Manager-ügyfél telepítése Linux és UNIX rendszerű tervezéséhez nyújtanak segítséget.  

##  <a name="BKMK_ClientDeployPrereqforLnU"></a>Linux és UNIX rendszerű kiszolgálókra az ügyfelek központi telepítésének előfeltételei  
 Az alábbi információk alapján megállapíthatja, hogy milyen előfeltételeknek kell teljesülniük a Linuxra és UNIX-ra készült ügyfél sikeres telepítéséhez.  

###  <a name="BKMK_ClientDeployExternalforLnU"></a>A Configuration Manageren kívüli függőségek:  
 Az alábbi táblázatban láthatók a szükséges UNIX és Linux operációs rendszerek, valamint csomagfüggőségek.  

 **Red Hat Enterprise Linux-ES kiadás 4**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc|Szabványos C-függvénytárak|2.3.4-2|  
|Openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.7a-43.1|  
|PAM|Cserélhető hitelesítési modulok|0.77-65.1|  

 **Red Hat Enterprise Linux Server kiadás 5.1 (Tikanga)**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc|Szabványos C-függvénytárak|2.5-12|  
|Openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.8b-8.3.el5|  
|PAM|Cserélhető hitelesítési modulok|0.99.6.2-3.14.el5|  

 **Red Hat Enterprise Linux Server kiadás 6**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc|Szabványos C-függvénytárak|2.12-1.7|  
|Openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|1.0.0-4|  
|PAM|Cserélhető hitelesítési modulok|1.1.1-4|  

 **Solaris 9 SPARC**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Szükséges javítás az operációs rendszerhez|PAM-memóriavesztés|112960-48|  
|SUNWlibC|Sun Workshop Compilers – kötegelt libC (sparc)|5.9,REV=2002.03.18|  
|SUNWlibms|Forte fejlesztői kötegelt és megosztott libm (sparc)|5.9,REV=2001.12.10|  
|OpenSSL|SMCosslg (sparc)<br /><br /> A Sun nem biztosít OpenSSL csomagot a Solaris 9 SPARC rendszerhez. A Sunfreeware oldaláról azonban elérhető egy verzió.|0.9.7g|  
|PAM|Cserélhető hitelesítési modulok<br /><br /> SUNWcsl, Solaris alaprendszer (megosztott függvénytárak) (sparc)|11.9.0,REV=2002.04.06.15.27|  

 **Solaris 10 SPARC**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Szükséges javítás az operációs rendszerhez|PAM-memóriavesztés|117463-05|  
|SUNWlibC|Sun Workshop Compilers – kötegelt libC (sparc)|5.10, REV=2004.12.22|  
|SUNWlibms|Matematikai & microtasking könyvtárak (Usr) (sparc)|5.10, REV=2004.11.23|  
|SUNWlibmsr|Matematikai & microtasking könyvtárak (Root) (sparc)|5.10, REV=2004.11.23|  
|SUNWcslr|A Solaris alap függvénytárai (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|SUNWcsl|A Solaris alap függvénytárai (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|OpenSSL|SUNopenssl-könyvtárak (Usr)<br /><br /> A Sun biztosítja az OpenSSL könyvtárakat a Solaris 10 SPARC-hoz. A könyvtárak egybe vannak csomagolva az operációs rendszerrel.|11.10.0,REV=2005.01.21.15.53|  
|PAM|Cserélhető hitelesítési modulok<br /><br /> SUNWcsr, Solaris alap (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  

 **Solaris 10 x86**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Szükséges javítás az operációs rendszerhez|PAM-memóriavesztés|117464-04|  
|SUNWlibC|Sun Workshop Compilers – kötegelt libC (i386)|5.10,REV=2004.12.20|  
|SUNWlibmsr|Matematikai & microtasking könyvtárak (Root) (i386)|5.10, REV=2004.12.18|  
|SUNWcsl|Solaris alaprendszer (megosztott függvénytárak) (i386)|11.10.0,REV=2005.01.21.16.34|  
|SUNWcslr|A Solaris alap függvénytárai (Root) (i386)|11.10.0, REV=2005.01.21.16.34|  
|OpenSSL|SUNWopenssl-libraries; OpenSSL-függvénytárak (Usr) (i386)|11.10.0, REV=2005.01.21.16.34|  
|PAM|Cserélhető hitelesítési modulok<br /><br /> SUNWcsr Solaris alaprendszer (Root) (i386)|11.10.0,REV=2005.01.21.16.34|  

 **Solaris 11 SPARC**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|SUNWlibC|Sun Workshop Compilers – kötegelt libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Matematikai és feladatfelosztási függvénytárak (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|A Solaris alap függvénytárai (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Solaris alaprendszer (megosztott függvénytárak)|11.11, REV=2009.11.11|  
|SUNWcsr|Solaris alaprendszer (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL-függvénytárak (Usr)|11.11.0,REV=2010.05.25.01.00|  

 **Solaris 11 x86**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------|-----------|---------------|  
|SUNWlibC|Sun Workshop Compilers – kötegelt libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Matematikai és feladatfelosztási függvénytárak (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|A Solaris alap függvénytárai (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Solaris alaprendszer (megosztott függvénytárak)|11.11, REV=2009.11.11|  
|SUNWcsr|Solaris alaprendszer (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL-függvénytárak (Usr)|11.11.0,REV=2010.05.25.01.00|  

 **SUSE Linux Enterprise Server 9 (i586)**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Service Pack 4|SUSE Linux Enterprise Server 9||  
|OS Patch lib gcc-41.rpm|Szabványos megosztott függvénytár|41-4.1.2_20070115-0.6|  
|OS Patch lib stdc++-41.rpm|Szabványos megosztott függvénytár|41-4.1.2_20070115-0.6|  
|Openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.7d-15.35|  
|PAM|Cserélhető hitelesítési modulok|0.77-221-11|  

 **SUSE Linux Enterprise Server 10 SP1 (i586)**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc-2.4-31.30|Szabványos megosztott C-függvénytár|2.4-31.30|  
|OpenSSL|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.90,8a-18,15|  
|PAM|Cserélhető hitelesítési modulok|0.99.6.3-28.8|  

 **SUSE Linux Enterprise Server 11 (i586)**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc-2.9-13.2|Szabványos megosztott C-függvénytár|2.9-13.2|  
|PAM|Cserélhető hitelesítési modulok|pam-1.0.2-20.1|  

 **Univerzális Linux (Debian-csomag) – Debian, Ubuntu Server**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|libc6|Szabványos megosztott C-függvénytár|2.3.6|  
|OpenSSL|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.8 vagy 1.0|  
|PAM|Cserélhető hitelesítési modulok|0.79-3|  

 **Univerzális Linux (RPM-csomag) – CentOS, Oracle Linux**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|glibc|Szabványos megosztott C-függvénytár|2.5-12|  
|OpenSSL|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.8 vagy 1.0|  
|PAM|Cserélhető hitelesítési modulok|0.99.6.2-3.14|  

 **IBM AIX 5L 5.3**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Operációs rendszer verziója|Operációs rendszer verziója|AIX 5.3, 6. technológiai szint, 5. szervizcsomag|  
|xlC.rte|XL C/C++ futtatókörnyezet|9.0.0.2|  
|openssl.base|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.8.4|  

 **IBM AIX 6.1**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Operációs rendszer verziója|Operációs rendszer verziója|AIX 6.1, minden technológiai szint és szervizcsomag|  
|xlC.rte|XL C/C++ futtatókörnyezet|9.0.0.5|  
|OpenSSL/openssl.base|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|0.9.8.4|  

 **IBM AIX 7.1 (Power)**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|Operációs rendszer verziója|Operációs rendszer verziója|AIX 7.1, minden technológiai szint és szervizcsomag|  
|xlC.rte|XL C/C++ futtatókörnyezet||  
|OpenSSL/openssl.base|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll||  

 **HP-UX 11i v2 IA-64**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|HPUXBaseOS|Alap operációs rendszer|B.11.23|  
|HPUXBaseAux|HP-UX alap operációs rendszer – kiegészítő|B.11.23.0706|  
|HPUXBaseAux.openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|A.00.09.07l.003|  
|PAM|Cserélhető hitelesítési modulok|A HP-UX rendszeren a PAM az alap operációs rendszeri összetevők része. Nincsenek más függőségek.|  

 **HP-UX 11i v2 PA-RISC**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX alap operációsrendszer-környezet|B.11.23.0706|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Kompatibilis fejlesztőeszköz-függvénytárak|B.11.23|  
|HPUXBaseAux|HP-UX alap operációs rendszer – kiegészítő|B.11.23.0706|  
|HPUXBaseAux.openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|A.00.09.071.003|  
|PAM|Cserélhető hitelesítési modulok|A HP-UX rendszeren a PAM az alap operációs rendszeri összetevők része. Nincsenek más függőségek.|  

 **HP-UX 11i v3 PA-RISC**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX alap operációsrendszer-környezet|B.110,310,0709|  
|OS-Core.MinimumRuntime.CORE2-SHLIBS|IA-specifikus emulátor függvénytárak|B.110,31|  
|openssl/Openssl.openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|A.00.09.08d.002|  
|PAM|Cserélhető hitelesítési modulok|A HP-UX rendszeren a PAM az alap operációs rendszeri összetevők része. Nincsenek más függőségek.|  

 **HP-UX 11i v3 IA64**  

|Szükséges csomag|Leírás|Minimális verzió|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX alap operációsrendszer-környezet|B.110,310,0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|IA-specifikus fejlesztő függvénytárak|B.110,31|  
|SysMgmtMin|Minimálisan szükséges szoftvertelepítési eszközök|B.110,310,0709|  
|SysMgmtMin.openssl|OpenSSL-függvénytárak, biztonságos hálózati kommunikációs protokoll|A.00.09.08d.002|  
|PAM|Cserélhető hitelesítési modulok|A HP-UX rendszeren a PAM az alap operációs rendszeri összetevők része. Nincsenek más függőségek.|  

 **A Configuration Manager függőségek:** Az alábbi táblázat a Linux és UNIX rendszerű ügyfeleket támogató helyrendszerszerepkörök. További információ ezekről a helyrendszerszerepkörökről: [A System Center Configuration Manager-ügyfelek helyrendszerszerepköreinek meghatározása](../../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|A Configuration Manager-helyrendszer|További információ|  
|---------------------------------------|----------------------|  
|Felügyeleti pont|Bár a felügyeleti pont nem szükséges a Configuration Manager-ügyfél telepítése Linux és UNIX rendszerekhez készült, rendelkeznie kell a felügyeleti pontok információt továbbítanak az ügyfélszámítógépek és a Configuration Manager-kiszolgálók között. Felügyeleti pontok nélkül nem tudja felügyelni az ügyfélszámítógépeket.|  
|Terjesztési pont|A terjesztési pont nincs szükség a Configuration Manager-ügyfél telepítése Linux és UNIX rendszerekhez készült. ha azonban Linux- és UNIX-alapú kiszolgálókra szeretne központilag szoftvereket telepíteni, ahhoz szükség van a helyrendszerszerepkörre.<br /><br /> A Configuration Manager-ügyfél Linux és UNIX rendszerű nem támogatja a kommunikációt az SMB, a terjesztési pontokat, az ügyféllel használt támogatnia kell a HTTP vagy HTTPS-kommunikációt.|  
|Tartalék állapotkezelő pont|A tartalék állapotkezelő pont nincs szükség a Configuration Manager-ügyfél telepítése Linux és UNIX rendszerekhez készült. A tartalék állapotkezelő pont azonban lehetővé teszi, hogy a Configuration Manager-hely, hogy állapotüzenetet küldjenek, amikor nem tudnak kommunikálni egy felügyeleti pont számítógépén. Az ügyfelek a telepítési állapotukat is elküldhetik a tartalék állapotkezelő pontnak.|  

 **Tűzfallal kapcsolatos követelmények**: Győződjön meg arról, hogy tűzfalak ne blokkolják a kommunikációt a portokat, adja meg, mint az ügyfélgépek kérelmeihez használt portszámokról között. A Linuxra és UNIX-ra készült ügyfél közvetlenül kommunikál a felügyeleti pontokkal, a terjesztési pontokkal és a tartalék állapotkezelő pontokkal.  

 További információ az ügyfél-kommunikációról és a kérelmek portjairól: [Az ügyfél konfigurálása Linux és UNIX rendszerekhez a felügyeleti pontok megkeresésére](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigClientMP).  

##  <a name="BKMK_PlanningforCommunicationsforLnU"></a>Linux és UNIX rendszerű kiszolgálók kommunikáció tervezése az erdőszintű Megbízhatóságok  
 Kezelheti a Configuration Manager Linux és UNIX rendszerű kiszolgálók munkacsoportbeli ügyfélként működnek, és egy munkacsoportban lévő Windows-alapú ügyfelekhez hasonló konfigurációt igényelnek. Információ a munkacsoportokban lévő számítógépek kommunikációjáról: [Active Directory-erdőkön keresztüli kommunikáció](../../../../core/plan-design/hierarchy/communications-between-endpoints.md#Plan_Com_X-Forest) szakasz a [Végpontok közötti kommunikáció a System Center Configuration Managerben](../../../../core/plan-design/hierarchy/communications-between-endpoints.md) témakörben.  

###  <a name="BKMK_ServiceLocationforLnU"></a>Szolgáltatáskeresés a Linuxra és UNIX-ügyfél által  
 Az ügyfelek számára szolgáltatást biztosító helyrendszer-kiszolgáló megkeresése a szolgáltatáskeresés. A Windows-alapú ügyfelektől eltérően a Linuxra és UNIX-ra készült ügyfél nem használ Active Directoryt a szolgáltatáskereséshez. Emellett a Configuration Manager-ügyfél Linux és UNIX rendszerű nem támogatja egy ügyféltulajdonságot, amely meghatározza a felügyeleti pont tartományutótagját. Ezzel szemben az ügyfélgép az ügyfélszoftver telepítésekor kijelölt ismert felügyeleti pontról kap információkat az ügyfeleknek szolgáltatásokat nyújtó további helyrendszer-kiszolgálókról.  

 További információt a szolgáltatások helyének meghatározására szolgáló módszerről [A System Center Configuration Managerben az ügyfelek által végzett helyerőforrás- és szolgáltatáskeresés ismertetése](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) című témakör [Szolgáltatáskeresés és az ügyfélhez rendelt felügyeleti pont meghatározása az ügyfél által](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) című szakaszában talál.  

##  <a name="BKMK_SecurityforLnU"></a>Biztonság és a tanúsítványok tervezése Linux és UNIX rendszerű kiszolgálók  
 A Configuration Manager-helyek biztonságos és hitelesített kommunikáció a Configuration Manager-ügyfél Linux és UNIX rendszerű ugyanannak a modellnek használja a Configuration Manager-ügyfél a Windows kommunikációs.  

 A Linux és UNIX rendszerű ügyfél telepítésekor rendelhet hozzá az ügyfél PKI-tanúsítványt, amely engedélyezi a HTTPS protokoll használatával kommunikálnak a Configuration Manager-helyek számára. Ha nem oszt ki PKI-tanúsítványt, az ügyfél önaláírt tanúsítványt hoz létre, és csak HTTP-alapú kommunikációt fog folytatni.  

 Azok az ügyfelek, amelyek a telepítéskor PKI-tanúsítványt kapnak, HTTPS protokollon fognak kommunikálni a felügyeleti pontokkal. Ha az ügyfél nem talál olyan felügyeleti pontot, amely támogatja a HTTPS protokollt, helyettesítő megoldásként HTTP-alapú kommunikációt fog folytatni a megadott PKI-tanúsítvány használatával.  

 Ha a Linux- vagy UNIX-alapú ügyfél PKI-tanúsítványt használ, abban az esetben nincs szükség jóváhagyásra. Amikor egy ügyfél egy önaláírt tanúsítványt használ, tekintse át a Configuration Manager konzolon ügyféljóváhagyás hierarchia beállításait. Ha nem a **Minden számítógép automatikus jóváhagyása (nem javasolt)** ügyfél-jóváhagyási módszer van beállítva, akkor manuális módszerrel kell jóváhagynia az ügyfelet.  

 További információt az ügyfél manuális jóváhagyásáról az [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../../core/clients/manage/manage-clients.md) című témakör [Ügyfelek kezelése az Eszközök csomópontból](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode) szakaszában találhat.  

 A Configuration Manager tanúsítványok használatával kapcsolatos információkért lásd: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

###  <a name="BKMK_AboutCertsforLnU"></a>Linux és UNIX rendszerű kiszolgálók által használt tanúsítványok  
 A Configuration Manager-ügyfél Linux és UNIX rendszerű egy önaláírt tanúsítványt vagy a Windows-alapú ügyfelekhez hasonlóan egy X.509 PKI-tanúsítványt használ. Nincsenek nem módosult a Configuration Manager helyrendszerei PKI követelményei Linux és UNIX rendszerű ügyfelek kezelésére is.  

 A tanúsítványok használhatja a Linux és UNIX-ügyfelek, amelyek kommunikálni a Configuration Manager helyrendszerei egy szabványos nyilvános kulcsú tanúsítványok (PKCS #12) formátumúnak kell lennie, és a jelszót kell lennie, meg kell adnia azt az ügyfél a PKI-tanúsítvány megadása.  

 A Configuration Manager-ügyfél Linux és UNIX rendszerű egyszeres PKI-tanúsítványokat támogatja, és nem támogatja a több tanúsítványt. Ezért a tanúsítvány kiválasztási feltételeinek konfigurál egy Configuration Manager hely nem érvényes.  

###  <a name="BKMK_ConfigCertsforLnU"></a>Tanúsítványok konfigurálása Linux és UNIX rendszerű kiszolgálók  
 A Configuration Manager-ügyfél Linux és UNIX rendszerű kiszolgálók HTTPS-kommunikáció használatára konfigurálja, konfigurálnia kell az ügyfél PKI-tanúsítványt az ügyfél telepítése során használt. A tanúsítvány konfigurálása az ügyfélszoftver telepítése előtt nem lehetséges.  

 PKI-tanúsítványt használó ügyfél telepítésekor a **-UsePKICert** parancssori paraméter segítségével adhatja meg a PKI-tanúsítványt tartalmazó PKCS#12-fájl helyét és nevét. Emellett a **-certpw** parancssori paraméterrel meg kell adnia a tanúsítvány jelszavát is.  

 Ha nem adja meg a **-UsePKICert** paramétert, az ügyfél önaláírt tanúsítványt generált, és csak HTTP protokollal próbál kommunikálni a helyrendszerkiszolgálókkal.  

##  <a name="BKMK_NoSHA-256"></a>Linux és UNIX operációs rendszerek, hajtsa végre a nem támogatja az SHA-256  
 A következő Linux és UNIX operációs rendszerek a Configuration Manager-ügyfélként támogatott kiadott olyan OpenSSL-verziót, amelyek nem támogatják az SHA-256 algoritmust:  

-   Red Hat Enterprise Linux 4 (x86/x64)  

-   Solaris 9 (SPARC) és Solaris 10 (SPARC/x86)  

-   SUSE Linux Enterprise Server 9 (x86)  

-   HP-UX 11iv2 (PA-RISH/IA64)  

 Az alábbi operációs rendszerek Configuration Managerrel kezeléséhez telepítenie kell a Configuration Manager-ügyfél Linux és UNIX rendszerű, amely arra utasítja az ügyfelet az SHA-256 ellenőrzésének kihagyására parancssori kapcsolóval. A Configuration Manager ügyfelek, amelyek az operációs rendszerek futnak mint SHA-256 algoritmust támogató ügyfelek kevésbé biztonságos üzemmódban működjenek. Erre a kevésbé biztonságos üzemmódra a következők jellemzők:  

-   Az ügyfelek nem ellenőrzik a felügyeleti pontról lekért házirendhez tartozó helykiszolgálói aláírást.  

-   Az ügyfelek nem ellenőrzik a terjesztési pontról letöltött csomagok kivonatait.  

> [!IMPORTANT]  
>  Az **ignoreSHA256validation** kapcsolóval a Linuxra és UNIX-ra készült ügyfél csökkentett biztonságú üzemmódban futtatható. Ez régebbi platformok esetében lehet célszerű, amelyek nem támogatják az SHA-256 algoritmust. Ez egy felülbíráló jellegű biztonsági beállítás, amelyet a Microsoft nem javasol, de biztonságos és megbízható adatközponti környezetben használható.  

 Amikor telepíti a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült, akkor a telepítő parancsprogram ellenőrzi az operációs rendszer verzióját. Alapértelmezés szerint ha az operációs rendszer verziójával nélkül SHA-256 algoritmust támogató OpenSSL-verzióval rendelkezik, amely azonosítja a Configuration Manager-ügyfél nem telepíthető.  

 Telepíti a Configuration Manager-ügyfél Linux és UNIX operációs rendszeren nem SHA-256 algoritmust támogató OpenSSL-verzióval rendelkező, a parancssori kapcsolót kell használnia **ignoreSHA256validation**. Ha a parancssori kapcsolót megfelelő Linux vagy UNIX operációs rendszeren használja, a Configuration Manager-ügyfél fog SHA-256 ellenőrzésének kihagyására, és a telepítés után az ügyfél nem használja az SHA-256 bejelentkezési adatok, a helyrendszerekre HTTP-n keresztül. A Linux és UNIX ügyfelek tanúsítványok használatára való konfigurálásával kapcsolatban olvassa el jelen témakör [A biztonság és a tanúsítványok tervezése Linux- és UNIX-alapú kiszolgálók esetén](#BKMK_SecurityforLnU) című szakaszát. További információt arról, hogy szükséges-e az SHA-256, [A biztonság konfigurálása a System Center Configuration Managerben](../../../../core/plan-design/security/configure-security.md) című témakör [Az aláírás és titkosítás konfigurálása](../../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) című szakaszában talál.  

> [!NOTE]  
>  Az SHA-256 algoritmust támogató OpenSSL-verzióval rendelkező Linux vagy UNIX rendszerű számítógépeken a telepítő figyelmen kívül hagyja az **ignoreSHA256validation** parancssori kapcsolót.  

