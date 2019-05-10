---
title: 'Procédure : Définir et consommer des Classes et Structs (C++ / c++ / CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447298"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Procédure : Définir et consommer des Classes et Structs (C++ / c++ / CLI)

Cet article explique comment définir et consommer des types référence définis par l’utilisateur et les types de valeur en C / c++ / CLI.

##  <a name="BKMK_Contents"></a> Sommaire

[Instanciation d’objet](#BKMK_Object_instantiation)

[Classes implicitement abstraites](#BKMK_Implicitly_abstract_classes)

[Visibilité du type](#BKMK_Type_visibility)

[Visibilité des membres](#BKMK_Member_visibility)

[Classes natives publiques et privées](#BKMK_Public_and_private_native_classes)

[Constructeurs statiques](#BKMK_Static_constructors)

[Sémantiques de ce pointeur](#BKMK_Semantics_of_the_this_pointer)

[Fonctions Hide-by-signature](#BKMK_Hide_by_signature_functions)

[Constructeurs de copie](#BKMK_Copy_constructors)

[Destructeurs et finaliseurs](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a> Instanciation d’objet

Types référence (ref) peuvent uniquement être instanciés sur le tas managé, pas sur la pile ou sur le tas natif. Types valeur peuvent être instanciés sur la pile ou le tas managé.

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

##  <a name="BKMK_Implicitly_abstract_classes"></a> Classes implicitement abstraites

Un *implicitement abstraites classe* ne peut pas être instanciée. Une classe est abstraite implicitement si le type de base de la classe est une interface et la classe n’implémente pas toutes les fonctions membres de l’interface.

Si vous ne parvenez pas à construire des objets à partir d’une classe qui est dérivée d’une interface, la raison peut être que la classe est abstraite implicitement. Pour plus d’informations sur les classes abstraites, consultez [abstraite](../extensions/abstract-cpp-component-extensions.md).

L’exemple de code suivant montre que le `MyClass` classe ne peut pas être instanciée, car fonction `MyClass::func2` n’est pas implémentée. Pour activer l’exemple compiler, supprimez les commentaires de `MyClass::func2`.

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

##  <a name="BKMK_Type_visibility"></a> Visibilité du type

Vous pouvez contrôler la visibilité des types common language runtime (CLR) de sorte que, si un assembly est référencé, les types dans l’assembly peuvent être visible ou non visible en dehors de l’assembly.

`public` Indique qu’un type est visible dans tout fichier source qui contienne un `#using` directive pour l’assembly qui contient le type.  `private` Indique qu’un type n’est pas visible aux fichiers sources qui contiennent un `#using` directive pour l’assembly qui contient le type. Toutefois, les types privés sont visibles dans le même assembly. Par défaut, la visibilité d’une classe est `private`.

Par défaut avant Visual Studio 2005, les types natifs avaient une accessibilité publique en dehors de l’assembly. Activer [Avertissement du compilateur (niveau 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) pour vous aider à voir où les types natifs privés sont utilisés correctement. Utilisez le [make_public](../preprocessor/make-public.md) pragma pour donner une accessibilité publique à un type natif dans un fichier de code source que vous ne pouvez pas modifier.

Pour plus d’informations, consultez [#using, directive](../preprocessor/hash-using-directive-cpp.md).

L’exemple suivant montre comment déclarer des types et spécifier leur accessibilité et ensuite accéder à ces types à l’intérieur de l’assembly. Bien entendu, si un assembly qui a des types privés est référencé à l’aide de `#using`, seuls les types publics dans l’assembly sont visibles.

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

Maintenant, nous allons réécrire l’exemple précédent afin qu’il est généré sous la forme d’une DLL.

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

L’exemple suivant montre comment accéder aux types en dehors de l’assembly. Dans cet exemple, le client utilise le composant qui est généré dans l’exemple précédent.

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

##  <a name="BKMK_Member_visibility"></a> Visibilité des membres

Vous pouvez vous l’accès à un membre d’une classe publique à partir du même assembly autre que l’accès à partir en dehors de l’assembly à l’aide de paires de spécificateurs d’accès `public`, `protected`, et `private`

Ce tableau récapitule l’effet des spécificateurs d’accès différents :

|Spécificateur|Effet|
|---------------|------------|
|public|Membre est accessible à l’intérieur et en dehors de l’assembly.  Consultez [public](../cpp/public-cpp.md) pour plus d’informations.|
|private|Membre n’est pas accessible, ni à l’intérieur, ni en dehors de l’assembly.  Consultez [privé](../cpp/private-cpp.md) pour plus d’informations.|
|protected|Membre est accessible à l’intérieur et en dehors de l’assembly, mais uniquement pour les types dérivés.  Consultez [protégé](../cpp/protected-cpp.md) pour plus d’informations.|
|internal|Membre est public à l’intérieur de l’assembly mais privé en dehors de l’assembly.  `internal` est un mot clé contextuel.  Pour plus d’informations, consultez [mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|public public protégé - ou - protégé|Membre est public à l’intérieur de l’assembly mais protégés en dehors de l’assembly.|
|privé privé protégé - ou - protégé|Membre est protégé à l’intérieur de l’assembly mais privé en dehors de l’assembly.|

L’exemple suivant illustre un type public qui a des membres qui sont déclarés avec les accessibilités différents et montre ensuite l’accès à ces membres d’à l’intérieur de l’assembly.

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

Maintenant nous allons générer l’exemple précédent en tant que DLL.

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

L’exemple suivant utilise le composant qui est créé dans l’exemple précédent et ce qui montre comment accéder aux membres à partir de l’extérieur de l’assembly.

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

##  <a name="BKMK_Public_and_private_native_classes"></a> Classes natives publiques et privées

Un type natif peut être référencé à partir d’un type managé.  Par exemple, une fonction dans un type managé peut prendre un paramètre dont le type est un struct natif.  Si le type managé et la fonction sont publiques dans un assembly, puis le type natif doit également être public.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Ensuite, créez le fichier de code source qui consomme le type natif :

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

##  <a name="BKMK_Static_constructors"></a> Constructeurs statiques

Un type CLR — par exemple, une classe ou un struct, peut avoir un constructeur statique qui peut être utilisé pour initialiser les données membres statiques.  Un constructeur statique est appelé une fois au maximum et est appelé avant la première fois d’accéder à n’importe quel membre statique du type.

Un constructeur d’instance s’exécute toujours après un constructeur statique.

Le compilateur ne peut pas incorporer un appel à un constructeur si la classe a un constructeur statique.  Le compilateur ne peut pas incorporer un appel à n’importe quelle fonction membre si la classe est un type valeur, possède un constructeur statique et n’a pas de constructeur d’instance.  Le CLR peut inline l’appel, mais le compilateur ne peut pas.

Définir un constructeur statique comme une fonction membre privé, car elle est destinée à être appelée uniquement par le CLR.

Pour plus d’informations sur les constructeurs statiques, consultez [Comment : Définir un constructeur d’Interface statique (C++ / c++ / CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

##  <a name="BKMK_Semantics_of_the_this_pointer"></a> Sémantiques de ce pointeur

Lorsque vous utilisez Visual C++ pour définir des types, le `this` pointeur dans un type référence est de type « handle ». Le `this` pointeur dans un type valeur est de type « pointeur intérieur ».

Ce une sémantique différente de la `this` pointeur peut provoquer un comportement inattendu lorsqu’un indexeur par défaut est appelé. L’exemple suivant montre la méthode correcte pour accéder à un indexeur par défaut dans un type ref et un type valeur.

Pour plus d'informations, consultez

- [Handle sur l'opérateur Object (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++-CLI)](../extensions/interior-ptr-cpp-cli.md)

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

##  <a name="BKMK_Hide_by_signature_functions"></a> Fonctions Hide-by-signature

En C++ standard, une fonction dans une classe de base est masquée par une fonction qui a le même nom dans une classe dérivée, même si la fonction de la classe dérivée n’a pas le même nombre ou le genre de paramètres. Cela est appelé *masquer par nom* sémantique. Dans un type référence, une fonction dans une classe de base peut uniquement être masquée par une fonction dans une classe dérivée si le nom et la liste de paramètres sont identiques. Il s’agit *hide-by-signature* sémantique.

Une classe est considérée comme une classe hide-by-signature lorsque toutes ses fonctions sont marquées dans les métadonnées en tant que `hidebysig`. Par défaut, toutes les classes qui sont créées sous **/CLR** ont `hidebysig` fonctions. Quand une classe a `hidebysig` fonctions, le compilateur ne masque pas les fonctions par nom dans les classes de base directes, mais si le compilateur rencontre une classe de masquage par nom dans une chaîne d’héritage, elle continue de ce comportement de masquage par nom.

La sémantique hide-by-signature, lorsqu’une fonction est appelée sur un objet, le compilateur identifie la classe la plus dérivée qui contient une fonction qui peut satisfaire à l’appel de fonction. S’il existe une seule fonction de la classe qui peut répondre à l’appel, le compilateur appelle cette fonction. S’il existe plusieurs fonctions dans la classe qui peut répondre à l’appel, le compilateur utilise surcharge les règles de résolution pour déterminer quelle fonction appeler. Pour plus d’informations sur les règles de surcharge, consultez [surcharge de fonction](../cpp/function-overloading.md).

Pour un appel de fonction donné, une fonction dans une classe de base peut avoir une signature qui rend légèrement mieux qu’une fonction dans une classe dérivée. Toutefois, si la fonction a été appelée explicitement sur un objet de la classe dérivée, la fonction dans la classe dérivée est appelée.

Étant donné que la valeur de retour n’est pas considéré comme partie de la signature d’une fonction, une fonction de la classe de base est masquée si elle a le même nom et prend le même nombre et type d’arguments comme une fonction de la classe dérivée, même si elle diffère dans le type de la valeur de retour.

L’exemple suivant montre une fonction dans une classe de base n’est pas masquée par une fonction dans une classe dérivée.

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

L’exemple suivant montre que Microsoft C++ compilateur appelle une fonction de la classe la plus dérivée, même si une conversion doit correspondre à un ou plusieurs des paramètres et pas appeler une fonction dans une classe de base qui est une meilleure correspondance pour l’appel de fonction.

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

L’exemple suivant montre qu’il est possible de masquer une fonction, même si la classe de base a la même signature que la classe dérivée.

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

##  <a name="BKMK_Copy_constructors"></a> Constructeurs de copie

La norme C++ indique qu’un constructeur de copie est appelé lorsqu’un objet est déplacé, telles qu’un objet est créé et détruit à la même adresse.

Toutefois, lorsque **/CLR** est utilisé pour la compilation et une fonction qui est compilée en appels MSIL où une classe native de fonction native, ou plusieurs, est passé par valeur et où la classe native a un constructeur de copie et/ou de destructeur, aucune copie constructeur est appelé et l’objet est détruit à une adresse différente de celle où il a été créé. Cela peut entraîner des problèmes si la classe a un pointeur dans lui-même, ou si le code effectue le suivi des objets par adresse.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant montre que lorsqu’un constructeur de copie n’est pas généré.

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

##  <a name="BKMK_Destructors_and_finalizers"></a> Destructeurs et finaliseurs

Les destructeurs dans un type référence effectuent un déterministe nettoyage des ressources. Les finaliseurs nettoyer les ressources non managées et peuvent être appelées de façon déterministe par le destructeur ou de façon non déterministe par le garbage collector. Pour plus d’informations à propos des destructeurs c++ standard, consultez [destructeurs](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Le comportement de destructeurs dans une classe managée de Visual C++ diffère des Extensions managées pour C++. Pour plus d’informations sur cette modification, consultez [modifications de la sémantique du destructeur](../dotnet/changes-in-destructor-semantics.md).

Le garbage collector CLR supprime les objets managés inutilisés et libère leur mémoire lorsqu’ils ne sont plus nécessaires. Toutefois, un type peut utiliser les ressources que le garbage collector ne sait pas comment libérer. Ces ressources sont des ressources non managées (fichier natif prend en charge, par exemple). Nous recommandons que vous libérer toutes les ressources non managées dans le finaliseur. Étant donné que les ressources managées sont libérées de façon non déterministe par le garbage collector, il est déconseillé faire référence à des ressources managées dans un finaliseur, car il est possible que le garbage collector a nettoyé déjà cette ressource managée.

Un finaliseur Visual C++ n’est pas le même que le <xref:System.Object.Finalize%2A> (méthode). (Documentation du CLR utilise le finaliseur et la <xref:System.Object.Finalize%2A> méthode synonymes). Le <xref:System.Object.Finalize%2A> méthode est appelée par le garbage collector, qui appelle chaque finaliseur dans une chaîne d’héritage de classe. Contrairement aux destructeurs Visual C++, un appel de la classe dérivée de finaliseur n’entraîne pas le compilateur appeler le finaliseur dans toutes les classes de base.

Étant donné que Microsoft C++ compilateur prend en charge la mise en production déterministe des ressources, n’essayez pas d’implémenter le <xref:System.IDisposable.Dispose%2A> ou <xref:System.Object.Finalize%2A> méthodes. Toutefois, si vous êtes familiarisé avec ces méthodes, voici comment un finaliseur de Visual C++ et un destructeur qui appelle le finaliseur mappent à la <xref:System.IDisposable.Dispose%2A> modèle :

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

Un type managé peut également utiliser les ressources managées que vous préférez pour libérer de manière déterministe et pas laisser le garbage collector pour libérer de manière non déterministe à un moment donné une fois que l’objet n’est plus nécessaire. La mise en production déterministe des ressources peut améliorer considérablement les performances.

Microsoft C++ compilateur permet la définition d’un destructeur pour nettoyer de façon déterministe les objets. Utilisez le destructeur pour libérer toutes les ressources que vous souhaitez libérer de façon déterministe.  Si un finaliseur est présent, appelez-le à partir du destructeur, pour éviter la duplication de code.

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

La présence d’un destructeur n’implique pas la présence d’un finaliseur. Toutefois, la présence d’un finaliseur implique que vous devez définir un destructeur et appelle le finaliseur à partir de ce destructeur. Ainsi, pour la mise en production déterministe des ressources non managées.

Supprime l’appelant le destructeur, à l’aide de <xref:System.GC.SuppressFinalize%2A>— la finalisation de l’objet. Si le destructeur n’est pas appelé, finaliseur de votre type sera finalement appelé par le garbage collector.

Nettoyage déterministe des ressources de l’objet en appelant le destructeur peut améliorer les performances comparées avec le CLR vous permettant de façon non déterministe finalise l’objet.

Code qui a écrit en Visual C++ et compilé à l’aide de **/CLR** exécute le destructeur d’un type si :

- Un objet qui est créé en utilisant la sémantique de pile est hors de portée. Pour plus d’informations, consultez [sémantique de pile C++ pour les Types référence](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Une exception est levée pendant la construction de l’objet.

- L’objet est un membre d’un objet dont le destructeur est en cours d’exécution.

- Vous appelez le [supprimer](../cpp/delete-operator-cpp.md) opérateur sur un handle ([gérer sur l’opérateur Object (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Vous appelez explicitement le destructeur.

Si votre type est consommé par un client qui est écrit dans une autre langue, le destructeur est appelé comme suit :

- Sur un appel à <xref:System.IDisposable.Dispose%2A>.

- Sur un appel à `Dispose(void)` sur le type.

- Si le type est hors de portée en C# `using` instruction.

Si vous créez un objet d’un type de référence sur le tas managé (ne pas à l’aide de la sémantique de pile pour les types référence), utilisez [try-finally](../cpp/try-finally-statement.md) syntaxe pour vous assurer qu’une exception n’empêche pas le destructeur d’en cours d’exécution.

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

Si votre type a un destructeur, le compilateur génère un `Dispose` méthode qui implémente <xref:System.IDisposable>. Si un type qui est écrit en Visual C++ et a un destructeur est consommé à partir d’une autre langue, l’appel `IDisposable::Dispose` sur ce type provoque le destructeur du type à appeler. Lorsque le type est consommé à partir d’un client de Visual C++, vous ne pouvez pas appeler directement `Dispose`; au lieu de cela, appelez le destructeur en utilisant le `delete` opérateur.

Si votre type a un finaliseur, le compilateur génère un `Finalize(void)` méthode substitue <xref:System.Object.Finalize%2A>.

Si un type a un finaliseur ou un destructeur, le compilateur génère un `Dispose(bool)` (méthode), selon le modèle de conception. (Pour plus d’informations, consultez [modèle Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). Vous ne pouvez pas explicitement créer ou appeler `Dispose(bool)` dans Visual C++.

Si un type a une classe de base qui est conforme au modèle de conception, les destructeurs pour toutes les classes de base sont appelés lorsque le destructeur de la classe dérivée est appelé. (Si votre type est écrit en Visual C++, le compilateur garantit que vos types implémentent ce modèle.) En d’autres termes, le destructeur d’une classe de référence lié à ses bases et des membres comme spécifié par la norme C++ : premier destructeur de la classe est l’exécution, puis les destructeurs pour ses membres dans l’ordre inverse de l’ordre dans lequel elles ont été construites, et enfin le destructeurs pour ses classes de base dans l’ordre inverse de l’ordre dans lequel elles ont été construites.

Destructeurs et finaliseurs ne sont pas autorisées dans les interfaces ou des types de valeur.

Un finaliseur peut uniquement être défini ou déclaré dans un type référence. Tout comme un constructeur et le destructeur, un finaliseur n’a aucun type de retour.

Après l’exécution du finaliseur d’un objet, les finaliseurs dans les classes de base sont également appelés, commençant par le type moins dérivé. Les finaliseurs pour les membres de données ne sont pas automatiquement chaînées à par un finaliseur de classe.

Si un finaliseur supprime un pointeur natif dans un type managé, vous devez vous assurer que les références à ou via le pointeur natif ne sont pas collectés prématurément ; appeler le destructeur sur le type managé au lieu d’utiliser <xref:System.GC.KeepAlive%2A>.

Au moment de la compilation, vous pouvez détecter si un type a un finaliseur ou un destructeur. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

L’exemple suivant montre deux types, un qui a des ressources non managées et un qui a géré les ressources sont libérées de façon déterministe.

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

[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)
