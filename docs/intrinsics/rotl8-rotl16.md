---
title: _rotl8, _rotl16 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _rotl8
- _rotl16
dev_langs:
- C++
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec83d862c119645582a552b7685e5ca364be6f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709137"
---
# <a name="rotl8-rotl16"></a>_rotl8, _rotl16
**Section spécifique à Microsoft**  
  
 Faire pivoter les valeurs d'entrée vers la gauche pour le bit le plus significatif (MSB) d'un nombre spécifié de positions de bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _rotl8(   
   unsigned char value,   
   unsigned char shift   
);  
unsigned short _rotl16(   
   unsigned short value,   
   unsigned char shift   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*valeur*<br/>
[in] Valeur à faire pivoter.  
  
*shift*<br/>
[in] Le nombre de bits de rotation.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur ayant fait l'objet d'une rotation.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_rotl8`|x86, ARM, x64|  
|`_rotl16`|x86, ARM, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Contrairement à une opération de décalage vers la gauche, lors de l'exécution d'une rotation vers la gauche, les bits de poids fort qui se trouvent hors limite sont placés dans les positions de bits les moins significatives.  
  
## <a name="example"></a>Exemple  
  
```  
// rotl.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotl8, _rotl16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,  
               i, _rotl8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",  
            s, nBit, _rotl16(s, nBit));  
}  
```  
  
```Output  
Rotating 0x41 left by 0 bits gives 0x41  
Rotating 0x41 left by 1 bits gives 0x82  
Rotating 0x41 left by 2 bits gives 0x5  
Rotating 0x41 left by 3 bits gives 0xa  
Rotating 0x41 left by 4 bits gives 0x14  
Rotating 0x41 left by 5 bits gives 0x28  
Rotating 0x41 left by 6 bits gives 0x50  
Rotating 0x41 left by 7 bits gives 0xa0  
Rotating unsigned short 0x12 left by 10 bits gives 0x4800  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)