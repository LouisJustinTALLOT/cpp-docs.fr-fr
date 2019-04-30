---
title: Erreur du compilateur C2877
ms.date: 11/04/2016
f1_keywords:
- C2877
helpviewer_keywords:
- C2877
ms.assetid: 0b54837e-fcae-4d90-9658-623250435e24
ms.openlocfilehash: 093efbf0c329967983c1808ee46011425745515f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390631"
---
# <a name="compiler-error-c2877"></a>Erreur du compilateur C2877

'symbole' n’est pas accessible à partir de 'class'

Tous les membres dérivés d’une classe de base doivent être accessibles dans la classe dérivée.

L’exemple suivant génère l’erreur C2877 :

```
// C2877.cpp
// compile with: /c
class A {
private:
   int a;
};

class B : public A {
   using A::a;   // C2877
};
```