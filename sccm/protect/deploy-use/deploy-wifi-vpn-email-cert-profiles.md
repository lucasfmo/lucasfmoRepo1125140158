---
title: "Wi-Fi, VPN, e-mail és a tanúsítványprofilok központi telepítése |} Microsoft Docs"
description: "Megtudhatja, hogyan telepítheti a Wi-Fi, VPN, e-mail és a System Center Configuration Managerben tanúsítványprofilok."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
caps.latest.revision: 5
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c2e3aef41e9a890d136039f85777ab07284e5c27
ms.openlocfilehash: 70372d5df13034b48f3e43b766776442f1be5823
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="deploy-profiles-in-system-center-configuration-manager"></a>A System Center Configuration Managerben profilok központi telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Profilok kell telepíteni kell egy vagy több gyűjteményt is használhatók.  

 Használja a **Wi-Fi-profil telepítése**, **VPN-profil telepítése**, **Deploy Exchange ActiveSync Profile**, vagy **Tanúsítványprofil** párbeszédpanelt, amelyen a profilok központi telepítésének konfigurálásához. A konfigurálás részeként meg kell határozni a gyűjteményt, amelyhez a profil telepítve, és adja meg, milyen gyakran legyen kiértékelve a profil megfelelőségét.  

> [!NOTE]  
>  Ha ugyanazon felhasználó számára több vállalati erőforrás-hozzáférési profilt telepít, a következő történik:  
>   
>  -   Ha egy ütköző beállítás választható értéket tartalmaz, azt a rendszer nem küldi el az eszközre.  
> -   Ha egy ütköző beállítás kötelező értéket tartalmaz, a rendszer az alapértelmezett értéket küldi el az eszközre. Ha nincs alapértelmezett érték, a teljes vállalati erőforrás-hozzáférési profil sikertelen lesz. Ha például két e-mail profilt telepít ugyanazon felhasználó számára, és az **Exchange ActiveSync host** (Exchange ActiveSync-állomás) vagy az **Email address** (E-mail cím) beállítás értékei eltérőek, mindkét e-mail profil sikertelen lesz, mivel ezek kötelező beállítások.  

> -   Tanúsítványprofilok központi telepítése előtt előbb konfigurálnia kell az infrastruktúrát, és tanúsítványprofilokat kell létrehoznia. További információ a következő témakörökben:  
>   
>  -   [Tanúsítványinfrastruktúra konfigurálása a System Center Configuration Managerben](certificate-infrastructure.md)  
> -   [Tanúsítványprofilok létrehozása a System Center Configuration Managerben](create-certificate-profiles.md)    

> [!IMPORTANT]  
>  Ha a VPN-profil központi telepítését eltávolítják, az nem törlődik az ügyféleszközökön marad. Ha el szeretné távolítani a profilt az eszközökről, ezt kézzel kell megtennie.
>   

## <a name="deploying--profiles"></a>Profilok központi telepítése  


1.  Kattintson a System Center Configuration Manager konzol **eszközök és megfelelőség**.  

2.  Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások**, bontsa ki a **hozzáférés a vállalati erőforrásokhoz**, és kattintson a megfelelő profil típusát, például a **Wi-Fi profilok**.  

3.  Profilok listájára, válassza ki a profilt, amelyet szeretne telepíteni, majd a a **Home** lap a **telepítési** csoportjában kattintson **telepítés**.  

4.  A profil központi telepítése párbeszédpanelen adja meg a következőket:  

    -   **Gyűjtemény** -kattintson **Tallózás** kattintva kiválaszthatja a gyűjteményt, ha szeretné a profilt telepíti.  

    -   **Riasztás létrehozása** -engedélyezi ezt a beállítást, konfigurálhat egy riasztást, ha a profil megfelelősége kisebb, mint a megadott százalék a megadott napon és időpontban. Azt is megadhatja, hogy kíván-e riasztást küldeni a System Center Operations Manager alkalmazásnak.  

    -   -   **Véletlenszerű késleltetés (óra)**: (Csak az egyszerű tanúsítvány-beiktatási beállítást tartalmazó tanúsítványprofilok) Megadja a késleltetést, amellyel elkerülhető a hálózati eszközök tanúsítványigénylési szolgáltatása túlzott terhelése. Az alapértelmezett érték **64** óra.  

    -   **Adja meg a megfelelőség értékelésének ütemezését ehhez <type> profil** -adja meg az ütemezést, amely szerint a központilag telepített profil ki lesz értékelve az ügyfélszámítógépeken. Az ütemezés egyszerű és egyéni is lehet.  

        > [!NOTE]  
        >  A profilt az ügyfélszámítógépek értékelik ki, amikor a felhasználó bejelentkezik.  

5.  Kattintson a **OK** a párbeszédpanel bezárásához és a központi telepítés létrehozásához.

### <a name="see-also"></a>További információ  

[Wi-Fi, VPN és e-mail profilok a System Center Configuration Manager figyelése](monitor-wifi-email-vpn-profiles.md)

[A System Center Configuration Managerben tanúsítványprofilok figyelése](monitor-certificate-profiles.md)

