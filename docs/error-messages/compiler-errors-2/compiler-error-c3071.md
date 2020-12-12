---
description: 'En savoir plus sur : erreur du compilateur C3071'
title: Erreur du compilateur C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: f99175021b87cb9c27982121567bbb0dd97b0163
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320408"
---
# <a name="compiler-error-c3071"></a>Erreur du compilateur C3071

l'opérateur 'opérateur' ne peut être appliqué qu'à une instance d'une classe ref ou d'un type valeur

Un opérateur CLR ne peut pas être utilisé sur un type natif. L'opérateur peut être utilisé sur une classe ref ou un struct ref (un type valeur), mais pas sur un type natif tel que int ni sur un alias pour un type natif tel que System::Int32. Ces types ne peuvent pas être convertis à partir de code C++ d'une manière faisant référence à la variable native, si bien que l'opérateur ne peut pas être utilisé.

Pour plus d’informations, consultez [opérateur de référence de suivi](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3071.

```cpp
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
