---
title: 'Procédure : Convertir à partir d’un conteneur STL/CLR en Collection .NET'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: cf67e362751dd164916cc94cd644d55110d88a5f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751581"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Procédure : Convertir à partir d’un conteneur STL/CLR en Collection .NET

Cette rubrique montre comment convertir des conteneurs STL/CLR en leurs équivalentes collections .NET. Par exemple, nous montrons comment convertir un STL/CLR [vecteur](../dotnet/vector-stl-clr.md) à .NET <xref:System.Collections.Generic.ICollection%601> et comment convertir un STL/CLR [carte](../dotnet/map-stl-clr.md) à .NET <xref:System.Collections.Generic.IDictionary%602>, mais la procédure est similaire pour toutes les collections et conteneurs.

### <a name="to-create-a-collection-from-a-container"></a>Pour créer une collection à partir d’un conteneur

1. Utilisez une des méthodes suivantes :

   - Pour convertir la partie d’un conteneur, appelez le [make_collection](../dotnet/make-collection-stl-clr.md) fonctionner et transmettre l’itérateur de début et l’itérateur de fin du conteneur STL/CLR doit être copié dans la collection .NET. Cette fonction de modèle prend un itérateur STL/CLR comme un argument de modèle. Le premier exemple illustre cette méthode.

   - Pour convertir un conteneur entier, effectuez un cast du conteneur à une interface de collection .NET appropriée ou la collection de l’interface. Le deuxième exemple illustre cette méthode.

## <a name="example"></a>Exemple

Dans cet exemple, nous créons un STL/CLR `vector` et lui ajouter 5 éléments. Ensuite, nous créons une collection .NET en appelant le `make_collection` (fonction). Enfin, nous affichons le contenu de la collection qui vient d’être créée.

```
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

## <a name="example"></a>Exemple

Dans cet exemple, nous créons un STL/CLR `map` et lui ajouter 5 éléments. Ensuite, nous créons un .NET <xref:System.Collections.Generic.IDictionary%602> et affecter le `map` directement. Enfin, nous affichons le contenu de la collection qui vient d’être créée.

```
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

[Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Guide pratique pour convertir une collection .NET en conteneur STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
