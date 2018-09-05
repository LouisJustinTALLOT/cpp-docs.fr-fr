---
title: ML erreur non fatale A2133 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678064"
---
# <a name="ml-nonfatal-error-a2133"></a>Erreur ML non fatale A2133

**remplacé par INVOKE de valeur de Registre**

Un Registre a été passé en tant qu’argument à une procédure, mais le code généré par [INVOKE](../../assembler/masm/invoke.md) pour passer des autres arguments détruit le contenu du Registre.

Les registres AX, AL, AH, EAX, DX, DL, Diffie-Hellman et EDX peuvent être utilisés par l’assembleur pour effectuer la conversion de données.

Utiliser un autre registre.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>