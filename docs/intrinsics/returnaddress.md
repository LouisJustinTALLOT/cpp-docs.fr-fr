---
title: _ReturnAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ReturnAddress
dev_langs: C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d207fcba6846d0a5e599d6273f5b35bb554bda40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Le `_ReturnAddress` intrinsèque fournit l’adresse de l’instruction dans la fonction appelante qui sera exécutée une fois que le contrôle retourne à l’appelant.  
  
 Générez le programme suivant et les exécuter pas à pas dans le débogueur. À mesure que vous parcourez le programme, notez l’adresse qui est retourné à partir de `_ReturnAddress`. Puis, immédiatement après le retour de la fonction où `_ReturnAddress` a été utilisé, ouvrez le [Comment : utiliser la fenêtre code machine](/visualstudio/debugger/how-to-use-the-disassembly-window) et notez que l’adresse de l’instruction suivante à exécuter correspond à l’adresse retournée par `_ReturnAddress`.  
  
 Optimisations comme l’incorporation (inlining) peut affecter l’adresse de retour. Par exemple, si le programme d’exemple suivant est compilé avec [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` seront incorporées dans la fonction appelante, `main`. Par conséquent, les appels à `_ReturnAddress` de `inline_func` et `main` chaque produit la même valeur.  
  
 Lorsque `_ReturnAddress` est utilisée dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction contenant le `_ReturnAddress` appel sera compilé dans une fonction native. Lorsqu’une fonction compilée comme géré appelle la fonction contenant `_ReturnAddress`, `_ReturnAddress` peut ne pas fonctionner comme prévu.  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="example"></a>Exemple  
  
```  
// compiler_intrinsics__ReturnAddress.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_ReturnAddress)  
  
__declspec(noinline)  
void noinline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
__forceinline  
void inline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
int main(void)  
{  
   noinline_func();   
   inline_func();  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
  
   return 0;  
}  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Mots clés](../cpp/keywords-cpp.md)