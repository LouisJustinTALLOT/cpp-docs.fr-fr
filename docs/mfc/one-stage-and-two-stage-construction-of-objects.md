---
title: Construction d'objets en une et en deux étapes
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375966"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construction d'objets en une et en deux étapes

Vous avez le choix entre deux techniques de création d’objets graphiques, tels que des stylos et des pinceaux :

- *Construction en une étape*: Construire et initialiser l’objet en une seule étape, le tout avec le constructeur.

- *Construction en deux étapes*: Construire et initialiser l’objet en deux étapes distinctes. Le constructeur crée l’objet et une fonction d’initialisation l’initialise.

La construction en deux étapes est toujours plus sûre. Dans la construction en une seule étape, le constructeur pourrait jeter une exception si vous fournissez des arguments incorrects ou l’allocation de mémoire échoue. Ce problème est évité par la construction en deux étapes, bien que vous ayez à vérifier l’échec. Dans les deux cas, détruire l’objet est le même processus.

> [!NOTE]
> Ces techniques s’appliquent à la création d’objets, pas seulement des objets graphiques.

## <a name="example-of-both-construction-techniques"></a>Exemple des deux techniques de construction

Le bref exemple suivant montre les deux méthodes de construction d’un objet à stylo :

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Objets graphiques](../mfc/graphic-objects.md)

- [Sélection d’un objet graphique dans un contexte d’appareil](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Voir aussi

[Objets graphiques](../mfc/graphic-objects.md)
