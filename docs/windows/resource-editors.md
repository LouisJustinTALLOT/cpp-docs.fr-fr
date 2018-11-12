---
title: Éditeurs de ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: ae35dbe98304fbf2f80dfe5cba8747d47cbba4d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622402"
---
# <a name="resource-editors"></a>éditeurs de ressources

Un **ressource** éditeur est un environnement spécialisé pour créer ou modifier des ressources qui sont inclus dans un projet Visual Studio. Les éditeurs de ressources de Visual Studio partagent des techniques et des interfaces pour vous aider à créer et à modifier rapidement et facilement des ressources d’application. Les éditeurs de ressources vous permettent d’ [afficher et de modifier des ressources dans l’éditeur approprié](../windows/viewing-and-editing-resources-in-a-resource-editor.md) et d’ [afficher un aperçu des ressources](../windows/previewing-resources.md).

L’éditeur approprié s’ouvre automatiquement quand vous créez ou que vous ouvrez une ressource.

**Remarque** comme les projets managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

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

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)