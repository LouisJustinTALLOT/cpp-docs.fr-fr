---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: fddfc2e3295552414a00692006ab12725dc07d52
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213110"
---
# <a name="void-c"></a>void (C++)

Lorsqu’il est utilisé en tant que type de retour de fonction, le **`void`** mot clé spécifie que la fonction ne retourne pas de valeur. Lorsqu’il est utilisé pour la liste de paramètres d’une fonction, **`void`** spécifie que la fonction n’accepte aucun paramètre. En cas d’utilisation dans la déclaration d’un pointeur, **`void`** spécifie que le pointeur est « universel ».

Si le type d’un pointeur **est \* void**, le pointeur peut pointer vers n’importe quelle variable qui n’est pas déclarée avec le **`const`** **`volatile`** mot clé ou. Un **pointeur \* void** ne peut pas être déréférencé, sauf s’il est casté en un autre type. Un **pointeur \* void** peut être converti en un autre type de pointeur de données.

Un **`void`** pointeur peut pointer vers une fonction, mais pas vers un membre de classe en C++.

Vous ne pouvez pas déclarer une variable de type **`void`** .

## <a name="example"></a>Exemple

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types intégrés](../cpp/fundamental-types-cpp.md)
