---

title: "Besorolások és termékek szinkronizálása konfigurálása |} Microsoft Docs"
description: "Ezek a lépések segítségével állítsa be a besorolások és termékek a Configuration Manager konzol szinkronizálása."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 6add66e625c790b65edf64216c2262a5d082f820
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
#  <a name="configure-classifications-and-products-to-synchronize"></a>Besorolások és termékek szinkronizálása konfigurálása  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


> [!NOTE]  
>  Az ebben a szakaszban ismertetett eljárást csak a legfelső szintű helyen használja.  

 Szoftverfrissítési metaadatok lekérése a szinkronizálás során a Configuration Managerben a szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen megadott beállítások alapján. A szoftverfrissítések első szinkronizálása után, vagy új termékek és besorolások megjelenésekor, akkor be kell lépnie a tulajdonságai lapon jelölje ki az új elemet. A következő eljárással konfigurálhatja a szinkronizálandó besorolásokat és termékeket.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>Besorolások és termékek konfigurálása szinkronizáláshoz  

1.  Az a **Configuration Manager** konzolt, keresse meg **felügyeleti** > **Helykonfiguráció** > **helyek**.

2. Válassza ki a központi adminisztrációs hely vagy önálló elsődleges helyen.  

3.  A **Kezdőlap** **Beállítások** csoportjában nyissa meg a **Helyösszetevők konfigurálása**elemet, majd kattintson a **Szoftverfrissítési pont**elemre.

4.  A **Besorolások** lapon adja meg a szoftverfrissítés azon besorolásait, amelyekhez szoftverfrissítéseket szeretne szinkronizálni.  

    > [!NOTE]  
    >  Minden szoftverfrissítéshez tartozik egy frissítési besorolás, amely a különböző típusú frissítések rendszerezésében nyújt segítséget. A szinkronizálási folyamat a megadott besorolás szoftverfrissítési metaadatait szinkronizálja. A Configuration Manager lehetővé teszi a szoftverfrissítések szinkronizálását a következő frissítési besorolásokkal:  
    >   
    > - **Kritikus frissítések**: Megadja, széles körben kiadott frissítés egy adott probléma, amely kritikus, nem biztonsági hiba kezelésére szolgál.  
    > - **Definíciófrissítések**: Megadja a vírus- vagy egyéb definíciós fájlok frissítése.  
    > - **Szolgáltatáscsomagok**: Adja meg az új termékszolgáltatások, amelyek termékkiadáson kívül terjesztett, és amelyek általában bekerülnek a soron következő teljes termékkiadásba.  
    > - **Biztonsági frissítések**: Megadja, széles körben kiadott frissítés egy termékspecifikus biztonsági problémára.  
    > - **Szervizcsomagot**: Meghatározza az adott alkalmazásnál alkalmazott gyorsjavítások összesített csomagja. A gyorsjavítások tartalmazhatnak biztonsági frissítéseket, kritikus frissítéseket, szoftverfrissítéseket stb.  
    > - **Eszközök**: Megadja a szolgáló segédprogramok vagy funkciók, amelyek egy vagy több feladat végrehajtására.  
    > - **Kumulatív frissítések**: Megadja az egyszerű telepítés egy csomagba gyorsjavítások összesített csomagja. A gyorsjavítások lehetnek biztonsági frissítések, kritikus frissítések, szoftverfrissítések stb. A kumulatív frissítések általában egy konkrét területre összpontosítanak, például a biztonságra vagy egy termékösszetevőre.  
    > - **Frissítések**: Megadja egy alkalmazás vagy a jelenleg telepített fájl frissítése.  
    > - **Frissítés**: Adja meg a Windows 10 szolgáltatásainak és funkcióinak frissítése.  
    >   
    >      A szoftverfrissítési pontok és a helyek legalább WSUS 4.0-s verziójának kell futnia a [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) lekérni a **frissítése** besorolás.  

5.  A **Besorolások** lapon adja meg azokat a termékeket, amelyekhez szoftverfrissítéseket szeretne szinkronizálni, majd kattintson a **Bezárás**gombra.  

    > [!NOTE]  
    >  Az egyes szoftverfrissítések metaadatai azokat a termékeket definiálják, amelyekhez a szoftverfrissítés alkalmazható. A termék egy operációs rendszer vagy alkalmazás adott kiadását jelenti, például Windows Server 2012. A termékcsalád az az operációs rendszer vagy alkalmazás, amelyből az egyes termékek származnak. Termékcsalád például a Windows, amelynek tagja a Windows Server 2012. Termékcsaládot is választhat, vagy konkrét termékeket is kijelölhet egy adott termékcsaládon belül. Minél több terméket választ ki, annál hosszabb ideig tart a szoftverfrissítések szinkronizálása.  
    >   
    >  Szoftverfrissítés több termékre érvényes, és legalább egy ilyen termék lett választva szinkronizálás céljából, ha az összes termék megjelenik a Configuration Manager konzolon még akkor is, ha bizonyos termékek nem lettek kiválasztva. Például ha a Windows Server 2012 az egyetlen operációs rendszer, verziószámával, és a szoftverfrissítés a Windows 8 és Windows Server 2012, mindkét termék fog megjelenni a Configuration Manager konzolon.  

    > [!IMPORTANT]  
    >  A Configuration Manager termékek listáját tárolja és termékcsaládok, amelyből kiválaszthatja, ha először telepíti a szoftverfrissítési pontra. Termékek és termékcsaládok, amelyek a Configuration Manager kiadása után nem feltétlenül érhető el, amíg be nem fejezi a szoftverfrissítések szinkronizálását, frissül a választható termékek és termékcsaládok, amelyről választhat listája kiválasztásához.  


## <a name="next-steps"></a>További lépések
Indítsa el az új feltételeknek megfelelő szoftverfrissítések beolvasni a szoftverfrissítések szinkronizálását. További információkért lásd: [szinkronizálhatók a szoftverfrissítések](synchronize-software-updates.md).

