---
title: __rdtscp | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d890afe9e19782f19442e8d95709b91a8680278
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="rdtscp"></a>__rdtscp
**Section spécifique à Microsoft**  
  
 Génère le `rdtscp` écrit des instructions, `TSC_AUX[31:0`] à la mémoire et retourne le compteur d’horodatage 64 bits (`TSC)` résultat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [out] `Aux`  
 Pointeur vers un emplacement qui contiendra le contenu du Registre spécifiques à l’ordinateur `TSC_AUX[31:0]`.  
  
## <a name="return-value"></a>Valeur de retour  
 Nombre de cycles d’entier non signé 64 bits.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__rdtscp`|AMD NPT famille 0Fh ou versions ultérieures|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cet intrinsèque génère le `rdtscp` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 27 de `CPUInfo[3] (EDX)`. Ce bit est 1 si l’instruction est prise en charge et 0 dans le cas contraire.  Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `rdtscp` instruction, les résultats sont imprévisibles.  
  
> [!CAUTION]
>  Contrairement aux `rdtsc`, `rdtscp` est une instruction de sérialisation ; Toutefois, le compilateur peut déplacer le code de contourner ce problème intrinsèque.  
  
 L’interprétation de la valeur TSC dans cette génération de matériel diffère de celui des versions antérieures de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Consultez les manuels de matériel pour plus d’informations.  
  
 La signification de la valeur dans `TSC_AUX[31:0]` dépend du système d’exploitation.  
  
## <a name="example"></a>Exemple  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
```Output  
3363423610155519 ticks  
TSC_AUX was 0  
```  
  
**FIN de la section spécifique à Microsoft**  
 Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Voir aussi  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)