---
description: 'En savoir plus sur : règles pour les instructions Module-Definition'
title: Règles s'appliquant aux instructions de définition de module
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: bca1f279a9a93690edeaabc2264d1cfe869b3e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224996"
---
# <a name="rules-for-module-definition-statements"></a>Règles s'appliquant aux instructions de définition de module

Les règles de syntaxe suivantes s’appliquent à toutes les instructions d’un fichier. def. Les autres règles qui s’appliquent à des instructions spécifiques sont décrites avec chaque instruction.

- Les instructions, les mots clés d’attribut et les identificateurs spécifiés par l’utilisateur respectent la casse.

- Noms de fichiers longs contenant des espaces ou des points-virgules (;) doit être placé entre guillemets (").

- Utilisez un ou plusieurs espaces, tabulations ou caractères de saut de ligne pour séparer un mot clé d’instruction de ses arguments et pour séparer les instructions les unes des autres. Deux-points ( :) ou signe égal (=) qui désigne un argument est entouré de zéro, un ou plusieurs espaces, tabulations ou caractères de saut de ligne.

- Une instruction **Name** ou **Library** , si elle est utilisée, doit précéder toutes les autres instructions.

- Les instructions **sections** et **exports** peuvent apparaître plusieurs fois dans le fichier. def. Chaque instruction peut prendre plusieurs spécifications, qui doivent être séparées par un ou plusieurs espaces, tabulations ou caractères de saut de ligne. Le mot clé de l’instruction doit apparaître une fois avant la première spécification et peut être répété avant chaque spécification supplémentaire.

- De nombreuses instructions ont une option de ligne de commande LINK équivalente. Pour plus d’informations, consultez la description de l’option de lien correspondante.

- Les commentaires dans le fichier. def sont désignés par un point-virgule (;) au début de chaque ligne de commentaire. Un commentaire ne peut pas partager une ligne avec une instruction, mais il peut apparaître entre les spécifications dans une instruction multiligne. (Les **sections** et les **exportations** sont des instructions multilignes.)

- Les arguments numériques sont spécifiés en base 10 ou hexadécimal.

- Si un argument de chaîne correspond à un [mot réservé](reserved-words.md), il doit être placé entre guillemets doubles (").

## <a name="see-also"></a>Voir aussi

[Module-Definition (. Fichiers def)](module-definition-dot-def-files.md)
