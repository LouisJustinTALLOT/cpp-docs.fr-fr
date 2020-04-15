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
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371996"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Exceptions : libération d'objets dans les exceptions

Cet article explique le besoin et la méthode de libération des objets lorsqu’une exception se produit. Les sujets abordés sont les suivants :

- [Gérer l’exception localement](#_core_handling_the_exception_locally)

- [Jeter des exceptions après la destruction d’objets](#_core_throwing_exceptions_after_destroying_objects)

Les exceptions prévues par le cadre ou par votre application interrompent le flux normal du programme. Ainsi, il est très important de garder une trace rapprochée des objets afin que vous puissiez bien les disposer au cas où une exception est lancée.

Il existe deux méthodes principales pour ce faire.

- Gérer les exceptions localement en utilisant les mots clés **essayer** et **attraper,** puis détruire tous les objets avec une seule instruction.

- Détruisez tout objet dans le bloc **de capture** avant de jeter l’exception à l’extérieur du bloc pour une manipulation ultérieure.

Ces deux approches sont illustrées ci-dessous comme des solutions à l’exemple problématique suivant :

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Comme écrit `myPerson` ci-dessus, ne sera pas `SomeFunc`supprimé si une exception est jetée par . L’exécution saute directement vers le gestionnaire d’exception externe suivant, contournant la sortie de fonction normale et le code qui supprime l’objet. Le pointeur de l’objet sort de portée lorsque l’exception quitte la fonction, et la mémoire occupée par l’objet ne sera jamais récupérée tant que le programme est en cours d’exécution. Il s’agit d’une fuite de mémoire; il serait détecté en utilisant les diagnostics de mémoire.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Gérer l’exception localement

Le paradigme **d’essai/capture** fournit une méthode de programmation défensive pour éviter les fuites de mémoire et s’assurer que vos objets sont détruits lorsque des exceptions se produisent. Par exemple, l’exemple montré plus tôt dans cet article pourrait être réécrit comme suit :

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Ce nouvel exemple met en place un gestionnaire d’exception pour attraper l’exception et la manipuler localement. Il quitte alors la fonction normalement et détruit l’objet. L’aspect important de cet exemple est qu’un contexte pour attraper l’exception est établi avec les blocs **d’essai/capture.** Sans un cadre d’exception local, la fonction ne saurait jamais qu’une exception avait été lancée et n’aurait pas la chance de sortir normalement et de détruire l’objet.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Mettre des exceptions après la destruction d’objets

Une autre façon de gérer les exceptions est de les transmettre au contexte extérieur suivant de gestion des exceptions. Dans votre bloc **de capture,** vous pouvez faire un peu de nettoyage de vos objets attribués localement, puis jeter l’exception pour un traitement ultérieur.

La fonction de lancement peut ou non avoir besoin de traiter des objets de tas. Si la fonction traite toujours l’objet de tas avant de revenir dans le cas normal, alors la fonction doit également traiter l’objet de tas avant de lancer l’exception. D’autre part, si la fonction ne traite pas normalement l’objet avant de revenir dans le cas normal, alors vous devez décider au cas par cas si l’objet de tas doit être deallocated.

L’exemple suivant montre comment les objets attribués localement peuvent être nettoyés :

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Le mécanisme d’exception traite automatiquement les objets de cadre ; le destructeur de l’objet cadre est également appelé.

Si vous appelez des fonctions qui peuvent jeter des exceptions, vous pouvez utiliser des blocs **d’essai/capture** pour vous assurer que vous attrapez les exceptions et que vous avez une chance de détruire tous les objets que vous avez créés. En particulier, sachez que de nombreuses fonctions MFC peuvent jeter des exceptions.

Pour plus d’informations, voir [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
