---
title: _ReturnAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c739590e5e208d9f83fa059f191ae80612a0dbd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380868"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Le `_ReturnAddress` intrinsèque fournit l’adresse de l’instruction dans la fonction appelante qui sera exécutée après le contrôle retourne à l’appelant.

Générer le programme et pas à pas dans le débogueur suivants. À mesure que vous parcourez le programme, notez l’adresse qui est retourné à partir de `_ReturnAddress`. Puis, immédiatement après le retour de la fonction où `_ReturnAddress` a été utilisé, ouvrez le [Comment : utiliser la fenêtre code machine](/visualstudio/debugger/how-to-use-the-disassembly-window) et notez que l’adresse de l’instruction suivante à exécuter correspond à l’adresse retournée par `_ReturnAddress`.

Les optimisations telles que mai incorporation (inlining) affecte l’adresse de retour. Par exemple, si le programme d’exemple ci-dessous est compilé avec [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` seront incorporées dans la fonction appelante, `main`. Par conséquent, les appels à `_ReturnAddress` de `inline_func` et `main` chacun génère la même valeur.

Lorsque `_ReturnAddress` est utilisée dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction contenant le `_ReturnAddress` appel est compilé comme une fonction native. Quand une fonction compilée comme géré appelle la fonction contenant `_ReturnAddress`, `_ReturnAddress` peuvent ne pas fonctionner comme prévu.

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

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)