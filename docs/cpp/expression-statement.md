---
description: 'En savoir plus sur : instruction d’expression'
title: Instruction d'expression
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: a208951c536883f2f08a6e856e9da48884255b1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186543"
---
# <a name="expression-statement"></a>Instruction d'expression

Les instructions d'expression entraînent des expressions à évaluer. Aucun transfert de contrôle ou d'itération n'a lieu à la suite d'une instruction d'expression.

La syntaxe de l'instruction d'expression est simplement

## <a name="syntax"></a>Syntaxe

```
[expression ] ;
```

## <a name="remarks"></a>Notes

Toutes les expressions appartenant à une instruction d'expression sont évaluées et tous les effets secondaires sont terminés avant l'exécution de l'instruction suivante. Les instructions d'expression les plus courantes sont les assignations et les appels de fonction.  Étant donné que l’expression est facultative, un point-virgule seul est considéré comme une instruction d’expression vide, appelée instruction [null](../cpp/null-statement.md) .

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)
