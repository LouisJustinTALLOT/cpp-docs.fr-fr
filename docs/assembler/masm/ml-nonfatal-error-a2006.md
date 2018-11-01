---
title: Erreur ML non fatale A2006
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 80283bde4dff36e32d276c998f6797b6eeed8160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490062"
---
# <a name="ml-nonfatal-error-a2006"></a>Erreur ML non fatale A2006

**symbole non défini : identificateur**

Une tentative a tenté d’utiliser un symbole qui n’était pas défini.

Parmi les options suivantes peut-être se sont produites :

- Un symbole n’est pas défini.

- Un champ n’était pas un membre de la structure spécifiée.

- Un symbole a été défini dans un fichier include qui n’était pas inclus.

- Un symbole externe a été utilisé sans un [EXTERN](../../assembler/masm/extern-masm.md) ou [EXTERNDEF](../../assembler/masm/externdef.md) directive.

- Un nom de symbole a été mal orthographié.

- Une étiquette de code local a été référencée en dehors de son étendue.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>