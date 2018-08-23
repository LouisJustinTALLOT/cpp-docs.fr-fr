---
title: C (structurées) et d’exceptions de C++ | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 580fb4c96db70b612135ac48e30bd9c0d45c4d1c
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42571976"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mélange d’exceptions C (structurées) et des exceptions C++

Si vous souhaitez écrire du code portable, l’utilisation de structurée des exceptions (SEH) dans un programme C++ n’est pas recommandée. Toutefois, vous souhaiterez parfois compiler à l’aide de [/EHa](../build/reference/eh-exception-handling-model.md) et combiner des exceptions structurées et code source C++ et avez besoin d’un autre mécanisme pour gérer ces deux types d’exceptions. Étant donné que le Gestionnaire d’exceptions structuré n’a aucun concept d’objets ou des exceptions typées, il ne peut pas gérer les exceptions levées par du code C++. Toutefois, C++ **catch** gestionnaires peuvent gérer les exceptions structurées. Syntaxe des exceptions C++ (**essayez**, **lever**, **catch**) n’est pas accepté par le compilateur C, mais la syntaxe de gestion structurée des exceptions (**__try**, **__except**, **__finally**) est pris en charge par le compilateur C++.

Consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) pour plus d’informations sur la façon de gérer les exceptions structurées en tant qu’exceptions C++.

Si vous combinez structurées et des exceptions C++, n’oubliez pas de ces problèmes potentiels :

- Les exceptions C++ et les exceptions structurées ne peuvent pas être mélangées dans la même fonction.

- Gestionnaires de terminaisons (**__finally** blocs) sont toujours exécutés, même pendant le déroulement après qu’une exception est levée.

- Gestion des exceptions C++ peuvent intercepter et conserver sémantiques de déroulement dans tous les modules compilés avec la [/EH](../build/reference/eh-exception-handling-model.md) options du compilateur, qui permettent les sémantiques de déroulement.

- Il peut exister des situations où les fonctions de destructeur ne sont pas appelées pour tous les objets. Par exemple, si une exception structurée se produit lorsque vous tentez d’appeler une fonction via un pointeur fonction non initialisé, et cette fonction prend comme paramètres des objets qui ont été construits avant l’appel, les destructeurs de ces objets sont appelés pas pendant le déroulement de pile.

## <a name="next-steps"></a>Étapes suivantes

- [Utilisation de setjmp ou longjmp dans les programmes C++](../cpp/using-setjmp-longjmp.md)

  Voir plus d’informations sur l’utilisation de `setjmp` et `longjmp` dans les programmes C++.

- [Gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md)

  Consultez les exemples des méthodes que vous pouvez utiliser C++ pour gérer structurée des exceptions.

## <a name="see-also"></a>Voir aussi

[Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)  
