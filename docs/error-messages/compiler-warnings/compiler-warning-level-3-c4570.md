---
title: Avertissement du compilateur (niveau 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 13767cdbd34c72953568181c15ad33119bf5179a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991928"
---
# <a name="compiler-warning-level-3-c4570"></a>Avertissement du compilateur (niveau 3) C4570

'type' : n’est pas explicitement déclaré comme abstract, mais a des fonctions abstraites

Un type qui contient des fonctions [abstraites](../../extensions/abstract-cpp-component-extensions.md) doit lui-même être marqué comme abstract.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4570.

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```
