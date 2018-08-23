---
title: inline_recursion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 222cb7151d975219d0e92bd1270778586e89b4d3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540562"
---
# <a name="inlinerecursion"></a>inline_recursion
Contrôle l’expansion inline des appels de fonction directe ou mutuellement récursive.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Notes  
 
Utiliser ce pragma pour contrôler les fonctions marqué comme [inline](../cpp/inline-functions-cpp.md) et [__inline](../cpp/inline-functions-cpp.md) ou des fonctions que le compilateur développe automatiquement sous le `/Ob2` option. Utilisation de ce pragma requiert un [/Ob](../build/reference/ob-inline-function-expansion.md) paramètre d’option du compilateur de 1 ou 2. L’état par défaut **inline_recursion** est désactivé. Ce pragma entre en vigueur au premier appel de fonction après sa détection et n'a aucune incidence sur la définition de la fonction.  
  
Le **inline_recursion** pragma contrôle comment les fonctions récursives sont développées. Si **inline_recursion** est désactivée, et si une fonction inline s’appelle elle-même (directement ou indirectement), la fonction est étendue qu’une seule fois. Si **inline_recursion** est activé, la fonction est développée plusieurs fois jusqu'à ce qu’il atteigne la valeur définie avec la [inline_depth](../preprocessor/inline-depth.md) pragma, la valeur par défaut pour les fonctions récursives qui est définie par le `inline_depth` pragma, ou une capacité limite.  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives pragma et mot clé _pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[inline_depth](../preprocessor/inline-depth.md)   
[/Ob (Expansion des fonctions Inline)](../build/reference/ob-inline-function-expansion.md)