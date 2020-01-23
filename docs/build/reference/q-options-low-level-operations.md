---
title: /Q (Opérations de bas niveau), options
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 9dd3675f200be4f0ec66620bcf3cf05706991b66
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518168"
---
# <a name="q-options-low-level-operations"></a>/Q (Opérations de bas niveau), options

Vous pouvez utiliser les options du compilateur **/q** pour effectuer les opérations de compilateur de bas niveau suivantes :

- [/Qfast_transcendentals (Force Fast fonctions transcendantes rapides)](qfast-transcendentals-force-fast-transcendentals.md): génère des fonctions transcendantes rapides rapides.

- [/QIfist (supprimer _ftol)](qifist-suppress-ftol.md): supprime les `_ftol` lorsqu’une conversion d’un type à virgule flottante en type entier est requise (x86 uniquement).

- [/Qimprecise_fwaits (supprimer fwaits à l’intérieur des blocs try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): supprime les commandes `fwait` à l’intérieur des blocs `try`.

- [/QIntel-JCC-Erratum](qintel-jcc-erratum.md): atténue l’impact sur les performances causé par la mise à jour de microcode vérification du défaut de la CMC (Jump ConditionalAttribute code).

- [/QPAR (auto-paralléliseur)](qpar-auto-parallelizer.md): active la parallélisation automatique des boucles marquées avec la directive [#pragma Loop ()](../../preprocessor/loop.md) .

- [/QPAR-Report (niveau de rapport paralléliseur automatique)](qpar-report-auto-parallelizer-reporting-level.md): active les niveaux de création de rapports pour la parallélisation automatique.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): supprime les optimisations pour les chargements de registres à virgule flottante et pour les déplacements entre la mémoire et les registres MMX.

- [/Qspectre](qspectre.md): génère des instructions pour limiter certaines vulnérabilités de sécurité spectre.

- [/Qvec-Report (niveau de rapport Vectoriseur automatique)](qvec-report-auto-vectorizer-reporting-level.md): active les niveaux de création de rapports pour la vectorisation automatique.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
