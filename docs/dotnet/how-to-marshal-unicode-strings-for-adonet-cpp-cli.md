---
title: 'Comment : marshaler des chaînes Unicode pour ADO.NET (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
ms.assetid: 1da090ff-6b53-40be-841f-dc79dfe8ba10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 15cf9e9806c0820ea5a410a93419016c2f678c65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137372"
---
# <a name="how-to-marshal-unicode-strings-for-adonet-ccli"></a>Comment : marshaler des chaînes Unicode pour ADO.NET (C++/CLI)
Montre comment ajouter une chaîne Unicode native (`wchar_t *`) pour une base de données et comment marshaler un <xref:System.String?displayProperty=fullName> à partir d’une base de données vers une chaîne Unicode native.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managé, non managé](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir de types managés, le `gcroot` (mot clé) est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédant la directive `main`. Dans cet exemple, nous sommes création d’une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et de remplir certaines lignes de la table. Notez que les chaînes Unicode C++ sont passées en tant que valeurs pour la colonne de base de données StringCol. Au sein de DatabaseClass, ces chaînes sont marshalées vers des chaînes managées à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> est utilisée pour marshaler un `wchar_t *` à un <xref:System.String>et la méthode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> est utilisée pour marshaler un <xref:System.String> à un `wchar_t *`.  
  
> [!NOTE]
>  La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> doit être libérée en appelant <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> ou `GlobalFree`.  
  
```  
// adonet_marshal_string_wide.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(wchar_t *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringUni(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a wchar_t *.  
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(  
                (String ^)rows[i][columnStr]).ToPointer();  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
    db->AddRow(L"This is string 1.");  
    db->AddRow(L"This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    wchar_t *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalUni.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_wide.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations sur les problèmes de sécurité impliquant ADO.NET, consultez [sécurisation des Applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices>   
 [Accès aux données en utilisant ADO.NET (C + c++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interopérabilité](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)