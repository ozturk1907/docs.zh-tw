---
title: 作法：存取受控 HTML 文件物件模型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 2a195dc6583d5a0a72bd08b66f8933f4002e879a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487280"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>作法：存取受控 HTML 文件物件模型
您可以從兩種類型的應用程式中，存取受管理的「HTML 文件物件模型」(DOM)：  
  
- 執行有受管理之 <xref:System.Windows.Forms.WebBrowser> 控制項的 Windows Forms 應用程式 (.exe)。 這兩種技術為互補，<xref:System.Windows.Forms.WebBrowser> 控制項負責將頁面顯示給使用者，HTML DOM 負責顯示文件的邏輯結構。  
  
- Windows Forms <xref:System.Windows.Forms.UserControl> 會在 Internet Explorer 中執行。 無論要變更文件的結構，或開啟強制回應對話方塊等等，都可以使用負責顯示您 <xref:System.Windows.Forms.UserControl> 執行所在之頁面的 HTML DOM。  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>從 Windows Forms 應用程式存取 DOM  
  
1. 在 Windows Forms 應用程式中執行 <xref:System.Windows.Forms.WebBrowser> 控制項並監視 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。 如需裝載控制項以及監視事件的詳細資訊，請參閱[事件](../../../standard/events/index.md)。  
  
2. 存取 <xref:System.Windows.Forms.HtmlDocument> 控制項的 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性，以擷取目前頁面的 <xref:System.Windows.Forms.WebBrowser>。  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>存取 Internet Explorer 中所執行之 UserControl 的 DOM  
  
1. 建立您自己之 <xref:System.Windows.Forms.UserControl> 類別的衍生類別。 如需詳細資訊，請參閱[如何：撰寫複合控制項](how-to-author-composite-controls.md)。  
  
2. 將下列程式碼放入您 <xref:System.Windows.Forms.UserControl> 的 Load 事件處理常式中：  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
1. 透過 <xref:System.Windows.Forms.WebBrowser> 控制項使用 DOM 時，請務必等候 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件發生，再嘗試存取 <xref:System.Windows.Forms.WebBrowser.Document%2A> 控制項的 <xref:System.Windows.Forms.WebBrowser> 屬性。 當整份文件全部載入之後，會引發 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件，若您在此之前使用 DOM，可能會導致應用程式執行時發生例外狀況。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
  
1. 您的應用程式或 <xref:System.Windows.Forms.UserControl> 需要完全信任，才能存取受管理的 HTML DOM。 如果您要部署使用 ClickOnce 在 Windows Forms 應用程式，您可以使用要求完全信任權限提升或受信任的應用程式部署;請參閱[保護 ClickOnce 應用程式](/visualstudio/deployment/securing-clickonce-applications)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱

- [使用 Managed HTML 文件物件模型](using-the-managed-html-document-object-model.md)
