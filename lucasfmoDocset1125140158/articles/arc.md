### YamlMime:Tutorial
title: <span data-ttu-id="556b9-101">Azure でサーバーレス Web アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="556b9-101">Build a serverless web app in Azure</span></span>
metadata:
  title: Azure でサーバーレス Web アプリを作成する | Microsoft Docs
  description: このチュートリアルでは、Azure のサーバーレス コンポーネントを使用して、画像をアップロード、分析、および変更する静的 Web アプリを発行する方法について説明します。
  audience: Developer
  level: Intermediate
  displayType: two-column
  interactive: azurecli
  author: ggailey777
  manager: cfowler
  ms.service: multiple
  ms.topic: interactive-tutorial
  ms.date: 06/22/2018
  ms.author: glenga
  ms.openlocfilehash: d0bd4c0b4b1a6995e2d5148a4f49769aee0f4dc7
  ms.sourcegitcommit: f96b5b10238122db9506f1a7c7f53ace9b28c293
  ms.translationtype: HT
  ms.contentlocale: ja-JP
  ms.lasthandoff: 08/24/2018
  ms.locfileid: "40079310"
items:
- durationInMinutes: 1
  content: >
    [!INCLUDE [](./includes/intro.md)]
- title: <span data-ttu-id="556b9-104">Azure Blob Storage で Web アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="556b9-104">Create a web app in Azure Blob storage</span></span>
  durationInMinutes: 12
  content: >
    [!INCLUDE [](./includes/static-site.md)]
- title: <span data-ttu-id="556b9-105">Azure Functions を使用して Blob Storage に画像をアップロードする</span><span class="sxs-lookup"><span data-stu-id="556b9-105">Upload images to Blob storage with Azure Functions</span></span>
  durationInMinutes: 20
  content: "[!INCLUDE [](./includes/upload-images.md)] \n"
- title: <span data-ttu-id="556b9-106">Azure Functions を使用して画像のサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="556b9-106">Resize images with Azure Functions</span></span>
  durationInMinutes: 15
  content: >
    [!INCLUDE [](includes/resize-images.md)]
- title: <span data-ttu-id="556b9-107">Azure Cosmos DB を使用して画像のメタデータを格納する</span><span class="sxs-lookup"><span data-stu-id="556b9-107">Store image metadata with Azure Cosmos DB</span></span>
  durationInMinutes: 15
  content: >
    [!INCLUDE [](includes/store-images.md)]
- title: <span data-ttu-id="556b9-108">Computer Vision を使用して画像のキャプションを追加する</span><span class="sxs-lookup"><span data-stu-id="556b9-108">Add image captions with Computer Vision</span></span>
  durationInMinutes: 15
  content: >
    [!INCLUDE [](includes/computer-vision.md)]
- title: <span data-ttu-id="556b9-109">認証を追加する</span><span class="sxs-lookup"><span data-stu-id="556b9-109">Add authentication</span></span>
  durationInMinutes: 15
  content: >
    [!INCLUDE [](includes/authentication.md)]
- content: '[!INCLUDE [](includes/completed.md)]'
