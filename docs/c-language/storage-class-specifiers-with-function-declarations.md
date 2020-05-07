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
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157877"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Spécificateurs de classe de stockage avec déclarations de fonction

Vous pouvez utiliser le spécificateur de classe de stockage **static** ou `extern` dans les déclarations de fonctions. Les fonctions ont toujours des durées de vie globales.

**Spécifique à Microsoft**

Les déclarations de fonctions au niveau interne ont la même signification que les déclarations de fonctions au niveau externe. Cela signifie qu'une fonction est visible de son point de déclaration jusqu'au reste de l'unité de traduction, même si elle est déclarée au niveau de la portée locale.

**FIN spécifique à Microsoft**

Les règles de visibilité des fonctions varient légèrement des règles pour les variables, comme suit :

- Une fonction déclarée comme étant **static** est visible uniquement dans le fichier source dans lequel elle est définie. Les fonctions du même fichier source peuvent appeler la fonction **static**, mais les fonctions dans d'autres fichiers sources ne peuvent pas y accéder directement par nom. Vous pouvez déclarer une autre fonction **static** avec le même nom dans un fichier source différent sans conflit.

- Les fonctions déclarées comme `extern` sont visibles dans tous les fichiers sources du programme (sauf si vous redéclarer ultérieurement une fonction comme étant **static**). Toute fonction peut appeler une fonction `extern`.

- Les déclarations de fonctions qui omettent le spécificateur de classe de stockage sont `extern` par défaut.

**Spécifique à Microsoft**

Microsoft permet la redéfinition d'un identificateur `extern` comme étant **static**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](../c-language/c-storage-classes.md)
