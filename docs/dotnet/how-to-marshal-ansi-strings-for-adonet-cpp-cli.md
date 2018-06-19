---
title: 'Comment : marshaler des chaînes ANSI pour ADO.NET (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
ms.assetid: 6759d5a2-515f-4079-856b-73b1c1e68f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d06f12a8a8d900e4604bea2800a1ba4c5c966770
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137469"
---
# <a name="how-to-marshal-ansi-strings-for-adonet-ccli"></a>Comment : marshaler des chaînes ANSI pour ADO.NET (C++/CLI)
Montre comment ajouter une chaîne native (`char *`) pour une base de données et comment marshaler un <xref:System.String?displayProperty=fullName> à partir d’une base de données vers une chaîne native.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managé, non managé](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir de types managés, le `gcroot` (mot clé) est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédant la directive `main`. Dans cet exemple, nous sommes création d’une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et de remplir certaines lignes de la table. Notez que les chaînes C++ natives sont passées en tant que valeurs pour la colonne de base de données StringCol. Au sein de DatabaseClass, ces chaînes sont marshalées vers des chaînes managées à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> est utilisée pour marshaler un `char *` à un <xref:System.String>et la méthode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> est utilisée pour marshaler un <xref:System.String> à un `char *`.  
  
> [!NOTE]
>  La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être libérée en appelant <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> ou `GlobalFree`.  
  
```  
// adonet_marshal_string_native.cpp  
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
  
    void AddRow(char *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringAnsi(  
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
  
    int GetValuesForColumn(char *dataColumn, char **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringAnsi(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a char *.  
            values[i] = (char *)Marshal::StringToHGlobalAnsi(  
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
    db->AddRow("This is string 1.");  
    db->AddRow("This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    char *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        "StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        cout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalAnsi.  
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
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_native.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations sur les problèmes de sécurité impliquant ADO.NET, consultez [sécurisation des Applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices>   
 [Accès aux données en utilisant ADO.NET (C + c++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interopérabilité](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)