---
title: Erreur ML non fatale A2085
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3bd89fb2b7f8b755cdb095e63ed89386332ecf9d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855756"
---
# <a name="ml-nonfatal-error-a2085"></a>Erreur ML non fatale A2085

**instruction ou inscription non acceptée en mode UC actuel**

Une tentative d’utilisation d’une instruction, d’un registre ou d’un mot clé qui n’était pas valide pour le mode de processeur actuel a été effectuée.

Par exemple, les registres 32 bits requièrent [. 386](../../assembler/masm/dot-386.md) ou version ultérieure. Les registres de contrôle tels que Registre CR0 nécessitent le mode privilégié [. 386P](../../assembler/masm/dot-386p.md) ou version ultérieure. Cette erreur est également générée pour les mots clés **NEAR32**, **FAR32**et **Flat** , qui requièrent. **386** ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>