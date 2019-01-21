---
title: /fp (spécifier le comportement de virgule flottante)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 77e6d0c97f1d0381fe32ae23f8d7e8bd02ddf219
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417640"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (spécifier le comportement de virgule flottante)

Spécifie la manière dont le compilateur traite les exceptions, les optimisations et les expressions en virgule flottante. Le **/FP** options spécifient si le code généré permet le changement d’environnement à virgule flottante pour le mode d’arrondi, les masques d’exception et les comportement subnormal, et si les vérifications d’état à virgule flottante retournent actuel, précis résultats. Elle contrôle si le compilateur génère du code qui gère l’opération de code source et le classement de l’expression et est conforme à la norme pour la propagation des NaN, ou si elle génère à la place du code plus efficace qui peut réorganiser ou combiner des opérations et utiliser ce qui simplifie transformations algébriques qui ne sont pas autorisées par la norme.

## <a name="syntax"></a>Syntaxe

> **/fp:**[**precise** | **strict** | **fast** | **except**[**-**]]

### <a name="arguments"></a>Arguments

#### <a name="precise"></a>Précise

Par défaut, le compilateur utilise **/fp : precise** comportement.

Sous **/fp : precise** le compilateur préserve l’expression de source de classement et arrondi des propriétés de code en virgule flottante lorsqu’il génère et optimise le code objet de l’ordinateur cible. Le compilateur arrondit à la précision de code source en quatre points spécifiques lors de l’évaluation d’expression : lors des affectations, à des conversions de type, quand un argument à virgule flottante est passé à un appel de fonction et lorsqu’une valeur à virgule flottante est retournée à partir d’un appel de fonction. Les calculs intermédiaires peuvent être effectués avec la précision de l’ordinateur. Conversions de type peut être utilisé pour arrondir explicitement les calculs intermédiaires.

Le compilateur n’effectue pas les transformations algébriques sur des expressions en virgule flottante, telles que l’association ou de distribution, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit.
Les expressions qui impliquent des valeurs spéciales (NaN, + infini, - infinity, -0.0) sont traitées en fonction des spécifications de normes IEEE-754. Par exemple, `x != x` prend la valeur **true** si x est NaN. À virgule flottante *contractions*, autrement dit, les instructions machine qui combinent des opérations à virgule flottante, peuvent être générés sous **/fp : precise**.

Le compilateur génère du code destiné à s’exécuter le [environnement à virgule flottante par défaut](#the-default-floating-point-environment) et suppose que l’environnement à virgule flottante n’est pas accessible ou modifié pendant l’exécution. Autrement dit, il suppose que le code ne démasquer les exceptions de virgule flottante, lire ou écrire des registres de l’état à virgule flottante ni modifier les modes d’arrondi.

Si votre code en virgule flottante ne dépend pas de l’ordre des opérations et des expressions dans vos instructions à virgule flottante (par exemple, si vous ne vous souciez si `a * b + a * c` est calculée en tant que `(b + c) * a` ou `2 * a` comme `a + a`), envisagez le [Fast](#fast) option, ce qui peut produire un code plus rapide et plus efficace. Si votre code à la fois dépend de l’ordre des opérations et des expressions et y accède ou modifie l’environnement à virgule flottante (par exemple, pour modifier les modes d’arrondi ou pour intercepter les exceptions de virgule flottante), utilisez [/fp : strict](#strict).

#### <a name="strict"></a>strict

**/ fp : strict** a un comportement similaire à **/fp : precise**, autrement dit, le compilateur préserve la source et arrondi des propriétés de code en virgule flottante lorsqu’il génère et optimise l’objet code de la machine cible et respecte la norme lors de la gestion des valeurs spéciales. En outre, le programme peut accéder en toute sécurité ou de modifier l’environnement à virgule flottante lors de l’exécution.

Sous **/fp : strict**, le compilateur génère du code qui permet au programme de démasquer les exceptions de virgule flottante, lire ou écrire des registres de l’état de virgule flottante ou modifier les modes d’arrondi en toute sécurité. Il est arrondi à la précision de code source à des moments particuliers quatre lors de l’évaluation d’expression : lors des affectations, à des conversions de type, quand un argument à virgule flottante est passé à un appel de fonction et lorsqu’une valeur à virgule flottante est retournée à partir d’un appel de fonction. Les calculs intermédiaires peuvent être effectués avec la précision de l’ordinateur. Conversions de type peut être utilisé pour arrondir explicitement les calculs intermédiaires. Le compilateur n’effectue pas les transformations algébriques sur des expressions en virgule flottante, telles que l’association ou de distribution, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit. Les expressions qui impliquent des valeurs spéciales (NaN, + infini, - infinity, -0.0) sont traitées en fonction des spécifications de normes IEEE-754. Par exemple, `x != x` prend la valeur **true** si x est NaN. Contractions à virgule flottante ne sont pas générées sous **/fp : strict**.

**/ fp : strict** calculs sont plus onéreux que **/fp : precise** , car le compilateur doit insérer des instructions supplémentaires pour intercepter les exceptions et autoriser des programmes accéder ou modifier l’environnement à virgule flottante à Runtime. Si votre code n’utilise pas cette fonctionnalité, mais nécessite l’ordre de code source et arrondi ou s’appuie sur des valeurs spéciales, utilisez **/fp : precise**. Sinon, envisagez d’utiliser **Fast**, ce qui peut produire du code plus rapide et plus petits.

#### <a name="fast"></a>Rapide

Le **Fast** option permet au compilateur de réorganiser, combiner et simplifier les opérations à virgule flottante pour optimiser le code en virgule flottante pour la vitesse et l’espace. Le compilateur peut omettre l’arrondi lors des instructions d’assignation, des conversions de type ou d’appels de fonction. Il peut réorganiser les opérations ou effectuer des transformations algébriques, par exemple, à l’aide de lois associatives et DISTRIBUTIVES, même si ces transformations entraînent un comportement arrondi logiciel différent. En raison de cette optimisation améliorée, le résultat de certains calculs en virgule flottante peut-être différer de celles générées par d’autres **/FP** options. Les valeurs spéciales (NaN, + infini, - infinity, -0.0) ne peuvent pas être propagées ou se comportent strictement selon la norme IEEE-754. Contractions à virgule flottante peuvent être générées sous **Fast**. Le compilateur est toujours lié à l’architecture sous-jacente sous **Fast**, et des optimisations supplémentaires peuvent être disponibles à l’aide de la [/arch](../../build/reference/arch-minimum-cpu-architecture.md) option.

Sous **Fast**, le compilateur génère du code destiné à s’exécuter dans l’environnement à virgule flottante par défaut et suppose que l’environnement à virgule flottante n’est pas ouvert ou modifié lors de l’exécution. Autrement dit, il suppose que le code ne démasquer les exceptions de virgule flottante, lire ou écrire des registres de l’état à virgule flottante ni modifier les modes d’arrondi.

**Fast** est conçue pour les programmes qui ne nécessitent pas de classement de code source strict et arrondi des expressions en virgule flottante et ne reposent pas sur les règles standard pour la gestion des valeurs spéciales telles que NaN. Si votre code en virgule flottante nécessite la conservation du code source classement et arrondi ou repose sur un comportement standard de valeurs spéciales, utilisez [/fp : precise](#precise). Si votre code accède ou modifie l’environnement à virgule flottante pour changer de mode d’arrondi, démasquer les exceptions de virgule flottante, ou vérifier l’état à virgule flottante, utilisez [/fp : strict](#strict).

#### <a name="except"></a>except

Le **/fp : sauf** option génère du code pour garantir que toutes les exceptions à virgule flottante non masquées sont déclenchées sur le point exact auquel ils se produisent, et qu’aucune exception de virgule flottante supplémentaires n’est déclenchées. Par défaut, le **/fp : strict** option permet **/fp : sauf**, et **/fp : precise** pas. Le **/fp : sauf** option n’est pas compatible avec **Fast**. L’option peut être désactivée explicitement par nous de **/fp : à l’exception de-**.

Notez que **/fp : sauf** n’active pas les exceptions de virgule flottante par lui-même, mais il est nécessaire pour les programmes activer les exceptions de virgule flottante. Consultez [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) pour plus d’informations sur l’activation des exceptions de virgule flottante.

## <a name="remarks"></a>Notes

Plusieurs **/FP** options peuvent être spécifiées dans la même ligne de commande du compilateur. Seul l’un des **/fp : strict**, **Fast**, et **/fp : precise** options peuvent être active à la fois. Si plusieurs de ces options est spécifié sur la ligne de commande, l’option de version ultérieure est prioritaire et le compilateur génère un avertissement. Le **/fp : strict** et **/fp : sauf** options ne sont pas compatibles avec **/CLR**.

Le [/Za](../../build/reference/za-ze-disable-language-extensions.md) option (compatibilité ANSI) n’est pas compatible avec **/FP**.

### <a name="using-pragmas-to-control-floating-point-behavior"></a>À l’aide des Pragmas pour contrôler le comportement à virgule flottante

Le compilateur fournit trois directives pragma pour substituer le comportement de virgule flottante spécifié sur la ligne de commande : [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md), et [fp_contract](../../preprocessor/fp-contract.md). Vous pouvez utiliser ces pragmas pour contrôler le comportement de virgule flottante au niveau de fonction, pas dans une fonction. Notez que ces pragmas ne correspondent pas directement à la **/FP** options. Ce tableau montre comment la **/FP** pragmas et options de mapper les unes aux autres. Pour plus d’informations, consultez la documentation pour les pragmas et options individuelles.

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|**/fp:fast**|Hors tension|Hors tension|Hors tension|actif|
|**/fp:precise**|actif|Hors tension|Hors tension|actif|
|**/fp:except**|actif|actif|actif|Hors tension|

### <a name="the-default-floating-point-environment"></a>L’environnement à virgule flottante par défaut

Quand un processus est initialisé, le *par défaut flottante de l’environnement* est définie. Cet environnement masque les exceptions de virgule flottante tout, définit le mode d’arrondi auquel arrondir le chiffre le plus proche (`FE_TONEAREST`), conserve subnormal (denormal) valeurs, utilisées par la précision par défaut de la mantisse (mantisse) pour **float**, **double**, et **long double** de valeurs et où la prise en charge, définit le contrôle de l’infini pour le mode affine par défaut.

### <a name="floating-point-environment-access-and-modification"></a>Modification et l’accès à l’environnement à virgule flottante

Le runtime Microsoft Visual C++ fournit plusieurs fonctions pour accéder et modifier l’environnement à virgule flottante. Ceux-ci incluent [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md), et [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) et leurs variantes. Pour garantir un comportement de programme approprié lorsque votre code accède ou modifie l’environnement à virgule flottante, `fenv_access` doit être activé, soit par le **/fp : strict** option ou en utilisant le `fenv_access` pragma, pour ces fonctions pour a aucun effet. Lorsque `fenv_access` est ne pas activé, l’accès ou modification de l’environnement à virgule flottante peut entraîner un comportement inattendu du programme : code ne pas appliquer les modifications demandées pour l’environnement à virgule flottante ; les registres de l’état à virgule flottante peut ne pas signalent. résultats attendus ou en cours ; et les exceptions de virgule flottante inattendues peuvent se produire ou des exceptions de virgule flottante attendues ne peuvent pas se produire.

Lorsque votre code accède ou modifie l’environnement à virgule flottante, vous devez être prudent lorsque vous combinez le code où `fenv_access` est activé avec le code qui n’a pas `fenv_access` activé. Dans le code où `fenv_access` n’est pas activé, le compilateur suppose que l’environnement à virgule flottante de plateforme par défaut est en vigueur, et que l’état à virgule flottante n’est pas ouvert ou modifié. Nous vous recommandons de vous enregistrer et restaurer l’environnement à virgule flottante local à son état par défaut avant que le contrôle est transféré à une fonction qui n’a pas `fenv_access` activé. Cet exemple montre comment la `float_control` pragma peut être défini et restauré :

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Modes d’arrondi à virgule flottante

Dans les répertoires **/fp : precise** et **Fast** le compilateur génère du code destiné à s’exécuter dans l’environnement à virgule flottante par défaut et suppose que l’environnement n’est pas ouvert ou modifié lors de l’exécution. Autrement dit, il suppose que le code ne démasquer les exceptions de virgule flottante, lire ou écrire des registres de l’état à virgule flottante ni modifier les modes d’arrondi.  Toutefois, certains programmes ont besoin modifier l’environnement à virgule flottante. Par exemple, cet exemple calcule les limites d’erreur d’une multiplication à virgule flottante en modifiant les modes d’arrondi à virgule flottante :

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Étant donné que le compilateur suppose que la valeur par défaut flottante de l’environnement sous **Fast** et **/fp : precise** il est libre d’ignorer les appels à `_controlfp_s`. Par exemple, lors de la compilation à l’aide de deux **/O2** et **/fp : precise** pour la x86 architecture, les limites ne sont pas calculées et sorties de l’exemple de programme :

```Output
cLower = -inf
cUpper = -inf
```

Lors de la compilation avec les deux **/O2** et **/fp : strict** pour la x86 architecture, l’exemple de programme génère :

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Valeurs spéciales à virgule flottante

Sous **/fp : precise** et **/fp : strict**, expressions qui impliquent des valeurs spéciales (NaN, + infini, - infinity, -0.0) se comportent selon les spécifications de normes IEEE-754. Sous **Fast**, le comportement de ces valeurs spéciales peut-être être incohérent avec la norme IEEE-754.

Cet exemple illustre le comportement différent de valeurs spéciales sous **/fp : precise**, **/fp : strict** et **Fast**:

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

Lors de la compilation avec **/O2** **/fp : precise** ou **/O2** **/fp : strict** pour x86 architecture, les sorties sont cohérents avec la norme IEEE-754 spécification :

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Lors de la compilation avec **/O2** **Fast** pour x86 architecture, les sorties ne sont pas cohérentes avec la norme IEEE-754 :

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Transformations algébriques à virgule flottante

Sous **/fp : precise** et **/fp : strict**, le compilateur n’effectue pas les transformations de mathématiques, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit. Le compilateur peut effectuer de telles transformations sous **Fast**. Par exemple, l’expression `a * b + a * c` dans l’exemple de fonction `algebraic_transformation` peut être compilée dans `a * (b + c)` sous **Fast**. Ces transformations ne sont pas effectuées sous **/fp : precise** ou **/fp : strict**, et le compilateur génère `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Points de conversion explicite à virgule flottante

Sous **/fp : precise** et **/fp : strict**, le compilateur arrondit à la précision de code source en quatre points spécifiques lors de l’évaluation d’expression : lors des affectations, à des conversions de type, quand un argument à virgule flottante est passé à un appel de fonction, et la valeur à virgule flottante est retournée à partir d’un appel de fonction. Conversions de type peut être utilisé pour arrondir explicitement les calculs intermédiaires. Sous **Fast**, le compilateur ne génère pas de conversions explicites à ces points pour garantir la précision de code source. Cet exemple illustre le comportement sous différents **/FP** options :

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Lors de la compilation à l’aide de **/O2** **/fp : precise** ou **/O2** **/fp : strict**, vous pouvez voir que les casts de types explicites sont insérés à la fois le conversion de type et à la fonction retourner le point dans le code généré pour le x64 architecture :

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

Sous **/O2** **Fast** le code généré est simplifié, car toutes les conversions de type sont optimisées :

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **génération de Code** page de propriétés.

1. Modifier le **modèle de virgule flottante** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](compiler-options.md)<br/>
[Définition des options du compilateur](setting-compiler-options.md)<br/>
[Microsoft Visual C++ d’optimisation à virgule flottante](floating-point-optimization.md)<br/>
