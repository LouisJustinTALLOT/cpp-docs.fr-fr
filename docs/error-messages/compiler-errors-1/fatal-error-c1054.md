---
title: Erreur irrécupérable C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569197"
---
# <a name="fatal-error-c1054"></a>Erreur irrécupérable C1054

limite du compilateur : initialiseurs imbriqués trop profondément

Le code dépasse la limite d’imbrication des initialiseurs (10-15 niveaux, selon la combinaison de types en cours d’initialisation).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifiez les types de données en cours d’initialisation pour réduire l’imbrication.

1. Initialiser des variables dans des instructions distinctes après la déclaration.