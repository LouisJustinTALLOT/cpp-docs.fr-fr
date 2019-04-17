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
ms.openlocfilehash: fa3d87e2cc17e297c3e6387920c6d527d8ddbe39
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767650"
---
# <a name="dialog-boxes-in-ole"></a>Boîtes de dialogue dans OLE

Lorsqu’un utilisateur exécute une application prenant en charge OLE, voici les heures lorsque l’application a besoin d’informations à partir de l’utilisateur afin d’effectuer l’opération. Les classes OLE MFC fournissent un nombre de boîtes de dialogue pour recueillir les informations requises. Cette rubrique répertorie les tâches gérées par les boîtes de dialogue OLE et les classes nécessaires pour afficher ces boîtes de dialogue. Pour plus d’informations sur les boîtes de dialogue OLE et les structures utilisées pour personnaliser leur comportement, consultez [référence MFC](../mfc/mfc-desktop-applications.md).

*Insérer un objet*<br/>
Cette boîte de dialogue permet à l’utilisateur d’insérer nouvellement créés ou les objets existants dans le document composé. Il permet à l’utilisateur de choisir d’afficher l’élément sous forme d’icône et Active le bouton de commande Changer d’icône. Afficher cette boîte de dialogue lorsque l’utilisateur choisit d’insérer un objet dans le menu Edition. Utilisez le [classe COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) classe pour afficher cette boîte de dialogue. Notez que vous ne pouvez pas insérer une application MDI en elle-même. Une application qui est conteneur/serveur ne peut pas être insérée dans elle-même à moins d'être une application SDI.

*Collage spécial*<br/>
Cette boîte de dialogue permet à l’utilisateur contrôler le format utilisé lors du collage des données dans un document composé. L’utilisateur peut choisir le format des données, d’incorporer ou de lier les données et l’afficher sous forme d’icône. Afficher cette boîte de dialogue lorsque l’utilisateur choisit Collage spécial dans le menu Edition. Utilisez le [classe COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) classe pour afficher cette boîte de dialogue.

*Changer d’icône*<br/>
Cette boîte de dialogue permet à l’utilisateur sélectionner l’icône qui s’affiche pour représenter l’élément lié ou incorporé. Afficher cette boîte de dialogue lorsque l’utilisateur choisit de changer d’icône dans le menu Edition ou clique sur le bouton Changer d’icône dans le collage spécial ou convertir les boîtes de dialogue. Affichez-la également lorsque l’utilisateur ouvre la boîte de dialogue Insérer un objet et choisit afficher sous forme d’icône. Utilisez le [classe COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) classe pour afficher cette boîte de dialogue.

*Convert*<br/>
Cette boîte de dialogue permet à l’utilisateur modifier le type d’un élément incorporé ou lié. Par exemple, si vous avez incorporé un métafichier dans un document composé et que vous souhaitez utiliser une autre application pour modifier le métafichier incorporé plus tard, vous pouvez utiliser la boîte de dialogue Convertir. Cette boîte de dialogue s’affiche généralement en cliquant sur *type d’élément* objet dans le menu Edition, puis, dans le menu en cascade, puis sur Convertir. Utilisez le [classe COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) classe pour afficher cette boîte de dialogue. Pour obtenir un exemple, exécutez l’exemple OLE MFC [OCLIENT](../overview/visual-cpp-samples.md).

*Modifier les liens ou les liens de la mise à jour*<br/>
La boîte de dialogue Modifier les liens permet à l’utilisateur modifier les informations sur la source d’un objet lié. La boîte de dialogue Mise à jour vérifie les sources de tous les éléments liés dans la boîte de dialogue et affiche la boîte de dialogue Modifier les liens si nécessaire. Afficher la boîte de dialogue Modifier les liens quand l’utilisateur choisit les liens dans le menu Edition. La boîte de dialogue Mise à jour s’affiche généralement lors de la première ouverture d’un document composé. Utilisez le [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) ou [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) class, selon quelle boîte de dialogue que vous souhaitez afficher.

*Serveur occupé ou le serveur ne répond ne pas*<br/>
La boîte de dialogue serveur occupé s’affiche lorsque l’utilisateur tente d’activer un élément et le serveur est actuellement incapable de traiter la demande, généralement parce que le serveur est en cours d’utilisation par un autre utilisateur ou de tâches. La boîte de dialogue serveur ne répond pas s’affiche si le serveur ne répond pas du tout à la demande d’activation. Ces boîtes de dialogue sont affichées `COleMessageFilter`, en se basant sur une implémentation de l’interface OLE `IMessageFilter`, et l’utilisateur peut décider s’il faut tenter à nouveau de la demande d’activation. Utilisez le [classe COleBusyDialog](../mfc/reference/colebusydialog-class.md) classe pour afficher cette boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
