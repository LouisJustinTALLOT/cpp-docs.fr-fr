---
title: Blocs de description
description: NMAKE utilise des blocs de description pour associer des cibles, des dépendances et des commandes dans un makefile.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322265"
---
# <a name="description-blocks"></a>Blocs de description

Les blocs de description forment le noyau d’un makefile. Ils décrivent les *cibles,* ou les fichiers à créer, et leurs *dépendances,* les fichiers nécessaires pour créer les cibles. Un bloc de description peut inclure des *commandes,* qui décrivent comment créer les cibles à partir des dépendances. Un bloc de description est une ligne de dépendance, suivi en option par un bloc de commandes :

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Lignes de dépendance

Une *ligne de dépendance* spécifie une ou plusieurs cibles, et zéro ou plus dépendant. Si une cible n’existe pas ou a un temps plus tôt qu’une personne à charge, NMAKE exécute les commandes dans le bloc de commande. NMAKE exécute également le bloc de commande si la cible est un [pseudotarget](pseudotargets.md). Voici un exemple de ligne de dépendance :

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

Dans cette ligne `hi_bye.exe` de dépendance, est la cible. Ses dépendances `hello.obj`sont `goodbye.obj`, `helper.lib`, et . La ligne de dépendance dit NMAKE `goodbye.obj`de `helper.lib` construire la `hi_bye.exe`cible chaque fois que `hello.obj`, , ou a changé plus récemment que .

Une cible doit être au début de la ligne. Il ne peut pas être en retrait avec des espaces ou des onglets. Utilisez un`:`côlon ( ) pour séparer les cibles des personnes à charge. Les espaces ou onglets sont autorisés`:`entre les cibles, le séparateur du côlon (), et les personnes à charge. Pour diviser la ligne de dépendance,`\`utilisez une barre oblique inverse () après une cible ou une personne à charge.

Avant d’exécuter les blocs de commande, NMAKE scanne toutes les dépendances et toutes les règles d’inférence applicables pour construire un *arbre de dépendance.* Un arbre de dépendance spécifie les étapes nécessaires pour mettre à jour complètement la cible. NMAKE vérifie de façon récursive si une personne à charge est elle-même une cible dans une autre liste de dépendance. Après avoir construit l’arbre de dépendance, NMAKE vérifie les horodatages. Si les personnes à charge dans l’arbre sont plus nouvelles que la cible, NMAKE construit la cible.

## <a name="targets"></a><a name="targets"></a>Cibles

La section cibles d’une ligne de dépendance spécifie une ou plusieurs cibles. Une cible peut être n’importe quel nom de fichier valide, nom d’annuaire, ou [pseudotarget.](pseudotargets.md) Séparez plusieurs cibles en utilisant un ou plusieurs espaces ou onglets. Les cibles ne sont pas sensibles aux cas. Les chemins sont autorisés avec des noms de fichiers. Une cible et son chemin ne peuvent pas dépasser 256 caractères. Si la cible qui précède le côlon est un seul caractère, utilisez un espace de séparation. Sinon, NMAKE interprète la combinaison lettre-colon comme un spécificateur d’entraînement.

### <a name="multiple-targets"></a><a name="multiple-targets"></a>Cibles multiples

NMAKE évalue plusieurs cibles dans une seule dépendance comme si chacune d’entre elles était spécifiée dans un bloc de description distinct.

Par exemple, cette règle :

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

est évalué comme:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>Dépendances cumulatives

Les dépendances sont cumulatives dans un bloc de description, si une cible est répétée.

Par exemple, cet ensemble de règles,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

est évalué comme:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Lorsque vous avez plusieurs cibles dans plusieurs lignes de dépendance dans un bloc de description unique, NMAKE les évalue comme si chacune d’entre elles était spécifiée dans un bloc de description distinct. Cependant, seules les cibles de la dernière ligne de dépendance utilisent le bloc de commandes. NMAKE tente d’utiliser une règle d’inférence pour les autres cibles.

Par exemple, cet ensemble de règles,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

est évalué comme:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>Cibles dans plusieurs blocs de description

Pour mettre à jour une cible dans plus d’un bloc de description à l’aide de commandes différentes, spécifiez deux colons consécutifs (::) entre les cibles et les personnes à charge.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>Effets secondaires de dépendance

Vous pouvez spécifier une cible avec un côlon (:) dans deux lignes de dépendance à des endroits différents. Si les commandes apparaissent après une seule des lignes, NMAKE interprète les dépendances comme si les lignes étaient adjacentes ou combinées. Il n’invoque pas une règle d’inférence pour la dépendance qui n’a pas de commandes. Au lieu de cela, NMAKE suppose que les dépendances appartiennent à un bloc de description, et exécute les commandes spécifiées avec l’autre dépendance. Considérez cet ensemble de règles :

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

est évalué comme:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Cet effet ne se produit pas`::`si un double côlon ( ) est utilisé. Par exemple, cet ensemble de règles :

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

est évalué comme:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>Pseudotargets

Un *pseudotarget* est une étiquette utilisée à la place d’un nom de fichier dans une ligne de dépendance. Il est interprété comme un fichier qui n’existe pas, et est donc obsolète. NMAKE suppose que le chrono d’un pseudotarget est le même que le plus récent de tous ses dépendants. S’il n’a pas de personnes à charge, le temps actuel est supposé. Si un pseudotarget est utilisé comme cible, ses commandes sont toujours exécutées. Un pseudotarget utilisé comme dépendant doit également apparaître comme une cible dans une autre dépendance. Cependant, cette dépendance n’a pas besoin d’avoir un bloc de commandes.

Les noms pseudotarget suivent les règles de syntaxe du nom de fichier pour les cibles. Toutefois, si le nom n’a pas d’extension, il peut dépasser la limite de 8 caractères pour les noms de fichiers, et peut être jusqu’à 256 caractères de long.

Les pseudo-groupes sont utiles lorsque vous voulez que NMAKE construise automatiquement plus d’une cible. NMAKE ne construit que des cibles spécifiées sur la ligne de commande. Ou, si aucune cible de ligne de commande n’est spécifiée, elle ne construit que la première cible dans la première dépendance dans le makefile. Vous pouvez dire à NMAKE de construire plusieurs cibles sans les énumérer individuellement sur la ligne de commande. Écrivez un bloc de description avec une dépendance contenant un pseudotarget, et la liste des cibles que vous voulez construire comme ses personnes à charge. Ensuite, placez ce bloc de description d’abord dans le makefile, ou spécifier le pseudotarget sur la ligne de commande NMAKE.

Dans cet exemple, UPDATE est un pseudotarget.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Lorsque UPDATE est évalué, NMAKE copie tous les fichiers de l’annuaire actuel au lecteur et au répertoire spécifiés.

Dans le makefile suivant, `all` le pseudotarget construit à la fois `project1.exe` et `project2.exe` si l’une ou l’autre `all` ou pas de cible est spécifiée sur la ligne de commande. Le pseudotarget `setenv` modifie la variable `.exe` de l’environnement LIB avant que les fichiers ne soient mis à jour :

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>Dépendants

Dans une ligne de dépendance, spécifiez zéro ou plus dépendant après le côlon (`:`) ou double côlon (`::`), en utilisant n’importe quel nom de fichier valide ou [pseudotarget](pseudotargets.md). Séparer plusieurs personnes à charge en utilisant un ou plusieurs espaces ou onglets. Les personnes à charge ne sont pas sensibles aux cas. Les chemins sont autorisés avec des noms de fichiers.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>Personnes à charge déduites

Avec les personnes à charge que vous énumérez explicitement dans la ligne de dépendance, NMAKE peut supposer une *personne à charge déduite*. Une personne à charge déduite est dérivée d’une règle d’inférence et est évaluée avant les personnes à charge explicites. Lorsqu’une personne à charge déduite est dépassée par rapport à sa cible, NMAKE invoque le bloc de commande pour la dépendance. Si une personne à charge déduite n’existe pas, ou est obsolète par rapport à ses propres personnes à charge, NMAKE met à jour d’abord la personne à charge déduite. Pour plus d’informations sur les personnes à charge déduites, voir [règles d’inférence](inference-rules.md).

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>Rechercher des chemins pour les personnes à charge

Vous pouvez spécifier un chemin de recherche facultatif pour chaque personne à charge. Voici la syntaxe pour spécifier un ensemble d’annuaires à rechercher :

> **-**_répertoire_\[**;** _répertoire_...] **-**_dépendant_

Enfermer les noms d’annuaire dans les accolades (`{ }`). Séparer plusieurs répertoires avec un`;`point-virgule (). Aucun espace ou onglet n’est autorisé. NMAKE recherche le dépendant d’abord dans l’annuaire actuel, puis dans la liste des répertoires dans l’ordre spécifié. Vous pouvez utiliser une macro pour spécifier une partie ou la totalité d’un chemin de recherche. Seule la personne à charge spécifiée utilise ce chemin de recherche.

#### <a name="directory-search-path-example"></a>Exemple de parcours de recherche d’annuaire

Cette ligne de dépendance montre comment créer une spécification d’annuaire pour une recherche :

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

La `reverse.exe` cible a `retro.obj`une personne à charge, . La liste ci-jointe spécifie deux répertoires. NMAKE recherche `retro.obj` d’abord dans l’annuaire actuel. S’il n’est pas là, `\src\omega` NMAKE `e:\repo\backwards` recherche l’annuaire, puis l’annuaire.

## <a name="see-also"></a>Voir aussi

[Référence NMAKE](nmake-reference.md)
