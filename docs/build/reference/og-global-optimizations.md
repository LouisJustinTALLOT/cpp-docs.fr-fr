---
title: /Og (Optimisations globales)
description: Décrit l’option/og du compilateur MSVC déconseillée, anciennement utilisée pour activer les optimisations globales.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: c1cab53ccb391bd7d6ca7660e2750f53aa7c72e4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180849"
---
# <a name="og-global-optimizations"></a>`/Og`(Optimisations globales)

Action déconseillée. Fournit des optimisations locales et globales, l’allocation automatique des registres et l’optimisation de la boucle. Nous vous recommandons d’utiliser à la place [ `/O1` (réduire la taille)](o1-o2-minimize-size-maximize-speed.md) ou [ `/O2` (maximiser la vitesse)](o1-o2-minimize-size-maximize-speed.md) .

## <a name="syntax"></a>Syntaxe

> **`/Og`**

## <a name="remarks"></a>Notes

**`/Og`** est déconseillé. Ces optimisations sont désormais activées par défaut lorsque des optimisations sont activées. Pour plus d’informations sur les optimisations, consultez [ `/O1` , `/O2` (réduire la taille, augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md)ou [ `/Ox` (activer la plupart des optimisations de vitesse)](ox-full-optimization.md).

Les optimisations suivantes sont disponibles sous **`/Og`** :

- Élimination de sous-expressions communes locales et globales

   Dans cette optimisation, la valeur d’une sous-expression commune est calculée une fois. Dans l’exemple suivant, si les valeurs de `b` et `c` ne changent pas entre les trois expressions, le compilateur peut assigner le calcul de `b + c` à une variable temporaire et utiliser cette variable pour `b + c` :

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Pour l’optimisation de sous-expression commune locale, le compilateur examine les courtes sections de code pour les sous-expressions communes. Pour l’optimisation globale commune sous-expression, le compilateur recherche des sous-expressions communes dans les fonctions entières.

- Allocation automatique des registres

   Cette optimisation permet au compilateur de stocker les variables et sous-expressions fréquemment utilisées dans les registres. le `register` mot clé est ignoré.

- Optimisation de la boucle

   Cette optimisation supprime les sous-expressions invariantes du corps d’une boucle. Une boucle optimale contient uniquement des expressions dont les valeurs changent à chaque exécution de la boucle. Dans l’exemple suivant, l’expression `x + y` ne change pas dans le corps de la boucle :

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Après l’optimisation, `x + y` est calculé une fois au lieu de chaque fois que la boucle est exécutée :

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   L’optimisation de la boucle est bien plus efficace lorsque le compilateur peut supposer qu’il n’y a pas d’alias, que vous définissez avec [`__restrict`](../../cpp/extension-restrict.md) , [`noalias`](../../cpp/noalias.md) ou [`restrict`](../../cpp/restrict.md) .

   > [!NOTE]
   > Vous pouvez activer ou désactiver l’optimisation globale sur une base fonction par fonction à l’aide du `optimize` pragma avec l' `g` option.

Pour obtenir des informations connexes, consultez [ `/Oi` (générer des fonctions intrinsèques)](oi-generate-intrinsic-functions.md) et [ `/Ox ` (activer la plupart des optimisations de vitesse)](ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
