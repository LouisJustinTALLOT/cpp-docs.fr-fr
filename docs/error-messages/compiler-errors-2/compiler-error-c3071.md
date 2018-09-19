---
title: Erreur du compilateur C3071 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3071
dev_langs:
- C++
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f004de3ed133ea77d543014ae1adcdc4e1eddef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077800"
---
# <a name="compiler-error-c3071"></a>Erreur du compilateur C3071

l'opérateur 'opérateur' ne peut être appliqué qu'à une instance d'une classe ref ou d'un type valeur

Un opérateur CLR ne peut pas être utilisé sur un type natif. L'opérateur peut être utilisé sur une classe ref ou un struct ref (un type valeur), mais pas sur un type natif tel que int ni sur un alias pour un type natif tel que System::Int32. Ces types ne peuvent pas être convertis à partir de code C++ d'une manière faisant référence à la variable native, si bien que l'opérateur ne peut pas être utilisé.

Pour plus d’informations, consultez [opérateur de référence de suivi](../../windows/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3071.

```
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```