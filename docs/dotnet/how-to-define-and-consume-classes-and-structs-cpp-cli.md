---
title: 'Comment : définir et consommer des classes et des structs (C++/CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5bec92ce2bd97f11723cdf59c58b7331b39565f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370184"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Comment : définir et consommer des classes et des structs (C++/CLI)

Cet article montre comment définir et consommer des types de référence et des types de valeur définis par l’utilisateur dans le CMD/CLI.

## <a name="contents"></a><a name="BKMK_Contents"></a>Contenu

[Instantanéisation de l’objet](#BKMK_Object_instantiation)

[Classes implicitement abstraites](#BKMK_Implicitly_abstract_classes)

[Visibilité type](#BKMK_Type_visibility)

[Visibilité des membres](#BKMK_Member_visibility)

[Classes autochtones publiques et privées](#BKMK_Public_and_private_native_classes)

[Constructeurs statiques](#BKMK_Static_constructors)

[Sémantique de ce pointeur](#BKMK_Semantics_of_the_this_pointer)

[Fonctions cache-cache](#BKMK_Hide_by_signature_functions)

[Constructeurs de copie](#BKMK_Copy_constructors)

[Destructeurs et finalisateurs](#BKMK_Destructors_and_finalizers)

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a>Instantanéisation de l’objet

Les types de référence (ref) ne peuvent être instantanés que sur le tas géré, pas sur la pile ou sur le tas indigène. Les types de valeur peuvent être instantanés sur la pile ou le tas géré.

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a>Classes implicitement abstraites

Une *classe implicitement abstraite* ne peut pas être instantanée. Une classe est implicitement abstraite si le type de base de la classe est une interface et que la classe n’implémente pas toutes les fonctions des membres de l’interface.

Si vous êtes incapable de construire des objets à partir d’une classe dérivée d’une interface, la raison pourrait être que la classe est implicitement abstraite. Pour plus d’informations sur les classes abstraites, voir [résumé](../extensions/abstract-cpp-component-extensions.md).

L’exemple de code `MyClass` suivant démontre que la `MyClass::func2` classe ne peut pas être instantanée parce que la fonction n’est pas implémentée. Pour permettre à l’exemple de `MyClass::func2`compiler, uncomment .

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a>Visibilité type

Vous pouvez contrôler la visibilité des types de temps d’exécution de langage courant (CLR) de sorte que, si une assemblée est référencée, les types dans l’assemblage peuvent être visibles ou non visibles à l’extérieur de l’assemblage.

`public`indique qu’un type est visible à `#using` tout fichier source qui contient une directive pour l’assemblage qui contient le type.  `private`indique qu’un type n’est pas `#using` visible pour les fichiers source qui contiennent une directive pour l’assemblage qui contient le type. Cependant, les types privés sont visibles au sein d’une même assemblée. Par défaut, la visibilité `private`d’une classe est .

Par défaut avant Visual Studio 2005, les types autochtones avaient une accessibilité publique à l’extérieur de l’assemblage. Activez [Compiler Warning (niveau 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) pour vous aider à voir où les types natifs privés sont utilisés incorrectement. Utilisez le [pragma make_public](../preprocessor/make-public.md) pour donner au public l’accessibilité à un type natif dans un fichier de code source que vous ne pouvez pas modifier.

Pour plus d’informations, consultez [#using, directive](../preprocessor/hash-using-directive-cpp.md).

L’échantillon suivant montre comment déclarer les types et spécifier leur accessibilité, puis accéder à ces types à l’intérieur de l’assemblage. Bien sûr, si une assemblée qui a `#using`des types privés est référencée par l’utilisation , seuls les types publics dans l’assemblée sont visibles.

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

Maintenant, réécrivons l’échantillon précédent afin qu’il soit construit comme un DLL.

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

L’échantillon suivant montre comment accéder aux types en dehors de l’assemblage. Dans cet échantillon, le client consomme le composant qui est intégré dans l’échantillon précédent.

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a>Visibilité des membres

Vous pouvez rendre l’accès à un membre d’une classe publique à partir d’une même `public`assemblée `protected`différente de l’accès à celui-ci de l’extérieur de l’assemblage en utilisant des paires de spécifications d’accès, , et`private`

Ce tableau résume l’effet des différents spécificateurs d’accès :

|Spécificateur|Résultat|
|---------------|------------|
|public|Le membre est accessible à l’intérieur et à l’extérieur de l’assemblée.  Consultez [le public](../cpp/public-cpp.md) pour plus d’informations.|
|private|Le député n’est pas accessible, ni à l’intérieur ni à l’extérieur de l’assemblée.  Voir [privé](../cpp/private-cpp.md) pour plus d’informations.|
|protected|Le membre est accessible à l’intérieur et à l’extérieur de l’assemblée, mais uniquement aux types dérivés.  Voir [protégé](../cpp/protected-cpp.md) pour plus d’informations.|
|internal|Le député est public à l’intérieur de l’assemblée mais privé à l’extérieur de l’assemblée.  `internal` est un mot clé contextuel.  Pour plus d’informations, consultez [Mots clés contextuels](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|public protégé -ou- public protégé|Le membre est public à l’intérieur de l’assemblée mais protégé à l’extérieur de l’assemblée.|
|privé protégé -ou- protégé privé|Le député est protégé à l’intérieur de l’assemblée mais privé à l’extérieur de l’assemblée.|

L’échantillon suivant montre un type public qui a des membres qui sont déclarés avec les différentes conditions d’accès, puis montre l’accès de ces membres de l’intérieur de l’assemblée.

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

Maintenant, nous allons construire l’échantillon précédent comme un DLL.

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

L’échantillon suivant consomme le composant qui a été créé dans l’échantillon précédent et montre ainsi comment accéder aux membres de l’extérieur de l’assemblée.

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a>Classes autochtones publiques et privées

Un type natif peut être référencé à partir d’un type géré.  Par exemple, une fonction dans un type géré peut prendre un paramètre dont le type est une struction indigène.  Si le type et la fonction gérés sont publics dans une assemblée, alors le type natif doit également être public.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Ensuite, créez le fichier de code source qui consomme le type natif :

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Maintenant, compilez un client :

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a>Constructeurs statiques

Un type CLR, par exemple, une classe ou une struct , peut avoir un constructeur statique qui peut être utilisé pour initialiser les membres de données statiques.  Un constructeur statique est appelé tout au plus une fois, et est appelé avant que tout membre statique du type est accessible la première fois.

Un constructeur d’instance fonctionne toujours après un constructeur statique.

Le compilateur ne peut pas téléphoner à un constructeur si la classe a un constructeur statique.  Le compilateur ne peut pas téléphoner à une fonction membre si la classe est un type de valeur, a un constructeur statique et n’a pas de constructeur d’instance.  Le CLR peut en ligne l’appel, mais le compilateur ne peut pas.

Définissez un constructeur statique comme fonction de membre privé, car il est destiné à être appelé uniquement par le CLR.

Pour plus d’informations sur les constructeurs statiques, voir [comment : Définir un constructeur statique d’interface (CMD/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>Sémantique de ce pointeur

Lorsque vous utilisez Visual CMD pour `this` définir les types, le pointeur dans un type de référence est de type "poignée". Le `this` pointeur dans un type de valeur est de type "pointeur intérieur".

Ces différentes sémantiques `this` du pointeur peuvent provoquer un comportement inattendu lorsqu’un indexeur par défaut est appelé. L’exemple suivant montre la bonne façon d’accéder à un indexeur par défaut à la fois dans un type de ref et un type de valeur.

Pour plus d'informations, consultez la rubrique

- [Handle sur l'opérateur Object (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C/CLI)](../extensions/interior-ptr-cpp-cli.md)

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a>Fonctions cache-cache

Dans la norme C, une fonction dans une classe de base est cachée par une fonction qui porte le même nom dans une classe dérivée, même si la fonction de classe dérivée n’a pas le même nombre ou le même type de paramètres. C’est ce qu’on appelle la sémantique *cache-nom.* Dans un type de référence, une fonction dans une classe de base ne peut être cachée par une fonction dans une classe dérivée que si le nom et la liste de paramètres sont les mêmes. C’est ce qu’on appelle la sémantique *cache-signature.*

Une classe est considérée comme une classe cache-signature lorsque toutes ses fonctions sont marquées dans les métadonnées comme `hidebysig`. Par défaut, toutes les classes qui `hidebysig` sont créées sous **/clr** ont des fonctions. Lorsqu’une `hidebysig` classe a des fonctions, le compilateur ne cache pas les fonctions par leur nom dans les classes de base directes, mais si le compilateur rencontre une classe de cache-nom dans une chaîne d’héritage, il continue ce comportement de cache par nom.

Sous la sémantique cache-signature, lorsqu’une fonction est appelée sur un objet, le compilateur identifie la classe la plus dérivée qui contient une fonction qui pourrait satisfaire l’appel de fonction. S’il n’y a qu’une seule fonction dans la classe qui pourrait satisfaire l’appel, le compilateur appelle cette fonction. S’il y a plus d’une fonction dans la classe qui pourrait satisfaire l’appel, le compilateur utilise des règles de résolution de surcharge pour déterminer quelle fonction appeler. Pour plus d’informations sur les règles de surcharge, voir [surcharge de fonction](../cpp/function-overloading.md).

Pour un appel de fonction donné, une fonction dans une classe de base peut avoir une signature qui en fait un match légèrement meilleur qu’une fonction dans une classe dérivée. Toutefois, si la fonction a été explicitement appelée sur un objet de la classe dérivée, la fonction dans la classe dérivée est appelée.

Étant donné que la valeur de retour n’est pas considérée comme faisant partie de la signature d’une fonction, une fonction de classe de base est cachée si elle porte le même nom et prend le même nombre et le même genre d’arguments qu’une fonction de classe dérivée, même si elle diffère dans le type de valeur de retour.

L’échantillon suivant montre qu’une fonction dans une classe de base n’est pas cachée par une fonction dans une classe dérivée.

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

L’échantillon suivant montre que le compilateur Microsoft CMD appelle une fonction dans la classe la plus dérivée, même si une conversion est nécessaire pour faire correspondre un ou plusieurs des paramètres, et ne pas appeler une fonction dans une classe de base qui correspond mieux à l’appel de fonction.

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

L’échantillon suivant montre qu’il est possible de masquer une fonction même si la classe de base a la même signature que la classe dérivée.

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a>Constructeurs de copie

La norme Cmd indique qu’un constructeur de copie est appelé lorsqu’un objet est déplacé, de sorte qu’un objet est créé et détruit à la même adresse.

Cependant, lorsque **/clr** est utilisé pour compiler et une fonction qui est compilée à MSIL appelle une fonction indigène où une classe indigène - ou plus d’un - est passée par la valeur et où la classe indigène a un constructeur de copie et / ou destructeur, aucun constructeur de copie est appelé et l’objet est détruit à une adresse différente de l’endroit où il a été créé. Cela pourrait causer des problèmes si la classe a un pointeur en soi, ou si le code est le suivi des objets par adresse.

Pour plus d’informations, voir [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

L’échantillon suivant montre quand un constructeur de copie n’est pas généré.

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a>Destructeurs et finalisateurs

Les destructeurs dans un type de référence effectuent un nettoyage déterministe des ressources. Les finalisateurs nettoient les ressources non manées et peuvent être appelés de façon déterministe par le destructeur ou non par le collecteur d’ordures. Pour plus d’informations sur les destructeurs dans la norme C, voir [Destructors](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Le comportement des destructeurs d’une classe Visual CMD gérée diffère des extensions gérées pour le C. Pour plus d’informations sur ce changement, voir [Changements dans la sémantique destructeurs](../dotnet/changes-in-destructor-semantics.md).

Le collecteur d’ordures CLR supprime les objets gérés inutilisés et libère leur mémoire lorsqu’ils ne sont plus nécessaires. Cependant, un type peut utiliser des ressources que le éboueur ne sait pas comment libérer. Ces ressources sont connues sous le nom de ressources non gérées (les poignées de fichiers autochtones, par exemple). Nous vous recommandons de libérer toutes les ressources non gestion dans le finalizer. Parce que les ressources gérées sont libérées de façon non déterministe par le collecteur d’ordures, il n’est pas sûr de se référer à des ressources gérées dans un finalisateur parce qu’il est possible que le collecteur d’ordures a déjà nettoyé cette ressource gérée.

Un finalisateur Visual CMD n’est <xref:System.Object.Finalize%2A> pas le même que la méthode. (La documentation CLR utilise <xref:System.Object.Finalize%2A> le finalisateur et la méthode synonyme). La <xref:System.Object.Finalize%2A> méthode est appelée par le collecteur d’ordures, qui invoque chaque finalisateur dans une chaîne d’héritage de classe. Contrairement aux destructeurs Visual CMD, un appel de finalisateur de classe dérivée ne fait pas invoquer le compilateur dans toutes les classes de base.

Étant donné que le compilateur Microsoft CMD prend en charge la <xref:System.IDisposable.Dispose%2A> <xref:System.Object.Finalize%2A> libération déterministe des ressources, n’essayez pas de mettre en œuvre les méthodes ou les méthodes. Cependant, si vous êtes familier avec ces méthodes, voici comment un finalisateur Visual CMD et un <xref:System.IDisposable.Dispose%2A> destructeur qui appelle la carte de finalisateur au modèle:

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

Un type géré peut également utiliser des ressources gérées que vous préférez libérer de façon déterministe, et ne pas laisser au éboueur de libérer non déterministement à un moment donné après que l’objet n’est plus nécessaire. La libération déterministe des ressources peut améliorer considérablement les performances.

Le compilateur Microsoft CMD permet à la définition d’un destructeur de nettoyer déterministement les objets. Utilisez le destructeur pour libérer toutes les ressources que vous souhaitez libérer de façon déterminante.  Si un finalisateur est présent, appelez-le du destructeur, pour éviter la duplication du code.

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

Si le code qui consomme votre type n’appelle pas le destructeur, le collecteur d’ordures finit par libérer toutes les ressources gérées.

La présence d’un destructeur n’implique pas la présence d’un finalisateur. Cependant, la présence d’un finalisateur implique que vous devez définir un destructeur et appeler le finalisateur de ce destructeur. Cela prévoit la libération déterministe de ressources non gestion.

Appeler le destructeur supprime— en <xref:System.GC.SuppressFinalize%2A>utilisant — la finalisation de l’objet. Si le destructeur n’est pas appelé, le finalisateur de votre type sera éventuellement appelé par le collecteur d’ordures.

Le nettoyage déterministique des ressources de votre objet en appelant le destructeur peut améliorer les performances par rapport à laisser le CLR finaliser non déterministement l’objet.

Le code qui est écrit dans Visual CM et compilé à l’aide **de /clr** exécute le destructeur d’un type si :

- Un objet qui est créé en utilisant la sémantique de pile sort hors de portée. Pour plus d’informations, voir [la sémantique de pile de CMD pour les types de référence](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Une exception est lancée pendant la construction de l’objet.

- L’objet est un membre d’un objet dont le destructeur est en marche.

- Vous appelez l’opérateur [de suppression](../cpp/delete-operator-cpp.md) sur une poignée[(Handle to Object Operator (](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)).

- Vous appelez explicitement le destructeur.

Si votre type est consommé par un client qui est écrit dans une autre langue, le destructeur est appelé comme suit:

- Sur un <xref:System.IDisposable.Dispose%2A>appel à .

- Sur un `Dispose(void)` appel à sur le type.

- Si le type n’a pas `using` de portée dans une déclaration C.

Si vous créez un objet d’un type de référence sur le tas géré (ne pas utiliser la sémantique de pile pour les types de référence), utilisez la syntaxe [try-finally](../cpp/try-finally-statement.md) pour s’assurer qu’une exception n’empêche pas le destructeur de s’exécuter.

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

Si votre type a un destructeur, le compilateur génère une `Dispose` méthode qui implémente <xref:System.IDisposable>. Si un type qui est écrit dans Visual CM et a un destructeur qui `IDisposable::Dispose` est consommé à partir d’une autre langue, faire appel à ce type provoque le destructeur du type d’être appelé. Lorsque le type est consommé à partir d’un client `Dispose`Visual CMD, vous ne pouvez pas appeler directement ; au lieu de cela, appelez `delete` le destructeur en utilisant l’opérateur.

Si votre type a un finalisateur, le `Finalize(void)` compilateur <xref:System.Object.Finalize%2A>génère une méthode qui l’emporte.

Si un type a soit un finalisateur ou un destructeur, `Dispose(bool)` le compilateur génère une méthode, selon le modèle de conception. (Pour plus d’informations, voir [Disposer pattern](/dotnet/standard/design-guidelines/dispose-pattern)). Vous ne pouvez `Dispose(bool)` pas explicitement faire appel à Visual C.

Si un type a une classe de base qui se conforme au modèle de conception, les destructeurs pour toutes les classes de base sont appelés lorsque le destructeur de la classe dérivée est appelé. (Si votre type est écrit dans Visual CMD, le compilateur garantit que vos types implémentent ce modèle.) En d’autres termes, le destructeur d’une classe de référence s’étend à ses bases et à ses membres, comme le précise la norme CMD, d’abord le destructeur de la classe est exécuté, puis les destructeurs pour ses membres à l’envers de l’ordre dans lequel ils ont été construits, et enfin les destructeurs pour ses classes de base dans le revers de l’ordre dans lequel ils ont été construits.

Les destructions et les finalisateurs ne sont pas autorisés à l’intérieur des types de valeurs ou des interfaces.

Un finalisateur ne peut être défini ou déclaré que dans un type de référence. Comme un constructeur et un destructeur, un finalisateur n’a pas de type retour.

Après les exécutions de finalisateur d’un objet, les finalistes dans toutes les classes de base sont également appelés, en commençant par le type le moins dérivé. Les finalisateurs pour les membres de données ne sont pas automatiquement enchaînés par le finalisateur d’une classe.

Si un finalisateur supprime un pointeur natif dans un type géré, vous devez vous assurer que les références au pointeur natif ou par l’intermédiaire de celle-ci ne sont pas perçues prématurément; appeler le destructeur sur le type <xref:System.GC.KeepAlive%2A>géré au lieu d’utiliser .

Au moment de la compilation, vous pouvez détecter si un type a un finalisateur ou un destructeur. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

L’échantillon suivant montre deux types, l’un qui a des ressources non gérées et l’autre qui a géré les ressources qui sont déterministées libérés.

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
