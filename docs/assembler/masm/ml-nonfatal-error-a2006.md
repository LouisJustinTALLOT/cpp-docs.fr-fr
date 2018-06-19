---
title: Erreur ML non fatale A2006 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d2f7df00d1c0658ee8301fbde1efe2522b52fc
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054853"
---
# <a name="ml-nonfatal-error-a2006"></a>Erreur ML non fatale A2006
**symbole non défini : identificateur**  
  
 Un utilisateur a tenté d’utiliser un symbole n’a été défini.  
  
 Une des opérations suivantes peut-être se sont produites :  
  
-   Un symbole n’a pas été défini.  
  
-   Un champ n’est pas un membre de la structure spécifiée.  
  
-   Un symbole a été défini dans un fichier include qui n’a pas été inclus.  
  
-   Un symbole externe a été utilisé sans un [EXTERN](../../assembler/masm/extern-masm.md) ou [EXTERNDEF](../../assembler/masm/externdef.md) la directive.  
  
-   Un nom de symbole a été mal orthographié.  
  
-   Une étiquette de codes locale a été référencée en dehors de son étendue.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)