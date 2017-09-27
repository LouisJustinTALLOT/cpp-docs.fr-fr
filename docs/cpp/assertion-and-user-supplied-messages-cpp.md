---
title: "Assertion et Messages fournis par l’utilisateur (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: def12cc22267d2cc25be790b7e6e6eebd4c46479
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="assertion-and-user-supplied-messages-c"></a>Assertion et messages fournis par l'utilisateur (C++)
Les C++ langage prend en charge trois la gestion des erreurs mécanismes qui vous aident à déboguer votre application : le [directive #error](../preprocessor/hash-error-directive-c-cpp.md), le [static_assert](../cpp/static-assert.md) (mot clé) et le [assert (macro), _assert, _ wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (macro). Ces trois mécanismes génèrent des messages d'erreur et deux d'entre eux testent également les assertions logicielles. Une assertion logicielle spécifie une condition supposée être vraie en un point particulier de votre programme. Si une assertion au moment de la compilation échoue, le compilateur génère un message de diagnostic et une erreur de compilation. Si une assertion d'exécution échoue, le système d'exploitation génère un message de diagnostic et ferme votre application.  
  
## <a name="remarks"></a>Remarques  
 La durée de vie de votre application se compose d'une phase de prétraitement, de compilation et d'exécution. Chaque mécanisme de gestion des erreurs accède aux informations de débogage disponibles pendant l'une de ces phases. Pour déboguer efficacement, sélectionnez le mécanisme qui fournit des informations pertinentes concernant cette phase :  
  
-   Le [directive #error](../preprocessor/hash-error-directive-c-cpp.md) est en vigueur au moment du prétraitement. Elle génère sans condition un message spécifié par l'utilisateur et provoque l'échec de la compilation avec une erreur. Le message peut contenir du texte manipulé par des directives de préprocesseur, mais aucune expression obtenue n'est évaluée.  
  
-   Le [static_assert](../cpp/static-assert.md) déclaration est en vigueur au moment de la compilation. Elle teste une assertion logicielle représentée par une expression intégrale spécifiée par l'utilisateur qui peut être convertie en valeur booléenne. Si l'expression est évaluée à la valeur zéro (false), le compilateur génère le message spécifié par l'utilisateur et la compilation échoue avec une erreur.  
  
     La déclaration `static_assert` est particulièrement utile pour le débogage des modèles, car des arguments template peuvent être inclus dans l'expression spécifiée par l'utilisateur.  
  
-   Le [assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (macro) est en vigueur au moment de l’exécution. Elle évalue une expression spécifiée par l'utilisateur, et si le résultat est zéro, le système génère un message de diagnostic et ferme votre application. Plusieurs autres macros, telles que[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) et `_ASSERTE`, ressembler à cette macro mais émettre différents messages de diagnostic définis par le système ou définies par l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [#error (directive) (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [Macro assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT, _ASSERTE, _ASSERT_EXPR, macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_Static_assert, macro](../c-runtime-library/reference/static-assert-macro.md)   
 [Modèles](../cpp/templates-cpp.md)
