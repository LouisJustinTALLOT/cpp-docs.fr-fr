---
title: Références (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: aafc582299402eabab2736ac7d07b6c4c397413c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244213"
---
# <a name="references-c"></a>Références (C++)

Une référence, comme un pointeur, stocke l'adresse d'un objet situé ailleurs dans la mémoire. Contrairement à un pointeur, une référence après son initialisation ne peut pas être définie pour faire référence à un autre objet ni prendre la valeur null. Il existe deux types de références : références lvalue qui font référence à un nommé variable et les références rvalue qui font référence à un [objet temporaire](../cpp/temporary-objects.md). Le & opérateur désigne une référence lvalue et & & opérateur signifie une référence rvalue ou une référence universelle (rvalue ou lvalue) en fonction du contexte.

Les références peuvent être déclarées à l'aide de la syntaxe suivante :

> \[*storage-class-specifiers*] \[*cv-qualifiers*] *type-specifiers* \[*ms-modifier*] *declarator* \[**=** *expression*]**;**

Tout déclarateur valide spécifiant une référence peut être utilisé. La syntaxe simplifiée suivante s'applique, sauf si la référence est une référence à un type de fonction ou à un type tableau :

> \[*spécificateurs de classe de stockage*] \[ *qualificateurs cv*] *spécificateurs de type* \[ **&** ou **&&**] \[ *qualificateurs cv*] *identificateur* \[ **=** *expression*]**;**

Les références sont déclarées à l'aide de la séquence suivante :

1. Les spécificateurs de déclaration :

   - Spécificateur de classe de stockage facultatif.

   - Facultatif **const** et/ou **volatile** qualificateurs.

   - Spécificateur de type : nom d'un type.

1. Déclarateur :

   - Modificateur spécifique Microsoft facultatif. Pour plus d’informations, consultez [modificateurs spécifiques Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Le **&** opérateur ou **&&** opérateur.

   - Facultatif **const** et/ou **volatile** facultatifs.

   - Identificateur.

1. Initialiseur facultatif.

Les formulaires de déclarateurs plus complexes pour les pointeurs vers des tableaux et aux fonctions s’appliquent également aux références à des tableaux et aux fonctions. Pour plus d’informations, consultez [pointeurs](../cpp/pointers-cpp.md).

Plusieurs déclarateurs et initialiseurs peuvent apparaître dans une liste séparée par des virgules après un spécificateur de déclaration unique. Exemple :

```cpp
int &i;
int &i, &j;
```

Les références, les pointeurs et les objets peuvent être déclarés ensemble :

```cpp
int &ref, *ptr, k;
```

Une référence contient l'adresse d'un objet, mais se comporte syntaxiquement comme un objet.

Dans le programme suivant, notez que le nom de l'objet, `s`, et la référence à l'objet, `SRef`, peuvent être utilisés de la même manière dans les programmes :

## <a name="example"></a>Exemple

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>Voir aussi

[Arguments de fonction de type référence](../cpp/reference-type-function-arguments.md)<br/>
[Retours de fonction de type référence](../cpp/reference-type-function-returns.md)<br/>
[Références aux pointeurs](../cpp/references-to-pointers.md)
