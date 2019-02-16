---
title: 'Procédure : Créer des ressources (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: dbb1d1d4b865380abde189ae6a72a1bfc3755840
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320846"
---
# <a name="how-to-create-resources-c"></a>Procédure : Créer des ressources (C++)

Le **affichage des ressources** fenêtre affiche les fichiers de ressources inclus dans vos projets. Développement du dossier supérieur (par exemple, *Project1.rc*) montre les types de ressources au sein de que le fichier et le développement de chaque type de ressource affiche les ressources individuelles de ce type.

> [!TIP]
> Pour ouvrir la fenêtre Affichage des ressources, sélectionnez **affichage des ressources** sur le **vue** menu (ou utilisez **Ctrl** + **MAJ**  +  **E**).
>
> Vous pouvez également utiliser avec le bouton droit sur le **affichage des ressources** fenêtre pour lancer un menu contextuel de commandes ou double-cliquez sur la barre de titre pour ancrer ou détacher de la fenêtre. Clic droit sur la barre de titre contient des commandes supplémentaires qui vous permettent de contrôler le comportement de la fenêtre. Pour plus d’informations, consultez [Windows gestion](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le **affichage des ressources** windows inclut le **ajouter une ressource** boîte de dialogue avec les propriétés suivantes pour ajouter des ressources à un projet d’application de bureau Windows de C++ :

|Propriété|Description|
|--|----|
|**Type de ressource**|Spécifie le type de ressource que vous voulez créer.<br/><br/>Vous pouvez développer les catégories de ressources curseur et boîte de dialogue pour afficher des ressources supplémentaires. Ces ressources se trouvent dans ...\Microsoft Visual Studio \<version\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si vous ajoutez des fichiers .rct, placez-les dans ce répertoire ou spécifier un autre [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Les ressources de ces fichiers apparaissent alors au deuxième niveau en dessous de la catégorie appropriée. Il n’existe aucune limite prédéfinie au nombre de fichiers .rct que vous pouvez ajouter.<br/><br/>Les ressources affichées au niveau le plus élevé du contrôle d’arborescence sont les ressources par défaut fournies par Visual Studio.|
|**Nouveau**|Crée une ressource en fonction du type sélectionné dans le **Type de ressource** zone et ouvre la ressource dans l’éditeur approprié. Par exemple, si vous créez une ressource de boîte de dialogue, il s’ouvre dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md).|
|**Import**|Ouvre le **importer** boîte de dialogue où vous pouvez accéder à la ressource que vous souhaitez importer dans votre projet actuel. Vous pouvez importer une image bitmap, icône, curseur, HTML, son (. WAV), ou le fichier de ressources personnalisées.|
|**Personnalisé**|Ouvre le **nouvelle ressource personnalisée** boîte de dialogue où vous pouvez créer une ressource personnalisée. Ressources personnalisées ne peuvent être modifiés que dans l’éditeur binaire.|

Le **ajouter une ressource** boîte de dialogue comprend le **nouvelle ressource personnalisée** boîte de dialogue avec la propriété suivante pour créer une nouvelle ressource personnalisée dans un projet C++ :

|Propriété|Description|
|--|----|
|**Type de ressource**|Fournit une zone de texte pour entrer le nom d’un type de ressource personnalisée. Visual C++ met automatiquement le nom lorsque vous quittez le **nouvelle ressource personnalisée** boîte de dialogue.|

> [!NOTE]
> Le **éditeur de ressources** ou **affichage des ressources** n’est pas disponible dans les éditions Express.

## <a name="resource-scripts"></a>Scripts de ressources

Avant de créer et ajouter de nouvelles ressources à votre projet, vous devez d’abord créer un script de ressources (fichier .rc).

> [!NOTE]
> Vous pouvez ajouter un script de ressources (fichier .rc) uniquement à un projet existant qui est chargé dans l’IDE de Visual Studio. Vous ne pouvez pas créer un script de ressources autonome (en dehors du projet). Modèles de ressources (fichiers .rct) peuvent être créés à tout moment.

### <a name="to-create-a-resource-script"></a>Pour créer un script de ressources

1. Placez le focus sur le dossier de votre projet dans **l’Explorateur de solutions**, par exemple, *MonProjet*.

   > [!NOTE]
   > Ne confondez pas avec le dossier de solution dans le dossier du projet **l’Explorateur de solutions**. Si vous placez le focus sur le **Solution** dossier, les choix disponibles dans le **ajouter un nouvel élément** boîte de dialogue sera différente.

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

1. Sélectionnez le **Visual C++** dossier, puis choisissez **le fichier de ressources (.rc)** dans le volet droit.

1. Fournissez un nom pour votre script de ressources dans le **nom** zone de texte, puis sélectionnez **Open**.

### <a name="to-open-a-resource-script"></a>Pour ouvrir un script de ressources

Vous pouvez afficher les ressources dans un script de ressources sans ouvrir de projet. Le fichier de script s’ouvre dans une fenêtre de document, par opposition à la **affichage des ressources** fenêtre.

> [!NOTE]
> Certaines commandes sont disponibles uniquement lorsque le fichier est ouvert en mode autonome (en dehors d’un projet). Ouverture d’un fichier d’autonome signifie l’ouvrir sans charger d’abord le projet.
>
> Par exemple, pour enregistrer un fichier dans un format différent ou un autre nom de fichier (comme le **Enregistrer sous** commande n’est pas disponible pour le fichier à l’intérieur d’un projet). Si vous ouvrez le premier projet à l’aide **fichier** > **ouvrir** > **projet**, ces commandes ne sont pas disponibles.

#### <a name="to-open-a-resource-script-outside-of-a-project"></a>Pour ouvrir un script de ressources en dehors d’un projet

1. À partir de la **fichier** menu, sélectionnez **Open**, puis choisissez **fichier**.

1. Accédez au fichier de script de ressources, sélectionnez le fichier, puis choisissez **Open**.

#### <a name="to-open-multiple-resource-scripts-outside-of-a-project"></a>Pour ouvrir plusieurs scripts de ressources en dehors d’un projet

1. Ouvrez les deux fichiers de ressources en mode autonome. Par exemple, ouvrez *Source1.rc* et *Source2.rc*.

1. À partir de la **fichier** menu, choisissez **Open**, puis sélectionnez **fichier**.

1. Accédez au premier fichier de script de ressources que vous souhaitez ouvrir (*Source1.rc*), sélectionnez le fichier, puis choisissez **ouvrir**.

1. Répétez l’étape précédente pour ouvrir le second fichier .rc (*Source2.rc*).

   Les deux fichiers .rc sont désormais ouverts dans les fenêtres de documents distinctes.

1. Utilisez le **fenêtre** menu (ou clic droit des fichiers .rc) et choisissez **nouveau groupe d’onglets Horizontal** ou **nouveau groupe d’onglets Vertical**.

   Les fenêtres sont maintenant en mosaïque pour pouvoir les afficher simultanément.

Parfois, vous souhaitez afficher le contenu du fichier de script (.rc) de ressources de votre projet sans ouvrir une ressource, par exemple une boîte de dialogue, dans son éditeur de ressources spécifique. Par exemple, vous souhaitez rechercher une chaîne dans toutes les boîtes de dialogue du fichier de ressources sans avoir à ouvrir chacune d'elles séparément.

Vous pouvez facilement ouvrir le fichier de ressources au format texte pour afficher toutes les ressources qu’il contient et effectuer des opérations globales prises en charge par l’éditeur de texte.

> [!NOTE]
> Les éditeurs de ressources ne lisent pas directement .rc ou `resource.h` fichiers. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps obtient désynchronisé avec le fichier .rc, le fichier .rc est régénéré (par exemple, lorsque vous enregistrez, l’éditeur de ressources remplace le fichier .rc et `resource.h` fichier). Les modifications apportées aux ressources continuent dans le fichier .rc, mais les commentaires sont perdues une fois que le fichier .rc est remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-in-text-format"></a>Pour ouvrir un fichier de script de ressources au format texte

1. À partir de la **fichier** menu, sélectionnez **Open**, puis choisissez **fichier**.

1. Dans le **ouvrir un fichier** boîte de dialogue, accédez au fichier de script de ressources à afficher au format texte.

1. Sélectionnez le fichier, puis sélectionnez la flèche déroulante sur le **Open** bouton (situé à droite du bouton).

1. Choisissez **ouvrir avec** dans le menu déroulant et sélectionnez **éditeur de Code Source (texte)**.

1. À partir de la **ouvrir en tant que** liste déroulante, sélectionnez **texte**.

   La ressource s’ouvre dans le **Code Source** éditeur.

> [!TIP]
> Un raccourci ici consiste à clic droit sur le fichier .rc dans **l’Explorateur de solutions**, choisissez **ouvrir avec...**  et sélectionnez **éditeur de Code Source (texte)**.

## <a name="resources"></a>Ressources

Vous pouvez créer une ressource comme une ressource par défaut (une ressource qui n’est pas basée sur un modèle) ou en tant que ressource inspirée d’un modèle.

Lorsque vous créez une nouvelle ressource, Visual C++ lui assigne un nom unique, par exemple, `IDD_Dialog1`. Vous pouvez personnaliser cet ID de ressource en modifiant les propriétés de la ressource dans l'éditeur de ressources associé ou dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Ne spécifiez pas un nom de ressource ou un ID qui est réservée par Visual Studio. Noms réservés sont DESIGNINFO, HWB et TEXTINCLUDE et l’ID réservé est 255.

### <a name="to-create-a-resource"></a>Pour créer une ressource

Vous pouvez créer une nouvelle ressource à l’aide d’une des opérations suivantes :

- Dans **affichage des ressources**, sélectionnez votre fichier .rc, puis utilisez **modifier** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

   > [!TIP]
   > Vous pouvez également cliquer sur le fichier .rc dans **affichage des ressources** et choisissez **ajouter une ressource** dans le menu contextuel.

- Dans **l’Explorateur de solutions**, cliquez sur le dossier du projet, sélectionnez **ajouter** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

   > [!NOTE]
   > Si vous ne disposez pas d’un fichier .rc dans votre projet, cette étape permet de créer un. Vous pouvez ensuite répéter cette étape pour ajouter des types de ressource spécifiques au nouveau fichier .rc.

- Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), avec le bouton droit de la classe, sélectionnez **ajouter** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

- Dans le **projet** menu, sélectionnez **ajouter une ressource**.

### <a name="support-for-mfc"></a>Prise en charge des MFC

En règle générale, si vous générez une application Microsoft Foundation classes (MFC) pour Windows à l’aide de la [Assistant application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de fichiers (y compris un fichier de script (.rc) de ressources) qui contient les principales fonctionnalités de base le MFC. Toutefois, lorsque vous modifiez un fichier .rc pour une application Windows ne pas basée sur MFC, les fonctionnalités spécifiques à MFC suivantes ne sont pas disponibles : Les Assistants code MFC, chaînes d’invite menu, affichage du contenu pour les contrôles de zone de liste déroulante et hébergement de contrôles ActiveX.

#### <a name="to-add-mfc-support-to-a-resource-script-file"></a>Pour ajouter la prise en charge MFC pour un fichier de script de ressources

1. Ouvrez le fichier de script de ressources.

1. Dans **affichage des ressources**, mettez en surbrillance le dossier de ressources (par exemple, *MFC.rc*).

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), définissez le **MFC Mode** propriété **True**.

   > [!NOTE]
   > Outre la définition de cette propriété, le fichier .rc doit faire partie d’un projet MFC. Par exemple, définissant simplement **MFC Mode** à **True** sur un .rc fichier dans un projet Win32 ne vous donne les fonctionnalités MFC.

## <a name="resource-templates"></a>Modèles de ressources

Un modèle de ressource est une ressource personnalisée que vous avez enregistré en tant que fichier .rct. Un modèle de ressource sert ensuite de point de départ pour la création de ressources. Modèles de ressources gagner du temps dans le développement des ressources supplémentaires ou des groupes de ressources qui partagent des fonctionnalités, telles que les contrôles standard ou répétée des éléments. Par exemple, si vous souhaitez inclure un bouton aide avec une icône de logo de société dans plusieurs boîtes de dialogue, créez un nouveau modèle de boîte de dialogue et personnalisez-le avec le bouton Aide et le logo.

Après avoir personnalisé le modèle de ressource, enregistrez vos modifications dans le dossier de modèles (ou l’emplacement spécifié dans le chemin d’accès include) afin que le nouveau modèle de ressource s’affiche sous son type de ressource dans le **ajouter une ressource** boîte de dialogue. Vous pouvez maintenant utiliser le nouveau modèle de ressource aussi souvent en fonction des besoins.

> [!NOTE]
> L'éditeur de ressources fournit automatiquement un ID de ressource unique. Vous pouvez réviser le [propriétés de ressource](../windows/changing-the-properties-of-a-resource.md) en fonction des besoins.

> [!NOTE]
> Placez les fichiers de modèles spécifiques aux langues dans les sous-répertoires du répertoire de modèle principal. Par exemple, placez les fichiers de modèle uniquement en anglais dans... \\< répertoire des modèles de ressource\>\1033. Visual Studio recherche les nouveaux fichiers RCT dans \Program Files\Microsoft Visual Studio \<version\>\VC\VCResourceTemplates, dans Visual Studio de \Program Files\Microsoft \<version > \VC\VCResourceTemplates\\< LCID\> (par exemple 1033 pour l’anglais), *ou* n’importe où sur le [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Si vous préférez stocker vos fichiers RCT dans un autre emplacement, par exemple Mes Documents, vous devez ajouter ce dossier au chemin include pour Visual Studio puisse trouver votre fichier RCT.

### <a name="to-create-a-resource-template"></a>Pour créer un modèle de ressource

1. Dans **l’Explorateur de solutions**, cliquez sur votre projet.

1. Dans le menu contextuel, sélectionnez **ajouter** > **ajouter un nouvel élément**.

1. Dans le **modèles :** volet, sélectionnez **le fichier de modèle de ressource (.rct)**.

1. Entrez un nom et un emplacement pour votre nouveau fichier .rct et choisissez **Open**.

   Le nouveau fichier .rct est ajouté à votre projet et apparaît dans **l’Explorateur de solutions** sous le **ressources** dossier.

1. Double-cliquez sur le fichier .rct pour l’ouvrir dans une fenêtre de document. Pour ajouter des ressources, cliquez sur le fichier dans la fenêtre de document et choisissez **ajouter une ressource**.

   Vous pouvez personnaliser ces ressources et enregistrez le fichier .rct.

### <a name="to-create-a-new-resource-from-a-template"></a>Pour créer une ressource à partir d'un modèle

1. Dans le **affichage des ressources** volet, cliquez sur le fichier .rc et choisissez **ajouter une ressource** dans le menu contextuel.

1. Sélectionnez le signe plus (**+**) en regard d’une ressource pour développer le nœud de ressource et afficher tous les modèles disponibles pour cette ressource.

1. Double-cliquez sur le modèle à utiliser.

1. En fonction des besoins, modifiez la ressource ajoutée dans son éditeur de ressources.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Pour convertir un fichier de ressources existant à un modèle

1. Ouvrez le fichier .rc en tant que fichier autonome.

1. Sur le **fichier** menu, sélectionnez **enregistrer \< *filename*> en tant que**.

1. Spécifiez un emplacement et choisissez **OK**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Gérer les ressources](../windows/how-to-copy-resources.md)<br/>
[Inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)<br/>