---
title: _InterlockedAddLargeStatistic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 602cfb415c17c9e57d9fc1e932777cd1929e5f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331395"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Section spécifique à Microsoft**  
  
 Effectue une addition verrouillée dans lequel le premier opérande est une valeur 64 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in, out] `Addend`  
 Pointeur vers le premier opérande pour l’opération d’ajout. La valeur indiquée est remplacée par le résultat de l’addition.  
  
 [in] `Value`  
 Le deuxième opérande. valeur à ajouter à la première opérande.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur du deuxième opérande.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette fonction intrinsèque n’est pas atomique, car il est implémenté comme deux séparer les instructions verrouillées. Une lecture 64 bits atomique qui se produit sur un autre thread pendant l’exécution de cette intrinsèque peut entraîner une valeur incohérente en cours de lecture.  
  
 Cette fonction se comporte comme une barrière en lecture-écriture. Pour plus d’informations, consultez [l’intrinsèque _ReadWriteBarrier](../intrinsics/readwritebarrier.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)