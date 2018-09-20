---
title: Création de Collections de piles et file d’attente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d050f27688d97cd3ef0352eed00f4dadb1fe6d98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403784"
---
# <a name="creating-stack-and-queue-collections"></a>Création de collections de piles et de files d’attente

Cet article explique comment créer les autres structures de données, tel que [piles](#_core_stacks) et [files d’attente](#_core_queues), à partir de MFC répertorient les classes. Les exemples utilisent des classes dérivées de `CList`, mais vous pouvez utiliser `CList` directement à moins que vous deviez ajouter des fonctionnalités.

##  <a name="_core_stacks"></a> Piles

Étant donné que la collection de listes standard a un début et une fin, il est facile de créer une collection de listes dérivée qui reproduit le comportement d’une pile de type "dernière entrée - première sortie". Une pile est similaire à un empilement de plateaux dans une cafétéria. Lorsque les plateaux sont ajoutés à la pile, ils sont sur le dessus de la pile. Le dernier plateau ajouté est le premier à être enlevé. Les fonctions membres de la collection de listes `AddHead` et `RemoveHead` peuvent être utilisées pour ajouter et supprimer des éléments en particulier en tête de liste. Ainsi, le dernier élément ajouté est le premier à être supprimé.

#### <a name="to-create-a-stack-collection"></a>Pour créer une collection de piles

1. Dérivez une nouvelle classe de liste de l'une des classes de liste MFC existantes et ajoutez des fonctions membres pour prendre en charge les fonctionnalités des opérations de pile.

     L'exemple suivant montre comment ajouter des fonctions membres pour empiler des éléments, jetez un coup d'œil à l'élément supérieur de la pile et désempilez-le :

     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Notez que cette approche présente la classe `CObList` sous-jacente. L'utilisateur peut appeler n'importe quelle fonction membre `CObList`, qu'elle soit logique pour une pile ou non.

##  <a name="_core_queues"></a> Files d’attente

Étant donné que la collection de listes standard a un début et une fin, il est facile de créer une collection de listes dérivée qui reproduit le comportement d’une file de type "première entrée-première sortie". Une file d'attente est similaire à une ligne de personnes dans une cafétéria. La première personne de la file est la première à être servie. Lorsque plusieurs personnes viennent, elles arrivent à la fin de la file pour attendre leur tour. Les fonctions membres de la collection de listes `AddTail` et `RemoveHead` peuvent être utilisées pour ajouter et supprimer des éléments en particulier en tête ou queue de liste. Ainsi, le dernier élément ajouté est toujours le dernier à être supprimé.

#### <a name="to-create-a-queue-collection"></a>Pour créer une collection en file d'attente

1. Dérivez une nouvelle classe de liste de l'une des classes de liste prédéfinies fournies dans la bibliothèque MFC et ajoutez des fonctions membres supplémentaires pour prendre en charge la sémantique des opérations de file.

     L'exemple suivant montre comment ajouter des fonctions membres pour insérer un élément à la fin de la file et obtenir l'élément situé au début de la file.

     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Voir aussi

[Collections](../mfc/collections.md)

