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
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371592"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Exceptions : utilisation de macros MFC et d'exceptions C++

Cet article traite des considérations relatives à la rédaction de code qui utilise à la fois les macros de manutention des exceptions MFC et les mots clés de manipulation des exceptions de C.

Cet article aborde les thèmes suivants :

- [Mélanger les mots clés d’exception et les macros](#_core_mixing_exception_keywords_and_macros)

- [Essayez les blocs à l’intérieur des blocs de capture](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mélanger les mots clés d’exception et les macros

Vous pouvez mélanger des macros d’exception MFC et des mots clés d’exception CMD dans le même programme. Mais vous ne pouvez pas mélanger les macros MFC avec les mots clés d’exception Cmd dans le même bloc parce que les macros suppriment automatiquement les objets d’exception lorsqu’ils sortent de portée, alors que le code utilisant les mots clés de manipulation d’exception ne le fait pas. Pour plus d’informations, voir l’article [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

La principale différence entre les macros et les mots clés est que les macros "automatiquement" supprimer une exception pris lorsque l’exception sort de portée. Code à l’aide des mots clés n’est pas; les exceptions prises dans un bloc de capture doivent être explicitement supprimées. Le mélange de macros et de mots-clés d’exception de CMD peut provoquer des fuites de mémoire lorsqu’un objet d’exception n’est pas supprimé, ou une corruption de tas lorsqu’une exception est supprimée deux fois.

Le code suivant, par exemple, invalide le pointeur d’exception :

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Le problème `e` se produit parce qu’il est supprimé lorsque l’exécution sort du bloc **CATCH** « intérieur ». L’utilisation de la macro **THROW_LAST** au lieu de l’instruction **THROW** fera en sorte que le bloc **CATCH** « externe » recevra un pointeur valide :

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Essayez les blocs à l’intérieur des blocs de capture

Vous ne pouvez pas re-jeter l’exception actuelle à partir d’un bloc **d’essai** qui est à l’intérieur d’un bloc **CATCH.** L’exemple suivant est invalide :

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Pour plus d’informations, voir [Exceptions: Examining Exceptions Contents](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
