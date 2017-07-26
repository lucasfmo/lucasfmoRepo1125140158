---
title: "Meglévő számítógép cseréje és a beállítások átvitele |} Microsoft Docs"
description: "A Configuration Managerben választhat központi telepítési módszer, rendszerindító adathordozó, a csoportos küldés vagy a Szoftverközpont, például egy meglévő számítógép cseréje egy új számítógépre."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d28f4363-9e8a-4c54-9cb7-0594fabfff26
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 243433980e1720fd468d52a4a61f2c3a8e3659b5
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="replace-an-existing-computer-and-transfer-settings-with-system-center-configuration-manager"></a>Meglévő számítógép cseréje és beállítások átvitele a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör az általános lépések a System Center Configuration Manager egy meglévő számítógép cseréje egy új számítógépre. Ebben a forgatókönyvben számos különböző központi telepítési módszer, például a rendszerindító adathordozó, a csoportos küldés vagy a Szoftverközpont használata közül választhat. Úgy is dönthet, hogy telepít egy állapotáttelepítési pontot a beállítások tárolásához, majd visszaállítja azokat az új operációs rendszerben annak telepítése után. Ha biztos abban, hogy ez az a megfelelő központi telepítési módszer meg, tekintse meg [vállalati operációs rendszerek központi telepítésének forgatókönyvei](scenarios-to-deploy-enterprise-operating-systems.md).  

 A következő szakaszok egyikét használhatja egy meglévő számítógép a Windows egy új verziójára való frissítéséhez.  

##  <a name="BKMK_Plan"></a> Terv  

-   **Infrastruktúrával kapcsolatos követelmények tervezése és implementálása**  

     Nincsenek több infrastruktúrával kapcsolatos követelménynek kell teljesülnie telepítése előtt, például a Windows ADK, felhasználói Felhasználóáttelepítő (USMT), Windows-telepítési szolgáltatások (WDS), a támogatott operációs rendszerek merevlemez-konfigurációk stb. További információkért lásd: [operációs rendszer központi telepítésének infrastrukturális követelményei](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)  

-   **Állapotáttelepítési pont telepítése (csak a beállítások átvitele esetén szükséges)**  

     Ha rögzíteni szeretné a meglévő számítógép beállításait, majd vissza szeretné állítani azokat az új operációs rendszerben, telepítenie kell egy állapotáttelepítési pontot. További információkért lásd: [állapotáttelepítési pont](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_Configure"></a> Konfigurálás  

1.  **Rendszerindító lemezkép előkészítése**  

     A rendszerindító lemezképek a számítógépet Windows PE környezetben (egy korlátozott összetevőkkel és szolgáltatásokkal rendelkező minimális méretű operációs rendszerrel) indítják el, mely képes a teljes Windows operációs rendszert telepíteni a számítógépre. Operációs rendszerek központi telepítésekor ki kell választania egy használni kívánt rendszerindító lemezképet, és azt továbbítania kell egy terjesztési pontra. A következőkkel készítheti elő a rendszerindító lemezképet:  

    -   Rendszerindító lemezképek kapcsolatos további információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

    -   A rendszerindító lemezképek testreszabásával kapcsolatos további információkért lásd: [rendszerindító lemezképek testreszabása](../get-started/customize-boot-images.md).  

    -   A rendszerindító lemezkép terjesztése a terjesztési pontokra. További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Operációs rendszer lemezképének előkészítése**  

     Az operációs rendszer lemezképe tartalmazza az operációs rendszer a célszámítógépen való telepítéséhez szükséges fájlokat. A következőkkel készítheti elő az operációs rendszer lemezképét:  

    -   Az operációs rendszer lemezképének létrehozásával kapcsolatos további tudnivalókért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

    -   Továbbítsa az operációs rendszer lemezképét a terjesztési pontokra. További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

3.  **Feladatütemezés létrehozása az operációs rendszer hálózaton keresztül történő központi telepítéséhez**  

     Egy feladatütemezéssel automatizálhatja az operációs rendszer hálózaton keresztül történő telepítését. Az alábbi témakörben található lépésekkel [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md) segítségével hozza létre a feladatütemezést az operációs rendszer központi telepítését. A kiválasztott központi telepítési módszertől függően előfordulhat, hogy további szempontokat is figyelembe kell venni a feladatütemezéshez.  

    > [!NOTE]  
    >  Ebben a forgatókönyvben állapotáttelepítési pontot is használhat a felhasználói beállítások rögzítéséhez és visszaállításához, vagy a helyi számítógépre is mentheti a fájlokat. További információkért lásd: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

##  <a name="BKMK_Deploy"></a> Telepítés  

-   Az operációs rendszer központi telepítéséhez használja a következő módszerek egyikét:  

    -   [Windows központi telepítése a hálózaton keresztül a Szoftverközpont használatával](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [Windows központi telepítése a hálózaton keresztül csoportos küldés használatára](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Lemezkép létrehozása OEM gyára vagy helyi raktár számára](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

## <a name="monitor"></a>Figyelő  

-   **A feladatütemezés központi telepítésének figyelése**  

     A feladatütemezési központi telepítés az operációs rendszer telepítésének figyeléséről lásd: [operációs rendszer központi telepítésének figyelése](monitor-operating-system-deployments.md).  

