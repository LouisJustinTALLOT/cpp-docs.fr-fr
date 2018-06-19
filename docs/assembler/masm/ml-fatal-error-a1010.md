---
title: Erreur ML irrécupérable A1010 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b622595b6994c4c4eaa74ed8f824f28dffe89b1a
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057680"
---
# <a name="ml-fatal-error-a1010"></a>Erreur ML irrécupérable A1010
**imbrication de blocs non appariées :**  
  
 Un début du bloc ne disposait pas d’end correspondant, ou une fin de bloc n’a pas d’un début correspondant. Un des éléments suivants peut-être être concerné :  
  
-   Une directive de haut niveau tels que [. IF](../../assembler/masm/dot-if.md), [. RÉPÉTEZ les](../../assembler/masm/dot-repeat.md), ou [. Alors que](../../assembler/masm/dot-while.md).  
  
-   Une directive conditionnelle de l’assembly comme [IF](../../assembler/masm/if-masm.md), [RÉPÉTEZ](../../assembler/masm/repeat.md), ou **tandis que**.  
  
-   Une définition de structure ou union.  
  
-   Une définition de procédure.  
  
-   Une définition de segment.  
  
-   A [POPCONTEXT](../../assembler/masm/popcontext.md) la directive.  
  
-   Un assembly de conditionnelle directive comme une [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), ou **ENDIF** sans une correspondance [IF](../../assembler/masm/if-masm.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)