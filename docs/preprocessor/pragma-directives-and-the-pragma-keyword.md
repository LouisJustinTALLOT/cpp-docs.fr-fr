---
title: Directives Pragma et mot clé __pragma
ms.date: 08/29/2019
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
ms.openlocfilehash: 786f76d9f7fd2eee73c6b1d009186bf93ea0c667
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842687"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Directives Pragma et mot clé __pragma

Les directives pragma spécifient des fonctionnalités de compilateur spécifiques à l’ordinateur ou au système d’exploitation. Le mot clé **__Pragma** , qui est spécifique au compilateur Microsoft, vous permet de coder des directives pragma dans les définitions de macros.

## <a name="syntax"></a>Syntaxe

> **#pragma** *chaîne de jeton de* #pragma\
> **__Pragma (** *chaîne de jeton* **)**

## <a name="remarks"></a>Notes

Chaque implémentation de C et C++ prend en charge des fonctionnalités spécifiques de son ordinateur hôte ou de son système d’exploitation. Certains programmes, par exemple, doivent exercer un contrôle précis sur l’emplacement des données en mémoire ou contrôler la façon dont certaines fonctions reçoivent des paramètres. Les directives **#pragma** permettent à chaque compilateur d’offrir des fonctionnalités propres aux ordinateurs et aux systèmes d’exploitation, tout en conservant la compatibilité générale avec les langages C et C++.

Les pragmas sont spécifiques à l’ordinateur ou au système d’exploitation par définition, et sont généralement différents pour chaque compilateur. Les pragmas peuvent être utilisés dans les directives conditionnelles pour fournir de nouvelles fonctionnalités de préprocesseur ou pour fournir des informations définies par l’implémentation au compilateur.

La *chaîne de jeton* est une série de caractères qui donne une instruction et des arguments spécifiques du compilateur, le cas échéant. Le signe dièse ( **#** ) doit être le premier caractère autre qu’un espace blanc sur la ligne qui contient le pragma. Les espaces blancs peuvent séparer le signe dièse et le mot « pragma ». Après **#pragma**, écrivez le texte que le traducteur peut analyser en tant que jetons de prétraitement. L’argument pour **#pragma** est soumis à une expansion macro.

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

Le compilateur prend également en charge le mot clé **__Pragma** spécifique à Microsoft, qui a les mêmes fonctionnalités que la directive **#pragma** . La différence est que le mot clé **__Pragma** est utilisable inline dans une définition de macro. La directive **#pragma** n’est pas utilisable dans une définition de macro, car le compilateur interprète le signe dièse (#) dans la directive comme opérateur de [chaîne (#)](../preprocessor/stringizing-operator-hash.md).

L’exemple de code suivant montre comment le mot clé **__Pragma** peut être utilisé dans une macro. Ce code est extrait de l'en-tête mfcdual.h de l'exemple CDUAL dans « Exemples de prise en charge COM du compilateur » :

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

## <a name="see-also"></a>Voir aussi

[Référence du préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Pragmas C](../c-language/c-pragmas.md)\
[Mots clés](../cpp/keywords-cpp.md)
