---
title: "Telepítse a Windows új számítógépre - Configuration Manager |} Microsoft Docs"
description: "Használja a Configuration Manager az operációs rendszer egy új (operációs rendszer nélküli) számítógépre telepítése a PXE, OEM vagy különálló adathordozó használatával."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5ad22d5-7df1-49c6-8a0f-db1c3f0cda19
caps.latest.revision: 8
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 584dad7d8b05a2da9f7a66b73028ae99ff1a594f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="install-a-new-version-of-windows-on-a-new-computer-bare-metal-with-system-center-configuration-manager"></a>A Windows új verziójának telepítése operációs rendszer nélküli új számítógépen a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör az általános lépések a System Center Configuration Managerben az operációs rendszer telepítéséhez egy új számítógépre. Ebben a forgatókönyvben számos különböző központi telepítési módszer, például a PXE, OEM vagy különálló adathordozó segítségével történő telepítés közül választhat. Ha biztos abban, hogy ez az a megfelelő központi telepítési módszer meg, tekintse meg [vállalati operációs rendszerek központi telepítésének forgatókönyvei](scenarios-to-deploy-enterprise-operating-systems.md).  

A következő szakaszok egyikét használhatja egy meglévő számítógép a Windows egy új verziójára való frissítéséhez.  

##  <a name="BKMK_Plan"></a> Terv  

-   **Infrastruktúrával kapcsolatos követelmények tervezése és implementálása**  

     Nincsenek több infrastruktúrával kapcsolatos követelménynek kell teljesülnie operációs rendszerek, például a Windows ADK, Windows-telepítési szolgáltatások (WDS), támogatott merevlemez-konfigurációk telepítése előtt. További információkért lásd: [operációs rendszer központi telepítésének infrastrukturális követelményei](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).

##  <a name="BKMK_Configure"></a> Konfigurálás  

1.  **Rendszerindító lemezkép előkészítése**  

     A rendszerindító lemezképek a számítógépet Windows PE környezetben (egy korlátozott összetevőkkel és szolgáltatásokkal rendelkező minimális méretű operációs rendszerrel) indítják el, mely képes a teljes Windows operációs rendszert telepíteni a számítógépre.   Operációs rendszerek központi telepítésekor ki kell választania egy használni kívánt rendszerindító lemezképet, és azt továbbítania kell egy terjesztési pontra. A következőkkel készítheti elő a rendszerindító lemezképet:  

    -   Rendszerindító lemezképek kapcsolatos további információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

    -   A rendszerindító lemezképek testreszabásával kapcsolatos további információkért lásd: [rendszerindító lemezképek testreszabása](../get-started/customize-boot-images.md).  

    -   A rendszerindító lemezkép terjesztése a terjesztési pontokra. További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Operációs rendszer lemezképének előkészítése**  

     Az operációs rendszer lemezképe tartalmazza az operációs rendszer a célszámítógépen való telepítéséhez szükséges fájlokat. A következőkkel készítheti elő az operációs rendszer lemezképét:  

    -   Az operációs rendszer lemezképének létrehozásával kapcsolatos további tudnivalókért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).

    -   Továbbítsa az operációs rendszer lemezképét a terjesztési pontokra. További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).

3.  **Feladatütemezés létrehozása az operációs rendszer hálózaton keresztül történő központi telepítéséhez**  

     Egy feladatütemezéssel automatizálhatja az operációs rendszer hálózaton keresztül történő telepítését. Az alábbi témakörben található lépésekkel [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md) segítségével hozza létre a feladatütemezést az operációs rendszer központi telepítését. A kiválasztott központi telepítési módszertől függően előfordulhat, hogy további szempontokat is figyelembe kell venni a feladatütemezéshez.  

##  <a name="BKMK_Deploy"></a> Telepítés  

-   Az operációs rendszer központi telepítéséhez használja a következő módszerek egyikét:  

    -   [A Windows központi telepítése a hálózaton keresztül PXE használatával](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Windows központi telepítése a hálózaton keresztül csoportos küldés használatára](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Lemezkép létrehozása OEM gyára vagy helyi raktár számára](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Windows központi telepítése a hálózaton keresztül nélkül a különálló adathordozó használatával](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával](use-bootable-media-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Figyelő  

-   **A feladatütemezés központi telepítésének figyelése**  

     A feladatütemezési központi telepítés az operációs rendszer telepítésének figyeléséről lásd: [operációs rendszer központi telepítésének figyelése](monitor-operating-system-deployments.md).  

