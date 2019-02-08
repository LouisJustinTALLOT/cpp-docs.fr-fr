---
title: 'Procédure : Créer un fichier de Script de ressources (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
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
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 9055e0f787c238276d3134c2fa6a8afae0102433
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905678"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Procédure : Créer un fichier de Script de ressources (C++)

> [!NOTE]
> Le **éditeur de ressources** n’est pas disponible dans les éditions Express.
>
> Ces informations s’appliquent aux applications de bureau Windows. Les projets dans les langages .NET n’utilisent pas de fichiers de script de ressources. Pour plus d’informations, consultez [fichiers de ressources](../windows/resource-files-visual-studio.md).

## <a name="to-create-a-new-resource-script-rc-file"></a>Pour créer un fichier de script de ressources (.rc)

1. Placez le focus sur le dossier de votre projet dans **l’Explorateur de solutions**, par exemple, `MyProject`.

   > [!NOTE]
   > Ne confondez pas avec le dossier de Solution dans le dossier du projet **l’Explorateur de solutions**. Si vous placez le focus sur le **Solution** dossier, les choix disponibles dans le **ajouter un nouvel élément** boîte de dialogue (à l’étape 3) seront différent.

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **Visual C++** dossier puis choisissez **le fichier de ressources (.rc)** dans le volet droit.

1. Fournissez un nom pour votre fichier de script de ressources dans le **nom** texte zone, puis choisissez **Open**.

Vous pouvez maintenant [créer](../windows/how-to-create-a-resource.md) et ajouter de nouvelles ressources à votre fichier .rc.

> [!NOTE]
> Vous pouvez ajouter un script de ressources (fichier .rc) uniquement à un projet existant qui est chargé dans l’IDE de Visual Studio. Vous ne pouvez pas créer de fichier .rc autonome (en dehors du projet). Vous pouvez créer des[modèles de ressources](../windows/how-to-use-resource-templates.md) (fichiers .rct) à tout moment.

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>Pour ouvrir un fichier de script de ressources en dehors d’un projet C++ (autonome)

Vous pouvez afficher les ressources contenues dans un fichier .rc sans ouvrir de projet. Le fichier .rc s’ouvre dans une fenêtre de document au lieu du [affichage des ressources](../windows/resource-view-window.md) fenêtre (comme lorsque le fichier est ouvert à l’intérieur d’un projet).

> [!NOTE]
> Cette distinction est importante, car certaines commandes ne sont disponibles qu'au moment où le fichier est ouvert en mode autonome (en dehors d'un projet). Par exemple, vous pouvez uniquement enregistrer un fichier dans un format différent ou en tant qu’un autre nom de fichier lorsque le fichier est ouvert en dehors d’un projet (le **Enregistrer sous** commande n’est pas disponible lorsqu’un fichier est ouvert à l’intérieur d’un projet).

### <a name="to-open-an-rc-file-outside-a-project"></a>Pour ouvrir un fichier .rc en dehors d'un projet

1. À partir de la **fichier** menu, choisissez **Open**, puis sélectionnez **fichier**.

1. Dans le **ouvrir un fichier** boîte de dialogue, accédez au fichier de script de ressources vous voulez afficher, sélectionnez le fichier, puis sélectionnez **Open**.

   > [!NOTE]
   > Si vous ouvrez d’abord (**fichier**, **ouvrir**, **projet**), certaines commandes ne seront pas disponibles pour vous. Ouvrir un fichier en mode « autonome » signifie l'ouvrir sans charger d'abord le projet.

### <a name="to-open-multiple-rc-files-outside-a-project"></a>Pour ouvrir plusieurs fichiers .rc en dehors d'un projet

1. Ouvrez les deux fichiers de ressources en mode autonome. Par exemple, ouvrez `Source1.rc` et `Source2.rc`.

   1. À partir de la **fichier** menu, choisissez **Open**, puis sélectionnez **fichier**.

   1. Dans le **ouvrir un fichier** boîte de dialogue, accédez au premier fichier de script de ressources que vous souhaitez ouvrir (`Source1.rc`), sélectionnez le fichier, puis choisissez **ouvrir**.

   1. Répétez l’étape précédente pour ouvrir le second fichier .rc (`Source2.rc`).

       Les fichiers .rc sont désormais ouverts dans des fenêtres de documents distinctes.

1. Quand les deux fichiers .rc sont ouverts, disposez-les fenêtres en mosaïque pour pouvoir les afficher simultanément :

   - À partir de la **fenêtre** menu, choisissez **nouveau groupe d’onglets Horizontal** ou **nouveau groupe d’onglets Vertical**.

       \- ou -

   - Cliquez sur un des fichiers .rc et choisissez **nouveau groupe d’onglets Horizontal** ou **nouveau groupe d’onglets Vertical** dans le menu contextuel.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-open-a-resource-script-file-in-text-format"></a>Pour ouvrir un fichier de script de ressources au format texte

Parfois, vous souhaitez afficher le contenu du fichier de script (.rc) de ressources de votre projet sans ouvrir une ressource, par exemple une boîte de dialogue, dans son éditeur de ressources spécifique. Par exemple, vous souhaitez rechercher une chaîne dans toutes les boîtes de dialogue du fichier de ressources sans avoir à ouvrir chacune d'elles séparément.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

Vous pouvez facilement ouvrir le fichier de ressources au format texte pour afficher toutes les ressources qu’il contient et effectuer des opérations globales prises en charge par l’éditeur de texte.

> [!NOTE]
> Les éditeurs de ressources ne lisent pas directement .rc ou `resource.h` fichiers. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>Pour ouvrir un fichier de script de ressources au format texte

1. À partir de la **fichier** menu Choisissez **Open**, puis choisissez **fichier**.

1. Dans le **ouvrir un fichier** boîte de dialogue, accédez au fichier de script de ressources à afficher au format texte.

1. Sélectionnez le fichier, puis sélectionnez la flèche déroulante sur le **Open** bouton (situé à droite du bouton).

1. Choisissez **ouvrir avec** dans le menu déroulant.

1. Dans le **ouvrir avec** boîte de dialogue, sélectionnez **éditeur de Code Source (texte)**.

1. À partir de la **ouvrir en tant que** liste déroulante, sélectionnez **texte**.

   La ressource s’ouvre dans le **Code Source** éditeur.

\- ou -

1. Dans **l’Explorateur de solutions**, cliquez sur le fichier .rc.

1. Dans le menu contextuel, choisissez **ouvrir avec...** , puis sélectionnez **éditeur de Code Source (texte)**.

## <a name="to-add-mfc-support-to-resource-script-files"></a>Pour ajouter la prise en charge MFC aux fichiers de script de ressources

Normalement, lorsque vous générez une application MFC pour Windows à l’aide de la [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de base de fichiers (y compris un fichier de script (.rc) de ressources) qui contiennent les principales fonctionnalités de Microsoft Foundation classes (MFC). Toutefois, si vous modifiez un fichier .rc pour une application Windows qui n’est pas basé sur MFC, les fonctionnalités suivantes propres à l’infrastructure MFC ne sont pas disponibles :

- Assistants code MFC

- Chaînes d'invite de menu

- Contenu des listes pour les contrôles zone de liste déroulante

- Hébergement de contrôles ActiveX

Toutefois, vous pouvez ajouter prise en charge MFC aux fichiers .rc existants qui n’ont pas encore.

> [!NOTE]
> Ces étapes nécessitent MFC.

### <a name="to-add-mfc-support-to-rc-files"></a>Pour ajouter la prise en charge de MFC à des fichiers .rc

1. Ouvrez le fichier de script de ressources.

1. Dans [affichage des ressources](../windows/resource-view-window.md), mettez en surbrillance le dossier de ressources (par exemple, MFC.rc).

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), définissez le **MFC Mode** propriété **True**.

   > [!NOTE]
   > Outre la définition de cet indicateur, le fichier .rc doit faire partie d'un projet MFC. Par exemple, définissant simplement **MFC Mode** à **True** sur un fichier .rc dans Win32 projet ne vous donne aucune des fonctionnalités MFC.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)