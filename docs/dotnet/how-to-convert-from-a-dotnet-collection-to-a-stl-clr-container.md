---
title: 'Comment : convertir une collection .NET en conteneur STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: a7b2ee94f02e663690287ecfa6bc8a7230830a95
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686455"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Comment : convertir une collection .NET en conteneur STL/CLR

Cette rubrique montre comment convertir des collections .NET en leurs conteneurs STL/CLR équivalents. À titre d’exemple, nous montrons comment convertir un .NET <xref:System.Collections.Generic.List%601> en [vecteur](../dotnet/vector-stl-clr.md) STL/CLR et comment convertir un .NET <xref:System.Collections.Generic.Dictionary%602> en [mappage](../dotnet/map-stl-clr.md)STL/CLR, mais la procédure est similaire pour toutes les collections et tous les conteneurs.

### <a name="to-create-a-container-from-a-collection"></a>Pour créer un conteneur à partir d’une collection

1. Pour convertir une collection entière, créez un conteneur STL/CLR et passez la collection au constructeur.

   Le premier exemple illustre cette procédure.

OU

1. Créez un conteneur STL/CLR générique en créant un objet [collection_adapter](../dotnet/collection-adapter-stl-clr.md) . Cette classe de modèle prend une interface de collection .NET comme argument. Pour vérifier les interfaces prises en charge, consultez [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Copiez le contenu de la collection .NET dans le conteneur. Cela peut être effectué à l’aide d’un [algorithme](../dotnet/algorithm-stl-clr.md)STL/CLR, ou en effectuant une itération sur la collection .net et en insérant une copie de chaque élément dans le conteneur STL/CLR.

   Le deuxième exemple illustre cette procédure.

## <a name="examples"></a>Exemples

Dans cet exemple, nous créons un générique <xref:System.Collections.Generic.List%601> et nous y ajoutons 5 éléments. Ensuite, nous créons un `vector` à l’aide du constructeur qui prend un <xref:System.Collections.Generic.IEnumerable%601> comme argument.

```cpp
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

Dans cet exemple, nous créons un générique <xref:System.Collections.Generic.Dictionary%602> et nous y ajoutons 5 éléments. Ensuite, nous créons un `collection_adapter` pour encapsuler <xref:System.Collections.Generic.Dictionary%602> en tant que conteneur STL/CLR simple. Enfin, nous créons un `map` et copions le contenu de <xref:System.Collections.Generic.Dictionary%602> dans le `map` en effectuant une itération sur le `collection_adapter` . Au cours de ce processus, nous créons une nouvelle paire à l’aide de la `make_pair` fonction, puis nous inséronsons la nouvelle paire directement dans le `map` .

```cpp
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Comment : effectuer une conversion à partir d’un conteneur STL/CLR en collection .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
