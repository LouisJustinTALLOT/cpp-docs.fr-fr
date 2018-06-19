---
title: Éditeur d’accélérateurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator.F1
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e5ce1fcd71f6f49532d083c7cb2dcfce9ed644c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856415"
---
# <a name="accelerator-editor"></a>Éditeur d’accélérateurs
Une table d’accélérateurs est une ressource Windows qui contient une liste de touches accélérateur (également appelées touches de raccourci) et les identificateurs de commandes qui leur sont associés. Un programme peut avoir plusieurs tables d’accélérateurs.  
  
 Normalement, les accélérateurs sont utilisés comme raccourcis clavier pour des commandes de programme qui sont également disponibles dans un menu ou une barre d’outils. Toutefois, vous pouvez utiliser la table d’accélérateurs pour définir des combinaisons de touches pour des commandes qui ne sont associées à aucun objet d’interface utilisateur.  
  
 Vous pouvez utiliser [Affichage de classes](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) pour raccorder des commandes de touches accélérateur à du code.  
  
 Avec l’éditeur d’accélérateurs, vous pouvez :  
  
-   [Définir des propriétés d’accélérateurs](../windows/setting-accelerator-properties.md)  
  
-   [Associer une touche accélérateur à un élément de menu](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Modifier des tables d’accélérateurs](../windows/editing-accelerator-tables.md)  
  
-   [Utiliser des touches accélérateur prédéfinies](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Lorsque vous utilisez l’éditeur d’accélérateurs, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel de commandes fréquemment utilisées. Les commandes disponibles varient selon la cible du pointeur.  
  
    > [!NOTE]
    >  Windows ne vous permet pas de créer des tables d’accélérateurs vides. Si vous créez une table d’accélérateurs sans entrée, elle est supprimée automatiquement lorsque vous l’enregistrez.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)

