---
title: _InterlockedExchangePointer, fonctions intrinsèques | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfeb1453cffac6cfe338f42da8b8efe60e18c9f8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42543175"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer, fonctions intrinsèques
**Section spécifique à Microsoft**  
  
 Effectuer une opération d’échange atomique, qui copie l’adresse passée comme deuxième argument au premier et retourne l’adresse d’origine du premier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _InterlockedExchangePointer(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_acq(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_rel(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_nf(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLEAcquire(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLERelease(  
   void * volatile * Target,  
   void * Value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in, out] `Target`  
 Pointeur vers le pointeur vers la valeur à échanger. La fonction définit la valeur sur `Value` et retourne sa valeur précédente.  
  
 [in] `Value`  
 Valeur à échanger avec la valeur pointée par `Target`.  
  
## <a name="return-value"></a>Valeur de retour  
 La fonction renvoie la valeur initiale indiquée par `Target`.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|Header|  
|---------------|------------------|------------|  
|`_InterlockedExchangePointer`|x86, ARM, x64|\<intrin.h>|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h>|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|x64 avec prise en charge HLE|\<immintrin.h>|  
  
 Sur l'architecture x86, `_InterlockedExchangePointer` est une macro qui appelle `_InterlockedExchange`.  
  
## <a name="remarks"></a>Notes  
 Sur un système 64 bits, les paramètres sont 64 bits et doivent être alignés sur les limites 64 bits ; dans le cas contraire, la fonction échoue. Sur un système 32 bits, les paramètres sont 32 bits et doivent être alignés sur les limites 32 bits. Pour plus d’informations, consultez [aligner](../cpp/align-cpp.md).  
  
 Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d'une section critique. La fonction intrinsèque avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agit pas comme une barrière mémoire.  
  
 Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l'indication est ignorée.  
  
 Ces routines sont disponibles seulement comme fonctions intrinsèques.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)