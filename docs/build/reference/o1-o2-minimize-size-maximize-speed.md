---
title: /O1, /O2 (Réduire la taille, augmenter la vitesse)
description: Les options du compilateur MSVC/O1 et/O2 spécifient toutes les optimisations pour la taille minimale ou maximale.
ms.date: 07/08/2020
f1_keywords:
- /O2
- /O1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: c1eda8395e604468cbb23572ec930d6171984fe4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180901"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>`/O1`, `/O2` (Réduire la taille, augmenter la vitesse)

Sélectionne un ensemble prédéfini d’options qui affectent la taille et la vitesse du code généré.

## <a name="syntax"></a>Syntaxe

> **`/O1`**\
> **`/O2`**

## <a name="remarks"></a>Notes

Les **`/O1`** **`/O2`** Options du compilateur et constituent un moyen rapide de définir plusieurs options d’optimisation spécifiques à la fois. L' **`/O1`** option définit les options d’optimisation individuelles qui créent le plus petit code dans la majorité des cas. L' **`/O2`** option définit les options qui créent le code le plus rapide dans la majorité des cas. L' **`/O2`** option est la valeur par défaut pour les versions release. Ce tableau montre les options spécifiques qui sont définies par **`/O1`** et **`/O2`** :

| Option | Équivalent à |
|--|--|
| **`/O1`**(Réduire la taille) | [`/Og`](og-global-optimizations.md) [`/Os`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |
| **`/O2`**(Maximiser la vitesse) | [`/Og`](og-global-optimizations.md) [`/Oi`](oi-generate-intrinsic-functions.md) [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |

**`/O1`** et **`/O2`** s’excluent mutuellement.

> [!NOTE]
> **spécifique à x86**\
> Ces options impliquent l’utilisation de l’option d’omission du pointeur de frame ( [`/Oy`](oy-frame-pointer-omission.md) ).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation des **Propriétés de configuration**  >  **C/C++**  >  **Optimization** .

1. Modifiez la propriété **Optimization** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[`/O`options (optimiser le code)](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[`/EH`(Modèle de gestion des exceptions)](eh-exception-handling-model.md)
