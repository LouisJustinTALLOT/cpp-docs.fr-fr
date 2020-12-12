---
description: 'En savoir plus sur : changement de nom'
title: Renommer
ms.date: 11/16/2016
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
ms.openlocfilehash: 21bd5b817e51c29f4103b3ea105217ae743bdb4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318726"
---
# <a name="rename"></a>Renommer

**Quoi :** vous permet de renommer des identificateurs pour des symboles de code, tels que des champs, variables locales, méthodes, espaces de noms, propriétés et types.

**Quand :** vous voulez renommer en toute sécurité un élément sans avoir à rechercher toutes les instances et à copier/coller le nouveau nom.

**Pourquoi :** un copier-coller du nouveau nom dans un projet entier entraînera probablement des erreurs.  Cet outil de refactorisation effectuera avec précision le changement de nom.

**Utilisation**

1. Mettez en surbrillance ou placez le curseur de texte dans l’élément à renommer :

   ![Code mis en surbrillance](images/rename_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+R**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Renommer**.
     * Cliquez avec le bouton droit et sélectionnez **Renommer**.

1. Dans la fenêtre **Renommer** qui s’affiche, entrez le nouveau nom de l’élément sélectionné et cliquez sur le bouton **Aperçu**.  Modifiez la valeur pour **Étendue de recherche** si vous avez besoin d’élargir ou de restreindre l’étendue du renommage.

   ![Boîte de dialogue Renommer](images/rename_dialog.png)

   > [!TIP]
   > Vous pouvez ignorer l’aperçu en cochant l’option **Ignorer l’aperçu des modifications si toutes les références sont confirmées**.

1. Quand la fenêtre **Aperçu des modifications - Renommer** s’affiche, vérifiez que les modifications demandées sont correctement apportées.  Pour activer ou désactiver le renommage d’un élément, utilisez les cases à cocher situées dans la moitié supérieure de la fenêtre.

   ![Renommer, aperçu](images/rename_preview.png)

1. Quand tout semble correct, cliquez sur le bouton **Appliquer** et l’élément sera renommé dans votre code source.
