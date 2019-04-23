---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 8a7829252cebb726363c67c990a94d08b0d6467a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032308"
---
# <a name="floatcontrol"></a>float_control

Spécifie le comportement de virgule flottante d'une fonction.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control** [ **(** [ *value* **,** *setting* [ **, push** ] ] | [ **push** | **pop** ] **)** ]

## <a name="options"></a>Options

*value*, *setting* [, **push**]<br/>
Spécifie le comportement de virgule flottante. *valeur* peut être **précise**, **strict**, ou **sauf**. Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md). Le *paramètre* peut être **sur** ou **hors**.

Si *valeur* est **strict**, les paramètres des options **strict** et **sauf** sont spécifiées par *paramètre* . **à l’exception** peut uniquement être définie sur **sur** lorsque **précise** ou **strict** est également défini sur **sur**.

Si le paramètre facultatif **push** jeton est ajouté, actuel définissant pour *valeur* est envoyée sur à la pile interne du compilateur.

**push**<br/>
Exécute un push du **float_control** définition sur la pile interne du compilateur

**pop**<br/>
Supprime le **float_control** définition à partir du haut de la pile interne du compilateur et qui rend la nouvelle **float_control** paramètre.

## <a name="remarks"></a>Notes

Vous ne pouvez pas utiliser **float_control** pour activer **précise** désactivé lorsque **sauf** se trouve sur. De même, **précise** ne peut pas être mis hors tension lorsque [fenv_access](../preprocessor/fenv-access.md) se trouve sur. Pour passer d’un modèle strict à un modèle rapide à l’aide de la **float_control** pragma, utilisez le code suivant :

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Pour passer d’un modèle rapide à un modèle strict avec le **float_control** pragma, utilisez le code suivant :

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Si aucune option est spécifiée, **float_control** n’a aucun effet.

Les autres pragmas à virgule flottante incluent :

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment intercepter une exception de virgule flottante de dépassement de capacité en utilisant le pragma **float_control**.

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

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
