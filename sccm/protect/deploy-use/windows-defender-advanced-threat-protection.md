---
title: "A Windows Defender komplex veszélyforrások elleni védelem |} Microsoft Docs"
description: "Megtudhatja, hogyan kezelhetik és megfigyelhetik a Windows Defender Advanced Threat Protection, egy új szolgáltatás, amely segít a vállalatok számára a speciális támadások válaszolni."
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
caps.latest.revision: 5
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 237dc9cbccb973720a633490f096aed4bc16d183
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="windows-defender-advanced-threat-protection"></a>A Windows Defender komplex veszélyforrások elleni védelem

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager (aktuális ág) 1606 verziója verziótól kezdődően az Endpoint Protection segítségével kezelni és megfigyelni a Windows Defender Advanced Threat Protection (ATP. A Windows Defender ATP egy új szolgáltatás, amely segítségére lesz a vállalatok számára, hogy észlelni, vizsgálja meg és a hálózat a speciális támadások válaszolni.  További információ [Windows Defender ATP](http://aka.ms/technet-wdatp). A Configuration Manager házirendek segítenek bevezetésében és a figyelő által felügyelt Windows 10 1607. verzió (build 14328) vagy újabb.

A Windows Defender ATP rendszer szolgáltatása a [Windows Security Center](https://securitycenter.windows.com). Hozzáadása, és egy ügyfél-bevezetési konfigurációs fájl telepítésével, a Configuration Manager központi telepítési állapotát és a Windows Defender ATP-ügynök állapota figyelheti. A Windows Defender ATP csak a Configuration Manager-ügyfelet futtató számítógépeken támogatott. A helyszíni mobileszköz-felügyelet és az Intune hibrid MDM által felügyelt számítógépek nem támogatottak.

 **Előfeltételek**  

-   Előfizetés a Windows Defender Advanced Threat Protection online szolgáltatáshoz  

-   Windows 10 1607 és újabb verzióit futtató ügyfelek  

## <a name="how-to-create-an-onboarding-configuration-file"></a>Az előkészítési konfigurációs fájl létrehozása  

 1.  Jelentkezzen be a [Windows Defender ATP online szolgáltatás](https://securitycenter.windows.com/)   

 2.  Kattintson a **végpont felügyeleti** menüpont.  

 3.  Válassza ki **System Center Configuration Manager (aktuális ág) verzió 1606** kattintson **letöltőcsomag**.  

 4.  Töltse le a tömörített (.zip) fájlt, és csomagolja ki annak tartalmát.

> [!IMPORTANT]
> A Windows Defender ATP-konfigurációs fájl tartalmaz bizalmas adatokat, amelyek biztonságos kell tartani.

## <a name="onboard-devices-for-windows-defender-atp"></a>A Windows Defender ATP az eszközök regisztrálásához  

1.  A Configuration Manager-konzolon lépjen a **eszközök és megfelelőség** > **áttekintése** > **Endpoint Protection** > **a Windows Defender ATP-házirendek** kattintson **létrehozása a Windows Defender ATP-házirend**. A Windows Defender ATP-házirend varázsló megnyílik.  

2.  Típus a **neve** és **leírás** a Windows Defender ATP-házirend, és válassza ki a **bevezetési**. Kattintson a **Tovább** gombra.  

3.  **Tallózás** a szervezet Windows Defender ATP-felhőszolgáltatásokat igénybe vevő által biztosított konfigurációs fájlból. Kattintson a **Tovább** gombra.  

4.  Adja meg a fájlminták gyűjtött és megosztott elemzéshez felügyelt eszközökről.  

    -   **Egyik sem**   

    -   **Az összes fájltípus esetében**  

     Kattintson a **Tovább** gombra.  

5.  Tekintse át az összefoglalást, és fejezze be a varázslót.  

6.  Most már telepítheti a Windows Defender ATP-házirend a felügyelt ügyfélszámítógépek kattintva **telepítés**.  

## <a name="monitor-windows-defender-atp"></a>A Windows Defender ATP figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **biztonsági** majd **Windows Defender ATP**.  

2.  Tekintse át a Windows Defender Advanced Threat Protection-irányítópult.  

    -   **A Windows Defender ügynök telepítési állapota** – a száma és a Windows Defender ATP-házirend active előkészítve jogosult felügyelt ügyfélszámítógépek százaléka  

    -   **A Windows Defender ATP ügyfélállapot** – a Windows Defender ATP-ügynök állapota reporting számítógép ügyfeleinek százalékos aránya  

        -   **Kifogástalan** -megfelelően működik-e  

        -   **Inaktív** -nincsenek időszakban szolgáltatásnak küldött adatok  

        -   **Ügynök állapota** – a rendszer az ügynök a Windows szolgáltatás nem fut  

        -   **Nincs előkészítve** - házirend alkalmazta, de az ügynök nem jelentette a házirend előkészítéséről  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Hogyan hozhat létre és telepíthet egy kivezetési konfigurációs fájl  

1.  Jelentkezzen be a [Windows Defender ATP online szolgáltatás](https://securitycenter.windows.com/)   

2.  Kattintson a **végpont felügyeleti** menüpont.  

3.  Válassza ki **System Center Configuration Manager (aktuális ág) verzió 1606** kattintson **végpont kivezetési**.  

4.  Töltse le a tömörített (.zip) fájlt, és csomagolja ki annak tartalmát. Kivezetési fájlok 30 napig érvényesek.

5.  A Configuration Manager-konzolon lépjen a **eszközök és megfelelőség** > **áttekintése** > **Endpoint Protection** > **a Windows Defender ATP-házirendek** kattintson **létrehozása a Windows Defender ATP-házirend**. A Windows Defender ATP-házirend varázsló megnyílik.  

6.  Típus a **neve** és **leírás** a Windows Defender ATP-házirend, és válassza ki a **kivezetési**. Kattintson a **Tovább** gombra.  

7.  **Tallózás** a szervezet Windows Defender ATP-felhőszolgáltatásokat igénybe vevő által biztosított konfigurációs fájlból. Kattintson a **Tovább** gombra.  

8.  Tekintse át az összefoglalást, és fejezze be a varázslót.  

9.  Most már telepítheti a Windows Defender ATP-házirend a felügyelt ügyfélszámítógépek kattintva **telepítés**.  

> [!IMPORTANT]
> A Windows Defender ATP konfigurációs fájlokat tartalmaz bizalmas adatokat, amelyek biztonságos kell tartani.

[A Windows Defender komplex veszélyforrások elleni védelem](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[A Windows Defender Advanced Threat Protection bevezetési problémák elhárítása](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)

