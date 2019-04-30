---
title: Erreur du compilateur C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: 78402c054573de8c9860e96b6abe60ec5c3cfe38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395519"
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