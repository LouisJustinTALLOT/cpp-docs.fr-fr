---
title: intrinsèque | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c222a939ccb00dc3b7466a1cb1a83abe7ea4036
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540204"
---
# <a name="intrinsic"></a>intrinsic

Spécifie que les appels aux fonctions spécifiées dans la liste d’arguments du pragma sont intrinsèques.

## <a name="syntax"></a>Syntaxe

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>Notes

Le **intrinsèque** pragma indique au compilateur qu’une fonction a un comportement connu.  Le compilateur peut appeler cette fonction sans remplacer l'appel de fonction par des instructions inline, si cela entraîne de meilleures performances.

Les fonctions de bibliothèque avec des formes intrinsèques sont répertoriées ci-dessous. Une fois un **intrinsèque** pragma est vu, il prend effet à la première définition de fonction contenant une fonction intrinsèque spécifiée. L’effet se poursuit jusqu'à la fin du fichier source ou à l’apparence d’un `function` pragma spécifiant la même fonction intrinsèque. Le **intrinsèque** pragma peut être utilisé uniquement en dehors d’une définition de fonction, au niveau global.

Les fonctions suivantes ont des formes intrinsèques et les formes intrinsèques sont utilisées lorsque vous spécifiez [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Les programmes qui utilisent des fonctions intrinsèques sont plus rapides, car ils n'ont pas la charge liée à l'appel des fonctions, mais ils peuvent être plus volumineux en raison du code supplémentaire généré.

**x86 spécifique**

Le `_disable` et `_enable` générer des instructions en mode noyau pour désactiver ou activer des interruptions de fonctions intrinsèques et peut être utiles dans les pilotes en mode noyau.

### <a name="example"></a>Exemple

Compilez le code suivant à partir de la ligne de commande avec `cl -c -FAs sample.c` et examinez sample.asm pour vérifier qu’ils activent dans x86 instructions CLI et STI :

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

**Fin x86 spécifiques**

Les fonctions à virgule flottante répertoriées ci-dessous n'ont pas de véritables formes intrinsèques. À la place, elles ont des versions qui passent directement des arguments au processeur à virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme :

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

 Les fonctions à virgule flottante répertoriées ci-dessous ont de véritables formes intrinsèques lorsque vous spécifiez [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/Og](../build/reference/og-global-optimizations.md), et [Fast](../build/reference/fp-specify-floating-point-behavior.md) (ou toute option qui inclut /Og : [/ Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)et/O2) :

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Vous pouvez utiliser [/fp : strict](../build/reference/fp-specify-floating-point-behavior.md) ou [/Za](../build/reference/za-ze-disable-language-extensions.md) pour remplacer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.

Consultez [fonction #pragma](../preprocessor/function-c-cpp.md) pour plus d’informations et un exemple sur la façon d’activer/désactiver les intrinsèques pour un bloc de texte source.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)  