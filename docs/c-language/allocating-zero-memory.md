---
title: Allocation de mémoire initialisée à zéro
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313491"
---
# <a name="allocating-zero-memory"></a>Allocation de mémoire initialisée à zéro

**4.10.3 ANSI** Comportement de la `calloc`fonction, `malloc`ou `realloc` si la taille demandée est égale à zéro

Les fonctions `calloc`, `malloc` et `realloc` acceptent zéro comme argument. Aucune mémoire réelle n'est allouée, mais un pointeur valide est retourné et le bloc de mémoire peut être modifié ultérieurement par réallocation.

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)
