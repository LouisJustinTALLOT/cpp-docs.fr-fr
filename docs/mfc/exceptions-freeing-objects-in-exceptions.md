---
title: "Exceptions : libération d'objets dans les exceptions"
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: e4fafd12d22f6ff7635380e139f60c110a193d9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622826"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Exceptions : libération d'objets dans les exceptions

Cet article explique les besoins et la méthode de libération d’objets lorsqu’une exception se produit. Les sujets abordés sont les suivants :

- [Gestion de l’exception en local](#_core_handling_the_exception_locally)

- [Levée d’exceptions après la destruction d’objets](#_core_throwing_exceptions_after_destroying_objects)

Les exceptions levées par le Framework ou par votre application interrompent le déroulement normal du programme. Par conséquent, il est très important d’effectuer un suivi des objets afin de pouvoir les supprimer correctement au cas où une exception serait levée.

Pour ce faire, il existe deux méthodes principales.

- Gérez les exceptions localement à l’aide des mots clés **try** et **catch** , puis Détruisez tous les objets avec une seule instruction.

- Détruisez tout objet dans le bloc **catch** avant de lever l’exception en dehors du bloc pour une gestion ultérieure.

Ces deux approches sont illustrées ci-dessous en tant que solutions aux exemples problématiques suivants :

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Comme indiqué ci-dessus, `myPerson` ne sera pas supprimé si une exception est levée par `SomeFunc` . L’exécution accède directement au gestionnaire d’exceptions externe suivant, en ignorant la sortie de la fonction normale et le code qui supprime l’objet. Le pointeur vers l’objet est hors de portée quand l’exception quitte la fonction, et la mémoire occupée par l’objet ne sera jamais Récupérée tant que le programme est en cours d’exécution. Il s’agit d’une fuite de mémoire ; elle est détectée à l’aide des diagnostics de la mémoire.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Gestion de l’exception en local

Le paradigme **try/catch** fournit une méthode de programmation défensive pour éviter les fuites de mémoire et vous assurer que vos objets sont détruits lorsque des exceptions se produisent. Par exemple, l’exemple indiqué plus haut dans cet article peut être réécrit comme suit :

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Ce nouvel exemple configure un gestionnaire d’exceptions pour intercepter l’exception et la gérer localement. Il quitte ensuite la fonction normalement et détruit l’objet. L’aspect important de cet exemple est qu’un contexte pour intercepter l’exception est établi avec les blocs **try/catch** . Sans Frame d’exception locale, la fonction ne sait jamais qu’une exception a été levée et n’a pas la possibilité de se fermer normalement et de détruire l’objet.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Levée d’exceptions après la destruction d’objets

Une autre façon de gérer les exceptions consiste à les passer au contexte de gestion des exceptions externe suivant. Dans votre bloc **catch** , vous pouvez effectuer un nettoyage de vos objets alloués localement, puis lever l’exception sur pour un traitement supplémentaire.

La fonction de levée peut ou non avoir besoin de libérer des objets de segment de mémoire. Si la fonction libère toujours l’objet segment de mémoire avant de retourner dans le cas normal, la fonction doit également libérer l’objet segment de mémoire avant de lever l’exception. En revanche, si la fonction ne libère pas normalement l’objet avant de retourner dans le cas normal, vous devez décider au cas par cas, si l’objet segment de mémoire doit être libéré.

L’exemple suivant montre comment les objets alloués localement peuvent être nettoyés :

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Le mécanisme d’exception libère automatiquement les objets Frame ; le destructeur de l’objet frame est également appelé.

Si vous appelez des fonctions qui peuvent lever des exceptions, vous pouvez utiliser des blocs **try/catch** pour vous assurer d’intercepter les exceptions et avoir la possibilité de détruire tous les objets que vous avez créés. En particulier, sachez que de nombreuses fonctions MFC peuvent lever des exceptions.

Pour plus d’informations, consultez [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
