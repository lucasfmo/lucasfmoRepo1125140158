---
title: "Az Endpoint Protection riasztásainak konfigurálása |} Microsoft Docs"
description: "Ismerje meg, hogy az Endpoint Protection-riasztások konfigurálása a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 7f4329b289b606dee5bf31aad8207de52667229f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Riasztások konfigurálása az Endpoint Protection a Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Konfigurálhatja az Endpoint Protection-riasztások a Microsoft System Center Configuration Manager a rendszergazda felhasználók értesítése, ha a hierarchiában előforduló meghatározott események, például a kártevők általi fertőzésről. Értesítések megjelenítése az Endpoint Protection-irányítópulton a Configuration Manager konzolján a a **riasztások** csomópontjának a **figyelés** munkaterületen vagy e-mailben a megadott felhasználóknak.

 Riasztások konfigurálása az Endpoint Protection a Configuration Manager ebben a témakörben használja a következő lépések és további eljárásaival.

> [!IMPORTANT]
>  Rendelkeznie kell a **biztonság kényszerítése** engedéllyel a gyűjteményekhez, hogy az Endpoint Protection riasztásainak konfigurálása.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>A Configuration Managerben az Endpoint Protection riasztások konfigurálásának lépései

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.

2.  Kattintson az **Eszközök és megfelelőség** munkaterületen az **Eszközgyűjtemények**elemre.

3.  Válassza ki az **Eszközgyűjtemények** listában azt a gyűjteményt, amelyre vonatkozóan a riasztásokat konfigurálni szeretné, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.

    > [!NOTE]
    >  Felhasználógyűjteményekre vonatkozóan nem lehet riasztásokat konfigurálni.

4.  A a **riasztások** lapján a *< gyűjteménynév\>***tulajdonságok** párbeszédpanelen jelölje ki **az Endpoint Protection irányítópultjában tekintse meg a gyűjteményt** Ha meg szeretné-e tekinteni a gyűjteményre vonatkozó kártevőirtó-műveletek részleteit a **figyelés** a Configuration Manager konzol munkaterületén.

    > [!NOTE]
    >  Ez a beállítás nem érhető el a **Minden rendszer** gyűjteményhez.

5.  A a **riasztások** lapján a *< gyűjteménynév\>***tulajdonságok** párbeszédpanel, kattintson a **Hozzáadás**.

6.  Az a **új gyűjteménnyel kapcsolatos riasztások hozzáadása** párbeszédpanel a **riasztás létrehozása esetén a következő feltételek fennállásakor** területen válassza ki a megjeleníteni kívánt elő, ha a megadott Endpoint Protection események fordulhat elő, és kattintson a Configuration Manager riasztásokat **OK**.

7.  Az a **feltételek** listája a **riasztások** lapra, jelölje ki minden egyes Endpoint Protection-riasztások, majd adja meg a következő információkat:

    -   **Riasztás neve** – elfogadhatja az alapértelmezett nevet, vagy adjon meg egy új nevet a riasztáshoz.

    -   **Riasztás súlyossága** - listájában válassza ki a Configuration Manager-konzolon megjelenítendő riasztási szintet.

8.  Attól függően, hogy a riasztás, amely választja adja meg a következő információt:

    -   **Kártevő-észlelési** -a riasztás akkor jön létre, ha kártevőket észlel az a figyelt gyűjteményhez tartozó összes számítógépen. A **kártevőészlelés küszöbértéket** határozza meg, amely a riasztást kiváltó kártevőészlelési szintet:

        -   **Magas – minden észlelés** -a riasztás akkor jön létre, ha egy vagy több olyan számítógép amelyen kártevőket észlelt, függetlenül attól, milyen műveletet, az Endpoint Protection-ügyfél által a megadott gyűjteményben.

        -   **Közepes – észlelt, függőben lévő művelet** – a riasztás akkor jön létre, ha a megadott gyűjteményhez, amelyeken kártevő észlelhető egy vagy több számítógépet, és azokat manuálisan kell eltávolítani a kártevő szoftvereket.

        -   **Alacsony – észlelt, függőben lévő művelet** -a riasztás akkor jön létre, ha a megadott gyűjteményben egy vagy több olyan számítógép amelyen a szoftver kártevőt észlelt, és még mindig aktív.

    -   **Kártevő szoftver jelentős terjedése** -a riasztás akkor jön létre, ha meghatározott kártevő észlelhető a figyelt gyűjtemény számítógépeinek meghatározott százalékán.

        -   **A számítógépek, amelyeken kártevő észlelhető százalékos** -a riasztás akkor jön létre, ha a gyűjteményben az észlelt kártevővel rendelkező számítógépek százalékos aránya meghaladja a megadott értékkel. A százalékot **1** és **99**között adja meg.

            > [!NOTE]
            >  A százalékos érték a gyűjteményben szereplő számítógépek száma alapján, de nem tartalmazza a számítógépek, amelyeken nincs telepítve a Configuration Manager-ügyfél. Ez magában foglalja a számítógépeken, amelyeken még nincs telepítve az Endpoint Protection-ügyfél.

    -   **Kártevő szoftver ismételt észlelése** -a riasztás akkor jön létre, ha meghatározott kártevő észlelhető több, mint a megadott számú alkalommal egy megadott a figyelt gyűjteményhez tartozó számítógépeken órák alatt. Adja meg a riasztás konfigurálásához a következő információkat:

        -   **Kártevő észleléseinek száma:** – Ez a riasztás akkor jön létre, ha a gyűjteményhez tartozó számítógépeken ugyanazt a kártevőt a szoftver a meghatározottnál többször észlelte. **2** és **32**közötti számot adjon meg.

        -   **Észlelési időköz (óra):** Adja meg az észlelési időközt (órában) a kártevő szoftverek észlelések száma elő kell. **1** és **168**közötti számot adjon meg.

    -   **Több kártevő szoftver észlelése** – Ez a riasztás akkor jön létre, ha több mint a megadott számú észlelt a megadott a figyelt gyűjteményhez tartozó számítógépeken órák alatt. Adja meg a riasztás konfigurálásához a következő információkat:

        -   **Észlelt kártevőtípusok száma:** A riasztás akkor jön létre, amikor a megadott számú különböző kártevőtípust észlelt a gyűjteményhez tartozó számítógépeken. **2** és **32**közötti számot adjon meg.

        -   **Észlelési időköz (óra):** Adja meg az észlelési időközt órában, kell magukat a kártevő szoftverek észlelések száma. **1** és **168**közötti számot adjon meg.

9. Kattintson a **OK** bezárásához a *< gyűjteménynév\>***tulajdonságok** párbeszédpanel megnyitásához.  

## <a name="alert-for-outdated-malware-client"></a>A riasztás elavult kártevő-ügyfél

Verziótól kezdve a Configuration Manager verziója 1702, hogy az Endpoint Protection-ügyfelek nem elavult riasztásokat lehet beállítani. Most már megtekintheti **kártevőirtó ügyfélverzió** és **Endpoint Protection központi telepítési állapota** címen **eszközök és megfelelőség** > **áttekintése** > **eszközök** > **összes asztali számítógép és az ügyfelek kiszolgálásához**. Riasztás ellenőrzéséhez tekintse meg **riasztások** a a **figyelés** munkaterületen. Ha több mint 20 %-ban felügyelt ügyfelek egy kártevőirtó szoftver lejárt verzióját futtatja, a kártevőirtó-ügyfél verziója elavult riasztás jelenik meg. Ez a riasztás nem jelenik meg a **figyelés** > **áttekintése** fülre. Lejárt kártevőirtó ügyfelek frissítéséhez engedélyezése a szoftverfrissítések kártevőirtó-ügyfelek számára.

Konfigurálja a százalékos arányát, amelyen a riasztás akkor jön létre, bontsa ki **figyelés** > **riasztások** > **minden riasztás**, kattintson duplán a **kártevőirtó ügyfelek elavult** , és módosítsa a **riasztás, ha a felügyelt ügyfelek százalékos aránya a kártevőirtó ügyfélprogram elavult verzióját futtató több mint** lehetőséget.

> [!div class="button"]
[Következő lépés >](endpoint-definition-updates.md)

> [!div class="button"]
[Vissza >](endpoint-protection-site-role.md)

