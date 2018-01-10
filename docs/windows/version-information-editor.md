---
title: "Éditeur d’informations | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version.F1
dev_langs: C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c221120bf7170025506fe49fe2ab6419ce66044
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="version-information-editor"></a>Éditeur d’informations sur la version
Les informations sur la version sont composées de l’identification de l’entreprise et du produit, d’un numéro de version du produit, et de la notification de copyright et de marque déposée. Avec l’Éditeur d’informations sur la version, vous pouvez créer et tenir à jour ces données, qui sont stockées dans la ressource d’informations sur la version. La ressource d’informations sur la version n’est pas obligatoire pour une application, mais elle est utile pour recueillir des informations qui identifient l’application. Les informations sur la version sont également utilisées par les API d’installation.  
  
 Une ressource d’informations sur la version a un bloc supérieur et un ou plusieurs blocs inférieurs : un bloc d’informations fixes unique en haut et un ou plusieurs blocs d’informations sur la version en bas (pour les autres langues et/ou jeux de caractères). Le bloc supérieur contient des zones numériques modifiables et des listes déroulantes sélectionnables. Les blocs inférieurs contiennent uniquement des zones de texte modifiables.  
  
> [!NOTE]
>  La norme Windows consiste à n’avoir qu’une seule ressource de version, nommée VS_VERSION_INFO.  
  
 L’Éditeur d’informations sur la version vous permet de :  
  
-   [Modifier une chaîne dans une ressource d’informations sur la version](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [Ajouter des informations sur la version pour une autre langue (nouveau bloc d’informations sur la version)](../windows/adding-version-information-for-another-language.md)  
  
-   [Supprimer un bloc d’informations sur la version](../windows/deleting-a-version-information-block.md)  
  
-   [Accéder aux informations sur la version à partir de votre programme](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Quand vous utilisez l’Éditeur d’informations sur la version, dans de nombreux cas vous pouvez cliquer sur le bouton droit de la souris pour afficher un menu contextuel de commandes propres à la ressource. Par exemple, si vous cliquez en pointant sur une entrée d’en-tête de bloc, le menu contextuel affiche les commandes Nouveau bloc d’informations sur la version et Supprimer un bloc d’informations sur la version.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Menus et autres ressources](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

