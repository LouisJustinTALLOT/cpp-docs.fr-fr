---
title: fenv_access (pragma)
description: Décrit l’utilisation et les effets de la directive fenv_access pragma. La directive fenv_access contrôle l’accès à l’environnement à virgule flottante au moment de l’exécution.
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305855"
---
# <a name="fenv_access-pragma"></a>fenv_access (pragma)

Désactive (activé) ou active (**off**) les optimisations qui peuvent modifier les tests d’indicateur**d'** environnement à virgule flottante et les modifications de mode.

## <a name="syntax"></a>Syntaxe

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Notes

Par défaut, **fenv_access** est **désactivé**. Le compilateur suppose que votre code n’accède pas ou ne manipule pas l’environnement à virgule flottante. Si l’accès à l’environnement n’est pas requis, le compilateur peut en faire plus pour optimiser votre code à virgule flottante.

Activez **fenv_access** si votre code teste des indicateurs d’État à virgule flottante, des exceptions ou définit des indicateurs de mode de contrôle. Le compilateur désactive les optimisations à virgule flottante, de sorte que votre code peut accéder de façon cohérente à l’environnement à virgule flottante.

L’option de ligne de commande [/FP : strict] active automatiquement **fenv_access**. Pour plus d’informations sur ce comportement et d’autres comportements à virgule flottante, consultez [/FP (spécifier le comportement à virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md).

Il existe des restrictions sur la façon dont vous pouvez utiliser le pragma **fenv_access** en combinaison avec d’autres paramètres à virgule flottante :

- Vous ne pouvez pas activer **fenv_access** , sauf si la sémantique précise est activée. Une sémantique précise peut être activée par le pragma [float_control](float-control.md) , ou à l’aide des options de compilateur [/FP : precise](../build/reference/fp-specify-floating-point-behavior.md) ou [/FP : strict](../build/reference/fp-specify-floating-point-behavior.md) . Par défaut, le compilateur a la valeur **/FP : precise** si aucune autre option de ligne de commande à virgule flottante n’est spécifiée.

- Vous ne pouvez pas utiliser **float_control** pour désactiver la sémantique précise lorsque **fenv_access (on)** est défini.

Les types d’optimisations qui sont soumis à des **fenv_access** sont les suivants :

- Élimination globale de sous-expressions communes

- Déplacement de code

- Pliage constant

Les autres pragmas à virgule flottante incluent :

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Exemples

Cet exemple affecte à **fenv_access** la valeur **on** pour définir le registre de contrôle à virgule flottante pour une précision de 24 bits :

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

Si vous mettez en commentaire `#pragma fenv_access (on)` de l’exemple précédent, la sortie est différente. Cela est dû au fait que le compilateur effectue une évaluation au moment de la compilation, qui n’utilise pas le mode de contrôle.

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

[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
