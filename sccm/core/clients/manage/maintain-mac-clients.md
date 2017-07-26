---
title: "Mac rendszerű ügyfelek karbantartása |} Microsoft Docs"
description: "Karbantartási feladatok a Configuration Manager Mac rendszerű ügyfelek esetén."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3bf6651f58dc0c2aa4773f77115c3fbcd4a33221
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="maintain-mac-clients"></a>Mac rendszerű ügyfelek kezelése
*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbiakban a Mac-ügyfél eltávolítása és a tanúsítványok megújítása eljárásokat.

##  <a name="uninstalling-the-mac-client"></a>A Mac-ügyfél eltávolítása  

1.  A Mac számítógépen nyisson meg egy terminálablakot, és keresse meg a mappát tartalmazó **macclient.dmg**.  

2.  Lépjen a Tools mappára, és írja be a következő parancssort:  

     **. / CMUninstall - c**  

    > [!NOTE]  
    >  A **- c** tulajdonság arra utasítja az ügyfelet is távolítsa el az ügyfél-összeomlási naplókat, és a naplófájlok eltávolítása. Azt javasoljuk, a bizonytalanság elkerüléséhez, ha később újratelepítené az ügyfelet.  

3.  Szükség esetén manuálisan távolítsa el a Configuration Manager használt ügyfél-hitelesítési tanúsítványt, vagy vonja vissza. A CMUnistall nem távolítja el és nem vonja vissza a tanúsítványt.  

##  <a name="renewing-the-mac-client-certificate"></a>A Mac-ügyfél tanúsítványának megújítása  
 A következő eljárások valamelyikével újítsa meg a Mac-ügyfél tanúsítványát:  

-   [Tanúsítvány megújítása varázsló](#renew-certificate-wizard)  

-   [Tanúsítványának manuális megújítása](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>Tanúsítvány megújítása varázsló  

1.  Konfigurálja a következő értékeket, mint a *karakterláncok* a ccmclient.plist fájlban, amely szabályozza, amikor a tanúsítvány megújítása varázsló:  

 -   **RenewalPeriod1** -másodpercben megadva, az első megújítási időszakot mely felhasználók megújíthatják a tanúsítványt. Az alapértelmezett érték 3 888 000 másodperc (45 nap). Ne állítson be egy érték kisebb, mint 300, mint az időszak visszaáll az alapértelmezett. 

 -   **RenewalPeriod2** – Megadja másodpercben a második megújítási időszakot mely felhasználók megújíthatják a tanúsítványt. Az alapértelmezett érték 259 200 másodperc (3 nap). Ha ez az érték van konfigurálva, és nagyobb vagy egyenlő 300 másodpercnél és kisebb vagy egyenlő, mint **RenewalPeriod1**, az értéket fogja használni. Ha a **RenewalPeriod1** értéke 3 napnál több, akkor a **RenewalPeriod2**esetében az érték 3 nap lesz.  Ha a **RenewalPeriod1** értéke 3 napnál kevesebb, akkor a **RenewalPeriod2** ugyanolyan értékre lesz állítva, mint a **RenewalPeriod1**.  

 -   **RenewalReminderInterval1** -másodpercben megadva, a gyakoriság, amellyel a tanúsítvány megújítása varázsló megjelenik a felhasználóknak az első megújítási időszak alatt. Az alapértelmezett érték 86 400 másodperc (1 nap). Ha a **RenewalReminderInterval1** nagyobb 300 másodpercnél és kisebb a **RenewalPeriod1**konfigurált értékénél, akkor a konfigurált értéket használja a rendszer. Más esetben az 1 napos alapértelmezett érték lesz érvényben.  

 -   **RenewalReminderInterval2** -a másodpercben azt a gyakoriságot, amellyel a tanúsítvány megújítása varázsló megjelenik a felhasználóknak a második megújítási időszak alatt, adja meg. Az alapértelmezett érték 28 800 másodperc (8 nap). Ha a **RenewalReminderInterval2** értéke 300 másodpercnél nagyobb, kisebb vagy megegyezik a **RenewalReminderInterval1** értékével, illetve kisebb vagy megegyezik a **RenewalPeriod2**értékével, akkor a rendszer a konfigurált értéket használja. Más esetben 8 napos érték lesz érvényben.  

     **Példa:** Az az alapértelmezett értékükön, ha a tanúsítvány lejárta előtt 45 nappal a varázsló megnyitja 24 óránként.  3 nappal a tanúsítvány lejárta előtt a varázsló 8 óránként nyílik meg.  

     **Példa:** Használja a következő parancsot, vagy egy parancsfájllal állítsa az első megújítási időszakot 20 napra.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  Amikor megnyílik a tanúsítvány megújítása varázsló, a **felhasználónév** és **kiszolgálónév** mező általában ki van töltve, és a felhasználó csak a tanúsítvány megújításához jelszót adhat meg.  

    > [!NOTE]  
    >  Ha nem nyílik meg a varázsló, vagy ha véletlenül bezárja azt, kattintson a **Megújítás** elemre a **Configuration Manager** beállításlapján a varázsló megnyitásához.  

###  <a name="renew-certificate-manually"></a>Tanúsítványának manuális megújítása  
 A Mac-ügyféltanúsítvány érvényessége általában 1 év. A Configuration Manager automatikusan megújítani a felhasználói tanúsítványt, amelyet beléptetéskor kérelmez, így az alábbi eljárást a tanúsítvány megújításához manuálisan kell használni.  

> [!IMPORTANT]  
>  Ha a tanúsítvány lejár, az Mac-ügyfelet el kell távolítani és újra kell telepíteni, majd újra be kell léptetni.  

 Ez a folyamat eltávolítja az SMS-azonosítót, amely szükséges egy új tanúsítvány kérelmezéséhez ugyanahhoz a Mac számítógéphez. Amikor eltávolítja és pótolja ügyfélelőzmény, köztük a leltár tárolt ügyfél korábbi törlődik, az ügyfél a Configuration Manager konzoljáról törlése után.  

1.  Hozzon létre, és egy eszközgyűjteményt azon Mac számítógépek számára, amely kell újítaniuk a felhasználói tanúsítványok feltöltése.  

    > [!WARNING]  
    >  A Configuration Manager nem figyeli a beléptetett tanúsítvány érvényességi Mac számítógépeken. Meg kell nyomon követhető, függetlenül a Configuration Manager az ehhez a gyűjteményhez adható Mac számítógépek azonosításához.  

2.  Az **Eszközök és megfelelőség** munkaterületen indítsa el a **Konfigurációelem létrehozása varázslót**.  

3.  Az **Általános** lapon adja meg az alábbi adatokat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Típus:Mac OS X**  

4.  Az a **által támogatott platformok** lapon, győződjön meg arról, hogy a Mac OS X minden verziója van-e jelölve.  

5.  Az a **beállítások** lapon, válassza ki **új** , majd a a **beállítás létrehozása** párbeszédpanelen adja meg a következő információkat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Beállítás típusa:Parancsfájl**  

    -   **Adattípus:Karakterlánc**  

6.  Az a **beállítás létrehozása** párbeszédpanelen a **felderítési parancsfájl**, válassza a **parancsfájl hozzáadása** lehetőségre olyan parancsfájl, amely felderíti a konfigurált SMS-AZONOSÍTÓVAL rendelkező Mac számítógépeket megadásához.  

7.  A **Felderítési parancsfájl szerkesztése** párbeszédpanelen adja meg a következő héjparancsfájlt:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Válasszon **OK** bezárásához a **felderítési parancsfájl szerkesztése** párbeszédpanel megnyitásához.  

9. Az a **beállítás létrehozása** párbeszédpanelen a **szervizelési parancsfájl (nem kötelező)**, válassza a **parancsfájl hozzáadása** adhatja meg, hogy eltávolítja az SMS-AZONOSÍTÓT, a Mac számítógépeken talált parancsprogramot.  

10. A **Szervizelési parancsfájl létrehozása** párbeszédpanelen adja meg a következő héjparancsfájlt:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Válasszon **OK** bezárásához a **szervizelési parancsfájl létrehozása** párbeszédpanel megnyitásához.  

12. A varázsló **Megfelelőségi szabályok** lapján kattintson az **Új**elemre, és a **Szabály létrehozása** párbeszédpanelen adja meg a következő adatokat:  

    -   **Név:SMSID eltávolítása Mac számítógépen**  

    -   **Kiválasztott beállítás:** Válasszon **Tallózás** , és jelölje ki a korábban megadott felderítési parancsfájlt.  

    -   A **következő értékek** mezőbe írja be a következőt: **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Engedélyezze a **Futtassa a megadott szervizelési parancsfájlt, ha a beállítás nem megfelelő**beállítást.  

13. Fejezze be a Konfigurációelem létrehozása varázslót.  

14. Hozzon létre egy referenciakonfigurációt, amely tartalmazza az imént létrehozott konfigurációs elemet, és telepítse azt az 1. lépésben létrehozott eszközgyűjteményre.  

     Hozzon létre és alapkonfigurációk központi telepítése kapcsolatos további információkért lásd: [referenciakonfigurációk létrehozása a System Center Configuration Managerben](../../../compliance/deploy-use/create-configuration-baselines.md) és [központi telepítése a System Center Configuration Managerben referenciakonfigurációk](../../../compliance/deploy-use/deploy-configuration-baselines.md).  

15. Azokon a Mac számítógépeken, amelyekről el lett távolítva az SMS-azonosító, futtassa a következő parancsot új tanúsítvány létrehozásához:  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     Amikor a rendszer rákérdez, adja meg a felügyeleti fiók jelszavát a parancs futtatásához, majd adja meg az Active Directory-fiók jelszavát.  

16. A regisztrált tanúsítvány a Configuration Manager, a Mac számítógépen nyisson meg egy terminálablakot, és hajtsa végre a következő módosításokat:  

    a.  Írja be a következő parancsot: **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**  

    b.  A a **Keychain Access** párbeszédpanelen, a a **Keychains** területen válassza a **rendszer**, majd a a **kategória** területen válassza a **kulcsok**.  

    c.  Az ügyfél tanúsítványainak megtekintéséhez bontsa ki a kulcsokat. Ha az imént telepített privát kulccsal azonosította a tanúsítványt, kattintson duplán a kulcsra.  

    d.  Az a **hozzáférés-vezérlés** lapra, majd **megerősítés hozzáférés engedélyezése előtt**.  

    e.  Keresse meg a **Library/Application Support/Microsoft/CCM**, jelölje be **CCMClient**, és válassza a **Hozzáadás**.  

    f.  Válasszon **módosítások mentése** és zárja be a **Keychain Access** párbeszédpanel megnyitásához.  

17. Indítsa újra a Mac számítógépet.  


