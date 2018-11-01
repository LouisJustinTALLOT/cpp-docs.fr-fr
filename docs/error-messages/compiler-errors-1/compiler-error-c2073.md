---
title: Erreur du compilateur C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 2b45d512224ec32459e6da040a6abb0211278e78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523279"
---
# <a name="compiler-error-c2073"></a>Erreur du compilateur C2073

'identificateur' : les éléments d’un tableau partiellement initialisé doivent avoir un constructeur par défaut

Trop peu d’initialiseurs ont été spécifiées pour un tableau de types définis par l’utilisateur ou de constantes. Si un initialiseur explicit et le constructeur correspondant ne sont pas spécifiés pour un membre du groupe, un constructeur par défaut doit être fourni.

L’exemple suivant génère l’erreur C2073 :

```
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```