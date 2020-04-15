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
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365515"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Exceptions : interception et suppression d'exceptions

Les instructions et exemples suivants vous montrent comment attraper et supprimer les exceptions. Pour plus d’informations sur **l’essai,** **attraper**, et **jeter** des mots clés, voir [les meilleures pratiques modernes C POUR les exceptions et la manipulation des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md).

Vos gestionnaires d’exception doivent supprimer les objets d’exception qu’ils manipulent, car le défaut de supprimer l’exception provoque une fuite de mémoire chaque fois que ce code attrape une exception.

Votre bloc **de capture** doit supprimer une exception lorsque :

- Le bloc **de capture** jette une nouvelle exception.

   Bien sûr, vous ne devez pas supprimer l’exception si vous jetez la même exception à nouveau:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- L’exécution revient de l’intérieur du bloc **de capture.**

> [!NOTE]
> Lors de la `CException`suppression `Delete` d’un , utilisez la fonction membre pour supprimer l’exception. N’utilisez pas le mot clé **de suppression,** car il peut échouer si l’exception n’est pas sur le tas.

#### <a name="to-catch-and-delete-exceptions"></a>Pour attraper et supprimer les exceptions

1. Utilisez le mot clé **d’essai** pour configurer un bloc **d’essai.** Exécutez toutes les instructions de programme qui pourraient jeter une exception dans un bloc **d’essai.**

   Utilisez le mot clé de **capture** pour configurer un bloc **de capture.** Placez le code de manipulation des exceptions dans un bloc **de capture.** Le code dans le bloc **de capture** n’est exécuté que si le code dans le bloc **d’essai** jette une exception du type spécifié dans **l’instruction de capture.**

   Le squelette suivant montre comment les blocs **d’essai** et **d’attraper** sont normalement disposés :

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Lorsqu’une exception est lancée, le contrôle passe au premier bloc **de capture** dont la déclaration d’exception correspond au type d’exception. Vous pouvez gérer sélectivement différents types d’exceptions avec des blocs de **capture** séquentiels énumérés ci-dessous :

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Pour plus d’informations, voir [Exceptions: Conversion de MFC Exception Macros](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
