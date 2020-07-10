---
title: /Ox (activer la plupart des optimisations de vitesse)
description: L’option MSVC/Ox associe certaines des options d’optimisation du compilateur pour la vitesse dans une seule option.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 10893fe1cf032f2ab56f27aa4af95b050c2ec37e
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180836"
---
# <a name="ox-enable-most-speed-optimizations"></a>`/Ox`(Activer la plupart des optimisations de vitesse)

L' **`/Ox`** option de compilateur active une combinaison d’optimisations qui favorisent la vitesse. Dans certaines versions de l’IDE de Visual Studio et du message d’aide du compilateur, il s’agit d’une *optimisation complète*, mais l' **`/Ox`** option du compilateur active uniquement un sous-ensemble des options d’optimisation de la vitesse activées par **`/O2`** .

## <a name="syntax"></a>Syntaxe

> **`/Ox`**

## <a name="remarks"></a>Notes

L' **`/Ox`** option du compilateur active les **`/O`** Options du compilateur qui privilégient la vitesse. L' **`/Ox`** option de compilateur n’inclut pas les options supplémentaires [ `/GF` (éliminer les chaînes dupliquées)](gf-eliminate-duplicate-strings.md) et [ `/Gy` (activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md) activées par [ `/O1` ou `/O2` (réduire la taille, augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md). Les options supplémentaires appliquées par **`/O1`** et **`/O2`** peuvent provoquer des pointeurs vers des chaînes ou des fonctions pour partager une adresse cible, ce qui peut affecter le débogage et la conformité stricte au langage. L' **`/Ox`** option est un moyen simple d’activer la plupart des optimisations sans inclure **`/GF`** et **`/Gy`** . Pour plus d’informations, consultez les descriptions des [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) options et.

L' **`/Ox`** option de compilateur est la même que celle utilisée pour combiner les options suivantes :

- [ `/Ob` (Expansion des fonctions inline)](ob-inline-function-expansion.md), où le paramètre d’option est 2 ( **`/Ob2`** )

- [`/Oi`(Générer des fonctions intrinsèques)](oi-generate-intrinsic-functions.md)

- [`/Ot`(Favoriser la rapidité du code)](os-ot-favor-small-code-favor-fast-code.md)

- [`/Oy`(Omission du pointeur de frame)](oy-frame-pointer-omission.md)

**`/Ox`** s’exclut mutuellement de :

- [`/O1`(Réduire la taille)](o1-o2-minimize-size-maximize-speed.md)

- [`/O2`(Maximiser la vitesse)](o1-o2-minimize-size-maximize-speed.md)

- [`/Od`(Désactiver (débogage))](od-disable-debug.md)

Vous pouvez annuler le décalage vers la vitesse de l' **`/Ox`** option du compilateur si vous spécifiez **`/Oxs`** , qui combine l' **`/Ox`** option du compilateur avec [ `/Os` (favoriser la taille du code)](os-ot-favor-small-code-favor-fast-code.md). Les options combinées favorisent une plus petite taille de code.  L' **`/Oxs`** option est exactement la même que la spécification **`/Ox`** **`/Os`** du moment où les options s’affichent dans cet ordre.

Pour appliquer toutes les optimisations de niveau fichier disponibles pour les versions release, nous vous recommandons de spécifier [ `/O2` (maximiser la vitesse)](o1-o2-minimize-size-maximize-speed.md) au lieu de **`/Ox`** et [ `/O1` (réduire la taille)](o1-o2-minimize-size-maximize-speed.md) au lieu de **`/Oxs`** . Pour une meilleure optimisation des versions release, pensez également à l’option du compilateur [ `/GL` (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md) et à l’option de l’éditeur de liens ( [ `/LTCG` génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation des **Propriétés de configuration**  >  **C/C++**  >  **Optimization** .

1. Modifiez la propriété **Optimization** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[`/O`Options (optimiser le code)](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
