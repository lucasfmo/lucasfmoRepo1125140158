---
title: IT Service Management Connector en Azure Log Analytics | Microsoft Docs
description: "En este artículo se proporciona información general sobre el Conector de Administración de servicios de TI (ITSMC) e información sobre cómo usar esta solución para supervisar y administrar de forma centralizada los elementos de trabajo de ITSM en Azure Log Analytics y resolver rápidamente cualquier problema."
services: log-analytics
documentationcenter: 
author: JYOTHIRMAISURI
manager: riyazp
editor: 
ms.assetid: 0b1414d9-b0a7-4e4e-a652-d3a6ff1118c4
ms.service: log-analytics
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/23/2018
ms.author: v-jysur
ms.openlocfilehash: 56da2d4349a4a32eed783045381e504b529b1a1c
ms.sourcegitcommit: 9d317dabf4a5cca13308c50a10349af0e72e1b7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="connect-azure-to-itsm-tools-using-it-service-management-connector"></a><span data-ttu-id="a8867-103">Conectar Azure a las herramientas de ITSM mediante el Conector de Administración de servicios de TI</span><span class="sxs-lookup"><span data-stu-id="a8867-103">Connect Azure to ITSM tools using IT Service Management Connector</span></span>

![Símbolo de IT Service Management Connector](./media/log-analytics-itsmc/itsmc-symbol.png)

<span data-ttu-id="a8867-105">El Conector de Administración de servicios de TI (ITSMC) le permite conectar Azure y un producto o servicio de Administración de servicios de TI (ITSM) compatibles.</span><span class="sxs-lookup"><span data-stu-id="a8867-105">The IT Service Management Connector (ITSMC) allows you to connect Azure and a supported IT Service Management (ITSM) product/service.</span></span>

<span data-ttu-id="a8867-106">Servicios de Azure como Log Analytics y Azure Monitor proporcionan herramientas para detectar, analizar y solucionar problemas relacionados con los recursos de Azure y de otros proveedores.</span><span class="sxs-lookup"><span data-stu-id="a8867-106">Azure services like Log Analytics and Azure Monitor provide tools to detect, analyze and troubleshoot issues with your Azure and non-Azure resources.</span></span> <span data-ttu-id="a8867-107">Sin embargo, los elementos de trabajo relacionados con un problema suelen residir en un producto o servicio de ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-107">However, the work items related to an issue  typically reside in an ITSM product/service.</span></span> <span data-ttu-id="a8867-108">El conector de ITSM proporciona una conexión bidireccional entre las herramientas de Azure e ITSM para ayudarle a resolver problemas con mayor rapidez.</span><span class="sxs-lookup"><span data-stu-id="a8867-108">The ITSM connector provides a bi-directional connection between Azure and ITSM tools to help you resolve issues faster.</span></span>

<span data-ttu-id="a8867-109">ITSMC admite conexiones con las siguientes herramientas ITSM:</span><span class="sxs-lookup"><span data-stu-id="a8867-109">ITSMC supports connections with the following ITSM tools:</span></span>

-   <span data-ttu-id="a8867-110">ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-110">ServiceNow</span></span>
-   <span data-ttu-id="a8867-111">System Center Service Manager</span><span class="sxs-lookup"><span data-stu-id="a8867-111">System Center Service Manager</span></span>
-   <span data-ttu-id="a8867-112">Provance</span><span class="sxs-lookup"><span data-stu-id="a8867-112">Provance</span></span>
-   <span data-ttu-id="a8867-113">Cherwell</span><span class="sxs-lookup"><span data-stu-id="a8867-113">Cherwell</span></span>

<span data-ttu-id="a8867-114">Con ITSMC, puede:</span><span class="sxs-lookup"><span data-stu-id="a8867-114">With ITSMC, you can</span></span>

-  <span data-ttu-id="a8867-115">Crear elementos de trabajo en la herramienta de ITSM, en función de las alertas de Azure (alertas de métricas, de Activity Log y de Log Analytics).</span><span class="sxs-lookup"><span data-stu-id="a8867-115">Create work items in ITSM tool, based on your Azure alerts (metric alerts, Activity Log alerts and Log Analytics alerts).</span></span>
-  <span data-ttu-id="a8867-116">Sincronizar de forma opcional los datos de incidentes y solicitudes de cambio de la herramienta ITSM con un área de trabajo de Azure Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="a8867-116">Optionally, you can sync your incident and change request data from your ITSM tool to an Azure Log Analytics workspace.</span></span>


<span data-ttu-id="a8867-117">Puede empezar a usar el conector de ITSM siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a8867-117">You can start using the ITSM Connector using the following steps:</span></span>

1.  <span data-ttu-id="a8867-118">[Agregue la solución del conector de ITSM](#adding-the-it-service-management-connector-solution).</span><span class="sxs-lookup"><span data-stu-id="a8867-118">[Add the ITSM Connector Solution](#adding-the-it-service-management-connector-solution)</span></span>
2.  <span data-ttu-id="a8867-119">[Cree una conexión de ITSM](#creating-an-itsm-connection).</span><span class="sxs-lookup"><span data-stu-id="a8867-119">[Create an ITSM connection](#creating-an-itsm-connection)</span></span>
3.  <span data-ttu-id="a8867-120">[Use la conexión](#using-the-solution).</span><span class="sxs-lookup"><span data-stu-id="a8867-120">[Use the connection](#using-the-solution)</span></span>


##  <a name="adding-the-it-service-management-connector-solution"></a><span data-ttu-id="a8867-121">Agregar la solución IT Service Management Connector</span><span class="sxs-lookup"><span data-stu-id="a8867-121">Adding the IT Service Management Connector Solution</span></span>

<span data-ttu-id="a8867-122">Para poder crear una conexión, debe agregar la solución del conector de ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-122">Before you can create a connection, you need to add the ITSM Connector Solution.</span></span>

1.  <span data-ttu-id="a8867-123">En Azure Portal, haga clic en el icono **+ Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="a8867-123">In Azure portal, click **+ New** icon.</span></span>

    ![Nuevo recurso de Azure](./media/log-analytics-itsmc/azure-add-new-resource.png)

2.  <span data-ttu-id="a8867-125">Busque el **Conector de Administración de servicios de TI** en Marketplace y haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="a8867-125">Search for **IT Service Management Connector** in the Marketplace and click **Create**.</span></span>

    ![Agregar la solución ITSMC](./media/log-analytics-itsmc/add-itsmc-solution.png)

3.  <span data-ttu-id="a8867-127">En la sección **Área de trabajo de OMS**, seleccione el área de trabajo de Azure Log Analytics donde quiera instalar la solución.</span><span class="sxs-lookup"><span data-stu-id="a8867-127">In the **OMS Workspace** section, select the Azure Log Analytics workspace where you want to install the solution.</span></span>
4.  <span data-ttu-id="a8867-128">En la sección **Configuración del área de trabajo de OMS**, seleccione el grupo de recursos donde quiera crear el recurso de la solución.</span><span class="sxs-lookup"><span data-stu-id="a8867-128">In the **OMS Workspace Settings** section, select the ResourceGroup where you want to create the solution resource.</span></span>

    ![Área de trabajo de ITSMC](./media/log-analytics-itsmc/itsmc-solution-workspace.png)

5.  <span data-ttu-id="a8867-130">Haga clic en **Create**(Crear).</span><span class="sxs-lookup"><span data-stu-id="a8867-130">Click **Create**.</span></span>

<span data-ttu-id="a8867-131">Cuando se implemente el recurso de la solución, aparecerá una notificación en la parte superior derecha de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a8867-131">When the solution resource is deployed, a notification appears at the top right of the window.</span></span>


## <a name="creating-an-itsm--connection"></a><span data-ttu-id="a8867-132">Crear una conexión de ITSM</span><span class="sxs-lookup"><span data-stu-id="a8867-132">Creating an ITSM  connection</span></span>

<span data-ttu-id="a8867-133">Después de instalar la solución, puede crear una conexión.</span><span class="sxs-lookup"><span data-stu-id="a8867-133">Once you have installed the solution, you can create a connection.</span></span>

<span data-ttu-id="a8867-134">Para crear una conexión, debe preparar la herramienta de ITSM para permitir la conexión a la solución del conector de ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-134">For creating a connection, you will need to prep your ITSM tool to allow the connection from the ITSM Connector solution.</span></span>  

<span data-ttu-id="a8867-135">Dependiendo del producto ITSM que se vaya a conectar, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a8867-135">Depending on the ITSM product you are connecting to, use the following steps :</span></span>

- [<span data-ttu-id="a8867-136">System Center Service Manager (SCSM)</span><span class="sxs-lookup"><span data-stu-id="a8867-136">System Center Service Manager (SCSM)</span></span>](log-analytics-itsmc-connections.md#connect-system-center-service-manager-to-it-service-management-connector-in-azure)
- [<span data-ttu-id="a8867-137">ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-137">ServiceNow</span></span>](log-analytics-itsmc-connections.md#connect-servicenow-to-it-service-management-connector-in-azure)
- [<span data-ttu-id="a8867-138">Provance</span><span class="sxs-lookup"><span data-stu-id="a8867-138">Provance</span></span>](log-analytics-itsmc-connections.md#connect-provance-to-it-service-management-connector-in-azure)  
- [<span data-ttu-id="a8867-139">Cherwell</span><span class="sxs-lookup"><span data-stu-id="a8867-139">Cherwell</span></span>](log-analytics-itsmc-connections.md#connect-cherwell-to-it-service-management-connector-in-azure)

<span data-ttu-id="a8867-140">Una vez que haya preparado sus herramientas ITSM, siga estos pasos para crear una conexión:</span><span class="sxs-lookup"><span data-stu-id="a8867-140">Once you have prepped your ITSM tools, follow the steps below to create a connection:</span></span>

1.  <span data-ttu-id="a8867-141">Vaya a **Todos los recursos** y busque **ServiceDesk(YourWorkspaceName)**.</span><span class="sxs-lookup"><span data-stu-id="a8867-141">Go to **All Resources**, look for **ServiceDesk(YourWorkspaceName)**.</span></span>
2.  <span data-ttu-id="a8867-142">En la opción **ORÍGENES DE DATOS DEL ÁREA DE TRABAJO** del panel izquierdo, haga clic en **Conexiones de ITSM** .</span><span class="sxs-lookup"><span data-stu-id="a8867-142">Under **WORKSPACE DATA SOURCES** in the left pane, click **ITSM Connections**.</span></span>
    <span data-ttu-id="a8867-143">![Conexiones de ITSM](./media/log-analytics-itsmc/itsm-connections.png)</span><span class="sxs-lookup"><span data-stu-id="a8867-143">![ITSM connections](./media/log-analytics-itsmc/itsm-connections.png)</span></span>

    <span data-ttu-id="a8867-144">En esta página se muestra la lista de conexiones.</span><span class="sxs-lookup"><span data-stu-id="a8867-144">This page displays the list of connections.</span></span>
3.  <span data-ttu-id="a8867-145">Haga clic en **Agregar conexión**.</span><span class="sxs-lookup"><span data-stu-id="a8867-145">Click **Add Connection**.</span></span>

    ![Agregar una conexión de ITSM](./media/log-analytics-itsmc/add-new-itsm-connection.png)

4.  <span data-ttu-id="a8867-147">Especifique la configuración de conexión tal como se describe en el artículo [Configuring the ITSMC connection with your ITSM products/services](log-analytics-itsmc-connections.md) (Configurar la conexión ITSMC con los productos o servicios de ITSM).</span><span class="sxs-lookup"><span data-stu-id="a8867-147">Specify the connection settings as described in [Configuring the ITSMC connection with your ITSM products/services article](log-analytics-itsmc-connections.md).</span></span>

    > [!NOTE]

    > <span data-ttu-id="a8867-148">De forma predeterminada, ITSMC actualiza los datos de configuración de la conexión una vez cada 24 horas.</span><span class="sxs-lookup"><span data-stu-id="a8867-148">By default, ITSMC refreshes the connection's configuration data once in every 24 hours.</span></span> <span data-ttu-id="a8867-149">Para actualizar los datos de la conexión al instante para cualquier modificación o actualizaciones de plantilla que se realicen, haga clic en el botón de actualización que se muestra junto a la conexión.</span><span class="sxs-lookup"><span data-stu-id="a8867-149">To refresh your connection's data instantly for any edits or template updates that you make, click the "Refresh" button displayed next to your connection.</span></span>

    ![Actualizar la conexión](./media/log-analytics-itsmc/itsmc-connections-refresh.png)


## <a name="using-the-solution"></a><span data-ttu-id="a8867-151">Uso de la solución</span><span class="sxs-lookup"><span data-stu-id="a8867-151">Using the solution</span></span>
   <span data-ttu-id="a8867-152">Al usar la solución del Conector ITSM, puede crear elementos de trabajo de alertas de Azure, alertas de Log Analytics y entradas de registros de Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="a8867-152">By using the ITSM Connector solution, you can create work items from Azure alerts, Log Analytics alerts  and  Log Analytics log records.</span></span>

## <a name="create-itsm-work-items-from-azure-alerts"></a><span data-ttu-id="a8867-153">Creación de elementos de trabajo de ITSM a partir de alertas de Azure</span><span class="sxs-lookup"><span data-stu-id="a8867-153">Create ITSM work items from Azure alerts</span></span>

<span data-ttu-id="a8867-154">Una vez que haya creado la conexión a ITSM, puede crear elementos de trabajo en la herramienta de ITSM según las alertas de Azure, mediante la **acción de ITSM** en **Grupos de acciones**.</span><span class="sxs-lookup"><span data-stu-id="a8867-154">Once you have your ITSM connection created, you can create work item(s) in your ITSM tool based on Azure alerts, by using the **ITSM Action** in **Action Groups**.</span></span>

<span data-ttu-id="a8867-155">Los grupos de acciones proporcionan una manera modular y reutilizable de desencadenar acciones para las alertas de Azure.</span><span class="sxs-lookup"><span data-stu-id="a8867-155">Action Groups provide a modular and reusable way of triggering actions for your Azure Alerts.</span></span> <span data-ttu-id="a8867-156">Puede usar los grupos de acciones con alertas de métricas, de Activity Log y de Azure Log Analytics en Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="a8867-156">You can use Action Groups with metric alerts, Activity Log alerts and Azure Log Analytics alerts in Azure portal.</span></span>

<span data-ttu-id="a8867-157">Utilice el siguiente procedimiento:</span><span class="sxs-lookup"><span data-stu-id="a8867-157">Use the following procedure:</span></span>

1. <span data-ttu-id="a8867-158">En Azure Portal, haga clic en **Monitor**</span><span class="sxs-lookup"><span data-stu-id="a8867-158">In Azure portal, click  **Monitor**.</span></span>
2. <span data-ttu-id="a8867-159">En el panel izquierdo, haga clic en **Grupos de acciones**.</span><span class="sxs-lookup"><span data-stu-id="a8867-159">In the left pane, click  **Action groups**.</span></span> <span data-ttu-id="a8867-160">Aparece la ventana **Agregar grupo de acciones**.</span><span class="sxs-lookup"><span data-stu-id="a8867-160">The **Add action group** window appears.</span></span>

    ![Grupos de acciones](media/log-analytics-itsmc/action-groups.png)

3. <span data-ttu-id="a8867-162">Complete los campos **Name** (Nombre) y **ShortName** (Nombre corto) para el grupo de acciones.</span><span class="sxs-lookup"><span data-stu-id="a8867-162">Provide **Name** and **ShortName** for your action group.</span></span> <span data-ttu-id="a8867-163">Seleccione el **grupo de recursos** y la **suscripción** donde quiere crear el grupo de acciones.</span><span class="sxs-lookup"><span data-stu-id="a8867-163">Select the **Resource Group** and **Subscription** where you want to create your action group.</span></span>

    ![Detalle de los grupos de acciones](media/log-analytics-itsmc/action-groups-details.png)

4. <span data-ttu-id="a8867-165">En la lista de acciones, seleccione **ITSM** en la lista desplegable **Tipo de acción**.</span><span class="sxs-lookup"><span data-stu-id="a8867-165">In the Actions list, select **ITSM** from the drop-down menu for **Action Type**.</span></span> <span data-ttu-id="a8867-166">Proporcione un **nombre** para la acción y haga clic en **Editar detalles**.</span><span class="sxs-lookup"><span data-stu-id="a8867-166">Provide a **Name** for the action and click **Edit details**.</span></span>
5. <span data-ttu-id="a8867-167">En **Subscription** (Suscripción), indique dónde se encuentra el área de trabajo de Log Analytics.</span><span class="sxs-lookup"><span data-stu-id="a8867-167">Select the **Subscription** where your Log Analytics workspace is located.</span></span> <span data-ttu-id="a8867-168">Seleccione el nombre de la **conexión** (el nombre del conector ITSM) seguido del nombre del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-168">Select the **Connection** name (your ITSM Connector name) followed by your Workspace name.</span></span> <span data-ttu-id="a8867-169">Por ejemplo, "MiITSMMConnector(MiAreaDeTrabajo)".</span><span class="sxs-lookup"><span data-stu-id="a8867-169">For example, "MyITSMMConnector(MyWorkspace)."</span></span>

    ![Detalles de acción de ITSM](./media/log-analytics-itsmc/itsm-action-details.png)

6. <span data-ttu-id="a8867-171">Seleccione el tipo **Elemento de trabajo** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="a8867-171">Select **Work Item** type from the drop-down menu.</span></span>
   <span data-ttu-id="a8867-172">Elija usar una plantilla existente o rellene los campos requeridos para el producto ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-172">Choose to use an existing template or fill the fields required by your ITSM product.</span></span>
7. <span data-ttu-id="a8867-173">Haga clic en **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8867-173">Click **OK**.</span></span>

<span data-ttu-id="a8867-174">Al crear o editar una regla de alerta de Azure, use un grupo de acciones, que tiene una acción de ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-174">When creating/editing an Azure alert rule, use an Action group, which has an ITSM Action.</span></span> <span data-ttu-id="a8867-175">Cuando se desencadena la alerta, se crea o actualiza un elemento de trabajo en la herramienta ITSM.</span><span class="sxs-lookup"><span data-stu-id="a8867-175">When the alert triggers, work item is created/updated in the ITSM tool.</span></span>

>[!NOTE]

> <span data-ttu-id="a8867-176">Para obtener información sobre los precios de las acciones de ITSM, consulte la [página de precios](https://azure.microsoft.com/pricing/details/monitor/) de los grupos de acciones.</span><span class="sxs-lookup"><span data-stu-id="a8867-176">For information on pricing of ITSM Action, see the [pricing page](https://azure.microsoft.com/pricing/details/monitor/) for Action Groups.</span></span>


## <a name="create-itsm-work-items-from-log-analytics-alerts"></a><span data-ttu-id="a8867-177">Crear elementos de trabajo de ITSM para alertas de Log Analytics</span><span class="sxs-lookup"><span data-stu-id="a8867-177">Create ITSM work items from Log Analytics alerts</span></span>

<span data-ttu-id="a8867-178">Para configurar las reglas de alertas en el portal de Azure Log Analytics para crear elementos de trabajo en la herramienta de ITSM, siga el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="a8867-178">You can configure alert rules in Azure Log Analytics portal to create work items in ITSM tool, using the following procedure.</span></span>

1. <span data-ttu-id="a8867-179">En la ventana **Búsqueda de registros**, ejecute una consulta de búsqueda de registros para ver los datos.</span><span class="sxs-lookup"><span data-stu-id="a8867-179">From **Log Search** window, run a log search query to view data.</span></span> <span data-ttu-id="a8867-180">Los resultados de la consulta son el origen de los elementos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-180">Query results are the source for work items.</span></span>
2. <span data-ttu-id="a8867-181">En **Búsqueda de registros**, haga clic en **Alerta** para abrir la página **Agregar regla de alerta**.</span><span class="sxs-lookup"><span data-stu-id="a8867-181">In **Log Search**, click **Alert** to open the **Add Alert Rule** page.</span></span>

    ![Pantalla de Log Analytics](./media/log-analytics-itsmc/itsmc-work-items-for-azure-alerts.png)

3. <span data-ttu-id="a8867-183">En la ventana **Agregar regla de alerta**, proporcione los detalles necesarios para **Nombre**, **Gravedad**, **Consulta de búsqueda** y **Criterios de alerta** (Ventana de tiempo/unidad métrica).</span><span class="sxs-lookup"><span data-stu-id="a8867-183">On the **Add Alert Rule** window, provide the required details for **Name**, **Severity**,  **Search query**, and **Alert criteria** (Time Window/Metric measurement).</span></span>
4. <span data-ttu-id="a8867-184">Seleccione **Sí** en **Acciones de ITSM**.</span><span class="sxs-lookup"><span data-stu-id="a8867-184">Select **Yes** for **ITSM Actions**.</span></span>
5. <span data-ttu-id="a8867-185">Seleccione la conexión de ITSM en la lista **Conexión seleccionada**.</span><span class="sxs-lookup"><span data-stu-id="a8867-185">Select your ITSM connection from the **Select Connection** list.</span></span>
6. <span data-ttu-id="a8867-186">Proporcione los detalles requeridos.</span><span class="sxs-lookup"><span data-stu-id="a8867-186">Provide the details as required.</span></span>
7. <span data-ttu-id="a8867-187">Para crear un elemento de trabajo independiente para cada entrada de registro de esta alerta, active la casilla **Crear elementos de trabajo individuales para cada entrada de registro**.</span><span class="sxs-lookup"><span data-stu-id="a8867-187">To create a separate work item for each log entry of this alert, select the **Create individual work items for each log entry** checkbox.</span></span>

    <span data-ttu-id="a8867-188">o</span><span class="sxs-lookup"><span data-stu-id="a8867-188">Or</span></span>

    <span data-ttu-id="a8867-189">deje desactivada esta casilla para crear solo un elemento de trabajo para cualquier número de entradas de registro en esta alerta.</span><span class="sxs-lookup"><span data-stu-id="a8867-189">leave this checkbox unselected to create only one work item for any number of log entries under this alert.</span></span>

7. <span data-ttu-id="a8867-190">Haga clic en **Save**(Guardar).</span><span class="sxs-lookup"><span data-stu-id="a8867-190">Click **Save**.</span></span>

<span data-ttu-id="a8867-191">Puede ver la alerta de Log Analytics que creó en **Configuración > Alertas**.</span><span class="sxs-lookup"><span data-stu-id="a8867-191">You can view the  Log Analytics alert that you created under **Settings>Alerts**.</span></span> <span data-ttu-id="a8867-192">Los elementos de trabajo de la conexión de ITSM correspondientes se crean cuando se cumple la condición de la alerta especificada.</span><span class="sxs-lookup"><span data-stu-id="a8867-192">The corresponding ITSM connection's work items are created when the specified alert's condition is met.</span></span>


## <a name="create-itsm-work-items-from-log-analytics-log-records"></a><span data-ttu-id="a8867-193">Crear elementos de trabajo de ITSM a partir de los registros de Log Analytics</span><span class="sxs-lookup"><span data-stu-id="a8867-193">Create ITSM work items from Log Analytics log records</span></span>

<span data-ttu-id="a8867-194">También puede crear elementos de trabajo en los orígenes de ITSM conectados directamente desde una entrada de registro.</span><span class="sxs-lookup"><span data-stu-id="a8867-194">You can also create work items in the connected ITSM sources directly from a log record.</span></span> <span data-ttu-id="a8867-195">Esto puede utilizarse para probar si la conexión funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="a8867-195">This can be used to test if the connection is working properly.</span></span>


1. <span data-ttu-id="a8867-196">En **Búsqueda de registros**, busque los datos requeridos, seleccione el detalle y haga clic en **Crear elemento de trabajo**.</span><span class="sxs-lookup"><span data-stu-id="a8867-196">From **Log Search**,  search the required data, select the detail, and click **Create work item**.</span></span>

    <span data-ttu-id="a8867-197">Aparece la ventana **Crear elemento de trabajo de ITSM**:</span><span class="sxs-lookup"><span data-stu-id="a8867-197">The **Create ITSM Work Item** window appears:</span></span>

    ![Pantalla de Log Analytics](media/log-analytics-itsmc/itsmc-work-items-from-azure-logs.png)

2.   <span data-ttu-id="a8867-199">Agregue los detalles siguientes:</span><span class="sxs-lookup"><span data-stu-id="a8867-199">Add the following details:</span></span>

  - <span data-ttu-id="a8867-200">**Título de elemento de trabajo**: el título del elemento de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-200">**Work item Title**: Title for the work item.</span></span>
  - <span data-ttu-id="a8867-201">**Descripción de elemento de trabajo**: la descripción del nuevo elemento de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-201">**Work item Description**: Description for the new work item.</span></span>
  - <span data-ttu-id="a8867-202">**Equipo afectado**: el nombre del equipo en que se encontraron estos datos de registro.</span><span class="sxs-lookup"><span data-stu-id="a8867-202">**Affected Computer**: Name of the computer where this log data was found.</span></span>
  - <span data-ttu-id="a8867-203">**Conexión seleccionada**: la conexión ITSM en la que desea crear este elemento de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-203">**Select Connection**:  ITSM connection in which you want to create this work item.</span></span>
  - <span data-ttu-id="a8867-204">**Elemento de trabajo**: tipo de elemento de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a8867-204">**Work item**:  Type of work item.</span></span>

3. <span data-ttu-id="a8867-205">Para usar una plantilla de elemento de trabajo existente para un incidente, haga clic en **Sí** en la opción **Generar elemento de trabajo basado en plantilla** y, luego, haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="a8867-205">To use an existing work item template for an incident, click **Yes** under **Generate Work item based on Template** option and then click **Create**.</span></span>

    <span data-ttu-id="a8867-206">O bien,</span><span class="sxs-lookup"><span data-stu-id="a8867-206">Or,</span></span>

    <span data-ttu-id="a8867-207">Haga clic en **No** si desea proporcionar valores personalizados.</span><span class="sxs-lookup"><span data-stu-id="a8867-207">Click **No** if you want to provide your customized values.</span></span>

4. <span data-ttu-id="a8867-208">Proporcione los valores adecuados en los cuadros de texto **Tipo de contacto**, **Impacto**, **Urgencia**, **Categoría** y **Subcategoría** y, luego, haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="a8867-208">Provide the appropriate values in the **Contact Type**, **Impact**, **Urgency**, **Category**, and **Sub Category** text boxes, and then click **Create**.</span></span>


##<a name="visualize-and-analyze-the-incident-and-change-request-data"></a><span data-ttu-id="a8867-209">Visualizar y analizar los datos de incidentes y solicitudes de cambios</span><span class="sxs-lookup"><span data-stu-id="a8867-209">Visualize and analyze the incident and change request data</span></span>

<span data-ttu-id="a8867-210">Si se tienen en cuenta las opciones de configuración de una conexión, el Conector ITSM puede sincronizar hasta 120 días de datos referentes a incidentes y a solicitudes cambios.</span><span class="sxs-lookup"><span data-stu-id="a8867-210">Based on your configuration when setting up a connection, ITSM connector can sync up to 120 days of Incident and Change request data.</span></span> <span data-ttu-id="a8867-211">El esquema de registros de estos datos se proporciona en la [próxima sección](#additional-information).</span><span class="sxs-lookup"><span data-stu-id="a8867-211">The log record schema for this data is provided in the [next section](#additional-information).</span></span>

<span data-ttu-id="a8867-212">Gracias al panel del Conector ITSM en la solución, se pueden visualizar los datos de incidentes y solicitudes de cambios.</span><span class="sxs-lookup"><span data-stu-id="a8867-212">The incident and change request data can be visualized using the ITSM Connector dashboard in the solution.</span></span>

![Pantalla de Log Analytics](./media/log-analytics-itsmc/itsmc-overview-sample-log-analytics.png)

<span data-ttu-id="a8867-214">Asimismo, el panel también proporciona información acerca del estado del conector que se puede usar como punto de partida para analizar cualquier problema con las conexiones.</span><span class="sxs-lookup"><span data-stu-id="a8867-214">The dashboard also provides information on connector status which can be used as a starting point to analyze any issues with the connections.</span></span>

<span data-ttu-id="a8867-215">También puede visualizar los incidentes que se sincronizan con los equipos afectados dentro de la solución Service Map.</span><span class="sxs-lookup"><span data-stu-id="a8867-215">You can also visualize the incidents synced against the impacted computers, within the Service Map solution.</span></span>

<span data-ttu-id="a8867-216">Mapa de servicio detecta automáticamente los componentes de la aplicación en sistemas Windows y Linux y asigna la comunicación entre servicios.</span><span class="sxs-lookup"><span data-stu-id="a8867-216">Service Map automatically discovers the application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="a8867-217">Permite ver los servidores a medida que piensa en ellos, como los sistemas interconectados que ofrecen servicios críticos.</span><span class="sxs-lookup"><span data-stu-id="a8867-217">It allows you to view your servers as you think of them – as interconnected systems that deliver critical services.</span></span> <span data-ttu-id="a8867-218">Mapa de servicio muestra las conexiones entre servidores, procesos y puertos en cualquier arquitectura conectada TCP sin una configuración necesaria que sea distinta a la instalación de un agente.</span><span class="sxs-lookup"><span data-stu-id="a8867-218">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture with no configuration required other than installation of an agent.</span></span> <span data-ttu-id="a8867-219">[Más información](../operations-management-suite/operations-management-suite-service-map.md).</span><span class="sxs-lookup"><span data-stu-id="a8867-219">[Learn more](../operations-management-suite/operations-management-suite-service-map.md).</span></span>

<span data-ttu-id="a8867-220">Si usa la solución Service Map, puede ver los elementos de la consola de servicio creados en la solución ITSM tal como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a8867-220">If you are using the Service Map solution, you can view the service desk items created in the ITSM solutions as shown in the following example:</span></span>

![Pantalla de Log Analytics](./media/log-analytics-itsmc/itsmc-overview-integrated-solutions.png)

<span data-ttu-id="a8867-222">Obtenga más información en: [Service Map](../operations-management-suite/operations-management-suite-service-map.md).</span><span class="sxs-lookup"><span data-stu-id="a8867-222">More information: [Service Map](../operations-management-suite/operations-management-suite-service-map.md)</span></span>


## <a name="additional-information"></a><span data-ttu-id="a8867-223">Información adicional</span><span class="sxs-lookup"><span data-stu-id="a8867-223">Additional information</span></span>

### <a name="data-synced-from-itsm-product"></a><span data-ttu-id="a8867-224">Datos que se sincronizan del producto ITSM</span><span class="sxs-lookup"><span data-stu-id="a8867-224">Data synced from ITSM product</span></span>
<span data-ttu-id="a8867-225">Los incidentes y las solicitudes de cambio se sincronizan desde el producto ITSM con el área de trabajo de Log Analytics según la configuración de la conexión.</span><span class="sxs-lookup"><span data-stu-id="a8867-225">Incidents and change requests are synced from your ITSM product to your Log Analytics workspace based on the connection's configuration.</span></span>

<span data-ttu-id="a8867-226">En la siguiente información se muestran ejemplos de datos recopilados por ITSMC:</span><span class="sxs-lookup"><span data-stu-id="a8867-226">The following information shows examples of data gathered by ITSMC:</span></span>

> [!NOTE]

> <span data-ttu-id="a8867-227">En función del tipo de elemento de trabajo que se importa a Log Analytics, **ServiceDesk_CL** contiene los campos siguientes:</span><span class="sxs-lookup"><span data-stu-id="a8867-227">Depending on the work item type imported into Log Analytics, **ServiceDesk_CL** contains the following fields:</span></span>

<span data-ttu-id="a8867-228">**Elemento de trabajo:****incidentes**</span><span class="sxs-lookup"><span data-stu-id="a8867-228">**Work item:** **Incidents**</span></span>  
<span data-ttu-id="a8867-229">ServiceDeskWorkItemType_s="Incidente"</span><span class="sxs-lookup"><span data-stu-id="a8867-229">ServiceDeskWorkItemType_s="Incident"</span></span>

<span data-ttu-id="a8867-230">**Fields**</span><span class="sxs-lookup"><span data-stu-id="a8867-230">**Fields**</span></span>

- <span data-ttu-id="a8867-231">ServiceDeskConnectionName</span><span class="sxs-lookup"><span data-stu-id="a8867-231">ServiceDeskConnectionName</span></span>
- <span data-ttu-id="a8867-232">Service Desk ID</span><span class="sxs-lookup"><span data-stu-id="a8867-232">Service Desk ID</span></span>
- <span data-ttu-id="a8867-233">Estado</span><span class="sxs-lookup"><span data-stu-id="a8867-233">State</span></span>
- <span data-ttu-id="a8867-234">Urgencia</span><span class="sxs-lookup"><span data-stu-id="a8867-234">Urgency</span></span>
- <span data-ttu-id="a8867-235">Impacto</span><span class="sxs-lookup"><span data-stu-id="a8867-235">Impact</span></span>
- <span data-ttu-id="a8867-236">Prioridad</span><span class="sxs-lookup"><span data-stu-id="a8867-236">Priority</span></span>
- <span data-ttu-id="a8867-237">Escalado</span><span class="sxs-lookup"><span data-stu-id="a8867-237">Escalation</span></span>
- <span data-ttu-id="a8867-238">Creado por</span><span class="sxs-lookup"><span data-stu-id="a8867-238">Created By</span></span>
- <span data-ttu-id="a8867-239">Resuelto por</span><span class="sxs-lookup"><span data-stu-id="a8867-239">Resolved By</span></span>
- <span data-ttu-id="a8867-240">Cerrado por</span><span class="sxs-lookup"><span data-stu-id="a8867-240">Closed By</span></span>
- <span data-ttu-id="a8867-241">Origen</span><span class="sxs-lookup"><span data-stu-id="a8867-241">Source</span></span>
- <span data-ttu-id="a8867-242">Asignado a</span><span class="sxs-lookup"><span data-stu-id="a8867-242">Assigned To</span></span>
- <span data-ttu-id="a8867-243">Categoría</span><span class="sxs-lookup"><span data-stu-id="a8867-243">Category</span></span>
- <span data-ttu-id="a8867-244">Título</span><span class="sxs-lookup"><span data-stu-id="a8867-244">Title</span></span>
- <span data-ttu-id="a8867-245">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="a8867-245">Description</span></span>
- <span data-ttu-id="a8867-246">Fecha de creación</span><span class="sxs-lookup"><span data-stu-id="a8867-246">Created Date</span></span>
- <span data-ttu-id="a8867-247">Fecha de cierre</span><span class="sxs-lookup"><span data-stu-id="a8867-247">Closed Date</span></span>
- <span data-ttu-id="a8867-248">Fecha de resolución</span><span class="sxs-lookup"><span data-stu-id="a8867-248">Resolved Date</span></span>
- <span data-ttu-id="a8867-249">Fecha de última modificación</span><span class="sxs-lookup"><span data-stu-id="a8867-249">Last Modified Date</span></span>
- <span data-ttu-id="a8867-250">Equipo</span><span class="sxs-lookup"><span data-stu-id="a8867-250">Computer</span></span>


<span data-ttu-id="a8867-251">**Elemento de trabajo:****solicitudes de cambio**</span><span class="sxs-lookup"><span data-stu-id="a8867-251">**Work item:** **Change Requests**</span></span>

<span data-ttu-id="a8867-252">ServiceDeskWorkItemType_s="ChangeRequest"</span><span class="sxs-lookup"><span data-stu-id="a8867-252">ServiceDeskWorkItemType_s="ChangeRequest"</span></span>

<span data-ttu-id="a8867-253">**Fields**</span><span class="sxs-lookup"><span data-stu-id="a8867-253">**Fields**</span></span>
- <span data-ttu-id="a8867-254">ServiceDeskConnectionName</span><span class="sxs-lookup"><span data-stu-id="a8867-254">ServiceDeskConnectionName</span></span>
- <span data-ttu-id="a8867-255">Service Desk ID</span><span class="sxs-lookup"><span data-stu-id="a8867-255">Service Desk ID</span></span>
- <span data-ttu-id="a8867-256">Creado por</span><span class="sxs-lookup"><span data-stu-id="a8867-256">Created By</span></span>
- <span data-ttu-id="a8867-257">Cerrado por</span><span class="sxs-lookup"><span data-stu-id="a8867-257">Closed By</span></span>
- <span data-ttu-id="a8867-258">Origen</span><span class="sxs-lookup"><span data-stu-id="a8867-258">Source</span></span>
- <span data-ttu-id="a8867-259">Asignado a</span><span class="sxs-lookup"><span data-stu-id="a8867-259">Assigned To</span></span>
- <span data-ttu-id="a8867-260">Título</span><span class="sxs-lookup"><span data-stu-id="a8867-260">Title</span></span>
- <span data-ttu-id="a8867-261">type</span><span class="sxs-lookup"><span data-stu-id="a8867-261">Type</span></span>
- <span data-ttu-id="a8867-262">Categoría</span><span class="sxs-lookup"><span data-stu-id="a8867-262">Category</span></span>
- <span data-ttu-id="a8867-263">Estado</span><span class="sxs-lookup"><span data-stu-id="a8867-263">State</span></span>
- <span data-ttu-id="a8867-264">Escalado</span><span class="sxs-lookup"><span data-stu-id="a8867-264">Escalation</span></span>
- <span data-ttu-id="a8867-265">Estado del conflicto</span><span class="sxs-lookup"><span data-stu-id="a8867-265">Conflict Status</span></span>
- <span data-ttu-id="a8867-266">Urgencia</span><span class="sxs-lookup"><span data-stu-id="a8867-266">Urgency</span></span>
- <span data-ttu-id="a8867-267">Prioridad</span><span class="sxs-lookup"><span data-stu-id="a8867-267">Priority</span></span>
- <span data-ttu-id="a8867-268">Riesgo</span><span class="sxs-lookup"><span data-stu-id="a8867-268">Risk</span></span>
- <span data-ttu-id="a8867-269">Impacto</span><span class="sxs-lookup"><span data-stu-id="a8867-269">Impact</span></span>
- <span data-ttu-id="a8867-270">Asignado a</span><span class="sxs-lookup"><span data-stu-id="a8867-270">Assigned To</span></span>
- <span data-ttu-id="a8867-271">Fecha de creación</span><span class="sxs-lookup"><span data-stu-id="a8867-271">Created Date</span></span>
- <span data-ttu-id="a8867-272">Fecha de cierre</span><span class="sxs-lookup"><span data-stu-id="a8867-272">Closed Date</span></span>
- <span data-ttu-id="a8867-273">Fecha de última modificación</span><span class="sxs-lookup"><span data-stu-id="a8867-273">Last Modified Date</span></span>
- <span data-ttu-id="a8867-274">Fecha de solicitud</span><span class="sxs-lookup"><span data-stu-id="a8867-274">Requested Date</span></span>
- <span data-ttu-id="a8867-275">Fecha de inicio planeada</span><span class="sxs-lookup"><span data-stu-id="a8867-275">Planned Start Date</span></span>
- <span data-ttu-id="a8867-276">Fecha de finalización planeada</span><span class="sxs-lookup"><span data-stu-id="a8867-276">Planned End Date</span></span>
- <span data-ttu-id="a8867-277">Fecha de inicio del trabajo</span><span class="sxs-lookup"><span data-stu-id="a8867-277">Work Start Date</span></span>
- <span data-ttu-id="a8867-278">Fecha de finalización del trabajo</span><span class="sxs-lookup"><span data-stu-id="a8867-278">Work End Date</span></span>
- <span data-ttu-id="a8867-279">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="a8867-279">Description</span></span>
- <span data-ttu-id="a8867-280">Equipo</span><span class="sxs-lookup"><span data-stu-id="a8867-280">Computer</span></span>

## <a name="output-data-for-a-servicenow-incident"></a><span data-ttu-id="a8867-281">Datos de salida para un incidente de ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-281">Output data for a ServiceNow incident</span></span>

| <span data-ttu-id="a8867-282">Campo de Log Analytics</span><span class="sxs-lookup"><span data-stu-id="a8867-282">Log Analytics field</span></span> | <span data-ttu-id="a8867-283">Campo de ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-283">ServiceNow field</span></span> |
|:--- |:--- |
| <span data-ttu-id="a8867-284">ServiceDeskId_s</span><span class="sxs-lookup"><span data-stu-id="a8867-284">ServiceDeskId_s</span></span>| <span data-ttu-id="a8867-285">Number</span><span class="sxs-lookup"><span data-stu-id="a8867-285">Number</span></span> |
| <span data-ttu-id="a8867-286">IncidentState_s</span><span class="sxs-lookup"><span data-stu-id="a8867-286">IncidentState_s</span></span> | <span data-ttu-id="a8867-287">Estado</span><span class="sxs-lookup"><span data-stu-id="a8867-287">State</span></span> |
| <span data-ttu-id="a8867-288">Urgency_s</span><span class="sxs-lookup"><span data-stu-id="a8867-288">Urgency_s</span></span> |<span data-ttu-id="a8867-289">Urgencia</span><span class="sxs-lookup"><span data-stu-id="a8867-289">Urgency</span></span> |
| <span data-ttu-id="a8867-290">Impact_s</span><span class="sxs-lookup"><span data-stu-id="a8867-290">Impact_s</span></span> |<span data-ttu-id="a8867-291">Impacto</span><span class="sxs-lookup"><span data-stu-id="a8867-291">Impact</span></span>|
| <span data-ttu-id="a8867-292">Priority_s</span><span class="sxs-lookup"><span data-stu-id="a8867-292">Priority_s</span></span> | <span data-ttu-id="a8867-293">Prioridad</span><span class="sxs-lookup"><span data-stu-id="a8867-293">Priority</span></span> |
| <span data-ttu-id="a8867-294">CreatedBy_s</span><span class="sxs-lookup"><span data-stu-id="a8867-294">CreatedBy_s</span></span> | <span data-ttu-id="a8867-295">Abierto por</span><span class="sxs-lookup"><span data-stu-id="a8867-295">Opened by</span></span> |
| <span data-ttu-id="a8867-296">ResolvedBy_s</span><span class="sxs-lookup"><span data-stu-id="a8867-296">ResolvedBy_s</span></span> | <span data-ttu-id="a8867-297">Resuelto por</span><span class="sxs-lookup"><span data-stu-id="a8867-297">Resolved by</span></span>|
| <span data-ttu-id="a8867-298">ClosedBy_s</span><span class="sxs-lookup"><span data-stu-id="a8867-298">ClosedBy_s</span></span>  | <span data-ttu-id="a8867-299">Cerrado por</span><span class="sxs-lookup"><span data-stu-id="a8867-299">Closed by</span></span> |
| <span data-ttu-id="a8867-300">Source_s</span><span class="sxs-lookup"><span data-stu-id="a8867-300">Source_s</span></span>| <span data-ttu-id="a8867-301">Tipo de contacto</span><span class="sxs-lookup"><span data-stu-id="a8867-301">Contact type</span></span> |
| <span data-ttu-id="a8867-302">AssignedTo_s</span><span class="sxs-lookup"><span data-stu-id="a8867-302">AssignedTo_s</span></span> | <span data-ttu-id="a8867-303">Asignado a</span><span class="sxs-lookup"><span data-stu-id="a8867-303">Assigned to</span></span>  |
| <span data-ttu-id="a8867-304">Category_s</span><span class="sxs-lookup"><span data-stu-id="a8867-304">Category_s</span></span> | <span data-ttu-id="a8867-305">Categoría</span><span class="sxs-lookup"><span data-stu-id="a8867-305">Category</span></span> |
| <span data-ttu-id="a8867-306">Title_s</span><span class="sxs-lookup"><span data-stu-id="a8867-306">Title_s</span></span>|  <span data-ttu-id="a8867-307">Descripción breve</span><span class="sxs-lookup"><span data-stu-id="a8867-307">Short description</span></span> |
| <span data-ttu-id="a8867-308">Description_s</span><span class="sxs-lookup"><span data-stu-id="a8867-308">Description_s</span></span>|  <span data-ttu-id="a8867-309">Notas</span><span class="sxs-lookup"><span data-stu-id="a8867-309">Notes</span></span> |
| <span data-ttu-id="a8867-310">CreatedDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-310">CreatedDate_t</span></span>|  <span data-ttu-id="a8867-311">Abierto</span><span class="sxs-lookup"><span data-stu-id="a8867-311">Opened</span></span> |
| <span data-ttu-id="a8867-312">ClosedDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-312">ClosedDate_t</span></span>| <span data-ttu-id="a8867-313">closed</span><span class="sxs-lookup"><span data-stu-id="a8867-313">closed</span></span>|
| <span data-ttu-id="a8867-314">ResolvedDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-314">ResolvedDate_t</span></span>|<span data-ttu-id="a8867-315">Resuelto</span><span class="sxs-lookup"><span data-stu-id="a8867-315">Resolved</span></span>|
| <span data-ttu-id="a8867-316">Equipo</span><span class="sxs-lookup"><span data-stu-id="a8867-316">Computer</span></span>  | <span data-ttu-id="a8867-317">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="a8867-317">Configuration item</span></span> |

## <a name="output-data-for-a-servicenow-change-request"></a><span data-ttu-id="a8867-318">Datos de salida para una solicitud de cambio de ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-318">Output data for a ServiceNow change request</span></span>

| <span data-ttu-id="a8867-319">Log Analytics</span><span class="sxs-lookup"><span data-stu-id="a8867-319">Log Analytics</span></span> | <span data-ttu-id="a8867-320">Campo de ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a8867-320">ServieNow field</span></span> |
|:--- |:--- |
| <span data-ttu-id="a8867-321">ServiceDeskId_s</span><span class="sxs-lookup"><span data-stu-id="a8867-321">ServiceDeskId_s</span></span>| <span data-ttu-id="a8867-322">Number</span><span class="sxs-lookup"><span data-stu-id="a8867-322">Number</span></span> |
| <span data-ttu-id="a8867-323">CreatedBy_s</span><span class="sxs-lookup"><span data-stu-id="a8867-323">CreatedBy_s</span></span> | <span data-ttu-id="a8867-324">Solicitado por</span><span class="sxs-lookup"><span data-stu-id="a8867-324">Requested by</span></span> |
| <span data-ttu-id="a8867-325">ClosedBy_s</span><span class="sxs-lookup"><span data-stu-id="a8867-325">ClosedBy_s</span></span> | <span data-ttu-id="a8867-326">Cerrado por</span><span class="sxs-lookup"><span data-stu-id="a8867-326">Closed by</span></span> |
| <span data-ttu-id="a8867-327">AssignedTo_s</span><span class="sxs-lookup"><span data-stu-id="a8867-327">AssignedTo_s</span></span> | <span data-ttu-id="a8867-328">Asignado a</span><span class="sxs-lookup"><span data-stu-id="a8867-328">Assigned to</span></span>  |
| <span data-ttu-id="a8867-329">Title_s</span><span class="sxs-lookup"><span data-stu-id="a8867-329">Title_s</span></span>|  <span data-ttu-id="a8867-330">Descripción breve</span><span class="sxs-lookup"><span data-stu-id="a8867-330">Short description</span></span> |
| <span data-ttu-id="a8867-331">Type_s</span><span class="sxs-lookup"><span data-stu-id="a8867-331">Type_s</span></span>|  <span data-ttu-id="a8867-332">type</span><span class="sxs-lookup"><span data-stu-id="a8867-332">Type</span></span> |
| <span data-ttu-id="a8867-333">Category_s</span><span class="sxs-lookup"><span data-stu-id="a8867-333">Category_s</span></span>|  <span data-ttu-id="a8867-334">Categoría</span><span class="sxs-lookup"><span data-stu-id="a8867-334">Category</span></span> |
| <span data-ttu-id="a8867-335">CRState_s</span><span class="sxs-lookup"><span data-stu-id="a8867-335">CRState_s</span></span>|  <span data-ttu-id="a8867-336">Estado</span><span class="sxs-lookup"><span data-stu-id="a8867-336">State</span></span>|
| <span data-ttu-id="a8867-337">Urgency_s</span><span class="sxs-lookup"><span data-stu-id="a8867-337">Urgency_s</span></span>|  <span data-ttu-id="a8867-338">Urgencia</span><span class="sxs-lookup"><span data-stu-id="a8867-338">Urgency</span></span> |
| <span data-ttu-id="a8867-339">Priority_s</span><span class="sxs-lookup"><span data-stu-id="a8867-339">Priority_s</span></span>| <span data-ttu-id="a8867-340">Prioridad</span><span class="sxs-lookup"><span data-stu-id="a8867-340">Priority</span></span>|
| <span data-ttu-id="a8867-341">Risk_s</span><span class="sxs-lookup"><span data-stu-id="a8867-341">Risk_s</span></span>| <span data-ttu-id="a8867-342">Riesgo</span><span class="sxs-lookup"><span data-stu-id="a8867-342">Risk</span></span>|
| <span data-ttu-id="a8867-343">Impact_s</span><span class="sxs-lookup"><span data-stu-id="a8867-343">Impact_s</span></span>| <span data-ttu-id="a8867-344">Impacto</span><span class="sxs-lookup"><span data-stu-id="a8867-344">Impact</span></span>|
| <span data-ttu-id="a8867-345">RequestedDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-345">RequestedDate_t</span></span>  | <span data-ttu-id="a8867-346">Solicitado por fecha</span><span class="sxs-lookup"><span data-stu-id="a8867-346">Requested by date</span></span> |
| <span data-ttu-id="a8867-347">ClosedDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-347">ClosedDate_t</span></span> | <span data-ttu-id="a8867-348">Fecha de cierre</span><span class="sxs-lookup"><span data-stu-id="a8867-348">Closed date</span></span> |
| <span data-ttu-id="a8867-349">PlannedStartDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-349">PlannedStartDate_t</span></span>  |     <span data-ttu-id="a8867-350">Fecha de inicio planeada</span><span class="sxs-lookup"><span data-stu-id="a8867-350">Planned start date</span></span> |
| <span data-ttu-id="a8867-351">PlannedEndDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-351">PlannedEndDate_t</span></span>  |   <span data-ttu-id="a8867-352">Fecha de finalización planeada</span><span class="sxs-lookup"><span data-stu-id="a8867-352">Planned end date</span></span> |
| <span data-ttu-id="a8867-353">WorkStartDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-353">WorkStartDate_t</span></span>  | <span data-ttu-id="a8867-354">Fecha de inicio real</span><span class="sxs-lookup"><span data-stu-id="a8867-354">Actual start date</span></span> |
| <span data-ttu-id="a8867-355">WorkEndDate_t</span><span class="sxs-lookup"><span data-stu-id="a8867-355">WorkEndDate_t</span></span> | <span data-ttu-id="a8867-356">Fecha de finalización real</span><span class="sxs-lookup"><span data-stu-id="a8867-356">Actual end date</span></span>|
| <span data-ttu-id="a8867-357">Description_s</span><span class="sxs-lookup"><span data-stu-id="a8867-357">Description_s</span></span> | <span data-ttu-id="a8867-358">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="a8867-358">Description</span></span> |
| <span data-ttu-id="a8867-359">Equipo</span><span class="sxs-lookup"><span data-stu-id="a8867-359">Computer</span></span>  | <span data-ttu-id="a8867-360">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="a8867-360">Configuration Item</span></span> |


## <a name="troubleshoot-itsm-connections"></a><span data-ttu-id="a8867-361">Solución de problemas de conexión de ITSM</span><span class="sxs-lookup"><span data-stu-id="a8867-361">Troubleshoot ITSM connections</span></span>
1.  <span data-ttu-id="a8867-362">Si se produce un error en la conexión de la UI del origen conectado y recibe el mensaje **Error al guardar la conexión**, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a8867-362">If connection fails from connected source's UI with an **Error in saving connection** message, take the following steps:</span></span>
- <span data-ttu-id="a8867-363">En el caso de conexiones de ServiceNow, Cherwell y Provance,</span><span class="sxs-lookup"><span data-stu-id="a8867-363">For ServiceNow, Cherwell and Provance connections,</span></span>  
           <span data-ttu-id="a8867-364">- Asegúrese de que ha introducido correctamente el nombre de usuario, la contraseña, el identificador de cliente y el secreto de cliente de cada una de las conexiones.</span><span class="sxs-lookup"><span data-stu-id="a8867-364">- ensure you correctly entered  the username, password, client ID, and client secret  for each of the connections.</span></span>  
           <span data-ttu-id="a8867-365">Compruebe si dispone de privilegios suficientes en el producto ITSM correspondiente para realizar la conexión.</span><span class="sxs-lookup"><span data-stu-id="a8867-365">- check if you have sufficient privileges in the corresponding ITSM product to make the connection.</span></span>  
- <span data-ttu-id="a8867-366">En el caso de conexiones de Service Manager,</span><span class="sxs-lookup"><span data-stu-id="a8867-366">For Service Manager connections,</span></span>  
           <span data-ttu-id="a8867-367">- Asegúrese de que la aplicación web se implementa correctamente y se crea la conexión híbrida.</span><span class="sxs-lookup"><span data-stu-id="a8867-367">- ensure that the Web app is successfully deployed and hybrid connection is created.</span></span> <span data-ttu-id="a8867-368">Para comprobar que la conexión se ha establecido correctamente con el equipo de Service Manager local, visite la dirección URL de la aplicación web como se detalla en la documentación para realizar la [conexión híbrida](log-analytics-itsmc-connections.md#configure-the-hybrid-connection).</span><span class="sxs-lookup"><span data-stu-id="a8867-368">To verify the connection is successfully established with the on-prem Service Manager machine, visit the  Web app URL as detailed in the documentation for making the [hybrid connection](log-analytics-itsmc-connections.md#configure-the-hybrid-connection).</span></span>  

2.  <span data-ttu-id="a8867-369">Si los datos de ServiceNow no se sincronizan con Log Analytics, asegúrese de que la instancia de ServiceNow no esté suspendida.</span><span class="sxs-lookup"><span data-stu-id="a8867-369">If data from ServiceNow is not getting synced to Log Analytics, ensure that the ServiceNow instance is not sleeping.</span></span> <span data-ttu-id="a8867-370">En algunas ocasiones, las instancias de desarrollo de ServiceNow se suspenden si están inactivas durante mucho tiempo.</span><span class="sxs-lookup"><span data-stu-id="a8867-370">ServiceNow Dev Instances sometimes go to sleep when idle for a long period.</span></span> <span data-ttu-id="a8867-371">En caso contrario, notifique el problema.</span><span class="sxs-lookup"><span data-stu-id="a8867-371">Else, report the issue.</span></span>
3.  <span data-ttu-id="a8867-372">Si se generan alertas de OMS, pero no se crean elementos de trabajo en el producto de ITSM, no se crean elementos de configuración o no se vinculan a elementos de trabajo, o, simplemente, quiere más información general, consulte:</span><span class="sxs-lookup"><span data-stu-id="a8867-372">If OMS Alerts fire but work items are not created in ITSM product or configuration items are not created/linked to work items or for any other generic information, look in the following places:</span></span>
 -  <span data-ttu-id="a8867-373">ITSMC: La solución muestra un resumen de conexiones, elementos de trabajo, equipos, etc. Haga clic en el icono que muestra **Estado del conector**, que le lleva a **Búsqueda de registros** con la consulta correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a8867-373">ITSMC: The solution shows a summary of connections/work items/computers etc. Click the tile showing **Connector Status**, which takes you to **Log Search**  with the relevant query.</span></span> <span data-ttu-id="a8867-374">Para obtener más información, consulte las entradas del registro con LogType_S como ERROR para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="a8867-374">Look at the log records with LogType_S as ERROR for more information.</span></span>
 - <span data-ttu-id="a8867-375">Página **Búsqueda de registros**: vea directamente los errores y la información relacionada mediante la consulta *Type=ServiceDeskLog_CL*.</span><span class="sxs-lookup"><span data-stu-id="a8867-375">**Log Search** page: view the errors/related information directly using the query *Type=ServiceDeskLog_CL*.</span></span>

## <a name="troubleshoot-service-manager-web-app-deployment"></a><span data-ttu-id="a8867-376">Solucionar problemas de implementación de aplicaciones web de Service Manager</span><span class="sxs-lookup"><span data-stu-id="a8867-376">Troubleshoot Service Manager Web App deployment</span></span>
1.  <span data-ttu-id="a8867-377">En caso de que se produzcan problemas con la implementación de la aplicación web, asegúrese de tener los permisos suficientes en la suscripción mencionada para crear o implementar recursos.</span><span class="sxs-lookup"><span data-stu-id="a8867-377">In case of any issues with web app deployment, ensure you have sufficient permissions in the subscription mentioned to create/deploy resources.</span></span>
2.  <span data-ttu-id="a8867-378">Si aparece el mensaje de error **Referencia a objeto no establecida como instancia de un objeto"** al ejecutar el [script](log-analytics-itsmc-service-manager-script.md), asegúrese de que especificó valores válidos en la sección **Configuración de usuario**.</span><span class="sxs-lookup"><span data-stu-id="a8867-378">If you get an **"Object reference not set to instance of an object"** error when you run the [script](log-analytics-itsmc-service-manager-script.md), ensure that you entered valid values  under **User Configuration** section.</span></span>
3.  <span data-ttu-id="a8867-379">Si no puede crear el espacio de nombres de retransmisión de Service Bus, asegúrese de que el proveedor de recursos necesario está registrado en la suscripción.</span><span class="sxs-lookup"><span data-stu-id="a8867-379">If you fail to create service bus relay namespace, ensure that the required resource provider is registered in the subscription.</span></span> <span data-ttu-id="a8867-380">Si no está registrado, cree el espacio de nombres de Bus Relay manualmente desde Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="a8867-380">If not registered, manually create service bus relay namespace from the Azure portal.</span></span> <span data-ttu-id="a8867-381">También puede crearlo mientras [crea la conexión híbrida](log-analytics-itsmc-connections.md#configure-the-hybrid-connection) desde Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="a8867-381">You can also create it while [creating the hybrid connection](log-analytics-itsmc-connections.md#configure-the-hybrid-connection) from the Azure portal.</span></span>


## <a name="contact-us"></a><span data-ttu-id="a8867-382">Ponerse en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="a8867-382">Contact us</span></span>

<span data-ttu-id="a8867-383">Si tiene consultas o comentarios sobre IT Service Management, póngase en contacto con nosotros en [omsitsmfeedback@microsoft.com](mailto:omsitsmfeedback@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8867-383">For any queries or feedback on the IT Service Management Connector, contact us at [omsitsmfeedback@microsoft.com](mailto:omsitsmfeedback@microsoft.com).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a8867-384">pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="a8867-384">Next steps</span></span>
<span data-ttu-id="a8867-385">[Incorporación de productos o servicios de ITSM a IT Service Management Connector](log-analytics-itsmc-connections.md).</span><span class="sxs-lookup"><span data-stu-id="a8867-385">[Add ITSM products/services to IT Service Management Connector](log-analytics-itsmc-connections.md).</span></span>
