---
title: /Q (Opérations de bas niveau), options
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514251"
---
# <a name="q-options-low-level-operations"></a>/Q (Opérations de bas niveau), options

Vous pouvez utiliser la **/Q** options du compilateur pour effectuer les opérations de bas niveau de compilateur suivantes :

- [/ Qfast_transcendentals (Force des fonctions transcendantes rapides)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): génère des fonctions transcendantes rapides.

- [/QIfist (Supprimer _ftol)](../../build/reference/qifist-suppress-ftol.md): supprime `_ftol` lorsque la conversion d’un type à virgule flottante vers un type entier est requis (x86 uniquement).

- [/ Qimprecise_fwaits (Supprimer fwaits dans des blocs Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): supprime `fwait` à l’intérieur des commandes `try` blocs.

- [/Qpar (PARALLÉLISEUR)](../../build/reference/qpar-auto-parallelizer.md): Active la parallélisation automatique des boucles marquées avec la [#pragma loop()](../../preprocessor/loop.md) directive.

- [/ Qpar-report (niveau de rapport du PARALLÉLISEUR automatique)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): Active la parallélisation automatique des niveaux de création de rapports.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): supprime les optimisations à virgule flottante register charge et pour les déplacements entre la mémoire et MMX inscrit.

- [/Qspectre](../../build/reference/qspectre.md): génère des instructions pour atténuer certaines vulnérabilités de sécurité du Spectre.

- [/ Qvec-report (niveau de rapport du Vectoriseur automatique)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): Active les niveaux de la vectorisation automatique de création de rapports.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
