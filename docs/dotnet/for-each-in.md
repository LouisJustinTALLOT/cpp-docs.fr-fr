---
title: for each, in
description: C++/CLI pour chaque, dans la description de l’instruction et des exemples.
ms.date: 09/25/2020
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: 7f228a773dfcbe791e26ea3e1bd8cfba7f3ab028
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413917"
---
# <a name="for-each-in"></a>for each, in

Itère dans un tableau ou une collection. Ce mot clé non standard est disponible dans C++/CLI et les projets natifs C++. Toutefois, son utilisation n’est pas recommandée. Envisagez d’utiliser à la place une [instruction for standard basée sur une plage (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

> **pour chaque (** *type* *identificateur* **de type dans l'** *expression* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*publication*\
> **}**

### <a name="parameters"></a>Paramètres

*type*<br/>
Type d'élément `identifier`.

*identificateur*<br/>
La variable d'itération qui représente l'élément de collection.  Lorsque `identifier` est un [opérateur de référence de suivi](../extensions/tracking-reference-operator-cpp-component-extensions.md), vous pouvez modifier l’élément.

*expression*<br/>
Expression ou collection de tableaux. L'élément de collection doit pouvoir être converti par le compilateur en type d'élément `identifier`.

*publication*<br/>
Une ou plusieurs instructions à exécuter.

### <a name="remarks"></a>Notes

L’instruction `for each` permet d’itérer au sein d’une collection. Vous pouvez modifier les éléments d’une collection, mais vous ne pouvez pas ajouter ou supprimer des éléments.

Les *instructions* sont exécutées pour chaque élément du tableau ou de la collection. Une fois l'itération terminée pour tous les éléments de la collection, le contrôle est transféré à l'instruction placée après le bloc `for each`.

`for each` et `in` sont des [Mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Spécifications

Option du compilateur : **/ZW**

### <a name="example"></a>Exemple

Cet exemple montre comment utiliser `for each` pour itérer au sein d'une chaîne.

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

La syntaxe CLR est identique à la syntaxe **All runtimes** , sauf dans les cas suivants.

*expression*<br/>
Collection ou expression de tableau managé. L’élément de collection doit être tel que le compilateur peut le convertir <xref:System.Object> en type d' *identificateur* .

l' *expression* prend la valeur d’un type qui implémente <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> ou un type qui définit une `GetEnumerator` méthode qui retourne un type qui implémente <xref:System.Collections.IEnumerator> ou déclare toutes les méthodes définies dans `IEnumerator` .

### <a name="requirements"></a>Spécifications

Option du compilateur : **/clr**

### <a name="example"></a>Exemple

Cet exemple montre comment utiliser `for each` pour itérer au sein d'une chaîne.

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

```Output
abcd

Testing
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md)\
[Instruction for basée sur une plage (C++)](../cpp/range-based-for-statement-cpp.md)
