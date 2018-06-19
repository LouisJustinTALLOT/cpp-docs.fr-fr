---
title: 'Conteneurs de contrôles ActiveX : Affichage et modification des propriétés du contrôle | Documents Microsoft'
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
ms.openlocfilehash: ef443442cb19b9aaca82b74a0a5d8c72098d5cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340292"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Conteneurs de contrôles ActiveX : consultation et modification des propriétés de contrôle
Lorsque vous insérez un contrôle ActiveX dans un projet, il est utile afficher et modifier les propriétés prises en charge par le contrôle ActiveX. Cet article explique comment utiliser l’éditeur de ressources Visual C++ pour ce faire.  
  
 Si votre application conteneur de contrôles ActiveX utilise des contrôles incorporés, vous pouvez afficher et modifier les propriétés du contrôle dans l’éditeur de ressources. Vous pouvez également utiliser l’éditeur de ressources pour définir les valeurs de propriété au moment du design. L’éditeur de ressources enregistre ensuite automatiquement ces valeurs dans le fichier de ressources du projet. N’importe quelle instance du contrôle aura ses propriétés initialisées à ces valeurs.  
  
 Cette procédure suppose que vous avez inséré un contrôle dans votre projet. Pour plus d’informations, consultez [conteneurs de contrôles ActiveX : insertion d’un contrôle dans une Application conteneur](../mfc/inserting-a-control-into-a-control-container-application.md).  
  
 La première étape dans l’affichage des propriétés d' un contrôle consiste à ajouter une instance du contrôle à un modèle de boîte de dialogue du projet.  
  
### <a name="to-view-the-properties-of-a-control"></a>Pour afficher les propriétés d’un contrôle  
  
1.  Dans l’affichage des ressources, ouvrez le **boîte de dialogue** dossier.  
  
2.  Ouvrez votre modèle de boîte de dialogue principale.  
  
3.  Insérer un contrôle ActiveX à l’aide du **insérer un contrôle ActiveX** boîte de dialogue. Pour plus d’informations, consultez [affichage et ajout de contrôles ActiveX à une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
4.  Dans la boîte de dialogue, sélectionnez le contrôle ActiveX.  
  
5.  Dans la fenêtre Propriétés, cliquez sur le **propriétés** bouton.  
  
 Utilisez le **propriétés** boîte de dialogue pour modifier et tester immédiatement les nouvelles propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

