---
title: Prise en charge des fonctions mathématiques complexes C
ms.date: 03/30/2018
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: 12ba858993d3712cbf390288df60faedc602c90a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452609"
---
# <a name="c-complex-math-support"></a>Prise en charge des fonctions mathématiques complexes C

La bibliothèque Microsoft Runtime C (CRT) propose des fonctions mathématiques complexes, notamment toutes celles exigées par la norme ISO C99. Le compilateur ne prend pas en charge directement un mot clé **complex** ou **_Complex**, donc l’implémentation Microsoft utilise les types de structure pour représenter des nombres complexes.

Ces fonctions sont implémentées pour équilibrer le niveau de performance avec exactitude. Étant donné que la production du résultat correctement arrondi peut atteindre un coût prohibitif, ces fonctions sont conçues pour produire efficacement une approximation précise du résultat correctement arrondi. Dans la plupart des cas, le résultat produit se situe à +/-1 ULP (Unit in the Last Place, unité en dernière position) du résultat correctement arrondi, même si parfois, le niveau d’imprécision peut être plus grand.

Les routines mathématiques complexes s’appuient sur les fonctions mathématiques à virgule flottante de la bibliothèque pour leur implémentation. Ces fonctions ont des implémentations différentes pour des architectures de processeur différentes. Par exemple, l’implémentation de la bibliothèque CRT x86 32 bits peut être différente de celle de la bibliothèque CRT x64 64 bits. De plus, certaines fonctions peuvent avoir plusieurs implémentations pour une architecture de processeur donnée. L’implémentation la plus efficace est sélectionnée de façon dynamique au moment de l’exécution selon les jeux d’instructions pris en charge par le processeur. Par exemple, dans la bibliothèque CRT x86 32 bits, certaines fonctions ont à la fois une implémentation x87 et une implémentation SSE2. Lors d’une exécution sur un processeur qui prend en charge SSE2, l’implémentation SSE2 plus rapide est utilisée. Lors d’une exécution sur un processeur qui ne prend pas en charge SSE2, l’implémentation x87 plus lente est utilisée. Étant donné que les différentes implémentations des fonctions de bibliothèque mathématique peuvent utiliser des instructions de processeur différentes et des algorithmes différents pour produire leurs résultats, les fonctions peuvent produire des résultats différents selon les processeurs. Dans la plupart des cas, les résultats se situent à +/-1 ULP (Unit in the Last Place, unité en dernière position) du résultat correctement arrondi, mais les résultats réels peuvent varier selon les processeurs.

## <a name="types-used-in-complex-math"></a>Types utilisés dans les calculs complexes

L’implémentation Microsoft de l’en-tête complex.h définit ces types comme équivalents pour les types complexes natifs standard C99 :

|Type standard|Type Microsoft|
|-|-|
|**float complex** ou **float _Complex**|**_FComplex**|
|**double complex** ou **double _Complex**|**_DComplex**|
|**long double complex** ou **long double _Complex**|**_LComplex**|

L’en-tête math.h définit un type distinct, **struct _complex**, utilisé pour la fonction [_cabs](../c-runtime-library/reference/cabs.md). Le type **struct _complex** n’est pas utilisé par les fonctions de calculs complexes équivalentes [cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Constantes et macros complexes

**I** est défini comme type complexe **float** **_FComplex** initialisé par `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Fonctions trigonométriques

|Fonction|Description|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Calcul de l’arc cosinus complexe d’un nombre complexe|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Calcul de l’arc sinus complexe d’un nombre complexe|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Calcul de l’arc tangente complexe d’un nombre complexe|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Calcul du cosinus complexe d’un nombre complexe|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Calcul du sinus complexe d’un nombre complexe|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Calcul de la tangente complexe d’un nombre complexe|

## <a name="hyperbolic-functions"></a>Fonctions hyperboliques

|Fonction|Description|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Calcul de l’arc cosinus hyperbolique complexe d’un nombre complexe|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Calcul de l’arc sinus hyperbolique complexe d’un nombre complexe|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Calcul de l’arc tangente hyperbolique complexe d’un nombre complexe|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Calcul du cosinus hyperbolique complexe d’un nombre complexe|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Calcul du sinus hyperbolique complexe d’un nombre complexe|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Calcul de la tangente hyperbolique complexe d’un nombre complexe|

## <a name="exponential-and-logarithmic-functions"></a>Fonctions exponentielles et logarithmiques

|Fonction|Description|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Calcul de la valeur exponentielle de base *e* complexe d’un nombre complexe|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Calcul du logarithme népérien (base-*e*) complexe d’un nombre complexe|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Calcul du logarithme en base-10 complexe d’un nombre complexe|

## <a name="power-and-absolute-value-functions"></a>Fonctions valeur absolue et puissance

|Fonction|Description|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Calcul de la valeur absolue complexe (également appelée norme, module ou magnitude) d’un nombre complexe|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Calcul de la fonction puissance complexe x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Calcul de la racine carrée complexe d’un nombre complexe|

## <a name="manipulation-functions"></a>Fonctions de manipulation

|Fonction|Description|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Construction d’un nombre complexe à partir de parties réelles et imaginaires|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Calcul de l’argument (également appelé angle de phase) d’un nombre complexe|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Calcul de la partie imaginaire d’un nombre complexe|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Calcul du conjugué complexe d'un nombre complexe|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Calcul d’une projection d’un nombre complexe sur la sphère de Reimann|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Calcul de la partie réelle d’un nombre complexe|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Calcul de la magnitude au carré d’un nombre complexe|

## <a name="operation-functions"></a>Fonctions d’opération

Comme les nombres complexes ne sont pas un type natif dans le compilateur Microsoft, les opérateurs arithmétiques standard ne sont pas définis sur des types complexes. Pour des raisons pratiques, ces fonctions mathématiques complexes de la bibliothèque sont fournies pour limiter la manipulation de nombres complexes dans le code utilisateur :

|Fonction|Description|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Multiplication de deux nombres complexes|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Multiplication d’un nombre complexe et d’un nombre à virgule flottante|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
