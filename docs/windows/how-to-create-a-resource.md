---
title: 'Procédure : Créer une ressource (C++)'
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764049"
---
# <a name="how-to-create-a-resource-c"></a>Procédure : Créer une ressource (C++)

Le **affichage des ressources** fenêtre affiche les fichiers de ressources inclus dans vos projets. Le développement du dossier supérieur (par exemple Project1.rc) permet d’afficher les types de ressource du fichier .rc. Le développement de chaque type de ressource permet d’afficher les ressources individuelles du type spécifié.

> [!NOTE]
> Ces informations ne s’applique pas aux ressources dans les applications de plateforme Windows universelle. Pour plus d’informations, consultez [ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).

> [!NOTE]
> **Affichage des ressources** n’est pas pris en charge dans les éditions Express.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

Le **affichage des ressources** fenêtre utilise le **ajouter une ressource** boîte de dialogue pour ajouter des ressources à un projet d’application de bureau Windows de C++. Cette boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Type de ressource**|Spécifie le type de ressource que vous voulez créer.<br/><br/>Vous pouvez développer les catégories de ressources curseur et boîte de dialogue pour afficher des ressources supplémentaires. Ces ressources se trouvent dans ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si vous ajoutez des fichiers .rct, vous devez les placer dans ce répertoire ou vous devez spécifier un [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md) pour eux. Les ressources de ces fichiers apparaissent alors au deuxième niveau en dessous de la catégorie appropriée. Il n’existe aucune limite prédéfinie au nombre de fichiers .rct que vous pouvez ajouter.<br/><br/>Les ressources affichées au niveau le plus élevé du contrôle d’arborescence sont les ressources par défaut fournies par Visual Studio.|
|**Nouveau**|Crée une ressource en fonction du type que vous avez sélectionné dans le **Type de ressource** boîte. La ressource s’ouvre dans l’éditeur approprié. Par exemple, si vous créez une ressource de boîte de dialogue, il s’ouvre dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md).|
|**Import**|Ouvre le **importer** boîte de dialogue dans laquelle vous pouvez accéder à une ressource que vous souhaitez importer dans votre projet actuel. Vous pouvez importer un bitmap, une icône, un curseur, un fichier de ressources HTML, un fichier de ressources audio (.WAV) ou un fichier de ressources personnalisées.|
|**Personnalisé**|Ouvre le **nouvelle ressource personnalisée** boîte de dialogue dans laquelle vous pouvez créer une ressource personnalisée. Les ressources personnalisées peuvent être modifiées seulement dans l’éditeur binaire.|

Le **nouvelle ressource personnalisée** boîte de dialogue vous permet de créer une nouvelle ressource personnalisée dans un projet C++. Cette boîte de dialogue a la propriété suivante :

|Propriété|Description|
|---|---|
|**Type de ressource**|Fournit une zone de texte, vous pouvez entrer le nom d’un type de ressource personnalisée. Visual C++ met automatiquement le nom lorsque vous quittez le **nouvelle ressource personnalisée** boîte de dialogue.|

Lorsque vous créez une nouvelle ressource, Visual C++ lui assigne un nom unique, par exemple, `IDD_Dialog1`. Vous pouvez personnaliser cet ID de ressource en modifiant les propriétés de la ressource dans l'éditeur de ressources associé ou dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

Vous pouvez créer une ressource comme une ressource par défaut (une ressource qui n’est pas basée sur un modèle) ou en tant que ressource inspirée un [modèle](../windows/how-to-use-resource-templates.md).

> [!NOTE]
> Ne spécifiez pas un nom de ressource ou un ID qui est réservée par Visual Studio. Les noms réservés sont DESIGNINFO, HWB et TEXTINCLUDE et l’ID réservé est 255.

## <a name="to-open-the-resource-view-window"></a>Pour ouvrir la fenêtre Affichage des ressources

Sélectionnez **affichage des ressources** sur le **vue** menu.

   \- ou -

Appuyez sur **Ctrl** + **MAJ** + **E**.

> [!TIP]
> Vous pouvez avec le bouton droit sur le **affichage des ressources** fenêtre pour lancer un menu contextuel de commandes. Vous pouvez également double-cliquer sur la barre de titre pour ancrer ou détacher la fenêtre. En cliquant avec le bouton droit sur la barre de titre, vous disposez de commandes supplémentaires qui vous permettent de contrôler le comportement de la fenêtre. Pour plus d’informations, consultez [Windows gestion](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

## <a name="to-create-a-new-resource-in-resource-view"></a>Pour créer une ressource dans l’affichage des ressources

1. Avec le focus sur votre fichier .rc dans **affichage des ressources**, sélectionnez le **modifier** menu et choisissez **ajouter une ressource** (ou cliquez sur le fichier .rc dans **affichagedesressources** et choisissez **ajouter une ressource** dans le menu contextuel).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez le type de ressource que vous souhaitez ajouter à votre projet.

## <a name="to-create-a-new-resource-in-solution-explorer"></a>Pour créer une ressource dans l’Explorateur de solutions

1. Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier du projet, choisissez **Ajouter**, puis cliquez sur **Ajouter une ressource** dans le menu contextuel.

   Si vous ne disposez pas d’un fichier .rc dans votre projet, cette étape permet de créer un. Vous pouvez ensuite répéter cette étape pour ajouter des types de ressource spécifiques au nouveau fichier .rc.

2. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez le type de ressource que vous souhaitez ajouter à votre projet.

## <a name="to-create-a-new-resource-in-class-view"></a>Pour créer une ressource dans l’affichage de classes

1. Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), avec le bouton droit de votre classe et choisissez **ajouter**, puis sélectionnez **ajouter une ressource** dans le menu contextuel.

2. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez le type de ressource que vous souhaitez ajouter à votre projet.

## <a name="to-create-a-new-resource-from-the-project-menu"></a>Pour créer une ressource à partir du menu Projet

Dans le menu **Projet** , choisissez **Ajouter une ressource**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
