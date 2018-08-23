---
title: Classes génériques (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76dc54662fac3dc769e0bbf72c672908196ef351
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598245"
---
# <a name="generic-classes-ccli"></a>Classes génériques (C++/CLI)

Une classe générique est déclarée à l’aide de la forme suivante :

## <a name="syntax"></a>Syntaxe

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>Notes

Dans la syntaxe ci-dessus, les termes suivants sont utilisés :

*attributs* (facultatif)  
Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et classes d’attributs, consultez attributs.

*clé de classe*  
Soit **classe** ou **typename**

*type-paramètre-identificateur (s)*, séparées par des virgules de liste d’identificateurs en spécifiant les noms des paramètres de type.

*clauses de contrainte*  
Une liste (ne pas séparées par des virgules) de **où** clauses spécifiant les contraintes pour les paramètres de type. Prend la forme :

`where`  *identificateur de paramètre de type*`:`*liste de contraintes*  `...`

*liste de contraintes*  
*classe ou interface*[`,` *...* ]

*modificateurs d’accessibilité*  
Modificateurs d’accessibilité pour la classe générique. Pour l’exécution de Windows, le seul modificateur autorisé est **privé**. Pour le common language runtime, les modificateurs autorisés sont **privé** et **public**.

*identifier*  
Le nom de la classe générique, n’importe quel identificateur C++ valide.

*modificateurs* (facultatif)  
Autorisées incluent des modificateurs **sealed** et **abstraite**.

*liste de base*  
Une liste qui contient la classe de base et les interfaces implémentées, toutes séparées par des virgules.

*corps de la classe*  
Le corps de la classe contenant des champs, fonctions membres, etc.

*déclarateurs*  
Déclarations de toutes les variables de ce type. Par exemple : `^` *identificateur*[`,` ...]

Vous pouvez déclarer des classes génériques telles que celles-ci (Notez que le mot clé **classe** peut être utilisé au lieu de **typename**). Dans cet exemple, `ItemType`, `KeyType` et `ValueType` sont des types inconnus qui sont spécifiées au point où le type. `HashTable<int, int>` est un type du type générique construit `HashTable<KeyType, ValueType>`. Un nombre de différents types construits peut être construit à partir d’un type générique unique. Types construits construits à partir de classes génériques sont traités comme tout autre type de classe ref.

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

Les deux types de valeur (soit intégré types tels que **int** ou **double**, ou les types valeur définis par l’utilisateur) et les types de référence peuvent être utilisés en tant qu’argument de type générique. La syntaxe dans la définition générique est le même quel que soit. Point de vue syntaxique, le type inconnu est traité comme s’il s’agissait d’un type référence. Toutefois, le runtime est en mesure de déterminer que si le type réellement utilisé est un type valeur et remplacez le code généré approprié pour un accès direct aux membres. Types valeur utilisés en tant qu’arguments de type générique ne sont pas converti (boxed) et par conséquent, ne sont pas confrontées la baisse des performances associée à une conversion boxing. La syntaxe utilisée dans le corps du générique doit être `T^` et `->` au lieu de `.`. Toute utilisation de [gcnew nouvelle, ref](../windows/ref-new-gcnew-cpp-component-extensions.md) pour le type de paramètre sera correctement interprété par le runtime en tant que la simple création d’un type valeur si l’argument de type est un type valeur.

Vous pouvez également déclarer une classe générique avec [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md) sur les types qui peuvent être utilisées pour le paramètre de type. Dans l’exemple suivant, un type utilisé pour `ItemType` doit implémenter le `IItem` interface. Toute tentative d’utilisation **int**, par exemple, ce qui n’implémente pas `IItem`, produirait une erreur de compilation, car l’argument de type ne satisfait pas la contrainte.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Les classes génériques dans le même espace de noms ne peut pas être surchargés en modifiant uniquement le nombre ou les types de paramètres de type. Toutefois, si chaque classe se trouve dans un espace de noms différents, ils peuvent être surchargés. Par exemple, considérez les deux classes suivantes, `MyClass` et `MyClass<ItemType>`, dans les espaces de noms `A` et `B`. Les deux classes peuvent ensuite être surchargés dans un espace de noms troisième C:

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

La classe de base et interfaces de base ne peut pas être des paramètres de type. Toutefois, la classe de base peut impliquer le paramètre de type en tant qu’argument, comme dans le cas suivant :

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Constructeurs et destructeurs sont exécutées une fois pour chaque instance d’objet (comme d’habitude) ; les constructeurs statiques sont exécutées une fois pour chaque type construit.

## <a name="fields-in-generic-classes"></a>Champs dans les Classes génériques

Cette section illustre l’utilisation de l’instance et des champs statiques dans les classes génériques.

### <a name="instance-variables"></a>Variables d’instance

Variables d’instance d’une classe générique peuvent avoir des types et les initialiseurs de variable qui incluent des paramètres de type à partir de la classe englobante.

## <a name="example"></a>Exemple

Dans l’exemple suivant, trois différentes instances de la classe générique, MyClass\<ItemType >, sont créés en utilisant les arguments de type approprié (**int**, **double**et **chaîne**).

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>Variables statiques

Sur la création d’un nouveau type générique, nouvelles instances de toutes les variables statiques sont créées et un constructeur statique pour ce type est exécuté.

Les variables statiques peuvent utiliser des paramètres de type à partir de la classe englobante.

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de champs statiques et un constructeur statique dans une classe générique.

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>Méthodes dans les Classes génériques

Méthodes dans les classes génériques peuvent être génériques eux-mêmes ; les méthodes non génériques seront implicitement paramétrées par le paramètre de type classe.

Les règles suivantes s’appliquent aux méthodes dans les classes génériques :

- Méthodes dans les classes génériques peuvent utiliser des paramètres de type en tant que paramètres, des types de retour ou des variables locales.

- Méthodes dans les classes génériques peuvent utiliser des types construits ouverts ou fermés en tant que paramètres, des types de retour ou des variables locales.

### <a name="non-generic-methods-in-generic-classes"></a>Méthodes non génériques dans les Classes génériques

Méthodes dans les classes génériques qui n’ont aucun paramètre de type supplémentaires sont généralement appelées non générique même si elles sont implicitement paramétrées par la classe générique englobante.

La signature d’une méthode non générique peut inclure un ou plusieurs paramètres de type de la classe englobante, directement ou dans un type construit ouvert. Exemple :

`void MyMethod(MyClass<ItemType> x) {}`

Le corps de ces méthodes peuvent également utiliser ces paramètres de type.

## <a name="example"></a>Exemple

L’exemple suivant déclare une méthode non générique, `ProtectData`, à l’intérieur d’une classe générique, `MyClass<ItemType>`. La méthode utilise le paramètre de type classe `ItemType` dans sa signature dans un type construit ouvert.

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**  
```

## <a name="generic-methods-in-generic-classes"></a>Méthodes génériques dans les Classes génériques

Vous pouvez déclarer des méthodes génériques dans les classes génériques et non génériques. Exemple :

## <a name="example"></a>Exemple

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

La méthode non générique est toujours générique en ce sens qu’il est paramétré par le paramètre de type de la classe, mais il n’a aucun paramètre de type supplémentaire.

Tous les types de méthodes dans les classes génériques peuvent être générique, y compris statique, instance et méthodes virtuelles.

## <a name="example"></a>Exemple

L’exemple suivant illustre la déclaration et utilisation des méthodes génériques dans les classes génériques :

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>À l’aide des Types imbriqués dans les Classes génériques

Tout comme avec les classes ordinaires, vous pouvez déclarer des autres types à l’intérieur d’une classe générique. La déclaration de classe imbriquée est implicitement paramétrée par les paramètres de type de la déclaration de classe externe. Par conséquent, une classe imbriquée distincte est définie pour chaque type externe construit. Par exemple, dans la déclaration,

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

Le type `Outer<int>::Inner` n’est pas identique au type `Outer<double>::Inner`.

Comme avec les méthodes génériques dans les classes génériques, les paramètres de type supplémentaires peuvent être définis pour le type imbriqué. Si vous utilisez les mêmes noms de paramètre de type dans la classe interne et externe, le paramètre de type interne masque le paramètre de type externe.

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

Dans la mesure où il n’existe aucun moyen pour faire référence au paramètre de type externe, le compilateur génère un avertissement dans ce cas.

Quand des types génériques construits imbriqués sont nommées, le paramètre de type pour le type externe n’est pas inclus dans la liste de paramètres de type pour le type interne, même si le type interne est implicitement paramétré par paramètre de type du type externe. Dans le cas ci-dessus, un nom d’un type construit serait `Outer<int>::Inner<string>`.

L’exemple suivant illustre la création et la lecture d’une liste liée à l’aide des types imbriqués dans les classes génériques.

## <a name="example"></a>Exemple

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Propriétés, des événements, des indexeurs et des opérateurs dans les Classes génériques

- Propriétés, événements, indexeurs et les opérateurs peuvent utiliser les paramètres de type de la classe générique englobante en tant que valeurs de retour, paramètres ou variables locales, par exemple quand `ItemType` est un paramètre de type d’une classe :

    ```cpp
    public ItemType MyProperty {}
    ```

- Propriétés, événements, indexeurs et les opérateurs ne peuvent pas eux-mêmes être paramétrables.

## <a name="example"></a>Exemple

Cet exemple montre des déclarations de propriété d’instance dans une classe générique.

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example"></a>Exemple

L’exemple suivant montre une classe générique avec un événement.

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>Structs génériques

Les règles de déclaration et d’utilisation de structs génériques sont les mêmes que celles pour les classes génériques, à part les différences indiqués dans la référence du langage Visual C++.

## <a name="example"></a>Exemple

L’exemple suivant déclare une structure générique, `MyGenStruct`, avec un champ, `myField`et assigne des valeurs de types différents (**int**, **double**, `String^`) à ce champ.

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>Voir aussi

[Génériques](../windows/generics-cpp-component-extensions.md)