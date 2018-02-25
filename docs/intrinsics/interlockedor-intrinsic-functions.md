---
title: "_InterlockedOr, fonctions intrinsèques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _InterlockedOr8_nf
- _InterlockedOr_HLEAcquire
- _InterlockedOr16_nf
- _InterlockedOr64
- _InterlockedOr8_np
- _InterlockedOr64_cpp
- _InterlockedOr8_acq
- _InterlockedOr_nf
- _InterlockedOr64_acq
- _InterlockedOr_np
- _InterlockedOr8
- _InterlockedOr
- _InterlockedOr64_np
- _InterlockedOr_acq
- _InterlockedOr64_HLERelease
- _InterlockedOr16_np
- _InterlockedOr_cpp
- _InterlockedOr8_rel
- _InterlockedOr64_rel
- _InterlockedOr16_acq
- _InterlockedOr_rel
- _InterlockedOr16_rel
- _InterlockedOr_HLERelease
- _InterlockedOr64_HLEAcquire
- _InterlockedOr16
- _InterlockedOr64_nf
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedOr_acq intrinsic
- InterlockedOr64 intrinsic
- _InterlockedOr_nf intrinsic
- _InterlockedOr intrinsic
- _InterlockedOr64_HLERelease intrinsic
- _InterlockedOr8_rel intrinsic
- _InterlockedOr8_np intrinsic
- _InterlockedOr64_nf intrinsic
- _InterlockedOr_HLERelease intrinsic
- _InterlockedOr16_np intrinsic
- InterlockedOr intrinsic
- _InterlockedOr8_nf intrinsic
- _InterlockedOr16_nf intrinsic
- _InterlockedOr8_acq intrinsic
- _InterlockedOr64 intrinsic
- _InterlockedOr16 intrinsic
- _InterlockedOr64_acq intrinsic
- _InterlockedOr64_HLEAcquire intrinsic
- _InterlockedOr_np intrinsic
- _InterlockedOr64_rel intrinsic
- _InterlockedOr64_np intrinsic
- _InterlockedOr_rel intrinsic
- _InterlockedOr8 intrinsic
- _InterlockedOr16_acq intrinsic
- _InterlockedOr16_rel intrinsic
- _InterlockedOr_HLEAcquire intrinsic
ms.assetid: 5f265240-7af8-44b7-b952-19f3a9c56186
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44949aad405fbfdad776548a73a3152595ffa158
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedor-intrinsic-functions"></a>_InterlockedOr, fonctions intrinsèques
**Section spécifique à Microsoft**  
  
 Effectuer une opération OR atomique au niveau du bit sur une variable partagée par plusieurs threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedOr(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_acq(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_HLEAcquire(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_HLERelease(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_nf(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_np(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_rel(  
   long volatile * Value,  
   long Mask  
);  
char _InterlockedOr8(  
   char volatile * Value,  
   long Mask  
);  
char _InterlockedOr8_acq(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_nf(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_np(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_rel(  
   char volatile * Value,  
   char Mask  
);  
short _InterlockedOr16(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_acq(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_nf(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_np(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_rel(  
   short volatile * Value,  
   short Mask  
);  
__int64 _InterlockedOr64(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_acq(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedOr64_HLEAcquire(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_HLERelease(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedOr64_nf(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_np(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_rel(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in, out] `Value`  
 Pointeur vers le premier opérande, à remplacer par le résultat.  
  
 [in] `Mask`  
 Deuxième opérande.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur d'origine vers laquelle pointe le premier paramètre.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|En-tête|  
|---------------|------------------|------------|  
|`_InterlockedOr`, `_InterlockedOr8`, `_InterlockedOr16`, `_InterlockedOr64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_InterlockedOr_acq`, `_InterlockedOr_nf`, `_InterlockedOr_rel`, `_InterlockedOr8_acq`, `_InterlockedOr8_nf`, `_InterlockedOr8_rel`, `_InterlockedOr16_acq`, `_InterlockedOr16_nf`, `_InterlockedOr16_rel`, `_InterlockedOr64_acq`, `_InterlockedOr64_nf`, `_InterlockedOr64_rel`|ARM|\<intrin.h>|  
|`_InterlockedOr_np`, `_InterlockedOr8_np`, `_InterlockedOr16_np`, `_InterlockedOr64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_InterlockedOr_HLEAcquire`, `_InterlockedOr_HLERelease`, `_InterlockedOr64_HLEAcquire`, `_InterlockedOr64_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
  
## <a name="remarks"></a>Notes  
 Le nombre dans le nom de chaque fonction spécifie la taille en bits des arguments.  
  
 Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d'une section critique. Les fonctions intrinsèques ARM avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agissent pas comme une barrière mémoire.  
  
 Les fonctions intrinsèques avec un suffixe `_np` (pour « no prefetch », « pas de prérécupération ») empêchent l'insertion par le compilateur d'une possible opération de prérécupération.  
  
 Sur les plateformes Intel qui prennent en charge les instructions HLE (Hardware Lock Elision), les fonctions intrinsèques avec les suffixes `_HLEAcquire` et `_HLERelease` comprennent une indication pour le processeur qui peut accélérer les performances en éliminant une étape d'écriture de verrou dans le matériel. Si ces fonctions intrinsèques sont appelées sur des plateformes qui ne prennent pas en charge HLE, l'indication est ignorée.  
  
## <a name="example"></a>Exemple  
  
```  
// _InterlockedOr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedOr)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedOr(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
```Output  
0xffffff00 0xffff00 0xff00ff00  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)