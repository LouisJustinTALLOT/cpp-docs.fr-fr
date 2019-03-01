---
title: Éditeurs de ressources (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: 118744f70242b511930399c5786035493e9b7cf0
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210742"
---
# <a name="resource-editors-c"></a>Éditeurs de ressources (C++)

Un **éditeur de ressources** est un environnement spécialisé pour créer ou modifier des ressources qui sont inclus dans un projet Visual Studio. Les éditeurs de ressources de Visual Studio partagent des techniques et des interfaces pour vous aider à créer et à modifier rapidement et facilement des ressources d’application. Éditeurs de ressources permettent d’afficher et modifier les ressources dans les ressources appropriées de l’éditeur et l’aperçu.

L’éditeur approprié s’ouvre automatiquement quand vous créez ou que vous ouvrez une ressource.

> [!NOTE]
> Étant donné que les projets managés n’utilisent pas les fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

|Utilisez|Pour modifier|
|----------------|----------------|
|[Éditeur d’accélérateurs](../windows/accelerator-editor.md)|Tables d’accélérateurs dans les projets Visual C++.|
|[Binary Editor](binary-editor.md)|Informations de données binaires et ressources personnalisées dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)|Boîtes de dialogue dans des projets Visual C++.|
|[Image Editor](../windows/image-editor-for-icons.md)|Bitmaps, icônes, curseurs et autres fichiers image dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de menus](../windows/menu-editor.md)|Ressources de menu dans des projets Visual C++.|
|[Éditeur Ribbon](../mfc/ribbon-designer-mfc.md)|Ressources de ruban dans les projets MFC.|
|[Éditeur de chaînes](../windows/string-editor.md)|Tableaux de chaînes dans des projets Visual C++.|
|[Éditeur de barres d’outils](../windows/toolbar-editor.md)|Ressources de barre d’outils dans des projets Visual C++. L’éditeur de la barre d’outils fait partie de l’éditeur d’images.|
|[Éditeur d’informations sur la version](../windows/version-information-editor.md)|Informations de version dans des projets Visual C++.|

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Comment : Créer des ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Affichage et ressources pour la modification

Chaque type de ressource a un **éditeur de ressources** spécifiques à ce type de ressource. Vous pouvez réorganiser, redimensionner, ajouter des contrôles et fonctionnalités ou bien modifier les aspects d’une ressource à l’aide de l’éditeur associé. Vous pouvez également modifier une ressource dans [au format texte](../windows/how-to-open-a-resource-script-file-in-text-format.md) et [format binaire](../windows/opening-a-resource-for-binary-editing.md).

Certains types de ressources sont des fichiers individuels qui peuvent être importés et utilisés de différentes manières. Citons notamment les bitmaps, icônes, curseurs, barres d’outils et les fichiers html. Ces ressources ont des noms de fichiers et [identificateurs de ressource](../windows/symbols-resource-identifiers.md). D’autres, telles que les boîtes de dialogue, des menus et des tables de chaînes dans les projets Win32, existent uniquement dans le cadre d’un fichier de script (.rc) de ressource ou un fichier de ressources (.rct) de modèle.

Les ressources peuvent également être modifié en dehors du projet sans ouvrir le projet, consultez [Comment : Créer des ressources](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Propriétés d’une ressource peuvent être modifiées à l’aide de la **propriétés** fenêtre.

- Pour modifier les propriétés d’une ressource, dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de la ressource que vous souhaitez modifier, puis choisissez **propriétés**.  Ensuite, dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifier les propriétés de votre ressource.

- Pour annuler une modification apportée aux propriétés d’une ressource, vérifiez que votre ressource a le focus dans **affichage des ressources** et choisissez **Annuler** à partir de la **modifier** menu.

### <a name="win32-resources"></a>Ressources Win32

Vous pouvez accéder à des ressources Win32 dans le [affichage des ressources](../windows/resource-view-window.md) volet.

Pour afficher une ressource Win32 dans un éditeur de ressources :

1. Sélectionnez **affichage des ressources** à partir de la **vue** menu.

1. Si le **affichage des ressources** fenêtre n’est pas la fenêtre supérieure, sélectionnez le **affichage des ressources** onglet pour les importer vers le haut.

1. À partir de **affichage des ressources**, développez le dossier du projet qui contient les ressources que vous souhaitez afficher. Par exemple, si vous souhaitez afficher une ressource de boîte de dialogue, développez le **boîte de dialogue** dossier.

1. Double-cliquez sur la ressource, par exemple, **IDD_ABOUTBOX**.

   La ressource s’ouvre dans l’éditeur approprié. Par exemple, pour les ressources de la boîte de dialogue, la ressource s’ouvre à l’intérieur de la **boîte de dialogue** éditeur.

Pour supprimer une ressource Win32 existante :

1. Dans **affichage des ressources**, développez le nœud pour un type de ressource.

1. Avec le bouton droit sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer**.

   > [!TIP]
   > Vous pouvez également utiliser cette méthode lorsque vous avez ouvert dans une fenêtre de document en dehors d’un projet le fichier .rc.

### <a name="managed-project-resources"></a>Ressources de projet managé

Étant donné que les projets managés n’utilisent des fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Utilisez le [Éditeur d’images](../windows/image-editor-for-icons.md) et [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans les projets managés. Toutes les ressources managées vous souhaitez modifier doivent être liées et éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

- Pour afficher une ressource managée dans un éditeur de ressources dans **l’Explorateur de solutions**, double-cliquez sur la ressource, par exemple, *Bitmap1.bmp*. La ressource s’ouvre dans l’éditeur approprié.

- Pour supprimer une ressource managée existante, dans **l’Explorateur de solutions**, avec le bouton droit de la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer**.

## <a name="preview-resources"></a>Ressources de la version préliminaire

Afficher un aperçu de vos ressources afin que vous puissiez afficher des ressources graphiques sans les ouvrir. L’aperçu est également utile pour les exécutables une fois que vous avez compilé, étant donné que les identificateurs de ressource se transformer en nombres. Dans la mesure où ces identificateurs numériques ne fournissent pas suffisamment d’informations, l’aperçu des ressources vous aide à identifier rapidement les.

Les types de ressources suivantes fournissent un aperçu de la disposition visuelle : Image bitmap, boîte de dialogue, icône, Menu, curseur, barre d’outils

Un aperçu visuel ne fournissent pas les ressources suivantes : Accélérateur, manifeste, la Table de chaînes, les informations de Version

> [!NOTE]
> Pour afficher un aperçu des ressources nécessite Win32.

Pour afficher un aperçu des ressources :

1. Dans [affichage des ressources](../windows/resource-view-window.md) ou une fenêtre de document, sélectionnez votre ressource, par exemple, **IDD_ABOUTBOX**.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez le **Pages de propriétés** bouton.

   > [!TIP]
   > Utilisez un raccourci, accédez au menu **vue** > **Pages de propriétés**.

   Le **Page de propriétés** pour la ressource s’ouvre affichant un aperçu de cette ressource. Vous pouvez utiliser la **des** et **vers le bas** dans contrôlent des touches de direction pour parcourir l’arborescence **affichage des ressources** ou la fenêtre de document. Le **Page de propriétés** reste ouverte et affiche toutes les ressources qui a le focus et peuvent être visualisés.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>