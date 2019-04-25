---
title: Construction d'objets en une et en deux étapes
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 871db7abd2682d557bf2e80e9cb97624f0dc53a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160157"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construction d'objets en une et en deux étapes

Vous avez le choix entre deux techniques pour créer des objets graphiques, tels que des stylets et des pinceaux :

- *Construction d’une étape*: Construire et initialiser l’objet en une seule phase, toutes avec le constructeur.

- *Construction en deux étapes*: Construire et initialiser l’objet en deux étapes distinctes. Le constructeur crée l’objet et l’initialise une fonction d’initialisation.

Construction en deux étapes est toujours plus sûre. Dans la construction d’une étape, le constructeur pouvait lever une exception si vous fournissez des arguments incorrects ou l’allocation de mémoire échoue. Ce problème est évité par construction en deux étapes, bien que vous avez à la recherche de l’échec. Dans les deux cas, la destruction de l’objet est le même processus.

> [!NOTE]
>  Ces techniques s’appliquent à la création des objets, le pas qu’il soit graphique.

## <a name="example-of-both-construction-techniques"></a>Exemple de ces deux Techniques de Construction

Le court exemple suivant illustre les deux méthodes de construction d’un objet pen :

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Objets graphiques](../mfc/graphic-objects.md)

- [Sélection d’un objet graphique dans un contexte de périphérique](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Voir aussi

[Objets graphiques](../mfc/graphic-objects.md)
