---
title: Portrait de l’Architecture Document / Vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d903d183675ae4b79d4610fe4413cfd8bf0e704c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928942"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portrait de l'architecture document/vue
Documents et vues sont associés dans une application MFC classique. Données stockées dans le document, mais la vue a un accès privilégié aux données. La séparation du document de vue sépare le stockage et la maintenance des données à partir de son affichage.  
  
## <a name="gaining-access-to-document-data-from-the-view"></a>L’accès aux données à partir de la vue du Document  
 La vue accède aux données de son document à l’aide du [GetDocument](../mfc/reference/cview-class.md#getdocument) de fonction, qui retourne un pointeur vers le document, ou en mettant à la vue de classe C++ `friend` de la classe de document. La vue utilise ensuite son accès aux données pour obtenir les données lorsqu’il est prêt à dessiner ou de les manipuler dans le cas contraire.  
  
 Par exemple, à partir de la vue [OnDraw](../mfc/reference/cview-class.md#ondraw) fonction membre, la vue utilise `GetDocument` pour obtenir un pointeur de document. Elle utilise ensuite ce pointeur pour accéder à un `CString` membre de données dans le document. La vue passe la chaîne à la `TextOut` (fonction). Pour afficher le code pour cet exemple, consultez [dessin dans une vue](../mfc/drawing-in-a-view.md).  
  
## <a name="user-input-to-the-view"></a>Entrée d’utilisateur à la vue  
 La vue peut également interpréter un clic de souris lui-même en tant que sélection ou de modification des données. De même, elle peut interpréter les séquences de touches en tant qu’entrée de données ou de la modification. Supposons que l’utilisateur tape une chaîne dans une vue qui gère le texte. La vue obtient un pointeur vers le document et utilise le pointeur pour transmettre les nouvelles données au document, qui les stocke dans une structure de données.  
  
## <a name="updating-multiple-views-of-the-same-document"></a>Mise à jour de plusieurs vues du même Document  
 Dans une application avec plusieurs vues du même document, par exemple une fenêtre fractionnée dans un éditeur de texte, la vue passe tout d’abord les nouvelles données au document. Ensuite, il appelle du document [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) fonction membre, ce qui indique à toutes les vues du document se mettre à jour, qui reflète les nouvelles données. Cette opération synchronise les vues.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Avantages de l’architecture document/vue](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Alternatives à l’architecture document/vue](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture document/vue](../mfc/document-view-architecture.md)

