---
title: /Q (Opérations de bas niveau), options
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927671"
---
# <a name="q-options-low-level-operations"></a>/Q (Opérations de bas niveau), options

Vous pouvez utiliser les options du compilateur **/q** pour effectuer les opérations de compilateur de bas niveau suivantes :

- [/Qfast_transcendentals (Force Fast fonctions transcendantes rapides)](qfast-transcendentals-force-fast-transcendentals.md): Génère des fonctions transcendantes rapides.

- [/QIfist (supprimer _ ftol)](qifist-suppress-ftol.md): `_ftol` Supprime lorsqu’une conversion d’un type à virgule flottante en type entier est requise (x86 uniquement).

- [/Qimprecise_fwaits (supprimer fwaits à l’intérieur des blocs try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Supprime les commandes `fwait` dans les blocs `try` .

- [/QPAR (auto-paralléliseur)](qpar-auto-parallelizer.md): Active la parallélisation automatique des boucles marquées avec la directive [#pragma loop()](../../preprocessor/loop.md) .

- [/QPAR-Report (niveau de rapport du paralléliseur automatique)](qpar-report-auto-parallelizer-reporting-level.md): Active les niveaux de création de rapports pour la parallélisation automatique.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Supprime les optimisations pour les chargements de registres à virgule flottante et pour les déplacements entre la mémoire et les registres MMX.

- [/Qspectre](qspectre.md): Génère des instructions pour limiter certaines vulnérabilités de sécurité spectre.

- [/Qvec-Report (niveau de rapport du Vectoriseur automatique)](qvec-report-auto-vectorizer-reporting-level.md): Active les niveaux de création de rapports pour le vectorisation automatique.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
