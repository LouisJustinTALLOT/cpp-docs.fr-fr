---
title: 'Procédure : Gérer les ressources (C++)'
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
ms.openlocfilehash: 1f176b3fa19374b402039ecca60e690ade5c0cef
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320625"
---
# <a name="how-to-manage-resources-c"></a>Procédure : Gérer les ressources (C++)

## <a name="copy-resources"></a>Copier les ressources

Vous pouvez copier des ressources à partir d’un fichier vers un autre sans les modifier, ou vous pouvez modifier la langue ou la condition d’une ressource lors de la copie.

Vous pouvez facilement copier les ressources à partir d’une ressource existante ou d’un fichier exécutable à votre fichier de ressources actuel. Pour copier des ressources, vous ouvrez les deux fichiers contenant des ressources en même temps et faire glisser des éléments à partir d’un fichier vers un autre, ou copiez et collez entre les deux fichiers. Cette méthode fonctionne pour les fichiers de script (.rc) de ressources et les fichiers de ressources (.rct) de modèle et en tant que fichiers exécutables (.exe).

> [!NOTE]
> Visual C++ inclut des exemples de fichiers de ressources que vous pouvez utiliser dans votre propre application. Pour plus d’informations, consultez [CLIPART : Ressources communes](https://github.com/Microsoft/VCSamples).

Vous pouvez utiliser la méthode glisser-déplacer entre les fichiers .rc qui sont ouverts [en dehors du projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Pour copier des ressources entre les fichiers à l’aide de la méthode glisser-déplacer

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [afficher les ressources dans un fichier .rc en dehors d’un projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, ouvrez *Source1.rc* et *Source2.rc*.

1. Dans le premier fichier .rc, sélectionnez la ressource que vous souhaitez copier. Par exemple, dans *Source1.rc*, sélectionnez **IDD_DIALOG1**.

1. Maintenez la **Ctrl** de clé et faites glisser la ressource pour le deuxième fichier .rc. Par exemple, faites glisser **IDD_DIALOG1** de *Source1.rc* à *Source2.rc*.

   > [!NOTE]
   > En faisant glisser la ressource sans maintenir enfoncée la **Ctrl** touche déplace la ressource plutôt que de le copier.

### <a name="to-copy-resources-using-copy-and-paste"></a>Ressources à l’aide de la copie de copier et coller

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [afficher les ressources dans un fichier .rc en dehors d’un projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, *Source1.rc* et *Source2.rc*.

1. Dans le fichier source à partir de laquelle vous souhaitez copier une ressource (par exemple, *Source1.rc*), cliquez sur une ressource et choisissez **copie** dans le menu contextuel.

1. Cliquez sur le fichier de ressources dans lequel vous souhaitez coller la ressource (par exemple, *Source2.rc*). Choisissez **coller** dans le menu contextuel.

   > [!NOTE]
   > Vous ne pouvez pas faire glisser et drop, copier, Couper ou -coller entre les fichiers de ressources dans le projet (**affichage des ressources**) et les fichiers .rc autonome (ceux qui sont ouverts dans les fenêtres de document). Vous le faisiez dans les versions précédentes du produit.

   > [!NOTE]
   > Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ peut modifier les valeur de symbole de la ressource transférée ou le nom et valeur lorsque vous la copiez dans le nouveau fichier.

### <a name="change-the-language-or-condition-of-a-resource-while-copying"></a>Modifier la langue ou la condition d’une ressource lors de la copie

Durant la copie d'une ressource, vous pouvez changer sa propriété language ou sa propriété condition, ou les deux.

- La langue de la ressource identifie simplement la langue correspondant à la ressource. La langue est utilisée par [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) pour aider à identifier la ressource pour laquelle vous avez besoin. (Toutefois, les ressources peuvent avoir des différences qui ne sont pas liées au texte pour chaque langue, par exemple, génère les accélérateurs qui fonctionnent uniquement sur un clavier japonais ou une image bitmap n’est appropriée pour localisées en chinois)

- La condition d'une ressource est un symbole défini qui identifie une condition dans laquelle cette copie particulière de la ressource doit être utilisée.

La langue et la condition d’une ressource sont affichées entre parenthèses après le nom de la ressource dans le **espace de travail** fenêtre. Dans cet exemple, la ressource nommée `IDD_AboutBox` utilise `Finnish` en tant que son langage et sa condition est `XX33`.

```cpp
IDD_AboutBox (Finnish - XX33)
```

#### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Pour copier une ressource existante et modifier sa langue ou sa condition

1. Dans le fichier .rc ou dans le [affichage des ressources](../windows/resource-view-window.md) fenêtre, avec le bouton droit de la ressource que vous souhaitez copier.

1. Choisissez **insérer une copie** à partir du menu contextuel et un ensemble les éléments suivants :

   - Pour le **langage** zone de liste, sélectionnez la langue.

   - Dans le **Condition** , tapez la condition.

## <a name="edit-resources"></a>Modifier des ressources

Fichiers de ressources managés (.resx) sont des fichiers XML. Lorsque vous ajoutez un fichier de ressources managé à votre projet à partir de la **ajouter un nouvel élément** boîte de dialogue, le **éditeur de ressources managées** s’ouvre par défaut.

## <a name="import-and-export-resources"></a>Importation et exportation de ressources

Vous pouvez importer des ressources graphiques (images bitmap, icônes, curseurs et barres d'outils), des fichiers HTML et des ressources personnalisées pour les utiliser dans Visual C++. Vous pouvez exporter les mêmes types de fichier depuis un projet Visual C++ vers des fichiers distincts utilisables en dehors de l'environnement de développement.

> [!NOTE]
> Les types de ressource tels que les accélérateurs, les boîtes de dialogue et les tables de chaînes ne peuvent pas être importés ou exportés, car il ne s'agit pas de types de fichier autonomes.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Pour importer une ressource individuelle dans votre fichier de ressources actuel

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur le nœud pour le script de ressources (* .rc) auquel vous souhaitez ajouter une ressource de fichier.

1. Sélectionnez **importation** dans le menu contextuel.

1. Recherchez et sélectionnez le nom de fichier de l'image bitmap (.bmp), de l'icône (.ico), du curseur (.cur), du fichier HTML (.htm), ou de tout autre fichier que vous souhaitez importer.

1. Choisissez **OK** pour ajouter la ressource au fichier sélectionné dans **ressource** vue.

   > [!NOTE]
   > Le processus d'importation fonctionne de la même façon, quel que soit le type de ressource que vous avez sélectionné. La ressource importée est automatiquement ajoutée au nœud approprié pour ce type de ressource.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Pour exporter une image bitmap, une icône ou un curseur en tant que fichier distinct (pour une utilisation en dehors de Visual C++)

1. Dans **ressource** , cliquez sur la ressource que vous voulez exporter.

1. Sélectionnez **exporter** dans le menu contextuel et acceptez le nom de fichier actuel, ou tapez-en un nouveau.

1. Accédez au dossier où vous souhaitez enregistrer le fichier et choisissez **exporter**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Créer des ressources](../windows/how-to-create-a-resource-script-file.md)<br/>
[Inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)<br/>