---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 22b18f2e238c780377b84fc2be3eb6678686bb73
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399274"
---
# <a name="align-masm"></a>ALIGN (MASM)

La directive **align** aligne l’élément ou l’instruction de données suivant sur une adresse qui est un multiple de son paramètre. Le paramètre doit être une puissance de 2 (par exemple, 1, 2, 4, etc.) qui est inférieure ou égale à l’alignement du segment.

## <a name="syntax"></a>Syntaxe

> **Aligner** le*numéro*⟦ ⟧

## <a name="remarks"></a>Notes

La directive **align** vous permet de spécifier le décalage de début d’un élément de données ou d’une instruction. Les données alignées peuvent améliorer les performances, au détriment d’un gaspillage d’espace entre les éléments de données. Des améliorations importantes en matière de performances peuvent se produire lorsque les accès aux données se trouvent sur des limites qui tiennent dans les lignes du cache. Les accès aux limites naturelles pour les types natifs signifient moins de temps passé dans le microcode de réalignement matériel interne.

Le besoin d’instructions alignées est rare sur les processeurs modernes qui utilisent un modèle d’adressage plat, mais peut être requis pour les cibles de saut dans du code plus ancien pour d’autres modèles d’adressage.

Lorsque les données sont alignées, l’espace ignoré est complété avec des zéros. Lorsque les instructions sont alignées, l’espace ignoré est rempli avec les instructions NOP de taille appropriée.

## <a name="see-also"></a>Voir aussi

[Même](even.md)\
[Informations de référence sur les directives](directives-reference.md)
