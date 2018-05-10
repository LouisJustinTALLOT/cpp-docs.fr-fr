---
title: boucle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9af0e01cd29d6fe89e0cd0d6c5ff4a7030909799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="loop"></a>boucle
Contrôle la façon dont le code de la boucle doit être considéré par le paralléliseur automatique et/ou exclut une boucle de la considération par le vectoriseur automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hint_parallel(` `n` `)`  
 Indique au compilateur que cette boucle doit être parallélisée sur `n` threads, où `n` est un littéral entier positif ou zéro. Si `n` est zéro, le nombre maximal de threads est utilisé au moment de l'exécution. Il s'agit d'un indicateur pour le compilateur, et non d'une commande, et il n'existe aucune garantie que la boucle soit parallélisée. Si la boucle présente des dépendances de données ou des problèmes structurels, par exemple si la boucle stocke dans un élément scalaire utilisé au-delà du corps de la boucle, la boucle ne sera pas parallélisée.  
  
 Le compilateur ignore cette option, sauf si le [/Qpar](../build/reference/qpar-auto-parallelizer.md) commutateur du compilateur est spécifiée.  
  
 `no_vector`  
 Par défaut, le vectoriseur automatique est activé et tente de vectoriser toutes les boucles considérées comme en tirant parti. Spécifiez ce pragma pour désactiver le vectoriseur automatique de la boucle qui le suit.  
  
 `ivdep`  
 Indique au compilateur d'ignorer les dépendances vectorielles pour cette boucle. Doit être utilisé avec `hint_parallel`.  
  
## <a name="remarks"></a>Notes  
 Pour utiliser le pragma `loop`, placez-le immédiatement avant la définition de la boucle, et non pas à l'intérieur de cette définition. Le pragma prend effet pour la portée de la boucle qui le suit. Vous pouvez appliquer plusieurs pragmas à une boucle, dans n'importe quel ordre, mais chacun doit être indiqué dans une instruction pragma distincte.  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisation et vectorisation automatiques](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)