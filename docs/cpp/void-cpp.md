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
ms.openlocfilehash: 2de019f908942a58b232877fcd9eebc4689d8e22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187477"
---
# <a name="void-c"></a>void (C++)

Lorsqu’il est utilisé en tant que type de retour de fonction, le mot clé **void** spécifie que la fonction ne retourne pas de valeur. Lorsqu’il est utilisé pour la liste de paramètres d’une fonction, **void** spécifie que la fonction n’accepte aucun paramètre. Lorsqu’il est utilisé dans la déclaration d’un pointeur, **void** spécifie que le pointeur est « Universal ».

Si le type d’un pointeur est **void\*** , le pointeur peut pointer vers n’importe quelle variable qui n’est pas déclarée avec le mot clé **const** ou **volatile** . Un pointeur d' **\*void** ne peut pas être déréférencé, sauf s’il est casté en un autre type. Un pointeur d' **\*void** peut être converti en un autre type de pointeur de données.

Un pointeur **void** peut pointer vers une fonction, mais pas vers un membre de C++classe dans.

Vous ne pouvez pas déclarer une variable de type **void**.

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
