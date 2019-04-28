---
title: Options BSCMAKE
ms.date: 11/04/2016
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
ms.openlocfilehash: b1d62e8d122cb4f08feef60d6936359b3e246749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272869"
---
# <a name="bscmake-options"></a>Options BSCMAKE

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Cette section décrit les options disponibles pour contrôler BSCMAKE. Plusieurs options contrôlent le contenu du fichier d’informations de consultation en excluant ou incluant certaines informations. Les options d’exclusion peuvent autoriser BSCMAKE accélère l’exécution et peuvent aboutir dans un fichier .bsc plus petit. Noms d’options respectent la casse (à l’exception de **/Help** et **/NOLOGO**).

Uniquement **/NOLOGO** et **/o** sont disponibles dans l’environnement de développement Visual Studio.  Consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md) pour plus d’informations sur accéder aux pages de propriétés d’un projet.

**/EI (** *filename*... **)**<br/>
Exclut le contenu des fichiers include spécifié à partir du fichier d’informations de navigation. Pour spécifier plusieurs fichiers, séparez les noms par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous spécifiez une seule *filename*. Utilisez **/Ei** avec la **/es** possibilité d’exclure des fichiers non exclus par **/es**.

**/El**<br/>
Exclut les symboles locaux. La valeur par défaut consiste à inclure les symboles locaux. Pour plus d’informations sur les symboles locaux, consultez [création d’un fichier .sbr](creating-an-dot-sbr-file.md).

**/Em**<br/>
Exclut les symboles dans le corps de macros. Utilisez **/Em** à inclure uniquement les noms des macros dans le fichier d’informations de consultation. La valeur par défaut consiste à inclure les noms des macros et le résultat de l’expansion macro.

**/Er (** *symbole*... **)**<br/>
Exclut les symboles spécifiés à partir du fichier d’informations de navigation. Pour spécifier plusieurs noms de symboles, séparez-les par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous spécifiez une seule *symbole*.

**/Es**<br/>
Exclut le fichier d’informations de chaque fichier include spécifié avec un chemin d’accès absolu ou trouvé dans un chemin d’accès absolu spécifié dans la variable d’environnement INCLUDE. (En règle générale, il s’agit du système de fichiers include, qui contiennent un grand nombre d’informations que vous devrez peut-être pas dans votre fichier d’informations de consultation.) Cette option n’exclut pas les fichiers spécifiés sans un chemin d’accès ou avec des chemins d’accès relatifs ou des fichiers qui que se trouvent dans un chemin d’accès relatif dans INCLUDE. Vous pouvez utiliser la **/Ei** option avec **/es** pour exclure des fichiers qui **/es** n’exclut pas. Si vous souhaitez exclure certains fichiers qui **/es** exclut, utilisez **/Ei** au lieu de **/es** et répertorier les fichiers que vous souhaitez exclure.

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
Vous permet d’envoyer des informations à Microsoft concernant des erreurs internes dans bscmake.exe.

Pour plus d’informations sur **/errorreport**, consultez [/errorReport (signaler les erreurs du compilateur interne)](errorreport-report-internal-compiler-errors.md).

**/HELP**<br/>
Affiche un résumé de la syntaxe de ligne de commande BSCMAKE.

**/Iu**<br/>
Inclut les symboles non référencés. Par défaut, BSCMAKE n’enregistre pas tous les symboles qui sont définies, mais non référencés. Si un fichier .sbr a été compressé, cette option n’a aucun effet sur ce fichier, car le compilateur a déjà supprimé les symboles non référencés.

**/n**<br/>
Force une génération non incrémentielle. Utilisez **/n** pour forcer une génération complète du fichier d’informations de navigation ou non un fichier .bsc existe et pour empêcher la troncature des fichiers .sbr. Consultez [génération d’un fichier .bsc par BSCMAKE](how-bscmake-builds-a-dot-bsc-file.md).

**/NOLOGO**<br/>
Supprime le message de copyright de BSCMAKE.

**/o** *filename*<br/>
Spécifie un nom pour le fichier d’informations de consultation. Par défaut, BSCMAKE donne le fichier d’informations de consultation le nom de base du premier fichier .sbr et une extension .bsc.

**/S (** *filename*... **)**<br/>
Indique à BSCMAKE pour traiter le fichier include spécifié la première fois, qu'il est trouvé et exclure dans le cas contraire. Cette option permet de gagner du temps de traitement quand un fichier (par exemple, un en-tête, ou .h, fichier pour un .c ou .cpp source) est inclus dans plusieurs fichiers sources, mais n’est pas modifié par les directives de prétraitement chaque fois. Vous pouvez également utiliser cette option si un fichier est modifié dans les méthodes qui sont sans importance pour le fichier d’informations que vous créez. Pour spécifier plusieurs fichiers, séparez les noms par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous spécifiez une seule *filename*. Si vous souhaitez exclure le fichier chaque fois qu’il est inclus, utilisez le **/Ei** ou **/es** option.

**/v**<br/>
Fournit une sortie détaillée, qui inclut le nom de chaque fichier .sbr en cours de traitement et des informations sur le déroulement de BSCMAKE.

**/?**<br/>
Affiche un bref résumé de syntaxe de ligne de commande BSCMAKE.

La ligne de commande suivante indique à BSCMAKE pour effectuer une génération complète de MAIN.bsc à partir de trois fichiers .sbr. Il indique également que les instances en double de TOOLBOX.h :

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](bscmake-reference.md)
