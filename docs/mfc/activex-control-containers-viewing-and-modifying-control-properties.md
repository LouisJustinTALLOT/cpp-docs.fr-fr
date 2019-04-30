---
title: 'Conteneurs de contrôles ActiveX : Affichage et modification des propriétés de contrôle'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 0a03acfd880bcf63017eec9796315b98e5d5f4d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394882"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Conteneurs de contrôles ActiveX : Affichage et modification des propriétés de contrôle

Lorsque vous insérez un contrôle ActiveX dans un projet, il est utile afficher et modifier les propriétés prises en charge par le contrôle ActiveX. Cet article explique comment utiliser l’éditeur de ressources Visual C++ pour ce faire.

Si votre application de conteneur de contrôle ActiveX utilise des contrôles incorporés, vous pouvez afficher et modifier les propriétés du contrôle dans l’éditeur de ressources. Vous pouvez également utiliser l’éditeur de ressources pour définir les valeurs de propriété au moment du design. L’éditeur de ressources enregistre ensuite automatiquement ces valeurs dans le fichier de ressources du projet. N’importe quelle instance du contrôle aura ses propriétés initialisées à ces valeurs.

Cette procédure suppose que vous avez inséré un contrôle dans votre projet. Pour plus d’informations, consultez [conteneurs de contrôles ActiveX : Insertion d’un contrôle dans une Application de conteneur de contrôle](../mfc/inserting-a-control-into-a-control-container-application.md).

Affichage des propriétés du contrôle, la première étape consiste à ajouter une instance du contrôle au modèle de boîte de dialogue du projet.

### <a name="to-view-the-properties-of-a-control"></a>Pour afficher les propriétés d’un contrôle

1. Dans l’affichage des ressources, ouvrez le **boîte de dialogue** dossier.

1. Ouvrez votre modèle de boîte de dialogue principale.

1. Insérer un contrôle ActiveX à l’aide du **insérer un contrôle ActiveX** boîte de dialogue. Pour plus d’informations, consultez [affichage et ajout de contrôles ActiveX à une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. Dans la boîte de dialogue, sélectionnez le contrôle ActiveX.

1. Dans la fenêtre Propriétés, cliquez sur le **propriétés** bouton.

Utilisez le **propriétés** boîte de dialogue pour modifier et tester immédiatement de nouvelles propriétés.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)
