---
title: Erreur ML non fatale A2008 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50f7329f698d23f875a29bc316067c39e8d1b8c1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055217"
---
# <a name="ml-nonfatal-error-a2008"></a>Erreur ML non fatale A2008
**Erreur de syntaxe :**  
  
 Un jeton à l’emplacement actuel a provoqué une erreur de syntaxe.  
  
 Une des opérations suivantes peut-être se sont produites :  
  
-   Un préfixe de point a été ajouté à ou omis à partir d’une directive.  
  
-   Un mot réservé (tel que **C** ou **taille**) a été utilisé en tant qu’identificateur.  
  
-   Une instruction a été utilisée qui n’était pas disponible avec la sélection actuelle de processeur ou de coprocesseur.  
  
-   Un opérateur d’exécution de comparaison (tels que `==`) a été utilisée dans une instruction conditionnelle assembly au lieu d’un opérateur relationnel (tel que [EQ](../../assembler/masm/operator-eq.md)).  
  
-   Une instruction ou une directive a été spécifiée trop peu d’opérandes.  
  
-   Une directive obsolète a été utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)