---
title: HOW TO：使用自動配置建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 8eb1e93dd87c210812c9b7758c744a616ef2d862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052387"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>HOW TO：使用自動配置建立按鈕
此範例說明如何使用自動版面配置方法，以建立可當地語系化之應用程式中的按鈕。  
  
 當地語系化[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]可以是耗時的程序。 當地語系化人員除了翻譯文字以外，通常還需要調整項目的大小並重新置放項目。 在過去每一種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]已調整的需要調整。 現在使用的功能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，您可以設計可降低的需求調整的項目。 在呼叫的方法來撰寫應用程式都可以更輕鬆地調整大小和重新置放`automatic layout`。  
  
## <a name="example"></a>範例  

下列兩個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會建立按鈕，一個用於英文字，一個使用西班牙文的文字，具現化的應用程式。 請注意，除了文字之外，其餘程式碼都相同；按鈕會配合文字進行調整。

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下圖顯示具有自動調整大小的按鈕的程式碼範例的輸出：
  
 ![按鈕相同，但文字的語言不同](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
## <a name="see-also"></a>另請參閱

- [使用自動配置概觀](use-automatic-layout-overview.md)
- [針對自動版面配置使用方格](how-to-use-a-grid-for-automatic-layout.md)
