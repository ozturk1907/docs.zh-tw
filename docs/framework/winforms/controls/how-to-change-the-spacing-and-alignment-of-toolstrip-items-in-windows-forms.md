---
title: 如何：變更 ToolStrip 專案的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746558"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式
<xref:System.Windows.Forms.ToolStrip> 控制項完全支援調整大小、每個 <xref:System.Windows.Forms.ToolStripItem> 控制項的間距、<xref:System.Windows.Forms.ToolStrip>上的控制項相片順序，以及相對於 <xref:System.Windows.Forms.ToolStrip>的控制項間距等版面配置功能。  
  
 由於 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性的預設值是 `true`，因此除非您將 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性設定為 `false`，否則控制項會自動調整大小。  
  
### <a name="to-manually-size-a-toolstripitem"></a>手動調整 ToolStripItem 大小  
  
1. 將相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性設定為 [`false`]。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. 以您想要的方式，將 <xref:System.Windows.Forms.ToolStripItem.Size%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ToolStripItem>。  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>設定 ToolStripItem 的間距  
  
1. 將想要的值（以圖元為單位）插入相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.Margin%2A> 屬性。  
  
     [<xref:System.Windows.Forms.ToolStripItem.Margin%2A>] 屬性的值會以下列順序指定專案與相鄰專案之間的間距： [左]、[上]、[右] 和 [下]。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>將 ToolStripItem 對齊 ToolStrip 的右側  
  
1. 將相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性設定為 [<xref:System.Windows.Forms.ToolStripItemAlignment.Right>]。 根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 設定為 [<xref:System.Windows.Forms.ToolStripItemAlignment.Left>]，這會將控制項對齊 <xref:System.Windows.Forms.ToolStrip>的左邊。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>排列 ToolStrip 上的 ToolStrip 專案  
  
- 將 [<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>] 屬性設為您想要 <xref:System.Windows.Forms.ToolStripLayoutStyle> 的值。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
