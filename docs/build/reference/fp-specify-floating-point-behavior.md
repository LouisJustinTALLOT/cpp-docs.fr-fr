---
title: -fp (spécifier le comportement de virgule flottante) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs:
- C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 520a6e2d675c55e47a0424ab93c6a76d521f2358
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422691"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Spécifier le comportement de virgule flottante)

Spécifie le comportement de la virgule flottante dans un fichier de code source.

## <a name="syntax"></a>Syntaxe

> **/ fp :**[**précise** | **sauf**[**-**] | **rapide** | **strict**]

### <a name="arguments"></a>Arguments

#### <a name="precise"></a>Précis

La valeur par défaut **/FP** est **/fp : precise**.

Le **/fp : precise** indicateur améliore la cohérence des tests en virgule flottante pour l’égalité et d’inégalité en désactivant les optimisations qui peuvent changer la précision des calculs à virgule flottante. (Le maintien d'une précision spécifique est requis pour des raisons de conformité stricte à la norme ANSI.) Par défaut, dans le code pour x86 architectures que x87 coprocesseur fournies, le compilateur utilise le coprocesseur de 80 bits registres pour stocker les résultats intermédiaires des calculs en virgule flottante. Cette approche augmente la vitesse du programme tout en diminuant sa taille. Cependant, dans la mesure où le calcul implique des types de données à virgule flottante qui sont représentés en mémoire sur moins de 80 bits, le fait de faire subir aux bits supplémentaires de précision (80 bits moins le nombre de bits dans un type à virgule flottante plus petit) un long calcul peut donner lieu à des résultats incohérents.

Avec **/fp : precise** sur x86 processeurs, le compilateur arrondit les variables de type `float` à la précision correcte pour les assignations et les casts et lorsque les paramètres sont passés à une fonction. Cet arrondi permet de garantir que les données ne conserveront pas une importance supérieure à la capacité de leur type. Un programme compilé avec **/fp : précise** peut être plus lent et plus volumineux qu’un compilé sans **/fp : precise**. **/ fp : precise** désactive les intrinsèques ; la bibliothèque runtime standard routines sont utilisés à la place. Pour plus d’informations, consultez l’article [/Oi (Générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md).

Le comportement de virgule flottante suivant est activé avec **/fp : precise**:

- Contractions, à savoir l'utilisation d'une opération composite qui a un seul arrondi à la fin pour remplacer plusieurs opérations.

- Les optimisations d'expression qui ne sont pas valides pour des valeurs spéciales (NaN, +infini, -infini, +0, -0) ne sont pas autorisées. L’optimisations x-x = > 0, x * 0 = > 0, x-0 = > x, x + 0 = > x et 0-x = > - x ne sont pas valides pour diverses raisons. (Consultez la documentation relative aux normes IEEE 754 et C99.)

- Le compilateur gère correctement les comparaisons qui impliquent NaN. Par exemple, x ! = x prend la valeur de **true** si `x` est une valeur NaN et les comparaisons ordonnées qui impliquent NaN lèvent une exception.

- L'évaluation d'expression respecte FLT_EVAL_METHOD=2 de la norme C99, sauf que lorsque vous programmez pour des processeurs x86, il s'agit d'une précision long double, car le FPU est défini à une précision de 53 bits.

- La multiplication par 1.0 exactement est transformée en utilisation de l'autre facteur. x * y\*1.0 est transformé en x\*y. De même, x\*1.0\*y est transformé en x\*y.

- La division par 1.0 exactement est transformée en utilisation du dividende. x * y/1.0 est transformé en x\*y. De même, x / 1.0\*y est transformé en x\*y.

À l’aide de **/fp : precise** lorsque [fenv_access](../../preprocessor/fenv-access.md) se trouve sur désactive les optimisations telles que des évaluations de la compilation d’expressions à virgule flottante. Par exemple, si vous utilisez [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) pour modifier le mode d’arrondi et le compilateur effectue un calcul en virgule flottante, le mode d’arrondi spécifié n’est pas activée, sauf si `fenv_access`a la valeur ON.

**/ fp : precise** remplace le **/Op** option du compilateur.

#### <a name="fast"></a>Le traitement rapide

Le **Fast** option crée le code le plus rapide dans la plupart des cas en assouplissant les règles pour optimiser les opérations à virgule flottante. Cela permet au compilateur d'optimiser le code à virgule flottante en matière de vitesse au détriment de la précision. Lorsque **Fast** est spécifié, le compilateur ne peut pas arrondir correctement instructions d’assignation, conversions de type, ou les appels de fonction et ne peut pas effectuer d’arrondi des expressions intermédiaires. Le compilateur peut réorganiser des opérations ou effectuer des transformations algébriques, par exemple en suivant les règles associatives et distributives, sans tenir compte de leur effet sur la précision finie des résultats. Le compilateur peut changer les opérations et les opérandes en simple précision au lieu de suivre les règles de promotion de type C++. Floating-point-spécifiques contraction optimisations sont toujours activées ([fp_contract](../../preprocessor/fp-contract.md) a la valeur ON). Exceptions de virgule flottante et l’accès à l’environnement FPU sont désactivées (**/fp : à l’exception de-** est implicite et [fenv_access](../../preprocessor/fenv-access.md) a la valeur OFF).

**Fast** ne peut pas être utilisé avec **/fp : strict** ou **/fp : precise**. La dernière option spécifiée sur la ligne de commande est utilisée. Le fait de spécifier **Fast** et **/fp : sauf** génère une erreur du compilateur.

Spécification de [/Za, /Ze (désactiver les Extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md) (compatibilité ANSI) et **Fast** peuvent provoquer un comportement inattendu. Par exemple, les opérations à virgule flottante à simple précision ne peuvent pas être arrondies à la simple précision.

#### <a name="except"></a>À l’exception

Le **/fp : sauf** option permet à un modèle de virgule flottante fiable. Les exceptions sont levées aussitôt après leur déclenchement. Cette option est désactivée par défaut. L’ajout d’un signe moins à l’option (**/fp : à l’exception de-**) désactive explicitement.

#### <a name="strict"></a>strict

Le **/fp : strict** option active le modèle de virgule flottante plus strict. **/ fp : strict** entraîne [fp_contract](../../preprocessor/fp-contract.md) OFF et [fenv_access](../../preprocessor/fenv-access.md) on. **/ fp : sauf** est implicite et peut être désactivée en spécifiant explicitement **/fp : à l’exception de-**. Lorsqu’il est utilisé avec **/fp : à l’exception de-**, **/fp : strict** applique une sémantique à virgule flottante stricte, mais sans tenir compte des événements exceptionnels.

## <a name="remarks"></a>Notes

Plusieurs **/FP** options peuvent être spécifiées dans la même compilation.

Pour contrôler le comportement de virgule flottante par fonction, consultez le [float_control](../../preprocessor/float-control.md) pragma. Cela remplace le **/FP** paramètre du compilateur. Nous vous conseillons d'enregistrer et de restaurer le comportement local en matière de virgule flottante :

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

La plupart des optimisations à virgule flottante liées à **/fp : strict**, **/fp : sauf** (et aux pragmas correspondants) et le `fp_contract` pragma sont dépendantes de l’ordinateur. **/ fp : strict** et **/fp : sauf** ne sont pas compatibles avec **/CLR**.

**/ fp : precise** doit répondre à la plupart des exigences à virgule flottante d’une application. Vous pouvez utiliser **/fp : sauf** et **/fp : strict**, mais il peut y avoir une baisse des performances. Si les performances sont plus importantes, songez à utiliser **Fast**.

**/ fp : strict**, **Fast**, et **/fp : precise** sont des modes de précision (exactitude). Une seule de ces options peut être active à la fois. Si les deux **/fp : strict** et **/fp : precise** sont spécifiés, le compilateur utilise celui qu’il traite en dernier. Les deux **/fp : strict** et **Fast** ne peut pas être spécifié.

Pour plus d’informations, consultez [Microsoft Visual C++ à virgule flottante optimisation](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **propriétés de Configuration** > **C/C++** > **génération de Code** page de propriétés.

1. Modifier la **modèle de virgule flottante** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur](compiler-options.md)
- [Définition des options du compilateur](setting-compiler-options.md)
- [Microsoft Visual C++ flottante Point optimisation](floating-point-optimization.md)