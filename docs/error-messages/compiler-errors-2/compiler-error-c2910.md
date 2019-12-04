---
title: Erreur du compilateur C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 0061a7171dd08440ec5d8c8b8cadb77303ff8f41
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761113"
---
# <a name="compiler-error-c2910"></a>Erreur du compilateur C2910

'fonction' : ne peut pas être explicitement spécialisé

Le compilateur a détecté une tentative de spécialisation explicite d’une fonction à deux reprises.

L’exemple suivant génère l’C2910 :

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

C2910 peut également être généré si vous essayez de spécialiser explicitement un membre qui n’est pas un modèle. Autrement dit, vous pouvez uniquement spécialiser explicitement un modèle de fonction.

L’exemple suivant génère l’C2910 :

```cpp
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

Cette erreur est également générée en raison du travail de conformité du compilateur effectué dans Visual Studio .NET 2003 :.

Pour que le code soit valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de C++Visual, supprimez `template <>`.

L’exemple suivant génère l’C2910 :

```cpp
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```
