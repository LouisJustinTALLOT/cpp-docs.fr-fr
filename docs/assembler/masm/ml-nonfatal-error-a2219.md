---
title: Erreur ML non fatale A2219 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2219
dev_langs:
- C++
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d1ae9eb4b8535ac3f1363bb1059468cddf5636
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056117"
---
# <a name="ml-nonfatal-error-a2219"></a>Erreur ML non fatale A2219
**Alignement incorrect pour le décalage de code de déroulement**  
  
 L’opérande de [. ALLOCSTACK](../../assembler/masm/dot-allocstack.md) et [. SAVEREG](../../assembler/masm/dot-savereg.md) doit être un multiple de 8.  L’opérande de [. SAVEXMM128](../../assembler/masm/dot-savexmm128.md) et [. SETFRAME](../../assembler/masm/dot-setframe.md) doit être un multiple de 16.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)