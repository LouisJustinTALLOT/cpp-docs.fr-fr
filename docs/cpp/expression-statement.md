---
title: Instruction d'expression
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2973c3e0a1cd59edfc7ef1e771454b780da23cf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562446"
---
# <a name="expression-statement"></a>Instruction d'expression

Les instructions d'expression entraînent des expressions à évaluer. Aucun transfert de contrôle ou d'itération n'a lieu à la suite d'une instruction d'expression.

La syntaxe de l'instruction d'expression est simplement

## <a name="syntax"></a>Syntaxe

```
[expression ] ;
```

## <a name="remarks"></a>Notes

Toutes les expressions appartenant à une instruction d'expression sont évaluées et tous les effets secondaires sont terminés avant l'exécution de l'instruction suivante. Les instructions d'expression les plus courantes sont les assignations et les appels de fonction.  Dans la mesure où l’expression est facultative, seul un point-virgule est considéré comme une instruction d’expression vide, appelée le [null](../cpp/null-statement.md) instruction.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)