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
ms.openlocfilehash: 1d42820efd06c2ae52f5d1b22b0bdfb6335c4a89
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907804"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Conteneurs de contrôles ActiveX : Affichage et modification des propriétés de contrôle

Lorsque vous insérez un contrôle ActiveX dans un projet, il est utile d’afficher et de modifier les propriétés prises en charge par le contrôle ActiveX. Cet article explique comment utiliser l’éditeur de ressources C++ visuel pour effectuer cette opération.

Si votre application de conteneur de contrôles ActiveX utilise des contrôles incorporés, vous pouvez afficher et modifier les propriétés du contrôle dans l’éditeur de ressources. Vous pouvez également utiliser l’éditeur de ressources pour définir des valeurs de propriété au moment de la conception. L’éditeur de ressources enregistre ensuite automatiquement ces valeurs dans le fichier de ressources du projet. Toutes les instances du contrôle auront alors ses propriétés initialisées à ces valeurs.

Cette procédure suppose que vous avez inséré un contrôle dans votre projet. Pour plus d’informations [, consultez conteneurs de contrôles ActiveX : Insertion d’un contrôle dans une application](../mfc/inserting-a-control-into-a-control-container-application.md)de conteneur de contrôle.

La première étape de l’affichage des propriétés du contrôle consiste à ajouter une instance du contrôle au modèle de boîte de dialogue du projet.

### <a name="to-view-the-properties-of-a-control"></a>Pour afficher les propriétés d’un contrôle

1. Dans Affichage des ressources, ouvrez le dossier **boîte de dialogue** .

1. Ouvrez votre modèle de boîte de dialogue principale.

1. Insérer un contrôle ActiveX à l’aide de la boîte de dialogue **Insérer un contrôle ActiveX** . Pour plus d’informations, consultez [affichage et ajout de contrôles ActiveX dans une](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)boîte de dialogue.

1. Sélectionnez le contrôle ActiveX dans la boîte de dialogue.

1. Dans la fenêtre **Propriétés** , cliquez sur le bouton **Propriétés** .

Utilisez la boîte de dialogue **Propriétés** pour modifier et tester immédiatement de nouvelles propriétés.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)
