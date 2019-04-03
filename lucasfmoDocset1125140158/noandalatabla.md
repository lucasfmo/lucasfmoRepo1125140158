<span data-ttu-id="3a245-101">Azure App Service Authentication enables turn-key authentication support in an Azure Function app.</span><span class="sxs-lookup"><span data-stu-id="3a245-101">Azure App Service Authentication enables turn-key authentication support in an Azure Function app.</span></span> <span data-ttu-id="3a245-102">It integrates seamlessly with Facebook, Twitter, Microsoft Account, Google, and Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3a245-102">It integrates seamlessly with Facebook, Twitter, Microsoft Account, Google, and Azure Active Directory.</span></span> <span data-ttu-id="3a245-103">You'll add App Service Authentication to protect the backend APIs of your web app.</span><span class="sxs-lookup"><span data-stu-id="3a245-103">You'll add App Service Authentication to protect the backend APIs of your web app.</span></span>

## <a name="enable-app-service-authentication"></a><span data-ttu-id="3a245-104">Enable App Service Authentication</span><span class="sxs-lookup"><span data-stu-id="3a245-104">Enable App Service Authentication</span></span>

1. <span data-ttu-id="3a245-105">Open the function app in the Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="3a245-105">Open the function app in the Azure Portal.</span></span>

2. <span data-ttu-id="3a245-106">Under **Platform features**, select **Authentication/Authorization**.</span><span class="sxs-lookup"><span data-stu-id="3a245-106">Under **Platform features**, select **Authentication/Authorization**.</span></span>

    ![Select Authentication / Authorization](media/functions-first-serverless-web-app/6-authorization.jpg)

3. <span data-ttu-id="3a245-108">Select the following values:</span><span class="sxs-lookup"><span data-stu-id="3a245-108">Select the following values:</span></span>


   |                   <span data-ttu-id="3a245-109">Setting</span><span class="sxs-lookup"><span data-stu-id="3a245-109">Setting</span></span>                    |                                        <span data-ttu-id="3a245-110">Suggested value</span><span class="sxs-lookup"><span data-stu-id="3a245-110">Suggested value</span></span>                                        |                                   <span data-ttu-id="3a245-111">Description</span><span class="sxs-lookup"><span data-stu-id="3a245-111">Description</span></span>                                    |
   |----------------------------------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
   |        <span data-ttu-id="3a245-112">**App Service Authentication**</span><span class="sxs-lookup"><span data-stu-id="3a245-112">**App Service Authentication**</span></span>        |                                              <span data-ttu-id="3a245-113">On</span><span class="sxs-lookup"><span data-stu-id="3a245-113">On</span></span>                                               |                              <span data-ttu-id="3a245-114">Enable authentication.</span><span class="sxs-lookup"><span data-stu-id="3a245-114">Enable authentication.</span></span>                              |
   | <span data-ttu-id="3a245-115">**Action when request is not authenticated**</span><span class="sxs-lookup"><span data-stu-id="3a245-115">**Action when request is not authenticated**</span></span> |                              <span data-ttu-id="3a245-116">Log in with Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="3a245-116">Log in with Azure Active Directory</span></span>                               |                <span data-ttu-id="3a245-117">Select a configured authentication method (below).</span><span class="sxs-lookup"><span data-stu-id="3a245-117">Select a configured authentication method (below).</span></span>                |
   |         <span data-ttu-id="3a245-118">**Authentication Providers**</span><span class="sxs-lookup"><span data-stu-id="3a245-118">**Authentication Providers**</span></span>         |                                           <span data-ttu-id="3a245-119">See below</span><span class="sxs-lookup"><span data-stu-id="3a245-119">See below</span></span>                                           |                                    <span data-ttu-id="3a245-120">See below</span><span class="sxs-lookup"><span data-stu-id="3a245-120">See below</span></span>                                     |
   |               <span data-ttu-id="3a245-121">**Token store**</span><span class="sxs-lookup"><span data-stu-id="3a245-121">**Token store**</span></span>                |                                              <span data-ttu-id="3a245-122">On</span><span class="sxs-lookup"><span data-stu-id="3a245-122">On</span></span>                                               |                  <span data-ttu-id="3a245-123">Allow App Service to store and manage tokens.</span><span class="sxs-lookup"><span data-stu-id="3a245-123">Allow App Service to store and manage tokens.</span></span>                   |
   |      <span data-ttu-id="3a245-124">**Allowed external redirect URLs**</span><span class="sxs-lookup"><span data-stu-id="3a245-124">**Allowed external redirect URLs**</span></span>      | <span data-ttu-id="3a245-125">The URL of your application, for example: https://firstserverlessweb.z4.web.core.windows.net/</span><span class="sxs-lookup"><span data-stu-id="3a245-125">The URL of your application, for example: https://firstserverlessweb.z4.web.core.windows.net/</span></span> | <span data-ttu-id="3a245-126">URL(s) that App Service is allowed to redirect to after a user is authenticated.</span><span class="sxs-lookup"><span data-stu-id="3a245-126">URL(s) that App Service is allowed to redirect to after a user is authenticated.</span></span> |


4. <span data-ttu-id="3a245-127">Select **Azure Active Directory** to reveal **Azure Active Directory Settings**.</span><span class="sxs-lookup"><span data-stu-id="3a245-127">Select **Azure Active Directory** to reveal **Azure Active Directory Settings**.</span></span>

   1. <span data-ttu-id="3a245-128">Select **Express** as the **Management Mode** and fill in the following information.</span><span class="sxs-lookup"><span data-stu-id="3a245-128">Select **Express** as the **Management Mode** and fill in the following information.</span></span>


    |       <span data-ttu-id="3a245-129">Setting</span><span class="sxs-lookup"><span data-stu-id="3a245-129">Setting</span></span>       |      <span data-ttu-id="3a245-130">Suggested value</span><span class="sxs-lookup"><span data-stu-id="3a245-130">Suggested value</span></span>       |                                     <span data-ttu-id="3a245-131">Description</span><span class="sxs-lookup"><span data-stu-id="3a245-131">Description</span></span>                                     |
    |---------------------|----------------------------|-------------------------------------------------------------------------------------|
    | <span data-ttu-id="3a245-132">**Management mode**</span><span class="sxs-lookup"><span data-stu-id="3a245-132">**Management mode**</span></span> | <span data-ttu-id="3a245-133">Express, Create new AD app</span><span class="sxs-lookup"><span data-stu-id="3a245-133">Express, Create new AD app</span></span> | <span data-ttu-id="3a245-134">Automatically set up a service principal and Azure Active Directory authentication.</span><span class="sxs-lookup"><span data-stu-id="3a245-134">Automatically set up a service principal and Azure Active Directory authentication.</span></span> |
    |   <span data-ttu-id="3a245-135">**Create app**</span><span class="sxs-lookup"><span data-stu-id="3a245-135">**Create app**</span></span>    |    <span data-ttu-id="3a245-136">my-serverless-webapp</span><span class="sxs-lookup"><span data-stu-id="3a245-136">my-serverless-webapp</span></span>    |                          <span data-ttu-id="3a245-137">Enter a unique application name.</span><span class="sxs-lookup"><span data-stu-id="3a245-137">Enter a unique application name.</span></span>                           |


   2. <span data-ttu-id="3a245-138">Click **OK** to save the Azure Active Directory settings.</span><span class="sxs-lookup"><span data-stu-id="3a245-138">Click **OK** to save the Azure Active Directory settings.</span></span>

      ![Authentication/Authorization and Azure Active Directory settings](media/functions-first-serverless-web-app/6-create-aad.png)

5. <span data-ttu-id="3a245-140">Click **Save**.</span><span class="sxs-lookup"><span data-stu-id="3a245-140">Click **Save**.</span></span>


## <a name="modify-the-web-app-to-enable-authentication"></a><span data-ttu-id="3a245-141">Modify the web app to enable authentication</span><span class="sxs-lookup"><span data-stu-id="3a245-141">Modify the web app to enable authentication</span></span>

1. <span data-ttu-id="3a245-142">In the Cloud Shell, ensure that the current directory is the **www/dist** folder.</span><span class="sxs-lookup"><span data-stu-id="3a245-142">In the Cloud Shell, ensure that the current directory is the **www/dist** folder.</span></span>

    ```azurecli
    cd ~/functions-first-serverless-web-application/www/dist
    ```

1. <span data-ttu-id="3a245-143">To enable authentication in your function app, append the following line of code to **settings.js**.</span><span class="sxs-lookup"><span data-stu-id="3a245-143">To enable authentication in your function app, append the following line of code to **settings.js**.</span></span>

    `window.authEnabled = true`

    <span data-ttu-id="3a245-144">Make the change and view the result by using the following commands or by using a command-line editor like VIM.</span><span class="sxs-lookup"><span data-stu-id="3a245-144">Make the change and view the result by using the following commands or by using a command-line editor like VIM.</span></span>

    ```azurecli
    echo "window.authEnabled = true" >> settings.js
    ```

    <span data-ttu-id="3a245-145">Confirm the change was made to the file.</span><span class="sxs-lookup"><span data-stu-id="3a245-145">Confirm the change was made to the file.</span></span>

    ```azurecli
    cat settings.js
    ```

1. <span data-ttu-id="3a245-146">Upload the file to Blob storage.</span><span class="sxs-lookup"><span data-stu-id="3a245-146">Upload the file to Blob storage.</span></span>

    ```azurecli
    az storage blob upload -c \$web --account-name <storage account name> -f settings.js -n settings.js
    ```


## <a name="test-the-application"></a><span data-ttu-id="3a245-147">Test the application</span><span class="sxs-lookup"><span data-stu-id="3a245-147">Test the application</span></span>

1. <span data-ttu-id="3a245-148">Open the application in a browser.</span><span class="sxs-lookup"><span data-stu-id="3a245-148">Open the application in a browser.</span></span> <span data-ttu-id="3a245-149">Click **Log in** and log in.</span><span class="sxs-lookup"><span data-stu-id="3a245-149">Click **Log in** and log in.</span></span>

1. <span data-ttu-id="3a245-150">Select an image file and upload it.</span><span class="sxs-lookup"><span data-stu-id="3a245-150">Select an image file and upload it.</span></span>

    ![Sign in page](media/functions-first-serverless-web-app/6-aad-auth.png)


## <a name="summary"></a><span data-ttu-id="3a245-152">Summary</span><span class="sxs-lookup"><span data-stu-id="3a245-152">Summary</span></span>

<span data-ttu-id="3a245-153">In this module, you learned how to add authentication to the applcation using Azure App Service Authentication.</span><span class="sxs-lookup"><span data-stu-id="3a245-153">In this module, you learned how to add authentication to the applcation using Azure App Service Authentication.</span></span>
