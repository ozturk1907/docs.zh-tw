---
title: 圖層物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1615b9c4df222edd95cda9bceae622ba6f1d8d78
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736347"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>如何： Windows Forms 上的圖層物件

當您建立複雜的使用者介面，或使用多重文件介面（MDI）表單時，您通常會想要將控制項和子表單分層，以建立更複雜的使用者介面（UI）。 若要移動和追蹤群組內容中的控制項和視窗，您可以操控其迭置*順序*。 迭置順序是表單上控制項的視覺分層，沿著表單的 Z 軸（深度）。 位於 z 順序頂端的視窗會與所有其他視窗重迭。 所有其他視窗會在迭置順序的底部重迭視窗。

## <a name="to-layer-controls-at-design-time"></a>在設計階段圖層控制項

1. 在 Visual Studio 中，選取您想要階層式控制項。

2. 在 [**格式**] 功能表上，選取 [**順序**]，然後選取 [**帶入前端**] 或 [**送回**]。

## <a name="to-layer-controls-programmatically"></a>以程式設計方式分層控制項

使用 <xref:System.Windows.Forms.Control.BringToFront%2A> 和 <xref:System.Windows.Forms.Control.SendToBack%2A> 方法來操作控制項的迭置順序。

例如，如果 <xref:System.Windows.Forms.TextBox> 控制項 [`txtFirstName`] 位於另一個控制項之下，而您想要將它放在最上層，請使用下列程式碼：

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> Windows Forms 支援*控制項*內含專案。 控制項內含專案牽涉到將一些控制項放在包含控制項內，例如 <xref:System.Windows.Forms.GroupBox> 控制項內的一些 <xref:System.Windows.Forms.RadioButton> 控制項。 然後，您可以在包含控制項內分層控制項。 移動 [群組方塊] 也會移動控制項，因為它們包含在其中。

## <a name="see-also"></a>請參閱

- [Windows Forms 控制項](index.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
