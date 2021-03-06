---
title: Panel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744313"
---
# <a name="panel-control-overview-windows-forms"></a>Panel 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.Panel> 控制項是用來為其他控制項提供可識別的群組。 一般而言，您可以使用面板依函式細分表單。 例如，您的訂單表單可能會指定郵寄選項，例如要使用的貨運公司。 將面板中的所有選項群組，可為使用者提供邏輯視覺提示。 在設計階段，所有控制項都可以輕鬆地移動，而當您移動 <xref:System.Windows.Forms.Panel> 控制項時，也會移動其包含的所有控制項。 在面板中分組的控制項可以透過其 <xref:System.Windows.Forms.Control.Controls%2A> 屬性來存取。 這個屬性會傳回 <xref:System.Windows.Forms.Control> 實例的集合，因此，您通常需要將以這種方式取得的控制項轉換成其特定類型。  
  
## <a name="panel-versus-groupbox"></a>面板與群組方塊  
 <xref:System.Windows.Forms.Panel> 控制項類似于 <xref:System.Windows.Forms.GroupBox> 控制項;不過，只有 <xref:System.Windows.Forms.Panel> 控制項可以有捲軸，而且只有 <xref:System.Windows.Forms.GroupBox> 控制項才會顯示標題。  
  
## <a name="key-properties"></a>索引鍵內容  
 若要顯示捲軸，請將 [<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>] 屬性設定為 [`true`]。 您也可以藉由設定 [<xref:System.Windows.Forms.Control.BackColor%2A>]、[<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 和 [<xref:System.Windows.Forms.Panel.BorderStyle%2A>] 屬性來自訂面板的外觀。 如需 <xref:System.Windows.Forms.Control.BackColor%2A> 和 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性的詳細資訊，請參閱[如何：設定面板的背景](how-to-set-the-background-of-a-windows-forms-panel.md)。 [<xref:System.Windows.Forms.Panel.BorderStyle%2A>] 屬性會決定面板是否以沒有可見框線（<xref:System.Windows.Forms.BorderStyle.None>）、純文字線（<xref:System.Windows.Forms.BorderStyle.FixedSingle>）或陰影線條（<xref:System.Windows.Forms.BorderStyle.Fixed3D>）來勾勒。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Panel>
- [GroupBox 控制項](groupbox-control-windows-forms.md)
- [操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項](group-controls-with-wf-panel-control-using-the-designer.md)
- [操作說明：使用設計工具設定 Windows Forms 面板的背景](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
