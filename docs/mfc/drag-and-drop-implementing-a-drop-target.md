---
title: 'Glisser -déplacer : Implémentation d’une cible de dépôt'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 46501193569d7f3098e23c67c68c76ce20a82ea3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405935"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Glisser -déplacer : Implémentation d’une cible de dépôt

Cet article explique comment rendre votre application une cible de dépôt. Implémentation d’une cible de déplacement prend plus de temps que l’implémentation d’une source de dépôt, mais il est encore relativement simple. Ces techniques s’appliquent également aux applications non-OLE.

#### <a name="to-implement-a-drop-target"></a>Pour implémenter une cible de dépôt

1. Ajouter une variable membre à chaque vue dans l’application que vous souhaitez être une cible de dépôt. Cette variable membre doit être de type `COleDropTarget` ou une classe dérivée à partir de celui-ci.

1. À partir de la fonction de votre classe d’affichage qui gère la **WM_CREATE** message (généralement `OnCreate`), appelez la nouvelle variable de membre `Register` fonction membre. `Revoke` sera appelé automatiquement pour vous lors de la destruction de la vue.

1. Substituer les fonctions suivantes. Si vous souhaitez le même comportement dans toute votre application, substituez ces fonctions dans votre classe d’affichage. Si vous souhaitez modifier le comportement dans certains cas isolés ou souhaitez activer la suppression non -`CView` windows, remplacer ces fonctions dans votre `COleDropTarget`-classe dérivée.

    |Remplacer|Pour autoriser|
    |--------------|--------------|
    |`OnDragEnter`|Supprimer les opérations dans la fenêtre. Appelé lorsque le curseur passe tout d’abord la fenêtre.|
    |`OnDragLeave`|Comportement spécial lorsque l’opération glisser quitte la fenêtre spécifiée.|
    |`OnDragOver`|Supprimer les opérations dans la fenêtre. Appelé lorsque le curseur est déplacé dans la fenêtre.|
    |`OnDrop`|La gestion des données en cours de suppression dans la fenêtre spécifiée.|
    |`OnScrollBy`|Comportement spécial lorsque le défilement est nécessaire dans la fenêtre cible.|

Consultez le fichier MAINVIEW. Cpp qui fait partie de l’exemple OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) pour obtenir un exemple du fonctionnement conjoint des ces fonctions.

Pour plus d'informations, voir :

- [Implémentation d’une Source de dépôt](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Création et la destruction des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulation des objets de données OLE et de Sources de données](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Voir aussi

[Glisser-déposer (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropTarget, classe](../mfc/reference/coledroptarget-class.md)
