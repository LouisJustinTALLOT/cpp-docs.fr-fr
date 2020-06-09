---
title: Boîtes de dialogue dans OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: b59ba16e6e68df2a539232636e8fe710750e3214
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616908"
---
# <a name="dialog-boxes-in-ole"></a>Boîtes de dialogue dans OLE

Lorsqu’un utilisateur exécute une application OLE, il peut arriver que l’application ait besoin d’informations de la part de l’utilisateur pour effectuer l’opération. Les classes OLE MFC fournissent un certain nombre de boîtes de dialogue pour recueillir les informations nécessaires. Cette rubrique répertorie les tâches gérées par les boîtes de dialogue OLE et les classes nécessaires à l’affichage de ces boîtes de dialogue. Pour plus d’informations sur les boîtes de dialogue OLE et les structures utilisées pour personnaliser leur comportement, consultez [MFC Reference](mfc-desktop-applications.md).

*Insérer un objet*<br/>
Cette boîte de dialogue permet à l’utilisateur d’insérer des objets nouvellement créés ou existants dans le document composé. Il permet également à l’utilisateur de choisir d’afficher l’élément sous la forme d’une icône et active le bouton de commande modifier l’icône. Affichez cette boîte de dialogue lorsque l’utilisateur choisit insérer un objet dans le menu Edition. Utilisez la classe [COleInsertDialog](reference/coleinsertdialog-class.md) pour afficher cette boîte de dialogue. Notez que vous ne pouvez pas insérer une application MDI en elle-même. Une application qui est conteneur/serveur ne peut pas être insérée dans elle-même à moins d'être une application SDI.

*Collage spécial*<br/>
Cette boîte de dialogue permet à l’utilisateur de contrôler le format utilisé lors du collage de données dans un document composé. L’utilisateur peut choisir le format des données, s’il faut incorporer ou lier les données et s’il faut l’afficher sous forme d’icône. Affichez cette boîte de dialogue lorsque l’utilisateur choisit Collage spécial dans le menu Edition. Utilisez la classe [COlePasteSpecialDialog](reference/colepastespecialdialog-class.md) pour afficher cette boîte de dialogue.

*Changer d'icône*<br/>
Cette boîte de dialogue permet à l’utilisateur de sélectionner l’icône qui est affichée pour représenter l’élément lié ou incorporé. Affichez cette boîte de dialogue lorsque l’utilisateur choisit modifier l’icône dans le menu Edition ou bien choisit le bouton modifier l’icône dans les boîtes de dialogue coller spécial ou convertir. Affichez-la également lorsque l’utilisateur ouvre la boîte de dialogue Insérer un objet et choisit afficher en tant qu’icône. Utilisez la classe [COleChangeIconDialog](reference/colechangeicondialog-class.md) pour afficher cette boîte de dialogue.

*Passer*<br/>
Cette boîte de dialogue permet à l’utilisateur de modifier le type d’un élément incorporé ou lié. Par exemple, si vous avez incorporé un métafichier dans un document composé et que vous souhaitez utiliser ultérieurement une autre application pour modifier le métafichier incorporé, vous pouvez utiliser la boîte de dialogue convertir. Pour afficher cette boîte de dialogue, dans le menu Edition, cliquez sur objet de *type d’élément* , puis, dans le menu en cascade, cliquez sur convertir. Utilisez la classe [COleConvertDialog](reference/coleconvertdialog-class.md) pour afficher cette boîte de dialogue. Pour obtenir un exemple, exécutez l’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

*Modifier les liens ou mettre à jour les liens*<br/>
La boîte de dialogue Modifier les liens permet à l’utilisateur de modifier les informations relatives à la source d’un objet lié. La boîte de dialogue mettre à jour les liens vérifie les sources de tous les éléments liés dans la boîte de dialogue active et affiche la boîte de dialogue Modifier les liens si nécessaire. Affiche la boîte de dialogue Modifier les liens lorsque l’utilisateur choisit des liens dans le menu Edition. La boîte de dialogue mettre à jour les liens s’affiche généralement lorsqu’un document composé est ouvert pour la première fois. Utilisez la classe [COleLinksDialog](reference/colelinksdialog-class.md) ou [COleUpdateDialog](reference/coleupdatedialog-class.md) , selon la boîte de dialogue que vous souhaitez afficher.

*Serveur occupé ou serveur ne répond pas*<br/>
La boîte de dialogue serveur occupé s’affiche lorsque l’utilisateur tente d’activer un élément et que le serveur ne parvient pas à traiter la demande, généralement parce que le serveur est en cours d’utilisation par un autre utilisateur ou une autre tâche. La boîte de dialogue le serveur ne répond pas s’affiche si le serveur ne répond pas du tout à la demande d’activation. Ces boîtes de dialogue sont affichées via `COleMessageFilter` , sur la base d’une implémentation de l’interface OLE `IMessageFilter` , et l’utilisateur peut décider s’il faut retenter la demande d’activation. Utilisez la classe [COleBusyDialog](reference/colebusydialog-class.md) pour afficher cette boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)<br/>
[OLE](ole-in-mfc.md)
