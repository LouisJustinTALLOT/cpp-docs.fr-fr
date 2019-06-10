---
title: Variables d’environnement CL
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821534"
---
# <a name="cl-environment-variables"></a>Variables d’environnement CL

L'outil CL utilise les variables d'environnement suivantes :

- CL et \_CL_, s’il est défini. L’outil CL ajoute les options et les arguments définis dans la variable d’environnement CL aux arguments de ligne de commande et ajoute les options et arguments définis dans \_CL_, avant le traitement.

- INCLURE, qui doit pointer vers le sous-répertoire \include de votre installation de Visual Studio.

- LIBPATH, qui spécifie les répertoires dans lesquels rechercher des fichiers de métadonnées référencés avec [#using](../../preprocessor/hash-using-directive-cpp.md). Pour plus d’informations sur LIBPATH, consultez [#using](../../preprocessor/hash-using-directive-cpp.md).

Vous pouvez définir le CL ou \_variable d’environnement CL_ à l’aide de la syntaxe suivante :

> DÉFINIR le CL = [[*option*]... [*fichier*]...] [/ link, *-opt lien* ...] \
> Définissez \_CL\_= [[*option*]... [*fichier*]...] [/ link, *-opt lien* ...]

Pour plus d’informations sur les arguments de la CL et \_CL_ variables d’environnement, consultez [syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md).

Vous pouvez utiliser ces variables d’environnement pour définir les fichiers et les options que vous utilisez le plus souvent. Puis, utilisez la ligne de commande pour donner plus des fichiers et des options à CL à des fins spécifiques. Le CL et \_variables d’environnement CL_ sont limités à 1 024 caractères (la limite d’entrée de ligne de commande).

Vous ne pouvez pas utiliser le [/D](d-preprocessor-definitions.md) permet de définir un symbole qui utilise un signe égal ( **=** ). Au lieu de cela, vous pouvez utiliser le signe dièse ( **#** ) pour un signe égal. De cette façon, vous pouvez utiliser le CL ou \_variables d’environnement CL_ pour définir les constantes du préprocesseur avec des valeurs explicites — par exemple, `/DDEBUG#1` pour définir `DEBUG=1`.

Pour plus d’informations, consultez [définir des Variables d’environnement](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Exemples

La commande suivante est un exemple de définition de la variable d’environnement CL :

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Lorsque la variable d’environnement CL est définie, si vous entrez `CL INPUT.C` à la ligne de commande, la commande effective devient :

> CL/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. ENTRÉE DE OBJ. C

Dans l'exemple suivant, une commande CL simple compile les fichiers sources FILE1.c et FILE2.c, puis lie les fichiers objets FILE1.obj, FILE2.obj et FILE3.obj :

> SET CL=FILE1.C FILE2.C \
> SET \_CL_=FILE3.OBJ \
> CL

Ces variables d’environnement effectuer l’appel à CL ont le même effet que la ligne de commande suivante :

> CL FILE1. C FICHIER2. C FICHIER3. OBJ

## <a name="see-also"></a>Voir aussi

[Définition des Options du compilateur](compiler-command-line-syntax.md) \
[Options du compilateur MSVC](compiler-options.md)
