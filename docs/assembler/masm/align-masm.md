---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031224"
---
# <a name="align-masm"></a>ALIGN (MASM)

Le **ALIGN** directive aligne l’élément suivant de données ou l’instruction sur une adresse qui est un multiple de son paramètre. Le paramètre doit être une puissance de 2 (par exemple, 1, 2, 4 et ainsi de suite) qui est inférieur ou égal à l’alignement du segment.

## <a name="syntax"></a>Syntaxe

> ALIGN [[*nombre*]]

## <a name="remarks"></a>Notes

Le **ALIGN** directive vous permet de spécifier le décalage de début d’un élément de données ou d’une instruction. Données alignés peuvent améliorer les performances, au détriment de l’espace gaspillé entre les éléments de données. Des améliorations des performances peuvent être consultées lorsque les accès aux données sont sur des limites qui tiennent les lignes de cache. Accès sur les frontières naturelles pour les types natifs signifie moins de temps passé dans le microcode de réalignement de matériels internes.

La nécessité pour obtenir des instructions alignées est rare sur les processeurs modernes qui utilisent un modèle d’adressage plat, mais peuvent être nécessaire pour les cibles de saut dans le code plus ancien pour d’autres modèles d’adressage.

Lorsque les données sont alignées, l’espace ignoré est complété avec des zéros. Lorsque des instructions sont alignées, l’espace ignoré est rempli avec des instructions de NOP-la taille appropriée.

## <a name="see-also"></a>Voir aussi

[EVEN](even.md)<br/>
[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>