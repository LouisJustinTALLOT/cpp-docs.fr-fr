---
title: Erreur du compilateur C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: 1477c767b770e4d1498df951d7ef5b4448e6fde7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536745"
---
# <a name="compiler-error-c2292"></a>Erreur du compilateur C2292

'identificateur' : représentation d’héritage : 'représentation1' déclarée mais 'représentation2' requis

Compilation du code suivant avec [/vmb](../../build/reference/vmb-vmg-representation-method.md) (« idéal toujours « représentation) génère C2292.

```
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```