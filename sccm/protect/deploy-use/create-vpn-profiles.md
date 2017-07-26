---
title: "Hozzon létre VPN-profilok a System Center Configuration Managerben |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager VPN-profilok létrehozásához."
ms.custom: 
ms.date: 4/19/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: 15
author: lleonard-msft
caps.handback.revision: 0
ms.author: alleonar
ms.manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7a6c89254d01f4074e5c170b20338686178ebdd3
ms.openlocfilehash: 359fcfd9754fb5c81763bc44cac45376ea3ab0b8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>VPN-profilok létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ismerteti a különböző platformokon elérhető kapcsolattípusokat [VPN-profilok a System Center Configuration Managerben](../../protect/deploy-use/vpn-profiles.md).  

Külső VPN-kapcsolatok terjeszteni a VPN-alkalmazást a VPN-profil üzembe helyezése előtt. Nem kell telepíteni az alkalmazást, ha felhasználók csatlakoznak a VPN-hez megkísérlésekor erre kéri. Alkalmazások súgójának [telepíthet központilag alkalmazásokat a System Center Configuration Managerrel](../../apps/deploy-use/deploy-applications.md).

### <a name="create-a-vpn-profile"></a>VPN-profil létrehozása   

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **megfelelőségi beállítások** > **hozzáférés a vállalati erőforrásokhoz** > **VPN-profilok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **VPN-profil létrehozása**.  


1.  Fejezze be a **általános** lap. Vegye figyelembe a következőket:  

       - Ne használja a karakterek \\/ :*?&lt; > &#124; vagy a szóköz karakter a VPN-profil neve. A Windows Server rendszer VPN-profilja nem támogatja ezeket a karaktereket.  

       -   Válassza ki **egy meglévő VPN-profil importálása fájlból** (Windows 8.1 és Windows RT csak) XML-fájlba exportált VPN-profil adatainak importálásához.  

1.  Az a **kapcsolat** csoportjában adja meg:  

    -   **Kapcsolat típusa**: Válassza ki a VPN-kapcsolat típusát. A következő táblázat kapcsolattípusok közül választhat.  

    -   **Kiszolgálólista**: Adjon hozzá egy új kiszolgálót a VPN-kapcsolathoz való használatra. A kapcsolat típusától függően egy vagy több VPN-kiszolgálók hozzáadása, és adja meg az alapértelmezett kiszolgálót.  

        > [!NOTE]  
        >  Az iOS rendszerrel működő eszközök nem támogatják több VPN-kiszolgáló használatát. Ha több VPN-kiszolgálót konfigurál, és aztán iOS eszközön hajtja végre a VPN-profil központi telepítését, az eszköz csak az alapértelmezett kiszolgálót fogja használni.  

     Ez a táblázat kapcsolattípusokat lehetőséget biztosít. További információt a VPN-kiszolgáló dokumentációjában talál.

| &nbsp;&nbsp;A beállítás&nbsp;&nbsp; | További információ | &nbsp;&nbsp;Kapcsolat&nbsp;típusa&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**Tartomány**     |A használni kívánt hitelesítési tartomány. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportosítása.|Pulse Secure|    
|**Szerepkör**        |A felhasználói szerepkör, amely hozzáfér ehhez a kapcsolathoz. |Pulse Secure|  
|**Bejelentkezési csoport vagy tartomány** |A bejelentkezési csoportnak vagy való csatlakozáshoz használni kívánt tartomány neve.|Dell SonicWALL Mobile Connect|  
|**Ujjlenyomat**  |Karakterlánc, például "Contoso Ujjlenyomatkód", hogy a VPN-kiszolgáló megbízhatóságának ellenőrzésére használt.<br /><br /> Az ujjlenyomatok:<br /><br /> – Elküldhetők az ügyfélprogramnak, így az tudni fogja, hogy megbízhat-e az azonos ujjlenyomatot adó kiszolgálókban a csatlakozáskor.<br /><br /> – Ha az eszköz még nem rendelkezik ujjlenyomattal, akkor fogja kérni a felhasználót, hogy bízzon meg a VPN-kiszolgálóban, amelyhez csatlakozik, miközben megjeleníti az ujjlenyomatot (a felhasználó manuálisan ellenőrizheti az ujjlenyomatot, majd **megbízhatósági** csatlakozni).|Check Point Mobile VPN|  
|**Az összes hálózati forgalom elküldése a VPN-kapcsolaton keresztül** |Ha ez a lehetőség nincs bejelölve, megadhat további útvonalakat a csatlakozáshoz ( **Microsoft SSL (SSTP)**, **Automatikus Microsoft**, **IKEv2**, **PPTP** és **L2TP** kapcsolattípusok esetében). Ez a módszer vegyes vagy VPN-alagútkezelés néven is ismert.<br /><br /> Csak a vállalati hálózat kapcsolatainak küldése történik VPN-alagúton keresztül. Az interneten megtalálható erőforrásokhoz való csatlakozás esetén a program nem használ VPN-alagutat. |Összes|  
|**Kapcsolatspecifikus DNS-utótag** |A kapcsolat kapcsolatspecifikus tartománynévrendszer (DNS) utótag.|– Microsoft SSL (SSTP)<br /><br /> – Microsoft Automatic<br /><br /> – IKEv2<br /><br /> – PPTP<br /><br /> – L2TP|  
|**VPN mellőzése a vállalati Wi-Fi hálózat használatakor**  |A VPN-kapcsolat nem használható, amikor az eszköz a vállalati Wi-Fi hálózathoz csatlakozik.|– Cisco AnyConnect<br /><br /> – Pulse Secure<br /><br /> – F5 Edge Client<br /><br /> – Dell SonicWALL Mobile Connect<br /><br /> – Check Point Mobile VPN<br /><br /> – Microsoft SSL (SSTP)<br /><br /> – Microsoft Automatic<br /><br /> – IKEv2<br /><br /> – L2TP|  
|**A VPN megkerülése otthoni Wi-Fi hálózathoz való csatlakozáskor**  |A VPN-kapcsolat nem használható, amikor az eszköz otthoni Wi-Fi hálózathoz csatlakozik.|Összes|  
|**Alkalmazásonkénti VPN (iOS 7 és újabb, Mac OS X 10.9 és újabb rendszeren)** |A VPN-kapcsolat társítson egy iOS-alkalmazást úgy, hogy a kapcsolatot fogja megnyitni az alkalmazás futtatásakor. A VPN-profilt a telepítéskor társíthatja egy alkalmazással.|– Cisco AnyConnect<br /><br /> – Pulse Secure<br /><br /> – F5 Edge Client<br /><br /> – Dell SonicWALL Mobile Connect<br /><br /> – Check Point Mobile VPN|  
|**Egyéni XML (nem kötelező)** |Adja meg a VPN-kapcsolatot konfiguráló egyéni XML-parancsokat.<br /><br /> Példák:<br /><br /> **Pulse Secure**esetében:<br /><br /> **&lt;Pulse-schema ><br /> &nbsp; &lt;isSingleSignOnCredential > true&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema >**<br /><br /> **CheckPoint Mobile VPN**esetében:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; port = "443" name = "CheckPointSelfhost" <br /> &nbsp; sso = "true" <br /> &nbsp; debug = "3"<br />/>**<br /><br /> **Dell SonicWALL Mobile Connect**esetén:<br /><br /> **&lt;MobileConnect\> <br /> &nbsp; &nbsp; &lt;tömörítés\>hamis&lt;/Compression\> <br /> &nbsp; &nbsp; &lt;debugLogging\>igaz&lt;/debugLogging\> <br /> &nbsp; &nbsp; &lt;packetCapture\>hamis&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> **F5 Edge Client**esetén:<br /><br /> **&lt;F5-vpn-conf >&lt;single-sign-on-credential >&lt;/f5-vpn-conf >**<br /><br /> Az egyéni XML-parancsok írásával kapcsolatban további információt az egyes gyártók VPN-dokumentációjában talál.|– Cisco AnyConnect<br /><br /> – Pulse Secure<br /><br /> – F5 Edge Client<br /><br /> – Dell SonicWALL Mobile Connect<br /><br /> – Check Point Mobile VPN|  

> [!NOTE]  
>  Mobileszközök VPN-profilok létrehozása vonatkozó információkért lásd: [VPN-profilok létrehozása](../../mdm/deploy-use/create-vpn-profiles.md)  

Fejezze be a varázslót. Az új VPN-profil az **Eszközök és megfelelőség** munkaterület **VPN-profilok** csomópontjában jelenik meg.

### <a name="next-steps"></a>További lépések

- Külső VPN-kapcsolatok terjeszteni a VPN-alkalmazást a VPN-profil üzembe helyezése előtt. Nem kell telepíteni az alkalmazást, ha felhasználók csatlakoznak a VPN-hez megkísérlésekor erre kéri. Alkalmazások súgójának [telepíthet központilag alkalmazásokat a System Center Configuration Managerrel](../../apps/deploy-use/deploy-applications.md).

- A VPN-profil központi telepítése, lásd: [profilok a System Center Configuration Manager központi telepítése](deploy-wifi-vpn-email-cert-profiles.md).  

