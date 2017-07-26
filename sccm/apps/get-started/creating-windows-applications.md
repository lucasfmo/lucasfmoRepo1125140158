---
title: "Windows-alkalmazások fejlesztéséhez |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozásakor és központi telepítése a Windows-eszközökhöz készült alkalmazások."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9181c84e-d74f-44ea-9bb9-f7805eb465fc
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: 9c80cc42f9ce6775067a89a9f5a63c1bf4a0c7ca
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>Windows-alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az egyéb System Center Configuration Manager követelményei és eljárásai alkalmazások létrehozására vonatkozó, felül kell vennie az alábbiakat is figyelembe létrehozása és központi telepítésekor a Windows-eszközökhöz készült alkalmazások.  

## <a name="general-considerations"></a>Általános megfontolások  
 A következő alkalmazás típusú központi telepítése a Configuration Manager támogatja:  

|Eszköz típusa|Támogatott fájltípusok|  
|-----------------|---------------------|  
|Windows RT és Windows RT 8.1|*.appx, \*.appxbundle|  
|Windows 8.1 vagy újabb rendszer mobileszközként beléptetve|*.appx, \*.appxbundle|  

 A következő központi telepítési műveletek támogatottak:  

|Eszköz típusa|Támogatott műveletek|  
|-----------------|-----------------------|  
|Windows 8.1 és újabb|elérhető, szükséges, eltávolítás|  
|Windows RT|elérhető, szükséges, eltávolítás|  

## <a name="support-for-universal-windows-platform-uwp-apps"></a>Az univerzális Windows-platformra épülő alkalmazások támogatása  
 Windows 10-eszközökre közvetlen telepítésre szolgáló kulcs, az üzletági alkalmazások telepítéséhez nem szükséges. Közvetlen telepítéséhez engedélyezni kell, azonban a beállításkulcs **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** 1 értékűnek kell lennie.  

 Ha ez a beállításkulcs nincs konfigurálva, a Configuration Manager automatikusan beállítja ezt az értéket **1** először telepít egy alkalmazást az eszközre. Ha ezt az értéket meg **0**, a Configuration Manager nem tudja azt automatikusan módosítani a, és az üzletági alkalmazások telepítése sikertelen.  

 Univerzális Windows Platform-üzletági alkalmazásokat kell aláírni egy kódaláíró tanúsítványt, amely megbízhatónak minősül minden olyan eszközön, amelyre telepítik az alkalmazást. Ehhez használhatók a nyilvános kulcsokra épülő belső infrastruktúra tanúsítványai vagy az eszközre telepített, harmadik féltől származó nyilvános főtanúsítvány valamely tanúsítványa.  

 A Windows 10 Mobile rendszerű eszközökön nem a Symantec által kiállított kódaláíró tanúsítvánnyal is aláírhatók az univerzális **APPX-alkalmazások** . Azok a Windows Phone 8.1-es **XAP-alkalmazások** és **APPX-csomagok** , amelyeket Windows 10 Mobile rendszerű eszközökre kíván telepíteni, csak a Symantec által kiállított kódaláíró tanúsítvánnyal írhatók alá.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>A Windows Installer-alkalmazások telepítése regisztrált Windows 10 rendszerű számítógépeken  
 A **Windows Installer MDM-en keresztül (\*.msi)** alkalmazástípus lehetővé teszi az alkalmazások létrehozását és telepítését Windows Installer-alapú Windows 10-et futtató, regisztrált számítógépeken.  

 Ennek a telepítőtípusnak a használatakor a következőket kell figyelembe venni:  

-   Csakis egyetlen MSI-fájlt tölthet fel.  

-   Az alkalmazások észlelése a fájl termékkódjával és termékverziójával történik.  

-   Az alkalmazás alapértelmezett újraindítási viselkedését szolgál. A Configuration Manager nem szabályozza ezt.  

-   Felhasználónkénti MSI csomag telepítve egy-egy felhasználóhoz.  

-   Gépenkénti MSI-csomagok telepítve vannak-e az eszköz minden felhasználójához.  

-   Az alkalmazások frissítése akkor támogatott, ha minden verzió MSI-termékkódja ugyanaz.  

