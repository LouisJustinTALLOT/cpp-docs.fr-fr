---
title: _umul128 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umul128
dev_langs:
- C++
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6998b51be8fd11092c4266fa7eee7434be8e5b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331530"
---
# <a name="umul128"></a>_umul128
**Section spécifique à Microsoft**  
  
 Multiplie deux entiers non signés 64 bits passés comme les deux premiers arguments, place les 64 bits de poids fort du produit dans l'entier non signé 64 bits vers lequel pointe `HighProduct` et retourne les 64 bits de poids faible du produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 _umul128(   
   unsigned __int64 Multiplier,   
   unsigned __int64 Multiplicand,   
   unsigned __int64 *HighProduct   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Multiplier`  
 Premier entier de 64 bits à multiplier.  
  
 [in] `Multiplicand`  
 Second entier de 64 bits à multiplier.  
  
 [out] `HighProduct`  
 64 bits de poids fort du produit.  
  
## <a name="return-value"></a>Valeur de retour  
 64 bits de poids faible du produit.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|Header|  
|---------------|------------------|------------|  
|`_umul128`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
  
## <a name="example"></a>Exemple  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)