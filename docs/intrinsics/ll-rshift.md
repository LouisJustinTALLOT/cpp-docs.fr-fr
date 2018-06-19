---
title: __ll_rshift | Documents Microsoft
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
ms.openlocfilehash: 4e086339c41f789323cb4aab386a96dae27a0eeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324926"
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
 [in] `Mask`  
 La valeur d’entier 64 bits de décalage vers la droite.  
  
 [in] `nBit`  
 Le nombre de bits de décalage, modulo 64 sur x64 et modulo 32 sur x86.  
  
## <a name="return-value"></a>Valeur de retour  
 Le masque décale `nBit` bits.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__ll_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Si le deuxième paramètre est supérieur à 64 sur x64 (32 sur x86), ce nombre est effectuée modulo 64 (32 sur x86) pour déterminer le nombre de bits à décaler. Le `ll` préfixe indique qu’il s’agit une opération sur `long long`, un autre nom pour `__int64`, le type intégral signé de 64 bits.  
  
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
  
 **Remarque** si `_ull_rshift` a été utilisé, l’octet le plus significatif de la valeur décalée vers la droite aurait égal à zéro, donc le résultat souhaité n’aurait été obtenu dans le cas d’une valeur négative.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)