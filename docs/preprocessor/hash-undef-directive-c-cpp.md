---
title: '#undef, directive (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220217"
---
# <a name="undef-directive-cc"></a>#undef, directive (CC++/)

Supprime (élimine) un nom créé précédemment avec `#define`.

## <a name="syntax"></a>Syntaxe

> **#undef** *identificateur*

## <a name="remarks"></a>Notes

La directive **#undef** supprime la définition actuelle de l' *identificateur*. Par conséquent, les occurrences suivantes de *identifier* sont ignorées par le préprocesseur. Pour supprimer une définition de macro à l’aide de **#undef**, attribuez uniquement l' *identificateur*de macro, et non une liste de paramètres.

Vous pouvez également appliquer la directive **#undef** à un identificateur qui n’a pas de définition précédente. Cela garantit que l'identificateur n'est pas défini. Le remplacement de macro n’est pas effectué dans les instructions **#undef** .

La directive **#undef** est généralement associée à une `#define` directive pour créer une zone dans un programme source dans lequel un identificateur a une signification particulière. Par exemple, une fonction spécifique du programme source peut utiliser des constantes manifestes pour définir les valeurs spécifiques à l'environnement qui n'affectent pas le reste du programme. La directive **#undef** fonctionne également avec la `#if` directive pour contrôler la compilation conditionnelle du programme source. Pour plus d’informations, consultez [les directives #if, #elif, #else et #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Dans l’exemple suivant, la directive **#undef** supprime les définitions d’une constante symbolique et une macro. Notez que seul l'identificateur de la macro est donné.

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Section spécifique à Microsoft**

Les macros peuvent être non définies à partir de la ligne de `/U` commande à l’aide de l’option, suivie des noms de macros à non définir. L’effet de l’émission de cette commande est équivalent à une `#undef` séquence d’instructions de *nom de macro* au début du fichier.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
