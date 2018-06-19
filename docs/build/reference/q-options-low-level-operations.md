---
title: Options de -Q (opérations de bas niveau) | Documents Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a18c5d790cf21e8eb130a2b2baa152e20d79a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375033"
---
# <a name="q-options-low-level-operations"></a>/Q (Opérations de bas niveau), options

Vous pouvez utiliser la **/Q** options du compilateur pour effectuer les opérations de compilateur de bas niveau suivantes :

- [/ Qfast_transcendentals (Force des fonctions transcendantes rapides)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): génère des fonctions transcendantes rapides.

- [/QIfist (Supprimer _ftol)](../../build/reference/qifist-suppress-ftol.md): supprime `_ftol` quand la conversion à partir d’un type à virgule flottante en type d’entier est requise (x86 uniquement).

- [/ Qimprecise_fwaits (Supprimer fwaits à l’intérieur des blocs Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): supprime `fwait` à l’intérieur des commandes `try` blocs.

- [/Qpar (PARALLÉLISEUR)](../../build/reference/qpar-auto-parallelizer.md): Active la parallélisation automatique des boucles marquées avec la [#pragma loop()](../../preprocessor/loop.md) la directive.

- [/ Qpar-report (niveau de Reporting PARALLÉLISEUR automatique)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): Active la parallélisation automatique des niveaux de création de rapports.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): supprime les optimisations de Registre à virgule flottante charge et pour les déplacements entre la mémoire et MMX inscrit.

- [/ Qspectre](../../build/reference/qspectre.md): génère des instructions pour atténuer certains des failles de sécurité Spectre.

- [/ Qvec-report (niveau de Reporting Vectoriseur automatique)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): Active les niveaux pour le vectorisation automatique de création de rapports.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
