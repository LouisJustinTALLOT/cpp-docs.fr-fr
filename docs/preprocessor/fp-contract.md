---
description: 'En savoir plus sur : pragma fp_contract'
title: fp_contract, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: cefcf0519f08b3fd68a0f8b464938ea7cdbda6d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261175"
---
# <a name="fp_contract-pragma"></a>fp_contract, pragma

Détermine si la contraction à virgule flottante a lieu. Une contraction à virgule flottante est une instruction, telle que FMA (multicolore-multiplier-Add) qui combine deux opérations à virgule flottante distinctes en une seule instruction. L’utilisation de ces instructions peut affecter la précision en virgule flottante, car au lieu d’effectuer un arrondi après chaque opération, le processeur peut arrondir une seule fois après les deux opérations.

## <a name="syntax"></a>Syntaxe

> **#pragma FP_CONTRACT (** { **on**  |  **off** } **)**

## <a name="remarks"></a>Notes

Par défaut, **fp_contract** est **activé**. Cela indique au compilateur d’utiliser des instructions de contraction à virgule flottante dans la mesure du possible. Affectez la valeur **off** à **fp_contract** pour conserver les instructions à virgule flottante individuelles.

Pour plus d’informations sur le comportement à virgule flottante, consultez [/FP (spécifier le comportement de Floating-Point)](../build/reference/fp-specify-floating-point-behavior.md).

Les autres pragmas à virgule flottante incluent :

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Exemple

Le code généré à partir de cet exemple n’utilise pas d’instruction de multiplication par fusion et d’ajout, même lorsqu’il est disponible sur le processeur cible. Si vous supprimez `#pragma fp_contract (off)` les commentaires, le code généré peut utiliser une instruction-multiplier-ajouter fusionnée s’il est disponible.

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
