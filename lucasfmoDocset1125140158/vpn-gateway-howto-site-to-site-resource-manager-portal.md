---
title: 'Herstellen einer Verbindung zwischen Ihrem lokalen Netzwerk und einem virtuellen Azure-Netzwerk: Site-to-Site-VPN: Portal | Microsoft-Dokumentation'
description: "Schritte zum Erstellen einer IPsec-Verbindung zwischen Ihrem lokalen Netzwerk und einem virtuellen Azure-Netzwerk über das öffentliche Internet. Anhand dieser Schritte können Sie über das Portal eine standortübergreifende Site-to-Site-VPN Gateway-Verbindung erstellen."
services: vpn-gateway
documentationcenter: na
author: cherylmc
manager: timlt
editor: 
tags: azure-resource-manager
ms.assetid: 827a4db7-7fa5-4eaf-b7e1-e1518c51c815
ms.service: vpn-gateway
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 11/17/2017
ms.author: cherylmc
ms.openlocfilehash: 4f5e249238020429b6c6e0d39c580c83bc43969e
ms.sourcegitcommit: 933af6219266cc685d0c9009f533ca1be03aa5e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-site-to-site-connection-in-the-azure-portal"></a>Erstellen einer Site-to-Site-Verbindung im Azure-Portal

In diesem Artikel wird beschrieben, wie Sie das Azure-Portal zum Erstellen einer Site-to-Site-VPN-Gateway-Verbindung zwischen Ihrem lokalen Netzwerk und dem VNET verwenden. Die Schritte in diesem Artikel gelten für das Resource Manager-Bereitstellungsmodell. Sie können diese Konfiguration auch mit einem anderen Bereitstellungstool oder -modell erstellen. Wählen Sie hierzu in der folgenden Liste eine andere Option:

> [!div class="op_single_selector"]
> * [Azure-Portal](vpn-gateway-howto-site-to-site-resource-manager-portal.md)
> * [PowerShell](vpn-gateway-create-site-to-site-rm-powershell.md)
> * [BEFEHLSZEILENSCHNITTSTELLE (CLI)](vpn-gateway-howto-site-to-site-resource-manager-cli.md)
> * [Azure-Portal (klassisch)](vpn-gateway-howto-site-to-site-classic-portal.md)
> 
>

Eine Site-to-Site-VPN-Gateway-Verbindung wird verwendet, um Ihr lokales Netzwerk über einen IPsec/IKE-VPN-Tunnel (IKEv1 oder IKEv2) mit einem virtuellen Azure-Netzwerk zu verbinden. Für diese Art von Verbindung wird ein lokales VPN-Gerät benötigt, dem eine extern zugängliche, öffentliche IP-Adresse zugewiesen ist. Weitere Informationen zu VPN-Gateways finden Sie unter [Informationen zu VPN Gateway](vpn-gateway-about-vpngateways.md).

![Diagramm für die standortübergreifende Site-to-Site-VPN Gateway-Verbindung](./media/vpn-gateway-howto-site-to-site-resource-manager-portal/site-to-site-diagram.png)

## <a name="before-you-begin"></a>Voraussetzungen

Vergewissern Sie sich vor Beginn der Konfiguration, dass die folgenden Voraussetzungen erfüllt sind bzw. Folgendes vorhanden ist:

* Achten Sie darauf, dass Sie ein kompatibles VPN-Gerät nutzen (und über eine Person verfügen, die es konfigurieren kann). Weitere Informationen zu kompatiblen VPN-Geräten und zur Gerätekonfiguration finden Sie unter [Informationen zu VPN-Geräten](vpn-gateway-about-vpn-devices.md).
* Vergewissern Sie sich, dass Sie über eine externe öffentliche IPv4-Adresse für Ihr VPN-Gerät verfügen. Diese IP-Adresse darf sich nicht hinter einer NAT befinden.
* Falls Sie nicht mit den IP-Adressbereichen in Ihrer lokalen Netzwerkkonfiguration vertraut sind, wenden Sie sich an eine Person, die Ihnen diese Informationen zur Verfügung stellen kann. Beim Erstellen dieser Konfiguration müssen Sie die Präfixe für die IP-Adressbereiche angeben, die Azure an Ihren lokalen Standort weiterleitet. Kein Subnetz Ihres lokalen Netzwerks darf sich mit den Subnetzen des virtuellen Netzwerks überschneiden, mit dem Sie eine Verbindung herstellen möchten. 

### <a name="values"></a>Beispielwerte

In den Beispielen dieses Artikels werden die folgenden Werte verwendet. Sie können diese Werte zum Erstellen einer Testumgebung verwenden oder zum besseren Verständnis der Beispiele in diesem Artikel heranziehen. Weitere Informationen zu Gatewayeinstellungen im Allgemeinen finden Sie unter [Informationen zu VPN Gateway-Einstellungen](vpn-gateway-about-vpn-gateway-settings.md).

* **VNET-Name:** TestVNet1
* **Adressbereich:** 10.11.0.0/16 und 10.12.0.0/16 (für diese Übung optional)
* **Abonnement:** Das zu verwendende Abonnement
* **Ressourcengruppe:** TestRG1
* **Standort:** USA, Osten
* **Subnetz:** FrontEnd: 10.11.0.0/24, BackEnd: 10.12.0.0/24 (für diese Übung optional)
* **Name des Gatewaysubnetzes:** GatewaySubnet (wird im Portal automatisch ausgefüllt)
* **Adressbereich des Gatewaysubnetzes:** 10.11.255.0/27
* **DNS-Server:** Optional. Die IP-Adresse Ihres DNS-Servers.
* **Name des Gateways für virtuelle Netzwerke:** VNet1GW
* **Öffentliche IP-Adresse:** VNet1GWIP
* **VPN-Typ:** Routenbasiert
* **Verbindungstyp:** Site-to-Site (IPsec)
* **Gatewaytyp:** VPN
* **Name des Gateways für das lokale Netzwerk:** Site2
* **Verbindungsname:** VNet1toSite2
* **Gemeinsam verwendeter Schlüssel:** In diesem Beispiel verwenden wir „abc123“. Sie können jedoch einen beliebigen, mit Ihrer VPN-Hardware kompatiblen Wert verwenden. Wichtig ist, dass die Werte auf beiden Seiten der Verbindung übereinstimmen.

## <a name="CreatVNet"></a>1. Erstellen eines virtuellen Netzwerks


## <a name="dns"></a>2. Angeben eines DNS-Servers

DNS ist zum Erstellen von Standort-zu-Standort-Verbindungen nicht erforderlich. Wenn Sie für Ressourcen, die in Ihren virtuellen Netzwerken bereitgestellt werden, die Namensauflösung verwenden möchten, müssen Sie aber einen DNS-Server angeben. Diese Einstellung bietet die Möglichkeit, den DNS-Server anzugeben, den Sie zur Namensauflösung für dieses virtuelle Netzwerk verwenden möchten. Mit dieser Einstellung wird kein DNS-Server erstellt. Weitere Informationen zur Funktionsweise der Namensauflösung finden Sie unter [Namensauflösung für virtuelle Computer und Rolleninstanzen](../virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances.md).


## <a name="gatewaysubnet"></a>3. Erstellen des Gatewaysubnetzes



## <a name="VNetGateway"></a>4. Erstellen des VPN-Gateways


## <a name="LocalNetworkGateway"></a>5. Erstellen des Gateways des lokalen Netzwerks

Mit dem Gateway des lokalen Netzwerks ist normalerweise Ihr lokaler Standort gemeint. Sie geben dem Standort einen Namen, über den Azure darauf verweisen kann, und geben dann die IP-Adresse des lokalen VPN-Geräts an, mit dem Sie eine Verbindung herstellen. Außerdem geben Sie die IP-Adresspräfixe an, die über das VPN-Gateway an das VPN-Gerät weitergeleitet werden. Die von Ihnen angegebenen Adresspräfixe befinden sich in Ihrem lokalen Netzwerk. Wenn bei dem lokalen Netzwerk Änderungen vorgenommen werden oder Sie die öffentliche IP-Adresse des VPN-Geräts ändern müssen, können Sie dies Werte später bequem aktualisieren.


## <a name="VPNDevice"></a>6. Konfigurieren des VPN-Geräts

Für Site-to-Site-Verbindungen mit einem lokalen Netzwerk ist ein VPN-Gerät erforderlich. In diesem Schritt konfigurieren Sie Ihr VPN-Gerät. Beim Konfigurieren des VPN-Geräts benötigen Sie Folgendes:

- Einen gemeinsam verwendeten Schlüssel. Dies ist derselbe gemeinsame Schlüssel, den Sie beim Erstellen Ihrer Site-to-Site-VPN-Verbindung angeben. In unseren Beispielen verwenden wir einen einfachen gemeinsamen Schlüssel. Es wird empfohlen, einen komplexeren Schlüssel zu generieren.
- Die öffentliche IP-Adresse Ihres Gateways für virtuelle Netzwerke. Sie können die öffentliche IP-Adresse mit dem Azure-Portal, mit PowerShell oder mit der CLI anzeigen. Sie können die öffentliche IP-Adresse des VPN-Gateways mit dem Azure-Portal ermitteln, indem Sie zu **Gateways für virtuelle Netzwerke** navigieren und auf den Namen Ihres Gateways klicken.


## <a name="CreateConnection"></a>7. Erstellen der VPN-Verbindung

Erstellen Sie die Site-to-Site-VPN-Verbindung zwischen dem Gateway Ihres virtuellen Netzwerks und Ihrem lokalen VPN-Gerät.


## <a name="VerifyConnection"></a>8. Überprüfen der VPN-Verbindung


## <a name="connectVM"></a>Herstellen einer Verbindung mit einem virtuellen Computer


## <a name="reset"></a>Zurücksetzen einer VPN Gateway-Instanz

Das Zurücksetzen von Azure VPN Gateway-Instanzen ist nützlich, wenn die standortübergreifende VPN-Verbindung bei mindestens einem Site-to-Site-VPN-Tunnel unterbrochen ist. In diesem Fall funktionieren Ihre lokalen VPN-Geräte ordnungsgemäß, können jedoch keine IPsec-Tunnelverbindungen mit Azure VPN Gateway-Instanzen herstellen. Eine entsprechende Anleitung finden Sie unter [Zurücksetzen einer VPN Gateway-Instanz](vpn-gateway-resetgw-classic.md).

## <a name="resize"></a>Ändern einer Gateway-SKU (Ändern der Gatewaygröße)

Eine Anleitung zum Ändern einer Gateway-SKU finden Sie unter [Gateway-SKUs](vpn-gateway-about-vpn-gateway-settings.md#gwsku).

## <a name="addconnect"></a>Hinzufügen zusätzlicher Verbindungen zu einem VPN-Gateway

Sie können weitere Verbindungen hinzufügen. Voraussetzung dafür ist, dass sich Adressbereiche zwischen Verbindungen nicht überlappen.

1. Navigieren Sie zum Hinzufügen einer zusätzlichen Verbindung zum VPN-Gateway, und klicken Sie auf **Verbindungen**, um die Seite „Verbindungen“ zu öffnen.
2. Klicken Sie auf **+Hinzufügen**, um die Verbindung hinzuzufügen. Passen Sie den Verbindungstyp an, um VNET-to-VNET (falls Sie eine Verbindung mit einem anderen VNET-Gateway herstellen) oder Site-to-Site widerzuspiegeln.
3. Wenn Sie eine Verbindung über Site-to-Site herstellen und noch kein lokales Netzwerkgateway für die Website erstellt haben, mit der Sie eine Verbindung herstellen möchten, können Sie ein neues erstellen.
4. Geben Sie den gemeinsam verwendeten Schlüssel ein, den Sie verwenden möchten, und klicken Sie auf **OK**, um die Verbindung zu erstellen.

## <a name="next-steps"></a>Nächste Schritte

* Informationen zu BGP finden Sie in der [Übersicht über BGP](vpn-gateway-bgp-overview.md) und unter [Konfigurieren von BGP](vpn-gateway-bgp-resource-manager-ps.md).
* Weitere Informationen zur Tunnelerzwingung finden Sie unter [Konfigurieren der Tunnelerzwingung mit dem Azure Resource Manager-Bereitstellungsmodell](vpn-gateway-forced-tunneling-rm.md).
* Informationen zu hochverfügbaren Aktiv/Aktiv-Verbindungen finden Sie unter [Standortübergreifende Verbindungen und VNET-zu-VNET-Verbindungen mit hoher Verfügbarkeit](vpn-gateway-highlyavailable.md).
* Informationen zum Beschränken von Netzwerkdatenverkehr auf Ressourcen in einem virtuellen Netzwerk finden Sie unter [Netzwerksicherheit](../virtual-network/security-overview.md).
* Informationen zur Weiterleitung von Datenverkehr zwischen Azure, lokalen Speicherorten und Internetressourcen finden Sie unter [Routing von Datenverkehr für virtuelle Netzwerke](../virtual-network/virtual-networks-udr-overview.md).
* Informationen zum Erstellen einer Site-to-Site-VPN-Verbindung mithilfe einer Azure Resource Manager-Vorlage finden Sie unter [Create a Site-to-Site VPN Connection](https://azure.microsoft.com/resources/templates/101-site-to-site-vpn-create/) (Erstellen einer Site-to-Site-VPN-Verbindung).
* Informationen zum Erstellen einer VNET-zu-VNET-VPN-Verbindung mithilfe einer Azure Resource Manager-Vorlage finden Sie unter [Deploy HBase geo replication](https://azure.microsoft.com/resources/templates/101-hdinsight-hbase-replication-geo/) (Bereitstellen der HBase-Georeplikation).
