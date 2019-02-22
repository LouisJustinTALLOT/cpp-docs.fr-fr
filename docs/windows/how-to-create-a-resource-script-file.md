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
ms.openlocfilehash: 768675a878891ebb75c7f42c12eae8dfcfa3510b
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676485"
---
# <a name="how-to-create-resources-c"></a>Procédure : Créer des ressources (C++)

Vous pouvez créer des ressources pour votre projet par :

- À l’aide d’un fichier de script de ressources. Cette étape est nécessaire avant d’ajouter des ressources.

- Ajout de ressources à votre projet. Cette étape vous montre comment utiliser le **affichage des ressources**.

- À l’aide d’un modèle de ressource pour créer des ressources personnalisées.

> [!NOTE]
> Le **éditeur de ressources** et **affichage des ressources** ne sont pas disponibles dans les éditions Express.

## <a name="use-resource-script-files"></a>Utiliser des fichiers de Script de ressources

Avant de créer et ajouter de nouvelles ressources à votre projet, vous devez d’abord créer un fichier de script (.rc) de ressources.

> [!NOTE]
> Vous pouvez uniquement ajouter un script de ressources à un projet existant chargé dans l’IDE Visual Studio. Impossible de créer un script de ressources autonome en dehors du projet, même si les modèles de ressources (fichiers .rct) peuvent être créés à tout moment.

### <a name="to-create-a-resource-script-file"></a>Pour créer un fichier de script de ressources

1. Placez le focus sur le dossier de votre projet dans **l’Explorateur de solutions**, par exemple, *MonProjet*.

   > [!NOTE]
   > Ne confondez pas avec le dossier de solution dans le dossier du projet **l’Explorateur de solutions**. Si vous placez le focus sur le **Solution** dossier, vous n’aurez pas la même **ajouter un nouvel élément** choix.

1. Dans le menu, accédez à **projet** > **ajouter un nouvel élément**.

1. Sélectionnez le **Visual C++** dossier et choisissez **le fichier de ressources (.rc)** dans le volet droit.

1. Fournissez un nom pour votre fichier de script de ressources dans le **nom** zone de texte, puis sélectionnez **Open**.

### <a name="to-open-a-resource-script-file"></a>Pour ouvrir un fichier de script de ressources

Vous pouvez afficher les ressources dans un fichier de script de ressources sans ouvrir de projet. Le fichier de script s’ouvre dans une fenêtre de document, par opposition à la **affichage des ressources**.

> [!NOTE]
> Certaines commandes sont disponibles uniquement si le fichier est ouvert en mode autonome, ce qui signifie qu’en dehors d’un projet ou sans charger d’abord le projet. Par exemple, pour utiliser le **Enregistrer sous** commande pour enregistrer un fichier avec un autre format ou nom de fichier, le fichier doit être ouvert en mode autonome.

- Pour ouvrir un fichier de script de ressources en dehors d’un projet, dans le menu, accédez à **fichier** > **ouvrir**, puis choisissez **fichier**. Puis accédez au fichier de script de ressources, sélectionnez le fichier, puis choisissez **Open**.

  - Pour ouvrir un fichier de script de ressources au format texte, utilisez la flèche déroulante sur le côté droit de la **ouvrir** bouton dans l’étape ci-dessus et choisissez **ouvrir avec**. Puis sélectionnez **éditeur de Code Source (texte)** et à partir de la **ouvrir en tant que** liste déroulante, sélectionnez **texte**, et la ressource s’ouvre dans le **Source Code**éditeur.

    > [!NOTE]
    > Il peut arriver lorsque vous souhaitez afficher le contenu du fichier de script de ressources de votre projet sans utiliser les éditeurs de ressources pour ouvrir une ressource. Par exemple, vous souhaitez rechercher une chaîne dans toutes les boîtes de dialogue du fichier de ressources sans avoir à ouvrir chacune d'elles séparément. Vous pouvez facilement ouvrir le fichier de ressources au format texte pour afficher toutes les ressources qu’il contient et effectuer des opérations globales prises en charge par l’éditeur de texte.

- Pour ouvrir la ressource plusieurs scripts suivent les étapes ci-dessus pour chaque fichier que vous souhaitez ouvrir, par exemple, *Source1.rc* et *Source2.rc*. Ensuite, lorsque les deux fichiers .rc sont ouverts dans les fenêtres de documents distincts, soit utiliser le **fenêtre** menu ou cliquez sur un des fichiers .rc et choisissez **nouveau groupe d’onglets Horizontal** ou **nouvelle tabulation verticale Groupe**. Les fenêtres sont maintenant en mosaïque pour pouvoir les afficher simultanément.

> [!TIP]
> Vous pouvez également ouvrir des fichiers de script de ressources en double-cliquant sur le fichier .rc dans **l’Explorateur de solutions**, en choisissant l’option **ouvrir avec...**  et en sélectionnant **éditeur de Code Source (texte)**.

### <a name="to-edit-a-resource-script-file"></a>Pour modifier un fichier de script de ressources

- Pour convertir un fichier de ressources existant à un modèle, avec le fichier de script de ressources ouvert, dans le menu, accédez à **fichier** > **enregistrer \< *filename*> en tant que**. Spécifiez un emplacement, puis choisissez **OK**.

Lorsque vous générez une application Microsoft Foundation classes (MFC) pour Windows à l’aide de la [Assistant application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de base de fichiers, y compris un fichier de script (.rc) de ressources) qui contient les fonctionnalités principales de la bibliothèque MFC. Toutefois, ces fonctionnalités spécifiques à MFC ne sont pas disponibles lorsque vous modifiez un fichier .rc pour les applications Windows ne pas basée sur MFC. Cela inclut des Assistants code, les chaînes d’invite menu, affichage du contenu pour les contrôles de zone de liste déroulante et hébergement de contrôles ActiveX.

- Pour ajouter de prise en charge MFC, avec le fichier de script de ressources ouvert, dans **affichage des ressources**, mettez en surbrillance le dossier de ressources (par exemple, *MFC.rc*). Ensuite, dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **MFC Mode** à **True**.

  > [!NOTE]
  > En plus du paramètre **MFC Mode**, le fichier .rc doit faire partie d’un projet MFC. Il suffit de définir **MFC Mode** à **True** sur un .rc fichier dans un projet Win32 ne vous donne les fonctionnalités MFC.

## <a name="create-resources"></a>Créer des ressources

Vous pouvez créer une ressource en tant qu’une nouvelle ressource par défaut, ce qui signifie qu’une ressource qui n’est pas basée sur un modèle, ou en tant que ressource inspirée d’un modèle.

Utilisez le **affichage des ressources** fenêtre pour afficher les fichiers de ressources inclus dans vos projets. Développement du dossier supérieur, par exemple, *Project1.rc*, montre les types de ressources dans ce fichier. Développez chaque type de ressource pour afficher les ressources individuelles de ce type.

> [!TIP]
> Pour ouvrir le **affichage des ressources** fenêtre, accédez au menu **vue** > **affichage des ressources** ou appuyez sur **Ctrl** +  **MAJ**+**E**.

Vous pouvez utiliser avec le bouton droit sur le **affichage des ressources** fenêtre afin de lancer un menu contextuel de commandes, ou double-cliquez sur la barre de titre pour ancrer et de détacher la fenêtre. Avec le bouton droit de la barre de titre pour les autres commandes qui contrôlent le comportement de la fenêtre. Pour plus d’informations, consultez [Windows gestion](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le **affichage des ressources** windows inclut le **ajouter une ressource** boîte de dialogue avec les propriétés suivantes pour ajouter des ressources à un projet d’application de bureau Windows de C++ :

| Propriété | Description |
|---|---|
| **Type de ressource** | Spécifiez le type de ressource que vous souhaitez créer.<br/><br/>Vous pouvez développer les catégories de ressources boîte curseur et boîte de dialogue pour afficher des ressources supplémentaires, qui sont trouvent dans ...\Microsoft Visual Studio \<version\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si vous avez besoin ajouter des fichiers .rct, placez-les ici ou spécifier un autre [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md).<br/><br/>Ressources affichées au niveau supérieur dans le contrôle d’arborescence sont les ressources par défaut fournis par Visual Studio. Ressources dans les fichiers .rct apparaissent au deuxième niveau sous la catégorie appropriée. Il n’existe aucune limite prédéfinie au nombre de fichiers .rct que vous pouvez ajouter.<br/><br/> |
| **Nouveau** | Créer une ressource en fonction du type sélectionné dans le **Type de ressource** zone et ouvrez la ressource dans l’éditeur approprié.<br/><br/>Par exemple, si vous créez une ressource de boîte de dialogue, il ouvre la ressource dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md). |
| **Import** | Ouvrez le **importer** boîte de dialogue pour accéder à la ressource que vous souhaitez importer dans votre projet actuel.<br/><br/>Vous pouvez importer une image bitmap, icône, curseur, HTML, son (. WAV), ou le fichier de ressources personnalisées. |
| **Personnalisé** | Ouvrez le **nouvelle ressource personnalisée** boîte de dialogue pour créer une ressource personnalisée.<br/><br/>Inclut également un **Type de ressource** propriété qui fournit une zone de texte, vous pouvez entrer le nom du type de ressource personnalisé. Visual C++ met automatiquement le nom lorsque vous quittez.<br/><br/>Ressources personnalisées ne peuvent être modifiés que dans l’éditeur binaire. |

Lorsque vous créez une nouvelle ressource, Visual C++ lui assigne un nom unique, par exemple, `IDD_Dialog1`. Vous pouvez personnaliser cet ID de ressource en modifiant les propriétés de ressource dans l’éditeur de ressources associé ou dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Ne spécifiez pas un nom de ressource ou un ID qui est réservée par Visual Studio. Noms réservés sont `DESIGNINFO`, `HWB`, et `TEXTINCLUDE`, et l’ID réservé est `255`.

Pour créer une ressource, utilisez une des opérations suivantes :

- Dans **affichage des ressources**, sélectionnez votre fichier .rc, puis utilisez **modifier** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

   > [!TIP]
   > Vous pouvez également cliquer sur le fichier .rc dans **affichage des ressources** et choisissez **ajouter une ressource** dans le menu contextuel.

- Dans **l’Explorateur de solutions**, cliquez sur le dossier du projet, sélectionnez **ajouter** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

   > [!NOTE]
   > Si vous ne disposez pas d’un fichier .rc dans votre projet, cette étape permet de créer un. Vous pouvez ensuite répéter cette étape pour ajouter des types de ressource spécifiques au nouveau fichier .rc.

- Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), avec le bouton droit de la classe, sélectionnez **ajouter** > **ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

- Utilisez le menu **projet** > **ajouter une ressource**.

## <a name="use-resource-templates"></a>Utiliser des modèles de ressources

Un modèle de ressource est une ressource personnalisée que vous avez enregistré en tant que fichier .rct. Un modèle de ressource sert ensuite de point de départ pour la création de ressources. Modèles de ressources gagner du temps dans le développement des ressources supplémentaires ou des groupes de ressources qui partagent des fonctionnalités, telles que les contrôles standard ou répétée des éléments. Par exemple, si vous souhaitez inclure un bouton aide avec une icône de logo de société dans plusieurs boîtes de dialogue, créez un nouveau modèle de boîte de dialogue et personnalisez-le avec le bouton Aide et le logo.

Après la personnalisation d’un modèle de ressource, enregistrez vos modifications dans le dossier de modèle ou de l’emplacement spécifié dans le chemin d’accès include, afin que le nouveau modèle de ressource s’affiche sous son type de ressource dans le **ajouter une ressource** boîte de dialogue. Vous pouvez maintenant utiliser le nouveau modèle de ressource aussi souvent en fonction des besoins.

> [!NOTE]
> L'éditeur de ressources fournit automatiquement un ID de ressource unique. Vous pouvez réviser le [propriétés de ressource](../windows/changing-the-properties-of-a-resource.md) en fonction des besoins.

> [!NOTE]
> Placez les fichiers de modèles spécifiques aux langues dans les sous-répertoires du répertoire de modèle principal. Par exemple, les fichiers de modèle en anglais uniquement aller... \\< répertoire des modèles de ressource\>\1033. Visual Studio recherche les nouveaux fichiers .rct dans \Program Files\Microsoft Visual Studio \<version\>\VC\VCResourceTemplates, \Program Files\Microsoft Visual Studio \<version > \VC\VCResourceTemplates\\< LCID\> (par exemple, LCID 1033 pour l’anglais), ou n’importe où sur le [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Si vous préférez stocker vos fichiers .rct dans un autre emplacement, vous devez ajouter l’emplacement pour le chemin d’accès include.

### <a name="to-create-and-use-a-resource-template"></a>Pour créer et utiliser un modèle de ressource

1. Dans **l’Explorateur de solutions**, cliquez sur votre projet.

1. Dans le menu contextuel, sélectionnez **ajouter** > **ajouter un nouvel élément**.

1. Dans le **modèles :** volet, sélectionnez **le fichier de modèle de ressource (.rct)**.

1. Entrez un nom et un emplacement pour votre nouveau fichier .rct et choisissez **Open**.

   Le nouveau fichier .rct est ajouté à votre projet et apparaît dans **l’Explorateur de solutions** sous le **ressources** dossier.

1. Double-cliquez sur le fichier .rct pour l’ouvrir dans une fenêtre de document. Pour ajouter des ressources, cliquez sur le fichier dans la fenêtre de document et choisissez **ajouter une ressource**.

   Vous pouvez personnaliser vos ressources ajoutées et enregistrez le fichier .rct.

1. Dans le **affichage des ressources** volet, cliquez sur le fichier .rc et choisissez **ajouter une ressource**.

1. Sélectionnez le signe plus (**+**) en regard d’une ressource pour développer le nœud de ressource et afficher les modèles disponibles pour cette ressource.

1. Double-cliquez sur le modèle à utiliser.

   Vous pouvez modifier la ressource ajoutée en fonction des besoins dans son éditeur de ressources.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Guide pratique pour Gestion des ressources](../windows/how-to-copy-resources.md)<br/>
[Guide pratique pour inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)<br/>