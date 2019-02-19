---
title: Addition (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 48672315960e32cb324aacc6c90d3d67891f3d39
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149880"
---
# <a name="addition-"></a>Addition (+)

L’opérateur d’addition (**+**) génère l’addition de ses deux opérandes. Les deux opérandes peuvent être des types intégraux ou flottants, ou un opérande peut être un pointeur et l’autre un entier.

Lorsqu'un entier est ajouté à un pointeur, la valeur entière (*i*) est convertie en la multipliant par la taille de la valeur que le pointeur adresse. Après la conversion, la valeur entière représente les emplacements de mémoire *i*, où chaque position a une longueur spécifiée par le type pointeur. Lorsque la valeur entière convertie est ajoutée à la valeur du pointeur, il en résulte une nouvelle valeur de pointeur représentant les positions de l'adresse *i* par rapport à l'adresse d'origine. La nouvelle valeur de pointeur adresse une valeur du même type que la valeur de pointeur d'origine. Par conséquent, elle est identique à l'indexation de tableau (consultez [Tableaux unidimensionnels](../c-language/one-dimensional-arrays.md) et [Tableaux multidimensionnels](../c-language/multidimensional-arrays-c.md)). Si le pointeur de somme passe hors du tableau, sauf au premier emplacement après l'extrémité supérieure, le résultat n'est pas défini. Pour plus d'informations, consultez [Opérations arithmétiques sur les pointeurs](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)
