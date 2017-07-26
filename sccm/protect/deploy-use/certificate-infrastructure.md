---
title: "Tanúsítványinfrastruktúra konfigurálása |} Microsoft Docs"
description: "Útmutató a tanúsítványigénylés konfigurálásának a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 29ae59b7-2695-4a0f-a9ff-4f29222f28b3
caps.latest.revision: 7
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 859a8da10f55e314b205b7a4a415a1d2a60a920a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="certificate-infrastructure"></a>Tanúsítvány-infrastruktúra

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbiakban a lépéseket, részleteket és további információ a tanúsítványok konfigurálása a System Center Configuration Managerben. Kezdés előtt ellenőrizze az itt felsorolt előfeltételeket:[Tanúsítványprofilok használatának előfeltételei a System Center Configuration Managerben](../../protect/plan-design/prerequisites-for-certificate-profiles.md).  

Az infrastruktúra konfigurálása az SCEP, az alábbi lépések segítségével vagy a PFX-tanúsítványokat.

## <a name="step-1---install-and-configure-the-network-device-enrollment-service-and-dependencies-for-scep-certificates-only"></a>1. lépés – és függőségeinek telepítése és konfigurálása a hálózati eszközök tanúsítványigénylési szolgáltatása (a csak SCEP-tanúsítványok)

 Telepítse és konfigurálja a Hálózati eszközök tanúsítványigénylési szolgáltatása szerepkört az Active Directory tanúsítványszolgáltatásokhoz (AD CS), módosítsa a tanúsítványsablonokra vonatkozó biztonsági engedélyeket, telepítsen egy nyilvános kulcsú infrastruktúrára (PKI) épülő ügyfél-hitelesítési tanúsítványt, majd a beállításjegyzék szerkesztésével növelje meg az Internet Information Services (IIS) alapértelmezett URL-méretének korlátját. Emellett ha szükséges, a kiállító hitelesítésszolgáltató konfigurálásával engedélyezze az egyéni érvényességi időt is.  

> [!IMPORTANT]  
>  A hálózati eszközök tanúsítványigénylési szolgáltatása használható a System Center Configuration Manager konfigurálása előtt ellenőrizze a telepítése és konfigurálása a hálózati eszközök tanúsítványigénylési szolgáltatása. Ha ezek a függőségi viszonyok nem működnek megfelelően, hogy nehezen tanúsítványigénylés hibaelhárításával a System Center Configuration Manager használatával.  

### <a name="to-install-and-configure-the-network-device-enrollment-service-and-dependencies"></a>A Hálózati eszközök tanúsítványigénylési szolgáltatásának és függőségeinek telepítése és konfigurálása  

1.  A Windows Server 2012 R2-t futtató kiszolgálón telepítse és konfigurálja a Hálózati eszközök tanúsítványigénylési szolgáltatása szerepkör-szolgáltatást az Active Directory tanúsítványszolgáltatások kiszolgálói szerepkörhöz. További információért olvassa el az [Útmutató a Hálózati eszközök tanúsítványigénylési szolgáltatásához](http://go.microsoft.com/fwlink/p/?LinkId=309016) című cikket az Active Directory tanúsítványszolgáltatások dokumentumtárában a TechNet webhelyen.  

2.  Ellenőrizze, és szükség esetén módosítsa a Hálózati eszközök tanúsítványigénylési szolgáltatása által használt tanúsítványsablonok biztonsági engedélyeit:  

    -   A fiók, amelyen fut a System Center Configuration Manager konzol: **Olvasási** engedéllyel.  

         Ez az engedély szükséges ahhoz, hogy a Tanúsítványprofil létrehozása varázsló futtatásakor tallózással kiválaszthassa az SCEP-beállításprofil létrehozásakor használni kívánt tanúsítványsablont. Tanúsítványsablon választásakor a rendszer a varázsló egyes beállításait automatikusan meghatározza, így kevesebb beállítást kell konfigurálni, és kisebb a veszélye annak, hogy a Hálózati eszközök tanúsítványigénylési szolgáltatása által használt tanúsítványsablonokkal nem kompatibilis beállításokat választ.  

    -   A hálózati eszközök tanúsítványigénylési szolgáltatásának alkalmazáskészlete által használt SCEP szolgáltatásfiók: **Olvasási** és **beléptetés** engedélyek.  

         Ez a követelmény nem a System Center Configuration Manager adott, de része a hálózati eszközök tanúsítványigénylési szolgáltatása konfigurálásának. További információért olvassa el az [Útmutató a Hálózati eszközök tanúsítványigénylési szolgáltatásához](http://go.microsoft.com/fwlink/p/?LinkId=309016) című cikket az Active Directory tanúsítványszolgáltatások dokumentumtárában a TechNet webhelyen.  

    > [!TIP]  
    >  A hálózati eszközök tanúsítványigénylési szolgáltatása által használt tanúsítványsablonok azonosításához keresse meg a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgálón a következő beállításkulcsot: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP.  

    > [!NOTE]  
    >  Ezek az alapértelmezett biztonsági engedélyek, amelyek a legtöbb környezetben megfelelő megoldást nyújtanak – ehelyett azonban alternatív biztonsági konfigurációt is használhat. További tájékoztatásért lásd: [Tanúsítványsablonok engedélyeinek tervezése a System Center Configuration Manager tanúsítványprofiljaihoz](../../protect/plan-design/planning-for-certificate-template-permissions.md).  

3.  Telepítsen a kiszolgálón egy PKI-tanúsítványt, amely támogatja az ügyfél-hitelesítést. Előfordulhat, hogy már használható tanúsítvány van telepítve a számítógépen, de az is lehet, hogy kifejezetten erre a célra szolgáló tanúsítványt kell (vagy célszerű) telepítenie. Ez a tanúsítvány követelményeivel kapcsolatos további információkért olvassa el a Configuration Manager házirend modulját és a hálózati eszközök tanúsítványigénylési szolgáltatása szerepkör-szolgáltatást futtató kiszolgálók a ** PKI-tanúsítványok a kiszolgálók ** szakasz a [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md) témakör.  

    > [!TIP]  
    >  Ha a tanúsítvány telepítéséhez segítségre van szüksége, használhatja a használati [a terjesztési pontok az ügyféltanúsítvány központi telepítése](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012), mivel a tanúsítványkövetelmények azonosak, egy kivétellel:  
    >   
    >  -   A tanúsítványsablon tulajdonságai között a **Kérelmek kezelése** lapon ne jelölje be **A titkos kulcs exportálható** négyzetet.  
    >   
    >  Nincs a tanúsítvány exportálása a titkos kulccsal, ugyanis a helyi számítógéptárolóból, és válassza ki azt a System Center Configuration Manager házirend moduljának konfigurálásakor.  

4.  Keresse meg azt a legfelső szintű tanúsítványt, amelyhez az ügyfél-hitelesítési tanúsítvány kapcsolódik, majd exportálja ezt a legfelső szintű hitelesítésszolgáltatói tanúsítványt egy tanúsítványfájlba (.cer). Mentse ezt a fájlt védett helyre, amelyet később biztonságosan elérhet a tanúsítványregisztrációs pont helyrendszer-kiszolgálójának telepítésekor és konfigurálásakor.  

5.  Ugyanezen a kiszolgálón használja a beállításszerkesztőt, hogy növelje az IIS alapértelmezett URL-méretének korlátját, amit a következő beállításkulcs DWORD-értékek beállításával itt tehet meg: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\HTTP\Parameters:  

    -   A **MaxFieldLength** kulcs értékét állítsa **65534**-re.  

    -   A **MaxRequestBytes** kulcs értékét állítsa **16777216**-ra.  

     További információkért lásd: a cikk [820129: A HTTP.sys beállításai Windowsban](http://go.microsoft.com/fwlink/?LinkId=309013) a Microsoft Tudásbázis.  

6.  Ugyanezen a kiszolgálón az Internet Information Services (IIS) kezelőjében módosítsa a /certsrv/mscep alkalmazás kérelemszűrési beállításait, majd indítsa újra a kiszolgálót. A **Kérelemszűrési beállítások szerkesztése** párbeszédpanelen a **Kérelmekre vonatkozó korlátok** az alábbiak legyenek:  

    -   **Tartalom engedélyezett maximális hossza (bájt)**: **30000000**  

    -   **Maximális URL-cím hossza (bájt)**: **65534**  

    -   **Maximális lekérdezési karakterlánc (bájt)**: **65534**  

     A fenti beállításokról és konfigurálásukról további információt a [Lekérdezési korlátok](http://go.microsoft.com/fwlink/?LinkId=309014) című cikkben olvashat az IIS referenciatárában.  

7.  Ha szeretne egy Ön által használt tanúsítványsablon rövidebb érvényességi idejű tanúsítványt igényelni: Ez a konfiguráció vállalati Hitelesítésszolgáltatók esetében alapértelmezés szerint le van tiltva. Ha vállalati hitelesítésszolgáltatón szeretné engedélyezni ezt a beállítást, a Certutil parancssori eszközzel állítsa le és indítsa újra a tanúsítványszolgáltatást, az alábbi parancsokkal:  

    1.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  

    2.  **net stop certsvc**  

    3.  **a net start certsvc**  

     További információért olvassa el a [Tanúsítványszolgáltatások – Eszközök és beállítások](http://go.microsoft.com/fwlink/p/?LinkId=309015) című cikket a PKI-technológiák dokumentumtárában a TechNet webhelyen.  

8.  A következő hivatkozással ellenőrizze, hogy működik-e a Hálózati eszközök tanúsítványigénylési szolgáltatása: **https://server.contoso.com/certsrv/mscep/mscep.dll**. Ha a szolgáltatás működik, a Hálózati eszközök tanúsítványigénylési szolgáltatásának beépített weblapja jelenik meg. A weblap bemutatja a szolgáltatást és leírja, hogy a hálózati eszközök az URL segítségével küldenek tanúsítványkérelmeket.  

 Most, hogy végzett a Hálózati eszközök tanúsítványigénylési szolgáltatása és függőségei konfigurálásával, készen áll a tanúsítványregisztrációs pont telepítésére és konfigurálására.


## <a name="step-2---install-and-configure-the-certificate-registration-point"></a>2. lépés – telepítés és a tanúsítványregisztrációs pont konfigurálásáról.

Ön telepítenie és konfigurálnia kell legalább egy tanúsítványregisztrációs pontot a System Center Configuration Manager-hierarchiában, és a helyrendszerszerepkör a központi adminisztrációs hely vagy elsődleges helyen telepíthető.  

> [!IMPORTANT]  
>  A tanúsítványregisztrációs pont telepítését megelőzően tekintse meg [A System Center Configuration Manager által támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md) című témakör **Helyrendszer követelményei** című szakaszát az operációs rendszerre vonatkozó követelményekért és a tanúsítványregisztrációs pont függőségeiért.  

##### <a name="to-install-and-configure-the-certificate-registration-point"></a>A tanúsítványregisztrációs pont telepítése és konfigurálása  

1.  A System Center Configuration Manager konzolon kattintson **felügyeleti**.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció** csomópontot, kattintson a **Kiszolgálók és helyrendszerszerepkörök** elemre, majd jelölje ki a kiszolgálót, amelyet a tanúsítványregisztrációs pontként használni kíván.  

3.  A **Kezdőlap** **Kiszolgáló** csoportjában kattintson a **Helyrendszerszerepkörök hozzáadása** elemre.  

4.  Az **Általános** lapon adja meg a helyrendszer általános beállításait, majd kattintson a **Tovább** gombra.  

5.  A **Proxy** lapon kattintson a **Tovább** gombra. A tanúsítványregisztrációs pont nem használ internetes proxybeállításokat.  

6.  A **Rendszerszerepkör kiválasztása** lapon az elérhető szerepkörök listájából válassza a **Tanúsítványregisztrációs pont** elemet, majd kattintson a **Tovább** gombra. 

8. Az a **tanúsítvány regisztrációs mód** lapon, válassza ki, hogy a tanúsítványregisztrációs pontot az **folyamat SCEP tanúsítványkérelmek**, vagy **folyamat PFX tanúsítványkérelmek**. A tanúsítványregisztrációs pont nem tudja feldolgozni a kéréseket mindkét típusú, de létrehozhat több tanúsítvány tanúsítványregisztrációs pont Ha mindkét tanúsítványtípusok dolgozik.

7.  Az a **Tanúsítványregisztrációs pont beállításainak** lapon megadott beállítások típusának megfelelő tanúsítványtároló fel fogja dolgozni a tanúsítványregisztrációs pont függ:
    -   Ha a kiválasztott **folyamat SCEP tanúsítványkérelmek**, majd konfigurálja a következőket:
        -   **Webhely neve**, **HTTPS-port száma**, és **virtuális alkalmazásnév** a tanúsítványregisztrációs pont. Ezek a mezők kitölti automatikusan az alapértelmezett értékekkel. 
        -   **A hálózati eszközök tanúsítványigénylési szolgáltatását és a legfelső szintű Hitelesítésszolgáltatói tanúsítvány URL-cím** -kattintson **Hozzáadás**, ezt a a **URL-CÍMEK hozzáadása és a legfelső szintű Hitelesítésszolgáltatói tanúsítvány** párbeszédpanelen adja meg a következő:
            - **A hálózati eszközök tanúsítványigénylési szolgáltatásához tartozó URL-cím**: A következő formátumban adja meg az URL-cím: https://*< Kiszolgáló_teljes_tartományneve >*/certsrv/mscep/mscep.dll. Ha például a Hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgáló teljes tartományneve server1.contoso.com, a következőt írja be: **https://server1.contoso.com/certsrv/mscep/mscep.dll**.
            - **Legfelső szintű hitelesítésszolgáltató tanúsítványának**: Keresse meg és jelölje ki a létrehozott és mentett tanúsítvány (.cer) fájlját **1. lépés: Telepítse és konfigurálja a hálózati eszközök tanúsítványigénylési szolgáltatásának és függőségeinek**. A legfelső szintű Hitelesítésszolgáltatói tanúsítvány lehetővé teszi a tanúsítványregisztrációs pontot az ügyfél hitelesítési tanúsítvánnyal, amely a System Center Configuration Manager házirend modulját fogja használni.  
    - Ha a kiválasztott **folyamat PFX tanúsítványkérelmek**, majd konfigurálja a következőket:
        - **Hitelesítésszolgáltató hitelesítésszolgáltatók (CA) és a fiók minden hitelesítésszolgáltatóra conenct szükséges** -kattintson **Hozzáadás** ezt a a **adja hozzá a hitelesítésszolgáltató és a fiók** párbeszédpanelen adja meg a következő:
            - **Tanúsítvány-szolgáltató kiszolgáló neve** -adja meg a tanúsítvány hitelesítésszolgáltatói kiszolgáló nevét.
            - **Tanúsítvány-szolgáltató fiók** -kattintson **beállítása** válassza ki, vagy hozzon létre a fiókot, amely jogosult az igénylésre a sablonok a hitelesítésszolgáltatón.
        - **Tanúsítványregisztrációs pont csatlakozási fiókja tanúsítvány** – válasszon ki vagy hozzon létre a fiókot, amely a tanúsítványregisztrációs pont csatlakozik a Configuration Manager adatbázisába. Alteratively a tanúsítványregisztrációs pontot futtató számítógép helyi számítógépfiók is használhatja.
        - **Active Directory tanúsítvány közzétételi fiók** – válassza ki a fiókot, vagy hozzon létre egy új fiókot, amely a tanúsítványok közzététele az Active Directory felhasználói objektumok történik.
8.  **Az URL és a legfelső szintű hitelesítésszolgáltató tanúsítványának megadása** párbeszédpanelen határozza meg az alábbiakat, majd kattintson az **OK** gombra:  

9. Kattintson a **Tovább** gombra, és fejezze be a varázslót.  

10. Várjon néhány percet, míg a telepítés befejeződik, majd az alábbi módszerek egyikével ellenőrizze, hogy a tanúsítványregisztrációs pont telepítése sikeres volt-e:  

    -   A **Figyelés** munkaterületen bontsa ki a **Rendszer állapota** elemet, kattintson az **Összetevő állapota** lehetőségre, és keresse meg az **SMS_CERTIFICATE_REGISTRATION_POINT** összetevőtől származó állapotüzeneteket.  

    -   A helyrendszer-kiszolgálón tekintse meg a *<ConfigMgr telepítési útvonala\>*\Logs\crpsetup.log és a *<ConfigMgr telepítési útvonala\>*\Logs\crpmsi.log fájlt. Sikeres telepítés esetén a kilépési kód „0”.  

    -   Egy böngészővel ellenőrizze, hogy képes-e csatlakozni a tanúsítvány regisztrációs pointâ "URL-címe"például: https://server1.contoso.com/CMCertificateRegistration. Ha a telepítés sikeres volt, egy **Kiszolgálóhiba** oldal jelenik meg az alkalmazás nevével és a HTTP 404-es hiba leírásával.  

11. Keresse meg a legfelső szintű hitelesítésszolgáltatóhoz tartozó exportált tanúsítványfájlt, amelyet a tanúsítványregisztrációs pont automatikusan létrehozott az elsődleges helykiszolgáló számítógépén a következő mappában: *<ConfigMgr Installation Path\>*\inboxes\certmgr.box. Mentse a fájlt védett helyre, ha később telepíti a System Center Configuration Manager házirend modulját a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgálón biztonságosan elérhetők.  

    > [!TIP]  
    >  A tanúsítvány nem érhető el azonnal a mappában; Előfordulhat, hogy meg kell várni valamennyit (körülbelül fél órát) System Center Configuration Manager átmásolja a fájlt erre a helyre.  


## <a name="step-3----install-the-system-center-configuration-manager-policy-module-for-scep-certificates-only"></a>3. lépés - a System Center Configuration Manager házirend modulját (a csak SCEP-tanúsítványok) telepítéséhez.

Ön telepítenie és konfigurálnia kell a System Center Configuration Manager házirend modulját minden kiszolgálón, amelyet a **2. lépés: Telepítse és konfigurálja a tanúsítványregisztrációs pont** , **a hálózati eszközök tanúsítványigénylési szolgáltatásához tartozó URL-cím** a tanúsítványregisztrációs pont tulajdonságainál.  

##### <a name="to-install-the-policy-module"></a>A házirendmodul telepítése  

1.  A hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgálón jelentkezzen be tartományi rendszergazdaként, és a következő fájlokat másolja a < configmgrtelepítési adathordozó\>\SMSSETUP\POLICYMODULE\X64 mappából a System Center Configuration Manager telepítési adathordozón egy ideiglenes mappába:  

    -   PolicyModule.msi  

    -   PolicyModuleSetup.exe  

    Emellett ha a telepítési adathordozón egy LanguagePack mappa is található, másolja azt is, a tartalmával együtt.  

2.  Az ideiglenes mappából futtassa a PolicyModuleSetup.exe a System Center Configuration Manager házirend moduljának telepítője varázsló elindításához.  

3.  A varázsló kezdőlapján kattintson a **Tovább** gombra, fogadja el a licencfeltételeket, majd kattintson ismét a **Tovább** gombra.  

4.  A **Telepítési mappa** lapon fogadja el a házirendmodul alapértelmezett telepítési mappáját, vagy adjon meg egy másik mappát, majd kattintson a **Tovább** gombra.  

5.  A **Tanúsítványregisztrációs pont** lapon a helyrendszer-kiszolgáló teljes tartományneve és a tanúsítványregisztrációs pont tulajdonságai között megadott virtuális alkalmazásnév használatával adja meg a tanúsítványregisztrációs pont URL-jét. Az alapértelmezett virtuális alkalmazásnév: CMCertificateRegistration. Ha például a helyrendszer-kiszolgáló teljes tartományneve server1.contoso.com, és az alapértelmezett virtuális alkalmazásnevet használta, a következő URL-t adja meg: **https://server1.contoso.com/CMCertificateRegistration**.  

6.  Fogadja el az alapértelmezett **443**-as portot, vagy ha a tanúsítványregisztrációs pont másik portot használ, adja meg annak a számát, majd kattintson a **Tovább** gombra.  

7.  Az a **házirend modul ügyfél-tanúsítványa**lapon keresse meg és adja meg a központilag telepített ügyfél-hitelesítési tanúsítvány **1. lépés: Telepítse és konfigurálja a hálózati eszközök tanúsítványigénylési szolgáltatásának és függőségeinek**, és kattintson a **következő**.  

8.  Az a **Tanúsítványregisztrációs pont tanúsítványa** kattintson **Tallózás** jelölje be az exportált tanúsítványfájlt a legfelső szintű hitelesítésszolgáltató, amely megkeresett és mentett végén **2. lépés: Telepítse és konfigurálja a tanúsítványregisztrációs pont**.  

    > [!NOTE]  
    >  Ha korábban nem mentette a tanúsítványfájlt, a következő útvonalon találhatja meg a helykiszolgálón: <ConfigMgr Telepítési Útvonala\>\inboxes\certmgr.box.  

9. Kattintson a **Tovább** gombra, és fejezze be a varázslót.  

 Ha el szeretné távolítani a System Center Configuration Manager házirend modulját, **programok és szolgáltatások** a Vezérlőpulton. 

 
Most, hogy befejezte a konfigurációs lépésekkel, készen áll tanúsítványokat telepítsen felhasználók és eszközök létrehozása és a tanúsítványprofilok központi telepítése. További információk tanúsítványprofilok létrehozásáról: [Tanúsítványprofilok létrehozása a System Center Configuration Managerben](../../protect/deploy-use/create-certificate-profiles.md).  

