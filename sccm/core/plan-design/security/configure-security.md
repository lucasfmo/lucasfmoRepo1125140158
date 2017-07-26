---
title: "A biztonság konfigurálása a System Center Configuration Managerben |} Microsoft Docs"
description: "Biztonsági beállítások a System Center Configuration Manager konfigurálása."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cf29123923436ed4cefc17c69630fc39989caeb4
ms.openlocfilehash: 0034381a7a388ddc3eda5e774f3c63d741336301
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-security-in-system-center-configuration-manager"></a>A biztonság konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a cikkben az információk használatával alakítsa ki a biztonsági beállítások a System Center Configuration Manager beállítása.  

##  <a name="BKMK_ConfigureClientPKI"></a> Beállítások konfigurálása PKI-ügyféltanúsítványokhoz  
Ha nyilvános kulcsokra épülő infrastruktúrájú (PKI) tanúsítványokat kíván használni az Internet Information Services (IIS) rendszert használó helyrendszerek ügyfélkapcsolatainál, a következő eljárás segítségével konfigurálhat beállításokat ezekhez a tanúsítványokhoz.  

#### <a name="to-configure-client-pki-certificate-settings"></a>PKI-ügyféltanúsítvány beállításainak konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, válassza a **helyek**, és válassza ki a konfigurálni kívánt elsődleges helyre.  

3.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**, majd válassza a **ügyfélszámítógép-kommunikáció** lapon.  

    Ez a lap csak elsődleges helyeknél érhető el. Ha nem látja az **Ügyfélszámítógép-kommunikáció** fület, ellenőrizze, hogy nem központi felügyeleti helyhez vagy másodlagos helyhez csatlakozott-e.  

4.  Válasszon **csak HTTPS** Ha azt szeretné, hogy a helyhez hozzárendelt mindig PKI-ügyféltanúsítványt használni, amikor IIS-t használó helyrendszerekhez csatlakoznak. Másik lehetőségként válasszon **HTTPS vagy HTTP** , ha nem írja elő az ügyfelek PKI-tanúsítványok számára.  

5.  Ha úgy döntött, hogy **HTTPS vagy HTTP**, válassza a **nyilvános kulcsokra épülő infrastruktúra ügyféltanúsítvány használata (ügyfél-hitelesítési képesség) Ha van ilyen** Ha azt szeretné, hogy PKI-ügyféltanúsítvány használható HTTP-kapcsolatoknál. Az ügyfélszámítógép ezt a tanúsítványt fogja használni önaláírt tanúsítvány helyett önmaga hitelesítéséhez a helyrendszereknél. Ez a beállítás automatikusan van kiválasztva, ha úgy dönt, **csak HTTPS**.  

    Amikor a rendszer észleli az ügyfélszámítógépeket az interneten, vagy ezek kizárólag internetes ügyfélfelügyeletre vannak beállítva, mindig PKI-ügyféltanúsítványt fognak használni.  

6.  Válasszon **módosítás** beállításához a választott tanúsítványkijelölési módszerének amikor egynél több érvényes PKI-ügyféltanúsítvány érhető el egy ügyfélnél, és válassza a **OK**.  

    Az ügyféltanúsítvány kijelöléséről kapcsolatban bővebben lásd: [PKI-ügyféltanúsítvány kiválasztásának tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

7.  Az ügyfeleknél jelölje be négyzetüket vagy törölje a négyzet jelölését a visszavont tanúsítványok listájának (CRL) ellenőrzéséhez.  

    További információ a CRL ügyfelek-ellenőrzésének engedélyezéséről: [PKI-tanúsítványok visszavonásának tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

8.  Ha az ügyfelek kell adnia a megbízható legfelső szintű hitelesítésszolgáltató (CA) tanúsítványait, válassza ki a **beállítása**, importálja a legfelső szintű CA tanúsítványfájlokat, és válassza a **OK**.  

    Ezzel a beállítással kapcsolatban bővebben lásd: [a nyilvános kulcsokra épülő infrastruktúra megbízható főtanúsítványok és a Tanúsítványkibocsátók listájának tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs).  

9. Válasszon **OK** az a hely tulajdonságai párbeszédpanel bezárásához.  

Ismételje meg ezt az eljárást a hierarchiában található összes elsődleges helyre vonatkozóan.  

##  <a name="BKMK_ConfigureSigningEncryption"></a>Aláírás és titkosítás konfigurálása  
Adja meg a legbiztonságosabb aláírási és titkosítási beállításokat a helyrendszerekhez, amelyeket a hely összes ügyfélszámítógépe támogat. Ezek a beállítások különösen akkor fontosak, ha lehetővé teszi az ügyfelek számára önaláírt tanúsítványok használatát a helyrendszerekkel való HTTP alapú kommunikációnál.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>Aláírás és titkosítás konfigurálása adott helyhez  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, válassza a **helyek**, és válassza ki a konfigurálni kívánt elsődleges helyre.  

3.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**, majd válassza a **aláírás és titkosítás** lapon.  

    Ez a lap csak elsődleges helyeknél érhető el. Ha nem látja az **Aláírás és titkosítás** fület, ellenőrizze, hogy nem központi felügyeleti helyhez vagy másodlagos helyhez csatlakozott-e.  

4.  Adja meg az aláírási és titkosítási beállításait, és válassza **OK**.  

    > [!WARNING]  
    >  Ne adja meg **SHA-256 megkövetelése** nélkül első ellenőrzését, amely hozzárendelhető a hely összes ügyfélszámítógép támogatja ezt a kivonatoló algoritmust, vagy rendelkeznek érvényes PKI ügyfél-hitelesítési tanúsítványt. Előfordulhat, hogy frissítéseket vagy gyorsjavításokat kell telepíteni az ügyfeleken az SHA-256 támogatásához. A Windows Server 2003 SP2 rendszert futtató számítógépeken például a [938397-es számú tudásbáziscikk](http://go.microsoft.com/fwlink/p/?LinkId=226666)által ismertetett gyorsjavítást kell telepíteni.  
    >   
    >  Ha ezt a beállítást, és az ügyfelek nem támogatják az SHA-256, és önaláírt tanúsítványokat használ, a Configuration Manager elutasítja ezeket. Ebben az esetben az SMS_MP_CONTROL_MANAGER összetevő az 5443 azonosítójú üzenetet naplózza.  

5.  Válasszon **OK** bezárásához a **tulajdonságok** párbeszédpanel a helyhez.  

Ismételje meg ezt az eljárást a hierarchiában található összes elsődleges helyre vonatkozóan.  

##  <a name="BKMK_ConfigureRBA"></a> Szerepköralapú felügyelet konfigurálása  
A szerepkör alapú felügyelet biztonsági szerepköröket, biztonsági hatóköröket és hozzárendelt gyűjteményeket használ vegyesen felügyeleti hatókör definiálásához az egyes rendszergazda felhasználók számára. Egy felügyeleti hatóköre kiterjed azokra a objektumokat, amelyeket a rendszergazda felhasználók megtekinthetnek a Configuration Manager konzolon, és azokat az objektumokat, amelyek a rendszergazda felhasználó rendelkezik jogosultsággal kapcsolatos feladatokat. A szerepkör alapú felügyeleti beállítások az adott hierarchia minden helyére érvényesek.  

Az alábbi hivatkozások vonatkozó szakaszaihoz vezetnek elő a [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../../core/servers/deploy/configure/configure-role-based-administration.md) cikk:  

-   [Egyéni biztonsági szerepkörök létrehozása](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [Biztonsági szerepkörök konfigurálása](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [Az objektum biztonsági hatókörök konfigurálása](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [Gyűjtemények konfigurálása biztonság kezeléséhez](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [Új rendszergazda felhasználó létrehozása](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [Egy rendszergazda felhasználó felügyeleti hatókörének módosítása](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  Saját felügyeleti hatóköre határozza meg azokat az objektumokat és beállításokat, amelyeket hozzárendelhet, amikor szerepkör alapú felügyeletet konfigurál másik rendszergazda felhasználó számára. További információ a szerepköralapú felügyelet tervezéséről: [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../../core/understand/fundamentals-of-role-based-administration.md).  

##  <a name="BKMK_ManageAccounts"></a> A Configuration Manager által használt fiókok kezelése  
A Configuration Manager Windows fiókok számos különböző feladat és felhasználás esetén támogatja.  

Az alábbi eljárással nézet fiókok vannak konfigurálva a különböző feladatokhoz, és kezelheti a jelszavát, amelyet a Configuration Manager használ az egyes fiókok számára.  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>A Configuration Manager által használt fiókok kezelése  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **biztonsági**, és válassza a **fiókok** a Configuration Manager konfigurált fiókok megtekintéséhez.  

3.  Egy Configuration Manager alkalmazáshoz konfigurált fiók jelszavának módosításához válassza ki a fiókot.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Válasszon **beállítása** megnyitásához a **Windows felhasználói fiók** párbeszédpanel mezőbe, majd adja meg a Configuration Manager által a fiókhoz használandó új jelszót.  

    > [!NOTE]  
    >  A megadott jelszónak egyeznie kell az Active Directory - felhasználók és számítógépek felügyeleti eszközben a fiókhoz megadott jelszóval.  

6.  Válasszon **OK** a művelet elvégzéséhez.  

