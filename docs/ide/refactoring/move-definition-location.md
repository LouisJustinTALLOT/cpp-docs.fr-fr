---
title: Déplacer l’emplacement de définition | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058e0b3bab1fb5fb5e8d52b55e3fa7c37fd8a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430043"
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
