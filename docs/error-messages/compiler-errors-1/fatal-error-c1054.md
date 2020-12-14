---
description: 'En savoir plus sur : erreur irrécupérable C1054'
title: Erreur irrécupérable C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 1bfe8718fcb0d3edb172f0f5a89bb2f479e56137
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251659"
---
# <a name="fatal-error-c1054"></a>Erreur irrécupérable C1054

limite du compilateur : initialiseurs imbriqués trop profondément

Le code dépasse la limite d’imbrication des initialiseurs (10-15 niveaux, selon la combinaison de types initialisés).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifiez les types de données initialisés pour réduire l’imbrication.

1. Initialisez les variables dans des instructions distinctes après la déclaration.
