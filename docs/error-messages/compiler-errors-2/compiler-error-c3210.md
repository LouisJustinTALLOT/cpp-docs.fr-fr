---
title: Erreur du compilateur C3210 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3210
dev_langs:
- C++
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 804586a866f6a4d2c3cf206af14e0e2f907ed1b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037110"
---
# <a name="compiler-error-c3210"></a>Erreur du compilateur C3210

'type' : déclaration d’accès peut uniquement être appliquée à un membre de classe de base

Un [à l’aide de la déclaration](../../cpp/using-declaration.md) a été spécifié de manière incorrecte.

## <a name="example"></a>Exemple

L’exemple suivant génère C3210.

```
// C3210.cpp
// compile with: /c
struct A {
protected:
   int i;
};

struct B {
   using A::i;   // C3210
};

struct C : public A {
   using A::i;   // OK
};
```