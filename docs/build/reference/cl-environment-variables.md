---
title: Variables d’environnement CL | Documents Microsoft
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
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f3986097bcb5028d9ad708c9a3132f5e417d502
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372609"
---
# <a name="cl-environment-variables"></a>Variables d'environnement CL

L'outil CL utilise les variables d'environnement suivantes :

- CL et \_CL\_, s’il est défini. L’outil CL ajoute les options et les arguments définis dans la variable d’environnement CL pour les arguments de ligne de commande et ajoute les options et les arguments définis dans \_CL\_, avant le traitement.

- INCLUDE, qui doit pointer vers le sous-répertoire \include de votre installation Visual C++.

- LIBPATH, qui spécifie les répertoires dans lesquels rechercher des fichiers de métadonnées référencés avec [#using](../../preprocessor/hash-using-directive-cpp.md). Consultez `#using` pour plus d'informations sur LIBPATH.

Vous pouvez définir la CL ou \_CL\_ variable d’environnement à l’aide de la syntaxe suivante :

> DÉFINIR les CL = [[*option*]... [*fichier*]...] [/ link *lien-opt* ...]  
> Définissez \_CL\_= [[*option*]... [*fichier*]...] [/ link *lien-opt* ...]

Pour plus d’informations sur les arguments de la CL et \_CL\_ variables d’environnement, consultez [syntaxe de ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md).

Vous pouvez utiliser ces variables d'environnement pour définir les fichiers et options que vous utilisez le plus souvent, et utiliser la ligne de commande afin de définir des fichiers et des options spécifiques pour des objectifs spécifiques. La CL et \_CL\_ variables d’environnement sont limités à 1 024 caractères (la limite d’entrée de ligne de commande).

Vous ne pouvez pas utiliser l'option /D pour définir un symbole qui utilise un signe égal (=). Vous pouvez remplacer le signe égal par un signe dièse (#). De cette façon, vous pouvez utiliser la CL ou \_CL\_ variables d’environnement pour définir les constantes du préprocesseur avec des valeurs explicites : par exemple, `/DDEBUG#1` pour définir `DEBUG=1`.

Pour plus d’informations, consultez [définition de Variables d’environnement](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Exemples

Voici un exemple de définition de la variable d’environnement CL :

> Définissez CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Lorsque cette variable est définie, si vous entrez `CL INPUT.C` à la ligne de commande, voici la commande effective :

> CL/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. ENTRÉE DE OBJ. C

Dans l'exemple suivant, une commande CL simple compile les fichiers sources FILE1.c et FILE2.c, puis lie les fichiers objets FILE1.obj, FILE2.obj et FILE3.obj :

> SET CL = FILE1. C FILE2. C  
> DÉFINISSEZ \_CL\_= 3. OBJ  
> CL  

Cela a le même effet que la ligne de commande suivante :

> CL FILE1. C FILE2. C, 3. OBJ

## <a name="see-also"></a>Voir aussi

[Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
[Options du compilateur](../../build/reference/compiler-options.md)
