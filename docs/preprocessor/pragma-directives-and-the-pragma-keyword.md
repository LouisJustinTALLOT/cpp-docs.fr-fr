---
title: Directives Pragma et mot clé __pragma
description: Décrit les directives pragma disponibles dans Microsoft Visual C et C++ (MSVC)
ms.date: 10/30/2020
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 784cd413b6b81033c9e49b22d979ece72e5ee101
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381543"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Directives Pragma et mot clé __pragma

Les directives pragma spécifient des fonctionnalités de compilateur spécifiques à l’ordinateur ou au système d’exploitation. Le mot clé **__Pragma** , qui est spécifique au compilateur Microsoft, vous permet de coder des directives pragma dans les définitions de macros.

## <a name="syntax"></a>Syntaxe

> **#`pragma`***jeton-chaîne*\
> **`__pragma(`***jeton-chaîne* **`)`** deux traits de soulignement de début : **`_Pragma(`** *chaîne littérale* d’extension spécifique à Microsoft **`)`** //C99

## <a name="remarks"></a>Remarques

Chaque implémentation de C et C++ prend en charge des fonctionnalités spécifiques de son ordinateur hôte ou de son système d’exploitation. Certains programmes, par exemple, doivent exercer un contrôle précis sur l’emplacement des données en mémoire ou contrôler la façon dont certaines fonctions reçoivent des paramètres. Les directives **#pragma** permettent à chaque compilateur d’offrir des fonctionnalités propres aux ordinateurs et aux systèmes d’exploitation, tout en conservant la compatibilité générale avec les langages C et C++.

Les pragmas sont spécifiques à l’ordinateur ou au système d’exploitation par définition, et sont généralement différents pour chaque compilateur. Les pragmas peuvent être utilisés dans les directives conditionnelles pour fournir de nouvelles fonctionnalités de préprocesseur ou pour fournir des informations définies par l’implémentation au compilateur.

La *chaîne de jeton* est une série de caractères représentant une instruction et des arguments spécifiques du compilateur, le cas échéant. Le signe dièse ( **#** ) doit être le premier caractère autre qu’un espace blanc sur la ligne qui contient le pragma. Les espaces blancs peuvent séparer le signe dièse et le mot « pragma ». Après **#pragma** , écrivez le texte que le traducteur peut analyser en tant que jetons de prétraitement. L’argument pour **#pragma** est soumis à une expansion macro.

Le *littéral de chaîne* est l’entrée de `_Pragma` . Les guillemets externes et les espaces de début/de fin sont supprimés. `\"` est remplacé par `"` et `\\` est remplacé par `\` .

Le compilateur émet un avertissement lorsqu’il trouve un pragma qu’il ne reconnaît pas, et poursuit la compilation.

Les compilateurs Microsoft C et C++ reconnaissent les pragmas suivants :

:::row:::
   :::column span="":::
      [`alloc_text`](../preprocessor/alloc-text.md)\
      [`auto_inline`](../preprocessor/auto-inline.md)\
      [`bss_seg`](../preprocessor/bss-seg.md)\
      [`check_stack`](../preprocessor/check-stack.md)\
      [`code_seg`](../preprocessor/code-seg.md)\
      [`comment`](../preprocessor/comment-c-cpp.md)\
      [`component`](../preprocessor/component.md)\
      [`conform`](../preprocessor/conform.md)<sup>1</sup>\
      [`const_seg`](../preprocessor/const-seg.md)\
      [`data_seg`](../preprocessor/data-seg.md)\
      [`deprecated`](../preprocessor/deprecated-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
      [`fenv_access`](../preprocessor/fenv-access.md)\
      [`float_control`](../preprocessor/float-control.md)\
      [`fp_contract`](../preprocessor/fp-contract.md)\
      [`function`](../preprocessor/function-c-cpp.md)\
      [`hdrstop`](../preprocessor/hdrstop.md)\
      [`include_alias`](../preprocessor/include-alias.md)\
      [`init_seg`](../preprocessor/init-seg.md)<sup>1</sup>\
      [`inline_depth`](../preprocessor/inline-depth.md)\
      [`inline_recursion`](../preprocessor/inline-recursion.md)
   :::column-end:::
   :::column span="":::
      [`intrinsic`](../preprocessor/intrinsic.md)\
      [`loop`](../preprocessor/loop.md)<sup>1</sup>\
      [`make_public`](../preprocessor/make-public.md)\
      [`managed`](../preprocessor/managed-unmanaged.md)\
      [`message`](../preprocessor/message.md)\
      [`omp`](../preprocessor/omp.md)\
      [`once`](../preprocessor/once.md)\
      [`optimize`](../preprocessor/optimize.md)\
      [`pack`](../preprocessor/pack.md)\
      [`pointers_to_members`](../preprocessor/pointers-to-members.md)<sup>1</sup>
   :::column-end:::
   :::column span="":::
      [`pop_macro`](../preprocessor/pop-macro.md)\
      [`push_macro`](../preprocessor/push-macro.md)\
      [`region`, endregion](../preprocessor/region-endregion.md)\
      [`runtime_checks`](../preprocessor/runtime-checks.md)\
      [`section`](../preprocessor/section.md)\
      [`setlocale`](../preprocessor/setlocale.md)\
      [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
      [`unmanaged`](../preprocessor/managed-unmanaged.md)\
      [`vtordisp`](../preprocessor/vtordisp.md)<sup>1</sup>\
      [`warning`](../preprocessor/warning.md)
   :::column-end:::
:::row-end:::

<sup>1</sup> pris en charge uniquement par le compilateur C++.

## <a name="pragmas-and-compiler-options"></a>Pragmas et options du compilateur

Certains pragmas fournissent les mêmes fonctionnalités que les options du compilateur. Lorsqu'un pragma est rencontré dans le code source, il remplace le comportement spécifié par l'option du compilateur. Par exemple, si vous avez spécifié [/Zp8](../build/reference/zp-struct-member-alignment.md), vous pouvez remplacer ce paramètre de compilateur pour des sections spécifiques du code avec [Pack](../preprocessor/pack.md):

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>Mot clé __pragma ()

Le compilateur prend également en charge le mot clé propre à Microsoft **`__pragma`** , qui a les mêmes fonctionnalités que la **`#pragma`** directive. La différence est que le **`__pragma`** mot clé est utilisable inline dans une définition de macro. La **`#pragma`** directive n’est pas utilisable dans une définition de macro, car le compilateur interprète le signe dièse (#) dans la directive comme opérateur de [chaîne (#)](../preprocessor/stringizing-operator-hash.md).

L’exemple de code suivant montre comment le **`__pragma`** mot clé peut être utilisé dans une macro. Ce code est extrait de l’en-tête *mfcdual. h* de l’exemple ACDual dans « exemples de prise en charge com du compilateur » :

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

## <a name="the-_pragma-preprocessing-operator-c99-c11"></a>`_Pragma`Opérateur de prétraitement (C99, c++ 11)

`_Pragma` est semblable au mot clé spécifique à Microsoft [`__pragma`](#the-__pragma-keyword) , sauf qu’il fait partie de la norme. Il a été introduit pour C dans C99. Pour C++, elle a été introduite dans C++ 11.

 Elle vous permet de placer des pragmas dans une définition de macro. Il a un trait de soulignement `_` de début au lieu de deux traits de soulignement de début `__` qui ont le mot clé propre à Microsoft, et la première lettre est en majuscule.

Le littéral de chaîne doit correspondre à ce que vous placeriez après une *`#pragma`* instruction. Par exemple :

```c
#pragma message("the #pragma way")
_Pragma ("message( \"the _Pragma way\")") 
```

Les guillemets et les barres obliques inverses doivent être placés dans une séquence d’échappement, comme illustré ci-dessus. Une chaîne pragma qui n’est pas reconnue est ignorée.

L’exemple de code suivant montre comment le **`_Pragma`** mot clé peut être utilisé dans une macro de type assertion lorsque vous ne souhaitez pas obtenir d’avertissement lorsque l’expression de condition devient constante. 

La définition de macro utilise l’idiome do/while (0) pour les macros à instructions multiples afin qu’il puisse être utilisé comme s’il s’agissait d’une seule instruction. Pour plus d’informations, consultez [macro multiligne C](https://stackoverflow.com/questions/1067226/c-multi-line-macro-do-while0-vs-scope-block) sur Stack overflow. L’instruction _Pragma s’applique uniquement à la ligne de code qui la suit.

```C
// Compile with /W4

#include <stdio.h>
#include <stdlib.h>

#define MY_ASSERT(BOOL_EXPRESSION) \
    do { \
        _Pragma("warning(suppress: 4127)") /* C4127 conditional expression is constant */  \
        if (!(BOOL_EXPRESSION)) {   \
            printf("MY_ASSERT FAILED: \"" #BOOL_EXPRESSION "\" on %s(%d)", __FILE__, __LINE__); \
            exit(-1); \
        } \
    } while (0)

int main()
{
    MY_ASSERT(0 && "Note that there is no warning: C4127 conditional expression is constant");

    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Référence du préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Pragmas C](../c-language/c-pragmas.md)\
[Mots clés](../cpp/keywords-cpp.md)
