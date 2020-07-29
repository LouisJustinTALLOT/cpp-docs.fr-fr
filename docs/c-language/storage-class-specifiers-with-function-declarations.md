---
title: Spécificateurs de classe de stockage avec déclarations de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: e27cc6ac748c0af3063dbc5b608114761da8b7dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211695"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Spécificateurs de classe de stockage avec déclarations de fonction

Vous pouvez utiliser le **`static`** **`extern`** spécificateur de classe de stockage ou dans les déclarations de fonction. Les fonctions ont toujours des durées de vie globales.

**Spécifique à Microsoft**

Les déclarations de fonctions au niveau interne ont la même signification que les déclarations de fonctions au niveau externe. Cela signifie qu'une fonction est visible de son point de déclaration jusqu'au reste de l'unité de traduction, même si elle est déclarée au niveau de la portée locale.

**FIN spécifique à Microsoft**

Les règles de visibilité des fonctions varient légèrement des règles pour les variables, comme suit :

- Une fonction déclarée comme étant **`static`** visible uniquement dans le fichier source dans lequel elle est définie. Les fonctions du même fichier source peuvent appeler la **`static`** fonction, mais les fonctions dans d’autres fichiers sources ne peuvent pas y accéder directement par nom. Vous pouvez déclarer une autre **`static`** fonction portant le même nom dans un fichier source différent sans conflit.

- Les fonctions déclarées comme **`extern`** sont visibles dans tous les fichiers sources du programme (sauf si vous redéclarez ultérieurement une telle fonction comme **`static`** ). Toute fonction peut appeler une **`extern`** fonction.

- Les déclarations de fonction qui omettent le spécificateur de classe de stockage sont **`extern`** par défaut.

**Spécifique à Microsoft**

Microsoft permet la redéfinition d’un **`extern`** identificateur en tant que **`static`** .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](../c-language/c-storage-classes.md)
