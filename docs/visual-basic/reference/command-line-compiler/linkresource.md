---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335486"
---
# <a name="-linkresource-visual-basic"></a>-linkresource （Visual Basic）
建立與 Managed 資源的連結。  
  
## <a name="syntax"></a>語法  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

或  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 必要。 要連結至元件的資源檔。 如果檔案名包含空格，請將名稱括在引號（""）中。  
  
 `identifier`  
 選擇性。 資源的邏輯名稱。 用來載入資源的名稱。 預設值是檔案的名稱。 （選擇性）您可以在組件資訊清單中指定檔案是否為公用或私用，例如： `-linkres:filename.res,myname.res,public`。 根據預設，`filename` 在元件中是公用的。  
  
## <a name="remarks"></a>備註  
 `-linkresource` 選項不會將資源檔內嵌在輸出檔案中;使用 [`-resource`] 選項來執行這項操作。  
  
 `-linkresource` 選項需要 `-target:module`以外的其中一個 `-target` 選項。  
  
 例如，如果 `filename` 是由[resgen.exe （資源檔](../../../framework/tools/resgen-exe-resource-file-generator.md)產生器）或在開發環境中建立的 .NET Framework 資源檔，則可以使用 <xref:System.Resources> 命名空間中的成員進行存取。 （如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>）。若要在執行時間存取所有其他資源，請在 <xref:System.Reflection.Assembly> 類別中使用以 `GetManifestResource` 開頭的方法。  
  
 檔案名可以是任何檔案格式。 例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。  
  
 `-linkresource` 的簡短形式為 `-linkres`。  
  
> [!NOTE]
> Visual Studio 開發環境中無法使用 [`-linkresource`] 選項。只有當您從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `in.vb` 和連結至資源檔 `rf.resource`。  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [-資源（Visual Basic）](../../../visual-basic/reference/command-line-compiler/resource.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
