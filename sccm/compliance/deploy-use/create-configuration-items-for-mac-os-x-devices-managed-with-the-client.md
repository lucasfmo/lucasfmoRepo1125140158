---
title: "Konfigurációelemek létrehozása a Mac számítógépekhez ügyfél által felügyelt - Configuration Manager |} Microsoft Docs"
description: "A System Center Configuration Manager Mac OS X-konfigurációs elem segítségével kezelheti a Mac OS X rendszerű eszközök beállításait."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 722d5bf5-bedc-4dfc-b324-6eeb773874e9
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 541e5ad629a9e2ed9c353dff150f9b86b9d12b7d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-mac-os-x-devices-managed-with-the-system-center-configuration-manager-client"></a>Konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazással felügyelt Mac OS X rendszerű eszközökhöz
A System Center Configuration Manager használata**Mac OS X (egyéni)** konfigurációelemet használva felügyelheti a Configuration Manager-ügyfél által felügyelt Mac OS X-eszközökön.  
  
 A Mac OS X operációs rendszer a tulajdonságlista- (vagy plist) fájlok használatával tárolja az alkalmazásbeállításokat. A megfelelőségi beállítások használatával kiértékelheti és javíthatja a beállításokat a tulajdonságlista-fájlokban. A Mac OS X beállításait felügyelheti egy olyan értéket visszaadó héjparancsfájl megírásával is, amelynek a megfelelőségét kiértékelheti és javíthatja.  
  
### <a name="to-create-a-custom-mac-os-x-configuration-item"></a>Egyéni Mac OS X-konfigurációelem létrehozása  
  
1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség**.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános** lapján adja meg a konfigurációelem nevét, és nem kötelezően leírást is megadhat hozzá.  
  
5.  A **Határozza meg a létrehozandó konfigurációelem típusát** csoportban válassza a **Mac OS X (egyéni)** elemet.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  A varázsló **Támogatott platformok** lapján jelölje ki azokat a Mac OS X-verziókat, amelyek kiértékelik a konfigurációelemet.  
  
8.  A varázsló **Beállítások** lapján új beállításokat adhat meg, amelyek megfelelőségét Mac számítógépeken fogja kiértékelni. Az **Új** elemre kattintva nyissa meg a **Beállítás létrehozása** párbeszédpanelt.  
  
9. A **Beállítás létrehozása** párbeszédpanelen egyéni nevet adhat a beállításnak, és leírást vehet fel hozzá.  
  
10. Válassza ki a kívánt **beállítástípust**, majd adja meg a szükséges információkat az alábbi táblázatban látható módon:  
  
    -   **Mac OS X-beállítások** -  
  
        -   **Alkalmazás azonosítója** – Itt adhatja meg annak a tulajdonságlista-fájlnak az azonosítóját, amelyből megfelelőség szempontjából ki szeretne értékelni egy kulcsot.  
  
             Ha például a Safari webböngésző beállításait szeretné szerkeszteni, használhatja a **com.apple.Safari.plist** azonosítót.  
  
        -   **Kulcs** – Itt adhatja meg annak a kulcsnak a nevét, amelynek a megfelelőségét Mac számítógépeken ki szeretne értékelni. A használandó szintaxis a következő: */<tár\>/<kulcsnév\>*.  
  
            > [!IMPORTANT]  
            >  A kulcsnevek megkülönböztetik a kis- és nagybetűket, és a rendszer nem értékeli ki őket, ha eltérnek a Mac számítógépen található kulcsnévtől. Miután megadta a kulcsnevet, a továbbiakban már nem módosíthatja azt. Ha módosítania kell a kulcsnevet, törölje, majd újból hozza létre a beállítást.  
  
    -   **Parancsfájl** -  
  
        -   **Felderítési parancsfájl** – Kattintson a **Parancsfájl hozzáadása** elemre, majd adja meg azt a héjparancsfájlt, amelyet a beállítások megfelelősége szempontjából a Mac számítógépen ki kell értékelni. Használja a **echo** parancsot a héjparancsfájlban megfelelőség a Configuration Manager visszaadott értékekre mutató. A Configuration Manager használ az adott eredmények **STDOUT** megfelelőség kiértékeléséhez.  
  
            > [!IMPORTANT]  
            >  A felderítési parancsfájl nem tartalmazhatja a **reboot** (újraindítás) parancsot. Mivel a felderítési parancsfájl az ügyfél minden indításakor fut, ez a Mac számítógép folyamatos újraindítását okozza.  
  
        -   **Szervizelési parancsfájl (nem kötelező)** – Kattinthat a **Parancsfájl hozzáadása** lehetőségre, és megadhat egy héjparancsfájlt, amely a Mac ügyfélszámítógépen talált nem megfelelő beállítások javítására használható.  
  
            > [!IMPORTANT]  
            >  Megelőzheti a Mac számítógép által nem értelmezhető formázási karakterek bevitelét, ha nem másol és beilleszt, hanem beír a parancsfájlba.  
  
11. Válassza azt az **Adattípus** lehetőséget, amely formátumban a feltétel visszaadja az adatot, mielőtt a beállítás kiértékeléséhez használta volna.  
  
    > [!NOTE]  
    >  A **Lebegőpontos szám** adattípus csak 3 tizedesjegyet támogat.  
    >   
    >  A Configuration Manager nem támogatja a **logikai** adattípusa Mac konfigurációelem parancsfájl-beállításai esetében. Adja meg ehelyett az **Egész** értéket az adattípushoz, és biztosítsa, hogy a parancsfájl egész értéket adjon vissza.  
  
12. Az **OK** gombra kattintva mentse a beállítást, zárja be a **Beállítás létrehozása** párbeszédpanelt, és adjon meg annyi beállítást, amennyi szükséges.  
  
13. A varázsló **Megfelelőségi szabályok** lapján adhatja meg a feltételeket, amelyek a konfigurációelemek megfelelőségét definiálják. A beállítások megfelelőségi kiértékelése előtt rendelkezniük kell legalább egy megfelelőségi szabállyal. Új szabály felvételéhez kattintson az **Új** elemre.  
  
14. A **Szabály létrehozása** párbeszédpanelen adja meg az alábbi adatokat:  
  
    -   **név:** Adja meg a megfelelőségi szabály nevét.  
  
    -   **Leírás:** Adja meg a megfelelőségi szabály leírását.  
  
    -   **Kiválasztott beállítás:** Kattintson a **Tallózás** megnyitásához a **beállítás kiválasztása** párbeszédpanel megnyitásához. Válassza a beállítást, amelyhez szabályt szeretne definiálni, vagy kattintson az **Új beállítás** elemre. Amikor végzett, kattintson a **Kijelölés** gombra.  
  
        > [!TIP]  
        >  A **Tulajdonságok** elemre kattintva megnézheti az aktuálisan kijelölt elemre vonatkozó információkat.  
  
    -   **Szabály típusa:** Válassza ki a megfelelőségi szabályt, amely a használni kívánt típusát:  
  
        -   **Érték:** Hozzon létre egy szabályt, amely egy érték, amely akkor adja meg a konfigurációelem által visszaadott értéket összehasonlítja.  
  
        -   **Meglétet vizsgáló:** Olyan szabályt hoz létre, amely kiértékeli a szabályt attól függően, hogy megtalálható-e egy eszközön.  
  
    -   Az **Érték** szabálytípus esetén adja meg az alábbi adatokat:  
  
        -   A beállításnak meg kell felelnie a következő szabálynak – Jelöljön ki egy operátort és egy értéket, amelyet megfelelőség szempontjában a kijelölt beállítással ellenőrizni kell. Az alábbi operátorok használhatók:  
  
            -   **Egyenlő**  
  
            -   **Nem egyenlő**  
  
            -   **Nagyobb, mint**  
  
            -   **Kisebb, mint**  
  
            -   **Között**  
  
            -   **Nagyobb vagy egyenlő**  
  
            -   **Kisebb vagy egyenlő, mint**  
  
            -   **Az egyik** – A szövegmezőben egy bejegyzést adjon meg soronként.  
  
            -   **A következők egyike sem** – A szövegmezőben egy bejegyzést adjon meg soronként.  
  
        -   **Nem megfelelő szabályok szervizelése (ha támogatott)** – Jelölje be ezt a jelölőnégyzetet, ha azt szeretné, hogy a Configuration Manager automatikusan javítsa a nem megfelelő szabályokat.  
  
            > [!IMPORTANT]  
            >  Csak akkor javíthatja a nem megfelelő szabályokat, ha a szabály operátor **Egyenlő**.  
  
        -   **Nem megfelelőségi jelentést ad, ha a beállításpéldány nem található** – Ha ez a beállítás nem található a Mac számítógépen, a konfigurációelem meg nem felelést jelent.  
  
    -   **Meg nem felelés súlyossága jelentésekhez** – A jelentett súlyossági szint megadása, ha ez a megfelelőségi szabály nem teljesül. A választható súlyossági szintek az alábbiak:  
  
        -   **Nincs** – a megfelelőségi szabályt nem teljesítő számítógépek a hiba súlyossága a Configuration Manager-jelentések nem jelenti.  
  
        -   **Információk** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **információkat** Configuration Manager jelentések.  
  
        -   **Figyelmeztetés** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **figyelmeztetés** Configuration Manager jelentések.  
  
        -   **Kritikus** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben.  
  
        -   **Kritikus eseménnyel** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet a Mac ügyfélszámítógép is naplózza.  
  
    -   A **Meglétet vizsgáló** szabálytípus esetén adja meg az alábbi adatokat:  
  
        -   Válasszon a következő lehetőségek közül:  
  
            -   **A beállításának léteznie kell az ügyféleszközökön**  
  
            -   **A beállítás nem szerepelhet az ügyféleszközökön**  
  
        -   **Meg nem felelés súlyossága jelentésekhez:** Adja meg, hogy milyen súlyossági szintről készüljön jelentés, ha a megfelelőségi szabályt nem sikerül. A választható súlyossági szintek az alábbiak:  
  
            -   **Nincs** – a megfelelőségi szabályt nem teljesítő számítógépek a hiba súlyossága a Configuration Manager-jelentések nem jelenti.  
  
            -   **Információk** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **információkat** Configuration Manager jelentések.  
  
            -   **Figyelmeztetés** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **figyelmeztetés** Configuration Manager jelentések.  
  
            -   **Kritikus** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben.  
  
            -   **Kritikus eseménnyel** – a megfelelőségi szabályt nem teljesítő számítógépek a jelentés a súlyosságot **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet a Mac ügyfélszámítógép is naplózza.  
  
        > [!NOTE]  
        >  A beállítások attól a beállítástípustól függően változhatnak, amelyhez szabályt ad meg.  
  
    -   Az **OK** gombra kattintva zárja be a **Szabály létrehozása** párbeszédpanelt.  
  
15. Az **Összegzés** lapon erősítse meg az új konfigurációelem beállításait, majd fejezze be a varázslót.  
  
 Az új konfigurációelem az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** csomópontjában látható.  
  
 Ha most hozzá szeretné adni ezt a konfigurációs elemet egy referenciakonfigurációhoz, tekintse meg a [Referenciakonfigurációk létrehozása a System Center Configuration Managerben](../../compliance/deploy-use/create-configuration-baselines.md) című szakaszt.  
  
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager-ügyféllel felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)

