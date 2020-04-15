---
title: Descripteur sur l’opérateur objet (^)  (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
ms.openlocfilehash: 3d08b2294da1599282feeb1739331c31d64a9e59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358331"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Descripteur sur l’opérateur objet (^)  (C++/CLI et C++/CX)

Le *déclarant de* `^`poignée (, prononcé « chapeau »), modifie le [spécificateur](../cpp/overview-of-declarators.md) de type pour signifier que l’objet déclaré doit être automatiquement supprimé lorsque le système détermine que l’objet n’est plus accessible.

## <a name="accessing-the-declared-object"></a>Accès à l'objet déclaré

Une variable déclarée avec le déclarateur de handle se comporte comme un pointeur vers l'objet. Toutefois, la variable pointe vers l'objet entier, ne peut pas pointer vers un membre de l'objet et ne prend pas en charge les opérations arithmétiques sur les pointeurs. Utilisez l'opérateur d'indirection (`*`) pour accéder à l'objet et l'opérateur d'accès aux membres flèche (`->`) pour accéder à un membre de l'objet.

## <a name="windows-runtime"></a>Windows Runtime

Le compilateur utilise le mécanisme de *décompte de références* COM pour déterminer si l’objet n’est plus utilisé et peut être supprimé. Ceci est possible car un objet dérivé d'une interface Windows Runtime est en fait un objet COM. Le nombre de références est incrémenté lorsque l'objet est créé ou copié et il est décrémenté lorsque l'objet prend la valeur null ou bascule hors de portée. Si le nombre de références atteint zéro, l'objet est supprimé automatiquement et immédiatement.

L'avantage du déclarateur de handle est que dans COM vous devez gérer explicitement le nombre de références pour un objet, ce qui est un processus fastidieux et sujet aux erreurs. Autrement dit, pour incrémenter ou décrémenter le nombre de références, vous devez appeler les méthodes AddRef() et Release() de l’objet. Toutefois, si vous déclarez un objet avec le déclarateur de handle, le compilateur génère du code qui ajuste automatiquement le nombre de références.

Pour plus d’informations sur la façon d’instancier un objet, consultez [ref new](ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Le système utilise le mécanisme de *garbage collector* du CLR pour déterminer si l’objet n’est plus utilisé et peut être supprimé. Le Common Langage Runtime gère un tas sur lequel il alloue des objets et utilise des références managées (variables) dans votre programme pour indiquer l'emplacement des objets sur le tas. Lorsqu'un objet n'est plus utilisé, la mémoire qu'il occupait sur le tas est libérée. Régulièrement, le garbage collector compacte le tas pour mieux utiliser la mémoire libérée. Le compactage du tas peut déplacer des objets sur le tas, ce qui invalide les emplacements référencés par des références managées. Toutefois, le garbage collector connaît l'emplacement de toutes les références managées et il les met automatiquement à jour pour indiquer l'emplacement actuel des objets sur le tas.

Les pointeurs (`*`) et les références (`&`) C++ natifs n'étant pas des références managées, le garbage collector ne peut pas mettre à jour automatiquement les adresses vers lesquelles ils pointent. Pour résoudre ce problème, utilisez le déclarateur de handle pour spécifier une variable que le garbage collector connaît et peut mettre à jour automatiquement.

Pour plus d’informations, voir [Comment : Déclarer les poignées dans les types autochtones](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Exemples

Cet exemple montre comment créer une instance d'un type référence sur le tas managé.  Cet exemple montre également que vous pouvez initialiser un handle avec un autre, générant ainsi deux références au même objet sur le tas managé et récupéré par le garbage collector. Notez que le fait d’assigner [nullptr](nullptr-cpp-component-extensions.md) à un handle ne marque pas l’objet pour le processus de garbage collection.

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

L'exemple suivant montre comment déclarer un handle vers un objet sur le tas managé, où le type d'objet est un type valeur boxed. Il montre également comment obtenir le type valeur à partir de l'objet converti.

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

Cet exemple montre que l’idiome C++ commun consistant à utiliser un pointeur de type `void*` pour pointer vers un objet arbitraire est remplacé par `Object^`, qui peut contenir un handle vers toute classe de référence. Il montre également que tous les types, tels que les tableaux et les délégués, peuvent être convertis en handle d'objet.

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

Cet échantillon montre qu’une référence indigène (`&`) ne peut pas se lier à un membre **int** d’un type géré, car **l’int** pourrait être stocké dans le tas d’ordures collectés, et les références indigènes ne suivent pas le mouvement de l’objet dans le tas géré. La solution consiste à utiliser une variable locale ou à remplacer `&` par `%` afin d'en faire une référence de suivi.

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

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Opérateur de référence de suivi](tracking-reference-operator-cpp-component-extensions.md)
