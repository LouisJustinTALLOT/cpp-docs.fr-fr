---
title: float_control, pragma
description: Décrit l’utilisation et les effets de la directive float_control pragma. La directive float_control contrôle l’état de la sémantique et de la sémantique d’exception précises à virgule flottante au moment de l’exécution.
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 5f907bfeb3f92f788fe951854ddc32accc83ae03
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166782"
---
# <a name="float_control-pragma"></a>float_control, pragma

Spécifie le comportement de virgule flottante d'une fonction.

## <a name="syntax"></a>Syntaxe

> **#pragma float_control**\
> **#pragma float_control (precise,** { **on** | **off** } [ **, push** ] **)** \
> **#pragma float_control (sauf,** { **on** | **off** } [ **, push** ] **)** \
> **#pragma float_control (** { **Push** | **pop** } **)**

## <a name="options"></a>Options

**precise**, **on** | **off**, **Push**\
Spécifie si la sémantique à virgule flottante exacte doit être activée (**on**) ou désactivée (**off**). Pour plus d’informations sur les différences avec l’option de compilateur **/FP : precise** , consultez la section Notes. Le jeton **Push** facultatif exécute un push du paramètre actuel pour **float_control** sur la pile interne du compilateur.

**à l’exception** **de** | **off**, **Envoyer**\
Spécifie si la sémantique d’exceptions de virgule flottante doit être activée (**on**) ou désactivée (**off**). Le jeton **Push** facultatif exécute un push du paramètre actuel pour **float_control** sur la pile interne du compilateur.

**except** ne peut avoir la valeur **on** que si **precise** a également la valeur **on**.

\ **Push**
Exécute un push du paramètre de **float_control** actuel sur la pile interne du compilateur.

\ **pop**
Supprime le paramètre de **float_control** du haut de la pile interne du compilateur et définit le nouveau paramètre de **float_control** .

## <a name="remarks"></a>Notes

Le pragma **float_control** n’a pas le même comportement que l’option de compilateur [/FP](../build/reference/fp-specify-floating-point-behavior.md) . Le pragma **float_control** régit uniquement une partie du comportement à virgule flottante. Elle doit être associée à [fp_contract](../preprocessor/fp-contract.md) et [fenv_access](../preprocessor/fenv-access.md) des pragmas pour recréer les options du compilateur **/FP** . Le tableau suivant présente les paramètres de pragma équivalents pour chaque option du compilateur :

| | float_control (précis, \*) | float_control (sauf, \*) | fp_contract (\*) | fenv_access (\*) |
|-|-|-|-|-|
| /FP : strict             | sur  | sur  | arrêt | sur  |
| /FP : precise            | sur  | arrêt | sur  | arrêt |
| /FP : Fast               | arrêt | arrêt | sur  | arrêt |

En d’autres termes, vous devrez peut-être utiliser plusieurs pragmas en association pour émuler les options de ligne de commande **/FP : Fast**, **/FP : precise**et **/FP : strict** .

Il existe des restrictions quant à la façon dont vous pouvez utiliser les **float_control** et **fenv_access** les pragmas à virgule flottante en combinaison :

- Vous pouvez uniquement utiliser **float_control** pour définir **sauf** si **la** sémantique précise est activée. Une sémantique précise peut être activée par le pragma **float_control** , ou à l’aide des options de compilateur **/FP : precise** ou **/FP : strict** .

- Vous ne pouvez pas utiliser **float_control** pour désactiver la **précision** lorsque la sémantique d’exception est activée, qu’il s’agisse d’un pragma **float_control** ou d’une option de compilateur **/FP : except** .

- Vous ne pouvez pas activer **fenv_access** à moins que la sémantique précise soit activée, qu’il s’agisse d’un pragma **float_control** ou d’une option du compilateur.

- Vous ne pouvez pas utiliser **float_control** pour désactiver la **précision** lorsque **fenv_access** est activé.

Ces restrictions signifient que l’ordre de certains pragmas à virgule flottante est significatif. Pour passer d’un modèle rapide à un modèle strict à l’aide de pragmas, utilisez le code suivant :

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

Pour passer d’un modèle strict à un modèle rapide à l’aide du pragma **float_control** , utilisez le code suivant :

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

Si aucune option n’est spécifiée, **float_control** n’a aucun effet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment intercepter une exception à virgule flottante de dépassement de capacité à l’aide du pragma **float_control**.

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

[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
