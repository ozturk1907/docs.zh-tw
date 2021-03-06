---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398410"
---
# <a name="allowaccounts"></a>\<allowAccounts>
包含設定專案的集合，這些專案會指定主控 Windows Communication Foundation （WCF）服務之進程的使用者帳戶，並授與共享服務的連接存取權。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel. 啟用 >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net.pipe >** ](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<d >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|屬性|描述|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|加入裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)|指定 Net Pipe 或 TCP 共用服務的組態設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
