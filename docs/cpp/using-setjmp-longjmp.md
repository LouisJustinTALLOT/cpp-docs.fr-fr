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
ms.openlocfilehash: 6adbe22eb684c9a1dda080f6d35a99c55d6c3d30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226995"
---
# <a name="using-setjmp-and-longjmp"></a>Utilisation de setjmp et longjmp

Lorsque [setjmp](../c-runtime-library/reference/setjmp.md) et [longjmp](../c-runtime-library/reference/longjmp.md) sont utilisés ensemble, ils offrent un moyen d’exécuter un non local **`goto`** . Elles sont généralement utilisées dans le code C pour passer le contrôle d’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour standard.

> [!CAUTION]
> Étant donné que `setjmp` et `longjmp` ne prennent pas en charge la destruction correcte des objets de frame de pile portables entre les compilateurs C++, et parce qu’ils risquent de nuire aux performances en empêchant l’optimisation sur les variables locales, nous ne recommandons pas leur utilisation dans les programmes C++. Nous vous recommandons d’utiliser à la **`try`** **`catch`** place des constructions et.

Si vous décidez d’utiliser `setjmp` et `longjmp` dans un programme C++, incluez également \<setjmp.h> ou \<setjmpex.h> pour garantir une interaction correcte entre les fonctions et la gestion structurée des exceptions (SEH) ou la gestion des exceptions C++.

**Spécifique à Microsoft**

Si vous utilisez une option [/Eh](../build/reference/eh-exception-handling-model.md) pour compiler du code C++, les destructeurs des objets locaux sont appelés pendant le déroulement de la pile. Toutefois, si vous utilisez **/EHS** ou **/EHsc** pour compiler, et l’une de vos fonctions qui utilisent des appels [noexcept](../cpp/noexcept-cpp.md) `longjmp` , le déroulement du destructeur pour cette fonction peut ne pas se produire, selon l’état de l’optimiseur.

Dans le code portable, lorsqu’un `longjmp` appel est exécuté, la destruction correcte des objets basés sur des frames n’est pas garantie explicitement par la norme et peut ne pas être prise en charge par d’autres compilateurs. Pour vous avertir, au niveau de l’avertissement 4, un appel à `setjmp` provoque l’avertissement C4611 : l’interaction entre' _setjmp’et la destruction d’objet C++ n’est pas portable.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mélange d’exceptions C (structurées) et C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
