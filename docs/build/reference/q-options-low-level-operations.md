---
title: /Q (Opérations de bas niveau), options
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 722a63a43e5e08fe80b26f908c7ae92df2fdb29c
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034517"
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

- [/Qspectre-Load](qspectre-load.md): génère des instructions pour atténuer les vulnérabilités de sécurité spectre en fonction des charges.

- [/Qspectre-Load-CF](qspectre-load-cf.md): génère des instructions pour atténuer les vulnérabilités de sécurité spectre en fonction des instructions de workflow de contrôle qui sont chargées.

- [/Qvec-Report (niveau de rapport Vectoriseur automatique)](qvec-report-auto-vectorizer-reporting-level.md): active les niveaux de création de rapports pour la vectorisation automatique.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
