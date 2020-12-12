---
description: 'En savoir plus sur : Comment : gérer des ressources (C++)'
title: 'Comment : gérer les ressources (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 3720cb5f3ab3b99ecba798abce1e4fdba25f8646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329382"
---
# <a name="how-to-manage-resources-c"></a>Comment : gérer les ressources (C++)

## <a name="copy-and-edit-resources"></a>Copier et modifier des ressources

Vous pouvez copier des ressources d’un fichier vers un autre sans les modifier, ou modifier la langue ou la condition d’une ressource lors de sa copie.

Vous pouvez facilement copier des ressources à partir d’une ressource ou d’un fichier exécutable existant dans votre fichier de ressources actuel. Pour copier des ressources, vous devez ouvrir les deux fichiers contenant les ressources en même temps et faire glisser les éléments d’un fichier vers un autre ou les copier et les coller entre les deux fichiers. Cette méthode fonctionne pour les fichiers de script de ressources (. RC) et les fichiers de modèle de ressource (. RCT) et comme fichiers exécutables (. exe).

> [!NOTE]
> Visual C++ comprend des exemples de fichiers de ressources que vous pouvez utiliser dans votre propre application. Pour plus d’informations, consultez [bibliothèque d’images : ressources communes](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general).

Vous ne pouvez pas effectuer des opérations de glisser-déplacer, copier, couper ou coller entre les fichiers de ressources du projet (**affichage des ressources**) et les fichiers. RC autonomes ouverts dans les fenêtres de document. Vous pouvez le faire dans les versions précédentes du produit. Utilisez uniquement la méthode de glisser-déplacer entre les fichiers. RC qui sont ouverts en dehors du projet.

### <a name="to-copy-resources"></a>Pour copier des ressources

1. Ouvrez les deux fichiers de ressources en mode autonome. (Voir [utiliser des fichiers de script de ressources](how-to-create-a-resource-script-file.md#use-resource-script-files)). Par exemple, ouvrez *source1. RC* et *source2. RC*.

1. Dans le premier fichier. RC, soit :

   - Utiliser la méthode de glisser-déplacer

      1. Sélectionnez la ressource que vous souhaitez copier. Par exemple, dans *source1. RC*, sélectionnez **IDD_DIALOG1**.

      1. Maintenez la touche **CTRL** enfoncée et faites glisser la ressource vers le deuxième fichier. rc. Par exemple, faites glisser **IDD_DIALOG1** à partir de *source1. RC* vers *source2. RC*.

         > [!TIP]
         > Le fait de faire glisser la ressource sans maintenir la touche **CTRL** enfoncée déplace la ressource au lieu de la copier.

   - Utiliser la méthode de copie et de collage

      1. Cliquez avec le bouton droit sur la ressource que vous souhaitez copier (par exemple, *source1. RC*) et choisissez **copier**.

      1. Cliquez avec le bouton droit sur le fichier de ressources dans lequel vous souhaitez coller la ressource (par exemple, *source2. RC*) et choisissez **coller**.

> [!NOTE]
> Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ pouvez modifier la valeur de symbole ou le nom et la valeur du symbole de la ressource transférée lorsque vous la copiez dans le nouveau fichier.

Durant la copie d'une ressource, vous pouvez changer sa propriété language ou sa propriété condition, ou les deux.

- La langue d’une ressource spécifie la langue utilisée par [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) pour aider à identifier la ressource que vous recherchez. Les ressources peuvent avoir des différences pour chaque langue qui ne sont pas liées à du texte, par exemple, des accélérateurs qui peuvent uniquement fonctionner sur un clavier japonais ou une bitmap qui serait uniquement appropriée pour les versions localisées en chinois.

- La condition d'une ressource est un symbole défini qui identifie une condition dans laquelle cette copie particulière de la ressource doit être utilisée.

La langue et la condition d’une ressource sont indiquées entre parenthèses après le nom de la ressource dans la fenêtre de l' **espace de travail** . Ici, la ressource nommée `IDD_AboutBox` utilise `Finnish` comme langue et sa condition est `XX33` :

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Pour copier une ressource existante et modifier sa langue ou sa condition

Dans le fichier *. RC* ou dans la fenêtre de [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) , cliquez avec le bouton droit sur la ressource que vous souhaitez copier, puis choisissez **Insérer une copie**. Ensuite, définissez les éléments suivants :

- Pour la zone de liste **langue** , sélectionnez la langue.

- Dans la zone **condition** , tapez la condition.

### <a name="to-edit-resources"></a>Pour modifier des ressources

Les fichiers de ressources managées (. resx) sont des fichiers XML. Lorsque vous ajoutez un fichier de ressources managé à votre projet à partir de la boîte de dialogue **Ajouter un nouvel élément** , l' **éditeur de ressources managées** s’ouvre par défaut.

## <a name="import-and-export-resources"></a>importer et exporter des ressources

Vous pouvez importer des ressources graphiques (images bitmap, icônes, curseurs et barres d'outils), des fichiers HTML et des ressources personnalisées pour les utiliser dans Visual C++. Vous pouvez exporter les mêmes types de fichiers à partir d’un projet Visual Studio C++ vers des fichiers distincts qui peuvent être utilisés en dehors de l’environnement de développement.

> [!NOTE]
> Les types de ressources tels que les accélérateurs, les boîtes de dialogue et les tables de chaînes ne peuvent pas être importés ou exportés, car ils ne sont pas des types de fichiers autonomes.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Pour importer une ressource dans le fichier de script de ressources

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) cliquez avec le bouton droit sur le nœud du fichier de script de ressources (. RC) auquel vous souhaitez ajouter une ressource, puis sélectionnez **Importer**.

1. Recherchez et choisissez le nom de fichier de l’image bitmap (. bmp), de l’icône (. ico), du curseur (. cur), du fichier HTML (. htm) ou de tout autre fichier à importer.

1. Sélectionnez **OK** pour ajouter la ressource au fichier de script de ressources.

> [!NOTE]
> Le processus d’importation fonctionne de la même façon quel que soit le type de ressource que vous avez sélectionné. La ressource importée est automatiquement ajoutée au nœud approprié de ce type de ressource.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Pour exporter une ressource en vue d’une utilisation en dehors de Visual C++

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur la ressource que vous souhaitez exporter, puis sélectionnez **Exporter**. Vous pouvez accepter le nom de fichier actuel ou en taper un nouveau.

1. Accédez au dossier dans lequel vous souhaitez enregistrer le fichier, puis sélectionnez **Exporter**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Comment : créer des ressources](../windows/how-to-create-a-resource-script-file.md)<br/>
[Comment : inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)
