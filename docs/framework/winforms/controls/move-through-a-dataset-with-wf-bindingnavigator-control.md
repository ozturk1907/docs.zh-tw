---
title: 使用 BindingNavigator 控制項在資料集中移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742148"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>如何：使用 Windows Form BindingNavigator 控制項在資料集中移動
當您建立資料驅動應用程式時，通常需要向使用者顯示資料集合。 <xref:System.Windows.Forms.BindingNavigator> 控制項搭配 <xref:System.Windows.Forms.BindingSource> 元件提供方便且可擴充的方案，可在集合中移動並循序顯示項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingNavigator> 控制項在資料中移動。 這個集合會包含在使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Data.DataView> 中。  
  
> [!NOTE]
> 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [BindingSource 元件](bindingsource-component.md)
- [如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)
