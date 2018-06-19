---
title: 'Comment : marshaler un VARIANT pour ADO.NET (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b442dcce2cdde28de8db1610971dd72dba84ab52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134430"
---
# <a name="how-to-marshal-a-variant-for-adonet-ccli"></a>Comment : marshaler un VARIANT pour ADO.NET (C++/CLI)
Montre comment ajouter un natif `VARIANT` à une base de données et comment marshaler un <xref:System.Object?displayProperty=fullName> à partir d’une base de données natif `VARIANT`.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managé, non managé](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir de types managés, le `gcroot` (mot clé) est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédant la directive `main`. Dans cet exemple, nous sommes création d’une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et de remplir certaines lignes de la table. Notez que natif `VARIANT` types sont passés en tant que valeurs pour la colonne de base de données ObjectCol. Au sein de DatabaseClass, ces `VARIANT` types sont marshalés vers des objets gérés à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> est utilisée pour marshaler un `VARIANT` à un <xref:System.Object>et la méthode <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> est utilisée pour marshaler un <xref:System.Object> à un `VARIANT`.  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
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
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
ObjectCol: This is a BSTR in a VARIANT.  
ObjectCol: 42  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_variant.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations sur les problèmes de sécurité impliquant ADO.NET, consultez [sécurisation des Applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices>   
 [Accès aux données en utilisant ADO.NET (C + c++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interopérabilité](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)