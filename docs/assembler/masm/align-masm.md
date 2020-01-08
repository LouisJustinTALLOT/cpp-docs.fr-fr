---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316588"
---
# <a name="align"></a>ALIGN

La directive **align** aligne l’élément ou l’instruction de données suivant sur une adresse qui est un multiple de son paramètre. Le paramètre doit être une puissance de 2 (par exemple, 1, 2, 4, etc.) qui est inférieure ou égale à l’alignement du segment.

## <a name="syntax"></a>Syntaxe

> **Aligner** ⟦*constantExpression*⟧

## <a name="remarks"></a>Notes

La directive **align** vous permet de spécifier le décalage de début d’un élément de données ou d’une instruction. Les données alignées peuvent améliorer les performances, au détriment d’un gaspillage d’espace entre les éléments de données. Des améliorations importantes en matière de performances peuvent se produire lorsque les accès aux données se trouvent sur des limites qui tiennent dans les lignes du cache. Les accès aux limites naturelles pour les types natifs signifient moins de temps passé dans le microcode de réalignement matériel interne.

Le besoin d’instructions alignées est rare sur les processeurs modernes qui utilisent un modèle d’adressage plat, mais peut être requis pour les cibles de saut dans du code plus ancien pour d’autres modèles d’adressage.

Lorsque les données sont alignées, l’espace ignoré est complété avec des zéros. Lorsque les instructions sont alignées, l’espace ignoré est rempli avec les instructions NOP de taille appropriée.

## <a name="see-also"></a>Voir aussi

[Même](even.md)\
Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
