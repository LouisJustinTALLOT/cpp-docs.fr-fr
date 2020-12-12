---
description: 'En savoir plus sur : erreur du compilateur C2292'
title: Erreur du compilateur C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: fb3630edc1aa3fc3aeb1b90d3ab79b17c775fa61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268247"
---
# <a name="compiler-error-c2292"></a>Erreur du compilateur C2292

'identifier' : représentation d’héritage du meilleur cas : 'representation1 'déclaré mais’representation2 'requis

La compilation du code suivant avec [/VMB](../../build/reference/vmb-vmg-representation-method.md) (représentation « Always-case Always ») provoque C2292.

```cpp
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```
