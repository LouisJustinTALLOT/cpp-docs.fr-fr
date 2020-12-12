---
description: 'En savoir plus sur : presse-papiers : utilisation du presse-papiers Windows'
title: 'Presse-papiers : utilisation du Presse-papiers Windows'
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
ms.openlocfilehash: 1c89c8888f7e3ffb81705ee146c00917a7763323
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338416"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Presse-papiers : utilisation du Presse-papiers Windows

Cette rubrique explique comment utiliser l’API du presse-papiers Windows standard dans votre application MFC.

La plupart des applications pour Windows prennent en charge la découpe ou la copie des données dans le presse-papiers Windows et le collage de données à partir du presse-papiers. Les formats de données du presse-papiers varient selon les applications. Le Framework ne prend en charge qu’un nombre limité de formats de presse-papiers pour un nombre limité de classes. Normalement, vous allez implémenter les commandes associées au Presse-papiers (couper, copier et coller) dans le menu Edition de votre affichage. La bibliothèque de classes définit les ID de commande pour les commandes suivantes : **ID_EDIT_CUT**, **ID_EDIT_COPY** et **ID_EDIT_PASTE**. Leurs invites de ligne de message sont également définies.

[Les messages et les commandes de l’infrastructure](messages-and-commands-in-the-framework.md) expliquent comment gérer les commandes de menu dans votre application en mappant la commande de menu à une fonction de gestionnaire. Tant que votre application ne définit pas de fonctions de gestionnaire pour les commandes du presse-papiers du menu Edition, elles restent désactivées. Pour écrire des fonctions de gestionnaire pour les commandes Couper et copier, implémentez la sélection dans votre application. Pour écrire une fonction de gestionnaire pour la commande Coller, interrogez le presse-papiers pour voir s’il contient des données dans un format que votre application peut accepter. Par exemple, pour activer la commande de copie, vous pouvez écrire un gestionnaire semblable au suivant :

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Les commandes Couper, copier et coller sont uniquement significatives dans certains contextes. Les commandes Couper et copier ne doivent être activées que si une action est sélectionnée, et la commande coller uniquement quand un contenu est présent dans le presse-papiers. Vous pouvez fournir ce comportement en définissant des fonctions de gestionnaire de mise à jour qui activent ou désactivent ces commandes en fonction du contexte. Pour plus d’informations, consultez [Comment mettre à jour des objets User-Interface](how-to-update-user-interface-objects.md).

La bibliothèque MFC (Microsoft Foundation Class) fournit la prise en charge du presse-papiers pour la modification de texte avec les `CEdit` `CEditView` classes et. Les classes OLE simplifient également l’implémentation des opérations du presse-papiers qui impliquent des éléments OLE. Pour plus d’informations sur les classes OLE, consultez [presse-papiers : utilisation du mécanisme de presse-papiers OLE](clipboard-using-the-ole-clipboard-mechanism.md).

Il est également possible d’implémenter d’autres commandes du menu Edition, telles que Undo (**ID_EDIT_UNDO**) et Redo (**ID_EDIT_REDO**). Si votre application ne prend pas en charge ces commandes, vous pouvez facilement les supprimer de votre fichier de ressources à l’aide de l’Visual C++ éditeurs de ressources.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Copie et collage de données](clipboard-copying-and-pasting-data.md)

- [Utilisation du mécanisme de presse-papiers OLE](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers](clipboard.md)
