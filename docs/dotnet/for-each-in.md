---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: b1dfe3a32f88c0e9456e3d73c31c533911f8d3ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404453"
---
# <a name="for-each-in"></a>for each, in

Itère dans un tableau ou une collection. Ce mot clé non standard est disponible dans C++/CLI et les projets natifs C++. Toutefois, son utilisation n'est pas recommandée. Envisagez d’utiliser une norme [Range-based pour instruction (C++)](../cpp/range-based-for-statement-cpp.md) à la place.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

> **pour chaque (** *type* *identificateur* **dans** *expression* **) {}**<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;*statements*<br/>
> **}**

### <a name="parameters"></a>Paramètres

*type*<br/>
Type d'élément `identifier`.

*identifier*<br/>
La variable d'itération qui représente l'élément de collection.  Lorsque `identifier` est un [opérateur de référence de suivi](../extensions/tracking-reference-operator-cpp-component-extensions.md), vous pouvez modifier l’élément.

*expression*<br/>
Expression ou collection de tableaux. L'élément de collection doit pouvoir être converti par le compilateur en type d'élément `identifier`.

*statements*<br/>
Une ou plusieurs instructions à exécuter.

### <a name="remarks"></a>Notes

L’instruction `for each` permet d’itérer au sein d’une collection. Vous pouvez modifier les éléments d'une collection, mais vous ne pouvez ni ajouter ni supprimer des éléments.

Le *instructions* sont exécutées pour chaque élément du tableau ou de la collection. Une fois l'itération terminée pour tous les éléments de la collection, le contrôle est transféré à l'instruction placée après le bloc `for each`.

`for each` et `in` sont [mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

Pour plus d'informations :

- [Itération au sein d’une collection de bibliothèque standard C++ en utilisant for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [Guide pratique pour Itérer des tableaux avec for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [Guide pratique pour Itérer une Collection générique en utilisant for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [Guide pratique pour Itérer une Collection définie par l’utilisateur avec for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Configuration requise

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

**Sortie**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

**Remarques**

La syntaxe CLR est identique à la **tous les Runtimes** syntaxe, sauf comme suit.

*expression*<br/>
Collection ou expression de tableau managé. L’élément de collection doit être converti par le compilateur peut convertir à partir <xref:System.Object> à la *identificateur* type.

*expression* correspond à un type qui implémente <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, ou un type qui définit un `GetEnumerator` méthode qui retourne un type qui implémente <xref:System.Collections.IEnumerator> ou déclare toutes les méthodes qui sont définies dans `IEnumerator`.

### <a name="requirements"></a>Configuration requise

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

**Sortie**

```Output
abcd

Testing
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md)
