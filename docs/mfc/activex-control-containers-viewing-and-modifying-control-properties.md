---
title: 'Conteneurs de contrôle ActiveX : Consultation et modification des propriétés du contrôle | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9614ecfcd23418f8b0abc08622e8c272bb5548a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388821"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Conteneurs de contrôles ActiveX : consultation et modification des propriétés de contrôle

Lorsque vous insérez un contrôle ActiveX dans un projet, il est utile afficher et modifier les propriétés prises en charge par le contrôle ActiveX. Cet article explique comment utiliser l’éditeur de ressources Visual C++ pour ce faire.

Si votre application de conteneur de contrôle ActiveX utilise des contrôles incorporés, vous pouvez afficher et modifier les propriétés du contrôle dans l’éditeur de ressources. Vous pouvez également utiliser l’éditeur de ressources pour définir les valeurs de propriété au moment du design. L’éditeur de ressources enregistre ensuite automatiquement ces valeurs dans le fichier de ressources du projet. N’importe quelle instance du contrôle aura ses propriétés initialisées à ces valeurs.

Cette procédure suppose que vous avez inséré un contrôle dans votre projet. Pour plus d’informations, consultez [conteneurs de contrôles ActiveX : insertion d’un contrôle dans une Application conteneur](../mfc/inserting-a-control-into-a-control-container-application.md).

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

