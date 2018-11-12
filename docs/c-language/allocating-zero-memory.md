---
title: Allocation de mémoire initialisée à zéro
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: c7d5f307a38fff938c94cf2e1660cec99262a10a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447305"
---
# <a name="allocating-zero-memory"></a>Allocation de mémoire initialisée à zéro

**ANSI 4.10.3** Le comportement de la fonction `calloc`, `malloc` ou fonction `realloc` si la taille demandée est zéro

Les fonctions `calloc`, `malloc` et `realloc` acceptent zéro comme argument. Aucune mémoire réelle n'est allouée, mais un pointeur valide est retourné et le bloc de mémoire peut être modifié ultérieurement par réallocation.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)