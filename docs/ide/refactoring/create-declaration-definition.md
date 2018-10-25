---
title: Créer la déclaration/la définition | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21edf09eb78d339c06c709b06e8fe43ea72475c4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808398"
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
