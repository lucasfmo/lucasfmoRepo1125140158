---
title: "Ügyfelek Windows Embedded-eszközökre való központi telepítésének megtervezése |} Microsoft Docs"
description: "Tervezze meg a Windows Embedded-eszközök a System Center Configuration Managerben történő központi ügyféltelepítésre."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 038e61f9-f49d-41d1-9a9f-87bec9e00d5d
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: f7ef476a2ebcf0161ebb70d8a3d95f77806aa05e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-windows-embedded-devices-in-system-center-configuration-manager"></a>Windows Embedded rendszerű eszközökön a System Center Configuration Manager ügyfél központi telepítésének tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

<a name="BKMK_DeployClientEmbedded"></a>Ha a Windows Embedded-eszköz nem tartalmazza a System Center Configuration Manager-ügyfél, ha az eszköz megfelel a szükséges függőségek használhatja bármelyik ügyfél-telepítési módszer. Ha az Embedded-eszköz támogatja az írási szűrőket, le kell tiltani ezeket a szűrőket az ügyfél telepítése előtt, majd újra engedélyezni kell és egy helyhez kell rendelni őket az ügyfél telepítése után.  

 Ügyeljen arra, hogy ha letiltja a szűrőket, ne tiltsa le a szűrő-illesztőprogramokat. Ezek az illesztőprogramok általában automatikusan elindulnak, amikor a számítógép elindul. Az illesztőprogramok letiltása egyrészt megakadályozhatja az ügyfél telepítését, másrészt ütközhet az írási szűrők vezénylésével, ami meghiúsíthatja az ügyfél műveleteit. Az alábbi szolgáltatások társulnak az egyes írásiszűrő-típusokhoz, amelyeknek nem szabad megszakítani a futását:  

|Írási szűrő típusa|Illesztőprogram|Típus|Leírás|  
|-----------------------|------------|----------|-----------------|  
|EWF|EWF|Kernel|Megvalósítja a szektorszintű I/O-átirányítást védett köteteken.|  
|FBWF|FBWF|Fájlrendszer|Megvalósítja a fájlszintű I/O-átirányítást védett köteteken.|  
|UWF|uwfreg|Kernel|UWF beállításjegyzék-átirányító|  
|UWF|uwfs|Fájlrendszer|UWF fájlátirányító|  
|UWF|uwfvol|Kernel|UWF kötetkezelő|  

 Az írási szűrők megadják, hogy az Embedded-eszköz operációs rendszere hogyan frissül, amikor módosításokat végez (például szoftvert telepít). Ha az írási szűrők engedélyezve vannak, akkor a módosítások nem közvetlenül az operációs rendszeren lesznek elvégezve, hanem egy átmeneti területre lesznek átirányítva. Ha a módosítások csak az átmeneti területre íródnak, akkor az eszköz leállásakor elvesznek. Ha azonban az írási szűrők átmenetileg le vannak tiltva, a módosítások véglegessé tehetők, így nem kell újból elvégezni a módosításokat (vagy újratelepíteni a szoftvert) az Embedded-eszköz minden újraindításakor. Az írási szűrők átmeneti letiltása és újbóli engedélyezése azonban egy vagy több újraindítást igényel, ezért érdemes megadni, hogy mikor történjen; ehhez konfigurálhatja úgy a karbantartási időszakokat, hogy az újraindítások ne munkaidőben történjenek.  

 A beállításokkal megadhatja az írási szűrők automatikus letiltását és újraengedélyezését, amikor központilag telepít szoftvert, például alkalmazásokat, feladatütemezéseket, szoftverfrissítéseket és az Endpoint Protection-ügyfelet. Kivételek az automatikus szervizelést használó konfigurációs elemekkel rendelkező referenciakonfigurációk. Ilyen esetben a szervizelés mindig az átmeneti területe történik, hogy csak az eszköz újraindításáig legyen elérhető. A szervizelést a rendszer újból alkalmazza a következő értékelési ciklusban, de csak az átmeneti területre, amelynek tartalma újraindításkor törlődik. Véglegesítse a szervizelési módosításokat, ha a Configuration Manager kényszerítéséhez telepítheti a referenciakonfigurációt, majd egy másik, amint lehetséges a módosítás véglegesítését támogató szoftvertelepítést.  

 Ha az írási szűrők le vannak tiltva, telepíthet szoftvert a Windows Embedded-eszközökre a Szoftverközpont használatával. Ha az írási szűrők engedélyezve vannak, a telepítés sikertelen lesz, és a Configuration Manager jelenik meg hibaüzenet, hogy rendelkezik-e megfelelő engedélye az alkalmazás telepítésére.  

> [!WARNING]  
>  Akkor is, ha nem jelöli be a Configuration Manager beállításait a módosítások véglegesítéséhez, a módosítások véglegessé válhatnak, ha egy másik Szoftvertelepítés vagy módosítás is, amely véglegesíti a módosításokat. Ilyen esetben az eredeti módosítások is véglegesítve lesznek az új módosítások mellett.  

 Ha a Configuration Manager letiltja az írási szűrőket a módosítások véglegesítéséhez, csak a helyi felügyeleti jogokkal rendelkező felhasználók jelentkezhetnek be és használhatják az embedded-eszközt. Ezen időszak alatt az alacsony jogosultságú felhasználók ki vannak zárva, és üzenet tájékoztatja őket arról, hogy a számítógép szervizelés miatt nem használható. Ez segíti az eszköz védelmét, amíg olyan állapotban van, amelyben a módosítások véglegesíthetők. A karbantartási üzemmód alatti zárolás miatt is olyan időpontra érdemes konfigurálni a karbantartási időszakot, amikor a felhasználók nem jelentkeznek be az eszközökre.  

 A Configuration Manager a következő szűrőtípusok kezelését támogatja:  

-   Fájlalapú írási szűrő (FBWF) – további információért lásd: [fájlalapú írási szűrő](http://go.microsoft.com/fwlink/?LinkID=204717).  

-   Speciális írási szűrő (EWF) memóriabeli Átfedéssel - további információkért lásd: [speciális írási szűrő](http://go.microsoft.com/fwlink/?LinkId=204718).  

-   Egyesített írási szűrő (UWF) – további információért lásd: [egyesített írási szűrő](http://go.microsoft.com/fwlink/?LinkId=309236).  

 A Configuration Manager nem támogatja a írásiszűrő-műveleteket, ha a Windows Embedded-eszköz EWF Memóriabeli beállításjegyzék-átfedő módban van.  

> [!IMPORTANT]  
>  Ha van rá lehetősége, használja fájlalapú írási szűrőt (FBWF) a Configuration Manager a jobb hatékonyság és méretezhetőség.
>
> **Csak FBWF használó eszközök esetén:** Konfigurálja a következő kivételeket az ügyfélállapot és a leltáradatok eszköz-újraindítások közötti megőrzéséhez:  
>   
>  -   A ccminstalldir mappa\\*.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
>  A Windows Embedded 8.0-s vagy újabb verzióját futtató eszközök nem támogatják a helyettesítő karaktereket tartalmazó kizárásokat. Ezeken az eszközökön egyedileg kell konfigurálnia az alábbi kizárásokat:  
>   
>  -   A CCMINSTALLDIR mappa .sdf kiterjesztésű összes fájlját, általában a következőket:  
>   
>     -   UserAffinityStore.sdf  
>     -   InventoryStore.sdf  
>     -   CcmStore.sdf  
>     -   StateMessageStore.sdf  
>     -   CertEnrollmentStore.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
> **Használó eszközök esetében FBWF és UWF csak:** Amikor egy munkacsoportban az ügyfelek tanúsítványokat használnak a hitelesítéshez a felügyeleti pontokon, ki kell zárnia a titkos kulcsot az ügyfél továbbra is a felügyeleti ponttal való kommunikáció biztosításához is. Ezeken az eszközökön konfigurálja a következő kizárásokat:  
>   
>  -   c:\Windows\System32\Microsoft\Protect  
> -   c:\ProgramData\Microsoft\Crypto  
> -   HKEY_LOCAL_MACHINE\Software\Microsoft\SystemCertificates\SMS\Certificates  

 Egy példán keresztül telepítésére és felügyeletére Windows Embedded engedélyezett írási szűrőkkel eszközökre a Configuration Managerben lásd [példa központi telepítésére és felügyeletére Windows Embedded-eszközökön a System Center Configuration Manager ügyfelek](../../../../core/clients/deploy/example-scenario-for-deploying-and-managing-clients-on-windows-embedded-devices.md).  

 A lemezképek Windows Embedded-eszközökhöz történő elkészítéséről és az írási szűrők konfigurálásáról a Windows Embedded dokumentációjából vagy a készülék gyártójától kaphat további információt.  

> [!NOTE]  
>  Amikor kiválasztja a megfelelő platformokat a szoftverek központi telepítéséhez és a konfigurációs elemekhez, az adott verziók helyett a Windows Embedded-családok láthatók. Az alábbi listából megfeleltetheti egymásnak a Windows Embedded adott verzióját és a listamező beállításait:  
>   
>  -   **A Windows XP-alapú (32 bites) Embedded operációs rendszerek** az alábbiak:  
>   
>      -   Windows XP Embedded  
>     -   Windows Embedded for Point of Service  
>     -   Windows Embedded Standard 2009  
>     -   Windows Embedded POSReady 2009  
> -   **A Windows 7-alapú (32 bites) Embedded operációs rendszerek** az alábbiak:  
>   
>      -   Windows Embedded Standard 7 (32 bites)  
>     -   Windows Embedded POSReady 7 (32 bites)  
>     -   Windows ThinPC  
> -   **A Windows 7-alapú (64 bites) Embedded operációs rendszerek** az alábbiak:  
>   
>      -   Windows Embedded Standard 7 (64 bites)  
>     -   Windows Embedded POSReady 7 (64 bites)

