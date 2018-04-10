---
title: 'Comment : convertir une collection .NET en conteneur STL/CLR | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6366dd10e60d8f2ea60811f74ba2b2e10457dd84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Comment : convertir une collection .NET en conteneur STL/CLR
Cette rubrique montre comment convertir en collections .NET leurs conteneurs STL/CLR équivalents. Par exemple, nous montrons comment convertir un .NET <xref:System.Collections.Generic.List%601> à un STL/CLR [vecteur](../dotnet/vector-stl-clr.md) et comment convertir un .NET <xref:System.Collections.Generic.Dictionary%602> à un STL/CLR [carte](../dotnet/map-stl-clr.md), mais la procédure est identique pour tous les conteneurs et les collections .  
  
### <a name="to-create-a-container-from-a-collection"></a>Pour créer un conteneur d’une collection  
  
1.  Pour convertir une collection entière, créer un conteneur STL/CLR et passez la collection au constructeur.  
  
     Le premier exemple illustre cette procédure.  
  
 - OU -  
  
1.  Créer un conteneur STL/CLR générique en créant un [collection_adapter](../dotnet/collection-adapter-stl-clr.md) objet. Cette classe de modèle prend une interface de collection .NET en tant qu’argument. Pour vérifier que les interfaces sont prises en charge, consultez [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).  
  
2.  Copiez le contenu de la collection .NET au conteneur. Cela est possible en utilisant un STL/CLR [algorithme](../dotnet/algorithm-stl-clr.md), ou en effectuer une itération au sein de la collection .NET et l’insertion d’une copie de chaque élément dans le conteneur STL/CLR.  
  
     Le deuxième exemple illustre cette procédure.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, nous créons un générique <xref:System.Collections.Generic.List%601> et ajouter des éléments de 5. Ensuite, nous créons un `vector` à l’aide du constructeur qui prend un <xref:System.Collections.Generic.IEnumerable%601> en tant qu’argument.  
  
```  
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
  
## <a name="example"></a>Exemple  
 Dans cet exemple, nous créons un générique <xref:System.Collections.Generic.Dictionary%602> et ajouter des éléments de 5. Ensuite, nous créons un `collection_adapter` pour encapsuler la <xref:System.Collections.Generic.Dictionary%602> comme un simple conteneur STL/CLR. Enfin, nous créons un `map` et copiez le contenu de la <xref:System.Collections.Generic.Dictionary%602> à la `map` en effectuant une itération sur la `collection_adapter`. Pendant ce processus, nous créer une nouvelle paire en utilisant la `make_pair` , la fonction et insérez la nouvelle paire directement dans le `map`.  
  
```  
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
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)   
 [adaptateur (STL/CLR)](../dotnet/adapter-stl-clr.md)   
 [Guide pratique pour convertir un conteneur STL/CLR en collection .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)