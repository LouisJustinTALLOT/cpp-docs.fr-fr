---
title: _BitScanForward, _BitScanForward64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
dev_langs:
- C++
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4720ca4a65a543ca09412ac0c1eb1e65bf6cdd23
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538655"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64
**Section spécifique à Microsoft**  
  
 Rechercher les données de masque du bit le moins significatif (LSB) au bit le plus significatif (MSB) pour un bit défini (1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _BitScanForward(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanForward64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [out] `Index`  
 Chargé avec la position de bit du premier bit défini (1) détecté.  
  
 [in] `Mask`  
 Valeur 32 bits ou 64 bits à rechercher.  
  
## <a name="return-value"></a>Valeur de retour  
 0 si le masque est zéro ; différent de zéro dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
 Si un bit défini est détecté, la position de bit du premier bit défini détecté est retournée dans le premier paramètre. Si aucun bit défini n'est détecté, 0 est retourné ; dans le cas contraire, 1 est retourné.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_BitScanForward`|x86, ARM, x64|  
|`_BitScanForward64`|ARM, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="example"></a>Exemple  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## <a name="input"></a>Entrée  
  
```  
12  
```  
  
## <a name="sample-output"></a>Résultat de l'exemple  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)