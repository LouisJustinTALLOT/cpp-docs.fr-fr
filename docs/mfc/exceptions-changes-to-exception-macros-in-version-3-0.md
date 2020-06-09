---
title: "Exceptions : modifications apportées aux macros d'exception dans la version 3.0"
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 25095257096efd869e237383c5cd202ae4e602c2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620167"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Exceptions : modifications apportées aux macros d'exception dans la version 3.0

Il s’agit d’une rubrique avancée.

Dans MFC version 3,0 et versions ultérieures, les macros de gestion des exceptions ont été modifiées pour utiliser des exceptions C++. Cet article explique comment ces modifications peuvent affecter le comportement du code existant qui utilise les macros.

Cet article aborde les thèmes suivants :

- [Types d’exception et macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Nouvelle levée des exceptions](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Types d’exception et macro CATCH

Dans les versions antérieures de MFC, la macro **catch** utilisait des informations de type au moment de l’exécution MFC pour déterminer le type d’une exception. le type de l’exception est déterminé, en d’autres termes, sur le site d’interception. Toutefois, avec les exceptions C++, le type de l’exception est toujours déterminé au niveau du site de levée par le type de l’objet d’exception qui est levé. Cela entraînera des incompatibilités dans le cas rare où le type du pointeur vers l’objet levé diffère du type de l’objet levé.

L’exemple suivant illustre la conséquence de cette différence entre la version 3,0 de MFC et les versions antérieures :

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ce code se comporte différemment dans la version 3,0 car le contrôle passe toujours au premier bloc **catch** avec une déclaration d’exception correspondante. Résultat de l’expression Throw

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

est levé en tant que `CException*` , même s’il est construit en tant que `CCustomException` . La macro **catch** dans MFC versions 2,5 et antérieures utilise `CObject::IsKindOf` pour tester le type au moment de l’exécution. Car l’expression

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

a la valeur true, le premier bloc catch intercepte l’exception. Dans la version 3,0, qui utilise des exceptions C++ pour implémenter la plupart des macros de gestion des exceptions, le deuxième bloc catch correspond à l’exception levée `CException` .

Un code similaire à celui-ci est rare. Il apparaît généralement lorsqu’un objet exception est passé à une autre fonction qui accepte un générique `CException*` , effectue le traitement « pré-lever », puis lève l’exception.

Pour contourner ce problème, déplacez l’expression Throw de la fonction vers le code appelant et levez une exception du type réel connu du compilateur au moment où l’exception est générée.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Nouvelle levée des exceptions

Un bloc catch ne peut pas lever le même pointeur d’exception qu’il A intercepté.

Par exemple, ce code était valide dans les versions précédentes, mais aura des résultats inattendus avec la version 3,0 :

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

L’utilisation de **throw** dans le bloc catch entraîne la suppression du pointeur `e` , de sorte que le site catch externe recevra un pointeur non valide. Utilisez **THROW_LAST** pour lever une nouvelle fois `e` .

Pour plus d’informations, consultez [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
