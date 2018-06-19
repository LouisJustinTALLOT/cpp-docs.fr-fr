---
title: fp_contract | Documents Microsoft
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 514b4708129d625ea7880e4c61be22c4b1ac2db5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912886"
---
# <a name="fpcontract"></a>fp_contract

Détermine si une contraction à virgule flottante a lieu. Une contraction à virgule flottante est une instruction comme FMA (fondus-multiplication-addition) qui combine deux opérations à virgule flottante distinct dans une même instruction. Utilisation de ces instructions peut affecter la précision en virgule flottante, car au lieu de l’arrondi après chaque opération, le processeur peut arrondir qu’une seule fois après les deux opérations.

## <a name="syntax"></a>Syntaxe

> **#pragma fp_contract (** { **sur** | **hors** } **)**  

## <a name="remarks"></a>Notes  

Par défaut, **fp_contract** est **sur**. Cela indique au compilateur d’utiliser les instructions de la contraction à virgule flottante lorsque cela est possible. Définissez **fp_contract** à **hors** pour conserver des instructions à virgule flottante.

Pour plus d’informations sur le comportement de virgule flottante, consultez [/fp (spécifier du comportement de nombres à virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Les autres pragmas à virgule flottante incluent :

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Exemple

Le code généré à partir de cet exemple n’utilise pas une instruction de fusion-multiplier-ajouter même lorsqu’elle est disponible sur le processeur cible. Si vous commentez `#pragma fp_contract (off)`, le code généré peut utiliser une instruction de fusion-multiplier-ajouter si elle est disponible.  
  
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
