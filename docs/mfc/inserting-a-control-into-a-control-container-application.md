---
title: "Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle"
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 1d2fc82628b3bcf842a6efb1d36ab9e8389fc0ba
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618495"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle

Avant de pouvoir accéder à un contrôle ActiveX à partir d’une application de conteneur de contrôles ActiveX, vous devez ajouter le contrôle ActiveX à l’application conteneur à l’aide de la boîte de dialogue [Insérer un contrôle ActiveX](../windows/insert-activex-control-dialog-box.md) .

Pour ajouter un contrôle ActiveX au projet conteneur de contrôles ActiveX, consultez [affichage et ajout de contrôles ActiveX dans une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Une fois que vous avez ajouté le contrôle, vous devez ajouter une variable membre (du type de contrôle ActiveX) à la classe de la boîte de dialogue. Pour plus d’informations sur cette procédure, consultez [Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md).

Une fois que vous avez ajouté la variable membre, une classe, appelée classe wrapper, est automatiquement générée et ajoutée à votre projet. Cette classe est utilisée comme une interface entre le conteneur de contrôle et le contrôle incorporé.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
