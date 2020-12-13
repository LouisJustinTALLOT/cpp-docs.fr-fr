---
description: 'En savoir plus sur : _ReturnAddress'
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: abb6b879c466372fce0ecbeb7371101e3a3ef82b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143739"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Spécifique à Microsoft**

L' `_ReturnAddress` intrinsèque fournit l’adresse de l’instruction dans la fonction appelante qui est exécutée une fois que le contrôle est retourné à l’appelant.

Générez le programme suivant et parcourez-le dans le débogueur. Au fur et à mesure que vous parcourez le programme, notez l’adresse qui est retournée à partir de `_ReturnAddress` . Ensuite, juste après le retour de la fonction où `_ReturnAddress` a été utilisé, ouvrez la [fenêtre Comment : utiliser le code machine](/visualstudio/debugger/how-to-use-the-disassembly-window) et notez que l’adresse de l’instruction suivante à exécuter correspond à l’adresse retournée à partir de `_ReturnAddress` .

Les optimisations telles que l’incorporation peuvent affecter l’adresse de retour. Par exemple, si l’exemple de programme ci-dessous est compilé avec [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` sera incorporé dans la fonction appelante, `main` . Par conséquent, les appels à `_ReturnAddress` from `inline_func` et `main` s’effectuent chacun avec la même valeur.

Quand `_ReturnAddress` est utilisé dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction qui contient l' `_ReturnAddress` appel sera compilée en tant que fonction native. Lorsqu’une fonction compilée en tant qu’appels managés dans la fonction contenant `_ReturnAddress` , `_ReturnAddress` peut ne pas se comporter comme prévu.

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<intrin.h>

## <a name="example"></a>Exemple

```cpp
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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
