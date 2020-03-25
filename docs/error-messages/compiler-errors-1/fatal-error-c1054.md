---
title: Erreur irrécupérable C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204462"
---
# <a name="fatal-error-c1054"></a>Erreur irrécupérable C1054

limite du compilateur : initialiseurs imbriqués trop profondément

Le code dépasse la limite d’imbrication des initialiseurs (10-15 niveaux, selon la combinaison de types initialisés).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifiez les types de données initialisés pour réduire l’imbrication.

1. Initialisez les variables dans des instructions distinctes après la déclaration.
