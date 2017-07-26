---
title: "Az Endpoint Protection kártevő-definíciók hálózati megosztásról |} Microsoft Docs"
description: "Megtudhatja, hogyan manuálisan töltse le a legújabb definíciófrissítéseket a Microsofttól, majd konfigurálja az ügyfelek számára, hogy letöltsék ezeket a definíciókat."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ddef4d2a-f481-4020-9ddd-9cca5f9795cb
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 110bd9a9d04b27ef6794145fae66dbd910308bdc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-a-network-share-for-configuration-manager"></a>Az Endpoint Protection kártevő-definíciók letöltése egy hálózati megosztáson a Configuration Manager engedélyezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Manuálisan is letöltheti a legújabb definíciófrissítéseket a Microsofttól, majd konfigurálhatja az ügyfeleket, hogy letöltsék ezeket a definíciókat a hálózaton lévő megosztott mappából. Ha ezt a frissítési forrást használja, a felhasználók is kezdeményezhetnek definíciófrissítéseket.

> [!NOTE]
>  Az ügyfeleknek olvasási hozzáféréssel kell rendelkezniük a megosztott mappához, hogy le tudják tölteni a definíciófrissítéseket.

 Töltse le a definíció- és keresőmotor-frissítéseket a fájlmegosztás kapcsolatos további információkért lásd: [telepítse a legújabb Microsoft kártevőirtó- és kémprogram-elhárító szoftvert](http://www.microsoft.com/security/portal/Definitions/HowToForeFront.aspx).

## <a name="to-configure-definition-downloads-from-a-file-share"></a>Definíciók fájlmegosztásból történő letöltésének konfigurálása

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.

2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki az **Endpoint Protection**csomópontot, majd kattintson a **Kártevőirtó-házirendek**lehetőségre.

3.  Nyissa meg az **Alapértelmezett kártevőirtó-házirend** tulajdonságlapját, vagy hozzon létre egy új kártevőirtó-házirendet. Kártevőirtó-házirendek létrehozásával kapcsolatos további információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).

4.  A kártevőirtó Tulajdonságok párbeszédpanelének **Definíciófrissítések** szakaszában kattintson a **Forrás beállítása**elemre.

5.  **A definíciófrissítések forrásainak konfigurálása** párbeszédpanelen jelölje ki a **Frissítések az UNC-fájlmegosztásokból**lehetőséget.

6.  Kattintson az **OK** gombra **A definíciófrissítések forrásainak konfigurálása** párbeszédpanel bezárásához.

7.  Kattintson az **Elérési útvonalak beállítása**lehetőségre, majd adjon hozzá egy vagy több UNC elérési útvonalat a hálózati megosztás definíciófrissítési fájljainak helyéhez **A definíciók frissítése UNC elérési útvonalainak konfigurálása** párbeszédpanelen.

8.  Kattintson az **OK** gombra **A definíciók frissítése UNC elérési útvonalainak konfigurálása** párbeszédpanel bezárásához.


> [!div class="button"]
[Következő lépés >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Vissza >](endpoint-configure-alerts.md)

