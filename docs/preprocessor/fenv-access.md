---
title: fenv_access | Documents Microsoft
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f6f379e61ea84c1142bd94be49b55a50b28753
ms.sourcegitcommit: 1ac8f983eeaacd09135a249dea00f10e1c94e0e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36963321"
---
# <a name="fenvaccess"></a>fenv_access

Désactive (**sur**) ou active (**hors**) optimisations qui peuvent modifier l’environnement à virgule flottante marquer les tests et les changements de mode.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **sur** | **hors** } **)**  

## <a name="remarks"></a>Notes

Par défaut, **fenv_access** est **hors**. Si le compilateur peut supposer que votre code ne pas accéder ou manipuler l’environnement à virgule flottante, puis il peut effectuer de nombreuses optimisations de code à virgule flottante. Définissez **fenv_access** à **sur** pour informer le compilateur que votre code accède à l’environnement à virgule flottante pour tester des indicateurs d’état, des exceptions, ou pour définir des indicateurs de mode de contrôle. Le compilateur désactive ces optimisations afin que votre code peut accéder à l’environnement à virgule flottante régulièrement. 

Pour plus d’informations sur le comportement de virgule flottante, consultez [/fp (spécifier du comportement de nombres à virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Les types d’optimisations qui sont soumises à **fenv_access** sont :

- Élimination globale de sous-expressions communes

- Déplacement de code

- Repli constant

Les autres pragmas à virgule flottante incluent :

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Exemples

Cet exemple définit **fenv_access** à **sur** pour définir le Registre de contrôle à virgule flottante pour la précision de 24 bits :

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-003
```

Si vous commentez `#pragma fenv_access (on)` à partir de l’exemple précédent, notez que la sortie est différente, car le compilateur effectue d’évaluation au moment de la compilation, qui n’utilise pas le mode de contrôle.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-002
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
