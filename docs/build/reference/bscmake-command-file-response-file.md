---
title: BSCMAKE, fichier de commandes (fichier réponse)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295043"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE, fichier de commandes (fichier réponse)

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Vous pouvez fournir tout ou partie de l’entrée de ligne de commande dans un fichier de commandes. Spécifiez le fichier de commandes à l’aide de la syntaxe suivante :

```
BSCMAKE @filename
```

Fichier de commandes qu’un seul est autorisé. Vous pouvez spécifier un chemin d’accès avec *filename*. Faites précéder *filename* avec un arobase (**\@**). BSCMAKE n’assume pas une extension. Vous pouvez spécifier supplémentaires *sbrfiles* sur la ligne de commande après *filename*. Le fichier de commandes est un fichier texte qui contient l’entrée à BSCMAKE dans le même ordre que vous le définiriez sur la ligne de commande. Séparez les arguments de ligne de commande avec un ou plusieurs espaces, des tabulations ou des caractères de saut de ligne.

La commande suivante appelle BSCMAKE à l’aide d’un fichier de commandes :

```
BSCMAKE @prog1.txt
```

Voici un exemple de fichier de commande :

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](bscmake-reference.md)
