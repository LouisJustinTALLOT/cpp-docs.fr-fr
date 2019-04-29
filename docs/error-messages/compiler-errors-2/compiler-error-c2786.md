---
title: Erreur du compilateur C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: b03155ad1a209ae59327dd31d432f5623f380ac9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265995"
---
# <a name="compiler-error-c2786"></a>Erreur du compilateur C2786

'type' : opérande non valide pour __uuidof

Le [__uuidof](../../cpp/uuidof-operator.md) opérateur accepte un type défini par l’utilisateur avec un GUID associé ou un objet d’un type défini par l’utilisateur.  Causes possibles :

1. L’argument n’est pas un type défini par l’utilisateur.

1. `__uuidof` Impossible d’extraire le GUID de l’argument.

L’exemple suivant génère C2786 :

```
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```