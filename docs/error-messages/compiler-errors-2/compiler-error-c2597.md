---
title: Erreur du compilateur C2597 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9f8deb325ae54393518698263f3ca93ca88ca48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114447"
---
# <a name="compiler-error-c2597"></a>Erreur du compilateur C2597

référence non conforme à un membre non static 'identificateur'

Causes possibles :

1. Un membre non statique est spécifié dans une fonction membre statique. Pour accéder au membre non statique, vous devez transmettre ou créer une instance locale de la classe et utiliser un opérateur d'accès au membre (`.` ou `->`).

1. L'identificateur spécifié n'est pas un membre d'une classe, d'une structure ni d'une union. Vérifiez l'orthographe de l'identificateur.

1. Un opérateur d'accès au membre fait référence à une fonction non membre.

1. L'exemple suivant génère l'erreur C2597 et montre comment la corriger :

```
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```