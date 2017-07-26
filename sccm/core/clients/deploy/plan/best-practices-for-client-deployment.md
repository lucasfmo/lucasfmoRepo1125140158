---
title: "Ügyfél-telepítési gyakorlati tanácsok |} Microsoft Docs"
description: "Első gyakorlati tanácsok az ügyfelek központi telepítéséhez a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a933d69c-5feb-4b2b-84e8-56b3b64d5947
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 979c21c436429cad03a61671b707a99817146d95
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-client-deployment-in-system-center-configuration-manager"></a>Gyakorlati tanácsok az ügyfelek központi telepítéséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


## <a name="use-software-update-based-client-installation-for-active-directory-computers"></a>A szoftverfrissítés alapú ügyféltelepítés használata az Active Directory-beli számítógépeknél  
 Az ügyfél-telepítési módszer meglévő Windows technológiát használ, együttműködik az Active Directory infrastruktúrával, a Configuration Manager a legkevesebb konfigurálást igényli, a legkönnyebben konfigurálható a tűzfalakhoz és a legbiztonságosabb. A biztonsági csoportokat és WMI-szűrést használ a csoportházirend konfigurálásához, a magas fokú rugalmasságot biztosít annak vezérléséhez, mely számítógépek telepítése a Configuration Manager-ügyfél is rendelkezik.  

 További információk: [A Configuration Manager-ügyfelek telepítése szoftverfrissítés-alapú telepítéssel](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

## <a name="extend-the-active-directory-schema-and-publish-the-site-so-that-you-can-run-ccmsetup-without-command-line-options"></a>Az Active Directory-séma kiterjesztése és a hely közzététele úgy, hogy parancssori kapcsolók nélkül futtathassa a CCMSetup eszközt  
 Amikor kiterjeszti az Active Directory-sémát a Configuration Manager és a helyet közzéteszi az Active Directory tartományi szolgáltatásokban, számos ügyfél-telepítési tulajdonságokat az Active Directory tartományi szolgáltatásokban közzétett. Ha egy számítógép megtalálja ezeket az ügyfélszoftver telepítési tulajdonságokat, akkor használhatja azokat a Configuration Manager-ügyfél telepítésekor. Ezek az információk automatikusan állnak elő, ami kiiktatja a telepítési tulajdonságok manuális megadásánál keletkező emberi hibákat.  

 További információ: [Információ az Active Directory tartományi szolgáltatásokban közzétett ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

## <a name="use-a-phased-rollout-to-manage-cpu-usage"></a>Használjon fázisokra bontva történő bevezetéséhez a CPU-felhasználás kezelésére  
 Az ügyfelek fázisokra bontva történő bevezetéséhez a minimalizálása érdekében a hatását, hogy a helykiszolgáló Processzorának feldolgozási terhelését. Központi telepítése a munkaidőn kívüli ügyfelek számára, hogy más szolgáltatásokkal rendelkezik több sávszélesség álljon rendelkezésre a nap folyamán, és ne zavarja a felhasználókat, ha számítógépük lelassul, vagy újra kell indítani.  

## <a name="enable-automatic-upgrade-after-your-main-client-deployment-has-finished"></a>A fő ügyféltelepítés befejezése után engedélyezze az automatikus frissítést  
 [Automatikus ügyfélfrissítések](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) hasznosak, ha az ügyfélszámítógépek, amelyek kimaradtak a fő ügyfél-telepítési módszert, amelyet esetleg mert offline állapotban volt néhány frissíti. 

> [!NOTE]  
>  Teljesítménnyel kapcsolatos fejlesztések a Configuration Manager alkalmazásban is lehetővé teszik az automatikus frissítéseket használja elsődleges ügyfélfrissítési módszerként. A teljesítmény azonban a hierarchia infrastruktúrájától, például az ügyfelek számától függően változhat.  


## <a name="use-smsmp-and-fsp-if-you-install-the-client-with-clientmsi-properties"></a>Használja az SMSMP-t és az FSP-t, ha a client.msi tulajdonságaival telepíti az ügyfélszoftvereket  
 Az SMSMP tulajdonsága meghatározza a kezdeti felügyeleti pontot, amellyel az ügyfél kommunikál, és eltávolítja a függő viszonyt az olyan szolgáltatáskeresési megoldásoktól, mint az Active Directory tartományszolgáltatások, a DNS és a WINS.  

 Használja az FSP tulajdonságait, és telepítsen egy tartalék állapotkezelő pontot, hogy figyelhesse az ügyféltelepítést és -hozzárendelést, és azonosíthassa a kommunikációs problémákat.  

 További információk ezekről a lehetőségekről: [Tudnivalók a System Center Configuration Manager ügyfél-telepítési tulajdonságairól](../../../../core/clients/deploy/about-client-installation-properties.md).  

## <a name="install-client-language-packs-before-you-install-the-clients"></a>Az ügyfelek telepítése előtt telepítse az ügyféloldali nyelvi csomagok  
Azt javasoljuk, hogy telepítse az ügyféloldali nyelvi csomagokat az ügyfél telepítése előtt. Ha telepíteni [ügyféloldali nyelvi csomagok](../../../../core/servers/deploy/install/language-packs.md) (ahhoz, hogy további nyelveket) helyen, az ügyfelek telepítése után újra kell telepítenie az ügyfeleket csak akkor azokat a nyelveket. A mobileszköz-ügyfelek esetében a mobileszköz törlésével és léptesse be újra.  

## <a name="prepare-required-pki-certificates-in-advance"></a>Készítse elő a szükséges PKI-tanúsítványokat előre  
 Az internetes eszközök, a beléptetett mobileszközök és a Mac számítógépek felügyeletéhez PKI-tanúsítványokkal kell rendelkeznie a helyrendszereken (felügyeleti pontok és terjesztési pontok) és az ügyféleszközökön. Éles hálózati környezetben változáskezelési jóváhagyásra lehet szüksége az új tanúsítványok használatához, a helyrendszer-kiszolgálók újraindításához, a felhasználóknak pedig ki, majd újra be kell jelentkezniük az új csoporttagságuk életbe lépéséhez. Ezen felül megfelelő időt kell hagynia a biztonsági engedélyek és az új tanúsítványok sablonjainak replikációjához.  

 További információ a szükséges PKI-tanúsítványokat: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

## <a name="before-you-install-clients-configure-any-required-client-settings-and-maintenance-windows"></a>Az ügyfelek telepítése előtt konfigurálja a szükséges ügyfélbeállításokat és karbantartási időszakokat  
 Bár [ügyfélbeállítások konfigurálása](../../../../core/clients/deploy/configure-client-settings.md) és karbantartási időszak előtt, vagy az ügyfelek telepítése után, ajánlott, hogy segítségükkel, amint az ügyfél telepítve van az ügyfelek telepítése előtt kötelező beállítások konfigurálása. 

 A kiszolgálók és a Windows Embedded-eszközökön az eszközök az üzletmenet folytonosságának biztosítása karbantartási időszakok konfigurálása. A karbantartási időszakok biztosítják, hogy kötelező szoftverfrissítések és a kártevőirtó szoftverek ne indítsa újra a számítógépet munkaidőben.  

> [!IMPORTANT]  
>  Az egyesített írási szűrő (UWF) használatával védendő Windows 10-es számítógépeken konfigurálnia kell az eszközt az UWF-hez az ügyfél telepítése előtt. Ez lehetővé teszi a Configuration Manager telepíti az ügyfelet egy egyéni hitelesítőadat-szolgáltatójánál, mely megakadályozza, hogy az alacsony szintű jogosultsággal rendelkező felhasználók bejelentkezzenek az eszközre a karbantartási mód alatt.  

## <a name="plan-your-user-enrollment-experience-for-mac-computers-and-mobile-devices"></a>Tervezze meg a felhasználói beléptetés élményét Mac számítógépek és mobileszközök   
 Ha a felhasználók a saját Mac számítógépek és mobileszközök a Configuration Manager fognak beléptetni, tervezze meg a felhasználói élmény. Például egy parancsfájlt a telepítési és beléptetési folyamatról egy weblap segítségével, így a felhasználók adja meg a minimális szükséges információkat, és küldje el e-mailek utasításokat egy hivatkozással együtt.  

## <a name="use-file-based-write-filters-for-windows-embedded-devices"></a>Használja a fájlalapú írási szűrőket a Windows Embedded-eszközök 
 A Speciális írási szűrőt (EWF) használó Embedded-eszközök állapotüzenet-újraszinkronizálásokat tapasztalhatnak. Ha csak néhány speciális írási szűrőt használó Embedded-eszköze van, ezt nem fogja észrevenni. Ha azonban sok Embedded-eszköze van, melyek újraszinkronizálják adataikat, például teljes leltárt küldenek változásleltár helyett, az jelentősen növelheti a hálózati csomagok számát és a helykiszolgáló processzorának feldolgozási terhelését.  

 Ha megválaszthatja, hogy milyen típusú írási szűrőt engedélyezéséhez, válassza a fájlalapú írási szűrőket, és konfigurálja a kivételeket az ügyfélállapot és a leltáradatok közötti hálózati eszköz-újraindítások és a Configuration Manager-ügyfél a Processzor hatékonyságának megőrzéséhez. További információ az írási szűrőkről: [Az ügyfelek központi telepítésének megtervezése Windows Embedded-eszközökre a System Center Configuration Managerben](../../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

 További információ arról, hogy egy elsődleges hely legfeljebb hány Windows Embedded-ügyfelet tud támogatni: [Ügyfelek és eszközök által támogatott operációs rendszerek](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).  

