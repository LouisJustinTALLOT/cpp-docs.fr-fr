---
title: Assertion et messages fournis par l'utilisateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: a4861b3e1d17835f11f5e148d6b62051a6747f80
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226019"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Assertion et messages fournis par l'utilisateur (C++)

Le langage C++ prend en charge trois mécanismes de gestion des erreurs qui vous aident à déboguer votre application : la [directive #error](../preprocessor/hash-error-directive-c-cpp.md), le mot clé [Static_assert](../cpp/static-assert.md) et la [macro assert, _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro. Ces trois mécanismes génèrent des messages d'erreur et deux d'entre eux testent également les assertions logicielles. Une assertion logicielle spécifie une condition supposée être vraie en un point particulier de votre programme. Si une assertion au moment de la compilation échoue, le compilateur génère un message de diagnostic et une erreur de compilation. Si une assertion d'exécution échoue, le système d'exploitation génère un message de diagnostic et ferme votre application.

## <a name="remarks"></a>Notes

La durée de vie de votre application se compose d'une phase de prétraitement, de compilation et d'exécution. Chaque mécanisme de gestion des erreurs accède aux informations de débogage disponibles pendant l'une de ces phases. Pour déboguer efficacement, sélectionnez le mécanisme qui fournit des informations pertinentes concernant cette phase :

- La [directive #error](../preprocessor/hash-error-directive-c-cpp.md) est appliquée au moment du prétraitement. Elle génère sans condition un message spécifié par l'utilisateur et provoque l'échec de la compilation avec une erreur. Le message peut contenir du texte manipulé par des directives de préprocesseur, mais aucune expression obtenue n'est évaluée.

- La déclaration de [static_assert](../cpp/static-assert.md) est appliquée au moment de la compilation. Elle teste une assertion logicielle représentée par une expression intégrale spécifiée par l'utilisateur qui peut être convertie en valeur booléenne. Si l'expression est évaluée à la valeur zéro (false), le compilateur génère le message spécifié par l'utilisateur et la compilation échoue avec une erreur.

   La **`static_assert`** déclaration est particulièrement utile pour déboguer des modèles, car les arguments template peuvent être inclus dans l’expression spécifiée par l’utilisateur.

- La [macro Assert, _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro est appliquée au moment de l’exécution. Elle évalue une expression spécifiée par l'utilisateur, et si le résultat est zéro, le système génère un message de diagnostic et ferme votre application. De nombreuses autres macros, telles que[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) et _ASSERTE, ressemblent à cette macro, mais émettent différents messages de diagnostic définis par le système ou définis par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[#error, directive (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[Macro Assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[Macro _STATIC_ASSERT](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Modèles](../cpp/templates-cpp.md)
