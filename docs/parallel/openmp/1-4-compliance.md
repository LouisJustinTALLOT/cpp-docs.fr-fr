---
title: 1.4 Conformité
ms.date: 11/04/2016
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
ms.openlocfilehash: 7fb47c9989e971e10701c2ee2bd7ac7823141812
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642453"
---
# <a name="14-compliance"></a>1.4 Conformité

Une implémentation de l’API C/C++ OpenMP est *compatibles OpenMP* si il reconnaît et conserve la sémantique de tous les éléments de cette spécification, tels que définis dans les chapitres 1, 2, 3, 4, et concernent l’annexe C. annexes A, B, D, E et F informations uniquement et ne font pas partie de la spécification. Les implémentations qui incluent uniquement un sous-ensemble de l’API ne sont pas compatibles avec OpenMP.

Les API C++ OpenMP C est une extension à la langue de base qui est pris en charge par une implémentation. Si la langue de base ne prend pas en charge une construction de langage ou une extension qui s’affiche dans ce document, l’implémentation d’OpenMP n’est pas obligée de prendre en charge.

Toutes les fonctions de bibliothèque standard C et C++ et les fonctions intégrées (autrement dit, les fonctions dont le compilateur connaît le spécifique) doit être thread-safe. Non synchronisé l’utilisation des fonctions de thread-safe par différents threads à l’intérieur d’une région parallèle ne produit pas un comportement non défini. Toutefois, le comportement peut-être pas les mêmes que dans une région de série. (Une fonction de génération de nombres aléatoires est un exemple.)

L’API C/C++ OpenMP Spécifie que certains comportements est *défini par l’implémentation.* Une implémentation conforme de OpenMP est nécessaire pour définir et documenter son comportement dans ces cas. Consultez [annexe E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), 97, pour obtenir la liste de comportements définis par l’implémentation de la page.