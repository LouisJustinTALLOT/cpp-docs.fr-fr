---
title: 'Comment : convertir à partir d’un conteneur STL/CLR en Collection .NET | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7fb4938121d1d2beed3133bee6013e17d37f1402
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132006"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Comment : convertir un conteneur STL/CLR en collection .NET
Cette rubrique montre comment convertir des conteneurs STL/CLR à leurs collections .NET équivalentes. Par exemple, nous montrons comment convertir un STL/CLR [vecteur](../dotnet/vector-stl-clr.md) à .NET <xref:System.Collections.Generic.ICollection%601> et comment convertir un STL/CLR [carte](../dotnet/map-stl-clr.md) à .NET <xref:System.Collections.Generic.IDictionary%602>, mais la procédure est identique pour toutes les collections et conteneurs.  
  
### <a name="to-create-a-collection-from-a-container"></a>Pour créer une collection à partir d’un conteneur  
  
1.  Utilisez une des méthodes suivantes :  
  
    -   Pour convertir la partie d’un conteneur, appelez le [make_collection](../dotnet/make-collection-stl-clr.md) , la fonction et transmettre l’itérateur de début et l’itérateur de fin du conteneur STL/CLR à copier dans la collection .NET. Cette fonction avec modèle prend un itérateur STL/CLR comme argument de modèle. Le premier exemple illustre cette méthode.  
  
    -   Pour convertir un conteneur entier, effectué le conteneur à une interface de collection .NET appropriée ou de la collection de l’interface. Le deuxième exemple illustre cette méthode.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, nous créons un STL/CLR `vector` et ajouter des éléments de 5. Ensuite, nous créer une collection .NET en appelant le `make_collection` (fonction). Enfin, nous afficher le contenu de la collection nouvellement créé.  
  
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
 Dans cet exemple, nous créons un STL/CLR `map` et ajouter des éléments de 5. Ensuite, nous créons un .NET <xref:System.Collections.Generic.IDictionary%602> et affecter le `map` directement. Enfin, nous afficher le contenu de la collection nouvellement créé.  
  
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
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)   
 [Comment : convertir une collection .NET en conteneur STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)