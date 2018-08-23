---
title: __shiftleft128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftleft128
dev_langs:
- C++
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3ca2c389b00126ff477b8e184d690afce07c484
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538860"
---
# <a name="shiftleft128"></a>__shiftleft128
**Section spécifique à Microsoft**  
  
 Décale une quantité de 128 bits, représentée par deux quantités de 64 bits `LowPart` et `HighPart`, vers la gauche d'un nombre de bits spécifié par `Shift` et retourne les 64 bits de poids fort du résultat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __shiftleft128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `LowPart`  
 64 bits de poids faible de la quantité de 128 bits à décaler.  
  
 [in] `HighPart`  
 64 bits de poids fort de la quantité de 128 bits à décaler.  
  
 [in] `Shift`  
 Nombre de bits à décaler.  
  
## <a name="return-value"></a>Valeur de retour  
 64 bits de poids fort du résultat.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__shiftleft128`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 La valeur `Shift` est toujours modulo 64 pour que, par exemple, si vous appelez `__shiftleft128(1, 0, 64)`, la fonction décale les `0` bits de la partie inférieure vers la gauche et renvoie une partie élevée de `0` et non `1` comme on pourrait s'y attendre.  
  
## <a name="example"></a>Exemple  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
```Output  
0x100000000000000001 << 1 = 0x200000000000000002  
0x100000000000000001 >> 1 = 0x080000000000000000  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__shiftright128](../intrinsics/shiftright128.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)