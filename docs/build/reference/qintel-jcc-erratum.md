---
title: /QIntel-jcc-erratum
description: Décrit l’option Microsoft CC++ /compiler (MSVC)/QIntel-JCC-Erratum.
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520878"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

L’option **/QIntel-JCC-Erratum** est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures.

::: moniker-end

::: moniker range=">=vs-2019"

Spécifie que le compilateur génère des instructions pour atténuer l’impact sur les performances provoqué par la mise à jour du microcode vérification du défaut d’Intel Jump ConditionalAttribute code (CMC) dans certains processeurs Intel.

## <a name="syntax"></a>Syntaxe

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Notes

Sous **/QIntel-JCC-Erratum**, le compilateur détecte les instructions de saut de saut et de macro-fusion qui se coupent ou se terminent sur une limite de 32 octets. Il aligne ces instructions sur la limite. Cette modification atténue l’impact sur les performances des mises à jour de microcode qui empêchent la vérification du défaut CMC dans certains processeurs Intel. Pour plus d’informations sur vérification du défaut, consultez [atténuations du saut de code conditionnel vérification du défaut](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) sur le site Web d’Intel.

L’option **/QIntel-JCC-Erratum** est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures. Cette option est disponible uniquement dans les compilateurs qui ciblent x86 et x64. L’option n’est pas disponible dans les compilateurs qui ciblent des processeurs ARM.

L’option **/QIntel-JCC-Erratum** est désactivée par défaut et fonctionne uniquement dans les builds optimisées. Cette option peut augmenter la taille du code.

**/QIntel-JCC-Erratum** est incompatible avec [/CLR](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez les **Propriétés de configuration** > page de propriétés de **génération de code** **C/C++**  >.

1. Sélectionnez une valeur pour la propriété activer l’atténuation de la vérification du défaut de la **CMC Intel** . Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)\
[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

::: moniker-end
