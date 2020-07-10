---
title: Fichiers de commandes CL
description: Le compilateur MSVC vous permet de spécifier des fichiers de commandes qui contiennent des options de ligne de commande.
ms.date: 07/08/2020
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 6deab4b11dcc6c53beb5b4fa8b014a56020c3420
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180940"
---
# <a name="cl-command-files"></a>Fichiers de commandes CL

Un fichier de commandes est un fichier texte qui contient les options et les noms de fichiers du compilateur. Il fournit des options que vous pourriez sinon taper sur la [ligne de commande](compiler-command-line-syntax.md), ou spécifier à l’aide de la [variable d’environnement CL](cl-environment-variables.md). CL accepte un fichier de commandes du compilateur comme argument, soit dans la variable d’environnement CL, soit sur la ligne de commande. Contrairement à la ligne de commande ou à la variable d’environnement CL, vous pouvez utiliser plusieurs lignes d’options et de noms de fichiers dans un fichier de commandes.

Les options et les noms de fichiers dans un fichier de commandes sont traités lorsqu’un nom de fichier de commande apparaît dans la variable d’environnement CL ou sur la ligne de commande. Toutefois, si l' **`/link`** option apparaît dans le fichier de commandes, toutes les options sur le reste de la ligne sont passées à l’éditeur de liens. Les options des lignes ultérieures dans le fichier de commandes, ainsi que les options de la ligne de commande après l’appel du fichier de commandes, sont toujours acceptées en tant qu’options du compilateur. Pour plus d’informations sur la façon dont l’ordre des options affecte leur interprétation, consultez [ordre des options CL](order-of-cl-options.md).

Un fichier de commandes ne doit pas contenir la commande CL. Chaque option doit commencer et se terminer sur la même ligne ; vous ne pouvez pas utiliser la barre oblique inverse ( **`\`** ) pour combiner une option sur deux lignes.

Un fichier de commandes est spécifié par un arobase ( **`@`** ) suivi d’un nom de fichier. Le nom de fichier peut spécifier un chemin d’accès absolu ou relatif.

Par exemple, si la commande suivante se trouve dans un fichier nommé RESP :

```cmd
/Ot /link LIBC.LIB
```

et vous spécifiez la commande CL suivante :

```cmd
CL /Ob2 @RESP MYAPP.C
```

la commande pour CL est la suivante :

```cmd
CL /Ob2 /Ot MYAPP.C /link LIBC.LIB
```

Ici, vous pouvez voir comment la ligne de commande et les commandes du fichier de commandes sont effectivement combinées.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Options du compilateur MSVC](compiler-options.md)
