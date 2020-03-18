---
title: Fichiers de commandes CL
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440268"
---
# <a name="cl-command-files"></a>Fichiers de commandes CL

Un fichier de commandes est un fichier texte qui contient des options et des noms de fichiers que vous pourriez autrement taper sur la [ligne de commande](compiler-command-line-syntax.md) ou spécifier à l’aide de la [variable d’environnement CL](cl-environment-variables.md). CL accepte un fichier de commandes du compilateur comme argument dans la variable d’environnement CL ou sur la ligne de commande. Contrairement à la ligne de commande ou à la variable d'environnement CL, un fichier de commandes vous permet d'utiliser plusieurs lignes d'options et de noms de fichiers.

Les options et les noms de fichiers dans un fichier de commandes sont traités en fonction de l’emplacement d’un nom de fichier de commande dans la variable d’environnement CL ou sur la ligne de commande. Toutefois, si l’option/Link apparaît dans le fichier de commandes, toutes les options sur le reste de la ligne sont passées à l’éditeur de liens. Les options des lignes suivantes dans le fichier de commandes et les options sur la ligne de commande après l’appel du fichier de commandes sont toujours acceptées en tant qu’options du compilateur. Pour plus d’informations sur la façon dont l’ordre des options affecte leur interprétation, consultez [ordre des options CL](order-of-cl-options.md).

Un fichier de commandes ne doit pas contenir la commande CL. Chaque option doit commencer et se terminer sur la même ligne ; vous ne pouvez pas utiliser la barre oblique inverse ( **\\** ) pour combiner une option sur deux lignes.

Un fichier de commandes est spécifié par un arobase ( **\@** ) suivi d’un nom de fichier ; le nom de fichier peut spécifier un chemin d’accès absolu ou relatif.

Par exemple, si la commande suivante se trouve dans un fichier nommé RESP :

```
/Og /link LIBC.LIB
```

et vous spécifiez la commande CL suivante :

```
CL /Ob2 @RESP MYAPP.C
```

la commande pour CL est la suivante :

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Notez que la ligne de commande et les commandes du fichier de commandes sont effectivement combinées.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Options du compilateur MSVC](compiler-options.md)
