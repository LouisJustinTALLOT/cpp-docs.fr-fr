---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221076"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Section spécifique à Microsoft**

Fournit l’adresse de l’emplacement de mémoire qui contient l’adresse de retour de la fonction active. Cette adresse ne peut pas être utilisée pour accéder à d’autres emplacements de mémoire (par exemple, les arguments de la fonction).

## <a name="syntax"></a>Syntaxe

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64, ARM, ARM64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Quand `_AddressOfReturnAddress` est utilisé dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction qui contient `_AddressOfReturnAddress` l’appel est compilée comme une fonction native. Lorsqu’une fonction compilée en tant qu’appels managés `_AddressOfReturnAddress`dans `_AddressOfReturnAddress` la fonction contenant, peut ne pas se comporter comme prévu.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
