---
title: 'Exceptions : Libération d’objets dans les Exceptions'
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
ms.openlocfilehash: 23fe85018d1bc2c41371afec2ad6931755e4e682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406065"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Exceptions : Libération d’objets dans les Exceptions

Cet article explique la nécessité et la méthode de libération d’objets lorsqu’une exception se produit. Les rubriques traitées ici sont les suivantes :

- [Gestion de l’exception localement](#_core_handling_the_exception_locally)

- [Levée d’exceptions après la destruction d’objets](#_core_throwing_exceptions_after_destroying_objects)

Exceptions levées par le framework ou par votre application interruption flux normal du programme. Par conséquent, il est très important de suivre de près les objets afin que vous pouvez supprimer correctement les au cas où une exception est levée.

Il existe deux méthodes principales pour ce faire.

- Gérer les exceptions localement à l’aide de la **essayez** et **catch** mots clés, puis détruit tous les objets avec une seule instruction.

- Détruire de n’importe quel objet dans le **catch** bloc avant de lever l’exception en dehors du bloc pour autre gestion.

Ces deux approches sont illustrées ci-dessous en tant que solutions à l’exemple suivant problématique :

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Comme ci-dessus, `myPerson` ne seront pas supprimés si une exception est levée par `SomeFunc`. L’exécution passe directement au gestionnaire d’exception externe suivant, en ignorant la sortie de la fonction normal et le code qui supprime l’objet. Le pointeur vers l’objet est hors de portée lorsque l’exception quitte la fonction, et la mémoire occupée par l’objet ne sera jamais récupérée tant que le programme est en cours d’exécution. Il s’agit d’une fuite de mémoire ; elle peut être détectée à l’aide des diagnostics de la mémoire.

##  <a name="_core_handling_the_exception_locally"></a> Gestion de l’Exception localement

Le **try/catch** paradigme fournit une méthode de programmation défensive permettant d’éviter les fuites de mémoire et de s’assurer que vos objets sont détruits lorsque des exceptions se produisent. Par exemple, l’exemple présenté plus haut dans cet article peut être réécrit comme suit :

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Ce nouvel exemple configure un gestionnaire d’exceptions pour intercepter l’exception et la gérer localement. Ensuite, il quitte la fonction normalement et détruit l’objet. L’aspect important de cet exemple est qu’un contexte pour intercepter l’exception est établi avec le **try/catch** blocs. Sans cadre d’exception local, la fonction ne saurait jamais qu’une exception a été levée et n’aurait pas l’occasion de vous quitter normalement et détruire l’objet.

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> Levée d’Exceptions après la destruction d’objets

Une autre pour gérer les exceptions consiste à les transmettre le contexte de la gestion des exceptions externe suivant. Dans votre **catch** bloc, vous pouvez effectuer un nettoyage de vos objets alloués localement et puis lève l’exception de pour un traitement ultérieur.

La fonction de levée peut ou peut ne pas vouloir libérer des objets du tas. Si la fonction désalloue toujours l’objet de tas avant de retourner dans le cas normal, la fonction doit également libérer l’objet de tas avant de lever l’exception. En revanche, si la fonction ne libérez pas normalement l’objet avant de retourner dans le cas normal, vous devez décider cas par cas si l’objet de segment de mémoire doit être libérée.

L’exemple suivant montre comment localement les objets alloués peut être nettoyés :

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Le mécanisme d’exception désalloue automatiquement les objets d’images ; le destructeur de l’objet de frame est également appelé.

Si vous appelez des fonctions qui peuvent lever des exceptions, vous pouvez utiliser **try/catch** blocs pour vous assurer que vous interceptez les exceptions et que vous avez la possibilité de détruire tous les objets que vous avez créé. En particulier, n’oubliez pas que de nombreuses fonctions MFC peuvent lever des exceptions.

Pour plus d’informations, consultez [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
