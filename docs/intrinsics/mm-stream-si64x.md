---
title: _mm_stream_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_si64x
dev_langs:
- C++
helpviewer_keywords:
- movnti instruction
- _mm_stream_si64x intrinsic
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0385f2812c58b65102780780a1b7a548b2b08429
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540019"
---
# <a name="mmstreamsi64x"></a>_mm_stream_si64x  
  
**Section spécifique à Microsoft**  
  
 Génère la movnti, instruction. Écrit les données `Source` vers un emplacement mémoire spécifié par `Dest`, sans polluer les caches.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _mm_stream_si64x(   
   __int64 * Dest,   
   __int64 Source   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
 [out] `Dest`  
 Un pointeur vers l’emplacement à écrire les données source.  
  
 [in] `Source`  
 Les données à écrire.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_mm_stream_si64x`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
## <a name="example"></a>Exemple  
  
```C  
// _mm_stream_si64x.c  
// processor: x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_mm_stream_si64x)  
  
int main()  
{  
    __int64 val = 0xFFFFFFFFFFFFI64;  
    __int64 a[10];  
  
    memset(a, 0, sizeof(a));  
    _mm_stream_si64x(a+1, val);  
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
```Output  
0 ffffffffffff 0 0  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)