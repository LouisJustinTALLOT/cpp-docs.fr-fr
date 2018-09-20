---
title: 'Conteneurs de contrôles ActiveX : Insertion d’un contrôle dans une Application de conteneur de contrôle | Microsoft Docs'
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
ms.openlocfilehash: f025c9fa564bcd37c585db6ea5c5cd0f5be83e0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432137"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle

Avant que vous pouvez accéder à un contrôle ActiveX à partir d’une application de conteneur de contrôle ActiveX, vous devez ajouter le contrôle ActiveX à l’application de conteneur à l’aide de la [insérer un contrôle ActiveX](../windows/insert-activex-control-dialog-box.md) boîte de dialogue.

Pour ajouter un contrôle ActiveX pour le projet de conteneur de contrôle ActiveX, consultez [affichage et ajout de contrôles ActiveX à une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Une fois que vous ajoutez le contrôle, vous devez ajouter une variable membre (du type de contrôle ActiveX) à la classe de boîte de dialogue. Pour plus d’informations sur cette procédure, consultez [Ajout d’une Variable membre](../ide/adding-a-member-variable-visual-cpp.md).

Une fois que vous avez ajouté la variable membre à une classe, appelée une classe wrapper, est automatiquement générée et ajoutée à votre projet. Cette classe est utilisée en tant qu’interface entre le conteneur de contrôle et le contrôle incorporé.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

