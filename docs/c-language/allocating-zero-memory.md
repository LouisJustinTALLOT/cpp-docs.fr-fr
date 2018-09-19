---
title: Allocation de mémoire zéro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085054"
---
# <a name="allocating-zero-memory"></a>Allocation de mémoire initialisée à zéro

**ANSI 4.10.3** Le comportement de la fonction `calloc`, `malloc` ou fonction `realloc` si la taille demandée est zéro

Les fonctions `calloc`, `malloc` et `realloc` acceptent zéro comme argument. Aucune mémoire réelle n'est allouée, mais un pointeur valide est retourné et le bloc de mémoire peut être modifié ultérieurement par réallocation.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)