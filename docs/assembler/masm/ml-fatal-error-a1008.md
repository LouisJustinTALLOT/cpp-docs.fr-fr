---
title: Erreur ML irrécupérable A1008 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1008
dev_langs:
- C++
helpviewer_keywords:
- A1008
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec709823856e17c90d4af2a06262b30c966f39c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691936"
---
# <a name="ml-fatal-error-a1008"></a>Erreur ML irrécupérable A1008

**imbrication de macro sans correspondance**

Une macro n’est pas terminée avant la fin du fichier ou la directive fin [ENDM](../../assembler/masm/endm.md) a été trouvé en dehors d’un bloc de macro.

Une des causes de cette erreur est l’omission du point avant [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md) ou [. Bien que](../../assembler/masm/dot-while.md).

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>