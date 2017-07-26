---
title: "A Windows új verziójára meglévő számítógép frissítése |} Microsoft Docs"
description: "Többféle módszer a Configuration Manager használatával particionálása és formázása (Törlés) egy meglévő számítógép, és új operációs rendszer telepítése a számítógépre."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b189a346-8c0d-4870-a876-0719fbb0ab04
caps.latest.revision: 7
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: b247cbb68ed63a8eb99715a248686d68a28c53e2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="refresh-an-existing-computer-with-a-new-version-of-windows-using-system-center-configuration-manager"></a>Meglévő számítógép frissítése a Windows új verziójára a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör az általános lépések a System Center Configuration Manager particionálását és formázását (Törlés) egy meglévő számítógép és egy új operációs rendszer telepítéséhez a számítógépen. Ebben a forgatókönyvben számos különböző központi telepítési módszer, például a PXE, rendszerindító adathordozó vagy a Szoftverközpont használata közül választhat. Úgy is dönthet, hogy telepít egy állapotáttelepítési pontot a beállítások tárolásához, majd visszaállítja azokat az új operációs rendszerben annak telepítése után. Ha biztos abban, hogy ez az a megfelelő központi telepítési módszer meg, tekintse meg [vállalati operációs rendszerek központi telepítésének forgatókönyvei](scenarios-to-deploy-enterprise-operating-systems.md).  

 A következő szakaszok egyikét használhatja egy meglévő számítógép a Windows egy új verziójára való frissítéséhez.  

##  <a name="BKMK_Plan"></a> Terv  

-   **Infrastruktúrával kapcsolatos követelmények tervezése és implementálása**  

     Nincsenek több infrastruktúrával kapcsolatos követelménynek kell teljesülnie telepítése előtt, például a Windows ADK, felhasználói Felhasználóáttelepítő (USMT), Windows-telepítési szolgáltatások (WDS), a támogatott operációs rendszerek merevlemez-konfigurációk stb. További információkért lásd: [operációs rendszer központi telepítésének infrastrukturális követelményei](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Állapotáttelepítési pont telepítése (csak a beállítások átvitele esetén szükséges)**  

     Ha rögzíteni szeretné a meglévő számítógép beállításait, majd vissza szeretné állítani azokat az új operációs rendszerben, telepítenie kell egy állapotáttelepítési pontot. További információkért lásd: [állapotáttelepítési pont](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

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

     Egy feladatütemezéssel automatizálhatja az operációs rendszer hálózaton keresztül történő telepítését. Az alábbi témakörben található lépésekkel [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md) létrehozása az operációs rendszer központi telepítéséhez használandó feladatütemezést. A kiválasztott központi telepítési módszertől függően előfordulhat, hogy további szempontokat is figyelembe kell venni a feladatütemezéshez.  

    > [!NOTE]  
    >  Ebben a forgatókönyvben a feladatütemezés formázza és particionálja a számítógép merevlemezeit. A felhasználói beállítások rögzítéséhez egy állapotáttelepítési pontot kell használnia, és a Feladatütemezés létrehozása varázsló **Állapotáttelepítés** lapján be kell jelölnie a **Felhasználói beállítások és fájlok mentése állapotáttelepítési pontra** lehetőséget. A felhasználói beállítások és fájlok helyi mentése, ha ezek elvesznek, ha a merevlemez formázása és a Configuration Manager nem tudja visszaállítani a beállításokat. További információkért lásd: [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

##  <a name="BKMK_Deploy"></a> Telepítés  

-   Az operációs rendszer központi telepítéséhez használja a következő módszerek egyikét:  

    -   [A Windows központi telepítése a hálózaton keresztül PXE használatával](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Windows központi telepítése a hálózaton keresztül csoportos küldés használatára](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Lemezkép létrehozása OEM gyára vagy helyi raktár számára](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Windows központi telepítése a hálózaton keresztül nélkül a különálló adathordozó használatával](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [Windows központi telepítése a hálózaton keresztül a Szoftverközpont használatával](use-software-center-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Figyelő  

-   **A feladatütemezés központi telepítésének figyelése**  

     A feladatütemezési központi telepítés az operációs rendszer telepítésének figyeléséről lásd: [operációs rendszer központi telepítésének figyelése](monitor-operating-system-deployments.md).  

