---
title: _mm_stream_sd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_sd
dev_langs:
- C++
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb8608e03a514228ecdbaf321124c17a00aeb5c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700165"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Section spécifique à Microsoft**  
  
 Écrit les données de 64 bits dans un emplacement de mémoire sans polluer les caches.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*dest*<br/>
[out] Pointeur vers l’emplacement où la source de données sera écrit.  
  
*Source*<br/>
[in] Une valeur 128 bits contenant le `double` valeur à écrire dans sa partie inférieure à 64 bits...  
  
## <a name="return-value"></a>Valeur de retour  
 Aucun.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_mm_stream_sd`|SSE4a|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cet intrinsèque génère le `movntsd` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 6 de `CPUInfo[2] (ECX)`. Ce bit est 1 si le matériel prend en charge les cette instruction et 0 dans le cas contraire.  
  
 Si vous exécutez le code qui utilise le `_mm_stream_sd` intrinsèque sur du matériel qui ne prend pas en charge la `movntsd` instruction, les résultats sont imprévisibles.  
  
## <a name="example"></a>Exemple  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128d vals;  
    double d[2];  
  
    d[0] = -1.;  
    d[1] = -2.;  
    vals.m128d_f64[0] = 0.;  
    vals.m128d_f64[1] = 1.;  
    _mm_stream_sd(&d[1], vals);  
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;  
}  
  
```  
  
```Output  
d[0] = -1, d[1] = 1  
```  
  
**FIN de la section spécifique à Microsoft**  

Copyright 2007 par avancées Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Voir aussi  
 [_mm_stream_ss](../intrinsics/mm-stream-ss.md)   
 [_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)