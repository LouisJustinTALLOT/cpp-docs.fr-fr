---
title: ML erreur non fatale A2031 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf6744224847e114e76df6e7ad6470696d3e8387
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682656"
---
# <a name="ml-nonfatal-error-a2031"></a>Erreur ML non fatale A2031

**doit être Registre de base ou d’index**

Une tentative a tenté d’utiliser un Registre qui n’était pas un Registre de base ou d’index dans une expression de la mémoire.

Par exemple, les expressions suivantes provoquent cette erreur :

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>