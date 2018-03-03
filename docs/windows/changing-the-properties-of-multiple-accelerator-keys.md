---
title: "Modification des propriétés de plusieurs touches accélérateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fbe5ab2202da457c8970d84d304ec97fdedd4a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>Modification des propriétés de plusieurs touches accélérateur
### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Pour modifier les propriétés de plusieurs touches accélérateur  
  
1.  Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Sélectionnez les touches accélérateur que vous souhaitez modifier en maintenant enfoncée la **CTRL** quand vous cliquez sur chacun d’eux.  
  
3.  Accédez à la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) et tapez les valeurs que vous voulez que tous les accélérateurs sélectionnés doivent partager.  
  
    > [!NOTE]
    >  Chaque valeur de modificateur apparaît comme une propriété booléenne dans la fenêtre Propriétés. Si vous modifiez un [modificateur](../windows/accelerator-modifier-property.md) valeur dans la fenêtre Propriétés, la table d’accélérateurs traite le nouveau modificateur comme un ajout aux modificateurs déjà présents. Pour cette raison, si vous définissez des valeurs de la modifier, vous devez définir tous les pour vous assurer que chaque accélérateur partage les mêmes paramètres de modificateur.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des Tables d’accélérateurs](../windows/editing-accelerator-tables.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)