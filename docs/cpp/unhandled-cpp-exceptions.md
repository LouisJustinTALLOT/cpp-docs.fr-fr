---
title: Exceptions C++ non gérées
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: 48b417c48a3cbb903f3fabaf31b1423e79a1a414
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233585"
---
# <a name="unhandled-c-exceptions"></a>Exceptions C++ non gérées

Si un gestionnaire correspondant (ou **`catch`** Gestionnaire de points de suspension) est introuvable pour l’exception actuelle, la fonction runtime prédéfinie `terminate` est appelée. (Vous pouvez également appeler explicitement `terminate` dans l’un de vos gestionnaires.) L’action par défaut de `terminate` est d’appeler `abort` . Si vous souhaitez `terminate` pour appeler une autre fonction dans votre programme avant de quitter l’application, appelez la fonction `set_terminate` avec le nom de la fonction à appeler comme unique argument. Vous pouvez appeler `set_terminate` à tout moment dans votre programme. La `terminate` routine appelle toujours la dernière fonction donnée comme argument à `set_terminate` .

## <a name="example"></a>Exemple

L'exemple suivant lève une exception `char *`, mais ne contient pas de gestionnaire désigné pour intercepter des exceptions de type `char *`. L'appel à `set_terminate` indique à `terminate` d'appeler `term_func`.

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>Output

```Output
term_func was called by terminate.
```

La fonction `term_func` doit terminer le programme ou le thread actuel, de préférence en appelant `exit`. Si elle ne fait pas cela et revient à la place à son appelant, la fonction `abort` est appelée.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)
