---
description: 'En savoir plus sur : remplacement d’une fonction virtuelle'
title: Remplacer une fonction virtuelle
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: d4c800006d5227ed5397c17284c03968a24a3964
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335913"
---
# <a name="override-a-virtual-function"></a>Remplacer une fonction virtuelle

Vous pouvez remplacer des fonctions virtuelles définies dans une classe de base à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) de Visual Studio.

**Pour remplacer une fonction virtuelle dans l’Fenêtre Propriétés :**

1. Dans Affichage de classes, sélectionnez la classe.

1. Dans la fenêtre Propriétés, sélectionnez le bouton **Remplacements**.

   > [!NOTE]
   > Le bouton **Remplacements** est disponible quand vous sélectionnez le nom de la classe dans Affichage de classes ou dans la fenêtre source.

   La colonne de gauche liste les fonctions virtuelles. Si le nom d’une fonction virtuelle apparaît également dans la colonne de droite, un remplacement a déjà été implémenté.

1. Si la fonction n’a pas de remplacement, sélectionnez la cellule dans la colonne de droite de la Fenêtre Propriétés pour afficher le nom suggéré de la substitution de fonction en tant que \<add> *funcname*.

1. Sélectionnez le nom suggéré pour ajouter du code stub pour la fonction.

1. Pour modifier une fonction de remplacement, double-cliquez sur le nom de la fonction dans Affichage de classes et modifiez le code dans la fenêtre source.

Pour supprimer un remplacement, sélectionnez le nom de la fonction de remplacement dans la colonne de droite, puis sélectionnez \<delete> *funcname*. Le code de la fonction est commenté.
