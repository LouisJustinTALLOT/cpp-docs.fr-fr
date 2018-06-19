---
title: Prise en charge des itérateurs de débogage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9153d5e85540c50e11e096c33c474f1344d3ad2f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846205"
---
# <a name="debug-iterator-support"></a>Debug Iterator Support

La bibliothèque Runtime Visual C++ détecte l’utilisation d’itérateurs incorrects, et effectue une assertion et affiche une boîte de dialogue au moment de l’exécution. Pour activer la prise en charge des itérateurs de débogage, vous devez utiliser les versions Debug de la bibliothèque C++ Standard et de la bibliothèque Runtime C pour compiler votre programme. Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md). Pour plus d’informations sur l’utilisation d’itérateurs vérifiés, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

La norme C++ décrit comment les fonctions membres peuvent entraîner la non-validité des itérateurs vers un conteneur. En voici deux exemples:

- La suppression d’un élément d’un conteneur entraîne la non-validité des itérateurs vers l’élément.

- L’augmentation de la taille d’un [vecteur](../standard-library/vector.md) à l’aide de push ou insert entraîne la non-validité des itérateurs dans le `vector`.

## <a name="example"></a>Exemple

Si vous compilez cet exemple de programme en mode débogage, au moment de l’exécution il effectue une assertion et s’arrête.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="example"></a>Exemple

Vous pouvez utiliser la macro de préprocesseur [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) pour désactiver la fonctionnalité de débogage des itérateurs dans une version Debug. Ce programme n’effectue pas d’assertion, mais déclenche un comportement non défini.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="example"></a>Exemple

Une assertion se produit également si vous essayez d’utiliser un itérateur avant son initialisation, comme illustré ici :

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="example"></a>Exemple

L’exemple de code suivant provoque une assertion, car les deux itérateurs vers l’algorithme [for_each](../standard-library/algorithm-functions.md#for_each) ne sont pas compatibles. Les algorithmes vérifient si les itérateurs qui leur sont fournis référencent le même conteneur.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1;
    vector<int> v2;

    v1.push_back(10);
    v1.push_back(20);

    v2.push_back(10);
    v2.push_back(20);

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

Notez que cet exemple utilise l’expression lambda `[] (int& elem) { elem *= 2; }` au lieu d’un foncteur. Bien que ce choix n’ait aucune incidence sur l’échec de l’assertion (un foncteur similaire entraîne un échec de la même façon), les expressions lambda sont un moyen très utile d’accomplir des tâches d’objet de fonction compact. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="example"></a>Exemple

La vérification des itérateur de débogage provoque également une variable d’itérateur déclarée dans une boucle `for` comme étant hors de portée quand la portée de la boucle `for` se termine.

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="example"></a>Exemple

Les itérateurs de débogage ont des destructeurs non triviaux. Si un destructeur ne s’exécute pas pour une raison quelconque, des violations d’accès et une altération des données peuvent se produire. Considérez cet exemple :

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
