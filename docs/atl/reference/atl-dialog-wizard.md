---
title: Assistant dialogue ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2d78f0a41edca44f8841d701cc87975c551466
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358004"
---
# <a name="atl-dialog-wizard"></a>Assistant Boîte de dialogue ATL
Cet Assistant insère dans le projet un objet boîte de dialogue ATL, dérivé de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Une boîte de dialogue dérivé `CAxDialogImpl` peut héberger des contrôles ActiveX.  
  
 L’Assistant crée une ressource de boîte de dialogue avec la valeur par défaut **OK** et **Annuler** boutons. Vous pouvez modifier la ressource de boîte de dialogue et ajouter des contrôles ActiveX à l’aide de la [boîte de dialogue Éditeur](../../windows/dialog-editor.md) dans l’affichage des ressources.  
  
 L’Assistant insère dans le fichier d’en-tête une [table des messages](../../atl/message-maps-atl.md) et déclarations pour la valeur par défaut de la gestion des événements click. Consultez [mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) pour plus d’informations sur les boîtes de dialogue ATL.  
  
 **Nom court**  
 Définit le nom abrégé de l’objet de la boîte de dialogue ATL. Le nom que vous fournissez détermine le nom de classe et le fichier (.cpp et .h), sauf si vous modifiez ces champs individuellement.  
  
 `Class`  
 Définit le nom de la classe à créer. Ce nom est basé sur le nom que vous fournissez dans **nom court**, précédé de « C » (préfixe classique pour un nom de classe.  
  
 **fichier .h**  
 Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant enregistrera pas à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.  
  
 L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.  
  
 **fichier .cpp**  
 Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. Le fichier n’est pas enregistré à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.  
  
 L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue ATL](../../atl/reference/adding-an-atl-dialog-box.md)

