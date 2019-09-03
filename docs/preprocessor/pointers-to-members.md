---
title: pointers_to_members, pragma
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219063"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members, pragma

**C++Plus**

Spécifie si un pointeur vers un membre de classe peut être déclaré avant sa définition de classe associée. Utilisé pour contrôler la taille du pointeur et le code requis pour interpréter le pointeur.

## <a name="syntax"></a>Syntaxe

> **#pragma pointers_to_members (** *pointeur-* DECLARATION [ **,** *la représentation la plus générale* ])

## <a name="remarks"></a>Notes

Vous pouvez placer un pragma **pointers_to_members** dans votre fichier source au lieu d’utiliser les options du compilateur [/VMB ou/VMG](../build/reference/vmb-vmg-representation-method.md) ou les [Mots clés d’héritage](../cpp/inheritance-keywords.md).

L’argument *pointer-* declaration spécifie si vous avez déclaré un pointeur vers un membre avant ou après la définition de fonction associée. L’argument *pointer-* declaration est l’un des deux symboles suivants:

| Argument | Commentaires |
|--------------|--------------|
| **full_generality** | Génère un code sécurisé, parfois non optimal. Vous utilisez **full_generality** si un pointeur vers un membre est déclaré avant la définition de classe associée. Cet argument utilise toujours la représentation de pointeur spécifiée par l’argument de *représentation le plus général* . Équivaut à /vmg. |
| **best_case** | Génère un code sécurisé et optimal à l'aide de la représentation préférentielle pour tous les pointeurs vers des membres. Nécessite de définir la classe avant de déclarer un pointeur vers un membre de la classe. La valeur par défaut est **best_case**. |

L’argument de *représentation la plus générale* spécifie la plus petite représentation de pointeur que le compilateur peut utiliser sans risque pour référencer n’importe quel pointeur vers un membre d’une classe dans une unité de traduction. L’argument peut prendre l’une des valeurs suivantes:

| Argument | Commentaires |
|--------------|--------------|
| **single_inheritance** | La représentation la plus générale est la fonction pointeur vers fonction membre héritage simple. Génère une erreur si le modèle d'héritage d'une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type multiple ou virtuel. |
| **multiple_inheritance** | La représentation la plus générale est la fonction pointeur vers fonction membre héritage multiple. Génère une erreur si le modèle d'héritage d'une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type virtuel. |
| **virtual_inheritance** | La représentation la plus générale est la fonction pointeur vers fonction membre héritage virtuel. Ne génère jamais d'erreur. **virtual_inheritance** est l’argument par défaut `#pragma pointers_to_members(full_generality)` lorsque est utilisé. |

> [!CAUTION]
> Nous vous conseillons de placer le pragma **pointers_to_members** uniquement dans le fichier de code source que vous souhaitez affecter, et uniquement après `#include` les directives. Cette pratique atténue le risque que le pragma affecte d'autres fichiers et que vous spécifiiez par erreur plusieurs définitions pour la même variable, la même fonction ou le même nom de classe.

## <a name="example"></a>Exemple

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
