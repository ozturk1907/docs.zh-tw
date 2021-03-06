---
title: 設定狀態資料的安全性
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705895"
---
# <a name="securing-state-data"></a>設定狀態資料的安全性
處理機密資料或執行任何種類安全性決策的應用程式需要保持該資料在自己的控制之下，而且不能允許其他潛在惡意程式碼直接存取資料。 保護記憶體中資料的最佳方式是將資料宣告為私用或內部 (具有限制為相同組件的範圍) 變數。 不過，即使此資料受限於存取權，您應該要注意︰  
  
- 使用反映機制，可以參考您物件的高度信任程式碼可以取得和設定私用成員。  
  
- 使用序列化，如果高度信任程式碼可以使用物件的序列化格式存取對應的資料，則高度信任程式碼可以有效地取得和設定私用成員。  
  
- 在偵錯時，可以讀取此資料。  
  
 請確定沒有任何您自己的方法或屬性會在無意中公開這些值。  
  
## <a name="see-also"></a>請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
