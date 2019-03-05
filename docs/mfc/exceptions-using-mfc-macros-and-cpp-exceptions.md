---
title: 'Exceptions : À l’aide de Macros MFC et des Exceptions C++'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297708"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Exceptions : À l’aide de Macros MFC et des Exceptions C++

Cet article traite des considérations sur l’écriture de code qui utilise les macros de gestion des exceptions MFC et les mots clés de gestion des exceptions C++.

Cet article aborde les rubriques suivantes :

- [Macros et les mots clés d’exception](#_core_mixing_exception_keywords_and_macros)

- [Blocs try à l’intérieur des blocs catch](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> Macros et les mots clés d’Exception

Vous pouvez combiner des macros d’exception MFC et mots clés des exceptions C++ dans le même programme. Mais vous ne pouvez pas mélanger les macros MFC avec les mots clés des exceptions C++ dans le même bloc étant donné que les macros de suppriment les objets d’exception automatiquement lorsqu’ils sont hors de portée, n’est pas le cas du code à l’aide de mots clés des gestion des exceptions. Pour plus d’informations, consultez l’article [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

La principale différence entre les macros et les mots clés est que les macros suppriment « automatique » une exception interceptée lorsque l’exception passe hors de portée. N’est pas ; le cas du code à l’aide de mots clés exceptions interceptées dans un bloc catch doivent être explicitement supprimées. Macros et les mots clés des exceptions C++ peut provoquer des fuites de mémoire lorsqu’un objet d’exception n’est pas supprimé ou endommagement du tas lorsqu’une exception est supprimé à deux reprises.

Le code suivant, par exemple, invalide le pointeur d’exception :

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Le problème se produit parce que `e` est supprimé lorsque l’exécution sort de la « interne » **CATCH** bloc. À l’aide de la **THROW_LAST** macro au lieu du **lever** instruction provoquera le « externe » **CATCH** bloc pour recevoir un pointeur valide :

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> Essayez de blocs à l’intérieur des blocs Catch

Vous ne pouvez pas lever à nouveau l’exception actuelle depuis un **essayez** bloc qui se trouve dans un **CATCH** bloc. L’exemple suivant n’est pas valide :

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Pour plus d’informations, consultez [Exceptions : Examen du contenu de l’Exception](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
