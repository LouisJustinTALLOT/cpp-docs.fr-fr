---
title: Fichiers de commandes CL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8458462304a9b739c61997505724d21bb56763f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708667"
---
# <a name="cl-command-files"></a>Fichiers de commandes CL

Un fichier de commandes est un fichier texte qui contient les options et les noms de fichiers vous taperiez sinon le [ligne de commande](../../build/reference/compiler-command-line-syntax.md) ou spécifier à l’aide de la [variable d’environnement CL](../../build/reference/cl-environment-variables.md). CL accepte un fichier de commande du compilateur en tant qu’argument dans la variable d’environnement CL ou sur la ligne de commande. Contrairement à la ligne de commande ou à la variable d'environnement CL, un fichier de commandes vous permet d'utiliser plusieurs lignes d'options et de noms de fichiers.

Options et les noms de fichiers dans un fichier de commandes sont traités en fonction de l’emplacement d’un nom de fichier de commande au sein de la variable d’environnement CL ou sur la ligne de commande. Cependant, si l’option /link apparaît dans le fichier de commandes, toutes les options sur le reste de la ligne sont passées à l’éditeur de liens. Options des lignes suivantes dans le fichier de commandes et options sur la ligne de commande après l’appel de fichier de commande sont toujours acceptées en tant qu’options du compilateur. Pour plus d’informations sur la façon dont l’ordre des options influe sur leur interprétation, consultez [ordre des Options CL](../../build/reference/order-of-cl-options.md).

Un fichier de commandes ne doit pas contenir la commande CL. Chaque option doit commencer et se terminer sur la même ligne ; Vous ne pouvez pas utiliser la barre oblique inverse (**\\**) pour combiner une option sur deux lignes.

Un fichier de commandes est spécifié par un arobase (**\@**) suivie d’un nom de fichier ; le nom de fichier peut spécifier un chemin d’accès absolu ou relatif.

Par exemple, si la commande suivante se trouve dans un fichier nommé RESP :

```
/Og /link LIBC.LIB
```

et que vous spécifiez la commande CL suivante :

```
CL /Ob2 @RESP MYAPP.C
```

la commande pour CL est comme suit :

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Notez que la ligne de commande et le fichier de commandes est en fait combinées.

## <a name="see-also"></a>Voir aussi

[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)