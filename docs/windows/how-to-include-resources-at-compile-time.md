---
title: 'Procédure : Inclure des ressources au moment de la compilation (C++)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: cd2f05b4944e26d8a96b3f96e4e39fda0ad8ee48
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328387"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Procédure : Inclure des ressources au moment de la compilation (C++)

Par défaut de toutes les ressources se trouvent dans un fichier de script (.rc) de ressources, voici toutefois plusieurs raisons pour placer les ressources dans un fichier autre que le fichier .rc principal :

- Pour ajouter des commentaires aux instructions de ressource qui ne sont pas supprimées lorsque vous enregistrez le fichier .rc.

- Inclure des ressources qui ont déjà été développées et testées et n’avez pas besoin davantage modification. Tous les fichiers inclus mais dépourvus d’extension .rc ne sont pas modifiables par les éditeurs de ressources.

- Pour inclure les ressources qui sont utilisés par des projets différents, ou qui font partie d’un système de contrôle de version du code source. Ces ressources doivent exister dans un emplacement central où les modifications affectent tous les projets.

- Pour inclure des ressources (telles que des ressources RCDATA) qui sont un format personnalisé. Ressources RCDATA ont des exigences particulières où vous ne pouvez pas utiliser une expression en tant que valeur pour le `nameID` champ.

Si vous avez des sections dans vos fichiers .rc existants qui répondent à ces conditions, placez ces sections dans un ou plusieurs fichiers .rc distincts et les incluent dans votre projet en utilisant le **Include des ressources** boîte de dialogue.

## <a name="resource-includes"></a>Include des ressources

Vous pouvez ajouter des ressources à partir d’autres fichiers à votre projet au moment de la compilation en les répertoriant dans la **directives de compilation** zone le **Include des ressources** boîte de dialogue. Utilisez le **Include des ressources** boîte de dialogue pour modifier de l’environnement projet normal de stockage de toutes les ressources dans le fichier .rc de projet et toutes les [symboles](../windows/symbols-resource-identifiers.md) dans `Resource.h`.

Pour commencer, ouvrez le **Include des ressources** boîte de dialogue en cliquant sur un fichier .rc dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), sélectionnez **Include des ressources** et notez les propriétés suivantes :

| Propriété | Description |
|---|---|
| **Fichier d’en-tête de symbole** | Vous permet de modifier le nom du fichier d’en-tête où sont stockées les définitions de symbole de vos fichiers de ressources.<br/><br/>Pour plus d’informations, consultez [modification des noms de symbole de fichiers d’en-tête](../windows/changing-the-names-of-symbol-header-files.md). |
| **Directives de symboles en lecture seule** | Vous permet d’inclure des fichiers d’en-tête qui contiennent les symboles qui ne doit pas être modifiées.<br/><br/>Par exemple, les fichiers de symboles devant être partagé avec d’autres projets. Cela peut également inclure des fichiers MFC .h. Pour plus d’informations, consultez [symboles notamment partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Directives de compilation** | Vous permet d’inclure des fichiers de ressources qui sont créés et modifiés séparément à partir des ressources dans votre fichier de ressources principal, contiennent des directives de compilation (par exemple, ces directives qui incluent des ressources de manière conditionnelle) ou contiennent des ressources dans un format personnalisé.<br/><br/>Vous pouvez également utiliser le **zone directives de compilation** pour inclure des fichiers de ressources MFC standards. |

> [!NOTE]
> Entrées de ces zones de texte apparaissent dans le fichier .rc marqué par `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, et `TEXTINCLUDE 3` respectivement. Pour plus d’informations, consultez [TN035 : À l’aide de plusieurs fichiers de ressources et les fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Une fois que les modifications sont apportées à votre fichier de ressources à l’aide de la **Include des ressources** boîte de dialogue, vous devez fermer puis rouvrir le *.rc* fichier pour que les modifications entrent en vigueur.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Pour inclure des ressources dans votre projet au moment de la compilation

1. Placez les ressources dans un fichier de script de ressources portant un nom de fichier unique. N’utilisez pas *projectname.rc*, car il s’agit du nom du fichier utilisé pour le fichier de script de ressources principal.

1. Avec le bouton droit le *.rc* fichier [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) et sélectionnez **Include des ressources**.

1. Dans le **directives de compilation** zone, ajoutez le [#include](../preprocessor/hash-include-directive-c-cpp.md) directive de compilateur pour inclure le fichier de ressources dans le fichier de ressources principal dans l’environnement de développement.

Les ressources dans les fichiers inclus de cette façon sont effectuées uniquement la partie de l’exécutable au moment de la compilation et ne sont pas disponibles pour l’édition ou la modification lorsque vous travaillez sur un fichier .rc principal de votre projet. Fichiers .rc inclus doivent être ouverts séparément, et les fichiers inclus sans l’extension .rc ne sont pas modifiables par les éditeurs de ressources.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Pour spécifier les répertoires include d’un fichier de ressources spécifique (.rc)

1. Avec le bouton droit le *.rc* fichier **l’Explorateur de solutions** et sélectionnez **propriétés**.

1. Sélectionnez le **ressources** nœud dans le volet gauche et spécifiez toute supplémentaires incluent les répertoires dans le **autres répertoires include** propriété.

### <a name="to-find-symbols-in-resources"></a>Pour rechercher des symboles dans les ressources

1. Accédez au menu **modifier** > [rechercher un symbole](/visualstudio/ide/go-to).

   > [!TIP]
   > Pour utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) dans votre recherche, sélectionnez [rechercher dans les fichiers](/visualstudio/ide/reference/find-command) dans le **modifier** menu au lieu de **rechercher un symbole**. Sélectionnez le **utilisation : Les Expressions régulières** case à cocher dans la [boîte de dialogue Rechercher](/visualstudio/ide/finding-and-replacing-text) et dans le **rechercher** zone vous pouvez choisir une expression régulière recherche dans la liste déroulante. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte.

1. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez la touche accélérateur que vous souhaitez rechercher, par exemple, `ID_ACCEL1`.

1. Sélectionnez un de la **trouver** options et choisissez **suivant**.

> [!NOTE]
> Vous ne pouvez pas rechercher de symboles dans les ressources de type chaîne, accélérateur ou binaire.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Guide pratique pour Créer des ressources](../windows/how-to-create-a-resource-script-file.md)<br/>
[Guide pratique pour Gestion des ressources](../windows/how-to-copy-resources.md)<br/>