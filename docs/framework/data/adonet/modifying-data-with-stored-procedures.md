---
title: 使用預存程序修改資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 46c92301b717e285c4c18241f84d0069069c7bdc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783521"
---
# <a name="modifying-data-with-stored-procedures"></a>使用預存程序修改資料
預存程序 (Stored Procedure) 可以接受資料做為輸入參數，也可以將資料以輸出參數、結果集 (Result Set) 或傳回值的形式傳回。 下列範例說明 ADO.NET 如何傳送及接收輸入參數、輸出參數和傳回值。 此範例會將新記錄插入資料表 (該資料表的主索引鍵資料行是 SQL Server 資料庫中的識別欄位)。  
  
> [!NOTE]
> 如果您要使用 SQL Server 預存程序搭配 <xref:System.Data.SqlClient.SqlDataAdapter> 來編輯或刪除資料，請務必不要在預存程序定義中使用 SET NOCOUNT ON。 因為這樣會讓傳回的受影響資料列計數成為零，而 `DataAdapter` 會將它解譯為並行衝突。 在此事件中，系統會擲回 <xref:System.Data.DBConcurrencyException>。  
  
## <a name="example"></a>範例  
 此範例會使用下列預存程式，將新的分類插入**Northwind** **分類**資料表。 預存程式會採用 [**類別名稱**] 資料行中的值做為輸入參數，並使用 SCOPE_IDENTITY （）函式來抓取識別欄位的新值，並將其設為**類別**，並在輸出參數中傳回。 Return 語句會使用 @@ROWCOUNT函數來傳回所插入的資料列數目。  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 下列程式碼範例使用以上所示的 `InsertCategory` 預存程序做為 <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的 <xref:System.Data.SqlClient.SqlDataAdapter> 的來源。 在呼叫 `@Identity` 的 <xref:System.Data.DataSet> 方法而將記錄插入至資料庫之後，`Update` 輸出參數將反映在 <xref:System.Data.SqlClient.SqlDataAdapter> 中。 程式碼也會擷取傳回值。  
  
> [!NOTE]
> 使用<xref:System.Data.OleDb.OleDbDataAdapter>時，您必須在其他參數之前， <xref:System.Data.ParameterDirection>使用**ReturnValue**的來指定參數。  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [執行命令](executing-a-command.md)
- [ADO.NET 概觀](ado-net-overview.md)
