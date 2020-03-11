---
title: 'Comment : créer des ressources (C++)'
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
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866119"
---
# <a name="how-to-create-resources-c"></a>Comment : créer des ressources (C++)

Vous pouvez créer des ressources pour votre projet en procédant comme suit :

- À l’aide d’un fichier de script de ressources.

   > [!NOTE]
   > Cette étape est nécessaire avant d’ajouter des ressources.

- L’ajout de ressources à votre projet et l’utilisation de l' **affichage des ressources**.

- Utilisation d’un modèle de ressource pour créer des ressources personnalisées.

## <a name="use-resource-script-files"></a>Utiliser des fichiers de script de ressources

Avant de créer et d’ajouter de nouvelles ressources à votre projet, vous devez d’abord créer un fichier de script de ressources (. RC).

> [!NOTE]
> Vous pouvez uniquement ajouter un fichier de script de ressources à un projet existant chargé dans l’IDE de Visual Studio. Vous ne pouvez pas créer un script de ressources autonome en dehors du projet, même si les fichiers de modèle de ressource (. RCT) peuvent être créés à tout moment.

### <a name="to-create-a-resource-script-file"></a>Pour créer un fichier de script de ressources

1. Placez le focus sur votre dossier de projet existant dans **Explorateur de solutions**, par exemple *MyProject*.

   > [!NOTE]
   > Ne confondez pas le dossier du projet avec le dossier de solution dans **Explorateur de solutions**. Si vous placez le focus sur le dossier de **solution** , vous n’aurez pas les mêmes choix **Ajouter un nouvel élément** .

1. Dans le menu, accédez à **projet** > **Ajouter un nouvel élément**.

1. Sélectionnez le **dossier C++ visuel** et choisissez **fichier de ressources (. RC)** dans le volet droit.

1. Donnez un nom à votre fichier de script de ressources dans la zone de texte **nom** , puis sélectionnez **ouvrir**.

### <a name="to-open-a-resource-script-file"></a>Pour ouvrir un fichier de script de ressources

Vous pouvez afficher les ressources dans un fichier de script de ressources sans ouvrir de projet. Le fichier de script s’ouvre dans une fenêtre de document, par opposition à l' **affichage des ressources**.

> [!NOTE]
> Certaines commandes ne sont disponibles que si le fichier est ouvert en mode autonome, ce qui signifie qu’en dehors d’un projet sans avoir chargé au préalable le projet. Par exemple, pour utiliser la commande **Enregistrer sous** et enregistrer un fichier avec un format ou un nom de fichier différent, le fichier doit être ouvert en mode autonome.

- Pour ouvrir un fichier de script de ressources en dehors d’un projet, dans le menu, accédez à **fichier** > **ouvrir**, puis choisissez **fichier**. Accédez au fichier de script de ressources, mettez en surbrillance le fichier, puis choisissez **ouvrir**.

    > [!NOTE]
    > Il peut arriver que vous souhaitiez afficher le contenu du fichier de script de ressources de votre projet sans utiliser les éditeurs de ressources pour ouvrir une ressource. Par exemple, vous souhaitez rechercher une chaîne dans toutes les boîtes de dialogue du fichier de ressources sans avoir à ouvrir chacune d'elles séparément. Vous pouvez facilement ouvrir le fichier de ressources au format texte pour afficher toutes les ressources qu’il contient et effectuer des opérations globales prises en charge par l’éditeur de texte.
    >
    > Pour ouvrir un fichier de script de ressources au format texte, utilisez la flèche de déroulement située à droite du bouton **ouvrir** à l’étape ci-dessus, puis choisissez **Ouvrir avec**. Sélectionnez **éditeur du code source (texte)** et dans la liste déroulante **ouvrir en tant que** , sélectionnez **texte** et la ressource s’ouvre dans l’éditeur de **code source** .

- Pour ouvrir plusieurs scripts de ressources, suivez la même étape ci-dessus pour chaque fichier que vous souhaitez ouvrir, par exemple, *source1. RC* et *source2. RC*. Ensuite, lorsque les deux fichiers. RC sont ouverts dans des fenêtres de documents distincts, utilisez le menu **fenêtre** ou cliquez avec le bouton droit sur l’un des fichiers, puis choisissez **nouveau groupe d’onglets horizontal** ou **nouveau groupe d’onglets vertical**. Les fenêtres sont maintenant en mosaïque afin que vous puissiez les afficher simultanément.

> [!TIP]
> Vous pouvez ouvrir les fichiers de script de ressources en cliquant avec le bouton droit sur le fichier. rc dans **Explorateur de solutions**, en sélectionnant **Ouvrir avec** et en choisissant l' **éditeur de code source (texte)** .

Lorsque vous générez une application MFC (Microsoft Foundation Class) pour Windows à l’aide de l' [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de fichiers de base, y compris un fichier de script de ressources (. RC), qui contient les fonctionnalités de base de MFC. Toutefois, ces fonctionnalités spécifiques à MFC ne sont pas disponibles lors de la modification d’un fichier. RC pour les applications Windows qui ne sont pas basées sur MFC. Cela comprend les assistants code, les chaînes d’invite de menu, le contenu de liste pour les contrôles de zone de liste déroulante et l’hébergement de contrôles ActiveX.

- Pour ajouter la prise en charge MFC, avec le fichier de script de ressources ouvert, dans **affichage des ressources**, mettez en surbrillance le dossier ressources (par exemple, *MFC. RC*). Ensuite, dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **true**au **mode MFC** .

  > [!NOTE]
  > En plus de définir le **mode MFC**, le fichier. RC doit faire partie d’un projet MFC. L’affectation de la **valeur true** au **mode MFC** sur un fichier. rc dans un projet Win32 n’offre pas de fonctionnalités MFC.

## <a name="create-resources"></a>Créer des ressources

Vous pouvez créer une ressource en tant que nouvelle ressource par défaut, ce qui signifie qu’il s’agit d’une ressource qui n’est pas basée sur un modèle ou d’une ressource basée sur un modèle.

Utilisez la fenêtre **affichage des ressources** pour afficher les fichiers de ressources inclus dans vos projets. Le développement du dossier supérieur, par exemple *Projet1. RC*, montre les types de ressources dans ce fichier. Développez chaque type de ressource pour afficher les ressources individuelles de ce type.

> [!TIP]
> Pour ouvrir la fenêtre **affichage des ressources** , accédez à la **vue** menu > **autres > Windows** **Affichage des ressources** ou appuyez sur **CTRL**+**MAJ**+**E**.

Vous pouvez également cliquer avec le bouton droit sur la fenêtre de **affichage des ressources** pour ouvrir un menu contextuel de commandes ou double-cliquer sur la barre de titre pour ancrer et détacher la fenêtre. Cliquez avec le bouton droit sur la barre de titre pour les commandes qui contrôlent le comportement de la fenêtre. Pour plus d’informations, consultez [gestion de Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

La **affichage des ressources** Windows comprend la boîte de dialogue **Ajouter une ressource** avec les propriétés suivantes pour ajouter des C++ ressources à un projet d’application de bureau Windows :

| Propriété | Description |
|---|---|
| **Type de ressource** | Spécifiez le type de ressource que vous souhaitez créer.<br/><br/>Vous pouvez développer les catégories de ressources curseur et boîte de dialogue pour afficher des ressources supplémentaires, qui se trouvent dans *. \Microsoft Visual Studio \<version\>\VC\VCResourceTemplates\\< LCID\>\mfc.RCT*. Si vous devez ajouter des fichiers. RCT, placez-les ici ou spécifiez un autre [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Les ressources affichées au niveau supérieur dans le contrôle d’arborescence sont les ressources par défaut fournies par Visual Studio. Les ressources des fichiers. RCT apparaissent au deuxième niveau sous la catégorie appropriée. Il n’existe pas de limite prédéfinie pour le nombre de fichiers. RCT que vous pouvez ajouter.<br/><br/> |
| **Nouveau** | Créez une ressource en fonction du type sélectionné dans la zone **type de ressource** et ouvrez la ressource dans l’éditeur approprié.<br/><br/>Par exemple, si vous créez une ressource de boîte de dialogue, celle-ci ouvre la ressource dans l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md). |
| **Importer** | Ouvrez la boîte de dialogue **Importer** pour accéder à la ressource que vous souhaitez importer dans votre projet actuel.<br/><br/>Vous pouvez importer une image bitmap, une icône, un curseur, du code HTML, du son (. WAV) ou un fichier de ressources personnalisé. |
| **Personnalisée** | Ouvrez la boîte de dialogue **nouvelle ressource personnalisée** pour créer une ressource personnalisée.<br/><br/>Inclut également une propriété de **type de ressource** qui fournit une zone de texte vous permettant d’entrer le nom du type de ressource personnalisé. Le C++ visuel met automatiquement en majuscule le nom lorsque vous quittez. Les ressources personnalisées sont uniquement modifiées dans l' [Éditeur binaire](../windows/binary-editor.md). |

Lorsque vous créez une ressource, Visual C++ lui attribue un nom unique, par exemple, `IDD_Dialog1`. Vous pouvez personnaliser cet ID de ressource en modifiant les propriétés de la ressource dans l’éditeur de ressources associé ou dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Ne spécifiez pas un nom de ressource ou un ID qui est réservé par Visual Studio. Les noms réservés sont `DESIGNINFO`, `HWB`et `TEXTINCLUDE`, et l’ID réservé est `255`.

### <a name="to-create-a-resource"></a>Pour créer une ressource

- Dans **affichage des ressources**, sélectionnez votre fichier. RC, puis utilisez **modifier** > **Ajouter une ressource** et choisissez le type de ressource à ajouter à votre projet.

   > [!TIP]
   > Vous pouvez également cliquer avec le bouton droit sur le fichier. rc dans **affichage des ressources** et choisir **Ajouter une ressource** dans le menu contextuel.

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier du projet, sélectionnez **Ajouter** > **Ajouter une ressource** , puis choisissez le type de ressource à ajouter à votre projet.

   > [!NOTE]
   > Si vous ne disposez pas déjà d’un fichier. rc dans votre projet, cette étape en crée un. Vous pouvez ensuite répéter cette étape pour ajouter des types de ressource spécifiques au nouveau fichier .rc.

- Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur la classe, sélectionnez **Ajouter** > **Ajouter une ressource** , puis choisissez le type de ressource à ajouter à votre projet.

- Utilisez le **projet** de menu > **Ajouter une ressource**.

## <a name="use-resource-templates"></a>Utiliser des modèles de ressources

Un modèle de ressource est une ressource personnalisée que vous avez enregistrée en tant que fichier. RCT. Un modèle de ressource sert alors de point de départ pour la création de ressources. Les modèles de ressources vous permet de gagner du temps lors du développement de ressources supplémentaires ou de groupes de ressources qui partagent des fonctionnalités, telles que des contrôles standard ou des éléments répétés. Par exemple, si vous souhaitez inclure un bouton d’aide avec une icône de logo de société dans plusieurs boîtes de dialogue, créez un modèle de boîte de dialogue et personnalisez-le avec le bouton aide et le logo.

Après la personnalisation d’un modèle de ressource, enregistrez vos modifications dans le dossier de modèles ou l’emplacement spécifié dans le chemin d’accès include, afin que le nouveau modèle de ressource apparaisse sous son type de ressource dans la boîte de dialogue **Ajouter une ressource** . Vous pouvez maintenant utiliser le nouveau modèle de ressource aussi souvent que nécessaire.

> [!NOTE]
> L'éditeur de ressources fournit automatiquement un ID de ressource unique. Vous pouvez modifier les propriétés de la [ressource](../windows/changing-the-properties-of-a-resource.md) en fonction des besoins.

> [!NOTE]
> Placez les fichiers modèles spécifiques à une langue dans les sous-répertoires du répertoire principal du modèle. Par exemple, les fichiers de modèles en anglais sont placés dans *..\\< répertoire de modèles de ressources\>\ 1033*.
>
> Visual Studio recherche de nouveaux fichiers. RCT dans *\Program Files\Microsoft Visual studio \<version\>\VC\VCResourceTemplates*, *\Program Files\Microsoft Visual Studio \<version > \VC\VCRESOURCETEMPLATES\\< LCID\>* (comme LCID de 1033 pour l’anglais) ou n’importe où sur le [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Si vous préférez stocker vos fichiers. RCT dans un autre emplacement, vous devez ajouter l’emplacement au chemin d’accès include.

### <a name="to-create-and-use-a-resource-template"></a>Pour créer et utiliser un modèle de ressource

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet et sélectionnez **Ajouter** > **Ajouter un nouvel élément**.

1. Dans le volet **modèles :** , sélectionnez **fichier de modèle de ressource (. RCT)** .

1. Indiquez un nom et un emplacement pour votre nouveau fichier *. RCT* , puis choisissez **ouvrir**.

   Le nouveau fichier *. RCT* est ajouté à votre projet et apparaît dans **Explorateur de solutions** sous le dossier **ressources** .

1. Double-cliquez sur le fichier *. RCT* pour l’ouvrir dans une fenêtre de document. Pour ajouter des ressources, cliquez avec le bouton droit sur le fichier dans la fenêtre de document, puis choisissez **Ajouter une ressource**.

   Vous pouvez personnaliser vos ressources ajoutées et enregistrer le fichier *. RCT* .

1. Dans le volet **affichage des ressources** , cliquez avec le bouton droit sur le fichier *. RC* , puis choisissez **Ajouter une ressource**.

1. Sélectionnez le signe plus ( **+** ) en regard d’une ressource pour développer le nœud de la ressource et afficher les modèles disponibles pour cette ressource.

1. Double-cliquez sur le modèle à utiliser.

   Vous pouvez modifier la ressource ajoutée en fonction des besoins dans son éditeur de ressources.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Pour convertir un fichier de ressources existant en modèle

Une fois le fichier de script de ressources ouvert, dans le menu, accédez à **fichier** > **Enregistrer \<*nom*de fichier > sous**. Spécifiez un emplacement, puis choisissez **OK**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Comment : gérer les ressources](../windows/how-to-copy-resources.md)<br/>
[Guide pratique pour inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)<br/>