---
description: 'En savoir plus sur les éléments suivants : One-Stage et Two-Stage construction d’objets'
title: Construction d'objets en une et en deux étapes
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: d46a8d380c263c4ce18671f02b11d5b058bc8410
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243911"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construction d'objets en une et en deux étapes

Vous avez le choix entre deux techniques pour créer des objets graphiques, tels que les stylets et les pinceaux :

- *Construction en une étape*: construisez et initialisez l’objet en une seule étape, le tout avec le constructeur.

- *Construction en deux étapes*: construction et initialisation de l’objet en deux étapes distinctes. Le constructeur crée l’objet et une fonction d’initialisation l’initialise.

La construction en deux étapes est toujours plus sûre. Dans une construction en une seule étape, le constructeur peut lever une exception si vous fournissez des arguments incorrects ou si l’allocation de mémoire échoue. Ce problème est évité par la construction en deux étapes, même si vous devez vérifier la défaillance. Dans les deux cas, la destruction de l’objet est le même processus.

> [!NOTE]
> Ces techniques s’appliquent à la création d’objets, et pas seulement à des objets graphiques.

## <a name="example-of-both-construction-techniques"></a>Exemple des deux techniques de construction

Le bref exemple suivant illustre les deux méthodes de construction d’un objet Pen :

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Objets graphiques](graphic-objects.md)

- [Sélection d'un objet graphique dans un contexte de périphérique](selecting-a-graphic-object-into-a-device-context.md)

- [Contextes de périphérique](device-contexts.md)

- [Dessin dans une vue](drawing-in-a-view.md)

## <a name="see-also"></a>Voir aussi

[Objets graphiques](graphic-objects.md)
