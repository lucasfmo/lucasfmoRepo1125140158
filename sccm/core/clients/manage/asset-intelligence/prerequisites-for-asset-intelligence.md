---
title: "Asset Intelligence Előfeltételek |} Microsoft Docs"
description: "Az Eszközintelligencia előfeltételei a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 23ab4f94-7bfe-436e-8a6a-029409a2730c
caps.latest.revision: 10
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 2bcc6dd84b236187ea9cbfa0b85c25e7ec25719c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-asset-intelligence-in-system-center-configuration-manager"></a>A System Center Configuration Manager Eszközintelligencia előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager Eszközintelligencia jelentéskészítésnek külső és a termékben lévő függőségei is.  

## <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  
 A következő táblázat a függőségeket, amelyek külső a Configuration Manager eszközintelligencia.  

|Függőség|További információ|  
|----------------|----------------------|  
|Sikeres bejelentkezési események naplózásának előfeltételei|Négy eszközintelligencia-jelentés az ügyfélszámítógépek Windows biztonsági eseménynaplójából gyűjtött információkat jelenít meg. Ha a biztonsági eseménynapló beállításai nincsenek konfigurálva minden sikeres bejelentkezés naplózásához, akkor ezek a jelentések nem tartalmaznak adatokat, még akkor sem, ha a megfelelő hardverleltár-jelentési osztály engedélyezve van.<br /><br /> A következő eszközintelligencia-jelentés a Windows biztonsági eseménynaplóból összegyűjtött információtól függ:<br /><br /> -A hardver 03A – elsődleges felhasználók<br />-A hardver 03B – a megadott elsődleges Konzolfelhasználóhoz tartozó számítógépek<br />-Hardver 04A - megosztott (többfelhasználós) számítógépek<br />-Hardver 05A – egy adott számítógép Konzolfelhasználói<br /><br /> Ahhoz, hogy a hardverleltározási ügyfélügynök leltározhassa az ezen jelentések támogatásához szükséges adatokat, előbb módosítania kell az ügyfelek Windows biztonsági eseménynaplójának beállításait, hogy az összes sikeres bejelentkezést naplózzák, és engedélyeznie kell a **SMS_SystemConsoleUser** hardverleltár-jelentési osztályt. Az összes sikeres bejelentkezési események naplózása a biztonsági eseménynapló beállításainak módosításával kapcsolatos további információkért lásd: [sikeres bejelentkezési események naplózásának engedélyezése](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableSuccessLogonEvents).|  

> [!NOTE]  
>  Az **SMS_SystemConsoleUser** hardverleltár-jelentési osztály csak az előző 90 nap sikeres bejelentkezés eseményeinek adatait őrzi meg a biztonsági eseménynaplóban, függetlenül a napló hosszától. Ha a biztonsági eseménynaplóban kevesebb, mint 90 nap adatai szerepelnek, a teljes naplót beolvassa a program.  

## <a name="dependencies-internal-to-configuration-manager"></a>A Configuration Manageren belüli függőségek  
 A következő táblázat az Eszközintelligencia, amelyek a Configuration Manageren belüli függőségek biztosít.  

|Függőség|További információ|  
|----------------|----------------------|  
|Ügyfélügynök előfeltételei|Az eszközintelligencia-jelentések az ügyfél hardver- és szoftverleltár-jelentésein keresztül szerzett ügyféladatoktól függenek. Az összes eszközintelligencia-jelentéshez szükséges információk beszerzéséhez engedélyezni kell a következő ügyfélügynököket:<br /><br /> -A hardverleltározási Ügyfélügynök<br />-Szoftverhasználat mérési Ügyfélügynök|  
|Hardverleltározási ügyfélügynök függőségei|Az egyes eszközintelligencia-jelentésekhez szükséges leltáradatok gyűjtéséhez engedélyezni kell a hardverleltározási ügyfélügynököt. Emellett az elsődleges helykiszolgáló számítógépeken engedélyezni kell bizonyos olyan hardverleltár-jelentési osztályokat, amelyekre eszközintelligencia-jelentések támaszkodnak.<br /><br /> A Hardverleltározási Ügyfélügynök engedélyezésével kapcsolatos információkért lásd: [a System Center Configuration Managerben a Hardverleltár bővítése](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).|  
|Szoftverhasználat-mérési ügyfélügynök függőségei|Az Eszközintelligencia néhány szoftverjelentése a Szoftverhasználat-mérési ügyfélügynök adataira  támaszkodik. A szoftverhasználat-mérési Ügyfélügynök engedélyezésével kapcsolatos információkért lásd: [Alkalmazáshasználat figyelése a szoftverhasználat-mérés a System Center Configuration Managerben](../../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).<br /><br /> A következő eszközintelligencia-jelentések a Szoftverhasználat-mérési ügyfélügynök adataira  támaszkodnak:<br /><br /> -Szoftver 07A – mostanában használt végrehajtható fájlok a számítógépek száma alapján<br />-Szoftver 07B – számítógépek mostanában használt egy megadott végrehajtható fájl<br />-Szoftver 07C – adott számítógépen mostanában használt végrehajtható fájlok<br />-Szoftver 08A – mostanában használt végrehajtható fájlok, a felhasználók száma szerint<br />-Szoftver 08B – a felhasználók mostanában használó egy megadott végrehajtható fájl<br />-Szoftver 08C – megadott felhasználó által mostanában használt végrehajtható fájlok|  
|Eszközintelligencia hardverleltár-jelentési osztályainak előfeltételei|A Configuration Manager Eszközintelligencia-jelentések adott Hardverleltár-jelentési osztályok függ. Amíg nem engedélyezi a hardverleltár-jelentési osztályokat, és az ügyfelek nem jelentették a hardverleltárt ezen osztályok alapján, addig a társított eszközintelligencia-jelentések nem tartalmaznak adatokat. A következő hardverleltár-jelentési osztályokat engedélyezheti az Eszközintelligencia jelentéskészítési követelményeinek támogatására:<br /><br /> -SMS_SystemConsoleUsage<sup>1</sup><br />-SMS_SystemConsoleUser<sup>1</sup><br />-SMS_InstalledSoftware<br />-SMS_AutoStartSoftware<br />-SMS_BrowserHelperObject<br />-Win32_USBDevice<br />-SMS_InstalledExecutable<br />-SMS_SoftwareShortcut<br />-SoftwareLicensingService<br />-SoftwareLicensingProduct<br />-SMS_SoftwareTag<br /><br /> <sup>1</sup> Az Eszközintelligencia **SMS_SystemConsoleUsage** és az **SMS_SystemConsoleUser** hardverleltár-jelentési osztályai alapértelmezés szerint engedélyezve vannak.<br /><br /> Szerkesztheti az Eszközintelligencia Hardverleltár-jelentési osztályok Configuration Manager konzolon a a **eszközök és megfelelőség** munkaterületen kattintva a **Eszközintelligencia** csomópont. További információkért lásd: a [engedélyezése az Eszközintelligencia Hardverleltár-jelentési osztályok](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableAssetIntelligence) szakasz a [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md) témakör.|  
|Jelentéskészítési szolgáltatási pont|A szoftverfrissítési jelentések megjelenítéséhez telepíteni kell a jelentéskészítési szolgáltatási pont helyrendszerszerepkörét. További információ jelentéskészítési szolgáltatási pont létrehozásáról: [A jelentéskészítés konfigurálása a Configuration Manager alkalmazásban](http://go.microsoft.com/fwlink/p/?LinkId=232661).|  

