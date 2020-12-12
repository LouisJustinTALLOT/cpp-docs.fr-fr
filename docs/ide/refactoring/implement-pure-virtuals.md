---
description: 'En savoir plus sur : implémenter des virtuels purs'
title: Implémenter les virtuels purs
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: b35ebba556ed9bae6ded649caca000b7d3554480
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318752"
---
# <a name="implement-pure-virtuals"></a>Implémenter les virtuels purs

**Quoi :** vous permet de générer immédiatement le code requis pour implémenter toutes les méthodes virtuelles pures dans une classe.

**Quand :** vous voulez hériter d’une classe avec des fonctions virtuelles pures.

**Pourquoi :** vous pouvez implémenter manuellement toutes les fonctions virtuelles pures une par une, mais cette fonctionnalité génère automatiquement toutes les signatures de méthode.

**Utilisation**

1. placez le curseur texte ou de la souris sur la classe dans laquelle vous souhaitez implémenter les fonctions virtuelles pures de la classe de base.

   ![Code mis en surbrillance](images/virtuals_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **CTRL +.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter tous les virtuels purs pour la classe '*ClassName*'** dans le menu contextuel, où *ClassName* est le nom de la classe sélectionnée.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter tous les virtuels purs pour la classe '*ClassName*'** dans le menu contextuel, où *ClassName* est le nom de la classe sélectionnée.

1. Les signatures de méthode virtuelle pure sont créées automatiquement, prêtes à être implémentées.

   ![Implémenter les virtuels purs, résultat](images/virtuals_result.png)
