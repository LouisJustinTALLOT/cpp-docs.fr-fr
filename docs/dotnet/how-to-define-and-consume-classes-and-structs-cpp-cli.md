---
title: 'Comment : définir et consommer des classes et des structs (C++/CLI)'
description: Comment créer et utiliser des classes définies par l’utilisateur et des types struct dans du code C++/CLI.
ms.date: 09/25/2020
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 17d0885d42febc1d2789c8711b54a76066ee8176
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414579"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Comment : définir et consommer des classes et des structs (C++/CLI)

Cet article explique comment définir et utiliser des types référence et des types valeur définis par l’utilisateur dans C++/CLI.

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a> Instanciation d’objets

Les types référence (Ref) peuvent uniquement être instanciés sur le tas managé, pas sur la pile ou sur le tas natif. Les types valeur peuvent être instanciés sur la pile ou le tas managé.

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> Classes implicitement abstraites

Une *classe implicitement abstraite* ne peut pas être instanciée. Une classe est implicitement abstraite dans les cas suivants :

- le type de base de la classe est une interface, et
- la classe n’implémente pas toutes les fonctions membres de l’interface.

Il se peut que vous ne puissiez pas construire d’objets à partir d’une classe dérivée d’une interface. Cela peut être dû au fait que la classe est implicitement abstraite. Pour plus d’informations sur les classes abstraites, consultez [abstract](../extensions/abstract-cpp-component-extensions.md).

L’exemple de code suivant montre que la `MyClass` classe ne peut pas être instanciée, car la fonction `MyClass::func2` n’est pas implémentée. Pour permettre à l’exemple de compiler, supprimez les marques de commentaire `MyClass::func2` .

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a> Visibilité du type

Vous pouvez contrôler la visibilité des types de common language runtime (CLR). Lorsque votre assembly est référencé, vous contrôlez si les types dans l’assembly sont visibles ou non visibles à l’extérieur de l’assembly.

`public` indique qu’un type est visible pour tout fichier source qui contient une `#using` directive pour l’assembly qui contient le type.  `private` indique qu’un type n’est pas visible dans les fichiers sources qui contiennent une `#using` directive pour l’assembly qui contient le type. Toutefois, les types privés sont visibles dans le même assembly. Par défaut, la visibilité d’une classe est `private` .

Par défaut avant Visual Studio 2005, les types natifs avaient une accessibilité publique en dehors de l’assembly. Activez l' [Avertissement du compilateur (niveau 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) pour vous aider à voir où les types natifs privés sont utilisés de manière incorrecte. Utilisez le pragma [make_public](../preprocessor/make-public.md) pour fournir une accessibilité publique à un type natif dans un fichier de code source que vous ne pouvez pas modifier.

Pour plus d’informations, consultez [#using, directive](../preprocessor/hash-using-directive-cpp.md).

L’exemple suivant montre comment déclarer des types et spécifier leur accessibilité, puis comment accéder à ces types à l’intérieur de l’assembly. Si un assembly qui a des types privés est référencé à l’aide de `#using` , seuls les types publics de l’assembly sont visibles.

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**Sortie**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

Nous allons maintenant réécrire l’exemple précédent pour qu’il soit généré en tant que DLL.

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

L’exemple suivant montre comment accéder aux types en dehors de l’assembly. Dans cet exemple, le client consomme le composant qui est généré dans l’exemple précédent.

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**Sortie**

```Output
in Public_Class
```

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a> Visibilité des membres

Vous pouvez rendre l’accès à un membre d’une classe publique à partir du même assembly que l’accès à celui-ci à partir de l’extérieur de l’assembly à l’aide de paires de spécificateurs d’accès **`public`** , **`protected`** et **`private`**

Ce tableau résume l’effet des différents spécificateurs d’accès :

|Spécificateur|Résultat|
|---------------|------------|
|`public`|Le membre est accessible à l’intérieur et à l’extérieur de l’assembly. Pour plus d’informations, consultez [`public`](../cpp/public-cpp.md).|
|`private`|Le membre est inaccessible, à l’intérieur et à l’extérieur de l’assembly.  Pour plus d’informations, consultez [`private`](../cpp/private-cpp.md).|
|`protected`|Le membre est accessible à l’intérieur et à l’extérieur de l’assembly, mais uniquement aux types dérivés. Pour plus d’informations, consultez [`protected`](../cpp/protected-cpp.md).|
|`internal`|Le membre est public à l’intérieur de l’assembly mais est privé en dehors de l’assembly. `internal` est un mot clé contextuel.  Pour plus d’informations, consultez [Mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|`public protected` ou `protected public`|Le membre est public à l’intérieur de l’assembly, mais protégé à l’extérieur de l’assembly.|
|`private protected` ou `protected private`|Le membre est protégé à l’intérieur de l’assembly mais privé à l’extérieur de l’assembly.|

L’exemple suivant montre un type public qui a des membres déclarés à l’aide des spécificateurs d’accès différents. Il affiche ensuite l’accès à ces membres à partir de l’assembly.

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**Sortie**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

Créons maintenant l’exemple précédent sous la forme d’une DLL.

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

L’exemple suivant utilise le composant qui est créé dans l’exemple précédent. Il montre comment accéder aux membres à partir de l’extérieur de l’assembly.

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**Sortie**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> Classes natives publiques et privées

Un type natif peut être référencé à partir d’un type managé.  Par exemple, une fonction dans un type managé peut accepter un paramètre dont le type est un struct natif.  Si le type et la fonction managés sont publics dans un assembly, le type natif doit également être public.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Ensuite, créez le fichier de code source qui utilise le type natif :

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

À présent, compilez un client :

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> Constructeurs statiques

Un type CLR (par exemple, une classe ou un struct) peut avoir un constructeur statique qui peut être utilisé pour initialiser des données membres statiques.  Un constructeur statique est appelé au plus une fois, et est appelé avant qu’un membre statique du type ne soit accédé la première fois.

Un constructeur d’instance s’exécute toujours après un constructeur statique.

Le compilateur ne peut pas incorporer un appel à un constructeur si la classe a un constructeur statique. Le compilateur ne peut pas incorporer un appel à une fonction membre si la classe est un type valeur, a un constructeur statique et n’a pas de constructeur d’instance. Le CLR peut incorporer l’appel, mais le compilateur ne peut pas le faire.

Définissez un constructeur statique comme une fonction membre privée, car il est destiné à être appelé uniquement par le CLR.

Pour plus d’informations sur les constructeurs statiques, consultez [Comment : définir un constructeur d’interface statique (C++/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**Sortie**

```Output
in static constructor
10
11
```

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a> Sémantique du `this` pointeur

Quand vous utilisez C++ \CLI pour définir des types, le **`this`** pointeur dans un type référence est de type *handle*. Le **`this`** pointeur dans un type valeur est de type *pointeur intérieur*.

Ces différentes sémantiques du **`this`** pointeur peuvent entraîner un comportement inattendu lorsqu’un indexeur par défaut est appelé. L’exemple suivant illustre la méthode correcte pour accéder à un indexeur par défaut dans un type REF et un type valeur.

Pour plus d’informations, consultez [handle to Object, opérateur (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) et [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**Sortie**

```Output
10.89
10.89
```

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> Fonctions de masquage par signature

Dans le langage C++ standard, une fonction d’une classe de base est masquée par une fonction qui a le même nom dans une classe dérivée, même si la fonction de la classe dérivée n’a pas le même type ou le même nombre de paramètres. Il s’agit d’une sémantique de *masquage par nom* . Dans un type référence, une fonction d’une classe de base est masquée uniquement par une fonction dans une classe dérivée si le nom et la liste des paramètres sont identiques. C’est ce qu’on appelle la sémantique de *masquage par signature* .

Une classe est considérée comme une classe masquer par signature lorsque toutes ses fonctions sont marquées dans les métadonnées sous la forme `hidebysig` . Par défaut, toutes les classes créées sous **`/clr`** ont des `hidebysig` fonctions. Quand une classe a `hidebysig` des fonctions, le compilateur ne masque pas les fonctions par nom dans les classes de base directes, mais si le compilateur rencontre une classe Hide-by-Name dans une chaîne d’héritage, il continue ce comportement de masquage par nom.

Sous la sémantique de masquage par signature, lorsqu’une fonction est appelée sur un objet, le compilateur identifie la classe la plus dérivée qui contient une fonction qui peut satisfaire l’appel de fonction. S’il n’existe qu’une seule fonction dans la classe qui satisfait l’appel, le compilateur appelle cette fonction. Si plusieurs fonctions de la classe peuvent satisfaire l’appel, le compilateur utilise les règles de résolution de surcharge pour déterminer la fonction à appeler. Pour plus d’informations sur les règles de surcharge, consultez surcharge de [fonction](../cpp/function-overloading.md).

Pour un appel de fonction donné, une fonction d’une classe de base peut avoir une signature qui en fait une correspondance légèrement meilleure qu’une fonction dans une classe dérivée. Toutefois, si la fonction a été appelée explicitement sur un objet de la classe dérivée, la fonction dans la classe dérivée est appelée.

Étant donné que la valeur de retour n’est pas considérée comme faisant partie de la signature d’une fonction, une fonction de classe de base est masquée si elle porte le même nom et accepte le même type et le même nombre d’arguments qu’une fonction de classe dérivée, même si elle diffère dans le type de la valeur de retour.

L’exemple suivant montre qu’une fonction d’une classe de base n’est pas masquée par une fonction dans une classe dérivée.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**Sortie**

```Output
Base::Test
```

L’exemple suivant montre que le compilateur Microsoft C++ appelle une fonction dans la classe la plus dérivée, même si une conversion est requise pour mettre en correspondance un ou plusieurs des paramètres, et n’appelle pas une fonction dans une classe de base qui est une meilleure correspondance pour l’appel de fonction.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**Sortie**

```Output
Derived::Test2
```

L’exemple suivant montre qu’il est possible de masquer une fonction même si la classe de base a la même signature que la classe dérivée.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**Sortie**

```Output
Derived::Test4
97
```

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a> Constructeurs de copie

La norme C++ indique qu’un constructeur de copie est appelé lorsqu’un objet est déplacé, de telle sorte qu’un objet est créé et détruit à la même adresse.

Toutefois, lorsqu’une fonction compilée en langage MSIL appelle une fonction native où une classe native (ou plusieurs) est passée par valeur et où la classe native a un constructeur de copie ou un destructeur, aucun constructeur de copie n’est appelé et l’objet est détruit à une adresse différente de celle où il a été créé. Ce comportement peut provoquer des problèmes si la classe a un pointeur vers lui-même, ou si le code effectue le suivi des objets par adresse.

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant montre qu’un constructeur de copie n’est pas généré.

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**Sortie**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> Destructeurs et finaliseurs

Les destructeurs dans un type référence effectuent un nettoyage déterministe des ressources. Les finaliseurs nettoient les ressources non managées et peuvent être appelées de manière déterministe par le destructeur ou non déterministe par le garbage collector. Pour plus d’informations sur les destructeurs en C++ standard, consultez [destructeurs](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Le garbage collector CLR supprime les objets managés inutilisés et libère leur mémoire lorsqu’ils ne sont plus nécessaires. Toutefois, un type peut utiliser des ressources que le garbage collector ne sait pas comment libérer. Ces ressources sont appelées ressources *non managées* (Handles de fichiers natifs, par exemple). Nous vous recommandons de libérer toutes les ressources non managées dans le finaliseur. Le garbage collector libère les ressources managées de façon non déterministe. il n’est donc pas possible de faire référence aux ressources managées dans un finaliseur. C’est parce qu’il est possible que le garbage collector les ait déjà nettoyés.

Un finaliseur Visual C++ n’est pas le même que la <xref:System.Object.Finalize%2A> méthode. (La documentation CLR utilise finaliseur et la <xref:System.Object.Finalize%2A> méthode synonymes). La <xref:System.Object.Finalize%2A> méthode est appelée par le garbage collector, qui appelle chaque finaliseur dans une chaîne d’héritage de classe. Contrairement aux destructeurs Visual C++, un appel de finaliseur de classe dérivée ne fait pas en sorte que le compilateur appelle le finaliseur dans toutes les classes de base.

Étant donné que le compilateur Microsoft C++ prend en charge la version déterministe des ressources, n’essayez pas d’implémenter les <xref:System.IDisposable.Dispose%2A> <xref:System.Object.Finalize%2A> méthodes ou. Toutefois, si vous êtes familiarisé avec ces méthodes, voici comment un finaliseur Visual C++ et un destructeur qui appelle le finaliseur mappent au <xref:System.IDisposable.Dispose%2A> modèle :

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

Un type managé peut également utiliser des ressources managées que vous préférez pouvoir libérer de manière déterministe. Vous ne souhaiterez peut-être pas que le garbage collector libère un objet de manière non déterministe à un moment donné après que l’objet n’est plus nécessaire. La version déterministe des ressources peut améliorer considérablement les performances.

Le compilateur Microsoft C++ permet à la définition d’un destructeur de nettoyer les objets de manière déterministe. Utilisez le destructeur pour libérer toutes les ressources que vous souhaitez libérer de manière déterministe.  Si un finaliseur est présent, appelez-le à partir du destructeur pour éviter la duplication de code.

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

Si le code qui utilise votre type n’appelle pas le destructeur, le garbage collector libère finalement toutes les ressources managées.

La présence d’un destructeur n’implique pas la présence d’un finaliseur. Toutefois, la présence d’un finaliseur implique que vous devez définir un destructeur et appeler le finaliseur à partir de ce destructeur. Cet appel fournit la version déterministe des ressources non managées.

L’appel du destructeur supprime (à l’aide <xref:System.GC.SuppressFinalize%2A> de) la finalisation de l’objet. Si le destructeur n’est pas appelé, le finaliseur de votre type finira par être appelé par le garbage collector.

Vous pouvez améliorer les performances en appelant le destructeur pour nettoyer de manière déterministe les ressources de votre objet, au lieu de laisser le CLR finaliser de manière non déterminante l’objet.

Le code écrit en Visual C++ et compilé à l’aide de **`/clr`** exécute le destructeur d’un type si :

- Un objet créé à l’aide de la sémantique de pile est hors de portée. Pour plus d’informations, consultez [sémantique de pile C++ pour les types référence](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Une exception est levée lors de la construction de l’objet.

- L’objet est un membre d’un objet dont le destructeur est en cours d’exécution.

- Vous appelez l’opérateur [Delete](../cpp/delete-operator-cpp.md) sur un descripteur ([handle vers l’opérateur Object (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Vous appelez explicitement le destructeur.

Si un client écrit dans un autre langage utilise votre type, le destructeur est appelé comme suit :

- Sur un appel à <xref:System.IDisposable.Dispose%2A> .

- Sur un appel à `Dispose(void)` sur le type.

- Si le type est hors de portée dans une **`using`** instruction C#.

Si vous n’utilisez pas la sémantique de pile pour les types référence et créez un objet d’un type référence sur le tas managé, utilisez la syntaxe [try-finally](../cpp/try-finally-statement.md) pour vous assurer qu’une exception n’empêche pas l’exécution du destructeur.

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

Si votre type a un destructeur, le compilateur génère une `Dispose` méthode qui implémente <xref:System.IDisposable> . Si un type écrit en Visual C++ et a un destructeur qui est consommé à partir d’un autre langage, `IDisposable::Dispose` l’appel de sur ce type entraîne l’appel du destructeur du type. Quand le type est consommé à partir d’un client Visual C++, vous ne pouvez pas appeler directement `Dispose` ; à la place, appelez le destructeur à l’aide de l' **`delete`** opérateur.

Si votre type a un finaliseur, le compilateur génère une `Finalize(void)` méthode qui remplace <xref:System.Object.Finalize%2A> .

Si un type a un finaliseur ou un destructeur, le compilateur génère une `Dispose(bool)` méthode, selon le modèle de conception. (Pour plus d’informations, consultez [modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)). Vous ne pouvez pas créer ou appeler explicitement `Dispose(bool)` dans Visual C++.

Si un type a une classe de base conforme au modèle de conception, les destructeurs pour toutes les classes de base sont appelés lorsque le destructeur de la classe dérivée est appelé. (Si votre type est écrit en Visual C++, le compilateur s’assure que vos types implémentent ce modèle.) En d’autres termes, le destructeur d’une classe de référence est lié à ses bases et à ses membres, comme spécifié par la norme C++. Tout d’abord, le destructeur de la classe est exécuté. Ensuite, les destructeurs de ses membres sont exécutés dans l’ordre inverse de l’ordre dans lequel ils ont été construits. Enfin, les destructeurs de ses classes de base sont exécutés à l’inverse de l’ordre dans lequel ils ont été construits.

Les destructeurs et les finaliseurs ne sont pas autorisés dans les types valeur ou les interfaces.

Un finaliseur peut uniquement être défini ou déclaré dans un type référence. À l’instar d’un constructeur et d’un destructeur, un finaliseur n’a aucun type de retour.

Après l’exécution du finaliseur d’un objet, les finaliseurs dans toutes les classes de base sont également appelées, en commençant par le type le moins dérivé. Les finaliseurs pour les membres de données ne sont pas automatiquement chaînés par le finaliseur d’une classe.

Si un finaliseur supprime un pointeur natif dans un type managé, vous devez vous assurer que les références vers ou via le pointeur natif ne sont pas collectées prématurément. Appelez le destructeur sur le type managé au lieu d’utiliser <xref:System.GC.KeepAlive%2A> .

Au moment de la compilation, vous pouvez détecter si un type a un finaliseur ou un destructeur. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

L’exemple suivant montre deux types : un qui a des ressources non managées et un qui contient des ressources managées qui sont publiées de façon déterministe.

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)
