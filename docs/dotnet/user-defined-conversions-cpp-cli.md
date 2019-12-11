---
title: Conversions définies par l'utilisateur (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988388"
---
# <a name="user-defined-conversions-ccli"></a>Conversions définies par l'utilisateur (C++/CLI)

Cette section décrit les conversions définies par l’utilisateur (UDC) quand l’un des types de la conversion est une référence ou une instance d’un type valeur ou d’un type référence.

## <a name="implicit-and-explicit-conversions"></a>Conversions implicites et explicites

Une conversion définie par l’utilisateur peut être implicite ou explicite.  Une UDC doit être implicite si la conversion n’entraîne pas de perte d’informations. Dans le cas contraire, une UDC explicite doit être définie.

Le constructeur d’une classe Native peut être utilisé pour convertir une référence ou un type valeur en une classe native.

Pour plus d’informations sur les conversions, consultez [conversion boxing](../extensions/boxing-cpp-component-extensions.md) et [conversions standard](../cpp/standard-conversions.md).

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**Sortie**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>Opérateurs Convert-From

Les opérateurs Convert-from créent un objet de la classe dans laquelle l’opérateur est défini à partir d’un objet d’une autre classe.

Standard C++ ne prend pas en charge les opérateurs Convert-from ; la C++ norme utilise des constructeurs à cet effet. Toutefois, lors de l’utilisation de types C++ CLR, Visual fournit une prise en charge syntaxique pour appeler des opérateurs Convert-from.

Pour interagir correctement avec d’autres langages conformes CLS, vous souhaiterez peut-être encapsuler chaque constructeur unaire défini par l’utilisateur pour une classe donnée avec un opérateur Convert-from correspondant.

Opérateurs Convert-from :

- Doit être défini en tant que fonctions statiques.

- Peut être implicite (pour les conversions qui ne perdent pas la précision, telles que short-to-int) ou Explicit, lorsqu’il peut y avoir une perte de précision.

- Doit retourner un objet de la classe conteneur.

- Doit avoir le type « from » comme type de paramètre unique.

L’exemple suivant montre un opérateur de conversion définie par l’utilisateur (UDC) implicite et explicite.

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**Sortie**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>Opérateurs Convert-to

Les opérateurs Convert-to convertissent un objet de la classe dans laquelle l’opérateur est défini sur un autre objet. L’exemple suivant montre un opérateur de conversion implicite, Convert-to, défini par l’utilisateur :

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**Sortie**

```Output
10
```

Un opérateur de conversion explicite défini par l’utilisateur est approprié pour les conversions qui risquent de perdre des données d’une certaine façon. Pour appeler un opérateur Convert-to explicite, vous devez utiliser un cast.

```cpp
// clr_udc_convert_to_2.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**Sortie**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>Pour convertir des classes génériques

Vous pouvez convertir une classe générique en T.

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**Sortie**

```Output
True
```

Un constructeur de conversion prend un type et l’utilise pour créer un objet.  Un constructeur de conversion est appelé avec une initialisation directe uniquement ; les casts n’appellent pas les constructeurs de conversion. Par défaut, les constructeurs de conversion sont explicites pour les types CLR.

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**Sortie**

```Output
5
R
```

Dans cet exemple de code, une fonction de conversion statique implicite fait la même chose qu’un constructeur de conversion explicite.

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**Sortie**

```Output
13
12
500
2000
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)
