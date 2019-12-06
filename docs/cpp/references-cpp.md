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
ms.openlocfilehash: 2353f0861f0f249416d0bb84a7a951b1cb6d64bc
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857331"
---
# <a name="references-c"></a>Références (C++)

Une référence, comme un pointeur, stocke l'adresse d'un objet situé ailleurs dans la mémoire. Contrairement à un pointeur, une référence après son initialisation ne peut pas être définie pour faire référence à un autre objet ni prendre la valeur null. Il existe deux genres de références : les références lvalue qui font référence à une variable nommée et les références rvalue qui font référence à un [objet temporaire](../cpp/temporary-objects.md). L’opérateur & désigne une référence lvalue et l’opérateur & & signifie soit une référence rvalue, soit une référence universelle (rvalue ou lvalue) en fonction du contexte.

Les références peuvent être déclarées à l'aide de la syntaxe suivante :

> \[*storage-class-specifiers*] \[*cv-qualifiers*] *type-specifiers* \[*ms-modifier*] *declarator* \[ **=** *expression*] **;**

Tout déclarateur valide spécifiant une référence peut être utilisé. La syntaxe simplifiée suivante s'applique, sauf si la référence est une référence à un type de fonction ou à un type tableau :

> \[*Storage-Class-Specifiers*] \[*CV-Qualifiers*] *type-specifiers* \[ **&** ou **&&** ] \[*CV-Qualifiers*] *identificateur* **\[=** *expression*] **;**

Les références sont déclarées à l'aide de la séquence suivante :

1. Les spécificateurs de déclaration :

   - Spécificateur de classe de stockage facultatif.

   - Qualificateurs **const** et/ou **volatile** facultatifs.

   - Spécificateur de type : nom d'un type.

1. Déclarateur :

   - Modificateur spécifique à Microsoft facultatif. Pour plus d’informations, consultez [modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Opérateur de **&** ou opérateur de **&&** .

   - Qualificateurs **const** et/ou **volatile** facultatifs.

   - Identificateur.

1. Initialiseur facultatif.

Les formulaires déclarateurs plus complexes pour les pointeurs vers des tableaux et des fonctions s’appliquent également aux références aux tableaux et aux fonctions. Pour plus d’informations, consultez [pointeurs](../cpp/pointers-cpp.md).

Plusieurs déclarateurs et initialiseurs peuvent apparaître dans une liste séparée par des virgules après un spécificateur de déclaration unique. Par exemple :

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
