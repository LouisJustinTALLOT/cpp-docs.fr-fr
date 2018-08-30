---
title: Accès aux données à l’aide d’ADO.NET (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3d87d41b97f587f2546df246044eaf8df3bba373
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221976"
---
# <a name="data-access-using-adonet-ccli"></a>Accès aux données à l'aide d'ADO.NET (C++/CLI)
ADO.NET est l’API .NET Framework pour accéder aux données et fournit la puissance et la facilité d’utilisation inégalée par les solutions d’accès de données précédente. Cette section décrit certains des problèmes impliquant ADO.NET qui sont uniques aux utilisateurs de Visual C++, telles que le marshaling des types natifs.  
  
 ADO.NET s’exécute sous le Common Language Runtime (CLR). Par conséquent, toute application qui interagit avec ADO.NET doit également cibler le CLR. Toutefois, cela ne signifie pas que les applications natives ne peuvent pas utiliser ADO.NET. Ces exemples montreront comment interagir avec une base de données ADO.NET à partir du code natif.  
  
## <a name="marshal_ansi"></a> Marshaler des chaînes ANSI pour ADO.NET
Montre comment ajouter une chaîne native (`char *`) à une base de données et comment marshaler un <xref:System.String?displayProperty=fullName> à partir d’une base de données vers une chaîne native.  
  
### <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir des types managés, le `gcroot` mot clé est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédente directive `main`. Dans cet exemple, nous allons créant une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et remplir quelques lignes dans la table. Notez que les chaînes C++ natives sont passées en tant que valeurs pour la colonne de base de données StringCol. Au sein de DatabaseClass, ces chaînes sont marshalées vers des chaînes managées à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> est utilisée pour marshaler un `char *` à un <xref:System.String>et la méthode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> est utilisée pour marshaler un <xref:System.String> à un `char *`.  
  
> [!NOTE]
>  La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être libérée en appelant <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> ou `GlobalFree`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_native.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  

## <a name="marshal_bstr"></a> Marshaler des chaînes BSTR pour ADO.NET
Montre comment ajouter une chaîne COM (`BSTR`) à une base de données et comment marshaler un <xref:System.String?displayProperty=fullName> à partir d’une base de données à un `BSTR`.  
  
### <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir des types managés, le `gcroot` mot clé est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédente directive `main`. Dans cet exemple, nous allons créant une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et remplir quelques lignes dans la table. Notez que les chaînes COM sont passées en tant que valeurs pour la colonne de base de données StringCol. Au sein de DatabaseClass, ces chaînes sont marshalées vers des chaînes managées à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> est utilisée pour marshaler un `BSTR` à un <xref:System.String>et la méthode <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> est utilisée pour marshaler un <xref:System.String> à un `BSTR`.  
  
> [!NOTE]
>  La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> doit être libérée en appelant <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> ou `SysFreeString`.  
  
``` cpp 
// adonet_marshal_string_bstr.cpp  
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
  
    void AddRow(BSTR stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringBSTR(  
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
  
    int GetValuesForColumn(BSTR dataColumn, BSTR *values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringBSTR(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a BSTR.  
            values[i] = (BSTR)Marshal::StringToBSTR(  
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
  
    BSTR str1 = SysAllocString(L"This is string 1.");  
    db->AddRow(str1);  
  
    BSTR str2 = SysAllocString(L"This is string 2.");  
    db->AddRow(str2);  
  
    // Now retrieve the rows and display their contents.  
    BSTR values[MAXCOLS];  
    BSTR str3 = SysAllocString(L"StringCol");  
    int len = db->GetValuesForColumn(  
        str3, values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToBSTR.  
        SysFreeString(values[i]);  
    }  
  
    SysFreeString(str1);  
    SysFreeString(str2);  
    SysFreeString(str3);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
### <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_native.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  

## <a name="marshal_unicode"></a> Marshaler des chaînes Unicode pour ADO.NET
Montre comment ajouter une chaîne Unicode native (`wchar_t *`) à une base de données et comment marshaler un <xref:System.String?displayProperty=fullName> à partir d’une base de données vers une chaîne Unicode native.  
  
### <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir des types managés, le `gcroot` mot clé est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédente directive `main`. Dans cet exemple, nous allons créant une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et remplir quelques lignes dans la table. Notez que les chaînes Unicode C++ sont passées en tant que valeurs pour la colonne de base de données StringCol. Au sein de DatabaseClass, ces chaînes sont marshalées vers des chaînes managées à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> est utilisée pour marshaler un `wchar_t *` à un <xref:System.String>et la méthode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> est utilisée pour marshaler un <xref:System.String> à un `wchar_t *`.  
  
> [!NOTE]
>  La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> doit être libérée en appelant <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> ou `GlobalFree`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_wide.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  

## <a name="marshal_variant"></a> Marshaler un VARIANT pour ADO.NET
Montre comment ajouter un natif `VARIANT` à une base de données et comment marshaler un <xref:System.Object?displayProperty=fullName> à partir d’une base de données native `VARIANT`.  
  
### <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir des types managés, le `gcroot` mot clé est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédente directive `main`. Dans cet exemple, nous allons créant une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et remplir quelques lignes dans la table. Notez que natif `VARIANT` types sont passés en tant que valeurs pour la colonne de base de données ObjectCol. Au sein de DatabaseClass, ces `VARIANT` types sont marshalés vers les objets managés à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> est utilisée pour marshaler un `VARIANT` à un <xref:System.Object>et la méthode <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> est utilisée pour marshaler un <xref:System.Object> à un `VARIANT`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_variant.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  

## <a name="marshal_safearray"></a> Marshaler un SAFEARRAY pour ADO.NET
Montre comment ajouter un natif `SAFEARRAY` à une base de données et comment marshaler un tableau managé à partir d’une base de données native `SAFEARRAY`.  
  
### <a name="example"></a>Exemple  
 Dans cet exemple, la classe DatabaseClass est créée pour interagir avec un élément ADO.NET <xref:System.Data.DataTable> objet. Notez que cette classe est un code C++ natif `class` (par rapport à un `ref class` ou `value class`). Cela est nécessaire, car nous souhaitons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser des types managés en code natif. Cette classe sera compilée pour cibler le CLR, comme indiqué par la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, consultez [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Notez le membre privé de la classe DatabaseClass : `gcroot<DataTable ^> table`. Étant donné que les types natifs ne peut pas contenir des types managés, le `gcroot` mot clé est nécessaire. Pour plus d’informations sur `gcroot`, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Le reste du code dans cet exemple est le code C++ natif, comme indiqué par le `#pragma unmanaged` précédente directive `main`. Dans cet exemple, nous allons créant une nouvelle instance de DatabaseClass et appeler ses méthodes pour créer une table et remplir quelques lignes dans la table. Notez que natif `SAFEARRAY` types sont passés en tant que valeurs pour la colonne de base de données ArrayIntsCol. Au sein de DatabaseClass, ces `SAFEARRAY` types sont marshalés vers les objets managés à l’aide des fonctionnalités de marshaling trouvées dans le <xref:System.Runtime.InteropServices?displayProperty=fullName> espace de noms. Plus précisément, la méthode <xref:System.Runtime.InteropServices.Marshal.Copy%2A> est utilisée pour marshaler un `SAFEARRAY` vers un tableau managé d’entiers et la méthode <xref:System.Runtime.InteropServices.Marshal.Copy%2A> est utilisée pour marshaler un tableau managé d’entiers à une `SAFEARRAY`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Compilation du code  
  
-   Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_safearray.cpp et entrez l’instruction suivante :  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations sur les problèmes de sécurité impliquant ADO.NET, consultez [sécurisation des Applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  

## <a name="related-sections"></a>Rubriques connexes  
  
|Section|Description|  
|-------------|-----------------|  
|[ADO.NET](/dotnet/framework/data/adonet/index)|Fournit une vue d’ensemble d’ADO.NET, un ensemble de classes qui exposent les services d’accès aux données au programmeur .NET.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

 <xref:System.Runtime.InteropServices>   

 [Interopérabilité](https://msdn.microsoft.com/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
