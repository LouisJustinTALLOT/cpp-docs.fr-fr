---
title: 'Procédure : Utiliser le suivi des références en C / c++ / CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- CLR types, passing by reference
ms.assetid: d91e471c-34ff-4786-9e0d-c6db0494b946
ms.openlocfilehash: 8be575bd39bc3b2e6512ba1bcb40d9206731f83a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777049"
---
# <a name="how-to-use-tracking-references-in-ccli"></a>Procédure : Utiliser le suivi des références en C / c++ / CLI

Cet article explique comment utiliser une référence de suivi (%) en C / c++ / CLI pour passer common language runtime (CLR) types par référence.

## <a name="to-pass-clr-types-by-reference"></a>Pour passer des types CLR par référence

L’exemple suivant montre comment utiliser une référence de suivi pour passer des types CLR par référence.

```cpp
// tracking_reference_handles.cpp
// compile with: /clr
using namespace System;

ref struct City {
private:
   Int16 zip_;

public:
   City (int zip) : zip_(zip) {};
   property Int16 zip {
      Int16 get(void) {
         return zip_;
      }   // get
   }   // property
};

void passByRef (City ^% myCity) {
   // cast required so this pointer in City struct is "const City"
   if (myCity->zip == 20100)
      Console::WriteLine("zip == 20100");
   else
      Console::WriteLine("zip != 20100");
}

ref class G {
public:
   int i;
};

void Test(int % i) {
   i++;
}

int main() {
   G ^ g1 = gcnew G;
   G ^% g2 = g1;
   g1 -> i = 12;

   Test(g2->i);   // g2->i will be changed in Test2()

   City ^ Milano = gcnew City(20100);
   passByRef(Milano);
}
```

```Output
zip == 20100
```

L’exemple suivant montre que prendre l’adresse d’une référence de suivi retourne un [interior_ptr (C++ / c++ / CLI)](../extensions/interior-ptr-cpp-cli.md)et montre comment modifier et accéder aux données via une référence de suivi.

```cpp
// tracking_reference_data.cpp
// compile with: /clr
using namespace System;

public ref class R {
public:
   R(int i) : m_i(i) {
      Console::WriteLine("ctor: R(int)");
   }

   int m_i;
};

class N {
public:
   N(int i) : m_i (i) {
      Console::WriteLine("ctor: N(int i)");
   }

   int m_i;
};

int main() {
   R ^hr = gcnew R('r');
   R ^%thr = hr;
   N n('n');
   N %tn = n;

   // Declare interior pointers
   interior_ptr<R^> iphr = &thr;
   interior_ptr<N> ipn = &tn;

   // Modify data through interior pointer
   (*iphr)->m_i = 1;   // (*iphr)->m_i == thr->m_i
   ipn->m_i = 4;   // ipn->m_i == tn.m_i

   ++thr-> m_i;   // hr->m_i == thr->m_i
   ++tn. m_i;   // n.m_i == tn.m_i

   ++hr-> m_i;   // (*iphr)->m_i == hr->m_i
   ++n. m_i;   // ipn->m_i == n.m_i
}
```

```Output
ctor: R(int)
ctor: N(int i)
```

## <a name="tracking-references-and-interior-pointers"></a>Références de suivi et des pointeurs intérieurs

L’exemple de code suivant montre que vous pouvez convertir entre des références de suivi et des pointeurs intérieurs.

```cpp
// tracking_reference_interior_ptr.cpp
// compile with: /clr
using namespace System;

public ref class R {
public:
   R(int i) : m_i(i) {
      Console::WriteLine("ctor: R(int)");
   }

   int m_i;
};

class N {
public:
   N(int i) : m_i(i) {
      Console::WriteLine("ctor: N(int i)");
   }

   int m_i;
};

int main() {
   R ^hr = gcnew R('r');
   N n('n');

   R ^%thr = hr;
   N %tn = n;

   // Declare interior pointers
   interior_ptr<R^> iphr = &hr;
   interior_ptr<N> ipn = &n;

   // Modify data through interior pointer
   (*iphr)->m_i = 1;   // (*iphr)-> m_i == thr->m_i
   ipn->m_i = 4;   // ipn->m_i == tn.m_i

   ++thr->m_i;   // hr->m_i == thr->m_i
   ++tn.m_i;   // n.m_i == tn.m_i

   ++hr->m_i;   // (*iphr)->m_i == hr->m_i
   ++n.m_i;   // ipn->m_i == n.m_i
}
```

```Output
ctor: R(int)
ctor: N(int i)
```

## <a name="tracking-references-and-value-types"></a>Références de suivi et les types valeur

Cet exemple montre un boxing simple via une référence de suivi à un type valeur :

```cpp
// tracking_reference_valuetypes_1.cpp
// compile with: /clr

using namespace System;

int main() {
   int i = 10;
   int % j = i;
   Object ^ o = j;   // j is implicitly boxed and assigned to o
}
```

L’exemple suivant montre que vous pouvez avoir des références de suivi et des références natives à des types valeur.

```cpp
// tracking_reference_valuetypes_2.cpp
// compile with: /clr
using namespace System;
int main() {
   int i = 10;
   int & j = i;
   int % k = j;
   i++;   // 11
   j++;   // 12
   k++;   // 13
   Console::WriteLine(i);
   Console::WriteLine(j);
   Console::WriteLine(k);
}
```

```Output
13
13
13
```

L’exemple suivant montre que vous pouvez utiliser des références de suivi avec les types valeur et les types natifs.

```cpp
// tracking_reference_valuetypes_3.cpp
// compile with: /clr
value struct G {
   int i;
};

struct H {
   int i;
};

int main() {
   G g;
   G % v = g;
   v.i = 4;
   System::Console::WriteLine(v.i);
   System::Console::WriteLine(g.i);

   H h;
   H % w = h;
   w.i = 5;
   System::Console::WriteLine(w.i);
   System::Console::WriteLine(h.i);
}
```

```Output
4
4
5
5
```

Cet exemple montre que vous pouvez lier une référence de suivi à un type valeur sur le tas de garbage collection :

```cpp
// tracking_reference_valuetypes_4.cpp
// compile with: /clr
using namespace System;
value struct V {
   int i;
};

void Test(V^ hV) {   // hv boxes another copy of original V on GC heap
   Console::WriteLine("Boxed new copy V: {0}", hV->i);
}

int main() {
   V v;   // V on the stack
   v.i = 1;
   V ^hV1 = v;   // v is boxed and assigned to hV1
   v.i = 2;
   V % trV = *hV1;   // trV is bound to boxed v, the v on the gc heap.
   Console::WriteLine("Original V: {0}, Tracking reference to boxed V: {1}", v.i, trV.i);
   V ^hV2 = trV;   // hv2 boxes another copy of boxed v on the GC heap
   hV2->i = 3;
   Console::WriteLine("Tracking reference to boxed V: {0}", hV2->i);
   Test(trV);
   v.i = 4;
   V ^% trhV = hV1;  // creates tracking reference to boxed type handle
   Console::WriteLine("Original V: {0}, Reference to handle of originally boxed V: {1}", v.i, trhV->i);
}
```

```Output
Original V: 2, Tracking reference to boxed V: 1
Tracking reference to boxed V: 3
Boxed new copy V: 1
Original V: 4, Reference to handle of originally boxed V: 1
```

## <a name="template-functions-that-take-native-value-or-reference-parameters"></a>Fonctions de modèle qui prennent natives, valeur ou paramètres de référence

En utilisant une référence de suivi dans la signature d’une fonction de modèle, vous vous assurer que la fonction peut être appelée par un paramètre de type natif, valeur CLR ou référence CLR.

```cpp
// tracking_reference_template.cpp
// compile with: /clr
using namespace System;

class Temp {
public:
   // template functions
   template<typename T>
   static int f1(T% tt) {   // works for object in any location
      Console::WriteLine("T %");
      return 0;
   }

   template<typename T>
   static int f2(T& rt) {   // won't work for object on the gc heap
      Console::WriteLine("T &");
      return 1;
   }
};

// Class Definitions
ref struct R {
   int i;
};

int main() {
   R ^hr = gcnew R;
   int i = 1;

   Temp::f1(i); // ok
   Temp::f1(hr->i); // ok
   Temp::f2(i); // ok

   // error can't track object on gc heap with a native reference
   // Temp::f2(hr->i);
}
```

```Output
T %
T %
T &
```

## <a name="see-also"></a>Voir aussi

[Opérateur de référence de suivi](../extensions/tracking-reference-operator-cpp-component-extensions.md)
