---
title: "IOS-eszközök Apple Configurator - Configuration Manager regisztrálása |} Microsoft Docs"
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
caps.latest.revision: 5
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f8242b4b454622388f45c34ba71c4148c87c27b7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>iOS-eszközök hibrid regisztrálása a Configuration Manager Apple Configurator eszközzel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Vállalatokat, amelyek vásárolnia az alkalmazottak által használt iOS-eszközök Microsoft Intune használatával kezelheti. Készítse elő a vállalati tulajdonú IOS rendszerű eszközök beléptetését, beléptetési profil konfigurálása a Configuration Manager konzolon, és exportálhatja a profil URL-CÍMÉT az Apple Configurator által használható. A regisztrációhoz az iOS-eszköz csatlakoztatása egy Mac számítógéphez egy USB-kábel, és állítsa be az Apple Configurator eszközzel készítse elő. Apple Configurator gyár állítja alaphelyzetbe az eszközt, és hozzáadja a regisztrációs profilt, hogy az eszköz regisztrálása, amikor a felhasználó először hatáskörrel azt be, és végig kell vinnie a beállítási asszisztens folyamatát.

Az alábbi eljárás az, hogy az eszközt használó hozzáférni a vállalati e-mailek és a vállalati erőforrásokhoz, mint az alkalmazások és a dátum egyetlen felhasználó dedikált iOS-eszközök ajánlott.  

## <a name="prerequisites"></a>Előfeltételek  

-   Fizikai hozzáférés iOS-eszközökhöz  

-   Az eszközök sorozatszámait - [hogyan kérhet egy iOS-sorozatszám](https://support.apple.com/en-us/HT204308)  

-   A Mac számítógép [Apple Configurator 2.0 verzióját](http://go.microsoft.com/fwlink/?LinkId=518017)  

-   USB-kábelt eszközökön történő kapcsolódáshoz a Mac számítógép  

## <a name="step-1-add-a-corporate-owned-device-enrollment-profile"></a>1. lépés: A vállalat által birtokolt eszköz beléptetési profil hozzáadása

1.  Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **minden céges eszköz** > **iOS** > **beléptetési profilok**. Kattintson a **profil létrehozása** a profil létrehozása varázsló megnyitásához. Adja meg a beállításokat a következő lapokon:  

2.  Az **Általános** lapon adja meg az alábbi adatokat:  

    -   **Név** (felhasználók számára nem látható)  

    -   **Leírás** (felhasználók számára nem látható)  

    -   **Felhasználói affinitás** – Az eszközök beléptetésének módja. A beállítási asszisztens legtöbb forgatókönyvéhez használja **Rákérdezés a felhasználói affinitásra**.  

        -   **Rákérdezés a felhasználói affinitásra**: Az eszköz tartoznia kell egy felhasználó a kezdeti beállítás során, és sikerült majd felhasználón keresztül hozzáférhet a vállalati adatokhoz és e-mailekhez.  

        -   **Nincs megadva felhasználói affinitás**: A felhasználó nem tagja az eszköz. Ezt a kapcsolatot olyan eszközök esetén alkalmazza, amelyek a helyi felhasználói adatok nélkül hajtanak végre feladatokat. A felhasználói kapcsolatot igénylő alkalmazások nem fognak működni.

    A folytatáshoz kattintson a **Tovább** gombra.  

3.  Az a **Device Enrollment Program** lapon, hagyja a **Eszközbeléptetési Program beállításainak megadása ehhez a profilhoz** jelölőnégyzet nincs bejelölve, és kattintson a **következő**.  

4.  Tekintse át az összefoglalást, és kattintson a **tovább** a beléptetési profil létrehozásához. A **Bezárás** gombra kattintva fejezze be a varázsló futtatását. Most már készen áll IMEI-számokkal vagy sorozatszámokat a regisztrálni kívánt eszközök hozzáadásához.  

## <a name="step-2-predeclare-devices-to-enroll-with-setup-assistant"></a>2. lépés: Eszközök regisztrálása a beállítási asszisztens előzetes deklarálása

Ebben a lépésben meg (imei-Azonosítót vagy sorozatszámot) hardver azonosítók listájának megadásával, a vállalat által birtokolt eszközök előzetes deklarálása.

További információkért lásd: [sorozatszámú IMEI- és IOS rendszerű eszközök előzetes deklarálása](predeclare-devices-with-hardware-id.md). Ha ez a feladat befejezése után térjen vissza ezen a lapon a következő lépéssel folytatja.

## <a name="step-3-export-the-profile-to-deploy-to-ios-devices"></a>3. lépés: IOS-eszközökre telepíteni kívánt profil exportálása

1.  Nyissa meg a Configuration Manager konzol **eszközök és megfelelőség** > **áttekintése** > **minden céges eszköz** > **iOS** > **beléptetési profilok**.

2.  Válassza ki a mobileszközökre, és kattintson a regisztrálási profil **exportálása...** .

3.  Másolja ki és mentse a **profil URL-Címének** szerkesztheti egy fájlban.   

4.  Apple Configurator 2 támogatásához a 2.0-s profil URL-CÍMÉT kell szerkeszteni. Cserélje le az URL-cím a következő részét:  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     a  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  Mentse a módosított profil URL-CÍMÉT. A regisztrációs profil URL-CÍMÉT az Apple Configurator eszközbe az hozzáadandó fogja használni a [következő szakasz](#step-4-prepare-the-device-with-apple-configurator).  

> [!NOTE]
> A beléptetési profil URL-címe az exportálásától számított két hétig érvényes. Két hét után kell exportálnia az iOS-eszközök regisztrálása egy új URL-címet.

## <a name="step-4-prepare-the-device-with-apple-configurator"></a>4. lépés: Az eszköz előkészítése az Apple Configurator

Felkészülés az iOS-eszközök beléptetését, minden eszköz csatlakozni egy Mac számítógéphez, majd töltse fel a beléptetési profilt.  

> [!WARNING]  
>  Apple Configurator törli, és alaphelyzetbe állítja az eszközöket a gyári beállításokat.  

1.  A Mac számítógépen nyissa meg a **az Apple Configurator 2**.  

2.  A menüsávban kattintson **az Apple Configurator 2** > **beállítások**.  

2.  A beállítások ablaktáblájában jelölje ki **kiszolgálók** , és kattintson a "+" szimbólumra az MDM-kiszolgáló varázsló indítása a bal oldali panel alatt. Kattintson a **Tovább** gombra.  

3.  Adja meg a **neve** és **regisztrációs URL-CÍMÉT** megtakarított [korábbi](#step-3-export-the-profile-to-deploy-to-ios-devices). Kattintson a **Tovább** gombra.  

   > [!NOTE]
   > Ha az Apple TV megbízhatósági profil követelményekkel kapcsolatos figyelmeztetést kap, nyugodtan megszakíthatja a **Trust Profile** beállítást a szürke "X" gombra kattintva. A tanúsítvány rögzítésére vonatkozó figyelmeztetést is nyugodtan figyelmen kívül hagyhatja.

   A folytatáshoz kattintson a **következő** gombokat a varázsló befejezéséig.  

4.  Az a **kiszolgálók** ablaktáblában kattintson melletti "Szerkesztés" az új kiszolgáló profilja. Győződjön meg arról, hogy a regisztrációs URL-CÍMÉT pontosan megegyezik-e a korábban beírt URL-cím. Adja meg újra az URL-címet, ha más, és kattintson a **mentése**.  

5.  A Mac számítógép egy iOS-eszköz csatlakozni, USB-kábellel.  

  > [!WARNING]  
  >  Ez a folyamat eszközök visszaállítja a gyári beállításokat. Az eszköz csatlakoztatása előtt állítsa alaphelyzetbe az eszközt, és kapcsolja be. Az ajánlott eljárás szerint az eszköz legyen az üdvözlő képernyőt folytatása előtt.  

6.  Kattintson a **előkészítése**. Az a **iOS eszköz előkészítése** ablaktáblán válassza előbb **manuális**, és kattintson a **következő**.  

7.  Az a **az MDM-kiszolgáló regisztrálása** ablaktáblában jelölje ki a kiszolgáló nevét, a létrehozott, és kattintson a **következő**.  

9. A a **hozzon létre egy szervezet** ablaktáblán válassza ki a **szervezet** vagy hozzon létre új szervezetet, majd **következő**.  

10. Az a **iOS beállítási asszisztens konfigurálása** ablaktáblán válassza ki a felhasználóra, és kattintson lépéseket **előkészítése**. Ha a rendszer kéri, hitelesítés bizalmi kapcsolat beállításainak frissítése.  

11. Befejezésekor leválaszthatja az USB-kábelt.  

Ismételje meg ezeket a lépéseket minden olyan eszközre, készítse elő a beléptetési szeretné.

## <a name="step-5-distribute-devices"></a>5. lépés: Eszközök terjesztése

Az eszközök most már készen állnak a vállalati beléptetésre. Kapcsolja ki az eszközöket, és ossza ki őket a felhasználóknak. Ha az eszköz be van kapcsolva, beállítási asszisztens fogja indítani és kéri a felhasználót a munkahelyi vagy iskolai fiókjuk a regisztráció megkezdéséhez.

