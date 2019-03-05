---
title: Classes de boîtes de dialogue communes OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: d34c141fc9a2b53eab6a4c0b0ce1799ff5243d84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263544"
---
# <a name="ole-common-dialog-classes"></a>Classes de boîtes de dialogue communes OLE

Ces classes gèrent les tâches courantes de OLE en implémentant un nombre de boîtes de dialogue OLE standards. Ils fournissent également une interface utilisateur cohérente pour les fonctionnalités OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Utilisé par l’infrastructure pour contenir les implémentations courantes pour toutes les boîtes de dialogue OLE. Toutes les classes de boîte de dialogue dans la catégorie de l’interface utilisateur sont dérivés de cette classe de base. `COleDialog` ne peut pas être utilisée directement.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Affiche la boîte de dialogue Insérer un objet, l’interface utilisateur standard pour l’insertion de nouvelles OLE éléments liés ou incorporés.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Affiche la boîte de dialogue Collage spécial, l’interface utilisateur standard pour l’implémentation de la commande modifier le collage spécial.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Affiche la boîte de dialogue Modifier les liens, l’interface utilisateur standard pour la modification des informations sur les éléments liés.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Affiche la boîte de dialogue Changer d’icône, l’interface utilisateur standard pour modifier l’icône associée à OLE incorporé ou un élément lié.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Affiche la boîte de dialogue Convertir, l’interface utilisateur standard pour la conversion des éléments OLE à partir d’un type.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Encapsule la boîte de dialogue de propriétés OLE commune Windows. Boîtes de dialogue communes OLE propriétés fournissent un moyen simple pour afficher et modifier les propriétés d’un élément de document OLE de manière cohérente avec les normes de Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Affiche la boîte de dialogue de mise à jour, l’interface utilisateur standard pour la mise à jour tous les liens dans un document. La boîte de dialogue contient un indicateur de progression pour indiquer comment fermer la procédure de mise à jour est terminée.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Affiche la boîte de dialogue Modifier la Source, l’interface utilisateur standard pour la modification de la source d’un lien ou de destination.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Affiche les boîtes de dialogue serveur occupé et serveur ne répond pas, l’interface utilisateur standard pour gérer les appels aux applications occupées. Généralement affiché automatiquement par le `COleMessageFilter` implémentation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
