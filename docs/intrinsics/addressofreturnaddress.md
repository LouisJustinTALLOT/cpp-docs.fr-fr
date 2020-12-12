---
description: 'En savoir plus sur : _AddressOfReturnAddress'
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 1a79ccbe7ddc2865d8225a62cd0d294f0bc66b4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331921"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Spécifique à Microsoft**

Fournit l’adresse de l’emplacement de mémoire qui contient l’adresse de retour de la fonction active. Cette adresse ne peut pas être utilisée pour accéder à d’autres emplacements de mémoire (par exemple, les arguments de la fonction).

## <a name="syntax"></a>Syntaxe

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64, ARM, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Quand `_AddressOfReturnAddress` est utilisé dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction qui contient l' `_AddressOfReturnAddress` appel est compilée comme une fonction native. Lorsqu’une fonction compilée en tant qu’appels managés dans la fonction contenant `_AddressOfReturnAddress` , `_AddressOfReturnAddress` peut ne pas se comporter comme prévu.

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
