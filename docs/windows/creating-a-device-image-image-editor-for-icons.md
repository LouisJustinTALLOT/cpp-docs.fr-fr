---
title: Création d'une image de périphérique (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560294"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Création d'une image de périphérique (Éditeur d'images pour les icônes)

Lorsque vous créez une nouvelle icône ou une ressource du curseur, la **Image** éditeur crée d’abord une image dans un style spécifique (32 x 32, 16 couleurs pour les icônes et 32 x 32, Monochrome pour les curseurs). Vous pouvez ensuite ajouter des images de différentes tailles et les styles à l’icône d’origine et modifier chaque image supplémentaire, en fonction des besoins, pour les périphériques d’affichage différent. Vous pouvez également modifier une image à l’aide d’une opération de couper-coller à partir d’un type d’image existant ou d’une bitmap créée dans un programme graphique.

Lorsque vous ouvrez la ressource icône ou curseur dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image de la plupart des étroitement le périphérique d’affichage actuel est ouverte par défaut.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="new-ltdevicegt-image-type-dialog-box"></a>Nouvelle &lt;appareil&gt; boîte de dialogue Type d’Image

Le **New &lt;appareil&gt; Type d’Image** boîte de dialogue vous permet de créer une nouvelle image de périphérique d’un type spécifié. Pour ouvrir le **New \<appareil > Image** boîte de dialogue, sélectionnez **nouveau Type d’Image** sur le **Image** menu. Les propriétés suivantes incluses sont **Type d’Image cible** et **personnalisé**.

### <a name="target-image-type"></a>Type d’Image cible

Répertorie les types d’images disponibles. Sélectionnez le type d’image que vous souhaitez ouvrir :

||||
|-|-|-|
|-16 x 16, 16 couleurs|-48 x 48, 16 couleurs|-96 x 96, 16 couleurs|
|-16 x 16, 256 couleurs|-48 x 48, 256 couleurs|-96 x 96, 256 couleurs|
|-16 x 16, Monochrome|-48 x 48, Monochrome|- 96 x 96, Monochrome|
|-32 x 32, 16 couleurs|-64 x 64, 16 couleurs||
|-32 x 32, 256 couleurs|-64 x 64, 256 couleurs||
|-32 x 32, Monochrome|-64 x 64, Monochrome||

> [!NOTE]
> Toutes les images existantes seront affichera pas dans cette liste.

### <a name="custom"></a>Personnalisé

Ouvre le **Image personnalisée** boîte de dialogue dans laquelle vous pouvez créer une nouvelle image avec une taille personnalisée et le nombre de couleurs.

Le **Image personnalisée** boîte de dialogue vous permet de créer une nouvelle image avec une taille personnalisée et le nombre de couleurs. Les propriétés suivantes incluses sont :

|Propriété|Description|
|---|---|
|**Width**|Fournit un espace vous permettant d’entrer la largeur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Height**|Fournit un espace vous permettant d’entrer la hauteur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Couleurs**|Fournit un espace vous permettant de choisir le nombre de couleurs pour l’image personnalisée : 2, 16 ou 256.|

## <a name="open-ltdevicegt-image-dialog-box"></a>Ouvrez &lt;appareil&gt; Image boîte de dialogue

Utilisez le **ouvrir &lt;appareil&gt; Image** boîte de dialogue pour ouvrir des images de périphérique dans les projets C++. Il répertorie les images de périphérique existantes dans la ressource actuelle (les images qui font partie de la ressource actuelle). La propriété suivante incluse est :

|Propriété|Description|
|---|---|
|**Images actuelles**|Répertorie les images incluses dans la ressource. Sélectionnez le type d’image que vous souhaitez ouvrir.|

## <a name="to-create-a-new-icon-or-cursor"></a>Pour créer une nouvelle icône ou curseur

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor** dans le menu contextuel.)

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**. Pour les icônes, cette action crée une ressource icône 16 couleurs, 32 x 32. Pour les curseurs, 32 x 32, Monochrome image (2-color) est créé.

   Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Icônes et curseurs : Ressources d’images pour périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Icônes et curseurs : Ressources d’images pour périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Menu image](../windows/image-menu-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
