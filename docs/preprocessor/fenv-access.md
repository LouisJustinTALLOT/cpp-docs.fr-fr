---
title: fenv_access, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218603"
---
# <a name="fenv_access-pragma"></a>fenv_access, pragma

Désactive (activé) ou active (**off**) les optimisations qui peuvent modifier les tests d’indicateur**d'** environnement à virgule flottante et les modifications de mode.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Notes

Par défaut, **fenv_access** est **désactivé**. Si le compilateur peut supposer que votre code n’accède pas ou ne manipule pas l’environnement à virgule flottante, il peut effectuer de nombreuses optimisations de code à virgule flottante. Affectez à **fenv_access** la valeur **on** pour indiquer au compilateur que votre code accède à l’environnement à virgule flottante pour tester les indicateurs d’État, les exceptions ou pour définir des indicateurs de mode de contrôle. Le compilateur désactive ces optimisations afin que votre code puisse accéder de façon cohérente à l’environnement à virgule flottante.

Pour plus d’informations sur le comportement de virgule flottante, consultez [/FP (spécifier le comportement à virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Les types d’optimisations qui sont soumis à **fenv_access** sont les suivants:

- Élimination globale de sous-expressions communes

- Déplacement de code

- Pliage constant

Les autres pragmas à virgule flottante incluent :

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Exemples

Cet exemple affecte à **fenv_access** la valeur **on** pour définir le registre de contrôle à virgule flottante pour une précision de 24 bits:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
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
out=9.999999776482582e-03
```

Si vous supprimez `#pragma fenv_access (on)` le commentaire de l’exemple précédent, Notez que la sortie est différente car le compilateur effectue une évaluation au moment de la compilation, qui n’utilise pas le mode de contrôle.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
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
out=1.000000000000000e-02
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
