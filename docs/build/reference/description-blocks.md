---
title: Blocs de description
description: NMAKE utilise des blocs de description pour associer des cibles, des dépendances et des commandes dans un Makefile.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417298"
---
# <a name="description-blocks"></a>Blocs de description

Les blocs de description forment le cœur d’un Makefile. Ils décrivent les *cibles*, ou les fichiers à créer, ainsi que leurs *dépendances*, les fichiers nécessaires à la création des cibles. Un bloc de description peut inclure des *commandes*qui décrivent comment créer les cibles à partir des dépendances. Un bloc de description est une ligne de dépendance, éventuellement suivie d’un bloc de commandes :

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Lignes de dépendance

Une *ligne de dépendance* spécifie une ou plusieurs cibles, et zéro, un ou plusieurs dépendants. Si une cible n’existe pas ou a un horodatage antérieur à un dépendant, NMAKE exécute les commandes dans le bloc de commande. NMAKE exécute également le bloc de commande si la cible est une [pseudocible](pseudotargets.md). Voici un exemple de ligne de dépendance :

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

Dans cette ligne de dépendance, `hi_bye.exe` est la cible. Ses dépendances sont `hello.obj`, `goodbye.obj`et `helper.lib`. La ligne de dépendance indique à NMAKE de générer la cible chaque fois que `hello.obj`, `goodbye.obj`ou `helper.lib` a changé plus récemment que `hi_bye.exe`.

Une cible doit se trouver au début de la ligne. Il ne peut pas être mis en retrait avec des espaces ou des tabulations. Utilisez un signe deux-points (`:`) pour séparer les cibles des dépendants. Des espaces ou des tabulations sont autorisés entre les cibles, le séparateur deux-points (`:`) et les dépendants. Pour fractionner la ligne de dépendance, utilisez une barre oblique inverse (`\`) après une cible ou un dépendant.

Avant d’exécuter des blocs de commande, NMAKE analyse toutes les dépendances et toutes les règles d’inférence applicables pour générer une *arborescence des dépendances*. Une arborescence des dépendances spécifie les étapes nécessaires à la mise à jour complète de la cible. NMAKE vérifie de manière récursive si un dépendant est lui-même une cible dans une autre liste de dépendances. Une fois l’arborescence des dépendances générée, NMAKE vérifie les horodatages. Si des dépendances dans l’arborescence sont plus récentes que la cible, NMAKE génère la cible.

## <a name="targets"></a> Cibles

La section cibles d’une ligne de dépendance spécifie une ou plusieurs cibles. Une cible peut être un nom de fichier, un nom de répertoire ou une [pseudocible](pseudotargets.md)valide. Séparez plusieurs cibles à l’aide d’un ou plusieurs espaces ou tabulations. Les cibles ne respectent pas la casse. Les chemins d’accès sont autorisés avec les noms de fichiers. Une cible et son chemin d’accès ne peuvent pas dépasser 256 caractères. Si la cible qui précède le signe deux-points est un caractère unique, utilisez un espace de séparation. Dans le cas contraire, NMAKE interprète la combinaison de lettres-points comme un spécificateur de lecteur.

### <a name="multiple-targets"></a>Plusieurs cibles

NMAKE évalue plusieurs cibles dans une seule dépendance comme si chacune était spécifiée dans un bloc de description distinct.

Par exemple, cette règle :

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

est évaluée comme suit :

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>Dépendances cumulatives

Les dépendances sont cumulatives dans un bloc de description, si une cible est répétée.

Par exemple, cet ensemble de règles,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

est évaluée comme suit :

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Lorsque vous avez plusieurs cibles dans plusieurs lignes de dépendance dans un bloc de description unique, NMAKE les évalue comme si chacune était spécifiée dans un bloc de description distinct. Toutefois, seules les cibles de la dernière ligne de dépendance utilisent le bloc de commandes. NMAKE tente d’utiliser une règle d’inférence pour les autres cibles.

Par exemple, cet ensemble de règles,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

est évaluée comme suit :

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>Cibles dans plusieurs blocs de description

Pour mettre à jour une cible dans plusieurs blocs de description à l’aide de commandes différentes, spécifiez deux signes deux-points consécutifs ( ::) entre les cibles et les dépendants.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>Effets secondaires des dépendances

Vous pouvez spécifier une cible avec un signe deux-points ( :) dans deux lignes de dépendance à différents emplacements. Si les commandes apparaissent après une seule des lignes, NMAKE interprète les dépendances comme si les lignes étaient adjacentes ou combinées. Elle n’appelle pas de règle d’inférence pour la dépendance qui n’a pas de commande. NMAKE suppose à la place que les dépendances appartiennent à un bloc de description et exécute les commandes spécifiées avec l’autre dépendance. Tenez compte de cet ensemble de règles :

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

est évaluée comme suit :

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Cet effet ne se produit pas si un double deux-points (`::`) est utilisé. Par exemple, cet ensemble de règles :

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

est évaluée comme suit :

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>Pseudocibles

Une *pseudocible* est une étiquette utilisée à la place d’un nom de fichier dans une ligne de dépendance. Elle est interprétée comme un fichier qui n’existe pas et, par conséquent, est obsolète. NMAKE suppose que l’horodateur d’une pseudocible est le même que le plus récent de tous ses dépendants. S’il n’a pas de dépendants, l’heure actuelle est utilisée. Si une pseudocible est utilisée en tant que cible, ses commandes sont toujours exécutées. Une pseudocible utilisée comme dépendant doit également apparaître en tant que cible dans une autre dépendance. Toutefois, cette dépendance n’a pas besoin d’un bloc de commandes.

Les noms de pseudocible suivent les règles de syntaxe des noms de fichiers pour les cibles. Toutefois, si le nom n’a pas d’extension, il peut dépasser la limite de 8 caractères pour les noms de fichiers et peut comporter jusqu’à 256 caractères.

Les pseudocibles sont utiles lorsque vous souhaitez que NMAKE crée plusieurs cibles automatiquement. NMAKE génère uniquement les cibles spécifiées sur la ligne de commande. Ou, si aucune cible de ligne de commande n’est spécifiée, elle génère uniquement la première cible de la première dépendance dans le Makefile. Vous pouvez demander à NMAKE de générer plusieurs cibles sans les répertorier individuellement sur la ligne de commande. Écrivez un bloc de description avec une dépendance contenant une pseudocible, puis répertoriez les cibles que vous souhaitez générer comme dépendants. Ensuite, placez ce bloc de description en premier dans le Makefile ou spécifiez l’pseudocible sur la ligne de commande NMAKE.

Dans cet exemple, la mise à jour est une pseudocible.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Quand la mise à jour est évaluée, NMAKE copie tous les fichiers du répertoire actif dans le lecteur et le répertoire spécifiés.

Dans le Makefile suivant, la `all` de la pseudocible génère `project1.exe` et `project2.exe` si `all` ou si aucune cible n’est spécifiée sur la ligne de commande. La pseudocible `setenv` modifie la variable d’environnement LIB avant la mise à jour des fichiers `.exe` :

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>Dépendants

Dans une ligne de dépendance, spécifiez zéro ou plusieurs dépendants après le signe deux-points (`:`) ou le double signe deux-points (`::`), à l’aide de n’importe quel nom de fichier ou [pseudocible](pseudotargets.md)valide. Séparez plusieurs dépendants à l’aide d’un ou plusieurs espaces ou tabulations. Les dépendants ne respectent pas la casse. Les chemins d’accès sont autorisés avec les noms de fichiers.

### <a name="inferred-dependents"></a>Dépendants inférés

En plus des dépendants que vous répertoriez explicitement dans la ligne de dépendance, NMAKE peut supposer une dépendance *déduite*. Un dépendant inféré est dérivé d’une règle d’inférence et est évalué avant les dépendants explicites. Lorsqu’un dépendant inféré est obsolète par rapport à sa cible, NMAKE appelle le bloc de commande pour la dépendance. Si une fonction dépendante déduite n’existe pas ou est obsolète par rapport à ses propres dépendants, NMAKE met d’abord à jour la fonction dépendante déduite. Pour plus d’informations sur les dépendants inférés, consultez [règles d’inférence](inference-rules.md).

### <a name="search-paths-for-dependents"></a>Chemins de recherche des dépendants

Vous pouvez spécifier un chemin de recherche facultatif pour chaque dépendant. Voici la syntaxe pour spécifier un ensemble de répertoires dans lesquels effectuer la recherche :

> **{** \[de_répertoire_ **;** _répertoire_...] **}** _dépendant_

Placez les noms de répertoire entre accolades (`{ }`). Séparez plusieurs répertoires par un point-virgule (`;`). Aucun espace ou tabulation n’est autorisé. NMAKE recherche le premier dépendant dans le répertoire actif, puis dans la liste des répertoires dans l’ordre spécifié. Vous pouvez utiliser une macro pour spécifier tout ou partie d’un chemin de recherche. Seul le dépendant spécifié utilise ce chemin de recherche.

#### <a name="directory-search-path-example"></a>Exemple de chemin de recherche de répertoire

Cette ligne de dépendance indique comment créer une spécification de répertoire pour une recherche :

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

La `reverse.exe` cible a une `retro.obj`dépendante. La liste entre accolades spécifie deux répertoires. NMAKE recherche d’abord `retro.obj` dans le répertoire actif. Si ce n’est pas le cas, NMAKE recherche le répertoire de `\src\omega`, puis le répertoire `e:\repo\backwards`.

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)
