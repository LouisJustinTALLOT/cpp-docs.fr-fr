---
title: Implémenter les virtuels purs
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692661"
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
