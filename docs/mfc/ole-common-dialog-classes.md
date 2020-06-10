---
title: Classes de boîtes de dialogue communes OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: 1854d19c540f5e3e64b47786f465a05213eced86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617792"
---
# <a name="ole-common-dialog-classes"></a>Classes de boîtes de dialogue communes OLE

Ces classes gèrent les tâches OLE courantes en implémentant un certain nombre de boîtes de dialogue OLE standard. Ils fournissent également une interface utilisateur cohérente pour les fonctionnalités OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Utilisé par l’infrastructure pour contenir des implémentations courantes pour toutes les boîtes de dialogue OLE. Toutes les classes de boîte de dialogue de la catégorie interface utilisateur sont dérivées de cette classe de base. `COleDialog`ne peut pas être utilisé directement.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Affiche la boîte de dialogue Insérer un objet, l’interface utilisateur standard qui permet d’insérer de nouveaux éléments OLE liés ou incorporés.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Affiche la boîte de dialogue Collage spécial, l’interface utilisateur standard pour l’implémentation de la commande Modifier Collage spécial.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Affiche la boîte de dialogue Modifier les liens, l’interface utilisateur standard permettant de modifier les informations relatives aux éléments liés.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Affiche la boîte de dialogue changer d’icône, l’interface utilisateur standard pour modifier l’icône associée à un élément OLE incorporé ou lié.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Affiche la boîte de dialogue convertir, l’interface utilisateur standard pour convertir les éléments OLE d’un type en un autre.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Encapsule la boîte de dialogue Propriétés communes de Windows OLE. Les boîtes de dialogue Propriétés OLE communes offrent un moyen simple d’afficher et de modifier les propriétés d’un élément de document OLE d’une manière cohérente avec les normes Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Affiche la boîte de dialogue mettre à jour, l’interface utilisateur standard pour la mise à jour de tous les liens d’un document. La boîte de dialogue contient un indicateur de progression pour indiquer la fin de la procédure de mise à jour.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Affiche la boîte de dialogue Modifier la source, l’interface utilisateur standard pour la modification de la destination ou de la source d’un lien.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Affiche les boîtes de dialogue serveur occupé et serveur ne répond pas, l’interface utilisateur standard pour la gestion des appels aux applications occupées. Généralement affiché automatiquement par l' `COleMessageFilter` implémentation.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
