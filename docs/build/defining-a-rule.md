---
title: Définition d'une règle
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 7031f56d82fcaf557388c7600d493ebda48add1a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416928"
---
# <a name="defining-a-rule"></a>Définition d'une règle

Le *fromext* représente l’extension d’un fichier dépendant, et *toext* représente l’extension d’un fichier cible.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Notes

Extensions ne respectent pas la casse. Les macros peuvent être appelées pour représenter *fromext* et *toext*; les macros sont développées pendant le prétraitement. Le point (.) précédent *fromext* doit apparaître au début de la ligne. Le signe deux-points ( :)) est précédé de zéro ou plusieurs espaces ou des tabulations. Il peut être suivi uniquement par des espaces ou onglets, un point-virgule ( ;) pour spécifier une commande, un signe dièse (#) pour spécifier un commentaire ou un caractère de saut de ligne. Aucune autres espaces ne sont autorisés. Les commandes sont spécifiées comme dans les blocs de description.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Chemins de recherche dans les règles](../build/search-paths-in-rules.md)

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](../build/inference-rules.md)
