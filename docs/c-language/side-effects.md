---
title: Effets secondaires | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e6e6dff87e447a3885906130b6a08286643d6a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="side-effects"></a>Effets secondaires
L'ordre d'évaluation des expressions est défini par l'implémentation spécifique, sauf lorsque le langage garantit un ordre d'évaluation particulier (comme décrit dans [Priorité et ordre d'évaluation](../c-language/precedence-and-order-of-evaluation.md)). Par exemple, des effets secondaires se produisent dans les appels de fonction suivants :  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 Les arguments d'un appel de fonction peuvent être évalués dans n'importe quel ordre. L'expression `i + 1` peut être évaluée avant `i = j + 2`, ou `i = j + 2` peut être évaluée avant `i + 1`. Le résultat diffère à chaque fois. De même, il est impossible de garantir quels caractères sont passés réellement à `myproc`. Étant donné que les opérations d'incrémentation et de décrémentation unaires impliquent des assignations, ces opérations peuvent provoquer des effets secondaires, comme illustré dans l'exemple suivant :  
  
```  
x[i] = i++;  
```  
  
 Dans cet exemple, la valeur de `x` modifiée est imprévisible. La valeur de l'indice peut être la nouvelle ou l'ancienne valeur de `i`. Le résultat peut varier selon le compilateur ou le niveau d'optimisation.  
  
 Comme C ne définit pas l'ordre d'évaluation des effets secondaires, les deux méthodes d'évaluation abordées ci-dessus sont correctes et peuvent être implémentées. Pour vous assurer que votre code est portable et clair, évitez les instructions qui dépendent d'un ordre d'évaluation particulier pour les effets secondaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluation des expressions](../c-language/expression-evaluation-c.md)