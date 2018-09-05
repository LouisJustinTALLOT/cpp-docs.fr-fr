---
title: ML erreur non fatale A2206 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2206
dev_langs:
- C++
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10edbe68ca7f0093cdeb6a9ca5a02cde07f556e6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676346"
---
# <a name="ml-nonfatal-error-a2206"></a>Erreur ML non fatale A2206

**opérateur manquant dans l’expression**

Une expression ne peut pas être évaluée, car il manque un opérateur. Ce message d’erreur peut également être un effet secondaire d’une erreur de programme précédent.

La ligne suivante génère cette erreur :

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>