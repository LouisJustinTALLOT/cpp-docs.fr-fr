---
title: Création d’une ressource personnalisée ou ressource de données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c82e41544bde9cdd945e23f4ea5884e4e76ae22b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871830"
---
# <a name="creating-a-new-custom-or-data-resource"></a>Création d'une ressource personnalisée ou d'une ressource données
Vous pouvez créer une ressource personnalisée ou une ressource de données en plaçant la ressource dans un fichier distinct à l’aide de la syntaxe de fichier de script de ressource normale, puis en incluant ce fichier en double-cliquant sur votre projet dans l’Explorateur de solutions et en cliquant sur **Include des ressources** dans le menu contextuel.  
  
### <a name="to-create-a-new-custom-or-data-resource"></a>Pour créer une ressource personnalisée ou une ressource de données  
  
1. [Créez un fichier .rc](../windows/how-to-create-a-resource-script-file.md) qui contient la ressource personnalisée ou de données.  
  
     Vous pouvez taper des données personnalisées dans un fichier .rc en tant que chaînes entre guillemets terminées par un caractère Null, ou sous forme d’entiers au format octal, hexadécimal ou décimal.  
  
2.  Dans l’ **Explorateur de solutions**, cliquez sur le fichier .rc de votre projet, puis sur **Include des ressources** dans le menu contextuel.  
  
3.  Dans la zone **Directives de compilation** , tapez une instruction **#include** qui fournit le nom du fichier contenant la ressource personnalisée. Par exemple :  
  
 ```  
    #include mydata.rc  
 ```  
  
     Assurez-vous que la syntaxe et l’orthographe de ce que vous tapez sont correctes. Le contenu de la zone **Directives de compilation** est inséré dans le fichier de script de ressources exactement comme vous l’avez tapé.  
  
4.  Cliquez sur **OK** pour enregistrer les modifications.  
  
 Une autre façon de créer une ressource personnalisée consiste à importer un fichier externe en tant que ressource personnalisée. Pour plus d’informations, consultez [Importation et exportation de ressources](../windows/how-to-import-and-export-resources.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Binary Editor](binary-editor.md)

