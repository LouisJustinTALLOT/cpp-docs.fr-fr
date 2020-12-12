---
description: 'En savoir plus sur : Comment : effectuer une conversion à partir d’un conteneur STL/CLR en collection .NET'
title: 'Comment : convertir un conteneur STL/CLR en collection .NET'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: 93649ae411c53d21db5e660d8faa6aa707f74f16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181304"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Comment : convertir un conteneur STL/CLR en collection .NET

Cette rubrique montre comment convertir des conteneurs STL/CLR en leurs collections .NET équivalentes. À titre d’exemple, nous montrons comment convertir un [vecteur](../dotnet/vector-stl-clr.md) STL/CLR en .NET <xref:System.Collections.Generic.ICollection%601> et comment convertir un [mappage](../dotnet/map-stl-clr.md) STL/CLR en .NET <xref:System.Collections.Generic.IDictionary%602> , mais la procédure est similaire pour tous les regroupements et conteneurs.

### <a name="to-create-a-collection-from-a-container"></a>Pour créer une collection à partir d’un conteneur

1. Appliquez l'une des méthodes suivantes :

   - Pour convertir une partie d’un conteneur, appelez la fonction [make_collection](./adapter-stl-clr.md#make_collection) et passez l’itérateur Begin et l’itérateur de fin du conteneur STL/CLR à copier dans la collection .net. Cette fonction de modèle prend un itérateur STL/CLR comme argument de modèle. Le premier exemple illustre cette méthode.

   - Pour convertir un conteneur entier, effectuez un cast du conteneur en une interface de collection .NET ou une collection d’interfaces appropriée. Le deuxième exemple illustre cette méthode.

## <a name="examples"></a>Exemples

Dans cet exemple, nous créons un STL/CLR `vector` et nous y ajoutons 5 éléments. Ensuite, nous créons une collection .NET en appelant la `make_collection` fonction. Enfin, nous affichons le contenu de la collection nouvellement créée.

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

Dans cet exemple, nous créons un STL/CLR `map` et nous y ajoutons 5 éléments. Ensuite, nous créons un .NET <xref:System.Collections.Generic.IDictionary%602> et nous lui affectons `map` directement. Enfin, nous affichons le contenu de la collection nouvellement créée.

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Comment : effectuer une conversion à partir d’une collection .NET vers un conteneur STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](./adapter-stl-clr.md#range_adapter)
