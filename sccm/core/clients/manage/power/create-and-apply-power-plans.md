---
title: "Hozzon létre és alkalmazhat energiasémákat |} Microsoft Docs"
description: "Hozzon létre és alkalmazhat energiasémákat a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 738eddaa-52e2-467f-b453-821ef2884d47
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: de81da31b524cebe8e820766a64ecc5fdb7e4771
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-and-apply-power-plans-in-system-center-configuration-manager"></a>Hogyan hozhat létre és alkalmazhat energiasémákat a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben az energiagazdálkodás lehetővé teszi gyűjtemény számítógépeire a hierarchiában a Configuration Manager biztosított energiasémák alkalmazását, vagy a saját egyéni energiasémákat hozzon létre. A jelen témakörben ismertetett eljárással beépített vagy egyéni energiasémát alkalmazhat a számítógépekre.  

> [!IMPORTANT]  
>  A Configuration Manager energiasémákat csak eszközgyűjtemények alkalmazhatók.  

 Ha egy számítógép több gyűjtemény tagja, és mind különböző energiasémát alkalmaz, a rendszer a következő műveleteket hajtja végre:  

-   Energiaséma: Ha egy számítógépre alkalmazott energiaellátási beállítások több értéket, a legkevésbé korlátozó értéket használja.  

-   Felébresztés ideje: Ha több Felébresztési idő is vonatkozik egy asztali számítógépre, az éjfélhez legközelebbi idő szolgál.  

 A **Több energiasémával rendelkező számítógépek** jelentést használva megjelenítheti az összes számítógépet, amelyre több energiaséma vonatkozik. Ez segíthet az energiaellátási ütközésekkel rendelkező számítógépek felderítésében. Energiagazdálkodási jelentések kapcsolatos további információkért lásd: [figyelés és tervezés a System Center Configuration Managerben az energiagazdálkodás hogyan](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  Windows csoportházirendjével konfigurált energiaellátási beállítások felülírják a Configuration Manager energiagazdálkodási konfigurált beállításait.  

 A következő eljárással hozhat létre és alkalmazhat a Configuration Manager egyik energiasémája.  

### <a name="to-create-and-apply-a-power-plan"></a>Energiaséma létrehozása és alkalmazása  

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  

2.  Kattintson az **Eszközök és megfelelőség** munkaterületen az **Eszközgyűjtemények**elemre.  

3.  Az **Eszközgyűjtemények** listában kattintson arra a gyűjteményre, amelyre alkalmazni szeretné az energiagazdálkodási beállításokat, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Az a **energiagazdálkodás** lapján a *< gyűjteménynév\>***tulajdonságok** párbeszédpanelen jelölje ki **adja meg az energiagazdálkodási beállítások megadása a gyűjtemény**.  

    > [!NOTE]  
    >  Kattinthat a **Tallózás** gombra is, majd átmásolhatja egy kijelölt gyűjtemény energiagazdálkodási beállításait a kijelölt gyűjteményre.  

5.  A **Kezdés** és a **Befejezés** mezőben adja meg a csúcsidő (vagy munkaidő) kezdő és befejező időpontját.  

6.  A **Felébresztés ideje (asztali számítógépek)** beállítást engedélyezve adja meg, hogy az asztali számítógép mikor ébredjen fel az alvó vagy a hibernált állapotból az ütemezett frissítések telepítése vagy a szoftvertelepítések végett.  

    > [!IMPORTANT]  
    >  Az energiagazdálkodás a Windows belső ébresztési időzítő funkciója segítségével ébreszti fel a számítógépeket az alvó vagy a hibernált állapotból. A felébresztési idő beállításai nem vonatkoznak a hordozható számítógépekre, hogy ne ébredjenek fel olyankor, amikor nincsenek csatlakoztatva. A felébresztés ideje véletlenszerű, és a számítógépek a megadott ébresztési időtől számított egy órás időszakban lesznek felébresztve.  

7.  Ha csúcsidőre (vagy munkaidőre) szeretne egyéni energiasémát beállítani, a **Csúcsidőre vonatkozó séma** legördülő listában válassza a **Csúcsidőre vonatkozó testre szabott beállítások (ConfigMgr)** elemet, majd kattintson a **Szerkesztés**lehetőségre. Ha nem csúcsidőre (vagy munkaidőre) szeretne energiasémát beállítani, a **Csúcsidőn kívüli terv** legördülő listában válassza a **Nem csúcsidőre vonatkozó testre szabott beállítások (ConfigMgr)** elemet, majd kattintson a **Szerkesztés**lehetőségre.  

    > [!NOTE]  
    >  A **Számítógépes tevékenység** jelentés használatával meghatározhatja a csúcsidőre és a nem csúcsidőre használandó ütemezéseket, amikor energiasémákat alkalmaz számítógép-gyűjteményekre. További információkért lásd: [figyelés és tervezés a System Center Configuration Managerben az energiagazdálkodás hogyan](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

     A beépített energiasémák közül is választhat ( **Kiegyensúlyozott (ConfigMgr)**, **Nagy teljesítményű (ConfigMgr)** és **Energiatakarékos (ConfigMgr)**), majd a **Megtekintés** elemre kattintva megjelenítheti az egyes energiasémák tulajdonságait.  

    > [!NOTE]  
    >  A beépített energiasémákat nem módosíthatja.  

8.  Az a *< energiaséma neve\>***tulajdonságok** párbeszédpanelen adja meg a következő beállításokat:  

    -   **név:** Adja meg az energiaséma nevét, vagy használja a megadott alapértelmezett értéket.  

    -   **Leírás:**  Adja meg az energiaséma leírását, vagy használja a megadott alapértelmezett értéket.  

    -   **Az energiaséma tulajdonságainak megadása:** Konfigurálhatja az energiaséma tulajdonságait. Tulajdonság letiltásához törölje a megfelelő jelölőnégyzet bejelölését. Az elérhető beállításokra vonatkozó információkat a jelen témakör [Available power management plan settings](#BKMK_Plans) című részén találja.  

        > [!IMPORTANT]  
        >  Az engedélyezett beállításokat az energiaséma alkalmazásakor alkalmazza a rendszer a számítógépekre. Ha törli egy energiagazdálkodási beállítás jelölőnégyzetének bejelölését, az energiaséma alkalmazásakor az ügyfélszámítógépen nem változik az érték. A jelölőnégyzet bejelölésének törlése nem állítja vissza az energiagazdálkodási beállítást az energiaséma alkalmazása előtti értékre.  

9. Kattintson a **OK** bezárásához a *< energiaséma neve\>***tulajdonságok** párbeszédpanel megnyitásához.  

10. Kattintson a **OK** bezárásához a *< gyűjtemény neve\>***beállítások** párbeszédpanelt az energiaséma alkalmazásához.  

##  <a name="BKMK_Plans"></a> Available power management plan settings  
 A következő táblázat az energiagazdálkodási beállítások a Configuration Manager alkalmazásban érhető el. Eltérő beállításokat konfigurálhat arra az esetre, amikor a számítógép hálózathoz csatlakozik, illetve akkumulátorról működik. A Windows használt verziójától függően előfordulhat, hogy egyes beállítások nem konfigurálhatók.  

> [!NOTE]  
>  A nem konfigurált energiaellátási beállítások megőrzik az aktuális értéküket az ügyfélszámítógépeken.  

|Név|Leírás|  
|----------|-----------------|  
|**Kijelző kikapcsolása (perc)**|Itt adhatja meg (percben kifejezve), hogy mennyi ideig kell a számítógépnek inaktívnak lennie, mielőtt a kijelző kikapcsolna. Adja meg a **0** értéket, ha nem szeretné, hogy az energiagazdálkodás kikapcsolja a kijelzőt.|  
|**Idő az alvó állapotig (perc)**|Itt adhatja meg (percben kifejezve), hogy mennyi ideig kell a számítógépnek inaktívnak lennie, mielőtt alvó állapotra váltana. Adja meg a **0** értéket, ha nem szeretné, hogy az energiagazdálkodás alvó állapotba léptesse a számítógépet.|  
|**Jelszókérés ébresztéskor**|A **Igen** vagy **nem** érték határozza meg, hogy a számítógép zárolásának feloldásához, amikor az alvó üzemmódból felébredni szükség-e jelszót.|  
|**Tápkapcsoló megnyomásakor**|Itt adhatja meg a számítógép tápkapcsolójának a megnyomásakor végrehajtandó műveletet. Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. A lehetséges értékek **nincs**, **alvó**, **hibernálás**, és **leállítása**.|  
|**Start menü kikapcsológombja**|Itt adhatja meg a számítógép **Start** menü kikapcsológombjának a megnyomásakor végrehajtandó műveletet. Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. A lehetséges értékek **alvó**, **hibernálás**, és **leállítása**.|  
|**Alvás gomb megnyomásakor**|Itt adhatja meg a számítógép **Alvás** gombjának a megnyomásakor végrehajtandó műveletet. Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. A lehetséges értékek **nincs**, **alvó**, **hibernálás**, és **leállítása**.|  
|**Fedél lehajtásakor**|Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. A lehetséges értékek **nincs**, **alvó**, **hibernálás**, és **leállítása**.|  
|**Merevlemez kikapcsolása (perc)**|Itt adhatja meg (percben kifejezve), hogy mennyi ideig kell a számítógép merevlemezének inaktívnak lennie a kikapcsolása előtt. Adja meg a **0** értéket, ha nem szeretné, hogy az energiagazdálkodás kikapcsolja a számítógép merevlemezét.|  
|**Idő a hibernálásig (perc)**|Itt adhatja meg (percben kifejezve), hogy mennyi ideig kell a számítógépnek inaktívnak lennie, mielőtt hibernált állapotra váltana. Adja meg a **0** értéket, ha nem szeretné, hogy az energiagazdálkodás hibernált állapotba léptesse a számítógépet.|  
|**Művelet alacsony töltöttség esetén**|Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a számítógép akkumulátora eléri az alacsony töltöttségű telepre vonatkozó értesítés szintjét. Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. A lehetséges értékek **nincs**, **alvó**, **hibernálás**, és **leállítása**.|  
|**Művelet kritikus töltöttség esetén**|Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a számítógép akkumulátora eléri a kritikus töltöttségű telepre vonatkozó értesítés szintjét. Itt adhatja meg, hogy milyen műveletet hajtson végre a rendszer, amikor a felhasználó lehajtja egy hordozható számítógép fedelét. Lehetséges értékek a következők **alvó**, **hibernálás**, és **leállítása**.|  
|**Hibrid alvás engedélyezése**|Válassza a **a** vagy **ki** érték határozza meg, hogy a Windows menti-e egy hibernálási fájlt, amikor alvó, amely a számítógép állapotát, az áramellátás megszakadása esetén visszaállíthatók a alvó állapotba lépésekor mentsen használható.<br /><br /> A hibrid alvás asztali számítógépekhez készült, és alapértelmezés szerint nem engedélyezett hordozható számítógépeken. Windows 7 rendszerű számítógépeken a hibrid alvás engedélyezése letiltja a hibernálási funkciót.|  
|**Készenléti üzemmód engedélyezése alvó állapot esetén**|Válassza a **a** vagy **ki** érték lehetővé teszi, hogy a számítógép készenléti üzemmódban legyen, amelyek továbbra is fogyaszt némi energiát, de lehetővé teszi, hogy a számítógép alvó állapotból a gyorsabb. Ha a beállítás értéke **Ki**, a számítógép csak hibernálhat vagy kikapcsolhat.|  
|**Alvó állapotot kiváltó üresjárat (%)**|Itt adhatja meg a számítógép alvó állapotába lépéséhez a számítógép processzoridején szükséges üresjárati időt százalékos értékben. Windows 7 rendszerű számítógépeken, ez az érték mindig értéke **0**.|  
|**Windows ébresztési időzítő engedélyezése asztali számítógépekhez**|Válassza a **engedélyezése** vagy **letiltása** érték engedélyezheti a beépített Windows-időzítőt, asztali számítógépek felébresztésére energiagazdálkodás használandó. Amikor egy asztali számítógépet a Windows ébresztési időzítővel ébresztenek fel, alapértelmezés szerint 10 percig aktív állapotban marad, hogy időt adjon a számítógépnek frissítések telepítésére vagy szabályzat fogadására.<br /><br /> Az ébresztési időzítők nem támogatottak hordozható számítógépeken annak megakadályozása végett, hogy akkor is felébredjenek, ha nincsenek csatlakoztatva.|  

