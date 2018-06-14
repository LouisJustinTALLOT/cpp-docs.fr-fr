---
title: Changer la signature | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f913f0b3065b136f626ef15cc2a77dce8d0254f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335089"
---
# <a name="change-signature"></a>Changer la signature
**Quoi :** vous permet de modifier les paramètres d’une fonction.

**Quand :** vous souhaitez réorganiser, ajouter, supprimer ou modifier les paramètres d’une fonction actuellement utilisés dans différents emplacements.  

**Pourquoi :** vous pourriez manuellement changer ces paramètres vous-même, puis rechercher tous les appels à cette fonction et les modifier un par un, mais cela peut entraîner des erreurs.  Cet outil de refactorisation effectuera automatiquement cette tâche.

**Comment :**

1. placez le curseur texte ou de la souris dans le nom de la méthode à modifier ou dans l’une de ses utilisations :

   ![Code mis en surbrillance](images/changesignature_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+O**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Changer la signature** dans le menu contextuel.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Réorganiser les paramètres**.
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Changer la signature** dans le menu contextuel.

1. Dans la boîte de dialogue **Modifier la signature** qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de la méthode :

   ![Boîte de dialogue Modifier la signature](images/changesignature_dialog.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas**    | Déplacer le paramètre sélectionné vers le haut ou le bas de la liste
   | **Ajouter**        | Ajouter un nouveau paramètre à la liste
   | **Supprimer**     | Supprimer le paramètre sélectionné de la liste
   | **Modifier**     | Modifier le paramètre sélectionné en changeant son type et/ou nom, en indiquant s’il est facultatif et ce que serait sa valeur injectée
   | **Rétablir**     | Rétablir l’état d’origine du paramètre sélectionné
   | **Tout rétablir** | Rétablir l’état d’origine de tous les paramètres

   > [!TIP]
   > Utilisez la case à cocher **Ignorer l’aperçu des modifications des références si toutes les références sont confirmées** pour apporter immédiatement les modifications sans afficher d’abord la fenêtre d’aperçu.

   Quand vous ajoutez ou modifiez un paramètre, la fenêtre **Ajouter un paramètre** ou **Modifier le paramètre** apparaît.

   ![Ajouter un paramètre/Modifier le paramètre](images/changesignature_addmodify.png)

   Vous pouvez ici effectuer les opérations suivantes :

   | Entrée | Description
   | ----- | ---
   | **Type**               | Type du paramètre (int, double, float, etc.)
   | **Name**               | Nom du paramètre
   | **Paramètre facultatif** | Spécifie éventuellement le paramètre
   | **Valeur injectée**     | Valeur insérée dans tous les appels à la fonction où le paramètre n’est pas spécifié (valide uniquement pour **Ajouter**)
   | **Valeur par défaut**      | Valeur utilisée par la fonction si l’appelant n’en spécifie aucune (valide uniquement pour **Paramètre facultatif**)

1. Utilisez la liste déroulante **Étendue de recherche** pour sélectionner si les modifications seront appliquées au projet ou à toute la solution.

1. Lorsque vous avez terminé, appuyez sur le bouton **OK** pour appliquer les modifications.  Vérifiez que les modifications demandées sont correctement apportées.  Pour activer ou désactiver le renommage d’un élément, utilisez les cases à cocher situées dans la moitié supérieure de la fenêtre.

   ![Changer la signature, aperçu](images/changesignature_preview.png)

1. Quand tout semble correct, cliquez sur le bouton **Appliquer** et la fonction sera modifiée dans votre code source.

   ![Résultat Modifier la signature](images/changesignature_result.png)