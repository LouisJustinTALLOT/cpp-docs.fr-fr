---
description: 'En savoir plus sur : exceptions : interception et suppression d’exceptions'
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
ms.openlocfilehash: 01f018694d211b4b60acc92c4121614d14769d6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290737"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Exceptions : interception et suppression d'exceptions

Les instructions et exemples suivants vous montrent comment intercepter et supprimer des exceptions. Pour plus d’informations sur **`try`** les **`catch`** **`throw`** Mots clés, et, consultez [meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md).

Vos gestionnaires d’exceptions doivent supprimer les objets d’exception qu’ils gèrent, car l’échec de la suppression de l’exception provoque une fuite de mémoire chaque fois que le code intercepte une exception.

Votre **`catch`** bloc doit supprimer une exception dans les cas suivants :

- Le **`catch`** bloc lève une nouvelle exception.

   Bien entendu, vous ne devez pas supprimer l’exception si vous relevez la même exception :

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- L’exécution retourne à partir du **`catch`** bloc.

> [!NOTE]
> Lors de la suppression d’un `CException` , utilisez la `Delete` fonction membre pour supprimer l’exception. N’utilisez pas le **`delete`** mot clé, car il peut échouer si l’exception n’est pas sur le tas.

#### <a name="to-catch-and-delete-exceptions"></a>Pour intercepter et supprimer des exceptions

1. Utilisez le **`try`** mot clé pour configurer un **`try`** bloc. Exécutez les instructions de programme qui peuvent lever une exception dans un **`try`** bloc.

   Utilisez le **`catch`** mot clé pour configurer un **`catch`** bloc. Placez le code de gestion des exceptions dans un **`catch`** bloc. Le code dans le **`catch`** bloc est exécuté uniquement si le code du **`try`** bloc lève une exception du type spécifié dans l' **`catch`** instruction.

   La structure suivante montre comment **`try`** les **`catch`** blocs et sont normalement organisés :

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Quand une exception est levée, le contrôle passe au premier **`catch`** bloc dont la déclaration d’exception correspond au type de l’exception. Vous pouvez gérer de manière sélective différents types d’exceptions avec des blocs séquentiels **`catch`** comme indiqué ci-dessous :

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Pour plus d’informations, consultez [exceptions : conversion à partir de macros d’exception MFC](exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
