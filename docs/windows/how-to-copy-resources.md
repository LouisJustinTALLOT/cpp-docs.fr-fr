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
ms.openlocfilehash: 6b9499fbd806c04774d12750c70816d0312a4e3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345264"
---
# <a name="how-to-manage-resources-c"></a>Procédure : Gérer les ressources (C++)

## <a name="copy-and-edit-resources"></a>Copie et ressources pour la modification

Vous pouvez copier des ressources à partir d’un fichier vers un autre sans les modifier, ou de modifier la langue ou la condition d’une ressource lors de la copie.

Vous pouvez facilement copier les ressources à partir d’une ressource existante ou d’un fichier exécutable à votre fichier de ressources actuel. Pour copier des ressources, vous ouvrez les deux fichiers contenant des ressources en même temps et faire glisser des éléments à partir d’un fichier vers un autre, ou copiez et collez entre les deux fichiers. Cette méthode fonctionne pour les fichiers de script (.rc) de ressources et les fichiers de ressources (.rct) de modèle et en tant que fichiers exécutables (.exe).

> [!NOTE]
> Visual C++ inclut des exemples de fichiers de ressources que vous pouvez utiliser dans votre propre application. Pour plus d’informations, consultez [CLIPART : Ressources communes](https://github.com/Microsoft/VCSamples).

Vous ne pouvez pas faire glisser et drop, copier, Couper ou -coller entre les fichiers de ressources dans le projet (**affichage des ressources**) et ouvrent des fichiers .rc autonome dans les fenêtres de document. Vous le faisiez dans les versions précédentes du produit. Utilisez uniquement la méthode glisser-déplacer entre les fichiers .rc qui sont ouverts en dehors du projet.

### <a name="to-copy-resources"></a>Pour copier des ressources

1. Ouvrez les deux fichiers de ressources en mode autonome. (Consultez [utilisent les fichiers de script de ressources](how-to-create-a-resource-script-file.md#use-resource-script-files)). Par exemple, ouvrez *Source1.rc* et *Source2.rc*.

1. À l’intérieur du premier fichier .rc, soit :

   - Utilisez la méthode glisser-déplacer

      1. Sélectionnez la ressource que vous souhaitez copier. Par exemple, dans *Source1.rc*, sélectionnez **IDD_DIALOG1**.

      1. Maintenez la **Ctrl** de clé et faites glisser la ressource pour le deuxième fichier .rc. Par exemple, faites glisser **IDD_DIALOG1** de *Source1.rc* à *Source2.rc*.

         > [!TIP]
         > En faisant glisser la ressource sans maintenir enfoncée la **Ctrl** touche déplace la ressource plutôt que de le copier.

   - Utilisez le copier-coller (méthode)

      1. Avec le bouton droit de la ressource vous avec copie (par exemple, *Source1.rc*) et choisissez **copie**.

      1. Cliquez sur le fichier de ressources dans lequel vous souhaitez coller la ressource (par exemple, *Source2.rc*) et choisissez **collez**.

> [!NOTE]
> Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ peut modifier les valeur de symbole de la ressource transférée ou le nom et valeur lorsque vous la copiez dans le nouveau fichier.

Durant la copie d'une ressource, vous pouvez changer sa propriété language ou sa propriété condition, ou les deux.

- La langue d’une ressource spécifie la langue utilisée par [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) pour aider à identifier la ressource pour laquelle vous avez besoin. Les ressources peuvent avoir des différences qui ne sont pas liées au texte pour chaque langue, par exemple, des accélérateurs qui fonctionnent uniquement sur un clavier japonais ou une image bitmap n’est appropriée pour localisées en chinois builds.

- La condition d'une ressource est un symbole défini qui identifie une condition dans laquelle cette copie particulière de la ressource doit être utilisée.

La langue et la condition d’une ressource sont affichées entre parenthèses après le nom de la ressource dans le **espace de travail** fenêtre. Ici, la ressource nommée `IDD_AboutBox` utilise `Finnish` en tant que son langage et sa condition est `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Pour copier une ressource existante et modifier sa langue ou sa condition

Dans le *.rc* fichier ou dans le [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) fenêtre, avec le bouton droit de la ressource que vous souhaitez copier et choisissez **insérer une copie**. Ensuite, définissez les éléments suivants :

- Pour le **langage** zone de liste, sélectionnez la langue.

- Dans le **Condition** , tapez la condition.

### <a name="to-edit-resources"></a>Pour modifier des ressources

Fichiers de ressources managés (.resx) sont des fichiers XML. Lorsque vous ajoutez un fichier de ressources managé à votre projet à partir de la **ajouter un nouvel élément** boîte de dialogue, le **éditeur de ressources managées** s’ouvre par défaut.

## <a name="import-and-export-resources"></a>Importation et exportation de ressources

Vous pouvez importer des ressources graphiques (images bitmap, icônes, curseurs et barres d'outils), des fichiers HTML et des ressources personnalisées pour les utiliser dans Visual C++. Vous pouvez exporter les mêmes types de fichier depuis un projet Visual C++ vers des fichiers distincts utilisables en dehors de l'environnement de développement.

> [!NOTE]
> Types de ressources tels que les accélérateurs, les boîtes de dialogue et les tables de chaînes ne peuvent pas être importées ou exportées, car ils ne sont pas des types de fichiers autonome.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Pour importer une ressource dans le fichier de script de ressources

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) cliquez sur le nœud du fichier de script (.rc) de ressources auquel vous souhaitez ajouter une ressource, puis sélectionnez **importation**.

1. Recherchez et choisissez le nom de fichier de l’image bitmap (.bmp), icône (.ico), curseur (.cur), le fichier html (.htm) ou un autre fichier à importer.

1. Sélectionnez **OK** pour ajouter la ressource au fichier de script de ressources.

> [!NOTE]
> Le processus d’importation fonctionne sans quel que soit le type de ressource auquel vous avez sélectionné. La ressource importée est automatiquement ajoutée au nœud correct de ce type de ressource.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Pour exporter une ressource pour une utilisation en dehors de Visual C++

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), avec le bouton droit de la ressource que vous souhaitez exporter, puis sélectionnez **exporter**. Vous pouvez accepter le nom de fichier en cours ou tapez-en un nouveau.

1. Accédez au dossier où vous souhaitez enregistrer le fichier et sélectionnez **exporter**.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Guide pratique pour Créer des ressources](../windows/how-to-create-a-resource-script-file.md)<br/>
[Guide pratique pour inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)<br/>