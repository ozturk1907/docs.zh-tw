---
title: 擴充中繼資料系統
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795715"
---
# <a name="extending-the-metadata-system"></a>擴充中繼資料系統
Windows Communication Foundation （WCF）中繼資料系統是一組類別和介面，代表執行以服務為基礎的應用程式所需的中繼資料。 修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。  
  
## <a name="in-this-section"></a>本節內容  
 [匯出 WCF 延伸模組的自訂中繼資料](exporting-custom-metadata-for-a-wcf-extension.md)  
 描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 介面，將自訂原則判斷提示嵌入 WSDL 文件中。  
  
 [匯入 WCF 延伸模組的自訂中繼資料](importing-custom-metadata-for-a-wcf-extension.md)  
 描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 介面，讀取和回應 WSDL 文件中的自訂原則判斷提示。  
  
 [發行與擷取自訂繫結上的中繼資料](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 描述如何透過自訂繫結交換中繼資料。
