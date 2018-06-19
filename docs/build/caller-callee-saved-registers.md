---
title: Registres enregistrés des appelants-appelés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366794"
---
# <a name="callercallee-saved-registers"></a>Registres enregistrés des appelants/appelés
Les registres RAX, RCX, RDX, R8, R9, R10, R11 sont considérés comme volatile et doit être considérée comme détruits sur les appels de fonction (sauf dans le cas contraire sécurité estimer par analyse telles qu’une optimisation de l’ensemble du programme).  
  
 Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14 et R15 sont considérés comme non volatile et doivent être enregistrés et restauré par une fonction qui les utilise.  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)