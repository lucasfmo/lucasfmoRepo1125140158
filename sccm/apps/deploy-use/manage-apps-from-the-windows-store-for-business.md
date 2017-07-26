---
title: "Alkalmazások kezelése a Windows áruházból származó vállalati |} Microsoft Docs"
description: "Kezelése és a vállalati Windows áruházból származó alkalmazások telepítése a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 3/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: f2d9da1c584f78e27e84b7f55e7ffe4dd052a27c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="manage-apps-from-the-windows-store-for-business-with-system-center-configuration-manager"></a>A Vállalati Windows Áruházban vásárolt alkalmazások felügyelete a System Center Configuration Managerrel
A [vállalati Windows áruház](https://www.microsoft.com/business-store) hol található, és Windows alkalmazásokat vásárolhat a szervezete számára egyenként vagy mennyiségi. Ha összekapcsolja az áruházat a Configuration Manager, szinkronizálhatja a vásárolt és a Configuration Managerben, ezeket a Configuration Manager konzolon megtekintheti, és azok meg, mint bármilyen más alkalmazást az alkalmazások listáját.


## <a name="online-and-offline-apps"></a>Online és offline alkalmazások

A vállalati Windows áruház alkalmazás két típusokat támogatja:

- **Online** – a licenc típusa van szükség a felhasználók és eszközök az áruházhoz csatlakozást a alkalmazást és annak licencével. Windows 10-eszközök Azure Active Directory-tartományhoz kell lennie.
- **Kapcsolat nélküli** - szervezetek gyorsítótárazásával alkalmazások és licencek közvetlenül belül a helyszíni központi telepítése hálózati, a tároló csatlakozik, vagy egy internetkapcsolattal rendelkező nélkül.

[További](https://technet.microsoft.com/itpro/windows/whats-new/windows-store-for-business-overview?f=255&MSPPError=-2147217396) kapcsolatban a vállalati Windows áruházból.

Windows áruház mind a Configuration Manager-ügyféllel rendelkező Windows 10-eszközökre, és (más néven a hibrid konfiguráció) a Microsoft Intune-nal regisztrált Windows 10-eszközökre is üzleti alkalmazások kezelése a Configuration Manager támogatja. A Configuration Manager a következő lehetőségeket nyújt a online és offline alkalmazások.

> [!IMPORTANT]
> Ez a funkció használatához Windows 10-eszközök kiadását kell futtatnia a 2015. November (1511-es) vagy újabb.


|Képesség|Kapcsolat nélküli alkalmazások|Online alkalmazásokhoz|
|------------|------------|------------|
|A Configuration Manager az alkalmazásadatok szinkronizálása<br>(szinkronizálásra 24 óránként)|Igen|Igen|
|A Configuration Manager-alkalmazások létrehozása az áruházbeli alkalmazások|Igen|Igen|
|Támogatja az ingyenes áruházból származó alkalmazásoknak|Igen|Igen|
|Az áruházból fizetős alkalmazások támogatása|Nem|Igen|
|Támogatja a szükséges központi telepítések a felhasználó- vagy eszközgyűjteményeibe|Igen|Igen|
|Támogatja az elérhető központi telepítések a felhasználó- vagy eszközgyűjteményeibe|Igen|Igen|
|Az áruházból-üzletági alkalmazások támogatásához alá|Igen|Igen|

Online licencelt alkalmazások telepítése Windows 10 rendszerű számítógépeken a Configuration Manager-ügyféllel, akkor futnia kell a Windows 10 Creators frissítés vagy újabb.

## <a name="deploying-online-apps-using-the-windows-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Online használata a Windows áruház a Configuration Manager-ügyfelet futtató számítógépeken az üzleti alkalmazások központi telepítéséhez
Mielőtt a teljes Configuration Manager-ügyfelet futtató számítógépeken az üzleti alkalmazások üzembe helyezése a Windows áruház, vegye figyelembe a következőket:

- Összes funkcióját, rendszerű számítógépek futnia kell a Windows 10 Creators frissítés vagy újabb.
- Számítógépek a Azure Active Directory munkahelyhez csatlakoztatott, és ugyanazt az AAD-bérlőt ahol felügyeleti eszközként a vállalati Windows áruházból regisztrálva kell lennie.
- Számítógépek jelentkezett be a beépített Rendszergazda fiókjával, ha azok nem tud hozzáférni Windows áruház üzleti alkalmazásokhoz.
- Számítógépek egy élő internetkapcsolat kell rendelkeznie a vállalati Windows áruházból.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Megjegyzések a Windows 10 korábbi verzióit futtató számítógépek
A Windows 10-es verziójánál (a Configuration Manager-ügyfél) Creators frissítés verzióját futtató számítógépeken alkalmazza az alábbi funkciókat:


- Amikor kényszeríti ki a telepítés a felhasználó által az alkalmazás, vagy a telepítési határidő elérésekor az alkalmazás telepítése vagy a szükséges központi telepítése újraértékelésének telepítés utáni:
    - Az alkalmazás "kényszeríti ki" a Windows Áruházbeli alkalmazás indításával. 
    - A végfelhasználó végre kell hajtania a telepítés az áruházból ténylegesen telepítése előtt
    - Az alkalmazás állapotát a Configuration Manager konzolon tartozik, nem sikerült a hiba: "a Windows Áruházbeli alkalmazás lett megnyitva az ügyfél PC és arra vár, hogy a felhasználó a telepítés befejezéséhez."
- A következő alkalmazás értékelési ciklus:
    - Ha az alkalmazás által a végfelhasználónak az áruházból lett telepítve, az alkalmazás tartozik-e az állapotát **siker**. 
    - Ha a végfelhasználó nem próbálta az áruházból telepítik az alkalmazást:
        - A kötelező központi telepítések megkísérli az áruház elindítani, és újra az alkalmazás telepítésének kényszerítéséhez.
        - Elérhető központi telepítések nem lesz újból kényszerített.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>További tudnivalók a a Windows 10 korábbi verzióit futtató számítógépeken:

- Nem lehet telepíteni az üzletági alkalmazások a vállalati Windows áruházban
- Az áruházból fizetős alkalmazások telepítésekor a végfelhasználók felkérik jelentkezzen be a tároló és vásároljon az alkalmazás saját magukat.
- Ha letiltása hozzáférést egy csoportházirend a Windows áruház fogyasztó verziója legyen telepítve, a vállalati Windows áruházban központi telepítések nem fog működni, akkor is, ha a vállalati Windows áruházból engedélyezve van.


## <a name="set-up-windows-store-for-business-synchronization"></a>Üzleti szinkronizálási Windows áruház beállítása

**Az Azure Active Directoryban regisztrálja a Configuration Manager "Web Application and/or Web API" felügyeleti eszközként. Ekkor kap egy ügyfél-Azonosítót, amely később szüksége lesz.**
1. Az Active Directory csomópontjában [https://manage.windowsazure.com](https://manage.windowsazure.com), válassza ki az Azure Active Directoryban, majd kattintson a **alkalmazások** > **Hozzáadás**.
2.  Kattintson a **a szerveztem által fejlesztett alkalmazás hozzáadása**.
3.  Adjon meg egy nevet az alkalmazásnak, válassza a **webes alkalmazás** és/vagy **Web API**, majd kattintson a **tovább** nyílra.
4.  Adja meg az URL-CÍMÉRE mind a **bejelentkezési URL-cím** és **App ID URI**. Az URL bármi lehet, és nem kell valódi címre mutatnia. Megadhat például *https://yourdomain/sccm*.
5.  Fejezze be a varázslót.

**Az Azure Active Directoryban hozzon létre egy ügyfélkulcsot a regisztrált felügyeleti eszközhöz**
1.  Jelölje ki az imént létrehozott alkalmazást, majd kattintson **konfigurálása**.
2.  A **kulcsok**, válasszon egy időtartamot a listából, és kattintson a **mentése**. Ezzel létrehoz egy új ügyfélkulcsot. Ne lépjen ki erről az oldalról, amíg sikeresen előkészítve a Configuration Manager vállalati Windows áruházból.

**A vállalati Windows áruházban konfigurálja a Configuration Manager áruházi kezelőeszközként**
1.  Nyissa meg [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) és jelentkezzen be a kérésre.
2.  Fogadja el a használati feltételeket, ha a kért.
3.  A **kezelőeszközök**, kattintson a **felügyeleti eszköz hozzáadása**.
4.  A **keressen rá név szerint az eszköz**, írja be a korábban létrehozott az aad-ben az alkalmazás nevét, majd kattintson a **Hozzáadás**.
5.  Kattintson a **aktiválás** imént importált alkalmazás neve mellett.
6.  Az a **kezelése > fiókadatok** lapon jelölje be **offline licencelt alkalmazások** Ha azt szeretné, hogy az offline licencelt alkalmazások vásárlását.

**A store-fiók hozzáadása a Configuration Managerhez**

1. Gondoskodjon arról, hogy legalább egy alkalmazást a vállalati Windows áruházban vásárolt. A a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **Cloud Services**, majd kattintson a **vállalati Windows áruház**.
2.  A a **Home** lap a **a vállalati Windows áruházzal** csoportjában kattintson a **hozzáadása a Windows áruház-fiók üzleti**. 
3.  A bérlő azonosítója, az ügyfél-azonosító és az ügyfél kulcs hozzáadása az Azure Active Directoryból, majd fejezze be a varázslót.
4. Ha elkészült, látni fogja a beállított fiók megjelenik a **vállalati Windows áruház** lista a Configuration Manager konzolon.


## <a name="create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-app"></a>Létrehozhat és telepíthet a Windows áruházbeli alkalmazás Configuration Manager-alkalmazás.
1.  Az a **szoftverkönyvtár** a Configuration Manager konzol munkaterületén bontsa ki a **Alkalmazáskezelés**, majd kattintson a **Áruházbeli alkalmazások Licencadatai**.
2.  Válassza ki a kívánt alkalmazást, telepíti, ezt követően a a **Home** lap a **létrehozása** csoportjában kattintson a **alkalmazás létrehozása**.
Configuration Manager-alkalmazás jön létre, amely tartalmazza a Windows Áruházbeli alkalmazás. Ezután telepítheti és figyelheti az alkalmazás, mint bármely más Configuration Manager-alkalmazás.
> [!IMPORTANT]
> Az Intune-nal regisztrált eszközökhöz, központilag telepített alkalmazások elérhetők csak a felhasználóra, aki eredetileg regisztrálta az eszközt. Más felhasználók nem férhetnek hozzá az alkalmazást.

## <a name="monitor-windows-store-for-business-apps"></a>Üzletági alkalmazások Windows áruház-figyelő

A a **szoftverkönyvtár** munkaterületet, bontsa ki a **Alkalmazáskezelés**, majd kattintson a **Áruházbeli alkalmazások Licencadatai**.

Kezelheti az áruházbeli alkalmazásokra vonatkozó információk is megtekinthetők az alkalmazásnak, beleértve a nevét, a platform, majd az alkalmazás a saját licencek számát, és a licencek számát rendelkezésére.

