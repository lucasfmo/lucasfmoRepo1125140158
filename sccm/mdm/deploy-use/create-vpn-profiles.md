---
title: A VPN-profilok a System Center Configuration Managerben |} Microsoft Docs
description: "VPN-profilok a System Center Configuration Managerben mobileszközökön."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: 18
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: aacd11708f9f9bd5b0a2d1b1cd6db3c60a7c0c28
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>VPN-profilokat a mobileszközökre a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

VPN-profilok használatával a System Center Configuration Manager mobileszköz-felhasználók a szervezet VPN-beállításokat telepíthet. Ezek a beállítások központi telepítésekor lecsökkentheti a vállalati hálózaton lévő erőforrások eléréséhez szükséges végfelhasználói beavatkozást.  

 Például be szeretné állítani a vállalati hálózaton lévő egyik fájlmegosztáshoz való csatlakozáshoz szükséges beállítások segítségével az iOS operációs rendszert futtató összes eszközöket. Létrehozhat egy VPN-profil csatlakoznak a vállalati hálózathoz, és ezután telepíti a profilt a hierarchiában az iOS rendszerű eszközök rendelkező felhasználók a szükséges beállításokkal. Az iOS-eszközök felhasználói látják majd a VPN kapcsolatot az elérhető hálózatok listájában, és minimális erőfeszítéssel tudnak kapcsolódni a hálózathoz.  

 VPN-profil létrehozásakor megadhat egy széleskörűen ellátható biztonsági beállításokkal. Megadhatja például, kiszolgáló-ellenőrzési és ügyfél-hitelesítési tanúsítványok, amelyek a System Center Configuration Manager tanúsítványprofilok használatával hoztak létre. További információ a tanúsítványprofilokról [Tanúsítványprofilok a System Center Configuration Managerben](../../protect/deploy-use/introduction-to-certificate-profiles.md).  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>A VPN-profilok a Configuration Manager és az Intune együttes használata esetén

 Profilokat telepíthet iOS, Android, Windows Phone és Windows 8.1-eszközökön, hogy ezek az eszközök Microsoft Intune-ban regisztrált kell. Az eszközök más platformokon is regisztrálása az Intune-hoz. Beléptetésének módjával kapcsolatos információkért lásd: [mobileszközök kezelése a Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). Az alábbi táblázatban a kapcsolat típusa, amely minden eszközplatform esetében támogatott:  

 |Kapcsolat típusa|iOS- és macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 asztali és mobil verziója|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|Igen|Igen|Nem|Nem|Nem|Nem|Igen (OMA-URI)|  
 |Pulse Secure|Igen|Igen|Igen|Nem|Igen|Igen|Igen|  
 |F5 Edge Client|Igen|Igen|Igen|Nem|Igen|Igen|Igen|  
 |Dell SonicWALL Mobile Connect|Igen|Igen|Igen|Nem|Igen|Igen|Igen|  
 |Check Point Mobile VPN|Igen|Igen|Igen|Nem|Igen|Igen|Igen|  
 |Microsoft SSL (SSTP)|Nem|Nem|Igen|Igen|Igen|Nem|Nem|  
 |Microsoft Automatic|Nem|Nem|Igen|Igen|Igen|Nem|Igen (OMA-URI)|  
 |IKEv2|Igen (egyéni házirend)|Nem|Igen|Igen|Igen|Igen|Igen (OMA-URI)|  
 |PPTP|Igen|Nem|Igen|Igen|Igen|Nem|Igen (OMA-URI)|  
 |L2TP|Igen|Nem|Igen|Igen|Igen|Nem|Igen (OMA-URI)|  

## <a name="create-vpn-profiles"></a>A VPN-profilok létrehozása
[VPN-profilok létrehozása a System Center Configuration Manager hogyan](../../protect/deploy-use/create-vpn-profiles.md) creat VPN-profilok általános információkat nyújt.

###   <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Windows 10 VPN-funkciók érhetők el, ha a Configuration Managerbe integrált Intune használata  


> [!NOTE]  
> A Windows 10 VPN-funkciók használó VPN-profil neve nem lehet Unicode vagy speciális karaktereket tartalmaz.


|Beállítás|További információ|Kapcsolat típusa|  
    |------------|----------------------|---------------------|  
    |**VPN mellőzése a vállalati Wi-Fi hálózat használatakor**|A VPN-kapcsolat nem használható, amikor az eszköz a vállalati Wi-Fi hálózathoz csatlakozik. Adja meg a megbízható hálózat nevét, amely azt határozza meg, ha az eszköz a vállalati hálózathoz csatlakozik.|Összes|  
    |**Hálózati forgalomra vonatkozó szabályok**|Állítsa be a protokollok, helyi port, távoli portok és címtartományok, amely a VPN-kapcsolat engedélyezve lesz.<br /><br /> **Megjegyzés:** Ha nem hoz létre hálózati forgalmi szabályt, minden protokollokat, portokat és címtartományokat engedélyezve lesz. Miután létrehozott egy szabályt, csak a protokollok, portok és címtartományok megadott vagy a további szabályok által használható a VPN-kapcsolatot.|Összes|  
    |**Útvonalak**|A VPN-kapcsolatot használó útvonalak. Vegye figyelembe, hogy létrehozása több mint 60 útvonalak okozhat a házirend sikertelen lesz. |Összes|  
    |**DNS-kiszolgálók**|A kapcsolat létrejötte után a VPN-kapcsolat által használt DNS-kiszolgálók.|Összes|  
    |**Alkalmazások, amelyek automatikusan csatlakoznak a VPN-hez**|Alkalmazások hozzáadása, és importálja a VPN-kapcsolatot automatikusan használó alkalmazásokat tartalmazó listáján. Az alkalmazás típusa határozza meg az alkalmazás azonosítóját. Egy asztali alkalmazások esetén adja meg az alkalmazás a fájl elérési útját. Univerzális alkalmazások esetén adja meg a csomagcsalád nevének (pfn Megkeresése). A PFN megkeresése egy alkalmazást, lásd: [egy csomagcsalád nevét megkeresése az alkalmazásonkénti VPN](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md). |Összes|

> [!IMPORTANT]
> Azt javasoljuk, hogy lássa társított alkalmazáslistákat azt az alkalmazásonkénti VPN-konfigurációban való használat céljából. Ha egy jogosulatlan felhasználó módosítja a listában, és importálja a alkalmazásonkénti VPN-alkalmazáslistába, potenciálisan engedélyeztetéséhez használandó alkalmazásokat, amelyek nem rendelkeznek hozzáféréssel VPN-hozzáférését. Hozzáférés-vezérlési listaként (ACL) segítségével egy védelmének módja lehet app listák el.


1.  A a **hitelesítési módszer** lapon adja meg a varázslóban:  

    -   **Hitelesítési módszer**: Válassza ki a hitelesítési módszert, amelyet a VPN-kapcsolat használni fog. Rendelkezésre álló módszer függ a kapcsolat típusa ebben a táblázatban látható módon.  

        |Hitelesítési módszer|Támogatott&nbsp;kapcsolat&nbsp;típusok|  
        |---------------------------|--------------------------------|  
        |**Tanúsítványok**<br /><br /> **Megjegyzések:**<ul><li>Ha az ügyféltanúsítványt egy, a RADIUS-kiszolgáló, például a hálózati házirend-kiszolgáló hitelesíti a tulajdonos alternatív neve a tanúsítvány az egyszerű felhasználónevet kell beállítani.</li><li>Android történő telepítés esetén válassza az EKU-azonosító és a tanúsítvány kiállítójának ujjlenyomata kivonat értéke.  Ellenkező esetben felhasználók kell választania a megfelelő tanúsítvány manuális.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Felhasználónév és jelszó**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**A Microsoft védett EAP (PEAP)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Microsoft biztonságos jelszó (EAP-MSCHAP v2)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Intelligens kártya vagy más tanúsítvány**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (csak iOS rendszeren)|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Számítógép-tanúsítványok használata**|<ul><li>IKEv2</li></ul>|  

         Attól függően, hogy a megadott beállítások kérheti adja meg a további információkat, például:  

        -   **A felhasználói hitelesítő adatok megjegyzése minden bejelentkezéskor**: Hogy a felhasználóknak nem kell megadnia őket minden egyes csatlakozás alkalmával a rendszer megjegyezze a felhasználó hitelesítő adatait.  

        -   **Válasszon ügyféltanúsítványt az ügyfél-hitelesítéshez**: Válassza ki a korábban létrehozott ügyfél [SCEP-tanúsítvány](create-pfx-certificate-profiles.md) , amely használható a VPN-kapcsolat hitelesítéséhez.   

            > [!NOTE]  
            >  IOS-eszközök esetén a SCEP-profilok kiválasztott rendszer beágyazza a VPN-profil. Egyéb platformok esetén egy alkalmazhatósági szabályt kerül győződjön meg arról, hogy a VPN-profil nincs telepítve, ha a tanúsítvány nincs jelen vagy nem megfelelő.  
            >   
            >  Ha a megadott SCEP-tanúsítvány nem megfelelő, vagy nem vezette be, majd a VPN-profil nem települ az eszközön.
            >  
            >  IOS rendszerű eszközök támogatja csak az RSA securid-titkosítást és MSCHAP v2 hitelesítési módszert, ha a kapcsolat típusa PPTP. A jelentéskészítési hibák elkerülése érdekében az iOS rendszerű eszközökön telepítsen egy külön PPTP VPN-profilt.  

        - **Feltételes hozzáférés**
            - Válasszon **engedélyezze a feltételes hozzáférést a VPN-kapcsolat** annak érdekében, hogy VPN hálózathoz csatlakozó eszközök feltételes hozzáférési megfelelőségi csatlakozás előtt ellenőrzi. Ismerteti a megfelelőségi szabályzatok [eszközmegfelelőségi szabályzatok a System Center Configuration Managerben](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md).
            - Válasszon **engedélyezése az egyszeri bejelentkezés (SSO) más tanúsítvánnyal való** eltérő a VPN-hitelesítési tanúsítványt az eszköznek meg kell felelnie a tanúsítvány kiválasztásához. Ha ezt a beállítást, adja meg a **EKU** (vesszővel elválasztva), és **kiállítói kivonatot**, a megfelelő tanúsítványt, amelyet, keresse meg a VPN-ügyfél.

         - A **a Windows információvédelem**, adja meg a vállalat által felügyelt vállalati identitás, amely általában a vállalat elsődleges tartományt, például, *contoso.com*. Megadhatja, hogy Ön szervezetéhez tartozik elválasztva őket a több tartományt a "|}" karaktert. Például *contoso.com|newcontoso.com*.   
              A Windows információvédelem kapcsolatban bővebben lásd: [a Microsoft Intune Windows információk védelme (folyamatban) házirend létrehozása](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune).   

         ![VPN feltételes hozzáférésének beállítása](media/vpn-conditional-access.png)

         Ha a Configuration Manager futó Windows-verzió támogatja _és_ kiválaszthatja a kijelölt engedélyezési módszer **konfigurálása** a Windows tulajdonságai párbeszédpanel megnyitásához, és konfigurálhatja a hitelesítési módszer tulajdonságait.  Ha **konfigurálása** van le van tiltva, az a különböző eszközök használatával konfigurálhatja a hitelesítési módszer tulajdonságait.

2.  Az a **proxybeállítások** oldalán a **VPN-profil létrehozása varázsló**, ellenőrizze a **a VPN-profil proxybeállításainak konfigurálása** mezőben, ha a VPN-kapcsolat proxykiszolgálót használ. Ezt követően adja meg a proxykiszolgáló kiszolgáló adatait. További információt a Windows Server rendszer dokumentációjában talál.  

    > [!NOTE]  
    >  A számítógépen, a Windows 8.1 a VPN-profil nem jelennek meg a proxy adatait mindaddig, amíg a számítógép használatával csatlakoznak a VPN-hez.  


3. További DNS-beállítások konfigurálása (ha szükséges).  
 A a **konfigurálása automatikus VPN-kapcsolat** lapon konfigurálhatja a következőket:  

    -   **Engedélyezze a VPN-igény szerinti**: Használja a Windows Phone 8.1 rendszerű eszközök további DNS-beállításainak konfigurálása. Ez a beállítás csak Windows Phone 8.1-eszközökre vonatkozik, és csak engedélyezni kell a VPN-profilok, hogy Windows Phone 8.1-eszközre telepíteni.

    -   **DNS-utótagok listája** (csak Windows Phone 8.1-eszközök esetén): VPN-kapcsolatot kialakító tartományok konfigurálása. Minden olyan tartományban, akkor adja meg vegye fel a DNS-utótagját, a DNS-kiszolgáló címét és a következő igény szerinti műveletek egyikét:  

        -   **Soha ne jöjjön létre**: Soha ne nyisson meg egy VPN-kapcsolatot.  

        -   **Szükség esetén jöjjön létre**: Csak akkor nyissa meg a VPN-kapcsolat, ha az erőforrások eléréséhez szükséges.  

        -   **Mindig jöjjön létre**: Mindig nyissa meg a VPN-kapcsolatot.  

    -   **Egyesítési**: Másolja át úgy konfigurálva, hogy minden DNS-utótagokat a **megbízható hálózatok listájára**.  

    -   **Megbízható hálózatok listájához** (csak Windows Phone 8.1-eszközök esetén): Egy DNS-utótagot adjon meg soronként. Ha az eszköz megbízható hálózaton van, a VPN-kapcsolat nem nyílik meg.  

    -   **Utótag-keresési listát** (csak Windows Phone 8.1-eszközök esetén): Egy DNS-utótagot adjon meg soronként. Minden DNS-utótagot kell keresni, amikor által egy rövid nevet használó webhelyhez csatlakozik.  

     Például adja meg a DNS-utótagok **tartomany1.contoso.com** és **tartoman2.contoso.com**, és keresse meg az URL-cím **http://mywebsite**. A rendszer ebben az esetben a következő címekre keres rá:  

    -   **http://sajatwebhely.tartomany1.contoso.com**  

    -   **http://sajatwebhely.tartomany2.contoso.com**  

    > [!NOTE]  
    >  Csak Windows Phone 8.1-eszközökön  
    >   
    >  Ha a *küldése az összes hálózati forgalom a VPN-kapcsolaton keresztül* beállítást *és* a VPN-kapcsolatot a teljes körű alagútkezelést használ, a VPN-kapcsolatot automatikusan megnyílik az első eszköz profilt használ. Egy kapcsolat megnyitásához egy másik profil használatával állítsa be a kívánt profilra az alapértelmezett.  
    >   
    >  Ha a *küldése az összes hálózati forgalom a VPN-kapcsolaton keresztül* lehetőség *nem* kijelölt *és* a VPN-kapcsolat a vegyes alagútkezelést használ, a VPN-kapcsolatok automatikusan nyissa meg a konfigurált útvonalakat vagy kapcsolatspecifikus DNS-utótagok.  


4. Az a **által támogatott platformok** oldalán a **VPN-profil létrehozása varázsló**, válassza ki az operációs rendszereket, amelyeken a VPN-profil lesz telepítve, vagy válasszon **válassza ki az összes** a VPN-profil telepítéséhez az összes rendelkezésre álló operációs rendszeren.  

5. Fejezze be a varázsló futtatását. A **VPN-profilok** csomópontja a **eszközök és megfelelőség** munkaterületen jeleníti meg az új VPN-profil.  


**Telepítése**: Lásd: [telepítése Wi-Fi, VPN, e-mail és tanúsítványprofilok](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) további információ a VPN-profilok központi telepítése.

### <a name="next-steps"></a>További lépések  
 A következő témakörök segítségével tervezze meg, állítsa be, fog működni, és a VPN-profilok a Configuration Manager karbantartásához.  

-   [A System Center Configuration Manager VPN-profilok használatának előfeltételei](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Biztonság és adatvédelem a VPN-profilok a System Center Configuration Managerben](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

