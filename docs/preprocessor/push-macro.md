---
title: push_macro | Microsoft Docs
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
ms.openlocfilehash: 70b472ba11445cdc5aa2a192d02d82c51d724b8c
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539959"
---
# <a name="pushmacro"></a>push_macro
Enregistre la valeur de la *macro_name* macro en haut de la pile pour cette macro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma push_macro("  
macro_name  
")  
```  
  
## <a name="remarks"></a>Notes  
 
Vous pouvez récupérer la valeur de *macro_name* avec `pop_macro`.  
  
Consultez [pop_macro](../preprocessor/pop-macro.md) pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)