---
title: Utilisation de setjmp et longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 4ead12f79701899b3977993c9de3c3803023150f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364517"
---
# <a name="using-setjmp-and-longjmp"></a>Utilisation de setjmp et longjmp

Lorsque [setjmp](../c-runtime-library/reference/setjmp.md) et [longjmp](../c-runtime-library/reference/longjmp.md) sont utilisés conjointement, ils fournissent un moyen d’exécuter non local **goto**. Ils sont généralement utilisés dans le code C pour passer le contrôle de l’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser l’appel standard ou les conventions de retour.

> [!CAUTION]
> Étant donné que `setjmp` et `longjmp` ne prennent pas en charge la destruction correcte des objets de frame de pile façon portable entre les compilateurs C++ et car elles peuvent dégrader les performances en empêchant l’optimisation sur les variables locales, nous vous déconseillons leur utilisation dans C++ programmes. Nous vous recommandons d’utiliser **essayez** et **catch** construit à la place.

Si vous décidez d’utiliser `setjmp` et `longjmp` dans un programme C++, également inclure \<setjmp.h > ou \<setjmpex.h > afin d’assurer une bonne interaction entre les fonctions et l’exception de gestion des exceptions structurées (SEH) ou C++ gestion.

**Section spécifique à Microsoft**

Si vous utilisez un [/EH](../build/reference/eh-exception-handling-model.md) option pour compiler le code C++, les destructeurs pour les objets locaux sont appelés durant le désempilage. Toutefois, si vous utilisez **/EHs** ou **/EHsc** à la compilation et celui de vos fonctions qui utilise [noexcept](../cpp/noexcept-cpp.md) appels `longjmp`, puis le destructeur de déroulement pour cette fonction peut pas se produire, selon l’état de l’optimiseur.

Dans le code portable, lorsqu’un `longjmp` appel est exécuté, destruction correcte des objets basés sur le frame n’est pas explicitement garantie par la norme et ne peut pas être pris en charge par d’autres compilateurs. Pour vous permettre de connaître, au niveau d’avertissement 4, un appel à `setjmp` avertissement C4611 : interaction entre '_setjmp' et C++ la destruction d’objets n’est pas portable.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mélange d’exceptions C (structurées) et d’exceptions C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
