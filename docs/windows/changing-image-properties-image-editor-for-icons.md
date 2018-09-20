---
title: Modification des propriétés de l’Image (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3b85faff95e3053ea46edcedef7443cdab445d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422224"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Modification des propriétés d'une image (Éditeur d'images pour les icônes)

Vous pouvez définir ou modifier les propriétés d’une image à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

### <a name="to-change-an-images-properties"></a>Pour modifier les propriétés d’une image

1. Ouvrir l’image dans le **Image** éditeur.

2. Dans le **propriétés** fenêtre, modifiez les propriétés de votre image.

   |Propriété|Description|
   |--------------|-----------------|
   |**Couleurs**|Spécifie le jeu de couleurs de l’image. Sélectionnez **Monochrome**, **16**, ou **256**, ou **couleurs vraies**. Si vous avez déjà dessiné l’image avec une palette de couleurs-16, en sélectionnant **Monochrome** provoque des substitutions de noir et blanc pour les couleurs dans l’image. Contraste n’est pas toujours conservé : par exemple, les zones adjacentes rouge et verte sont converties en noir.|
   |**Nom de fichier**|Spécifie le nom du fichier image. Par défaut, Visual Studio assigne un nom de fichier de base créé en supprimant les quatre premiers caractères (« IDB_ ») à partir de l’identificateur de ressource par défaut (IDB_BITMAP1) et en ajoutant l’extension appropriée. Le nom de fichier pour l’image dans cet exemple serait `BITMAP1.bmp`. Vous pouvez le renommer `MYBITMAP1.bmp`.|
   |**Hauteur**|Définit la hauteur de l’image (en pixels). La valeur par défaut est 48. L’image est rognée ou espace vide est ajouté en dessous de l’image existante.|
   |**ID**|Définit l’identificateur de ressource. Pour une image, Microsoft Visual Studio, par défaut, attribue l’identificateur disponible suivant dans une série : IDB_BITMAP1, IDB_BITMAP2, et ainsi de suite. Des noms similaires sont utilisés pour les icônes et curseurs.|
   |**Palette**|Modifications des propriétés de couleur. Double-clic pour sélectionner une couleur et afficher la [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Définir la couleur en tapant des valeurs RVB ou TSL dans les zones de texte appropriées.|
   |**SaveCompressed**|Indique si l’image est dans un format compressé. Cette propriété est en lecture seule. Visual Studio ne vous permet pas d’enregistrer des images dans un format compressé, donc pour toutes les images créées dans Visual Studio, cette propriété sera **False**. Si vous ouvrez une image compressée (créée dans un autre programme) dans Visual Studio, cette propriété sera **True**. Si vous enregistrez une image compressée à l’aide de Visual Studio, elle sera décompressée et cette propriété est rétablis au **False**.|
   |**Largeur**|Définit la largeur de l’image (en pixels). La valeur par défaut pour les bitmaps est 48. L’image est rognée ou espace vide est ajouté à droite de l’image existante.|

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)