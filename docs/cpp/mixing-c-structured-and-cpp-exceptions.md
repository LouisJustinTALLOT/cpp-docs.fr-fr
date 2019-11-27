---
title: Mélange de C (structuré) C++ et des exceptions
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246462"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mélange de C (structuré) C++ et des exceptions

Si vous souhaitez écrire du code portable, l’utilisation de la gestion structurée des exceptions (SEH C++ ) dans un programme n’est pas recommandée. Toutefois, vous pouvez parfois souhaiter compiler à l’aide de [/EHa](../build/reference/eh-exception-handling-model.md) et mélanger des C++ exceptions structurées et du code source, et vous avez besoin d’une fonctionnalité pour gérer les deux types d’exceptions. Comme un gestionnaire d’exceptions structurées n’a pas de concept d’objets ou d’exceptions typées, C++ il ne peut pas gérer les exceptions levées par le code. Toutefois, C++ les gestionnaires **catch** peuvent gérer des exceptions structurées. C++la syntaxe de gestion des exceptions (**try**, **throw**, **catch**) n’est pas acceptée par le compilateur C, mais la syntaxe de gestion des exceptions structurées ( **__try**, **__except** **__finally**) est prise en charge par le C++ compilateur.

Consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) pour plus d’informations sur la gestion des exceptions C++ structurées en tant qu’exceptions.

Si vous combinez des C++ exceptions et structurées, tenez compte de ces problèmes potentiels :

- Les exceptions C++ et les exceptions structurées ne peuvent pas être mélangées dans la même fonction.

- Les gestionnaires de terminaisons (blocs **__finally** ) sont toujours exécutés, même pendant le déroulement après la levée d’une exception.

- C++la gestion des exceptions peut intercepter et préserver la sémantique de déroulement dans tous les modules compilés avec les options de compilateur [/Eh](../build/reference/eh-exception-handling-model.md) , qui activent la sémantique de déroulement.

- Il peut exister des situations où les fonctions de destructeur ne sont pas appelées pour tous les objets. Par exemple, si une exception structurée se produit lors de la tentative d’effectuer un appel de fonction via un pointeur de fonction non initialisé et que cette fonction prend comme des objets de paramètres construits avant l’appel, les destructeurs de ces objets ne sont pas appelés pendant le déroulement de la pile.

## <a name="next-steps"></a>Étapes suivantes :

- [Utilisation de setjmp ou longjmp C++ dans les programmes](../cpp/using-setjmp-longjmp.md)

  Pour plus d’informations sur l’utilisation des `setjmp` et des C++ `longjmp` dans les programmes, consultez.

- [Gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md)

  Consultez des exemples de la façon dont vous C++ pouvez utiliser pour gérer les exceptions structurées.

## <a name="see-also"></a>Voir aussi

[Meilleures C++ pratiques modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)
