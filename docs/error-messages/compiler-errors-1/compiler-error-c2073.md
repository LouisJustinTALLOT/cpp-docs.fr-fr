---
description: 'En savoir plus sur : erreur du compilateur C2073'
title: Erreur du compilateur C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 791f07040b0a0dd70d2cb0aa8373eb6c342c5b97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209163"
---
# <a name="compiler-error-c2073"></a>Erreur du compilateur C2073

'identificateur' : les éléments d’un tableau partiellement initialisé doivent avoir un constructeur par défaut

Trop peu d’initialiseurs ont été spécifiés pour un tableau de types ou de constantes définis par l’utilisateur. Si un initialiseur explicite et son constructeur correspondant ne sont pas spécifiés pour un membre de tableau, un constructeur par défaut doit être fourni.

L’exemple suivant génère l’C2073 :

```cpp
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```cpp
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```
