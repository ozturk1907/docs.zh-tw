---
title: <httpDigest> 項目
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785822"
---
# <a name="httpdigest-element"></a>\<HTTPDigest > 元素
指定對服務驗證用戶端時，所使用的摘要式類型認證。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<HTTPDigest >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`impersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。 用戶端選取的模擬模式不會在伺服器上強制使用。 有效值包括以下的值：<br /><br /> 發現伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。<br />申請伺服器可以在本機系統上模擬用戶端的安全性內容。<br />其它伺服器可以在遠端系統上模擬用戶端的安全性內容。<br />匿名伺服器無法模擬或識別用戶端。<br />無未指派模擬層級。<br /><br /> 預設為 Identification。 此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="remarks"></a>備註  
 摘要是指使用演算法和一組輸入所決定的雜湊。 驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。 用戶端可計算雜湊，並將它傳送至服務。 服務也會計算雜湊並比較兩者的值。 比對會驗證用戶端。  
  
 此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。 如需詳細資訊，請參閱[IIS 6.0 中的摘要式驗證](https://go.microsoft.com/fwlink/?LinkId=88443)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
