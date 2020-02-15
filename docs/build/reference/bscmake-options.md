---
title: Options BSCMAKE
description: Référence aux options de ligne de commande de l’utilitaire Microsoft BSCMAKE.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257791"
---
# <a name="bscmake-options"></a>Options BSCMAKE

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de navigation et de symboles sont stockées automatiquement dans un fichier SQL Server *`.sdf`* dans le dossier de solution.

Cette section décrit les options disponibles pour le contrôle de BSCMAKE. Plusieurs options contrôlent le contenu du fichier d’informations de consultation en excluant ou incluant certaines informations. Les options d’exclusion peuvent permettre à BSCMAKE de s’exécuter plus rapidement et peuvent entraîner une plus petite *`.bsc`* fichier. Les noms d’option respectent la casse (à l’exception de **/Help** et **/nologo**).

Seuls **/nologo** et **/o** sont disponibles dans l’environnement de développement Visual Studio.  Pour plus d’informations sur l’accès aux pages de propriétés d’un projet, consultez [ C++ définir des propriétés de compilation et de génération dans Visual Studio](../working-with-project-properties.md) .

**/EI (nom de**_fichier_... **)** \
Exclut le contenu des fichiers include spécifiés du fichier d’informations de consultation. Pour spécifier plusieurs fichiers, séparez les noms par un espace et mettez la liste entre parenthèses. Les parenthèses ne sont pas nécessaires si vous spécifiez un seul *nom de fichier*. Utilisez **/EI** avec l’option **/es** pour exclure les fichiers non exclus par **/es**.

**/El**\
Exclut les symboles locaux. La valeur par défaut consiste à inclure les symboles locaux. Pour plus d’informations sur les symboles locaux, consultez [création d’un fichier. SBR](creating-an-dot-sbr-file.md).

**/Em**\
Exclut les symboles dans le corps des macros. Utilisez **/em** pour inclure uniquement les noms des macros dans le fichier d’informations de consultation. La valeur par défaut consiste à inclure les noms des macros et le résultat des expansions de macro.

**/Er (** _symbole_... **)** \
Exclut les symboles spécifiés du fichier d’informations de consultation. Pour spécifier plusieurs noms de symboles, séparez les noms par un espace et mettez la liste entre parenthèses. Les parenthèses ne sont pas nécessaires si vous spécifiez un seul *symbole*.

**/Es**\
Exclut tous les fichiers include spécifiés avec un chemin d’accès absolu, ou trouvés dans un chemin d’accès absolu spécifié dans la variable d’environnement INCLUDe. (En général, ces fichiers sont les fichiers include système, qui contiennent de nombreuses informations dont vous n’aurez peut-être pas besoin dans votre fichier d’informations de consultation.) Cette option n’exclut pas les fichiers spécifiés sans chemin d’accès, ou avec des chemins d’accès relatifs, ou les fichiers trouvés dans un chemin d’accès relatif dans INCLUDe. Vous pouvez utiliser l’option **/EI** avec **/es** pour exclure les fichiers que **/es** n’exclut pas. Si vous souhaitez exclure uniquement certains fichiers, utilisez **/EI** au lieu de **/es**, puis répertoriez les fichiers que vous souhaitez exclure.

**/errorreport :** [**aucune** &#124; **invite** &#124; de **file d’attente d'** &#124; **envoi**] \
Cette fonction est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

**/Help**\
Affiche un résumé de la syntaxe de la ligne de commande BSCMAKE.

**/Iu**\
Comprend les symboles non référencés. Par défaut, BSCMAKE n’enregistre aucun symbole qui est défini mais qui n’est pas référencé. Si un fichier de *`.sbr`* a été compressé, cette option n’a aucun effet pour ce fichier d’entrée, car le compilateur a déjà supprimé les symboles non référencés.

**/n**\
Force une génération non incrémentielle. Utilisez **/n** pour forcer une version complète du fichier d’informations de consultation, qu’il existe ou non un fichier *`.bsc`* et pour empêcher la troncation des fichiers *`.sbr`* . Découvrez [Comment BSCMAKE génère un fichier. bsc](how-bscmake-builds-a-dot-bsc-file.md).

**/Nologo**\
Supprime le message de Copyright BSCMAKE.

**/o**\ de *noms* de fichiers
Spécifie un nom pour le fichier d’informations de consultation. Par défaut, BSCMAKE donne au fichier d’informations de consultation le nom de base du premier fichier de *`.sbr`* et une extension de *`.bsc`* .

**/S (nom de**_fichier_... **)** \
Indique à BSCMAKE de traiter le fichier include spécifié la première fois qu’il est rencontré et de l’exclure dans le cas contraire. Utilisez cette option pour enregistrer le temps de traitement lorsqu’un fichier (par exemple, un en-tête ou un *`.h`* , un fichier pour un fichier source *`.c`* ou *`.cpp`* ) est inclus dans plusieurs fichiers sources, mais n’est pas modifié à chaque fois par les directives de prétraitement. Utilisez cette option si un fichier est modifié de manière non importante pour le fichier d’informations de consultation que vous créez. Pour spécifier plusieurs fichiers, séparez les noms par un espace et mettez la liste entre parenthèses. Les parenthèses ne sont pas nécessaires si vous spécifiez un seul *nom de fichier*. Si vous souhaitez exclure le fichier à chaque fois qu’il est inclus, utilisez l’option **/EI** ou **/es** .

**/v**\
Fournit une sortie détaillée, qui inclut le nom de chaque fichier *`.sbr`* en cours de traitement et des informations sur l’exécution BSCMAKE complète.

**/?** \
Affiche un bref résumé de la syntaxe de la ligne de commande BSCMAKE.

La ligne de commande suivante indique à BSCMAKE d’effectuer une build complète de MAIN. bsc à partir de trois fichiers *`.sbr`* . Il indique également à BSCMAKE d’exclure les instances dupliquées de TOOLBOX. h :

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](bscmake-reference.md)
