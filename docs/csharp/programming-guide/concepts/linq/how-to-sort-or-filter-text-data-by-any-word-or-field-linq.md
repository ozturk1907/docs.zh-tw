---
title: 如何依任何字或欄位排序或篩選文字資料（LINQ）（C#）
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: e869d57c413d175c092cdc15a6fe54cab94e04b8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347354"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>如何依任何字或欄位排序或篩選文字資料（LINQ）（C#）
下列範例示範如何依行中的任一欄位，來排序多行結構化文字 (例如逗號分隔值)。 此欄位可能會在執行階段以動態方式指定。 假設 scores.csv 中的欄位各代表學生的學號和四個測驗分數。  
  
### <a name="to-create-a-file-that-contains-data"></a>建立內含資料的檔案  
  
1. 複製[如何從不同的檔案聯結內容（LINQ）（C#）](./how-to-join-content-from-dissimilar-files-linq.md)主題中的分數 .csv 資料，並將它儲存至您的方案資料夾。  
  
## <a name="example"></a>範例  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 此範例也會示範如何從方法傳回查詢變數。  
  
## <a name="compiling-the-code"></a>編譯程式碼  

建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。
  
## <a name="see-also"></a>請參閱

- [LINQ 和字串 (C#)](./linq-and-strings.md)
