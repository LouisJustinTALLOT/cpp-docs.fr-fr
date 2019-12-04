---
title: Erreur du compilateur C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745393"
---
# <a name="compiler-error-c2381"></a>Erreur du compilateur C2381

'fonction' : redéfinition ; __declspec (noreturn) est différent

Une fonction a été déclarée, puis définie, mais la définition a utilisé le modificateur `__declspec` [noreturn](../../cpp/noreturn.md) . L’utilisation de `noreturn` constitue une redéfinition de la fonction ; la déclaration et la définition doivent s’accorder sur l’utilisation de `noreturn`.

L’exemple suivant génère l’C2381 :

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
