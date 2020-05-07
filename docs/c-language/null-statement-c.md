---
title: null, instruction (C)
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
ms.openlocfilehash: 4fdfa2283e40856ccaffd55daacb697b1344134b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343420"
---
# <a name="null-statement-c"></a>null, instruction (C)

Une « instruction null » est une instruction contenant uniquement un point-virgule ; elle peut figurer partout où une instruction est attendue. Rien ne se produit lorsqu'une instruction null est exécutée. La façon correcte de coder une instruction null est :

## <a name="syntax"></a>Syntaxe

> **;**

## <a name="remarks"></a>Notes 

Les instructions telles que **do**, **for**, **if** et `while` requièrent qu'une instruction exécutable apparaissent comme corps d'instruction. L’instruction null répond à la syntaxe requise dans les situations qui ne nécessitent pas de corps d’instruction substantiel.

Comme pour toute autre instruction C, vous pouvez inclure une étiquette avant une instruction null. Pour étiqueter un élément qui n'est pas une instruction, telle que l'accolade fermante d'une instruction composée, vous pouvez étiqueter une instruction null et l'insérer immédiatement avant l'élément pour obtenir le même effet.

L'exemple suivant illustre l'instruction null :

```C
for ( i = 0; i < 10; line[i++] = 0 )
     ;
```

Dans cet exemple, l'expression de boucle de l'instruction **for**`line[i++] = 0` initialise les 10 premiers éléments de `line` à 0. Le corps d'instruction est une instruction null, car aucune autre instruction n'est nécessaire.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
