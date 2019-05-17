---
title: 'Procédure : déclarer des types de valeur avec le mot clé interior_ptr (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 2b75f6c4763ddd7d3fd2d802371e21c40d506b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515754"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Procédure : déclarer des types de valeur avec le mot clé interior_ptr (C++/CLI)

Un **interior_ptr** peut être utilisé avec un type valeur.

> [!IMPORTANT]
> Cette fonctionnalité de langage est prise en charge par l’option du compilateur `/clr`, mais pas par l’option du compilateur `/ZW`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple C++/CLI suivant montre comment utiliser un **interior_ptr** avec un type valeur.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Dans un type valeur, le pointeur **this** correspond à un interior_ptr.

Dans le corps d’une fonction membre non statique d’un type valeur `V`, **this** est une expression de type `interior_ptr<V>` dont la valeur est l’adresse de l’objet pour lequel la fonction est appelée.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre comment utiliser l’opérateur address-of avec des membres statiques.

L’adresse d’un membre de type Visual C++ statique génère un pointeur natif.  L’adresse d’un membre de type valeur statique est un pointeur managé, car le membre de type valeur est alloué sur le tas du runtime et peut être déplacé par le récupérateur de mémoire.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>Voir aussi

[interior_ptr (C++-CLI)](interior-ptr-cpp-cli.md)