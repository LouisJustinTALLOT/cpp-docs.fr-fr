---
title: Délégués génériques (C++ / c++ / CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 78a8e0ebd1217000671cad2a266da367c76d0a67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639048"
---
# <a name="generic-delegates-ccli"></a>Délégués génériques (C++ / c++ / CLI)

Vous pouvez utiliser les paramètres de type générique avec les délégués. Pour plus d’informations sur les délégués, consultez [déléguer (C++ / c++ / CLI et c++ / CX)](../windows/delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Paramètres

*Attributs*<br/>
(Facultatif) Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et classes d’attributs, consultez attributs.

*type-paramètre-identificateur (s)*<br/>
Liste séparée par des virgules d’identificateurs pour les paramètres de type.

*type de paramètre contraintes clauses*<br/>
Prend la forme spécifiée dans [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)

*modificateurs d’accessibilité*<br/>
(Facultatif) Les modificateurs d’accessibilité (par exemple, **public**, **privé**).

*result-type*<br/>
Le type de retour du délégué.

*identifier*<br/>
Le nom du délégué.

*paramètres-formels*<br/>
(Facultatif) La liste de paramètres du délégué.

## <a name="example"></a>Exemple

Les paramètres de type de délégué sont spécifiés au niveau du point où un objet délégué est créé. Le délégué et la méthode associée doivent avoir la même signature. Voici un exemple d’une déclaration de délégué générique.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Exemple

L’exemple suivant montre que

- Vous ne pouvez pas utiliser le même objet de délégué avec différents types construits. Permet de créer des objets pour différents types de délégués différents.

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

L’exemple suivant déclare un délégué générique `GenDelegate<ItemType>`, puis l’instancie en l’associant à la méthode `MyMethod` qui utilise le paramètre de type `ItemType`. Deux instances du délégué (entier et double) sont créés et appelés.

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

[Génériques](../windows/generics-cpp-component-extensions.md)