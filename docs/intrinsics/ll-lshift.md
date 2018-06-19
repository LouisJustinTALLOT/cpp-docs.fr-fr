---
title: __ll_lshift | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs:
- C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cf50287c28fe530df939488c4e707d17aede03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327370"
---
# <a name="lllshift"></a>__ll_lshift
**Section spécifique à Microsoft**  
  
 Décale la valeur 64 bits fournie à gauche du nombre de bits spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Mask`  
 La valeur d’entier 64 bits de décalage vers la gauche.  
  
 [in] `nBit`  
 Nombre de bits à décaler.  
  
## <a name="return-value"></a>Valeur de retour  
 Le masque décalée vers la gauche en `nBit` bits.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__ll_lshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Si vous compilez votre programme à l’aide de l’architecture 64 bits et `nBit` est supérieur à 63, le nombre de bits de décalage est `nBit` modulo 64. Si vous compilez votre programme à l’aide de l’architecture 32 bits et `nBit` est supérieur à 31, le nombre de bits de décalage est `nBit` modulo 32.  
  
 Le `ll` dans le nom indique qu’il s’agit une opération sur `long long` (`__int64`).  
  
## <a name="example"></a>Exemple  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
10000  
```  
  
 **Remarque** il n’existe aucune version non signée de l’opération de décalage vers la gauche. C’est parce que `__ll_lshift` utilise déjà un paramètre d’entrée non signé. Le décalage vers la droite, à la différence ne de connexion pour le décalage vers la gauche, car le bit le moins significatif dans le résultat est toujours défini sur zéro, quel que soit le signe de la valeur décalée vers.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)