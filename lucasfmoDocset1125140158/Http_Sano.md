---
title: "Azure Data Lake Store'a erişmek için bir Linux VM yönetilen hizmet kimliği (MSI) kullanma"
description: "Bir Linux VM yönetilen hizmet kimliği (MSI) Azure Data Lake Store'a erişmek için nasıl kullanılacağını gösteren bir öğretici."
services: active-directory
documentationcenter: 
author: skwan
manager: mtillman
editor: 
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 11/20/2017
ms.author: skwan
ms.openlocfilehash: 98ff833fe541e1207a87421d54a8ce2dfc17cda1
ms.sourcegitcommit: e266df9f97d04acfc4a843770fadfd8edf4fa2b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2017
---
# <a name="use-a-linux-vm-managed-service-identity-msi-to-access-azure-data-lake-store"></a>Azure Data Lake Store'a erişmek için bir Linux VM yönetilen hizmet kimliği (MSI) kullanın



Bu öğretici, bir yönetilen hizmet Kimliği'ni (MSI) bir Linux sanal makine (VM) için bir Azure Data Lake Store'a erişmek için nasıl kullanılacağını gösterir. Yönetilen hizmet kimliği Azure tarafından otomatik olarak yönetilir ve Azure AD kimlik doğrulaması, kimlik bilgileri kodunuza eklemek zorunda kalmadan destekleyen hizmetler için kimlik doğrulaması sağlar. Aşağıdakileri nasıl yapacağınızı öğrenirsiniz:

> [!div class="checklist"]
> * Bir Linux VM üzerinde MSI etkinleştir 
> * Bir Azure Data Lake Store, VM erişim
> * VM kimliğini kullanarak bir erişim belirteci almak ve bir Azure Data Lake Store'a erişmek için kullanın

## <a name="prerequisites"></a>Ön koşullar



## <a name="sign-in-to-azure"></a>Azure'da oturum açma

[https://portal.azure.com](https://portal.azure.com) adresindeki Azure portalında oturum açın.

## <a name="create-a-linux-virtual-machine-in-a-new-resource-group"></a>Yeni bir kaynak grubunda bir Linux sanal makine oluşturun

Bu öğretici için yeni bir Linux VM oluşturun. Mevcut bir VM'yi üzerinde MSI de etkinleştirebilirsiniz.

1. Azure portalının sol üst köşesinde bulunan **Yeni** düğmesine tıklayın.
2. **İşlem**'i ve ardından **Ubuntu Server 16.04 LTS**'yi seçin.
3. Sanal makine bilgilerini girin. İçin **kimlik doğrulama türü**seçin **SSH ortak anahtarını** veya **parola**. Oluşturulan kimlik bilgileri, VM'ye oturum açmak izin verir.

   ![Alt görüntü metin](media/msi-tutorial-linux-vm-access-arm/msi-linux-vm.png)

4. Seçin bir **abonelik** sanal makine açılır.
5. Yeni bir seçmek için **kaynak grubu** sanal makinenin oluşturulması, seçmek istediğiniz **Yeni Oluştur**. İşlem tamamlandığında **Tamam**’a tıklayın.
6. VM boyutunu seçin. Daha fazla boyutları görmek için seçin **tüm görüntüle** veya desteklenen disk türü filtresini değiştirin. Ayarlar dikey penceresinde varsayılan değerleri koruyun ve **Tamam**'a tıklayın.

## <a name="enable-msi-on-your-vm"></a>MSI VM üzerinde etkinleştir

Bir sanal makine MSI erişim belirteçleri, kimlik bilgileri kodunuza koyma gereksinimi olmadan Azure AD'den almanızı sağlar. Perde arkasında MSI etkinleştirme iki işlemi yapar: MSI VM uzantısı, VM yükler ve MSI Azure Kaynak Yöneticisi'nde sağlar.  

1. Seçin **sanal makine** MSI etkinleştirmek istediğiniz.
2. Sol gezinti çubuğunda **yapılandırma**.
3. Gördüğünüz **yönetilen hizmet kimliği**. Kaydolun ve MSI etkinleştirmek için seçin **Evet**, devre dışı bırakmak istiyorsanız seçin No
4. Tıklattığınız olun **kaydetmek** yapılandırmayı kaydetmek için.

   ![Alt görüntü metin](media/msi-tutorial-linux-vm-access-arm/msi-linux-extension.png)

5. Bu bilgisayarda hangi uzantıların olduğunu denetlemek istiyorsanız **Linux VM**, tıklatın **uzantıları**. MSI etkinleştirilirse, **ManagedIdentityExtensionforLinux** listede görünür.

   ![Alt görüntü metin](media/msi-tutorial-linux-vm-access-arm/msi-extension-value.png)

## <a name="grant-your-vm-access-to-azure-data-lake-store"></a>Azure Data Lake Store, VM erişim

Şimdi bir Azure Data Lake Store bulunan dosya ve klasörleri, VM erişim izni verebilir.  Bu adım için mevcut bir Data Lake Store kullanın veya yeni bir tane oluşturun.  Azure Portalı'nı kullanarak yeni bir Data Lake Store oluşturmak için bu izleyin [Azure Data Lake Store quickstart](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-get-started-portal). Ayrıca Azure CLI ve Azure PowerShell'de kullanın quickstarts olan [Azure Data Lake deposu belgeleri](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-overview).

Data Lake Store, yeni bir klasör oluşturun ve okuma, yazma ve o klasördeki dosyaları yürütme VM MSI izni verin:

1. Azure portalında tıklatın **Data Lake Store** sol gezinti içinde.
2. Bu öğretici için kullanmak istediğiniz Data Lake Store'ı tıklatın.
3. Tıklatın **Veri Gezgini** komut çubuğunda.
4. Data Lake Store kök klasöründe seçilir.  Tıklatın **erişim** komut çubuğunda.
5. **Ekle**'ye tıklayın.  İçinde **seçin** alan, VM adını girin, örneğin **DevTestVM**.  Arama sonuçlarından VM seçmek için tıklayın ve ardından **seçin**.
6. Tıklatın **seçin izinleri**.  Seçin **okuma** ve **yürütme**, eklemek **bu klasör**ve eklediğiniz **erişim izni yalnızca**.  **Tamam**’a tıklayın.  İzni başarıyla eklenmesi gerekir.
7. Kapat **erişim** dikey.
8. Bu öğretici için yeni bir klasör oluşturun.  Tıklatın **yeni klasör** yeni klasör örneği için bir ad verin ve komut çubuğunda **TestFolder**.  **Tamam**’a tıklayın.
9. Oluşturduğunuz klasöre tıklayın ve ardından **erişim** komut çubuğunda.
10. 5. adım, tıklatın benzer **Ekle**, **seçin** alan VM adını girin, seçin ve tıklatın **seçin**.
11. Adım 6 için benzer **Select izinleri**seçin **okuma**, **yazma**, ve **yürütme**, eklemek **bu klasör**ve eklediğiniz **erişim izni girdisi ve varsayılan izin girdisi**.  **Tamam**’a tıklayın.  İzni başarıyla eklenmesi gerekir.

VM MSI şimdi tüm dosyaları oluşturduğunuz klasöre işlemleri yapabilirsiniz.  Data Lake Store, erişimi yönetme hakkında daha fazla bilgi okumak için bu makalede [Data Lake Store'da erişim denetimi](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-access-control).

## <a name="get-an-access-token-using-the-vm-msi-and-use-it-to-call-the-azure-data-lake-store-filesystem"></a>VM MSI kullanarak bir erişim belirteci alın ve Azure Data Lake Store dosya sistemi çağırmak için kullanın

Azure Data Lake Store MSI kullanarak doğrudan erişim belirteçleri kabul edebilir destekler Azure AD kimlik doğrulama, yerel olarak alınır.  Data Lake Store dosya sistemi için kimlik doğrulaması yapmak için Data Lake Store dosya sistemi uç noktası bir Authorization Üstbilgisi biçimde Azure AD tarafından verilen bir erişim belirteci Gönder "taşıyıcı \<ACCESS_TOKEN_VALUE\>".  Azure AD kimlik doğrulaması için Data Lake Store desteği hakkında daha fazla bilgi için okuma [Data Lake Store ile Azure Active Directory'yi kullanarak kimlik doğrulaması](https://docs.microsoft.com/azure/data-lake-store/data-lakes-store-authentication-using-azure-active-directory)

Bu öğreticide, REST yapmak için CURL kullanarak REST API istekleri Data Lake Store dosya sistemi için kimlik doğrulaması.

> [!NOTE]
> Data Lake Store dosya sistemi istemci SDK'ları henüz desteklemediği yönetilen hizmet kimliği.  Destek SDK'SININ eklendiğinde Bu öğretici güncelleştirilir.

Bu adımları tamamlamak için bir SSH istemcisi gerekir. Windows kullanıyorsanız, SSH İstemcisi'nde kullanabileceğiniz [Linux için Windows alt](https://msdn.microsoft.com/commandline/wsl/about). SSH istemcinin anahtarları yapılandırma yardıma gereksinim duyarsanız, bkz: [kullanmak SSH anahtarları nasıl Windows Azure üzerinde ile](../virtual-machines/linux/ssh-from-windows.md), veya [nasıl oluşturulacağı ve Linux VM'ler için Azure'da bir SSH ortak ve özel anahtar çifti kullanılmak](../virtual-machines/linux/mac-create-ssh-keys.md).

1. Linux VM hem de Portalı'nda gidin **genel bakış**, tıklatın **Bağlan**.  
2. **Connect** tercih ettiğiniz SSH istemcisi ile VM. 
3. Terminal penceresinde CURL, kullanarak Data Lake Store dosya sistemi için bir erişim belirteci almak üzere yerel MSI uç nokta için bir isteği oluşturun.  "https://datalake.azure.net/." Data Lake Store için kaynak tanımlayıcısıdır  Kaynak tanımlayıcısı eğik eklemek önemlidir.
    
   ```bash
   curl http://localhost:50342/oauth2/token --data "resource=https://datalake.azure.net/" -H Metadata:true   
   ```
    
   Başarılı yanıt Data Lake Store için kimlik doğrulaması kullanma erişim belirteci döndürür:

   ```bash
   {"access_token":"eyJ0eXAiOiJ...",
    "refresh_token":"",
    "expires_in":"3599",
    "expires_on":"1508119757",
    "not_before":"1508115857",
    "resource":"https://datalake.azure.net/",
    "token_type":"Bearer"}
   ```

4. CURL kullanarak, bir isteği kök klasöründe klasörleri listelemek için Data Lake Store dosya sistemi REST uç noktanızı oluşturun.  Bu, her şeyin doğru yapılandırıldığını denetlemek için basit bir yoludur.  Erişim belirteci değerini önceki adımdan kopyalayın.  Bu, yetkilendirme üst "Bearer" dize "B" büyük olması önemlidir.  Data Lake Store'da adını bulabilirsiniz **genel bakış** Azure Portal'daki Data Lake Store dikey bölümü.

   ```bash
   curl https://<YOUR_ADLS_NAME>.azuredatalakestore.net/webhdfs/v1/?op=LISTSTATUS -H "Authorization: Bearer <ACCESS_TOKEN>"
   ```
    
   Başarılı yanıt şuna benzer:

   ```bash
   {"FileStatuses":{"FileStatus":[{"length":0,"pathSuffix":"TestFolder","type":"DIRECTORY","blockSize":0,"accessTime":1507934941392,"modificationTime":1508105430590,"replication":0,"permission":"770","owner":"bd0e76d8-ad45-4fe1-8941-04a7bf27f071","group":"bd0e76d8-ad45-4fe1-8941-04a7bf27f071"}]}}
   ```

5. Şimdi, Data Lake Store için bir dosyayı karşıya yüklemeyi deneyebilirsiniz.  İlk olarak, karşıya yüklemek için bir dosya oluşturun.

   ```bash
   echo "Test file." > Test1.txt
   ```

6. CURL kullanarak, bir isteği dosyayı karşıya yüklemeyi daha önce oluşturduğunuz klasöre Data Lake Store dosya sistemi REST uç noktanızı oluşturun.  CURL yeniden yönlendirme otomatik olarak izler ve karşıya yükleme yeniden yönlendirme içerir. 

   ```bash
   curl -i -X PUT -L -T Test1.txt -H "Authorization: Bearer <ACCESS_TOKEN>" 'https://<YOUR_ADLS_NAME>.azuredatalakestore.net/webhdfs/v1/<FOLDER_NAME>/Test1.txt?op=CREATE' 
   ```

    Başarılı yanıt şuna benzer:

   ```bash
   HTTP/1.1 100 Continue
   HTTP/1.1 307 Temporary Redirect
   Cache-Control: no-cache, no-cache, no-store, max-age=0
   Pragma: no-cache
   Expires: -1
   Location: https://mytestadls.azuredatalakestore.net/webhdfs/v1/TestFolder/Test1.txt?op=CREATE&write=true
   x-ms-request-id: 756f6b24-0cca-47ef-aa12-52c3b45b954c
   ContentLength: 0
   x-ms-webhdfs-version: 17.04.22.00
   Status: 0x0
   X-Content-Type-Options: nosniff
   Strict-Transport-Security: max-age=15724800; includeSubDomains
   Date: Sun, 15 Oct 2017 22:10:30 GMT
   Content-Length: 0
       
   HTTP/1.1 100 Continue
       
   HTTP/1.1 201 Created
   Cache-Control: no-cache, no-cache, no-store, max-age=0
   Pragma: no-cache
   Expires: -1
   Location: https://mytestadls.azuredatalakestore.net/webhdfs/v1/TestFolder/Test1.txt?op=CREATE&write=true
   x-ms-request-id: af5baa07-3c79-43af-a01a-71d63d53e6c4
   ContentLength: 0
   x-ms-webhdfs-version: 17.04.22.00
   Status: 0x0
   X-Content-Type-Options: nosniff
   Strict-Transport-Security: max-age=15724800; includeSubDomains
   Date: Sun, 15 Oct 2017 22:10:30 GMT
   Content-Length: 0
   ```

Diğer Data Lake Store dosya sistemi dosyalarına ekleme API'lerini kullanarak, dosyaları ve diğer indirin.

Tebrikler!  Bir VM MSI kullanarak Data Lake Store dosya sistemi doğruladınız.

## <a name="related-content"></a>İlgili içerik

- MSI genel bakış için bkz: [yönetilen hizmet Kimliği'ne genel bakış](../active-directory/msi-overview.md).
- Yönetimi için Azure Resource Manager operations Data Lake Store kullanır.  Resource Manager kimliğini doğrulamak için bir VM MSI kullanma hakkında daha fazla bilgi için okuma [Resource Manager erişmek için bir Linux VM yönetilen hizmet kimliği (MSI) kullanan](https://docs.microsoft.com/azure/active-directory/msi-tutorial-linux-vm-access-arm).
- Daha fazla bilgi edinmek [Data Lake Store ile Azure Active Directory'yi kullanarak kimlik doğrulaması](https://docs.microsoft.com/azure/data-lake-store/data-lakes-store-authentication-using-azure-active-directory).
- Daha fazla bilgi edinmek [REST API kullanarak Azure Data Lake Store dosya sistemi işlemleri](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-data-operations-rest-api) veya [WebHDFS dosya sistemi API'lerini](https://docs.microsoft.com/rest/api/datalakestore/webhdfs-filesystem-apis).
- Daha fazla bilgi edinmek [Data Lake Store'da erişim denetimi](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-access-control).

Geri bildirim sağlamak ve iyileştirmek ve içeriği şekil yardımcı olmak için aşağıdaki açıklamaları bölümü kullanın.