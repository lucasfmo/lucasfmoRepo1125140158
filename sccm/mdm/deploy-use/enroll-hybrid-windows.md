---
title: "A System Center Configuration Manager és a Microsoft Intune Windows hibrid-eszközök kezelésének beállítása |} Microsoft Docs"
description: "A System Center Configuration Manager és a Microsoft Intune Windows-eszközök kezelésének beállítása."
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: 9
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 329de5ffb6eb1403c02cd1db634c32f045e82488
ms.openlocfilehash: 47348baeac26bfa2ad5016622fe4dbcb9f572483
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid windowsos eszközkezelés beállítása a System Center Configuration Managerrel és a Microsoft Intune-nal

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör IT-rendszergazdák megtudhatja, hogyan engedélyezheti, hogy Windows rendszerű számítógépek és mobileszközök kezelése a Configuration Manager és a Microsoft Intune segítségével a felhasználók.

## <a name="enable-windows-device-management"></a>Windowsos eszközök kezelésének engedélyezése
Számítógépek vagy mobileszközök a windowsos eszközök kezelésének engedélyezéséhez használja az alábbi lépéseket:

1.  Mielőtt bármely platformhoz regisztráció beállítása, végezze el az előfeltételeket és eljárások alapján [telepítő hibrid MDM](setup-hybrid-mdm.md).  
2.  A Configuration Manager konzol a **felügyeleti** munkaterületén válassza **áttekintése** > **Felhőszolgáltatások** > **Microsoft Intune-előfizetések**.  
3.  Kattintson a menüszalagon található **platformok konfigurálása**, majd válassza ki a Windows platform:
    - **Windows** Windows rendszerű számítógépek és laptopok, majd hajtsa végre a következő lépéseket:
      1. Az a **általános** lapra, majd a **Windows-igénylés engedélyezése** jelölőnégyzetet.
      2. Ha kódjának aláírása tanúsítványt használ, és telepíteni a vállalati portál alkalmazást, keresse meg a **kódaláíró tanúsítvány**. Eszköz felhasználók is telepíthetik a vállalati portál alkalmazást a Windows áruházból, vagy kódaláíró nélkül telepítheti az alkalmazást a vállalati Windows áruházban.
      3. Beállíthatja úgy is [üzleti beállítások a Windows Hello-](windows-hello-for-business-settings.md).
    - **Windows Phone** Windows Phone-telefonokon és táblagépeken, majd végezze el a következő lépéseket:
      1. Az a **általános** lapra, majd a **Windows Phone 8.1 és Windows 10 Mobile** jelölőnégyzetet. Windows Phone 8.0 már nem támogatott.
      2. Ha a szervezetének korlátoznia kell közvetlenül telepíteni vállalati alkalmazásokat, feltöltheti a szükséges jogkivonat vagy fájlt. Alkalmazások közvetlen telepítésének kapcsolatos további információkért lásd: [létrehozása Windows-alkalmazások](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications).
        - **Alkalmazásregisztrációs**
        - **.pfx-fájlt**
        - **Nincs** egy Symantec-tanúsítványt használ, ha megadhatja **riasztás megjelenítése a Symantec tanúsítványok lejárta előtt**.
4. A párbeszédpanel bezárásához kattintson az **OK** gombra.  Egyszerűbbé teheti a regisztrációs folyamatot a vállalati portál használatával, az eszközök regisztrálása a DNS-alias kell létrehoznia. Majd utasíthatja a felhasználókat hogyan regisztrálhatják eszközeiket.

## <a name="choose-how-to-enroll-windows-devices"></a>Válassza ki a Windows-eszközök regisztrálása

Miután a felhasználók Intune-licenceket rendelt hozzá, a Windows-eszközök regisztrálása további teendők nélkül, de hogy beléptetési megkönnyíti a felhasználók számára.

Két tényező határozza meg, hogyan egyszerűsítheti a Windows-eszközök regisztrálása:
- **Azure Active Directory Premium használ?** <br>[Prémium szintű Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) nagyvállalati mobilitási + biztonsági és egyéb licencelési tervek tartalmazza.
- **Windows-ügyfelek mely verzióit regisztrálni?** <br>Windows 10-es eszközöket automatikusan egy munkahelyi vagy iskolai fiók hozzáadásával lehet regisztrálni. A korábbi regisztrálnia kell a vállalati portál alkalmazással.

||**Prémium szintű Azure AD**|**Más AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatikus igénylés](#enable-windows-10-automatic-enrollment) |[Felhasználó regisztrálása](#enable-windows-enrollment-without-azure-ad-premium)|
|**A Windows korábbi verziói**|[Felhasználó regisztrálása](#enable-windows-enrollment-without-azure-ad-premium)|[Felhasználó regisztrálása](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10-automatikus igénylés engedélyezése

Automatikus igénylés lehetővé teszi, hogy a felhasználók vállalati tulajdonúnak vagy személyes Windows 10-es számítógépekhez és Windows 10 mobileszközök regisztrálása az Intune munkahelyi vagy iskolai fiókkal, és kezelhető, elfogadja. Egyszerű, mint a. A háttérben a felhasználó eszközét regisztrálja, és csatlakozik az Azure Active Directoryban. Regisztrálás után az eszköz Intune-nal kezeli.

**Előfeltételek**
- Az Azure Active Directory Premium előfizetést ([próba-előfizetés](http://go.microsoft.com/fwlink/?LinkID=816845))
- A Microsoft Intune-előfizetés


### <a name="configure-automatic-mdm-enrollment"></a>MDM-automatikus igénylés konfigurálása

1. Jelentkezzen be a [Azure felügyeleti portálján](https://portal.azure.com) (https://manage.windowsazure.com), és válassza ki **Azure Active Directory**.

  ![Képernyőfelvétel az Azure-portálon](../media/auto-enroll-azure-main.png)

2. Válassza ki **mobilitási (MDM- és MAM-)**.

  ![Képernyőfelvétel az Azure-portálon](../media/auto-enroll-mdm.png)

3. Válassza ki **Microsoft Intune-ban**.

  ![Képernyőfelvétel az Azure-portálon](../media/auto-enroll-intune.png)

4. Konfigurálása **MDM felhasználói hatókörében**. Adja meg, melyik felhasználói eszközök Microsoft Intune kell kezelnie. A felhasználók Windows 10-eszközök lesz automatikusan regisztrálhatja a felügyelethez a Microsoft Intune-nal.

    - **Egyik sem**
    - **Néhány**
    - **Minden**

   ![Képernyőfelvétel az Azure-portálon](../media/auto-enroll-scope.png)

5. Az alapértelmezett értékeket használja a következő URL-címek esetén:
    - **Mobileszköz-kezelési feltételeit használható URL-címe**
    - **MDM-felderítés URL-címe**
    - **MDM megfelelőségi URL-címe**

6. Válassza ki **mentése**.


Alapértelmezés szerint a kéttényezős hitelesítés a szolgáltatás nincs engedélyezve. Kéttényezős hitelesítés azonban ajánlott eszközök regisztrálásakor. Mielőtt kéttényezős hitelesítést igénylő ezt a szolgáltatást, egy kéttényezős hitelesítési szolgáltató konfigurálása az Azure Active Directoryban és a felhasználói fiókok, a többtényezős hitelesítés konfigurálása. Lásd: [Ismerkedés az Azure multi-factor Authentication kiszolgáló az](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Azure AD Premium nélküli Windows-igénylés engedélyezése
Engedélyezheti a felhasználók beléptethessék az eszközeiket az Azure AD Premium-automatikus igénylés nélkül. Licencek hozzárendelése után a felhasználók regisztrálhatják a munkahelyi fiók felvétele a személyes tulajdonban lévő eszközök, vagy a vállalat által birtokolt eszközök csatlakoztatása az Azure ad után. Létrehozása egy DNS alias (CNAME rekordtípus) megkönnyíti a felhasználók regisztrálhatják az eszközeiket. DNS CNAME erőforrásrekordokat létrehozása, ha a felhasználók csatlakozni, és regisztrálása az Intune-ban az Intune-kiszolgáló nevének megadása nélkül.

### <a name="create-cnames-to-simplify-enrollment"></a>Hozzon létre CNAME tudja leegyszerűsíteni a regisztrációt
Hozza létre a CNAME DNS erőforrásrekordokat a munkahelyi tartományhoz. Például ha a vállalati webhely contoso.com, akkor létrehozhat egy olyan CNAME REKORDOT a DNS-ben, amely az EnterpriseEnrollment.contoso.com webhelyről átirányítja a felhasználókat az enterpriseenrollment-s.Manage.microsoft.com címre.

Bár a CNAME DNS-bejegyzéseinek létrehozása nem kötelező, a CNAME-rekordok könnyebbé beléptetési a felhasználók számára. Nincs beléptetési CNAME rekord található, ha felhasználók megkezdésére vonatkozó manuálisan is beírhatja az MDM-kiszolgáló nevének enrollment.manage.microsoft.com.

|Típus|Gazdagép neve|A következő helyre mutat|ÉLETTARTAM|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.munkahelyi_tartomány.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 óra|

Ha egynél több egyszerű Felhasználónévi utótagot, minden egyes tartománynév egy CNAME rekordot kell létrehoznia, és mindegyiknél az EnterpriseEnrollment-s.Manage.microsoft.com címre ponton szüksége. Például, ha a felhasználók a Contoso name@contoso.com, de is name@us.contoso.com, és name@eu.constoso.com azok/UPN, e-mail, a Contoso DNS-rendszergazdai kell létrehozni a CNAME-rekordok követését.

|Típus|Gazdagép neve|A következő helyre mutat|ÉLETTARTAM|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 óra|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 óra|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 óra|

`EnterpriseEnrollment-s.manage.microsoft.com`– Támogatja az átirányítást tartomány nevéből felismert tartománynév az Intune szolgáltatásnak a levelezési tartomány neve

DNS-rekordok módosítása való terjesztése akár 72 órát is igénybe vehet. A DNS-módosítás az Intune-ban nem ellenőrizhető, amíg a DNS-rekord propagálása zajlik.

## <a name="tell-users-how-to-enroll-devices"></a>A felhasználók tájékoztatása a eszközök regisztrálása  

 Ha elvégezte a beállításokat, tudassa a felhasználókkal, hogyan regisztrálhatják eszközeiket. Lásd: [mit kell tudniuk a felhasználóknak eszközeik regisztrálásáról](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) útmutatót. Megadhatja, hogy a felhasználók [Windows-eszköz regisztrálása az Intune-ban](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Ezek az információk a Microsoft Intune és a Configuration Manager által felügyelt mobileszközökre egyaránt vonatkoznak.

> [!div class="button"]
[< Előző lépés](create-service-connection-point.md)[következő lépés >  ](set-up-additional-management.md)

