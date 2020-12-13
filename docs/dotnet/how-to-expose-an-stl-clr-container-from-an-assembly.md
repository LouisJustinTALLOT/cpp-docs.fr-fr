---
description: 'En savoir plus sur : Comment : exposer un conteneur STL/CLR à partir d’un assembly'
title: "Comment : exposer un conteneur STL/CLR d'un assembly"
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: a4ed92af956def030c80f8f303f0a7501c4944c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134977"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Comment : exposer un conteneur STL/CLR d'un assembly

Les conteneurs STL/CLR, tels que `list` et, `map` sont implémentés en tant que classes Ref de modèle. Étant donné que les modèles C++ sont instanciés au moment de la compilation, deux classes de modèle qui ont exactement la même signature mais qui se trouvent dans des assemblys différents sont en fait des types différents. Cela signifie que les classes de modèle ne peuvent pas être utilisées dans les limites de l’assembly.

Pour que le partage entre assemblys soit possible, les conteneurs STL/CLR implémentent l’interface générique <xref:System.Collections.Generic.ICollection%601> . À l’aide de cette interface générique, tous les langages qui prennent en charge les génériques, y compris C++, C# et Visual Basic, peuvent accéder aux conteneurs STL/CLR.

Cette rubrique montre comment afficher les éléments de plusieurs conteneurs STL/CLR écrits dans un assembly C++ nommé `StlClrClassLibrary` . Nous affichons deux assemblys auxquels accéder `StlClrClassLibrary` . Le premier assembly est écrit en C++ et le second en C#.

Si les deux assemblys sont écrits en C++, vous pouvez accéder à l’interface générique d’un conteneur à l’aide de son `generic_container` typedef. Par exemple, si vous avez un conteneur de type `cliext::vector<int>` , son interface générique est : `cliext::vector<int>::generic_container` . De même, vous pouvez récupérer un itérateur sur l’interface générique à l’aide du `generic_iterator` typedef, comme dans : `cliext::vector<int>::generic_iterator` .

Étant donné que ces typedefs sont déclarés dans les fichiers d’en-tête C++, les assemblys écrits dans d’autres langages ne peuvent pas les utiliser. Par conséquent, pour accéder à l’interface générique pour `cliext::vector<int>` en C# ou tout autre langage .net, utilisez `System.Collections.Generic.ICollection<int>` . Pour itérer au sein de cette collection, utilisez une `foreach` boucle.

Le tableau suivant répertorie l’interface générique implémentée par chaque conteneur STL/CLR :

|Conteneur STL/CLR|Interface générique|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> Étant donné que les `queue` `priority_queue` conteneurs, et `stack` ne prennent pas en charge les itérateurs, ils n’implémentent pas les interfaces génériques et ne sont pas accessibles entre les assemblys.

## <a name="example-1"></a>Exemple 1

### <a name="description"></a>Description

Dans cet exemple, nous déclarons une classe C++ qui contient des données de membre STL/CLR privées. Nous déclarons ensuite les méthodes publiques pour accorder l’accès aux collections privées de la classe. Nous le faisons de deux manières différentes : une pour les clients C++ et une autre pour les clients .NET.

### <a name="code"></a>Code

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>Exemple 2

### <a name="description"></a>Description

Dans cet exemple, nous implémentons la classe déclarée dans l’exemple 1. Pour que les clients utilisent cette bibliothèque de classes, nous utilisons l’outil manifeste **mt.exe** pour incorporer le fichier manifeste dans la dll. Pour plus d’informations, consultez les commentaires de code.

Pour plus d’informations sur l’outil manifeste et les assemblys côte à côte, consultez [génération d’applications isolées C/C++ et d’assemblys côte à côte](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

### <a name="code"></a>Code

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>Exemple 3

### <a name="description"></a>Description

Dans cet exemple, nous créons un client C++ qui utilise la bibliothèque de classes créée dans les exemples 1 et 2. Ce client utilise les `generic_container` typedefs des conteneurs STL/CLR pour itérer au sein des conteneurs et afficher leur contenu.

### <a name="code"></a>Code

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>Exemple 4

### <a name="description"></a>Description

Dans cet exemple, nous créons un client C# qui utilise la bibliothèque de classes créée dans les exemples 1 et 2. Ce client utilise les <xref:System.Collections.Generic.ICollection%601> méthodes des conteneurs STL/CLR pour itérer au sein des conteneurs et afficher leur contenu.

### <a name="code"></a>Code

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
