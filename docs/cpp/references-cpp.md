---
description: 'En savoir plus sur : références (C++)'
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
ms.openlocfilehash: 1f49e089d8992a32f30e1a384d5f0c36fa327c0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250047"
---
# <a name="references-c"></a>Références (C++)

Une référence, comme un pointeur, stocke l'adresse d'un objet situé ailleurs dans la mémoire. Contrairement à un pointeur, une référence après son initialisation ne peut pas être définie pour faire référence à un autre objet ni prendre la valeur null. Il existe deux genres de références : les références lvalue qui font référence à une variable nommée et les références rvalue qui font référence à un [objet temporaire](../cpp/temporary-objects.md). L’opérateur & désigne une référence lvalue et l’opérateur && signifie soit une référence rvalue, soit une référence universelle (rvalue ou lvalue) en fonction du contexte.

Les références peuvent être déclarées à l'aide de la syntaxe suivante :

> \[*Storage-Class-Specifiers*] \[ *CV-Qualifiers*] *type-Specifiers* \[ *MS-modifier*] expression *déclarateur* \[ **=** ]**;**

Tout déclarateur valide spécifiant une référence peut être utilisé. La syntaxe simplifiée suivante s'applique, sauf si la référence est une référence à un type de fonction ou à un type tableau :

> \[*Storage-Class-Specifiers*] \[ *CV-Qualifiers*] *type-Specifiers* \[ **&** ou **&&** ] « \[ *CV-Qualifiers*] expression d' *identificateur* \[ **=** ]**;**

Les références sont déclarées à l'aide de la séquence suivante :

1. Les spécificateurs de déclaration :

   - Spécificateur de classe de stockage facultatif.

   - **`const`** Qualificateurs facultatifs et/ou **`volatile`** .

   - Spécificateur de type : nom d'un type.

1. Déclarateur :

   - Modificateur spécifique à Microsoft facultatif. Pour plus d’informations, consultez [modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md).

   - **&** Opérateur ou opérateur **&&** .

   - **`const`** Qualificateurs facultatifs et/ou **`volatile`** .

   - L'identificateur.

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
[Retourne une fonction de type référence](../cpp/reference-type-function-returns.md)<br/>
[Références aux pointeurs](../cpp/references-to-pointers.md)
