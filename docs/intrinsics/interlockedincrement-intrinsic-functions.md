---
title: _InterlockedIncrement, fonctions intrinsèques | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 369d7c1c6c5bf2201c52bab67361f196b309c6f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702544"
---
# <a name="interlockedincrement-intrinsic-functions"></a>_InterlockedIncrement, fonctions intrinsèques
**Section spécifique à Microsoft**  
  
 Fournir la prise en charge intrinsèque du compilateur pour le Kit de développement logiciel Windows Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*lpAddend*<br/>
[in, out] Pointeur vers la variable à incrémenter.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour est la valeur incrémentée résultante.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|Header|  
|---------------|------------------|------------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|  
  
## <a name="remarks"></a>Notes  
 Il existe plusieurs variantes de `_InterlockedIncrement` qui varient selon les types de données qu'elles impliquent et l'utilisation d'une sémantique acquire ou release spécifique au processeur.  
  
 La fonction `_InterlockedIncrement` opère sur des valeurs entières de 32 bits, `_InterlockedIncrement16` sur des valeurs entières de 16 bits et `_InterlockedIncrement64` sur des valeurs entières de 64 bits.  
  
 Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d'une section critique. La fonction intrinsèque avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agit pas comme une barrière mémoire.  
  
 La variable vers laquelle pointe le paramètre `lpAddend` doit être alignée sur une limite de 32 bits. Dans le cas contraire, cette fonction échoue sur les systèmes x86 multiprocesseurs et les systèmes autres que x86. Pour plus d’informations, consultez [aligner](../cpp/align-cpp.md).  
  
 La fonction Win32 est déclarée dans `Wdm.h` ou `Ntddk.h`.  
  
 Ces routines sont disponibles seulement comme fonctions intrinsèques.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple montrant comment utiliser `_InterlockedIncrement`, consultez [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)