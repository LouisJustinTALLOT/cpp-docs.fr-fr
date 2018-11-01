---
title: Avantages de l’Architecture Document / Vue
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: ccb2e786eb2397efd2d8b34e118f0935fdb05283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655963"
---
# <a name="advantages-of-the-documentview-architecture"></a>Avantages de l'architecture document/vue

Le principal avantage à l’aide de l’architecture document/vue MFC est que l’excellente prise en charge plusieurs vues du même document. (Si vous n’avez pas besoin plusieurs vues et la surcharge de document/vue est excessive dans votre application, vous pouvez éviter l’architecture. [Alternatives à l’Architecture Document/vue](../mfc/alternatives-to-the-document-view-architecture.md).)

Supposons que votre application permet aux utilisateurs d’afficher des données numériques sous forme de feuille de calcul ou sous forme de graphique. Un utilisateur peut souhaiter afficher simultanément les deux les données brutes, sous forme de feuille de calcul et un graphique obtenu à partir des données. Vous Affrichez ces vues distinctes dans des fenêtres frame distinct ou dans les volets de fractionnement au sein d’une fenêtre unique. Maintenant Supposons que l’utilisateur peut modifier les données dans la feuille de calcul et voir les modifications reflétées immédiatement dans le graphique.

Dans MFC, la vue de la feuille de calcul et l’affichage du graphique seraient basés sur les différentes classes dérivées de CView. Les deux vues seraient associés à un objet de document unique. Le document stocke les données (ou encore les obtient à partir d’une base de données). Les deux affichages accèdent au document et affichent les données qu’ils récupéreront à partir de celui-ci.

Quand un utilisateur met à jour d’une des vues, d’afficher les appels de l’objet `CDocument::UpdateAllViews`. Cette fonction signale toutes les vues du document, et chaque vue met à jour lui-même à l’aide des données les plus récentes à partir du document. L’appel unique à `UpdateAllViews` synchronise les différentes vues.

Ce scénario serait difficile à coder sans la séparation des données à partir de la vue, en particulier si les vues stockent les données elles-mêmes. Document/vue, il est facile. L’infrastructure effectue l’essentiel du travail de coordination pour vous.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Alternatives à document/vue](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)

