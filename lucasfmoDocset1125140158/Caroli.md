---
title: 'Comment : créer des projets Office dans Visual Studio | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50739bfde7578a49226e5396c8eeb78e56c4b0ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-office-projects-in-visual-studio"></a><span data-ttu-id="cc100-102">Comment : créer des projets Office dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cc100-102">How to: Create Office Projects in Visual Studio</span></span>
  <span data-ttu-id="cc100-103">Vous pouvez utiliser  pour créer le complément VSTO et au niveau du document personnalisations pour les applications Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="cc100-103">You can use to create VSTO Add-in and document-level customizations for Microsoft Office applications.</span></span> <span data-ttu-id="cc100-104">Pour plus d’informations sur ces types de projets, consultez [présentation du développement de Solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).</span><span class="sxs-lookup"><span data-stu-id="cc100-104">For more information about these types of projects, see [Office Solutions Development Overview &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).</span></span>  
  
   
  
   
  
### <a name="to-create-a-vsto-add-in-project"></a><span data-ttu-id="cc100-105">Pour créer un projet de complément VSTO</span><span class="sxs-lookup"><span data-stu-id="cc100-105">To create a VSTO Add-in project</span></span>  
  
1.  <span data-ttu-id="cc100-106">Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="cc100-106">On the **File** menu, choose **New**, **Project**.</span></span> <span data-ttu-id="cc100-107">Si votre environnement de développement intégré (IDE) est définie pour utiliser  des paramètres de développement, dans le **fichier** menu, choisissez **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="cc100-107">If your integrated development environment (IDE) is set to use development settings, on the **File** menu, choose **New**, **Project**.</span></span>  
  
     <span data-ttu-id="cc100-108">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cc100-108">The **New Project** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-109">Par défaut, les projets Office ciblent le .</span><span class="sxs-lookup"><span data-stu-id="cc100-109">Office projects target the  by default.</span></span> <span data-ttu-id="cc100-110">Pour plus d’informations, consultez [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).</span><span class="sxs-lookup"><span data-stu-id="cc100-110">For more information, see [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).</span></span>  
  
2.  <span data-ttu-id="cc100-111">Dans le volet Modèles, sous le nœud correspondant à la langue que vous souhaitez utiliser, développez **Office/SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="cc100-111">In the templates pane, under the node for the language you want to use, expand **Office/SharePoint**.</span></span>  
  
3.  <span data-ttu-id="cc100-112">Choisissez le **compléments Office** nœud.</span><span class="sxs-lookup"><span data-stu-id="cc100-112">Choose the **Office Add-ins** node.</span></span>  
  
4.  <span data-ttu-id="cc100-113">Dans la liste des modèles de projet, sélectionnez un modèle de projet de complément VSTO.</span><span class="sxs-lookup"><span data-stu-id="cc100-113">In the list of project templates, select a VSTO Add-in project template.</span></span> <span data-ttu-id="cc100-114">Pour obtenir la liste des modèles de projet disponibles complément VSTO, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc100-114">For a list of available VSTO Add-in project templates, see [Office Project Templates Overview](../vsto/office-project-templates-overview.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-115">Si les modèles de projet ne sont pas visibles quand vous sélectionnez le **compléments Office** nœud, vérifiez que **.NET Framework 4** ou version ultérieure est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="cc100-115">If project templates are not visible when you select the **Office Add-ins** node, make sure that **.NET Framework 4** or later is selected in the combo box at the top of the dialog box.</span></span> <span data-ttu-id="cc100-116">Les modèles de projet Office sont visibles pour les deux versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc100-116">Office project templates are visible for both versions of the .NET Framework.</span></span>  
  
5.  <span data-ttu-id="cc100-117">Dans le **nom** , tapez un nom pour le projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-117">In the **Name** box, type a name for the project.</span></span> <span data-ttu-id="cc100-118">Par défaut, le nom du projet est également utilisé comme nom de solution.</span><span class="sxs-lookup"><span data-stu-id="cc100-118">By default, the project name is also used as the solution name.</span></span>  
  
6.  <span data-ttu-id="cc100-119">Dans le **emplacement** , entrez le chemin d’accès où vous souhaitez créer le projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-119">In the **Location** box, enter the path where you want to create the project.</span></span> <span data-ttu-id="cc100-120">Vous pouvez utiliser des chemins d’accès UNC absolus et universels.</span><span class="sxs-lookup"><span data-stu-id="cc100-120">You can use absolute and universal naming convention (UNC) paths.</span></span> <span data-ttu-id="cc100-121">N’utilisez pas HTTP, FTP ni d’autres chemins d’accès de protocole.</span><span class="sxs-lookup"><span data-stu-id="cc100-121">Do not use HTTP, FTP, or other protocol paths.</span></span>  
  
     <span data-ttu-id="cc100-122">Les emplacements ont les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="cc100-122">Locations have the following formats:</span></span>  
  
    -   [*lecteur*\]: \\
[*drive*\]:\\  
  
    -   <span data-ttu-id="cc100-124">\\\\*Serveur*\\*partage*</span><span class="sxs-lookup"><span data-stu-id="cc100-124">\\\\*Server*\\*Share*</span></span>  
  
     <span data-ttu-id="cc100-125">N'utilisez pas les caractères suivants dans l'emplacement :</span><span class="sxs-lookup"><span data-stu-id="cc100-125">Do not use these characters in the location:</span></span>  
  
    -   <span data-ttu-id="cc100-126">astérisque (\*)</span><span class="sxs-lookup"><span data-stu-id="cc100-126">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="cc100-127">barre verticale (|)</span><span class="sxs-lookup"><span data-stu-id="cc100-127">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="cc100-128">deux-points (:) (sauf après la lettre de lecteur)</span><span class="sxs-lookup"><span data-stu-id="cc100-128">Colon (:) (Except following the drive letter.)</span></span>  
  
    -   <span data-ttu-id="cc100-129">guillemet double (") (les chemins d’accès qui contiennent des espaces n’ont pas besoin de guillemets.)</span><span class="sxs-lookup"><span data-stu-id="cc100-129">Double quotation mark (") (Paths that contain spaces do not need quotation marks.)</span></span>  
  
    -   <span data-ttu-id="cc100-130">Inférieur à (\<)</span><span class="sxs-lookup"><span data-stu-id="cc100-130">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="cc100-131">Supérieur à (>)</span><span class="sxs-lookup"><span data-stu-id="cc100-131">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="cc100-132">point d'interrogation (?)</span><span class="sxs-lookup"><span data-stu-id="cc100-132">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="cc100-133">pourcentage (%)</span><span class="sxs-lookup"><span data-stu-id="cc100-133">Percent sign (%)</span></span>  
  
7.  <span data-ttu-id="cc100-134">Sélectionnez le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="cc100-134">Choose the **OK** button.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-135">Les projets de complément sont toujours enregistrés quand ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="cc100-135">Add-in projects are always saved when they are created.</span></span> <span data-ttu-id="cc100-136">Ils ne peuvent pas être créés en tant que projets temporaires.</span><span class="sxs-lookup"><span data-stu-id="cc100-136">They cannot be created as temporary projects.</span></span> <span data-ttu-id="cc100-137">Pour plus d’informations sur les projets temporaires, consultez [projets temporaires](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).</span><span class="sxs-lookup"><span data-stu-id="cc100-137">For more information about temporary projects, see [Temporary Projects](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).</span></span>  
  
### <a name="to-create-a-document-level-customization-project"></a><span data-ttu-id="cc100-138">Pour créer un projet de personnalisation au niveau du document</span><span class="sxs-lookup"><span data-stu-id="cc100-138">To create a document-level customization project</span></span>  
  
1.  <span data-ttu-id="cc100-139">Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="cc100-139">On the **File** menu, choose **New**, **Project**.</span></span> <span data-ttu-id="cc100-140">Si votre interface IDE est définie pour utiliser des paramètres de développement Visual Basic, sur le **fichier** menu, choisissez **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="cc100-140">If your IDE is set to use Visual Basic development settings, on the **File** menu, choose **New**, **Project**.</span></span>  
  
     <span data-ttu-id="cc100-141">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cc100-141">The **New Project** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-142">Par défaut, les projets Office ciblent le .</span><span class="sxs-lookup"><span data-stu-id="cc100-142">Office projects target the  by default.</span></span>  <span data-ttu-id="cc100-143">Pour plus d’informations, consultez [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).</span><span class="sxs-lookup"><span data-stu-id="cc100-143">For more information, see [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).</span></span>  
  
2.  <span data-ttu-id="cc100-144">Dans le volet Modèles, sous le nœud correspondant à la langue que vous souhaitez utiliser, développez **Office/SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="cc100-144">In the templates pane, under the node for the language you want to use, expand **Office/SharePoint**.</span></span>  
  
3.  <span data-ttu-id="cc100-145">Sélectionnez le nœud **Compléments Office** .</span><span class="sxs-lookup"><span data-stu-id="cc100-145">Select the **Office Add-ins** node.</span></span>  
  
4.  <span data-ttu-id="cc100-146">Dans la liste des modèles de projet, sélectionnez un modèle de projet au niveau du document.</span><span class="sxs-lookup"><span data-stu-id="cc100-146">In the list of project templates, select a document-level project template.</span></span> <span data-ttu-id="cc100-147">Pour obtenir la liste des modèles de projet au niveau du document disponibles, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc100-147">For a list of available document-level project templates, see [Office Project Templates Overview](../vsto/office-project-templates-overview.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-148">Si les modèles de projet ne sont pas visibles quand vous sélectionnez le **compléments Office** nœud, vérifiez que **.NET Framework 4** ou version ultérieure est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="cc100-148">If project templates are not visible when you select the **Office Add-ins** node, make sure that **.NET Framework 4** or later is selected in the combo box at the top of the dialog box.</span></span> <span data-ttu-id="cc100-149">Les modèles de projet Office sont visibles pour les deux versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc100-149">Office project templates are visible for both versions of the .NET Framework.</span></span>  
  
5.  <span data-ttu-id="cc100-150">Dans le **nom** , tapez un nom pour le projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-150">In the **Name** box, type a name for the project.</span></span> <span data-ttu-id="cc100-151">Par défaut, ce nom est également utilisé pour le document.</span><span class="sxs-lookup"><span data-stu-id="cc100-151">By default, this name is also used for the document.</span></span> <span data-ttu-id="cc100-152">Si votre interface IDE est configurée pour utiliser des paramètres de développement Visual C# ou des paramètres de développement généraux, entrez également un emplacement et un nom de solution.</span><span class="sxs-lookup"><span data-stu-id="cc100-152">If your IDE is set to use Visual C# development settings or General development settings, also enter a location and solution name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-153">Vous ne pouvez pas utiliser de caractères de substitution dans le chemin d’accès à l’emplacement du projet ou dans le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-153">You cannot use surrogate characters in the path of the project location or in the project name.</span></span> <span data-ttu-id="cc100-154">En outre, si vous envisagez de déployer la solution pour une utilisation en mode hors connexion, les caractères du nom du projet doivent respecter les spécifications du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc100-154">Also, if you plan to deploy the solution for use offline, the characters in the project name must fit the HTTP protocol specifications.</span></span>  
  
6.  <span data-ttu-id="cc100-155">Sélectionnez le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="cc100-155">Choose the **OK** button.</span></span>  
  
     <span data-ttu-id="cc100-156">L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="cc100-156">The **Visual Studio Tools for Office Project Wizard** opens.</span></span>  
  
7.  <span data-ttu-id="cc100-157">Sélectionnez **créer un nouveau document** si vous souhaitez créer un document de la solution, ou sélectionnez **copier un document existant** si vous souhaitez personnaliser un document existant.</span><span class="sxs-lookup"><span data-stu-id="cc100-157">Select **Create a new document** if you want to create a new document for the solution, or select **Copy an existing document** if you want to customize an existing document.</span></span>  
  
     <span data-ttu-id="cc100-158">Si vous créez un nouveau document, spécifiez le nom de la **nom** zone, puis sélectionnez le format du document à l’aide de la **Format** boîte.</span><span class="sxs-lookup"><span data-stu-id="cc100-158">If you create a new document, specify the name in the **Name** box and select the format of the document by using the **Format** box.</span></span> <span data-ttu-id="cc100-159">Pour plus d’informations sur les formats disponibles, consultez [Architecture des personnalisations de niveau Document](../vsto/architecture-of-document-level-customizations.md).</span><span class="sxs-lookup"><span data-stu-id="cc100-159">For more information about the available formats, see [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md).</span></span>  
  
     <span data-ttu-id="cc100-160">Si vous utilisez un document existant, spécifiez l’emplacement du document dans le **chemin d’accès complet du document existant** boîte.</span><span class="sxs-lookup"><span data-stu-id="cc100-160">If you use an existing document, specify the location of the document in the **Full path of the existing document** box.</span></span> <span data-ttu-id="cc100-161">Vous pouvez utiliser des chemins d’accès absolus ou UNC.</span><span class="sxs-lookup"><span data-stu-id="cc100-161">You can use absolute and UNC paths.</span></span> <span data-ttu-id="cc100-162">N’utilisez aucun chemin d’accès de protocole, notamment HTTP ou FTP, vers le document.</span><span class="sxs-lookup"><span data-stu-id="cc100-162">Do not use HTTP, FTP, or other protocol paths to the document.</span></span>  
  
     <span data-ttu-id="cc100-163">Les emplacements ont les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="cc100-163">Locations have the following formats:</span></span>  
  
    -   [*lecteur*\]: \\
[*drive*\]:\\  
  
    -   <span data-ttu-id="cc100-165">\\\\*Serveur*\\*partage*</span><span class="sxs-lookup"><span data-stu-id="cc100-165">\\\\*Server*\\*Share*</span></span>  
  
     <span data-ttu-id="cc100-166">N'utilisez pas les caractères suivants dans l'emplacement :</span><span class="sxs-lookup"><span data-stu-id="cc100-166">Do not use these characters in the location:</span></span>  
  
    -   <span data-ttu-id="cc100-167">astérisque (\*)</span><span class="sxs-lookup"><span data-stu-id="cc100-167">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="cc100-168">barre verticale (|)</span><span class="sxs-lookup"><span data-stu-id="cc100-168">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="cc100-169">deux-points (:) (sauf après la lettre de lecteur)</span><span class="sxs-lookup"><span data-stu-id="cc100-169">Colon (:) (Except following the drive letter.)</span></span>  
  
    -   <span data-ttu-id="cc100-170">guillemet double (") (les chemins d’accès qui contiennent des espaces n’ont pas besoin de guillemets.)</span><span class="sxs-lookup"><span data-stu-id="cc100-170">Double quotation mark (") (Paths that contain spaces do not need quotation marks.)</span></span>  
  
    -   <span data-ttu-id="cc100-171">Inférieur à (\<)</span><span class="sxs-lookup"><span data-stu-id="cc100-171">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="cc100-172">Supérieur à (>)</span><span class="sxs-lookup"><span data-stu-id="cc100-172">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="cc100-173">point d'interrogation (?)</span><span class="sxs-lookup"><span data-stu-id="cc100-173">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="cc100-174">pourcentage (%)</span><span class="sxs-lookup"><span data-stu-id="cc100-174">Percent sign (%)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc100-175">Si vous utilisez un document existant dans un projet , utilisez uniquement des documents qui ont été créés ou convertis dans .</span><span class="sxs-lookup"><span data-stu-id="cc100-175">If you use an existing document in a  project, only use documents that were created in or converted to .</span></span> <span data-ttu-id="cc100-176">De même, si vous utilisez un document existant dans un projet Word 2010, utilisez uniquement des documents qui ont été créés dans Word 2010 ou convertis dans ce format.</span><span class="sxs-lookup"><span data-stu-id="cc100-176">Similarly, if you use an existing document in a Word 2010 project, only use documents that were created in or converted to Word 2010.</span></span> <span data-ttu-id="cc100-177">Certaines fonctionnalités seront désactivées dans le document si celui-ci a été créé dans une version antérieure de Word.</span><span class="sxs-lookup"><span data-stu-id="cc100-177">Certain features will be disabled in the document if you use a document that was created in an earlier version of Word.</span></span> <span data-ttu-id="cc100-178">Si vous tentez d’écrire du code qui utilise ces fonctionnalités, vous pouvez rencontrer des erreurs dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-178">If you try to write code that uses these features, you might encounter errors in your project.</span></span> <span data-ttu-id="cc100-179">Pour convertir un document, ouvrez-le dans  ou Word 2010, sur le **fichier** onglet sur le ruban, choisissez **Info**, **convertir**.</span><span class="sxs-lookup"><span data-stu-id="cc100-179">To convert a document, open it in  or Word 2010, on the **File** tab on the ribbon, choose **Info**, **Convert**.</span></span>  
  
8.  <span data-ttu-id="cc100-180">Choisissez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="cc100-180">Choose **Finish**.</span></span>  
  z
9. <span data-ttu-id="cc100-181">Ajoutez le dossier du projet et ses sous-dossiers à la liste d’emplacements approuvés dans le Centre de gestion de la confidentialité dans Word, dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="cc100-181">Add the project folder and its subfolders to the list of trusted locations in the Trust Center in Word in the following cases:</span></span>  
  
    -   <span data-ttu-id="cc100-182">Vous créez un document Word basé sur un fichier .docm, et le document contient un projet VBA ou héberge des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cc100-182">You are creating a Word Document that is based on a .docm file, and the document contains a VBA project or hosts Windows Forms controls.</span></span> <span data-ttu-id="cc100-183">L'ajout du dossier du projet à la liste d'emplacements approuvés aidera à s'assurer que le document fonctionne comme prévu au moment du design.</span><span class="sxs-lookup"><span data-stu-id="cc100-183">Adding the project folder to the list of trusted locations will help make sure that the document works as expected at design time.</span></span>  
  
    -   <span data-ttu-id="cc100-184">Vous créez un projet de modèle basé sur un fichier .dotx.</span><span class="sxs-lookup"><span data-stu-id="cc100-184">You are creating a Word Template project that is based on a .dotx file.</span></span> <span data-ttu-id="cc100-185">Vous devez ajouter le dossier du projet à la liste d’emplacements approuvés afin de pouvoir exécuter et déboguer le projet.</span><span class="sxs-lookup"><span data-stu-id="cc100-185">You must add the project folder to the list of trusted locations so that you can run and debug the project.</span></span>  
  
     <span data-ttu-id="cc100-186">Pour plus d’informations sur l’ajout d’un document aux emplacements approuvés, consultez le site web Microsoft Office Online [créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).</span><span class="sxs-lookup"><span data-stu-id="cc100-186">For more information on how to add a document to the trusted locations, see the Microsoft Office Online web site [Create, remove, or change a trusted location for your files](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc100-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc100-187">See Also</span></span>  
 <span data-ttu-id="cc100-188">[Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md) </span><span class="sxs-lookup"><span data-stu-id="cc100-188">[Office Project Templates Overview](../vsto/office-project-templates-overview.md) </span></span>  
 <span data-ttu-id="cc100-189">[Développement collaboratif de Solutions Office](../vsto/collaborative-development-of-office-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="cc100-189">[Collaborative Development of Office Solutions](../vsto/collaborative-development-of-office-solutions.md) </span></span>  
 <span data-ttu-id="cc100-190">[Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="cc100-190">[Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md) </span></span>  
 [<span data-ttu-id="cc100-191">Bien démarrer avec la programmation des compléments VSTO</span><span class="sxs-lookup"><span data-stu-id="cc100-191">Getting Started Programming VSTO Add-ins</span></span>](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
