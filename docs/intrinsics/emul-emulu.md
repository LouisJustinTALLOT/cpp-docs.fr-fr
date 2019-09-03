---
title: __emul, __emulu
ms.date: 09/02/2019
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 16b2b38f6f44b99c9f5b9370ba586342a860684e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216744"
---
# <a name="__emul-__emulu"></a>__emul, __emulu

**Section spécifique à Microsoft**

Effectue des multiplications qui dépassent ce qu’un entier 32 bits peut contenir.

## <a name="syntax"></a>Syntaxe

```C
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

### <a name="parameters"></a>Paramètres

*un*\
dans Premier opérande entier de la multiplication.

*p*\
dans Deuxième opérande entier de la multiplication.

## <a name="return-value"></a>Valeur de retour

Résultat de la multiplication.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

`__emul`prend des valeurs signées 2 32 bits et retourne le résultat de la multiplication sous la forme d’une valeur entière signée 64 bits.

`__emulu`prend des valeurs entières non signées 2 32 bits et retourne le résultat de la multiplication sous la forme d’une valeur entière non signée 64 bits.

## <a name="example"></a>Exemple

```cpp
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Sortie

```Output
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
