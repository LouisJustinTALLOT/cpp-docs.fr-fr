---
title: 'Exceptions : Modifications apportées aux Macros d’Exception de la Version 3.0 | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4e6c7744c3d5328985eee24e67ee1eb359fb3c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931016"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Exceptions : modifications apportées aux macros d'exception dans la version 3.0
Il s’agit d’une rubrique avancée.  
  
 Dans les MFC version 3.0 et versions ultérieure, les macros de gestion des exceptions ont été modifiés pour utiliser des exceptions C++. Cet article explique comment ces modifications peuvent affecter le comportement du code existant qui utilise les macros.  
  
 Cet article couvre les rubriques suivantes :  
  
-   [Types d’exception et la macro CATCH](#_core_exception_types_and_the_catch_macro)  
  
-   [Nouvelle levée des exceptions](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> Types d’exception et la Macro CATCH  
 Dans les versions antérieures de MFC, la **CATCH** macro utilisé les informations de type au moment de l’exécution MFC pour déterminer le type d’une exception ; le type de l’exception est déterminée, en d’autres termes, au niveau du site d’interception. Avec les exceptions C++, toutefois, type de l’exception est toujours déterminé au niveau du site de levée par le type de l’objet exception qui est levée. Cela entraîne des incompatibilités dans les rares cas où le type du pointeur vers l’objet levé est différent du type de l’objet levé.  
  
 L’exemple suivant illustre les conséquences de cette différence entre MFC version 3.0 et versions antérieures :  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 Ce code se comporte différemment de la version 3.0, car il est toujours le contrôle passe à la première **catch** bloc avec une déclaration d’exception correspondante. Le résultat de l’expression throw  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 est levée comme un `CException*`, même si elle est construite comme un `CCustomException`. Le **CATCH** macro dans les versions 2.5 et antérieures utilise `CObject::IsKindOf` pour tester le type au moment de l’exécution. Étant donné que l’expression  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 a la valeur true, le premier bloc catch intercepte l’exception. Dans la version 3.0, qui utilise des exceptions C++ pour implémentent la majorité des macros de gestion des exceptions, le second bloc catch correspond à la levée `CException`.  
  
 Code similaire à celui-ci est rare. Il apparaît généralement lorsqu’un objet d’exception est passé à une autre fonction qui accepte un type générique `CException*`, effectue le traitement de « throw préliminaire » et enfin lève l’exception.  
  
 Pour contourner ce problème, déplacez l’expression throw à partir de la fonction au code appelant et lève une exception du type réellement connu du compilateur au moment de que l’exception est générée.  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> Nouvelle levée des Exceptions  
 Un bloc catch ne peuvent pas lever le pointeur d’exception qu’il a intercepté.  
  
 Par exemple, ce code était valide dans les versions précédentes, mais ont des résultats inattendus avec la version 3.0 :  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 À l’aide de **lever** dans le bloc catch bloc provoque le pointeur `e` à supprimer, afin que le site d’interception extérieur recevra un pointeur non valide. Utilisez **THROW_LAST** à lever de nouveau `e`.  
  
 Pour plus d’informations, consultez [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

