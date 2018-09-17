---
title: Définition d’une règle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a5cb7a0285f7abf8bcf476141451eae1b10f85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705573"
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