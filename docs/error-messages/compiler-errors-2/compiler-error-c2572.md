---
title: Erreur du compilateur C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: 78402c054573de8c9860e96b6abe60ec5c3cfe38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621245"
---
# <a name="compiler-error-c2572"></a>Erreur du compilateur C2572

'classe::membre' : redéfinition du paramètre par défaut : paramètre param

Paramètres par défaut ne peut pas être redéfinis. Si vous avez besoin une autre valeur pour le paramètre, le paramètre par défaut doit rester indéfini.

L’exemple suivant génère C2572 :

```
// C2572.cpp
// compile with: /c
void f(int i = 1);   // function declaration

// function definition
void f(int i = 1) {}   // C2572

// try the following line instead
// void f(int i) {}
```