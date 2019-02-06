---
title: 'Procédure : Inclure des ressources au moment de la compilation (C++)'
ms.date: 11/04/2016
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
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 52145d2a656a7cac0d07a43ceaf298fbebb5ad40
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764075"
---
# <a name="how-to-include-resources-at-compile-time"></a>Procédure : Inclure des ressources au moment de la compilation

Normalement, il est facile et pratique d’utiliser la disposition par défaut de toutes les ressources dans un fichier de script (.rc) de ressources. Toutefois, vous pouvez ajouter des ressources dans d’autres fichiers à votre projet actif au moment de la compilation en les répertoriant dans la **directives de compilation** zone le **Include des ressources** boîte de dialogue.

Il existe plusieurs raisons qui justifient le placement des ressources dans un autre fichier que le fichier .rc principal :

- Pour ajouter des commentaires aux instructions de ressource qui ne sont pas supprimées lorsque vous enregistrez le fichier .rc.

   Les éditeurs de ressources ne lisent pas directement .rc ou `resource.h` fichiers. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme le processus de compilation avec un élément normal, informations non symboliques (par exemple, les commentaires) sont ignorées pendant le processus de compilation. Chaque fois que le fichier .aps obtient désynchronisé avec le fichier .rc, le fichier .rc est régénéré (par exemple, lorsque vous enregistrez, l’éditeur de ressources remplace le fichier .rc et `resource.h` fichier). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé.

- Inclure des ressources qui ont déjà été développées et testées et n’avez pas besoin davantage modification. (Tous les fichiers inclus mais dépourvus d’extension .rc ne sont pas modifiables par les éditeurs de ressources.)

- Pour inclure les ressources qui sont utilisés par plusieurs projets différents, ou qui font partie d’un système de contrôle de version du code source et donc il doit exister dans un emplacement central où les modifications affectent tous les projets.

- Vous souhaitez inclure des ressources (par exemple des ressources RCDATA) qui ont un format personnalisé. Les ressources RCDATA peuvent avoir des spécifications particulières. Par exemple, vous ne pouvez pas utiliser une expression en tant que valeur pour le champ nameID. Consultez la documentation du Kit de développement logiciel Windows pour plus d’informations.

Si vous avez des sections dans vos fichiers .rc existants qui répondent à ces conditions, vous devez placer les sections dans un ou plusieurs fichiers .rc distincts et les incluent dans votre projet en utilisant le **Include des ressources** boîte de dialogue. Le *nom_projet*fichier .rc2 créé dans le sous-répertoire \res d’un nouveau projet est utilisé à cet effet.

Vous pouvez utiliser la **Include des ressources** boîte de dialogue dans un projet C++ à modifier l’environnement classique de stockage de toutes les ressources dans le fichier .rc de projet et toutes les [symboles](../windows/symbols-resource-identifiers.md) dans Resource.h.

Pour ouvrir le **Include des ressources** de fichiers dans la boîte de dialogue, avec le bouton droit une .rc [affichage des ressources](../windows/resource-view-window.md), puis choisissez **Include des ressources** dans le menu contextuel. Cette boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Fichier d’en-tête de symbole**|Vous permet de modifier le nom du fichier d'en-tête où sont stockées les définitions de symbole de votre fichier de ressources. Pour plus d’informations, consultez [modification des noms de symbole de fichiers d’en-tête](../windows/changing-the-names-of-symbol-header-files.md).|
|**Directives de symboles en lecture seule**|Vous permet d’inclure des fichiers d’en-tête qui contiennent les symboles qui ne doit pas être modifiées pendant une session d’édition. Par exemple, vous pouvez inclure un fichier de symboles partagé entre plusieurs projets. Vous pouvez également inclure des fichiers MFC .h. Pour plus d’informations, consultez [symboles notamment partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md).|
|**Directives de compilation**|Vous permet d’inclure des fichiers de ressources qui sont créés et modifiés séparément à partir des ressources dans votre fichier de ressources principal, contiennent des directives de compilation (par exemple, ces directives qui incluent des ressources de manière conditionnelle) ou contiennent des ressources dans un format personnalisé. Vous pouvez également utiliser le **zone directives de compilation** pour inclure des fichiers de ressources MFC standards. Pour plus d’informations, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).|

> [!NOTE]
> Entrées de ces zones de texte apparaissent dans le fichier .rc marqué par `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, et `TEXTINCLUDE 3` respectivement. Pour plus d’informations, consultez [TN035 : À l’aide de plusieurs fichiers de ressources et les fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Une fois que vous avez apporté des modifications à votre fichier de ressources en utilisant le **Include des ressources** boîte de dialogue, vous devez fermer le fichier .rc et puis le rouvrir pour que les modifications entrent en vigueur. Pour plus d’informations, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le Guide du développeur .NET Framework.

## <a name="to-include-resources-in-your-project-at-compile-time"></a>Pour inclure des ressources dans votre projet au moment de la compilation

1. Placez les ressources dans un fichier de script de ressources portant un nom de fichier unique. N’utilisez pas *nom_projet*.rc, car ce nom est le nom de fichier utilisé pour le fichier de script de ressources principal.

1. Cliquez sur le fichier .rc (dans [affichage des ressources](../windows/resource-view-window.md)) et choisissez **Include des ressources** dans le menu contextuel.

1. Dans le **directives de compilation** zone, ajoutez le [#include](../preprocessor/hash-include-directive-c-cpp.md) directive de compilateur pour inclure le fichier de ressources dans le fichier de ressources principal dans l’environnement de développement.

   Les ressources des fichiers inclus de cette façon sont intégrées à votre fichier exécutable au moment de la compilation. Ils ne sont pas directement disponibles pour l’édition ou la modification lorsque vous travaillez sur un fichier .rc principal de votre projet. Ouvrir les fichiers .rc inclus séparément. Tous les fichiers inclus mais dépourvus d’extension .rc ne sont pas modifiables par les éditeurs de ressources.

## <a name="to-specify-include-directories-for-a-specific-resource-rc-file-c"></a>Pour spécifier les répertoires include d’une ressource spécifique (fichier .rc) (C++)

1. Cliquez sur le fichier .rc dans l’Explorateur de solutions et sélectionnez **propriétés** dans le menu contextuel.

1. Dans le **Pages de propriétés** boîte de dialogue, sélectionnez le **ressources** nœud dans le volet gauche, puis spécifiez les répertoires dans include supplémentaires le **autres répertoiresinclude**propriété.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[TN035 : À l’aide de plusieurs fichiers de ressources et les fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
