---
title: "Exceptions : interception et suppression d'exceptions"
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246691"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Exceptions : interception et suppression d'exceptions

Les instructions et exemples suivants vous montrent comment intercepter et supprimer des exceptions. Pour plus d’informations sur les mots clés **try**, **catch**et **throw** , [consultez C++ meilleures pratiques modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md).

Vos gestionnaires d’exceptions doivent supprimer les objets d’exception qu’ils gèrent, car l’échec de la suppression de l’exception provoque une fuite de mémoire chaque fois que le code intercepte une exception.

Votre bloc **catch** doit supprimer une exception dans les cas suivants :

- Le bloc **catch** lève une nouvelle exception.

   Bien entendu, vous ne devez pas supprimer l’exception si vous relevez la même exception :

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- L’exécution retourne à partir du bloc **catch** .

> [!NOTE]
>  Lors de la suppression d’un `CException`, utilisez la fonction membre `Delete` pour supprimer l’exception. N’utilisez pas le mot clé **Delete** , car il peut échouer si l’exception n’est pas sur le tas.

#### <a name="to-catch-and-delete-exceptions"></a>Pour intercepter et supprimer des exceptions

1. Utilisez le mot clé **try** pour configurer un bloc **try** . Exécutez les instructions de programme qui peuvent lever une exception dans un bloc **try** .

   Utilisez le mot clé **catch** pour configurer un bloc **catch** . Placez le code de gestion des exceptions dans un bloc **catch** . Le code du bloc **catch** est exécuté uniquement si le code du bloc **try** lève une exception du type spécifié dans l’instruction **catch** .

   La structure suivante montre comment les blocs **try** et **catch** sont normalement organisés :

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Quand une exception est levée, le contrôle passe au premier bloc **catch** dont la déclaration d’exception correspond au type de l’exception. Vous pouvez gérer de manière sélective différents types d’exceptions avec des blocs **catch** séquentiels, comme indiqué ci-dessous :

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Pour plus d’informations, consultez [exceptions : conversion à partir de macros d’exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
