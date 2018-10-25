---
title: Opérateur de référence de suivi (C++ / c++ / CLI et c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- '%'
dev_langs:
- C++
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f2277e09bc4835cabd73d9be5177042dd0817e5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056098"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Opérateur de référence de suivi (C++ / c++ / CLI et c++ / CX)

Un *référence de suivi* (`%`) se comporte comme une référence C++ ordinaire (`&`), à ceci près que lorsqu’un objet est assigné à une référence de suivi, le décompte de références de l’objet est incrémenté.

## <a name="all-platforms"></a>Toutes les plateformes

Une référence de suivi possède les caractéristiques suivantes.

- L'assignation d'un objet à une référence de suivi provoque l'incrémentation du nombre de références de l'objet.

- Une référence native (`&`) est le résultat lorsque vous déréférencez un `*`. Une référence de suivi (`%`) est le résultat lorsque vous déréférencez un `^`. Tant que vous avez un `%` à un objet, l’objet reste actif en mémoire.

- L'opérateur d'accès aux membres point (`.`) est utilisé pour accéder à un membre de l'objet.

- Les références de suivi sont valides pour les types valeur et les handles (par exemple `String^`).

- Une référence de suivi ne peut pas être assignée à une valeur null ou **nullptr** valeur. Une référence de suivi peut être réassignée à un autre objet valide autant de fois que nécessaire.

- Une référence de suivi ne peut pas être utilisée comme opérateur de prise d'adresse unaire.

## <a name="windows-runtime"></a>Windows Runtime

Une référence de suivi se comporte comme une référence C++ standard, sauf qu'un % inclus un comptage des références. L'extrait de code suivant montre comment effectuer une conversion entre les types % et ^ :

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

L'exemple suivant montre comment passer un ^ en fonction qui accepte un %.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>Common Language Runtime

En C++/CLI, vous pouvez utiliser une référence de suivi à un handle quand vous établissez une liaison à un objet de type CLR sur le tas récupéré par le garbage collector.

Dans le CLR, la valeur d'une variable de référence de suivi est mise à jour automatiquement chaque fois que le garbage collector déplace l'objet référencé.

Une référence de suivi peut être déclarée uniquement sur la pile. Une référence de suivi ne peut pas être membre d'une classe.

Il est impossible d'avoir une référence C++ native à un objet sur le tas récupéré par le garbage collector.

Pour plus d'informations sur les références de suivi en C++/CLI, consultez :

- [Guide pratique pour utiliser des références de suivi dans C++-CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Exemples

L'exemple suivant pour C++/CLI montre comment utiliser une référence de suivi avec des types managés et natifs.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

L'exemple suivant pour C++/CLI montre comment lier une référence de suivi à un tableau.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```