---
title: "Ügyfél-telepítési tulajdonságok |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságokat."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
caps.latest.revision: 15
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 11737bf2ff35dc9b04ec1d9690c0983ddd0c286a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-installation-properties-in-system-center-configuration-manager"></a>Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager CCMSetup.exe parancs segítségével manuálisan telepíti a Configuration Manager-ügyfelet.  

##  <a name="aboutCCMSetup"></a> A CCMSetup.exe áttekintése  
 A CCMSetup.exe parancsot a felügyeleti pontot vagy egy forrás helyéről az ügyfél telepítéséhez szükséges fájlokat tölti le. Ilyen fájlok lehetnek:  

-   A Windows Installer-csomag az ügyfélszoftver telepítéséhez szükséges Client.msi.  

-   A Microsoft háttérben futó intelligens átviteli szolgáltatás (BITS) telepítőfájljai.  

-   A Windows Installer telepítőfájljai.  

-   Frissítések és javítások a Configuration Manager-ügyfél.  

> [!NOTE]  
>  A Configuration Managerben, akkor a Client.msi fájl közvetlenül nem futtatható.  

 CCMSetup.exe biztosít [parancssori tulajdonságok](#ccmsetup-exe-command-line-properties) a telepítés testreszabásához. Adja meg a tulajdonságokat a CCMSetup.exe parancssori a Client.msi működése módosítható is.  

> [!IMPORTANT]  
>  Adja meg a CCMSetup tulajdonságait Client.msi tulajdonságainak megadása előtt.  

 A CCMSetup.exe és a hozzá kapcsolódó fájlok a Configuration Manager helykiszolgálón találhatók a **ügyfél** a Configuration Manager telepítési mappa. A hálózaton: megosztott mappa  **&lt;Helykiszolgálónév\>\SMS_&lt;Helykód\>\Client**.  

 A CCMSetup.exe parancssori formátuma a következő:  

 `CCMSetup.exe [&lt;Ccmsetup properties\>] [&lt;client.msi setup properties>]`  

 Például:  

 "CCMSetup.exe smsmp01 / Logon SMSSITECODE = S01 FSP = SMSFSP01"  

 Ebben a példában a következőket teszi:  

-   Adja meg a terjesztési pontot az Ügyféltelepítő fájlok letöltéséhez egy listát kér smsmp01 felügyeleti pont.  

-   Meghatározza, hogy a telepítés álljon le, ha az ügyfél verziója már megtalálható a számítógépen.  

-   Arra utasítja a client.msi csomagot, hogy az S01 helykódhoz rendelje hozzá az ügyfelet.  

-   Az SMSFP01 tartalék állapotkezelő pont használatára utasítja a client.msi csomagot.  

> [!NOTE]  
>  Ha egy tulajdonság szóközöket tartalmaz, helyezze idézőjelek közé.  


> [!IMPORTANT]  
>  Ha ki van bővítve az Active Directory-sémát a Configuration Manager, számos ügyfél-telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban közzétett, és a Configuration Manager-ügyfél automatikusan olvasni. Az Active Directory tartományi szolgáltatásokban közzétett ügyféltelepítési tulajdonságok listáját lásd: [Információ az Active Directory tartományi szolgáltatásokban közzétett ügyfélszoftver-telepítési tulajdonságokról a System Center Configuration Managerben](about-client-installation-properties-published-to-active-directory-domain-services.md)  

##  <a name="ccmsetupexe-command-line-properties"></a>A CCMSetup.exe parancssori tulajdonságai  

### <a name=""></a>/?  

A **CCMSetup** párbeszédpanel megnyitása, amelyen a ccmsetup.exe parancssori tulajdonságai szerepelnek.  

Például: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/ source:&lt;elérési útja\>  

 A fájl letöltési helyét adja meg. Egy helyi vagy UNC elérési utat használja. A server message block (SMB) protokoll a fájlok letöltése.  Használandó **/source**, az ügyfél telepítéséhez a Windows felhasználói fiók olvasási engedéllyel a hely kell rendelkeznie.

> [!NOTE]  
>  Használhatja a **/source** tulajdonságot többszöri az alternatív letöltési helyét adja meg egy parancssort.  

 Például: **ccmsetup.exe /source:"\\\computer\folder"**  

### <a name="mpltcomputer"></a>/mp:&lt;számítógép\>

 Számítógépek kapcsolódjanak, így a legközelebbi terjesztési pontot talál a telepítési fájlok egy forrás felügyeleti pontot adja meg. Ha nincsenek terjesztési pontok, vagy a számítógépek 4 óra elteltével sem képesek letölteni a fájlokat a terjesztési pontokról, az ügyfelek a megadott felügyeleti pontról töltik le a fájlokat.  

> [!IMPORTANT]  
>  Ez a tulajdonság használatával adja meg a letöltési forrás található számítógépek kezdeti felügyeleti pontot, és bármely helyen bármely felügyeleti pontja lehet. Nem létezik *hozzárendelése* az ügyfél egy felügyeleti pontra.   

 A számítógépek a helyrendszerszerepkör ügyfélkapcsolatokra vonatkozó konfigurációjától függően HTTP- vagy HTTPS-kapcsolaton keresztül töltik le a fájlokat. A letöltés BITS sávszélesség-szabályozást, használja, ha konfigurálva. Ha a terjesztési pontok és a felügyeleti pontok csak HTTPS-ügyfélkapcsolatokat lettek konfigurálva, győződjön meg arról, hogy az ügyfélszámítógépnek van-e egy érvényes ügyféltanúsítványt.  

Az **/mp** parancssori tulajdonsággal több felügyeleti pontot is meghatározhat arra az esetre, ha a számítógép az elsőhöz nem képes csatlakozni – ebben az esetben a következőkkel próbálkozik, a megadott sorrendben. Ha több felügyeleti pont megadása esetén pontosvesszővel az értékeket.

Ha az ügyfél csatlakozik egy felügyeleti pont HTTPS-en keresztül általában, meg kell adnia a teljes tartománynév, a nem a számítógép neve. Az értéket meg kell egyeznie a felügyeleti pont PKI-tanúsítvány tulajdonosának vagy a tulajdonos alternatív neve. Bár a Configuration Manager támogatja a számítógépnév használatával a tanúsítvány az intranetes kapcsolatok esetén ajánlott biztonsági eljárásként, ajánlott teljes Tartománynevet.

Példa a számítógépnév használatára:`ccmsetup.exe /mp:SMSMP01`  

Példa a teljes tartománynév:`ccmsetup.exe /mp:smsmp01.contoso.com`  

### <a name="retryltminutes"></a>/ újra:&lt;perc\>

Az újrapróbálkozási időköz, ha a CCMSetup.exe a telepítési fájlok letöltési meghiúsul.  CCMSetup addig próbálkozik, amíg eléri a megadott határértéket a **downloadtimeout** tulajdonság.  

Például: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

Megakadályozza a CCMSetup szolgáltatásként, ez az alapértelmezett futtatását. Ha a CCMSetup szolgáltatásként fut, a számítógép, amely esetleg nincs elegendő jogosultsága ahhoz, hogy a telepítéshez szükséges hálózati erőforrásokhoz férnek hozzá a helyi rendszerfiók környezetében futtatja. A **/noservice**, a telepítés elindításához használt felhasználói fiók kontextusában fut. CCMSetup.exe. Is, ha egy parancsfájl segítségével futtassa a CCMSetup.exe a **/service** tulajdonság, a CCMSetup.exe kilép, miután a szolgáltatás elindul, és előfordulhat, hogy nem jelenti a telepítés részleteit megfelelően.   

Például: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

Megadja, hogy a CCMSetup a helyi rendszerfiókot használó szolgáltatásként fusson.  

Például: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

Meghatározza, hogy az ügyfélszoftvert el kell távolítani. További információkért lásd: [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../manage/manage-clients.md).  

Például: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

Meghatározza, hogy az ügyfél telepítése álljon le, ha az ügyfél bármelyik verziója már telepítve van.  

Például: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 Meghatározza, hogy a CCMSetup kényszerítse az ügyfélszámítógép újraindítása, ha a telepítés befejezéséhez szükséges. Ha nincs megadva, a CCMSetup kilép, amikor újraindítás szükséges, és a Folytatás a következő manuális újraindítás után.  

 Például: `CCMSetup.exe /forcereboot`  

### <a name="bitspriorityltpriority"></a>/ BITSPriority:&lt;prioritása\>

 Meghatározza a letöltési prioritást, amikor az ügyféltelepítő fájlok letöltése HTTP-kapcsolaton keresztül történik. A lehetséges értékek a következők:  

-   FOREGROUND (Előtérben)  

-   HIGH (Magas)  

-   NORMAL (Normál)  

-   LOW (Alacsony)  

 Az alapértelmezett érték a NORMAL (Normál).  

 Például: `ccmsetup.exe /BITSPriority:HIGH`  

### <a name="downloadtimeoutltminutes"></a>/ downloadtimeout:&lt;perc\>

Idő (percben), amely a CCMSetup próbál meg letölteni a telepítési fájlokat, mielőtt leállna hosszát. Az alapértelmezett érték **1440** perc (1 nap).  

Például: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

 Adja meg, amikor az ügyfél, amely tartalmazza az ügyfél-hitelesítéshez, PKI-tanúsítványt használ, ha elérhető. Ha nem talál érvényes tanúsítványt, az ügyfél használja a HTTP-kapcsolat és önaláírt tanúsítványt, amely esetén is a viselkedés nem használja ezt a tulajdonságot.

> [!NOTE]  
>  Bizonyos esetekben nem kell megadnia ezt a tulajdonságot, amikor egy ügyfél telepítése, és továbbra is használhatják az ügyféltanúsítványt. Ilyen például egy ügyfél telepítése ügyfélleküldés, és a szoftverfrissítési pont ügyfelének telepítése. Meg kell azonban adnia a tulajdonságot minden olyan esetben, amikor az ügyfelet manuális módszerrel telepíti, és az **/mp** tulajdonsággal csak HTTPS-kapcsolatok fogadására konfigurált felügyeleti pontot határoz meg. Akkor is meg kell adnia a tulajdonságot, amikor csak internetes kommunikációra telepít ügyfelet a CCMALWAYSINF=1 tulajdonság használatával (az internetalapú felügyeleti pont tulajdonságaival és a helykóddal együtt). Az internetalapú ügyfélfelügyeletről további információt a [Végpontok közötti kommunikáció a System Center Configuration Managerben](../../plan-design/hierarchy/communications-between-endpoints.md) témakör [Az internetről vagy nem megbízható erdőből kapcsolódó ügyfelekkel folytatott kommunikáció esetén megfontolandó szempontok](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) című szakaszában talál.  

 Például: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 Meghatározza, hogy az ügyfelet nem kell ellenőrizze a visszavont tanúsítványok listáját (CRL), ha a PKI-tanúsítványt a HTTPS-KAPCSOLATON keresztül kommunikál.  

 Ha nincs megadva, az ügyfél ellenőrzi a tanúsítvány-visszavonási listát, mielőtt HTTPS-kapcsolatot létesít.  

 További információt a CRL ügyfelek általi ellenőrzéséről a [Biztonsági tervezés a System Center Configuration Managerben](../../plan-design/security/plan-for-security.md) témakör [A PKI-tanúsítványok visszavonásának tervezése](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs) című szakaszában talál.  

 Például: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>/ config:&lt;konfigurációs fájl\>

Az ügyfél telepítési tulajdonságait tartalmazó szövegfájl nevének meghatározására szolgál.

- Ha nem adja meg a **/noservice** CCMSetup-tulajdonságot, ezt a fájlt kell lennie a CCMSetup mappájában, amely a % Windir %\\Ccmsetup 32 bites és 64 bites operációs rendszerek.
- Ha a **/noservice** tulajdonság is meg van adva, a fájlnak abban a mappában kell lennie, amelyből a CCMSetup.exe fájlt is futtatja.  

Például: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

Használja a a &lt;Configuration Manager-könyvtár\>\\bin\\&lt;platform\> mappát a helykiszolgáló számítógépen fájl helyes formátumának megadásához. Ez a fájl is a részek és azok felhasználásáról megjegyzéseket tartalmaz. Adja meg az ügyfél-telepítési tulajdonságokat a [Client Install] szakaszban a következő karakterlánc után: **Telepítse = INSTALL = ALL**.  

Példa a [Client Install] szakasz bejegyzésére:`Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/ skipprereq:&lt;fájlnév\>

 Meghatározza, hogy a CCMSetup.exe nem telepítheti a megadott Előfeltételek programot a Configuration Manager-ügyfél telepítésekor. A tulajdonsághoz több érték is megadható. Az egyes értékeket pontosvesszővel (;) válassza el egymástól.  


 Példák: `CCMSetup.exe /skipprereq:silverlight.exe` vagy`CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;Silverlight.exe`  

### <a name="forceinstall"></a>/forceinstall

 Adja meg, hogy minden meglévő ügyfélprogramot el lesz távolítva, és egy új ügyfél lesz telepítve.  

### <a name="excludefeaturesltfeature"></a>/ ExcludeFeatures:&lt;szolgáltatás\>

Meghatározza, hogy a CCMSetup.exe nem telepítheti a megadott szolgáltatás, az ügyfél telepítésekor.  

Példa: `CCMSetup.exe /ExcludeFeatures:ClientUI` a Szoftverközpont nem telepíti az ügyfélen.  

> [!NOTE]  
>  A jelen kiadásban kizárólag a **ClientUI** érték használható az **/ExcludeFeatures** tulajdonsággal.  

##  <a name="ccmsetupReturnCodes"></a> A CCMSetup.exe visszatérési kódjai  
 A CCMSetup.exe parancs biztosítja, hogy a következő visszatérési kódok befejeződött. A hibaelhárításhoz tekintse át a ccmsetup.log fájlt az ügyfélszámítógépen környezet és a visszatérési kódok további részleteit.  

|Visszatérési kód|Jelentés|  
|-----------------|-------------|  
|0|Siker|  
|6|Hiba|  
|7|Újraindítás szükséges|  
|8|A telepítő már fut|  
|9|Előfeltétel-kiértékelési hiba|  
|10|Hiba a telepítő jegyzékfájl-kivonatának érvényesítésekor|  

##  <a name="clientMsiProps"></a> Client.msi-tulajdonságok  
 A következő tulajdonságok módosíthatják a client.msi telepítési viselkedését. Ügyfélleküldéses telepítés esetén ezeket a tulajdonságokat az **Ügyfélleküldéses telepítés tulajdonságai** párbeszédpanel **Ügyfél** lapján is megadhatja.  

### <a name="ccmadmins"></a>CCMADMINS  

Egy vagy több olyan Windows felhasználói fiókot és csoportot ad meg, amelyeknek ügyfélbeállításokhoz és -házirendekhez való hozzáférést kell adni. Ez akkor hasznos, ahol a Configuration Manager rendszergazda nem rendelkezik helyi rendszergazdai hitelesítő adatokkal az ügyfélszámítógépen. Adjon meg egy pontosvesszővel elválasztott listája.  

Például: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

Megadja, hogy a számítógép engedélyezve van-e ügyféltelepítés után indítsa újra, ha szükséges.  

> [!IMPORTANT]  
>  A számítógép újraindul figyelmeztetés nélkül, akkor is, ha van bejelentkezett felhasználó.  

Például: **CCMSetup.exe CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 1-es érték megadásával meghatározhatja, hogy az ügyfél mindig internetalapú legyen, és soha ne csatlakozzon az intranethez. Az ügyfél kapcsolattípusaként **Mindig internet**jelenik meg.  

 A CCMHOSTNAME tulajdonsággal együtt használandó, amely az internetalapú felügyeleti pont teljes tartománynevének meghatározására szolgál. Emellett a /UsePKICert CCMSetup-tulajdonságot is tüntesse fel, a helykóddal együtt.  

 Az internetalapú ügyfélfelügyeletről további információt a [Végpontok közötti kommunikáció a System Center Configuration Managerben](../../plan-design/hierarchy/communications-between-endpoints.md) témakör [Az internetről vagy nem megbízható erdőből kapcsolódó ügyfelekkel folytatott kommunikáció esetén megfontolandó szempontok](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) című szakaszában talál.  

 Például: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Adja meg a tanúsítványkibocsátók listájának, amely megbízható legfelső szintű hitelesítésszolgáltató (CA) tanúsítványok, amelyek a Configuration Manager-hely Megbízhatóságok listáját.  

 További információt a tanúsítványkibocsátók listájáról, illetve arról, hogy az ügyfelek miként használják a listát a tanúsítványkiválasztási folyamat során, a [Biztonsági tervezés a System Center Configuration Managerben](../../plan-design/security/plan-for-security.md) témakör [A PKI-ügyféltanúsítvány kiválasztásának tervezése](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection) című szakaszában talál.  

 A tulajdonság a legfelső szintű hitelesítésszolgáltatói tanúsítványban szereplő tulajdonosi attribútumokkal egyeztet, a kis- és nagybetűk figyelembevételével. Az attribútumok vesszővel (,) vagy pontosvesszővel (;) választhatók el egymástól. Függőleges elválasztó karakterrel több legfelső szintű hitelesítésszolgáltatói tanúsítvány is megadható. Például:  

 `CCMCERTISSUERS=”CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US &#124; CN=Litware Corporate Root CA; O=Litware, Inc.”`  

> [!TIP]  
>  Hivatkozzon a mobileclient.tcf fájlra a &lt;Configuration Manager-könyvtár\>\bin\\&lt;platform\> mappájába másolja a helykiszolgáló számítógépén a **CertificateIssuers =&lt;karakterlánc\>**  , amely a hely van konfigurálva.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 Adja meg a tanúsítvány kiválasztási feltételeinek, ha az ügyfél HTTPS-kommunikációhoz (egy érvényes tanúsítvány, amely tartalmazza az ügyfél-hitelesítési képesség) egynél több tanúsítvány rendelkezik.  

 Pontos egyezéssel kereshet (használata **tulajdonos:**) illetve részleges egyezéssel (használata **SubjectStr:)** a tulajdonos neve vagy a tulajdonos alternatív neve. Példák:  

 `CCMCERTSEL="Subject:computer1.contoso.com"`a számítógép: "szamitogep1.contoso.com" a tulajdonos neve vagy a tulajdonos alternatív neve pontosan egyező olyan tanúsítványt keres.  

 `CCMCERTSEL="SubjectStr:contoso.com"`olyan tanúsítványt, amely tartalmazza a "contoso.com" a tulajdonos neve vagy a tulajdonos alternatív neve keres.  

 A Tulajdonos neve és a Tulajdonos alternatív neve attribútumaként emellett objektumazonosítót (OID) vagy megkülönböztető nevet is használhat, például a következő módon:  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"`szervezetiegység-attribútumot keres objektumazonosítóként kifejezett, és a számítógépek neve.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"`szervezetiegység-attribútumot keres megkülönböztető névként kifejezett, és a számítógépek neve.  

> [!IMPORTANT]  
>  Ha a tulajdonos neve mező használata a **tulajdonos:** a kis-és nagybetűket, és a **SubjectStr:** nagybetűk között.  
>   
>  Ha a tulajdonos alternatív neve mező használata a **tulajdonos:**és a **SubjectStr:** nem különböztetik meg.  

 A tanúsítványkiválasztáshoz használható attribútumok teljes listáját [A PKI-tanúsítvány kiválasztási feltételeinek támogatott attribútumértékei](#BKMK_attributevalues)tartalmazza.  

 Ha egynél több tanúsítvány felel meg a keresésnek, és a CCMFIRSTCERT tulajdonság értéke 1, a leghosszabb érvényességi idejű tanúsítvány van kiválasztva.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 Adja meg egy alternatív tanúsítványtároló-nevet, ha a HTTPS ügyfél-tanúsítványa nem található az alapértelmezett tanúsítványtárolóban található **személyes** számítógép tárolójában.  

 Például: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  Engedélyezi a hibakeresési naplózást. Értékek állítható be (ki, alapértelmezett) 0 vagy 1 (be). Ennek hatására a hibaelhárítási információkat naplózhat az ügyfél. Érdemes elkerülni e tulajdonság használatát éles üzemben működő helyeken, mert a naplózási tevékenység túlzott mértékű lehet, ami megnehezítheti a lényeges információk megtalálását a naplófájlokban. CCMENABLELOGGING is meg kell hibakeresési naplózás engedélyezéséhez.  

  Például: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  Alapértelmezés szerint a naplózás engedélyezéséhez igaz értékre kell beállítani. A napló fájljai a **naplók** mappa a Configuration Manager-ügyfél telepítési mappájában. Alapértelmezés szerint ez a %Windir%\CCM\Logs mappa.  

  Például: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 A gyakoriság, mely ügyfélen az ügyfélállapot értékelésére szolgáló eszköz (ccmeval.exe) futtatja. Lehet **1** való **1440** perc. Alapértelmezés szerint naponta egyszer futtatja.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 Az órát, amikor az ügyfélállapot értékelésére szolgáló eszköz (ccmeval.exe) futtatja, közötti **0** (éjfél) és **23** (23 óra). Alapértelmezés szerint éjfélkor futtatja.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 Ha a tulajdonság értéke 1, az ügyfélnek a leghosszabb érvényességi idővel rendelkező PKI-tanúsítványt kell kiválasztania. Erre a beállításra IPsec-kényszerítéses hálózatvédelem használata esetén lehet szükség.  

 Például: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  

### <a name="ccmhostname"></a>CCMHOSTNAME

 Az internetalapú felügyeleti pont teljes tartománynevét adja meg, ha az ügyfél felügyelete interneten keresztül megoldott.  

 Ezt a lehetőséget ne a következő telepítési tulajdonságával adja meg: SMSSITECODE=AUTO. Az internetalapú ügyfeleket közvetlenül a saját internetalapú helyükhöz kell hozzárendelni.  

 Például: `CCMSetup.exe  /UsePKICert/ CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

### <a name="ccmhttpport"></a>CCMHTTPPORT

 Azt a portot adja meg, amelyet az ügyfélnek használnia kell, ha HTTP protokollon keresztül kommunikál a helyrendszer-kiszolgálókkal. Alapértelmezés szerint a 80-as beállítva.  

 Például: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

Azt a portot adja meg, amelyet az ügyfélnek használnia kell, ha HTTPS protokollon keresztül kommunikál a helyrendszer-kiszolgálókkal. Alapértelmezés szerint a 443-as Port beállítva.  

Például: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 A mappát, ahol a Configuration Manager-ügyfélfájlok telepítési, azonosító *% Windir %*\CCM alapértelmezés szerint. Ezeket a fájlokat telepíti, függetlenül a Ccmcore.dll fájl is mindig telepíti a *%Windir%\System32* mappát. Emellett a 64 bites operációs rendszerek esetében a Ccmcore.dll fájl egy példányát is mindig telepíti a *% Windir %*\SysWOW64 mappába a Configuration Manager-ügyfél API-k a Configuration Manager szoftverfejlesztői készlet (SDK) a 32 bites verzióját használó 32 bites alkalmazások támogatásához.  

 Például: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Adja meg a Configuration Manager naplófájljainak írni a részletességi szintje. Adjon meg egy egész számot 0 3, ahol a 0 a legrészletesebb naplózást és a 3 pedig kizárólag a hibanaplózást. Az alapértelmezett érték az 1.  

Például: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

A Configuration Manager-naplófájl eléri a 250 000 bájtos méretet (vagy a CCMLOGMAXSIZE tulajdonság által megadott értéket), amikor a rendszer biztonsági másolatként átnevezi, és egy új naplófájl keletkezik.  

Ez a tulajdonság meghatározza, hogy a naplófájl korábbi változataiból hányat őrizzen meg a rendszer. Az alapértelmezett érték az 1. Ha a beállított érték a 0, a rendszer nem őrzi meg a régi naplófájlokat.  

Például: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

A naplófájl maximális fájlméret bájtban. Ha a naplófájl eléri a meghatározott méretet, a rendszer előzményfájlként nevezi át, és új fájlt hoz létre. Ezt a tulajdonságot legalább 10 000 bájtra kell állítani. Az alapértelmezett érték 250 000 bájt.  

Például: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 Ha állítsa igaz értéke esetén letiltja az ügyfélszámítógépen rendszergazdai hitelesítő adatokkal rendelkező végfelhasználók módosítása a Configuration Manager rendelt hely **Configuration Manager** az ügyfél a Vezérlőpulton.  

 Például: **CCMSetup.exe DISABLESITEOPT = TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

Ha értékre van állítva értéke igaz, a rendszergazdai hitelesítő adatokkal rendelkező végfelhasználók lehetőségét, módosíthatja az ügyfél az ügyfélszámítógépen a Configuration Manager-ügyfél ügyfélgyorsítótár-mappájának beállításait az ügyfélszámítógép Vezérlőpultján található Configuration Manager használatával.  

Például: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 DNS tartományt határoz meg az ügyfelek számára a DNS-ben közzétett felügyeleti pontok megtalálásához. Ha az ügyfél megtalálja a felügyeleti pontot, az tájékoztatja a hierarchiában található többi felügyeleti pontról. Ilyen módon a DNS-közzététel révén megtalált felügyeleti pontnak nem kell az ügyfél helyén lennie, a hierarchia bármely felügyeleti pontja lehet.  

> [!NOTE]  
>  Nem kell megadni ezt a tulajdonságot, ha az ügyfél ugyanabban a tartományban található, mint a közzétett felügyeleti pont. Ebben az esetben az ügyfél tartományában automatikusan használt DNS-keresésre a felügyeleti pontokhoz.  

 További információ a DNS-közzétételről mint a szolgáltatás helyének meghatározására szolgáló módszerről a Configuration Manager-ügyfelek: [szolgáltatás helyét, és hogyan meg az ügyfelek a hozzájuk rendelt felügyeleti pontról](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) a [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) .  

> [!NOTE]  
>  Alapértelmezés szerint a DNS-közzététel nincs engedélyezve a Configuration Manager alkalmazásban.  

 Például: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Adja meg a tartalék állapotkezelő pont fogadó és feldolgozó Configuration Manager-ügyfélszámítógépek által küldött állapotüzenetek.  

A tartalék állapotkezelő pontra vonatkozó további információkért lásd: [határozza meg, ha a tartalék állapotkezelő pont szükséges](/sccm/core/clients/deploy/plan#determine-if-you-need-a-fallback-status-point).  

Például: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 Meghatározza, hogy a Microsoft Application Virtualization (App-V) szükséges minimális verziójának meglétét nem ellenőrzi, az ügyfél telepítése előtt.  

> [!IMPORTANT]  
>  Ha a Configuration Manager-ügyfél App-V telepítése nélkül telepíti, nem telepíthet virtuális alkalmazások.  

 Például: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

Meghatározza, hogy az ügyfélállapot fog jelentést, de nem oldja meg az ügyfél a talált problémákat.  

Például: `CCMSetup.exe NOTIFYONLY=TRUE`  

További információkért lásd: [Az ügyfélállapot konfigurálása a System Center Configuration Managerben](configure-client-status.md).  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 Ha a Configuration Manager-ügyfél a megfelelő Configuration Manager megbízható legfelső szintű kulcsot, és nem tud kapcsolatba lépni egy megbízható felügyeleti ponttal, annak megkapják az új megbízható legfelső szintű kulcsot, manuálisan kell eltávolítani a régi megbízható legfelső szintű kulcsot e tulajdonság használatával. Ez a helyzet akkor fordulhat elő, ha az ügyfelet egyik helyhierarchiából egy másikra áthelyezése. Ez a tulajdonság HTTP és HTTPS ügyfél-kommunikációt használó ügyfelek esetében érvényes.  

 Például: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

Lehetővé teszi, hogy automatikus hely újbóli hozzárendelése ügyfélfrissítés használata esetén a [SMSSITECODE](#smssitecode)= AUTO.

Például: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

Az ideiglenes fájlok tárolására szolgáló ügyfélgyorsítótár-mappa helyét adja meg az ügyfélszámítógépen. Az alapértelmezett hely a *%Windir \ccmcache*mappa.  

Például: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

Ez a tulajdonság a SMSCACHEFLAGS tulajdonsággal együtt használható az ügyfélgyorsítótár-mappa helyének szabályozására.  

Példa: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE` telepíti az ügyfélgyorsítótár mappája a legnagyobb rendelkezésre álló ügyfélkezelési meghajtón.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

További telepítési adatokat ad meg az ügyfélgyorsítótár mappájához. A SMSCACHEFLAGS tulajdonságok külön-külön és pontosvesszővel elválasztva, kombinálva is használhatók. Ha ez a tulajdonság nincs meghatározva, a rendszer az ügyfélgyorsítótár mappáját a SMSCACHEDIR tulajdonság szerint telepíti, nem tömöríti, és a SMSCACHESIZE értéket használja a mappa MB-ban megadott méreteként.  

Ezt a beállítást meglévő ügyfél frissítése esetén figyelmen kívül hagyja a rendszer.  

Tulajdonságok:  

-   PERCENTDISKSPACE: A mappa méretét adja meg a teljes lemezterület százalékában. E tulajdonság meghatározásakor mindig meg kell adni a SMSCACHESIZE tulajdonság használandó százalékos értékét.  

-   PERCENTFREEDISKSPACE: A mappa méretét a szabad lemezterület százalékos adja meg. E tulajdonság meghatározásakor mindig meg kell adni a SMSCACHESIZE tulajdonság használandó százalékos értékét. Ha például a lemezen 10 MB-nyi szabad terület van, a SMSCACHESIZE értéke pedig 50, a mappa mérete 5 MB-ra van állítva. Ez a tulajdonság nem használható a PERCENTDISKSPACE tulajdonsággal.  

-   MAXDRIVE: Meghatározza, hogy a mappát a legnagyobb kapacitású lemezre kell telepíteni. Az értéket a rendszer figyelmen kívül hagyja, ha a SMSCACHEDIR tulajdonsággal elérési út van megadva.  

-   MAXDRIVESPACE: Meghatározza, hogy a mappát a legnagyobb szabad hellyel rendelkező lemezmeghajtóra kell telepíteni. Az értéket a rendszer figyelmen kívül hagyja, ha a SMSCACHEDIR tulajdonsággal elérési út van megadva.  

-   NTFSONLY: Meghatározza, hogy a mappát csak NTFS-meghajtón lemez kell telepíteni. Az értéket a rendszer figyelmen kívül hagyja, ha a SMSCACHEDIR tulajdonsággal elérési út van megadva.  

-   COMPRESS: Meghatározza, hogy a mappa stöd tömörített formátumban kell lennie.  

-   FAILIFNOSPACE: Meghatározza, hogy az ügyfélszoftvert el kell távolítani, ha nincs elegendő hely a mappa telepítéséhez.  

Például: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE:

> [!IMPORTANT]
> A Configuration Manager verziója 1606 kezdve új ügyfélbeállítások használhatók annak az ügyfél gyorsítótára. Ezen ügyfélbeállítások alkalmazásával lecserélhető az SMSCACHESIZE használata client.msi tulajdonságként az ügyfél-gyorsítótár méretének meghatározásához. További információért lásd a [gyorsítótár méretének ügyfélbeállításaival](about-client-settings.md#client-cache-settings) foglalkozó részt.  

Az 1602-es és korábbi kiadásokban az SMSCACHESIZE megabájtban (MB), illetve a PERCENTDISKSPACE vagy a PERCENTFREEDISKSPACE tulajdonság használata esetén százalékban adja meg az ügyfélgyorsítótár-mappa méretét. Ha ez a tulajdonság nincs beállítva, a mappa mérete alapértelmezés szerint a legnagyobb érték, 5120 MB. A legkisebb megadható érték 1 MB.  

> [!NOTE]  
>  Ha egy letöltendő új csomag miatt a mappa mérete meghaladná a maximális méretet, és a mappa nem törölhető elegendő hely felszabadítása érdekében, a csomag letöltése sikertelen, és a program vagy az alkalmazás nem futtatható.  

Ezt a beállítást meglévő ügyfél frissítése esetén, illetve ha az ügyfél szoftverfrissítéseket tölt le, figyelmen kívül hagyja a rendszer.  

Például: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  Ügyfél újratelepítése esetén nem használható a SMSCACHESIZE vagy a SMSCACHEFLAGS telepítési tulajdonság ahhoz, hogy a gyorsítótár mérete kisebb legyen, mint korábban volt. Ha ehhez, az értéket a rendszer figyelmen kívül hagyja, és a gyorsítótár mérete automatikusan értéke azt korábban méretét.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Megadja a helyét és a Configuration Manager telepítője leellenőriz a konfigurációs beállítások sorrendjében. A tulajdonság egy vagy több karaktert tartalmazó karakterlánc, amelyek mindegyike egyedi konfigurációs forrást határoz meg. Használja az R, a P, a M és az U karakterértékeket önmagukban vagy kombinációként:  

-   R: Ellenőrizze a konfigurációs beállítások keresése a beállításjegyzékben.  

   További információkért lásd: [információ az ügyfél-telepítési tulajdonságok tárolásához a beállításjegyzékben.](https://technet.microsoft.com/library/gg712298.aspx#BKMK_Provision).  

-   P: Ellenőrizze a konfigurációs beállítások keresése a parancssorban megadott telepítési tulajdonságokban.  

-   M: Meglévő beállításokat ellenőrzi egy régebbi ügyfél a Configuration Manager ügyfélszoftver frissítésekor.  

-   U: Egy újabb verzióra frissíti a telepített ügyfelet (és a hozzárendelt helykódot használja).  

 Alapértelmezés szerint az ügyféltelepítés `PU` kódot használ először a telepítési tulajdonságok, majd a meglévő beállítások ellenőrzéséhez.  

 Például: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 Azt adja meg, hogy az ügyfél használhatja-e a Windows Internet Name Service (WINS) szolgáltatást HTTP-kapcsolatot fogadó felügyeleti pont megtalálásához. Ez a módszer akkor használható, ha nem található felügyeleti pont az Active Directory tartományi szolgáltatásokban vagy a DNS-ben.  

 Ez a tulajdonság nincs hatással arra, hogy az ügyfél WINS szolgáltatást használ a névfeloldáshoz.  

 A tulajdonság esetében kétféle mód konfigurálható:  

-   NOWINS: Ez a tulajdonság legbiztonságosabb beállítása, és megakadályozza, hogy az ügyfelek felügyeleti pontot találjanak a WINS-ben.  Ha ezt a beállítást használja, az ügyfeleknek alternatív módot kell biztosítani ahhoz, hogy felügyeleti pontot találjanak az intraneten keresztül, például Active Directory tartományi szolgáltatások vagy DNS-közzététel révén.  

-   WINSSECURE (alapértelmezett): Ebben a módban a HTTP-kommunikációt használó ügyfél a WINS használatával is találjon meg felügyeleti pontot. Az ügyfél azonban csak a megbízható legfelső szintű kulcs példányának birtokában tud sikeresen csatlakozni a felügyeleti ponthoz. További információt a [Biztonsági tervezés a System Center Configuration Managerben](../../plan-design/security/plan-for-security.md) témakör [A megbízható legfelső szintű kulcs tervezése](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) című szakaszában talál.  


 Például: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Adja meg a Configuration Manager-ügyfél használata a kezdeti felügyeleti pontot.  

> [!IMPORTANT]  
>  Ha a felügyeleti pont csak HTTPS-KAPCSOLATON keresztül fogadja az ügyfélkapcsolatokat, https://, a felügyeleti pont elé kell írni.  

Példa:`CCMSetup.exe SMSMP=smsmp01.contoso.com`  

Például: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

Például: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  

### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Megadja a Configuration Manager megbízható legfelső szintű kulcsot, ha a nem sikerült beolvasni az Active Directory tartományi szolgáltatásokból. Ez a tulajdonság HTTP és HTTPS ügyfél-kommunikációt használó ügyfelek esetében érvényes. További információt a [Biztonsági tervezés a System Center Configuration Managerben](../../plan-design/security/plan-for-security.md) témakör [A megbízható legfelső szintű kulcs tervezése](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) című szakaszában talál.  

 Például: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 A Configuration Manager megbízható legfelső szintű kulcsának újratelepítésére szolgál. A megbízható legfelső szintű kulcsot tartalmazó fájl teljes elérési útját és fájlnevét adja meg. Ez a tulajdonság HTTP és HTTPS ügyfél-kommunikációt használó ügyfelek esetében érvényes. További információt a [Biztonsági tervezés a System Center Configuration Managerben](../../plan-design/security/plan-for-security.md) témakör [A megbízható legfelső szintű kulcs tervezése](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) című szakaszában talál.  

 Például: "CCMSetup.exe SMSROOTKEYPATH =&lt;teljes elérési út és fájlnév\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 Megadja az exportált önaláírt tanúsítvány teljes elérési útját és a tanúsítványhoz tartozó .cer fájlnevet a helykiszolgálón.  

 Ezt a tanúsítványt az **SMS** tanúsítványtároló tárolja, a tulajdonos neve **Helykiszolgáló** , a rövid név: **Helykiszolgáló aláíró tanúsítványa**.  

 Például: **CCMSetup.exe/UsePKICert SMSSIGNCERT =&lt;teljes elérési útja és neve\>**  

### <a name="smssitecode"></a>SMSSITECODE

 Adja meg a Configuration Manager-hely a Configuration Manager-ügyfél történő. Ez lehet egy háromkarakteres Helykód vagy az Auto. Ha az Auto kifejezés van megadva, vagy ha ez a tulajdonság nincs megadva, az ügyfél kísérli meg meghatározni a Configuration Manager helyhozzárendelése Active Directory tartományi szolgáltatásokból vagy egy meghatározott felügyeleti pontból. AUTOMATIKUS ügyfélfrissítések engedélyezéséhez meg kell adnia [SITEREASSIGN](#sitereassign) igaz értékre.    

> [!NOTE]  
>  Ne használja az AUTO kifejezést, ha az internetalapú felügyeleti pontot (CCMHOSTNAME) is megadja. Ebben az esetben közvetlenül hozzá kell rendelnie az ügyfelet a helyhez.  

 Például: `CCMSetup.exe SMSSITECODE=XZY`  

##  <a name="BKMK_attributevalues"></a> A PKI-tanúsítvány kiválasztási feltételeinek támogatott attribútumértékei  
 A Configuration Manager a PKI-tanúsítvány kiválasztási feltételeinek a következő attribútumértékeit támogatja:  

|OID-attribútum|Megkülönböztető név attribútum|Attribútumdefiníció|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|Tartomány-összetevő|  
|1.2.840.113549.1.9.1|E vagy E-mail|E-mail cím|  
|2.5.4.3|CN|Köznapi név|  
|2.5.4.4|SN|Tulajdonos neve|  
|2.5.4.5|SERIALNUMBER|Sorozatszám|  
|2.5.4.6|C|Országkód|  
|2.5.4.7|L|Helység|  
|2.5.4.8|S vagy ST|Állam vagy megye neve|  
|2.5.4.9|STREET|Utca, házszám|  
|2.5.4.10|O|Szervezet neve|  
|2.5.4.11|OU|Szervezeti egység|  
|2.5.4.12|T vagy Title|Cím|  
|2.5.4.42|G vagy GN vagy GivenName|Utónév|  
|2.5.4.43|I vagy Initials|Monogram|  
|2.5.29.17|(nincs érték)|Tulajdonos alternatív neve|  

