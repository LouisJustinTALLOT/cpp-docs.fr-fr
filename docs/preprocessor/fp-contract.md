---
title: fp_contract
ms.date: 03/12/2018
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 14c3ac60d4fc0f45fcf0ece6c3f73153e5de4271
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476503"
---
# <a name="fpcontract"></a>fp_contract

Détermine si une contraction à virgule flottante a lieu. Une contraction à virgule flottante est une instruction comme FMA (fondus-multiplication / addition) qui combine deux opérations à virgule flottante distincts dans une seule instruction. Utilisation de ces instructions peut affecter la précision à virgule flottante, car au lieu de l’arrondi après chaque opération, le processeur peut arrondir qu’une seule fois après les deux opérations.

## <a name="syntax"></a>Syntaxe

> **#pragma fp_contract (** { **sur** | **hors** } **)**

## <a name="remarks"></a>Notes

Par défaut, **fp_contract** est **sur**. Cela indique au compilateur d’utiliser les instructions de la contraction à virgule flottante lorsque cela est possible. Définissez **fp_contract** à **hors** pour conserver les instructions à virgule flottante individuelles.

Pour plus d’informations sur le comportement de virgule flottante, consultez [/fp (spécifier le comportement de virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Les autres pragmas à virgule flottante incluent :

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Exemple

Le code généré à partir de cet exemple n’utilise pas une instruction fusionnés-multiplication / addition même lorsqu’il est disponible sur le processeur cible. Si vous commentez `#pragma fp_contract (off)`, le code généré peut utiliser une instruction fusionnés-multiplication / addition s’il est disponible.

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
