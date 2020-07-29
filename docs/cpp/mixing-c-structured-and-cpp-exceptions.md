---
title: Mélange d’exceptions C (structurées) et C++
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 72ddde9bc284a005c77694d599a8e9a3908cb2d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233689"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mélange d’exceptions C (structurées) et C++

Si vous souhaitez écrire du code portable, l’utilisation de la gestion structurée des exceptions (SEH) dans un programme C++ n’est pas recommandée. Toutefois, vous pouvez parfois souhaiter compiler à l’aide de [/EHa](../build/reference/eh-exception-handling-model.md) et mélanger des exceptions structurées et du code source C++, et avoir besoin d’une fonctionnalité pour gérer les deux types d’exceptions. Comme un gestionnaire d’exceptions structurées n’a pas de concept d’objets ou d’exceptions typées, il ne peut pas gérer les exceptions levées par le code C++. Toutefois, les **`catch`** gestionnaires C++ peuvent gérer des exceptions structurées. La syntaxe de gestion des exceptions C++ ( **`try`** , **`throw`** , **`catch`** ) n’est pas acceptée par le compilateur C, mais la syntaxe de gestion des exceptions structurées (**__try**, **`__except`** , **`__finally`** ) est prise en charge par le compilateur C++.

Pour plus d’informations sur la gestion des exceptions structurées en tant qu’exceptions C++, consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) .

Si vous combinez des exceptions structurées et C++, tenez compte de ces problèmes potentiels :

- Les exceptions C++ et les exceptions structurées ne peuvent pas être mélangées dans la même fonction.

- Les gestionnaires de terminaisons ( **`__finally`** blocs) sont toujours exécutés, même pendant le déroulement après la levée d’une exception.

- La gestion des exceptions C++ peut intercepter et préserver la sémantique de déroulement dans tous les modules compilés avec les options de compilateur [/Eh](../build/reference/eh-exception-handling-model.md) , qui activent la sémantique de déroulement.

- Il peut exister des situations où les fonctions de destructeur ne sont pas appelées pour tous les objets. Par exemple, si une exception structurée se produit lors de la tentative d’effectuer un appel de fonction via un pointeur de fonction non initialisé et que cette fonction prend comme des objets de paramètres construits avant l’appel, les destructeurs de ces objets ne sont pas appelés pendant le déroulement de la pile.

## <a name="next-steps"></a>Étapes suivantes

- [Utilisation de setjmp ou de longjmp dans les programmes C++](../cpp/using-setjmp-longjmp.md)

  Pour plus d’informations sur l’utilisation de `setjmp` et `longjmp` dans les programmes C++, consultez.

- [Gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md)

  Découvrez des exemples de la façon dont vous pouvez utiliser C++ pour gérer les exceptions structurées.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)
