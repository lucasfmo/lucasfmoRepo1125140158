---
title: Azure Monitor 中的 Azure Active Directory 活动日志（预览版）| Microsoft Docs
description: Azure Monitor 中的 Azure Active Directory 活动日志（预览版）概述
services: active-directory
documentationcenter: ''
author: priyamohanram
manager: mtillman
editor: ''
ms.assetid: 4b18127b-d1d0-4bdc-8f9c-6a4c991c5f75
ms.service: active-directory
ms.devlang: na
ms.topic: concept
ms.tgt_pltfrm: na
ms.workload: identity
ms.component: report-monitor
ms.date: 07/13/2018
ms.author: priyamo
ms.reviewer: dhanyahk
ms.openlocfilehash: 0c59cac666dec00e02f21ba20c0608b6b8142ba4
ms.sourcegitcommit: 1b561b77aa080416b094b6f41fce5b6a4721e7d5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45740642"
---
# <a name="azure-ad-activity-logs-in-azure-monitor-preview"></a><span data-ttu-id="0849a-103">Azure Monitor 中的 Azure AD 活动日志（预览版）</span><span class="sxs-lookup"><span data-stu-id="0849a-103">Azure AD activity logs in Azure Monitor (preview)</span></span>

<span data-ttu-id="0849a-104">现在可以使用 Azure Monitor 将 Azure Active Directory (Azure AD) 活动日志路由到你自己的存储帐户或事件中心。</span><span class="sxs-lookup"><span data-stu-id="0849a-104">You can now route Azure Active Directory (Azure AD) activity logs to your own storage account or event hub by using Azure Monitor.</span></span> <span data-ttu-id="0849a-105">Azure Monitor 中的 Azure Active Directory 日志的公共预览版提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="0849a-105">With the public preview of Azure Active Directory logs in Azure Monitor, you can:</span></span>

* <span data-ttu-id="0849a-106">将 Azure 存储帐户的审核日志存档，以便长期保留数据。</span><span class="sxs-lookup"><span data-stu-id="0849a-106">Archive your audit logs for an Azure storage account, which enables you to retain the data for a long time.</span></span>
* <span data-ttu-id="0849a-107">使用常用的安全信息和事件管理 (SIEM) 工具（例如 Splunk 和 QRadar）将审核日志流式传输到 Azure 事件中心进行分析。</span><span class="sxs-lookup"><span data-stu-id="0849a-107">Stream your audit logs to an Azure event hub for analytics by using popular Security Information and Event Management (SIEM) tools, such as Splunk and QRadar.</span></span>
* <span data-ttu-id="0849a-108">将审核日志流式传输到事件中心，以便与自定义日志解决方案集成。</span><span class="sxs-lookup"><span data-stu-id="0849a-108">Integrate your audit logs with your own custom log solutions by streaming them to an event hub.</span></span>

> [!VIDEO https://www.youtube.com/embed/syT-9KNfug8]

## <a name="supported-reports"></a><span data-ttu-id="0849a-109">支持的报表</span><span class="sxs-lookup"><span data-stu-id="0849a-109">Supported reports</span></span>

<span data-ttu-id="0849a-110">可以使用此功能将审核活动日志和登录活动日志路由到 Azure 存储帐户、事件中心或自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="0849a-110">You can route audit activity logs and sign-in activity logs to your Azure storage account, event hub, or custom solution by using this feature.</span></span> 

* <span data-ttu-id="0849a-111">**审核日志**： 可以通过[审核日志活动报表](concept-audit-logs.md)访问在租户中执行的每个任务的历史记录。</span><span class="sxs-lookup"><span data-stu-id="0849a-111">**Audit logs**: The [audit logs activity report](concept-audit-logs.md) gives you access to the history of every task that's performed in your tenant.</span></span>
* <span data-ttu-id="0849a-112">**登录日志**： 可以通过[登录活动报表](concept-sign-ins.md)来确定谁执行了审核日志中报告的任务。</span><span class="sxs-lookup"><span data-stu-id="0849a-112">**Sign-in logs**: With the [sign-in activity report](concept-sign-ins.md), you can determine who performed the tasks that are reported in the audit logs.</span></span>

> [!NOTE]
> <span data-ttu-id="0849a-113">目前不支持 B2C 相关的审核和登录活动日志。</span><span class="sxs-lookup"><span data-stu-id="0849a-113">B2C-related audit and sign-in activity logs are not supported at this time.</span></span>
>

## <a name="prerequisites"></a><span data-ttu-id="0849a-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="0849a-114">Prerequisites</span></span>

<span data-ttu-id="0849a-115">若要使用此功能，需满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="0849a-115">To use this feature, you need:</span></span>

* <span data-ttu-id="0849a-116">Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="0849a-116">An Azure subscription.</span></span> <span data-ttu-id="0849a-117">如果没有 Azure 订阅，可以[注册免费试用版](https://azure.microsoft.com/free/)。</span><span class="sxs-lookup"><span data-stu-id="0849a-117">If you don't have an Azure subscription, you can [sign up for a free trial](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="0849a-118">在 Azure 门户中访问 Azure AD 审核日志所需的 Azure AD Free、Basic、Premium 1 或 Premium 2 [许可证](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="0849a-118">Azure AD Free, Basic, Premium 1, or Premium 2 [license](https://azure.microsoft.com/pricing/details/active-directory/), to access the Azure AD audit logs in the Azure portal.</span></span> 
* <span data-ttu-id="0849a-119">在 Azure 门户中访问 Azure AD 登录日志所需的 Azure AD Premium 1 或 Premium 2 [许可证](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="0849a-119">Azure AD Premium 1, or Premium 2 [license](https://azure.microsoft.com/pricing/details/active-directory/), to access the Azure AD sign-in logs in the Azure portal.</span></span> 

<span data-ttu-id="0849a-120">根据审核日志数据要路由到的位置，需满足以下条件之一：</span><span class="sxs-lookup"><span data-stu-id="0849a-120">Depending on where you want to route the audit log data, you need either of the following:</span></span>

* <span data-ttu-id="0849a-121">你对其拥有 *ListKeys* 权限的 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="0849a-121">An Azure storage account that you have *ListKeys* permissions for.</span></span> <span data-ttu-id="0849a-122">建议使用常规存储帐户而非 Blob 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="0849a-122">We recommend that you use a general storage account and not a Blob storage account.</span></span> <span data-ttu-id="0849a-123">有关存储定价信息，请查看 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/calculator/?service=storage)。</span><span class="sxs-lookup"><span data-stu-id="0849a-123">For storage pricing information, see the [Azure Storage pricing calculator](https://azure.microsoft.com/pricing/calculator/?service=storage).</span></span> 
* <span data-ttu-id="0849a-124">用于与第三方解决方案集成的 Azure 事件中心命名空间。</span><span class="sxs-lookup"><span data-stu-id="0849a-124">An Azure Event Hubs namespace to integrate with third-party solutions.</span></span>

> [!NOTE]
> <span data-ttu-id="0849a-125">必须是 Azure AD 租户中的全局管理员或安全管理员才能访问 Azure AD 活动日志。</span><span class="sxs-lookup"><span data-stu-id="0849a-125">To access the Azure AD activity logs, you need to be a *global administrator* or *security administrator* in the Azure AD tenant.</span></span>
>

## <a name="cost-considerations"></a><span data-ttu-id="0849a-126">成本注意事项</span><span class="sxs-lookup"><span data-stu-id="0849a-126">Cost considerations</span></span>

<span data-ttu-id="0849a-127">如果已经有 Azure AD 许可证，则还需要一个 Azure 订阅才能设置存储帐户和事件中心。</span><span class="sxs-lookup"><span data-stu-id="0849a-127">If you already have an Azure AD license, you need an Azure subscription to set up the storage account and event hub.</span></span> <span data-ttu-id="0849a-128">Azure 订阅可以免费获取，但若要使用 Azure 资源（包括用于存档的存储帐户以及用于流式处理的事件中心），则需付费。</span><span class="sxs-lookup"><span data-stu-id="0849a-128">The Azure subscription comes at no cost, but you have to pay to utilize Azure resources, including the storage account that you use for archival and the event hub that you use for streaming.</span></span> <span data-ttu-id="0849a-129">数据量以及因此引发的费用可能因租户大小的不同而差异很大。</span><span class="sxs-lookup"><span data-stu-id="0849a-129">The amount of data and, thus, the cost incurred, can vary significantly depending on the tenant size.</span></span> 

### <a name="storage-size-for-activity-logs"></a><span data-ttu-id="0849a-130">用于活动日志的存储大小</span><span class="sxs-lookup"><span data-stu-id="0849a-130">Storage size for activity logs</span></span>

<span data-ttu-id="0849a-131">每个审核日志事件使用大约 2 KB 的数据存储。</span><span class="sxs-lookup"><span data-stu-id="0849a-131">Every audit log event uses about 2 KB of data storage.</span></span> <span data-ttu-id="0849a-132">如果一个租户有 100,000 个用户，每天会引发大约 150 万个事件，则每天需要大约 3 GB 的数据存储。</span><span class="sxs-lookup"><span data-stu-id="0849a-132">For a tenant with 100,000 users, which would incur about 1.5 million events per day, you would need about 3 GB of data storage per day.</span></span> <span data-ttu-id="0849a-133">由于写入时每批需要大约五分钟的时间，则可预计每月大约有 9,000 次写入操作。</span><span class="sxs-lookup"><span data-stu-id="0849a-133">Because writes occur in approximately five-minute batches, you can anticipate approximately 9,000 write operations per month.</span></span> 

<span data-ttu-id="0849a-134">下表包含的内容是根据租户大小进行的成本估算。这是一个常规用途的 v2 存储帐户，位于“美国西部”区域，保留期至少为一年。</span><span class="sxs-lookup"><span data-stu-id="0849a-134">The following table contains a cost estimate of, depending on the size of the tenant, a general-purpose v2 storage account in West US for at least one year of retention.</span></span> <span data-ttu-id="0849a-135">若要针对应用程序的预期数据量进行更准确的估算，请使用 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/details/storage/blobs/)。</span><span class="sxs-lookup"><span data-stu-id="0849a-135">To create a more accurate estimate for the data volume that you anticipate for your application, use the [Azure storage pricing calculator](https://azure.microsoft.com/pricing/details/storage/blobs/).</span></span> 

| <span data-ttu-id="0849a-136">日志类别</span><span class="sxs-lookup"><span data-stu-id="0849a-136">Log category</span></span> | <span data-ttu-id="0849a-137">用户数</span><span class="sxs-lookup"><span data-stu-id="0849a-137">Number of users</span></span> | <span data-ttu-id="0849a-138">每日事件数</span><span class="sxs-lookup"><span data-stu-id="0849a-138">Events per day</span></span> | <span data-ttu-id="0849a-139">每月数据量（估算）</span><span class="sxs-lookup"><span data-stu-id="0849a-139">Volume of data per month (est.)</span></span> | <span data-ttu-id="0849a-140">每月成本（估算）</span><span class="sxs-lookup"><span data-stu-id="0849a-140">Cost per month (est.)</span></span> | <span data-ttu-id="0849a-141">每年成本（估算）</span><span class="sxs-lookup"><span data-stu-id="0849a-141">Cost per year (est.)</span></span> |
|--------------|-----------------|----------------------|--------------------------------------|----------------------------|---------------------------|
| <span data-ttu-id="0849a-142">审核</span><span class="sxs-lookup"><span data-stu-id="0849a-142">Audit</span></span> | <span data-ttu-id="0849a-143">100,000</span><span class="sxs-lookup"><span data-stu-id="0849a-143">100,000</span></span> | <span data-ttu-id="0849a-144">150&nbsp;万</span><span class="sxs-lookup"><span data-stu-id="0849a-144">1.5&nbsp;million</span></span> | <span data-ttu-id="0849a-145">90 GB</span><span class="sxs-lookup"><span data-stu-id="0849a-145">90 GB</span></span> | <span data-ttu-id="0849a-146">$1.93</span><span class="sxs-lookup"><span data-stu-id="0849a-146">$1.93</span></span> | <span data-ttu-id="0849a-147">$23.12</span><span class="sxs-lookup"><span data-stu-id="0849a-147">$23.12</span></span> |
| <span data-ttu-id="0849a-148">审核</span><span class="sxs-lookup"><span data-stu-id="0849a-148">Audit</span></span> | <span data-ttu-id="0849a-149">1,000</span><span class="sxs-lookup"><span data-stu-id="0849a-149">1,000</span></span> | <span data-ttu-id="0849a-150">15,000</span><span class="sxs-lookup"><span data-stu-id="0849a-150">15,000</span></span> | <span data-ttu-id="0849a-151">900 MB</span><span class="sxs-lookup"><span data-stu-id="0849a-151">900 MB</span></span> | <span data-ttu-id="0849a-152">$0.02</span><span class="sxs-lookup"><span data-stu-id="0849a-152">$0.02</span></span> | <span data-ttu-id="0849a-153">$0.24</span><span class="sxs-lookup"><span data-stu-id="0849a-153">$0.24</span></span> |
| <span data-ttu-id="0849a-154">登录</span><span class="sxs-lookup"><span data-stu-id="0849a-154">Sign-ins</span></span> | <span data-ttu-id="0849a-155">1,000</span><span class="sxs-lookup"><span data-stu-id="0849a-155">1,000</span></span> | <span data-ttu-id="0849a-156">34,800</span><span class="sxs-lookup"><span data-stu-id="0849a-156">34,800</span></span> | <span data-ttu-id="0849a-157">4 GB</span><span class="sxs-lookup"><span data-stu-id="0849a-157">4 GB</span></span> | <span data-ttu-id="0849a-158">$0.13</span><span class="sxs-lookup"><span data-stu-id="0849a-158">$0.13</span></span> | <span data-ttu-id="0849a-159">$1.56</span><span class="sxs-lookup"><span data-stu-id="0849a-159">$1.56</span></span> |
| <span data-ttu-id="0849a-160">登录</span><span class="sxs-lookup"><span data-stu-id="0849a-160">Sign-ins</span></span> | <span data-ttu-id="0849a-161">100,000</span><span class="sxs-lookup"><span data-stu-id="0849a-161">100,000</span></span> | <span data-ttu-id="0849a-162">1,500&nbsp;万</span><span class="sxs-lookup"><span data-stu-id="0849a-162">15&nbsp;million</span></span> | <span data-ttu-id="0849a-163">1.7 TB</span><span class="sxs-lookup"><span data-stu-id="0849a-163">1.7 TB</span></span> | <span data-ttu-id="0849a-164">$35.41</span><span class="sxs-lookup"><span data-stu-id="0849a-164">$35.41</span></span> | <span data-ttu-id="0849a-165">$424.92</span><span class="sxs-lookup"><span data-stu-id="0849a-165">$424.92</span></span> | 


### <a name="event-hub-messages-for-activity-logs"></a><span data-ttu-id="0849a-166">活动日志的事件中心消息</span><span class="sxs-lookup"><span data-stu-id="0849a-166">Event hub messages for activity logs</span></span>

<span data-ttu-id="0849a-167">事件按大约五分钟的时间间隔进行批处理，并以单条消息的形式发送，每条包含该时间范围内的所有事件。</span><span class="sxs-lookup"><span data-stu-id="0849a-167">Events are batched into approximately five-minute intervals and sent as a single message that contains all the events within that timeframe.</span></span> <span data-ttu-id="0849a-168">事件中心的消息的最大大小为 256 KB，如果该时间范围内所有消息的总大小超出该大小，则会发送多条消息。</span><span class="sxs-lookup"><span data-stu-id="0849a-168">A message in the event hub has a maximum size of 256 KB, and if the total size of all the messages within the timeframe exceeds that volume, multiple messages are sent.</span></span> 

<span data-ttu-id="0849a-169">例如，对于用户数超出 100,000 的大型租户来说，通常情况下每秒大约有 18 个事件，该频率相当于每五分钟 5,400 个事件。</span><span class="sxs-lookup"><span data-stu-id="0849a-169">For example, about 18 events per second ordinarily occur for a large tenant of more than 100,000 users, a rate that equates to 5,400 events every five minutes.</span></span> <span data-ttu-id="0849a-170">由于审核日志大约每个事件 2 KB，上述事件相当于 10.8 MB 的数据，</span><span class="sxs-lookup"><span data-stu-id="0849a-170">Because audit logs are about 2 KB per event, this equates to 10.8 MB of data.</span></span> <span data-ttu-id="0849a-171">因此会在五分钟的时间间隔内向事件中心发送 43 条消息。</span><span class="sxs-lookup"><span data-stu-id="0849a-171">Therefore, 43 messages are sent to the event hub in that five-minute interval.</span></span> 

<span data-ttu-id="0849a-172">下表包含的内容是根据事件数据的量对“美国西部”区域一个基本事件中心进行的每月成本估算。</span><span class="sxs-lookup"><span data-stu-id="0849a-172">The following table contains estimated costs per month for a basic event hub in West US, depending on the volume of event data.</span></span> <span data-ttu-id="0849a-173">若要针对应用程序的预期数据量进行准确的估算，请使用[事件中心定价计算器](https://azure.microsoft.com/pricing/details/event-hubs/)。</span><span class="sxs-lookup"><span data-stu-id="0849a-173">To calculate an accurate estimate of the data volume that you anticipate for your application, use the [Event Hubs pricing calculator](https://azure.microsoft.com/pricing/details/event-hubs/).</span></span>

| <span data-ttu-id="0849a-174">日志类别</span><span class="sxs-lookup"><span data-stu-id="0849a-174">Log category</span></span> | <span data-ttu-id="0849a-175">用户数</span><span class="sxs-lookup"><span data-stu-id="0849a-175">Number of users</span></span> | <span data-ttu-id="0849a-176">每秒事件数</span><span class="sxs-lookup"><span data-stu-id="0849a-176">Events per second</span></span> | <span data-ttu-id="0849a-177">每五分钟时间间隔的事件数</span><span class="sxs-lookup"><span data-stu-id="0849a-177">Events per five-minute interval</span></span> | <span data-ttu-id="0849a-178">每个时间间隔的数据量</span><span class="sxs-lookup"><span data-stu-id="0849a-178">Volume per interval</span></span> | <span data-ttu-id="0849a-179">每个时间间隔的消息数</span><span class="sxs-lookup"><span data-stu-id="0849a-179">Messages per interval</span></span> | <span data-ttu-id="0849a-180">每月消息数</span><span class="sxs-lookup"><span data-stu-id="0849a-180">Messages per month</span></span> | <span data-ttu-id="0849a-181">每月成本（估算）</span><span class="sxs-lookup"><span data-stu-id="0849a-181">Cost per month (est.)</span></span> |
|--------------|-----------------|-------------------------|----------------------------------------|---------------------|---------------------------------|------------------------------|----------------------------|
| <span data-ttu-id="0849a-182">审核</span><span class="sxs-lookup"><span data-stu-id="0849a-182">Audit</span></span> | <span data-ttu-id="0849a-183">100,000</span><span class="sxs-lookup"><span data-stu-id="0849a-183">100,000</span></span> | <span data-ttu-id="0849a-184">18</span><span class="sxs-lookup"><span data-stu-id="0849a-184">18</span></span> | <span data-ttu-id="0849a-185">5,400</span><span class="sxs-lookup"><span data-stu-id="0849a-185">5,400</span></span> | <span data-ttu-id="0849a-186">10.8 MB</span><span class="sxs-lookup"><span data-stu-id="0849a-186">10.8 MB</span></span> | <span data-ttu-id="0849a-187">43</span><span class="sxs-lookup"><span data-stu-id="0849a-187">43</span></span> | <span data-ttu-id="0849a-188">371,520</span><span class="sxs-lookup"><span data-stu-id="0849a-188">371,520</span></span> | <span data-ttu-id="0849a-189">$10.83</span><span class="sxs-lookup"><span data-stu-id="0849a-189">$10.83</span></span> |
| <span data-ttu-id="0849a-190">审核</span><span class="sxs-lookup"><span data-stu-id="0849a-190">Audit</span></span> | <span data-ttu-id="0849a-191">1,000</span><span class="sxs-lookup"><span data-stu-id="0849a-191">1,000</span></span> | <span data-ttu-id="0849a-192">0.1</span><span class="sxs-lookup"><span data-stu-id="0849a-192">0.1</span></span> | <span data-ttu-id="0849a-193">52</span><span class="sxs-lookup"><span data-stu-id="0849a-193">52</span></span> | <span data-ttu-id="0849a-194">104 KB</span><span class="sxs-lookup"><span data-stu-id="0849a-194">104 KB</span></span> | <span data-ttu-id="0849a-195">1</span><span class="sxs-lookup"><span data-stu-id="0849a-195">1</span></span> | <span data-ttu-id="0849a-196">8,640</span><span class="sxs-lookup"><span data-stu-id="0849a-196">8,640</span></span> | <span data-ttu-id="0849a-197">$10.80</span><span class="sxs-lookup"><span data-stu-id="0849a-197">$10.80</span></span> |
| <span data-ttu-id="0849a-198">登录</span><span class="sxs-lookup"><span data-stu-id="0849a-198">Sign-ins</span></span> | <span data-ttu-id="0849a-199">1,000</span><span class="sxs-lookup"><span data-stu-id="0849a-199">1,000</span></span> | <span data-ttu-id="0849a-200">178</span><span class="sxs-lookup"><span data-stu-id="0849a-200">178</span></span> | <span data-ttu-id="0849a-201">53,400</span><span class="sxs-lookup"><span data-stu-id="0849a-201">53,400</span></span> | <span data-ttu-id="0849a-202">106.8&nbsp;MB</span><span class="sxs-lookup"><span data-stu-id="0849a-202">106.8&nbsp;MB</span></span> | <span data-ttu-id="0849a-203">418</span><span class="sxs-lookup"><span data-stu-id="0849a-203">418</span></span> | <span data-ttu-id="0849a-204">3,611,520</span><span class="sxs-lookup"><span data-stu-id="0849a-204">3,611,520</span></span> | <span data-ttu-id="0849a-205">$11.06</span><span class="sxs-lookup"><span data-stu-id="0849a-205">$11.06</span></span> |  


## <a name="frequently-asked-questions"></a><span data-ttu-id="0849a-206">常见问题</span><span class="sxs-lookup"><span data-stu-id="0849a-206">Frequently asked questions</span></span>

<span data-ttu-id="0849a-207">此部分回答 Azure Monitor 中 Azure AD 日志的常见问题并讨论已知问题。</span><span class="sxs-lookup"><span data-stu-id="0849a-207">This section answers frequently asked questions and discusses known issues with Azure AD logs in Azure Monitor.</span></span>

<span data-ttu-id="0849a-208">**问：我应该从何处着手？**</span><span class="sxs-lookup"><span data-stu-id="0849a-208">**Q: Where should I start?**</span></span> 

<span data-ttu-id="0849a-209">**答**： 本文讨论部署此功能需要做哪些准备。</span><span class="sxs-lookup"><span data-stu-id="0849a-209">**A**: This article discusses what you need to deploy this feature.</span></span> <span data-ttu-id="0849a-210">符合先决条件以后，请查看各个教程，了解如何配置日志并将其路由到事件中心。</span><span class="sxs-lookup"><span data-stu-id="0849a-210">After you've satisfied the prerequisites, go to the tutorials that can help you configure and route your logs to an event hub.</span></span>


<span data-ttu-id="0849a-211">**问：哪些日志包括在其中？**</span><span class="sxs-lookup"><span data-stu-id="0849a-211">**Q: Which logs are included?**</span></span>

<span data-ttu-id="0849a-212">**答**： 登录活动日志和审核日志均可通过此功能进行路由，虽然与 B2C 相关的审核事件目前未包括在其中。</span><span class="sxs-lookup"><span data-stu-id="0849a-212">**A**: The sign-in activity logs and audit logs are both available for routing through this feature, although B2C-related audit events are currently not included.</span></span> <span data-ttu-id="0849a-213">若要了解目前支持哪些类型的日志和哪些基于功能的日志，请参阅[审核日志架构](reference-azure-monitor-audit-log-schema.md)和[登录日志架构](reference-azure-monitor-sign-ins-log-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="0849a-213">To find out which types of logs and which feature-based logs are currently supported, see [Audit log schema](reference-azure-monitor-audit-log-schema.md) and [Sign-in log schema](reference-azure-monitor-sign-ins-log-schema.md).</span></span> 



<span data-ttu-id="0849a-214">**问：执行某项操作之后，相应的日志多快会显示在事件中心？**</span><span class="sxs-lookup"><span data-stu-id="0849a-214">**Q: How soon after an action do the corresponding logs show up in event hubs?**</span></span>

<span data-ttu-id="0849a-215">**答**： 日志会在执行操作后两到五分钟内显示在事件中心。</span><span class="sxs-lookup"><span data-stu-id="0849a-215">**A**: The logs should show up in your event hub within two to five minutes after the action is performed.</span></span> <span data-ttu-id="0849a-216">有关事件中心的详细信息，请参阅[什么是 Azure 事件中心？](../../event-hubs/event-hubs-about.md)。</span><span class="sxs-lookup"><span data-stu-id="0849a-216">For more information about Event Hubs, see [What is Azure Event Hubs?](../../event-hubs/event-hubs-about.md).</span></span>


<span data-ttu-id="0849a-217">**问：执行某项操作之后，相应的日志多快会显示在存储帐户中？**</span><span class="sxs-lookup"><span data-stu-id="0849a-217">**Q: How soon after an action do the corresponding logs show up in storage accounts?**</span></span>

<span data-ttu-id="0849a-218">**答**： 就 Azure 存储帐户来说，执行操作之后，日志在其中的显示会有一个 5 到 15 分钟的延迟。</span><span class="sxs-lookup"><span data-stu-id="0849a-218">**A**: For Azure storage accounts, the latency is anywhere from 5 to 15 minutes after the action is performed.</span></span>


<span data-ttu-id="0849a-219">**问：存储数据的费用是多少？**</span><span class="sxs-lookup"><span data-stu-id="0849a-219">**Q: How much will it cost to store my data?**</span></span>

<span data-ttu-id="0849a-220">**答**： 存储费用取决于日志大小以及所选保留期。</span><span class="sxs-lookup"><span data-stu-id="0849a-220">**A**: The storage costs depend on both the size of your logs and the retention period you choose.</span></span> <span data-ttu-id="0849a-221">如需租户估算费用（取决于生成的日志量）的列表，请参阅[活动日志的存储大小](#storage-size-for-activity-logs)部分。</span><span class="sxs-lookup"><span data-stu-id="0849a-221">For a list of the estimated costs for tenants, which depend on the volume of logs generated, see the [Storage size for activity logs](#storage-size-for-activity-logs) section.</span></span>



<span data-ttu-id="0849a-222">**问：将数据流式传输到事件中心的费用是多少？**</span><span class="sxs-lookup"><span data-stu-id="0849a-222">**Q: How much will it cost to stream my data to an event hub?**</span></span>

<span data-ttu-id="0849a-223">**答**： 流式传输费用取决于你每分钟收到的消息数。</span><span class="sxs-lookup"><span data-stu-id="0849a-223">**A**: The streaming costs depend on the number of messages you receive per minute.</span></span> <span data-ttu-id="0849a-224">本文介绍了费用计算方法并列出了根据消息数估算的费用。</span><span class="sxs-lookup"><span data-stu-id="0849a-224">This article discusses how the costs are calculated and lists cost estimates, which are based on the number of messages.</span></span> 



<span data-ttu-id="0849a-225">**问：如何将 Azure AD 活动日志与 SIEM 系统集成？**</span><span class="sxs-lookup"><span data-stu-id="0849a-225">**Q: How do I integrate Azure AD activity logs with my SIEM system?**</span></span>

<span data-ttu-id="0849a-226">**答**： 可通过两种方式实现此目的：</span><span class="sxs-lookup"><span data-stu-id="0849a-226">**A**: You can do this in two ways:</span></span>

- <span data-ttu-id="0849a-227">将 Azure Monitor 与事件中心配合使用，以将日志流式传输到 SIEM 系统。</span><span class="sxs-lookup"><span data-stu-id="0849a-227">Use Azure Monitor with Event Hubs to stream logs to your SIEM system.</span></span> <span data-ttu-id="0849a-228">首先，[将日志流式传输到事件中心](tutorial-azure-monitor-stream-logs-to-event-hub.md)，然后使用配置的事件中心[设置 SIEM 工具](tutorial-azure-monitor-stream-logs-to-event-hub.md#access-data-from-your-event-hub)。</span><span class="sxs-lookup"><span data-stu-id="0849a-228">First, [stream the logs to an event hub](tutorial-azure-monitor-stream-logs-to-event-hub.md) and then [set up your SIEM tool](tutorial-azure-monitor-stream-logs-to-event-hub.md#access-data-from-your-event-hub) with the configured event hub.</span></span> 

- <span data-ttu-id="0849a-229">使用[报告图形 API](concept-reporting-api.md) 访问数据，并使用自己的脚本将其推送到 SIEM 系统。</span><span class="sxs-lookup"><span data-stu-id="0849a-229">Use the [Reporting Graph API](concept-reporting-api.md) to access the data, and push it into the SIEM system using your own scripts.</span></span>



<span data-ttu-id="0849a-230">**问：目前支持哪些 SIEM 工具？**</span><span class="sxs-lookup"><span data-stu-id="0849a-230">**Q: What SIEM tools are currently supported?**</span></span> 

<span data-ttu-id="0849a-231">**答**： 目前，[Splunk](tutorial-integrate-activity-logs-with-splunk.md)、QRadar 和 [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) 支持 Azure Monitor。</span><span class="sxs-lookup"><span data-stu-id="0849a-231">**A**: Currently, Azure Monitor is supported by [Splunk](tutorial-integrate-activity-logs-with-splunk.md), QRadar, and [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory).</span></span> <span data-ttu-id="0849a-232">若要详细了解连接器的工作方式，请参阅[将 Azure 监视数据流式传输到事件中心供外部工具使用](../../monitoring-and-diagnostics/monitor-stream-monitoring-data-event-hubs.md)。</span><span class="sxs-lookup"><span data-stu-id="0849a-232">For more information about how the connectors work, see [Stream Azure monitoring data to an event hub for consumption by an external tool](../../monitoring-and-diagnostics/monitor-stream-monitoring-data-event-hubs.md).</span></span>


<span data-ttu-id="0849a-233">**问：如何将 Azure AD 活动日志与 Splunk 实例集成？**</span><span class="sxs-lookup"><span data-stu-id="0849a-233">**Q: How do I integrate Azure AD activity logs with my Splunk instance?**</span></span>

<span data-ttu-id="0849a-234">**答**： 首先，[将 Azure AD 活动日志路由到事件中心](quickstart-azure-monitor-stream-logs-to-event-hub.md)，然后按照步骤[将活动日志与 Splunk 集成](tutorial-integrate-activity-logs-with-splunk.md)。</span><span class="sxs-lookup"><span data-stu-id="0849a-234">**A**: First, [route the Azure AD activity logs to an event hub](quickstart-azure-monitor-stream-logs-to-event-hub.md), then follow the steps to [Integrate activity logs with Splunk](tutorial-integrate-activity-logs-with-splunk.md).</span></span>



<span data-ttu-id="0849a-235">**问：如何将 Azure AD 活动日志与 Sumo Logic 集成？**</span><span class="sxs-lookup"><span data-stu-id="0849a-235">**Q: How do I integrate Azure AD activity logs with Sumo Logic?**</span></span> 

<span data-ttu-id="0849a-236">**答**： 首先，[将 Azure AD 活动日志路由到事件中心](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Collect_Logs_for_Azure_Active_Directory)，然后按照步骤[安装 Azure AD 应用程序并查看 SumoLogic 中的仪表板](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Install_the_Azure_Active_Directory_App_and_View_the_Dashboards)。</span><span class="sxs-lookup"><span data-stu-id="0849a-236">**A**: First, [route the Azure AD activity logs to an event hub](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Collect_Logs_for_Azure_Active_Directory), then follow the steps to [Install the Azure AD application and view the dashboards in SumoLogic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Install_the_Azure_Active_Directory_App_and_View_the_Dashboards).</span></span>



<span data-ttu-id="0849a-237">**问：是否可以在不使用外部 SIEM 工具的情况下，从事件中心访问数据？**</span><span class="sxs-lookup"><span data-stu-id="0849a-237">**Q: Can I access the data from an event hub without using an external SIEM tool?**</span></span> 

<span data-ttu-id="0849a-238">**答**： 可以。</span><span class="sxs-lookup"><span data-stu-id="0849a-238">**A**: Yes.</span></span> <span data-ttu-id="0849a-239">若要通过自定义应用程序来访问日志，可以使用[事件中心 API](../../event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph.md)。</span><span class="sxs-lookup"><span data-stu-id="0849a-239">To access the logs from your custom application, you can use the [Event Hubs API](../../event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph.md).</span></span> 




## <a name="next-steps"></a><span data-ttu-id="0849a-240">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0849a-240">Next steps</span></span>

* [<span data-ttu-id="0849a-241">将活动日志存档到存储帐户</span><span class="sxs-lookup"><span data-stu-id="0849a-241">Archive activity logs to a storage account</span></span>](quickstart-azure-monitor-route-logs-to-storage-account.md)
* [<span data-ttu-id="0849a-242">将活动日志路由到事件中心</span><span class="sxs-lookup"><span data-stu-id="0849a-242">Route activity logs to an event hub</span></span>](quickstart-azure-monitor-stream-logs-to-event-hub.md)
* [<span data-ttu-id="0849a-243">详细了解 Azure 诊断日志</span><span class="sxs-lookup"><span data-stu-id="0849a-243">Read more about Azure Diagnostic Logs</span></span>](../../monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs.md)
