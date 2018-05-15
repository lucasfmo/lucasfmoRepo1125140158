---
title: 'Erreur : Le processus cible s’est arrêté lors de l’évaluation de la fonction &#39;fonction&#39; | Documents Microsoft'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: reference
f1_keywords:
- vs.debug.error.process_exit_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8dd6f0f47eb7160198d59e788096613da85e22f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-target-process-exited-while-evaluating-the-function-39function39"></a><span data-ttu-id="003dc-102">Erreur : Le processus cible s’est arrêté lors de l’évaluation de la fonction &#39;(fonction)&#39;</span><span class="sxs-lookup"><span data-stu-id="003dc-102">Error: The target process exited while evaluating the function &#39;function&#39;</span></span>

<span data-ttu-id="003dc-103">Texte du message complet : le processus cible s’est arrêté lors de l’évaluation de la fonction 'fonction'.</span><span class="sxs-lookup"><span data-stu-id="003dc-103">Full message text: The target process exited while evaluating the function 'function'.</span></span> <span data-ttu-id="003dc-104">Consultez la fenêtre Sortie pour le code de sortie du processus cible.</span><span class="sxs-lookup"><span data-stu-id="003dc-104">See the Output window for the target process' exit code.</span></span>

<span data-ttu-id="003dc-105">Pour faciliter l’inspecter l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et `ToString` fonctions).</span><span class="sxs-lookup"><span data-stu-id="003dc-105">To make it easier to inspect the state of .NET objects, the debugger will automatically force the debugged process to run additional code (typically property getter methods and `ToString` functions).</span></span> <span data-ttu-id="003dc-106">Dans la plupart des scénarios, ces fonctions terminent correctement ou lever des exceptions qui peuvent être interceptées par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="003dc-106">In most scenarios, these functions complete successfully or throw exceptions that can be caught by the debugger.</span></span> <span data-ttu-id="003dc-107">Toutefois, il existe certains cas dans lequel les exceptions ne peuvent pas être interceptées, car elles franchissent les limites de noyau, nécessitent le pompage de messages utilisateur ou sont irrécupérables.</span><span class="sxs-lookup"><span data-stu-id="003dc-107">However, there are some circumstances in which exceptions cannot be caught because they cross kernel boundaries, require user message pumping, or are unrecoverable.</span></span> <span data-ttu-id="003dc-108">Un résultat, un accesseur Get de propriété ou la méthode ToString qui exécute le code qui soit explicitement met fin au processus (par exemple, appelle `ExitProcess()`) ou lève une exception non gérée ne peut pas être interceptée (par exemple, `StackOverflowException`) mettra fin à la processus débogué et fin de la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="003dc-108">As a result, a property getter or ToString method that executes code that either explicitly terminates the process (for example, calls `ExitProcess()`) or throws an unhandled exception that cannot be caught (for example, `StackOverflowException`) will terminate the debugged process and end the debug session.</span></span> <span data-ttu-id="003dc-109">Si vous rencontrez ce message d’erreur, cela s’est produite.</span><span class="sxs-lookup"><span data-stu-id="003dc-109">If you encounter this error message, this has occurred.</span></span>
 
<span data-ttu-id="003dc-110">Une des raisons courantes de ce problème sont que lorsque le débogueur évalue une propriété qui s’appelle elle-même, cela peut entraîner une exception de dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="003dc-110">One common reason for this problem is that when the debugger evaluates a property that calls itself, this may result in a stack overflow exception.</span></span> <span data-ttu-id="003dc-111">L’exception de dépassement de capacité de pile ne peuvent pas être récupérée et que le processus cible va se terminer.</span><span class="sxs-lookup"><span data-stu-id="003dc-111">The stack overflow exception cannot be recovered and the target process will terminate.</span></span>
 
## <a name="to-correct-this-error"></a><span data-ttu-id="003dc-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="003dc-112">To correct this error</span></span>
 
<span data-ttu-id="003dc-113">Il existe deux solutions possibles à ce problème.</span><span class="sxs-lookup"><span data-stu-id="003dc-113">There are two possible solutions to this issue.</span></span>
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a><span data-ttu-id="003dc-114">Solution #1 : Empêcher le débogueur à partir de l’appel de la propriété d’accesseur Get ou la méthode ToString</span><span class="sxs-lookup"><span data-stu-id="003dc-114">Solution #1: Prevent the debugger from calling the getter property or ToString method</span></span> 

<span data-ttu-id="003dc-115">Le message d’erreur vous indique le nom de la fonction que le débogueur a essayé d’appeler.</span><span class="sxs-lookup"><span data-stu-id="003dc-115">The error message will tell you the name of the function that the debugger tried to call.</span></span> <span data-ttu-id="003dc-116">Avec le nom de la fonction, vous pouvez essayer de réévaluer cette fonction à partir de la **exécution** fenêtre pour déboguer l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="003dc-116">With the name of the function, you can try re-evaluating that function from the **Immediate** window to debug the evaluation.</span></span> <span data-ttu-id="003dc-117">Le débogage est possible lors de l’évaluation de la **immédiat** fenêtre car, contrairement aux évaluations implicites à partir de la **automatique/variables locales/espion** windows, le débogueur s’arrête sur les exceptions non gérées.</span><span class="sxs-lookup"><span data-stu-id="003dc-117">Debugging is possible when evaluating from the **Immediate** window because, unlike implicit evaluations from the **Autos/Locals/Watch** windows, the debugger breaks on unhandled exceptions.</span></span>

<span data-ttu-id="003dc-118">Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur de l’appel de l’accesseur Get de propriété ou `ToString` (méthode).</span><span class="sxs-lookup"><span data-stu-id="003dc-118">If you can modify this function, you can prevent the debugger from calling the property getter or `ToString` method.</span></span> <span data-ttu-id="003dc-119">Essayez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="003dc-119">Try one of the following:</span></span>
 
* <span data-ttu-id="003dc-120">Modifier la méthode en un autre type de code en dehors d’un accesseur Get de propriété ou méthode ToString et le problème disparaîtra.</span><span class="sxs-lookup"><span data-stu-id="003dc-120">Change the method to some other type of code besides a property getter or ToString method and the problem will go away.</span></span>
    <span data-ttu-id="003dc-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="003dc-121">-or-</span></span>
* <span data-ttu-id="003dc-122">(Pour `ToString`) définir un `DebuggerDisplay` attribut sur le type et vous pouvez que le débogueur évaluer un élément autre que `ToString`.</span><span class="sxs-lookup"><span data-stu-id="003dc-122">(For `ToString`) Define a `DebuggerDisplay` attribute on the type and you can have the debugger evaluate something other than `ToString`.</span></span>
    <span data-ttu-id="003dc-123">- ou -</span><span class="sxs-lookup"><span data-stu-id="003dc-123">-or-</span></span>
* <span data-ttu-id="003dc-124">(Pour un accesseur Get de propriété) Placez le `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété.</span><span class="sxs-lookup"><span data-stu-id="003dc-124">(For a property getter) Put the `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribute on the property.</span></span> <span data-ttu-id="003dc-125">Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais il doit être réellement d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="003dc-125">This can be useful if you have a method that needs to remain a property for API compatibility reasons, but it should really be a method.</span></span>

<span data-ttu-id="003dc-126">Si vous ne pouvez pas modifier cette méthode, vous pourrez peut-être arrêter le processus cible à une autre instruction, puis réessayez de l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="003dc-126">If you cannot modify this method, you may be able to break the target process at an alternate instruction and retry the evaluation.</span></span>
 
### <a name="solution-2-disable-all-implicit-evaluation"></a><span data-ttu-id="003dc-127">Solution #2 : Désactiver tous les évaluation implicite</span><span class="sxs-lookup"><span data-stu-id="003dc-127">Solution #2: Disable all implicit evaluation</span></span>
 
<span data-ttu-id="003dc-128">Si les solutions précédentes ne résout le problème, accédez à **outils** > **Options**et désactivez le paramètre **débogage**  >   **Général** > **activer l’évaluation de la propriété et d’autres appels de fonction implicite**.</span><span class="sxs-lookup"><span data-stu-id="003dc-128">If the previous solutions don't fix the issue, go to **Tools** > **Options**, and uncheck the setting **Debugging** > **General** > **Enable property evaluation and other implicit function calls**.</span></span> <span data-ttu-id="003dc-129">Cela désactive la plupart des évaluations de fonction implicite et devrait résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="003dc-129">This will disable most implicit function evaluations and should resolve the issue.</span></span>



  
