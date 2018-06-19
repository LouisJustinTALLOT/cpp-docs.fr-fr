---
title: Erreur ML irrécupérable A1007 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b883fad01943cd8cff71b3da9dee66407ccc93
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055727"
---
# <a name="ml-fatal-error-a1007"></a>Erreur ML irrécupérable A1007
**niveau d’imbrication trop profond**  
  
 L’assembleur atteint sa limite d’imbrication. La limite est de 20 niveaux sauf indication contraire dans le cas contraire.  
  
 Une des conditions suivantes a été imbriquée trop profondément :  
  
-   Une directive de haut niveau tels que [. IF](../../assembler/masm/dot-if.md), [. RÉPÉTEZ les](../../assembler/masm/dot-repeat.md), ou [. Alors que](../../assembler/masm/dot-while.md).  
  
-   Une définition de structure.  
  
-   Une directive conditionnelle de l’assembly.  
  
-   Une définition de procédure.  
  
-   A [PUSHCONTEXT](../../assembler/masm/pushcontext.md) directive (la limite est 10).  
  
-   Une définition de segment.  
  
-   Un fichier include.  
  
-   Une macro.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)