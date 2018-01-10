---
title: Fichiers de ressources (Visual Studio) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 117472c764dd6f13858881275b067600579a0fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="resource-files-visual-studio"></a>Fichiers de ressources (Visual Studio)
> [!NOTE]
>  Ces informations s’appliquent aux applications de bureau Windows. Pour plus d’informations sur les ressources dans les applications de plateforme Windows universelle, consultez [définition des ressources d’application](http://msdn.microsoft.com/en-us/476ea844-632c-4467-9ce3-966be1350dd4).  
>   
> Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
>  
> Comme les projets écrits dans les langages de programmation .NET managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de l’ **Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.  
  
 Le terme « fichier de ressource » peut faire référence à différents types de fichiers, notamment :  
  
-   Le fichier de script de ressources (.rc) d’un programme  
  
-   Un fichier de modèle de ressource (.rct)  
  
-   Une ressource individuelle existant en tant que fichier autonome, telle qu’une bitmap, une icône ou un fichier curseur référencé à partir d’un fichier .rc  
  
-   Un fichier d’en-tête généré par l’environnement de développement, par exemple Resource.h, référencé à partir d’un fichier .rc  
  
 Il existe aussi des ressources dans d’ [autres types de fichiers](../windows/editable-file-types-for-resources.md) , tels que les fichiers .exe, .dll et .res. Vous pouvez travailler avec des ressources et des fichiers de ressources à partir de votre projet et avec ceux qui ne font pas partie de votre projet actif. Vous pouvez également travailler avec des fichiers de ressources qui n’ont pas été créés dans l’environnement de développement de Visual Studio. Par exemple, vous pouvez :  
  
-   Travailler avec des fichiers de ressources imbriqués et inclus de manière conditionnelle  
  
-   Mettre à jour des ressources existantes ou les convertir au format Visual C++  
  
-   Importer ou exporter des ressources graphiques vers ou à partir de votre fichier de ressources actif  
  
-   Inclure des identificateurs partagés ou en lecture seule  (symboles) qui ne peuvent pas être modifiés par l’environnement de développement  
  
-   Inclure dans votre fichier exécutable (.exe) des ressources qui ne nécessitent pas de modification (ou que vous ne voulez pas voir modifiées) pendant votre projet actif, telles que des ressources partagées entre plusieurs projets  
  
-   Inclure des types de ressources non pris en charge par l’environnement de développement  
  
 Cette section traite des sujets suivants :  
  
-   [Création d’un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md)  
  
-   [Création d’une ressource](../windows/how-to-create-a-resource.md)  
  
-   [Affichage de ressources dans un fichier de script de ressources](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [Ouverture d’un fichier de script de ressources au format texte](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [Inclusion de ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [Copie de ressources](../windows/how-to-copy-resources.md)  
  
-   [Utilisation de modèles de ressources (.rct)](../windows/how-to-use-resource-templates.md)  
  
-   [Importation et exportation de ressources](../windows/how-to-import-and-export-resources.md)  
  
-   [Types de fichier modifiables pour les ressources](../windows/editable-file-types-for-resources.md)  
  
-   [Fichiers affectés par la modification des ressources](../windows/files-affected-by-resource-editing.md)  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)   
 [Menus et autres ressources](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

