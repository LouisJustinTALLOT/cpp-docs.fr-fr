---
description: 'En savoir plus sur : un portrait de l’architecture document/vue'
title: Portrait de l’architecture Document-View
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: e4f8fc636349aaa12ee4481c7f6223c343b6d406
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169630"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portrait de l'architecture document/vue

Les documents et les vues sont associés à une application MFC classique. Les données sont stockées dans le document, mais la vue a un accès privilégié aux données. La séparation du document de la vue sépare le stockage et la maintenance des données de son affichage.

## <a name="gaining-access-to-document-data-from-the-view"></a>Obtention de l’accès aux données de document à partir de la vue

La vue accède aux données de son document à l’aide de la fonction [GetDocument](reference/cview-class.md#getdocument) , qui retourne un pointeur vers le document ou en faisant de la classe de vue un C++ **`friend`** de la classe de document. La vue utilise ensuite son accès aux données pour obtenir les données lorsqu’elle est prête à dessiner ou à la manipuler.

Par exemple, à partir de la fonction membre [OnDraw](reference/cview-class.md#ondraw) de la vue, la vue utilise `GetDocument` pour obtenir un pointeur de document. Il utilise ensuite ce pointeur pour accéder à un `CString` membre de données dans le document. La vue passe la chaîne à la `TextOut` fonction. Pour afficher le code de cet exemple, consultez [dessin dans une vue](drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Entrée d’utilisateur dans la vue

La vue peut également interpréter un clic de souris dans lui-même en tant que sélection ou modification de données. De même, il peut interpréter les séquences de touches comme des entrées ou des modifications de données. Supposons que l’utilisateur tape une chaîne dans une vue qui gère le texte. La vue obtient un pointeur vers le document et utilise le pointeur pour passer les nouvelles données au document, qui les stocke dans une structure de données.

## <a name="updating-multiple-views-of-the-same-document"></a>Mise à jour de plusieurs vues d’un même document

Dans une application avec plusieurs vues du même document, telles qu’une fenêtre fractionnée dans un éditeur de texte, la vue passe d’abord les nouvelles données au document. Elle appelle ensuite la fonction membre [UpdateAllViews](reference/cdocument-class.md#updateallviews) du document, qui indique à toutes les vues du document de se mettre à jour eux-mêmes, en reflétant les nouvelles données. Cela synchronise les vues.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Avantages de l’architecture document/vue](advantages-of-the-document-view-architecture.md)

- [Alternatives à l’architecture document/vue](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
