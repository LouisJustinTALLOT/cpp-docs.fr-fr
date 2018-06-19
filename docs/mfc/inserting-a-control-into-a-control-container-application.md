---
title: 'Conteneurs de contrôles ActiveX : Insertion d’un contrôle dans une Application de conteneur du contrôle | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 716c045fc10b4dd5f3dede20a233d958e669bbd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346335"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle
Avant de pouvoir accéder à un contrôle ActiveX à partir d’une application de conteneur de contrôle ActiveX, vous devez ajouter le contrôle ActiveX à l’application de conteneur à l’aide de la [insérer un contrôle ActiveX](../windows/insert-activex-control-dialog-box.md) boîte de dialogue.  
  
 Pour ajouter un contrôle ActiveX au projet conteneur de contrôle ActiveX, consultez [affichage et ajout de contrôles ActiveX à une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Une fois que vous ajoutez le contrôle, vous devez ajouter une variable membre (du type de contrôle ActiveX) à la classe de boîte de dialogue. Pour plus d’informations sur cette procédure, consultez [Ajout d’une Variable membre](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Une fois que vous avez ajouté la variable membre à une classe, appelée une classe wrapper, est automatiquement générée et ajoutée à votre projet. Cette classe est utilisée en tant qu’interface entre le conteneur de contrôle et le contrôle incorporé.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

