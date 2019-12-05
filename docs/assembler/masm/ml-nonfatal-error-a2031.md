---
title: Erreur ML non fatale A2031
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: f964c67ba7bf399e9a3761e4e201662a6a712a1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856699"
---
# <a name="ml-nonfatal-error-a2031"></a>Erreur ML non fatale A2031

**doit être un registre d’index ou de base**

Une tentative d’utilisation d’un registre qui n’était pas un registre de base ou d’index dans une expression de mémoire a été effectuée.

Par exemple, les expressions suivantes provoquent cette erreur :

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>