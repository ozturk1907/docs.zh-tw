---
title: SQL Server 和 ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: b54725fa8dbff7db82ed197f4961e773a06895e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782325"
---
# <a name="sql-server-and-adonet"></a>SQL Server 和 ADO.NET
本節說明 .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 特有的功能與行為。  
  
 <xref:System.Data.SqlClient> 封裝了資料庫特有的通訊協定，可讓您存取不同的 SQL Server 版本。 該資料提供者的功能設計類似於 OLE DB、ODBC 及 Oracle 的 .NET Framework 資料提供者。 <xref:System.Data.SqlClient> 包含可直接與 SQL Server 通訊的表格式資料流 (TDS) 剖析器。  
  
> [!NOTE]
> 若要使用 SQL Server 的 .NET Framework 資料提供者，應用程式必須參考 <xref:System.Data.SqlClient> 命名空間。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server 安全性](sql-server-security.md)  
 提供 SQL Server 安全性功能的概觀，以及可用於建立以 SQL Server 為目標之安全 ADO.NET 應用程式的應用程式案例。  
  
 [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)  
 說明如何使用 SQL Server 資料型別，以及它們如何與 .NET Framework 資料型別互動。  
  
 [SQL Server 二進位和大量數值資料](sql-server-binary-and-large-value-data.md)  
 說明如何在 SQL Server 中使用大數值資料。  
  
 [ADO.NET 中的 SQL Server 資料作業](sql-server-data-operations.md)  
 說明如何使用 SQL Server 中的資料。 包含有關大量複製作業、MARS、非同步作業和資料表值參數的章節。  
  
 [SQL Server 功能和 ADO.NET](sql-server-features-and-adonet.md)  
 說明對於 ADO.NET 應用程式開發人員很有用的 SQL Server 功能。  
  
 [LINQ to SQL](./linq/index.md)  
 說明建立 LINQ to SQL 應用程式所需的基本建置組塊 (Building Blocks)、處理序和技巧。  
  
 如需 SQL Server Database Engine 的完整文件，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》。  
  
 [SQL Server 線上叢書](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [ADO.NET 中的資料類型對應](../data-type-mappings-in-ado-net.md)
- [DataSet、DataTable 和 DataView](../dataset-datatable-dataview/index.md)
- [在 ADO.NET 中擷取和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
