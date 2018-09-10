---
title: Création d’une ressource personnalisée ou la ressource de données (C++) | Microsoft Docs
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
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a92e7904b3b42422bebf5a80e0f1b03dd818f86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314577"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>Création d’une ressource personnalisée ou la ressource de données (C++)

Vous pouvez créer une nouvelle ressource personnalisée ou de données en plaçant la ressource dans un fichier distinct à l’aide de la syntaxe de fichier de script (.rc) de ressource normale, puis en incluant ce fichier en double-cliquant sur votre projet dans **l’Explorateur de solutions** et en cliquant sur  **Inclut des ressources** dans le menu contextuel.

### <a name="to-create-a-new-custom-or-data-resource"></a>Pour créer une ressource personnalisée ou une ressource de données

1. [Créez un fichier .rc](../windows/how-to-create-a-resource-script-file.md) qui contient la ressource personnalisée ou de données.

   Vous pouvez taper des données personnalisées dans un fichier .rc en tant que chaînes entre guillemets terminées par un caractère Null, ou sous forme d’entiers au format octal, hexadécimal ou décimal.

2. Dans l’ **Explorateur de solutions**, cliquez sur le fichier .rc de votre projet, puis sur **Include des ressources** dans le menu contextuel.

3. Dans le **Directives de compilation** , tapez un `#include` instruction qui fournit le nom du fichier contenant la ressource personnalisée. Exemple :

```cpp
    #include mydata.rc
 ```

   Assurez-vous que la syntaxe et l’orthographe de ce que vous tapez sont correctes. Le contenu de la zone **Directives de compilation** est inséré dans le fichier de script de ressources exactement comme vous l’avez tapé.

4. Cliquez sur **OK** pour enregistrer les modifications.

Une autre façon de créer une ressource personnalisée consiste à importer un fichier externe en tant que ressource personnalisée. Pour plus d’informations, consultez [Importation et exportation de ressources](../windows/how-to-import-and-export-resources.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Binary Editor](binary-editor.md)