---
title: Variables d’environnement CL
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440243"
---
# <a name="cl-environment-variables"></a>Variables d’environnement CL

L'outil CL utilise les variables d'environnement suivantes :

- CL et \_CL_, si elles sont définies. L’outil CL ajoute les options et les arguments définis dans la variable d’environnement CL aux arguments de ligne de commande et ajoute les options et les arguments définis dans \_CL_ avant le traitement.

- INCLUez, qui doit pointer vers le sous-répertoire \include de votre installation Visual Studio.

- LIBPATH, qui spécifie les répertoires dans lesquels rechercher les fichiers de métadonnées référencés avec [#using](../../preprocessor/hash-using-directive-cpp.md). Pour plus d’informations sur LIBPATH, consultez [#using](../../preprocessor/hash-using-directive-cpp.md).

Vous pouvez définir la variable d’environnement CL ou \_CL_ à l’aide de la syntaxe suivante :

> SET CL = [[*option*]... [*fichier*]...] [/Link *Link-opt* ...] \
> SET \_CL\_= [[*option*]... [*fichier*]...] [/Link *Link-opt* ...]

Pour plus d’informations sur les arguments pour les variables d’environnement CL et \_CL_, consultez [syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md).

Vous pouvez utiliser ces variables d’environnement pour définir les fichiers et les options que vous utilisez le plus souvent. Utilisez ensuite la ligne de commande pour fournir plus de fichiers et d’options à CL à des fins spécifiques. Les variables d’environnement CL et \_CL_ sont limitées à 1024 caractères (limite d’entrée de ligne de commande).

Vous ne pouvez pas utiliser l’option [/d](d-preprocessor-definitions.md) pour définir un symbole qui utilise un signe égal ( **=** ). Au lieu de cela, vous pouvez utiliser le signe dièse ( **#** ) pour un signe égal. De cette façon, vous pouvez utiliser les variables d’environnement CL ou \_CL_ pour définir des constantes de préprocesseur avec des valeurs explicites, par exemple, `/DDEBUG#1` pour définir `DEBUG=1`.

Pour obtenir des informations connexes, consultez [définir des variables d’environnement](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Exemples

La commande suivante est un exemple de définition de la variable d’environnement CL :

> SET CL =/ZP2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Lorsque la variable d’environnement CL est définie, si vous entrez `CL INPUT.C` sur la ligne de commande, la commande effective devient :

> CL/ZP2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE. ENTRÉE OBJ. Secteur

Dans l'exemple suivant, une commande CL simple compile les fichiers sources FILE1.c et FILE2.c, puis lie les fichiers objets FILE1.obj, FILE2.obj et FILE3.obj :

> SET CL = FICHIER1. C FICHIER2. Secteur
> Définissez \_CL_ = FICHIER3. OBJ
> CL

Ces variables d’environnement rendent l’appel à CL avoir le même effet que la ligne de commande suivante :

> CL. C FICHIER2. C FICHIER3. OBJ

## <a name="see-also"></a>Voir aussi

[Définition des options du compilateur](compiler-command-line-syntax.md) \
[Options du compilateur MSVC](compiler-options.md)
