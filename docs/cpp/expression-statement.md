---
title: Instruction d’expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60879ca8792e3259a69b7a9a3de6cd83dce0d6d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411578"
---
# <a name="expression-statement"></a>Instruction d'expression
Les instructions d'expression entraînent des expressions à évaluer. Aucun transfert de contrôle ou d'itération n'a lieu à la suite d'une instruction d'expression.  
  
 La syntaxe de l'instruction d'expression est simplement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>Notes  
 Toutes les expressions appartenant à une instruction d'expression sont évaluées et tous les effets secondaires sont terminés avant l'exécution de l'instruction suivante. Les instructions d'expression les plus courantes sont les assignations et les appels de fonction.  Étant donné que l’expression est facultative, seul un point-virgule est considéré comme une instruction d’expression vide, appelée le [null](../cpp/null-statement.md) instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)