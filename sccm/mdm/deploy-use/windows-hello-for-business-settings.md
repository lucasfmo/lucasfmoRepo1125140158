---
title: "Üzleti beállítások a Windows Hello |} Microsoft Docs"
description: "Ismerje meg, hogyan integrálható a vállalati Windows Hello-a System Center Configuration Managerrel."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0593c07-5dd7-4d23-a0d8-d30165f49ef7
caps.latest.revision: 17
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8c7bf901caa49c8585a9ed3913d4a5a2aac57013
ms.openlocfilehash: 7ac2baeb3c10ce90eb643fa28a953186b571d037
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager-hybrid"></a>A Windows Hello-üzleti beállításait a System Center Configuration Manager (hibrid)

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager lehetővé teszi az integrációt a Windows Hello-üzleti (korábbi nevén Microsoft Passport for Windows), amely egy alternatív bejelentkezési mód a Windows 10-eszközökre. A Hello for Business Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett.  

A Hello for Business lehetővé teszi jelszó helyett **felhasználói kézmozdulatok** használatát a bejelentkezéshez. A felhasználói hitelesítési mód lehet egy egyszerű PIN-kód, biometrikus hitelesítés vagy egy külső eszköz, például egy ujjlenyomat-olvasó.  

 A Configuration Manager két módon integrálható a vállalati Windows Hello:  

-   A Configuration Manager segítségével szabályozhatja, hogy mely kézmozdulatok felhasználók és nem használható a bejelentkezéshez.  

-   A hitelesítési tanúsítványokat tárolhatja a Windows Hello for Business kulcstároló-szolgáltatójában. További információkért lásd: [Tanúsítványprofilok](create-pfx-certificate-profiles.md).  

- Telepítheti a Windows Hello üzleti házirendek a tartományhoz csatlakoztatott Windows 10 rendszerű eszközökre a Configuration Manager-ügyfél. Ez a konfiguráció leírása [konfigurálása vállalati Windows Hello tartományhoz csatlakoztatott Windows 10-es eszközökön](../../protect/deploy-use/windows-hello-for-business-settings.md#configure-windows-hello-for-business-on-domain-joined-windows-10-devices). A Configuration Manager használatakor az Intune (hibrid) is ezeket a beállításokat a Windows 10 és Windows 10 Mobile-eszközökhöz, de nem a Configuration Manager-ügyfelet futtató, tartományhoz csatlakozó eszközök.   

Konfigurálása a Windows Hello üzleti beállítások kapcsolatos általános információkért lásd: [üzleti beállításait a System Center Configuration Managerben a Windows Hello-](../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="configure-windows-hello-for-business-settings-hybrid"></a>Konfigurálja a vállalati Windows Hello-beállítások (hibrid)  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Felhőszolgáltatások** > **Microsoft Intune-előfizetések**.  

3.  A listáról válassza ki a Microsoft Intune-előfizetését, majd kattintson a **Platformok konfigurálása** Windows (MDM) **lehetőségre a** Kezdőlap ****  > **Előfizetés**csoportjában.  

4.  A **Microsoft Intune Előfizetés tulajdonságai** párbeszédpanel **Windows Hello for Business** lapján válasszon a következő értékek közül, amelyek hatással lesznek az összes regisztrált Windows 10 és Windows 10 Mobile rendszerű eszközre:  

    -   **A Windows Hello for Business letiltása beléptetett eszközökön** vagy **A Windows Hello for Business engedélyezése beléptetett eszközökön** – A Windows Hello for Business használatának engedélyezése vagy letiltása az összes regisztrált Windows 10 és Windows 10 Mobile rendszerű eszközökön.  

    -   **Platformmegbízhatósági modul (TPM) használata** – A platformmegbízhatósági modul (TPM) extra adatbiztonsági réteget biztosít. Válasszon egyet az alábbi lehetőségek közül:  

        -   **Kötelező** (alapértelmezett) – a Windows Hello for Business csak az elérhető TPM modullal rendelkező eszközökön építhető ki.  

        -   **Elsődleges** : az eszközök először a TPM használatára tesznek kísérletet. Ha az nem érhető el, használhatnak szoftveralapú titkosítást.  

    -   **PIN-kód minimális hosszának megkövetelése** – Azt adja meg, hogy legalább hány karakterből kell állnia a Windows Hello for Business PIN-kódjának. Legalább 4 karaktert kell használnia (az alapértelmezett érték 6 karakter).  

    -   **PIN-kód maximális hosszának megkövetelése** – Azt adja meg, hogy legfeljebb hány karakterből állhat a Windows Hello for Business PIN-kódjának. Legfeljebb 127 karaktert használhat.  

    -   **Kisbetűk használatának megkövetelése a PIN kódban** – Azt adja meg, hogy szükséges-e a kisbetűk használata a Windows Hello for Business PIN-kódjában. A következő lehetőségek közül választhat:  

        -   **Engedélyezett** : a felhasználók használhatnak kisbetűket a PIN-kódjukban.  

        -   **Kötelező** : a felhasználóknak legalább egy kisbetűt használniuk kell a PIN-kódjukban.  

        -   **Nem engedélyezett** (alapértelmezett): a felhasználók nem használhatnak kisbetűket a PIN-kódjukban.  

    -   **Nagybetűk használatának megkövetelése a PIN kódban** – Azt adja meg, hogy szükséges-e a nagybetűk használata a Windows Hello for Business PIN-kódjában. A következő lehetőségek közül választhat:  

        -   **Engedélyezett** : a felhasználók használhatnak nagybetűket a PIN-kódjukban.  

        -   **Kötelező** : a felhasználóknak legalább egy nagybetűt használniuk kell a PIN-kódjukban.  

        -   **Nem engedélyezett** (alapértelmezett): a felhasználók nem használhatnak nagybetűket a PIN-kódjukban.  

    -   **Speciális karakterek megkövetelése** – Meghatározza a speciális karakterek használati módját a PIN-kódban. A következő lehetőségek közül választhat:  

        -   **Engedélyezett** : a felhasználók használhatnak speciális karaktereket a PIN-kódjukban.  

        -   **Kötelező** : a felhasználóknak legalább egy speciális karaktert használniuk kell a PIN-kódjukban.  

        -   **Nem engedélyezett** (alapértelmezett): a felhasználók nem használhatnak speciális karaktereket a PIN-kódjukban (ez történik akkor is, ha a beállítás nincs konfigurálva).  

         Speciális karakterek a következők: **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**.  

    -   **PIN-kód (napokban megadott) érvényességének megkövetelése** – A napok számát adja meg, amely után meg kell változtatni a PIN-kódot. Az alapértelmezett érték 41 nap.  

    -   **Korábbi PIN-kódok újbóli használatának megakadályozása** – Ezzel a beállítással korlátozhatja a korábban használt PIN-kódok újrafelhasználását. Az alapértelmezett érték szerint az utolsó 5 PIN-kód nem használható fel újra.  

    -   **Biometrikus kézmozdulatok engedélyezése** – Lehetővé teszi a biometrikus hitelesítést, például az arcfelismerést vagy az ujjlenyomat használatát a PIN-kód alternatívájaként a Windows Hello for Business szolgáltatásban. A felhasználóknak ekkor is be kell állítaniuk egy PIN-kódot arra az esetre, ha a biometrikus hitelesítés nem sikerül.  

         Ha az **Engedélyezve**érték van beállítva, a Windows Hello for Business lehetővé teszi a biometrikus hitelesítést.  Ha a **Letiltva**érték van beállítva, a Windows Hello for Business letiltja a biometrikus hitelesítést (minden fióktípushoz).  

    -   **Bővített hamisításszűrés használata, ha lehetséges** – Annak beállítása, hogy a rendszer bővített hamisításszűrést használjon-e azokon az eszközökön, amelyek támogatják ezt.  

         Ha az **Engedélyezve**értékre van állítva, a Windows minden felhasználótól megköveteli a kibővített hamisításszűrés alkalmazását arcfelismerés esetén, ha az támogatott.  

    -   **Remote Passport használata** – Ha a beállítás **Engedélyezve**van, a felhasználók távoli Vállalati Hello eszközt is használhatnak hordozható társeszközként az asztali számítógép hitelesítéséhez. Az asztali gépnek csatlakoztatva kell lennie az Azure Active Directoryhoz, és a társeszköznek rendelkeznie kell a Windows Hello for Business PIN-kódjával.  

5.  Amikor végzett, kattintson az **OK**gombra.  

### <a name="see-also"></a>További információ  
 [Adatok és a helyinfrastruktúra a System Center Configuration Managerrel védelme](../../protect/understand/protect-data-and-site-infrastructure.md)

 [Identitás-ellenőrzés használata a Windows Hello for Business kezelése](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport).  

