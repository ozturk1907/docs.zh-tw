---
title: 在 DataGrid 控制項中變更執行時間顯示的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740598"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 使用設計階段功能建立 Windows Forms <xref:System.Windows.Forms.DataGrid> 之後，您可能也會想要在執行時間動態變更方格中 <xref:System.Data.DataSet> 物件的元素。 這可能包括變更資料表的個別值，或變更哪一個資料來源系結至 <xref:System.Windows.Forms.DataGrid> 控制項。 個別值的變更是透過 <xref:System.Data.DataSet> 物件來完成，而不是 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
### <a name="to-change-data-programmatically"></a>以程式設計方式變更資料  
  
1. 從 [<xref:System.Data.DataSet>] 物件中指定所需的資料表，並從資料表中指定所需的資料列和欄位，並將資料格設定為等於新的值。  
  
    > [!NOTE]
    > 若要指定 <xref:System.Data.DataSet> 或資料表第一個資料列的第一個資料表，請使用0。  
  
     下列範例顯示如何藉由按一下 [`Button1`] 來變更資料集第一個資料表第一列的第二個專案。 先前已建立 <xref:System.Data.DataSet> （`ds`）和資料表（`0` 和 `1`）。  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     （視覺C#效果， C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     在執行時間，您可以使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將 <xref:System.Windows.Forms.DataGrid> 控制項系結到不同的資料來源。 例如，您可能有數個 ADO.NET 資料控制項，每個都連接到不同的資料庫。  
  
### <a name="to-change-the-datasource-programmatically"></a>以程式設計方式變更資料來源  
  
1. 將 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法設定為您要系結的資料來源和資料表的名稱。  
  
     下列範例示範如何使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，將日期來源變更為連接到 Pubs 資料庫中作者資料表的 ADO.NET 資料控制項（adoPubsAuthors）。  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>請參閱

- [ADO.NET 資料集](../../data/adonet/ado-net-datasets.md)
- [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [如何：將 Windows Forms DataGrid 控制項繫結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
