---
title: Implémenter les virtuels purs
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: e693fdc17057d3800053bf5a7bad64ec441bcc3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614901"
---
# <a name="implement-pure-virtuals"></a>Implémenter les virtuels purs
**Quoi :** vous permet de générer immédiatement le code requis pour implémenter toutes les méthodes virtuelles pures dans une classe.

**Quand :** vous voulez hériter d’une classe avec des fonctions virtuelles pures.

**Pourquoi :** vous pouvez implémenter manuellement toutes les fonctions virtuelles pures une par une, mais cette fonctionnalité génère automatiquement toutes les signatures de méthode.

**Comment :**

1. placez le curseur texte ou de la souris sur la classe dans laquelle vous souhaitez implémenter les fonctions virtuelles pures de la classe de base.

   ![Code mis en surbrillance](images/virtuals_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter tous les virtuels purs pour la classe '*ClassName*'** dans le menu contextuel, où  *ClassName* est le nom de la classe sélectionnée.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter tous les virtuels purs pour la classe '*ClassName*'** dans le menu contextuel, où  *ClassName* est le nom de la classe sélectionnée.

1. Les signatures de méthode virtuelle pure sont créées automatiquement, prêtes à être implémentées.

   ![Implémenter les virtuels purs, résultat](images/virtuals_result.png)
