---
title: "A Technical Preview-ban 1607 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1607 verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 4717e0f8eef01501fb5b5790e855c476c1ca4590
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>A rendszer 1607 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1607 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="dmp_edition"></a>A Windows 10-kiadás fejlesztései házirend frissítése

Ebben a kiadásban a következő fejlesztéseken ment-e a házirend:

* A Kiadásfrissítési házirend most futtassa a Configuration Manager ügyfél mellett a Windows 10 rendszerű számítógépen regisztrált a Microsoft Intune-nal, a Windows 10 rendszerű számítógépeken használható.
* A varázsló a platformokat, amelyek kompatibilisek-e a hardver egyik a Windows 10 Professional frissíthető.

[További tudnivalók a Windows 10 Kiadásfrissítési házirend](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>Próbálja ki!

1. Az információk a [meglévő Kiadásfrissítési házirend témakör](/sccm/compliance/deploy-use/upgrade-windows-version) egy Kiadásfrissítési házirend létrehozása.
2. Ez a házirend telepítése a Configuration Manager-ügyféllel rendelkező Windows 10 rendszerű Számítógépeken.
Ha a házirend elérte a célként megadott Windows-számítógépet, a számítógép két órán belül újraindul a frissítés alkalmazásához. Jelenleg akkor nem tudja letiltani az ezt az újraindítást. Győződjön meg arról értesíti azokat a felhasználókat telepítette a házirendet, vagy a házirendet, a felhasználók futtatható ütemezése munkaidőn.

### <a name="known-issue-with-this-release"></a>Ebben a kiadásban ismert problémái
A Configuration Manager-ügyfél beállításainak, előfordulhat, hogy látja beállításainak **Kiadásfrissítési**. Ebben a kiadásban ezek a beállítások nincsenek működési. Kövesse az utasításokat egy újabb verzióra frissítése a Windows 10 fent megadott.

## <a name="customizable-branding-for-software-center-dialogs"></a>Testreszabható védjegyezés a Software Center-párbeszédpanelekhez

A Szoftverközpont egyéni branding jelent meg a Configuration Manager 1602-es verzióját. Technical Preview verziójában 1607 adott branding kiterjesztettük a társított párbeszédpanel, és a tálca értesítések egységesebb adhat a felhasználók a Szoftverközpontban.

### <a name="try-it-out"></a>Próbálja ki!

A Szoftverközpont egyéni arculat a következő szabályok szerint alkalmazza:

1. Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre nincs telepítve, akkor a szoftverközpont a szervezet nevét a **Számítógépügynök** ügyfélbeállítás **a Szoftverközpontban megjelenített név**. Útmutatásért lásd: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).

2. Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre telepítve van, akkor a Szoftverközpont jelenít meg a szervezet nevét és az Alkalmazáskatalógus weboldal-elérési pont helykiszolgáló-szerepkörének tulajdonságaiban megadott színt. További információkért lásd: [Alkalmazáskatalógus weboldal-elérési pontjának konfigurációs beállításait](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website).

3. Ha a Microsoft Intune-előfizetés konfigurálva, és a Configuration Manager környezethez csatlakozik, akkor a Szoftverközpont jelenít meg a szervezet neve, a színt és vállalati emblémát az Intune-előfizetés tulajdonságai. További információkért lásd: [a Microsoft Intune-előfizetés konfigurálása](/mdm/deploy-use/configure-intune-subscription).

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>Használja az azonos hálózati adapterre több PXE-hez kezdeményezett központi telepítések
Technikai előzetes verziójában 1607 történő használatakor az ethernet-adapter lemezképet több eszközön (például egy USB-ethernet-adapter több eszközön használt) egy új beállítás, amely lehetővé teszi az ethernet-adapterek hardverazonosítók is engedélyezheti. A Configuration Manager figyelmen kívül hagyja a listában, amikor PXE telepítését hajtja végre, és az ügyfél-regisztrációk hardverazonosítók.

A problémával kapcsolatos további információkért tekintse meg a [Configuration Manager OSD támogatási munkacsoportjának blogjából](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/).  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>Ismétlődő hardverazonosítók kezelése funkció engedélyezése  
1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **áttekintése** > **Felhőszolgáltatások** > **frissítés és karbantartás** > **szolgáltatásait**.
2. A kijelzőpanelen válassza ki a **kezelése ismétlődő hardverazonosítók**.
3. A a **Home** lap a **szolgáltatásait** csoportjában kattintson a **bekapcsolása**.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>A Configuration Manager figyelmen kívül hagyása hardverazonosítók hozzáadása  
1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**.
2. A **Kezdőlap** **Helyek** csoportjában kattintson a **Hierarchiabeállítások**elemre.
3. Lépjen a **Ügyféljóváhagyás és ütköző rekordok** fülre.
4. Kattintson a **Hozzáadás** a a **hardverazonosítók ismétlődő** szakasz új hardverazonosítók hozzáadása.

