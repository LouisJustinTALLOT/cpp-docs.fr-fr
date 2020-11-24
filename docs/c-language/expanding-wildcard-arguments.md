---
title: Développement des arguments avec caractères génériques
description: Comment utiliser une option de l’éditeur de liens pour traiter des arguments de ligne de commande génériques dans vos programmes.
ms.date: 11/20/2020
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.openlocfilehash: b847a5dd8af577a4e30edcd9bc7fc34add296c17
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483306"
---
# <a name="expanding-wildcard-arguments"></a>Développement des arguments avec caractères génériques

L’expansion des arguments génériques est spécifique à Microsoft.

Lorsque vous exécutez un programme C, vous pouvez utiliser l’un des deux caractères génériques, le point d’interrogation ( **`?`** ) et l’astérisque ( **`*`** ), pour spécifier des arguments de nom de fichier et de chemin d’accès sur la ligne de commande.

Par défaut, les caractères génériques ne sont pas développés dans les arguments de ligne de commande. Vous pouvez remplacer la routine normale de chargement du vecteur d’arguments par `argv` une version qui développe les caractères génériques en établissant une liaison avec le *`setargv.obj`* *`wsetargv.obj`* fichier ou. Si votre programme utilise une `main` fonction, liez avec *`setargv.obj`* . Si votre programme utilise une `wmain` fonction, liez avec *`wsetargv.obj`* . Ces deux éléments ont un comportement équivalent. 

Pour établir une liaison avec *`setargv.obj`* ou *`wsetargv.obj`* , utilisez l' **`/link`** option. Par exemple :

**`cl example.c /link setargv.obj`**

Les caractères génériques sont développés de la même façon que les commandes du système d'exploitation.

## <a name="see-also"></a>Voir aussi

[Options de lien](../c-runtime-library/link-options.md)\
[`main` fonction et exécution du programme](../c-language/main-function-and-program-execution.md)
