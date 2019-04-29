---
title: 'Presse-papiers : Utilisation du Presse-papiers Windows'
ms.date: 11/04/2016
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
ms.openlocfilehash: 49111e4efd2a12264d61030fe038d80b974514c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326987"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Presse-papiers : Utilisation du Presse-papiers Windows

Cette rubrique décrit comment utiliser l’API du Presse-papiers Windows standard au sein de votre application MFC.

La plupart des applications pour Windows prend en charge les couper ou copier des données dans le Presse-papiers de Windows et le collage des données à partir du Presse-papiers. Les formats de données du Presse-papiers varient selon les applications. Le framework prend en charge uniquement un nombre limité de formats de Presse-papiers pour un nombre limité de classes. Vous pouvez implémenter normalement les commandes liées au Presse-papiers, couper, copier et coller, dans le menu Edition de votre affichage. La bibliothèque de classes définit les ID de commande pour les commandes suivantes : **ID_EDIT_CUT**, **ID_EDIT_COPY**, et **ID_EDIT_PASTE**. Les invites de ligne de message sont également définies.

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md) explique comment gérer les commandes de menu dans votre application en mappant la commande de menu à une fonction gestionnaire. Tant que votre application ne définit pas de fonctions de gestionnaire pour les commandes du Presse-papiers dans le menu Edition, ils restent désactivés. Pour écrire des fonctions du gestionnaire pour les commandes Couper et copier, implémentez la sélection dans votre application. Pour écrire une fonction gestionnaire pour la commande Coller, interrogez le Presse-papiers pour voir si elle contient des données dans un format que votre application peut accepter. Par exemple, pour activer la commande de copie, vous pouvez écrire un gestionnaire de ce qui suit :

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Les commandes Couper, copier et coller sont uniquement significatives dans certains contextes. Les commandes Couper et copier doivent être activées uniquement quand un élément est sélectionné, et la commande Coller uniquement lorsque quelque chose est dans le Presse-papiers. Vous pouvez fournir ce comportement en définissant des fonctions de gestionnaire de mise à jour qui activent ou désactivent ces commandes en fonction du contexte. Pour plus d’informations, consultez [comment les objets d’Interface utilisateur mise à jour](../mfc/how-to-update-user-interface-objects.md).

La bibliothèque Microsoft Foundation Class fournit la prise en charge du Presse-papiers pour modifier le texte avec le `CEdit` et `CEditView` classes. Les classes OLE simplifient également l’implémentation des opérations de Presse-papiers qui impliquent des éléments OLE. Pour plus d’informations sur les classes OLE, consultez [Presse-papiers : À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).

Implémentation d’autres de modifier les commandes de menu, telles que l’annulation (**ID_EDIT_UNDO**) et de restauration par progression (**ID_EDIT_REDO**), est également de gauche à vous. Si votre application ne prend pas en charge ces commandes, vous pouvez facilement les supprimer à partir de votre fichier de ressources en utilisant les éditeurs de ressources Visual C++.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)

- [À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers](../mfc/clipboard.md)
