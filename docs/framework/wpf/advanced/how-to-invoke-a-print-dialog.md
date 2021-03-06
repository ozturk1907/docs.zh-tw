---
title: 如何：叫用列印對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636090"
---
# <a name="how-to-invoke-a-print-dialog"></a>如何：叫用列印對話方塊
若要提供從您的應用程式列印的功能，您可以直接建立並開啟 <xref:System.Windows.Controls.PrintDialog> 物件。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.PrintDialog> 控制項提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、設定和 XPS 工作提交的單一進入點。 控制項很容易使用，而且可以使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 標記或程式碼來具現化。 下列範例示範如何在程式碼中具現化和開啟控制項，以及如何從它進行列印。 它也會示範如何確保對話方塊會提供使用者設定特定頁面範圍的選項。 範例程式碼假設 C：磁片磁碟機的根目錄中有一個檔案 FixedDocumentSequence。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 對話方塊開啟之後，使用者就可以從安裝在其電腦上的印表機中選取。 他們也可以選擇選取[MICROSOFT XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)來建立 XML 檔規格（Xps）檔案，而不是列印。  
  
> [!NOTE]
> 本主題中討論的 WPF <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> 控制項，不應與 Windows Forms 的 <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> 元件混淆。  
  
 嚴格來說，您可以使用 <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> 方法，而不需要開啟對話方塊。 就這一點而言，控制項可用來做為看不見的列印元件。 但基於效能的考慮，最好是使用 <xref:System.Printing.PrintQueue.AddJob%2A> 方法，或是 <xref:System.Windows.Xps.XpsDocumentWriter>的許多 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> 和 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> 方法之一。 如需詳細資訊，請參閱以程式設計[方式列印 XPS](how-to-programmatically-print-xps-files.md)檔案和。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.PrintDialog>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [Microsoft XPS 檔寫入器](https://go.microsoft.com/fwlink/?LinkId=147319)
