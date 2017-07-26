---
title: "Az eszköz beléptetési Program (DEP) – a Configuration Manager iOS-eszközök regisztrálása |} Microsoft Docs"
description: "IOS-eszközök hibrid telepítések esetén a Configuration Managerben az Intune Eszközregisztrációs Program (DEP) regisztrációjának engedélyezéséhez."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: 9
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 5b5eadd7b4026eae59acceaef43cdacd7a33d3ac
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>iOS-eszköz beléptetési Program (DEP) regisztráció hibrid telepítések esetén a Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A vállalatok vásárolhat iOS-eszközök az Apple eszköz beléptetési program keresztül, és kezelheti azokat a Microsoft Intune használatával. A cégek csak azt követően tudják kezelni a munkahelyi iOS-eszközeiket az Apple eszközbeléptetési programjával (DEP), hogy regisztrálják magukat a programban az Apple által megkövetelt módon, és a programon keresztül megvásárolják az eszközöket. A folyamat részletei a következő webhelyen érhetők el:  [https://deploy-tel.apple-tel.com](https://deploy.apple.com)-tel. A program előnyei közé tartozik a beavatkozás nélküli telepítés anélkül, hogy az eszközöket csatlakoztatnia kellene egy számítógép USB-portjához.  

 Mielőtt a munkahelyi iOS-eszközöket regisztrálni lehetne a DEP programban, DEP-jogkivonatot kell vásárolni az Apple-től. Ez a token lehetővé teszi az Intune szinkronizálja a DEP-ben résztvevő, vállalat által birtokolt eszközöket. Azt is lehetővé teszi, hogy az Intune feltöltse a regisztrációs profilokat az Apple-nek, és eszközöket rendeljen az egyes profilokhoz.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>iOS-eszközök Apple DEP-regisztrációja  
 A következő eljárások azt ismertetik, hogyan adhatja meg a vállalat által birtokolt eszközöket az Intune által kezelt Apple DEP keretében vásárolt iOS-eszközök. Amikor a felhasználó első megoldásaira épül fel az eszköz az fogadja a DEP-felügyeleti profilt, és futtassa a Telepítősegédet és vonja felügyelet.  

###  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>A Configuration Managerben az Intune-nal DEP-regisztráció engedélyezése  

1.  **iOS-eszközök kezelésének megkezdése a Configuration Managerrel**   
    IOS-alapú eszköz beléptetési Program (DEP) eszközök igényléséhez előtt el kell végeznie a [hibrid mobileszköz-kezelés beállítása](../../mdm/deploy-use/setup-hybrid-mdm.md) beleértve [támogatásához az IOS-eszközök regisztrálása lépéseket](../deploy-use/enroll-hybrid-ios-mac.md).

2.  **DEP-jogkivonatkérelem létrehozása**   
    A Configuration Manager konzolon a a **felügyeleti** munkaterületet, bontsa ki a **Hierarchiakonfiguráció**, bontsa ki a **Cloud Services**, és kattintson **Microsoft Intune-előfizetések**. Kattintson a **Kezdőlap** lapon a **DEP-jogkivonatkérelem létrehozása** elemre, a **Tallózás** gombra kattintva adja meg a kérelem letöltési helyét, és kattintson a **Letöltés**elemre. Mentse a PEM-fájlt a helyi gépre. Ezzel a PEM-fájllal megbízható jogkivonatot (.p7m) kérhet az Apple Device Enrollment Program portálról.  

3.  **Az eszközbeléptetési program jogkivonatának beszerzése**   
    Nyissa meg a [Device Enrollment Program portált](https://deploy.apple.com) (https://deploy.apple.com), és jelentkezzen be a vállalati Apple ID-vel. A későbbiekben ezt az Apple ID-t kell használnia a DEP-token megújításához.  

    1.  A [Device Enrollment Program portált](https://deploy.apple.com)válassza a **Device Enrollment Program** > **Manage Servers**(Kiszolgálók kezelése) lehetőséget, és kattintson az **Add MDM Server**-tel.  

    2.  Töltse ki az **MDM Server Name**(Kiszolgálók kezelése) lehetőséget, és kattintson az **Next**-tel. A kiszolgálónév az MDM-kiszolgáló azonosítására szolgál, Nincs a nevét vagy az Intune-ban vagy a Configuration Manager-kiszolgáló URL-CÍMÉT.  

    3.  A **Add < kiszolgálónév\>**  párbeszédpanel. Kattintson a **Choose File…** (Fájl kiválasztása) elemre, és töltse fel az előző lépésnél létrehozott -tel.pem-fájlt, majd kattintson a **Next**-tel.  

    4.  A **Add < kiszolgálónév\>**  párbeszédpanelen megjelenik egy **Your Server Token** hivatkozásra. Töltse le a kiszolgálói jogkivonatfájlt (-tel.p7m) számítógépre, és kattintson a **Done**-tel.  

     A tanúsítványfájl (.p7m) segítségével bizalmi kapcsolatot hozhat létre az Intune és az Apple DEP-kiszolgálói között.  

4.  **DEP-jogkivonat hozzáadása a Configuration Managerhez**   
    A Configuration Manager konzolon a a **felügyeleti** munkaterületet, bontsa ki a **Hierarchiakonfiguráció** kattintson **Microsoft Intune-előfizetések**. Kattintson a **Platformok konfigurálása** elemre a **Kezdőlap** lapon, majd kattintson az **iOS**elemre. Válassza az **Eszközbeléptetési program engedélyezése**lehetőséget, a Tallózás gombra kattintva keresse meg a .p7m kiterjesztésű tanúsítványfájlt, kattintson a **Megnyitás**, majd a **Feltöltés**elemre, végül pedig az **OK**gombra.  

#### <a name="set-up-enrollment-for-apple-device-enrollment-program-dep-ios-devices"></a>Az Apple eszköz beléptetési Program (DEP) iOS-eszközök regisztrálásának beállítása  

1.  **Vállalati Eszközregisztrációs szabályzat hozzáadása**   
    A Configuration Manager konzolon a a **eszközök és megfelelőség** munkaterületen bontsa ki **áttekintése**, bontsa ki a **minden vállalati tulajdonú eszközök**, bontsa ki a **iOS**, és kattintson **beléptetési profilok**. A **Kezdőlap** lap **Profil létrehozása** elemére kattintva nyissa meg a Profil létrehozása varázslót. Adja meg a beállításokat a következő lapokon:  

    1.  On the **Általános** lapon adja meg a következő adatokat, majd kattintson a **Next**-tel.  

        -   **Név** – Az eszközbeléptetési profil neve. (A felhasználók ezt nem látják)  

        -   **Leírás** -az eszközregisztrációs profil leírása. (A felhasználók ezt nem látják)  

        -   **Felhasználói affinitás** – Az eszközök beléptetésének módja. Lásd: [felhasználókapcsolat a hibrid felügyelt eszközöket a Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

            -   **Rákérdezés a felhasználói affinitásra**: Az eszköz tartoznia kell egy felhasználó a kezdeti beállítás során, és sikerült majd felhasználón keresztül hozzáférhet a vállalati adatokhoz és e-mailekhez.  Felhasználói affinitást a DEP programmal kezelt olyan eszközökhöz kell beállítani, amelyek a felhasználókhoz tartoznak és a vállalati portált kell használniuk (például alkalmazások telepítéséhez).  

            > [!NOTE]
            > A felhasználói affinitással DEP az AD FS WS-Trust 1.3 felhasználónév/Mixed végpont engedélyezni kell a felhasználói jogkivonat kéréséhez szükséges.

            -   **Nincs megadva felhasználói affinitás**: Az eszköz nem áll a felhasználóhoz. Ezt a kapcsolatot olyan eszközök esetén alkalmazza, amelyek a helyi felhasználói adatok nélkül hajtanak végre feladatokat. A felhasználói kapcsolatot igénylő alkalmazások nem fognak működni.  
             ![Képernyőfelvétel a DEP-profil nevét, leírását és felhasználókapcsolat kérése](../media/dep-general.png)

    2.  Az a **beléptetési Program eszközbeállítások** lapon adja meg a következő adatokat, és kattintson a **tovább**.  

        -   **Részleg**: Ez az információ akkor jelenik meg, amikor a felhasználók koppintson a "Kapcsolatos konfiguráció" az aktiválás során.  

        -   **Ügyfélszolgálat telefonszáma**: Jelenik meg, ha a felhasználó kattint a **kell** gomb az aktiválás során.
       ![Képernyőkép a DEP-profilt hozzárendelése iOS-eszközök](../media/dep-settings.png)

        -   **Előkészítés módja**: Ez az állapot aktiválás közben állítja be, és változtathatók gyári alaphelyzetbe állíthatja az eszközt:  

            -   **Felügyeletlen** – korlátozott felügyeleti funkciók  

            -   **Felügyelt** – több felügyeleti funkciót engedélyez, és alapértelmezés szerint letiltja az aktiválási zár  

        -   **Beléptetési profil zárolása ehhez az eszközhöz**: Ez az állapot aktiválás közben állítja be, és a gyári beállítások visszaállítása nélkül nem módosítható.  

            -   **Tiltsa le a** -lehetővé teszi, hogy a felügyeleti profil eltávolítsa őket a **beállítások** menü  

            -   **Engedélyezése** -(igényel **előkészítés módja** = **felügyelt**) letiltja a felügyeleti profil eltávolítását lehetővé tévő iOS-beállítások  

    3.  A **Beállítási asszisztens** lapon adja meg az iOS beállítási asszisztensét meghatározó beállításokat (ez az asszisztens jelenik meg az eszköz első bekapcsolásakor), és kattintson a **Tovább**gombra. Ezek a beállítások többek között a következők:  
        -   **PIN-kód** - aktiválás közben PIN-kód kérése. A PIN-kód minden esetben szükséges, kivéve, ha az eszköz megfelelően történik, illetve elérésének ellenőrzése valamilyen más módon (pl. teljes képernyős móddal, amely korlátozza az eszközt egy alkalmazás).  
        -   **Helyalapú szolgáltatások** – Ha engedélyezve van a beállítási asszisztens kérni fogja a szolgáltatás aktiválása során,  
        -   **Visszaállítás** – Ha engedélyezve van a beállítási asszisztens az icloud tárhelyére végzett biztonsági mentés aktiválás során kérni fogja,  
        -   **Apple ID** – az Apple ID azonosító szükséges iOS App Store-alkalmazásokat, beleértve az Intune által telepített letöltéséhez. Ha engedélyezve van, iOS kérni fogja a felhasználótól az Apple ID azonosítót amikor Intune megkísérli nem azonosítóval rendelkező alkalmazások telepítése  
        -   **Feltételek és kikötések** – Ha engedélyezve van, beállítási asszisztens kéri a felhasználóktól az Apple használati feltételeinek elfogadására az aktiválás során  
        -   **Touch ID** – Ha engedélyezve van a beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja,
        -   **Apple Pay** – Ha engedélyezve van a beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja,
        -   **Nagyítás** – Ha engedélyezve van a beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja,
        -   **A Siri** – Ha engedélyezve van a beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja,  
        -   **Diagnosztikai adatok küldése az Apple** – Ha engedélyezve van a beállítási asszisztens ezt a szolgáltatást aktiválás során kérni fogja,  
        ![Képernyőkép a DEP-profilt hozzárendelése iOS-eszközök](../media/dep-setup-assistant.png)

    4.  Az a **további felügyeleti** csoportjában adja meg, hogy használható-e a USB-kapcsolaton a további felügyeleti beállításokat. Ha bejelöli **szükséges tanúsítvány**, importálnia kell az Apple Configurator felügyeleti tanúsítványt ehhez a profilhoz használandó.  Beállítása **Disallow** az iTunes vagy az Apple Configuratoron keresztüli felügyelet szinkronizálja fájlok. A Microsoft azt javasolja, hogy beállította-e **Disallow**, a további konfigurációkat exportálja az Apple Configuratorból, és ezután egyéni iOS konfigurációs profil központi telepítése, nem pedig a beállítás segítségével vagy a tanúsítvány nélkül manuális központi telepítésének engedélyezése.  

        -   **Engedélyezi a** -megakadályozza, hogy az eszköz kommunikáljon (párosítás letiltása) USB-kapcsolaton keresztül  

        -   **Engedélyezése** -engedélyezi az eszköz és bármely PC vagy Mac az USB-kapcsolaton keresztüli kommunikáció  

        -   **Szükséges tanúsítvány**-lehetővé teszi, hogy a regisztrációs profilba importált tanúsítvánnyal rendelkező Mac párosítás  

2.  **DEP eszközök hozzárendelése kezelés céljából**   
    Nyissa meg a [Device Enrollment Program portált](https://deploy.apple.com) (https://deploy.apple.com), és jelentkezzen be a vállalati Apple ID-vel. Válassza a **Deployment Program** > **Device Enrollment Program** > **Manage Devices**-tel. Adja meg, hogy hogyan fogja **kiválasztani az eszközöket**(Choose Devices), adja meg az eszközinformációkat, és adja meg a részleteket az eszköz **sorozatszáma**(Serial Number) vagy **rendelésszáma**(Order Number) alapján, illetve **CSV-fájl feltöltésével**(Upload CSV File). Válassza ki, **kiszolgáló hozzárendelése** , és válassza a <*kiszolgálónév*> 3. lépésében megadott, és kattintson **OK**.  

3.  **DEP által felügyelt eszközök szinkronizálása**   
    Az a **eszközök és megfelelőség** munkaterületén válassza **minden vállalati tulajdonú eszközök** > **Predeclared eszközök**. A **Kezdőlap** lapon kattintson a **DEP-szinkronizálás**elemre. A szolgáltatás elküld egy szinkronizálási kérelmet az Apple-nek. A szinkronizálás befejeződése után megjelennek a DEP programmal kezelt eszközök.

4.  **Rendelje hozzá a DEP-profilt**<br>Az a **eszközök és megfelelőség** munkaterületén válassza **minden céges eszköz** > **iOS** > **beléptetési profilok**. Válassza ki a DEP regisztrációs profiljának, majd a a **Home** lapra, majd **eszközökhöz**. Jelölje ki az eszközöket, majd a regisztrációs profil használata kattintson **Hozzáadás**, és kattintson a **OK**.   
     ![Képernyőkép a DEP-profilt hozzárendelése iOS-eszközök](../media/dep-assign-profile.png)

5.  **Eszközök kiosztása a felhasználóknak**   
    Most már megkezdheti a céges eszközök kiosztását a felhasználóknak. Megnyílik az **Beléptetés állapota** beállításának értéke mindaddig **Nincs kapcsolat** lesz, amíg be nem kapcsolták őket, és nem futtatták az eszközt regisztráló beállítási asszisztenst. Az iOS-eszközök bekapcsolásakor a rendszer regisztrálja az eszközöket az Intune-nal való felügyelet számára.

