---
description: 'En savoir plus sur : fichier de commandes BSCMAKE (fichier réponse)'
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
ms.openlocfilehash: 4bb321cd7aa705d7e33d0f539ab3e0aa2e3cb8bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187154"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE, fichier de commandes (fichier réponse)

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Vous pouvez fournir tout ou partie de l’entrée de ligne de commande dans un fichier de commandes. Spécifiez le fichier de commandes à l’aide de la syntaxe suivante :

```
BSCMAKE @filename
```

Un seul fichier de commandes est autorisé. Vous pouvez spécifier un chemin d’accès avec le *nom de fichier*. Faites précéder le *nom de fichier* d’un arobase ( **\@** ). BSCMAKE ne suppose pas d’extension. Vous pouvez spécifier des *sbrfiles* supplémentaires sur la ligne de commande après le *nom de fichier*. Le fichier de commandes est un fichier texte qui contient l’entrée dans BSCMAKE dans le même ordre que celui que vous spécifiez sur la ligne de commande. Séparez les arguments de ligne de commande par un ou plusieurs espaces, tabulations ou caractères de saut de ligne.

La commande suivante appelle BSCMAKE à l’aide d’un fichier de commandes :

```
BSCMAKE @prog1.txt
```

Voici un exemple de fichier de commandes :

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
