---
title: Erreur ML non fatale A2085
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 729f6f38761171c6ddc4cccfc2443c6a2b597bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177186"
---
# <a name="ml-nonfatal-error-a2085"></a>Erreur ML non fatale A2085

**instruction ou register ne pas accepté dans le mode actuel du processeur**

Une tentative a été effectuée d’utiliser une instruction, Registre ou mot clé qui n’était pas valide pour le mode de processeur actuelle.

Par exemple, les registres 32 bits requièrent [.386](../../assembler/masm/dot-386.md) ou version ultérieure. Les registres de contrôle, telles que CR0 nécessiter mode privilégié [.386P](../../assembler/masm/dot-386p.md) ou version ultérieure. Cette erreur sera également générée pour le **NEAR32**, **FAR32**, et **plat** les mots clés, qui nécessitent. **386** ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>