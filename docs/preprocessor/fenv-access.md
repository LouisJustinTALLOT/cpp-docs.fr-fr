---
title: fenv_access
ms.date: 03/12/2018
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: 507e78dd9f9571cc9ce44d7fd91e78b1c955ba73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664033"
---
# <a name="fenvaccess"></a>fenv_access
Désactive (**sur**) ou active (**hors**) optimisations qui peuvent modifier l’environnement à virgule flottante signaler des tests et les changements de mode.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **sur** | **hors** } **)**

## <a name="remarks"></a>Notes

Par défaut, **fenv_access** est **hors**. Si le compilateur peut supposer que votre code ne pas accéder à ou manipuler l’environnement à virgule flottante, il peut effectuer de nombreuses optimisations de code en virgule flottante. Définissez **fenv_access** à **sur** pour informer le compilateur que votre code accède à l’environnement à virgule flottante pour tester les indicateurs d’état, exceptions, ou pour définir des indicateurs de mode de contrôle. Le compilateur désactive ces optimisations afin que votre code peut accéder à l’environnement à virgule flottante régulièrement.

Pour plus d’informations sur le comportement de virgule flottante, consultez [/fp (spécifier le comportement de virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Les types d’optimisations qui sont soumis aux **fenv_access** sont :

- Élimination globale de sous-expressions communes

- Déplacement de code

- Repli constant

Les autres pragmas à virgule flottante incluent :

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Exemples

Cet exemple définit **fenv_access** à **sur** pour définir le Registre de contrôle à virgule flottante de précision de 24 bits :

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

Si vous commentez `#pragma fenv_access (on)` à partir de l’exemple précédent, notez que la sortie est différente, car le compilateur effectue l’évaluation au moment de la compilation, qui n’utilise pas le mode de contrôle.

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
