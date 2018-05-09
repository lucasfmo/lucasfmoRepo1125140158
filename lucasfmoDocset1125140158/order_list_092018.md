---
title: 'Analizzare i dati sui ritardi dei voli con Hadoop in HDInsight: Azure | Microsoft Docs'
description: 'Informazioni su come usare uno script di Windows PowerShell per creare di un cluster HDInsight, eseguire un processo Hive, eseguire un processo Sqoop ed eliminare il cluster.'
services: hdinsight
documentationcenter: ''
author: mumian
manager: jhubbard
editor: cgronlun
ms.assetid: 00e26aa9-82fb-4dbe-b87d-ffe8e39a5412
ms.service: hdinsight
ms.devlang: na
ms.topic: conceptual
ms.date: 05/25/2017
ms.author: jgao
ROBOTS: NOINDEX
ms.openlocfilehash: eec5d0eb3c9cb0ae6e3e7f4eadfc58c4ab039cfd
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="analyze-flight-delay-data-by-using-hive-in-hdinsight"></a><span data-ttu-id="15310-103">Analizzare i dati sui ritardi dei voli con Hive in HDInsight</span><span class="sxs-lookup"><span data-stu-id="15310-103">Analizzare i dati sui ritardi dei voli con Hive in HDInsight</span></span>
<span data-ttu-id="15310-104">Hive fornisce un metodo per l'esecuzione di processi MapReduce mediante un linguaggio di scripting simile a SQL, denominato *[HiveQL][hadoop-hiveql]*, che può essere applicato per attività di riepilogo, query e analisi di volumi di dati molto elevati.</span><span class="sxs-lookup"><span data-stu-id="15310-104">Hive fornisce un metodo per l'esecuzione di processi MapReduce mediante un linguaggio di scripting simile a SQL, denominato *[HiveQL][hadoop-hiveql]*, che può essere applicato per attività di riepilogo, query e analisi di volumi di dati molto elevati.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15310-105">I passaggi descritti in questo documento richiedono un cluster HDInsight basato su Windows.</span><span class="sxs-lookup"><span data-stu-id="15310-105">I passaggi descritti in questo documento richiedono un cluster HDInsight basato su Windows.</span></span> <span data-ttu-id="15310-106">Linux è l'unico sistema operativo usato in HDInsight versione 3.4 o successiva.</span><span class="sxs-lookup"><span data-stu-id="15310-106">Linux è l'unico sistema operativo usato in HDInsight versione 3.4 o successiva.</span></span> <span data-ttu-id="15310-107">Per altre informazioni, vedere la sezione relativa al [ritiro di HDInsight in Windows](hdinsight-component-versioning.md#hdinsight-windows-retirement).</span><span class="sxs-lookup"><span data-stu-id="15310-107">Per altre informazioni, vedere la sezione relativa al [ritiro di HDInsight in Windows](hdinsight-component-versioning.md#hdinsight-windows-retirement).</span></span> <span data-ttu-id="15310-108">Per i passaggi relativi a un cluster basato su Linux, vedere [Analizzare i dati sui ritardi dei voli con Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md).</span><span class="sxs-lookup"><span data-stu-id="15310-108">Per i passaggi relativi a un cluster basato su Linux, vedere [Analizzare i dati sui ritardi dei voli con Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md).</span></span>

<span data-ttu-id="15310-109">Uno dei principali vantaggi di Azure HDInsight è la separazione tra archiviazione e calcolo dei dati.</span><span class="sxs-lookup"><span data-stu-id="15310-109">Uno dei principali vantaggi di Azure HDInsight è la separazione tra archiviazione e calcolo dei dati.</span></span> <span data-ttu-id="15310-110">HDInsight usa l'archiviazione BLOB di Azure per l'archiviazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="15310-110">HDInsight usa l'archiviazione BLOB di Azure per l'archiviazione dei dati.</span></span> <span data-ttu-id="15310-111">Un tipico processo è costituito da tre parti:</span><span class="sxs-lookup"><span data-stu-id="15310-111">Un tipico processo è costituito da tre parti:</span></span>

1. <span data-ttu-id="15310-112">**Archiviare dati nell'archivio BLOB di Azure:**  Ad esempio, i dati meteo, i dati dei sensori, i blog e, in questo caso, i dati sui ritardi dei voli vengono salvati nell'archivio BLOB.</span><span class="sxs-lookup"><span data-stu-id="15310-112">**Archiviare dati nell'archivio BLOB di Azure:**  Ad esempio, i dati meteo, i dati dei sensori, i blog e, in questo caso, i dati sui ritardi dei voli vengono salvati nell'archivio BLOB.</span></span>
2. <span data-ttu-id="15310-113">**Eseguire i processi.**</span><span class="sxs-lookup"><span data-stu-id="15310-113">**Eseguire i processi.**</span></span> <span data-ttu-id="15310-114">Quando giunge il momento di elaborare i dati, viene eseguito uno script di Windows PowerShell (o un'applicazione client) per creare un cluster HDInsight, eseguire i processi ed eliminare il cluster.</span><span class="sxs-lookup"><span data-stu-id="15310-114">Quando giunge il momento di elaborare i dati, viene eseguito uno script di Windows PowerShell (o un'applicazione client) per creare un cluster HDInsight, eseguire i processi ed eliminare il cluster.</span></span> <span data-ttu-id="15310-115">I dati di output dei processi vengono salvati nell'archivio BLOB di Azure e vengono mantenuti anche in seguito all'eliminazione del cluster.</span><span class="sxs-lookup"><span data-stu-id="15310-115">I dati di output dei processi vengono salvati nell'archivio BLOB di Azure e vengono mantenuti anche in seguito all'eliminazione del cluster.</span></span> <span data-ttu-id="15310-116">In questo modo, l'utente paga solo in base al consumo effettivo.</span><span class="sxs-lookup"><span data-stu-id="15310-116">In questo modo, l'utente paga solo in base al consumo effettivo.</span></span>
3. <span data-ttu-id="15310-117">**Recuperare l'output dall'archivio BLOB di Azure**oppure, in questo caso, esportare i dati in un database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-117">**Recuperare l'output dall'archivio BLOB di Azure**oppure, in questo caso, esportare i dati in un database SQL di Azure.</span></span>

<span data-ttu-id="15310-118">Nel diagramma seguente vengono illustrati lo scenario e la struttura di questo articolo:</span><span class="sxs-lookup"><span data-stu-id="15310-118">Nel diagramma seguente vengono illustrati lo scenario e la struttura di questo articolo:</span></span>

![HDI.FlightDelays.flow][img-hdi-flightdelays-flow]

<span data-ttu-id="15310-120">Si noti che i numeri nel diagramma corrispondono ai titoli delle sezioni.</span><span class="sxs-lookup"><span data-stu-id="15310-120">Si noti che i numeri nel diagramma corrispondono ai titoli delle sezioni.</span></span> <span data-ttu-id="15310-121">**M** sta per processo principale.</span><span class="sxs-lookup"><span data-stu-id="15310-121">**M** sta per processo principale.</span></span> <span data-ttu-id="15310-122">**A** sta per contenuto nell'appendice.</span><span class="sxs-lookup"><span data-stu-id="15310-122">**A** sta per contenuto nell'appendice.</span></span>

<span data-ttu-id="15310-123">La parte principale dell'esercitazione mostra come usare uno script di Windows PowerShell per eseguire le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="15310-123">La parte principale dell'esercitazione mostra come usare uno script di Windows PowerShell per eseguire le attività seguenti:</span></span>

* <span data-ttu-id="15310-124">Creare un cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="15310-124">Creare un cluster HDInsight</span></span>
* <span data-ttu-id="15310-125">Eseguire un processo Hive sul cluster per calcolare la media dei ritardi negli aeroporti.</span><span class="sxs-lookup"><span data-stu-id="15310-125">Eseguire un processo Hive sul cluster per calcolare la media dei ritardi negli aeroporti.</span></span> <span data-ttu-id="15310-126">I dati relativi ai ritardi dei voli sono archiviati in un account di archiviazione BLOB di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-126">I dati relativi ai ritardi dei voli sono archiviati in un account di archiviazione BLOB di Azure.</span></span>
* <span data-ttu-id="15310-127">Eseguire un processo Sqoop per esportare l'output del processo Hive in un database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-127">Eseguire un processo Sqoop per esportare l'output del processo Hive in un database SQL di Azure.</span></span>
* <span data-ttu-id="15310-128">Eliminare il cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="15310-128">Eliminare il cluster HDInsight.</span></span>

<span data-ttu-id="15310-129">Nelle appendici sono disponibili istruzioni per caricare i dati relativi ai ritardi dei voli, creare/caricare la stringa di query Hive e preparare il database SQL di Azure per il processo Sqoop.</span><span class="sxs-lookup"><span data-stu-id="15310-129">Nelle appendici sono disponibili istruzioni per caricare i dati relativi ai ritardi dei voli, creare/caricare la stringa di query Hive e preparare il database SQL di Azure per il processo Sqoop.</span></span>

> [!NOTE]
> <span data-ttu-id="15310-130">I passaggi descritti in questo documento sono specifici per i cluster HDInsight basati su Windows.</span><span class="sxs-lookup"><span data-stu-id="15310-130">I passaggi descritti in questo documento sono specifici per i cluster HDInsight basati su Windows.</span></span> <span data-ttu-id="15310-131">Per i passaggi relativi a un cluster basato su Linux, vedere [Analizzare i dati sui ritardi dei voli con Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md)</span><span class="sxs-lookup"><span data-stu-id="15310-131">Per i passaggi relativi a un cluster basato su Linux, vedere [Analizzare i dati sui ritardi dei voli con Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md)</span></span>

### <a name="prerequisites"></a><span data-ttu-id="15310-132">prerequisiti</span><span class="sxs-lookup"><span data-stu-id="15310-132">prerequisiti</span></span>
<span data-ttu-id="15310-133">Prima di iniziare questa esercitazione sono necessari gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="15310-133">Prima di iniziare questa esercitazione sono necessari gli elementi seguenti:</span></span>

* <span data-ttu-id="15310-134">**Una sottoscrizione di Azure**.</span><span class="sxs-lookup"><span data-stu-id="15310-134">**Una sottoscrizione di Azure**.</span></span> <span data-ttu-id="15310-135">Vedere [Ottenere una versione di prova gratuita di Azure](https://azure.microsoft.com/documentation/videos/get-azure-free-trial-for-testing-hadoop-in-hdinsight/).</span><span class="sxs-lookup"><span data-stu-id="15310-135">Vedere [Ottenere una versione di prova gratuita di Azure](https://azure.microsoft.com/documentation/videos/get-azure-free-trial-for-testing-hadoop-in-hdinsight/).</span></span>
* <span data-ttu-id="15310-136">**Workstation con Azure PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="15310-136">**Workstation con Azure PowerShell**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="15310-137">Il supporto di Azure PowerShell per la gestione delle risorse HDInsight tramite Azure Service Manager è **deprecato** ed è stato rimosso dal 1° gennaio 2017.</span><span class="sxs-lookup"><span data-stu-id="15310-137">Il supporto di Azure PowerShell per la gestione delle risorse HDInsight tramite Azure Service Manager è **deprecato** ed è stato rimosso dal 1° gennaio 2017.</span></span> <span data-ttu-id="15310-138">La procedura descritta in questo documento usa i nuovi cmdlet HDInsight, compatibili con Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="15310-138">La procedura descritta in questo documento usa i nuovi cmdlet HDInsight, compatibili con Azure Resource Manager.</span></span>
    >
    > <span data-ttu-id="15310-139">Per installare la versione più recente, seguire la procedura descritta in [Come installare e configurare Azure PowerShell](/powershell/azureps-cmdlets-docs) .</span><span class="sxs-lookup"><span data-stu-id="15310-139">Per installare la versione più recente, seguire la procedura descritta in [Come installare e configurare Azure PowerShell](/powershell/azureps-cmdlets-docs) .</span></span> <span data-ttu-id="15310-140">Se sono presenti script che devono essere modificati per l'uso dei nuovi cmdlet compatibili con Azure Resource Manager, per altre informazioni vedere [Migrazione a strumenti di sviluppo basati su Azure Resource Manager per i cluster HDInsight](hdinsight-hadoop-development-using-azure-resource-manager.md) .</span><span class="sxs-lookup"><span data-stu-id="15310-140">Se sono presenti script che devono essere modificati per l'uso dei nuovi cmdlet compatibili con Azure Resource Manager, per altre informazioni vedere [Migrazione a strumenti di sviluppo basati su Azure Resource Manager per i cluster HDInsight](hdinsight-hadoop-development-using-azure-resource-manager.md) .</span></span>

<span data-ttu-id="15310-141">**File usati in questa esercitazione**</span><span class="sxs-lookup"><span data-stu-id="15310-141">**File usati in questa esercitazione**</span></span>

<span data-ttu-id="15310-142">Questa esercitazione usa dati relativi alle prestazioni rispetto agli orari previsti dei voli delle compagnie aeree, che possono essere scaricati dalla pagina relativa a [Research and Innovative Technology Administration, Bureau of Transportation Statistics (RITA)][rita-website].</span><span class="sxs-lookup"><span data-stu-id="15310-142">Questa esercitazione usa dati relativi alle prestazioni rispetto agli orari previsti dei voli delle compagnie aeree, che possono essere scaricati dalla pagina relativa a [Research and Innovative Technology Administration, Bureau of Transportation Statistics (RITA)][rita-website].</span></span>
<span data-ttu-id="15310-143">Una copia dei dati è stata caricata in un contenitore di archiviazione BLOB di Azure con autorizzazione di accesso al BLOB pubblico.</span><span class="sxs-lookup"><span data-stu-id="15310-143">Una copia dei dati è stata caricata in un contenitore di archiviazione BLOB di Azure con autorizzazione di accesso al BLOB pubblico.</span></span>
<span data-ttu-id="15310-144">Una parte dello script PowerShell copia i dati dal contenitore BLOB pubblico al contenitore BLOB predefinito del cluster.</span><span class="sxs-lookup"><span data-stu-id="15310-144">Una parte dello script PowerShell copia i dati dal contenitore BLOB pubblico al contenitore BLOB predefinito del cluster.</span></span> <span data-ttu-id="15310-145">Anche lo script HiveQL viene copiato nello stesso contenitore BLOB.</span><span class="sxs-lookup"><span data-stu-id="15310-145">Anche lo script HiveQL viene copiato nello stesso contenitore BLOB.</span></span>
<span data-ttu-id="15310-146">Per informazioni su come ottenere/caricare i dati nel proprio account di archiviazione e su come creare/caricare il file di script HiveQL, vedere [Appendice A](#appendix-a) e [Appendice B](#appendix-b).</span><span class="sxs-lookup"><span data-stu-id="15310-146">Per informazioni su come ottenere/caricare i dati nel proprio account di archiviazione e su come creare/caricare il file di script HiveQL, vedere [Appendice A](#appendix-a) e [Appendice B](#appendix-b).</span></span>

<span data-ttu-id="15310-147">Nella tabella seguente vengono elencati i file usati nell'esercitazione:</span><span class="sxs-lookup"><span data-stu-id="15310-147">Nella tabella seguente vengono elencati i file usati nell'esercitazione:</span></span>

<table border="1">
<tr><th><span data-ttu-id="15310-148">File</span><span class="sxs-lookup"><span data-stu-id="15310-148">File</span></span></th><th><span data-ttu-id="15310-149">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="15310-149">DESCRIZIONE</span></span></th></tr>
<tr><td>wasb://flightdelay@hditutorialdata.blob.core.windows.net/flightdelays.hql</td><td><span data-ttu-id="15310-150">File script HiveQL necessario per il processo Hive.</span><span class="sxs-lookup"><span data-stu-id="15310-150">File script HiveQL necessario per il processo Hive.</span></span> <span data-ttu-id="15310-151">Lo script è stato caricato in un contenitore di archiviazione BLOB di Azure con autorizzazione di accesso pubblico.</span><span class="sxs-lookup"><span data-stu-id="15310-151">Lo script è stato caricato in un contenitore di archiviazione BLOB di Azure con autorizzazione di accesso pubblico.</span></span> <span data-ttu-id="15310-152">L'<a href="#appendix-b">Appendice B</a> include istruzioni su come preparare e caricare il file nel proprio account di archiviazione BLOB di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-152">L'<a href="#appendix-b">Appendice B</a> include istruzioni su come preparare e caricare il file nel proprio account di archiviazione BLOB di Azure.</span></span></td></tr>
<tr><td>wasb://flightdelay@hditutorialdata.blob.core.windows.net/2013Data</td><td><span data-ttu-id="15310-153">Dati di input per il processo Hive.</span><span class="sxs-lookup"><span data-stu-id="15310-153">Dati di input per il processo Hive.</span></span> <span data-ttu-id="15310-154">I dati sono stati caricati in un account di archiviazione BLOB di Azure con autorizzazione di accesso pubblico.</span><span class="sxs-lookup"><span data-stu-id="15310-154">I dati sono stati caricati in un account di archiviazione BLOB di Azure con autorizzazione di accesso pubblico.</span></span> <span data-ttu-id="15310-155">L'<a href="#appendix-a">Appendice A</a> include istruzioni su come ottenere i dati e caricarli nel proprio account di archiviazione BLOB di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-155">L'<a href="#appendix-a">Appendice A</a> include istruzioni su come ottenere i dati e caricarli nel proprio account di archiviazione BLOB di Azure.</span></span></td></tr>
<tr><td><span data-ttu-id="15310-156">\tutorials\flightdelays\output</span><span class="sxs-lookup"><span data-stu-id="15310-156">\tutorials\flightdelays\output</span></span></td><td><span data-ttu-id="15310-157">Percorso di output per il processo Hive.</span><span class="sxs-lookup"><span data-stu-id="15310-157">Percorso di output per il processo Hive.</span></span> <span data-ttu-id="15310-158">Il contenitore predefinito viene usato per archiviare i dati di output.</span><span class="sxs-lookup"><span data-stu-id="15310-158">Il contenitore predefinito viene usato per archiviare i dati di output.</span></span></td></tr>
<tr><td><span data-ttu-id="15310-159">\tutorials\flightdelays\jobstatus</span><span class="sxs-lookup"><span data-stu-id="15310-159">\tutorials\flightdelays\jobstatus</span></span></td><td><span data-ttu-id="15310-160">Cartella di stato del processo Hive nel contenitore predefinito.</span><span class="sxs-lookup"><span data-stu-id="15310-160">Cartella di stato del processo Hive nel contenitore predefinito.</span></span></td></tr>
</table>

## <a name="create-cluster-and-run-hivesqoop-jobs"></a><span data-ttu-id="15310-161">Creare cluster ed eseguire processi Hive/Sqoop</span><span class="sxs-lookup"><span data-stu-id="15310-161">Creare cluster ed eseguire processi Hive/Sqoop</span></span>
<span data-ttu-id="15310-162">Per Hadoop MapReduce è prevista l'elaborazione batch.</span><span class="sxs-lookup"><span data-stu-id="15310-162">Per Hadoop MapReduce è prevista l'elaborazione batch.</span></span> <span data-ttu-id="15310-163">Il modo più economico di eseguire un processo Hive consiste nel creare un cluster per il processo ed eliminare il processo dopo il completamento.</span><span class="sxs-lookup"><span data-stu-id="15310-163">Il modo più economico di eseguire un processo Hive consiste nel creare un cluster per il processo ed eliminare il processo dopo il completamento.</span></span> <span data-ttu-id="15310-164">Lo script seguente descrive l'intero processo.</span><span class="sxs-lookup"><span data-stu-id="15310-164">Lo script seguente descrive l'intero processo.</span></span>
<span data-ttu-id="15310-165">Per altre informazioni sulla creazione di un cluster HDInsight e sull'esecuzione di processi Hive, vedere [Creare cluster Hadoop in HDInsight][hdinsight-provision] e [Usare Hive con HDInsight][hdinsight-use-hive].</span><span class="sxs-lookup"><span data-stu-id="15310-165">Per altre informazioni sulla creazione di un cluster HDInsight e sull'esecuzione di processi Hive, vedere [Creare cluster Hadoop in HDInsight][hdinsight-provision] e [Usare Hive con HDInsight][hdinsight-use-hive].</span></span>

<span data-ttu-id="15310-166">**Per eseguire le query Hive con Azure PowerShell**</span><span class="sxs-lookup"><span data-stu-id="15310-166">**Per eseguire le query Hive con Azure PowerShell**</span></span>

1. <span data-ttu-id="15310-167">Creare un database SQL di Azure e la tabella per l'output del processo Sqoop usando le istruzioni nell' [Appendice C](#appendix-c).</span><span class="sxs-lookup"><span data-stu-id="15310-167">Creare un database SQL di Azure e la tabella per l'output del processo Sqoop usando le istruzioni nell' [Appendice C](#appendix-c).</span></span>
2. <span data-ttu-id="15310-168">Aprire Windows PowerShell ISE ed eseguire lo script seguente:</span><span class="sxs-lookup"><span data-stu-id="15310-168">Aprire Windows PowerShell ISE ed eseguire lo script seguente:</span></span>

    ```powershell
    $subscriptionID = "<Azure Subscription ID>"
    $nameToken = "<Enter an Alias>"

    ###########################################
    # You must configure the follwing variables
    # for an existing Azure SQL Database
    ###########################################
    $existingSqlDatabaseServerName = "<Azure SQL Database Server>"
    $existingSqlDatabaseLogin = "<Azure SQL Database Server Login>"
    $existingSqlDatabasePassword = "<Azure SQL Database Server login password>"
    $existingSqlDatabaseName = "<Azure SQL Database name>"

    $localFolder = "E:\Tutorials\Downloads\" # A temp location for copying files.
    $azcopyPath = "C:\Program Files (x86)\Microsoft SDKs\Azure\AzCopy" # depends on the version, the folder can be different

    ###########################################
    # (Optional) configure the following variables
    ###########################################

    $namePrefix = $nameToken.ToLower() + (Get-Date -Format "MMdd")

    $resourceGroupName = $namePrefix + "rg"
    $location = "EAST US 2"

    $HDInsightClusterName = $namePrefix + "hdi"
    $httpUserName = "admin"
    $httpPassword = "<Enter the Password>"

    $defaultStorageAccountName = $namePrefix + "store"
    $defaultBlobContainerName = $HDInsightClusterName # use the cluster name

    $existingSqlDatabaseTableName = "AvgDelays"
    $sqlDatabaseConnectionString = "jdbc:sqlserver://$existingSqlDatabaseServerName.database.windows.net;user=$existingSqlDatabaseLogin@$existingSqlDatabaseServerName;password=$existingSqlDatabaseLogin;database=$existingSqlDatabaseName"

    $hqlScriptFile = "/tutorials/flightdelays/flightdelays.hql"

    $jobStatusFolder = "/tutorials/flightdelays/jobstatus"

    ###########################################
    # Login
    ###########################################
    try{
        $acct = Get-AzureRmSubscription
    }
    catch{
        Connect-AzureRmAccount
    }
    Select-AzureRmSubscription -SubscriptionID $subscriptionID

    ###########################################
    # Create a new HDInsight cluster
    ###########################################

    # Create ARM group
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $location

    # Create the default storage account
    New-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $defaultStorageAccountName -Location $location -Type Standard_LRS

    # Create the default Blob container
    $defaultStorageAccountKey = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $defaultStorageAccountName)[0].Value
    $defaultStorageAccountContext = New-AzureStorageContext -StorageAccountName $defaultStorageAccountName -StorageAccountKey $defaultStorageAccountKey
    New-AzureStorageContainer -Name $defaultBlobContainerName -Context $defaultStorageAccountContext

    # Create the HDInsight cluster
    $pw = ConvertTo-SecureString -String $httpPassword -AsPlainText -Force
    $httpCredential = New-Object System.Management.Automation.PSCredential($httpUserName,$pw)

    New-AzureRmHDInsightCluster `
        -ResourceGroupName $resourceGroupName `
        -ClusterName $HDInsightClusterName `
        -Location $location `
        -ClusterType Hadoop `
        -OSType Windows `
        -ClusterSizeInNodes 2 `
        -HttpCredential $httpCredential `
        -DefaultStorageAccountName "$defaultStorageAccountName.blob.core.windows.net" `
        -DefaultStorageAccountKey $defaultStorageAccountKey `
        -DefaultStorageContainer $existingDefaultBlobContainerName

    ###########################################
    # Prepare the HiveQL script and source data
    ###########################################

    # Create the temp location
    New-Item -Path $localFolder -ItemType Directory -Force

    # Download the sample file from Azure Blob storage
    $context = New-AzureStorageContext -StorageAccountName "hditutorialdata" -Anonymous
    $blobs = Get-AzureStorageBlob -Container "flightdelay" -Context $context
    #$blobs | Get-AzureStorageBlobContent -Context $context -Destination $localFolder

    # Upload data to default container

    $azcopycmd = "cmd.exe /C '$azcopyPath\azcopy.exe' /S /Source:'$localFolder' /Dest:'https://$defaultStorageAccountName.blob.core.windows.net/$defaultBlobContainerName/tutorials/flightdelays' /DestKey:$defaultStorageAccountKey"

    Invoke-Expression -Command:$azcopycmd

    ###########################################
    # Submit the Hive job
    ###########################################
    Use-AzureRmHDInsightCluster -ClusterName $HDInsightClusterName -HttpCredential $httpCredential
    $response = Invoke-AzureRmHDInsightHiveJob `
                    -Files $hqlScriptFile `
                    -DefaultContainer $defaultBlobContainerName `
                    -DefaultStorageAccountName $defaultStorageAccountName `
                    -DefaultStorageAccountKey $defaultStorageAccountKey `
                    -StatusFolder $jobStatusFolder

    write-Host $response

    ###########################################
    # Submit the Sqoop job
    ###########################################
    $exportDir = "wasb://$defaultBlobContainerName@$defaultStorageAccountName.blob.core.windows.net/tutorials/flightdelays/output"

    $sqoopDef = New-AzureRmHDInsightSqoopJobDefinition `
                    -Command "export --connect $sqlDatabaseConnectionString --table $sqlDatabaseTableName --export-dir $exportDir --fields-terminated-by \001 "
    $sqoopJob = Start-AzureRmHDInsightJob `
                    -ResourceGroupName $resourceGroupName `
                    -ClusterName $hdinsightClusterName `
                    -HttpCredential $httpCredential `
                    -JobDefinition $sqoopDef #-Debug -Verbose

    Wait-AzureRmHDInsightJob `
        -ResourceGroupName $resourceGroupName `
        -ClusterName $HDInsightClusterName `
        -HttpCredential $httpCredential `
        -WaitTimeoutInSeconds 3600 `
        -Job $sqoopJob.JobId

    Get-AzureRmHDInsightJobOutput `
        -ResourceGroupName $resourceGroupName `
        -ClusterName $hdinsightClusterName `
        -HttpCredential $httpCredential `
        -DefaultContainer $existingDefaultBlobContainerName `
        -DefaultStorageAccountName $defaultStorageAccountName `
        -DefaultStorageAccountKey $defaultStorageAccountKey `
        -JobId $sqoopJob.JobId `
        -DisplayOutputType StandardError

    ###########################################
    # Delete the cluster
    ###########################################
    Remove-AzureRmHDInsightCluster -ResourceGroupName $resourceGroupName -ClusterName $hdinsightClusterName
    ```
3. <span data-ttu-id="15310-169">Connettersi al database SQL e verificare la media dei ritardi dei voli per ogni città nella tabella AvgDelays:</span><span class="sxs-lookup"><span data-stu-id="15310-169">Connettersi al database SQL e verificare la media dei ritardi dei voli per ogni città nella tabella AvgDelays:</span></span>

    ![HDI.FlightDelays.AvgDelays.Dataset][image-hdi-flightdelays-avgdelays-dataset]

- - -

## <a id="appendix-a"></a><span data-ttu-id="15310-171">Appendice A: caricare i dati relativi ai ritardi dei voli nell'archivio BLOB di Azure</span><span class="sxs-lookup"><span data-stu-id="15310-171">Appendice A: caricare i dati relativi ai ritardi dei voli nell'archivio BLOB di Azure</span></span>
<span data-ttu-id="15310-172">Prima di caricare il file di dati e i file script HiveQL, vedere l' [Appendice B](#appendix-b), è richiesta un'attività di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="15310-172">Prima di caricare il file di dati e i file script HiveQL, vedere l' [Appendice B](#appendix-b), è richiesta un'attività di pianificazione.</span></span> <span data-ttu-id="15310-173">L'idea è quella di archiviare i file di dati e il file HiveQL prima di creare un cluster HDInsight e di eseguire il processo Hive.</span><span class="sxs-lookup"><span data-stu-id="15310-173">L'idea è quella di archiviare i file di dati e il file HiveQL prima di creare un cluster HDInsight e di eseguire il processo Hive.</span></span> <span data-ttu-id="15310-174">Sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="15310-174">Sono disponibili due opzioni:</span></span>

* <span data-ttu-id="15310-175">**Usare lo stesso account di archiviazione di Azure che sarà usato come file system predefinito per il cluster HDInsight:** poiché il cluster HDInsight avrà la chiave di accesso dell'account di archiviazione, non è necessario apportare altre modifiche.</span><span class="sxs-lookup"><span data-stu-id="15310-175">**Usare lo stesso account di archiviazione di Azure che sarà usato come file system predefinito per il cluster HDInsight:** poiché il cluster HDInsight avrà la chiave di accesso dell'account di archiviazione, non è necessario apportare altre modifiche.</span></span>
* <span data-ttu-id="15310-176">**Usare un account di archiviazione di Azure diverso dal file system predefinito del cluster HDInsight:** In questo caso è necessario modificare la parte relativa alla creazione dello script di Windows PowerShell disponibile in [Creare un cluster HDInsight ed eseguire processi Hive/Sqoop](#runjob) per includere l'account di archiviazione come account di archiviazione aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="15310-176">**Usare un account di archiviazione di Azure diverso dal file system predefinito del cluster HDInsight:** In questo caso è necessario modificare la parte relativa alla creazione dello script di Windows PowerShell disponibile in [Creare un cluster HDInsight ed eseguire processi Hive/Sqoop](#runjob) per includere l'account di archiviazione come account di archiviazione aggiuntivo.</span></span> <span data-ttu-id="15310-177">Per istruzioni, vedere [Creare cluster Hadoop in HDInsight][hdinsight-provision].</span><span class="sxs-lookup"><span data-stu-id="15310-177">Per istruzioni, vedere [Creare cluster Hadoop in HDInsight][hdinsight-provision].</span></span> <span data-ttu-id="15310-178">Il cluster HDInsight conosce quindi la chiave di accesso per l'account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="15310-178">Il cluster HDInsight conosce quindi la chiave di accesso per l'account di archiviazione.</span></span>

> [!NOTE]
> <span data-ttu-id="15310-179">Il percorso dell'archivio BLOB per il file di dati è hardcoded nel file di script HiveQL.</span><span class="sxs-lookup"><span data-stu-id="15310-179">Il percorso dell'archivio BLOB per il file di dati è hardcoded nel file di script HiveQL.</span></span> <span data-ttu-id="15310-180">È necessario aggiornarlo di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="15310-180">È necessario aggiornarlo di conseguenza.</span></span>

<span data-ttu-id="15310-181">**Per scaricare i dati relativi ai voli**</span><span class="sxs-lookup"><span data-stu-id="15310-181">**Per scaricare i dati relativi ai voli**</span></span>

1. <span data-ttu-id="15310-182">Passare alla pagina [Research and Innovative Technology Administration, Bureau of Transportation Statistics (RITA)][rita-website].</span><span class="sxs-lookup"><span data-stu-id="15310-182">Passare alla pagina [Research and Innovative Technology Administration, Bureau of Transportation Statistics (RITA)][rita-website].</span></span>
2. <span data-ttu-id="15310-183">Selezionare i valori seguenti nella pagina:</span><span class="sxs-lookup"><span data-stu-id="15310-183">Selezionare i valori seguenti nella pagina:</span></span>

    <table border="1">
    <tr><th><span data-ttu-id="15310-184">NOME</span><span class="sxs-lookup"><span data-stu-id="15310-184">NOME</span></span></th><th><span data-ttu-id="15310-185">Valore</span><span class="sxs-lookup"><span data-stu-id="15310-185">Valore</span></span></th></tr>
    <tr><td><span data-ttu-id="15310-186">Filter Year</span><span class="sxs-lookup"><span data-stu-id="15310-186">Filter Year</span></span></td><td><span data-ttu-id="15310-187">2013</span><span class="sxs-lookup"><span data-stu-id="15310-187">2013</span></span> </td></tr>
    <tr><td><span data-ttu-id="15310-188">Filter Period</span><span class="sxs-lookup"><span data-stu-id="15310-188">Filter Period</span></span></td><td><span data-ttu-id="15310-189">January</span><span class="sxs-lookup"><span data-stu-id="15310-189">January</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-190">Fields</span><span class="sxs-lookup"><span data-stu-id="15310-190">Fields</span></span></td><td><span data-ttu-id="15310-191">*Year*, *FlightDate*, *UniqueCarrier*, *Carrier*, *FlightNum*, *OriginAirportID*, *Origin*, *OriginCityName*, *OriginState*, *DestAirportID*, *Dest*, *DestCityName*, *DestState*, *DepDelayMinutes*, *ArrDelay*, *ArrDelayMinutes*, *CarrierDelay*, *WeatherDelay*, *NASDelay*, *SecurityDelay*, *LateAircraftDelay* (deselezionare tutti gli altri campi)</span><span class="sxs-lookup"><span data-stu-id="15310-191">*Year*, *FlightDate*, *UniqueCarrier*, *Carrier*, *FlightNum*, *OriginAirportID*, *Origin*, *OriginCityName*, *OriginState*, *DestAirportID*, *Dest*, *DestCityName*, *DestState*, *DepDelayMinutes*, *ArrDelay*, *ArrDelayMinutes*, *CarrierDelay*, *WeatherDelay*, *NASDelay*, *SecurityDelay*, *LateAircraftDelay* (deselezionare tutti gli altri campi)</span></span></td></tr>
    </table>

3. <span data-ttu-id="15310-192">Fare clic su **Download**.</span><span class="sxs-lookup"><span data-stu-id="15310-192">Fare clic su **Download**.</span></span>
4. <span data-ttu-id="15310-193">Decomprimere il file nella cartella **C:\Tutorials\FlightDelay\2013Data**.</span><span class="sxs-lookup"><span data-stu-id="15310-193">Decomprimere il file nella cartella **C:\Tutorials\FlightDelay\2013Data**.</span></span> <span data-ttu-id="15310-194">Ogni file è in formato CSV e ha dimensioni pari a circa 60 GB.</span><span class="sxs-lookup"><span data-stu-id="15310-194">Ogni file è in formato CSV e ha dimensioni pari a circa 60 GB.</span></span>
5. <span data-ttu-id="15310-195">Rinominare il file, specificando il nome del mese a cui fanno riferimento i dati.</span><span class="sxs-lookup"><span data-stu-id="15310-195">Rinominare il file, specificando il nome del mese a cui fanno riferimento i dati.</span></span> <span data-ttu-id="15310-196">Ad esempio, al file contenente i dati relativi a gennaio verrà assegnato il nome *January.csv*.</span><span class="sxs-lookup"><span data-stu-id="15310-196">Ad esempio, al file contenente i dati relativi a gennaio verrà assegnato il nome *January.csv*.</span></span>
6. <span data-ttu-id="15310-197">Ripetere i passaggi 2 e 5 per scaricare un file per ognuno dei 12 mesi del 2013.</span><span class="sxs-lookup"><span data-stu-id="15310-197">Ripetere i passaggi 2 e 5 per scaricare un file per ognuno dei 12 mesi del 2013.</span></span> <span data-ttu-id="15310-198">Per eseguire l'esercitazione, è necessario avere almeno un file.</span><span class="sxs-lookup"><span data-stu-id="15310-198">Per eseguire l'esercitazione, è necessario avere almeno un file.</span></span>

<span data-ttu-id="15310-199">**Per caricare i dati relativi ai ritardi dei voli nell'archivio BLOB di Azure**</span><span class="sxs-lookup"><span data-stu-id="15310-199">**Per caricare i dati relativi ai ritardi dei voli nell'archivio BLOB di Azure**</span></span>

1. <span data-ttu-id="15310-200">Preparare i parametri:</span><span class="sxs-lookup"><span data-stu-id="15310-200">Preparare i parametri:</span></span>

    <table border="1">
    <tr><th><span data-ttu-id="15310-201">Nome variabile</span><span class="sxs-lookup"><span data-stu-id="15310-201">Nome variabile</span></span></th><th><span data-ttu-id="15310-202">Note</span><span class="sxs-lookup"><span data-stu-id="15310-202">Note</span></span></th></tr>
    <tr><td><span data-ttu-id="15310-203">$storageAccountName</span><span class="sxs-lookup"><span data-stu-id="15310-203">$storageAccountName</span></span></td><td><span data-ttu-id="15310-204">Account di archiviazione di Azure nel quale si desidera caricare i dati.</span><span class="sxs-lookup"><span data-stu-id="15310-204">Account di archiviazione di Azure nel quale si desidera caricare i dati.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-205">$blobContainerName</span><span class="sxs-lookup"><span data-stu-id="15310-205">$blobContainerName</span></span></td><td><span data-ttu-id="15310-206">Contenitore BLOB nel quale si desidera caricare i dati.</span><span class="sxs-lookup"><span data-stu-id="15310-206">Contenitore BLOB nel quale si desidera caricare i dati.</span></span></td></tr>
    </table>
    
2. <span data-ttu-id="15310-207">Aprire Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="15310-207">Aprire Azure PowerShell ISE.</span></span>
3. <span data-ttu-id="15310-208">Incollare lo script seguente nel riquadro di script:</span><span class="sxs-lookup"><span data-stu-id="15310-208">Incollare lo script seguente nel riquadro di script:</span></span>

    ```powershell
    [CmdletBinding()]
    Param(

        [Parameter(Mandatory=$True,
                    HelpMessage="Enter the Azure storage account name for creating a new HDInsight cluster. If the account doesn't exist, the script will create one.")]
        [String]$storageAccountName,

        [Parameter(Mandatory=$True,
                    HelpMessage="Enter the Azure blob container name for creating a new HDInsight cluster. If not specified, the HDInsight cluster name will be used.")]
        [String]$blobContainerName
    )

    #Region - Variables
    $localFolder = "C:\Tutorials\FlightDelay\2013Data"  # The source folder
    $destFolder = "tutorials/flightdelay/2013data"     #The blob name prefix for the files to be uploaded
    #EndRegion

    #Region - Connect to Azure subscription
    Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    try{Get-AzureRmContext}
    catch{Connect-AzureRmAccount}
    #EndRegion

    #Region - Validate user input
    Write-Host "`nValidating the Azure Storage account and the Blob container..." -ForegroundColor Green
    # Validate the Storage account
    if (-not (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}))
    {
        Write-Host "The storage account, $storageAccountName, doesn't exist." -ForegroundColor Red
        exit
    }
    else{
        $resourceGroupName = (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}).ResourceGroupName
    }

    # Validate the container
    $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    if (-not (Get-AzureStorageContainer -Context $storageContext |Where-Object{$_.Name -eq $blobContainerName}))
    {
        Write-Host "The Blob container, $blobContainerName, doesn't exist" -ForegroundColor Red
        Exit
    }
    #EngRegion

    #Region - Copy the file from local workstation to Azure Blob storage
    if (test-path -Path $localFolder)
    {
        foreach ($item in Get-ChildItem -Path $localFolder){
            $fileName = "$localFolder\$item"
            $blobName = "$destFolder/$item"

            Write-Host "Copying $fileName to $blobName" -ForegroundColor Green

            Set-AzureStorageBlobContent -File $fileName -Container $blobContainerName -Blob $blobName -Context $storageContext
        }
    }
    else
    {
        Write-Host "The source folder on the workstation doesn't exist" -ForegroundColor Red
    }

    # List the uploaded files on HDInsight
    Get-AzureStorageBlob -Container $blobContainerName  -Context $storageContext -Prefix $destFolder
    #EndRegion
    ```
4. <span data-ttu-id="15310-209">Premere **F5** per eseguire lo script.</span><span class="sxs-lookup"><span data-stu-id="15310-209">Premere **F5** per eseguire lo script.</span></span>

<span data-ttu-id="15310-210">Se si sceglie un metodo diverso per il caricamento dei file, verificare che il percorso sia tutorials/flightdelay/data.</span><span class="sxs-lookup"><span data-stu-id="15310-210">Se si sceglie un metodo diverso per il caricamento dei file, verificare che il percorso sia tutorials/flightdelay/data.</span></span> <span data-ttu-id="15310-211">Di seguito viene riportata la sintassi per l'accesso ai file:</span><span class="sxs-lookup"><span data-stu-id="15310-211">Di seguito viene riportata la sintassi per l'accesso ai file:</span></span>

    wasb://<ContainerName>@<StorageAccountName>.blob.core.windows.net/tutorials/flightdelay/data

<span data-ttu-id="15310-212">Il percorso tutorials/flightdelay/data è la cartella virtuale creata durante il caricamento dei file.</span><span class="sxs-lookup"><span data-stu-id="15310-212">Il percorso tutorials/flightdelay/data è la cartella virtuale creata durante il caricamento dei file.</span></span> <span data-ttu-id="15310-213">Verificare che siano disponibili 12 file, uno per ogni mese.</span><span class="sxs-lookup"><span data-stu-id="15310-213">Verificare che siano disponibili 12 file, uno per ogni mese.</span></span>

> [!NOTE]
> <span data-ttu-id="15310-214">È necessario aggiornare la query Hive per consentire la lettura dal nuovo percorso.</span><span class="sxs-lookup"><span data-stu-id="15310-214">È necessario aggiornare la query Hive per consentire la lettura dal nuovo percorso.</span></span>
>
> <span data-ttu-id="15310-215">Occorre configurare l'autorizzazione di accesso pubblico al contenitore oppure associare l'account di archiviazione al cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="15310-215">Occorre configurare l'autorizzazione di accesso pubblico al contenitore oppure associare l'account di archiviazione al cluster HDInsight.</span></span> <span data-ttu-id="15310-216">In caso contrario, la stringa di query Hive non potrà accedere ai file di dati.</span><span class="sxs-lookup"><span data-stu-id="15310-216">In caso contrario, la stringa di query Hive non potrà accedere ai file di dati.</span></span>

- - -

## <a id="appendix-b"></a><span data-ttu-id="15310-217">Appendice B: creare e caricare uno script HiveQL</span><span class="sxs-lookup"><span data-stu-id="15310-217">Appendice B: creare e caricare uno script HiveQL</span></span>
<span data-ttu-id="15310-218">Azure PowerShell consente di eseguire più istruzioni HiveQL contemporaneamente o di inserire l'istruzione HiveQL in un file di script.</span><span class="sxs-lookup"><span data-stu-id="15310-218">Azure PowerShell consente di eseguire più istruzioni HiveQL contemporaneamente o di inserire l'istruzione HiveQL in un file di script.</span></span> <span data-ttu-id="15310-219">Questa sezione illustra come creare uno script HiveQL e caricarlo nell'archivio BLOB di Azure con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15310-219">Questa sezione illustra come creare uno script HiveQL e caricarlo nell'archivio BLOB di Azure con PowerShell.</span></span> <span data-ttu-id="15310-220">Hive richiede che gli script HiveQL siano archiviati nell'archivio BLOB di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-220">Hive richiede che gli script HiveQL siano archiviati nell'archivio BLOB di Azure.</span></span>

<span data-ttu-id="15310-221">Il file di script HiveQL eseguirà le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="15310-221">Il file di script HiveQL eseguirà le operazioni seguenti:</span></span>

1. <span data-ttu-id="15310-222">**Eliminazione della tabella delays_raw**, nel caso in cui la tabella esista già.</span><span class="sxs-lookup"><span data-stu-id="15310-222">**Eliminazione della tabella delays_raw**, nel caso in cui la tabella esista già.</span></span>
2. <span data-ttu-id="15310-223">**Creazione della tabella Hive esterna delays_raw**, che fa riferimento al percorso dell'archivio BLOB che include i file relativi ai ritardi dei voli.</span><span class="sxs-lookup"><span data-stu-id="15310-223">**Creazione della tabella Hive esterna delays_raw**, che fa riferimento al percorso dell'archivio BLOB che include i file relativi ai ritardi dei voli.</span></span> <span data-ttu-id="15310-224">La query consente di specificare che i campi sono delimitati da "," e che le righe vengono interrotte da "\n".</span><span class="sxs-lookup"><span data-stu-id="15310-224">La query consente di specificare che i campi sono delimitati da "," e che le righe vengono interrotte da "\n".</span></span> <span data-ttu-id="15310-225">Ciò costituisce un problema quando i valori dei campi contengono virgole, poiché Hive non è in grado di distinguere tra una virgola che delimita i campi e una virgola inclusa in un valore di campo, come ad esempio nel caso dei valori di campo per ORIGIN\_CITY\_NAME e DEST\_CITY\_NAME.</span><span class="sxs-lookup"><span data-stu-id="15310-225">Ciò costituisce un problema quando i valori dei campi contengono virgole, poiché Hive non è in grado di distinguere tra una virgola che delimita i campi e una virgola inclusa in un valore di campo, come ad esempio nel caso dei valori di campo per ORIGIN\_CITY\_NAME e DEST\_CITY\_NAME.</span></span> <span data-ttu-id="15310-226">Per risolvere questo problema, la query crea colonne TEMP in cui inserire i dati suddivisi erroneamente in colonne.</span><span class="sxs-lookup"><span data-stu-id="15310-226">Per risolvere questo problema, la query crea colonne TEMP in cui inserire i dati suddivisi erroneamente in colonne.</span></span>
3. <span data-ttu-id="15310-227">**Eliminazione della tabella delays**, se la tabella esiste già.</span><span class="sxs-lookup"><span data-stu-id="15310-227">**Eliminazione della tabella delays**, se la tabella esiste già.</span></span>
4. <span data-ttu-id="15310-228">**Creazione della tabella delays**.</span><span class="sxs-lookup"><span data-stu-id="15310-228">**Creazione della tabella delays**.</span></span> <span data-ttu-id="15310-229">È consigliabile ripulire i dati prima di procedere con l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="15310-229">È consigliabile ripulire i dati prima di procedere con l'elaborazione.</span></span> <span data-ttu-id="15310-230">La query crea una nuova tabella *delays* dalla tabella delays_raw.</span><span class="sxs-lookup"><span data-stu-id="15310-230">La query crea una nuova tabella *delays* dalla tabella delays_raw.</span></span> <span data-ttu-id="15310-231">Si noti che le colonne TEMP, come indicato in precedenza, non vengono copiate e che la funzione **substring** viene usata per rimuovere le virgolette dai dati.</span><span class="sxs-lookup"><span data-stu-id="15310-231">Si noti che le colonne TEMP, come indicato in precedenza, non vengono copiate e che la funzione **substring** viene usata per rimuovere le virgolette dai dati.</span></span>
5. <span data-ttu-id="15310-232">**Calcolo della media dei ritardi dovuti alle condizioni climatiche e raggruppamento dei risultati in base al nome della città.**</span><span class="sxs-lookup"><span data-stu-id="15310-232">**Calcolo della media dei ritardi dovuti alle condizioni climatiche e raggruppamento dei risultati in base al nome della città.**</span></span> <span data-ttu-id="15310-233">I risultati verranno anche inviati come output all'archivio BLOB.</span><span class="sxs-lookup"><span data-stu-id="15310-233">I risultati verranno anche inviati come output all'archivio BLOB.</span></span> <span data-ttu-id="15310-234">Si noti che la query rimuoverà gli apostrofi dai dati ed escluderà le righe in cui il valore per **weather_delay** è Null.</span><span class="sxs-lookup"><span data-stu-id="15310-234">Si noti che la query rimuoverà gli apostrofi dai dati ed escluderà le righe in cui il valore per **weather_delay** è Null.</span></span> <span data-ttu-id="15310-235">Ciò è necessario perché Sqoop, usato più avanti nell'esercitazione, non è in grado di gestire correttamente tali valori per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="15310-235">Ciò è necessario perché Sqoop, usato più avanti nell'esercitazione, non è in grado di gestire correttamente tali valori per impostazione predefinita.</span></span>

<span data-ttu-id="15310-236">Per un elenco completo di comandi di HiveQL, vedere [Hive Data Definition Language][hadoop-hiveql] (Linguaggio di definizione dei dati Hive).</span><span class="sxs-lookup"><span data-stu-id="15310-236">Per un elenco completo di comandi di HiveQL, vedere [Hive Data Definition Language][hadoop-hiveql] (Linguaggio di definizione dei dati Hive).</span></span> <span data-ttu-id="15310-237">Ogni comando HiveQL deve terminare con un punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="15310-237">Ogni comando HiveQL deve terminare con un punto e virgola.</span></span>

<span data-ttu-id="15310-238">**Per creare un file di script HiveQL**</span><span class="sxs-lookup"><span data-stu-id="15310-238">**Per creare un file di script HiveQL**</span></span>

1. <span data-ttu-id="15310-239">Preparare i parametri:</span><span class="sxs-lookup"><span data-stu-id="15310-239">Preparare i parametri:</span></span>

    <table border="1">
    <tr><th><span data-ttu-id="15310-240">Nome variabile</span><span class="sxs-lookup"><span data-stu-id="15310-240">Nome variabile</span></span></th><th><span data-ttu-id="15310-241">Note</span><span class="sxs-lookup"><span data-stu-id="15310-241">Note</span></span></th></tr>
    <tr><td><span data-ttu-id="15310-242">$storageAccountName</span><span class="sxs-lookup"><span data-stu-id="15310-242">$storageAccountName</span></span></td><td><span data-ttu-id="15310-243">Account di archiviazione di Azure nel quale si desidera caricare lo script HiveQL.</span><span class="sxs-lookup"><span data-stu-id="15310-243">Account di archiviazione di Azure nel quale si desidera caricare lo script HiveQL.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-244">$blobContainerName</span><span class="sxs-lookup"><span data-stu-id="15310-244">$blobContainerName</span></span></td><td><span data-ttu-id="15310-245">Contenitore BLOB nel quale si desidera caricare lo script HiveQL.</span><span class="sxs-lookup"><span data-stu-id="15310-245">Contenitore BLOB nel quale si desidera caricare lo script HiveQL.</span></span></td></tr>
    </table>
    
2. <span data-ttu-id="15310-246">Aprire Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="15310-246">Aprire Azure PowerShell ISE.</span></span>  

3. <span data-ttu-id="15310-247">Copiare e incollare lo script seguente nel riquadro dello script:</span><span class="sxs-lookup"><span data-stu-id="15310-247">Copiare e incollare lo script seguente nel riquadro dello script:</span></span>  

    ```powershell
    [CmdletBinding()]
    Param(

        # Azure Blob storage variables
        [Parameter(Mandatory=$True,
                    HelpMessage="Enter the Azure storage account name for creating a new HDInsight cluster. If the account doesn't exist, the script will create one.")]
        [String]$storageAccountName,

        [Parameter(Mandatory=$True,
                    HelpMessage="Enter the Azure blob container name for creating a new HDInsight cluster. If not specified, the HDInsight cluster name will be used.")]
        [String]$blobContainerName
    )

    #region - Define variables
    # Treat all errors as terminating
    $ErrorActionPreference = "Stop"

    # The HiveQL script file is exported as this file before it's uploaded to Blob storage
    $hqlLocalFileName = "e:\tutorials\flightdelay\flightdelays.hql"

    # The HiveQL script file will be uploaded to Blob storage as this blob name
    $hqlBlobName = "tutorials/flightdelay/flightdelays.hql"

    # These two constants are used by the HiveQL script file
    #$srcDataFolder = "tutorials/flightdelay/data"
    $dstDataFolder = "/tutorials/flightdelay/output"
    #endregion

    #Region - Connect to Azure subscription
    Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    try{Get-AzureRmContext}
    catch{Connect-AzureRmAccount}
    #EndRegion

    #Region - Validate user input
    Write-Host "`nValidating the Azure Storage account and the Blob container..." -ForegroundColor Green
    # Validate the Storage account
    if (-not (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}))
    {
        Write-Host "The storage account, $storageAccountName, doesn't exist." -ForegroundColor Red
        exit
    }
    else{
        $resourceGroupName = (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}).ResourceGroupName
    }

    # Validate the container
    $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    if (-not (Get-AzureStorageContainer -Context $storageContext |Where-Object{$_.Name -eq $blobContainerName}))
    {
        Write-Host "The Blob container, $blobContainerName, doesn't exist" -ForegroundColor Red
        Exit
    }
    #EngRegion

    #region - Validate the file and file path

    # Check if a file with the same file name already exists on the workstation
    Write-Host "`nvalidating the folder structure on the workstation for saving the HQL script file ..."  -ForegroundColor Green
    if (test-path $hqlLocalFileName){

        $isDelete = Read-Host 'The file, ' $hqlLocalFileName ', exists.  Do you want to overwirte it? (Y/N)'

        if ($isDelete.ToLower() -ne "y")
        {
            Exit
        }
    }

    # Create the folder if it doesn't exist
    $folder = split-path $hqlLocalFileName
    if (-not (test-path $folder))
    {
        Write-Host "`nCreating folder, $folder ..." -ForegroundColor Green

        new-item $folder -ItemType directory
    }
    #end region

    #region - Write the Hive script into a local file
    Write-Host "`nWriting the Hive script into a file on your workstation ..." `
                -ForegroundColor Green

    $hqlDropDelaysRaw = "DROP TABLE delays_raw;"

    $hqlCreateDelaysRaw = "CREATE EXTERNAL TABLE delays_raw (" +
            "YEAR string, " +
            "FL_DATE string, " +
            "UNIQUE_CARRIER string, " +
            "CARRIER string, " +
            "FL_NUM string, " +
            "ORIGIN_AIRPORT_ID string, " +
            "ORIGIN string, " +
            "ORIGIN_CITY_NAME string, " +
            "ORIGIN_CITY_NAME_TEMP string, " +
            "ORIGIN_STATE_ABR string, " +
            "DEST_AIRPORT_ID string, " +
            "DEST string, " +
            "DEST_CITY_NAME string, " +
            "DEST_CITY_NAME_TEMP string, " +
            "DEST_STATE_ABR string, " +
            "DEP_DELAY_NEW float, " +
            "ARR_DELAY_NEW float, " +
            "CARRIER_DELAY float, " +
            "WEATHER_DELAY float, " +
            "NAS_DELAY float, " +
            "SECURITY_DELAY float, " +
            "LATE_AIRCRAFT_DELAY float) " +
        "ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' " +
        "LINES TERMINATED BY '\n' " +
        "STORED AS TEXTFILE " +
        "LOCATION 'wasb://flightdelay@hditutorialdata.blob.core.windows.net/2013Data';"

    $hqlDropDelays = "DROP TABLE delays;"

    $hqlCreateDelays = "CREATE TABLE delays AS " +
        "SELECT YEAR AS year, " +
            "FL_DATE AS flight_date, " +
            "substring(UNIQUE_CARRIER, 2, length(UNIQUE_CARRIER) -1) AS unique_carrier, " +
            "substring(CARRIER, 2, length(CARRIER) -1) AS carrier, " +
            "substring(FL_NUM, 2, length(FL_NUM) -1) AS flight_num, " +
            "ORIGIN_AIRPORT_ID AS origin_airport_id, " +
            "substring(ORIGIN, 2, length(ORIGIN) -1) AS origin_airport_code, " +
            "substring(ORIGIN_CITY_NAME, 2) AS origin_city_name, " +
            "substring(ORIGIN_STATE_ABR, 2, length(ORIGIN_STATE_ABR) -1)  AS origin_state_abr, " +
            "DEST_AIRPORT_ID AS dest_airport_id, " +
            "substring(DEST, 2, length(DEST) -1) AS dest_airport_code, " +
            "substring(DEST_CITY_NAME,2) AS dest_city_name, " +
            "substring(DEST_STATE_ABR, 2, length(DEST_STATE_ABR) -1) AS dest_state_abr, " +
            "DEP_DELAY_NEW AS dep_delay_new, " +
            "ARR_DELAY_NEW AS arr_delay_new, " +
            "CARRIER_DELAY AS carrier_delay, " +
            "WEATHER_DELAY AS weather_delay, " +
            "NAS_DELAY AS nas_delay, " +
            "SECURITY_DELAY AS security_delay, " +
            "LATE_AIRCRAFT_DELAY AS late_aircraft_delay " +
        "FROM delays_raw;"

    $hqlInsertLocal = "INSERT OVERWRITE DIRECTORY '$dstDataFolder' " +
        "SELECT regexp_replace(origin_city_name, '''', ''), " +
            "avg(weather_delay) " +
        "FROM delays " +
        "WHERE weather_delay IS NOT NULL " +
        "GROUP BY origin_city_name;"

    $hqlScript = $hqlDropDelaysRaw + $hqlCreateDelaysRaw + $hqlDropDelays + $hqlCreateDelays + $hqlInsertLocal

    $hqlScript | Out-File $hqlLocalFileName -Encoding ascii -Force
    #endregion

    #region - Upload the Hive script to the default Blob container
    Write-Host "`nUploading the Hive script to the default Blob container ..." -ForegroundColor Green

    # Create a storage context object
    $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    $destContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    # Upload the file from local workstation to Blob storage
    Set-AzureStorageBlobContent -File $hqlLocalFileName -Container $blobContainerName -Blob $hqlBlobName -Context $destContext
    #endregion

    Write-host "`nEnd of the PowerShell script" -ForegroundColor Green
    ```

    <span data-ttu-id="15310-248">Ecco le variabili usate nello script:</span><span class="sxs-lookup"><span data-stu-id="15310-248">Ecco le variabili usate nello script:</span></span>

   * <span data-ttu-id="15310-249">**$hqlLocalFileName** : lo script salva il file di script HiveQL in locale prima di caricarlo nell'archivio BLOB.</span><span class="sxs-lookup"><span data-stu-id="15310-249">**$hqlLocalFileName** : lo script salva il file di script HiveQL in locale prima di caricarlo nell'archivio BLOB.</span></span> <span data-ttu-id="15310-250">Questo è il nome file.</span><span class="sxs-lookup"><span data-stu-id="15310-250">Questo è il nome file.</span></span> <span data-ttu-id="15310-251">Il valore predefinito è <u>C:\tutorials\flightdelay\flightdelays.hql</u>.</span><span class="sxs-lookup"><span data-stu-id="15310-251">Il valore predefinito è <u>C:\tutorials\flightdelay\flightdelays.hql</u>.</span></span>
   * <span data-ttu-id="15310-252">**$hqlBlobName** : questo è il nome BLOB del file di script HiveQL usato per l'archivio BLOB di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-252">**$hqlBlobName** : questo è il nome BLOB del file di script HiveQL usato per l'archivio BLOB di Azure.</span></span> <span data-ttu-id="15310-253">Il valore predefinito è tutorials/flightdelay/flightdelays.hql.</span><span class="sxs-lookup"><span data-stu-id="15310-253">Il valore predefinito è tutorials/flightdelay/flightdelays.hql.</span></span> <span data-ttu-id="15310-254">Poiché il file verrà scritto direttamente nell'archiviazione BLOB di Azure, all'inizio del nome BLOB NON è presente il carattere "/".</span><span class="sxs-lookup"><span data-stu-id="15310-254">Poiché il file verrà scritto direttamente nell'archiviazione BLOB di Azure, all'inizio del nome BLOB NON è presente il carattere "/".</span></span> <span data-ttu-id="15310-255">Per accedere al file dall'archivio BLOB di Azure sarà necessario aggiungere "/" all'inizio del nome file.</span><span class="sxs-lookup"><span data-stu-id="15310-255">Per accedere al file dall'archivio BLOB di Azure sarà necessario aggiungere "/" all'inizio del nome file.</span></span>
   * <span data-ttu-id="15310-256">**$srcDataFolder** e **$dstDataFolder** - = "tutorials/flightdelay/data" = "tutorials/flightdelay/output"</span><span class="sxs-lookup"><span data-stu-id="15310-256">**$srcDataFolder** e **$dstDataFolder** - = "tutorials/flightdelay/data" = "tutorials/flightdelay/output"</span></span>

- - -
## <a id="appendix-c"></a><span data-ttu-id="15310-257">Appendice C: preparare il database SQL di Azure per l'output del processo Sqoop</span><span class="sxs-lookup"><span data-stu-id="15310-257">Appendice C: preparare il database SQL di Azure per l'output del processo Sqoop</span></span>
<span data-ttu-id="15310-258">**Per preparare il database SQL (unirlo con lo script Sqoop)**</span><span class="sxs-lookup"><span data-stu-id="15310-258">**Per preparare il database SQL (unirlo con lo script Sqoop)**</span></span>

1. <span data-ttu-id="15310-259">Preparare i parametri:</span><span class="sxs-lookup"><span data-stu-id="15310-259">Preparare i parametri:</span></span>

    <table border="1">
    <tr><th><span data-ttu-id="15310-260">Nome variabile</span><span class="sxs-lookup"><span data-stu-id="15310-260">Nome variabile</span></span></th><th><span data-ttu-id="15310-261">Note</span><span class="sxs-lookup"><span data-stu-id="15310-261">Note</span></span></th></tr>
    <tr><td><span data-ttu-id="15310-262">$sqlDatabaseServerName</span><span class="sxs-lookup"><span data-stu-id="15310-262">$sqlDatabaseServerName</span></span></td><td><span data-ttu-id="15310-263">Nome del server di database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-263">Nome del server di database SQL di Azure.</span></span> <span data-ttu-id="15310-264">Lasciare vuoto per creare un nuovo server.</span><span class="sxs-lookup"><span data-stu-id="15310-264">Lasciare vuoto per creare un nuovo server.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-265">$sqlDatabaseUsername</span><span class="sxs-lookup"><span data-stu-id="15310-265">$sqlDatabaseUsername</span></span></td><td><span data-ttu-id="15310-266">Nome di accesso del server di database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-266">Nome di accesso del server di database SQL di Azure.</span></span> <span data-ttu-id="15310-267">Se $sqlDatabaseServerName è un server esistente, per l'autenticzione con il server vengono usati l'account di accesso e la password di accesso.</span><span class="sxs-lookup"><span data-stu-id="15310-267">Se $sqlDatabaseServerName è un server esistente, per l'autenticzione con il server vengono usati l'account di accesso e la password di accesso.</span></span> <span data-ttu-id="15310-268">In caso contrario, vengono usati per creare un nuovo server.</span><span class="sxs-lookup"><span data-stu-id="15310-268">In caso contrario, vengono usati per creare un nuovo server.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-269">$sqlDatabasePassword</span><span class="sxs-lookup"><span data-stu-id="15310-269">$sqlDatabasePassword</span></span></td><td><span data-ttu-id="15310-270">Password di accesso del server di database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-270">Password di accesso del server di database SQL di Azure.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-271">$sqlDatabaseLocation</span><span class="sxs-lookup"><span data-stu-id="15310-271">$sqlDatabaseLocation</span></span></td><td><span data-ttu-id="15310-272">Questo valore viene usato solo durante la creazione di un nuovo server di database di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-272">Questo valore viene usato solo durante la creazione di un nuovo server di database di Azure.</span></span></td></tr>
    <tr><td><span data-ttu-id="15310-273">$sqlDatabaseName</span><span class="sxs-lookup"><span data-stu-id="15310-273">$sqlDatabaseName</span></span></td><td><span data-ttu-id="15310-274">Database SQL usato per creare la tabella AvgDelays per il processo Sqoop.</span><span class="sxs-lookup"><span data-stu-id="15310-274">Database SQL usato per creare la tabella AvgDelays per il processo Sqoop.</span></span> <span data-ttu-id="15310-275">Lasciando il valore vuoto, verrà creato un database denominato "HDISqoop".</span><span class="sxs-lookup"><span data-stu-id="15310-275">Lasciando il valore vuoto, verrà creato un database denominato "HDISqoop".</span></span> <span data-ttu-id="15310-276">Il nome della tabella per l'output del processo Sqoop è "AvgDelays".</span><span class="sxs-lookup"><span data-stu-id="15310-276">Il nome della tabella per l'output del processo Sqoop è "AvgDelays".</span></span> </td></tr>
    </table>
    
2. <span data-ttu-id="15310-277">Aprire Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="15310-277">Aprire Azure PowerShell ISE.</span></span>

3. <span data-ttu-id="15310-278">Copiare e incollare lo script seguente nel riquadro dello script:</span><span class="sxs-lookup"><span data-stu-id="15310-278">Copiare e incollare lo script seguente nel riquadro dello script:</span></span>  

    ```powershell
    [CmdletBinding()]
    Param(

        # Azure Resource group variables
        [Parameter(Mandatory=$True,
                HelpMessage="Enter the Azure resource group name. It will be created if it doesn't exist.")]
        [String]$resourceGroupName,

        # SQL database server variables
        [Parameter(Mandatory=$True,
                HelpMessage="Enter the Azure SQL Database Server Name. It will be created if it doesn't exist.")]
        [String]$sqlDatabaseServer,

        [Parameter(Mandatory=$True,
                HelpMessage="Enter the Azure SQL Database admin user.")]
        [String]$sqlDatabaseLogin,

        [Parameter(Mandatory=$True,
                HelpMessage="Enter the Azure SQL Database admin user password.")]
        [String]$sqlDatabasePassword,

        [Parameter(Mandatory=$True,
                HelpMessage="Enter the region to create the Database in.")]
        [String]$sqlDatabaseLocation,   #For example, West US.

        # SQL database variables
        [Parameter(Mandatory=$True,
                HelpMessage="Enter the database name. It will be created if it doesn't exist.")]
        [String]$sqlDatabaseName # specify the database name if you have one created. Otherwise use "" to have the script create one for you.
    )

    # Treat all errors as terminating
    $ErrorActionPreference = "Stop"

    #region - Constants and variables

    # IP address REST service used for retrieving external IP address and creating firewall rules
    [String]$ipAddressRestService = "http://bot.whatismyipaddress.com"
    [String]$fireWallRuleName = "FlightDelay"

    # SQL database variables
    [String]$sqlDatabaseMaxSizeGB = 10

    #SQL query string for creating AvgDelays table
    [String]$sqlDatabaseTableName = "AvgDelays"
    [String]$sqlCreateAvgDelaysTable = " CREATE TABLE [dbo].[$sqlDatabaseTableName](
                [origin_city_name] [nvarchar](50) NOT NULL,
                [weather_delay] float,
            CONSTRAINT [PK_$sqlDatabaseTableName] PRIMARY KEY CLUSTERED
            (
                [origin_city_name] ASC
            )
            )"
    #endregion

    #Region - Connect to Azure subscription
    Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    try{Get-AzureRmContext}
    catch{Connect-AzureRmAccount}
    #EndRegion

    #region - Create and validate Azure resouce group
    try{
        Get-AzureRmResourceGroup -Name $resourceGroupName
    }
    catch{
        New-AzureRmResourceGroup -Name $resourceGroupName -Location $sqlDatabaseLocation
    }

    #EndRegion

    #region - Create and validate Azure SQL database server
    try{
        Get-AzureRmSqlServer -ServerName $sqlDatabaseServer -ResourceGroupName $resourceGroupName}
    catch{
        Write-Host "`nCreating SQL Database server ..."  -ForegroundColor Green

        $sqlDatabasePW = ConvertTo-SecureString -String $sqlDatabasePassword -AsPlainText -Force
        $credential = New-Object System.Management.Automation.PSCredential($sqlDatabaseLogin,$sqlDatabasePW)

        $sqlDatabaseServer = (New-AzureRmSqlServer -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -SqlAdministratorCredentials $credential -Location $sqlDatabaseLocation).ServerName
        Write-Host "`tThe new SQL database server name is $sqlDatabaseServer." -ForegroundColor Cyan

        Write-Host "`nCreating firewall rule, $fireWallRuleName ..." -ForegroundColor Green
        $workstationIPAddress = Invoke-RestMethod $ipAddressRestService
        New-AzureRmSqlServerFirewallRule -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -FirewallRuleName "$fireWallRuleName-workstation" -StartIpAddress $workstationIPAddress -EndIpAddress $workstationIPAddress

        #To allow other Azure services to access the server add a firewall rule and set both the StartIpAddress and EndIpAddress to 0.0.0.0. Note that this allows Azure traffic from any Azure subscription to access the server.
        New-AzureRmSqlServerFirewallRule -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -FirewallRuleName "$fireWallRuleName-Azureservices" -StartIpAddress "0.0.0.0" -EndIpAddress "0.0.0.0"
    }

    #endregion

    #region - Create and validate Azure SQL database

    try {
        Get-AzureRmSqlDatabase -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -DatabaseName $sqlDatabaseName
    }
    catch {
        Write-Host "`nCreating SQL Database, $sqlDatabaseName ..."  -ForegroundColor Green
        New-AzureRMSqlDatabase -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -DatabaseName $sqlDatabaseName -Edition "Standard" -RequestedServiceObjectiveName "S1"
    }

    #endregion

    #region -  Execute an SQL command to create the AvgDelays table

    Write-Host "`nCreating SQL Database table ..."  -ForegroundColor Green
    $conn = New-Object System.Data.SqlClient.SqlConnection
    $conn.ConnectionString = "Data Source=$sqlDatabaseServer.database.windows.net;Initial Catalog=$sqlDatabaseName;User ID=$sqlDatabaseLogin;Password=$sqlDatabasePassword;Encrypt=true;Trusted_Connection=false;"
    $conn.open()
    $cmd = New-Object System.Data.SqlClient.SqlCommand
    $cmd.connection = $conn
    $cmd.commandtext = $sqlCreateAvgDelaysTable
    $cmd.executenonquery()

    $conn.close()

    Write-host "`nEnd of the PowerShell script" -ForegroundColor Green
    ```

   > [!NOTE]
   > <span data-ttu-id="15310-279">Lo script usa un servizio REST (Representational State Transfer), http://bot.whatismyipaddress.com, per recuperare l'indirizzo IP esterno.</span><span class="sxs-lookup"><span data-stu-id="15310-279">Lo script usa un servizio REST (Representational State Transfer), http://bot.whatismyipaddress.com, per recuperare l'indirizzo IP esterno.</span></span> <span data-ttu-id="15310-280">L'indirizzo IP viene usato per creare una regola del firewall per il server di database SQL.</span><span class="sxs-lookup"><span data-stu-id="15310-280">L'indirizzo IP viene usato per creare una regola del firewall per il server di database SQL.</span></span>

    <span data-ttu-id="15310-281">Ecco alcune variabili usate nello script:</span><span class="sxs-lookup"><span data-stu-id="15310-281">Ecco alcune variabili usate nello script:</span></span>

   * <span data-ttu-id="15310-282">**$ipAddressRestService**: il valore predefinito è http://bot.whatismyipaddress.com. È un servizio REST per l'indirizzo IP pubblico che consente di ottenere l'indirizzo IP esterno.</span><span class="sxs-lookup"><span data-stu-id="15310-282">**$ipAddressRestService**: il valore predefinito è http://bot.whatismyipaddress.com. È un servizio REST per l'indirizzo IP pubblico che consente di ottenere l'indirizzo IP esterno.</span></span> <span data-ttu-id="15310-283">È anche possibile usare altri servizi.</span><span class="sxs-lookup"><span data-stu-id="15310-283">È anche possibile usare altri servizi.</span></span> <span data-ttu-id="15310-284">L'indirizzo IP esterno recuperato tramite il servizio verrà usato per creare una regola del firewall per il proprio server di database SQL di Azure, in modo che sia possibile accedere al database dalla workstation (usando uno script di Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="15310-284">L'indirizzo IP esterno recuperato tramite il servizio verrà usato per creare una regola del firewall per il proprio server di database SQL di Azure, in modo che sia possibile accedere al database dalla workstation (usando uno script di Windows PowerShell).</span></span>
   * <span data-ttu-id="15310-285">**$fireWallRuleName** : è il nome della regola del firewall del server di database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-285">**$fireWallRuleName** : è il nome della regola del firewall del server di database SQL di Azure.</span></span> <span data-ttu-id="15310-286">Il nome predefinito è <u>FlightDelay</u>.</span><span class="sxs-lookup"><span data-stu-id="15310-286">Il nome predefinito è <u>FlightDelay</u>.</span></span> <span data-ttu-id="15310-287">È anche possibile rinominarla.</span><span class="sxs-lookup"><span data-stu-id="15310-287">È anche possibile rinominarla.</span></span>
   * <span data-ttu-id="15310-288">**$sqlDatabaseMaxSizeGB** : questo valore viene usato solo durante la creazione di un nuovo server di database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-288">**$sqlDatabaseMaxSizeGB** : questo valore viene usato solo durante la creazione di un nuovo server di database SQL di Azure.</span></span> <span data-ttu-id="15310-289">Il valore predefinito è 10GB.</span><span class="sxs-lookup"><span data-stu-id="15310-289">Il valore predefinito è 10GB.</span></span> <span data-ttu-id="15310-290">sufficiente per questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="15310-290">sufficiente per questa esercitazione.</span></span>
   * <span data-ttu-id="15310-291">**$sqlDatabaseName** : questo valore viene usato solo durante la creazione di un nuovo database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-291">**$sqlDatabaseName** : questo valore viene usato solo durante la creazione di un nuovo database SQL di Azure.</span></span> <span data-ttu-id="15310-292">Il valore predefinito è HDISqoop.</span><span class="sxs-lookup"><span data-stu-id="15310-292">Il valore predefinito è HDISqoop.</span></span> <span data-ttu-id="15310-293">Se viene rinominato, sarà necessario aggiornare anche lo script di Windows PowerShell Sqoop.</span><span class="sxs-lookup"><span data-stu-id="15310-293">Se viene rinominato, sarà necessario aggiornare anche lo script di Windows PowerShell Sqoop.</span></span>
4. <span data-ttu-id="15310-294">Premere **F5** per eseguire lo script.</span><span class="sxs-lookup"><span data-stu-id="15310-294">Premere **F5** per eseguire lo script.</span></span>
5. <span data-ttu-id="15310-295">Convalidare l'output dello script.</span><span class="sxs-lookup"><span data-stu-id="15310-295">Convalidare l'output dello script.</span></span> <span data-ttu-id="15310-296">Assicurarsi che lo script sia stato eseguito correttamente.</span><span class="sxs-lookup"><span data-stu-id="15310-296">Assicurarsi che lo script sia stato eseguito correttamente.</span></span>

## <a id="nextsteps"></a> <span data-ttu-id="15310-297">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="15310-297">Passaggi successivi</span></span>
<span data-ttu-id="15310-298">È stato illustrato come caricare file nell'archivio BLOB di Azure, come popolare una tabella Hive con i dati disponibili nell'archivio BLOB di Azure, come eseguire query Hive e come usare Sqoop per esportare i dati da HDFS in un database SQL di Azure.</span><span class="sxs-lookup"><span data-stu-id="15310-298">È stato illustrato come caricare file nell'archivio BLOB di Azure, come popolare una tabella Hive con i dati disponibili nell'archivio BLOB di Azure, come eseguire query Hive e come usare Sqoop per esportare i dati da HDFS in un database SQL di Azure.</span></span> <span data-ttu-id="15310-299">Per altre informazioni, vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="15310-299">Per altre informazioni, vedere gli articoli seguenti:</span></span>

* <span data-ttu-id="15310-300">[Introduzione a HDInsight][hdinsight-get-started]</span><span class="sxs-lookup"><span data-stu-id="15310-300">[Introduzione a HDInsight][hdinsight-get-started]</span></span>
* <span data-ttu-id="15310-301">[Usare Hive con HDInsight][hdinsight-use-hive]</span><span class="sxs-lookup"><span data-stu-id="15310-301">[Usare Hive con HDInsight][hdinsight-use-hive]</span></span>
* <span data-ttu-id="15310-302">[Usare Oozie con HDInsight][hdinsight-use-oozie]</span><span class="sxs-lookup"><span data-stu-id="15310-302">[Usare Oozie con HDInsight][hdinsight-use-oozie]</span></span>
* <span data-ttu-id="15310-303">[Usare Sqoop con Hadoop in HDInsight][hdinsight-use-sqoop]</span><span class="sxs-lookup"><span data-stu-id="15310-303">[Usare Sqoop con Hadoop in HDInsight][hdinsight-use-sqoop]</span></span>
* <span data-ttu-id="15310-304">[Usare Pig con HDInsight][hdinsight-use-pig]</span><span class="sxs-lookup"><span data-stu-id="15310-304">[Usare Pig con HDInsight][hdinsight-use-pig]</span></span>
* <span data-ttu-id="15310-305">[Sviluppare programmi MapReduce Java per HDInsight][hdinsight-develop-mapreduce]</span><span class="sxs-lookup"><span data-stu-id="15310-305">[Sviluppare programmi MapReduce Java per HDInsight][hdinsight-develop-mapreduce]</span></span>

[azure-purchase-options]: http://azure.microsoft.com/pricing/purchase-options/
[azure-member-offers]: http://azure.microsoft.com/pricing/member-offers/
[azure-free-trial]: http://azure.microsoft.com/pricing/free-trial/

[rita-website]: http://www.transtats.bts.gov/DL_SelectFields.asp?Table_ID=236&DB_Short_Name=On-Time
[powershell-install-configure]: /powershell/azureps-cmdlets-docs

[hdinsight-use-oozie]: hdinsight-use-oozie.md
[hdinsight-use-hive]:hadoop/hdinsight-use-hive.md
[hdinsight-provision]: hdinsight-hadoop-provision-linux-clusters.md
[hdinsight-storage]: hdinsight-hadoop-use-blob-storage.md
[hdinsight-upload-data]: hdinsight-upload-data.md
[hdinsight-get-started]:hadoop/apache-hadoop-linux-tutorial-get-started.md
[hdinsight-use-sqoop]:hadoop/hdinsight-use-sqoop.md
[hdinsight-use-pig]:hadoop/hdinsight-use-pig.md
[hdinsight-develop-mapreduce]:hadoop/apache-hadoop-develop-deploy-java-mapreduce-linux.md

[hadoop-hiveql]: https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL
[hadoop-shell-commands]: http://hadoop.apache.org/docs/r0.18.3/hdfs_shell.html

[technetwiki-hive-error]: http://social.technet.microsoft.com/wiki/contents/articles/23047.hdinsight-hive-error-unable-to-rename.aspx

[image-hdi-flightdelays-avgdelays-dataset]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.AvgDelays.DataSet.png
[img-hdi-flightdelays-run-hive-job-output]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.RunHiveJob.Output.png
[img-hdi-flightdelays-flow]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.Flow.png
            
