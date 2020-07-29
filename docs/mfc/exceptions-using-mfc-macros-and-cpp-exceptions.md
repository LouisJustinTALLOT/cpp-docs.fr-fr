---
title: "Exceptions : utilisation de macros MFC et d'exceptions C++"
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
ms.openlocfilehash: 9e97eb545dedd3ac38dd93471f82aecc382717ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223172"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Exceptions : utilisation de macros MFC et d'exceptions C++

Cet article aborde les considérations relatives à l’écriture de code qui utilise à la fois les macros de gestion des exceptions MFC et les mots clés de gestion des exceptions C++.

Cet article aborde les thèmes suivants :

- [Combinaison de mots clés et macros d’exception](#_core_mixing_exception_keywords_and_macros)

- [Blocs try dans les blocs catch](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Combinaison de mots clés et macros d’exception

Vous pouvez mélanger les macros d’exception MFC et les mots clés d’exceptions C++ dans le même programme. Toutefois, vous ne pouvez pas mélanger les macros MFC avec les mots clés d’exceptions C++ dans le même bloc, car les macros suppriment automatiquement des objets d’exception lorsqu’ils sont hors de portée, alors que le code qui utilise les mots clés de gestion des exceptions ne le fait pas. Pour plus d’informations, consultez l’article [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

La principale différence entre les macros et les mots clés est que les macros suppriment « automatiquement » une exception interceptée lorsque l’exception est hors de portée. Le code qui utilise les mots clés ne le fait pas ; les exceptions interceptées dans un bloc catch doivent être supprimées explicitement. La combinaison de macros et de mots clés d’exceptions C++ peut provoquer des fuites de mémoire lorsqu’un objet exception n’est pas supprimé ou un tas endommagé quand une exception est supprimée deux fois.

Le code suivant, par exemple, invalide le pointeur d’exception :

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Le problème se produit car `e` est supprimé lorsque l’exécution est en dehors du bloc **catch** « interne ». Si vous utilisez la macro **THROW_LAST** au lieu de l’instruction **throw** , le bloc **catch** « Outer » reçoit un pointeur valide :

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Blocs try dans les blocs catch

Vous ne pouvez pas lever à nouveau l’exception actuelle à partir d’un **`try`** bloc qui se trouve à l’intérieur d’un bloc **catch** . L’exemple suivant n’est pas valide :

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Pour plus d’informations, consultez [exceptions : examen du contenu des exceptions](exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
