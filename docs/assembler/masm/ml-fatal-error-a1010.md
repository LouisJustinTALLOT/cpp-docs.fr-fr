---
title: Erreur ML irrécupérable A1010
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: eb4d77b856e93a8d64ee6c51bec63ceae59b22e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449125"
---
# <a name="ml-fatal-error-a1010"></a>Erreur ML irrécupérable A1010

**imbrication de blocs sans correspondance :**

Un début de bloc ne disposait pas end correspondant, ou une fin du bloc ne disposait pas d’un début correspondant. Parmi les options suivantes peut-être être concerné :

- Une directive de haut niveau tels que [. IF](../../assembler/masm/dot-if.md), [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md), ou [. Bien que](../../assembler/masm/dot-while.md).

- Une directive conditionnelle de l’assembly comme [IF](../../assembler/masm/if-masm.md), [RÉPÉTEZ](../../assembler/masm/repeat.md), ou **tandis que**.

- Une définition de structure ou union.

- Une définition de procédure.

- Une définition des segments.

- Un [POPCONTEXT](../../assembler/masm/popcontext.md) directive.

- Un assembly de conditionnel directive comme une [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), ou **ENDIF** sans une mise en correspondance [IF](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>