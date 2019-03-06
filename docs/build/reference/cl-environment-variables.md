---
title: Variables d'environnement CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 47d6966cdc821cee4bd9ffd61b36c0c79143b6c2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412456"
---
# <a name="cl-environment-variables"></a>Variables d'environnement CL

L'outil CL utilise les variables d'environnement suivantes :

- CL et \_CL\_, s’il est défini. L’outil CL ajoute les options et les arguments définis dans la variable d’environnement CL pour les arguments de ligne de commande et ajoute les options et arguments définis dans \_CL\_, avant le traitement.

- INCLUDE, qui doit pointer vers le sous-répertoire \include de votre installation Visual C++.

- LIBPATH, qui spécifie les répertoires dans lesquels rechercher des fichiers de métadonnées référencés avec [#using](../../preprocessor/hash-using-directive-cpp.md). Consultez `#using` pour plus d'informations sur LIBPATH.

Vous pouvez définir le CL ou \_CL\_ variable d’environnement à l’aide de la syntaxe suivante :

> DÉFINIR le CL = [[*option*]... [*fichier*]...] [/ link, *-opt lien* ...] Définissez \_CL\_= [[*option*]... [*fichier*]...] [/ link, *-opt lien* ...]

Pour plus d’informations sur les arguments de la CL et \_CL\_ variables d’environnement, consultez [du compilateur de ligne de commande syntaxe](../../build/reference/compiler-command-line-syntax.md).

Vous pouvez utiliser ces variables d'environnement pour définir les fichiers et options que vous utilisez le plus souvent, et utiliser la ligne de commande afin de définir des fichiers et des options spécifiques pour des objectifs spécifiques. Le CL et \_CL\_ variables d’environnement sont limités à 1 024 caractères (la limite d’entrée de ligne de commande).

Vous ne pouvez pas utiliser l'option /D pour définir un symbole qui utilise un signe égal (=). Vous pouvez remplacer le signe égal par un signe dièse (#). De cette façon, vous pouvez utiliser le CL ou \_CL\_ variables d’environnement pour définir les constantes du préprocesseur avec des valeurs explicites — par exemple, `/DDEBUG#1` pour définir `DEBUG=1`.

Pour plus d’informations, consultez [définir des Variables d’environnement](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Exemples

Voici un exemple de définition de la variable d’environnement CL :

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Lorsque cette variable est définie, si vous entrez `CL INPUT.C` en ligne de commande, il s’agit la commande effective :

> CL/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. ENTRÉE DE OBJ. C

Dans l'exemple suivant, une commande CL simple compile les fichiers sources FILE1.c et FILE2.c, puis lie les fichiers objets FILE1.obj, FILE2.obj et FILE3.obj :

> SET CL=FILE1.C FILE2.C SET \_CL\_=FILE3.OBJ CL

Cela a le même effet que la ligne de commande suivante :

> CL FILE1. C FICHIER2. C FICHIER3. OBJ

## <a name="see-also"></a>Voir aussi

[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)
