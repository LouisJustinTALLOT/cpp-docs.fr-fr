---
title: __popcnt16, __popcnt, __popcnt64 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
dev_langs: C++
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45e60a412dc24f685fd375ebc19c109b2bee0e2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16, __popcnt, __popcnt64
**Section spécifique à Microsoft**  
  
 Compte le nombre de bits (peuplement) dans un 16, 32 ou entier non signé de 64 octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `value`  
 Les 16, 32 ou entier non signé de 64 bits pour lequel nous souhaitons le volume de peuplement.  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de bits un dans le `value` paramètre.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__popcnt16`|Manipulation de bits avancées|  
|`__popcnt`|Manipulation de bits avancées|  
|`__popcnt64`|Manipulation de bits avancées en mode 64 bits.|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Chacune de ces fonctions intrinsèques génère le `popcnt` instruction.  La taille de la valeur que la `popcnt` instruction retourne une valeur est identique à la taille de son argument.  En mode 32 bits ne des aucun 64 bits registres à caractère général, par conséquent, ne 64 bits `popcnt`.  
  
 Pour déterminer la prise en charge matérielle pour le `popcnt` instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x00000001` et vérifiez le bit 23 de `CPUInfo[2] (ECX)`. Ce bit est 1 si l’instruction est prise en charge et 0 dans le cas contraire. Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `popcnt` instruction, les résultats sont imprévisibles.  
  
## <a name="example"></a>Exemple  
  
```  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__popcnt16(0x0) = 0  
__popcnt16(0xff) = 8  
__popcnt16(0xffff) = 16  
__popcnt(0x0) = 0  
__popcnt(0xff) = 8  
__oopcnt(0xffff) = 16  
__popcnt(0xffffffff) = 32  
```  
  
**FIN de la section spécifique à Microsoft**  
 Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)