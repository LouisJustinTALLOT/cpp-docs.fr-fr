---
title: Erreur du compilateur C2439 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33bfe8ebf00850a54020b2a3f21159daf28b7224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225687"
---
# <a name="compiler-error-c2439"></a>Erreur du compilateur C2439
'identificateur' : membre n’a pas pu être initialisé.  
  
 Une classe, une structure ou un membre d’union ne peut pas être initialisé.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  La tentative d’initialiser une classe de base indirecte ou une structure.  
  
2.  Tentative d’initialisation d’un membre hérité d’une classe ou structure. Un membre hérité doit être initialisé par le constructeur de la classe ou structure.