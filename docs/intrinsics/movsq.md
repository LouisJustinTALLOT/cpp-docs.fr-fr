---
title: __movsq | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __movsq
dev_langs:
- C++
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0231c2514805479c0ec999698ebd027ab51e3119
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540020"
---
# <a name="movsq"></a>__movsq
**Section spécifique à Microsoft**  
  
 Génère une chaîne de déplacer répétées (`rep movsq`) instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __movsq(   
   unsigned char* Dest,   
   unsigned char* Source,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [out] `Dest`  
 La destination de l’opération.  
  
 [in] `Source`  
 La source de l’opération.  
  
 [in] `Count`  
 Le nombre de mots quadruples à copier.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__movsq`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le résultat est que la première `Count` mots quadruples vers lequel pointe `Source` sont copiés vers le `Dest` chaîne.  
  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
## <a name="example"></a>Exemple  
  
```  
// movsq.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsq)  
  
int main()  
{  
    unsigned __int64 a1[10];  
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,  
                               150, 50};  
    __movsq(a1, a2, 10);  
  
    for (int i = 0; i < 10; i++)  
       printf_s("%d ", a1[i]);  
    printf_s("\n");  
}  
```  
  
```Output  
950 850 750 650 550 450 350 250 150 50   
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)