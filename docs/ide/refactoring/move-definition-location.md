---
title: Déplacer l'emplacement de définition
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: 7957e18732dfae92b7b3ae9cf7ecea441fc3a6b4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693203"
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
