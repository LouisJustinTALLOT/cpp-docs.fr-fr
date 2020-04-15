---
title: Accès aux données à l'aide d'ADO.NET (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364412"
---
# <a name="data-access-using-adonet-ccli"></a>Accès aux données à l'aide d'ADO.NET (C++/CLI)

ADO.NET est l’API cadre .NET pour l’accès aux données et fournit la puissance et la facilité d’utilisation inégalée par les solutions précédentes d’accès aux données. Cette section décrit quelques-unes des questions concernant les ADO.NET qui sont uniques aux utilisateurs de Visual C, comme le marshaling des types autochtones.

ADO.NET s’exécute sous le Common Language Runtime (CLR). Par conséquent, toute application qui interagit avec ADO.NET doit également cibler le CLR. Toutefois, cela ne signifie pas que les applications autochtones ne peuvent pas utiliser ADO.NET. Ces exemples montreront comment interagir avec une base de données ADO.NET à partir de code natif.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Marshal ANSI Cordes pour ADO.NET

Démontre comment ajouter une chaîne`char *`native ( ) à <xref:System.String?displayProperty=fullName> une base de données et comment mobiliser un d’une base de données à une chaîne indigène.

### <a name="example"></a>Exemple

Dans cet exemple, la classe DatabaseClass est créée <xref:System.Data.DataTable> pour interagir avec un objet ADO.NET. Notez que cette classe est `class` un C `ref class` natif `value class`(par rapport à un ou ). Ceci est nécessaire parce que nous voulons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser les types gérés dans le code natif. Cette catégorie sera compilée pour cibler le CLR, comme l’indique la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, voir [géré, non géré](../preprocessor/managed-unmanaged.md).

Notez le membre privé de `gcroot<DataTable ^> table`la classe DatabaseClass: . Étant donné que les types `gcroot` natifs ne peuvent pas contenir de types gérés, le mot clé est nécessaire. Pour plus `gcroot`d’informations sur , voir [Comment: Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

Le reste du code dans cet exemple est le code `#pragma unmanaged` Cô `main`natif, comme l’indique la directive précédente . Dans cet exemple, nous créons une nouvelle instance de DatabaseClass et appelons ses méthodes pour créer une table et peupler quelques rangées dans le tableau. Notez que les chaînes natives de CMD sont passées comme valeurs pour la colonne de base de données StringCol. À l’intérieur de DatabaseClass, ces cordes sont assemblées à <xref:System.Runtime.InteropServices?displayProperty=fullName> des chaînes gérées en utilisant la fonctionnalité de marshaling trouvée dans l’espace de nom. Plus précisément, <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> la méthode `char *` est <xref:System.String>utilisée pour <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> marshal a, <xref:System.String> et `char *`la méthode est utilisée pour marshal a .

> [!NOTE]
> La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> deallocated en appelant soit ou `GlobalFree`.

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

- Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_native.cpp et entrez la déclaration suivante :

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Marshal BSTR Cordes pour ADO.NET

Démontre comment ajouter une chaîne`BSTR`COM ( ) à <xref:System.String?displayProperty=fullName> une base de `BSTR`données et comment mobiliser un d’une base de données à un .

### <a name="example"></a>Exemple

Dans cet exemple, la classe DatabaseClass est créée <xref:System.Data.DataTable> pour interagir avec un objet ADO.NET. Notez que cette classe est `class` un C `ref class` natif `value class`(par rapport à un ou ). Ceci est nécessaire parce que nous voulons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser les types gérés dans le code natif. Cette catégorie sera compilée pour cibler le CLR, comme l’indique la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, voir [géré, non géré](../preprocessor/managed-unmanaged.md).

Notez le membre privé de `gcroot<DataTable ^> table`la classe DatabaseClass: . Étant donné que les types `gcroot` natifs ne peuvent pas contenir de types gérés, le mot clé est nécessaire. Pour plus `gcroot`d’informations sur , voir [Comment: Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

Le reste du code dans cet exemple est le code `#pragma unmanaged` Cô `main`natif, comme l’indique la directive précédente . Dans cet exemple, nous créons une nouvelle instance de DatabaseClass et appelons ses méthodes pour créer une table et peupler quelques rangées dans le tableau. Notez que les chaînes COM sont passées comme valeurs pour la colonne de base de données StringCol. À l’intérieur de DatabaseClass, ces cordes sont assemblées à <xref:System.Runtime.InteropServices?displayProperty=fullName> des chaînes gérées en utilisant la fonctionnalité de marshaling trouvée dans l’espace de nom. Plus précisément, <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> la méthode `BSTR` est <xref:System.String>utilisée pour <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> marshal a, <xref:System.String> et `BSTR`la méthode est utilisée pour marshal a .

> [!NOTE]
> La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> doit être <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> deallocated en appelant soit ou `SysFreeString`.

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

- Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_native.cpp et entrez la déclaration suivante :

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Marshal Unicode Cordes pour ADO.NET

Démontre comment ajouter une chaîne Unicode natif (`wchar_t *`) à <xref:System.String?displayProperty=fullName> une base de données et comment mobiliser une base de données à une chaîne Unicode indigène.

### <a name="example"></a>Exemple

Dans cet exemple, la classe DatabaseClass est créée <xref:System.Data.DataTable> pour interagir avec un objet ADO.NET. Notez que cette classe est `class` un C `ref class` natif `value class`(par rapport à un ou ). Ceci est nécessaire parce que nous voulons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser les types gérés dans le code natif. Cette catégorie sera compilée pour cibler le CLR, comme l’indique la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, voir [géré, non géré](../preprocessor/managed-unmanaged.md).

Notez le membre privé de `gcroot<DataTable ^> table`la classe DatabaseClass: . Étant donné que les types `gcroot` natifs ne peuvent pas contenir de types gérés, le mot clé est nécessaire. Pour plus `gcroot`d’informations sur , voir [Comment: Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

Le reste du code dans cet exemple est le code `#pragma unmanaged` Cô `main`natif, comme l’indique la directive précédente . Dans cet exemple, nous créons une nouvelle instance de DatabaseClass et appelons ses méthodes pour créer une table et peupler quelques rangées dans le tableau. Notez que les chaînes Unicode CMD sont passées comme valeurs pour la colonne de base de données StringCol. À l’intérieur de DatabaseClass, ces cordes sont assemblées à <xref:System.Runtime.InteropServices?displayProperty=fullName> des chaînes gérées en utilisant la fonctionnalité de marshaling trouvée dans l’espace de nom. Plus précisément, <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> la méthode `wchar_t *` est <xref:System.String>utilisée pour <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> marshal a, <xref:System.String> et `wchar_t *`la méthode est utilisée pour marshal a .

> [!NOTE]
> La mémoire allouée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> doit être <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> deallocated en appelant soit ou `GlobalFree`.

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

- Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_string_wide.cpp et entrez la déclaration suivante :

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Maréchal un VARIANT pour ADO.NET

Démontre comment ajouter un `VARIANT` natif à une base <xref:System.Object?displayProperty=fullName> de données et `VARIANT`comment mobiliser un d’une base de données à un natif .

### <a name="example"></a>Exemple

Dans cet exemple, la classe DatabaseClass est créée <xref:System.Data.DataTable> pour interagir avec un objet ADO.NET. Notez que cette classe est `class` un C `ref class` natif `value class`(par rapport à un ou ). Ceci est nécessaire parce que nous voulons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser les types gérés dans le code natif. Cette catégorie sera compilée pour cibler le CLR, comme l’indique la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, voir [géré, non géré](../preprocessor/managed-unmanaged.md).

Notez le membre privé de `gcroot<DataTable ^> table`la classe DatabaseClass: . Étant donné que les types `gcroot` natifs ne peuvent pas contenir de types gérés, le mot clé est nécessaire. Pour plus `gcroot`d’informations sur , voir [Comment: Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

Le reste du code dans cet exemple est le code `#pragma unmanaged` Cô `main`natif, comme l’indique la directive précédente . Dans cet exemple, nous créons une nouvelle instance de DatabaseClass et appelons ses méthodes pour créer une table et peupler quelques rangées dans le tableau. Notez `VARIANT` que les types natifs sont adoptés comme valeurs pour la colonne de base de données ObjectCol. À l’intérieur `VARIANT` de DatabaseClass, ces types sont mobilisés <xref:System.Runtime.InteropServices?displayProperty=fullName> pour gérer les objets en utilisant la fonctionnalité de marshaling trouvée dans l’espace de nom. Plus précisément, <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> la méthode `VARIANT` est <xref:System.Object>utilisée pour <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> marshal a à <xref:System.Object> un `VARIANT`, et la méthode est utilisée pour mobiliser un à un .

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

- Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_variant.cpp et entrez la déclaration suivante :

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Marshal un SAFEARRAY pour ADO.NET

Démontre comment ajouter un `SAFEARRAY` natif à une base de données et comment `SAFEARRAY`mobiliser un tableau géré d’une base de données à un natif .

### <a name="example"></a>Exemple

Dans cet exemple, la classe DatabaseClass est créée <xref:System.Data.DataTable> pour interagir avec un objet ADO.NET. Notez que cette classe est `class` un C `ref class` natif `value class`(par rapport à un ou ). Ceci est nécessaire parce que nous voulons utiliser cette classe à partir de code natif, et vous ne pouvez pas utiliser les types gérés dans le code natif. Cette catégorie sera compilée pour cibler le CLR, comme l’indique la `#pragma managed` directive précédant la déclaration de classe. Pour plus d’informations sur cette directive, voir [géré, non géré](../preprocessor/managed-unmanaged.md).

Notez le membre privé de `gcroot<DataTable ^> table`la classe DatabaseClass: . Étant donné que les types `gcroot` natifs ne peuvent pas contenir de types gérés, le mot clé est nécessaire. Pour plus `gcroot`d’informations sur , voir [Comment: Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

Le reste du code dans cet exemple est le code `#pragma unmanaged` Cô `main`natif, comme l’indique la directive précédente . Dans cet exemple, nous créons une nouvelle instance de DatabaseClass et appelons ses méthodes pour créer une table et peupler quelques rangées dans le tableau. Notez `SAFEARRAY` que les types natifs sont adoptés comme valeurs pour la colonne de base de données ArrayIntsCol. À l’intérieur `SAFEARRAY` de DatabaseClass, ces types sont mobilisés <xref:System.Runtime.InteropServices?displayProperty=fullName> pour gérer les objets en utilisant la fonctionnalité de marshaling trouvée dans l’espace de nom. Plus précisément, <xref:System.Runtime.InteropServices.Marshal.Copy%2A> la méthode `SAFEARRAY` est utilisée pour mobiliser un tableau géré <xref:System.Runtime.InteropServices.Marshal.Copy%2A> d’intégrants, et la méthode `SAFEARRAY`est utilisée pour mobiliser un tableau géré d’intégrants à un .

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

- Pour compiler le code à partir de la ligne de commande, enregistrez l’exemple de code dans un fichier nommé adonet_marshal_safearray.cpp et entrez la déclaration suivante :

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>Sécurité du .NET Framework

Pour plus d’informations sur les questions de sécurité impliquant ADO.NET, voir [Sécurisation des applications ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Sections connexes

|Section|Description|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Fournit un aperçu de ADO.NET, un ensemble de classes qui exposent les services d’accès aux données au programmeur .NET.|

## <a name="see-also"></a>Voir aussi

[.NET Programmation avec CMD/CLI (Visual CMD)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Interopérabilité](/dotnet/framework/interop/index)
