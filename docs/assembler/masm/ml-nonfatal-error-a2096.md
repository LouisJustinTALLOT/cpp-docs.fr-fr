---
title: Erreur ML non fatale A2096 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053670"
---
# <a name="ml-nonfatal-error-a2096"></a>Erreur ML non fatale A2096
**segment, groupe ou un Registre de segment attendu**  
  
 Un segment ou un groupe était attendu mais n’a été trouvé.  
  
 Une des conditions suivantes s’est produite :  
  
-   L’opérande de gauche spécifiée avec le segment remplacent l’opérateur (**:**) n’était pas un segment historique (CS, DS, SS, ES, FS ou GS), nom du groupe, nom du segment ou expression de segment.  
  
-   Le [SUPPOSÉ](../../assembler/masm/assume.md) la directive a été attribuée à un Registre de segment sans une adresse valide de segment, Registre de segment, groupe ou spéciale **plat** groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)