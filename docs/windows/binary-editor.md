---
title: Éditeur binaire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d5deb511069830de5ea7aa542bb010f57be5af9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857855"
---
# <a name="binary-editor"></a>éditeur binaire
> [!WARNING]
>  L’éditeur binaire n’est pas disponible dans les éditions Express.  
  
 L’éditeur binaire vous permet de modifier n’importe quelle ressource au niveau binaire au format hexadécimal ou ASCII. Vous pouvez également utiliser la [commande Rechercher](/visualstudio/ide/reference/find-command) pour rechercher des chaînes ASCII ou des octets hexadécimaux. Vous devez utiliser l’éditeur binaire uniquement lorsque vous avez besoin d’afficher ou d’apporter des modifications mineures à des ressources personnalisées ou à des types de ressources non pris en charge par l’environnement Visual Studio.  
  
 Pour ouvrir l’éditeur binaire, choisissez **fichier &#124; nouveau &#124; fichier** dans le menu principal, sélectionnez le fichier que vous souhaitez modifier, puis cliquez sur la flèche à côté du **ouvrir** bouton et choisissez **Ouvrir avec &#124; éditeur binaire**.  
  
> [!CAUTION]
>  Modifier des ressources telles que des boîtes de dialogue, des images ou des menus dans l’éditeur binaire est une opération dangereuse. Une modification incorrecte peut endommager la ressource et la rendre illisible dans son éditeur natif.  
  
> [!TIP]
>  Quand vous utilisez l’éditeur binaire, dans de nombreux cas vous pouvez cliquer sur le bouton droit de la souris pour afficher un menu contextuel de commandes propres à la ressource. Les commandes disponibles varient selon la cible du pointeur. Par exemple, si vous cliquez en pointant sur l’éditeur binaire avec des valeurs hexadécimales sélectionnées, le menu contextuel affiche les commandes **Couper**, **Copier**et **Coller** .  
  
 Dans l’éditeur binaire, vous pouvez :  
  
-   [Ouvrir une ressource à des fins d’édition binaire](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [Modifier des données binaires](../windows/editing-binary-data.md)  
  
-   [Rechercher des données binaires](../windows/finding-binary-data.md)  
  
-   [Créer une ressource personnalisée ou une ressource de données](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>Ressources managées  
 Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’éditeur binaire pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)

