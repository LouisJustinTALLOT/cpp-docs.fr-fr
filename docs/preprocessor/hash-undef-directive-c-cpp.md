---
title: '#undef, Directive (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: cb3a08165e41f336df0e141f50310f191cd83257
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537265"
---
# <a name="undef-directive-cc"></a>#undef, directive (C/C++)
Supprime (élimine) un nom créé précédemment avec `#define`.

## <a name="syntax"></a>Syntaxe

```
#undef
identifier
```

## <a name="remarks"></a>Notes

Le **#undef** directive supprime la définition actuelle de *identificateur*. Par conséquent, les occurrences suivantes de *identificateur* sont ignorés par le préprocesseur. Pour supprimer une définition de macro à l’aide **#undef**, donnez uniquement la macro *identificateur* ; ne donnent pas une liste de paramètres.

Vous pouvez également appliquer le **#undef** directive à un identificateur qui n’a aucune définition précédente. Cela garantit que l'identificateur n'est pas défini. Remplacement de macro n’est pas effectué dans **#undef** instructions.

Le **#undef** directive est généralement associée à un `#define` directive permettant de créer une région dans un programme source dans lequel un identificateur a une signification particulière. Par exemple, une fonction spécifique du programme source peut utiliser des constantes manifestes pour définir les valeurs spécifiques à l'environnement qui n'affectent pas le reste du programme. Le **#undef** directive fonctionne également avec la `#if` directive pour contrôler la compilation conditionnelle du programme source. Consultez [le #if, #elif #else et #endif Directives](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) pour plus d’informations.

Dans l’exemple suivant, le **#undef** directive supprime des définitions d’une constante symbolique et une macro. Notez que seul l'identificateur de la macro est donné.

```
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Section spécifique à Microsoft**

Macros peuvent être supprimées à partir de la ligne de commande à l’aide de la `/U` option, suivie des noms de macro pour être non défini. Le fait de publier cette commande est équivalent à une séquence de `#undef` *nom de la macro* instructions au début du fichier.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)