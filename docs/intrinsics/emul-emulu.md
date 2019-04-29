---
title: __emul, __emulu
ms.date: 11/04/2016
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 8657c0fb034ac6bbcfbebb946e059ad08d9e7046
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264047"
---
# <a name="emul-emulu"></a>__emul, __emulu

**Section spécifique à Microsoft**

Effectue des multiplications dépassant ce qui peut contenir un entier 32 bits.

## <a name="syntax"></a>Syntaxe

```
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

#### <a name="parameters"></a>Paramètres

*a*<br/>
[in] Le premier opérande entier de la multiplication.

*b*<br/>
[in] Le second opérande entier de la multiplication.

## <a name="return-value"></a>Valeur de retour

Le résultat de la multiplication.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

`__emul` accepte deux valeurs de 32 bits signés et retourne le résultat de la multiplication comme une valeur entière signée 64 bits.

`__emulu` accepte deux valeurs d’entier non signé 32 bits et retourne le résultat de la multiplication comme valeur de l’entier non signé 64 bits.

## <a name="example"></a>Exemple

```
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

```
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)