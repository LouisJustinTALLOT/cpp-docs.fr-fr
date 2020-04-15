---
title: "Exceptions : modifications apportées aux macros d'exception dans la version 3.0"
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365495"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Exceptions : modifications apportées aux macros d'exception dans la version 3.0

C’est un sujet avancé.

Dans la version MFC 3.0 et plus tard, les macros de manipulation d’exception ont été modifiées pour utiliser les exceptions de C. Cet article indique comment ces modifications peuvent affecter le comportement du code existant qui utilise les macros.

Cet article aborde les thèmes suivants :

- [Types d’exception et la macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Re-lancer des exceptions](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Types d’exception et catch Macro

Dans les versions antérieures de MFC, la macro **CATCH** utilisait des informations de type temps d’exécution MFC pour déterminer le type d’exception; le type d’exception est déterminé, en d’autres termes, sur le site de capture. Toutefois, à l’exception de C, le type d’exception est toujours déterminé sur le site de lancer par le type d’objet d’exception qui est lancé. Cela entraînera des incompatibilités dans le cas rare où le type de pointeur à l’objet lancé diffère du type de l’objet lancé.

L’exemple suivant illustre la conséquence de cette différence entre la version 3.0 de MFC et les versions antérieures :

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ce code se comporte différemment dans la version 3.0 parce que le contrôle passe toujours au premier bloc **de capture** avec une exception-déclaration correspondante. Le résultat de l’expression de lancer

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

est jeté `CException*`comme un , même `CCustomException`si elle est construite comme un . La macro **CATCH** dans les versions MFC `CObject::IsKindOf` 2.5 et les utilisations antérieures pour tester le type au moment de l’exécution. Parce que l’expression

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

est vrai, le premier bloc de capture attrape l’exception. Dans la version 3.0, qui utilise les exceptions C pour mettre en œuvre `CException`bon nombre des macros de manipulation d’exception, le deuxième bloc de capture correspond au lancer .

Un code comme celui-ci est rare. Il apparaît généralement quand un objet d’exception est `CException*`passé à une autre fonction qui accepte un générique , effectue "pré-jeter" traitement, et jette enfin l’exception.

Pour contourner ce problème, déplacez l’expression de lancer de la fonction au code d’appel et jetez une exception du type réel connu du compilateur au moment où l’exception est générée.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Re-Throwing Exceptions

Un bloc de capture ne peut pas lancer le même pointeur d’exception qu’il a attrapé.

Par exemple, ce code était valide dans les versions précédentes, mais aura des résultats inattendus avec la version 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

L’utilisation **de THROW** dans `e` le bloc de capture provoque la suppression du pointeur, de sorte que le site de capture externe recevra un pointeur invalide. Utilisez **THROW_LAST** pour re-jeter `e`.

Pour plus d’informations, voir [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
