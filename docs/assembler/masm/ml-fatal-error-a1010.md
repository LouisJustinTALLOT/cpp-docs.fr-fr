---
description: 'En savoir plus sur : ML d’erreur irrécupérable A1010'
title: Erreur ML irrécupérable A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 4a00d9594c71c8a22942e869d109bf51176394c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129504"
---
# <a name="ml-fatal-error-a1010"></a>Erreur ML irrécupérable A1010

**imbrication des blocs non appariés :**

Le début d’un bloc n’a pas de terminaison correspondante, ou la fin d’un bloc n’a pas de début correspondant. L’une des conditions suivantes peut être utilisée :

- Directive de niveau supérieur, telle que [. Si](dot-if.md), [. REPEAT](dot-repeat.md), ou [. WHILe](dot-while.md).

- Directive d’assembly conditionnel, telle que [If](if-masm.md), [REPEAT](repeat.md)ou **while**.

- Définition de structure ou d’Union.

- Définition de procédure.

- Définition de segment.

- Directive [POPCONTEXT](popcontext.md) .

- Une directive d’assembly conditionnel, telle qu' [else](else-masm.md), [ElseIf](elseif-masm.md)ou **endif** , sans [If](if-masm.md)correspondant.

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
