---
description: 'En savoir plus sur : erreur du compilateur C2864'
title: Erreur du compilateur C2864
ms.date: 10/04/2019
f1_keywords:
- C2864
helpviewer_keywords:
- C2864
ms.assetid: d0ca2ad9-90a6-4aef-8511-98a3b414c102
ms.openlocfilehash: 763e70fd3ac988cca94f71feeab975e8b8630402
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305362"
---
# <a name="compiler-error-c2864"></a>Erreur du compilateur C2864

> '*member-name*' : un membre de données statique avec un initialiseur de classe doit avoir un type intégral const non volatile

## <a name="remarks"></a>Notes

Pour initialiser un **`static`** membre de données défini en tant que type, qui n’est **`volatile`** **`const`** pas, ou n’est pas un type intégral, utilisez une instruction de définition de membre. Elles ne peuvent pas être initialisées dans une déclaration.

## <a name="example"></a>Exemple

Cet exemple génère C2864 :

```cpp
// C2864.cpp
// compile with: /c
class B  {
private:
   int a = 3;   // OK
   static int b = 3;   // C2864
   volatile static int c = 3;   // C2864
   volatile static const int d = 3;   // C2864
   static const long long e = 3;   // OK
   static const double f = 3.33;   // C2864
};
```

Cet exemple montre comment corriger l'erreur C2864 :

```cpp
// C2864b.cpp
// compile with: /c
class C  {
private:
   int a = 3;
   static int b; // = 3; C2864
   volatile static int c; // = 3; C2864
   volatile static const int d; // = 3; C2864
   static const long long e = 3;
   static const double f; // = 3.33; C2864
};

// Initialize static volatile, non-const, or non-integral
// data members when defined, not when declared:
int C::b = 3;
volatile int C::c = 3;
volatile const int C::d = 3;
const double C::f = 3.33;
```
