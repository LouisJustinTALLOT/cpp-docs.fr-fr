---
title: 'Comment : inclure des ressources au moment de la compilation (C++)'
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
ms.openlocfilehash: 5ac4cba4e8ad8a08fa1010758c5a343501d3af2c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504418"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Comment : inclure des ressources au moment de la compilation (C++)

Par défaut, toutes les ressources se trouvent dans un fichier de script de ressources (. RC). Toutefois, il existe de nombreuses raisons de placer des ressources dans un fichier autre que le fichier main. RC :

- Pour ajouter des commentaires aux instructions de ressources qui ne seront pas supprimées lorsque vous enregistrerez le fichier. rc.

- Pour inclure des ressources qui ont déjà été développées et testées et qui n’ont pas besoin d’être modifiées. Tous les fichiers inclus mais qui n’ont pas d’extension. RC ne sont pas modifiables par les éditeurs de ressources.

- Pour inclure des ressources qui sont utilisées par différents projets ou qui font partie d’un système de contrôle de version de code source. Ces ressources doivent se trouver dans un emplacement central où les modifications affectent tous les projets.

- Pour inclure des ressources (telles que des ressources RCDATA) qui sont un format personnalisé. Les ressources RCDATA ont des exigences spéciales pour lesquelles vous ne pouvez pas utiliser une expression comme valeur pour le `nameID` champ.

Si vous avez des sections dans vos fichiers. RC existants qui répondent à l’une de ces conditions, placez ces sections dans un ou plusieurs fichiers. RC distincts et incluez-les dans votre projet à l’aide de la boîte de dialogue **include des ressources** .

## <a name="resource-includes"></a>Include des ressources

Vous pouvez ajouter des ressources à partir d’autres fichiers à votre projet au moment de la compilation en les répertoriant dans la zone **directives au moment** de la compilation de la boîte de dialogue **include des ressources** . Utilisez la boîte de dialogue **include des ressources** pour modifier l’organisation de travail normale de l’environnement du projet en stockant toutes les ressources dans le fichier Project. RC et tous les [symboles](../windows/symbols-resource-identifiers.md) dans `Resource.h` .

Pour commencer, ouvrez la boîte de dialogue **include des ressources** en cliquant avec le bouton droit sur un fichier. rc dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), sélectionnez **include des ressources** et notez les propriétés suivantes :

| Propriété | Description |
|---|---|
| **Fichier d’en-tête de symbole** | Vous permet de modifier le nom du fichier d’en-tête où sont stockées les définitions de symboles de vos fichiers de ressources.<br/><br/>Pour plus d’informations, consultez [modification des noms des fichiers d’en-tête de symbole](./changing-a-symbol-or-symbol-name-id.md). |
| **Directives de symboles en lecture seule** | Vous permet d’inclure des fichiers d’en-tête qui contiennent des symboles qui ne doivent pas être modifiés.<br/><br/>Par exemple, les fichiers de symboles à partager avec d’autres projets. Cela peut également inclure des fichiers MFC. h. Pour plus d’informations, consultez [inclusion de symboles partagés (en lecture seule) ou calculés](./changing-a-symbol-or-symbol-name-id.md). |
| **Directives au moment de la compilation** | Vous permet d’inclure des fichiers de ressources qui sont créés et modifiés séparément des ressources dans votre fichier de ressources principal, qui contiennent des directives au moment de la compilation (telles que les directives qui incluent des ressources de manière conditionnelle) ou qui contiennent des ressources dans un format personnalisé.<br/><br/>Vous pouvez également utiliser la **zone directives au moment** de la compilation pour inclure des fichiers de ressources MFC standard. |

> [!NOTE]
> Les entrées de ces zones de texte apparaissent dans le fichier. RC marqué par `TEXTINCLUDE 1` , `TEXTINCLUDE 2` et, `TEXTINCLUDE 3` respectivement. Pour plus d’informations, consultez [TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Une fois les modifications apportées à votre fichier de ressources à l’aide de la boîte de dialogue **include des ressources** , vous devez fermer et rouvrir le fichier *. RC* pour que les modifications prennent effet.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Pour inclure des ressources dans votre projet au moment de la compilation

1. Placez les ressources dans un fichier de script de ressources portant un nom de fichier unique. N’utilisez pas *ProjectName. RC*, car il s’agit du nom du fichier utilisé pour le fichier de script de ressources principal.

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) , cliquez avec le bouton droit sur le fichier *. RC* , puis sélectionnez **include des ressources**.

1. Dans la zone **directives au moment** de la compilation, ajoutez la directive de compilateur [#include](../preprocessor/hash-include-directive-c-cpp.md) pour inclure le nouveau fichier de ressources dans le fichier de ressources principal de l’environnement de développement.

Les ressources des fichiers inclus de cette façon ne font partie de l’exécutable qu’au moment de la compilation et ne sont pas disponibles pour modification ou modification lorsque vous travaillez sur le fichier. RC principal de votre projet. Les fichiers. RC inclus doivent être ouverts séparément et tous les fichiers inclus sans l’extension. RC ne seront pas modifiables par les éditeurs de ressources.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Pour spécifier les répertoires Include d’un fichier de ressources spécifique (. RC)

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier *. RC* , puis sélectionnez **Propriétés**.

1. Sélectionnez le nœud **ressources** dans le volet gauche et spécifiez les autres répertoires Include dans la propriété **autres répertoires Include** .

### <a name="to-find-symbols-in-resources"></a>Pour rechercher des symboles dans les ressources

1. Accédez au menu **modifier**  >  [Rechercher un symbole](/visualstudio/ide/go-to).

   > [!TIP]
   > Pour utiliser des [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) dans votre recherche, sélectionnez [Rechercher dans les fichiers](/visualstudio/ide/reference/find-command) dans le menu **Edition** au lieu de **Rechercher le symbole**. Activez la case à cocher **utiliser : expressions régulières** dans la boîte de [dialogue Rechercher](/visualstudio/ide/finding-and-replacing-text) , puis dans la zone **Rechercher** , vous pouvez choisir une expression de recherche standard dans la liste déroulante. Lorsque vous sélectionnez une expression dans cette liste, elle est remplacée par le texte recherché dans la zone **Rechercher** .

1. Dans la zone **Rechercher** , sélectionnez une chaîne de recherche précédente dans la liste déroulante ou tapez la touche d’accès rapide que vous souhaitez rechercher, par exemple, `ID_ACCEL1` .

1. Sélectionnez l’une des options de **recherche** , puis choisissez **suivant**.

> [!NOTE]
> Vous ne pouvez pas rechercher de symboles dans les ressources de type chaîne, accélérateur ou binaire.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Comment : créer des ressources](../windows/how-to-create-a-resource-script-file.md)<br/>
[Comment : gérer les ressources](../windows/how-to-copy-resources.md)<br/>
