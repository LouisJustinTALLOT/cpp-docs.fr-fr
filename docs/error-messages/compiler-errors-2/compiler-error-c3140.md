---
title: Erreur du compilateur C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: dc1e1828583b3ac8342c12a62e6ba4c1694b5824
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760567"
---
# <a name="compiler-error-c3140"></a>Erreur du compilateur C3140

Impossible d’avoir plusieurs attributs’module’dans la même unité de compilation

L’attribut de [module](../../windows/module-cpp.md) ne peut être défini qu’une seule fois par projet.

L’exemple suivant génère l’C3140 :

```cpp
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```
