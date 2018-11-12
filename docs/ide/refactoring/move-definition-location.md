---
title: Déplacer l'emplacement de définition
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: fd4fe2fb755919656fba935c29ab8a8591426bea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462359"
---
# <a name="move-definition-location"></a>Déplacer l'emplacement de définition
**Quoi :** vous permet de déplacer immédiatement une définition de fonction vers le fichier d’en-tête correspondant.

**Quand :** vous avez une fonction que vous souhaitez déplacer vers un fichier d’en-tête.

**Pourquoi :** vous pouvez déplacer manuellement la fonction, mais cette fonctionnalité la déplace automatiquement, en créant le fichier d’en-tête si nécessaire.

**Comment :**

1. placez le curseur texte ou de la souris sur la fonction à déplacer.

   ![Code mis en surbrillance](images/movedefinition_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer l’emplacement de définition** dans le menu contextuel.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer l’emplacement de définition** dans le menu contextuel.

1. La fonction est déplacée vers le fichier d’en-tête correspondant, qui s’affiche dans une fenêtre d’aperçu contextuelle.  Si le fichier d’en-tête n’existe pas, il est également créé et placé dans le projet.

   ![Créer la déclaration/la définition, résultat](images/movedefinition_result.png)
