---
title: Erreur du compilateur C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: e7dde3eb27c018502225ea3bc45e4bee7c699379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623156"
---
# <a name="compiler-error-c3140"></a>Erreur du compilateur C3140

ne peut pas avoir plusieurs attributs 'module' dans la même unité de compilation

Le [module](../../windows/module-cpp.md) attribut ne peut être défini qu’une seule fois par projet.

L’exemple suivant génère l’erreur C3140 :

```
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```