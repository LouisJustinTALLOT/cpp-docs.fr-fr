---
description: 'En savoir plus sur : conteneurs de contrôles ActiveX : insertion d’un contrôle dans une application de conteneur de contrôle'
title: "Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle"
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 14e1895c39aeea788ab83b8a18be6d8b0ef6c20c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220602"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle

Avant de pouvoir accéder à un contrôle ActiveX à partir d’une application de conteneur de contrôles ActiveX, vous devez ajouter le contrôle ActiveX à l’application conteneur à l’aide de la boîte de dialogue [Insérer un contrôle ActiveX](../windows/adding-editing-or-deleting-controls.md) .

Pour ajouter un contrôle ActiveX au projet conteneur de contrôles ActiveX, consultez [affichage et ajout de contrôles ActiveX dans une boîte de dialogue](../windows/adding-editing-or-deleting-controls.md).

Une fois que vous avez ajouté le contrôle, vous devez ajouter une variable membre (du type de contrôle ActiveX) à la classe de la boîte de dialogue. Pour plus d’informations sur cette procédure, consultez [Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md).

Une fois que vous avez ajouté la variable membre, une classe, appelée classe wrapper, est automatiquement générée et ajoutée à votre projet. Cette classe est utilisée comme une interface entre le conteneur de contrôle et le contrôle incorporé.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
