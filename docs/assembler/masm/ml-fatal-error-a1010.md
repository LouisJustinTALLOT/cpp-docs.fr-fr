---
title: Erreur ML irrécupérable A1010
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856876"
---
# <a name="ml-fatal-error-a1010"></a>Erreur ML irrécupérable A1010

**imbrication des blocs non appariés :**

Le début d’un bloc n’a pas de terminaison correspondante, ou la fin d’un bloc n’a pas de début correspondant. L’une des conditions suivantes peut être utilisée :

- Directive de niveau supérieur, telle que [. Si](../../assembler/masm/dot-if.md), [. REPEAT](../../assembler/masm/dot-repeat.md), ou [. WHILe](../../assembler/masm/dot-while.md).

- Directive d’assembly conditionnel, telle que [If](../../assembler/masm/if-masm.md), [REPEAT](../../assembler/masm/repeat.md)ou **while**.

- Définition de structure ou d’Union.

- Définition de procédure.

- Définition de segment.

- Directive [POPCONTEXT](../../assembler/masm/popcontext.md) .

- Une directive d’assembly conditionnel, telle qu' [else](../../assembler/masm/else-masm.md), [ElseIf](../../assembler/masm/elseif-masm.md)ou **endif** , sans [If](../../assembler/masm/if-masm.md)correspondant.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>