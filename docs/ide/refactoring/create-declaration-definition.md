---
title: Créer la déclaration/la définition
ms.date: 10/19/2018
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
ms.openlocfilehash: 59ae3ebc23303554a35eea17c7e28850a4a1499a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693124"
---
# <a name="create-declaration--definition"></a>Créer la déclaration/la définition

**Quoi :** vous permet de générer immédiatement la déclaration ou définition d’une fonction.

**Quand :** vous avez une fonction qui nécessite une déclaration, ou inversement.

**Pourquoi :** vous pouvez créer manuellement la définition/déclaration, mais cette fonctionnalité la crée automatiquement, avec le fichier d’en-tête/de code si nécessaire.

**Comment :**

1. placez le curseur texte ou de la souris sur la fonction pour laquelle vous souhaitez créer la déclaration ou la définition.

   ![Code mis en surbrillance](images/createdefinition_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Créer la déclaration/la définition** dans le menu contextuel.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Créer la déclaration/la définition** dans le menu contextuel.

1. La définition/déclaration de la fonction est créée dans le fichier source ou d’en-tête, qui s’affiche dans une fenêtre d’aperçu contextuelle.  Si le fichier source ou d’en-tête n’existe pas, il est également créé et placé dans le projet.

   ![Créer la déclaration/la définition, résultat](images/createdefinition_result.png)
