---
title: Enregistrement de Bitmaps au format GIF ou JPEG (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e8ec15272fd9e49173149655c0806f7873f2a1d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590952"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Enregistrement de bitmaps au format GIF ou JPEG (Éditeur d'images pour les icônes)

Lorsque vous créez une image bitmap, l’image est créée au format bitmap (.bmp). Vous pouvez, toutefois, enregistrer l’image au format GIF ou JPEG ou dans d’autres formats graphiques.

> [!NOTE]
> Ce processus ne s’applique pas aux icônes et curseurs.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Pour créer et enregistrer une image bitmap en tant que .gif ou .jpeg

1. À partir de la **fichier** menu, choisissez **Open**, puis cliquez sur **fichier**.

2. Dans le **boîte de dialogue Nouveau fichier**, cliquez sur le **Visual C++** dossier, puis sélectionnez **fichier Bitmap (.bmp)** dans le **modèles** , puis cliquez sur  **Ouvrez**.

   La bitmap s’ouvre dans le **Image** éditeur.

3. Apportez des modifications à votre nouvelle image bitmap en fonction des besoins.

4. Avec la bitmap est ouverte dans le **Image** éditeur, cliquez sur **enregistrer *filename*.bmp comme** sur le **fichier** menu.

5. Dans le **enregistrer le fichier sous** boîte de dialogue, tapez le nom que vous souhaitez attribuer au fichier et l’extension qui dénote le format de fichier dans le **nom de fichier** boîte. Par exemple, *MonFichier.gif*.

   > [!NOTE]
   > Vous devez créer ou ouvrir l’image bitmap en dehors de votre projet afin d’enregistrer dans un autre format de fichier. Si vous créez ou ouvrez dans votre projet, le **enregistrer en tant que** n’est pas disponible. Pour plus d’informations, consultez [affichage des ressources dans un fichier de Script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

6. Cliquez sur **Enregistrer**.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="see-also"></a>Voir aussi

[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)