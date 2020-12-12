---
description: 'En savoir plus sur : void (C++)'
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: e49dfa03e289cdbace50a24cf6854d25c51b3426
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213349"
---
# <a name="void-c"></a>void (C++)

Lorsqu’il est utilisé en tant que type de retour de fonction, le **`void`** mot clé spécifie que la fonction ne retourne pas de valeur. Lorsqu’il est utilisé pour la liste de paramètres d’une fonction, **`void`** spécifie que la fonction n’accepte aucun paramètre. En cas d’utilisation dans la déclaration d’un pointeur, **`void`** spécifie que le pointeur est « universel ».

Si le type d’un pointeur est **void \* *_, le pointeur peut pointer vers n’importe quelle variable qui n’est pas déclarée avec le* `const`** **`volatile`** mot clé _ ou. Un pointeur ** \* void* _ ne peut pas être déréférencé, sauf s’il est casté en un autre type. Un _*pointeur \* void*_ peut être converti en un autre type de pointeur de données.

Un *`void`* pointeur _ * peut pointer vers une fonction, mais pas vers un membre de classe en C++.

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
