---
title: "A feladatütemezési műveletek változói feladat |} Microsoft Docs"
description: "Feladatütemezési művelet változói hálózati beállítás változók, például használatával határozhatja meg a Configuration Manager feladatütemezés konfigurációs beállításai egyetlen lépésben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: 10
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 6049ec2369e0a97b21ce6523ba8448335385ab9a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>Feladatütemezési művelet változói a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezési művelet változói adja meg, hogy egy System Center Configuration Manager feladatütemezési lépésben által használt beállításait. Alapértelmezés szerint a feladatütemezési lépés által használt beállításokat a rendszer a lépés futtatása előtt inicializálja, és azok csak a kapcsolódó feladatütemezési lépés futtatása közben érhetők el. Ez azt jelenti, hogy a feladatütemezési változó beállítását a rendszer a feladatütemezési lépés futtatása előtt hozzáadja a feladatütemezési környezethez, a feladatütemezési lépés futtatása után pedig eltávolítja a feladatütemezési környezetből.  

## <a name="action-variable-example"></a>Példa műveleti változóra  
 A **Parancssor futtatása** feladatütemezési lépéssel lehetősége van például megadni egy indítási könyvtárat a parancssori műveletekhez. A lépéshez tartozik az **Indítás helye** tulajdonság, melynek alapértelmezett értékét a rendszer a **WorkingDirectory** változó értékeként a feladatütemezési környezetben tárolja. A **WorkingDirectory** környezeti változót a rendszer a **Parancssor futtatása** feladatütemezési művelet futtatása előtt inicializálja. A **Parancssor futtatása** lépés során a **WorkingDirectory** érték az **Indítás helye** tulajdonságon keresztül érhető el. Miután a feladatütemezési lépés befejeződött, a **WorkingDirectory** változó törlődik a feladatütemezési környezetből. Ha az ütemezés egy másik **Parancssor futtatása** feladatütemezési lépést is tartalmaz, a rendszer inicializálja az új **WorkingDirectory** változót, és értékét az adott feladatütemezési lépéshez tartozó kezdőértékre állítja.  

 Bár a feladatütemezési művelet beállításának alapértelmezett értéke jelen van a feladatütemezési lépés futtatása közben, az újonnan beállított értékeket az ütemezés több lépése is használhatja. Ha a feladatütemezési változók létrehozására szolgáló egyik módszerrel a beépített változóértéket felülírja, az új érték a környezetben marad, és felülírja a feladatütemezés további lépéseinek alapértelmezett értékét. Az előző példában ha egy **feladatütemezési változó beállítása** lépés meg van adva az első lépés a feladatütemezés, és beállítja a **WorkingDirectory** környezeti változó értékét **C:\\**, mindkét **parancssor futtatása** a feladatütemezés lépéseinek az új kezdőkönyvtárértéket fogja használni.  

## <a name="action-variables-for-task-sequence-actions"></a>Feladatütemezési műveletek műveleti változói  
 A Configuration Manager feladatütemezési változói a társított feladatütemezési művelet szerint vannak csoportosítva. Az alábbi hivatkozásokra kattintva az adott művelethez társított műveleti változókról tudhat meg többet. A feladatütemezés változói határozzák meg a feladatütemezési művelet működését. A feladatütemezési művelet a bemeneti változóként megjelölt változókat olvassa be és használja. Alternatív megoldásként a Feladatütemezés megadása művelet vagy a TSEnvironment COM-objektum használatával is megadhatja a változókat futás közben. Csak a feladatütemezési művelet jelöli a változókat kimeneti változókként, amelyeket a feladatütemezés során később végzett műveletek olvasnak be.  

> [!NOTE]  
>  Nem minden feladatütemezési művelet van feladatütemezési változók egy csoportjához társítva. Például bár a BitLocker engedélyezése művelethez változók vannak társítva, a BitLocker letiltása műveletnek nincsenek társított változói.  

###  <a name="BKMK_ApplyDataImage"></a> Az Adatlemezképfájl alkalmazása feladatütemezési művelet változói  
 Ennek a műveletnek a változói azt határozzák meg, hogy a rendszer a WIM-fájl melyik képfájlját alkalmazza a célszámítógép esetében, és hogy törölje-e a fájlokat a célpartíción. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [alkalmazása adatok kép feladatütemezési lépés](task-sequence-steps.md#BKMK_ApplyDataImage).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (bemenet)|A célszámítógépen alkalmazott képfájl indexértékét adja meg.|  
|OSDWipeDestinationPartition<br /><br /> (bemenet)|Meghatározza, hogy a rendszer törli-e a célpartíción található fájlokat.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  

###  <a name="BKMK_ApplyDriverPackage"></a> Az Illesztőprogram-csomag alkalmazása feladatütemezési művelet változói  
 A művelet változói a háttértár-illesztőprogramok telepítésére vonatkozóan tartalmaznak információkat, illetve meghatározzák, hogy az aláírás nélküli illesztőprogramok telepíthetők-e. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [illesztőprogram-csomag alkalmazása](task-sequence-steps.md#BKMK_ApplyDriverPackage).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (bemenet)|Az illesztőprogram-csomagból telepítendő háttértár-illesztőprogram tartalomazonosítóját határozza meg. Ha nincs megadva, a rendszer nem telepít háttértár-illesztőprogramot.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (bemenet)|A telepítendő háttértár-illesztőprogramhoz tartozó INF-fájlt adja meg.<br /><br /> <br /><br /> Az OSDApplyDriverBootCriticalContentUniqueID beállítása esetén ezt a feladatütemezési változót kötelező megadni.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (bemenet)|Megadja, hogy a háttértár-illesztőprogram telepítve van, csak lehet **scsi**.<br /><br /> <br /><br /> Az OSDApplyDriverBootCriticalContentUniqueID beállítása esetén ezt a feladatütemezési változót kötelező megadni.|  
|OSDApplyDriverBootCriticalID<br /><br /> (bemenet)|A telepítendő háttértár-illesztőprogram rendszerindításhoz szükséges azonosítóját határozza meg. Ez az azonosító szerepel a "**scsi**" szakaszában az eszközillesztő txtsetup.oem fájlt.<br /><br /> <br /><br /> Az OSDApplyDriverBootCriticalContentUniqueID beállítása esetén ezt a feladatütemezési változót kötelező megadni.|  
|OSDAllowUnsignedDriver<br /><br /> (bemenet)|Meghatározza, hogy a Windows az aláírás nélküli illesztőprogramok telepítésének engedélyezésére legyen-e beállítva. Ez a feladatütemezési változó a Windows Vista és későbbi operációs rendszerek központi telepítésekor nem használatos.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  

###  <a name="BKMK_ApplyNetworkSettings"></a> A Hálózati beállítások alkalmazása feladatütemezési művelet változói  
 A művelethez tartozó változók a célszámítógép hálózati beállításait (például a számítógép hálózati adapterének beállításait, a tartománybeállításokat és a munkacsoport-beállításokat) határozzák meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [alkalmazni a hálózati beállítások lépés](task-sequence-steps.md#BKMK_ApplyNetworkSettings).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (bemenet)|Ez a feladatütemezési változó egy tömbváltozó. A tömb egyes elemei a számítógép egyes hálózati adaptereinek beállításait jelölik. Az egyes adapterekhez definiált beállítások a tömbváltozó nevének, a nulla alapú hálózatiadapter-indexnek és a tulajdonságnévnek a kombinálásával érhetők el.<br /><br /> <br /><br /> Ha a feladatütemezési művelet több hálózati adaptert konfigurál, a második hálózati adapter tulajdonságainak definiálásához az adapter indexét kell használni a változónévben. Például: OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList, OSDAdapter1EnableWINS stb.<br /><br /> <br /><br /> A következő változónevek például a feladatütemezési művelet által konfigurált első hálózati adapter tulajdonságainak definiálásához használhatók:<br /><br /> <ul><li>**OSDAdapter0EnableDHCP** – az adapterhez Dynamic Host Configuration Protocol (DHCP) engedélyezéséhez.<br />    Ez a beállítás kötelező. Lehetséges értékek a következők:  IGAZ vagy hamis.</li><li>**OSDAdapter0IPAddressList** -tartalmazó, vesszővel elválasztott IP-címek listája az adapterhez. Ha az **EnableDHCP** értéke nem **false**(hamis), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.<br />    Ez a beállítás kötelező.</li><li>**OSDAdapter0SubnetMask** – az alhálózati maszkok vesszővel tagolt listája. Ha az **EnableDHCP** értéke nem **false**(hamis), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.<br />    Ez a beállítás kötelező.</li><li>**OSDAdapter0Gateways** -IP-átjárócímek vesszővel tagolt listája. Ha az **EnableDHCP** értéke nem **false**(hamis), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.<br />    Ez a beállítás kötelező.</li><li>**OSDAdapter0DNSDomain** – Az adapterhez tartozó DNS-tartomány.</li><li>**OSDAdapter0DNSServerList** – az adapterhez tartozó DNS-kiszolgálók vesszővel tagolt listája.<br />    Ez a beállítás kötelező.</li><li>**OSDAdapter0EnableDNSRegistration** - **igaz** regisztrálja az adapter IP-címét a DNS-ben.</li><li>**OSDAdapter0EnableFullDNSRegistration** - **igaz** regisztrálja az adapter IP-címét a DNS-ben alatt a számítógép teljes DNS-nevét.</li><li>**OSDAdapter0EnableIPProtocolFiltering** - **true** IP protokoll szűrése az adapteren.</li><li>**OSDAdapter0IPProtocolFilterList** -IP-futtatása engedélyezett protokollok vesszővel tagolt listája. Ha az **EnableIPProtocolFiltering** változó értéke **false**(hamis), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.</li><li>**OSDAdapter0EnableTCPFiltering** - **true** TCP-port szűrése az adapter engedélyezéséhez.</li><li>**OSDAdapter0TCPFilterPortList** -portok a TCP hozzáférési engedélyt a vesszővel tagolt listája. Ha az **EnableTCPFiltering** változó értéke **false**(hamis), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.</li><li>**OSDAdapter0TcpipNetbiosOptions** -beállítások a NetBIOS TCP/IP felett. A lehetséges értékek a következők:<br /><br /> <ul><li>0 A DHCP-kiszolgálótól kapott NetBIOS-beállítások használata.</li><li>1 NetBIOS engedélyezése TCP/IP felett.</li><li>2 NetBIOS tiltása TCP/IP felett.</li></ul></li><li>**OSDAdapter0EnableWINS** - **igaz** névfeloldás a WINS használatára.</li><li>**OSDAdapter0WINSServerList** -WINS-kiszolgáló IP-címeket vesszővel tagolt listája. Ha az **EnableWINS** értéke nem **true**(igaz), a rendszer figyelmen kívül hagyja ezt a tulajdonságot.</li><li>**OSDAdapter0MacAddress** -vezérlő (MAC) címe felel meg a fizikai hálózati adapter beállításainak használatával.</li><li>**OSDAdapter0Name** - neve, mert a hálózati kapcsolat jelenik meg a hálózati kapcsolatok vezérlő panel programban. A név 0–255 karakter hosszúságú lehet.</li><li>**OSDAdapter0Index** -beállítások a tömbben a hálózati adapter beállításainak indexe.<br /><br />     OSDAdapterCount = 1<br />    OSDAdapter0EnableDHCP = FALSE<br />    OSDAdapter0IPAddressList = 192.168.0.40<br />    OSDAdapter0SubnetMask = 255.255.255.0<br />    OSDAdapter0Gateways = 192.168.0.1<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (bemenet)|A célszámítógépen telepített hálózati adapterek számát adja meg. Ha az **OSDAdapterCount** értéke be van állítva, akkor az egyes adapterek összes beállítását meg kell adni. Ha például egy adapter esetében megadja az **OSDAdapterTCPIPNetbiosOptions** értékét, úgy az adapterhez tartozó többi értéket is be kell állítania.<br /><br /> <br /><br /> Ha ez az érték nincs megadva, a rendszer az összes **OSDAdapter** értéket figyelmen kívül hagyja.|  
|OSDDNSDomain<br /><br /> (bemenet)|A célszámítógép által használt elsődleges DNS-kiszolgálót adja meg.|  
|OSDDomainName<br /><br /> (bemenet)|Annak a Windows-tartománynak a nevét adja meg, amelyhez a célszámítógép csatlakozik. A megadott értéknek az Active Directory tartományi szolgáltatások érvényes tartománynevének kell lennie.|  
|OSDDomainOUName<br /><br /> (bemenet)|Annak a szervezeti egységnek (OU) az RFC 1779 formátumú nevét adja meg, amelyhez a célszámítógép csatlakozik. Az érték megadása esetén annak a teljes elérési utat tartalmaznia kell.<br /><br /> Például:<br /><br /> **LDAP://OU=SajátSzervezetiEgység,DC=SajátTartomány,DC=SajátVállalat,DC=hu**|  
|OSDEnableTCPIPFiltering<br /><br /> (bemenet)|Meghatározza, hogy a TCP/IP-szűrés engedélyezve van-e.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDJoinAccount<br /><br /> (bemenet)|Azt a hálózati fiókot határozza meg, melynek használatával a rendszer a célszámítógépet a Windows-tartományhoz adja.|  
|OSDJoinPassword<br /><br /> (bemenet)|Azt a hálózati jelszót határozza meg, melynek használatával a rendszer a célszámítógépet a Windows-tartományhoz adja.|  
|OSDNetworkJoinType<br /><br /> (bemenet)|Meghatározza, hogy a célszámítógép Windows-tartományhoz vagy munkacsoporthoz csatlakozik.<br /><br /> A**"0"** érték azt jelzi, hogy a célszámítógép Windows-tartományhoz csatlakozik. Az**"1"** érték azt jelzi, hogy a számítógép egy munkacsoporthoz csatlakozik.<br /><br /> Érvényes értékek:<br /><br /> **"0"**<br /><br /> **"1"**|  
|OSDDNSSuffixSearchOrder<br /><br /> (bemenet)|Meghatározza a DNS-keresési sorrendet a célszámítógépen.|  
|OSDWorkgroupName<br /><br /> (bemenet)|Annak a munkacsoportnak a nevét adja meg, amelyhez a célszámítógép csatlakozik.<br /><br /> Vagy ezt az értéket, vagy az **OSDDomainName** változó értékét meg kell adnia. A munkacsoport neve legfeljebb 32 karakter hosszúságú lehet.<br /><br /> Például:<br /><br /> **"Könyvelés"**|  

###  <a name="BKMK_ApplyOperatingSystem"></a> Az Operációs rendszer lemezképének alkalmazása feladatütemezési művelet változói  
 A művelet változói a célszámítógépen telepíteni kívánt operációs rendszer beállításait határozzák meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [operációs rendszer lemezképének alkalmazása](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (bemenet)|Megadja az operációs rendszer központi telepítési csomagjához társított operációsrendszer-telepítési válaszfájl nevét.|  
|OSDImageIndex<br /><br /> (bemenet)|A célszámítógépen alkalmazott WIM-fájl lemezképindex-értékét adja meg.|  
|OSDInstallEditionIndex<br /><br /> (bemenet)|A telepített Windows Vista vagy újabb operációs rendszer verziószámát adja meg. Ha nincs megadva verziószám, a Windows telepítő a hivatkozott termékkulcs alapján állapítja meg a telepítendő verziót.<br /><br /> Ha a következő feltételek igazak, kizárólag nullát (0) adjon meg értékként:<br /><br /> -Telepíti egy Vista előtti Windows operációs rendszer<br />-Telepíti a Windows Vista vagy újabb mennyiségi licences kiadásra, és nem termékkulcsot.<br /><br /> Érvényes értékek:<br /><br /> **"0"** (alapértelmezett)|  
|OSDTargetSystemDrive (kimenet)|Az operációs rendszer fájljait tartalmazó partíció meghajtóbetűjelét adja meg.|  

###  <a name="BKMK_ApplyWindowsSettings"></a> A Windows-beállítások alkalmazása feladatütemezési művelet változói  
 A művelet változói a célszámítógép olyan Windows-beállításait adják meg, mint a számítógép neve, a Windows termékkulcs, a regisztrált felhasználó és szervezet, valamit a helyi rendszergazda jelszava. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [Windows beállítások alkalmazása](task-sequence-steps.md#BKMK_ApplyWindowsSettings).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (bemenet)|Megadja a célszámítógép nevét.<br /><br /> Például:<br /><br /> **"%_SMSTSMachineName%"** (alapértelmezett)|  
|OSDProductKey<br /><br /> (bemenet)|Megadja a Windows termékkulcsot. A megadott érték 1–255 karakterből állhat.|  
|OSDRegisteredUserName<br /><br /> (bemenet)|A regisztrált felhasználók alapértelmezett nevét határozza meg az új operációs rendszerben. A megadott érték 1–255 karakterből állhat.|  
|OSDRegisteredOrgName<br /><br /> (bemenet)|A regisztrált szervezetek alapértelmezett nevét határozza meg az új operációs rendszerben. A megadott érték 1–255 karakterből állhat.|  
|OSDTimeZone<br /><br /> (bemenet)|Az új operációs rendszerben használt alapértelmezett időzóna-beállítást határozza meg.|  
|OSDServerLicenseMode<br /><br /> (bemenet)|Megadja, hogy a Windows Server milyen licencelési módot használ.<br /><br /> Érvényes értékek:<br /><br /> **"PerSeat"**<br /><br /> **"PerServer"**|  
|OSDServerLicenseConnectionLimit<br /><br /> (bemenet)|Az engedélyezett kapcsolatok maximális számát adja meg. A megadott számnak az 5 és 9999 közötti tartományba kell esnie.|  
|OSDRandomAdminPassword<br /><br /> (bemenet)|Véletlenszerűen létrehozott jelszót ad meg az új operációs rendszer rendszergazdai fiókjához. Ha beállítása **igaz**, a helyi rendszergazdai fiók le lesz tiltva a célszámítógépen. Ha beállítása **hamis**, a helyi rendszergazdai fiók engedélyezve lesz a cél számítógépen, és a helyi rendszergazdai fiók jelszavát kap a változó értékének **OSDLocalAdminPassword**.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  
|OSDLocalAdminPassword<br /><br /> (bemenet)|Megadja a helyi rendszergazdai jelszót. A rendszer figyelmen kívül hagyja ezt az értéket, ha a **Véletlenszerűen generálja a helyi rendszergazda jelszavát, és a tiltsa le a fiókot az összes támogatott platformon** beállítás engedélyezett. A megadott érték 1–255 karakterből állhat.|  

###  <a name="BKMK_AutoApplyDrivers"></a> Az Illesztőprogramok automatikus alkalmazása feladatütemezési művelet változói  
 A művelet változói megadják, hogy a célszámítógépen mely Windows-illesztőprogramok lesznek telepítve, valamint hogy engedélyezett-e az aláírás nélküli illesztőprogramok telepítés. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [illesztőprogramok automatikus alkalmazása](task-sequence-steps.md#BKMK_AutoApplyDrivers).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (bemenet)|Az illesztőprogram-katalógus kategóriáinak egyedi azonosítóit tartalmazó, vesszővel elválasztott lista. Ha meg van adva érték, az **Illesztőprogram automatikus alkalmazása** feladatütemezési művelet csak akkor veszi figyelembe az illesztőprogramokat az illesztőprogramok telepítése során, ha azok e kategóriák közül legalább egyben szerepelnek. Az értéket nem kötelező megadni, és alapértelmezés szerint nincs beállítva. A rendelkezésre álló kategóriaazonosítók a helyhez tartozó **SMS_CategoryInstance** objektumok listájáról érhetők el|  
|OSDAllowUnsignedDriver<br /><br /> (bemenet)|Megadja, hogy a Windows konfigurációja lehetővé teszi-e az aláírás nélküli illesztőprogramok telepítését. Ez a feladatütemezési változó a Windows Vista és későbbi operációs rendszerek központi telepítésekor nem használatos.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (bemenet)|Megadja, hogy mit tegyen a feladatütemezés, ha az illesztőprogram-katalógusban a hardvereszközzel kompatibilis több illesztőprogram is szerepel. Ha beállítása **"true"**, csak a legjobb eszközillesztőt telepíti.  Ha **hamis**, az összes kompatibilis eszközillesztő telepítve lesz, és az operációs rendszer választja ki a legjobb illesztőprogramot.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  

###  <a name="BKMK_CaptureNetworkSettings"></a> A Hálózati beállítások rögzítése feladatütemezési művelet változói  
 A művelet változói azt adják meg, hogy a rendszer rögzíti-e a hálózati adapter beállításainak (TCP/IP, DNS és WINS) konfigurációs adatait, valamint hogy a munkacsoport- vagy tartománytagság adatai is át lesznek-e telepíve az operációs rendszer központi telepítésének részeként. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [hálózati beállítások rögzítése](task-sequence-steps.md#BKMK_CaptureNetworkSettings).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (bemenet)|Megadja, hogy a hálózati adapter beállításait (TCP/IP, DNS és WINS) rögzíti-e a rendszer.<br /><br /> Példák:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  
|OSDMigrateNetworkMembership<br /><br /> (bemenet)|Megadja, hogy a munkacsoport- vagy tartománytagság adatai át lesznek-e telepítve az operációs rendszer központi telepítésének részeként.<br /><br /> Példák:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  

###  <a name="BKMK_CaptureOperatingSystemImage"></a> Az Operációs rendszer lemezképének rögzítése feladatütemezési művelet változói  
 A művelet változói az operációs rendszer rögzített lemezképéről tartalmaznak adatokat, például, hogy a rendszer hol tárolja a lemezképet, ki hozta létre a lemezképet, illetve tartalmazzák a lemezkép leírását. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [operációs rendszer lemezképének rögzítése](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDCaptureAccount<br /><br /> (bemenet)|Annak a Windows-fióknak a nevét adja meg, amely jogosult a rögzített lemezképet hálózati megosztáson tárolni.|  
|OSDCaptureAccountPassword<br /><br /> (bemenet)|A rögzített lemezkép hálózati megosztáson való tárolásához használt Windows-fiók jelszavát adja meg.|  
|OSDCaptureDestination<br /><br /> (bemenet)|A rögzített operációsrendszer-lemezkép mentésének helyét adja meg. A könyvtárnév legfeljebb 255 karakterből állhat.|  
|OSDImageCreator<br /><br /> (bemenet)|A lemezképet létrehozó felhasználó nem kötelezően megadandó neve. A nevet a rendszer egy WIM-fájlban tárolja. A felhasználónév hossza legfeljebb 255 karakter lehet.|  
|OSDImageDescription<br /><br /> (bemenet)|Az operációsrendszer-lemezkép felhasználó által definiált, nem kötelezően megadandó leírása. A leírást a rendszer egy WIM-fájlban tárolja. A leírás hossza legfeljebb 255 karakter lehet.|  
|OSDImageVersion<br /><br /> (bemenet)|A rögzített operációsrendszer-lemezképhez hozzárendelendő, felhasználó által definiált verziószám, melyet nem kötelező megadni. Ezt a verziószámot a rendszer egy a WIM-fájlban tárolja. Az érték egy legfeljebb 32 karakterből álló, tetszőleges betűkombináció lehet.|  
|OSDTargetSystemRoot<br /><br /> (bemenet)|A referencia-számítógépen telepített operációs rendszer Windows-könyvtárának elérési útvonalát határozza meg. Ez az operációs rendszer ellenőrzötten rögzítésre alkalmas támogatott operációs rendszer által a Configuration Manager.|  

###  <a name="BKMK_CaptureUserState"></a> A Felhasználói állapot rögzítése feladatütemezési művelet változói  
 A művelet változói a Felhasználóáttelepítő (USMT) által használt adatokat (például a mappát, amelybe a rendszer menti a felhasználói állapotot, a Felhasználóáttelepítővel használható parancssori kapcsolókat és a felhasználói profilok rögzítését vezérlő konfigurációs fájlokat) adják meg.  További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [felhasználói állapot rögzítése](task-sequence-steps.md#BKMK_CaptureUserState).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (bemenet)|A felhasználói állapot mentéséhez használt mappa UNC vagy helyi elérési útja. Nincs alapértelmezett érték.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (bemenet)|Adja meg a felhasználói állapot áttelepítési Tool (USMT) eszköz parancssori kapcsolók, amelyek a felhasználói állapot rögzítéséhez használt azonban nem lesz közzétéve a Configuration Manager felhasználói felületén. A kapcsolók az automatikusan létrehozott USMT-parancssorhoz fűzött karakterláncként vannak megadva.<br /><br /> <br /><br /> Azon USMT-kapcsolók pontosságát, amelyek ezzel a feladatütemezési változóval lettek megadva, a rendszer nem ellenőrzi a feladatütemezés futtatása előtt.|  
|OSDMigrateMode<br /><br /> (bemenet)|Lehetővé teszi az USMT által rögzített fájlok testreszabását. Ha ez a változó értéke "Simple", akkor a csak az USMT szokásos konfigurációs fájljait használja. Ha ez a változó értéke "Advanced", a feladatütemezési változó az OSDMigrateConfigFiles adja meg a konfigurációs fájlokat az USMT által.<br /><br /> Érvényes értékek:<br /><br /> **"Simple"**<br /><br /> **"Advanced"**|  
|OSDMigrateConfigFiles<br /><br /> (bemenet)|A felhasználói profilok rögzítését vezérlő konfigurációs fájlokat adja meg. A változó akkor használatos, csak ha az OSDMigrateMode értéke "Advanced". Ezzel a vesszővel elválasztott listaértékkel a felhasználói profilok áttelepítése szabható testre.<br /><br /> Például: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (bemenet)|Engedélyezi a felhasználói állapot rögzítését akkor, ha egyes fájlok nem rögzíthetők.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (bemenet)|Engedélyezi a részletes naplózást az USMT számára.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (bemenet)|Meghatározza, hogy a rendszer rögzíti-e a titkosított fájlokat<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|_OSDMigrateUsmtPackageID<br /><br /> (bemenet)|Az USMT fájljait tartalmazó Configuration Manager-csomagot a csomag Azonosítóját adja meg. A változó megadása kötelező.|  

###  <a name="BKMK_CaptureWindowsSettings"></a> A Windows-beállítások rögzítése feladatütemezési művelet változói  
 A művelet változói azt határozzák meg, hogy bizonyos Windows-beállítások (például a számítógépnév, regisztrált szervezetnév és az időzóna-információk) át lesznek-e telepítve a célszámítógépre. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [Windows beállítások rögzítése](task-sequence-steps.md#BKMK_CaptureWindowsSettings).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (bemenet)|Megadja, hogy a számítógépnév át lesz-e telepítve.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**<br /><br /> Ha értéke "true", majd az osdcomputername értéke a számítógép NetBIOS-nevét.|  
|OSDComputerName<br /><br /> (kimenet)|A változó értéke a számítógép NetBIOS-neve. A beállítás értéke csak akkor, ha az OSDMigrateComputerName változó értéke "true"értékre.|  
|OSDMigrateRegistrationInfo<br /><br /> (bemenet)|Megadja, hogy a számítógép felhasználói és szervezeti adatai át lesznek-e telepítve.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**<br /><br /> Ha értéke "true", majd az osdregisteredorgname értéke a számítógép regisztrált szervezeti neve.|  
|OSDRegisteredOrgName<br /><br /> (kimenet)|A változó értéke a számítógép regisztrált szervezetneve. A beállítás értéke csak akkor, ha az OSDMigrateRegistrationInfo változó értéke "true"értékre.|  
|OSDMigrateTimeZone<br /><br /> (bemenet)|Megadja, hogy a számítógép időzóna-beállításai át lesznek-e telepítve.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**<br /><br /> Ha értéke "true", akkor a változó OSDTimeZone értéke a számítógép időzónája.|  
|OSDTimeZone<br /><br /> (kimenet)|A változó értéke a számítógép időzónája. A beállítás értéke csak akkor, ha az OSDMigrateTimeZone változó értéke "true"értékre.|  

###  <a name="BKMK_ConnecttoNetworkFolder"></a> A Csatlakozás hálózati mappához feladatütemezési művelet változói  
 A művelet változói egy hálózati mappáról adnak meg információkat, például a hálózati mappához való csatlakozáshoz használt fiókot és jelszót, a mappa meghajtónak betűjelét és a mappa elérési útját. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [csatlakoztassa a hálózati mappába](task-sequence-steps.md#BKMK_ConnectToNetworkFolder).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (bemenet)|A hálózati megosztáshoz való csatlakozáshoz használt rendszergazdai fiókot adja meg.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (bemenet)|Annak a hálózati meghajtónak a betűjelét adja meg, amelyhez csatlakozni kell. Az értéket nem kötelező megadni. Ha nincs megadva, a hálózati kapcsolatot a rendszer nem rendeli hozzá meghajtóbetűjelhez. Ha megadja az értéket, annak a D: és Z: közötti tartományban kell lennie.  Ne használja továbbá az X: betűjelet, ugyanis a Windows PE ezt a meghajtóbetűjelet használja a Windows PE-fázis során.<br /><br /> Példák:<br /><br /> **"D:"**<br /><br /> **"E:"**|  
|SMSConnectNetworkFolderPassword<br /><br /> (bemenet)|Megadja a hálózati megosztáshoz való csatlakozáshoz használt jelszót.|  
|SMSConnectNetworkFolderPath<br /><br /> (bemenet)|Megadja a kapcsolat hálózati elérési útját.<br /><br /> Például:<br /><br /> **"\\\servername\sharename"**|  

###  <a name="BKMK_ConvertDisk"></a> A Lemez konvertálása dinamikus lemezzé feladatütemezés műveleti változói  
 A művelet változója az alaplemez típusúról dinamikus lemezzé konvertálandó fizikai lemez számát adja meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [lemez konvertálása dinamikus lemezzé](task-sequence-steps.md#BKMK_ConvertDisktoDynamic).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDConvertDiskIndex<br /><br /> (bemenet)|Megadja a konvertálandó fizikai lemez számát.|  

###  <a name="BKMK_EnableBitLocker"></a> A BitLocker engedélyezése feladatütemezési művelet változói  
 A művelet változói a BitLocker célszámítógépen való engedélyezéséhez használt helyreállítási jelszót és indítókulcsot adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [BitLocker engedélyezése](task-sequence-steps.md#BKMK_EnableBitLocker).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (bemenet)|Véletlenszerű helyreállítási jelszó generálása helyett a **BitLocker engedélyezése** feladatütemezési művelet a megadott értéket használja helyreállítási jelszóként. Az értéknek egy érvényes numerikus BitLocker helyreállítási jelszónak kell lennie.|  
|OSDBitLockerStartupKey<br /><br /> (bemenet)|A kulcskezelési beállításhoz egy véletlenszerű indítókulcsot generálna generálása helyett **indítókulcs csak USB-n** a **BitLocker engedélyezése** feladatütemezési művelet a platformmegbízhatósági modul (TPM) használja indítókulcsként. Az értéknek érvényes, 256 bites Base64-kódolású BitLocker indítókulcsnak kell lennie.|  

###  <a name="BKMK_FormatPartitionDisk"></a> A Lemez formázása és particionálása feladatütemezési művelet változói  
 A művelet változói a fizikai lemezek formázására és particionálására vonatkozó adatokat határozzák meg, például a lemez számát és a partícióbeállítások tömbjét. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [lemez formázása és particionálása](task-sequence-steps.md#BKMK_FormatandPartitionDisk).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (bemenet)|Megadja a particionálandó fizikai lemez számát.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (bemenet)|Megadja, hogy letiltandó-e a gyorsítótár igazításának optimalizálása a merevlemez particionálásakor az egyes BIOS-típusokkal való kompatibilitás érdekében. Erre a Windows XP vagy Windows Server 2003 operációs rendszerek központi telepítésekor lehet szükség. További információkért tekintse meg a [931760-es számú](http://go.microsoft.com/fwlink/?LinkId=134081) és [931761-es számú](http://go.microsoft.com/fwlink/?LinkId=134082) cikket a Microsoft tudásbázisában.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDGPTBootDisk<br /><br /> (bemenet)|Megadja, hogy a GPT merevlemezeken létre kell-e hozni EFI-partíciót annak érdekében, hogy azok rendszerindító lemezként legyenek használhatók az EFI-alapú számítógépekben.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDPartitions<br /><br /> (bemenet)|A partícióbeállítások egy tömbjét adja meg. A feladatütemezési környezet tömbváltozóinak eléréséről az SDK témakörben olvashat bővebben.<br /><br /> Ez a feladatütemezési változó egy tömbváltozó. A tömb egyes elemei a merevlemez egyes partícióinak beállításait jelölik. Az egyes partíciókhoz definiált beállítások a tömbváltozó nevének, a nulla alapú lemezpartíció-számnak és a tulajdonságnévnek a kombinálásával érhetők el.<br /><br /> A következő változónevek például a feladatütemezési művelet által a merevlemezen elsőként létrehozott partíció tulajdonságainak definiálásához használhatók:<br /><br /> - **OSDPartitions0Type** -meghatározza a partíció típusát. Ezt a tulajdonságot kötelező megadni. Érvényes értékek: "**Primary**" (elsődleges), "**Extended**" (kiterjesztett), "**Logical**" (logikai) és "**Hidden**" (rejtett).<br />-   **OSDPartitions0FileSystem** – Megadja a partíció formázásakor használandó fájlrendszer típusát. Ezt a tulajdonságot nem kötelező megadni. Ha nincs megadva fájlrendszer, a partíció nem lesz formázva. Érvényes értékek: "**FAT32**" és "**NTFS**".<br />-   **OSDPartitions0Bootable** – Meghatározza, hogy a partíció alkalmas-e rendszerindításra. Ezt a tulajdonságot kötelező megadni. MBR-lemezek esetében, ha ez az érték "**TRUE**" (igaz), ez a partíció lesz az aktív partíció.<br />-   **OSDPartitions0QuickFormat** – A formázás típusát adja meg. Ezt a tulajdonságot kötelező megadni. Ha a beállított érték "**TRUE**" (igaz), a rendszer gyorsformázást végezni. Egyéb esetben teljes formázás lesz végrehajtva.<br />-   **OSDPartitions0VolumeName** – Megadja a formázás során a kötethez hozzárendelt nevet. Ezt a tulajdonságot nem kötelező megadni.<br />-   **OSDPartitions0Size** – Meghatározza a partíció méretét. A mértékegységet az **OSDPartitions0SizeUnits** változó határozza meg. Ezt a tulajdonságot nem kötelező megadni. Ha a tulajdonsághoz nincs megadva érték, a partíció az összes rendelkezésre álló szabad területet felhasználásával jön létre.<br />-   **OSDPartitions0SizeUnits** – Meghatározza az **OSDPartitions0Size** feladatütemezési változót értelmezésekor használt mértékegységet. Ezt a tulajdonságot nem kötelező megadni. Érvényes értékek: "**MB**" (alapértelmezett), "**GB**" és "**Percent**" (százalék).<br />-   **OSDPartitions0VolumeLetterVariable** – Windows PE rendszerben a partíciókhoz létrehozáskor mindig a következő szabad meghajtóbetűjel lesz hozzárendelve. Ezzel a nem kötelező tulajdonsággal megadható egy másik feladatütemezési változó neve, mely az új meghajtóbetűjelet későbbi használat céljából menti.<br /><br /> <br /><br /> Ha a feladatütemezési művelet több partíciót fog definiálni, a második partíció tulajdonságainak definiálásához a partíció indexét kell használni a változók nevében. Például: **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, **OSDPartitions1VolumeName** stb.|  
|OSDPartitionStyle<br /><br /> (bemenet)|Megadja a lemez particionálásának módját. Az "**MBR**" érték a fő rendszerindító rekord típusú particionálási módot, a "**GPT**" pedig a GUID partíciós tábla típusú particionálási módot adja meg.<br /><br /> Érvényes értékek:<br /><br /> **"GPT"**<br /><br /> **"MBR"**|  

###  <a name="BKMK_InstallSoftwareUpdates"></a> A Szoftverfrissítések telepítése feladatütemezési művelet változói  
 A művelet változója megadja, hogy az összes frissítés telepítendő-e, vagy csak a kötelező frissítések telepítendőek. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [szoftverfrissítések telepítése](task-sequence-steps.md#BKMK_InstallSoftwareUpdates).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve<br /><br /> (bemenet)|Leírás|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (bemenet)|Megadja, hogy mely frissítések telepítendők: az összes frissítés, vagy csak a kötelezők.<br /><br /> Érvényes értékek:<br /><br /> **"All" (összes) (összes)**<br /><br /> **"Mandatory" (kötelező) (kötelező)**|  

###  <a name="BKMK_JoinDomainWorkgroup"></a> A Csatlakozás tartományhoz vagy munkacsoporthoz feladatütemezési művelet változói  
 A művelet változói a célszámítógép Windows-tartományhoz vagy munkacsoporthoz való csatlakoztatásához szükséges információkat adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [csatlakozás tartományhoz vagy munkacsoporthoz](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (bemenet)|Azt a fiókot adja meg, melynek használatával a célszámítógép a Windows-tartományhoz csatlakozik. Tartományhoz való csatlakozáskor a változó értékét kötelező megadni.|  
|OSDJoinDomainName<br /><br /> (bemenet)|Annak a Windows-tartománynak a nevét adja meg, amelyhez a célszámítógép csatlakozik. A Windows-tartomány neve 1–255 karakter hosszúságú lehet.|  
|OSDJoinDomainOUName<br /><br /> (bemenet)|Annak a szervezeti egységnek (OU) az RFC 1779 formátumú nevét adja meg, amelyhez a célszámítógép csatlakozik. Az érték megadása esetén annak a teljes elérési utat tartalmaznia kell. A Windows-tartomány szervezeti egységének neve 0–32 767 karakter hosszúságú lehet. Ezt az értéket nem kell megadni, ha a **OSDJoinType** változó értéke "1" (csatlakozás munkacsoporthoz).<br /><br /> Például:<br /><br /> **LDAP://OU=SajátSzervezetiEgység,DC=SajátTartomány,DC=SajátVállalat,DC=hu**|  
|OSDJoinPassword<br /><br /> (bemenet)|Azt a hálózati jelszót határozza meg, melynek használatával a célszámítógép a Windows-tartományhoz csatlakozik. Ha a változó értéke nincs megadva, a rendszer jelszó megadása nélkül próbál csatlakozni. Az értéket kötelező megadni, ha a **OSDJoinType** változó értéke "**0**" (csatlakozás tartományhoz).|  
|OSDJoinSkipReboot<br /><br /> (bemenet)|Megadja, hogy elmaradjon-e az újraindítás, miután a célszámítógép csatlakozott a tartományhoz vagy munkacsoporthoz.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"**|  
|OSDJoinType<br /><br /> (bemenet)|Meghatározza, hogy a célszámítógép Windows-tartományhoz vagy munkacsoporthoz csatlakozik. Ha a célszámítógépet Windows-tartományhoz kívánja hozzáadni, a "**0**" értéket kell megadni. Ha a célszámítógépet munkacsoporthoz kívánja hozzáadni, az "**1**" értéket kell megadni.<br /><br /> Érvényes értékek:<br /><br /> **"0"**<br /><br /> **"1"**|  
|OSDJoinWorkgroupName<br /><br /> (bemenet)|Annak a munkacsoportnak a nevét adja meg, amelyhez a célszámítógép csatlakozik. A munkacsoport neve 1–32 karakter hosszúságú lehet.<br /><br /> Például:<br /><br /> **"Könyvelés"**|  

###  <a name="BKMK_PrepareWindowsCapture"></a> A Windows előkészítése a rögzítéshez feladatütemezési művelet változói  
 A művelet változói a Windows operációs rendszer célszámítógépről való rögzítéséhez használt információkat adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [ConfigMgr-ügyfél előkészítése a rögzítéshez](task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (bemenet)|Meghatározza, hogy a sysprep eszköz összeállítsa-e a háttértár-illesztőprogramok listáját. Ez a beállítás csak a Windows XP és Windows Server 2003 operációs rendszerekre vonatkozik. A művelet a sysprep.inf fájl [SysprepMassStorage] szakaszát feltölti a rögzítendő lemezkép által támogatott háttértár-illesztőprogramok adataival.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDKeepActivation<br /><br /> (bemenet)|Meghatározza, hogy a sysprep eszköz alaphelyzetbe állítja-e a termékaktiválási jelzőt.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDTargetSystemRoot<br /><br /> (kimenet)|A referencia-számítógépen telepített operációs rendszer Windows-könyvtárának elérési útvonalát határozza meg. Ez az operációs rendszer ellenőrzötten rögzítésre alkalmas támogatott operációs rendszer által a Configuration Manager.|  

###  <a name="BKMK_ReleaseStateStore"></a> Az Állapot tárolásának felszabadítása ütemezési művelet változói  
 A művelet változói a tárolt felhasználói állapot feloldásához használt információkat adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [állapot tárolásának felszabadítása](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (bemenet)|Annak a helynek a UNC vagy helyi elérési útvonala, amelyről a rendszer visszaállítja a felhasználói állapot. Ezt az értéket a **Felhasználói állapot rögzítése** feladatütemezési művelet és a **Felhasználói állapot visszaállítása** feladatütemezési művelet is használja.|  

###  <a name="BKMK_RequestState"></a> Az Állapot tárolásának igénylése feladatütemezési művelet változói  
 A művelet változói a tárolt felhasználói állapot lekéréséhez szükséges információkat (például az állapotáttelepítési ponton a felhasználói adatok tároló mappát) adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [állapot tárolásának felszabadítása](../../osd/understand/task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (bemenet)|Meghatározza, hogy használható-e a hálózatelérési fiókot alternatívaként, ha a számítógépfiók nem tud csatlakozni az állapotáttelepítési ponthoz.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDStateSMPRetryCount<br /><br /> (bemenet)|Megadja, hogy a feladatütemezési lépés hányszor próbál meg megtalálni egy állapotáttelepítési pontot, mielőtt hibát jelentene. A megadott számnak 0 és 600 közötti értéknek kell lennie.|  
|OSDStateSMPRetryTime<br /><br /> (bemenet)|Meghatározza, hogy a feladatütemezési lépés hány másodpercig várjon az újrapróbálkozások között. A megadott érték legfeljebb 30 másodperc lehet.|  
|OSDStateStorePath<br /><br /> (kimenet)|Az állapotáttelepítési ponton a felhasználói állapotot tároló mappa UNC elérési útja.|  

###  <a name="BKMK_RestartComputer"></a> A Számítógép újraindítása feladatütemezési művelet változói  
 A művelet változói a célszámítógép újraindításához használt információkat adják meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [számítógép újraindítása](task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (bemenet)|A célszámítógép újraindítása előtt a felhasználóknak megjelenített üzenet szövegét adja meg. Ha a változó nincs megadva, az alapértelmezett üzenet jelenik meg. A megadott üzenet legfeljebb 512 karakterből állhat.<br /><br /> Például:<br /><br /> – "A számítógép újraindul; Mentse a munkáját."|  
|SMSRebootTimeout<br /><br /> (bemenet)|Megadja, hogy a rendszer hány másodpercig jeleníti meg a figyelmeztetést, mielőtt a számítógép újraindul. Nulla másodperc beállítása esetén nem jelenik meg újraindítási üzenet.<br /><br /> Példák:<br /><br /> **"0"** (alapértelmezett)<br /><br /> **"5"**<br /><br /> **"10"**|  

###  <a name="BKMK_RestoreUserState"></a> A Felhasználói állapot visszaállítása feladatütemezési művelet változói  
 A művelet változói a célszámítógép felhasználói állapotának visszaállításához használt információkat adják meg, például a felhasználói állapot visszaállításához használt forrásmappa elérési útját, illetve meghatározzák hogy a helyi számítógépfiók is vissza legyen-e állítva. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [felhasználói állapot visszaállítása](task-sequence-steps.md#BKMK_RestoreUserState).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (bemenet)|Annak a mappának az UNC vagy helyi elérési útvonala, amelyről a rendszer visszaállítja a felhasználói állapot.|  
|OSDMigrateContinueOnRestore<br /><br /> (bemenet)|Megadja, hogy a rendszer folytatja-e a felhasználói állapot visszaállítását akkor is, ha egyes fájlok nem állíthatók vissza.<br /><br /> Érvényes értékek:<br /><br /> **"true"** (alapértelmezett)<br /><br /> **"false"**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (bemenet)|Engedélyezi a részletes naplózást az USMT eszköz számára. Ez az érték szükséges a művelet futtatásához. Megadható értékek: "true" (igaz) vagy "false" (hamis).<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDMigrateLocalAccounts<br /><br /> (bemenet)|Megadja, hogy a rendszer visszaállítja-e a helyi számítógépfiókot.<br /><br /> Érvényes értékek:<br /><br /> **"true"**<br /><br /> **"false"** (alapértelmezett)|  
|OSDMigrateLocalAccountPassword<br /><br /> (bemenet)|Ha a **OSDMigrateLocalAccounts** változó értéke "true," a változónak tartalmaznia kell az áttelepített összes helyi fiókokhoz rendelt jelszót. Ugyanazt a jelszót az összes áttelepített helyi fiókhoz van rendelve, mert ez egy ideiglenes jelszót később a Configuration Manager operációs rendszer központi telepítésének eltérő módon módosítani tekintendő.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (bemenet)|A Felhasználóáttelepítő (USMT) további, a felhasználói állapot visszaállításakor használatos parancssori kapcsolóit adja meg. A kapcsolók az automatikusan létrehozott USMT-parancssorhoz fűzött karakterláncként vannak megadva. Azon USMT-kapcsolók pontosságát, amelyek ezzel a feladatütemezési változóval lettek megadva, a rendszer nem ellenőrzi a feladatütemezés futtatása előtt.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (bemenet)|Az USMT fájljait tartalmazó Configuration Manager-csomagot a csomag Azonosítóját adja meg. A változó megadása kötelező.|  

###  <a name="BKMK_RunCommand"></a> Az Parancssor futtatása feladatütemezési művelet változói  
 A művelet változói a parancsok parancssorból való futtatásához használt információkat adják meg, például azt a munkakönyvtárat, amelyben a parancs fut. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [parancssor futtatása](task-sequence-steps.md#BKMK_RunCommandLine).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve|Leírás|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (bemenet)|64 bites operációs rendszerek esetén a parancssorban alapértelmezés szerint a WOW64 fájlrendszer-átirányító keresi meg és futtatja a programokat azért, hogy az operációs rendszer programjainak és DLL-jeinek 32 bites verziói kerüljenek használatra. Ha e változónak a "true" letiltja a WOW64 fájlrendszer-átirányító használatát, így megtalálhatók az operációs rendszer programjainak és DLL-ek natív 64 bites verziói. A változónak 32 bites operációs rendszerek használatakor nincs hatása.|  
|WorkingDirectory<br /><br /> (bemenet)|A parancssori művelet kezdőkönyvtárát adja meg. A megadott könyvtárnév legfeljebb 255 karakterből állhat.<br /><br /> Példák:<br /><br /> -   **"C:\\"**<br />-   **"% SystemRoot %"**|  
|SMSTSRunCommandLineUserName<br /><br /> (bemenet)|A parancssort futtató fiókot adja meg. A váltózó értéke egy „felhasználónév” vagy „tartomány\felhasználónév” formátumú karakterlánc.|  
|SMSTSRunCommandLinePassword<br /><br /> (bemenet)|Megadja az SMSTSRunCommandLineUserName változó által megadott fiók jelszavát.|  

### <a name="set-dynamic-variables"></a>Dinamikus változók megadása  
 A rendszer a Dinamikus változók beállítása feladatütemezési lépés hozzáadásakor automatikusan beállítja a művelet változóit. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [dinamikus változók beállítása](task-sequence-steps.md#BKMK_SetDynamicVariables).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve<br /><br /> (bemenet)|Leírás|  
|----------------------------------------|-----------------|  
|_SMSTSMake|A számítógép gyártmányát adja meg.|  
|_SMSTSModel|A számítógép modelljét adja meg.|  
|_SMSTSMacAddresses|A számítógép által használt MAC-címeket adja meg.|  
|_SMSTSIPAddresses|A számítógép által használt IP-címeket adja meg.|  
|_SMSTSSerialNumber|A számítógép sorozatszámát adja meg.|  
|_SMSTSAssetTag|A számítógép eszközcímkéjét adja meg.|  
|_SMSTSUUID|A számítógép UUID azonosítóját adja meg.|  
|_SMSTSDefaultGateways|A számítógép által használt alapértelmezett átjárókat adja meg.|  

###  <a name="BKMK_SetupWindows"></a> A Windows és ConfigMgr beállítása feladatütemezési művelet változói  
 Ez a művelet változója megadja a Configuration Manager-ügyfél telepítésekor használt ügyfél-telepítési tulajdonságokat. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [Windows és ConfigMgr beállítása](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve<br /><br /> (bemenet)|Leírás|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (bemenet)|Meghatározza, hogy a Configuration Manager-ügyfél telepítésekor használt ügyfél-telepítési tulajdonságokat.|  

### <a name="upgrade-operating-system"></a>Operációs rendszer verziófrissítésének elvégzése  
 Ez a művelet változója további parancssori kapcsolókat, amelyek nem érhető el a Configuration Manager konzol telepítő adódnak hozzá a Windows 10-frissítés történő határozza meg. További információ a a változókhoz kapcsolódó feladatütemezési lépésről: [operációs rendszer verziófrissítésének elvégzése](task-sequence-steps.md#BKMK_UpgradeOS).  

#### <a name="details"></a>Részletek  

|Műveleti változó neve<br /><br /> (bemenet)|Leírás|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (bemenet)|Megadja azokat a parancssori kapcsolókat, melyek a Windows 10 operációs rendszerre való frissítés során lettek a telepítőhöz hozzáadva. A parancssori kapcsolókat a rendszer nem ellenőrzi. Ezért mindig ellenőrizze, hogy a kapcsoló pontosan lett-e megadva.<br /><br /> További információ: [Windows Setup Command-Line Options](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx)(A Windows telepítő parancssori kapcsolói).|  

