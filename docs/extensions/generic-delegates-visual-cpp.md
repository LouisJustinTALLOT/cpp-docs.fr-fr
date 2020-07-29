---
title: Délégués génériques (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 527f2837f0c29299727a22df8d4f3d807be0e25b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228711"
---
# <a name="generic-delegates-ccli"></a>Délégués génériques (C++/CLI)

Vous pouvez utiliser des paramètres de type générique avec des délégués. Pour plus d’informations sur les délégués, consultez [délégué (C++/CLI et C++/CX)](delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Paramètres

*attributes*<br/>
(Facultatif) Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et les classes d’attributs, consultez Attributs.

*type-parameter-identifier(s)*<br/>
Liste d’identificateurs séparés par des virgules pour les paramètres de type.

*type-parameter-constraints-clauses*<br/>
Prend la forme spécifiée dans [Contraintes sur les paramètres de type générique (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)

*accessibility-modifiers*<br/>
Facultatif Modificateurs d’accessibilité (par exemple **`public`** , **`private`** ).

*type de résultat*<br/>
Le type de retour du délégué.

*identificateur*<br/>
Nom du délégué.

*formal-parameters*<br/>
(Facultatif) Liste des paramètres du délégué.

## <a name="example"></a>Exemple

Les paramètres de type de délégué sont spécifiés à l’emplacement où un objet délégué est créé. Le délégué et la méthode associée doivent avoir la même signature. L’exemple suivant est une déclaration de délégué générique.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Exemple

L’exemple suivant montre que

- Vous ne pouvez pas utiliser le même objet délégué avec différents types construits. Permet de créer des objets délégués pour différents types.

- Un délégué générique peut être associé à une méthode générique.

- Quand une méthode générique est appelée sans spécifier les arguments de type, le compilateur tente de déduire les arguments de type pour l’appel.

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>Exemple

L’exemple suivant déclare un délégué générique `GenDelegate<ItemType>`, puis l’instancie en l’associant à la méthode `MyMethod` qui utilise le paramètre de type `ItemType`. Deux instances du délégué (un entier et un double) sont créées et appelées.

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>Voir aussi

[Génériques](generics-cpp-component-extensions.md)
