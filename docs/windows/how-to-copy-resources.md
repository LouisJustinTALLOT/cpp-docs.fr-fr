---
title: 'Comment : copier des ressources (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05f4fbfba70b0c97341749fd7e71064487eef9a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439898"
---
# <a name="how-to-copy-resources-c"></a>Comment : copier des ressources (C++)

Vous pouvez copier des ressources à partir d’un fichier vers un autre sans les modifier ou vous pouvez [modifier la langue ou la condition d’une ressource lors de la copie](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).

Vous pouvez facilement copier les ressources à partir d’une ressource existante ou d’un fichier exécutable à votre fichier de ressources actuel. Pour ce faire, vous ouvrez les deux fichiers contenant des ressources en même temps et faire glisser des éléments à partir d’un fichier vers un autre, ou copiez et collez entre les deux fichiers. Cette méthode fonctionne pour les fichiers de script (.rc) de ressources et les fichiers de ressources (.rct) de modèle, ainsi que les fichiers exécutables (.exe).

> [!NOTE]
> Visual C++ inclut des exemples de fichiers de ressources que vous pouvez utiliser dans votre propre application. Pour plus d’informations, consultez [CLIPART : ressources communes](https://github.com/Microsoft/VCSamples).

Vous pouvez utiliser la méthode glisser-déplacer entre les fichiers .rc qui sont ouverts [en dehors du projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Pour copier des ressources entre les fichiers à l’aide de la méthode glisser-déplacer

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, ouvrez Source1.rc et Source2.rc.

2. Dans le premier fichier .rc, cliquez sur la ressource que vous souhaitez copier. Par exemple, dans `Source1.rc`, cliquez sur **IDD_DIALOG1**.

3. Maintenez la touche CTRL enfoncée et faites glisser la ressource pour le deuxième fichier .rc. Par exemple, faites glisser **IDD_DIALOG1** de `Source1.rc` à `Source2.rc`.

   > [!NOTE]
   > En faisant glisser la ressource sans maintenir enfoncée la **Ctrl** touche déplace la ressource plutôt que de le copier.

### <a name="to-copy-resources-using-copy-and-paste"></a>Ressources à l’aide de la copie de copier et coller

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, Source1.rc et Source2.rc.

2. Dans le fichier source à partir de laquelle vous souhaitez copier une ressource (par exemple, `Source1.rc`), cliquez sur une ressource et choisissez **copie** dans le menu contextuel.

3. Cliquez sur le fichier de ressources dans lequel vous souhaitez coller la ressource (par exemple, `Source2.rc`). Choisissez **coller** dans le menu contextuel.

   > [!NOTE]
   > Vous ne pouvez pas faire glisser et drop, copier, Couper ou -coller entre les fichiers de ressources dans le projet (**affichage des ressources**) et les fichiers .rc autonome (ceux qui sont ouverts dans les fenêtres de document). Vous le faisiez dans les versions précédentes du produit.

   > [!NOTE]
   > Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ peut modifier les valeur de symbole de la ressource transférée ou le nom et valeur lorsque vous la copiez dans le nouveau fichier.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour ouvrir un fichier de script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)