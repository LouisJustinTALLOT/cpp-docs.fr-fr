---
title: Options BSCMAKE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16fd9bc8813179d23e83ab0a21a84ad815501bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377853"
---
# <a name="bscmake-options"></a>Options BSCMAKE
Cette section décrit les options disponibles pour contrôler BSCMAKE. Plusieurs options contrôlent le contenu du fichier d’informations de consultation en excluant ou incluant certaines informations. Les options d’exclusion peuvent autoriser BSCMAKE pour s’exécuter plus rapidement et peuvent entraîner un fichier .bsc plus petit. Noms d’options respectent la casse (à l’exception de **/Help** et **/NOLOGO**).  
  
 Uniquement **/NOLOGO** et **/o** sont disponibles dans l’environnement de développement Visual Studio.  Consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md) pour plus d’informations sur les pages de propriétés d’un projet d’accès.  
  
 /EI ( `filename`...)  
 Exclut le contenu des fichiers include spécifiés à partir du fichier d’informations. Pour spécifier plusieurs fichiers, séparez les noms par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous ne spécifiez qu’un seul `filename`. Utilisez **/Ei** avec la **/Es** option pour exclure des fichiers n’a ne pas exclues **/Es**.  
  
 /EL  
 Exclut les symboles locaux. La valeur par défaut consiste à inclure les symboles locaux. Pour plus d’informations sur les symboles locaux, consultez [création d’un fichier .sbr](../../build/reference/creating-an-dot-sbr-file.md).  
  
 /Em  
 Exclut les symboles dans le corps de macros. Utilisez **/Em** pour inclure uniquement les noms de macros dans le fichier d’informations de consultation. La valeur par défaut est pour inclure les noms des macros et le résultat de leur expansion.  
  
 /Er ( `symbol`...)  
 Exclut les symboles spécifiés à partir du fichier d’informations. Pour spécifier plusieurs noms de symboles, séparez les noms par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous ne spécifiez qu’un seul `symbol`.  
  
 /Es  
 Exclut le fichier d’informations de chaque fichier include spécifié avec un chemin d’accès absolu ou trouvé dans un chemin d’accès absolu spécifié dans la variable d’environnement INCLUDE. (En règle générale, il s’agit du système de fichiers include, qui contiennent de nombreuses informations que vous devrez peut-être pas dans votre fichier d’informations.) Cette option n’exclut pas les fichiers spécifiés sans un chemin d’accès ou avec des chemins d’accès relatifs ou des fichiers que se trouvent dans un chemin d’accès relatif dans INCLUDE. Vous pouvez utiliser la **/Ei** option avec **/Es** pour exclure des fichiers **/Es** n’exclut pas. Si vous souhaitez exclure certains fichiers qui **/Es** exclut, utilisez **/Ei** au lieu de **/Es** et répertorient les fichiers que vous souhaitez exclure.  
  
 / errorreport : [none &#124; invite &#124; file d’attente &#124; envoi]  
 Vous permet d’envoyer des informations à Microsoft concernant des erreurs internes dans bscmake.exe.  
  
 Pour plus d’informations sur **/errorreport**, consultez [/errorReport (signaler les erreurs du compilateur interne)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 /HELP  
 Affiche un résumé de la syntaxe de ligne de commande BSCMAKE.  
  
 /IU  
 Inclut les symboles non référencés. Par défaut, BSCMAKE n’enregistre pas tous les symboles qui sont définis mais pas référencés. Si un fichier .sbr a été compressé, cette option n’a aucun effet sur ce fichier, car le compilateur a déjà supprimé les symboles non référencés.  
  
 /n  
 Force une génération non incrémentielle. Utilisez **/n** pour forcer une génération complète du fichier d’informations Parcourir ou non un fichier .bsc existe et pour empêcher la troncature des fichiers .sbr. Consultez [génération d’un fichier .bsc par BSCMAKE](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md).  
  
 /NOLOGO  
 Supprime le message de copyright de BSCMAKE.  
  
 /o `filename`  
 Spécifie un nom pour le fichier d’informations. Par défaut, BSCMAKE donne le fichier d’informations de consultation le nom de base du premier fichier .sbr et une extension .bsc.  
  
 /S ( `filename`...)  
 Indique à BSCMAKE pour traiter le fichier include spécifié la première fois qu’elle est rencontrée et exclure dans le cas contraire. Cette option permet de gagner du temps de traitement lorsqu’un fichier (par exemple, un en-tête, ou .h, fichier pour un .c ou .cpp source) est inclus dans plusieurs fichiers sources, mais n’est pas affecté par les directives de prétraitement chaque fois. Vous pouvez souhaiter utiliser cette option si un fichier est modifié d’une manière qui est sans importance pour le fichier d’informations de consultation que vous créez. Pour spécifier plusieurs fichiers, séparez les noms par un espace et placez la liste entre parenthèses. Parenthèses ne sont pas nécessaires si vous ne spécifiez qu’un seul `filename`. Si vous souhaitez exclure le fichier chaque fois qu’elle est incluse, utilisez le **/Ei** ou **/Es** option.  
  
 /v  
 Fournit une sortie détaillée, ce qui inclut le nom de chaque fichier .sbr en cours de traitement et des informations sur le déroulement de BSCMAKE.  
  
 /?  
 Affiche un bref résumé de syntaxe de ligne de commande BSCMAKE.  
  
 La ligne de commande indique à BSCMAKE pour effectuer une génération complète de MAIN.bsc à partir de trois fichiers .sbr. Il indique également que les instances en double de TOOLBOX.h :  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence BSCMAKE](../../build/reference/bscmake-reference.md)