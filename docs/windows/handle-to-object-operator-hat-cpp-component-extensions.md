---
title: Handle de l’opérateur Object (^) (C++ / c++ / CLI et c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fe5bf67df643f83d555d3f2d6fc9a0aadf84b01
ms.sourcegitcommit: 68cd127a6606f0aed2eb1bc9a75cdfb95b9b6526
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204888"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Handle de l’opérateur Object (^) (C++ / c++ / CLI et c++ / CX)

Le *déclarateur de handle* (`^`, prononcé « chapeau »), modifie le type [spécificateur](../cpp/overview-of-declarators.md) pour indiquer que l’objet déclaré doit être supprimé automatiquement lorsque le système détermine que l’objet est ne seront plus accessibles.

## <a name="accessing-the-declared-object"></a>Accès à l'objet déclaré

Une variable déclarée avec le déclarateur de handle se comporte comme un pointeur vers l'objet. Toutefois, la variable pointe vers l'objet entier, ne peut pas pointer vers un membre de l'objet et ne prend pas en charge les opérations arithmétiques sur les pointeurs. Utilisez l'opérateur d'indirection (`*`) pour accéder à l'objet et l'opérateur d'accès aux membres flèche (`->`) pour accéder à un membre de l'objet.

## <a name="windows-runtime"></a>Windows Runtime

Le compilateur utilise le modèle COM *décompte* mécanisme pour déterminer si l’objet n’est plus utilisé et peut être supprimé. Ceci est possible car un objet dérivé d'une interface Windows Runtime est en fait un objet COM. Le nombre de références est incrémenté lorsque l'objet est créé ou copié et il est décrémenté lorsque l'objet prend la valeur null ou bascule hors de portée. Si le nombre de références atteint zéro, l'objet est supprimé automatiquement et immédiatement.

L'avantage du déclarateur de handle est que dans COM vous devez gérer explicitement le nombre de références pour un objet, ce qui est un processus fastidieux et sujet aux erreurs. Autrement dit, pour incrémenter ou décrémenter le nombre de références, vous devez appeler les méthodes AddRef() et Release() de l’objet. Toutefois, si vous déclarez un objet avec le déclarateur de handle, le compilateur génère du code qui s’ajuste automatiquement le décompte de références.

Pour plus d’informations sur la façon d’instancier un objet, consultez [ref nouvelle](../windows/ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Le système utilise le CLR *RÉCUPÉRATEUR de mémoire* mécanisme pour déterminer si l’objet n’est plus utilisé et peut être supprimé. Le Common Langage Runtime gère un tas sur lequel il alloue des objets et utilise des références managées (variables) dans votre programme pour indiquer l'emplacement des objets sur le tas. Lorsqu'un objet n'est plus utilisé, la mémoire qu'il occupait sur le tas est libérée. Régulièrement, le garbage collector compacte le tas pour mieux utiliser la mémoire libérée. Le compactage du tas peut déplacer des objets sur le tas, ce qui invalide les emplacements référencés par des références managées. Toutefois, le garbage collector connaît l'emplacement de toutes les références managées et il les met automatiquement à jour pour indiquer l'emplacement actuel des objets sur le tas.

Les pointeurs (`*`) et les références (`&`) C++ natifs n'étant pas des références managées, le garbage collector ne peut pas mettre à jour automatiquement les adresses vers lesquelles ils pointent. Pour résoudre ce problème, utilisez le déclarateur de handle pour spécifier une variable que le garbage collector connaît et peut mettre à jour automatiquement.

Pour plus d’informations, consultez [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Exemples

Cet exemple montre comment créer une instance d’un type référence sur le tas managé.  Cet exemple montre également que vous pouvez initialiser un handle avec un autre, générant ainsi deux références au même objet sur le tas managé et récupéré par le garbage collector. Notez que l’assignation [nullptr](../windows/nullptr-cpp-component-extensions.md) à un handle ne marque pas l’objet pour le garbage collection.

```cpp
// mcppv2_handle.cpp
// compile with: /clr
ref class MyClass {
public:
   MyClass() : i(){}
   int i;
   void Test() {
      i++;
      System::Console::WriteLine(i);
   }
};

int main() {
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass->Test();

   MyClass ^ p_MyClass2;
   p_MyClass2 = p_MyClass;

   p_MyClass = nullptr;
   p_MyClass2->Test();
}
```

```Output
1
2
```

L’exemple suivant montre comment déclarer un handle vers un objet sur le tas managé, où le type d’objet est un type valeur boxed. Il montre également comment obtenir le type valeur à partir de l'objet converti.

```cpp
// mcppv2_handle_2.cpp
// compile with: /clr
using namespace System;

void Test(Object^ o) {
   Int32^ i = dynamic_cast<Int32^>(o);

   if(i)
      Console::WriteLine(i);
   else
      Console::WriteLine("Not a boxed int");
}

int main() {
   String^ str = "test";
   Test(str);

   int n = 100;
   Test(n);
}
```

```Output
Not a boxed int
100
```

Cet exemple montre que l’idiome C++ commun de l’utilisation un `void*` pointeur pour pointer vers un objet arbitraire est remplacé par `Object^`, qui peut contenir un handle vers n’importe quelle classe de référence. Il montre également que tous les types, tels que les tableaux et les délégués, peuvent être convertis en handle d'objet.

```cpp
// mcppv2_handle_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Collections;
public delegate void MyDel();
ref class MyClass {
public:
   void Test() {}
};

void Test(Object ^ x) {
   Console::WriteLine("Type is {0}", x->GetType());
}

int main() {
   // handle to Object can hold any ref type
   Object ^ h_MyClass = gcnew MyClass;

   ArrayList ^ arr = gcnew ArrayList();
   arr->Add(gcnew MyClass);

   h_MyClass = dynamic_cast<MyClass ^>(arr[0]);
   Test(arr);

   Int32 ^ bi = 1;
   Test(bi);

   MyClass ^ h_MyClass2 = gcnew MyClass;

   MyDel^ DelInst = gcnew MyDel(h_MyClass2, &MyClass::Test);
   Test(DelInst);
}
```

```Output
Type is System.Collections.ArrayList

Type is System.Int32

Type is MyDel
```

Cet exemple montre qu'un handle peut être déréférencé et qu'un membre est accessible via un handle déréférencé.

```cpp
// mcppv2_handle_4.cpp
// compile with: /clr
using namespace System;
value struct DataCollection {
private:
   int Size;
   array<String^>^ x;

public:
   DataCollection(int i) : Size(i) {
      x = gcnew array<String^>(Size);
      for (int i = 0 ; i < Size ; i++)
         x[i] = i.ToString();
   }

   void f(int Item) {
      if (Item >= Size)
      {
         System::Console::WriteLine("Cannot access array element {0}, size is {1}", Item, Size);
         return;
      }
      else
         System::Console::WriteLine("Array value: {0}", x[Item]);
   }
};

void f(DataCollection y, int Item) {
   y.f(Item);
}

int main() {
   DataCollection ^ a = gcnew DataCollection(10);
   f(*a, 7);   // dereference a handle, return handle's object
   (*a).f(11);   // access member via dereferenced handle
}
```

```Output
Array value: 7

Cannot access array element 11, size is 10
```

Cet exemple montre qu’une référence native (`&`) ne peut pas lier à un **int** membre d’un type managé, comme le **int** peut être stocké dans le tas de garbage collectées et ne pas suivre les références natives déplacement d’objets dans le tas managé. La solution consiste à utiliser une variable locale ou à remplacer `&` par `%` afin d'en faire une référence de suivi.

```cpp
// mcppv2_handle_5.cpp
// compile with: /clr
ref struct A {
   void Test(unsigned int &){}
   void Test2(unsigned int %){}
   unsigned int i;
};

int main() {
   A a;
   a.i = 9;
   a.Test(a.i);   // C2664
   a.Test2(a.i);   // OK

   unsigned int j = 0;
   a.Test(j);   // OK
}
```

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Opérateur de référence de suivi](../windows/tracking-reference-operator-cpp-component-extensions.md)
