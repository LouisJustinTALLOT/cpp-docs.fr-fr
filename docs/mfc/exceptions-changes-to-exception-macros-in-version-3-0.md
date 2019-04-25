---
title: 'Exceptions : Modifications apportées aux Macros d’Exception dans la Version 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: fb51ad91e001f0ed153bf4fdb5aa598ab5ba5042
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173265"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Exceptions : Modifications apportées aux Macros d’Exception dans la Version 3.0

Il s’agit d’une rubrique avancée.

Dans les MFC version 3.0 et versions ultérieure, les macros de gestion des exceptions ont été modifiés pour utiliser des exceptions C++. Cet article indique comment ces modifications peuvent affecter le comportement du code existant qui utilise les macros.

Cet article aborde les rubriques suivantes :

- [Types d’exceptions et la macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Génération répétée d’exceptions](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> Types d’exceptions et la Macro CATCH

Dans les versions antérieures de MFC, la **CATCH** macro utilisé les informations de type au moment de l’exécution MFC pour déterminer le type d’une exception ; type de l’exception est déterminé, en d’autres termes, sur le site catch. Avec les exceptions C++, toutefois, type de l’exception est toujours déterminé au niveau du site throw par le type de l’objet exception qui est levée. Cela entraîne des incompatibilités dans les rares cas où le type du pointeur vers l’objet levé est différent du type de l’objet levé.

L’exemple suivant illustre les conséquences de cette différence entre MFC version 3.0 et versions antérieures :

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ce code se comporte différemment dans la version 3.0, car le contrôle passe toujours à la première **catch** bloc avec une déclaration d’exception correspondante. Le résultat de l’expression throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

est levée comme un `CException*`, même si elle est construite comme un `CCustomException`. Le **CATCH** macro dans les versions 2.5 et versions antérieures utilisent `CObject::IsKindOf` pour tester le type au moment de l’exécution. Étant donné que l’expression

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

est true, le premier bloc catch intercepte l’exception. Dans la version 3.0, qui utilise des exceptions C++ pour implémenter la plupart des macros de gestion des exceptions, le second bloc catch correspond à la levée `CException`.

Code comme cela est rare. Il apparaît généralement lorsqu’un objet d’exception est passé à une autre fonction qui accepte un générique `CException*`, effectue un traitement « throw préliminaire » et enfin lève l’exception.

Pour contourner ce problème, déplacez l’expression throw à partir de la fonction au code appelant et lève une exception du type réel connu du compilateur au moment de que l’exception est générée.

##  <a name="_core_re.2d.throwing_exceptions"></a> Génération répétée d’Exceptions

Un bloc catch ne peut pas lever le pointeur d’exception qu’il a intercepté.

Par exemple, ce code était valide dans les versions précédentes, mais ont des résultats inattendus avec la version 3.0 :

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

À l’aide de **lever** dans le bloc catch provoque le pointeur `e` doit être supprimé, afin que le site catch externe reçoit un pointeur non valide. Utilisez **THROW_LAST** pour lever de nouveau `e`.

Pour plus d’informations, consultez [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
