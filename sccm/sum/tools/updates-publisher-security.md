---
title: "Tanúsítványok és biztonsági |} Microsoft Docs"
description: "Tanúsítványok és biztonsági kezelése a System Center frissítés-közzétevő"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7f91e63-4750-402e-9970-dd14be7f76a3
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: c43af95a539a9284e4e49822b284783e02f9fa21
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-certificates-and-security-for-updates-publisher"></a>Tanúsítványok és biztonsági kezelése az Updates Publisher

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbi eljárások segítségével konfigurálhatja a tanúsítványtároló a frissítési kiszolgálóhoz, önálló aláíró tanúsítvány konfigurálása az ügyfélszámítógépen, és engedélyezi a Windows Update Agent szolgáltatást a számítógépeken a csoportházirend konfigurálásához közzé a frissítéseket.

## <a name="configure-the-certificate-store-on-the-update-server"></a>A frissítési kiszolgálóhoz a tanúsítványtároló konfigurálása
 Frissítés-közzétevő teszi közzé a katalógusok lévő frissítések aláírásához használt digitális tanúsítványt. A katalógus teheti közzé a frissítési kiszolgálót, mielőtt tanúsítvány kell lennie a tanúsítványtárolóban a frissítési kiszolgálóhoz, és az Updates Publisher számítógép tanúsítványtárolójában a frissítési kiszolgálót a távoli számítógép esetén.

Az alábbi eljárást az egyik több lehetséges módszer a tanúsítvány felvétele a frissítési kiszolgáló tanúsítványtárolójában.

### <a name="to-configure-the-certificate-store"></a>A tanúsítványtároló konfigurálása
1.  Egy olyan számítógépen, amely hozzáférhet az Updates Publisher számítógép és a frissítési kiszolgálót, kattintson **Start**, kattintson a **futtassa**, típus **MMC** a szövegmezőbe, majd **OK** megnyitni a Microsoft Management Console (MMC).

2.  Kattintson a **fájl**, kattintson **beépülő modul hozzáadása/eltávolítása**, kattintson **hozzáadása**, kattintson a **tanúsítványok**, kattintson **hozzáadása**, jelölje be **számítógépfiók**, és kattintson a **következő**.

3.  Válassza ki **egy másik számítógép**, írja be a frissítési kiszolgáló nevét, vagy kattintson a **Tallózás** a frissítési kiszolgáló számítógép megkereséséhez kattintson **Befejezés**, kattintson **Bezárás**, és kattintson a **OK**.

4.  Bontsa ki a  **tanúsítványok (*frissítés kiszolgálónév*) **, bontsa ki a **WSUS**, és kattintson a **tanúsítványok**.

5.  Az eredménypanelen kattintson jobb gombbal a kívánt tanúsítványra, kattintson a **feladataival**, és kattintson a **exportálása**.

6.  A Tanúsítványexportáló varázslóban az alapértelmezett beállítások használatával hozzon létre egy exportálási fájl nevét és helyét, a varázslóban megadott. Ez a fájl elérhető a frissítési kiszolgálót, mielőtt továbblép a következő lépéssel kell lennie.

7.  Kattintson a jobb gombbal **megbízható közzétevők**, kattintson a **feladataival**, és kattintson a **importálási**. 6. lépésben az exportált fájl használata a Tanúsítványimportáló varázsló befejezése.

8.  Önaláírt tanúsítvány használata esetén például **WSUS Publishers önaláírt**, kattintson a jobb gombbal **megbízható legfelső szintű hitelesítésszolgáltatók**, kattintson a **feladataival**, és kattintson a **importálási**. 6. lépésben az exportált fájl használata a Tanúsítványimportáló varázsló befejezése.

9.  Kattintson a jobb gombbal  **tanúsítványok (*frissítés kiszolgálónév*) **, kattintson a **Csatlakozás másik számítógéphez**, írja be az Updates Publisher számítógép a számítógép nevét, majd kattintson **OK**.

10. Ha frissítés-közzétevő távoli a frissítési kiszolgálóról, ismételje meg a 7 – 9, a tanúsítvány importálása az Updates Publisher számítógép tanúsítványtárolójába.



## <a name="configure-a-self-signing-certificate-on-client-computers"></a>Önálló aláíró tanúsítvány konfigurálása az ügyfélszámítógépeken
Az ügyfélszámítógépeken a Windows Update Agent (WUA) keresni kezdi a frissítések a katalógusból. Ez a folyamat nem frissítések telepítésére, amikor az ügynök nem keresse meg, hogy digitális tanúsítványt a megbízható közzétevők tanúsítványtárolóban a helyi számítógépen. Ha önaláírt tanúsítványt használt közzétételt a frissítések a katalógus, például a **WSUS Publishers önaláírt**, a tanúsítványt is kell a megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárolójában a helyi számítógépen, hogy az ügynök ellenőrizheti a tanúsítvány érvényességét.

Többféle módszer a tanúsítványok konfigurálásáról az ügyfélszámítógépeken, például a csoportházirend használatával is használja, és a **Tanúsítványimportáló varázsló** vagy a Certutil eszközt és a szoftverterjesztés használatával.

A következő van megadva egy példa az aláíró tanúsítvány konfigurálása az ügyfélszámítógépeken.

### <a name="to-configure-a-self-signing-certificate-on-client-computers"></a>Önálló aláíró tanúsítvány konfigurálása az ügyfélszámítógépeken
1.  Egy olyan számítógépen, aki hozzáféréssel rendelkezik a frissítési kiszolgálót, kattintson **Start**, kattintson a **futtassa**, típus **MMC** a szövegmezőbe, majd **OK** a Microsoft Management Console (MMC) lehetőségre.

2.  Kattintson a **fájl**, kattintson **beépülő modul hozzáadása/eltávolítása**, kattintson **hozzáadása**, kattintson a **tanúsítványok**, kattintson **hozzáadása**, jelölje be **számítógépfiók**, és kattintson a **következő**.

3.  Válassza ki **egy másik számítógép**, írja be a frissítési kiszolgáló nevét, vagy kattintson a **Tallózás** a frissítési kiszolgáló számítógép megkereséséhez kattintson **Befejezés**, kattintson **Bezárás**, és kattintson a **OK**.

4.  Bontsa ki a  **tanúsítványok (*frissítés kiszolgálónév*) **, bontsa ki a **WSUS**, és kattintson a **tanúsítványok**.

5.  Kattintson a jobb gombbal a tanúsítványt az eredménypanelen, kattintson a **feladataival**, és kattintson a **exportálása**. Fejezze be a **Tanúsítványexportáló varázsló** hozzon létre tanúsítványt exportfájl neve és a varázslóban megadott helyen az alapértelmezett beállításokkal.

6.  Az alábbi módszerek valamelyikével adja hozzá a frissítési katalógus lesz WUA való vizsgálatához használja a frissítések a katalógus ügyfélszámítógépekre aláírásához használt tanúsítványt. Adja hozzá a tanúsítványt az ügyfélszámítógépen a következőképpen:

    -   Az önaláírt tanúsítványok: A tanúsítvány hozzáadása a **megbízható legfelső szintű hitelesítésszolgáltatók** és **megbízható közzétevők** tanúsítványtárolókban.

    -   A hitelesítésszolgáltató (CA) kiállított tanúsítványok: A tanúsítvány hozzáadása a **megbízható közzétevők** tanúsítványtárolójába.

    > [!NOTE]
    > A WUA azt is ellenőrzi, hogy a **aláírt tartalom az intraneten futó Microsoft frissítési szolgáltatás helye engedélyezése** csoportházirend-beállítás engedélyezve van a helyi számítógépen. Ezt a házirend-beállítást engedélyezni kell ahhoz, hogy a WUA tudjon olyan frissítéseket keresni, amelyeket a frissítés-közzétevővel hoztak létre és tettek közzé. A csoportházirend-beállítás engedélyezésével kapcsolatos további információkért lásd: [hogyan konfigurálható a csoportházirend az ügyfélszámítógépeken] (https://technet.microsoft.com/library/bb530967.aspx(d=robot).



## <a name="configuring-group-policy-to-allow-wua-on-computers-to-scan-for-published-updates"></a>A WUA engedélyezze a közzétett frissítések keresése a számítógépeken csoportházirend konfigurálása
Mielőtt a Windows Update Agent (WUA) számítógépeken keresni kezdi a frissítés-közzétevője létrehozott és közzétett frissítéseket, a házirend-beállítást engedélyezni kell az intranetes Microsoft frissítési szolgáltatás helyéről származó aláírt tartalom engedélyezése. Ha a házirend-beállítás engedélyezve van, a WUA elfogadja az intranet helyeken keresztül beérkező Ha a frissítések be van jelentkezve a frissítések a **megbízható közzétevők** a helyi számítógép tanúsítványtárolójába. Többféleképpen a környezetben lévő számítógépeken a csoportházirend konfigurálásához.

A számítógépek számára, amelyek nincsenek a tartomány egy beállításkulcs-érték konfigurálhatók, amely lehetővé teszi egy intraneten futó Microsoft Update szolgáltatás helyéről származó aláírt tartalom.

Az alábbi eljárások nyújtanak a lépéseken, amelyeket a tartományban található számítógépek és a beállításkulcs-érték nem a tartományhoz csatlakozó számítógépeken a csoportházirend konfigurálásához használható.

### <a name="to-configure-group-policy-to-allow-wua-to-scan-for-published-updates"></a>A csoportházirend lehetővé teszi a WUA tudjon olyan közzé a frissítések
1.  A felhasználóhoz, amely rendelkezik a megfelelő biztonsági jogosultsággal a csoportházirend a csoport házirend objektum szerkesztő Microsoft Management Console (MMC) beépülő modul megnyitásához.

2.  Kattintson a **Tallózás** és válassza ki a tartományt, a szervezeti Egységhez vagy a csoportházirend-objektumok a hely, ahol a a beállított csoportházirend továbbterjeszti majd a kívánt ügyfélszámítógépekhez csatolva. Kattintson a **OK**, kattintson a **Befejezés**, kattintson a **Bezárás**, és kattintson a **OK**.

3.  A kijelölt házirend-beállítást, a konzolfán bontsa ki, majd **számítógép konfigurációja**, bontsa ki a **felügyeleti sablonok**, bontsa ki a **Windows-összetevők**, és kattintson a **Windows Update**.

4.  Az eredmények ablaktáblán kattintson jobb gombbal **aláírt tartalom az intraneten futó Microsoft frissítési szolgáltatás helye engedélyezése**, kattintson a **tulajdonságok**, kattintson a **engedélyezve**, és kattintson a **OK**.

