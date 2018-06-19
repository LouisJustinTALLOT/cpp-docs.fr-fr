---
title: Évaluateur d’expression, erreur CXX0019 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302488"
---
# <a name="expression-evaluator-error-cxx0019"></a>Évaluateur d'expression, erreur CXX0019
cast de type incorrect  
  
 L’évaluateur d’expression C ne peut pas effectuer la conversion lors de l’écriture du type.  
  
 Cette erreur est identique à CAN0019.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Le type spécifié est inconnu.  
  
2.  Trop de niveaux de types pointeur a été effectuée. Par exemple, la conversion de type  
  
    ```  
    (char **)h_message  
    ```  
  
     ne peut pas être évaluée par l’évaluateur d’expression C.