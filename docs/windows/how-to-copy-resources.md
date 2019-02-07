---
title: 'Procédure : Copier les ressources (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 772c9b905d4cb0c4e2ccab9ec51aa02860b2db32
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849659"
---
# <a name="how-to-copy-resources-c"></a>Procédure : Copier les ressources (C++)

Vous pouvez copier des ressources à partir d’un fichier vers un autre sans les modifier, ou vous pouvez modifier la langue ou la condition d’une ressource lors de la copie.

Vous pouvez facilement copier les ressources à partir d’une ressource existante ou d’un fichier exécutable à votre fichier de ressources actuel. Pour copier des ressources, vous ouvrez les deux fichiers contenant des ressources en même temps et faire glisser des éléments à partir d’un fichier vers un autre, ou copiez et collez entre les deux fichiers. Cette méthode fonctionne pour les fichiers de script (.rc) de ressources et les fichiers de ressources (.rct) de modèle et en tant que fichiers exécutables (.exe).

> [!NOTE]
> Visual C++ inclut des exemples de fichiers de ressources que vous pouvez utiliser dans votre propre application. Pour plus d’informations, consultez [CLIPART : Ressources communes](https://github.com/Microsoft/VCSamples).

Vous pouvez utiliser la méthode glisser-déplacer entre les fichiers .rc qui sont ouverts [en dehors du projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

## <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Pour copier des ressources entre les fichiers à l’aide de la méthode glisser-déplacer

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, ouvrez Source1.rc et Source2.rc.

1. Dans le premier fichier .rc, sélectionnez la ressource que vous souhaitez copier. Par exemple, dans `Source1.rc`, sélectionnez **IDD_DIALOG1**.

1. Maintenez la **Ctrl** de clé et faites glisser la ressource pour le deuxième fichier .rc. Par exemple, faites glisser **IDD_DIALOG1** de `Source1.rc` à `Source2.rc`.

   > [!NOTE]
   > En faisant glisser la ressource sans maintenir enfoncée la **Ctrl** touche déplace la ressource plutôt que de le copier.

## <a name="to-copy-resources-using-copy-and-paste"></a>Ressources à l’aide de la copie de copier et coller

1. Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, Source1.rc et Source2.rc.

1. Dans le fichier source à partir de laquelle vous souhaitez copier une ressource (par exemple, `Source1.rc`), cliquez sur une ressource et choisissez **copie** dans le menu contextuel.

1. Cliquez sur le fichier de ressources dans lequel vous souhaitez coller la ressource (par exemple, `Source2.rc`). Choisissez **coller** dans le menu contextuel.

   > [!NOTE]
   > Vous ne pouvez pas faire glisser et drop, copier, Couper ou -coller entre les fichiers de ressources dans le projet (**affichage des ressources**) et les fichiers .rc autonome (ceux qui sont ouverts dans les fenêtres de document). Vous le faisiez dans les versions précédentes du produit.

   > [!NOTE]
   > Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ peut modifier les valeur de symbole de la ressource transférée ou le nom et valeur lorsque vous la copiez dans le nouveau fichier.

## <a name="to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Pour modifier la langue ou la condition d’une ressource lors de la copie (C++)

Durant la copie d'une ressource, vous pouvez changer sa propriété language ou sa propriété condition, ou les deux.

- La langue de la ressource identifie simplement la langue correspondant à la ressource. La langue est utilisée par [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) pour aider à identifier la ressource pour laquelle vous avez besoin. (Toutefois, les ressources peuvent avoir des différences qui ne sont pas liées au texte pour chaque langue, par exemple, génère les accélérateurs qui fonctionnent uniquement sur un clavier japonais ou une image bitmap n’est appropriée pour localisées en chinois)

- La condition d'une ressource est un symbole défini qui identifie une condition dans laquelle cette copie particulière de la ressource doit être utilisée.

La langue et la condition d'une ressource sont affichées entre parenthèses après le nom de la ressource dans la fenêtre Espace de travail. Dans cet exemple, la ressource nommée IDD_AboutBox utilise le finnois comme langue et sa condition est XX33.

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Pour copier une ressource existante et modifier sa langue ou sa condition

1. Dans le fichier .rc ou dans le [affichage des ressources](../windows/resource-view-window.md) fenêtre, avec le bouton droit de la ressource que vous souhaitez copier.

1. Choisissez **insérer une copie** dans le menu contextuel.

1. Dans le **insérer une copie de ressources** boîte de dialogue :

   - Pour le **langage** zone de liste, sélectionnez la langue.

   - Dans le **Condition** , tapez la condition.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Guide pratique pour ouvrir un fichier de script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
