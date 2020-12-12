---
description: 'En savoir plus sur : déplacer la définition de l’emplacement'
title: Déplacer l'emplacement de définition
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: 5c0ae4ed5e14a50f4d54226fb298c34099c8aec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318713"
---
# <a name="move-definition-location"></a>Déplacer l'emplacement de définition

**Quoi :** vous permet de déplacer immédiatement une définition de fonction vers le fichier d’en-tête correspondant.

**Quand :** vous avez une fonction que vous souhaitez déplacer vers un fichier d’en-tête.

**Pourquoi :** vous pouvez déplacer manuellement la fonction, mais cette fonctionnalité la déplace automatiquement, en créant le fichier d’en-tête si nécessaire.

**Utilisation**

1. placez le curseur texte ou de la souris sur la fonction à déplacer.

   ![Code mis en surbrillance](images/movedefinition_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **CTRL +.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer l’emplacement de définition** dans le menu contextuel.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer l’emplacement de définition** dans le menu contextuel.

1. La fonction est déplacée vers le fichier d’en-tête correspondant, qui s’affiche dans une fenêtre d’aperçu contextuelle.  Si le fichier d’en-tête n’existe pas, il est également créé et placé dans le projet.

   ![Créer la déclaration/la définition, résultat](images/movedefinition_result.png)
