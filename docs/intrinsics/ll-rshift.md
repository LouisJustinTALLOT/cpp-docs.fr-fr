---
title: __ll_rshift | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs:
- C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8df70d0ba5c0f957620ee204256b6c92ce4c01f1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722070"
---
# <a name="llrshift"></a>__ll_rshift
**Section spécifique à Microsoft**  
  
 Déplace une valeur 64 bits spécifiée par le premier paramètre à droite d’un nombre de bits spécifié par le deuxième paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*Masque*<br/>
[in] La valeur d’entier 64 bits de décalage vers la droite.  
  
*nBit*<br/>
[in] Le nombre de bits de décalage, modulo 64 sur x64 et modulo 32 sur x86.  
  
## <a name="return-value"></a>Valeur de retour  
 Le masque décalés `nBit` bits.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__ll_rshift`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Si le deuxième paramètre est supérieur à 64 sur x64 (32 sur x86), ce nombre est effectuée modulo 64 (32 sur x86) pour déterminer le nombre de bits de décalage. Le `ll` préfixe indique que cette opération se fait sur `long long`, un autre nom pour `__int64`, le type intégral signé de 64 bits.  
  
## <a name="example"></a>Exemple  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **Remarque** si `_ull_rshift` a été utilisé, l’octet le plus significatif de la valeur décalée vers la droite aurait été égal à zéro, donc le résultat souhaité n’aurait été obtenu dans le cas d’une valeur négative.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)