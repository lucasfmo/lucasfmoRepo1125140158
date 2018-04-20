---
# <a name="title-analyze-flight-delay-data-with-hadoop-in-hdinsight---azure--microsoft-docs"></a><span data-ttu-id="3258d-101">title: Analyze flight delay data with Hadoop in HDInsight - Azure | Microsoft Docs</span><span class="sxs-lookup"><span data-stu-id="3258d-101">title: Analyze flight delay data with Hadoop in HDInsight - Azure | Microsoft Docs</span></span>
# <a name="description-learn-how-to-use-one-windows-powershell-script-to-create-an-hdinsight-cluster-run-a-hive-job-run-a-sqoop-job-and-delete-the-cluster"></a><span data-ttu-id="3258d-102">description: 'Learn how to use one Windows PowerShell script to create an HDInsight cluster, run a Hive job, run a Sqoop job, and delete the cluster.'</span><span class="sxs-lookup"><span data-stu-id="3258d-102">description: 'Learn how to use one Windows PowerShell script to create an HDInsight cluster, run a Hive job, run a Sqoop job, and delete the cluster.'</span></span>
# <a name="services-hdinsight"></a><span data-ttu-id="3258d-103">services: hdinsight</span><span class="sxs-lookup"><span data-stu-id="3258d-103">services: hdinsight</span></span>
# <a name="documentationcenter-"></a><span data-ttu-id="3258d-104">documentationcenter: ''</span><span class="sxs-lookup"><span data-stu-id="3258d-104">documentationcenter: ''</span></span>
# <a name="author-mumian"></a><span data-ttu-id="3258d-105">author: mumian</span><span class="sxs-lookup"><span data-stu-id="3258d-105">author: mumian</span></span>
# <a name="manager-jhubbard"></a><span data-ttu-id="3258d-106">manager: jhubbard</span><span class="sxs-lookup"><span data-stu-id="3258d-106">manager: jhubbard</span></span>
# <a name="editor-cgronlun"></a><span data-ttu-id="3258d-107">editor: cgronlun</span><span class="sxs-lookup"><span data-stu-id="3258d-107">editor: cgronlun</span></span>
# <a name="msassetid-00e26aa9-82fb-4dbe-b87d-ffe8e39a5412"></a><span data-ttu-id="3258d-108">ms.assetid: 00e26aa9-82fb-4dbe-b87d-ffe8e39a5412</span><span class="sxs-lookup"><span data-stu-id="3258d-108">ms.assetid: 00e26aa9-82fb-4dbe-b87d-ffe8e39a5412</span></span>
# <a name="msservice-hdinsight"></a><span data-ttu-id="3258d-109">ms.service: hdinsight</span><span class="sxs-lookup"><span data-stu-id="3258d-109">ms.service: hdinsight</span></span>
# <a name="msdevlang-na"></a><span data-ttu-id="3258d-110">ms.devlang: na</span><span class="sxs-lookup"><span data-stu-id="3258d-110">ms.devlang: na</span></span>
# <a name="mstopic-conceptual"></a><span data-ttu-id="3258d-111">ms.topic: conceptual</span><span class="sxs-lookup"><span data-stu-id="3258d-111">ms.topic: conceptual</span></span>
# <a name="msdate-05252017"></a><span data-ttu-id="3258d-112">ms.date: 05/25/2017</span><span class="sxs-lookup"><span data-stu-id="3258d-112">ms.date: 05/25/2017</span></span>
# <a name="msauthor-jgao"></a><span data-ttu-id="3258d-113">ms.author: jgao</span><span class="sxs-lookup"><span data-stu-id="3258d-113">ms.author: jgao</span></span>
# <a name="robots-noindex"></a><span data-ttu-id="3258d-114">ROBOTS: NOINDEX</span><span class="sxs-lookup"><span data-stu-id="3258d-114">ROBOTS: NOINDEX</span></span>
# <a name="---"></a>---
<a name="analyze-flight-delay-data-by-using-hive-in-hdinsight"></a><span data-ttu-id="3258d-115">Analyze flight delay data by using Hive in HDInsight</span><span class="sxs-lookup"><span data-stu-id="3258d-115">Analyze flight delay data by using Hive in HDInsight</span></span>
# <a name="hive-provides-a-means-of-running-hadoop-mapreduce-jobs-through-an-sql-like-scripting-language-called-hiveqlhadoop-hiveql-which-can-be-applied-towards-summarizing-querying-and-analyzing-large-volumes-of-data"></a><span data-ttu-id="3258d-116">Hive provides a means of running Hadoop MapReduce jobs through an SQL-like scripting language called *[HiveQL][hadoop-hiveql]*, which can be applied towards summarizing, querying, and analyzing large volumes of data.</span><span class="sxs-lookup"><span data-stu-id="3258d-116">Hive provides a means of running Hadoop MapReduce jobs through an SQL-like scripting language called *[HiveQL][hadoop-hiveql]*, which can be applied towards summarizing, querying, and analyzing large volumes of data.</span></span>

# <a name="-important"></a><span data-ttu-id="3258d-117">> [!IMPORTANT]</span><span class="sxs-lookup"><span data-stu-id="3258d-117">> [!IMPORTANT]</span></span>
# <a name="-the-steps-in-this-document-require-a-windows-based-hdinsight-cluster-linux-is-the-only-operating-system-used-on-hdinsight-version-34-or-greater-for-more-information-see-hdinsight-retirement-on-windowshdinsight-component-versioningmdhdinsight-windows-retirement-for-steps-that-work-with-a-linux-based-cluster-see-analyze-flight-delay-data-by-using-hive-in-hdinsight-linuxhdinsight-analyze-flight-delay-data-linuxmd"></a><span data-ttu-id="3258d-118">> The steps in this document require a Windows-based HDInsight cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-118">> The steps in this document require a Windows-based HDInsight cluster.</span></span> <span data-ttu-id="3258d-119">Linux is the only operating system used on HDInsight version 3.4 or greater.</span><span class="sxs-lookup"><span data-stu-id="3258d-119">Linux is the only operating system used on HDInsight version 3.4 or greater.</span></span> <span data-ttu-id="3258d-120">For more information, see [HDInsight retirement on Windows](hdinsight-component-versioning.md#hdinsight-windows-retirement).</span><span class="sxs-lookup"><span data-stu-id="3258d-120">For more information, see [HDInsight retirement on Windows](hdinsight-component-versioning.md#hdinsight-windows-retirement).</span></span> <span data-ttu-id="3258d-121">For steps that work with a Linux-based cluster, see [Analyze flight delay data by using Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md).</span><span class="sxs-lookup"><span data-stu-id="3258d-121">For steps that work with a Linux-based cluster, see [Analyze flight delay data by using Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md).</span></span>

# <a name="one-of-the-major-benefits-of-azure-hdinsight-is-the-separation-of-data-storage-and-compute-hdinsight-uses-azure-blob-storage-for-data-storage-a-typical-job-involves-three-parts"></a><span data-ttu-id="3258d-122">One of the major benefits of Azure HDInsight is the separation of data storage and compute.</span><span class="sxs-lookup"><span data-stu-id="3258d-122">One of the major benefits of Azure HDInsight is the separation of data storage and compute.</span></span> <span data-ttu-id="3258d-123">HDInsight uses Azure Blob storage for data storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-123">HDInsight uses Azure Blob storage for data storage.</span></span> <span data-ttu-id="3258d-124">A typical job involves three parts:</span><span class="sxs-lookup"><span data-stu-id="3258d-124">A typical job involves three parts:</span></span>

# <a name="1-store-data-in-azure-blob-storage--for-example-weather-data-sensor-data-web-logs-and-in-this-case-flight-delay-data-are-saved-into-azure-blob-storage"></a><span data-ttu-id="3258d-125">1. **Store data in Azure Blob storage.**</span><span class="sxs-lookup"><span data-stu-id="3258d-125">1. **Store data in Azure Blob storage.**</span></span>  <span data-ttu-id="3258d-126">For example, weather data, sensor data, web logs, and in this case, flight delay data are saved into Azure Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-126">For example, weather data, sensor data, web logs, and in this case, flight delay data are saved into Azure Blob storage.</span></span>
# <a name="2-run-jobs-when-it-is-time-to-process-the-data-you-run-a-windows-powershell-script-or-a-client-application-to-create-an-hdinsight-cluster-run-jobs-and-delete-the-cluster-the-jobs-save-output-data-to-azure-blob-storage-the-output-data-is-retained-even-after-the-cluster-is-deleted-this-way-you-pay-for-only-what-you-have-consumed"></a><span data-ttu-id="3258d-127">2. **Run jobs.**</span><span class="sxs-lookup"><span data-stu-id="3258d-127">2. **Run jobs.**</span></span> <span data-ttu-id="3258d-128">When it is time to process the data, you run a Windows PowerShell script (or a client application) to create an HDInsight cluster, run jobs, and delete the cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-128">When it is time to process the data, you run a Windows PowerShell script (or a client application) to create an HDInsight cluster, run jobs, and delete the cluster.</span></span> <span data-ttu-id="3258d-129">The jobs save output data to Azure Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-129">The jobs save output data to Azure Blob storage.</span></span> <span data-ttu-id="3258d-130">The output data is retained even after the cluster is deleted.</span><span class="sxs-lookup"><span data-stu-id="3258d-130">The output data is retained even after the cluster is deleted.</span></span> <span data-ttu-id="3258d-131">This way, you pay for only what you have consumed.</span><span class="sxs-lookup"><span data-stu-id="3258d-131">This way, you pay for only what you have consumed.</span></span>
# <a name="3-retrieve-the-output-from-azure-blob-storage-or-in-this-tutorial-export-the-data-to-an-azure-sql-database"></a><span data-ttu-id="3258d-132">3. **Retrieve the output from Azure Blob storage**, or in this tutorial, export the data to an Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="3258d-132">3. **Retrieve the output from Azure Blob storage**, or in this tutorial, export the data to an Azure SQL database.</span></span>

# <a name="the-following-diagram-illustrates-the-scenario-and-the-structure-of-this-tutorial"></a><span data-ttu-id="3258d-133">The following diagram illustrates the scenario and the structure of this tutorial:</span><span class="sxs-lookup"><span data-stu-id="3258d-133">The following diagram illustrates the scenario and the structure of this tutorial:</span></span>

# <a name="hdiflightdelaysflowimg-hdi-flightdelays-flow"></a><span data-ttu-id="3258d-134">![HDI.FlightDelays.flow][img-hdi-flightdelays-flow]</span><span class="sxs-lookup"><span data-stu-id="3258d-134">![HDI.FlightDelays.flow][img-hdi-flightdelays-flow]</span></span>

# <a name="note-that-the-numbers-in-the-diagram-correspond-to-the-section-titles-m-stands-for-the-main-process-a-stands-for-the-content-in-the-appendix"></a><span data-ttu-id="3258d-135">Note that the numbers in the diagram correspond to the section titles.</span><span class="sxs-lookup"><span data-stu-id="3258d-135">Note that the numbers in the diagram correspond to the section titles.</span></span> <span data-ttu-id="3258d-136">**M** stands for the main process.</span><span class="sxs-lookup"><span data-stu-id="3258d-136">**M** stands for the main process.</span></span> <span data-ttu-id="3258d-137">**A** stands for the content in the appendix.</span><span class="sxs-lookup"><span data-stu-id="3258d-137">**A** stands for the content in the appendix.</span></span>

# <a name="the-main-portion-of-the-tutorial-shows-you-how-to-use-one-windows-powershell-script-to-perform-the-following-tasks"></a><span data-ttu-id="3258d-138">The main portion of the tutorial shows you how to use one Windows PowerShell script to perform the following tasks:</span><span class="sxs-lookup"><span data-stu-id="3258d-138">The main portion of the tutorial shows you how to use one Windows PowerShell script to perform the following tasks:</span></span>

# <a name="-create-an-hdinsight-cluster"></a><span data-ttu-id="3258d-139">\* Create an HDInsight cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-139">\* Create an HDInsight cluster.</span></span>
# <a name="-run-a-hive-job-on-the-cluster-to-calculate-average-delays-at-airports-the-flight-delay-data-is-stored-in-an-azure-blob-storage-account"></a><span data-ttu-id="3258d-140">\* Run a Hive job on the cluster to calculate average delays at airports.</span><span class="sxs-lookup"><span data-stu-id="3258d-140">\* Run a Hive job on the cluster to calculate average delays at airports.</span></span> <span data-ttu-id="3258d-141">The flight delay data is stored in an Azure Blob storage account.</span><span class="sxs-lookup"><span data-stu-id="3258d-141">The flight delay data is stored in an Azure Blob storage account.</span></span>
# <a name="-run-a-sqoop-job-to-export-the-hive-job-output-to-an-azure-sql-database"></a><span data-ttu-id="3258d-142">\* Run a Sqoop job to export the Hive job output to an Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="3258d-142">\* Run a Sqoop job to export the Hive job output to an Azure SQL database.</span></span>
# <a name="-delete-the-hdinsight-cluster"></a><span data-ttu-id="3258d-143">\* Delete the HDInsight cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-143">\* Delete the HDInsight cluster.</span></span>

# <a name="in-the-appendixes-you-can-find-the-instructions-for-uploading-flight-delay-data-creatinguploading-a-hive-query-string-and-preparing-the-azure-sql-database-for-the-sqoop-job"></a><span data-ttu-id="3258d-144">In the appendixes, you can find the instructions for uploading flight delay data, creating/uploading a Hive query string, and preparing the Azure SQL database for the Sqoop job.</span><span class="sxs-lookup"><span data-stu-id="3258d-144">In the appendixes, you can find the instructions for uploading flight delay data, creating/uploading a Hive query string, and preparing the Azure SQL database for the Sqoop job.</span></span>

# <a name="-note"></a><span data-ttu-id="3258d-145">> [!NOTE]</span><span class="sxs-lookup"><span data-stu-id="3258d-145">> [!NOTE]</span></span>
# <a name="-the-steps-in-this-document-are-specific-to-windows-based-hdinsight-clusters-for-steps-that-work-with-a-linux-based-cluster-see-analyze-flight-delay-data-using-hive-in-hdinsight-linuxhdinsight-analyze-flight-delay-data-linuxmd"></a><span data-ttu-id="3258d-146">> The steps in this document are specific to Windows-based HDInsight clusters.</span><span class="sxs-lookup"><span data-stu-id="3258d-146">> The steps in this document are specific to Windows-based HDInsight clusters.</span></span> <span data-ttu-id="3258d-147">For steps that work with a Linux-based cluster, see [Analyze flight delay data using Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md)</span><span class="sxs-lookup"><span data-stu-id="3258d-147">For steps that work with a Linux-based cluster, see [Analyze flight delay data using Hive in HDInsight (Linux)](hdinsight-analyze-flight-delay-data-linux.md)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3258d-148">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3258d-148">Prerequisites</span></span>
# <a name="before-you-begin-this-tutorial-you-must-have-the-following-items"></a><span data-ttu-id="3258d-149">Before you begin this tutorial, you must have the following items:</span><span class="sxs-lookup"><span data-stu-id="3258d-149">Before you begin this tutorial, you must have the following items:</span></span>

# <a name="-an-azure-subscription-see-get-azure-free-trialhttpsazuremicrosoftcomdocumentationvideosget-azure-free-trial-for-testing-hadoop-in-hdinsight"></a><span data-ttu-id="3258d-150">\* **An Azure subscription**.</span><span class="sxs-lookup"><span data-stu-id="3258d-150">\* **An Azure subscription**.</span></span> <span data-ttu-id="3258d-151">See [Get Azure free trial](https://azure.microsoft.com/documentation/videos/get-azure-free-trial-for-testing-hadoop-in-hdinsight/).</span><span class="sxs-lookup"><span data-stu-id="3258d-151">See [Get Azure free trial](https://azure.microsoft.com/documentation/videos/get-azure-free-trial-for-testing-hadoop-in-hdinsight/).</span></span>
# <a name="-a-workstation-with-azure-powershell"></a><span data-ttu-id="3258d-152">\* **A workstation with Azure PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3258d-152">\* **A workstation with Azure PowerShell**.</span></span>

    # > [!IMPORTANT]
    # > Azure PowerShell support for managing HDInsight resources using Azure Service Manager is **deprecated**, and was removed on January 1, 2017. The steps in this document use the new HDInsight cmdlets that work with Azure Resource Manager.
    # >
    # > Please follow the steps in [Install and configure Azure PowerShell](/powershell/azureps-cmdlets-docs) to install the latest version of Azure PowerShell. If you have scripts that need to be modified to use the new cmdlets that work with Azure Resource Manager, see [Migrating to Azure Resource Manager-based development tools for HDInsight clusters](hdinsight-hadoop-development-using-azure-resource-manager.md) for more information.

# <a name="files-used-in-this-tutorial"></a><span data-ttu-id="3258d-153">**Files used in this tutorial**</span><span class="sxs-lookup"><span data-stu-id="3258d-153">**Files used in this tutorial**</span></span>

# <a name="this-tutorial-uses-the-on-time-performance-of-airline-flight-data-from-research-and-innovative-technology-administration-bureau-of-transportation-statistics-or-ritarita-website"></a><span data-ttu-id="3258d-154">This tutorial uses the on-time performance of airline flight data from [Research and Innovative Technology Administration, Bureau of Transportation Statistics or RITA][rita-website].</span><span class="sxs-lookup"><span data-stu-id="3258d-154">This tutorial uses the on-time performance of airline flight data from [Research and Innovative Technology Administration, Bureau of Transportation Statistics or RITA][rita-website].</span></span>
# <a name="a-copy-of-the-data-has-been-uploaded-to-an-azure-blob-storage-container-with-the-public-blob-access-permission"></a><span data-ttu-id="3258d-155">A copy of the data has been uploaded to an Azure Blob storage container with the Public Blob access permission.</span><span class="sxs-lookup"><span data-stu-id="3258d-155">A copy of the data has been uploaded to an Azure Blob storage container with the Public Blob access permission.</span></span>
# <a name="a-part-of-your-powershell-script-copies-the-data-from-the-public-blob-container-to-the-default-blob-container-of-your-cluster-the-hiveql-script-is-also-copied-to-the-same-blob-container"></a><span data-ttu-id="3258d-156">A part of your PowerShell script copies the data from the public blob container to the default blob container of your cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-156">A part of your PowerShell script copies the data from the public blob container to the default blob container of your cluster.</span></span> <span data-ttu-id="3258d-157">The HiveQL script is also copied to the same Blob container.</span><span class="sxs-lookup"><span data-stu-id="3258d-157">The HiveQL script is also copied to the same Blob container.</span></span>
# <a name="if-you-want-to-learn-how-to-getupload-the-data-to-your-own-storage-account-and-how-to-createupload-the-hiveql-script-file-see-appendix-aappendix-a-and-appendix-bappendix-b"></a><span data-ttu-id="3258d-158">If you want to learn how to get/upload the data to your own Storage account, and how to create/upload the HiveQL script file, see [Appendix A](#appendix-a) and [Appendix B](#appendix-b).</span><span class="sxs-lookup"><span data-stu-id="3258d-158">If you want to learn how to get/upload the data to your own Storage account, and how to create/upload the HiveQL script file, see [Appendix A](#appendix-a) and [Appendix B](#appendix-b).</span></span>

# <a name="the-following-table-lists-the-files-used-in-this-tutorial"></a><span data-ttu-id="3258d-159">The following table lists the files used in this tutorial:</span><span class="sxs-lookup"><span data-stu-id="3258d-159">The following table lists the files used in this tutorial:</span></span>

# <table border="1">
# <a name="trthfilesththdescriptionthtr"></a><tr><th><span data-ttu-id="3258d-160">Files</span><span class="sxs-lookup"><span data-stu-id="3258d-160">Files</span></span></th><th><span data-ttu-id="3258d-161">Description</span><span class="sxs-lookup"><span data-stu-id="3258d-161">Description</span></span></th></tr>
# <tr><td>wasb://flightdelay@hditutorialdata.blob.core.windows.net/flightdelays.hql</td><td><span data-ttu-id="3258d-162">The HiveQL script file used by the Hive job.</span><span class="sxs-lookup"><span data-stu-id="3258d-162">The HiveQL script file used by the Hive job.</span></span> <span data-ttu-id="3258d-163">This script has been uploaded to an Azure Blob storage account with the public access.</span><span class="sxs-lookup"><span data-stu-id="3258d-163">This script has been uploaded to an Azure Blob storage account with the public access.</span></span> <span data-ttu-id="3258d-164"><a href="#appendix-b">Appendix B</a> has instructions on preparing and uploading this file to your own Azure Blob storage account.</span><span class="sxs-lookup"><span data-stu-id="3258d-164"><a href="#appendix-b">Appendix B</a> has instructions on preparing and uploading this file to your own Azure Blob storage account.</span></span></td></tr>
# <tr><td>wasb://flightdelay@hditutorialdata.blob.core.windows.net/2013Data</td><td><span data-ttu-id="3258d-165">Input data for the Hive job.</span><span class="sxs-lookup"><span data-stu-id="3258d-165">Input data for the Hive job.</span></span> <span data-ttu-id="3258d-166">The data has been uploaded to an Azure Blob storage account with the public access.</span><span class="sxs-lookup"><span data-stu-id="3258d-166">The data has been uploaded to an Azure Blob storage account with the public access.</span></span> <span data-ttu-id="3258d-167"><a href="#appendix-a">Appendix A</a> has instructions on getting the data and uploading the data to your own Azure Blob storage account.</span><span class="sxs-lookup"><span data-stu-id="3258d-167"><a href="#appendix-a">Appendix A</a> has instructions on getting the data and uploading the data to your own Azure Blob storage account.</span></span></td></tr>
# <a name="trtdtutorialsflightdelaysoutputtdtdthe-output-path-for-the-hive-job-the-default-container-is-used-for-storing-the-output-datatdtr"></a><tr><td><span data-ttu-id="3258d-168">\tutorials\flightdelays\output</span><span class="sxs-lookup"><span data-stu-id="3258d-168">\tutorials\flightdelays\output</span></span></td><td><span data-ttu-id="3258d-169">The output path for the Hive job.</span><span class="sxs-lookup"><span data-stu-id="3258d-169">The output path for the Hive job.</span></span> <span data-ttu-id="3258d-170">The default container is used for storing the output data.</span><span class="sxs-lookup"><span data-stu-id="3258d-170">The default container is used for storing the output data.</span></span></td></tr>
# <a name="trtdtutorialsflightdelaysjobstatustdtdthe-hive-job-status-folder-on-the-default-containertdtr"></a><tr><td><span data-ttu-id="3258d-171">\tutorials\flightdelays\jobstatus</span><span class="sxs-lookup"><span data-stu-id="3258d-171">\tutorials\flightdelays\jobstatus</span></span></td><td><span data-ttu-id="3258d-172">The Hive job status folder on the default container.</span><span class="sxs-lookup"><span data-stu-id="3258d-172">The Hive job status folder on the default container.</span></span></td></tr>
# </table>

# <a name="create-cluster-and-run-hivesqoop-jobs"></a><span data-ttu-id="3258d-173">Create cluster and run Hive/Sqoop jobs</span><span class="sxs-lookup"><span data-stu-id="3258d-173">Create cluster and run Hive/Sqoop jobs</span></span>
# <a name="hadoop-mapreduce-is-batch-processing-the-most-cost-effective-way-to-run-a-hive-job-is-to-create-a-cluster-for-the-job-and-delete-the-job-after-the-job-is-completed-the-following-script-covers-the-whole-process"></a><span data-ttu-id="3258d-174">Hadoop MapReduce is batch processing.</span><span class="sxs-lookup"><span data-stu-id="3258d-174">Hadoop MapReduce is batch processing.</span></span> <span data-ttu-id="3258d-175">The most cost-effective way to run a Hive job is to create a cluster for the job, and delete the job after the job is completed.</span><span class="sxs-lookup"><span data-stu-id="3258d-175">The most cost-effective way to run a Hive job is to create a cluster for the job, and delete the job after the job is completed.</span></span> <span data-ttu-id="3258d-176">The following script covers the whole process.</span><span class="sxs-lookup"><span data-stu-id="3258d-176">The following script covers the whole process.</span></span>
# <a name="for-more-information-on-creating-an-hdinsight-cluster-and-running-hive-jobs-see-create-hadoop-clusters-in-hdinsighthdinsight-provision-and-use-hive-with-hdinsighthdinsight-use-hive"></a><span data-ttu-id="3258d-177">For more information on creating an HDInsight cluster and running Hive jobs, see [Create Hadoop clusters in HDInsight][hdinsight-provision] and [Use Hive with HDInsight][hdinsight-use-hive].</span><span class="sxs-lookup"><span data-stu-id="3258d-177">For more information on creating an HDInsight cluster and running Hive jobs, see [Create Hadoop clusters in HDInsight][hdinsight-provision] and [Use Hive with HDInsight][hdinsight-use-hive].</span></span>

# <a name="to-run-the-hive-queries-by-azure-powershell"></a><span data-ttu-id="3258d-178">**To run the Hive queries by Azure PowerShell**</span><span class="sxs-lookup"><span data-stu-id="3258d-178">**To run the Hive queries by Azure PowerShell**</span></span>

# <a name="1-create-an-azure-sql-database-and-the-table-for-the-sqoop-job-output-by-using-the-instructions-in-appendix-cappendix-c"></a><span data-ttu-id="3258d-179">1. Create an Azure SQL database and the table for the Sqoop job output by using the instructions in [Appendix C](#appendix-c).</span><span class="sxs-lookup"><span data-stu-id="3258d-179">1. Create an Azure SQL database and the table for the Sqoop job output by using the instructions in [Appendix C](#appendix-c).</span></span>
# <a name="2-open-windows-powershell-ise-and-run-the-following-script"></a><span data-ttu-id="3258d-180">2. Open Windows PowerShell ISE, and run the following script:</span><span class="sxs-lookup"><span data-stu-id="3258d-180">2. Open Windows PowerShell ISE, and run the following script:</span></span>

    # ```powershell
    # $subscriptionID = "<Azure Subscription ID>"
    # $nameToken = "<Enter an Alias>"

    ##########################################
    You must configure the follwing variables
    for an existing Azure SQL Database
    ##########################################
    # $existingSqlDatabaseServerName = "<Azure SQL Database Server>"
    # $existingSqlDatabaseLogin = "<Azure SQL Database Server Login>"
    # $existingSqlDatabasePassword = "<Azure SQL Database Server login password>"
    # $existingSqlDatabaseName = "<Azure SQL Database name>"

    # $localFolder = "E:\Tutorials\Downloads\" # A temp location for copying files.
    # $azcopyPath = "C:\Program Files (x86)\Microsoft SDKs\Azure\AzCopy" # depends on the version, the folder can be different

    ##########################################
    (Optional) configure the following variables
    ##########################################

    # $namePrefix = $nameToken.ToLower() + (Get-Date -Format "MMdd")

    # $resourceGroupName = $namePrefix + "rg"
    # $location = "EAST US 2"

    # $HDInsightClusterName = $namePrefix + "hdi"
    # $httpUserName = "admin"
    # $httpPassword = "<Enter the Password>"

    # $defaultStorageAccountName = $namePrefix + "store"
    # $defaultBlobContainerName = $HDInsightClusterName # use the cluster name

    # $existingSqlDatabaseTableName = "AvgDelays"
    # $sqlDatabaseConnectionString = "jdbc:sqlserver://$existingSqlDatabaseServerName.database.windows.net;user=$existingSqlDatabaseLogin@$existingSqlDatabaseServerName;password=$existingSqlDatabaseLogin;database=$existingSqlDatabaseName"

    # $hqlScriptFile = "/tutorials/flightdelays/flightdelays.hql"

    # $jobStatusFolder = "/tutorials/flightdelays/jobstatus"

    ##########################################
    Login
    ##########################################
    # try{
        # $acct = Get-AzureRmSubscription
    # }
    # catch{
        # Connect-AzureRmAccount
    # }
    # Select-AzureRmSubscription -SubscriptionID $subscriptionID

    ##########################################
    Create a new HDInsight cluster
    ##########################################

    Create ARM group
    # New-AzureRmResourceGroup -Name $resourceGroupName -Location $location

    Create the default storage account
    # New-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $defaultStorageAccountName -Location $location -Type Standard_LRS

    Create the default Blob container
    # $defaultStorageAccountKey = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $defaultStorageAccountName)[0].Value
    # $defaultStorageAccountContext = New-AzureStorageContext -StorageAccountName $defaultStorageAccountName -StorageAccountKey $defaultStorageAccountKey
    # New-AzureStorageContainer -Name $defaultBlobContainerName -Context $defaultStorageAccountContext

    Create the HDInsight cluster
    # $pw = ConvertTo-SecureString -String $httpPassword -AsPlainText -Force
    # $httpCredential = New-Object System.Management.Automation.PSCredential($httpUserName,$pw)

    # New-AzureRmHDInsightCluster `
        # -ResourceGroupName $resourceGroupName `
        # -ClusterName $HDInsightClusterName `
        # -Location $location `
        # -ClusterType Hadoop `
        # -OSType Windows `
        # -ClusterSizeInNodes 2 `
        # -HttpCredential $httpCredential `
        # -DefaultStorageAccountName "$defaultStorageAccountName.blob.core.windows.net" `
        # -DefaultStorageAccountKey $defaultStorageAccountKey `
        # -DefaultStorageContainer $existingDefaultBlobContainerName

    ##########################################
    Prepare the HiveQL script and source data
    ##########################################

    Create the temp location
    # New-Item -Path $localFolder -ItemType Directory -Force

    Download the sample file from Azure Blob storage
    # $context = New-AzureStorageContext -StorageAccountName "hditutorialdata" -Anonymous
    # $blobs = Get-AzureStorageBlob -Container "flightdelay" -Context $context
    $blobs | Get-AzureStorageBlobContent -Context $context -Destination $localFolder

    Upload data to default container

    # $azcopycmd = "cmd.exe /C '$azcopyPath\azcopy.exe' /S /Source:'$localFolder' /Dest:'https://$defaultStorageAccountName.blob.core.windows.net/$defaultBlobContainerName/tutorials/flightdelays' /DestKey:$defaultStorageAccountKey"

    # Invoke-Expression -Command:$azcopycmd

    ##########################################
    Submit the Hive job
    ##########################################
    # Use-AzureRmHDInsightCluster -ClusterName $HDInsightClusterName -HttpCredential $httpCredential
    # $response = Invoke-AzureRmHDInsightHiveJob `
                    # -Files $hqlScriptFile `
                    # -DefaultContainer $defaultBlobContainerName `
                    # -DefaultStorageAccountName $defaultStorageAccountName `
                    # -DefaultStorageAccountKey $defaultStorageAccountKey `
                    # -StatusFolder $jobStatusFolder

    # write-Host $response

    ##########################################
    Submit the Sqoop job
    ##########################################
    # $exportDir = "wasb://$defaultBlobContainerName@$defaultStorageAccountName.blob.core.windows.net/tutorials/flightdelays/output"

    # $sqoopDef = New-AzureRmHDInsightSqoopJobDefinition `
                    # -Command "export --connect $sqlDatabaseConnectionString --table $sqlDatabaseTableName --export-dir $exportDir --fields-terminated-by \001 "
    # $sqoopJob = Start-AzureRmHDInsightJob `
                    # -ResourceGroupName $resourceGroupName `
                    # -ClusterName $hdinsightClusterName `
                    # -HttpCredential $httpCredential `
                    # -JobDefinition $sqoopDef #-Debug -Verbose

    # Wait-AzureRmHDInsightJob `
        # -ResourceGroupName $resourceGroupName `
        # -ClusterName $HDInsightClusterName `
        # -HttpCredential $httpCredential `
        # -WaitTimeoutInSeconds 3600 `
        # -Job $sqoopJob.JobId

    # Get-AzureRmHDInsightJobOutput `
        # -ResourceGroupName $resourceGroupName `
        # -ClusterName $hdinsightClusterName `
        # -HttpCredential $httpCredential `
        # -DefaultContainer $existingDefaultBlobContainerName `
        # -DefaultStorageAccountName $defaultStorageAccountName `
        # -DefaultStorageAccountKey $defaultStorageAccountKey `
        # -JobId $sqoopJob.JobId `
        # -DisplayOutputType StandardError

    ##########################################
    Delete the cluster
    ##########################################
    # Remove-AzureRmHDInsightCluster -ResourceGroupName $resourceGroupName -ClusterName $hdinsightClusterName
    # ```
# <a name="3-connect-to-your-sql-database-and-see-average-flight-delays-by-city-in-the-avgdelays-table"></a><span data-ttu-id="3258d-181">3. Connect to your SQL database and see average flight delays by city in the AvgDelays table:</span><span class="sxs-lookup"><span data-stu-id="3258d-181">3. Connect to your SQL database and see average flight delays by city in the AvgDelays table:</span></span>

    # ![HDI.FlightDelays.AvgDelays.Dataset][image-hdi-flightdelays-avgdelays-dataset]

# <a name="-----"></a><span data-ttu-id="3258d-182">- - -</span><span class="sxs-lookup"><span data-stu-id="3258d-182">- - -</span></span>

# <a id="appendix-a"></a><span data-ttu-id="3258d-183">Appendix A - Upload flight delay data to Azure Blob storage</span><span class="sxs-lookup"><span data-stu-id="3258d-183">Appendix A - Upload flight delay data to Azure Blob storage</span></span>
# <a name="uploading-the-data-file-and-the-hiveql-script-files-see-appendix-bappendix-b-requires-some-planning-the-idea-is-to-store-the-data-files-and-the-hiveql-file-before-creating-an-hdinsight-cluster-and-running-the-hive-job-you-have-two-options"></a><span data-ttu-id="3258d-184">Uploading the data file and the HiveQL script files (see [Appendix B](#appendix-b)) requires some planning.</span><span class="sxs-lookup"><span data-stu-id="3258d-184">Uploading the data file and the HiveQL script files (see [Appendix B](#appendix-b)) requires some planning.</span></span> <span data-ttu-id="3258d-185">The idea is to store the data files and the HiveQL file before creating an HDInsight cluster and running the Hive job.</span><span class="sxs-lookup"><span data-stu-id="3258d-185">The idea is to store the data files and the HiveQL file before creating an HDInsight cluster and running the Hive job.</span></span> <span data-ttu-id="3258d-186">You have two options:</span><span class="sxs-lookup"><span data-stu-id="3258d-186">You have two options:</span></span>

# <a name="-use-the-same-azure-storage-account-that-will-be-used-by-the-hdinsight-cluster-as-the-default-file-system-because-the-hdinsight-cluster-will-have-the-storage-account-access-key-you-dont-need-to-make-any-additional-changes"></a><span data-ttu-id="3258d-187">\* **Use the same Azure Storage account that will be used by the HDInsight cluster as the default file system.**</span><span class="sxs-lookup"><span data-stu-id="3258d-187">\* **Use the same Azure Storage account that will be used by the HDInsight cluster as the default file system.**</span></span> <span data-ttu-id="3258d-188">Because the HDInsight cluster will have the Storage account access key, you don't need to make any additional changes.</span><span class="sxs-lookup"><span data-stu-id="3258d-188">Because the HDInsight cluster will have the Storage account access key, you don't need to make any additional changes.</span></span>
# <a name="-use-a-different-azure-storage-account-from-the-hdinsight-cluster-default-file-system-if-this-is-the-case-you-must-modify-the-creation-part-of-the-windows-powershell-script-found-in-create-hdinsight-cluster-and-run-hivesqoop-jobsrunjob-to-link-the-storage-account-as-an-additional-storage-account-for-instructions-see-create-hadoop-clusters-in-hdinsighthdinsight-provision-the-hdinsight-cluster-then-knows-the-access-key-for-the-storage-account"></a><span data-ttu-id="3258d-189">\* **Use a different Azure Storage account from the HDInsight cluster default file system.**</span><span class="sxs-lookup"><span data-stu-id="3258d-189">\* **Use a different Azure Storage account from the HDInsight cluster default file system.**</span></span> <span data-ttu-id="3258d-190">If this is the case, you must modify the creation part of the Windows PowerShell script found in [Create HDInsight cluster and run Hive/Sqoop jobs](#runjob) to link the Storage account as an additional Storage account.</span><span class="sxs-lookup"><span data-stu-id="3258d-190">If this is the case, you must modify the creation part of the Windows PowerShell script found in [Create HDInsight cluster and run Hive/Sqoop jobs](#runjob) to link the Storage account as an additional Storage account.</span></span> <span data-ttu-id="3258d-191">For instructions, see [Create Hadoop clusters in HDInsight][hdinsight-provision].</span><span class="sxs-lookup"><span data-stu-id="3258d-191">For instructions, see [Create Hadoop clusters in HDInsight][hdinsight-provision].</span></span> <span data-ttu-id="3258d-192">The HDInsight cluster then knows the access key for the Storage account.</span><span class="sxs-lookup"><span data-stu-id="3258d-192">The HDInsight cluster then knows the access key for the Storage account.</span></span>

# <a name="-note"></a><span data-ttu-id="3258d-193">> [!NOTE]</span><span class="sxs-lookup"><span data-stu-id="3258d-193">> [!NOTE]</span></span>
# <a name="-the-blob-storage-path-for-the-data-file-is-hard-coded-in-the-hiveql-script-file-you-must-update-it-accordingly"></a><span data-ttu-id="3258d-194">> The Blob storage path for the data file is hard coded in the HiveQL script file.</span><span class="sxs-lookup"><span data-stu-id="3258d-194">> The Blob storage path for the data file is hard coded in the HiveQL script file.</span></span> <span data-ttu-id="3258d-195">You must update it accordingly.</span><span class="sxs-lookup"><span data-stu-id="3258d-195">You must update it accordingly.</span></span>

# <a name="to-download-the-flight-data"></a><span data-ttu-id="3258d-196">**To download the flight data**</span><span class="sxs-lookup"><span data-stu-id="3258d-196">**To download the flight data**</span></span>

# <a name="1-browse-to-research-and-innovative-technology-administration-bureau-of-transportation-statisticsrita-website"></a><span data-ttu-id="3258d-197">1. Browse to [Research and Innovative Technology Administration, Bureau of Transportation Statistics][rita-website].</span><span class="sxs-lookup"><span data-stu-id="3258d-197">1. Browse to [Research and Innovative Technology Administration, Bureau of Transportation Statistics][rita-website].</span></span>
# <a name="2-on-the-page-select-the-following-values"></a><span data-ttu-id="3258d-198">2. On the page, select the following values:</span><span class="sxs-lookup"><span data-stu-id="3258d-198">2. On the page, select the following values:</span></span>

    # <table border="1">
    # <tr><th>Name</th><th>Value</th></tr>
    # <tr><td>Filter Year</td><td>2013 </td></tr>
    # <tr><td>Filter Period</td><td>January</td></tr>
    # <tr><td>Fields</td><td>*Year*, *FlightDate*, *UniqueCarrier*, *Carrier*, *FlightNum*, *OriginAirportID*, *Origin*, *OriginCityName*, *OriginState*, *DestAirportID*, *Dest*, *DestCityName*, *DestState*, *DepDelayMinutes*, *ArrDelay*, *ArrDelayMinutes*, *CarrierDelay*, *WeatherDelay*, *NASDelay*, *SecurityDelay*, *LateAircraftDelay* (clear all other fields)</td></tr>
    # </table>
# <a name="3-click-download"></a><span data-ttu-id="3258d-199">3. Click **Download**.</span><span class="sxs-lookup"><span data-stu-id="3258d-199">3. Click **Download**.</span></span>
# <a name="4-unzip-the-file-to-the-ctutorialsflightdelay2013data-folder-each-file-is-a-csv-file-and-is-approximately-60gb-in-size"></a><span data-ttu-id="3258d-200">4. Unzip the file to the **C:\Tutorials\FlightDelay\2013Data** folder.</span><span class="sxs-lookup"><span data-stu-id="3258d-200">4. Unzip the file to the **C:\Tutorials\FlightDelay\2013Data** folder.</span></span> <span data-ttu-id="3258d-201">Each file is a CSV file and is approximately 60GB in size.</span><span class="sxs-lookup"><span data-stu-id="3258d-201">Each file is a CSV file and is approximately 60GB in size.</span></span>
# <a name="5-rename-the-file-to-the-name-of-the-month-that-it-contains-data-for-for-example-the-file-containing-the-january-data-would-be-named-januarycsv"></a><span data-ttu-id="3258d-202">5. Rename the file to the name of the month that it contains data for.</span><span class="sxs-lookup"><span data-stu-id="3258d-202">5. Rename the file to the name of the month that it contains data for.</span></span> <span data-ttu-id="3258d-203">For example, the file containing the January data would be named *January.csv*.</span><span class="sxs-lookup"><span data-stu-id="3258d-203">For example, the file containing the January data would be named *January.csv*.</span></span>
# <a name="6-repeat-steps-2-and-5-to-download-a-file-for-each-of-the-12-months-in-2013-you-will-need-a-minimum-of-one-file-to-run-the-tutorial"></a><span data-ttu-id="3258d-204">6. Repeat steps 2 and 5 to download a file for each of the 12 months in 2013.</span><span class="sxs-lookup"><span data-stu-id="3258d-204">6. Repeat steps 2 and 5 to download a file for each of the 12 months in 2013.</span></span> <span data-ttu-id="3258d-205">You will need a minimum of one file to run the tutorial.</span><span class="sxs-lookup"><span data-stu-id="3258d-205">You will need a minimum of one file to run the tutorial.</span></span>

# <a name="to-upload-the-flight-delay-data-to-azure-blob-storage"></a><span data-ttu-id="3258d-206">**To upload the flight delay data to Azure Blob storage**</span><span class="sxs-lookup"><span data-stu-id="3258d-206">**To upload the flight delay data to Azure Blob storage**</span></span>

# <a name="1-prepare-the-parameters"></a><span data-ttu-id="3258d-207">1. Prepare the parameters:</span><span class="sxs-lookup"><span data-stu-id="3258d-207">1. Prepare the parameters:</span></span>

    # <table border="1">
    # <tr><th>Variable Name</th><th>Notes</th></tr>
    # <tr><td>$storageAccountName</td><td>The Azure Storage account where you want to upload the data to.</td></tr>
    # <tr><td>$blobContainerName</td><td>The Blob container where you want to upload the data to.</td></tr>
    # </table>
# <a name="2-open-azure-powershell-ise"></a><span data-ttu-id="3258d-208">2. Open Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3258d-208">2. Open Azure PowerShell ISE.</span></span>
# <a name="3-paste-the-following-script-into-the-script-pane"></a><span data-ttu-id="3258d-209">3. Paste the following script into the script pane:</span><span class="sxs-lookup"><span data-stu-id="3258d-209">3. Paste the following script into the script pane:</span></span>

    # ```powershell
    # [CmdletBinding()]
    # Param(

        # [Parameter(Mandatory=$True,
                    # HelpMessage="Enter the Azure storage account name for creating a new HDInsight cluster. If the account doesn't exist, the script will create one.")]
        # [String]$storageAccountName,

        # [Parameter(Mandatory=$True,
                    # HelpMessage="Enter the Azure blob container name for creating a new HDInsight cluster. If not specified, the HDInsight cluster name will be used.")]
        # [String]$blobContainerName
    # )

    Region - Variables
    # $localFolder = "C:\Tutorials\FlightDelay\2013Data"  # The source folder
    # $destFolder = "tutorials/flightdelay/2013data"     #The blob name prefix for the files to be uploaded
    EndRegion

    Region - Connect to Azure subscription
    # Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    # try{Get-AzureRmContext}
    # catch{Connect-AzureRmAccount}
    EndRegion

    Region - Validate user input
    # Write-Host "`nValidating the Azure Storage account and the Blob container..." -ForegroundColor Green
    Validate the Storage account
    # if (-not (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}))
    # {
        # Write-Host "The storage account, $storageAccountName, doesn't exist." -ForegroundColor Red
        # exit
    # }
    # else{
        # $resourceGroupName = (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}).ResourceGroupName
    # }

    Validate the container
    # $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    # $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    # if (-not (Get-AzureStorageContainer -Context $storageContext |Where-Object{$_.Name -eq $blobContainerName}))
    # {
        # Write-Host "The Blob container, $blobContainerName, doesn't exist" -ForegroundColor Red
        # Exit
    # }
    EngRegion

    Region - Copy the file from local workstation to Azure Blob storage
    # if (test-path -Path $localFolder)
    # {
        # foreach ($item in Get-ChildItem -Path $localFolder){
            # $fileName = "$localFolder\$item"
            # $blobName = "$destFolder/$item"

            # Write-Host "Copying $fileName to $blobName" -ForegroundColor Green

            # Set-AzureStorageBlobContent -File $fileName -Container $blobContainerName -Blob $blobName -Context $storageContext
        # }
    # }
    # else
    # {
        # Write-Host "The source folder on the workstation doesn't exist" -ForegroundColor Red
    # }

    List the uploaded files on HDInsight
    # Get-AzureStorageBlob -Container $blobContainerName  -Context $storageContext -Prefix $destFolder
    EndRegion
    # ```
# <a name="4-press-f5-to-run-the-script"></a><span data-ttu-id="3258d-210">4. Press **F5** to run the script.</span><span class="sxs-lookup"><span data-stu-id="3258d-210">4. Press **F5** to run the script.</span></span>

# <a name="if-you-choose-to-use-a-different-method-for-uploading-the-files-please-make-sure-the-file-path-is-tutorialsflightdelaydata-the-syntax-for-accessing-the-files-is"></a><span data-ttu-id="3258d-211">If you choose to use a different method for uploading the files, please make sure the file path is tutorials/flightdelay/data.</span><span class="sxs-lookup"><span data-stu-id="3258d-211">If you choose to use a different method for uploading the files, please make sure the file path is tutorials/flightdelay/data.</span></span> <span data-ttu-id="3258d-212">The syntax for accessing the files is:</span><span class="sxs-lookup"><span data-stu-id="3258d-212">The syntax for accessing the files is:</span></span>

    # wasb://<ContainerName>@<StorageAccountName>.blob.core.windows.net/tutorials/flightdelay/data

# <a name="the-path-tutorialsflightdelaydata-is-the-virtual-folder-you-created-when-you-uploaded-the-files-verify-that-there-are-12-files-one-for-each-month"></a><span data-ttu-id="3258d-213">The path tutorials/flightdelay/data is the virtual folder you created when you uploaded the files.</span><span class="sxs-lookup"><span data-stu-id="3258d-213">The path tutorials/flightdelay/data is the virtual folder you created when you uploaded the files.</span></span> <span data-ttu-id="3258d-214">Verify that there are 12 files, one for each month.</span><span class="sxs-lookup"><span data-stu-id="3258d-214">Verify that there are 12 files, one for each month.</span></span>

# <a name="-note"></a><span data-ttu-id="3258d-215">> [!NOTE]</span><span class="sxs-lookup"><span data-stu-id="3258d-215">> [!NOTE]</span></span>
# <a name="-you-must-update-the-hive-query-to-read-from-the-new-location"></a><span data-ttu-id="3258d-216">> You must update the Hive query to read from the new location.</span><span class="sxs-lookup"><span data-stu-id="3258d-216">> You must update the Hive query to read from the new location.</span></span>
# <a name=""></a>>
# <a name="-you-must-either-configure-the-container-access-permission-to-be-public-or-bind-the-storage-account-to-the-hdinsight-cluster-otherwise-the-hive-query-string-will-not-be-able-to-access-the-data-files"></a><span data-ttu-id="3258d-217">> You must either configure the container access permission to be public or bind the Storage account to the HDInsight cluster.</span><span class="sxs-lookup"><span data-stu-id="3258d-217">> You must either configure the container access permission to be public or bind the Storage account to the HDInsight cluster.</span></span> <span data-ttu-id="3258d-218">Otherwise, the Hive query string will not be able to access the data files.</span><span class="sxs-lookup"><span data-stu-id="3258d-218">Otherwise, the Hive query string will not be able to access the data files.</span></span>

# <a name="-----"></a><span data-ttu-id="3258d-219">- - -</span><span class="sxs-lookup"><span data-stu-id="3258d-219">- - -</span></span>

# <a id="appendix-b"></a><span data-ttu-id="3258d-220">Appendix B - Create and upload a HiveQL script</span><span class="sxs-lookup"><span data-stu-id="3258d-220">Appendix B - Create and upload a HiveQL script</span></span>
# <a name="using-azure-powershell-you-can-run-multiple-hiveql-statements-one-at-a-time-or-package-the-hiveql-statement-into-a-script-file-this-section-shows-you-how-to-create-a-hiveql-script-and-upload-the-script-to-azure-blob-storage-by-using-azure-powershell-hive-requires-the-hiveql-scripts-to-be-stored-in-azure-blob-storage"></a><span data-ttu-id="3258d-221">Using Azure PowerShell, you can run multiple HiveQL statements one at a time, or package the HiveQL statement into a script file.</span><span class="sxs-lookup"><span data-stu-id="3258d-221">Using Azure PowerShell, you can run multiple HiveQL statements one at a time, or package the HiveQL statement into a script file.</span></span> <span data-ttu-id="3258d-222">This section shows you how to create a HiveQL script and upload the script to Azure Blob storage by using Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3258d-222">This section shows you how to create a HiveQL script and upload the script to Azure Blob storage by using Azure PowerShell.</span></span> <span data-ttu-id="3258d-223">Hive requires the HiveQL scripts to be stored in Azure Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-223">Hive requires the HiveQL scripts to be stored in Azure Blob storage.</span></span>

# <a name="the-hiveql-script-will-perform-the-following"></a><span data-ttu-id="3258d-224">The HiveQL script will perform the following:</span><span class="sxs-lookup"><span data-stu-id="3258d-224">The HiveQL script will perform the following:</span></span>

# <a name="1-drop-the-delaysraw-table-in-case-the-table-already-exists"></a><span data-ttu-id="3258d-225">1. **Drop the delays_raw table**, in case the table already exists.</span><span class="sxs-lookup"><span data-stu-id="3258d-225">1. **Drop the delays_raw table**, in case the table already exists.</span></span>
# <a name="2-create-the-delaysraw-external-hive-table-pointing-to-the-blob-storage-location-with-the-flight-delay-files-this-query-specifies-that-fields-are-delimited-by--and-that-lines-are-terminated-by-n-this-poses-a-problem-when-field-values-contain-commas-because-hive-cannot-differentiate-between-a-comma-that-is-a-field-delimiter-and-a-one-that-is-part-of-a-field-value-which-is-the-case-in-field-values-for-origincityname-and-destcityname-to-address-this-the-query-creates-temp-columns-to-hold-data-that-is-incorrectly-split-into-columns"></a><span data-ttu-id="3258d-226">2. **Create the delays_raw external Hive table** pointing to the Blob storage location with the flight delay files.</span><span class="sxs-lookup"><span data-stu-id="3258d-226">2. **Create the delays_raw external Hive table** pointing to the Blob storage location with the flight delay files.</span></span> <span data-ttu-id="3258d-227">This query specifies that fields are delimited by "," and that lines are terminated by "\n".</span><span class="sxs-lookup"><span data-stu-id="3258d-227">This query specifies that fields are delimited by "," and that lines are terminated by "\n".</span></span> <span data-ttu-id="3258d-228">This poses a problem when field values contain commas because Hive cannot differentiate between a comma that is a field delimiter and a one that is part of a field value (which is the case in field values for ORIGIN\_CITY\_NAME and DEST\_CITY\_NAME).</span><span class="sxs-lookup"><span data-stu-id="3258d-228">This poses a problem when field values contain commas because Hive cannot differentiate between a comma that is a field delimiter and a one that is part of a field value (which is the case in field values for ORIGIN\_CITY\_NAME and DEST\_CITY\_NAME).</span></span> <span data-ttu-id="3258d-229">To address this, the query creates TEMP columns to hold data that is incorrectly split into columns.</span><span class="sxs-lookup"><span data-stu-id="3258d-229">To address this, the query creates TEMP columns to hold data that is incorrectly split into columns.</span></span>
# <a name="3-drop-the-delays-table-in-case-the-table-already-exists"></a><span data-ttu-id="3258d-230">3. **Drop the delays table**, in case the table already exists.</span><span class="sxs-lookup"><span data-stu-id="3258d-230">3. **Drop the delays table**, in case the table already exists.</span></span>
# <a name="4-create-the-delays-table-it-is-helpful-to-clean-up-the-data-before-further-processing-this-query-creates-a-new-table-delays-from-the-delaysraw-table-note-that-the-temp-columns-as-mentioned-previously-are-not-copied-and-that-the-substring-function-is-used-to-remove-quotation-marks-from-the-data"></a><span data-ttu-id="3258d-231">4. **Create the delays table**.</span><span class="sxs-lookup"><span data-stu-id="3258d-231">4. **Create the delays table**.</span></span> <span data-ttu-id="3258d-232">It is helpful to clean up the data before further processing.</span><span class="sxs-lookup"><span data-stu-id="3258d-232">It is helpful to clean up the data before further processing.</span></span> <span data-ttu-id="3258d-233">This query creates a new table, *delays*, from the delays_raw table.</span><span class="sxs-lookup"><span data-stu-id="3258d-233">This query creates a new table, *delays*, from the delays_raw table.</span></span> <span data-ttu-id="3258d-234">Note that the TEMP columns (as mentioned previously) are not copied, and that the **substring** function is used to remove quotation marks from the data.</span><span class="sxs-lookup"><span data-stu-id="3258d-234">Note that the TEMP columns (as mentioned previously) are not copied, and that the **substring** function is used to remove quotation marks from the data.</span></span>
# <a name="5-compute-the-average-weather-delay-and-groups-the-results-by-city-name-it-will-also-output-the-results-to-blob-storage-note-that-the-query-will-remove-apostrophes-from-the-data-and-will-exclude-rows-where-the-value-for-weatherdelay-is-null-this-is-necessary-because-sqoop-used-later-in-this-tutorial-doesnt-handle-those-values-gracefully-by-default"></a><span data-ttu-id="3258d-235">5. **Compute the average weather delay and groups the results by city name.**</span><span class="sxs-lookup"><span data-stu-id="3258d-235">5. **Compute the average weather delay and groups the results by city name.**</span></span> <span data-ttu-id="3258d-236">It will also output the results to Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-236">It will also output the results to Blob storage.</span></span> <span data-ttu-id="3258d-237">Note that the query will remove apostrophes from the data and will exclude rows where the value for **weather_delay** is null.</span><span class="sxs-lookup"><span data-stu-id="3258d-237">Note that the query will remove apostrophes from the data and will exclude rows where the value for **weather_delay** is null.</span></span> <span data-ttu-id="3258d-238">This is necessary because Sqoop, used later in this tutorial, doesn't handle those values gracefully by default.</span><span class="sxs-lookup"><span data-stu-id="3258d-238">This is necessary because Sqoop, used later in this tutorial, doesn't handle those values gracefully by default.</span></span>

# <a name="for-a-full-list-of-the-hiveql-commands-see-hive-data-definition-languagehadoop-hiveql-each-hiveql-command-must-terminate-with-a-semicolon"></a><span data-ttu-id="3258d-239">For a full list of the HiveQL commands, see [Hive Data Definition Language][hadoop-hiveql].</span><span class="sxs-lookup"><span data-stu-id="3258d-239">For a full list of the HiveQL commands, see [Hive Data Definition Language][hadoop-hiveql].</span></span> <span data-ttu-id="3258d-240">Each HiveQL command must terminate with a semicolon.</span><span class="sxs-lookup"><span data-stu-id="3258d-240">Each HiveQL command must terminate with a semicolon.</span></span>

# <a name="to-create-a-hiveql-script-file"></a><span data-ttu-id="3258d-241">**To create a HiveQL script file**</span><span class="sxs-lookup"><span data-stu-id="3258d-241">**To create a HiveQL script file**</span></span>

# <a name="1-prepare-the-parameters"></a><span data-ttu-id="3258d-242">1. Prepare the parameters:</span><span class="sxs-lookup"><span data-stu-id="3258d-242">1. Prepare the parameters:</span></span>

    # <table border="1">
    # <tr><th>Variable Name</th><th>Notes</th></tr>
    # <tr><td>$storageAccountName</td><td>The Azure Storage account where you want to upload the HiveQL script to.</td></tr>
    # <tr><td>$blobContainerName</td><td>The Blob container where you want to upload the HiveQL script to.</td></tr>
    # </table>
    
# <a name="2-open-azure-powershell-ise"></a><span data-ttu-id="3258d-243">2. Open Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3258d-243">2. Open Azure PowerShell ISE.</span></span>  

# <a name="3-copy-and-paste-the-following-script-into-the-script-pane"></a><span data-ttu-id="3258d-244">3. Copy and paste the following script into the script pane:</span><span class="sxs-lookup"><span data-stu-id="3258d-244">3. Copy and paste the following script into the script pane:</span></span>  

    # ```powershell
    # [CmdletBinding()]
    # Param(

        Azure Blob storage variables
        # [Parameter(Mandatory=$True,
                    # HelpMessage="Enter the Azure storage account name for creating a new HDInsight cluster. If the account doesn't exist, the script will create one.")]
        # [String]$storageAccountName,

        # [Parameter(Mandatory=$True,
                    # HelpMessage="Enter the Azure blob container name for creating a new HDInsight cluster. If not specified, the HDInsight cluster name will be used.")]
        # [String]$blobContainerName
    # )

    region - Define variables
    Treat all errors as terminating
    # $ErrorActionPreference = "Stop"

    The HiveQL script file is exported as this file before it's uploaded to Blob storage
    # $hqlLocalFileName = "e:\tutorials\flightdelay\flightdelays.hql"

    The HiveQL script file will be uploaded to Blob storage as this blob name
    # $hqlBlobName = "tutorials/flightdelay/flightdelays.hql"

    These two constants are used by the HiveQL script file
    $srcDataFolder = "tutorials/flightdelay/data"
    # $dstDataFolder = "/tutorials/flightdelay/output"
    endregion

    Region - Connect to Azure subscription
    # Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    # try{Get-AzureRmContext}
    # catch{Connect-AzureRmAccount}
    EndRegion

    Region - Validate user input
    # Write-Host "`nValidating the Azure Storage account and the Blob container..." -ForegroundColor Green
    Validate the Storage account
    # if (-not (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}))
    # {
        # Write-Host "The storage account, $storageAccountName, doesn't exist." -ForegroundColor Red
        # exit
    # }
    # else{
        # $resourceGroupName = (Get-AzureRmStorageAccount|Where-Object{$_.StorageAccountName -eq $storageAccountName}).ResourceGroupName
    # }

    Validate the container
    # $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    # $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    # if (-not (Get-AzureStorageContainer -Context $storageContext |Where-Object{$_.Name -eq $blobContainerName}))
    # {
        # Write-Host "The Blob container, $blobContainerName, doesn't exist" -ForegroundColor Red
        # Exit
    # }
    EngRegion

    region - Validate the file and file path

    Check if a file with the same file name already exists on the workstation
    # Write-Host "`nvalidating the folder structure on the workstation for saving the HQL script file ..."  -ForegroundColor Green
    # if (test-path $hqlLocalFileName){

        # $isDelete = Read-Host 'The file, ' $hqlLocalFileName ', exists.  Do you want to overwirte it? (Y/N)'

        # if ($isDelete.ToLower() -ne "y")
        # {
            # Exit
        # }
    # }

    Create the folder if it doesn't exist
    # $folder = split-path $hqlLocalFileName
    # if (-not (test-path $folder))
    # {
        # Write-Host "`nCreating folder, $folder ..." -ForegroundColor Green

        # new-item $folder -ItemType directory
    # }
    end region

    region - Write the Hive script into a local file
    # Write-Host "`nWriting the Hive script into a file on your workstation ..." `
                # -ForegroundColor Green

    # $hqlDropDelaysRaw = "DROP TABLE delays_raw;"

    # $hqlCreateDelaysRaw = "CREATE EXTERNAL TABLE delays_raw (" +
            # "YEAR string, " +
            # "FL_DATE string, " +
            # "UNIQUE_CARRIER string, " +
            # "CARRIER string, " +
            # "FL_NUM string, " +
            # "ORIGIN_AIRPORT_ID string, " +
            # "ORIGIN string, " +
            # "ORIGIN_CITY_NAME string, " +
            # "ORIGIN_CITY_NAME_TEMP string, " +
            # "ORIGIN_STATE_ABR string, " +
            # "DEST_AIRPORT_ID string, " +
            # "DEST string, " +
            # "DEST_CITY_NAME string, " +
            # "DEST_CITY_NAME_TEMP string, " +
            # "DEST_STATE_ABR string, " +
            # "DEP_DELAY_NEW float, " +
            # "ARR_DELAY_NEW float, " +
            # "CARRIER_DELAY float, " +
            # "WEATHER_DELAY float, " +
            # "NAS_DELAY float, " +
            # "SECURITY_DELAY float, " +
            # "LATE_AIRCRAFT_DELAY float) " +
        # "ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' " +
        # "LINES TERMINATED BY '\n' " +
        # "STORED AS TEXTFILE " +
        # "LOCATION 'wasb://flightdelay@hditutorialdata.blob.core.windows.net/2013Data';"

    # $hqlDropDelays = "DROP TABLE delays;"

    # $hqlCreateDelays = "CREATE TABLE delays AS " +
        # "SELECT YEAR AS year, " +
            # "FL_DATE AS flight_date, " +
            # "substring(UNIQUE_CARRIER, 2, length(UNIQUE_CARRIER) -1) AS unique_carrier, " +
            # "substring(CARRIER, 2, length(CARRIER) -1) AS carrier, " +
            # "substring(FL_NUM, 2, length(FL_NUM) -1) AS flight_num, " +
            # "ORIGIN_AIRPORT_ID AS origin_airport_id, " +
            # "substring(ORIGIN, 2, length(ORIGIN) -1) AS origin_airport_code, " +
            # "substring(ORIGIN_CITY_NAME, 2) AS origin_city_name, " +
            # "substring(ORIGIN_STATE_ABR, 2, length(ORIGIN_STATE_ABR) -1)  AS origin_state_abr, " +
            # "DEST_AIRPORT_ID AS dest_airport_id, " +
            # "substring(DEST, 2, length(DEST) -1) AS dest_airport_code, " +
            # "substring(DEST_CITY_NAME,2) AS dest_city_name, " +
            # "substring(DEST_STATE_ABR, 2, length(DEST_STATE_ABR) -1) AS dest_state_abr, " +
            # "DEP_DELAY_NEW AS dep_delay_new, " +
            # "ARR_DELAY_NEW AS arr_delay_new, " +
            # "CARRIER_DELAY AS carrier_delay, " +
            # "WEATHER_DELAY AS weather_delay, " +
            # "NAS_DELAY AS nas_delay, " +
            # "SECURITY_DELAY AS security_delay, " +
            # "LATE_AIRCRAFT_DELAY AS late_aircraft_delay " +
        # "FROM delays_raw;"

    # $hqlInsertLocal = "INSERT OVERWRITE DIRECTORY '$dstDataFolder' " +
        # "SELECT regexp_replace(origin_city_name, '''', ''), " +
            # "avg(weather_delay) " +
        # "FROM delays " +
        # "WHERE weather_delay IS NOT NULL " +
        # "GROUP BY origin_city_name;"

    # $hqlScript = $hqlDropDelaysRaw + $hqlCreateDelaysRaw + $hqlDropDelays + $hqlCreateDelays + $hqlInsertLocal

    # $hqlScript | Out-File $hqlLocalFileName -Encoding ascii -Force
    endregion

    region - Upload the Hive script to the default Blob container
    # Write-Host "`nUploading the Hive script to the default Blob container ..." -ForegroundColor Green

    Create a storage context object
    # $storageAccountKey = (Get-AzureRmStorageAccountKey -StorageAccountName $storageAccountName -ResourceGroupName $resourceGroupName)[0].Value
    # $destContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $storageAccountKey

    Upload the file from local workstation to Blob storage
    # Set-AzureStorageBlobContent -File $hqlLocalFileName -Container $blobContainerName -Blob $hqlBlobName -Context $destContext
    endregion

    # Write-host "`nEnd of the PowerShell script" -ForegroundColor Green
    # ```

    # Here are the variables used in the script:

   # <a name="-hqllocalfilename---the-script-saves-the-hiveql-script-file-locally-before-uploading-it-to-blob-storage-this-is-the-file-name-the-default-value-is-uctutorialsflightdelayflightdelayshqlu"></a><span data-ttu-id="3258d-245">\* **$hqlLocalFileName** - The script saves the HiveQL script file locally before uploading it to Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-245">\* **$hqlLocalFileName** - The script saves the HiveQL script file locally before uploading it to Blob storage.</span></span> <span data-ttu-id="3258d-246">This is the file name.</span><span class="sxs-lookup"><span data-stu-id="3258d-246">This is the file name.</span></span> <span data-ttu-id="3258d-247">The default value is <u>C:\tutorials\flightdelay\flightdelays.hql</u>.</span><span class="sxs-lookup"><span data-stu-id="3258d-247">The default value is <u>C:\tutorials\flightdelay\flightdelays.hql</u>.</span></span>
   # <a name="-hqlblobname---this-is-the-hiveql-script-file-blob-name-used-in-the-azure-blob-storage-the-default-value-is-tutorialsflightdelayflightdelayshql-because-the-file-will-be-written-directly-to-azure-blob-storage-there-is-not-a--at-the-beginning-of-the-blob-name-if-you-want-to-access-the-file-from-blob-storage-you-will-need-to-add-a--at-the-beginning-of-the-file-name"></a><span data-ttu-id="3258d-248">\* **$hqlBlobName** - This is the HiveQL script file blob name used in the Azure Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3258d-248">\* **$hqlBlobName** - This is the HiveQL script file blob name used in the Azure Blob storage.</span></span> <span data-ttu-id="3258d-249">The default value is tutorials/flightdelay/flightdelays.hql.</span><span class="sxs-lookup"><span data-stu-id="3258d-249">The default value is tutorials/flightdelay/flightdelays.hql.</span></span> <span data-ttu-id="3258d-250">Because the file will be written directly to Azure Blob storage, there is NOT a "/" at the beginning of the blob name.</span><span class="sxs-lookup"><span data-stu-id="3258d-250">Because the file will be written directly to Azure Blob storage, there is NOT a "/" at the beginning of the blob name.</span></span> <span data-ttu-id="3258d-251">If you want to access the file from Blob storage, you will need to add a "/" at the beginning of the file name.</span><span class="sxs-lookup"><span data-stu-id="3258d-251">If you want to access the file from Blob storage, you will need to add a "/" at the beginning of the file name.</span></span>
   # <a name="-srcdatafolder-and-dstdatafolder----tutorialsflightdelaydata--tutorialsflightdelayoutput"></a><span data-ttu-id="3258d-252">\* **$srcDataFolder** and **$dstDataFolder** - = "tutorials/flightdelay/data" = "tutorials/flightdelay/output"</span><span class="sxs-lookup"><span data-stu-id="3258d-252">\* **$srcDataFolder** and **$dstDataFolder** - = "tutorials/flightdelay/data" = "tutorials/flightdelay/output"</span></span>

# <a name="-----"></a><span data-ttu-id="3258d-253">- - -</span><span class="sxs-lookup"><span data-stu-id="3258d-253">- - -</span></span>
# <a id="appendix-c"></a><span data-ttu-id="3258d-254">Appendix C - Prepare an Azure SQL database for the Sqoop job output</span><span class="sxs-lookup"><span data-stu-id="3258d-254">Appendix C - Prepare an Azure SQL database for the Sqoop job output</span></span>
# <a name="to-prepare-the-sql-database-merge-this-with-the-sqoop-script"></a><span data-ttu-id="3258d-255">**To prepare the SQL database (merge this with the Sqoop script)**</span><span class="sxs-lookup"><span data-stu-id="3258d-255">**To prepare the SQL database (merge this with the Sqoop script)**</span></span>

# <a name="1-prepare-the-parameters"></a><span data-ttu-id="3258d-256">1. Prepare the parameters:</span><span class="sxs-lookup"><span data-stu-id="3258d-256">1. Prepare the parameters:</span></span>

    # <table border="1">
    # <tr><th>Variable Name</th><th>Notes</th></tr>
    # <tr><td>$sqlDatabaseServerName</td><td>The name of the Azure SQL database server. Enter nothing to create a new server.</td></tr>
    # <tr><td>$sqlDatabaseUsername</td><td>The login name for the Azure SQL database server. If $sqlDatabaseServerName is an existing server, the login and login password are used to authenticate with the server. Otherwise they are used to create a new server.</td></tr>
    # <tr><td>$sqlDatabasePassword</td><td>The login password for the Azure SQL database server.</td></tr>
    # <tr><td>$sqlDatabaseLocation</td><td>This value is used only when you're creating a new Azure database server.</td></tr>
    # <tr><td>$sqlDatabaseName</td><td>The SQL database used to create the AvgDelays table for the Sqoop job. Leaving it blank will create a database called HDISqoop. The table name for the Sqoop job output is AvgDelays. </td></tr>
    # </table>
    
# <a name="2-open-azure-powershell-ise"></a><span data-ttu-id="3258d-257">2. Open Azure PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3258d-257">2. Open Azure PowerShell ISE.</span></span>

# <a name="3-copy-and-paste-the-following-script-into-the-script-pane"></a><span data-ttu-id="3258d-258">3. Copy and paste the following script into the script pane:</span><span class="sxs-lookup"><span data-stu-id="3258d-258">3. Copy and paste the following script into the script pane:</span></span>  

    # ```powershell
    # [CmdletBinding()]
    # Param(

        Azure Resource group variables
        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the Azure resource group name. It will be created if it doesn't exist.")]
        # [String]$resourceGroupName,

        SQL database server variables
        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the Azure SQL Database Server Name. It will be created if it doesn't exist.")]
        # [String]$sqlDatabaseServer,

        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the Azure SQL Database admin user.")]
        # [String]$sqlDatabaseLogin,

        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the Azure SQL Database admin user password.")]
        # [String]$sqlDatabasePassword,

        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the region to create the Database in.")]
        # [String]$sqlDatabaseLocation,   #For example, West US.

        SQL database variables
        # [Parameter(Mandatory=$True,
                # HelpMessage="Enter the database name. It will be created if it doesn't exist.")]
        # [String]$sqlDatabaseName # specify the database name if you have one created. Otherwise use "" to have the script create one for you.
    # )

    Treat all errors as terminating
    # $ErrorActionPreference = "Stop"

    region - Constants and variables

    IP address REST service used for retrieving external IP address and creating firewall rules
    # [String]$ipAddressRestService = "http://bot.whatismyipaddress.com"
    # [String]$fireWallRuleName = "FlightDelay"

    SQL database variables
    # [String]$sqlDatabaseMaxSizeGB = 10

    SQL query string for creating AvgDelays table
    # [String]$sqlDatabaseTableName = "AvgDelays"
    # [String]$sqlCreateAvgDelaysTable = " CREATE TABLE [dbo].[$sqlDatabaseTableName](
                # [origin_city_name] [nvarchar](50) NOT NULL,
                # [weather_delay] float,
            # CONSTRAINT [PK_$sqlDatabaseTableName] PRIMARY KEY CLUSTERED
            # (
                # [origin_city_name] ASC
            # )
            # )"
    endregion

    Region - Connect to Azure subscription
    # Write-Host "`nConnecting to your Azure subscription ..." -ForegroundColor Green
    # try{Get-AzureRmContext}
    # catch{Connect-AzureRmAccount}
    EndRegion

    region - Create and validate Azure resouce group
    # try{
        # Get-AzureRmResourceGroup -Name $resourceGroupName
    # }
    # catch{
        # New-AzureRmResourceGroup -Name $resourceGroupName -Location $sqlDatabaseLocation
    # }

    EndRegion

    region - Create and validate Azure SQL database server
    # try{
        # Get-AzureRmSqlServer -ServerName $sqlDatabaseServer -ResourceGroupName $resourceGroupName}
    # catch{
        # Write-Host "`nCreating SQL Database server ..."  -ForegroundColor Green

        # $sqlDatabasePW = ConvertTo-SecureString -String $sqlDatabasePassword -AsPlainText -Force
        # $credential = New-Object System.Management.Automation.PSCredential($sqlDatabaseLogin,$sqlDatabasePW)

        # $sqlDatabaseServer = (New-AzureRmSqlServer -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -SqlAdministratorCredentials $credential -Location $sqlDatabaseLocation).ServerName
        # Write-Host "`tThe new SQL database server name is $sqlDatabaseServer." -ForegroundColor Cyan

        # Write-Host "`nCreating firewall rule, $fireWallRuleName ..." -ForegroundColor Green
        # $workstationIPAddress = Invoke-RestMethod $ipAddressRestService
        # New-AzureRmSqlServerFirewallRule -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -FirewallRuleName "$fireWallRuleName-workstation" -StartIpAddress $workstationIPAddress -EndIpAddress $workstationIPAddress

        To allow other Azure services to access the server add a firewall rule and set both the StartIpAddress and EndIpAddress to 0.0.0.0. Note that this allows Azure traffic from any Azure subscription to access the server.
        # New-AzureRmSqlServerFirewallRule -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -FirewallRuleName "$fireWallRuleName-Azureservices" -StartIpAddress "0.0.0.0" -EndIpAddress "0.0.0.0"
    # }

    endregion

    region - Create and validate Azure SQL database

    # try {
        # Get-AzureRmSqlDatabase -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -DatabaseName $sqlDatabaseName
    # }
    # catch {
        # Write-Host "`nCreating SQL Database, $sqlDatabaseName ..."  -ForegroundColor Green
        # New-AzureRMSqlDatabase -ResourceGroupName $resourceGroupName -ServerName $sqlDatabaseServer -DatabaseName $sqlDatabaseName -Edition "Standard" -RequestedServiceObjectiveName "S1"
    # }

    endregion

    region -  Execute an SQL command to create the AvgDelays table

    # Write-Host "`nCreating SQL Database table ..."  -ForegroundColor Green
    # $conn = New-Object System.Data.SqlClient.SqlConnection
    # $conn.ConnectionString = "Data Source=$sqlDatabaseServer.database.windows.net;Initial Catalog=$sqlDatabaseName;User ID=$sqlDatabaseLogin;Password=$sqlDatabasePassword;Encrypt=true;Trusted_Connection=false;"
    # $conn.open()
    # $cmd = New-Object System.Data.SqlClient.SqlCommand
    # $cmd.connection = $conn
    # $cmd.commandtext = $sqlCreateAvgDelaysTable
    # $cmd.executenonquery()

    # $conn.close()

    # Write-host "`nEnd of the PowerShell script" -ForegroundColor Green
    # ```

   # <a name="-note"></a><span data-ttu-id="3258d-259">> [!NOTE]</span><span class="sxs-lookup"><span data-stu-id="3258d-259">> [!NOTE]</span></span>
   # <a name="-the-script-uses-a-representational-state-transfer-rest-service-httpbotwhatismyipaddresscom-to-retrieve-your-external-ip-address-the-ip-address-is-used-for-creating-a-firewall-rule-for-your-sql-database-server"></a><span data-ttu-id="3258d-260">> The script uses a representational state transfer (REST) service, http://bot.whatismyipaddress.com, to retrieve your external IP address.</span><span class="sxs-lookup"><span data-stu-id="3258d-260">> The script uses a representational state transfer (REST) service, http://bot.whatismyipaddress.com, to retrieve your external IP address.</span></span> <span data-ttu-id="3258d-261">The IP address is used for creating a firewall rule for your SQL database server.</span><span class="sxs-lookup"><span data-stu-id="3258d-261">The IP address is used for creating a firewall rule for your SQL database server.</span></span>

    # Here are some variables used in the script:

   # <a name="-ipaddressrestservice---the-default-value-is-httpbotwhatismyipaddresscom-it-is-a-public-ip-address-rest-service-for-getting-your-external-ip-address-you-can-use-other-services-if-you-want-the-external-ip-address-retrieved-through-the-service-will-be-used-to-create-a-firewall-rule-for-your-azure-sql-database-server-so-that-you-can-access-the-database-from-your-workstation-by-using-a-windows-powershell-script"></a><span data-ttu-id="3258d-262">\* **$ipAddressRestService** - The default value is http://bot.whatismyipaddress.com. It is a public IP address REST service for getting your external IP address.</span><span class="sxs-lookup"><span data-stu-id="3258d-262">\* **$ipAddressRestService** - The default value is http://bot.whatismyipaddress.com. It is a public IP address REST service for getting your external IP address.</span></span> <span data-ttu-id="3258d-263">You can use other services if you want.</span><span class="sxs-lookup"><span data-stu-id="3258d-263">You can use other services if you want.</span></span> <span data-ttu-id="3258d-264">The external IP address retrieved through the service will be used to create a firewall rule for your Azure SQL database server, so that you can access the database from your workstation (by using a Windows PowerShell script).</span><span class="sxs-lookup"><span data-stu-id="3258d-264">The external IP address retrieved through the service will be used to create a firewall rule for your Azure SQL database server, so that you can access the database from your workstation (by using a Windows PowerShell script).</span></span>
   # <a name="-firewallrulename---this-is-the-name-of-the-firewall-rule-for-the-azure-sql-database-server-the-default-name-is-uflightdelayu-you-can-rename-it-if-you-want"></a><span data-ttu-id="3258d-265">\* **$fireWallRuleName** - This is the name of the firewall rule for the Azure SQL database server.</span><span class="sxs-lookup"><span data-stu-id="3258d-265">\* **$fireWallRuleName** - This is the name of the firewall rule for the Azure SQL database server.</span></span> <span data-ttu-id="3258d-266">The default name is <u>FlightDelay</u>.</span><span class="sxs-lookup"><span data-stu-id="3258d-266">The default name is <u>FlightDelay</u>.</span></span> <span data-ttu-id="3258d-267">You can rename it if you want.</span><span class="sxs-lookup"><span data-stu-id="3258d-267">You can rename it if you want.</span></span>
   # <a name="-sqldatabasemaxsizegb---this-value-is-used-only-when-youre-creating-a-new-azure-sql-database-server-the-default-value-is-10gb-10gb-is-sufficient-for-this-tutorial"></a><span data-ttu-id="3258d-268">\* **$sqlDatabaseMaxSizeGB** - This value is used only when you're creating a new Azure SQL database server.</span><span class="sxs-lookup"><span data-stu-id="3258d-268">\* **$sqlDatabaseMaxSizeGB** - This value is used only when you're creating a new Azure SQL database server.</span></span> <span data-ttu-id="3258d-269">The default value is 10GB.</span><span class="sxs-lookup"><span data-stu-id="3258d-269">The default value is 10GB.</span></span> <span data-ttu-id="3258d-270">10GB is sufficient for this tutorial.</span><span class="sxs-lookup"><span data-stu-id="3258d-270">10GB is sufficient for this tutorial.</span></span>
   # <a name="-sqldatabasename---this-value-is-used-only-when-youre-creating-a-new-azure-sql-database-the-default-value-is-hdisqoop-if-you-rename-it-you-must-update-the-sqoop-windows-powershell-script-accordingly"></a><span data-ttu-id="3258d-271">\* **$sqlDatabaseName** - This value is used only when you're creating a new Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="3258d-271">\* **$sqlDatabaseName** - This value is used only when you're creating a new Azure SQL database.</span></span> <span data-ttu-id="3258d-272">The default value is HDISqoop.</span><span class="sxs-lookup"><span data-stu-id="3258d-272">The default value is HDISqoop.</span></span> <span data-ttu-id="3258d-273">If you rename it, you must update the Sqoop Windows PowerShell script accordingly.</span><span class="sxs-lookup"><span data-stu-id="3258d-273">If you rename it, you must update the Sqoop Windows PowerShell script accordingly.</span></span>
# <a name="4-press-f5-to-run-the-script"></a><span data-ttu-id="3258d-274">4. Press **F5** to run the script.</span><span class="sxs-lookup"><span data-stu-id="3258d-274">4. Press **F5** to run the script.</span></span>
# <a name="5-validate-the-script-output-make-sure-the-script-ran-successfully"></a><span data-ttu-id="3258d-275">5. Validate the script output.</span><span class="sxs-lookup"><span data-stu-id="3258d-275">5. Validate the script output.</span></span> <span data-ttu-id="3258d-276">Make sure the script ran successfully.</span><span class="sxs-lookup"><span data-stu-id="3258d-276">Make sure the script ran successfully.</span></span>

# <a id="nextsteps"></a> <span data-ttu-id="3258d-277">Next steps</span><span class="sxs-lookup"><span data-stu-id="3258d-277">Next steps</span></span>
# <a name="now-you-understand-how-to-upload-a-file-to-azure-blob-storage-how-to-populate-a-hive-table-by-using-the-data-from-azure-blob-storage-how-to-run-hive-queries-and-how-to-use-sqoop-to-export-data-from-hdfs-to-an-azure-sql-database-to-learn-more-see-the-following-articles"></a><span data-ttu-id="3258d-278">Now you understand how to upload a file to Azure Blob storage, how to populate a Hive table by using the data from Azure Blob storage, how to run Hive queries, and how to use Sqoop to export data from HDFS to an Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="3258d-278">Now you understand how to upload a file to Azure Blob storage, how to populate a Hive table by using the data from Azure Blob storage, how to run Hive queries, and how to use Sqoop to export data from HDFS to an Azure SQL database.</span></span> <span data-ttu-id="3258d-279">To learn more, see the following articles:</span><span class="sxs-lookup"><span data-stu-id="3258d-279">To learn more, see the following articles:</span></span>

# <a name="-get-started-with-hdinsighthdinsight-get-started"></a><span data-ttu-id="3258d-280">\* [Get started with HDInsight][hdinsight-get-started]</span><span class="sxs-lookup"><span data-stu-id="3258d-280">\* [Get started with HDInsight][hdinsight-get-started]</span></span>
# <a name="-use-hive-with-hdinsighthdinsight-use-hive"></a><span data-ttu-id="3258d-281">\* [Use Hive with HDInsight][hdinsight-use-hive]</span><span class="sxs-lookup"><span data-stu-id="3258d-281">\* [Use Hive with HDInsight][hdinsight-use-hive]</span></span>
# <a name="-use-oozie-with-hdinsighthdinsight-use-oozie"></a><span data-ttu-id="3258d-282">\* [Use Oozie with HDInsight][hdinsight-use-oozie]</span><span class="sxs-lookup"><span data-stu-id="3258d-282">\* [Use Oozie with HDInsight][hdinsight-use-oozie]</span></span>
# <a name="-use-sqoop-with-hdinsighthdinsight-use-sqoop"></a><span data-ttu-id="3258d-283">\* [Use Sqoop with HDInsight][hdinsight-use-sqoop]</span><span class="sxs-lookup"><span data-stu-id="3258d-283">\* [Use Sqoop with HDInsight][hdinsight-use-sqoop]</span></span>
# <a name="-use-pig-with-hdinsighthdinsight-use-pig"></a><span data-ttu-id="3258d-284">\* [Use Pig with HDInsight][hdinsight-use-pig]</span><span class="sxs-lookup"><span data-stu-id="3258d-284">\* [Use Pig with HDInsight][hdinsight-use-pig]</span></span>
# <a name="-develop-java-mapreduce-programs-for-hdinsighthdinsight-develop-mapreduce"></a><span data-ttu-id="3258d-285">\* [Develop Java MapReduce programs for HDInsight][hdinsight-develop-mapreduce]</span><span class="sxs-lookup"><span data-stu-id="3258d-285">\* [Develop Java MapReduce programs for HDInsight][hdinsight-develop-mapreduce]</span></span>

# <a name="azure-purchase-options-httpazuremicrosoftcompricingpurchase-options"></a>[azure-purchase-options]: http://azure.microsoft.com/pricing/purchase-options/
# <a name="azure-member-offers-httpazuremicrosoftcompricingmember-offers"></a>[azure-member-offers]: http://azure.microsoft.com/pricing/member-offers/
# <a name="azure-free-trial-httpazuremicrosoftcompricingfree-trial"></a>[azure-free-trial]: http://azure.microsoft.com/pricing/free-trial/

# <a name="rita-website-httpwwwtranstatsbtsgovdlselectfieldsasptableid236dbshortnameon-time"></a>[rita-website]: http://www.transtats.bts.gov/DL_SelectFields.asp?Table_ID=236&DB_Short_Name=On-Time
# <a name="powershell-install-configure-powershellazureps-cmdlets-docs"></a>[powershell-install-configure]: /powershell/azureps-cmdlets-docs

# <a name="hdinsight-use-oozie-hdinsight-use-ooziemd"></a>[hdinsight-use-oozie]: hdinsight-use-oozie.md
# <a name="hdinsight-use-hivehadoophdinsight-use-hivemd"></a>[hdinsight-use-hive]:hadoop/hdinsight-use-hive.md
# <a name="hdinsight-provision-hdinsight-hadoop-provision-linux-clustersmd"></a>[hdinsight-provision]: hdinsight-hadoop-provision-linux-clusters.md
# <a name="hdinsight-storage-hdinsight-hadoop-use-blob-storagemd"></a>[hdinsight-storage]: hdinsight-hadoop-use-blob-storage.md
# <a name="hdinsight-upload-data-hdinsight-upload-datamd"></a>[hdinsight-upload-data]: hdinsight-upload-data.md
# <a name="hdinsight-get-startedhadoopapache-hadoop-linux-tutorial-get-startedmd"></a>[hdinsight-get-started]:hadoop/apache-hadoop-linux-tutorial-get-started.md
# <a name="hdinsight-use-sqoophadoophdinsight-use-sqoopmd"></a>[hdinsight-use-sqoop]:hadoop/hdinsight-use-sqoop.md
# <a name="hdinsight-use-pighadoophdinsight-use-pigmd"></a>[hdinsight-use-pig]:hadoop/hdinsight-use-pig.md
# <a name="hdinsight-develop-mapreducehadoopapache-hadoop-develop-deploy-java-mapreduce-linuxmd"></a>[hdinsight-develop-mapreduce]:hadoop/apache-hadoop-develop-deploy-java-mapreduce-linux.md

# <a name="hadoop-hiveql-httpscwikiapacheorgconfluencedisplayhivelanguagemanualddl"></a>[hadoop-hiveql]: https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL
# <a name="hadoop-shell-commands-httphadoopapacheorgdocsr0183hdfsshellhtml"></a>[hadoop-shell-commands]: http://hadoop.apache.org/docs/r0.18.3/hdfs_shell.html

# <a name="technetwiki-hive-error-httpsocialtechnetmicrosoftcomwikicontentsarticles23047hdinsight-hive-error-unable-to-renameaspx"></a>[technetwiki-hive-error]: http://social.technet.microsoft.com/wiki/contents/articles/23047.hdinsight-hive-error-unable-to-rename.aspx

# <a name="image-hdi-flightdelays-avgdelays-dataset-mediahdinsight-analyze-flight-delay-datahdiflightdelaysavgdelaysdatasetpng"></a>[image-hdi-flightdelays-avgdelays-dataset]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.AvgDelays.DataSet.png
# <a name="img-hdi-flightdelays-run-hive-job-output-mediahdinsight-analyze-flight-delay-datahdiflightdelaysrunhivejoboutputpng"></a>[img-hdi-flightdelays-run-hive-job-output]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.RunHiveJob.Output.png
# <a name="img-hdi-flightdelays-flow-mediahdinsight-analyze-flight-delay-datahdiflightdelaysflowpng"></a>[img-hdi-flightdelays-flow]: ./media/hdinsight-analyze-flight-delay-data/HDI.FlightDelays.Flow.png


# <!--HONumber=Apr18_HO3-->


            
