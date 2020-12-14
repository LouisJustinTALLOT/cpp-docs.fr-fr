---
description: 'En savoir plus sur : définition d’une règle'
title: Définition d'une règle
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 89a5db90162ede02743aa469ac4f9e3d75c5e147
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201675"
---
# <a name="defining-a-rule"></a>Définition d'une règle

*Fromext* représente l’extension d’un fichier dépendant et *toext* représente l’extension d’un fichier cible.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Notes

Les extensions ne respectent pas la casse. Les macros peuvent être appelées pour représenter *fromext* et *toext*; les macros sont développées pendant le prétraitement. Le point (.) précédant *fromext* doit apparaître au début de la ligne. Le signe deux-points ( :) est précédé de zéro, un ou plusieurs espaces ou tabulations. Il ne peut être suivi que par des espaces ou des tabulations, un point-virgule (;) pour spécifier une commande, un signe dièse (#) pour spécifier un commentaire ou un caractère de saut de ligne. Aucun autre espace n’est autorisé. Les commandes sont spécifiées comme dans les blocs de description.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Chemins de recherche dans les règles](search-paths-in-rules.md)

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
