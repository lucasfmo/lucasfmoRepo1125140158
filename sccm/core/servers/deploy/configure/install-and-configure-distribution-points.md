---
title: "Terjesztési pontok kezelése |} Microsoft Docs"
description: "Terjesztési pontok használatával eszközök és felhasználók számára központilag telepített tartalmat (fájlokat és szoftvereket) tároló. Megtudhatja, hogyan történő telepítésére és konfigurálására."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8728d9f2ae63282a8f58b20105e488fb1a5ef55b
ms.openlocfilehash: 4c94e4de5bbfe621492e8682c9424a48eb38196d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>Telepítse és konfigurálja a terjesztési pontokat a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*
 
System Center Configuration Manager terjesztési pontok eszközök és felhasználók számára központilag telepített tartalmát (fájlokat és szoftvereket) telepítését. Terjesztési csoportok, amelyek megkönnyítik a terjesztési pontok kezelése, és a terjesztési pontra tartalom elosztásának módját is létrehozhat.  

 Ha Ön *új terjesztési pont telepítése* (a telepítési varázsló használatával) vagy *egy már létező terjesztési pont tulajdonságainak kezelésekor* (a terjesztési pont tulajdonságainak szerkesztésével), konfigurálhatja a terjesztési pont beállításait a legtöbb. Néhány beállítások állnak rendelkezésre, csak ha éppen telepítése vagy szerkesztését, de nem mindkettőn keresztül:  

-   Elérhető beállítások csak amikor telepít egy terjesztési pontot:  

    -   **Engedélyezése a Configuration Manager telepíteni az IIS a terjesztési pont számítógépén**

    -   **A terjesztési ponthoz tartozó lemezterület-beállítások konfigurálása**  

-   Rendelkezésre álló csak amikor szerkesztése a terjesztési pont tulajdonságainak beállításait:  

    -   **Terjesztésipontcsoport-kapcsolatok kezelése**  

    -   **A terjesztési pontra központilag telepített tartalom megtekintése**  

    -   **A terjesztési pontokra irányuló adatátvitelek sebességhatárainak**  

    -   **Terjesztési pontokra irányuló adatátvitelek ütemezéseinek beállítása**  

##  <a name="bkmk_install"></a>Terjesztési pont telepítése  
 Ki kell jelölnie egy helyrendszer-kiszolgálót a terjesztési pontok előtt tartalom elérhetők az ügyfélszámítógépek számára. Adja hozzá a terjesztési pont helyszerepkört egy új helyrendszer-kiszolgálóra, vagy a helyrendszer-szerepkör hozzáadása egy meglévő helyrendszer-kiszolgálóra.  

 Új terjesztési pont telepítésekor használhatja, amely végigvezeti a rendelkezésre álló beállítások telepítővarázsló. Mielőtt elkezdené, vegye figyelembe a következőket:  

-   Hozzon létre, és a terjesztési pont konfigurálása a következő biztonsági engedélyekkel kell rendelkeznie:  

    -   **Olvasási** a a **terjesztési pont** objektum  

    -   **Másolás terjesztési pontra** a a **terjesztési pont** objektum  

    -   **Módosítsa** a a **hely** objektum  

    -   **Tanúsítványok kezelése az operációs rendszer központi telepítésének** a a **hely** objektum  

-   Internet Information Services (IIS) telepítve kell lennie a terjesztési pontot futtató kiszolgáló. A helyrendszer-szerepkör telepítésekor a Configuration Manager telepítése és az IIS konfigurálása.  

Az alábbi eljárásokkal alapvető telepítéséhez, vagy módosítsa a terjesztési pont. Rendelkezésre álló konfigurációs beállításokat, lásd: a [a terjesztési pont](#bkmk_configs) című szakaszát.  

#### <a name="to-install-a-distribution-point"></a>A terjesztési pont telepítése  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.  

2.  A terjesztési pont helyrendszer-szerepkör hozzáadása egy új vagy meglévő helyrendszer-kiszolgálóra:  

    -   **Új helyrendszer-kiszolgáló**: Az a **Home** lap a **létrehozása** csoportjában válassza **helyrendszer-kiszolgáló létrehozása**. Megjelenik a Helyrendszer-kiszolgáló létrehozása varázsló.  

    -   **Meglévő helyrendszer-kiszolgáló**: Válassza ki a kiszolgáló, amelyen a terjesztési pont helyrendszerszerepkört telepíteni kívánja. Ha úgy dönt, hogy a kiszolgáló, az eredmények ablaktáblájában a kiszolgálóra már telepített helyrendszerszerepkörök listája jelenik meg.  

         Az a **Home** lap a **Server** csoportjában válassza **Helyrendszerszerepkörök hozzáadása**. Megjelenik a Helyrendszerszerepkörök hozzáadása varázsló.  

3.  Az **Általános** lapon adja meg a helyrendszer-kiszolgáló általános beállításait. Amikor a terjesztési pontot ad hozzá egy meglévő helyrendszer-kiszolgálóra, ellenőrizze a korábban beállított értékeket.  

4.  A a **Rendszerszerepkör kiválasztása** lapon, válassza ki **terjesztési pont** az elérhető szerepkörök listájából válassza ki, és **tovább**.  

5.  A varázsló következő lapjain, olvassa el a a [a terjesztési pont](#bkmk_configs) szakasz.  

     Például, ha szeretné telepíteni a terjesztési pontot lekéréses terjesztési pontként, dönthet **engedélyezése e terjesztési pont való lekérésére más terjesztési pontokról tartalom** , és végezze el a lekéréses terjesztési pontok azt igénylik, hogy további konfigurációs lépéseket.  

6.  A varázsló befejezése után a terjesztési pont helyszerepkört a helyrendszer-kiszolgáló kerül.  

#### <a name="to-change-a-distribution-point"></a>A terjesztési pont módosítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **terjesztési pontok**, majd válassza ki a konfigurálni kívánt terjesztési pontot.  

2.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

3.  Az információk a [a terjesztési pont](#bkmk_configs) szakasz a terjesztési pont tulajdonságainak szerkesztésekor.  

4.  Miután elvégezte a kívánt módosításokat, mentse a beállításokat, és a terjesztési pont tulajdonságainak bezárásához.  

##  <a name="bkmk_manage"></a>Terjesztésipont-csoportok kezelése  
 Terjesztésipont-csoportokat adja meg a tartalom terjesztése a terjesztési pontok logikai csoportosítása. Ezek a csoportok használatával kezelni és megfigyelni a tartalom több helyet kiszolgáló terjesztési pontok esetén központi helyről. Vegye figyelembe a következőket:

-   Egy terjesztésipont-csoporthoz a hierarchiában található bármelyik helyről felvehető egy vagy több terjesztési pont.  

-   A terjesztési pont egynél több terjesztésipont-csoporthoz is hozzáadhat.  

-   A terjesztésipont-csoporthoz tartalom terjesztésekor a Configuration Manager eljuttatja a tartalmat, minden olyan terjesztési pontokra, terjesztésipont-csoport tagjai.  

-   Ha egy terjesztési pontot a terjesztésipont-csoporthoz az első tartalomterjesztési után vesz fel, a Configuration Manager automatikusan elküldi az új tagnak.  

-   A terjesztésipont-csoporthoz gyűjtemény is társíthat. Gyűjteményhez tartalom terjesztésekor a Configuration Manager meghatározza, hogy mely terjesztésipont-csoportok társítva a gyűjteményben. A tartalom majd terjesztése az összes olyan terjesztési pontokra, amelyek a terjesztésipont-csoportnak tagjai.  

    > [!NOTE]  
    >  A gyűjteménybe, amennyiben majd társít a gyűjtemény új terjesztésipont-csoport terjesztése, újra kell terjesztenie a tartalmat a gyűjteményre ahhoz a tartalom eljusson az új terjesztésipont-csoporthoz.  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>Hozzon létre, és egy új terjesztésipont-csoport konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **terjesztésipont-csoportok**.  

2.  Az a **Home** lap a **létrehozása** csoportjában válassza **csoport létrehozása**.  

3.  Adja meg a nevét és leírását a terjesztésipont-csoportot.  

4.  Az a **gyűjtemények** lapra, majd **Hozzáadás**, válassza ki a terjesztésipont-csoporthoz társítani, és válassza a kívánt gyűjteményeket **OK**.  

5.  Az a **tagok** lapra, majd **Hozzáadás**, válassza ki a terjesztési pontokat a terjesztésipont-csoport tagjaként felvenni, és válassza a kívánt **OK**.  

6.  Válasszon **OK** a terjesztésipont-csoport létrehozásához.  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>Adja hozzá a terjesztési pontok és gyűjtemények társítása egy meglévő terjesztésipont-csoportot  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **terjesztésipont-csoportok**.  

2.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

3.  Az a **gyűjtemények** lapra, majd **Hozzáadás** ki a gyűjteményt, amelyet szeretne társítani a terjesztésipont-csoportot, és válassza a **OK**.  

4.  Az a **tagok** lapra, majd **Hozzáadás** jelölje be a terjesztési pontokat a terjesztésipont-csoport tagjaként felvenni, és válassza a kívánt **OK**.  

5.  Válasszon **OK** menti a módosításokat a terjesztésipont-csoporthoz.  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>Kijelölt terjesztési pontok hozzáadása egy új terjesztésipont-csoporthoz  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **terjesztési pontok**, majd válassza ki a terjesztési pontokat, amelyeket hozzá szeretne adni az új terjesztésipont-csoporthoz.  

2.  A a **Home** lap a **terjesztési pont** csoportjában bontsa ki a **kijelölt elemek hozzáadása**, és válassza a **kijelölt elemek hozzáadása új terjesztésipont-csoport**.  

3.  Adja meg a nevét és leírását a terjesztésipont-csoportot.  

4.  Az a **gyűjtemények** lapra, majd **Hozzáadás** ki a gyűjteményt, amelyet szeretne társítani a terjesztésipont-csoportot, és válassza a **OK**.  

5.  Az a **tagok** lapra, győződjön meg arról, hogy szeretné-e a Configuration Manager hozzáadja a felsorolt terjesztési pontokat a terjesztésipont-csoporthoz. Válasszon **Hozzáadás** adja hozzá a terjesztési pontokat, és válassza a **OK**.  

6.  Válasszon **OK** a terjesztésipont-csoport létrehozásához.  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>Kijelölt terjesztési pontok hozzáadása meglévő terjesztésipont-csoportokhoz  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **terjesztési pontok**, majd válassza ki a terjesztési pontokat, amelyeket hozzá szeretne adni az új terjesztésipont-csoporthoz.  

2.  A a **Home** lap a **terjesztési pont** csoportjában bontsa ki a **kijelölt elemek hozzáadása**, és válassza a **kijelölt elemek hozzáadása létező terjesztésipont-csoportokhoz**.  

3.  Az a **elérhető terjesztésipont-csoportok**, válassza ki a terjesztésipont-csoportokat, amelyhez a kijelölt terjesztési pontok tagként ad hozzá, és válassza a **OK**.  

##  <a name="bkmk_configs"></a>A terjesztési pont konfigurálása  
 Az egyes terjesztési pontok támogatják a számos különböző konfigurációt. Azonban nem mindegyik terjesztésipont-típus összes-konfigurációk támogatására. Felhőalapú terjesztési pontok például nem támogatja a tartalmak központi telepítése PXE-t vagy csoportos küldés engedélyezett. Bizonyos korlátozások információ található a következő témakörökben található:  

-   [Felhőalapú terjesztési pontot használ a System Center Configuration Managerrel](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [A lekéréses terjesztési pontok használata a System Center Configuration Managerrel](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

A következő szakaszok ismertetik a konfigurációkat, akkor a rendszer új terjesztési pont telepítésekor vagy egy már létező terjesztési pont tulajdonságainak szerkesztésével.  

### <a name="general"></a>Általános  
 A terjesztési pont általános beállításait konfigurálhatja:  

-   **Telepítse és konfigurálja az IIS, ha a Configuration Manager által igényelt**: Válassza ezt a beállítást választva engedélyezheti a Configuration Manager telepítése és konfigurálása az IIS a kiszolgálón, ha még nincs telepítve. Az összes terjesztési ponton telepíteni kell az IIS. Ha az IIS nincs telepítve a kiszolgálón, és nem adja meg ezt a beállítást, telepítenie kell az IIS a terjesztési pont sikeres telepítése előtt.  

    > [!NOTE]  
    >  Ez a beállítás csak új terjesztési pont telepítése esetén érhető el.  

- **BranchCache engedélyezése és konfigurálása a terjesztési pont számára**: Válassza ezt a beállítást, hogy a Windows BranchCache a terjesztésipont-kiszolgáló konfigurálása a Configuration Manager. A Windows BranchCache szolgáltatást a System Center Configuration Managerrel kapcsolatos további információkért lásd: [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache) a *támogatása a Windows-szolgáltatások és -hálózatok a System Center Configuration Managerben*.

-   **Konfigurálja, hogy ügyféleszközök hogyan kommunikáljanak a terjesztési pont**: Vannak előnyei és hátrányai HTTP és HTTPS használatával. További információkért lásd a "Ajánlott biztonsági eljárások a tartalomkezeléshez" [a System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   **Ügyfelek névtelen kapcsolódásának engedélyezése**: Ez a beállítás megadja, hogy a terjesztési pont engedélyezi anonim felhasználói kapcsolatok a Configuration Manager-ügyfelek a tartalomtárhoz.  

    > [!IMPORTANT]  
    >  A Windows Installer-alkalmazások javítása az ügyfélen sikertelen lehet, ha nem használja ezt a beállítást.  
    >   
    >  A Configuration Manager-ügyfél a Windows Installer-alkalmazás központi telepítésekor a Configuration Manager letölti a fájlt az ügyfél helyi gyorsítótárába. A fájlok törlődnek a telepítés befejezése után.
    >  
    >  A Configuration Manager-ügyfél a Windows Installer telepített alkalmazásai a Windows Installer forráslistáját a tartalom elérési útjával a társított terjesztési pontok tartalomtárában frissíti. Később Ha a Configuration Manager-ügyfelet a Programok telepítése és törlése elindítják a javítási műveletet, MSIExec próbálja elérni a tartalom elérési útját névtelen felhasználó használatával.  
    >   
    >  Azonban telepítheti a frissítést a Microsoft Tudásbázis következő cikke [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) és módosíthatja a beállításkulcsot a működés megváltoztatásához.  
    >   
    >  Az ügyfelek számára a frissítés telepítése után MSIExec éri el a tartalom elérési útvonalát a bejelentkezett felhasználói fiók használatával, ha nem adja meg a **ügyfelek névtelen kapcsolódásának engedélyezése** beállítást.  

-   **Hozzon létre egy önaláírt tanúsítványt, vagy importáljon egy nyilvános kulcsokra épülő infrastruktúra (PKI) ügyféltanúsítványt a terjesztési pont**: A tanúsítványnak a következő célok érdekében:  

    -   Mielőtt a terjesztési pont elküldi az állapotüzeneteket hitelesíti a terjesztési pontot egy felügyeleti pontra.  

    -   Ha a **PXE-támogatás engedélyezése ügyfeleknek** a mezőben a **PXE-beállítások** lapon rendszer elküldi a tanúsítványt a számítógépeknek, amelyeken a PXE-rendszerindítást végző, hogy csatlakozhassanak egy felügyeleti ponthoz az operációs rendszer telepítése során.  

    Ha a hely összes felügyeleti pontja a HTTP-Kapcsolatra van konfigurálva, hozzon létre egy önaláírt tanúsítványt. Ha a felügyeleti pontok a HTTPS-hez van konfigurálva, egy PKI-ügyféltanúsítvány importálása  

    A tanúsítvány importálásához jelöljön ki egy szabványos nyilvános kulcsú titkosítási (PKCS #12) fájlt, amely rendelkezik a következő követelményeket a Configuration Manager PKI-tanúsítványt:  

    -   Felhasználási célnak tartalmaznia ügyfél-hitelesítéshez.  

    -   A titkos kulcs exportálható engedélyezni kell.  

    > [!TIP]  
    >  Nincsenek a tanúsítvány tulajdonosára vagy a tulajdonos alternatív neve (SAN) megadott követelmények, és egy tanúsítvány pedig több terjesztési ponthoz is használhatja.  

     További információ a tanúsítványkövetelményekről: [A System Center Configuration Manager PKI-tanúsítványának követelményei](../../../../core/plan-design/network/pki-certificate-requirements.md).  

     Ez a tanúsítvány telepítését bemutató példát, a "Központi telepítése az ügyfél tanúsítványa a terjesztési pontok" szakaszában talál [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

-   **Engedélyezése e terjesztési pont használatát előzetesen beállított tartalomhoz**: Válassza ki az ezzel a beállítással engedélyezheti a terjesztési pont használatát előzetesen beállított tartalomhoz. Ha ez a beállítás be van jelölve, a tartalom terjesztésekor konfigurálhatja terjesztés működését. Választhat, hogy mindig a következők közül:

 - A terjesztési ponton lévő tartalmat manuálisan előkészíteni.
 - A csomag kezdő tartalmát, de a normál tartalomterjesztési folyamatot használja, ha a tartalom frissítéseit.
 - A normál tartalomterjesztési folyamatot használja a csomag tartalmához.  

### <a name="drive-settings"></a>Meghajtóbeállítások  

> [!NOTE]  
>  Ezek a beállítások csak új terjesztési pont telepítése esetén érhetők el.  

Adja meg a terjesztési pontra vonatkozó meghajtóbeállításokat. Legfeljebb két lemezmeghajtót a tartalomtár és két lemezmeghajtót a csomagmegosztás számára is konfigurálhatja. A Configuration Manager más meghajtókat is használhat, ha az első kettő eléri a beállított lemezterület-tartalékot. A **Meghajtóbeállítások** lap megadja a prioritását a merevlemez-meghajtók és a fennmaradó szabad lemezterület szükséges az egyes meghajtókon.  

-   **Lemezterület-tartalék (MB)**: Az ezzel a beállítással megadható határozza meg a minimális szabad területet a meghajtón a Configuration Manager egy másik meghajtót választ, és folytatja a másolást, amelynek előtt. Tartalomfájlok több meghajtóra is átnyúlhatnak.  

-   **Tartalom helye**: Adja meg a tartalom helyét. a tartalom és a csomagmegosztás megosztást. A Configuration Manager a tartalmat az elsődleges tartalomhelyre másolja át, amíg a szabad terület mennyisége el nem éri a megadott **lemezterület-tartalék (MB)**. Alapértelmezés szerint a tartalomhelyekhez beállítás van megadva **automatikus**. Az elsődleges tartalomhely a telepítéskor a legtöbb lemezterülettel rendelkező lemezmeghajtó van beállítva, és a másodlagos hely van hozzárendelve a második-legtöbb szabad lemezterülettel rendelkező lemezmeghajtó. Ha az elsődleges és másodlagos meghajtó eléri a lemezterület-tartalék értékét, a Configuration Manager választja ki a legtöbb szabad lemezterülettel rendelkező másik elérhető meghajtók közül, és folytatja a másolást.  

> [!NOTE]  
>  A Configuration Manager egy adott meghajtót, hozzon létre egy üres fájlt **no_sms_on_drive.sms** és a terjesztési pont telepítése előtt másolja azt a meghajtó gyökérmappájába.  

### <a name="pull-distribution-point"></a>Lekéréses terjesztési pont  
Ha úgy dönt, **engedélyezése e terjesztési pont való lekérésére más terjesztési pontokról tartalom**, hogyan számítógép lekérdezi a tartalmat a terjesztési pontra való működésének módosításához. A lekéréses terjesztési ponttá válik.  

Az egyes konfigurált lekéréses terjesztési pont meg kell adnia egy vagy több forrás terjesztési pontokat, amelyből a lekéréses terjesztési pont lekérdezi a tartalmat:  

-   Válasszon **Hozzáadás**, majd válassza ki legalább egy elérhető terjesztési pontot a forrás terjesztési pontként.  

-   Válasszon **eltávolítása** eltávolítja a kijelölt terjesztési pontot forrás terjesztési pontként.  

-   A nyílgombokkal úgy, hogy a sorrendet, amelyben a lekéréses terjesztési pont az ügyfelek a forrás terjesztési pontokat, amikor a lekéréses terjesztési pont tartalmat próbál továbbítani. A legkisebb értékű terjesztési pontok először próbál kapcsolódni.  

### <a name="pxe"></a>PXE  
Adja meg, hogy a PXE engedélyezve van a terjesztési ponton. Ha engedélyezi a PXE, a Configuration Manager szükség telepíti a Windows-telepítési szolgáltatásokat a kiszolgálón. Windows-telepítési szolgáltatások az operációs rendszer telepítése a PXE-rendszerindítást végző szolgáltatás. A terjesztési pont létrehozása a varázsló befejezése után a Configuration Manager telepít egy szolgáltatót a PXE-rendszerindítási funkcióit használó Windows-telepítési szolgáltatások.  

Ha úgy dönt, **PXE-támogatás engedélyezése ügyfeleknek**, a következő beállításokat:  

-   **A terjesztési pontot a bejövő PXE-kérésekre való válaszolás engedélyezése**: Adja meg, hogy engedélyezze a Windows-telepítési szolgáltatások reagáljon a PXE szolgáltatási kérelmekre. Ez a mező segítségével engedélyezheti vagy letilthatja a szolgáltatást anélkül, hogy eltávolítaná a PXE funkciót a terjesztési pontról.  

-   **Ismeretlen számítógépek támogatásának engedélyezése**: Adja meg, hogy a Configuration Manager nem tudja kezelni számítógépek támogatásának engedélyezése.  

-   **Jelszó kérése, amikor a számítógépek a PXE szolgáltatást használják**: A PXE típusú központi telepítések további biztonsága érdekében, hogy adjon meg egy erős jelszót.  

-   **Felhasználó-eszköz kapcsolat**: Adja meg, hogyan rendelje hozzá a felhasználókat a célszámítógéppel a PXE típusú központi telepítések a terjesztési pont. Válasszon egyet az alábbi lehetőségek közül:  

    -   **Felhasználó-eszköz kapcsolat automatikus jóváhagyással engedélyezze**: Válassza ezt a beállítást automatikusan társítja a felhasználókat a célszámítógéphez jóváhagyás kérése nélkül.  

    -   **Felhasználó-eszköz kapcsolat, a rendszergazda jóváhagyásától függően engedélyezze**: Válassza ezt a beállítást várni kelljen a rendszergazda felhasználó jóváhagyására felhasználókat a célszámítógéphez.  

    -   **Engedélyezze a felhasználó-eszköz kapcsolatot**: Válassza ki az ezzel a beállítással adhatja meg, hogy a felhasználók nem hozzárendelve a célszámítógépen.  

     További információk a felhasználó és eszköz közötti kapcsolatról: [Felhasználók és eszközök összekapcsolása felhasználó és eszköz közti kapcsolattal a System Center Configuration Managerben](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   **Hálózati interfészek**: Adja meg, hogy a terjesztési pont bármely hálózati interfész vagy csak bizonyos hálózati interfészek esetén válaszolhat a PXE-kérésekre. Ha a terjesztési pont bizonyos hálózati interfészek válaszol, meg kell adnia mindegyik hálózati interfész MAC-címét.  

-   **Adja meg a PXE-kiszolgáló válaszkésleltetés (másodperc)**: Adja meg másodpercben, hogy a több PXE képességű terjesztési pont használatakor mennyi késleltetési idő legyen a számítógép kérelmére reagálás előtt. Alapértelmezés szerint a Configuration Manager PXE szolgáltatási pont elsőként a hálózati PXE kérelmekre reagál.  

> [!NOTE]  
>  A PXE protokoll segítségével indítsa el az operációs rendszerek központi telepítését a Configuration Manager ügyfélszámítógépein. A Configuration Manager a PXE-képes terjesztési pont helyszerepkört használja az operációs rendszer telepítési folyamatát. A PXE képességű terjesztési pont úgy kell konfigurálni, hogy:
>
> 1. Válaszol a PXE rendszerindítási kérelmeket, amelyek a Configuration Manager-ügyfelek a hálózaton.
> 2. A Configuration Manager-infrastruktúrát meghatározza a megfelelő központi telepítési műveleteket kommunikál.  

### <a name="multicast"></a>Csoportos küldés  
Adja meg, hogy a terjesztési pontot a csoportos küldés. Ha a csoportos küldés, a Configuration Manager szükség telepíti a Windows-telepítési szolgáltatások a kiszolgálón.  

Ha a **engedélyezés csoportos küldés egyszerre több ügyfélnek adatokat küldeni** adja meg a következő beállításokat:  

-   **Csoportos kapcsolat fiókja**: Adja meg a fiókot használja a Configuration Manager adatbázis-kapcsolatok a csoportos küldéshez.  

-   **Csoportos Címbeállítások**: Adja meg a célszámítógépekre történő adatküldés IP-címét. Alapértelmezés szerint az IP-cím olyan DHCP-kiszolgálótól kérhető le, amelyen engedélyezve van a csoportos címek terjesztése. A hálózati környezettől függően 239.0.0.0 és 239.255.255.255 közötti tartományból egy adott IP-címek is megadhat.  

    > [!IMPORTANT]  
    >  Az Ön által konfigurált IP-címek által az operációs rendszer lemezképét kérő célszámítógépeknek elérhetőnek kell lennie. Győződjön meg arról, hogy az útválasztók és tűzfalak engedélyezik a csoportos küldéssel továbbított forgalmat a célszámítógép és a helykiszolgáló között.  

-   **UDP-porttartomány csoportos küldéshez**: Adja meg a tartomány a User Datagram Protocol (UDP) a célszámítógépekre történő adatküldéshez használt portokat.  

    > [!IMPORTANT]  
    >  Az UDP-portok által az operációs rendszer lemezképét kérő célszámítógépeknek elérhetőnek kell lennie. Győződjön meg arról, hogy az útválasztók és tűzfalak engedélyezik a csoportos küldéssel továbbított forgalmat a célszámítógép és a helykiszolgáló között.  

-   **Ügyfél átviteli sebessége**: Az a célszámítógépekre történő adatletöltéshez használt átviteli sebesség kiválasztására.  

-   **Ügyfelek maximális**: Adja meg a célszámítógépeken, amelyek a terjesztési pontról töltheti le az operációs rendszer maximális számát.  

-   **Ütemezett csoportos küldés**: Adja meg, hogy a Configuration Manager szabályozza, mikor kell elkezdeni az operációs rendszerek telepítését a célszámítógépekre. Adja meg a következő beállításokat:  

    -   **Munkamenet indításának késleltetése (perc)**: Adja meg percben, amely a Configuration Manager vár, mielőtt válaszol az első telepítési kérésre.  

    -   **Minimális munkamenetméret (ügyfelek)**: Adja meg, hány kérésnek kell érkeznie, mielőtt Configuration Manager az operációs rendszer központi telepítését megkezdené.  

> [!NOTE]  
>  Csoportos központi telepítést kíméli a sávszélességet, mivel párhuzamosan küldi adatok több Configuration Manager-ügyfelek az adatok másolatát küldése minden egyes ügyfélnek külön kapcsolaton keresztül helyett. Az operációs rendszer központi telepítéséhez csoportos küldés használatával kapcsolatos további információkért lásd: [használjon csoportos Windows központi telepítése a hálózaton a System Center Configuration Managerrel](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

### <a name="group-relationships"></a>Csoportok közötti kapcsolatok  

> [!NOTE]  
>  Ezek a beállítások csak korábban telepített terjesztési pont tulajdonságainak szerkesztése esetén érhetők el.  

A terjesztésipont-csoportokat, amelynek tagja a terjesztési pont kezeléséhez.  

Adhatja hozzá a terjesztési pont tagként egy meglévő terjesztésipont-csoporthoz, **Hozzáadás**. Válassza ki egy meglévő terjesztésipont-csoportot a listában a **terjesztésipont-csoportok hozzáadása** párbeszédpanel mezőbe, majd válassza a **OK**.  

A terjesztési pont eltávolítása a terjesztésipont-csoportot, a listában jelölje ki a terjesztésipont-csoportot, és válassza **eltávolítása**.  

### <a name="content"></a>Tartalom  

> [!NOTE]  
>  Ezek a beállítások csak korábban telepített terjesztési pont tulajdonságainak szerkesztése esetén érhetők el.  

A terjesztési pontra elhelyezett tartalmak kezelésére szolgál. A **központi telepítési csomagok** szakasz a terjesztési pontra helyezett csomagok listáját tartalmazza. Válassza ki a csomagot a listából, és hajtsa végre a következő műveleteket:  

-   **Érvényesítése**: Elindítja a csomagban lévő tartalomfájlok integritásának ellenőrzését. A tartalomérvényesítési folyamat eredményeinek megtekintéséhez a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, majd válassza a **tartalom állapota** csomópont.  

-   **Továbbterjesztés**: A terjesztési pontra a csomagban lévő összes tartalomfájlt átmásolja, és felülírja a meglévő fájlokat. Ez a művelettel általában a csomag tartalomfájljainak javítására.  

-   **Távolítsa el**: Eltávolítja a tartalomfájlokat a terjesztési pont a csomag.  

### <a name="content-validation"></a>Tartalomérvényesítés  
Adja meg, hogy a terjesztési ponton lévő tartalomfájlok integritásának ellenőrzését ütemezésének beállításához. Ha engedélyezi a tartalomérvényesítési ütemezés szerint, a Configuration Manager az ütemezett időpontban elindítja a folyamatot, és a terjesztési pont összes tartalmát ellenőrzi. A tartalomérvényesítési prioritás is konfigurálhatja. Alapértelmezés szerint a prioritás van beállítva, **legalacsonyabb**.  

A tartalomérvényesítési folyamat eredményeinek megtekintéséhez a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, majd válassza a **tartalom állapota** csomópont. A tartalom az egyes csomagtípusok (például alkalmazás, szoftverfrissítési csomag és rendszerindító lemezkép) jelenik meg.  

> [!WARNING]  
>  Bár a tartalomérvényesítés ütemezését a számítógép helyi ideje használatával adja meg, a Configuration Manager konzol UTC szerint jeleníti meg az ütemezést.  

### <a name="boundary-group"></a>Határcsoport  
Kezelheti a határcsoportok, amelyekhez a terjesztési pont hozzá van rendelve. Határcsoportokat társíthat a terjesztési pont. A tartalomterjesztés során az ügyfelek a határcsoport a terjesztési ponthoz társított a tartalom forráshelyeként használni kell lennie.

Egyéb rendelkezések:

- 1610 verzióban előtt ellenőrizheti a **engedélyezése az ügyfelek számára a helyrendszer tartalék forráshelyeként használják a tartalom** ahhoz, hogy a csoportok visszatérjenek, és a terjesztési pontokat használják a forráshely tartalom Ha érhetők el más terjesztési pontoktól ezeken a határcsoportokon kívüli ügyfelek mezőbe. A határcsoportok kapcsolatos további információkért lásd: [határcsoportjainak, 1511-es, a 1602-es és a 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606). Előnyben részesített terjesztési pontokra, lásd: [a System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).

- 1610 vagy újabb verziója, a határcsoporthoz konfigurálását *kapcsolatok* , adja meg, mikor és milyen határcsoportokhoz ügyfelek visszatérhetnek tartalom található. További információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


### <a name="schedule"></a>Ütemezés  

> [!NOTE]  
>  Ezek a beállítások csak korábban telepített terjesztési pont tulajdonságainak szerkesztése esetén érhetők el.  

> [!TIP]  
>  Ezen a lapon csak a helykiszolgáló számítógép távoli terjesztési pont tulajdonságainak szerkesztésekor érhető el.  

 Adja meg, hogy konfiguráljon egy ütemezést, amely korlátozza, ha a Configuration Manager küldhetnek adatokat a terjesztési pontra.  

> [!IMPORTANT]  
>  Az ütemezés az időzónát a küldő helyről, nem a terjesztési pont alapul.  

Az adatok korlátozásához válassza ki az időszakot, és válassza a következő lehetőségek egyikét a **rendelkezésre állási**:  

-   **Megnyitás minden prioritás esetén**: Meghatározza, hogy a Configuration Manager adatokat küld a terjesztési pont korlátozás nélkül.  

-   **Közepes és magas prioritás engedélyezése**: Meghatározza, hogy a Configuration Manager csak a közepes- és magas prioritású adatokat küldi el a terjesztési pontra.  

-   **Csak magas prioritású**: Meghatározza, hogy a Configuration Manager csak magas prioritású adatokat küld a terjesztési pontra.  

-   **Lezárt**: Meghatározza, hogy a Configuration Manager nem küld adatokat a terjesztési pontra.  

Adatokat prioritás szerint korlátozhatja, vagy zárja le a kapcsolatot az adott időszakokra.  

### <a name="rate-limits"></a>Sebességhatárok  

> [!NOTE]  
>  Ezek a beállítások csak korábban telepített terjesztési pont tulajdonságainak szerkesztése esetén érhetők el.  

> [!TIP]  
>  Ezen a lapon csak a helykiszolgáló számítógép távoli terjesztési pont tulajdonságainak szerkesztésekor érhető el.  

Adja meg, akkor használja, ha a Configuration Manager átvitte a tartalmat a terjesztési pontra a hálózati sávszélesség szabályozására a sebességhatár beállításával. Az alábbi lehetőségek közül választhat:  

-   **Korlátlan e célra történő küldéskor**: Ezzel a beállítással megadhatja, hogy a Configuration Manager a terjesztési pont a sebesség korlátozása nélkül küldhet tartalmakat.  

-   **Impulzusos mód**: Ez a beállítás a terjesztési pontra küldött adatblokkok méretét határozza meg. Emellett az egyes adatblokkok küldése közötti késleltetés is megadható. Használja ezt a beállítást, ha a terjesztési pontra nagyon alacsony sávszélességű hálózati kapcsolaton keresztül kell adatokat küldenie. Például lehetséges, hogy az adatküldés 1 KB adatot öt másodpercenként, függetlenül a a kapcsolat sebességétől vagy egy adott időben a használatát.  

-   **A megadott maximális átviteli sebességre korlátozva óránként**: Adja meg ezt a beállítást szeretné, hogy a konfigurált időszázalék csak az Ön által konfigurált szerint küldjön adatokat egy terjesztési pontot. Ha ezt a beállítást használja, a Configuration Manager határozza meg a hálózaton elérhető sávszélességet, hanem osztja az adatküldés. Majd adatküldést egy rövid ideig tartó, amely idő, amikor a rendszer nem küld adatokat Időblokkok következnek. Például, ha a maximális sebesség értéke **50 %**, a Configuration Manager ideig adatokat küld egy adott időn belül nem történik adatküldés egy ugyanannyi ideig követ. A rendszer ilyenkor nem veszi figyelembe az adatok tényleges mennyiségét vagy az adatblokk méretét. Ehelyett csak az adatküldés idejének kezelésére kerül sor.  

