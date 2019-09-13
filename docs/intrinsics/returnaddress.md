---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218061"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Section spécifique à Microsoft**

L' `_ReturnAddress` intrinsèque fournit l’adresse de l’instruction dans la fonction appelante qui est exécutée une fois que le contrôle est retourné à l’appelant.

Générez le programme suivant et parcourez-le dans le débogueur. Au fur et à mesure que vous parcourez le programme, notez `_ReturnAddress`l’adresse qui est retournée à partir de. Ensuite, juste après le retour de la fonction `_ReturnAddress` où a été utilisé, [Ouvrez la procédure : Utilisez la fenêtre](/visualstudio/debugger/how-to-use-the-disassembly-window) code machine et notez que l’adresse de l’instruction suivante à exécuter correspond à l’adresse retournée `_ReturnAddress`par.

Les optimisations telles que l’incorporation peuvent affecter l’adresse de retour. Par exemple, si l’exemple de programme ci-dessous est compilé avec [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` sera incorporé dans la fonction appelante, `main`. Par conséquent, les appels `_ReturnAddress` à `inline_func` from `main` et s’effectuent chacun avec la même valeur.

Quand `_ReturnAddress` est utilisé dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction qui contient `_ReturnAddress` l’appel sera compilée en tant que fonction native. Lorsqu’une fonction compilée en tant qu’appels managés `_ReturnAddress`dans `_ReturnAddress` la fonction contenant, peut ne pas se comporter comme prévu.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<> Intro. h

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
