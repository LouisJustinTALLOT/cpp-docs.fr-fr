---
description: En savoir plus sur les avantages de l’architecture document/vue
title: Avantages de l’architecture Document-View
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 54ff7cc0e4717f7f487ece3acee79f39ad7dfa3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185451"
---
# <a name="advantages-of-the-documentview-architecture"></a>Avantages de l'architecture document/vue

Le principal avantage lié à l’utilisation de l’architecture document/vue MFC est que l’architecture prend en charge plusieurs vues du même document en particulier. (Si vous n’avez pas besoin de plusieurs vues et que la surcharge de document/vue est excessive dans votre application, vous pouvez éviter l’architecture. [Alternatives à l’architecture document/vue](alternatives-to-the-document-view-architecture.md).)

Supposons que votre application permette aux utilisateurs d’afficher des données numériques sous forme de feuille de calcul ou sous forme de graphique. Un utilisateur peut souhaiter voir simultanément les données brutes, le formulaire de feuille de calcul et un graphique qui résulte des données. Vous pouvez afficher ces vues distinctes dans des fenêtres Frame distinctes ou dans des volets Splitter au sein d’une même fenêtre. Supposons à présent que l’utilisateur puisse modifier les données dans la feuille de calcul et voir les modifications instantanément reflétées dans le graphique.

Dans MFC, la vue de feuille de calcul et la vue de graphique sont basées sur différentes classes dérivées de CView. Les deux vues sont associées à un objet document unique. Le document stocke les données (ou peut les obtenir à partir d’une base de données). Les deux vues accèdent au document et affichent les données qu’elles récupèrent.

Lorsqu’un utilisateur met à jour l’une des vues, cet objet d’affichage appelle `CDocument::UpdateAllViews` . Cette fonction avertit toutes les vues du document, et chaque vue se met à jour en utilisant les données les plus récentes du document. L’appel unique à `UpdateAllViews` synchronise les différentes vues.

Ce scénario serait difficile à coder sans la séparation des données de la vue, en particulier si les vues stockent les données elles-mêmes. Avec document/vue, c’est facile. L’infrastructure effectue la plupart des tâches de coordination pour vous.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Alternatives à document/vue](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument :: UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView :: GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
