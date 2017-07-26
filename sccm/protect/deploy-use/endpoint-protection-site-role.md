---
title: "Az Endpoint Protection pont helyrendszer-szerepkör létrehozása |} Microsoft Docs"
description: "Megtudhatja, hogyan konfigurálhatja az Endpoint Protection biztonsági és a Configuration Manager ügyfél-számítógépeken kártevő szoftverek kezeléséhez."
defintion: 
definition: 
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: 6e717bcbe5ef8c3f2efa717d0cebb9e675e7c127
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Az Endpoint Protection pont helyrendszer-szerepkör létrehozása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Az Endpoint Protection használata előtt telepítenie kell az Endpoint Protection-pont helyrendszerszerepkört. Csak egy helyrendszer-kiszolgálóra lehet telepíteni, és a központi adminisztrációs hely vagy önálló elsődleges hely hierarchiájának a tetejére kell telepíteni.

 Használja, attól függően, hogy a következő eljárásokkal egy új helyrendszer-kiszolgáló telepítése az Endpoint Protection vagy egy meglévő helyrendszer-kiszolgálót használ:
 - [Új helyrendszer-kiszolgáló telepítése](#new-site-system-server)
 - [Egy meglévő helyrendszer-kiszolgáló telepítése](#existing-site-system-server)

> [!IMPORTANT]
>  Ha telepíti az Endpoint Protection-pont, az Endpoint Protection-ügyfél telepítve van az Endpoint Protection-pontot üzemeltető kiszolgálón. Ezen az ügyfélen a szolgáltatások és a vizsgálatok le vannak tiltva, így az ügyfél párhuzamosan működhet a kiszolgálóra telepített más kártevőirtó megoldásokkal. Ha később e kiszolgáló felügyeletét, az Endpoint Protection engedélyezése és bármely harmadik féltől származó kártevőirtó megoldás eltávolítása választja, a harmadik féltől származó terméket nem lesznek eltávolítva. Ezeket a szoftvereket kézzel kell eltávolítania.

## <a name="new-site-system-server"></a>Új helyrendszer-kiszolgáló

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**lehetőségre.

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Helyrendszer-kiszolgáló létrehozása**lehetőségre.

4.  Az **Általános** lapon adja meg a helyrendszer általános beállításait, majd kattintson a **Tovább**gombra.

5.  A **Rendszerszerepkör kiválasztása** lapon az elérhető szerepkörök listájából válassza ki az **Endpoint Protection-pont** elemet, majd kattintson a **Tovább**gombra.

6.  Az **Endpoint Protection** oldalon jelölje be az **Elfogadom az Endpoint Protection licencfeltételeit** jelölőnégyzetet, majd kattintson a **Tovább**gombra.

    > [!IMPORTANT]
    >  Nem használhatja az Endpoint Protection a Configuration Manager kivéve, ha elfogadja a licencfeltételeket.

7.  Az a **felhőalapú szolgáltatás** lapon, válassza ki a szintet, amely küldeni a Microsoftnak, hogy új definíciók fejlesztését, és kattintson a kívánt **következő**.

    > [!NOTE]
    >  Ez a beállítás alapértelmezés szerint használt (korábbi nevén Microsoft Active Protection Service szolgáltatáshoz vagy a MAPS) felhőalapú szolgáltatás beállításait konfigurálja. Ezután egyéni beállításokat adhat meg minden létrehozott kártevőirtó-házirendhez. Felhő hálózatvédelmi szolgáltatását, a Súgó gombra a számítógépek nagyobb biztonságban úgy, hogy megadja a Microsoft kártevő minták, amelyek segítségével naprakész állapotban tarthassa a kártevőirtó-definíciókat a csatlakozás. Emellett ha igénybe veszi a felhőalapú szolgáltatás, az Endpoint Protection-ügyfél segítségével a dinamikus aláírási szolgáltatás új definíciók letöltése a Windows Update előtt. További információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).

8.  Fejezze be a varázslót.


## <a name="existing-site-system-server"></a>Meglévő helyrendszer-kiszolgáló

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

2.  A a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, kattintson **kiszolgálók és Helyrendszerszerepkörök**, majd jelölje ki az Endpoint Protection használni kívánt kiszolgálót.

3.  A **Kezdőlap** **Kiszolgáló** csoportjában kattintson a **Helyrendszerszerepkörök hozzáadása**elemre.

4.  Az **Általános** lapon adja meg a helyrendszer általános beállításait, majd kattintson a **Tovább**gombra.

5.  A **Rendszerszerepkör kiválasztása** lapon az elérhető szerepkörök listájából válassza ki az **Endpoint Protection-pont** elemet, majd kattintson a **Tovább**gombra.

6.  Az **Endpoint Protection** oldalon jelölje be az **Elfogadom az Endpoint Protection licencfeltételeit** jelölőnégyzetet, majd kattintson a **Tovább**gombra.

    > [!IMPORTANT]
    >  Nem használhatja az Endpoint Protection a Configuration Manager kivéve, ha elfogadja a licencfeltételeket.

7.  Az a **felhőalapú szolgáltatás** lapon, válassza ki a szintet, amely küldeni a Microsoftnak, hogy új definíciók fejlesztését, és kattintson a kívánt **következő**.

    > [!NOTE]
    >  Ez a beállítás a felhőalapú szolgáltatás (korábbi nevén MAPS), alapértelmezés szerint használt beállítások konfigurálása. Egyéni beállításokat adhat meg minden konfigurált kártevőirtó-házirendhez. További információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).

8.  Fejezze be a varázslót.

