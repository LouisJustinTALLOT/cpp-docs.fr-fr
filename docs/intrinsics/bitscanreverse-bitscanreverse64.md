---
title: _BitScanReverse, _BitScanReverse64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs:
- C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe9fc90556c15cdab13f68647f07b877aa15abf
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538482"
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64
**Section spécifique à Microsoft**  
  
 Rechercher les données de masque du bit le plus significatif (MSB) au bit le moins significatif (LSB) pour un bit défini (1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _BitScanReverse(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanReverse64(  
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
 Différent de zéro si `Index` a été défini ou 0 si aucun bit défini n'a été détecté.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|Header|  
|---------------|------------------|------------|  
|`_BitScanReverse`|x86, ARM, x64|\<intrin.h>|  
|`_BitScanReverse64`|ARM, x64||  
  
## <a name="example"></a>Exemple  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
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
Mask: 12 Index: 3  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)