---
title: Extraire la fonction
ms.date: 11/16/2016
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
ms.openlocfilehash: ec3b9a0aeaef9e418b457bafdfb9bb1bbd2edffc
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692318"
---
# <a name="extract-function"></a>Extraire la fonction

**Quoi :** vous permet de transformer un fragment de code en sa propre fonction.

**Quand :** vous avez un fragment de code existant dans une fonction qui doit être appelée à partir d’une autre fonction.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication.  Une meilleure solution consiste à refactoriser ce fragment dans sa propre fonction pouvant être appelée librement par toute autre fonction.

**Comment :**

1. Mettez en surbrillance le code à extraire :

   ![Code mis en surbrillance](images/extractfunction_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+M**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la fonction (expérimental)** dans le menu contextuel.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Extraire la fonction (expérimental)**.
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la fonction (expérimental)** dans le menu contextuel.
     * Cliquez sur l’icône ![Ampoule](images/bulb.png) qui apparaît dans la marge de gauche et sélectionnez **Extraire la fonction (expérimental)** dans le menu contextuel.

1. Dans la fenêtre **Extraire la fonction/méthode (expérimental)**, entrez le nom de la nouvelle fonction, sélectionnez l’emplacement où placer le code, puis cliquez sur le bouton **OK**.

   ![Extraire la fonction, boîte de dialogue](images/extractfunction_dialog.png)

1. La nouvelle fonction est créée à l’emplacement indiqué, un prototype de fonction dans le fichier d’en-tête correspondant, et le code d’origine est modifié pour appeler cette fonction.

   ![Extraire la fonction, résultat](images/extractfunction_result.png)
