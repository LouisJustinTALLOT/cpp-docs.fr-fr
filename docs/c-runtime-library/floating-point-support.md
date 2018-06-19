---
title: Prise en charge des fonctions mathématiques et à virgule flottante | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.math
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf4a6ce7e2ad98841c20fcef5fd9639a5797852
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392547"
---
# <a name="math-and-floating-point-support"></a>Prise en charge des fonctions mathématiques et à virgule flottante

La bibliothèque du Runtime C universel (UCRT) propose de nombreuses fonctions de bibliothèque mathématique à virgule flottante, notamment toutes celles exigées par la norme ISO C99. Les fonctions à virgule flottante sont implémentées pour équilibrer le niveau de performance avec exactitude. Étant donné que la production du résultat correctement arrondi peut atteindre un coût prohibitif, ces fonctions sont conçues pour produire efficacement une approximation précise du résultat correctement arrondi. Dans la plupart des cas, le résultat produit se situe à +/-1 ULP (Unit in the Last Place, unité en dernière position) du résultat correctement arrondi, même si parfois, le niveau d’imprécision peut être plus grand.

De nombreuses fonctions de bibliothèque mathématique à virgule flottante ont des implémentations différentes pour des architectures de processeur différentes. Par exemple, l’implémentation de la bibliothèque CRT x86 32 bits peut être différente de celle de la bibliothèque CRT x64 64 bits. De plus, certaines fonctions peuvent avoir plusieurs implémentations pour une architecture de processeur donnée. L’implémentation la plus efficace est sélectionnée de façon dynamique au moment de l’exécution selon les jeux d’instructions pris en charge par le processeur. Par exemple, dans la bibliothèque CRT x86 32 bits, certaines fonctions ont à la fois une implémentation x87 et une implémentation SSE2. Lors d’une exécution sur un processeur qui prend en charge SSE2, l’implémentation SSE2 plus rapide est utilisée. Lors d’une exécution sur un processeur qui ne prend pas en charge SSE2, l’implémentation x87 plus lente est utilisée. Étant donné que les différentes implémentations des fonctions de bibliothèque mathématique peuvent utiliser des instructions de processeur différentes et des algorithmes différents pour produire leurs résultats, les fonctions peuvent produire des résultats différents selon les processeurs. Dans la plupart des cas, les résultats se situent à +/-1 ULP (Unit in the Last Place, unité en dernière position) du résultat correctement arrondi, mais les résultats réels peuvent varier selon les processeurs.

Les précédentes versions 16 bits de Microsoft C/C++ et Microsoft Visual C++ prenaient en charge le type **long double** en tant que type de données à virgule flottante de précision 80 bits. Dans les versions plus récentes de Visual C++, le type de données **long double** est un type de données à virgule flottante de précision 64 bits identique au type **double**. Le compilateur traite **long double** et **double** comme deux types distincts, mais les fonctions **long double** sont identiques à leurs équivalents **double**. La bibliothèque CRT fournit des versions **long double** des fonctions mathématiques à des fins de compatibilité du code source ISO C99, mais notez que la représentation binaire peut différer de celle d’autres compilateurs.

## <a name="supported-math-and-floating-point-routines"></a>Routines à virgule flottante et mathématiques prises en charge

|Routine|Utilisez|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Calcule la valeur absolue d’un type integer
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Calcule l’arc cosinus
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Calcule l’arc cosinus hyperbolique
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Calcule l’arc sinus
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Calcule l’arc sinus hyperbolique
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Calcule l’arc tangente
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Calcule l’arc tangente hyperbolique
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convertit une chaîne de paramètres régionaux en une valeur **double**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertit une chaîne en une valeur **double**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convertit une chaîne de paramètres régionaux en une valeur **float** ou **long double**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Calcule la racine cubique
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Calcule la valeur plafond
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Calcule l’inverse additif
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Obtient et efface le registre d’état à virgule flottante
[_control87, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Obtient et définit le mot de contrôle à virgule flottante
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Version sécurisée de **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Retourne une valeur qui a la grandeur d’un argument et le signe d’un autre
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|Calcule le sinus
[cos, cosf, cosl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Calcule le sinus hyperbolique
[div, ldiv, lldiv](../c-runtime-library/reference/div.md)|Calcule le quotient et le reste de deux valeurs entières
[_ecvt](../c-runtime-library/reference/ecvt.md), [ecvt](../c-runtime-library/reference/posix-ecvt.md)|Convertit une valeur **double** en une chaîne
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Version sécurisée de **_ecvt**
[erf, erff, erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Calcule la fonction d’erreur
[erfc, erfcf, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Calcule la fonction d’erreur complémentaire
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Calcule la valeur exponentielle *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Calcule la valeur exponentielle 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Calcule *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Calcule la valeur absolue d’un type à virgule flottante
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|Convertir un nombre à virgule flottante en chaîne
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Version sécurisée de **_fcvt**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Détermine la différence positive entre les deux valeurs
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Efface les exceptions de virgule flottante spécifiées
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Stocke l’environnement à virgule flottante actuel
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Obtient l’état des exceptions de virgule flottante spécifiées
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Obtient le mode d’arrondi de virgule flottante
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Définit le mode d’exception de virgule flottante non stop
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Lève les exceptions de virgule flottante spécifiées
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Définit l’environnement à virgule flottante actuel
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Définit les indicateurs d’état de virgule flottante spécifiés
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Définit le mode d’arrondi de virgule flottante spécifié
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Détermine les indicateurs d’état d’exception de virgule flottante à définir
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Restaure un environnement à virgule flottante, puis lève les exceptions précédentes
[_finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Détermine si une valeur est finie
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Calcule la valeur plancher
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Calcule une multiplication-addition fusionnées
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Calcule la valeur maximale des arguments
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Calcule la valeur minimale des arguments
[fmod, fmodf, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Calcule le reste à virgule flottante
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Retourne la classification d’une valeur à virgule flottante
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Retourne la classification d’une valeur à virgule flottante
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Définit un gestionnaire pour les exceptions de virgule flottante
[_fpreset](../c-runtime-library/reference/fpreset.md)|Redéfinit l’environnement à virgule flottante
[frexp, frexpf, frexpl](../c-runtime-library/reference/frexp.md)|Obtient la mantisse et l’exposant d’un nombre à virgule flottante
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|Convertir un nombre à virgule flottante en chaîne
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Version sécurisée de **_gcvt**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Obtient ou définit un indicateur pour l’utilisation des instructions FMA3 sur x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Calcule l’hypoténuse
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Calcule l’exposant de base 2 entier
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Calcule la valeur absolue d’un type integer
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Calcule le quotient et le reste de deux valeurs entières
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Teste une valeur à virgule flottante pour une valeur NaN
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Calcule la fonction de Bessel
[ldexp, ldexpf, ldexpl](../c-runtime-library/reference/ldexp.md)|Calcule x*2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Calcule le logarithme népérien de la valeur absolue de la fonction gamma
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Arrondit une valeur à virgule flottante à la valeur **long long** la plus proche
[llround, llroundf, llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Arrondit une valeur à virgule flottante à la valeur **long long** la plus proche
[log, logf, logl, log10, log10f, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Calcule le logarithme népérien ou de base 10
[log1p, log1pf, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Calcule le logarithme népérien de 1+x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Calcule le logarithme de base 2
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Retourne l’exposant d’une valeur à virgule flottante
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Arrondit une valeur à virgule flottante à la valeur **long** la plus proche
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Fait pivoter une valeur entière vers la gauche ou vers la droite
[lround, lroundf, lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Arrondit une valeur à virgule flottante à la valeur **long** la plus proche
[_matherr](../c-runtime-library/reference/matherr.md)|Gestionnaire d’erreurs mathématiques par défaut
[__max](../c-runtime-library/reference/max.md)|Macro qui retourne la plus grande de deux valeurs
[__min](../c-runtime-library/reference/min.md)|Macro qui retourne la plus petite de deux valeurs
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Fractionne une valeur à virgule flottante en une partie fractionnaire et une partie entière
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Retourne une valeur NaN silencieuse
[nearbyint, nearbyintf, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Retourne la valeur arrondie
[nextafter, nextafterf, nextafterl, _nextafter, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Retourne la valeur à virgule flottante représentable suivante
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Retourne la valeur à virgule flottante représentable suivante
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Retourne la valeur de *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Calcule le reste du quotient de deux valeurs à virgule flottante
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Calcule le reste de deux valeurs entières
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Arrondit une valeur à virgule flottante
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Fait pivoter les bits de types integer
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Arrondit une valeur à virgule flottante
[_scalb, _scalbf](../c-runtime-library/reference/scalb.md)|Met à l’échelle un argument par une puissance de 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Multiplie un nombre à virgule flottante par une puissance intégrale de **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Définit le mot de contrôle à virgule flottante
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Active ou désactive les instructions SSE2
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Calcule le sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Calcule le sinus hyperbolique
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Calcule la racine carrée
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Obtient le mot d’état de virgule flottante
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Convertit une chaîne en une valeur **float**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Convertit une chaîne en une valeur **long** **double**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Calcule la tangente
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Calcule la tangente hyperbolique
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Calcule la fonction gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Tronque la partie fractionnaire
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertit une chaîne large en une valeur **double**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Calcule la fonction de Bessel

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
