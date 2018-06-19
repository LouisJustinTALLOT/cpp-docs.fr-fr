---
title: push_macro | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81e41ef7bf7b93e4b2a533dddcb82fee904cb428
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912990"
---
# <a name="pushmacro"></a>push_macro
Enregistre la valeur de la *macro_name* (macro) en haut de la pile pour cette macro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez récupérer la valeur de *macro_name* avec **pop_macro**.  
  
 Consultez [pop_macro](../preprocessor/pop-macro.md) pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)