---
title: Éditeurs de ressources (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 43eab011cefed116723bd983b685c1c8c230326f
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226317"
---
# <a name="resource-editors-c"></a>Éditeurs de ressources (C++)

Un **ressource** éditeur est un environnement spécialisé pour créer ou modifier des ressources qui sont inclus dans un projet Visual Studio. Les éditeurs de ressources de Visual Studio partagent des techniques et des interfaces pour vous aider à créer et à modifier rapidement et facilement des ressources d’application. Éditeurs de ressources permettent d’afficher et modifier les ressources dans les ressources appropriées de l’éditeur et l’aperçu.

L’éditeur approprié s’ouvre automatiquement quand vous créez ou que vous ouvrez une ressource.

> [!NOTE]
> Étant donné que les projets managés n’utilisent pas les fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

|Utilisez|Pour modifier|
|----------------|----------------|
|[Éditeur d’accélérateurs](../windows/accelerator-editor.md)|Tables d’accélérateurs dans les projets Visual C++.|
|[Binary Editor](binary-editor.md)|Informations de données binaires et ressources personnalisées dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)|Boîtes de dialogue dans des projets Visual C++.|
|[Image Editor](../windows/image-editor-for-icons.md)|Bitmaps, icônes, curseurs et autres fichiers image dans des projets Visual C++, Visual Basic ou Visual C#.|
|[Éditeur de menus](../windows/menu-editor.md)|Ressources de menu dans des projets Visual C++.|
|[Éditeur Ribbon](../mfc/ribbon-designer-mfc.md)|Ressources de ruban dans les projets MFC.|
|[Éditeur de chaînes](../windows/string-editor.md)|Tableaux de chaînes dans des projets Visual C++.|
|[Éditeur de barres d’outils](../windows/toolbar-editor.md)|Ressources de barre d’outils dans des projets Visual C++. L’éditeur de barres d’outils fait partie de l’éditeur d’images.|
|[Éditeur d’informations sur la version](../windows/version-information-editor.md)|Informations de version dans des projets Visual C++.|

## <a name="view-and-edit-resources-in-a-resource-editor"></a>Afficher et modifier les ressources dans un éditeur de ressources

Chaque type de ressource a un **ressource** éditeur spécifique à ce type de ressource. Vous pouvez réorganiser, redimensionner, ajouter des contrôles et fonctionnalités ou bien modifier les aspects d’une ressource à l’aide de l’éditeur associé. Vous pouvez également modifier une ressource dans [au format texte](../windows/how-to-open-a-resource-script-file-in-text-format.md) et [format binaire](../windows/opening-a-resource-for-binary-editing.md).

Certains types de ressources sont des fichiers individuels qui peuvent être importés et utilisés de différentes manières. Citons notamment les bitmaps, icônes, curseurs, barres d’outils et les fichiers html. Ces ressources ont des noms de fichiers et [identificateurs de ressource](../windows/symbols-resource-identifiers.md). D’autres, telles que les boîtes de dialogue, des menus et des tables de chaînes dans les projets Win32, existent uniquement dans le cadre d’un fichier de script (.rc) de ressource ou un fichier de ressources (.rct) de modèle.

Ressources peuvent également être modifiées en dehors du projet, consultez [Comment : Ouvrir un fichier de Script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Propriétés d’une ressource [peut être modifié à l’aide de la fenêtre Propriétés](../windows/changing-the-properties-of-a-resource.md).

Pour modifier les propriétés d’une ressource :

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de la ressource que vous souhaitez modifier, puis choisissez **propriétés** dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifier les propriétés de votre ressource.

Pour annuler une modification apportée aux propriétés d’une ressource :

1. Assurez-vous que votre ressource a le focus dans **affichage des ressources**.

1. Choisissez **Annuler** à partir de la **modifier** menu.

### <a name="win32-resources"></a>Ressources Win32

Vous pouvez accéder à des ressources Win32 dans le [affichage des ressources](../windows/resource-view-window.md) volet.

Pour afficher une ressource Win32 dans un éditeur de ressources :

1. Sélectionnez **affichage des ressources** à partir de la **vue** menu.

1. Si le **affichage des ressources** fenêtre n’est pas la fenêtre supérieure, sélectionnez le **affichage des ressources** onglet pour les importer vers le haut.

1. À partir de **affichage des ressources**, développez le dossier du projet qui contient les ressources que vous souhaitez afficher. Par exemple, si vous souhaitez afficher une ressource de boîte de dialogue, développez le **boîte de dialogue** dossier.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Double-cliquez sur la ressource, par exemple, **IDD_ABOUTBOX**.

   La ressource s’ouvre dans l’éditeur approprié. Par exemple, pour les ressources de la boîte de dialogue, la ressource s’ouvre à l’intérieur de la **boîte de dialogue** éditeur.

   Vous pouvez également [afficher des ressources dans un fichier .rc (script de ressources) sans ouvrir de projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

Pour supprimer une ressource Win 32 existante :

1. Dans **affichage des ressources**, développez le nœud pour un type de ressource.

2. Avec le bouton droit sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.

   > [!NOTE]
   > Vous pouvez supprimer une ressource à l’aide de la même commande de menu contextuel lorsque vous avez ouvert dans une fenêtre de document en dehors d’un projet le fichier .rc.

### <a name="resources-in-managed-projects"></a>Ressources dans les projets managés

Étant donné que les projets managés n’utilisent des fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Pour afficher une ressource managée dans un éditeur de ressources :

Dans **l’Explorateur de solutions**, double-cliquez sur la ressource, par exemple, *Bitmap1.bmp*.

   La ressource s’ouvre dans l’éditeur approprié.

Pour supprimer une ressource managée existante :

Dans **l’Explorateur de solutions**, avec le bouton droit de la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.

## <a name="preview-resources"></a>Ressources de la version préliminaire

Afficher un aperçu de vos ressources afin que vous puissiez afficher des ressources graphiques sans les ouvrir. L’aperçu est également utile pour les exécutables une fois que vous les avez compilé, car les identificateurs de ressource se transformer en nombres. Dans la mesure où ces identificateurs numériques ne fournissent pas suffisamment d’informations, l’aperçu des ressources vous aide à identifier rapidement les.

Vous pouvez afficher un aperçu de la présentation visuelle des types de ressources suivants : Image bitmap, boîte de dialogue, icône, Menu, curseur, barre d’outils

La fonction d’aperçu visuel ne s’applique pas aux ressources : Accélérateur, manifeste, Table de chaînes et informations de Version

> [!NOTE]
> Pour afficher un aperçu des ressources nécessite Win32.

Pour afficher un aperçu des ressources :

1. Dans [affichage des ressources](../windows/resource-view-window.md) ou une fenêtre de document, sélectionnez votre ressource, par exemple, `IDD_ABOUTBOX`.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez le **Pages de propriétés** bouton.

   > [!TIP]
   > Pour créer un raccourci, sur le **vue** menu, sélectionnez **Pages de propriétés**.

   Le **Page de propriétés** pour la ressource s’ouvre affichant un aperçu de cette ressource. Vous pouvez ensuite utiliser le **des** et **vers le bas** dans contrôlent des touches de direction pour parcourir l’arborescence **affichage des ressources** ou la fenêtre de document. Le **Page de propriétés** reste ouverte et affiche toutes les ressources qui a le focus et peuvent être visualisés.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)