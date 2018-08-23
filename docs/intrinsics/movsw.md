---
title: __movsw | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __movsw
dev_langs:
- C++
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f25cea28d18f8377def35959be573c1a41f9098b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540230"
---
# <a name="movsw"></a>__movsw
**Section spécifique à Microsoft**  
  
 Génère une chaîne de déplacer (`rep movsw`) instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __movsw(   
   unsigned short* Dest,   
   unsigned short* Source,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [out] `Dest`  
 La destination de l’opération.  
  
 [in] `Source`  
 La source de l’opération.  
  
 [in] `Count`  
 Le nombre de mots à copier.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__movsw`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le résultat est que la première `Count` mots vers lequel pointe `Source` sont copiés vers le `Dest` chaîne.  
  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
## <a name="example"></a>Exemple  
  
```  
// movsw.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsw)  
  
int main()  
{  
    unsigned short s1[10];  
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
    __movsw(s1, s2, 10);  
  
    for (int i = 0; i < 10; i++)  
        printf_s("%d ", s1[i]);  
    printf_s("\n");  
}  
```  
  
```Output  
0 1 2 3 4 5 6 7 8 9   
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)