---
title: Basculer entre les contrôles de boîte de dialogue et le Code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ffcb4621bf0005e6b22991da7a2dde9372afa6c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891920"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>Basculement entre l'Éditeur de boîtes de dialogue et le code
Dans les applications MFC, vous pouvez double-cliquer sur les contrôles de boîte de dialogue pour atteindre le code du gestionnaire ou pour créer rapidement des fonctions gestionnaires stub.  
  
 Avec un contrôle est sélectionné, cliquez sur le **ControlEvents** bouton ou le **Messages** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour afficher une liste complète des événements et les messages Windows disponible pour l’élément sélectionné. Choisissez dans la liste pour créer ou modifier des fonctions de gestionnaire.  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>Pour accéder au code à partir de l’éditeur de boîte de dialogue  
  
1.  Double-cliquez sur un contrôle dans la boîte de dialogue pour accéder à la déclaration de son message implémentée en dernier, fonction de gestion. (Pour les classes de boîte de dialogue ATL, vous passez toujours à la définition du constructeur.)  
  
### <a name="to-view-events-for-a-control"></a>Pour afficher les événements pour un contrôle  
  
1.  Un contrôle est sélectionné, puis cliquez sur le **ControlEvents** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).  
  
    > [!NOTE]
    >  En cliquant sur le **ControlEvents** bouton lorsque le *boîte de dialogue* a le focus expose une liste de tous les contrôles dans la boîte de dialogue, vous pouvez développer pour modifier les événements pour les contrôles individuels.  
  
     Lorsqu’un contrôle a le focus dans la boîte de dialogue, vous pouvez faites un clic droit et sélectionnez **ajouter un gestionnaire d’événements** dans le menu contextuel. Cela vous permet de spécifier la classe à laquelle le gestionnaire est ajouté. Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).  
  
### <a name="to-view-messages-for-a-dialog-box"></a>Pour afficher les messages pour une boîte de dialogue  
  
1.  La boîte de dialogue sélectionnée, puis cliquez sur le **Messages** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

