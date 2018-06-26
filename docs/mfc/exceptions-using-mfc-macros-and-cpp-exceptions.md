---
title: 'Exceptions : Utilisation des Macros MFC et des Exceptions C++ | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 698d8a754716f6876f9a72a0d5043807a32d2089
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932206"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Exceptions : utilisation de macros MFC et d'exceptions C++
Cet article décrit des considérations sur l’écriture de code qui utilise les macros de gestion des exceptions MFC et les mots clés de gestion des exceptions C++.  
  
 Cet article couvre les rubriques suivantes :  
  
-   [Macros et les mots clés d’exception](#_core_mixing_exception_keywords_and_macros)  
  
-   [Try (blocs) à l’intérieur des blocs catch](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> Macros et les mots clés d’Exception  
 Vous pouvez combiner des macros d’exception MFC et mots clés des exceptions C++ dans le même programme. Mais vous ne pouvez pas mélanger les macros MFC avec les mots clés des exceptions C++ dans le même bloc étant donné que les macros de suppriment les objets exception automatiquement lorsqu’ils sont hors de portée, n’est pas le cas du code à l’aide de mots clés des gestion des exceptions. Pour plus d’informations, consultez l’article [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 La principale différence entre les macros et les mots clés est que les macros suppriment « automatiquement » une exception interceptée lorsque l’exception passe hors de portée. Code utilisant les mots clés n’est pas ; les exceptions interceptées dans un bloc catch doivent être supprimées explicitement. Macros et les mots clés des exceptions C++ peut provoquer des fuites de mémoire lorsqu’un objet d’exception n’est pas supprimé ou endommagement du tas lorsqu’une exception est supprimée deux fois.  
  
 Le code suivant, par exemple, invalide le pointeur d’exception :  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 Le problème se produit parce que `e` est supprimé quand l’exécution sort « interne » **CATCH** bloc. À l’aide de la **THROW_LAST** macro au lieu du **lever** instruction provoquera la « externe » **CATCH** bloc pour recevoir un pointeur valid :  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> Try (blocs) à l’intérieur des blocs Catch  
 Vous ne pouvez pas lever à nouveau l’exception actuelle à partir d’un **essayez** bloc qui est à l’intérieur d’un **CATCH** bloc. L’exemple suivant n’est pas valide :  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 Pour plus d’informations, consultez [Exceptions : examen de contenu des exceptions](../mfc/exceptions-examining-exception-contents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

