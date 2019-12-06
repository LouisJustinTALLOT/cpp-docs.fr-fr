---
title: Erreur ML irrécupérable A1008
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1008
helpviewer_keywords:
- A1008
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
ms.openlocfilehash: 19b1aa5bdc5f3b254cf87840bbf6fabb03c18ada
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856889"
---
# <a name="ml-fatal-error-a1008"></a>Erreur ML irrécupérable A1008

**imbrication des macros non appariées**

Soit une macro n’a pas été arrêtée avant la fin du fichier, soit la directive de fin [ENDM](../../assembler/masm/endm.md) a été trouvée en dehors d’un bloc macro.

L’une des causes de cette erreur est l’omission du point avant [. RÉPÉTez](../../assembler/masm/dot-repeat.md) ou [. WHILe](../../assembler/masm/dot-while.md).

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>