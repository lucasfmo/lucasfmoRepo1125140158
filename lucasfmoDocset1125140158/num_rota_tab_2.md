---
title: Establecimiento de notificaciones de Advanced Threat Analytics | Microsoft Docs
description: Describe cómo establecer alertas de ATA para que se le informe cuando se detecten actividades sospechosas.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 444fd71f4c343619ceeea4056fbe98dce4f06b6a
ms.sourcegitcommit: 9f02f0f6669b25f39b616bb0885bb55b8c4f050b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46362449"
---
*Se aplica a: Advanced Threat Analytics versión 1.9*



# <a name="set-ata-notifications"></a>Establecer notificaciones de ATA
ATA puede enviar notificaciones cuando detecta una actividad sospechosa, ya sea por correo electrónico o mediante el reenvío de eventos de ATA, y reenviar el evento al servidor SIEM/Syslog. Antes de seleccionar las notificaciones que quiere recibir, tendrá que [configurar el servidor de correo electrónico y el servidor de Syslog](setting-syslog-email-server-settings.md).

> [!NOTE]
> -   Las notificaciones de correo electrónico incluyen un vínculo que llevará al usuario directamente a la actividad sospechosa que se ha detectado. La parte del nombre de host del vínculo se toma de la configuración de la dirección URL de la consola de ATA en la página del Centro ATA. De forma predeterminada, la dirección URL de la consola ATA es la dirección IP seleccionada durante la instalación del Centro ATA. Si va a configurar notificaciones de correo electrónico, se recomienda usar un FQDN como dirección URL de la consola de ATA.
> -   Las notificaciones se envían desde el centro ATA al servidor SMTP o al servidor de Syslog.


Para recibir notificaciones, establezca los siguientes parámetros:


1. En la consola de ATA, seleccione la opción de configuración en la barra de herramientas y, luego, **Configuración**.
    
    ![Icono de los valores de configuración de ATA](media/ATA-config-icon.png)
    
1. En la sección **Notificaciones e informes**, seleccione **Notificaciones**.
1. En **Notificaciones de correo**, especifique las notificaciones que se deben enviar por correo electrónico: las nuevas actividades sospechosas y los nuevos problemas de mantenimiento. Puede establecer una dirección de correo electrónico independiente para las actividades sospechosas que se deben enviar a y para las alertas de estado de manera que, por ejemplo, se puedan enviar notificaciones de cualquier actividad sospechosa a los analistas de seguridad y notificaciones de alerta de estado al administrador de TI.
    
  > [!NOTE]
  > Las alertas de correo electrónico sobre actividades sospechosas solo se envían cuando se crea la actividad sospechosa.

1. En **Notificaciones de Syslog**, especifique las notificaciones que se deben enviar al servidor de Syslog: las nuevas actividades sospechosas, las actividades sospechosas actualizadas y los nuevos problemas de mantenimiento.
1. Haga clic en **Guardar**.
    
    ![Imagen de configuración de notificación de correo de ATA](media/ata-mail-notification-settings.png)




## <a name="see-also"></a>Consulte también
[Visitar el foro de ATA](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
