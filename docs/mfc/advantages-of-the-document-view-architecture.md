---
title: Avantages de l’Architecture Document / Vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45065b38128a2e3239b1fd10ded490fdcbcb3eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340846"
---
# <a name="advantages-of-the-documentview-architecture"></a>Avantages de l'architecture document/vue
Le principal avantage à l’aide de l’architecture document/vue MFC est que la prise en charge de plusieurs vues du même document en particulier. (Si vous n’avez pas besoin plusieurs vues et la surcharge de document/vue est excessive dans votre application, vous pouvez éviter l’architecture. [Alternatives à l’Architecture Document/vue](../mfc/alternatives-to-the-document-view-architecture.md).)  
  
 Supposons que votre application permet aux utilisateurs d’afficher des données numériques sous forme de feuille de calcul ou sous forme de graphique. Un utilisateur peut souhaiter voir simultanément à la fois les données brutes, sous forme de feuille de calcul et un graphique des résultats à partir des données. Vous Affrichez ces vues distinctes dans des fenêtres frame séparées ou dans les volets de fractionnement dans une seule fenêtre. Maintenant Supposons que l’utilisateur peut modifier les données dans la feuille de calcul et voir les modifications reflétées immédiatement dans le graphique.  
  
 Dans MFC, la vue de la feuille de calcul et l’affichage du graphique sont basées sur les différentes classes dérivées de CView. Les deux vues doit être associées à un objet de document unique. Le document stocke les données (ou encore les obtient à partir d’une base de données). Les deux vues accèdent au document et affichent les données qu’ils récupéreront à partir de celui-ci.  
  
 Lorsqu’un utilisateur met à jour d’une des vues, d’afficher les appels de l’objet `CDocument::UpdateAllViews`. Cette fonction signale toutes les vues du document, et chaque vue met à jour lui-même à l’aide des données les plus récentes à partir du document. L’appel à `UpdateAllViews` synchronise les différentes vues.  
  
 Ce scénario serait difficile à coder sans la séparation des données à partir de la vue, en particulier si les vues stockent les données elles-mêmes. Avec le document/vue, il est facile. L’infrastructure effectue la plupart du travail de coordination.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Solutions de remplacement de document/vue](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture document/vue](../mfc/document-view-architecture.md)

