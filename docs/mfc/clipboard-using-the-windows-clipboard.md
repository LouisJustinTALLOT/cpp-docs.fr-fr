---
title: 'Presse-papiers : Utilisation du Presse-papiers Windows | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed1b3e9cc0cdd368a37657a751df67bed3f72dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342106"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Presse-papiers : utilisation du Presse-papiers Windows
Cette rubrique décrit comment utiliser l’API standard du Presse-papiers Windows dans votre application MFC.  
  
 La plupart des applications pour Windows prend en charge les couper ou copier les données dans le Presse-papiers de Windows et le collage de données à partir du Presse-papiers. Les formats de données du Presse-papiers varient selon les applications. Le framework prend en charge uniquement un nombre limité de formats de Presse-papiers pour un nombre limité de classes. Vous pouvez implémenter normalement les commandes liées au Presse-papiers, couper, copier et coller, dans le menu Edition de votre affichage. La bibliothèque de classes définit les ID de commande pour ces commandes : **ID_EDIT_CUT**, **ID_EDIT_COPY**, et **ID_EDIT_PASTE**. Les invites de ligne de message sont également définies.  
  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md) explique comment gérer les commandes de menu dans votre application en mappant la commande de menu à une fonction gestionnaire. Tant que votre application ne définit pas de fonctions gestionnaires pour les commandes du Presse-papiers dans le menu Edition, ils sont désactivés. Pour écrire des fonctions gestionnaires pour les commandes Couper et copier, implémentez la sélection dans votre application. Pour écrire une fonction gestionnaire pour la commande Coller, interrogez le Presse-papiers pour voir si elle contient des données dans un format que votre application peut accepter. Par exemple, pour activer la commande de copie, vous pouvez écrire un gestionnaire comme suit :  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 Les commandes Couper, copier et coller ne sont pas significatives dans certains contextes. Les commandes Couper et copier doivent être activés uniquement lorsqu’un élément est sélectionné, et la commande Coller uniquement lorsque quelque chose est dans le Presse-papiers. Vous pouvez fournir ce comportement en définissant des fonctions de gestionnaire de mise à jour qui activent ou désactivent ces commandes en fonction du contexte. Pour plus d’informations, consultez [comment les objets d’Interface utilisateur de mise à jour](../mfc/how-to-update-user-interface-objects.md).  
  
 La bibliothèque Microsoft Foundation Class assure une prise en charge du Presse-papiers pour modifier le texte avec le `CEdit` et `CEditView` classes. Les classes OLE simplifient également l’implémentation des opérations du Presse-papiers impliquant des éléments OLE. Pour plus d’informations sur les classes OLE, consultez [Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).  
  
 Implémentation d’autres de modifier les commandes de menu, telles qu’Annuler (**ID_EDIT_UNDO**) et de restauration par progression (**ID_EDIT_REDO**), est également de gauche à vous. Si votre application ne prend pas en charge ces commandes, vous pouvez facilement les supprimer à partir de votre fichier de ressources à l’aide d’éditeurs de ressources Visual C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Presse-papiers](../mfc/clipboard.md)

