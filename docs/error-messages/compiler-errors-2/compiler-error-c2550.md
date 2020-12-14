---
description: 'En savoir plus sur : erreur du compilateur C2550'
title: Erreur du compilateur C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 046cb88be2dfdb0e73273a7c370d6d7fdd97243f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204080"
---
# <a name="compiler-error-c2550"></a>Erreur du compilateur C2550

'identificateur' : les listes d’initialiseurs de constructeur ne sont autorisées que sur les définitions de constructeur

Une liste d’initialiseurs de classe de base est utilisée sur la définition d’une fonction qui n’est pas un constructeur.

L’exemple suivant génère l’C2550 :

```cpp
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```
