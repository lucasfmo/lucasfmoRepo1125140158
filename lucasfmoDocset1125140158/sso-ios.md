---
title: "Configure o Intune para dispositivos iOS de logon único"
titlesuffix: Azure portal
description: "Saiba como configurar o Intune para logon único do dispositivo iOS."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/7/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff71239a360b09ca831a6e99f5f7a759b08f5d56
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2017
---
# <a name="configure-intune-for-ios-device-single-sign-on"></a><span data-ttu-id="51b60-103">Configure o Intune para dispositivos iOS de logon único</span><span class="sxs-lookup"><span data-stu-id="51b60-103">Configure Intune for iOS device single sign-on</span></span>



<span data-ttu-id="51b60-104">A maioria dos aplicativos LOB (Linha de Negócios) exigem algum nível de autenticação de usuário para dar suporte à segurança.</span><span class="sxs-lookup"><span data-stu-id="51b60-104">Most Line of Business (LOB) apps require some level of user authentication to support security.</span></span> <span data-ttu-id="51b60-105">Em muitos casos, isso requer que o usuário digite as mesmas credenciais várias vezes, o que pode ser frustrante.</span><span class="sxs-lookup"><span data-stu-id="51b60-105">In many cases this requires the user to type the same credentials multiple times, which can be frustrating for users.</span></span> <span data-ttu-id="51b60-106">Para melhorar a experiência do usuário, os desenvolvedores podem criar aplicativos que usam o logon único, reduzindo o número de vezes que um usuário deve fornecer credenciais.</span><span class="sxs-lookup"><span data-stu-id="51b60-106">To improve the user experience, developers can create apps that use single sign-on, reducing the number of times a user must provide credentials.</span></span>

<span data-ttu-id="51b60-107">Para aproveitar o Logon Único do dispositivo iOS, você deve ter as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="51b60-107">To take advantage of iOS device Single Sign-on, you must have the following conditions:</span></span>

- <span data-ttu-id="51b60-108">Um aplicativo codificado para procurar o repositório de credenciais do usuário no conteúdo de logon único no dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="51b60-108">An app coded to look for the user credential store in the single sign-on payload on the iOS device.</span></span>
- <span data-ttu-id="51b60-109">Intune configurado para logon único de dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="51b60-109">Intune configured for iOS device single sign-on.</span></span>

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a><span data-ttu-id="51b60-110">Para configurar o Intune para logon único de dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="51b60-110">To configure Intune for iOS device single sign-on</span></span>


1. <span data-ttu-id="51b60-111">Entre no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="51b60-111">Sign into the [Azure portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="51b60-112">Escolha **Mais Serviços** > **Monitoramento + Gerenciamento** > **Intune**.</span><span class="sxs-lookup"><span data-stu-id="51b60-112">Choose **More Services** > **Monitoring + Management** > **Intune**.</span></span>
3. <span data-ttu-id="51b60-113">Na folha **Intune**, escolha **Configuração do dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="51b60-113">On the **Intune** blade, choose **Device configuration**.</span></span>
2. <span data-ttu-id="51b60-114">Na folha **Configurações do Dispositivo**, escolha **Perfis**.</span><span class="sxs-lookup"><span data-stu-id="51b60-114">On the **Device configuration** blade, choose **Profiles**.</span></span>
3. <span data-ttu-id="51b60-115">Na folha de perfis, escolha **Criar Perfil**, forneça um nome e uma descrição e defina as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="51b60-115">On the profiles blade, choose **Create Profile**, provide a name and description, and configure the following settings:</span></span>
   - <span data-ttu-id="51b60-116">**Plataforma**: escolha **iOS**.</span><span class="sxs-lookup"><span data-stu-id="51b60-116">**Platform**: Choose **iOS**.</span></span> 
   - <span data-ttu-id="51b60-117">**Tipo de perfil**: escolha **recursos de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="51b60-117">**Profile type**: Choose **Device features**.</span></span>
4. <span data-ttu-id="51b60-118">Na folha **Recursos de dispositivo**, escolha **Logon Único**.</span><span class="sxs-lookup"><span data-stu-id="51b60-118">On the **Device features** blade, choose **Single Sign On**.</span></span>

   ![Folha de logon único](./media/sso-blade.png)

2. <span data-ttu-id="51b60-120">Use a seguinte tabela de resumo para ajudá-lo a preencher os campos na folha **Logon Único**.</span><span class="sxs-lookup"><span data-stu-id="51b60-120">Use the following summary table to help you fill in the fields on the **Single Sign On** blade.</span></span> <span data-ttu-id="51b60-121">Para obter detalhes, consulte as seções após a tabela.</span><span class="sxs-lookup"><span data-stu-id="51b60-121">For details, see the sections after the table.</span></span>
   
   |<span data-ttu-id="51b60-122">Campo</span><span class="sxs-lookup"><span data-stu-id="51b60-122">Field</span></span>  |<span data-ttu-id="51b60-123">Anotações</span><span class="sxs-lookup"><span data-stu-id="51b60-123">Notes</span></span>|
   |---------|---------|
   |<span data-ttu-id="51b60-124">**Atributo de nome de usuário do AAD**</span><span class="sxs-lookup"><span data-stu-id="51b60-124">**Username attribute from AAD**</span></span>|<span data-ttu-id="51b60-125">O atributo que o Intune procura para cada usuário no AAD e preenche o respectivo campo (como o UPN) antes de gerar a carga XML que é instalada no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51b60-125">The attribute that Intune looks at for each user in AAD and populates the respective field (such as UPN) before generating the XML payload that gets installed on the device.</span></span>|
   |<span data-ttu-id="51b60-126">**Território**</span><span class="sxs-lookup"><span data-stu-id="51b60-126">**Realm**</span></span>|<span data-ttu-id="51b60-127">A parte do domínio da URL.</span><span class="sxs-lookup"><span data-stu-id="51b60-127">The domain portion of the URL.</span></span>|
   |<span data-ttu-id="51b60-128">**Prefixos de URL que usarão Logon Único**</span><span class="sxs-lookup"><span data-stu-id="51b60-128">**URL prefixes that will use Single Sign On**</span></span>|<span data-ttu-id="51b60-129">Quaisquer URLs em sua organização que exijam autenticação de logon único usuário</span><span class="sxs-lookup"><span data-stu-id="51b60-129">Any URLs in your organization that require user single sign-on authentication</span></span>|
   |<span data-ttu-id="51b60-130">**Os aplicativos que usarão o Logon Único**</span><span class="sxs-lookup"><span data-stu-id="51b60-130">**Apps that will use Single Sign On**</span></span>|<span data-ttu-id="51b60-131">Aplicativos no dispositivo do usuário final que usam o conteúdo de logon único.</span><span class="sxs-lookup"><span data-stu-id="51b60-131">Apps on end user’s device that use the single sign-on payload.</span></span>|
   |<span data-ttu-id="51b60-132">**Certificado de renovação de credencial**</span><span class="sxs-lookup"><span data-stu-id="51b60-132">**Credential renewal certificate**</span></span>|<span data-ttu-id="51b60-133">Se estiver usando certificados para autenticação, selecione o certificado SCEP ou PFX implantado para o usuário como o certificado de autenticação.</span><span class="sxs-lookup"><span data-stu-id="51b60-133">If using certificates for authentication, select the SCEP or PFX certificate that is deployed to the user as the authentication certificate.</span></span>|

<span data-ttu-id="51b60-134">As seções a seguir dão mais detalhes sobre cada um dos campos de logon único.</span><span class="sxs-lookup"><span data-stu-id="51b60-134">The following sections provide more details about each of the single sign-on fields.</span></span>

### <a name="username-attribute-from-aad-and-realm"></a><span data-ttu-id="51b60-135">Atributo de nome de usuário do AAD e do Realm</span><span class="sxs-lookup"><span data-stu-id="51b60-135">Username attribute from AAD and Realm</span></span>

- <span data-ttu-id="51b60-136">Se **Nome do Princípio do Usuário** estiver selecionado para esse campo, ele é analisada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="51b60-136">If **User Principle Name** is selected for this field, it is parsed in the following way:</span></span>

   ![Atributo de nome de usuário](media/User-name-attribute.png)

   <span data-ttu-id="51b60-138">Você também tem a opção de substituir o realm pelo texto digitado na caixa de texto **Realm**.</span><span class="sxs-lookup"><span data-stu-id="51b60-138">You also have the choice to overwrite the realm with the text you type in the **Realm** text box.</span></span>

   <span data-ttu-id="51b60-139">Por exemplo, Contoso pode ter várias sub-regiões, como América do Norte, Europa e Ásia.</span><span class="sxs-lookup"><span data-stu-id="51b60-139">For example, Contoso might have several subregions such as Europe, Asia, and North America.</span></span> <span data-ttu-id="51b60-140">Ela talvez queira que os usuários na Ásia usem o conteúdo SSO e o aplicativo exige o UPN no formato *username@asia.contoso.com*. Nesse caso, se você selecionar **Nome do Princípio do Usuário**, por padrão, o realm para cada usuário será obtido do AAD, podendo ser apenas *contoso.com*. Especialmente para os usuários na Ásia, você pode criar esse conteúdo e substituir o realm pelo valor *asia.contoso.com*. Agora o UPN do usuário final se torna *username@asia.contoso.com* e não *username@contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="51b60-140">They might want their users in Asia to use the SSO payload, and the app requires the UPN in the form *username@asia.contoso.com*. In this case, if you select **User Principle Name**, by default the realm for each user is taken from AAD that may be just *contoso.com*. So for users in Asia specially, you can create this payload and overwrite the realm with the value *asia.contoso.com*. Now the end user's UPN becomes *username@asia.contoso.com* and not *username@contoso.com*.</span></span>

- <span data-ttu-id="51b60-141">Se você selecionar **ID do Dispositivo**, o Intune selecionará automaticamente a ID do Dispositivo Intune.</span><span class="sxs-lookup"><span data-stu-id="51b60-141">If you select **Device ID**, Intune automatically selects the Intune Device ID.</span></span>

   <span data-ttu-id="51b60-142">Por padrão, aplicativos precisam usar somente a ID do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51b60-142">By default, apps only need to use the device ID.</span></span> <span data-ttu-id="51b60-143">Porém, se seu aplicativo usar o realm além da ID do dispositivo, você poderá digitar o realm na caixa de texto **Realm**.</span><span class="sxs-lookup"><span data-stu-id="51b60-143">But if your app uses the realm in addition to the device ID, you can type the realm in the **Realm** text box.</span></span>

   > [!NOTE]
   > <span data-ttu-id="51b60-144">Por padrão, mantenha o realm vazio se você usar a ID do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51b60-144">By default keep the realm empty if you use device ID.</span></span>

### <a name="url-prefixes-that-will-use-single-sign-on"></a><span data-ttu-id="51b60-145">Prefixos de URL que usarão Logon Único</span><span class="sxs-lookup"><span data-stu-id="51b60-145">URL prefixes that will use Single Sign On</span></span>

<span data-ttu-id="51b60-146">Digite aqui qualquer URL que exista na sua organização e que exija autenticação de usuário.</span><span class="sxs-lookup"><span data-stu-id="51b60-146">Type any URLs here that exist in your organization that require user authentication.</span></span>

<span data-ttu-id="51b60-147">Por exemplo, quando um usuário se conecta a qualquer um desses sites, o dispositivo iOS usa as credenciais de logon único e o usuário não precisa inserir credenciais adicionais.</span><span class="sxs-lookup"><span data-stu-id="51b60-147">For example, when a user connects to any of these sites, the iOS device uses the single sign-on credentials and the user does not need to enter any additional credentials.</span></span> <span data-ttu-id="51b60-148">No entanto, se você tiver autenticação multifator habilitada, os usuários deverão digitar a segunda autenticação.</span><span class="sxs-lookup"><span data-stu-id="51b60-148">However, if you have multi-factor authentication enabled, users are required to enter the second authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="51b60-149">Essas URLs devem ter FQDN corretamente formatado.</span><span class="sxs-lookup"><span data-stu-id="51b60-149">These URLs must be properly formatted FQDN.</span></span> <span data-ttu-id="51b60-150">A Apple exige que estejam no formato `http://<yourURL.domain>`</span><span class="sxs-lookup"><span data-stu-id="51b60-150">Apple requires these to be in the form `http://<yourURL.domain>`</span></span>

<span data-ttu-id="51b60-151">Os padrões de correspondência de URL devem começar com um `http://` ou `https://`.</span><span class="sxs-lookup"><span data-stu-id="51b60-151">The URL matching patterns must begin with either `http://` or `https://`.</span></span> <span data-ttu-id="51b60-152">Uma correspondência de cadeia de caracteres simples é executada, de modo que o prefixo URL `http://www.contoso.com/` não corresponde a `http://www.contoso.com:80/`.</span><span class="sxs-lookup"><span data-stu-id="51b60-152">A simple string match is performed, so the URL prefix `http://www.contoso.com/` does not match `http://www.contoso.com:80/`.</span></span> <span data-ttu-id="51b60-153">Com o iOS 9.0 ou posterior, no entanto, um único curinga * pode ser usado para especificar todos os valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="51b60-153">With iOS 9.0 or later, however, a single wildcard * may be used to specify all matching values.</span></span> <span data-ttu-id="51b60-154">Por exemplo, `http://*.contoso.com/` corresponde tanto a `http://store.contoso.com/` quanto a `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="51b60-154">For example, `http://*.contoso.com/`  matches both `http://store.contoso.com/` and `http://www.contoso.com`.</span></span>
<span data-ttu-id="51b60-155">Os padrões `http://.com` e `https://.com` correspondem a todas as URLs HTTP e HTTPS, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="51b60-155">The patterns `http://.com` and `https://.com` match all HTTP and HTTPS URLs, respectively.</span></span>

### <a name="apps-that-will-use-single-sign-on"></a><span data-ttu-id="51b60-156">Os aplicativos que usarão o Logon Único</span><span class="sxs-lookup"><span data-stu-id="51b60-156">Apps that will use Single Sign On</span></span>

<span data-ttu-id="51b60-157">Indique quais aplicativos no dispositivo do usuário final podem usar o Logon Único no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="51b60-157">Indicate which apps on an end user’s device that can use the Single Sign on payload.</span></span>

<span data-ttu-id="51b60-158">A matriz `AppIdentifierMatches` deve conter cadeias de caracteres que correspondam a IDs de pacote de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b60-158">The `AppIdentifierMatches` array must contain strings that match app bundle IDs.</span></span> <span data-ttu-id="51b60-159">Essas cadeias de caracteres podem ser correspondências exatas (por exemplo: `com.contoso.myapp`) ou especificar uma correspondência de prefixo na ID de pacote usando o caractere curinga *.</span><span class="sxs-lookup"><span data-stu-id="51b60-159">These strings may be exact matches (for example: `com.contoso.myapp`) or may specify a prefix match on the bundle ID by using the * wildcard character.</span></span> <span data-ttu-id="51b60-160">O caractere curinga deve aparecer após um caractere de ponto (.) e pode aparecer apenas uma vez, no final da cadeia de caracteres (por exemplo: `com.contoso.\*`).</span><span class="sxs-lookup"><span data-stu-id="51b60-160">The wildcard character must appear after a period character (.), and may appear only once, at the end of the string (for example: `com.contoso.*`).</span></span> <span data-ttu-id="51b60-161">Quando um caractere curinga for incluído, qualquer aplicativo cuja ID do pacote comece com o prefixo receberá acesso à conta.</span><span class="sxs-lookup"><span data-stu-id="51b60-161">When a wildcard is included, any app whose bundle ID begins with the prefix is granted access to the account.</span></span>

<span data-ttu-id="51b60-162">O campo **Nome do Aplicativo** é usado para adicionar um nome amigável para ajudá-lo a identificar a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="51b60-162">The **App Name** field is used to add a user-friendly name to help you identify the bundle ID.</span></span>

### <a name="credential-renewal-certificate"></a><span data-ttu-id="51b60-163">Certificado de renovação de credencial</span><span class="sxs-lookup"><span data-stu-id="51b60-163">Credential renewal certificate</span></span>

<span data-ttu-id="51b60-164">Se você autenticar seus usuários finais com certificados (não senhas), use este campo para selecionar o certificado do SCEP ou PFX que é implantado para o usuário como o certificado de autenticação.</span><span class="sxs-lookup"><span data-stu-id="51b60-164">If you authenticate your end users with certificates (not passwords), then use this field to select the SCEP or PFX certificate that is deployed to the user as the authentication certificate.</span></span> <span data-ttu-id="51b60-165">Normalmente, é o mesmo certificado implantado para o usuário para outros perfis, como VPN, Wi-Fi ou Email.</span><span class="sxs-lookup"><span data-stu-id="51b60-165">Typically, this is the same certificate that is deployed to the user for other profiles such as VPN, WiFi, or Email.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51b60-166">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="51b60-166">Next steps</span></span>

<span data-ttu-id="51b60-167">Para informações de configuração do recurso de dispositivos adicionais, consulte [Como definir configurações de recurso do dispositivo no Microsoft Intune](device-features-configure.md).</span><span class="sxs-lookup"><span data-stu-id="51b60-167">For additional device feature configuration information, see [How to configure device feature settings in Microsoft Intune](device-features-configure.md).</span></span>