---
title: intrinsic, pragma
description: Le pragma Intrinsic MSVC est utilisé pour spécifier les fonctions intrinsèques prises en charge à utiliser comme intrinsèques.
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 45a5a13f3bda3657b93e1a89e7a842a4465b01d5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041105"
---
# <a name="intrinsic-pragma"></a>`intrinsic` pragma

Spécifie que les appels aux fonctions spécifiées dans la liste d'arguments du pragma sont intrinsèques.

## <a name="syntax"></a>Syntaxe

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>Remarques

Le **`intrinsic`** pragma indique au compilateur qu’une fonction a un comportement connu. Le compilateur peut appeler cette fonction sans remplacer l'appel de fonction par des instructions inline, si cela entraîne de meilleures performances.

Les fonctions de bibliothèque avec des formes intrinsèques sont répertoriées ci-dessous. Une fois qu’un **`intrinsic`** pragma est visible, il prend effet à la première définition de fonction contenant une fonction intrinsèque spécifiée. L’effet se poursuit jusqu’à la fin du fichier source ou à l’apparence d’un `function` pragma qui spécifie la même fonction intrinsèque. Le **`intrinsic`** pragma peut être utilisé uniquement en dehors d’une définition de fonction, au niveau global.

Les fonctions suivantes ont des formes intrinsèques, et les formulaires intrinsèques sont utilisés lorsque vous spécifiez [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) :

:::row:::
   :::column span="":::
      [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_disable`](../intrinsics/disable.md)\
      [`_enable`](../intrinsics/enable.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_inp`](../c-runtime-library/inp-inpw-inpd.md)\
      [`_inpw`](../c-runtime-library/inp-inpw-inpd.md)\
   :::column-end:::
   :::column span="":::
      [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md)\
      [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md)\
   :::column-end:::
   :::column span="":::
      [`memset`](../c-runtime-library/reference/memset-wmemset.md)\
      [`_outp`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_outpw`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
      [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
   :::column-end:::
   :::column span="":::
      [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md)\
      [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)\
      [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)\
      [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
      [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)\
   :::column-end:::
:::row-end:::

Les programmes qui utilisent des fonctions intrinsèques sont plus rapides, car ils n’ont pas la surcharge des appels de fonction. Toutefois, ils peuvent être plus volumineux en raison du code supplémentaire généré.

### <a name="x86-specific-example"></a>exemple spécifique à x86

Les `_disable` `_enable` intrinsèques et génèrent des instructions en mode noyau pour désactiver ou activer les interruptions, et peuvent être utiles dans les pilotes en mode noyau.

Compilez le code suivant à partir de la ligne de commande avec `cl -c -FAs sample.c` et examinez *`sample.asm`* -le pour qu’il se transforme en instructions x86 CLI et STI :

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>Fonctions à virgule flottante intrinsèques

Ces fonctions à virgule flottante n’ont pas de véritables formes intrinsèques. Au lieu de cela, elles ont des versions qui passent directement des arguments au processeur à virgule flottante, plutôt que de les pousser sur la pile :

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
   :::column-end:::
   :::column span="":::
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
   :::column-end:::
   :::column span="":::
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
   :::column-end:::
   :::column span="":::
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)\
   :::column-end:::
:::row-end:::

Ces fonctions à virgule flottante ont des véritables formes intrinsèques lorsque vous spécifiez [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) et [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (ou toute autre option qui comprend **`/Oi`** : [`/Ox`](../build/reference/ox-full-optimization.md) , [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) et [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ) :

:::row:::
   :::column span="":::
      [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
   :::column-end:::
   :::column span="":::
      [`exp`](../c-runtime-library/reference/exp-expf.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
   :::column-end:::
   :::column span="":::
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
   :::column-end:::
   :::column span="":::
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
   :::column-end:::
:::row-end:::

Vous pouvez utiliser [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) ou [`/Za`](../build/reference/za-ze-disable-language-extensions.md) pour remplacer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.

[`#pragma function`](../preprocessor/function-c-cpp.md)Pour plus d’informations et pour obtenir un exemple d’activation et de désactivation d’intrinsèques pour un bloc de texte source, consultez.

## <a name="see-also"></a>Voir aussi

[Directives pragma et `__pragma` mot clé](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
