---
title: Éditeur de chaînes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23211293313135cb0341ac234014ae3c144b7fec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891374"
---
# <a name="string-editor"></a>Éditeur de chaînes
Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.  
  
 Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.  
  
 Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Il est généralement préférable de procéder ainsi plutôt que de rechercher et de remplacer manuellement différentes chaînes dans les fichiers sources.  
  
 Avec l’Éditeur de chaînes, vous pouvez :  
  
-   [Rechercher une ou plusieurs chaînes](../windows/finding-a-string.md)  
  
-   [Insérer rapidement de nouvelles entrées](../windows/adding-or-deleting-a-string.md) dans la table de chaînes  
  
-   [Déplacer une chaîne d’un fichier de ressources vers un autre](../windows/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [Utiliser la modification sur place pour les propriétés ID, Value et Caption](../windows/changing-the-properties-of-a-string.md) et afficher immédiatement les modifications  
  
-   [Modifier la propriété de légende de plusieurs chaînes](../windows/changing-the-caption-property-of-multiple-strings.md)  
  
-   [Ajouter des caractères de mise en forme ou des caractères spéciaux à une chaîne](../windows/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows n’autorise pas la création de tables de chaînes vides. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, et ceci manuellement, consultez [Procédure pas à pas : localisation des applications Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Chaînes](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [À propos des chaînes](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)

