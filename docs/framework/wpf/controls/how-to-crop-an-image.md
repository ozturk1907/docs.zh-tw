---
title: HOW TO：裁剪影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: e672c7e24ec4db2d6424fa0b611cb1c135cf8eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053388"
---
# <a name="how-to-crop-an-image"></a>HOW TO：裁剪影像
此範例示範如何裁剪影像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>。  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> 是主要用於編碼影像的裁剪的版本時儲存檔案。 若要裁剪的影像顯示用途，請參閱[How to:建立裁剪區域](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))主題。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]下面的範例中使用的資源進行定義。  
  
 [!code-xaml[imageelementexample#CroppedXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 下列範例會建立映像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>做為其來源。  
  
 [!code-xaml[imageelementexample#CroppedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap>也可用來當做另一個來源<xref:System.Windows.Media.Imaging.CroppedBitmap>，鏈結裁剪。 請注意，<xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A>使用相對於來源點陣圖和不初始映像將裁剪的值。  
  
 [!code-xaml[imageelementexample#CroppedXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a>另請參閱

- [如何：建立裁剪區域](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))
