---
title: _mm_cvtsi64x_ss | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb529e8aab204df85de2da0a2fdf4c820964239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340604"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Section spécifique à Microsoft**  
  
 Génère le [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] version étendue de la convertir en entier 64 bits en à la valeur de nombres à virgule flottante simple précision scalaire (`cvtsi2ss`) instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `a`  
 Un `__m128` structure qui contient quatre valeurs à virgule flottante simple précision.  
  
 [in] `b`  
 Un entier 64 bits à convertir en valeur à virgule flottante.  
  
## <a name="return-value"></a>Valeur de retour  
 Un `__m128` structure dont la première valeur à virgule flottante est le résultat de la conversion. Les trois autres valeurs sont copiées telles quelles à partir de `a`.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le `__m128` structure représente un registre XMM, par conséquent, cette fonction intrinsèque autorise une valeur `b` de la mémoire système à déplacer vers un XMM inscrire.  
  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
## <a name="example"></a>Exemple  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__m128](../cpp/m128.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)