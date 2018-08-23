---
title: __rdtsc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7888f00b1b95a18e839ab61fc8ff28a2646f9875
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540825"
---
# <a name="rdtsc"></a>__rdtsc
**Section spécifique à Microsoft**  
  
 Génère le `rdtsc` instruction, qui retourne l’horodatage du processeur. L’horodatage de processeur enregistre le nombre de cycles d’horloge depuis la dernière réinitialisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Entier non signé 64 bits représentant le nombre de cycles.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__rdtsc`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement comme intrinsèque.  
  
 L’interprétation de la valeur TSC dans cette génération de matériel diffère de celui des versions précédentes de x64. Consultez les manuels de matériel pour plus d’informations.  
  
## <a name="example"></a>Exemple  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
```Output  
3363423610155519 ticks  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)