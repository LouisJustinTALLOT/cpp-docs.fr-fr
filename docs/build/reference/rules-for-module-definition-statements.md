---
title: "Règles pour les instructions de définition de Module | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- .def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40eb4875b195871aff8d274667e005d63424a110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="rules-for-module-definition-statements"></a>Règles s'appliquant aux instructions de définition de module
Les règles de syntaxe suivantes s’appliquent à toutes les instructions dans un fichier .def. Autres règles qui s’appliquent à des instructions spécifiques sont décrites dans chaque instruction.  
  
-   Instructions, les mots clés des attributs et les identificateurs spécifiés par l’utilisateur respectent la casse.  
  
-   Durée pendant laquelle les noms contenant des espaces ou des points-virgules ( ;) de fichiers doit être entre guillemets («).  
  
-   Utilisez un ou plusieurs espaces, tabulations ou caractères de saut de ligne pour séparer un mot clé d’instruction de ses arguments et pour séparer les instructions de l’autre. Un signe deux-points ( :) ou signe égal (=) qui désigne un argument est entourée par zéro ou plusieurs espaces, de tabulations ou caractères de saut de ligne.  
  
-   A **nom** ou **bibliothèque** instruction, si vous, doit précéder toutes les autres instructions.  
  
-   Le **SECTIONS** et **exportations** instructions peuvent apparaître plusieurs fois dans le fichier .def. Chaque instruction accepte plusieurs spécifications, qui doivent être séparées par un ou plusieurs espaces, tabulations ou caractères de saut de ligne. Le mot clé instruction doit apparaître une fois avant la première spécification et peut être répété avant chaque spécification supplémentaire.  
  
-   De nombreuses instructions ont une option de ligne de commande lien équivalente. Consultez la description de l’option de liaison correspondante pour plus d’informations.  
  
-   Commentaires dans le fichier .def sont signalés par un point-virgule ( ;) au début de chaque ligne de commentaire. Un commentaire ne peuvent pas partager une ligne avec une instruction, mais il peut apparaître entre les spécifications dans une instruction multiligne. (**SECTIONS** et **exportations** sont des instructions multilignes.)  
  
-   Les arguments numériques sont spécifiés en base 10 ou hexadécimale.  
  
-   Si un argument de chaîne correspond à un [mot réservé](../../build/reference/reserved-words.md), il doit être encadré par des guillemets doubles («).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de définition de module (.Def)](../../build/reference/module-definition-dot-def-files.md)  