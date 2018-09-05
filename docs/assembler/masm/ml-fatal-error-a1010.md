---
title: Erreur ML irrécupérable A1010 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7e8698951e8ef59e0433134ec992af5d5f77f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676295"
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