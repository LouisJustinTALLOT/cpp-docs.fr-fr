---
description: 'En savoir plus sur : Assistant boîte de dialogue ATL'
title: Assistant Boîte de dialogue ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 2fc110f12399c0c855cb98a9d7e505180bef7b0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158879"
---
# <a name="atl-dialog-wizard"></a>Assistant Boîte de dialogue ATL

Cet Assistant insère dans le projet un objet de boîte de dialogue ATL, dérivé de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Une boîte de dialogue dérivée de `CAxDialogImpl` peut héberger des contrôles ActiveX.

L’Assistant crée une ressource de boîte de dialogue avec les boutons **OK** et **Annuler** par défaut. Vous pouvez modifier la ressource de boîte de dialogue et ajouter des contrôles ActiveX à l’aide de l' [éditeur de boîtes de dialogue](../../windows/dialog-editor.md) dans Affichage des ressources.

L’Assistant insère dans le fichier d’en-tête une [table des messages](../../atl/message-maps-atl.md) et des déclarations pour gérer les événements Click par défaut. Pour plus d’informations sur les boîtes de dialogue ATL, consultez [implémentation d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) .

- **Nom court**

   Définit le nom abrégé de l’objet de boîte de dialogue ATL. Le nom que vous fournissez détermine le nom de la classe et le nom du fichier (. cpp et. h), à moins que vous ne modifiiez ces champs individuellement.

- **Classe**

   Définit le nom de la classe à créer. Ce nom est basé sur le nom que vous renseignez dans **Nom court**, précédé de « C », préfixe typique d’un nom de classe.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

## <a name="see-also"></a>Voir aussi

[Boîte de dialogue ATL](../../atl/reference/adding-an-atl-dialog-box.md)
