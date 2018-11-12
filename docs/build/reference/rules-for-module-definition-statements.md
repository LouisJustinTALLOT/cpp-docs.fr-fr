---
title: Règles s'appliquant aux instructions de définition de module
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: 6921043bd4618692be788ec5a61978f1178c64ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442768"
---
# <a name="rules-for-module-definition-statements"></a>Règles s'appliquant aux instructions de définition de module

Les règles de syntaxe suivantes s’appliquent à toutes les instructions dans un fichier .def. Autres règles qui s’appliquent aux instructions spécifiques sont décrites avec chaque instruction.

- Instructions, les mots clés des attributs et les identificateurs spécifié par l’utilisateur respectent la casse.

- Durée pendant laquelle les noms contenant des espaces ou des points-virgules ( ;) de fichiers doit être placé entre guillemets («).

- Utiliser un ou plusieurs espaces, des tabulations ou des caractères de saut de ligne pour séparer un mot clé d’instruction de ses arguments et pour séparer les instructions les unes des autres. Un signe deux-points ( :)) ou signe égal (=) qui désigne un argument est entouré de zéro ou plusieurs espaces, tabulations ou caractères de saut de ligne.

- Un **nom** ou **bibliothèque** instruction, si vous, doit précéder toutes les autres instructions.

- Le **SECTIONS** et **exportations** instructions peuvent apparaître plusieurs fois dans le fichier .def. Chaque instruction accepte plusieurs spécifications, qui doivent être séparées par un ou plusieurs espaces, des tabulations ou des caractères de saut de ligne. Le mot clé d’instruction doit apparaître une seule fois avant la première spécification et peut être répété avant chaque spécification supplémentaire.

- De nombreuses instructions ont une option de ligne de commande de lien équivalente. Consultez la description de l’option de liaison correspondante pour plus d’informations.

- Commentaires dans le fichier .def sont désignés par un point-virgule ( ;) au début de chaque ligne de commentaire. Un commentaire ne peuvent pas partager une ligne avec une instruction, mais il peut apparaître entre les spécifications dans une instruction multiligne. (**SECTIONS** et **exportations** sont des instructions multilignes.)

- Arguments numériques sont spécifiés en base 10 ou hexadécimale.

- Si un argument de chaîne correspond à un [mot réservé](../../build/reference/reserved-words.md), elle doit figurer entre guillemets doubles («).

## <a name="see-also"></a>Voir aussi

[Fichiers de définition de module (.Def)](../../build/reference/module-definition-dot-def-files.md)