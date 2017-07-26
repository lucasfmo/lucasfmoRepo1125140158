---
title: "Eszközregisztráció beállítása |} Microsoft Docs"
description: "Megadja a felhasználóknak az eszközeik regisztrálását helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ffaea91-1379-4b86-9953-b25e152f56a9
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 16d4106d486d821b7ce92a1de65ebb04469d18de
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-device-enrollment-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Eszközregisztráció beállítása a helyszíni mobileszköz-felügyelethez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Így a felhasználók regisztrálhatják az eszközeiket a System Center Configuration Manager a\-helyszíni mobileszköz-kezelés megköveteli, hogy engedélyt ehhez. Megadja a felhasználóknak eszköz regisztrálására vonatkozó engedéllyel, kövesse az alábbi feladatok.

-   [A felhasználók számára a modern eszközök regisztrálását lehetővé tevő regisztrációs profil létrehozása](#bkmk_createProf)  

-   [A regisztrált eszközök további ügyfél-beállításainak megadása](#bkmk_addClient)  

-   [Annak engedélyezése, hogy a felhasználók megkapják a modern eszközök regisztrációs profilját](#bkmk_enableUsers)  

-   [A főtanúsítvány tárolása a regisztrálandó eszközökön](#bkmk_storeCert)  

##  <a name="bkmk_createProf"></a> A felhasználók számára a modern eszközök regisztrálását lehetővé tevő regisztrációs profil létrehozása  
 Engedélyezése a felhasználók számára modern eszközök regisztrálásához szükséges beállítások leküldéséhez hozzáadhat szánt új beléptetési profil az ügyfél alapértelmezett beállításait, amelyeket lekérdezi a Configuration Manager-hely összes felderített felhasználójára alkalmaz.  

1.  A Configuration Manager konzolon kattintson **felügyeleti** > **áttekintése** > **ügyfélbeállítások**, nyissa meg **alapértelmezett ügyfélbeállítások** válassza **beléptetési**.  

2.  Az Eszközbeállítások szakaszban adja meg a modern eszközök lekérdezési időközét.  

3.  A Felhasználói beállítások szakasz **Allow users to enroll modern devices** (Modern eszközök beléptetésének engedélyezése a felhasználóknak) beállításánál válassza az **Igen**lehetőséget.  

4.  A **Modern eszköz regisztrációs profilja**, kattintson a **profil beállítása...**  majd **létrehozása...**  

5.  A Beléptetési profil létrehozása párbeszédpanelen írja be a regisztrációs profil nevét, és válassza ki a felügyeleti hely kódját, melyet szeretne, ha a felhasználók és a regisztrációs profil használna. Többször az **OK** gombra kattintva lépjen ki az Alapértelmezett beállítások lapról.  

> [!NOTE]  
>  Ha a regisztrációs profilt a felderített felhasználók egy részhalmaza számára szeretné telepíteni, használhat egy felhasználógyűjteményt, és egyéni ügyfélbeállításokat hozhat létre a gyűjteményben való központi telepítéshez. Információk az egyedi ügyfélbeállítások létrehozásáról: [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md).  

##  <a name="bkmk_addClient"></a> A regisztrált eszközök további ügyfél-beállításainak megadása  
 A modern eszközök regisztrációs profiljának beállítása mellett további ügyfélbeállításokat is megadhat az eszközök konfigurálásához a regisztrálás során.  Információk az ügyfélbeállítások megadásáról: [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md).  

 Nem minden ügyfélbeállítás érhetők el a\-helyszíni mobileszköz-kezelés. A Configuration Manager aktuális ágának a következő ügyfélbeállításait támogatja a\-helyszíni mobileszköz-kezelés:  

-   Beléptetés – Ezek a beállítások határozzák meg a felügyelt eszközök regisztrációs profilját. További információk regisztrációs profil létrehozásáról: [A felhasználók számára a modern eszközök regisztrálását lehetővé tevő regisztrációs profil létrehozása](#bkmk_createProf).  

-   Ügyfélházirend – Ezekkel a beállításokkal adhatja meg, hogy milyen gyakran töltődjön le az ügyfélházirend az eszközre. Ezenkívül engedélyezheti a felhasználók házirendek lekérdezésével történő célzásának beállításait is. További információk az ügyfélházirend-beállításokról: [Tudnivalók a System Center Configuration Manager ügyfélbeállításairól](../../core/clients/deploy/about-client-settings.md), Ügyfélházirend szekció.  

-   Szoftver központi telepítése – Ez a beállítás határozza meg, hogy milyen időközönként vizsgálja meg a rendszer, kell-e szoftvert telepíteni az ügyféleszközökre. További információk a szoftverek központi telepítésének beállításairól: [Tudnivalók a System Center Configuration Manager ügyfélbeállításairól](../../core/clients/deploy/about-client-settings.md) című témakör Szoftverek központi telepítése című szakasza.  

    > [!NOTE]  
    >  Az a\-helyszíni mobileszköz-kezelés, szoftver központi telepítése a beállítások csak akkor használható, alapértelmezett ügyfélbeállításokat. Szoftverek központi telepítési beállításai a Configuration Manager aktuális ágának egyéni ügyfélbeállítások nem használható.  

##  <a name="bkmk_enableUsers"></a> Annak engedélyezése, hogy a felhasználók megkapják a modern eszközök regisztrációs profilját  
 A felhasználók megkapják a módosított ügyfélbeállításokat a beléptetési profil a\-helyszíni mobileszköz-kezelés, akkor fel kell deríteni az Active Directory felderítési módszer használatával. Futtassa az Active Directory-felhasználók felderítését annak biztosítására, hogy mindenki megkapja a regisztrációs profilt, akinek szüksége van rá. További információk felhasználók felderítéséről: [A felderítés futtatása a System Center Configuration Managerből](../../core/servers/deploy/configure/run-discovery.md).  

##  <a name="bkmk_storeCert"></a> A főtanúsítvány tárolása a regisztrálandó eszközökön  
 A tartományhoz csatlakoztatott eszközökkel rendelkező felhasználók valószínűleg már rendelkeznek a helyrendszerszerepköröket üzemeltető kiszolgálókkal való megbízható kommunikációhoz szükséges főtanúsítvánnyal, mert a főtanúsítvány az Active Directoryval elvégzett tartományhoz való csatlakozási folyamat részeként ki lett adva. A tartományon kívüli számítógépeken és mobileszközökön manuálisan kell telepíteni a főtanúsítványt, hogy végre lehessen hajtani a regisztrációt. Ezek az eszközök nem fognak automatikusan rendelkezni a szükséges főtanúsítvánnyal.  

 Biztosítani kell az eszköz számára az exportált tanúsítványfájlt a manuális telepítéshez. Ezt megteheti e-mailben, a OneDrive-val, SD-kártyával, USB-meghajtóval vagy bármilyen, az igényeinek leginkább megfelelő módszerrel.  

 Az eszközökön használni kívánt főtanúsítvány az, amelyet az alábbi helyen exportált: [A tanúsítvány exportálása a webkiszolgáló-tanúsítványéval megegyező legfelső szinttel](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

1.  Keresse meg a főtanúsítványfájlt a regisztrálni kívánt eszközön, és kattintson rá duplán.  

2.  A tanúsítvány ablakban kattintson a **tanúsítvány telepítése...**  

3.  A Tanúsítványimportáló varázslóban válassza a **Helyi számítógép**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  A Felhasználói fiókok felügyelete ablakban kattintson az **Igen**gombra.  

5.  Válassza a **Minden tanúsítvány tárolása ebben a tárolóban**lehetőséget, majd kattintson a **Tallózás**gombra.  

6.  Kattintson a **Megbízható legfelső szintű hitelesítésszolgáltatók**lehetőségre, az **OK**gombra, majd a **Tovább**lehetőségre.  

7.  Kattintson a **Befejezés** gombra.  

