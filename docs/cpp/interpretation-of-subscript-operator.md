---
title: Interprétation de l'opérateur Indice
ms.date: 08/27/2018
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
ms.openlocfilehash: 1c3d5bca66cb294503805fd5b7691331ac380ae5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446603"
---
# <a name="interpretation-of-subscript-operator"></a>Interprétation de l'opérateur Indice

Comme d’autres opérateurs, l’opérateur d’indice (**\[]**) peut être redéfini par l’utilisateur. Le comportement par défaut de l'opérateur d'indice, s'il n'est pas surchargé, est de combiner le nom d'un tableau et l'indice à l'aide de la méthode suivante :

\*((*nom de tableau*) + (*indice*))

Comme dans toute addition qui implique des types pointeur, la mise à l'échelle est exécutée automatiquement pour ajuster la taille du type. Par conséquent, la valeur résultante n’est pas *indice* octets à partir de l’origine de *nom de tableau*; au lieu de cela, il est le *indice*-ième élément du tableau. (Pour plus d’informations sur cette conversion, consultez [opérateurs additifs](../cpp/additive-operators-plus-and.md).)

De même, pour des tableaux multidimensionnels, l'adresse est dérivée à l'aide de la méthode suivante :

((*nom de tableau*) + (*indice*1 \* *max*2 \* *max*3 \* ... \* *max*n) + (*indice*2 \* *max*3 \* ... \* *max*n) +... + *indice*n))

## <a name="see-also"></a>Voir aussi

[Tableaux](../cpp/arrays-cpp.md)<br/>
