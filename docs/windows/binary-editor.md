---
title: Éditeur binaire (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary.F1
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 1b5e1c16ff63c55617ee9b2bbcb47a7201635789
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451699"
---
# <a name="binary-editor-c"></a>Éditeur binaire (C++)

> [!WARNING]
> Le **éditeur binaire** n’est pas disponible dans les éditions Express.

L’éditeur binaire vous permet de modifier n’importe quelle ressource au niveau binaire au format hexadécimal ou ASCII. Vous pouvez également utiliser la [commande Rechercher](/visualstudio/ide/reference/find-command) pour rechercher des chaînes ASCII ou des octets hexadécimaux. Vous devez utiliser le **binaire** éditeur uniquement lorsque vous avez besoin afficher ou de légères modifications à des ressources personnalisées ou des types de ressources non pris en charge par l’environnement Visual Studio.

Pour ouvrir le **éditeur binaire**, choisissez d’abord **fichier** > **New** > **fichier** dans le menu principal, sélectionnez le fichier à modifier, puis cliquez sur la flèche à côté du **Open** bouton, puis choisissez **ouvrir avec** > **éditeur binaire**.

> [!CAUTION]
> Modifier des ressources telles que des boîtes de dialogue, des images ou des menus dans l’éditeur binaire est une opération dangereuse. Une modification incorrecte peut endommager la ressource et la rendre illisible dans son éditeur natif.

> [!TIP]
> Lors de l’utilisation du **binaire** éditeur, dans de nombreux cas, vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Les commandes disponibles varient selon la cible du pointeur. Par exemple, si vous cliquez en pointant sur le **binaire** éditeur avec des valeurs hexadécimales sélectionnées, le menu contextuel affiche les **couper**, **copie**, et **coller**  commandes.

Avec le **binaire** éditeur, vous pouvez :

- [Ouvrir une ressource à des fins d’édition binaire](../windows/opening-a-resource-for-binary-editing.md)

- [Modifier des données binaires](../windows/editing-binary-data.md)

- [Rechercher des données binaires](../windows/finding-binary-data.md)

- [Créer une ressource personnalisée ou une ressource de données](../windows/creating-a-new-custom-or-data-resource.md)

## <a name="managed-resources"></a>Ressources managées

Vous pouvez utiliser la [Éditeur d’images](../windows/image-editor-for-icons.md) et **binaire** éditeur pour travailler avec les fichiers de ressources dans les projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)