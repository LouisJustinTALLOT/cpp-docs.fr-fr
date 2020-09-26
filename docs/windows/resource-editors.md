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
ms.openlocfilehash: 2552f9eea79aa0a3545d9746d85cacfbd9a3f25d
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353166"
---
# <a name="resource-editors-c"></a>Éditeurs de ressources (C++)

Un éditeur de ressources est un environnement spécialisé pour créer ou modifier des ressources incluses dans un projet Visual Studio. Les éditeurs de ressources de Visual Studio partagent des techniques et des interfaces pour vous aider à créer et à modifier rapidement et facilement des ressources d’application. Les éditeurs de ressources vous permettent d’afficher et de modifier des ressources dans l’éditeur approprié et d’afficher un aperçu des ressources.

L’éditeur approprié s’ouvre automatiquement quand vous créez ou que vous ouvrez une ressource.

> [!NOTE]
> Étant donné que les projets managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **Explorateur de solutions**. Vous pouvez utiliser l' [éditeur d’images](../windows/image-editor-for-icons.md) et l' [Éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

|Utilisez|Pour modifier|
|----------------|----------------|
|[Éditeur d’accélérateurs](../windows/accelerator-editor.md)|Tables d’accélérateurs dans les projets Visual Studio C++.|
|[Éditeur binaire](binary-editor.md)|Informations de données binaires et ressources personnalisées dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)|Boîtes de dialogue dans les projets Visual Studio C++.|
|[Éditeur d’images](../windows/image-editor-for-icons.md)|Bitmaps, icônes, curseurs et autres fichiers image dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de menus](../windows/menu-editor.md)|Ressources de menu dans les projets Visual Studio C++.|
|[Éditeur Ribbon](../mfc/ribbon-designer-mfc.md)|Ressources de ruban dans les projets MFC.|
|[Éditeur de chaînes](../windows/string-editor.md)|Tables de chaînes dans les projets Visual Studio C++.|
|[Éditeur de barres d’outils](../windows/toolbar-editor.md)|Ressources de barre d’outils dans les projets Visual Studio C++. L' **éditeur de barres d’outils** fait partie de l' **éditeur d’images**.|
|[Éditeur d’informations sur la version](../windows/version-information-editor.md)|Informations de version dans les projets Visual Studio C++.|

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier. RC, consultez [Comment : créer des ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Afficher et modifier des ressources

Chaque type de ressource a un éditeur de ressources spécifique à ce type de ressource. Vous pouvez réorganiser, redimensionner, ajouter des contrôles et des fonctionnalités, ou modifier des aspects d’une ressource à l’aide de l’éditeur associé. Vous pouvez également modifier une ressource au format texte et au format binaire. Pour plus d’informations, consultez [Comment : créer des ressources](../windows/how-to-create-a-resource-script-file.md).

Certains types de ressources sont des fichiers individuels qui peuvent être importés et utilisés de différentes façons ; Il s’agit notamment des bitmaps, des icônes, des curseurs, des barres d’outils et des fichiers html. De telles ressources ont des noms de fichiers et des [identificateurs de ressource](../windows/symbols-resource-identifiers.md). D’autres, telles que les boîtes de dialogue, les menus et les tables de chaînes des projets Win32, existent uniquement dans le cadre d’un fichier de script de ressources (. RC) ou d’un fichier de modèle de ressource (. RCT).

Les ressources peuvent également être modifiées en dehors du projet sans avoir ouvert le projet. Pour plus d’informations, consultez [Comment : créer des ressources](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Les propriétés d’une ressource peuvent être modifiées à l’aide de la fenêtre **Propriétés** .

- Pour modifier les propriétés d’une ressource, dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur la ressource que vous souhaitez modifier, puis sélectionnez **Propriétés**.  Ensuite, dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifiez les propriétés de votre ressource.

- Pour annuler une modification apportée aux propriétés d’une ressource, assurez-vous que votre ressource a le focus dans **affichage des ressources** et choisissez **Annuler** dans le menu **Edition** .

### <a name="win32-resources"></a>Ressources Win32

Vous pouvez accéder aux ressources Win32 dans le volet [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) .

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Pour afficher une ressource Win32 dans un éditeur de ressources

1. Accédez à menu **Afficher**d'  >  **autres fenêtres**  >  **affichage des ressources**.

1. Si la fenêtre de **affichage des ressources** n’est pas la fenêtre supérieure, sélectionnez l’onglet **affichage des ressources** pour l’afficher en haut.

1. Dans **affichage des ressources**, développez le dossier du projet qui contient les ressources que vous souhaitez afficher. Par exemple, si vous souhaitez afficher une ressource de boîte de dialogue, développez le dossier **boîte de dialogue** .

1. Double-cliquez sur la ressource, par exemple, **IDD_ABOUTBOX**.

   La ressource s’ouvre dans l’éditeur approprié. Par exemple, pour les ressources de boîte de dialogue, la ressource s’ouvre dans l' **éditeur de boîtes de dialogue**.

#### <a name="to-delete-an-existing-win32-resource"></a>Pour supprimer une ressource Win32 existante

1. Dans **affichage des ressources**, développez le nœud d’un type de ressource.

1. Cliquez avec le bouton droit sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer**.

> [!TIP]
> Vous pouvez également utiliser cette méthode lorsque le fichier. RC est ouvert dans une fenêtre de document à l’extérieur d’un projet.

### <a name="managed-project-resources"></a>Ressources de projet managées

Étant donné que les projets managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **Explorateur de solutions**. Utilisez l' [éditeur d’images](../windows/image-editor-for-icons.md) et l' [Éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Les ressources managées que vous souhaitez modifier doivent être des ressources liées et les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

- Pour afficher une ressource managée dans un éditeur de ressources, dans **Explorateur de solutions**, double-cliquez sur la ressource, par exemple, *Bitmap1.bmp*, et la ressource s’ouvre dans l’éditeur approprié.

- Pour supprimer une ressource managée existante, dans **Explorateur de solutions**, cliquez avec le bouton droit sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer**.

## <a name="preview-resources"></a>Aperçu des ressources

Affichez un aperçu de vos ressources pour vous permettre d’afficher les ressources graphiques sans les ouvrir. L’aperçu est également utile pour les exécutables une fois que vous les avez compilés, car les identificateurs de ressource sont modifiés en nombres. Étant donné que ces identificateurs numériques ne fournissent pas suffisamment d’informations, l’aperçu des ressources vous aide à les identifier rapidement.

Les types de ressources suivants fournissent un aperçu de la présentation visuelle : bitmap, boîte de dialogue, icône, menu, curseur, barre d’outils

Les ressources suivantes ne fournissent pas d’aperçu visuel : accélérateur, manifeste, table de chaînes, informations sur la version

> [!NOTE]
> Pour afficher un aperçu des ressources requiert Win32.

### <a name="to-preview-resources"></a>Pour afficher un aperçu des ressources

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) ou dans une fenêtre de document, sélectionnez votre ressource, par exemple, **IDD_ABOUTBOX**.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez le bouton **pages de propriétés** .

   > [!TIP]
   > Utilisez un raccourci, accédez à menu **Afficher**les  >  **pages de propriétés**.

   La page de **Propriétés** de la ressource s’ouvre et affiche un aperçu de cette ressource. Vous pouvez utiliser les touches de direction **haut** et **bas** pour parcourir le contrôle d’arborescence dans **affichage des ressources** ou la fenêtre de document. La page de **Propriétés** reste ouverte et affiche toutes les ressources qui ont le focus et peuvent être prévisualisées.

## <a name="requirements"></a>Spécifications

Aucune

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Identificateurs de ressource (symboles)](../windows/symbols-resource-identifiers.md)<br/>
