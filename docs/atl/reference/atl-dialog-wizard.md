---
title: Assistant Boîte de dialogue ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 7f868800bb8453ac47ec0f188d6a2970aee7a55f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458051"
---
# <a name="atl-dialog-wizard"></a>Assistant Boîte de dialogue ATL

Cet Assistant insère dans le projet, un objet de boîte de dialogue ATL, dérivé [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Une boîte de dialogue dérivée de `CAxDialogImpl` peut héberger des contrôles ActiveX.

L’Assistant crée une ressource de boîte de dialogue avec la valeur par défaut **OK** et **Annuler** boutons. Vous pouvez modifier la ressource de boîte de dialogue et ajouter des contrôles ActiveX à l’aide de la [boîte de dialogue Éditeur](../../windows/dialog-editor.md) dans Affichage des ressources.

L’Assistant a inséré dans le fichier d’en-tête une [table des messages](../../atl/message-maps-atl.md) et événements de clic de déclarations pour gérer la valeur par défaut. Consultez [mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) pour plus d’informations sur les boîtes de dialogue ATL.

- **Nom court**

   Définit le nom abrégé pour l’objet de la boîte de dialogue ATL. Le nom que vous fournissez détermine le nom de classe et le fichier (.cpp et .h), sauf si vous modifiez ces champs individuellement.

- **Classe**

   Définit le nom de la classe à créer. Ce nom est basé sur le nom que vous fournissez dans **nom court**, précédé de « C », le préfixe classique pour un nom de classe.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

## <a name="see-also"></a>Voir aussi

[Boîte de dialogue ATL](../../atl/reference/adding-an-atl-dialog-box.md)

