---
title: Boîtes de dialogue dans OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe7f9b4b97fd17e73c3dd9f113a87d8f087b93c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929661"
---
# <a name="dialog-boxes-in-ole"></a>Boîtes de dialogue dans OLE
Lorsqu’un utilisateur exécute une application OLE, voici les heures lorsque l’application a besoin d’informations à partir de l’utilisateur afin d’effectuer l’opération. Les classes OLE MFC fournissent un nombre de boîtes de dialogue pour recueillir les informations requises. Cette rubrique répertorie les tâches gérées par les boîtes de dialogue OLE et les classes nécessaires pour afficher ces boîtes de dialogue. Pour plus d’informations sur les boîtes de dialogue OLE et les structures utilisées pour personnaliser leur comportement, consultez [référence MFC](../mfc/mfc-desktop-applications.md).  
  
 *Insérer l’objet*  
 Cette boîte de dialogue permet à l’utilisateur d’insérer nouvellement créés ou des objets existants dans le document composé. Aussi, il permet à l’utilisateur choisir d’afficher l’élément sous forme d’icône et Active le bouton de commande Changer d’icône. Afficher cette boîte de dialogue lorsque l’utilisateur choisit insérer un objet dans le menu Edition. Utilisez le [classe COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) classe pour afficher cette boîte de dialogue. Notez que vous ne pouvez pas insérer une application MDI en elle-même. Une application qui est conteneur/serveur ne peut pas être insérée dans elle-même à moins d'être une application SDI.  
  
 *Collage spécial*  
 Cette boîte de dialogue permet à l’utilisateur de contrôler le format utilisé lors du collage de données dans un document composé. L’utilisateur peut choisir le format des données, s’il faut incorporer ou lier les données et l’afficher sous forme d’icône. Afficher cette boîte de dialogue lorsque l’utilisateur choisit Collage spécial dans le menu Edition. Utilisez le [classe COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) classe pour afficher cette boîte de dialogue.  
  
 *Changer d’icône*  
 Cette boîte de dialogue permet à l’utilisateur de sélectionner l’icône qui s’affiche pour représenter l’élément lié ou incorporé. Afficher cette boîte de dialogue lorsque l’utilisateur choisit de changer d’icône dans le menu Edition ou clique sur le bouton Changer d’icône dans le collage spécial ou convertir les boîtes de dialogue. Affichez-la également lorsque l’utilisateur ouvre la boîte de dialogue Insérer un objet et choisit afficher sous forme d’icône. Utilisez le [classe COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) classe pour afficher cette boîte de dialogue.  
  
 *Convertir*  
 Cette boîte de dialogue permet à l’utilisateur modifier le type d’un élément incorporé ou lié. Par exemple, si vous avez incorporé un métafichier dans un document composé et que vous souhaitez utiliser une autre application pour modifier le métafichier incorporé plus tard, vous pouvez utiliser la boîte de dialogue de conversion. Cette boîte de dialogue s’affiche généralement en cliquant sur *le type d’élément* objet dans le menu Edition, puis, dans le menu en cascade, cliquez sur Convertir. Utilisez le [classe COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) classe pour afficher cette boîte de dialogue. Pour obtenir un exemple, exécuter l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md).  
  
 *Modifier les liens ou les liens de la mise à jour*  
 La boîte de dialogue Modifier les liaisons permet à l’utilisateur modifier les informations sur la source d’un objet lié. La boîte de dialogue Mise à jour vérifie les sources de tous les éléments liés dans la boîte de dialogue et affiche la boîte de dialogue Modifier les liens si nécessaire. Afficher la boîte de dialogue Modifier les liaisons lorsque l’utilisateur choisit de liens dans le menu Edition. La boîte de dialogue Mise à jour est généralement affichée lors de la première ouverture d’un document composé. Utilisez le [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) ou [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) de classe, en fonction de la boîte de dialogue où vous souhaitez afficher.  
  
 *Le serveur est occupé ou le serveur ne répond ne pas*  
 La boîte de dialogue serveur occupé s’affiche lorsque l’utilisateur tente d’activer un élément et le serveur est actuellement incapable de traiter la demande, généralement parce que le serveur est en cours d’utilisation par un autre utilisateur ou de tâches. La boîte de dialogue serveur ne répond pas s’affiche si le serveur ne répond pas du tout à la demande d’activation. Ces boîtes de dialogue sont affichés `COleMessageFilter`, basé sur une implémentation de l’interface OLE `IMessageFilter`, et l’utilisateur peut décider s’il faut essayer de nouveau la demande d’activation. Utilisez le [classe COleBusyDialog](../mfc/reference/colebusydialog-class.md) classe pour afficher cette boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)   
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

