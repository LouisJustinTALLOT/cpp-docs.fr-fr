---
title: Mathématiques de type générique
description: Décrit les macros dans <tgmath. h> qui facilitent l’écriture de code C qui appelle la fonction mathématique appropriée, en fonction du type d’argument.
ms.topic: conceptual
ms.date: 12/10/2020
helpviewer_keywords:
- CRT tgmath.h
ms.openlocfilehash: 70ade08387ebbca9dd1ecd68cce92f5fd8ba936b
ms.sourcegitcommit: be469dd87453255b0e35e333712c8207b09b3dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97411848"
---
# <a name="type-generic-math"></a>Mathématiques de type générique

Pour la norme ISO C standard 11 (C11) et les versions ultérieures, l' `<tgmath.h>` en-tête, en plus d’inclure `<math.h>` et `<complex.h>` , fournit des macros qui appellent une fonction mathématique correspondante en fonction des types de paramètres.

Les fonctions mathématiques de la bibliothèque Runtime C sont des variantes réelles et complexes. Chaque variante est proposée en trois versions, en fonction du type de l’argument : `float` , `double` et `long double` . Comme C ne prend pas en charge la surcharge comme le fait C++, chaque variante a un nom différent. Par exemple, pour obtenir la valeur absolue d’une valeur à virgule flottante réelle, vous pouvez appeler `fabsf` , `fabs` ou `fabsl` selon que vous passez une `float` `double` valeur, ou, `long double` respectivement. Pour obtenir la valeur absolue complexe, vous devez appeler l’une des valeurs, `cabsf` `cabs` ou `cabsl` selon que vous passez `float` respectivement une valeur, `double` et une `long double` valeur complexe. Si les arguments ne correspondent pas à l’un des types mentionnés ci-dessus, la fonction est choisie comme si les arguments étaient doubles.

`<tgmath.h>` contient des macros qui simplifient la sélection de la fonction mathématique appropriée à appeler. Les macros examinent le type qu’elles sont passées, puis appellent la fonction Right. Par exemple, la `sqrt` macro est liée `sqrt(9.9f)` à `sqrtf()` , mais elle est liée `sqrt(9.9)` à `sqrt()` . Si au moins un argument de macro pour un paramètre générique est complexe, la macro est liée à une fonction complexe ; Sinon, elle appelle une fonction réelle.

Les macros génériques de type dans `<tgmath.h>` vous permettent d’écrire du code plus portable, car vous n’avez pas besoin de gérer le cast ou de sélectionner des noms de fonction différents en fonction du type d’argument.

Ces macros sont dans leur propre en-tête afin que les programmes écrits à l’aide de l' `<math.h>` en-tête ne s’interrompent pas. Ainsi `double x = sin(42);` se comporte comme s’il s’agissait toujours de \<math.h> . Même dans ce cas, la plupart des programmes C existants sont censés ne pas être affectés lorsque l' `<tgmath.h>` en-tête est inclus à la place de `<math.h>` ou `<complex.h>` .

Le tableau suivant répertorie les macros disponibles dans `<tgmath.h>` et leur développement. `modf` n’est pas inclus dans ce tableau, car il n’a pas de macro générique de type correspondant, car il n’est pas évident de savoir comment le rendre sécurisé sans compliquer la résolution de type.

|Macro  |Real</br>`float`  | Real</br>`double` | Real</br>`long double` | Complex</br>`float` | Complex</br>`double` | Complex</br>`long double` |
|---------|---------|---------|---------|---------|---------|---------|
`acos` | [`acosf`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`acos`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`acosl`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`cacosf`](reference/cacos-cacosf-cacosl.md) | [`cacos`](reference/cacos-cacosf-cacosl.md) | [`cacosl`](reference/cacos-cacosf-cacosl.md) |
`acosh` | [`acoshf`](reference/acosh-acoshf-acoshl.md) | [`acosh`](reference/acosh-acoshf-acoshl.md) | [`acoshl`](reference/acosh-acoshf-acoshl.md) | [`cacoshf`](reference/cacosh-cacoshf-cacoshl.md) | [`cacosh`](reference/cacosh-cacoshf-cacoshl.md) | [`cacoshl`](reference/cacosh-cacoshf-cacoshl.md) |
`asin` | [`asinf`](reference/asin-asinf-asinl.md) | [`asin`](reference/asin-asinf-asinl.md) | [`asinl`](reference/asin-asinf-asinl.md) | [`casinf`](reference/casin-casinf-casinl.md) | [`casin`](reference/casin-casinf-casinl.md) | [`casinl`](reference/casin-casinf-casinl.md) |
`asinh` | [`asinhf`](reference/asin-asinf-asinl.md) | [`asinh`](reference/asin-asinf-asinl.md) | [`asinhl`](reference/asin-asinf-asinl.md) | [`casinhf`](reference/casinh-casinhf-casinhl.md) | [`casinh`](reference/casinh-casinhf-casinhl.md) | [`casinhl`](reference/casinh-casinhf-casinhl.md) |
`atan` | [`atanf`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atanl`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`catanf`](reference/catan-catanf-catanl.md) | [`catan`](reference/catan-catanf-catanl.md) | [`catanl`](reference/catan-catanf-catanl.md) |
`atanh` | [`atanhf`](reference/atanh-atanhf-atanhl.md) | [`atanh`](reference/atanh-atanhf-atanhl.md) | [`atanhl`](reference/atanh-atanhf-atanhl.md) | [`catanhf`](reference/catanh-catanhf-catanhl.md) | [`catanh`](reference/catanh-catanhf-catanhl.md) | [`catanhl`](reference/catanh-catanhf-catanhl.md) |
`cos` | [`cosf`](reference/cos-cosf-cosl.md) | [`cos`](reference/cos-cosf-cosl.md) | [`cosl`](reference/cos-cosf-cosl.md) | [`ccosf`](reference/ccos-ccosf-ccosl.md) | [`ccos`](reference/ccos-ccosf-ccosl.md) | [`ccosl`](reference/ccos-ccosf-ccosl.md) |
`cosh` | [`coshf`](reference/cosh-coshf-coshl.md) | [`cosh`](reference/cosh-coshf-coshl.md) | [`coshl`](reference/cosh-coshf-coshl.md) | [`ccoshf`](reference/ccosh-ccoshf-ccoshl.md) | [`ccosh`](reference/ccosh-ccoshf-ccoshl.md) | [`ccoshl`](reference/ccosh-ccoshf-ccoshl.md) |
`exp` | [`expf`](reference/exp-expf.md) | [`exp`](reference/exp-expf.md) | [`expl`](reference/exp-expf.md) | [`cexpf`](reference/cexp-cexpf-cexpl.md) | [`cexp`](reference/cexp-cexpf-cexpl.md) | [`cexpl`](reference/cexp-cexpf-cexpl.md) |
`fabs` | [`fabsf`](reference/fabs-fabsf-fabsl.md) | [`fabs`](reference/fabs-fabsf-fabsl.md) | [`fabsl`](reference/fabs-fabsf-fabsl.md) | [`cabsf`](reference/cabs-cabsf-cabsl.md) | [`cabs`](reference/cabs-cabsf-cabsl.md) | [`cabsl`](reference/cabs-cabsf-cabsl.md) |
`log` | [`logf`](reference/log-logf-log10-log10f.md) | [`log`](reference/log-logf-log10-log10f.md) | [`logl`](reference/log-logf-log10-log10f.md) | [`clogf`](reference/clog-clogf-clogl.md) | [`clog`](reference/clog-clogf-clogl.md) | [`clogl`](reference/clog-clogf-clogl.md) |
`pow` | [`powf`](reference/pow-powf-powl.md) | [`pow`](reference/pow-powf-powl.md) | [`powl`](reference/pow-powf-powl.md) | [`cpowf`](reference/cpow-cpowf-cpowl.md) | [`cpow`](reference/cpow-cpowf-cpowl.md) | [`cpowl`](reference/cpow-cpowf-cpowl.md) |
`sin` | [`sinf`](reference/sin-sinf-sinl.md) | [`sin`](reference/sin-sinf-sinl.md) | [`sinl`](reference/sin-sinf-sinl.md) | [`csinf`](reference/csin-csinf-csinl.md) | [`csin`](reference/csin-csinf-csinl.md) | [`csinl`](reference/csin-csinf-csinl.md) |
`sinh` | [`sinhf`](reference/sinh-sinhf-sinhl.md) | [`sinh`](reference/sinh-sinhf-sinhl.md) | [`sinhl`](reference/sinh-sinhf-sinhl.md) | [`csinhf`](reference/csinh-csinhf-csinhl.md) | [`csinh`](reference/csinh-csinhf-csinhl.md) | [`csinhl`](reference/csinh-csinhf-csinhl.md) |
`sqrt` | [`sqrtf`](reference/sqrt-sqrtf-sqrtl.md) | [`sqrt`](reference/sqrt-sqrtf-sqrtl.md) | [`sqrtl`](reference/sqrt-sqrtf-sqrtl.md) | [`csqrtf`](reference/csqrt-csqrtf-csqrtl.md) | [`csqrt`](reference/csqrt-csqrtf-csqrtl.md) | [`csqrtl`](reference/csqrt-csqrtf-csqrtl.md) |
`tan` | [`tanf`](reference/tan-tanf-tanl.md) | [`tan`](reference/tan-tanf-tanl.md) | [`tanl`](reference/tan-tanf-tanl.md) | [`ctanf`](reference/ctan-ctanf-ctanl.md) | [`ctan`](reference/ctan-ctanf-ctanl.md) | [`ctanl`](reference/ctan-ctanf-ctanl.md) |
`tanh` | [`tanhf`](reference/tanh-tanhf-tanhl.md) | [`tanh`](reference/tanh-tanhf-tanhl.md) | [`tanhl`](reference/tanh-tanhf-tanhl.md) | [`ctanhf`](reference/ctanh-ctanhf-ctanhl.md) | [`ctanh`](reference/ctanh-ctanhf-ctanhl.md) | [`ctanhl`](reference/ctanh-ctanhf-ctanhl.md) |
`atan2` | [`atan2f`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan2`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan2l`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | - | - | - |
`cbrt` | [`cbrtf`](reference/cbrt-cbrtf-cbrtl.md) | [`cbrt`](reference/cbrt-cbrtf-cbrtl.md) | [`cbrtl`](reference/cbrt-cbrtf-cbrtl.md) | - | - | - |
`ceil` | [`ceilf`](reference/ceil-ceilf-ceill.md) | [`ceil`](reference/ceil-ceilf-ceill.md) | [`ceill`](reference/ceil-ceilf-ceill.md) | - | - | - |
`copysign` | [`copysignf`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [`copysign`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [`copysignl`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | - | - | - |
`erf` | [`erff`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erf`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfl`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`erfc` | [`erfcf`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfc`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfcl`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`exp2` | [`exp2f`](reference/exp2-exp2f-exp2l.md) | [`exp2`](reference/exp2-exp2f-exp2l.md) | [`exp2l`](reference/exp2-exp2f-exp2l.md) | - | - | - |
`expm1` | [`expm1f`](reference/expm1-expm1f-expm1l.md) | [`expm1`](reference/expm1-expm1f-expm1l.md) | [`expm1l`](reference/expm1-expm1f-expm1l.md) | - | - | - |
`fdim` | [`fdimf`](reference/fdim-fdimf-fdiml.md) | [`fdim`](reference/fdim-fdimf-fdiml.md) | [`fdiml`](reference/fdim-fdimf-fdiml.md) | - | - | - |
`floor` | [`floorf`](reference/floor-floorf-floorl.md) | [`floor`](reference/floor-floorf-floorl.md) | [`floorl`](reference/floor-floorf-floorl.md) | - | - | - |
`fma` | [`fmaf`](reference/fma-fmaf-fmal.md) | [`fma`](reference/fma-fmaf-fmal.md) | [`fmal`](reference/fma-fmaf-fmal.md) | - | - | - |
`fmax` | [`fmaxf`](reference/fmax-fmaxf-fmaxl.md) | [`fmax`](reference/fmax-fmaxf-fmaxl.md) | [`fmaxl`](reference/fmax-fmaxf-fmaxl.md) | - | - | - |
`fmin` | [`fminf`](reference/fmin-fminf-fminl.md) | [`fmin`](reference/fmin-fminf-fminl.md) | [`fminl`](reference/fmin-fminf-fminl.md) | - | - | - |
`fmod` | [`fmodf`](reference/fmod-fmodf.md) | [`fmod`](reference/fmod-fmodf.md) | [`fmodl`](reference/fmod-fmodf.md) | - | - | - |
`frexp` | [`frexpf`](reference/frexp.md) | [`frexp`](reference/frexp.md) | [`frexpl`](reference/frexp.md) | - | - | - |
`hypot` | [`hypotf`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [`hypot`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [`hypotl`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | - | - | - |
`ilogb` | [`ilogbf`](reference/ilogb-ilogbf-ilogbl2.md) | [`ilogb`](reference/ilogb-ilogbf-ilogbl2.md) | [`ilogbl`](reference/ilogb-ilogbf-ilogbl2.md) | - | - | - |
`ldexp` | [`ldexpf`](reference/ldexp.md) | [`ldexp`](reference/ldexp.md) | [`ldexpl`](reference/ldexp.md) | - | - | - |
`lgamma` | [`lgammaf`](reference/lgamma-lgammaf-lgammal.md) | [`lgamma`](reference/lgamma-lgammaf-lgammal.md) | [`lgammal`](reference/lgamma-lgammaf-lgammal.md) | - | - | - |
`llrint` | [`llrintf`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`llrint`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`llrintl`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`llround` | [`llroundf`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`llround`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`llroundl`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`log10` | [`log10f`](reference/log-logf-log10-log10f.md) | [`log10`](reference/log-logf-log10-log10f.md) | [`log10l`](reference/log-logf-log10-log10f.md) | - | - | - |
`log1p` | [`log1pf`](reference/log1p-log1pf-log1pl2.md) | [`log1p`](reference/log1p-log1pf-log1pl2.md) | [`log1pl`](reference/log1p-log1pf-log1pl2.md) | - | - | - |
`log2` | [`log2f`](reference/log2-log2f-log2l.md) | [`log2`](reference/log2-log2f-log2l.md) | [`log2l`](reference/log2-log2f-log2l.md) | - | - | - |
`logb` | [`logbf`](reference/logb-logbf-logbl-logb-logbf.md) | [`logb`](reference/logb-logbf-logbl-logb-logbf.md) | [`logbl`](reference/logb-logbf-logbl-logb-logbf.md) | - | - | - |
`lrint` | [`lrintf`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`lrint`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`lrintl`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`lround` | [`lroundf`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`lround`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`lroundl`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`nearbyint` | [`nearbyintf`](reference/nearbyint-nearbyintf-nearbyintl1.md) | [`nearbyint`](reference/nearbyint-nearbyintf-nearbyintl1.md) | [`nearbyintl`](reference/nearbyint-nearbyintf-nearbyintl1.md) | - | - | - |
`nextafter` | [`nextafterf`](reference/nextafter-functions.md) | [`nextafter`](reference/nextafter-functions.md) | [`nextafterl`](reference/nextafter-functions.md) | - | - | - |
`nexttoward` | [`nexttowardf`](reference/nextafter-functions.md) | [`nexttoward`](reference/nextafter-functions.md) | [`nexttowardl`](reference/nextafter-functions.md) | - | - | - |
`remainder` | [`remainderf`](reference/remainder-remainderf-remainderl.md) | [`remainder`](reference/remainder-remainderf-remainderl.md) | [`remainderl`](reference/remainder-remainderf-remainderl.md) | - | - | - |
`remquo` | [`remquof`](reference/remquo-remquof-remquol.md) | [`remquo`](reference/remquo-remquof-remquol.md) | [`remquol`](reference/remquo-remquof-remquol.md) | - | - | - |
`rint` | [`rintf`](reference/rint-rintf-rintl.md) | [`rint`](reference/rint-rintf-rintl.md) | [`rintl`](reference/rint-rintf-rintl.md) | - | - | - |
`round` | [`roundf`](reference/round-roundf-roundl.md) | [`round`](reference/round-roundf-roundl.md) | [`roundl`](reference/round-roundf-roundl.md) | - | - | - |
`scalbln` | [`scalblnf`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbln`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalblnl`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`scalbn` | [`scalbnf`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbn`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbnl`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`tgamma` | [`tgammaf`](reference/tgamma-tgammaf-tgammal.md) | [`tgamma`](reference/tgamma-tgammaf-tgammal.md) | [`tgammal`](reference/tgamma-tgammaf-tgammal.md) | - | - | - |
`trunc` | [`truncf`](reference/trunc-truncf-truncl.md) | [`trunc`](reference/trunc-truncf-truncl.md) | [`truncl`](reference/trunc-truncf-truncl.md) | - | - | - |
`carg` | - | - | - | [`cargf`](reference/carg-cargf-cargl.md) | [`carg`](reference/carg-cargf-cargl.md) | [`cargl`](reference/carg-cargf-cargl.md) |
`conj` | - | - | - | [`conjf`](reference/conj-conjf-conjl.md) | [`conj`](reference/conj-conjf-conjl.md) | [`conjl`](reference/conj-conjf-conjl.md) |
`creal` | - | - | - | [`crealf`](reference/creal-crealf-creall.md) | [`creal`](reference/creal-crealf-creall.md) | [`creall`](reference/creal-crealf-creall.md) |
`cimag` | - | - | - | [`cimagf`](reference/cimag-cimagf-cimagl.md) | [`cimag`](reference/cimag-cimagf-cimagl.md) | [`cimagl`](reference/cimag-cimagf-cimagl.md) |
`cproj` | - | - | - | [`cprojf`](reference/cproj-cprojf-cprojl.md) | [`cproj`](reference/cproj-cprojf-cprojl.md) | [`cprojl`](reference/cproj-cprojf-cprojl.md) |

## <a name="requirements"></a>Configuration requise

[std : c++ 11](../build/reference/std-specify-language-standard-version.md) ou version ultérieure est requis.

SDK Windows version 10.0.20201.0 ou ultérieure. Il s’agit actuellement d’une version Insider que vous pouvez télécharger à partir des [Téléchargements Windows Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK). Consultez [C11 et C17 : prise en main](https://devblogs.microsoft.com/cppblog/c11-and-c17-standard-support-arriving-in-msvc/#c11-and-c17-getting-started) pour obtenir des instructions sur l’installation et l’utilisation de ce kit de développement logiciel (SDK).

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque de Run-Time C](c-run-time-library-reference.md)
