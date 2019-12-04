---
title: Erreur du compilateur C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: b3b37788d6e4727761ab993f0502746edace18e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759176"
---
# <a name="compiler-error-c2279"></a>Erreur du compilateur C2279

la spécification d’exception ne peut pas apparaître dans une déclaration typedef

Sous **/za**, les [spécifications d’exception](../../cpp/exception-specifications-throw-cpp.md) ne sont pas autorisées dans une déclaration typedef.

L’exemple suivant génère l’C2279 :

```cpp
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```
