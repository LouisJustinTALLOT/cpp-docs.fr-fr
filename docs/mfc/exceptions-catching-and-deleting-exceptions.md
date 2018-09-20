---
title: 'Exceptions : Interception et suppression d’Exceptions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd59cc19c80e305a7e57fb711a49f59a024d528
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434763"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Exceptions : interception et suppression d'exceptions

Les instructions et les exemples suivants montrent comment intercepter et supprimer des exceptions. Pour plus d’informations sur la **essayez**, **catch**, et **lever** mots clés, consultez [gestion des exceptions C++](../cpp/cpp-exception-handling.md).

Vos gestionnaires d’exceptions doivent supprimer les objets d’exception qu’ils gèrent, car échec de suppression de l’exception entraîne une fuite de mémoire chaque fois que ce code intercepte une exception.

Votre **catch** bloc doit supprimer une exception lorsque :

- Le **catch** bloc lève une exception.

     Bien sûr, vous ne devez pas supprimer l’exception si vous levez à nouveau la même exception :

     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- L’exécution retourne depuis la **catch** bloc.

> [!NOTE]
>  Lorsque vous supprimez un `CException`, utilisez le `Delete` fonction membre à supprimer de l’exception. N’utilisez pas le **supprimer** mot clé, car elle peut échouer si l’exception n’est pas sur le tas.

#### <a name="to-catch-and-delete-exceptions"></a>Pour intercepter et supprimer des exceptions

1. Utilisez le **essayez** mot clé pour configurer un **essayez** bloc. Les instructions de n’importe quel programme susceptible de lever une exception dans un **essayez** bloc.

     Utilisez le **catch** mot clé pour configurer un **catch** bloc. Placez le code de gestion des exceptions dans un **catch** bloc. Le code dans le **catch** bloc est exécuté uniquement si le code dans le **essayez** bloc lève une exception du type spécifié dans le **catch** instruction.

     Le squelette suivant montre comment **essayez** et **catch** blocs sont organisés normalement :

     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

     Lorsqu’une exception est levée, le contrôle passe à la première **catch** bloc dont déclaration d’exception correspond au type de l’exception. Vous pouvez gérer de manière sélective différents types d’exceptions avec séquentiel **catch** bloque comme indiqué ci-dessous :

     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Pour plus d’informations, consultez [Exceptions : conversion à partir de Macros d’Exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

