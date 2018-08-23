---
title: __ull_rshift | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ull_rshift
dev_langs:
- C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c834b3b2284a7a5ae660870b840d3275c985dc9e
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541251"
---
# <a name="ullrshift"></a>__ull_rshift
**Section spécifique à Microsoft**  
  
 sur x64, déplace une valeur 64 bits spécifiée par le premier paramètre à droite d’un nombre de bits spécifié par le deuxième paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `mask`  
 La valeur d’entier 64 bits de décalage vers la droite.  
  
 [in] `nBit`  
 Le nombre de bits de décalage, modulo 32 sur x86 et modulo 64 sur x64.  
  
## <a name="return-value"></a>Valeur de retour  
 Le masque décalés `nBit` bits.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__ull_rshift`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Si le deuxième paramètre est supérieur à 31 sur x86 (63 sur x64), ce nombre est effectuée modulo 32 (64 sur x64) pour déterminer le nombre de bits de décalage. Le `ull` dans le nom indique `unsigned long long (unsigned __int64)`.  
  
## <a name="example"></a>Exemple  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
1  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)