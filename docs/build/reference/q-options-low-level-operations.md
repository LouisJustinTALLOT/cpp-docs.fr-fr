---
title: /Q (Opérations de bas niveau), options
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819907"
---
# <a name="q-options-low-level-operations"></a>/Q (Opérations de bas niveau), options

Vous pouvez utiliser la **/Q** options du compilateur pour effectuer les opérations de bas niveau de compilateur suivantes :

- [/ Qfast_transcendentals (Force des fonctions transcendantes rapides)](qfast-transcendentals-force-fast-transcendentals.md): Génère des fonctions transcendantes rapides.

- [/QIfist (Supprimer _ftol)](qifist-suppress-ftol.md): Supprime `_ftol` lorsque la conversion d’un type à virgule flottante vers un type entier est requis (x86 uniquement).

- [/ Qimprecise_fwaits (Supprimer fwaits dans des blocs Try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Supprime les commandes `fwait` dans les blocs `try` .

- [/Qpar (PARALLÉLISEUR)](qpar-auto-parallelizer.md): Active la parallélisation automatique des boucles marquées avec la directive [#pragma loop()](../../preprocessor/loop.md) .

- [/ Qpar-report (rapport du PARALLÉLISEUR automatique niveau)](qpar-report-auto-parallelizer-reporting-level.md): Active les niveaux de création de rapports pour la parallélisation automatique.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Supprime les optimisations pour les charges de Registre à virgule flottante et pour les déplacements entre la mémoire et les registres MMX.

- [/Qspectre](qspectre.md): Génère des instructions pour atténuer certaines vulnérabilités de sécurité du Spectre.

- [/ Qvec-report (Vectoriseur niveau de rapport)](qvec-report-auto-vectorizer-reporting-level.md): Active les niveaux de création de rapports pour le vectorisation automatique.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
