---
title: Création de nouvelles barres d’outils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor, creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b61d1c530272ecaba2cbeb36c21e158bd5a6b401
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888078"
---
# <a name="creating-new-toolbars"></a>Création de nouvelles barres d'outils
### <a name="to-create-a-new-toolbar"></a>Pour créer une nouvelle barre d’outils  
  
1.  Dans **ressource** afficher, cliquez sur votre fichier .rc, puis choisissez **ajouter une ressource** dans le menu contextuel. (Si vous avez une barre d’outils existante dans votre fichier .rc, vous pouvez simplement cliquer sur le **barre d’outils** et sélectionnez **insérer une barre d’outils** dans le menu contextuel.)  
  
     **Remarque** Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **barre d’outils** dans les **Type de ressource** liste, puis cliquez sur **nouveau**.  
  
     Si un signe plus (+) s’affiche en regard du **barre d’outils** type de ressource, cela signifie que les modèles de la barre d’outils sont disponibles. Cliquez sur le signe plus pour développer la liste des modèles, sélectionnez un modèle, puis cliquez sur **nouveau**.  
  
     \- ou -  
  
3.  [Convertir une bitmap existante à une barre d’outils](../windows/converting-bitmaps-to-toolbars.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 MFC ou ATL  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de barres d’outils](../windows/toolbar-editor.md)

