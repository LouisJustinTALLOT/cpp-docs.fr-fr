---
title: Conversion d’une Image d’un Format à un autre (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 0409c2bd-3bd8-4d72-9c71-c683b6cf51be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ef3a2ce99309781ecbfd0c406fe8e0f6f7e0613
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592116"
---
# <a name="converting-an-image-from-one-format-to-another-image-editor-for-icons"></a>Conversion d'une image d'un format à un autre (Éditeur d'images pour les icônes)

Vous pouvez ouvrir des images GIF ou JPEG dans la **Image** éditeur et enregistrez-les en tant que les bitmaps. En outre, vous pouvez ouvrir un fichier bitmap et enregistrez-le au format GIF ou JPEG. Vous travaillez avec des images ne sont pas nécessairement partie d’un projet pour le modifier dans l’environnement de développement (consultez [modification d’image autonome](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

### <a name="to-convert-an-image-from-one-format-to-another"></a>Pour convertir une image d’un format vers un autre

1. Ouvrir l’image dans le **Image** éditeur.

2. À partir de la **fichier** menu, choisissez **enregistrer *filename* comme**.

3. Dans le **enregistrer le fichier sous** boîte de dialogue le **nom de fichier** , tapez le nom de fichier et l’extension qui dénote le format souhaité.

4. Cliquez sur **Enregistrer**.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)