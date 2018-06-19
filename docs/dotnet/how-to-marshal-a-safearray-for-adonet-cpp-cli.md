---
title: 'Comment : marshaler un SAFEARRAY pour ADO.NET (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ddd6250fac293fef58ccc21894661ddf32e3fa61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137417"
---
# <a name="how-to-marshal-a-safearray-for-adonet-ccli"></a>Comment : marshaler un SAFEARRAY pour ADO.NET (C++/CLI)
Montre comment ajouter un natif `SAFEARRAY` à une base de données et comment marshaler un tableau managé à partir d’une base de données natif `SAFEARRAY`.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managé, non managé](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir de types managés, le `gcroot` (mot clé) est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédant la directive `main`. Dans cet exemple, nous sommes création d’une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et de remplir certaines lignes de la table. Notez que natif `SAFEARRAY` types sont passés en tant que valeurs pour la colonne de base de données ArrayIntsCol. Au sein de DatabaseClass, ces `SAFEARRAY` types sont marshalés vers des objets gérés à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.Copy%2A> est utilisée pour marshaler un `SAFEARRAY` vers un tableau managé d’entiers et la méthode <xref:System.Runtime.InteropServices.Marshal.Copy%2A> est utilisée pour marshaler un tableau managé d’entiers à un `SAFEARRAY`.  
  
```  
// adonet_marshal_safearray.cpp  
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
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
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
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
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
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_safearray.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations sur les problèmes de sécurité impliquant ADO.NET, consultez [sécurisation des Applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices>   
 [Accès aux données en utilisant ADO.NET (C + c++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interopérabilité](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)