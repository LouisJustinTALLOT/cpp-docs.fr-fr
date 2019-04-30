---
title: Erreur du compilateur C3205
ms.date: 11/04/2016
f1_keywords:
- C3205
helpviewer_keywords:
- C3205
ms.assetid: 802d306e-5ff3-4491-8a22-c5f1c072d005
ms.openlocfilehash: bd4d17ff2b6a0197db730a53c5846806335c9fd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402695"
---
# <a name="compiler-error-c3205"></a>Erreur du compilateur C3205

La liste des arguments pour le paramètre template 'paramètre' du modèle est manquante

Un paramètre [template](../../cpp/templates-cpp.md) est manquant.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3205 :

```cpp
// C3205.cpp
template<template<class> class T> struct A {
   typedef T unparameterized_type;   // C3205
   // try the following line instead
   // typedef T<int> unparameterized_type;
};

template <class T>
struct B {
   typedef int value_type;
};

int main() {
   A<B> x;
}
```