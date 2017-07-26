---
title: "Hely rendszer szerepkör-beállítások |} Microsoft Docs"
description: "Tekintse meg a Configuration Manager helyrendszer-szerepköröket, amelyek nem feltétlenül értetődő vonatkozó további információért."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fff93794afdfa9f890b1f06d6c330d8cffc5796c
ms.openlocfilehash: b4db5d86cc0ed020ed176feb2e8f1f9dc51a2280
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>Configuration options for site system roles for System Center Configuration Manager (Konfigurációs beállítások helyrendszerszerepkörökhöz a System Center Configuration Managerhez)

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager helyrendszer-szerepkörök konfigurációs beállításainak többsége magától értetődő, illetve szakaszban találhatók a varázsló vagy a párbeszédpaneleken őket konfigurálásakor. Az alábbi szakaszok ismertetik a helyrendszer-szerepkörök, amelynek beállításait további információra lehet szükség.  

##  <a name="BKMK_ApplicationCatalog_Website"></a>Az Alkalmazáskatalógus weboldal-elérési pontja  
 Az alkalmazáskatalógus az Alkalmazáskatalógus weboldal-elérési pontja beállításával kapcsolatos információkért lásd: [tervezése és az Alkalmazáskezelés konfigurálása a System Center Configuration Managerben](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **Ügyfélkapcsolatok**  

 Válassza ki **HTTPS** szeretne használni a biztonságosabb beállítás, és ellenőrizze, hogy az ügyfelek az internetről kapcsolódnak. Ez a beállítás PKI-tanúsítványt igényel a kiszolgálón az ügyfelek számára a kiszolgáló hitelesítéséhez, és az adatok titkosítása a Secure Socket Layer (SSL) rétegen keresztül. További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Egy példával szemlélteti a telepítést a kiszolgálói tanúsítvány és konfigurálása az Internet Information Services (IIS) kapcsolatos információkat lásd: a *a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS* szakasz [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

 **Alkalmazáskatalógus hozzáadása a megbízható helyek zónához**  

 Ezt az üzenetet jeleníti meg az értékét az alapértelmezett ügyfélbeállítások e a **alkalmazáskatalógus hozzáadása az Internet Explorer Megbízható helyek zónához** ügyfélbeállítást a jelenleg beállított **igaz** vagy **hamis**. Egyéni ügyfélbeállítások segítségével konfigurálja ezt a beállítást, ellenőrizni kell ezt az értéket saját maga.  

 Ha a helyrendszer be van állítva egy teljesen minősített tartománynevét (FQDN), és a webhely nincs az Internet Explorer Megbízható helyek zónájába, felhasználók rendszer hitelesítő adatokat kér az Alkalmazáskatalógushoz történő csatlakozáskor.  

 **Szervezet neve**  

 Adja meg, amelyet a felhasználók az Alkalmazáskatalógust. A márkajelzés alapján a felhasználók azonosíthatják azokat a webhely megbízható forrásból származik.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a>Az Alkalmazáskatalógus webszolgáltatási pontja  
 Az alkalmazáskatalógus az Alkalmazáskatalógus webszolgáltatási pontját beállításával kapcsolatos információkért lásd: [tervezése és az Alkalmazáskezelés konfigurálása a System Center Configuration Managerben](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **HTTPS**  

 Válassza ki **HTTPS** beállítással hitelesítheti az Alkalmazáskatalógus weboldal-elérési pontjait az Alkalmazáskatalógus webszolgáltatási pontjai számára.  Ez a beállítás a kiszolgálóra, amelyik futtatja a Alkalmazáskatalógus weboldal-elérési pontja server-hitelesítést és az adatok titkosítása SSL-en keresztül PKI-tanúsítványt igényel. További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Telepítését bemutató példát a kiszolgálói tanúsítvány és az IIS konfigurálásának ismertetését lásd: a *a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS* szakasz [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_CertificateRegistrationPoint"></a>Tanúsítványregisztrációs pont  
 A tanúsítványregisztrációs pont beállításával kapcsolatban bővebben lásd: [tanúsítványprofilok ismertetése](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

##  <a name="BKMK_Distribution_Point"></a>Terjesztési pont  
 A terjesztési pontnak a tartalom központi telepítéséhez beállításával kapcsolatban bővebben lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 További információ a terjesztési pont PXE központi telepítéshez beállításához, lásd: [PXE használatával a Windows központi telepítése a hálózaton a System Center Configuration Managerrel](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Állítsa be a csoportos központi telepítést a terjesztési ponthoz kapcsolatos információkért lásd: [használjon csoportos Windows központi telepítése a hálózaton a System Center Configuration Managerrel](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 **Telepítse és konfigurálja az IIS, ha a Configuration Manager megköveteli**  
 Válassza ezt a lehetőséget, hogy a Configuration Manager telepítése és beállítása IIS szolgáltatást a helyrendszeren, ha még nincs telepítve. Az IIS telepíteni kell az összes terjesztési ponton, és ezt a beállítást, a varázslóban a folytatáshoz ki kell választania.  

 **Helyrendszer-telepítési fiók**  
 A helykiszolgálón telepített terjesztési pontok csak a helykiszolgáló számítógépfiókja támogatott a helyrendszer-telepítési fiókot használni.  

 **Hozzon létre egy önaláírt tanúsítványt, vagy importáljon egy PKI ügyféltanúsítványt**  
 Ennek a tanúsítványnak két célja van:  

1.  Mielőtt a terjesztési pont elküldi az állapotüzeneteket hitelesíti a terjesztési pontot egy felügyeleti pontra.  

2.  Ha **PXE-támogatás engedélyezése ügyfeleknek** van kijelölve, rendszer elküldi a tanúsítványt a számítógépeknek, amelyeken a PXE-rendszerindítást tegye, hogy csatlakozhassanak egy felügyeleti ponthoz az operációs rendszer telepítése során.  

Amikor a hely a felügyeleti pontok HTTP vannak beállítva, hozzon létre egy önaláírt tanúsítványt. A felügyeleti pontok vannak beállítva a HTTPS-hez, ha PKI-ügyféltanúsítvány importálása  

A tanúsítvány importálásához jelöljön ki egy nyilvános kulcsú titkosítás szabványok #12 (PKCS #12) fájlt, amely rendelkezik a következő követelményeket a Configuration Manager PKI-tanúsítványt:  

-   Felhasználási célnak tartalmaznia ügyfél-hitelesítéshez.  

-   A titkos kulcs exportálható kell beállítani.  

Nincsenek a tanúsítvány tulajdonos neve vagy a tulajdonos alternatív nevére (SAN) megadott követelmények, és egy tanúsítvány pedig több terjesztési ponthoz is használhatja.  

További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md). Ez a tanúsítvány telepítését bemutató példát, tekintse meg a *a terjesztési pontok az ügyféltanúsítvány központi telepítése* szakasz [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

**Engedélyezése e terjesztési pont használatát előzetesen beállított tartalomhoz**  
Ellenőrizze a jelölőnégyzet bejelölésével engedélyezheti a terjesztési pont használatát előzetesen beállított tartalomhoz. Ha a jelölőnégyzet be van jelölve, állíthat be terjesztés működését a tartalmak terjesztése során. Dönthet úgy, hogy Ön mindig manuálisan előkészíti a tartalmat a terjesztési ponton, a csomag kezdeti tartalmát, de a normál tartalomterjesztési folyamatot használja a tartalom frissítése vagy mindig a normál tartalomterjesztési folyamatot használja a csomag tartalmához.  

**Határcsoportok**  
 A terjesztési pontokhoz határcsoportokat társíthat. Tartalom központi telepítésekor az ügyfeleknek a terjesztési pont a tartalom forráshelyeként használni társított határcsoportban kell lenniük.
 - **1610-es vagy korábbi**, ellenőrizheti a **tartalék forráshely engedélyezése a tartalom** jelölőnégyzet bejelölésével engedélyezheti, hogy csoportok visszatérjenek, és a terjesztési pontokat használják a forráshely tartalom Ha érhetők el más terjesztési pontoktól ezeken a határcsoportokon kívüli ügyfelek.
 - **Verziójától 1610**, már nem konfigurálható **tartalék forráshely engedélyezése a tartalom**.  Ehelyett határcsoportokat, ellenőrizze, hogy amikor egy ügyfél kezdődhet keressen további határcsoportok érvényes tartalomforrás-helyek közötti kapcsolatot létrehozni.

##  <a name="BKMK_Enrollment_Point"></a>A beléptetési pont  
A beléptetési pontok Mac számítógépek telepítése és regisztrálása a helyszíni mobileszköz-kezeléssel kezelt eszközök segítségével. További információkért tekintse át a következőket:  

-   [Ügyfélszoftverek központi telepítése Mac-számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [A helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök regisztrálása a felhasználók](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**Megengedett kapcsolatok**  
 A HTTPS beállítás automatikusan ki van jelölve, és a kiszolgálón PKI-tanúsítványt igényel a hitelesítéshez a beléptetési proxypont, a kiszolgáló hitelesítéséhez a sávon kívüli szolgáltatási pont és az adatok titkosítása SSL-en keresztül. További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Telepítését bemutató példát a kiszolgálói tanúsítvány és az IIS konfigurálásának ismertetését lásd: a *a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS* szakasz [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Enrollment_Proxy_Point"></a>Beléptetési proxypont  
A beléptetési proxypont mobileszközökhöz beállításával kapcsolatban bővebben lásd: [a helyszíni mobileszköz-kezelés a System Center Configuration Manager-eszközök regisztrálása a felhasználók](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md).  

**Ügyfélkapcsolatok**  
 A HTTPS beállítás automatikusan ki van jelölve, és PKI-tanúsítványt igényel a kiszolgálón a kiszolgálóhitelesítés mobileszközökre és Mac számítógépek, a Configuration Manager által beléptetett, valamint az adatok titkosítása a Secure Sockets Layer (SSL) rétegen keresztül. További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Telepítését bemutató példát a kiszolgálói tanúsítvány és az IIS konfigurálásának ismertetését lásd: a *a webkiszolgáló-tanúsítvány telepítése a Helyrendszerekhez, hogy futtassa IIS* szakasz [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Fallback_Status_Point"></a>Tartalék állapotkezelő pont  
**Állapotjelző üzenetek számának** és **késleltetési időköz (másodpercben)**  
Bár ezek a beállítások (10 000 állapotjelző üzenetek és 3600 másodperces késleltetési időköz) alapértelmezett beállításai elegendőek a legtöbb esetben, lehetséges, hogy a módosításukra, mindkét alábbi feltétel teljesülése esetén:  

-   A tartalék állapotkezelő pont csak az intranetről érkező kapcsolatokat fogad.  

-   Sok számítógép használja a tartalék állapotkezelő pont egy ügyfél-telepítési bevezetés alatt.  

Ebben az esetben az állapotüzenetek állandó folyama előfordulhat, hogy hozzon létre a várakozó állapotüzenetek előidéző magas processzor (CPU) a helykiszolgálón huzamosabb ideig. Ezenkívül, előfordulhat, hogy nem jelennek meg a friss információk az ügyféltelepítésről a Configuration Manager konzolon, és az ügyfél-telepítési jelentésekben.  

A tartalék állapotkezelő pont beállításainak úgy tervezték, hogy ügyféltelepítéskor keletkező állapotüzenetekkel kapcsolatos beállítása. A beállítások tervezték nem állítható be, az ügyfél-kommunikációs problémák, például ha az interneten lévő ügyfelek az internetalapú felügyeleti pont nem tud kapcsolódni. A tartalék állapotkezelő pont nem vonatkoznak ezek a beállítások csak az állapotüzeneteket, amelyek ügyféltelepítés közben keletkeznek, mert konfigurálja őket, ha a tartalék állapotkezelő pont az internetről érkező kapcsolatokat fogad.  

Minden számítógép, amely sikeresen telepíti a System Center 2012 Configuration Manager-ügyfél a következő négy állapotüzenetet küldi a tartalék állapotkezelő pont:  

-   Ügyfél-KözpontiTelepítés elindítva  

-   Ügyfelek központi telepítése sikeres volt.  

-   Ügyfél-hozzárendelés elindítva  

-   Ügyfél-hozzárendelés sikerült  

Számítógépek, amelyek nem lehet telepíteni vagy, amely a Configuration Manager-ügyfelet rendelje hozzá a további állapotüzeneteket küldenek.  

Például 20000 számítógépre telepíti a Configuration Manager-ügyfél, ha a központi telepítés el tudja küldeni 80000 állapotüzenetet a tartalék állapotkezelő pont számára. Az alapértelmezett késleltetési konfiguráció lehetővé teszi 10000 állapotüzenet küldését a tartalék állapotkezelő pont minden 3600 másodperc (1 óra), mert állapotüzenetek várakozhatnak a tartalék állapotkezelő pontot. A rendelkezésre álló hálózati sávszélességet a tartalék állapotkezelő pont és a helykiszolgáló és a sok állapotüzenet feldolgozásához a helykiszolgáló feldolgozási kapacitását között is figyelembe kell vennie.  

Ezek a problémák megelőzése érdekében fontolja meg az állapotjelző üzenetek számának növelését és a késleltetési időközt csökkenését.  

Alaphelyzetbe állítja a késleltetési értékeket a tartalék állapotkezelő pont, ha a következő feltételek valamelyike teljesül:  

-   Akkor kiszámítja, hogy az aktuális késleltetési értékek magasabbak szükséges állapotüzenetek feldolgozásához a tartalék állapotkezelő pontról.  

-   Látnia, ha az aktuális késleltetési beállítások magas CPU-használatot hozzon létre a helykiszolgálón.  

Ne módosítsa a tartalék állapotkezelő pont késleltetési beállításait beállításait, ha nincs tisztában a következményekkel. Például növeli a késleltetési beállításokat, a helykiszolgáló Processzorának terhelése emelheti magas, ami lelassítja az összes műveletet a helyen.  

