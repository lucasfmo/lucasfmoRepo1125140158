---
title: "A Technical Preview-ban 1606 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1606 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 134a2f60-811e-4dc9-a8f5-1ce0018c5c12
caps.latest.revision: 31
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7cb553d553a1d2e3118731118a566c38e7b4e161
ms.openlocfilehash: 08747ca981f6697e2bd621afe5df0e3bd06b332d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>A rendszer 1606 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1606 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    

**A Technical Preview kiadással kapcsolatos ismert problémák:**  
*  Ha a Technical Preview 1604-1605, majd 1606 verzióra frissíti, a frissítés sikertelen lehet, és a következőhöz hasonló hiba bekerül a **cmupdate.log**:

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    Ha ez történik, a a **frissítés és karbantartás** csomópont kattintson **frissítések keresése**, majd **próbálja meg újra** a frissítés telepítését.
    ***

**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="dmp_category"></a>Automatikusan eszközök gyűjteményekbe kategorizálása
Eszközök automatikus elhelyezése a eszközgyűjtemények használatakor a Configuration Manager a Microsoft Intune-nal használható eszközkategóriákat hozhat létre. Felhasználók majd válasszon egy eszközkategóriát, amikor regisztrálják az eszköz Intune-beli van szükség. Emellett módosíthatja a kategóriája az eszköz a Configuration Manager konzoljáról.

**Fontos:** Ez a funkció együttműködik az **2016. június** a Microsoft Intune kibocsátási. Győződjön meg arról, hogy Ön frissített ebben a kiadásban ahhoz, hogy próbálja ki ezeket az eljárásokat.

### <a name="try-it-out"></a>Próbálja ki!

### <a name="create-a-set-of-device-categories"></a>Létrehozhat egy eszközkategóriák
1.  Az a **eszközök és megfelelőség** a Configuration Manager konzol munkaterületén bontsa ki a **áttekintése**, majd kattintson a **Eszközgyűjtemények**.
2.  A a **Home** lap a **kategóriák** csoportjában **kezeléséhez eszközkategóriák**.
3.  Az a **kezeléséhez eszközkategóriák** párbeszédpanelen létrehozása, szerkesztése, vagy távolítsa el a kategóriák. Próbálja meg létrehozni egy új kategóriát.

### <a name="associate-a-collection-with-a-device-category"></a>Egy gyűjtemény társítandó eszközkategória
Eszközkategória hozzárendel egy gyűjteményt, ha a megadott kategóriában minden eszköz megkapja gyűjteményhez.
1.  Az a **tulajdonságok** párbeszédpanel egy eszközgyűjteményt, kattintson a **szabály hozzáadása** > **eszköz kategória szabály**.
2.  Az a **eszköz kategória tagsági szabály létrehozása** párbeszédpanelen jelölje ki a kategóriát a gyűjteményben lévő összes eszközre alkalmazni fogja őket.
3.  Zárja be a **eszköz kategória tagsági szabály létrehozása** párbeszédpanel bezárásához és a gyűjtemény tulajdonságai párbeszédpanel megnyitásához.

### <a name="change-the-category-of-a-device"></a>Egy eszköz kategóriájának módosítása
1.  A a **eszközök és megfelelőség** a Configuration Manager konzol munkaterületén bontsa ki a **áttekintése**, majd kattintson a **eszközök**.
2.  Jelöljön ki egy eszközt a a **eszközök** listában, majd a a **Home** lap a **eszköz** csoportjában kattintson **változás kategóriája**.
3.  Az a **eszközkategóriát szerkesztése** párbeszédpanelen válassza ki azokat alkalmazni, erre az eszközre, majd kattintson a kategória **OK**.

## <a name="dmp_grace"></a>Érvényesítési türelmi idő a szükséges alkalmazást és a szoftverfrissítés központi telepítései

Bizonyos esetekben célszerű telepíteni a szükséges alkalmazások központi telepítéseit vagy szoftverfrissítéseket minden konfigurált határidők túl további időt hagy a felhasználók. Ez lehet, hogy általában szükség lehet, amikor a számítógép ki van kapcsolva hosszabb ideig, és számos alkalmazás vagy frissítés központi telepítéséhez szükséges.
Például ha a felhasználó csak adott vissza a szabadsága, előfordulhat, hogy rendelkeznek long vár, amíg a lejárt alkalmazásként telepíti a központi telepítések.
Ez a probléma megoldásához most definiálhat egy kényszerítési türelmi időszak gyűjteményhez a Configuration Manager ügyfél beállítások telepítésével.

### <a name="try-it-out"></a>Próbálja ki!

A türelmi időszak konfigurálásához hajtsa végre a következő műveleteket:

1.  Az a **Számítógépügynök** lap, az ügyfélbeállítások konfigurálása az új tulajdonság **türelmi idő a kényszerítésre a telepítés utáni határidő (óra)** közötti értékű **1** és **120** óra.
2.  Szükséges alkalmazás új központi telepítést, vagy egy létező központi telepítés tulajdonságait a a **ütemezés** lapon, a jelölőnégyzet bejelölésével **felhasználói beállítások szerint a telepítés kényszerítésének késleltetés**, legfeljebb az ügyfélbeállításokban meghatározott türelmi időszak.
Minden, a jelölőnégyzet, kijelölve, és amely az eszközökön, amelyek is telepített ügyfélbeállítás célozzák telepítést használja a kényszerítési türelmi időszak.

Konfigurálja a kényszerítési türelmi időszak, és jelölje be a jelölőnégyzetet, az alkalmazás telepítési határidő elérésekor, ha telepítve az első nem üzleti ablak, amely a felhasználó és a türelmi időszak konfigurált történik. A felhasználó azonban továbbra is nyissa meg a Szoftverközpont és telepítheti az alkalmazást szeretnék bármikor. A türelmi időszak lejárta után a kényszerítési visszatér a lejárt központi telepítések elvégzéséhez ezek normál viselkedése.
Hasonló beállítások érhetőek el a szoftverfrissítések központi telepítési varázsló, az automatikus központi telepítési szabályok varázslóban és a Tulajdonságok lap.

##  <a name="dmp_devg"></a>A Configuration Manager használata egy felügyelt Eszközvédelem és-telepítő

Eszközvédelem hardvert használja a Windows 10 szolgáltatás és szoftver szolgáltatások szigorúan szabályozzák az eszközön való futtatásának megengedett érték.

Eszközvédelem funkciója, és annak működéséről részletes áttekintést olvasható [a Technet-cikkben](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview).

Ebben a kiadásban a Configuration Manager képes együttműködni a Eszközvédelem és [Windows AppLocker](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx) , amelyek az executable és a DLL-fájlok, a Configuration Managerrel telepített automatikusan megbízható, egy felügyelt telepítő származnak, ami azt jelenti, hogy a céleszközön futtatását engedélyezi, és egyéb szoftverek futtatásához, kivéve, ha explicit módon engedélyezni szeretné a futtatását, az egyéb AppLocker-szabályok nem használhatók.  

Jelenleg ez a funkció nem lehet konfigurálni a Configuration Manager konzoljáról. A házirend konfigurálási csak egy beállításkulcs megadásával konfigurálja az egyes ügyfelekre, és konfigurálja a Windows-szolgáltatásokat az ügyfélen.
Ha ezzel végzett, az AppLocker házirend fájl konfigurálása. Miután konfigurálta a házirendfájl, telepítheti bármely kompatibilis ügyfél eszközre.


Minden AppLocker-házirendek, például a szabályzatok által felügyelt Installer-szabályok két módban futtatható:

- A rendszervizsgálati mód – alkalmazások Megjegyzés futtathatók, de volna tiltott alkalmazások jelentett egy naplófájlban (Ez támogatott lesz egy későbbi kiadásban a Configuration Manager).
- Érvényesítési engedélyezve – alkalmazások futtatását sem.

Eszközvédelem és Configuration Manager használatával kapcsolatos további információk találhatók a [nagyvállalati mobilitási és biztonsági blogot](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10).

További információ:

- [Eszköz őr bemutatása](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Eszköz őr hitelesítő és megfelelőség](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Eszköz őr telepítési útmutatója](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

 ##  <a name="dmp_onprem"></a>Több eszköz felügyeleti pontot a helyszíni mobileszközök kezeléséhez  
 Technikai előzetes 1606,\-helyszíni mobileszköz-felügyeleti (MDM) egy új funkció támogatja a Windows 10 évforduló frissítés automatikusan konfigurálja a regisztrált eszköz szeretné, hogy több eszköz kezelése pont használható. Ez a funkció lehetővé teszi, hogy az eszköz egy másik eszközfelügyeleti pont tartalék amikor nem érhető el a szokásos használ egy. Ez a funkció csak akkor működik, a Windows 10 évforduló Update telepített számítógépek.  

### <a name="try-it-out"></a>Próbálja ki!  

1.  Egynél több felügyeleti pont telepítéséhez a hierarchiában.  

2.  A Windows 10 évforduló frissítés eszköz beléptetése a\-helyszíni mobileszköz-kezelés.  

Készítse elő a helyet, és az eszközök regisztrálása a információt\-helyszíni mobileszköz-kezelés, lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

## <a name="cloud_proxy"></a>Felhőbeli proxyszolgáltatás az interneten lévő ügyfelek kezeléséhez

Felhőbeli proxyszolgáltatás kezelése a Configuration Manager-ügyfelek az interneten lévő egyszerű módszert kínál. A szolgáltatást, amely a Microsoft Azure telepít, és az Azure-előfizetés szükséges, a helyi Configuration Manager-infrastruktúrát, a felhőbeli proxy összekötőpontja nevű új szerepkör alapján csatlakozik. Miután teljes mértékben telepítve és konfigurálva, ügyfelek fognak tudni hozzáférni a helyi Configuration Manager helyrendszer-szerepkörök függetlenül attól, hogy a belső magánhálózaton vagy az interneten kapcsolódó.

A Configuration Manager konzol segítségével a szolgáltatás üzembe helyezése az Azure-ba, adja hozzá a felhőbeli proxy connector-pont szerepkört, és helyrendszer-szerepköröket felhőbeli proxy forgalom engedélyezésére kell konfigurálni. Felhőbeli proxyszolgáltatás jelenleg csak támogatja a felügyeleti pont, a terjesztési pont és a szoftver frissítés pont szerepköre.

Ügyféltanúsítványok és a Secure Socket Layer (SSL)-tanúsítványok szükségesek számítógépek hitelesítéséhez és a különböző rétegeket, a szolgáltatás közötti kommunikáció titkosításához. Ügyfélszámítógépek általában keresztül csoport házirend betartatása ügyfél tanúsítványt kaphasson. Az ügyfelek és a szerepköröket üzemeltető helyrendszer-kiszolgáló közötti forgalom titkosításához, hozzon létre egy egyéni SSL-tanúsítványt a CA-tól kell. Kétféle típusú tanúsítványok, mellett is kell állít be, amely lehetővé teszi, hogy a Felhőbeli proxyszolgáltatás telepítése a Configuration Manager Azure felügyeleti tanúsítvánnyal.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>Felhőbeli proxyszolgáltatás a TP 1606 követelményei
- Ügyfélszámítógépek és a felhőbeli proxy összekötőpontja futtató helyrendszer-kiszolgálón.
- Egyéni SSL, a belső hitelesítésszolgáltató – az ügyfélszámítógépek számára a kommunikáció titkosítására és Felhőbeli proxyszolgáltatás identitásának hitelesítésére használt tanúsítványok.
- Azure-előfizetés felhőszolgáltatásai számára.
- Az Azure felügyeleti tanúsítvány - való hitelesítéshez szükséges a Configuration Manager az Azure-ral.

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>Felhőbeli proxyszolgáltatás a TP 1606 korlátozásai

- Csak a felügyeleti pont, a terjesztési pont és a szoftver frissítés pont szerepköre támogatja.
- A felhasználói házirendek nem támogatottak.
- Nem használható [a helyszíni mobileszköz-kezelés](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) a Configuration Manager alkalmazásban.
- Csak az Azure nyilvános felhő platform támogatott.


### <a name="try-it-out"></a>Próbálja ki!

A Felhőbeli proxyszolgáltatás telepítésének folyamata a következő lépésekből áll:

1. Hozzon létre, és egy egyéni SSL-tanúsítvány kiállításához a Felhőbeli proxyszolgáltatást.
1. Exportálja az ügyféltanúsítvány legfelső szintű.
2. A felügyeleti tanúsítvány feltöltése az Azure-bA.
3. Felhőbeli proxyszolgáltatás beállítása a Configuration Manager konzolon.
4. Az elsődleges hely ügyféltanúsítvány-alapú hitelesítés használatára konfigurálja.
5. A felhőbeli proxy összekötőpontja hozzá a helyhez.
6. Konfigurálja a helyrendszerszerepköröket a felhőbeli proxy forgalom fogadására.

Az alábbi szakaszok nyújtanak további információt az alábbi lépések elvégzése.

#### <a name="create-a-custom-ssl-certificate"></a>Hozzon létre egy egyéni SSL-tanúsítványt

Létrehozhat egy egyéni SSL-tanúsítványt a Felhőbeli proxyszolgáltatás ugyanúgy teheti a felhő alapú terjesztési pontok. Kövesse az utasításokat [a felhő alapú terjesztési pontok a szolgáltatástanúsítvány központi telepítése](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) , de eltérő tegye a következőket:

* Az új tanúsítványsablon beállításakor ad **olvasási** és **beléptetés** engedélyeket a biztonsági csoportnak, amely a Configuration Manager-kiszolgálók beállítása.

#### <a name="export-the-client-certificates-root"></a>Az ügyféltanúsítvány főtanúsítvány exportálása

A legegyszerűbb módja exportálási gyökere ügyféltanúsítványt a hálózaton használt, egy a tartományhoz csatlakoztatott számítógépeken, amelyek egy ügyféltanúsítványt megnyitásához, és másolja.

>[!NOTE]
>Ügyféltanúsítványok szükségesek Felhőbeli proxyszolgáltatás kezelése és a felhőbeli proxy összekötőjének üzemeltető helyrendszer-kiszolgálón kattintson a kívánt számítógépen. Ha ügyfél-tanúsítvány hozzáadása bármely ezeknek a gépeknek szüksége, tekintse meg [központi telepítése a tanúsítvány a Windows ügyfélszámítógépek](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012).

1. A Futtatás ablakba írja be a **mmc** nyomja le az ENTER.
2. A felügyeleti konzolon a Fájl menüben kattintson **beépülő modul hozzáadása/eltávolítása...** .
3. Hozzáadása vagy eltávolítása beépülő modulok párbeszédpanelen kattintson **tanúsítványok**, kattintson a **Hozzáadás >**, kattintson **számítógépfiók**, kattintson a **tovább**, kattintson **helyi számítógép**, és kattintson a **Befejezés**. A párbeszédpanel bezárásához kattintson az **OK** gombra.
4. Ugrás a **tanúsítványok > személyes > Tanúsítványok**.
5. Kattintson duplán a tanúsítványra, az ügyfél-hitelesítéshez a számítógépen, kattintson az Általános lapon, és kattintson duplán a legfelső szintű hitelesítésszolgáltatóval (tetején az elérési út).
6.  Kattintson a részleteket tartalmazó lapot, majd **Másolás fájlba...** .
7. Fejezze be a Tanúsítványexportáló varázsló segítségével az alapértelmezett tanúsítvány formátuma. Ellenőrizze, jegyezze fel a nevét, és a legfelső szintű tanúsítványt hoz létre. Szüksége lesz egy későbbi lépésben Felhőbeli proxyszolgáltatás konfigurálásához.

#### <a name="upload-the-management-certificate-to-azure"></a>A felügyeleti tanúsítvány feltöltése az Azure-bA

Az Azure felügyeleti tanúsítvány megadása kötelező a Configuration Manager az Azure API eléréséhez és Felhőbeli proxyszolgáltatás konfigurálásához. További információt és útmutatást a felügyeleti tanúsítvány feltöltése az Azure dokumentációjának a következő cikkekben talál:
- [Azure Cloud Services tanúsítványok áttekintése](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Az Azure szolgáltatásfelügyeleti API Management-tanúsítvány feltöltése](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/).

Ügyeljen arra, hogy az előfizetés-azonosító, a felügyeleti tanúsítvány másolja. Szüksége lesz az Felhőbeli proxyszolgáltatás konfigurálása a Configuration Manager konzolon.

#### <a name="set-up-cloud-proxy-service"></a>Felhőbeli proxyszolgáltatás beállítása

1. Nyissa meg a Configuration Manager konzol **Adminisztráció > Felhőszolgáltatások > Felhőbeli proxyszolgáltatás**.
2. Kattintson a **Felhőbeli proxyszolgáltatás létrehozása**.
3. A felhő létrehozása Proxy szolgáltatás varázslóban (az Azure felügyeleti portálján átmásolva) Azure-előfizetése Azonosítóját adja meg, kattintson a Tallózás gombra, és válassza ki az Azure felügyeleti tanúsítvány feltöltéséhez használt tanúsítvány fájlt. Kattintson a **Tovább** gombra. Várjon egy kis ideig, a konzol Azure való kapcsolódáshoz.
4. Töltse ki a varázsló további részletek:
    - Adja meg az egyéni SSL-tanúsítvány exportált titkos kulcs (.pfx fájlt).
    - Adja meg, hogy az ügyféltanúsítvány-ból exportált legfelső szintű tanúsítványát.
    - Adja meg a szolgáltatás néven az új tanúsítványsablon létrehozásakor használt teljes tartománynév.
    - Törölje a jelölését **ügyfél tanúsítvány-visszavonás ellenőrzése** (kivéve, ha van nyilvánosan közzétételt a CRL-adatok).
    - Kattintson a **következő** befejezése.
5. Tekintse át a beállításokat, és kattintson a **következő**. A Configuration Manager elindítja a szolgáltatás beállítása. A varázsló befejezését követően kattinthat **Bezárás**, azonban a szolgáltatás teljesen az Azure-ban kiépítése vesz majd igénybe 5-15 perc. Ellenőrizze a **állapot** oszlopában az újonnan beállítani annak meghatározásához, ha a szolgáltatás készen áll a Felhőbeli proxyszolgáltatást.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>Elsődleges hely ügyfél-hitelesítő hitelesítés konfigurálása

1. Nyissa meg a Configuration Manager konzol **Adminisztráció > Helykonfiguráció > helyek**.
2. Válassza ki az elsődleges helyen az ügyfelek kezelésére Felhőbeli proxyszolgáltatás keresztül, és kattintson a kívánt **tulajdonságok**.
3. Az ügyfél-kommunikáció számítógép lapon elsődleges hely tulajdonságlapon, jelölje be a jelölőnégyzetet a **használjon PKI-ügyféltanúsítvány (ügyfél-hitelesítés) Ha van ilyen**.
4. Ügyeljen arra, hogy törölje a jelölését **ügyfelek ellenőrizze a visszavont tanúsítványok listáját (CRL) a helyrendszerekhez**. Ez a beállítás csak lenne szükséges, ha volt nyilvánosan közzétételt a CRL-t.
5. Kattintson az **OK** gombra.

#### <a name="add-the-cloud-proxy-connector-point"></a>Adja hozzá a felhőbeli proxy összekötőpontja

A felhőbeli proxy összekötőpontja egy új helyrendszer-szerepkör Felhőbeli proxyszolgáltatás való kommunikációhoz. A felhőbeli proxy összekötőpontja hozzáadásához kövesse az utasításokat a [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](../../core/servers/deploy/configure/add-site-system-roles.md).

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>A felhőbeli proxy forgalom szerepkörök konfigurálása

Az utolsó lépés a Felhőbeli proxyszolgáltatás beállítása, hogy a felhőbeli proxy forgalom fogadására a helyrendszer-szerepkörök konfigurálása. A technikai előzetes 1606 csak a felügyeleti pont, a terjesztési pont és a szoftver frissítés pont szerepkörök támogatottak Felhőbeli proxyszolgáltatást. Minden egyes szerepkör külön-külön kell konfigurálni.

1. Nyissa meg a Configuration Manager konzol **Adminisztráció > Helykonfiguráció > kiszolgálók és Helyrendszerszerepkörök**.
2. Kattintson a helyrendszer-kiszolgáló proxy felhőforgalom konfigurálni szeretné a szerepkörhöz.
3. Kattintson a szerepkört, majd a **tulajdonságok**.
4. Szerepkör tulajdonságai alapján ügyfélkapcsolatokat, válassza a **HTTPS**, melletti jelölőnégyzetet **engedélyezése a Configuration Manager felhő Proxy forgalom**, és kattintson a **OK**. Ismételje meg ezeket a lépéseket a fennmaradó szerepkörök.

#### <a name="check-status-on-a-client-on-the-internet"></a>Ellenőrizze az interneten lévő ügyfél állapotát

A szolgáltatás és a szerepkörök teljesen konfigurálása után, belső ügyfelek kap a következő helyére vonatkozó kérelmet a Felhőbeli proxyszolgáltatás helyét. Ügyfelek frissített helyinformációkkal majd képes kommunikálni a Configuration Manager az interneten. A lekérdezési ciklus helyére irányuló kérelmek 24 óránként van. Ha nem szeretné a szokásos módon ütemezett helyére vonatkozó kérelmet. várja meg, az SMS Ügynökállomás szolgáltatás (ccmexec.exe) a számítógép újraindításával kényszerítheti a kérelmet.

Után az ügyfelek az új helyére vonatkozó információkat a Felhőbeli proxyszolgáltatás rendelkezik, próbálja meg, amelyeket már nem a belső magánhálózaton ügyfelek állapotának ellenőrzése, de rendelkezik Internet-hozzáféréssel. Felhőbeli proxyszolgáltatás forgalmat is ellenőrizheti a **felügyeleti > Felhőszolgáltatások > Felhőbeli proxyszolgáltatás**, jelölje ki a szolgáltatás a lista ablaktáblájában, és a forgalmi információk megtekintése a részleteket tartalmazó ablaktáblán.   

## <a name="manage_o365"></a>Kezelheti az Office 365-ügyfélügynök a Configuration Managerben  

Technical Preview 1606 indítása, használhatja a Configuration Manager ügyfélügynök-beállítást, a Csoportházirend helyett az Office 365 ügyfelek kapják a frissítéseket a Configuration Manager alkalmazásból. Miután konfigurálja ezt a beállítást, és Office 365-frissítéseket, a Configuration Manager ügyfélügynök Office 365-frissítések letöltése a terjesztési pontról, és telepítheti az Office 365 ügyfélügynök kommunikál. A Configuration Manager is az ügyfélügynök beállítása leltárt készít.

További információkért lásd: [Office 365 ProPlus kezelése frissíti](https://technet.microsoft.com/library/mt741983.aspx).

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>Állítsa be a Configuration Manager-ügyfél kezelése az Office 365-ügyfélügynök beállítása
1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **áttekintése** > **ügyfélbeállítások**.
2. Nyissa meg a megfelelő eszközbeállítások az ügyfélügynök engedélyezése. További információ az alapértelmezett és egyéni ügyfélbeállítások: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md).
3. Kattintson a **szoftverfrissítések** válassza **Igen** a a **az Office 365 ügyfélügynök-kezelés engedélyezéséhez** beállítás.  


## <a name="osdpreservedriveletter"></a>A OSDPreserveDriveLetter feladatütemezési változó elavult
A OSDPreserveDriveLetter feladatütemezési változó meghatározza, hogy a feladatütemezés a lemezkép célszámítógépre alkalmazásakor az operációs rendszer lemezképének WIM-fájljában rögzített meghajtóbetűjelet használja-e.
- Ez a feladatütemezési változó a Technical Preview 1606 elavult.

Az operációs rendszer központi telepítése során alapértelmezés szerint a Windows telepítő most meghatározza, hogy a legjobb meghajtóbetűjel (általában a C:) használatára. Adjon meg egy másik meghajtót használni szeretne, ha a hely az operációs rendszer alkalmazása feladatütemezési lépés a módosíthatja. Lépjen a **válassza ki a helyet, ahová szeretné alkalmazni az operációs rendszer** beállításnál válassza **adott logikai meghajtó betűjelét**, és válassza ki a használni kívánt meghajtót. A meghajtó rendelni, amelyben a levél úgy dönt, a célszámítógépen kell lennie. 

## <a name="updatesandservicing"></a>A módosítások a frissítések és karbantartás csomópont
A Technical Preview 1606 több olyan változás jelentek meg, amelyek érvényesek a Configuration Manager konzol frissítés és karbantartás:
- **Csomópont módosítása:**

    Az a **figyelés** munkaterületen, a **hely karbantartásának állapota** csomópont át lett nevezve a **frissítések és karbantartás állapot**.
- **További telepítési állapotát:**

    Amikor egy hely a frissítés telepítési állapotát, a konzol ettől kezdve különálló részleteit a következő műveleteket:
    - **Töltse le** (Ez vonatkozik csak a legfelső szintű helyet, ahol a szolgáltatás kapcsolódási pont helyrendszerszerepkör telepítve van)
    - **Replikáció**
    - **Előfeltételek ellenőrzése**
    - **Telepítés**

  Emellett most egyes lépéseihez szükséges további részletes információt, beleértve mely naplófájljában tekintse meg a további információt.  
-   **Új beállítás az újbóli előfeltétel-ellenőrzési hibák:**

    Mind a **felügyeleti** és **figyelés** munkaterületek, a **frissítés és karbantartás** csomópont tartalmazza egy új gombot a menüszalagon nevű **előfeltételekre vonatkozó figyelmeztetések mellőzését**.

    Előfeltételekre vonatkozó figyelmeztetések mellőzését a beállítás használata nélkül frissítések telepítésekor (a frissítések varázslóban), és, hogy a frissítés telepítése leáll állapotú **felelt**, választhatja ki **előfeltételekre vonatkozó figyelmeztetések mellőzését** elindítható egy adott frissítés telepítésére vonatkozóan, amely figyelmen kívül hagyja az előfeltételekkel kapcsolatos figyelmeztetéseket automatikus folytatása a szalagról.  



- **A frissítések tisztító megtekintése:**

    Amikor a **frissítés és karbantartás** csomópontot, ekkor megjelenik a legutóbb telepített frissítés, és más új frissítések érhetők el, hogy telepítse. Korábban telepített frissítések megtekintéséhez kattintson az új **előzmények** gomb, amely megjelenik a menüszalagon.  

-   **Átnevezett lehetőséget éles üzem előtti használathoz:**

    A frissítések és karbantartás csomópontjánál, a gomb mi neve **ügyfél beállításai** át lett nevezve, hogy **üzem előtti ügyfél előléptetése**.

