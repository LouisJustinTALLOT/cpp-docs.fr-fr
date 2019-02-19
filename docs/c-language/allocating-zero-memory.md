---
title: Allocation de mémoire initialisée à zéro
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147462"
---
# <a name="allocating-zero-memory"></a>Allocation de mémoire initialisée à zéro

**ANSI 4.10.3** Le comportement de la fonction `calloc`, `malloc` ou fonction `realloc` si la taille demandée est zéro

Les fonctions `calloc`, `malloc` et `realloc` acceptent zéro comme argument. Aucune mémoire réelle n'est allouée, mais un pointeur valide est retourné et le bloc de mémoire peut être modifié ultérieurement par réallocation.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)
