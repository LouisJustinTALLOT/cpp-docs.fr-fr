---
title: Compilateur avertissement (niveau 3) C4570 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4570
dev_langs:
- C++
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 063c976915e744df8eda3604bdfa121ba21ef36d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099444"
---
# <a name="compiler-warning-level-3-c4570"></a>Avertissement du compilateur (niveau 3) C4570

'type' : n’est pas explicitement déclaré comme abstract mais comporte des fonctions abstract

Un type qui contient [abstraite](../../windows/abstract-cpp-component-extensions.md) fonctions doivent lui-même être marquées comme abstract.

## <a name="example"></a>Exemple

L’exemple suivant génère C4570.

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```