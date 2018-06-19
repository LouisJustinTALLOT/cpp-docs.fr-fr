---
title: -Og (optimisations globales) | Documents Microsoft
ms.custom: ''
ms.date: 09/22/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs:
- C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ef87f31e478bfbc8691b7e678186dd1a0621e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377155"
---
# <a name="og-global-optimizations"></a>/Og (Optimisations globales)

Obsolète. Fournit des optimisations locales et globales, une allocation automatique de registres et l’optimisation des boucles. Nous vous recommandons d’utiliser soit [/O1 (réduire la taille)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ou [/O2 (augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) à la place.

## <a name="syntax"></a>Syntaxe

> /Og

## <a name="remarks"></a>Notes

**/Og** est déconseillée. Ces optimisations sont désormais généralement activées par défaut. Pour plus d’informations sur les optimisations, consultez [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ou [/Ox (activer plus vitesse optimisations)](../../build/reference/ox-full-optimization.md).

Les optimisations suivantes sont disponibles sous **/Og**:

- Élimination de sous-expressions communes locales et globales

     Dans cette optimisation, la valeur d’une sous-expression commune est calculée une fois. Dans l’exemple suivant, si les valeurs de `b` et `c` ne changent pas entre les trois expressions, le compilateur peut assigner le calcul de `b + c` à une variable temporaire et substituer la variable à `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     Pour une optimisation de sous-expressions communes locales, le compilateur examine courtes sections de code de sous-expressions communes. Pour une optimisation de sous-expressions communes globales, le compilateur recherche des fonctions entières sous-expressions communes.

- Allocation automatique de registres

     Cette optimisation permet au compilateur de variables du magasin fréquemment utilisé et les sous-expressions dans les registres ; le `register` mot clé est ignoré.

- Optimisation de la boucle

     Cette optimisation supprime les sous-expressions de type invariant dans le corps d’une boucle. Une boucle optimale contient uniquement des expressions dont les valeurs changent à chaque exécution de la boucle. Dans l’exemple suivant, l’expression `x + y` ne change pas dans le corps de la boucle :

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

     Après l’optimisation, `x + y` est calculée une fois au lieu de chaque fois que la boucle est exécutée :

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

     Optimisation de la boucle est beaucoup plus efficace lorsque le compilateur ne peut prendre aucune attribution d’alias, que vous définissez avec [__restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), ou [restreindre](../../cpp/restrict.md).

    > [!NOTE]
    > Vous pouvez activer ou désactiver l’optimisation globale sur une fonction par fonction à l’aide de la `optimize` pragma avec la `g` option.

 Pour plus d’informations, consultez [/Oi (générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md) et [/Ox (activer plus vitesse optimisations)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)

[Options du compilateur](../../build/reference/compiler-options.md)

[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)