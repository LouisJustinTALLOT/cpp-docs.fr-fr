---
title: float_control, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218579"
---
# <a name="float_control-pragma"></a>float_control, pragma

Spécifie le comportement de virgule flottante d'une fonction.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control**\
> **#pragma float_control (** { **precise** |  |  Except}, {on off} [, Push]) | \
> **#pragma float_control (** { **Push** | **pop** } **)**

## <a name="options"></a>Options

**strict strict** **except:** OFF, push |  |  | \
Spécifie le comportement à virgule flottante, qui peut être **précis**, **strict**ou **except**. Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md). Le paramètre peut être **activé** ou **désactivé**.

Lorsque la valeur est **strict**, les paramètres de **strict** et **except** sont spécifiés par le paramètre **on** ou **off** . **except** ne peut avoir la valeur **on** que si precise ou **strict** est également défini sur **on**.

Si le jeton **Push** facultatif est ajouté, le paramètre actuel pour **float_control** fait l’objet d’un push sur la pile interne du compilateur.

**souleve**\
Exécute un push du paramètre **float_control** actuel sur la pile interne du compilateur

**roulant**\
Supprime le paramètre **float_control** du haut de la pile interne du compilateur et en fait le nouveau paramètre **float_control** .

## <a name="remarks"></a>Notes

Vous ne pouvez pas utiliser **float_control** pour désactiver la **précision** lorsque **except** est activé. De même, la **précision** ne peut pas être désactivée lorsque [fenv_access](../preprocessor/fenv-access.md) est activé. Pour passer du modèle strict à un modèle rapide à l’aide du pragma **float_control** , utilisez le code suivant:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Pour passer du modèle Fast à un modèle strict avec le pragma **float_control** , utilisez le code suivant:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Si aucune option n’est spécifiée, **float_control** n’a aucun effet.

Les autres pragmas à virgule flottante incluent :

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment intercepter une exception à virgule flottante de dépassement de capacité à l’aide de pragma **float_control**.

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
