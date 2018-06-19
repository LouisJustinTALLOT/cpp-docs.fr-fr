---
title: Erreur ML non fatale A2133 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f240ed6f2e8330017e56334dfcc41be478537c7b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056205"
---
# <a name="ml-nonfatal-error-a2133"></a>Erreur ML non fatale A2133
**remplacé par INVOKE de valeur de Registre**  
  
 Un Registre a été passé comme argument à une procédure, mais le code généré par [INVOKE](../../assembler/masm/invoke.md) pour passer des autres arguments détruit le contenu du Registre.  
  
 Les registres AX, AL, AH, EAX, DX, DL, Diffie-Hellman et EDX peuvent être utilisés par l’assembleur pour effectuer la conversion de données.  
  
 Utilisez un autre registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)