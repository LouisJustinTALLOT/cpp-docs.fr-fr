---
title: Range-based for, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1284e4f6e096ab8021c597b841a8e983673561bd
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942909"
---
# <a name="range-based-for-statement-c"></a>Basé sur une plage, instruction (C++)
Exécute `statement` à plusieurs reprises et de façon séquentielle pour chaque élément dans `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>Notes  
 Utiliser la plage **pour** instruction pour créer des boucles qui doivent s’exécuter via un « range », ce qui est définie comme tout ce que vous pouvez itérer sur — par exemple, `std::vector`, ou dont la plage de séquence de toute autre bibliothèque Standard C++ est défini par un `begin()` et `end()`. Le nom qui est déclaré dans le `for-range-declaration` partie est locale pour le **pour** instruction et ne peut pas être déclarée de nouveau dans `expression` ou `statement`. Notez que le [automatique](../cpp/auto-cpp.md) mot clé, il est recommandé dans la `for-range-declaration` partie de l’instruction. 

 **Nouveautés de Visual Studio 2017 :** Range-based pour les boucles ne nécessitent plus que begin() et end() retournent des objets du même type. Ainsi, end() peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies selon la proposition Ranges-V3. Pour plus d’informations, consultez [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) et la [bibliothèque range-v3 sur GitHub](https://github.com/ericniebler/range-v3).
  
 Ce code montre comment utiliser basé sur une plage **pour** boucles pour itérer un tableau et un vecteur :  
  
```cpp  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by const reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 Voici la sortie :  

```Output
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
```

 Basé sur une plage **pour** boucle termine lorsque un d’eux dans `statement` est exécutée : un [saut](../cpp/break-statement-cpp.md), [retourner](../cpp/return-statement-cpp.md), ou [goto](../cpp/goto-statement-cpp.md) à un élément étiqueté instruction en dehors de la plage basée **pour** boucle. Un [continuer](../cpp/continue-statement-cpp.md) instruction dans basées sur une plage **pour** boucle termine uniquement l’itération actuelle.  
  
 N’oubliez pas ces faits sur basé sur une plage **pour**:  
  
-   Reconnaît automatiquement les tableaux.  
  
-   Reconnaît les conteneurs qui ont `.begin()` et `.end()`.  
  
-   Utilise la recherche dépendante d’un argument `begin()` et `end()` pour tout autre élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Auto](../cpp/auto-cpp.md)   
 [Instructions d’itération](../cpp/iteration-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [while, instruction (C++)](../cpp/while-statement-cpp.md)   
 [do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)   
 [for, instruction (C++)](../cpp/for-statement-cpp.md)