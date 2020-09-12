---
title: /fp (Spécifier le comportement de virgule flottante)
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
ms.openlocfilehash: 7a8ae885bbbf00ae916505bf5df646b32268a17a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040910"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Spécifier le comportement de virgule flottante)

Spécifie comment le compilateur traite les expressions à virgule flottante, les optimisations et les exceptions. Les options **/FP** spécifient si le code généré autorise les modifications de l’environnement à virgule flottante pour le mode d’arrondi, les masques d’exception et le comportement sous-normal, et si les contrôles d’État à virgule flottante retournent les résultats actuels et précis. Il contrôle si le compilateur génère du code qui gère l’opération source et l’ordonnancement des expressions, et s’il est conforme à la norme pour la propagation NaN, ou si, à la place, il génère un code plus efficace qui peut réorganiser ou combiner des opérations et utiliser des transformations algébriques simplifiées qui ne sont pas autorisées par la norme.

## <a name="syntax"></a>Syntaxe

> **/FP :**[**precise**  |  **strict**  |  **Fast**  |  **except**[ **-** ]]

### <a name="arguments"></a>Arguments

#### <a name="precise"></a>établir

Par défaut, le compilateur utilise le `/fp:precise` comportement.

Sous, `/fp:precise` le compilateur conserve les propriétés de classement et d’arrondi de l’expression source du code à virgule flottante lors de la génération et de l’optimisation du code objet pour l’ordinateur cible. Le compilateur arrondit à la précision du code source à quatre points spécifiques pendant l’évaluation de l’expression : aux assignations, à conversions, lorsqu’un argument à virgule flottante est passé à un appel de fonction, et lorsqu’une valeur à virgule flottante est retournée à partir d’un appel de fonction. Les calculs intermédiaires peuvent être effectués au niveau de la précision de l’ordinateur. Conversions peut être utilisé pour arrondir explicitement des calculs intermédiaires.

Le compilateur n’effectue pas de transformations algébriques sur les expressions à virgule flottante, telles que la réassociation ou la distribution, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit.
Les expressions qui impliquent des valeurs spéciales (NaN, + Infinity,-Infinity,-0,0) sont traitées conformément aux spécifications IEEE-754. Par exemple, `x != x` prend la valeur **`true`** si x est NaN. Les *contractions*à virgule flottante, c’est-à-dire les instructions machine qui combinent des opérations à virgule flottante, peuvent être générées sous `/fp:precise` .

Le compilateur génère du code destiné à s’exécuter dans l' [environnement à virgule flottante par défaut](#the-default-floating-point-environment) et suppose que l’environnement à virgule flottante n’est pas accessible ou modifié au moment de l’exécution. Autrement dit, il suppose que le code ne masque pas les exceptions à virgule flottante, ne lit ou n’écrit pas les registres d’État à virgule flottante, ni ne modifie les modes d’arrondi.

Si votre code à virgule flottante ne dépend pas de l’ordre des opérations et des expressions dans vos instructions à virgule flottante (par exemple, si vous ne vous préoccupez pas du `a * b + a * c` calcul en tant que `(b + c) * a` `2 * a` `a + a` ), envisagez l’option [/FP : Fast](#fast) , qui peut produire du code plus rapide et plus efficace. Si votre code dépend de l’ordre des opérations et des expressions, et qu’il accède ou modifie l’environnement à virgule flottante (par exemple, pour modifier les modes d’arrondi ou pour intercepter les exceptions de virgule flottante), utilisez [/FP : strict](#strict).

#### <a name="strict"></a>strict

`/fp:strict` a un comportement semblable à `/fp:precise` , autrement dit, le compilateur conserve les propriétés d’arrondi et de classement de la source de code à virgule flottante lorsqu’il génère et optimise le code de l’objet pour l’ordinateur cible, et observe la norme lors du traitement des valeurs spéciales. En outre, le programme peut accéder à l’environnement à virgule flottante ou le modifier en toute sécurité au moment de l’exécution.

Sous `/fp:strict` , le compilateur génère du code qui permet au programme de masquer en toute sécurité des exceptions de virgule flottante, de lire ou d’écrire des registres d’État à virgule flottante ou de modifier les modes d’arrondi. Il arrondit à la précision du code source à quatre points spécifiques pendant l’évaluation de l’expression : aux assignations, à conversions, lorsqu’un argument à virgule flottante est passé à un appel de fonction, et lorsqu’une valeur à virgule flottante est retournée à partir d’un appel de fonction. Les calculs intermédiaires peuvent être effectués au niveau de la précision de l’ordinateur. Conversions peut être utilisé pour arrondir explicitement des calculs intermédiaires. Le compilateur n’effectue pas de transformations algébriques sur les expressions à virgule flottante, telles que la réassociation ou la distribution, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit. Les expressions qui impliquent des valeurs spéciales (NaN, + Infinity,-Infinity,-0,0) sont traitées conformément aux spécifications IEEE-754. Par exemple, `x != x` prend la valeur **`true`** si x est NaN. Les contractions à virgule flottante ne sont pas générées sous `/fp:strict` .

`/fp:strict` le calcul est plus coûteux que `/fp:precise` parce que le compilateur doit insérer des instructions supplémentaires pour intercepter les exceptions et autoriser les programmes à accéder ou à modifier l’environnement à virgule flottante au moment de l’exécution. Si votre code n’utilise pas cette fonctionnalité, mais requiert le classement et l’arrondi du code source, ou s’appuie sur des valeurs spéciales, utilisez `/fp:precise` . Sinon, envisagez d’utiliser `/fp:fast` , qui peut produire du code plus rapide et plus petit.

#### <a name="fast"></a>fast

L' `/fp:fast` option permet au compilateur de réorganiser, combiner ou simplifier les opérations à virgule flottante pour optimiser le code à virgule flottante pour la vitesse et l’espace. Le compilateur peut omettre l’arrondi au niveau des instructions d’assignation, des conversions ou des appels de fonction. Il peut réorganiser les opérations ou effectuer des transformations algébriques, par exemple, à l’aide de lois associatives et distributive, même si ces transformations entraînent un comportement d’arrondi observable. En raison de cette optimisation améliorée, le résultat de certains calculs à virgule flottante peut différer de ceux produits par d’autres `/fp` options. Les valeurs spéciales (NaN, + Infinity,-Infinity,-0,0) peuvent ne pas être propagées ou se comporter de façon stricte en fonction de la norme IEEE-754. Les contractions à virgule flottante peuvent être générées sous `/fp:fast` . Le compilateur est toujours lié par l’architecture sous-jacente sous `/fp:fast` , et des optimisations supplémentaires peuvent être disponibles via l’utilisation de l’option [/ARCH](arch-minimum-cpu-architecture.md) .

Sous `/fp:fast` , le compilateur génère du code destiné à s’exécuter dans l’environnement à virgule flottante par défaut et suppose que l’environnement à virgule flottante n’est pas accessible ou modifié au moment de l’exécution. Autrement dit, il suppose que le code ne masque pas les exceptions à virgule flottante, ne lit ou n’écrit pas les registres d’État à virgule flottante, ni ne modifie les modes d’arrondi.

`/fp:fast` est destiné aux programmes qui ne nécessitent pas un classement et un arrondi de code source stricts des expressions à virgule flottante, et ne s’appuient pas sur les règles standard pour gérer des valeurs spéciales telles que NaN. Si votre code à virgule flottante requiert la préservation du classement et de l’arrondi du code source, ou s’appuie sur le comportement standard des valeurs spéciales, utilisez [/FP : precise](#precise). Si votre code accède à l’environnement à virgule flottante ou le modifie pour modifier les modes d’arrondi, afficher les exceptions à virgule flottante ou vérifier l’état de la virgule flottante, utilisez [/FP : strict](#strict).

#### <a name="except"></a>mais

L' `/fp:except` option génère du code pour s’assurer que toutes les exceptions de virgule flottante non masquées sont déclenchées au point exact où elles se produisent, et qu’aucune exception de virgule flottante supplémentaire n’est levée. Par défaut, l' `/fp:strict` option active `/fp:except` , et `/fp:precise` non. L' `/fp:except` option n’est pas compatible avec `/fp:fast` . L’option peut être explicitement désactivée par nous `/fp:except-` .

Notez que `/fp:except` ne permet pas d’effectuer des exceptions à virgule flottante en soi, mais il est requis pour que les programmes activent les exceptions de virgule flottante. Pour plus d’informations sur l’activation des exceptions de virgule flottante, consultez [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) .

## <a name="remarks"></a>Remarques

Plusieurs `/fp` options peuvent être spécifiées dans la même ligne de commande du compilateur. Une seule des `/fp:strict` `/fp:fast` options, et `/fp:precise` peut être appliquée à la fois. Si plusieurs de ces options sont spécifiées sur la ligne de commande, l’option la plus récente est prioritaire et le compilateur génère un avertissement. Les `/fp:strict` options et ne `/fp:except` sont pas compatibles avec `/clr` .

L’option [/za](za-ze-disable-language-extensions.md) (compatibilité ANSI) n’est pas compatible avec `/fp` .

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Utilisation de directives de compilateur pour contrôler le comportement à virgule flottante

Le compilateur fournit trois directives pragma pour remplacer le comportement à virgule flottante spécifié sur la ligne de commande : [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)et [fp_contract](../../preprocessor/fp-contract.md). Vous pouvez utiliser ces directives pour contrôler le comportement à virgule flottante au niveau de la fonction, et non dans une fonction. Notez que ces directives ne correspondent pas directement aux `/fp` options. Ce tableau montre comment les `/fp` directives de pragma et les options sont mappées entre elles. Pour plus d’informations, consultez la documentation relative aux options individuelles et aux directives pragma.

| Option | float_control (précision) | float_control (sauf) | fenv_access | fp_contract |
|-|-|-|-|-|
|`/fp:fast`|arrêt|arrêt|arrêt|on|
|`/fp:precise`|sur|arrêt|arrêt|on|
|`/fp:strict`|on|on|sur|arrêt|

### <a name="the-default-floating-point-environment"></a>Environnement à virgule flottante par défaut

Quand un processus est initialisé, l' *environnement à virgule flottante par défaut* est défini. Cet environnement masque toutes les exceptions à virgule flottante, définit le mode d’arrondi sur arrondi à la valeur la plus proche ( `FE_TONEAREST` ), conserve les valeurs subnormal (dénormal), utilise la précision par défaut de mantisse (mantisse) pour les **`float`** **`double`** valeurs, et **`long double`** , et où est pris en charge, définit le contrôle infini sur le mode affin par défaut.

### <a name="floating-point-environment-access-and-modification"></a>Accès et modification de l’environnement à virgule flottante

Le runtime Microsoft Visual C++ fournit plusieurs fonctions permettant d’accéder à l’environnement à virgule flottante et de le modifier. Celles-ci incluent [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)et [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) et leurs variantes. Pour garantir un comportement correct du programme lorsque votre code accède à l’environnement à virgule flottante ou le modifie, `fenv_access` doit être activé, soit par l’option, soit `/fp:strict` par l’utilisation du `fenv_access` pragma, pour que ces fonctions aient un effet. Lorsque `fenv_access` n’est pas activé, l’accès ou la modification de l’environnement à virgule flottante peut entraîner un comportement inattendu du programme : le code ne peut pas honorer les modifications demandées dans l’environnement à virgule flottante ; les registres d’État à virgule flottante peuvent ne pas signaler les résultats attendus ou les résultats actuels, et les exceptions de virgule flottante inattendues peuvent ne pas se

Lorsque votre code accède à l’environnement à virgule flottante ou le modifie, vous devez faire attention lorsque vous combinez du code où `fenv_access` est activé avec du code qui n’est pas `fenv_access` activé. Dans le code où `fenv_access` n’est pas activé, le compilateur suppose que l’environnement à virgule flottante par défaut de la plateforme est activé et que l’état de la virgule flottante n’est pas accessible ou modifié. Nous vous recommandons d’enregistrer et de restaurer l’environnement à virgule flottante local à son état par défaut avant que le contrôle soit transféré à une fonction qui n’a pas `fenv_access` activé. Cet exemple montre comment le `float_control` pragma peut être défini et restauré :

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Modes d’arrondi à virgule flottante

Sous `/fp:precise` et, `/fp:fast` le compilateur génère du code destiné à s’exécuter dans l’environnement à virgule flottante par défaut et suppose que l’environnement n’est pas accessible ou modifié au moment de l’exécution. Autrement dit, il suppose que le code ne masque pas les exceptions à virgule flottante, ne lit ou n’écrit pas les registres d’État à virgule flottante, ni ne modifie les modes d’arrondi.  Toutefois, certains programmes doivent modifier l’environnement à virgule flottante. Par exemple, cet exemple calcule les limites d’erreur d’une multiplication à virgule flottante en modifiant les modes d’arrondi à virgule flottante :

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

Dans la mesure où le compilateur suppose l’environnement à virgule flottante par défaut sous `/fp:fast` et `/fp:precise` il est libre d’ignorer les appels à `_controlfp_s` . Par exemple, lorsqu’elles sont compilées à l’aide de `/O2` et `/fp:precise` pour l’architecture x86, les limites ne sont pas calculées et l’exemple de programme génère :

```Output
cLower = -inf
cUpper = -inf
```

En cas de compilation avec `/O2` et `/fp:strict` pour l’architecture x86, l’exemple de programme génère :

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Valeurs spéciales à virgule flottante

Sous `/fp:precise` et `/fp:strict` , les expressions qui impliquent des valeurs spéciales (NaN, + Infinity,-Infinity,-0,0) se comportent selon les spécifications IEEE-754. Sous `/fp:fast` , le comportement de ces valeurs spéciales peut être incohérent avec IEEE-754.

Cet exemple illustre le comportement différent des valeurs spéciales sous `/fp:precise` , `/fp:strict` et `/fp:fast` :

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

En cas de compilation avec `/O2` `/fp:precise` ou `/O2` `/fp:strict` pour l’architecture x86, les sorties sont cohérentes avec la spécification IEEE-754 :

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Lorsqu’elles sont compilées avec `/O2` `/fp:fast` pour l’architecture x86, les sorties ne sont pas cohérentes avec IEEE-754 :

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Transformations algébriques à virgule flottante

Sous `/fp:precise` et `/fp:strict` , le compilateur n’effectue pas de transformations mathématiques, sauf si la transformation est garantie pour produire un résultat identique au niveau du bit. Le compilateur peut effectuer ces transformations sous `/fp:fast` . Par exemple, l’expression `a * b + a * c` dans l’exemple de fonction `algebraic_transformation` peut être compilée en `a * (b + c)` sous `/fp:fast` . Ces transformations ne sont pas effectuées sous `/fp:precise` ou `/fp:strict` , et le compilateur génère `a * b + a * c` .

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Points de cast explicites à virgule flottante

Sous `/fp:precise` et `/fp:strict` , le compilateur arrondit à la précision du code source à quatre points spécifiques pendant l’évaluation de l’expression : au niveau des assignations, à conversions, lorsqu’un argument à virgule flottante est passé à un appel de fonction, et lorsqu’une valeur à virgule flottante est retournée à partir d’un appel de fonction. Conversions peut être utilisé pour arrondir explicitement des calculs intermédiaires. Sous `/fp:fast` , le compilateur ne génère pas de casts explicites à ces points pour garantir la précision du code source. Cet exemple illustre le comportement sous différentes `/fp` Options :

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

En cas de compilation à l’aide `/O2` `/fp:precise` de ou de `/O2` `/fp:strict` , vous pouvez voir que les casts de type explicite sont insérés à la fois sur la conversion et sur le point de retour de fonction dans le code généré pour l’architecture x64 :

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

`/O2` `/fp:fast` Le code généré est simplifié, car tous les casts de type sont optimisés :

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  **C/C++**  >  **génération de code** .

1. Modifiez la propriété de **modèle à virgule flottante** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
